[Uploading index_17.html…]()
<!DOCTYPE html>
<html lang="ja">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, viewport-fit=cover">
<meta name="color-scheme" content="light dark">
<title>SWAPayサポートAI</title>
<link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Zen+Kaku+Gothic+New:wght@500;700;900&family=Noto+Sans+JP:wght@400;500;700&family=JetBrains+Mono:wght@400;600&display=swap">
<style>
  html,body{margin:0;height:100%;}
  [hidden]{display:none !important;}
  img{max-width:100%;}
  :root{
    /* SWAPay brand: black + emerald blue (symbol mark), white */
    --ink:#14191a;
    --muted:#5b6567;
    --paper:#f5f7f7;
    --surface:#ffffff;
    --surface-alt:#edf2f2;
    --line:#dbe2e2;
    --accent:#0089a8;
    --accent-strong:#00697f;
    --accent-ink:#ffffff;
    --accent-soft:#e1f0f4;
    --deep:#12171a;
    --warn-bg:#fdf3e0;
    --warn-line:#eccf8f;
    --warn-ink:#7a5a05;
    --user-bubble:#0089a8;
    --user-bubble-ink:#ffffff;
    --shadow: 0 1px 2px rgba(18,23,26,.08), 0 10px 28px rgba(18,23,26,.10);
  }
  @media (prefers-color-scheme: dark){
    :root:not([data-theme="light"]){
      --ink:#e9f2f3;
      --muted:#93a6a8;
      --paper:#0b0e0f;
      --surface:#141a1b;
      --surface-alt:#1a2223;
      --line:#2a3436;
      --accent:#33c2e0;
      --accent-strong:#5cd3ec;
      --accent-ink:#04141a;
      --accent-soft:#123138;
      --warn-bg:#2c2410;
      --warn-line:#5a4a1c;
      --warn-ink:#e6c97a;
      --user-bubble:#33c2e0;
      --user-bubble-ink:#04141a;
      --shadow: 0 1px 2px rgba(0,0,0,.35), 0 10px 28px rgba(0,0,0,.4);
    }
  }
  :root[data-theme="dark"]{
    --ink:#e9f2f3;
    --muted:#93a6a8;
    --paper:#0b0e0f;
    --surface:#141a1b;
    --surface-alt:#1a2223;
    --line:#2a3436;
    --accent:#33c2e0;
    --accent-strong:#5cd3ec;
    --accent-ink:#04141a;
    --accent-soft:#123138;
    --warn-bg:#2c2410;
    --warn-line:#5a4a1c;
    --warn-ink:#e6c97a;
    --user-bubble:#33c2e0;
    --user-bubble-ink:#04141a;
    --shadow: 0 1px 2px rgba(0,0,0,.35), 0 10px 28px rgba(0,0,0,.4);
  }

  *{box-sizing:border-box;}
  body{
    background:var(--paper);
    color:var(--ink);
    font-family:"Noto Sans JP","Hiragino Kaku Gothic ProN","Yu Gothic",sans-serif;
    padding-inline:16px;
    display:flex;
    justify-content:center;
    min-height:100%;
  }
  .app{
    width:100%;
    max-width:560px;
    display:flex;
    flex-direction:column;
    padding-block:20px 16px;
    gap:12px;
    min-height:calc(100% - 36px);
  }
  .device{
    background:var(--surface);
    border:1px solid var(--line);
    border-radius:20px;
    box-shadow:var(--shadow);
    display:flex;
    flex-direction:column;
    flex:1;
    overflow:hidden;
    min-height:560px;
  }
  header.bar{
    display:flex;
    align-items:center;
    gap:12px;
    padding:14px 18px;
    background:var(--deep);
    color:var(--accent-soft);
    flex-shrink:0;
  }
  .mark{
    width:36px;height:36px;border-radius:10px;
    background:var(--accent);
    color:var(--accent-ink);
    display:flex;align-items:center;justify-content:center;
    font-family:"Zen Kaku Gothic New",sans-serif;
    font-weight:900;
    font-size:15px;
    flex-shrink:0;
  }
  .bar-titles{display:flex;flex-direction:column;gap:1px;min-width:0;}
  .bar-titles .name{
    font-family:"Zen Kaku Gothic New",sans-serif;
    font-weight:700;
    font-size:15px;
    color:#fff;
  }
  .bar-titles .sub{
    font-size:11px;
    color:var(--accent-soft);
    opacity:.8;
  }
  .restart-btn{
    margin-left:auto;
    background:transparent;
    border:1px solid rgba(255,255,255,.28);
    color:#fff;
    font-size:11.5px;
    padding:6px 10px;
    border-radius:100px;
    cursor:pointer;
    font-family:"Noto Sans JP",sans-serif;
    flex-shrink:0;
    transition:background .15s ease;
  }
  .restart-btn:hover{background:rgba(255,255,255,.12);}
  .restart-btn:focus-visible, button:focus-visible, input:focus-visible, textarea:focus-visible{
    outline:2px solid var(--accent-strong);
    outline-offset:2px;
  }

  .crumbs{
    padding:9px 18px;
    font-size:11.5px;
    color:var(--muted);
    background:var(--surface-alt);
    border-bottom:1px solid var(--line);
    display:flex;
    flex-wrap:wrap;
    gap:4px 6px;
    flex-shrink:0;
  }
  .crumbs .seg::after{content:"›";margin-left:6px;color:var(--line);}
  .crumbs .seg:last-child::after{content:"";}
  .crumbs[hidden]{display:none;}

  .transcript{
    flex:1;
    overflow-y:auto;
    padding:18px;
    display:flex;
    flex-direction:column;
    gap:12px;
    scroll-behavior:smooth;
  }
  .row{display:flex;width:100%;}
  .row.bot{justify-content:flex-start;}
  .row.user{justify-content:flex-end;}
  .bubble{
    max-width:84%;
    padding:10px 14px;
    border-radius:16px;
    font-size:14px;
    line-height:1.65;
    white-space:pre-wrap;
    animation:rise .28s ease both;
  }
  @media (prefers-reduced-motion: reduce){ .bubble{animation:none;} }
  @keyframes rise{ from{opacity:0; transform:translateY(6px);} to{opacity:1; transform:translateY(0);} }
  .row.bot .bubble{
    background:var(--surface-alt);
    color:var(--ink);
    border-bottom-left-radius:4px;
  }
  .row.user .bubble{
    background:var(--user-bubble);
    color:var(--user-bubble-ink);
    border-bottom-right-radius:4px;
    font-weight:500;
  }
  .bubble.answer{
    background:var(--accent-soft);
    border:1px solid var(--line);
    max-width:92%;
  }
  .bubble.answer .tag{
    display:block;
    font-family:"Zen Kaku Gothic New",sans-serif;
    font-weight:700;
    font-size:11px;
    letter-spacing:.04em;
    color:var(--accent-strong);
    margin-bottom:4px;
  }
  .bubble.info{
    background:var(--surface-alt);
    border:1px solid var(--line);
    max-width:92%;
  }
  .bubble.info ul{margin:8px 0 0;padding-left:18px;}
  .bubble.info li{margin-bottom:3px;}
  .bubble.warn{
    background:var(--warn-bg);
    border:1px solid var(--warn-line);
    color:var(--warn-ink);
    max-width:92%;
    font-size:12.5px;
  }
  .receipt{
    max-width:100%;
    width:100%;
    background:var(--surface-alt);
    border:1px dashed var(--line);
    border-radius:12px;
    padding:14px 16px;
    font-family:"JetBrains Mono",ui-monospace,monospace;
    font-size:12px;
    line-height:1.7;
  }
  .receipt h4{
    margin:0 0 8px;
    font-family:"Zen Kaku Gothic New",sans-serif;
    font-size:13px;
    letter-spacing:.03em;
  }
  .receipt .line{border-top:1px dashed var(--line);margin:8px 0;}
  .receipt .qa{margin-bottom:7px;}
  .receipt .q{color:var(--muted);}
  .receipt .a{color:var(--ink);font-weight:600;}
  .receipt .f{display:flex;justify-content:space-between;gap:10px;margin-bottom:4px;}
  .receipt .f .k{color:var(--muted);}
  .receipt .f .v{text-align:right;}

  .controls{
    border-top:1px solid var(--line);
    padding:14px 16px;
    background:var(--surface);
    flex-shrink:0;
    display:flex;
    flex-direction:column;
    gap:8px;
  }
  .controls .hint{
    font-size:11px;
    color:var(--muted);
    text-align:center;
    margin-bottom:2px;
  }
  .opt-btn{
    display:flex;
    align-items:center;
    gap:10px;
    width:100%;
    text-align:left;
    background:var(--surface-alt);
    border:1px solid var(--line);
    color:var(--ink);
    padding:11px 14px;
    border-radius:12px;
    font-size:14px;
    font-family:"Noto Sans JP",sans-serif;
    cursor:pointer;
    transition:border-color .15s ease, transform .1s ease, background .15s ease;
  }
  .opt-btn:hover{border-color:var(--accent);background:var(--accent-soft);}
  .opt-btn:active{transform:scale(.99);}
  .opt-btn:disabled{opacity:.45;cursor:default;}
  .opt-num{
    flex-shrink:0;
    width:22px;height:22px;
    border-radius:6px;
    background:var(--deep);
    color:var(--accent-soft);
    font-family:"JetBrains Mono",monospace;
    font-weight:600;
    font-size:12px;
    display:flex;align-items:center;justify-content:center;
  }

  .field{display:flex;flex-direction:column;gap:4px;}
  .field label{font-size:12px;color:var(--muted);}
  .field .req{color:var(--accent-strong);margin-left:2px;}
  .field input,.field textarea{
    font-family:"Noto Sans JP",sans-serif;
    font-size:13.5px;
    padding:9px 11px;
    border-radius:9px;
    border:1px solid var(--line);
    background:var(--paper);
    color:var(--ink);
    resize:vertical;
  }
  .field textarea{min-height:56px;}
  .field input:focus,.field textarea:focus{border-color:var(--accent);}

  .primary-btn, .ghost-btn{
    width:100%;
    padding:12px 14px;
    border-radius:12px;
    font-size:14px;
    font-family:"Zen Kaku Gothic New",sans-serif;
    font-weight:700;
    cursor:pointer;
    border:1px solid transparent;
    text-align:center;
    text-decoration:none;
    display:block;
  }
  .primary-btn{background:var(--accent);color:var(--accent-ink);}
  .primary-btn:hover{background:var(--accent-strong);}
  .ghost-btn{background:transparent;border-color:var(--line);color:var(--ink);font-weight:500;font-family:"Noto Sans JP",sans-serif;}
  .ghost-btn:hover{border-color:var(--accent);}
  .btn-row{display:flex;gap:8px;}
  .btn-row > *{flex:1;}
  .copy-note{font-size:11px;color:var(--accent-strong);text-align:center;min-height:14px;}

  footer.credit{
    text-align:center;
    font-size:11px;
    color:var(--muted);
  }
</style>
</head>
<body>

<div class="app">
  <div class="device">
    <header class="bar">
      <div class="mark">4択</div>
      <div class="bar-titles">
        <div class="name">SWAPay サポートAI</div>
        <div class="sub">加盟店様向け・選択式ガイド</div>
      </div>
      <button class="restart-btn" id="restartBtn" type="button">はじめから</button>
    </header>
    <div class="crumbs" id="crumbs" hidden></div>
    <div class="transcript" id="transcript"></div>
    <div class="controls" id="controls"></div>
  </div>
  <footer class="credit">選択肢をタップして進みます。文字入力は最後のお問い合わせ内容のみです。</footer>
</div>

<script>
(function(){
  "use strict";

  var TREE = {
    step1:{type:"choice", crumb:null, q:"お困りの内容を選択してください。", options:[
      {label:"ID・パスワードについて", to:"cat_id"},
      {label:"決済について", to:"cat_payment"},
      {label:"端末について", to:"cat_device"},
      {label:"通信・その他について", to:"cat_network"}
    ]},

    cat_id:{type:"choice", crumb:"① ID・パスワードについて", q:"どの内容についてお困りですか？", options:[
      {label:"端末IDが分からない", to:"id_terminal_q"},
      {label:"パスワードが分からない", to:"id_password_q"},
      {label:"ログインできない", to:"id_login_q"},
      {label:"ID・パスワードを変更したい", to:"id_change_q"}
    ]},
    id_terminal_q:{type:"choice", crumb:"端末IDが分からない", q:"現在、決済端末をお手元にお持ちですか？", options:[
      {label:"端末を持っている", to:"id_terminal_a"},
      {label:"端末を持っていない", to:"id_terminal_a"},
      {label:"端末が故障して確認できない", to:"id_terminal_a"},
      {label:"どこを確認すればよいか分からない", to:"id_terminal_a"}
    ]},
    id_terminal_a:{type:"answer", text:"端末IDの確認方法をご案内します。端末本体または管理画面をご確認ください。確認できない場合は、SWAPayサポートへお問い合わせください。", to:"resolve_check"},

    id_password_q:{type:"choice", crumb:"パスワードが分からない", q:"パスワードについて、どの状況ですか？", options:[
      {label:"パスワードを忘れた", to:"id_password_a"},
      {label:"入力してもログインできない", to:"id_password_a"},
      {label:"パスワードを変更したい", to:"id_password_a"},
      {label:"その他", to:"id_password_a"}
    ]},
    id_password_a:{type:"answer", text:"端末を起動する際の初期パスワードは「000000」（0が6つ）です。数字のみ入力できる画面の場合も、まずはこちらの初期パスワードをお試しください。コード決済(QRコード決済)用のログインID・パスワードは別のもので、お申し込み完了後にお送りしているご案内に記載されています。初期パスワードでもログインできない場合や、変更後のパスワードが分からなくなった場合は、SWAPayサポートまでご連絡ください（現在のパスワードそのものをサポートへ送信する必要はありません）。", to:"resolve_check"},

    id_login_q:{type:"choice", crumb:"ログインできない", q:"どのような状態ですか？", options:[
      {label:"IDが違うと表示される", to:"id_login_a"},
      {label:"パスワードが違うと表示される", to:"id_login_a"},
      {label:"エラー画面が表示される", to:"id_login_a"},
      {label:"画面が進まない・反応しない", to:"id_login_a"}
    ]},
    id_login_a:{type:"answer", text:"表示されているエラー内容をご確認ください。解決しない場合は、端末ID・発生日時・表示されたエラー内容を添えてSWAPayサポートへお問い合わせください。", to:"resolve_check"},

    id_change_q:{type:"choice", crumb:"ID・パスワードを変更したい", q:"変更したい内容はどれですか？", options:[
      {label:"IDを変更したい", to:"id_change_a"},
      {label:"パスワードを変更したい", to:"id_change_a"},
      {label:"両方変更したい", to:"id_change_a"},
      {label:"変更方法が分からない", to:"id_change_a"}
    ]},
    id_change_a:{type:"answer", text:"変更方法をご案内します。変更後のID・パスワードは安全に管理してください。", to:"resolve_check"},

    cat_payment:{type:"choice", crumb:"② 決済について", q:"どの内容についてお困りですか？", options:[
      {label:"決済できない", to:"pay_fail_method_q"},
      {label:"決済結果が分からない", to:"pay_unknown_q"},
      {label:"決済金額を間違えた", to:"pay_wrong_amount_q"},
      {label:"取消・返金したい", to:"pay_cancel_q"}
    ]},
    pay_fail_method_q:{type:"choice", crumb:"決済できない", q:"どの決済方法で発生していますか？", options:[
      {label:"クレジットカード", to:"pay_fail_card_q"},
      {label:"タッチ決済", to:"pay_fail_card_q"},
      {label:"ICカード決済", to:"pay_fail_card_q"},
      {label:"QRコード決済", to:"pay_qr_q"}
    ]},
    pay_fail_card_q:{type:"choice", crumb:"カード・タッチ決済ができない", q:"どのような状態ですか？", options:[
      {label:"通信エラーが表示される", to:"pay_fail_card_a"},
      {label:"カードエラーが表示される", to:"pay_fail_card_a"},
      {label:"処理中のまま進まない", to:"pay_fail_card_a"},
      {label:"その他のエラー", to:"pay_fail_card_a"}
    ]},
    pay_fail_card_a:{type:"answer", text:"エラー内容をご確認ください。通信状態・カードの状態・端末の状態を確認し、必要に応じて再起動してください。決済結果が不明な場合は、同じ決済をすぐに再実行しないでください。", to:"resolve_check"},

    pay_qr_q:{type:"choice", crumb:"QRコード決済", q:"QRコード決済について、どの内容ですか？", options:[
      {label:"これから利用したい・申込方法を知りたい", to:"pay_qr_apply_a"},
      {label:"申込み後、ログインできない", to:"pay_qr_login_q"},
      {label:"申込み状況やID・パスワードを確認したい", to:"pay_qr_status_a"},
      {label:"その他", to:"pay_qr_other_a"}
    ]},
    pay_qr_apply_a:{type:"answer", text:"QRコード決済のご利用には、別途お申し込みが必要です。SWAPayサポートよりお申し込みのご案内をお送りしますので、3営業日程度を目安にお待ちください。ご案内が届きましたら、記載のURLよりお申し込み手続きをお願いいたします。お申し込み完了後、決済端末にログインするためのID・パスワードが発行されます。セキュリティの都合上、URL発行から72時間以内に初回ログインが必要ですので、あわせてご注意ください。なお、月額の基本料金は発生せず、ご負担いただくのは決済手数料のみです。", to:"resolve_check"},

    pay_qr_login_q:{type:"choice", crumb:"QRコード決済にログインできない", q:"お申し込み手続きはすでに完了していますか？", options:[
      {label:"完了している（IDは入力したがログインできない）", to:"pay_qr_login_done_a"},
      {label:"完了しているか分からない", to:"pay_qr_status_a"},
      {label:"まだ完了していない", to:"pay_qr_apply_a"},
      {label:"ID・パスワードが分からない", to:"pay_qr_status_a"}
    ]},
    pay_qr_login_done_a:{type:"answer", text:"ログインIDには、管理画面でご確認いただける「T」から始まる8桁の番号をご入力いただく必要があります。管理画面上では「端末ID」として表示されている場合がありますが、同じ番号です。ログインID欄に「T」から始まる番号を入力されているか、今一度ご確認ください。ご確認いただいてもログインできない場合は、状況を確認いたしますので、SWAPayサポートまでご連絡ください。", to:"resolve_check"},

    pay_qr_status_a:{type:"answer", text:"お申し込みの状況、またはログイン用ID・パスワードについては、加盟店様ごとに確認が必要な内容です。加盟店名・店舗名を添えてSWAPayサポートへお問い合わせいただければ、状況を確認のうえご案内いたします（現在お使いのパスワードそのものをお送りいただく必要はありません）。", to:"resolve_check"},

    pay_qr_other_a:{type:"answer", text:"QRコード決済の操作方法や設定については、お送りしているご利用マニュアル・お申し込みマニュアルもあわせてご確認ください。入力や手続きの途中で進めなくなった場合は、画面が固まる・エラーが表示される・ボタンが反応しないなど、発生している状況を詳しくお聞かせいただけますと、確認のうえご案内いたします。文章でのご説明が難しい場合は、お電話でのご案内も可能です。SWAPayサポートまでお問い合わせください。", to:"resolve_check"},

    pay_unknown_q:{type:"choice", crumb:"決済結果が分からない", q:"現在の状態を選択してください。", options:[
      {label:"画面が固まっている", to:"pay_unknown_a"},
      {label:"お客様のカードが決済されたか分からない", to:"pay_unknown_a"},
      {label:"端末の電源が切れた", to:"pay_unknown_a"},
      {label:"売上履歴に表示されない", to:"pay_unknown_a"}
    ]},
    pay_unknown_a:{type:"answer", text:"決済結果が不明な場合は、二重決済を防ぐため、同じ決済をすぐに再実行しないでください。端末の状態や売上履歴をご確認ください。", to:"resolve_check"},

    pay_wrong_amount_q:{type:"choice", crumb:"決済金額を間違えた", q:"どの状態ですか？", options:[
      {label:"多い金額で決済した", to:"pay_wrong_amount_a"},
      {label:"少ない金額で決済した", to:"pay_wrong_amount_a"},
      {label:"決済を取り消したい", to:"pay_wrong_amount_a"},
      {label:"正しい金額でもう一度決済したい", to:"pay_wrong_amount_a"}
    ]},
    pay_wrong_amount_a:{type:"answer", text:"誤った金額の決済については、取消・返金方法をご案内します。すでに決済済みの場合は、同じ取引を重複して処理しないようご注意ください。", to:"resolve_check"},

    pay_cancel_q:{type:"choice", crumb:"取消・返金したい", q:"どの内容ですか？", options:[
      {label:"当日の決済を取り消したい", to:"pay_cancel_a"},
      {label:"過去の決済を返金したい", to:"pay_cancel_a"},
      {label:"お客様から返金を依頼された", to:"pay_cancel_a"},
      {label:"取消・返金方法が分からない", to:"pay_cancel_a"}
    ]},
    pay_cancel_a:{type:"answer", text:"取消・返金の対象となる取引をご確認のうえ、所定の操作を行ってください。操作方法が不明な場合は、取引日時・金額・決済方法などを確認してSWAPayサポートへお問い合わせください。", to:"resolve_check"},

    cat_device:{type:"choice", crumb:"③ 端末について", q:"端末について、どの内容ですか？", options:[
      {label:"電源が入らない", to:"dev_power_q"},
      {label:"画面が固まった・動かない", to:"dev_freeze_q"},
      {label:"操作方法が分からない", to:"dev_howto_q"},
      {label:"端末を交換・返却したい", to:"dev_replace_q"}
    ]},
    dev_power_q:{type:"choice", crumb:"電源が入らない", q:"どの状態ですか？", options:[
      {label:"電源ボタンを押しても反応しない", to:"dev_power_a"},
      {label:"画面が真っ暗", to:"dev_power_a"},
      {label:"充電しても起動しない", to:"dev_power_a"},
      {label:"その他", to:"dev_power_a"}
    ]},
    dev_power_a:{type:"answer", text:"充電状態や電源コードの接続をご確認のうえ、電源を再度お試しください。電源コードを接続した状態でも起動しない場合は、まず端末に記載されているサポート窓口へお問い合わせください。窓口に繋がらない場合は、SWAPayサポートまでご連絡いただければ、弊社にて対応いたします。", to:"resolve_check"},

    dev_freeze_q:{type:"choice", crumb:"画面が固まった・動かない", q:"どの状態ですか？", options:[
      {label:"タッチ操作ができない", to:"dev_freeze_a"},
      {label:"処理中の画面から進まない", to:"dev_freeze_a"},
      {label:"アプリ・画面が固まった", to:"dev_freeze_a"},
      {label:"端末全体が反応しない", to:"dev_freeze_a"}
    ]},
    dev_freeze_a:{type:"answer", text:"しばらく待っても改善しない場合は、端末の再起動をお試しください。決済処理中に固まった場合は、決済結果を確認するまで同じ取引を再実行しないでください。", to:"resolve_check"},

    dev_howto_q:{type:"choice", crumb:"操作方法が分からない", q:"どの操作についてですか？", options:[
      {label:"決済操作", to:"dev_howto_a"},
      {label:"取消・返金操作", to:"dev_howto_a"},
      {label:"売上・履歴の確認", to:"dev_howto_a"},
      {label:"その他の操作", to:"dev_howto_a"}
    ]},
    dev_howto_a:{type:"answer", text:"該当する操作方法をご案内します。画面に表示されている内容と異なる場合は、端末の写真や画面内容を添えてお問い合わせください。", to:"resolve_check"},

    dev_replace_q:{type:"choice", crumb:"端末を交換・返却したい", q:"ご希望の内容はどれですか？", options:[
      {label:"故障した（交換したい）", to:"dev_replace_a"},
      {label:"破損した（交換したい）", to:"dev_replace_a"},
      {label:"紛失した", to:"dev_replace_a"},
      {label:"利用をやめて返却したい", to:"dev_return_a"}
    ]},
    dev_replace_a:{type:"answer", text:"端末交換の可否・手続きについて確認いたします。紛失・破損の場合は、速やかにSWAPayサポートへご連絡ください。", to:"resolve_check"},
    dev_return_a:{type:"answer", text:"ご利用を中止し、端末を返却したいとのこと、承知いたしました。返却の可否・返却方法についてご案内いたしますので、加盟店名・店舗名を添えてSWAPayサポートへご連絡ください。", to:"resolve_check"},

    cat_network:{type:"choice", crumb:"④ 通信・その他について", q:"どの内容についてお困りですか？", options:[
      {label:"Wi-Fiにつながらない", to:"net_wifi_q"},
      {label:"通信エラーが発生する", to:"net_error_q"},
      {label:"売上・入金について確認したい", to:"sales_top_q"},
      {label:"レシート・その他について確認したい", to:"receipt_q"}
    ]},
    net_wifi_q:{type:"choice", crumb:"Wi-Fiにつながらない", q:"どの状態ですか？", options:[
      {label:"Wi-Fi一覧が表示されない", to:"net_wifi_a"},
      {label:"Wi-Fiに接続できない", to:"net_wifi_a"},
      {label:"接続済みだが通信できない", to:"net_wifi_a"},
      {label:"パスワードが分からない", to:"net_wifi_a"}
    ]},
    net_wifi_a:{type:"answer", text:"Wi-Fiの電波・接続先(SSID)・パスワードをご確認ください。他の機器は接続できるのに決済端末のみ接続できない場合は、端末側で接続先とパスワードを入力し直し、端末を再起動してから再接続をお試しください。端末が対応する周波数帯(2.4GHz/5GHz)かどうかもあわせてご確認ください。改善しない場合は、SWAPayサポートへご連絡ください。", to:"resolve_check"},

    net_error_q:{type:"choice", crumb:"通信エラーが発生する", q:"どの状態ですか？", options:[
      {label:"決済時に通信エラー", to:"net_error_a"},
      {label:"ログイン時に通信エラー", to:"net_error_a"},
      {label:"Wi-Fi接続時に通信エラー", to:"net_error_a"},
      {label:"頻繁に通信エラーが発生する", to:"net_error_a"}
    ]},
    net_error_a:{type:"answer", text:"通信環境をご確認ください。Wi-Fiの再接続や端末の再起動をお試しください。改善しない場合は、エラー内容・発生日時をご連絡ください。", to:"resolve_check"},

    sales_top_q:{type:"choice", crumb:"売上・入金について", q:"何を確認したいですか？", options:[
      {label:"今日の売上を確認したい", to:"sales_today_a"},
      {label:"昨日以前の売上を確認したい", to:"sales_past_a"},
      {label:"入金日・入金額を確認したい", to:"sales_deposit_q"},
      {label:"手数料・明細を確認したい", to:"sales_fee_a"}
    ]},
    sales_today_a:{type:"answer", text:"決済端末の売上は、端末の売上照会機能、またはGMOフィナンシャルゲートウェイの管理画面でご確認いただけます。管理画面のログイン情報は、端末発送から10営業日以内にお届けします。表示に相違がある、またはログイン情報が届かない場合は、SWAPayサポートへお問い合わせください。", to:"resolve_check"},
    sales_past_a:{type:"answer", text:"過去の売上については、管理画面の売上履歴から日付ごとにご確認いただけます。期間の合計しか確認できない、部門別・日別の内訳が分からないなど、表示内容でお困りの場合は、確認したい対象期間と単位（日別・部門別など）を添えてSWAPayサポートへお問い合わせください。", to:"resolve_check"},
    sales_fee_a:{type:"answer", text:"手数料や明細については、管理画面の明細情報をご確認ください。内容にご不明な点がある場合は、SWAPayサポートへお問い合わせください。", to:"resolve_check"},

    sales_deposit_q:{type:"choice", crumb:"入金について", q:"どの内容ですか？", options:[
      {label:"入金予定日を知りたい", to:"sales_deposit_a"},
      {label:"入金額が合わない", to:"sales_deposit_a"},
      {label:"売上明細を確認したい", to:"sales_deposit_a"},
      {label:"その他", to:"sales_deposit_a"}
    ]},
    sales_deposit_a:{type:"answer", text:"対象期間・売上金額・入金額をご確認ください。確認が必要な場合は、対象の取引日や店舗情報を添えてSWAPayサポートへお問い合わせください。なお、カード会社への売上表の提出要否など、契約内容によって異なる場合がある点は、SWAPayサポートにて正確な内容をご確認いただけます。", to:"resolve_check"},

    receipt_q:{type:"choice", crumb:"レシート・明細について", q:"どの内容ですか？", options:[
      {label:"レシートが印刷されない", to:"receipt_a"},
      {label:"レシートを再発行したい", to:"receipt_a"},
      {label:"売上明細を確認したい", to:"receipt_a"},
      {label:"領収書・その他について確認したい", to:"receipt_a"}
    ]},
    receipt_a:{type:"answer", text:"端末・プリンターの接続状態や用紙をご確認ください。再発行や明細確認については、端末の機能・契約内容に応じてご案内します。", to:"resolve_check"},

    resolve_check:{type:"choice", crumb:null, q:"上記のご案内で解決しましたか？", options:[
      {label:"解決した", to:"end_resolved"},
      {label:"解決していない", to:"inquiry_prep"},
      {label:"別の問題がある", to:"inquiry_prep"},
      {label:"サポートへ問い合わせたい", to:"inquiry_prep"}
    ]},

    end_resolved:{type:"end", text:"ご不明点が解決したとのことで、よかったです。ご利用ありがとうございました。"},

    inquiry_prep:{type:"info",
      text:"サポートへのお問い合わせですね。以下の情報をご準備いただくと、スムーズに確認できます。",
      list:["加盟店名・店舗名","端末ID","発生日時","決済金額・決済方法・エラー内容"],
      note:"必要に応じて、端末画面の写真やエラー画面のスクリーンショットもご用意ください。"
    }
  };

  var SUPPORT_EMAIL = "support@swa-pay.com";

  var els = {
    transcript: document.getElementById("transcript"),
    controls: document.getElementById("controls"),
    crumbs: document.getElementById("crumbs"),
    restart: document.getElementById("restartBtn")
  };

  var state = { history: [], crumbTrail: [], formData: {} };

  function el(tag, cls, text){
    var e = document.createElement(tag);
    if(cls) e.className = cls;
    if(text !== undefined) e.textContent = text;
    return e;
  }

  function scrollDown(){
    requestAnimationFrame(function(){ els.transcript.scrollTop = els.transcript.scrollHeight; });
  }

  function addBotBubble(text, extraClass){
    var row = el("div","row bot");
    var b = el("div","bubble" + (extraClass ? " " + extraClass : ""));
    b.textContent = text;
    row.appendChild(b);
    els.transcript.appendChild(row);
    scrollDown();
    return b;
  }

  function addUserBubble(text){
    var row = el("div","row user");
    var b = el("div","bubble", text);
    row.appendChild(b);
    els.transcript.appendChild(row);
    scrollDown();
  }

  function addAnswerBubble(text){
    var row = el("div","row bot");
    var b = el("div","bubble answer");
    var tag = el("span","tag","ご案内");
    b.appendChild(tag);
    b.appendChild(document.createTextNode(text));
    row.appendChild(b);
    els.transcript.appendChild(row);
    scrollDown();
  }

  function addInfoBubble(node){
    var row = el("div","row bot");
    var b = el("div","bubble info");
    b.appendChild(document.createTextNode(node.text));
    var ul = el("ul");
    node.list.forEach(function(item){ ul.appendChild(el("li",null,item)); });
    b.appendChild(ul);
    row.appendChild(b);
    els.transcript.appendChild(row);
    scrollDown();

    var row2 = el("div","row bot");
    var b2 = el("div","bubble warn");
    b2.textContent = "※ " + node.note;
    row2.appendChild(b2);
    els.transcript.appendChild(row2);
    scrollDown();
  }

  function updateCrumbs(label){
    if(!label) return;
    var last = state.crumbTrail[state.crumbTrail.length - 1];
    if(last === label) return;
    state.crumbTrail.push(label);
    els.crumbs.hidden = false;
    els.crumbs.innerHTML = "";
    state.crumbTrail.forEach(function(c){
      els.crumbs.appendChild(el("span","seg",c));
    });
  }

  function clearControls(){
    els.controls.innerHTML = "";
  }

  function renderChoice(nodeId, node){
    addBotBubble(node.q);
    updateCrumbs(node.crumb);
    clearControls();
    var wrap = el("div");
    node.options.forEach(function(opt, i){
      var btn = el("button","opt-btn");
      btn.type = "button";
      var num = el("span","opt-num", String(i+1));
      btn.appendChild(num);
      btn.appendChild(document.createTextNode(opt.label));
      btn.addEventListener("click", function(){
        Array.prototype.forEach.call(wrap.querySelectorAll(".opt-btn"), function(b){ b.disabled = true; });
        addUserBubble(opt.label);
        state.history.push({ q: node.q, a: opt.label });
        setTimeout(function(){ goTo(opt.to); }, 260);
      });
      wrap.appendChild(btn);
    });
    els.controls.appendChild(wrap);
  }

  function renderAnswer(nodeId, node){
    addAnswerBubble(node.text);
    state.history.push({ info: node.text });
    clearControls();
    els.controls.appendChild(el("div","hint","ご案内を表示しています…"));
    setTimeout(function(){ goTo(node.to); }, 500);
  }

  function renderInfo(nodeId, node){
    addInfoBubble(node);
    clearControls();
    els.controls.appendChild(el("div","hint","お問い合わせ内容を入力してください"));
    setTimeout(renderForm, 300);
  }

  function fieldBlock(id, labelText, required, isTextarea, placeholder){
    var wrap = el("div","field");
    var label = el("label");
    label.setAttribute("for", id);
    label.textContent = labelText;
    if(required) label.appendChild(el("span","req","*"));
    wrap.appendChild(label);
    var input = el(isTextarea ? "textarea" : "input");
    input.id = id;
    if(!isTextarea) input.type = "text";
    if(placeholder) input.placeholder = placeholder;
    if(state.formData[id]) input.value = state.formData[id];
    wrap.appendChild(input);
    return { wrap: wrap, input: input };
  }

  function renderForm(){
    clearControls();
    var form = el("div");
    form.style.display = "flex";
    form.style.flexDirection = "column";
    form.style.gap = "10px";

    var f1 = fieldBlock("f_store", "加盟店名・店舗名", true, false, "例：株式会社〇〇 △△店");
    var f2 = fieldBlock("f_person", "ご担当者名", false, false, "例：山田 太郎");
    var f3 = fieldBlock("f_termid", "端末ID", false, false, "お分かりの範囲で結構です");
    var f4 = fieldBlock("f_when", "発生日時", false, false, "例：2026年9月18日 14時頃");
    var f5 = fieldBlock("f_detail", "決済金額・決済方法・エラー内容など", false, true, "分かる範囲でご記入ください（例：3,300円 / タッチ決済 / 通信エラーと表示）");
    var f6 = fieldBlock("f_other", "その他伝えたいこと", false, true, "任意");

    [f1,f2,f3,f4,f5,f6].forEach(function(f){ form.appendChild(f.wrap); });

    var errorLine = el("div","copy-note");
    var submit = el("button","primary-btn","この内容で確認画面へ進む");
    submit.type = "button";
    submit.addEventListener("click", function(){
      if(!f1.input.value.trim()){
        errorLine.textContent = "加盟店名・店舗名は必須です。ご入力ください。";
        errorLine.style.color = "var(--warn-ink)";
        f1.input.focus();
        return;
      }
      state.formData = {
        f_store: f1.input.value.trim(),
        f_person: f2.input.value.trim(),
        f_termid: f3.input.value.trim(),
        f_when: f4.input.value.trim(),
        f_detail: f5.input.value.trim(),
        f_other: f6.input.value.trim()
      };
      renderSummary();
    });

    els.controls.appendChild(form);
    els.controls.appendChild(errorLine);
    els.controls.appendChild(submit);
  }

  function buildPlainSummary(){
    var lines = [];
    lines.push("【SWAPayサポート お問い合わせ内容】");
    lines.push("");
    lines.push("■ ここまでの選択内容");
    state.history.forEach(function(h){
      if(h.info){
        lines.push("・ご案内：" + h.info);
      } else {
        lines.push("・" + h.q + " → 「" + h.a + "」");
      }
    });
    lines.push("");
    lines.push("■ お問い合わせ内容");
    lines.push("加盟店名・店舗名：" + (state.formData.f_store || "（未記入）"));
    lines.push("ご担当者名：" + (state.formData.f_person || "（未記入）"));
    lines.push("端末ID：" + (state.formData.f_termid || "（未記入）"));
    lines.push("発生日時：" + (state.formData.f_when || "（未記入）"));
    lines.push("決済金額・決済方法・エラー内容：" + (state.formData.f_detail || "（未記入）"));
    if(state.formData.f_other){
      lines.push("その他：" + state.formData.f_other);
    }
    lines.push("");
    lines.push("※ ID・パスワードなどの認証情報は記載しておりません。");
    return lines.join("\n");
  }

  function renderSummary(){
    var row = el("div","row bot");
    var box = el("div","receipt");
    var h = el("h4", null, "お問い合わせ内容の確認");
    box.appendChild(h);

    state.history.forEach(function(h2){
      var qa = el("div","qa");
      if(h2.info){
        var a = el("div","a", "ご案内：" + h2.info);
        qa.appendChild(a);
      } else {
        qa.appendChild(el("div","q", h2.q));
        qa.appendChild(el("div","a", "→ " + h2.a));
      }
      box.appendChild(qa);
    });

    box.appendChild(el("div","line"));

    var fields = [
      ["加盟店名・店舗名", state.formData.f_store],
      ["ご担当者名", state.formData.f_person],
      ["端末ID", state.formData.f_termid],
      ["発生日時", state.formData.f_when],
      ["決済等の内容", state.formData.f_detail],
      ["その他", state.formData.f_other]
    ];
    fields.forEach(function(pair){
      if(!pair[1]) return;
      var f = el("div","f");
      f.appendChild(el("span","k", pair[0]));
      f.appendChild(el("span","v", pair[1]));
      box.appendChild(f);
    });

    row.appendChild(box);
    els.transcript.appendChild(row);
    scrollDown();

    var warnRow = el("div","row bot");
    var warnB = el("div","bubble warn","※ ID・パスワードなどの認証情報そのものはメール本文へ記載しないようご注意ください（このフォームでも収集していません）。");
    warnRow.appendChild(warnB);
    els.transcript.appendChild(warnRow);
    scrollDown();

    clearControls();

    var subject = "【SWAPayサポートお問い合わせ】" + (state.formData.f_store || "加盟店") + "様";
    var body = buildPlainSummary();
    var mailto = "mailto:" + SUPPORT_EMAIL
      + "?subject=" + encodeURIComponent(subject)
      + "&body=" + encodeURIComponent(body);

    var mailBtn = document.createElement("a");
    mailBtn.className = "primary-btn";
    mailBtn.href = mailto;
    mailBtn.textContent = "メールを作成する（" + SUPPORT_EMAIL + "）";

    var copyNote = el("div","copy-note");
    var copyBtn = el("button","ghost-btn","この内容をコピーする");
    copyBtn.type = "button";
    copyBtn.addEventListener("click", function(){
      var text = "宛先：" + SUPPORT_EMAIL + "\n件名：" + subject + "\n\n" + body;
      try{
        if(navigator.clipboard && navigator.clipboard.writeText){
          navigator.clipboard.writeText(text).then(function(){
            copyNote.textContent = "コピーしました。メールソフトに貼り付けてください。";
          }, function(){ fallbackCopy(text); });
        } else {
          fallbackCopy(text);
        }
      }catch(e){
        fallbackCopy(text);
      }
      function fallbackCopy(t){
        try{
          var ta = document.createElement("textarea");
          ta.value = t;
          ta.style.position = "fixed";
          ta.style.opacity = "0";
          document.body.appendChild(ta);
          ta.focus(); ta.select();
          document.execCommand("copy");
          document.body.removeChild(ta);
          copyNote.textContent = "コピーしました。メールソフトに貼り付けてください。";
        }catch(e2){
          copyNote.textContent = "コピーできませんでした。テキストを選択してお使いください。";
        }
      }
    });

    var backBtn = el("button","ghost-btn","内容を修正する");
    backBtn.type = "button";
    backBtn.addEventListener("click", renderForm);

    var restartLink = el("button","ghost-btn","最初からやり直す");
    restartLink.type = "button";
    restartLink.addEventListener("click", restart);

    var row1 = el("div","btn-row");
    row1.appendChild(backBtn);
    row1.appendChild(restartLink);

    els.controls.appendChild(mailBtn);
    els.controls.appendChild(copyBtn);
    els.controls.appendChild(copyNote);
    els.controls.appendChild(row1);
  }

  function renderEnd(nodeId, node){
    addBotBubble(node.text);
    clearControls();
    var btn = el("button","primary-btn","最初からやり直す");
    btn.type = "button";
    btn.addEventListener("click", restart);
    els.controls.appendChild(btn);
  }

  function goTo(nodeId){
    var node = TREE[nodeId];
    if(!node){ return; }
    if(node.type === "choice"){ renderChoice(nodeId, node); }
    else if(node.type === "answer"){ renderAnswer(nodeId, node); }
    else if(node.type === "info"){ renderInfo(nodeId, node); }
    else if(node.type === "end"){ renderEnd(nodeId, node); }
  }

  function restart(){
    state.history = [];
    state.crumbTrail = [];
    state.formData = {};
    els.transcript.innerHTML = "";
    els.crumbs.innerHTML = "";
    els.crumbs.hidden = true;
    addBotBubble("SWAPay加盟店様サポートAIです。あてはまる項目を選んでいただくだけで、順番にご案内します。");
    goTo("step1");
  }

  els.restart.addEventListener("click", restart);

  restart();
})();
</script>
</body>
</html>
