<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>Sopaan · Percentage</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Fraunces:opsz,wght@9..144,500;9..144,700&family=Source+Sans+3:wght@400;600;700&family=IBM+Plex+Mono:wght@500;600&display=swap">
<style>
  html,body{margin:0;} img{max-width:100%;} [hidden]{display:none !important;}
  :root{
    --navy:#16264A; --navy-2:#1F3B6B; --gold:#C79A3E; --gold-soft:#F3E7C9;
    --paper:#FBF9F4; --paper-2:#F1EAD8; --card:#FFFFFF;
    --ink:#211E1A; --ink-soft:#655D4C; --rule:#E4DCC8;
    --success:#2E8B57; --success-soft:#E1F2E7;
    --danger:#BF4B45; --danger-soft:#FAE3E1;
    --locked:#C7BEA9;
    --focus:#1F3B6B;
    --accent-text:#1F3B6B; --retry-text:#8A661F;
    color-scheme:light;
  }
  @media (prefers-color-scheme: dark){
    :root:not([data-theme="light"]){
      --navy:#0E1830; --navy-2:#16264A; --gold:#E0B75B; --gold-soft:#3A2F16;
      --paper:#141210; --paper-2:#1C1914; --card:#1C1914;
      --ink:#EDE7DA; --ink-soft:#B2A996; --rule:#3A342A;
      --success:#7BC79A; --success-soft:#1B2E22;
      --danger:#E38884; --danger-soft:#331D1B;
      --locked:#4A4436;
      --focus:#E0B75B;
      --accent-text:#E0B75B; --retry-text:#E0B75B;
      color-scheme:dark;
    }
  }
  :root[data-theme="dark"]{
    --navy:#0E1830; --navy-2:#16264A; --gold:#E0B75B; --gold-soft:#3A2F16;
    --paper:#141210; --paper-2:#1C1914; --card:#1C1914;
    --ink:#EDE7DA; --ink-soft:#B2A996; --rule:#3A342A;
    --success:#7BC79A; --success-soft:#1B2E22;
    --danger:#E38884; --danger-soft:#331D1B;
    --locked:#4A4436;
    --focus:#E0B75B;
    --accent-text:#E0B75B; --retry-text:#E0B75B;
    color-scheme:dark;
  }

  *{box-sizing:border-box;}
  body{background:var(--paper); color:var(--ink); font-family:'Source Sans 3',-apple-system,'Segoe UI',sans-serif; padding-inline:0; padding-block:0;}
  h1,h2,h3{font-family:'Fraunces',Georgia,serif; text-wrap:balance; margin:0;}
  .num{font-family:'IBM Plex Mono',ui-monospace,monospace; font-variant-numeric:tabular-nums;}

  header.brand{
    background:linear-gradient(155deg,var(--navy) 0%, var(--navy-2) 100%);
    color:#F4EFDF; padding-block:calc(20px + env(safe-area-inset-top,0px)) 18px; padding-inline:20px;
  }
  .brand-row{display:flex; align-items:center; gap:12px; max-width:900px; margin:0 auto;}
  .crest{
    width:42px; height:42px; border-radius:10px; background:var(--gold); color:var(--navy);
    display:flex; align-items:center; justify-content:center; font-family:'Fraunces',serif; font-weight:700; font-size:18px; flex-shrink:0;
  }
  .brand-name{font-size:12px; letter-spacing:.08em; text-transform:uppercase; color:var(--gold); font-weight:700;}
  .series-name{font-size:19px; font-weight:700; font-family:'Fraunces',serif;}
  .chapter-eyebrow{max-width:900px; margin:14px auto 0; font-size:12px; letter-spacing:.06em; text-transform:uppercase; color:#AEB9D6;}
  .chapter-title{font-size:28px; max-width:900px; margin:2px auto 0;}
  .chapter-sub{font-size:14.5px; color:var(--gold); font-weight:700; max-width:900px; margin:3px auto 0;}

  .chapter-progress{max-width:900px; margin:14px auto 0; display:flex; align-items:center; gap:10px;}
  .cp-track{flex:1; height:6px; border-radius:99px; background:rgba(255,255,255,.18); overflow:hidden;}
  .cp-fill{height:100%; background:var(--gold); border-radius:99px; transition:width .3s ease;}
  .cp-label{font-size:11.5px; color:#CFD7EA; white-space:nowrap;}

  .tabbar{position:sticky; top:env(safe-area-inset-top,0px); z-index:15; background:var(--paper); border-bottom:1px solid var(--rule); overflow-x:auto; white-space:nowrap;}
  .tabbar-inner{max-width:900px; margin:0 auto; display:flex; padding-inline:16px;}
  .tab-btn{font-family:inherit; font-size:14px; font-weight:600; color:var(--ink-soft); background:none; border:none; padding:13px 16px; cursor:pointer; position:relative; flex-shrink:0;}
  .tab-btn.active{color:var(--accent-text);}
  .tab-btn.active::after{content:''; position:absolute; left:12px; right:12px; bottom:0; height:3px; background:var(--gold); border-radius:3px 3px 0 0;}
  .tab-count{font-size:11px; color:var(--ink-soft); margin-left:5px;}

  .slide-progress{max-width:900px; margin:0 auto; padding:10px 16px 0; display:flex; align-items:center; gap:10px;}
  .sp-track{flex:1; height:5px; border-radius:99px; background:var(--rule); overflow:hidden;}
  .sp-fill{height:100%; background:var(--accent-text); border-radius:99px; transition:width .3s ease;}
  .sp-label{font-size:12px; color:var(--ink-soft); white-space:nowrap; font-weight:600;}

  .wrap{max-width:900px; margin:0 auto; padding:16px 16px calc(110px + env(safe-area-inset-bottom,0px));}

  .qcard{background:var(--card); border:1px solid var(--rule); border-radius:14px; padding:18px;}
  .qhead{display:flex; align-items:flex-start; gap:10px; margin-bottom:10px;}
  .qnum{width:32px; height:32px; border-radius:8px; background:var(--gold-soft); color:var(--accent-text); display:flex; align-items:center; justify-content:center; font-weight:700; font-family:'Fraunces',serif; flex-shrink:0; font-size:14px;}
  .qtext{font-size:16px; line-height:1.55; flex:1;}
  .qtag{font-size:10.5px; color:var(--gold); background:var(--gold-soft); padding:2px 7px; border-radius:99px; font-weight:700; margin-left:6px; white-space:nowrap;}
  .marks-pill{font-size:11px; font-weight:700; color:var(--ink-soft); border:1px solid var(--rule); padding:3px 9px; border-radius:99px; margin-left:auto; flex-shrink:0; white-space:nowrap;}
  .step-badge{font-size:11px; font-weight:700; color:var(--accent-text); background:var(--paper-2); border:1px solid var(--rule); padding:3px 9px; border-radius:99px; display:inline-block; margin-bottom:12px;}

  .options{display:flex; flex-direction:column; gap:8px; margin-top:10px;}
  .opt{display:flex; align-items:center; gap:10px; padding:11px 12px; border:1.5px solid var(--rule); border-radius:10px; cursor:pointer; font-size:15px; background:var(--paper);}
  .opt input{accent-color:var(--navy-2);}
  .opt.is-correct{border-color:var(--success); background:var(--success-soft);}
  .opt.is-wrong{border-color:var(--danger); background:var(--danger-soft);}
  .opt.locked{cursor:not-allowed;}

  .subpart-label{font-weight:700; font-size:12.5px; color:var(--accent-text); text-transform:uppercase; letter-spacing:.03em; margin:14px 0 6px;}
  .or-divider{text-align:center; font-size:11px; font-weight:700; letter-spacing:.08em; color:var(--ink-soft); margin:8px 0;}

  .steps{display:flex; flex-direction:column; gap:10px;}
  .step-line{font-size:14.5px; line-height:1.9; background:var(--paper); border:1px dashed var(--rule); border-radius:10px; padding:9px 12px;}
  .step-line.resolved{opacity:.9;}
  .blank-input{font-family:'IBM Plex Mono',monospace; font-size:14px; border:1.5px solid var(--rule); border-radius:6px; padding:3px 8px; width:120px; background:var(--card); color:var(--ink); margin:0 2px;}
  .blank-input:focus{outline:none; border-color:var(--focus); box-shadow:0 0 0 3px var(--gold-soft);}
  .blank-input.is-correct{border-color:var(--success); background:var(--success-soft);}
  .blank-input.is-wrong{border-color:var(--danger); background:var(--danger-soft);}
  .blank-input[disabled]{opacity:.85;}
  .reveal-note{font-size:12px; color:var(--danger); padding-left:2px; margin-top:-2px;}

  .feedback{font-size:13.5px; padding:10px 12px; border-radius:9px; margin-top:14px; display:none;}
  .feedback.show{display:block;}
  .feedback.ok{background:var(--success-soft); color:var(--success);}
  .feedback.retry{background:var(--gold-soft); color:var(--retry-text);}
  .feedback.reveal{background:var(--danger-soft); color:var(--danger);}
  .feedback.err{background:var(--danger-soft); color:var(--danger);}
  .attempts-dots{display:inline-flex; gap:4px; margin-left:2px;}
  .attempts-dots span{width:6px; height:6px; border-radius:50%; background:var(--ink-soft); opacity:.3; display:inline-block;}
  .attempts-dots span.used{opacity:1; background:var(--danger);}

  .ar-box{background:var(--paper-2); border-radius:10px; padding:10px 12px; margin-bottom:12px; font-size:13px; color:var(--ink-soft);}

  .navbar{
    position:fixed; left:0; right:0; bottom:0; z-index:30; background:var(--paper);
    border-top:1px solid var(--rule); padding:10px 16px calc(10px + env(safe-area-inset-bottom,0px));
  }
  .navbar-inner{max-width:900px; margin:0 auto; display:flex; gap:8px; flex-wrap:wrap; align-items:center;}
  .btn{font-family:inherit; font-size:13.5px; font-weight:700; padding:10px 14px; border-radius:9px; border:1.5px solid var(--rule); background:var(--card); color:var(--ink); cursor:pointer;}
  .btn:hover{border-color:var(--navy-2);}
  .btn:disabled{opacity:.4; cursor:not-allowed;}
  .btn-primary{background:var(--navy-2); color:#fff; border-color:var(--navy-2);}
  .navbar .spacer{flex:1;}

  .fab{position:fixed; right:16px; bottom:calc(74px + env(safe-area-inset-bottom,0px)); background:var(--gold); color:var(--navy); border:none; border-radius:999px; padding:11px 16px; font-family:inherit; font-weight:700; font-size:13px; display:flex; align-items:center; gap:7px; cursor:pointer; box-shadow:0 6px 16px rgba(0,0,0,.18); z-index:35;}
  .fab-badge{background:rgba(255,255,255,.55); border-radius:99px; padding:1px 7px; font-size:11px;}

  .overlay{position:fixed; inset:0; background:rgba(20,18,14,.45); z-index:50; display:none; align-items:flex-end; justify-content:center;}
  .overlay.show{display:flex;}
  .palette{background:var(--card); width:min(480px,100%); max-height:78vh; overflow-y:auto; border-radius:18px 18px 0 0; padding:18px 18px calc(18px + env(safe-area-inset-bottom,0px)); border:1px solid var(--rule); border-bottom:none;}
  @media (min-width:640px){ .overlay{align-items:center;} .palette{border-radius:18px; border-bottom:1px solid var(--rule); max-height:74vh;} }
  .palette-head{display:flex; align-items:center; justify-content:space-between; margin-bottom:6px;}
  .palette-head h2{font-size:16px;}
  .palette-close{background:none; border:none; font-size:20px; color:var(--ink-soft); cursor:pointer; padding:4px;}
  .palette-legend{display:flex; gap:12px; flex-wrap:wrap; font-size:11px; color:var(--ink-soft); margin:10px 0 14px;}
  .palette-legend span{display:inline-flex; align-items:center; gap:5px;}
  .dot{width:9px; height:9px; border-radius:50%; display:inline-block;}
  .dot.correct{background:var(--success);} .dot.revealed{background:var(--danger);}
  .dot.skipped{background:var(--gold);} .dot.locked{background:var(--locked);}
  .dot.current{background:var(--navy-2);}
  .chip-grid{display:grid; grid-template-columns:repeat(auto-fill,minmax(48px,1fr)); gap:8px;}
  .chip{border:1.5px solid var(--rule); border-radius:9px; padding:8px 4px; text-align:center; font-family:'IBM Plex Mono',monospace; font-size:12.5px; font-weight:600; cursor:pointer; background:var(--paper); color:var(--ink);}
  .chip[data-status="correct"]{border-color:var(--success); background:var(--success-soft); color:var(--success);}
  .chip[data-status="revealed"]{border-color:var(--danger); background:var(--danger-soft); color:var(--danger);}
  .chip[data-status="skipped"]{border-color:var(--gold); background:var(--gold-soft); color:var(--retry-text);}
  .chip[data-status="locked"]{border-color:var(--rule); color:var(--locked); cursor:not-allowed; background:var(--paper-2);}
  .chip[data-status="current"]{outline:2px solid var(--navy-2); outline-offset:1px;}

  .toast{position:fixed; left:50%; bottom:calc(140px + env(safe-area-inset-bottom,0px)); transform:translateX(-50%); background:var(--ink); color:var(--paper); padding:9px 16px; border-radius:99px; font-size:13px; opacity:0; pointer-events:none; transition:opacity .25s ease; z-index:60;}
  .toast.show{opacity:1;}

  .done-card{text-align:center; padding:36px 20px;}
  .done-card .big{font-size:38px; margin-bottom:6px;}
  .score-pills{display:flex; gap:10px; justify-content:center; flex-wrap:wrap; margin:16px 0;}
  .score-pill{padding:8px 16px; border-radius:99px; font-size:13px; font-weight:700;}

  footer.brandfoot{max-width:900px; margin:14px auto 0; padding:0 16px calc(110px + env(safe-area-inset-bottom,0px)); text-align:center; font-size:12px; color:var(--ink-soft);}

  .mode-pill{font-family:inherit; font-size:12.5px; font-weight:700; color:var(--navy); background:var(--gold); border:none; border-radius:99px; padding:6px 14px; cursor:pointer; margin-top:12px; display:inline-flex; align-items:center; gap:6px;}
  .mode-pick{display:flex; flex-direction:column; gap:14px; padding:8px 0 24px;}
  .mode-card{background:var(--card); border:1.5px solid var(--rule); border-radius:16px; padding:22px; cursor:pointer; text-align:left;}
  .mode-card:hover{border-color:var(--navy-2);}
  .mode-card .mode-icon{font-size:26px; margin-bottom:8px;}
  .mode-card h3{font-size:18px; margin-bottom:6px;}
  .mode-card p{font-size:13.5px; color:var(--ink-soft); line-height:1.5; margin:0;}
  .quiz-hint{font-size:12.5px; color:var(--ink-soft); background:var(--paper-2); border-radius:9px; padding:8px 12px; margin-bottom:14px;}
  .review-row{border:1px solid var(--rule); border-radius:10px; padding:11px 13px; margin-bottom:10px;}
  .review-tag{font-size:11.5px; font-weight:700; margin-bottom:4px; display:block;}
  .review-tag.ok{color:var(--success);} .review-tag.bad{color:var(--danger);} .review-tag.na{color:var(--ink-soft);}
  .review-q{font-size:13.5px; margin-bottom:6px; color:var(--ink-soft);}
  .review-ans{font-size:13px; margin-bottom:2px;}

  .who-row{max-width:900px; margin:12px auto 0; display:flex; flex-wrap:wrap; gap:8px; align-items:center;}
  .who-row .mode-pill{margin-top:0;}
  .who{display:inline-flex; flex-wrap:wrap; align-items:center; gap:6px; font-size:12.5px; color:#CFD7EA;}
  .who b{color:#F4EFDF;}
  .who button{font-family:inherit; font-size:12px; font-weight:700; color:#F4EFDF; background:rgba(255,255,255,.12); border:1px solid rgba(255,255,255,.22); border-radius:99px; padding:5px 11px; cursor:pointer;}
  .who button:hover{background:rgba(255,255,255,.2);}
  .login-card{max-width:460px; margin:8px auto 0; background:var(--card); border:1px solid var(--rule); border-radius:16px; padding:22px;}
  .login-card h2{font-size:21px; margin-bottom:4px;}
  .login-card p.lead{font-size:13.5px; color:var(--ink-soft); margin:0 0 16px; line-height:1.5;}
  .fld{display:flex; flex-direction:column; gap:5px; margin-bottom:12px;}
  .fld label{font-size:12px; font-weight:700; letter-spacing:.04em; text-transform:uppercase; color:var(--ink-soft);}
  .fld input{font-family:inherit; font-size:15px; padding:10px 12px; border:1.5px solid var(--rule); border-radius:9px; background:var(--paper); color:var(--ink);}
  .fld input:focus{outline:none; border-color:var(--focus); box-shadow:0 0 0 3px var(--gold-soft);}
  .fld-row{display:grid; grid-template-columns:1fr 1fr; gap:10px;}
  .login-err{font-size:13px; color:var(--danger); background:var(--danger-soft); border-radius:8px; padding:8px 10px; margin-bottom:12px;}
  .login-note{font-size:12px; color:var(--ink-soft); margin-top:12px; line-height:1.5;}
  .known{margin:0 0 16px; display:flex; flex-direction:column; gap:6px;}
  .known-label{font-size:12px; font-weight:700; letter-spacing:.04em; text-transform:uppercase; color:var(--ink-soft);}
  .known-btn{display:flex; justify-content:space-between; align-items:center; gap:10px; text-align:left; font-family:inherit; font-size:14.5px; padding:10px 12px; border:1.5px solid var(--rule); border-radius:10px; background:var(--paper); color:var(--ink); cursor:pointer;}
  .known-btn:hover{border-color:var(--navy-2);}
  .known-btn small{font-size:12px; color:var(--ink-soft);}
  .rec-card{background:var(--card); border:1px solid var(--rule); border-radius:14px; padding:18px; margin-bottom:14px;}
  .rec-card h2{font-size:19px; margin-bottom:10px;}
  .rec-card h3{font-size:15px; margin:4px 0 8px;}
  .rec-table-wrap{overflow-x:auto;}
  .rec-table{width:100%; border-collapse:collapse; font-size:13.5px; font-variant-numeric:tabular-nums;}
  .rec-table th{text-align:left; font-size:11.5px; text-transform:uppercase; letter-spacing:.04em; color:var(--ink-soft); padding:6px 8px; border-bottom:1px solid var(--rule); white-space:nowrap;}
  .rec-table td{padding:8px; border-bottom:1px solid var(--rule); white-space:nowrap;}
  .rec-bar{display:inline-block; width:70px; height:6px; border-radius:99px; background:var(--rule); overflow:hidden; vertical-align:middle; margin-right:6px;}
  .rec-bar i{display:block; height:100%; background:var(--success);}
  .rec-empty{font-size:13.5px; color:var(--ink-soft);}
  .sec-sub{max-width:900px; margin:0 auto; padding:10px 16px 0; font-size:12.5px; font-weight:700; color:var(--accent-text); letter-spacing:.02em;}
  .opt{flex-wrap:wrap;}
  .opt-l{font-family:'IBM Plex Mono',monospace; font-size:13px; font-weight:600; color:var(--ink-soft);}
  .opt-t{flex:1; min-width:0;}
  .opt.is-chosen:not(.is-correct):not(.is-wrong){border-color:var(--navy-2); background:var(--gold-soft);}
  .opt-tag{font-size:11px; font-weight:700; padding:2px 8px; border-radius:99px; background:var(--card); border:1px solid currentColor; white-space:nowrap;}
  .opt.is-correct .opt-tag{color:var(--success);} .opt.is-wrong .opt-tag{color:var(--danger);} .opt.is-chosen:not(.is-correct):not(.is-wrong) .opt-tag{color:var(--accent-text);}
  .chosen{font-size:13.5px; margin-top:10px; padding:8px 12px; border-radius:9px;}
  .chosen.ok{background:var(--success-soft); color:var(--success);} .chosen.bad{background:var(--danger-soft); color:var(--danger);}
  .chosen + .chosen{margin-top:6px;}
  .solution{margin-top:14px; border:1px solid var(--rule); border-left:4px solid var(--gold); background:var(--paper-2); border-radius:10px; padding:12px 14px;}
  .sol-h{font-family:'Fraunces',Georgia,serif; font-weight:700; font-size:14px; color:var(--accent-text); margin-bottom:6px;}
  .sol-line{font-size:14.5px; line-height:1.7;}
  .rev-sol summary{cursor:pointer; font-size:12.5px; font-weight:700; color:var(--accent-text); margin-top:6px;}
  .rev-sol .solution{margin-top:8px;}
  .chapter-credit{max-width:900px; margin:4px auto 0; font-size:12px; color:#CFD7EA;}
  footer.brandfoot a{color:inherit;}
  .blank-input.wide{width:260px; max-width:100%; font-family:'Source Sans 3',sans-serif;}
  .blank-input.expr{width:170px; max-width:100%;}
  /*fix-layout*/ .cp-fill,.sp-fill{width:0;} .fld{min-width:0;} .fld input{width:100%; min-width:0; box-sizing:border-box;}
  .fig{margin:6px 0 10px; display:flex; justify-content:center;}
  .figsvg{width:100%; max-width:340px; height:auto; overflow:visible;}
  .figsvg .ln,.figsvg .arm{stroke:var(--ink); stroke-width:1.6; fill:none;}
  .figsvg .arm{stroke:var(--accent-text); stroke-width:2;}
  .figsvg .pt{fill:var(--ink);}
  .figsvg .lb{fill:var(--ink); font:600 13px 'Source Sans 3',sans-serif;}
  .figsvg .al{fill:var(--accent-text); font:700 12px 'Source Sans 3',sans-serif;}
  .figsvg .wg{fill:var(--gold-soft); stroke:var(--gold); stroke-width:1.2;}
  .figsvg .wg2{fill:rgba(199,154,62,.35); stroke:var(--gold); stroke-width:1.2;}
  .figsvg .ra{fill:none; stroke:var(--ink); stroke-width:1.2;}
  .figsvg .ahd{fill:var(--ink);}
  .figsvg .pr{fill:var(--paper-2); stroke:var(--ink-soft); stroke-width:1.2;}
  .figsvg .tk{stroke:var(--ink-soft); stroke-width:.8;}
  .figsvg .po{fill:var(--ink); font:600 8.5px 'IBM Plex Mono',monospace;}
  .figsvg .pi{fill:var(--danger); font:600 7.5px 'IBM Plex Mono',monospace;}
  .figsvg .sh{fill:var(--gold-soft); stroke:var(--ink); stroke-width:1.5; stroke-linejoin:round;}
  .figsvg .sh2{fill:rgba(199,154,62,.38); stroke:var(--ink); stroke-width:1.5; stroke-linejoin:round;}
  .figsvg .sh3{fill:rgba(199,154,62,.22); stroke:var(--ink); stroke-width:1.5; stroke-linejoin:round;}
  .figsvg .none{fill:none;}
  .figsvg .hid{stroke-dasharray:5 4; fill:none;}
  .figsvg .tick{stroke:var(--ink); stroke-width:1.4; fill:none;}
  .figsvg .shd{fill:var(--accent-text); fill-opacity:.55;}
  .figsvg .cell{fill:var(--card); stroke:var(--ink); stroke-width:1.1;}
  .figsvg .dr{fill:var(--danger);} .figsvg .dw{fill:var(--card); stroke:var(--ink); stroke-width:1.2;}
  .figsvg .dotfill{fill:var(--danger);}
  .tt{border-collapse:collapse; font-size:13.5px; margin:4px auto; font-variant-numeric:tabular-nums;} .tt th,.tt td{border:1px solid var(--rule); padding:4px 9px; text-align:left;} .tt th{background:var(--paper-2); font-weight:700;} .ttw{overflow-x:auto; max-width:100%;}
  .fq{display:inline-flex; flex-direction:column; vertical-align:middle; text-align:center; font-size:.82em; line-height:1.12; margin:0 2px;}
  .fq>span:first-child{border-bottom:1.5px solid currentColor; padding:0 2px;}
  .fq>span:last-child{padding:0 2px;}
  .mx{white-space:nowrap;}
  .blank-input.fr{width:110px;}
  @media (prefers-reduced-motion:reduce){ *{transition:none !important;} }
</style>
</head>
<body>
<header class="brand">
  <div class="brand-row">
    <div class="crest">BM</div>
    <div>
      <div class="brand-name">Brain &amp; Mind Academy</div>
      <div class="series-name">Sopaan <span style="font-weight:400;font-size:14px;color:#CFD7EA;">Practice Series</span></div>
    </div>
  </div>
  <div class="chapter-eyebrow">Grade 6 Mathematics · Chapter 12</div>
  <div class="chapter-title">Percentage</div>
  <div class="chapter-sub">Exercises 12A–12I · Review Sets · Step-by-Step Practice</div><div class="chapter-credit">Follows Haese Mathematics 6 (MYP 1), Chapter 12</div>
  <div class="chapter-progress">
    <div class="cp-track"><div class="cp-fill" id="cpFill"></div></div>
    <div class="cp-label" id="cpLabel">0% complete</div>
  </div>
  <div class="who-row"><button class="mode-pill" id="modePill" hidden>Choose a mode</button><span class="who" id="whoBar" hidden></span></div>
</header>

<nav class="tabbar"><div class="tabbar-inner" id="tabbar"></div></nav>
<div class="sec-sub" id="secSub"></div><div class="slide-progress"><div class="sp-track"><div class="sp-fill" id="spFill"></div></div><div class="sp-label" id="spLabel">Question 1 of 49</div></div>
<div class="wrap" id="wrap"></div>
<footer class="brandfoot">Brain &amp; Mind Academy · Sopaan Practice Series · Grade 6 Mathematics<br>Exercises follow the structure of <i>Mathematics 6 (MYP 1), 3rd edition</i>, Haese Mathematics. Questions, steps and solutions written by Brain &amp; Mind Academy.</footer>

<div class="navbar"><div class="navbar-inner" id="navbarInner"></div></div>
<button class="fab" id="paletteFab"><span>Questions</span><span class="fab-badge" id="fabBadge">0/49</span></button>

<div class="overlay" id="overlay">
  <div class="palette" role="dialog" aria-label="Question palette">
    <div class="palette-head"><h2 id="paletteTitle">Question palette</h2><button class="palette-close" id="paletteClose">&times;</button></div>
    <div class="palette-legend">
      <span><i class="dot current"></i>Current</span><span><i class="dot correct"></i>Correct</span>
      <span><i class="dot revealed"></i>Revealed</span><span><i class="dot skipped"></i>Skipped</span>
      <span><i class="dot locked"></i>Locked</span>
    </div>
    <div class="chip-grid" id="paletteBody"></div>
  </div>
</div>
<div class="toast" id="toast"></div>

<script>
(function(){
"use strict";

/* ================= audio ================= */
var audioCtx=null;
function ensureAudio(){ if(!audioCtx){ try{ audioCtx=new (window.AudioContext||window.webkitAudioContext)(); }catch(e){} } return audioCtx; }
function playTone(freqs,dur,type){
  var ctx=ensureAudio(); if(!ctx) return;
  try{
    var t0=ctx.currentTime;
    freqs.forEach(function(f,i){
      var o=ctx.createOscillator(), g=ctx.createGain();
      o.type=type||'sine'; o.frequency.value=f;
      var start=t0+i*dur;
      g.gain.setValueAtTime(0.0001,start);
      g.gain.exponentialRampToValueAtTime(0.16,start+0.02);
      g.gain.exponentialRampToValueAtTime(0.0001,start+dur);
      o.connect(g); g.connect(ctx.destination);
      o.start(start); o.stop(start+dur+0.02);
    });
  }catch(e){}
}
function playSuccess(){ playTone([523.25,659.25,783.99],0.11,'sine'); }
function playWrong(){ playTone([220,185],0.14,'square'); }
function playReveal(){ playTone([300,220],0.16,'triangle'); }

/* ================= helpers ================= */
function norm(s){
  return String(s===undefined||s===null?'':s).trim().toLowerCase().replace(/\s+/g,'')
    .replace(/[×∗*·]/g,'x').replace(/÷/g,'/').replace(/–|—|−/g,'-')
    .replace(/[²]/g,'^2').replace(/[³]/g,'^3').replace(/[⁴]/g,'^4').replace(/[⁵]/g,'^5')
    .replace(/[⁶]/g,'^6').replace(/[⁷]/g,'^7').replace(/[⁸]/g,'^8').replace(/[⁹]/g,'^9')
    .replace(/\^/g,'');
}
function parseNum(s){
  if(s===undefined||s===null) return null;
  var t=String(s).trim().replace(/,/g,'').replace(/[−–—]/g,'-').replace(/\s+/g,''); if(t==='') return null;
  var neg=false; if(t[0]==='-'){neg=true;t=t.slice(1);}
  var m=t.match(/^(\d+)\/(\d+)$/);
  if(m){ var v=parseInt(m[1],10)/parseInt(m[2],10); return neg?-v:v; }
  if(/^\d+(\.\d+)?$/.test(t)){ var v2=parseFloat(t); return neg?-v2:v2; }
  return null;
}
/* ---- expression checker: compares answers like (P-2w)/2 and P/2-w at random values ---- */
function exprPrep(s){
  return String(s).replace(/\s+/g,'').replace(/[×∗·]/g,'*').replace(/÷/g,'/').replace(/[−–—]/g,'-')
    .replace(/²/g,'^2').replace(/³/g,'^3').replace(/π/g,'#').replace(/pi/gi,'#').replace(/½/g,'(1/2)');
}
function exprCompile(src){
  var s=exprPrep(src), i=0, toks=[];
  while(i<s.length){
    var ch=s[i];
    if(/[0-9.]/.test(ch)){ var j=i; while(j<s.length && /[0-9.]/.test(s[j])) j++; toks.push({k:'n',v:parseFloat(s.slice(i,j))}); i=j; continue; }
    if(/[a-zA-Z#]/.test(ch)){ toks.push({k:'v',v:ch}); i++; continue; }
    if('+-*/^()'.indexOf(ch)>=0){ toks.push({k:ch}); i++; continue; }
    return null;
  }
  var out=[];
  for(var t=0;t<toks.length;t++){
    var a=toks[t], b=out[out.length-1];
    if(b && (b.k==='n'||b.k==='v'||b.k===')') && (a.k==='n'||a.k==='v'||a.k==='(')) out.push({k:'&'});
    out.push(a);
  }
  var p=0;
  function peek(){ return out[p]; }
  function parseE(){ var n=parseT(); while(peek() && (peek().k==='+'||peek().k==='-')){ var o=out[p++].k, r=parseT(); n=(function(l,r,o){return function(e){ return o==='+'?l(e)+r(e):l(e)-r(e); };})(n,r,o); } return n; }
  function parseI(){ var n=parseU(); while(peek() && peek().k==='&'){ p++; var r=parseP(); n=(function(l,r){return function(e){ return l(e)*r(e); };})(n,r); } return n; }
  function parseT(){ var n=parseI(); while(peek() && (peek().k==='*'||peek().k==='/')){ var o=out[p++].k, r=parseI(); n=(function(l,r,o){return function(e){ return o==='*'?l(e)*r(e):l(e)/r(e); };})(n,r,o); } return n; }
  function parseU(){ if(peek() && peek().k==='-'){ p++; var u=parseU(); return function(e){ return -u(e); }; } if(peek() && peek().k==='+'){ p++; return parseU(); } return parseP(); }
  function parseP(){ var b=parseA(); if(peek() && peek().k==='^'){ p++; var x=parseU(); return function(e){ return Math.pow(b(e),x(e)); }; } return b; }
  function parseA(){
    var t=out[p++]; if(!t) throw 0;
    if(t.k==='n') return function(){ return t.v; };
    if(t.k==='v') return t.v==='#' ? function(){ return Math.PI; } : function(e){ return e[t.v]; };
    if(t.k==='('){ var n=parseE(); if(!peek()||peek().k!==')') throw 0; p++; return n; }
    throw 0;
  }
  try{ var f=parseE(); if(p!==out.length) return null; return f; }catch(e){ return null; }
}
function exprEqual(input,answer){
  var f=exprCompile(input), g=exprCompile(answer); if(!f||!g) return false;
  var hits=0;
  for(var trial=0;trial<8;trial++){
    var env={}; 'abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ'.split('').forEach(function(c){ env[c]=1.3+Math.random()*4.1; });
    var x=f(env), y=g(env);
    if(!isFinite(x)||!isFinite(y)) continue;
    if(Math.abs(x-y)>1e-7*Math.max(1,Math.abs(x),Math.abs(y))) return false;
    hits++;
  }
  return hits>=3;
}
function wordsNorm(s){ return String(s||'').toLowerCase().replace(/\band\b/g,' ').replace(/[^a-z]/g,''); }
function listNorm(s){ return (String(s||'').replace(/(\d) (?=\d{3}\b)/g,'$1').match(/-?\d+(\.\d+)?/g)||[]).join(','); }
function powNorm(s){ return String(s||'').toLowerCase().replace(/\s+/g,'').replace(/[×∗*·.]/g,'x').replace(/[⁰¹²³⁴⁵⁶⁷⁸⁹]+/g,function(m){ return '^'+m.split('').map(function(c){ return '⁰¹²³⁴⁵⁶⁷⁸⁹'.indexOf(c); }).join(''); }).replace(/\^1(?!\d)/g,''); }
function fr(s){ return String(s).replace(/\{(\d+) (\d+)\/(\d+)\}/g,'<span class="mx">$1<span class="fq"><span>$2</span><span>$3</span></span></span>').replace(/\{(\d+)\/(\d+)\}/g,'<span class="fq"><span>$1</span><span>$2</span></span>'); }
function gcdI(a,b){ a=Math.abs(a); b=Math.abs(b); while(b){ var t=a%b; a=b; b=t; } return a; }
function fracParse(s){ s=String(s===undefined||s===null?'':s).trim().replace(/[\u2044\u2215\u00f7]/g,'/').replace(/\s+/g,' ').replace(/\s*\/\s*/g,'/'); var m;
  if((m=s.match(/^(-?\d+)$/))) return {v:+m[1],form:'int',n:+m[1],d:1};
  if((m=s.match(/^(-?\d+)\/(\d+)$/))){ if(+m[2]===0) return null; return {v:m[1]/m[2],form:'frac',n:+m[1],d:+m[2]}; }
  if((m=s.match(/^(\d+)(?: |\+|-)(\d+)\/(\d+)$/))){ if(+m[3]===0) return null; return {v:+m[1]+m[2]/m[3],form:'mixed',w:+m[1],n:+m[2],d:+m[3]}; }
  if((m=s.match(/^-?\d*\.\d+$/))) return {v:parseFloat(s),form:'dec'};
  return null; }
function fracOK(mode,input,answer){
  if(mode==='flist'){ var A=String(input).split(/[,;]/).map(function(x){return x.trim();}).filter(Boolean), K=String(answer).split(/[,;]/).map(function(x){return x.trim();});
    if(A.length!==K.length) return false; return A.every(function(x,i){ var a=fracParse(x), k=fracParse(K[i]); return a&&k&&Math.abs(a.v-k.v)<1e-9; }); }
  var a=fracParse(input), k=fracParse(answer); if(!a||!k) return false;
  var same=Math.abs(a.v-k.v)<1e-9; if(!same) return false;
  if(mode==='fv') return true;
  if(mode==='dec') return a.form==='dec'||a.form==='int';
  if(mode==='fe') return (a.form==='frac'&&k.form==='frac'&&a.n===k.n&&a.d===k.d)||(a.form==='int'&&k.form==='int');
  if(mode==='fi') return a.form==='frac'||(a.form==='int'&&k.form==='int');
  if(mode==='fl') return a.form==='int'||(a.form==='frac'&&gcdI(a.n,a.d)===1)||(a.form==='mixed'&&a.n<a.d&&gcdI(a.n,a.d)===1);
  if(mode==='fm') return a.form==='int'||(a.form==='mixed'&&a.n>0&&a.n<a.d&&gcdI(a.n,a.d)===1);
  return false; }
function answerMatches(input,answer,accept,expr){
  if(expr==='dec'||expr==='fv'||expr==='fe'||expr==='fl'||expr==='fm'||expr==='fi'||expr==='flist'){ if(input===undefined||input===null||String(input).trim()==='') return false; return fracOK(expr,input,answer); }
  if(input===undefined||input===null||String(input).trim()==='') return false;
  if(expr==='words'){ return [answer].concat(accept||[]).some(function(a){ return wordsNorm(a)===wordsNorm(input); }); }
  if(expr==='list'){ return [answer].concat(accept||[]).some(function(a){ return listNorm(a)===listNorm(input); }); }
  if(expr==='pow'){ return [answer].concat(accept||[]).some(function(a){ return powNorm(a)===powNorm(input); }); }
  if(expr==='time'){ var tn=function(x){ var t=String(x).toLowerCase().replace(/[\s.]/g,'').replace(/[:h]/g,''); if(/^\d{3}(am|pm)?$/.test(t)) t='0'+t; return t; }; return [answer].concat(accept||[]).some(function(a){ return tn(a)===tn(input); }); }
  if(expr==='dlist'){ var dn=function(x){ return (String(x).match(/-?\d*\.?\d+/g)||[]).map(Number).join(','); }; return [answer].concat(accept||[]).some(function(a){ return dn(a)===dn(input); }); }
  if(expr==='set'){ var sn=function(x){ return (String(x).match(/-?\d+/g)||[]).map(Number).sort(function(a,b){return a-b;}).join(','); }; return [answer].concat(accept||[]).some(function(a){ return sn(a)===sn(input); }); }
  if(expr==='primes'){ var pn=function(x){ var t=powNorm(x).replace(/[^0-9x^]/g,''); var out=[]; t.split('x').forEach(function(tok){ if(!tok) return; var m=tok.split('^'); var b=+m[0], e=m[1]?+m[1]:1; for(var i=0;i<e;i++) out.push(b); }); return out.sort(function(a,b){return a-b;}).join(','); }; return [answer].concat(accept||[]).some(function(a){ return pn(a)===pn(input); }); }
  if(expr==='angle'){ var an=function(x){ return String(x).toUpperCase().replace(/[^A-Z]/g,''); }; var k=an(answer), v=an(input); return v===k || v===k.split('').reverse().join(''); }
  if(expr==='expanded'){ var f=function(x){ return String(x).replace(/\s+/g,'').replace(/,/g,''); }; return [answer].concat(accept||[]).some(function(a){ return f(a)===f(input); }); }
  if(expr===true && input!==undefined && input!==null && String(input).trim()!==''){
    if(exprEqual(input,answer)) return true;
    return (accept||[]).some(function(a){ return exprEqual(input,a); });
  }
  if(input===undefined||input===null||String(input).trim()==='') return false;
  var n1=parseNum(input), n2=parseNum(answer);
  if(n1!==null && n2!==null) return Math.abs(n1-n2)<1e-3;
  var cands=[answer].concat(accept||[]); var ni=norm(input);
  for(var i=0;i<cands.length;i++){ if(norm(cands[i])===ni) return true; }
  return false;
}
function esc(s){ return String(s).replace(/&/g,'&amp;').replace(/</g,'&lt;'); }

/* ================= DATA ================= */
var AR_OPTIONS = ["Both A and R are true, and R is the correct explanation of A","Both A and R are true, but R is NOT the correct explanation of A","A is true but R is false","A is false but R is true"];
var SECTIONS = [{"id": "s1", "label": "Ex 12A", "sub": "Percentage", "slides": [{"kind": "blank", "p": "Each pattern has 100 tiles. Write the shaded part as a fraction with denominator 100 and as a percentage.", "tag": "", "marks": "", "flat": [{"t": "a) fraction __B1__/100, percentage __B2__%", "a": {"B1": "23", "B2": "23"}, "fig": "<svg class=\"figsvg\" viewBox=\"0 0 220 220\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"10\" y=\"10\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"30\" y=\"10\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"50\" y=\"10\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"70\" y=\"10\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"90\" y=\"10\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"110\" y=\"10\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"130\" y=\"10\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"150\" y=\"10\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"170\" y=\"10\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"190\" y=\"10\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"10\" y=\"30\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"30\" y=\"30\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"50\" y=\"30\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"70\" y=\"30\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"90\" y=\"30\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"110\" y=\"30\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"130\" y=\"30\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"150\" y=\"30\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"170\" y=\"30\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"190\" y=\"30\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"10\" y=\"50\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"30\" y=\"50\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"50\" y=\"50\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"70\" y=\"50\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"90\" y=\"50\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"110\" y=\"50\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"130\" y=\"50\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"150\" y=\"50\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"170\" y=\"50\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"190\" y=\"50\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"10\" y=\"70\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"30\" y=\"70\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"50\" y=\"70\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"70\" y=\"70\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"90\" y=\"70\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"110\" y=\"70\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"130\" y=\"70\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"150\" y=\"70\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"170\" y=\"70\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"190\" y=\"70\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"10\" y=\"90\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"30\" y=\"90\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"50\" y=\"90\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"70\" y=\"90\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"90\" y=\"90\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"110\" y=\"90\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"130\" y=\"90\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"150\" y=\"90\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"170\" y=\"90\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"190\" y=\"90\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"10\" y=\"110\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"30\" y=\"110\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"50\" y=\"110\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"70\" y=\"110\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"90\" y=\"110\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"110\" y=\"110\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"130\" y=\"110\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"150\" y=\"110\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"170\" y=\"110\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"190\" y=\"110\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"10\" y=\"130\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"30\" y=\"130\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"50\" y=\"130\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"70\" y=\"130\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"90\" y=\"130\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"110\" y=\"130\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"130\" y=\"130\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"150\" y=\"130\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"170\" y=\"130\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"190\" y=\"130\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"10\" y=\"150\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"30\" y=\"150\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"50\" y=\"150\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"70\" y=\"150\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"90\" y=\"150\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"110\" y=\"150\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"130\" y=\"150\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"150\" y=\"150\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"170\" y=\"150\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"190\" y=\"150\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"10\" y=\"170\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"30\" y=\"170\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"50\" y=\"170\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"70\" y=\"170\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"90\" y=\"170\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"110\" y=\"170\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"130\" y=\"170\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"150\" y=\"170\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"170\" y=\"170\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"190\" y=\"170\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"10\" y=\"190\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"30\" y=\"190\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"50\" y=\"190\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"70\" y=\"190\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"90\" y=\"190\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"110\" y=\"190\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"130\" y=\"190\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"150\" y=\"190\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"170\" y=\"190\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"190\" y=\"190\" width=\"20\" height=\"20\"/></svg>"}, {"t": "b) fraction __B1__/100, percentage __B2__%", "a": {"B1": "48", "B2": "48"}, "fig": "<svg class=\"figsvg\" viewBox=\"0 0 220 220\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"10\" y=\"10\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"30\" y=\"10\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"50\" y=\"10\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"70\" y=\"10\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"90\" y=\"10\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"110\" y=\"10\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"130\" y=\"10\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"150\" y=\"10\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"170\" y=\"10\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"190\" y=\"10\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"10\" y=\"30\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"30\" y=\"30\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"50\" y=\"30\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"70\" y=\"30\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"90\" y=\"30\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"110\" y=\"30\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"130\" y=\"30\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"150\" y=\"30\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"170\" y=\"30\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"190\" y=\"30\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"10\" y=\"50\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"30\" y=\"50\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"50\" y=\"50\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"70\" y=\"50\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"90\" y=\"50\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"110\" y=\"50\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"130\" y=\"50\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"150\" y=\"50\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"170\" y=\"50\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"190\" y=\"50\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"10\" y=\"70\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"30\" y=\"70\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"50\" y=\"70\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"70\" y=\"70\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"90\" y=\"70\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"110\" y=\"70\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"130\" y=\"70\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"150\" y=\"70\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"170\" y=\"70\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"190\" y=\"70\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"10\" y=\"90\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"30\" y=\"90\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"50\" y=\"90\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"70\" y=\"90\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"90\" y=\"90\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"110\" y=\"90\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"130\" y=\"90\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"150\" y=\"90\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"170\" y=\"90\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"190\" y=\"90\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"10\" y=\"110\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"30\" y=\"110\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"50\" y=\"110\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"70\" y=\"110\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"90\" y=\"110\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"110\" y=\"110\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"130\" y=\"110\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"150\" y=\"110\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"170\" y=\"110\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"190\" y=\"110\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"10\" y=\"130\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"30\" y=\"130\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"50\" y=\"130\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"70\" y=\"130\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"90\" y=\"130\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"110\" y=\"130\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"130\" y=\"130\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"150\" y=\"130\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"170\" y=\"130\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"190\" y=\"130\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"10\" y=\"150\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"30\" y=\"150\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"50\" y=\"150\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"70\" y=\"150\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"90\" y=\"150\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"110\" y=\"150\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"130\" y=\"150\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"150\" y=\"150\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"170\" y=\"150\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"190\" y=\"150\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"10\" y=\"170\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"30\" y=\"170\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"50\" y=\"170\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"70\" y=\"170\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"90\" y=\"170\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"110\" y=\"170\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"130\" y=\"170\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"150\" y=\"170\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"170\" y=\"170\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"190\" y=\"170\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"10\" y=\"190\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"30\" y=\"190\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"50\" y=\"190\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"70\" y=\"190\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"90\" y=\"190\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"110\" y=\"190\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"130\" y=\"190\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"150\" y=\"190\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"170\" y=\"190\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"190\" y=\"190\" width=\"20\" height=\"20\"/></svg>"}, {"t": "c) fraction __B1__/100, percentage __B2__%", "a": {"B1": "70", "B2": "70"}, "fig": "<svg class=\"figsvg\" viewBox=\"0 0 220 220\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"10\" y=\"10\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"30\" y=\"10\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"50\" y=\"10\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"70\" y=\"10\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"90\" y=\"10\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"110\" y=\"10\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"130\" y=\"10\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"150\" y=\"10\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"170\" y=\"10\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"190\" y=\"10\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"10\" y=\"30\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"30\" y=\"30\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"50\" y=\"30\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"70\" y=\"30\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"90\" y=\"30\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"110\" y=\"30\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"130\" y=\"30\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"150\" y=\"30\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"170\" y=\"30\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"190\" y=\"30\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"10\" y=\"50\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"30\" y=\"50\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"50\" y=\"50\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"70\" y=\"50\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"90\" y=\"50\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"110\" y=\"50\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"130\" y=\"50\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"150\" y=\"50\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"170\" y=\"50\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"190\" y=\"50\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"10\" y=\"70\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"30\" y=\"70\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"50\" y=\"70\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"70\" y=\"70\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"90\" y=\"70\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"110\" y=\"70\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"130\" y=\"70\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"150\" y=\"70\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"170\" y=\"70\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"190\" y=\"70\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"10\" y=\"90\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"30\" y=\"90\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"50\" y=\"90\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"70\" y=\"90\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"90\" y=\"90\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"110\" y=\"90\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"130\" y=\"90\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"150\" y=\"90\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"170\" y=\"90\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"190\" y=\"90\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"10\" y=\"110\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"30\" y=\"110\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"50\" y=\"110\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"70\" y=\"110\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"90\" y=\"110\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"110\" y=\"110\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"130\" y=\"110\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"150\" y=\"110\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"170\" y=\"110\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"190\" y=\"110\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"10\" y=\"130\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"30\" y=\"130\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"50\" y=\"130\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"70\" y=\"130\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"90\" y=\"130\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"110\" y=\"130\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"130\" y=\"130\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"150\" y=\"130\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"170\" y=\"130\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"190\" y=\"130\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"10\" y=\"150\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"30\" y=\"150\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"50\" y=\"150\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"70\" y=\"150\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"90\" y=\"150\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"110\" y=\"150\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"130\" y=\"150\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"150\" y=\"150\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"170\" y=\"150\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"190\" y=\"150\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"10\" y=\"170\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"30\" y=\"170\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"50\" y=\"170\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"70\" y=\"170\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"90\" y=\"170\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"110\" y=\"170\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"130\" y=\"170\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"150\" y=\"170\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"170\" y=\"170\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"190\" y=\"170\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"10\" y=\"190\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"30\" y=\"190\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"50\" y=\"190\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"70\" y=\"190\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"90\" y=\"190\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"110\" y=\"190\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"130\" y=\"190\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"150\" y=\"190\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"170\" y=\"190\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"190\" y=\"190\" width=\"20\" height=\"20\"/></svg>"}, {"t": "d) fraction __B1__/100, percentage __B2__%", "a": {"B1": "6", "B2": "6"}, "fig": "<svg class=\"figsvg\" viewBox=\"0 0 220 220\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"10\" y=\"10\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"30\" y=\"10\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"50\" y=\"10\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"70\" y=\"10\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"90\" y=\"10\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"110\" y=\"10\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"130\" y=\"10\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"150\" y=\"10\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"170\" y=\"10\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"190\" y=\"10\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"10\" y=\"30\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"30\" y=\"30\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"50\" y=\"30\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"70\" y=\"30\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"90\" y=\"30\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"110\" y=\"30\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"130\" y=\"30\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"150\" y=\"30\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"170\" y=\"30\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"190\" y=\"30\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"10\" y=\"50\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"30\" y=\"50\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"50\" y=\"50\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"70\" y=\"50\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"90\" y=\"50\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"110\" y=\"50\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"130\" y=\"50\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"150\" y=\"50\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"170\" y=\"50\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"190\" y=\"50\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"10\" y=\"70\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"30\" y=\"70\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"50\" y=\"70\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"70\" y=\"70\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"90\" y=\"70\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"110\" y=\"70\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"130\" y=\"70\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"150\" y=\"70\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"170\" y=\"70\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"190\" y=\"70\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"10\" y=\"90\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"30\" y=\"90\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"50\" y=\"90\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"70\" y=\"90\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"90\" y=\"90\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"110\" y=\"90\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"130\" y=\"90\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"150\" y=\"90\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"170\" y=\"90\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"190\" y=\"90\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"10\" y=\"110\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"30\" y=\"110\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"50\" y=\"110\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"70\" y=\"110\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"90\" y=\"110\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"110\" y=\"110\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"130\" y=\"110\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"150\" y=\"110\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"170\" y=\"110\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"190\" y=\"110\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"10\" y=\"130\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"30\" y=\"130\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"50\" y=\"130\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"70\" y=\"130\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"90\" y=\"130\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"110\" y=\"130\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"130\" y=\"130\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"150\" y=\"130\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"170\" y=\"130\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"190\" y=\"130\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"10\" y=\"150\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"30\" y=\"150\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"50\" y=\"150\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"70\" y=\"150\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"90\" y=\"150\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"110\" y=\"150\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"130\" y=\"150\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"150\" y=\"150\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"170\" y=\"150\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"190\" y=\"150\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"10\" y=\"170\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"30\" y=\"170\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"50\" y=\"170\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"70\" y=\"170\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"90\" y=\"170\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"110\" y=\"170\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"130\" y=\"170\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"150\" y=\"170\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"170\" y=\"170\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"190\" y=\"170\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"10\" y=\"190\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"30\" y=\"190\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"50\" y=\"190\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"70\" y=\"190\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"90\" y=\"190\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"110\" y=\"190\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"130\" y=\"190\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"150\" y=\"190\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"170\" y=\"190\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"190\" y=\"190\" width=\"20\" height=\"20\"/></svg>"}], "sol": "Count the shaded tiles out of 100: that number is the percentage.\na) {23/100} = 23%\nb) {48/100} = 48%\nc) {70/100} = 70%\nd) {6/100} = 6%"}, {"kind": "blank", "p": "Estimate the percentage of each bar that is shaded:", "tag": "", "marks": "", "flat": [{"t": "a) __B1__%", "a": {"B1": "40"}, "fig": "<svg class=\"figsvg\" viewBox=\"0 0 300 64\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><rect class=\"cell\" style=\"stroke:var(--ink)\" x=\"20\" y=\"8\" width=\"260\" height=\"24\"/><rect class=\"shd\" x=\"20\" y=\"8\" width=\"104.0\" height=\"24\"/><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:.8\" x1=\"20.0\" y1=\"8\" x2=\"20.0\" y2=\"32\"/><text class=\"po\" x=\"20.0\" y=\"46.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">0</text><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:.8\" x1=\"46.0\" y1=\"8\" x2=\"46.0\" y2=\"32\"/><text class=\"po\" x=\"46.0\" y=\"46.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">10</text><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:.8\" x1=\"72.0\" y1=\"8\" x2=\"72.0\" y2=\"32\"/><text class=\"po\" x=\"72.0\" y=\"46.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">20</text><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:.8\" x1=\"98.0\" y1=\"8\" x2=\"98.0\" y2=\"32\"/><text class=\"po\" x=\"98.0\" y=\"46.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">30</text><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:.8\" x1=\"124.0\" y1=\"8\" x2=\"124.0\" y2=\"32\"/><text class=\"po\" x=\"124.0\" y=\"46.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">40</text><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:.8\" x1=\"150.0\" y1=\"8\" x2=\"150.0\" y2=\"32\"/><text class=\"po\" x=\"150.0\" y=\"46.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">50</text><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:.8\" x1=\"176.0\" y1=\"8\" x2=\"176.0\" y2=\"32\"/><text class=\"po\" x=\"176.0\" y=\"46.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">60</text><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:.8\" x1=\"202.0\" y1=\"8\" x2=\"202.0\" y2=\"32\"/><text class=\"po\" x=\"202.0\" y=\"46.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">70</text><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:.8\" x1=\"228.0\" y1=\"8\" x2=\"228.0\" y2=\"32\"/><text class=\"po\" x=\"228.0\" y=\"46.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">80</text><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:.8\" x1=\"254.0\" y1=\"8\" x2=\"254.0\" y2=\"32\"/><text class=\"po\" x=\"254.0\" y=\"46.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">90</text><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:.8\" x1=\"280.0\" y1=\"8\" x2=\"280.0\" y2=\"32\"/><text class=\"po\" x=\"280.0\" y=\"46.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">100</text></svg>", "expr": "dec"}, {"t": "b) __B1__%", "a": {"B1": "75"}, "fig": "<svg class=\"figsvg\" viewBox=\"0 0 300 64\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><rect class=\"cell\" style=\"stroke:var(--ink)\" x=\"20\" y=\"8\" width=\"260\" height=\"24\"/><rect class=\"shd\" x=\"20\" y=\"8\" width=\"195.0\" height=\"24\"/><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:.8\" x1=\"20.0\" y1=\"8\" x2=\"20.0\" y2=\"32\"/><text class=\"po\" x=\"20.0\" y=\"46.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">0</text><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:.8\" x1=\"46.0\" y1=\"8\" x2=\"46.0\" y2=\"32\"/><text class=\"po\" x=\"46.0\" y=\"46.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">10</text><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:.8\" x1=\"72.0\" y1=\"8\" x2=\"72.0\" y2=\"32\"/><text class=\"po\" x=\"72.0\" y=\"46.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">20</text><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:.8\" x1=\"98.0\" y1=\"8\" x2=\"98.0\" y2=\"32\"/><text class=\"po\" x=\"98.0\" y=\"46.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">30</text><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:.8\" x1=\"124.0\" y1=\"8\" x2=\"124.0\" y2=\"32\"/><text class=\"po\" x=\"124.0\" y=\"46.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">40</text><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:.8\" x1=\"150.0\" y1=\"8\" x2=\"150.0\" y2=\"32\"/><text class=\"po\" x=\"150.0\" y=\"46.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">50</text><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:.8\" x1=\"176.0\" y1=\"8\" x2=\"176.0\" y2=\"32\"/><text class=\"po\" x=\"176.0\" y=\"46.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">60</text><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:.8\" x1=\"202.0\" y1=\"8\" x2=\"202.0\" y2=\"32\"/><text class=\"po\" x=\"202.0\" y=\"46.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">70</text><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:.8\" x1=\"228.0\" y1=\"8\" x2=\"228.0\" y2=\"32\"/><text class=\"po\" x=\"228.0\" y=\"46.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">80</text><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:.8\" x1=\"254.0\" y1=\"8\" x2=\"254.0\" y2=\"32\"/><text class=\"po\" x=\"254.0\" y=\"46.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">90</text><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:.8\" x1=\"280.0\" y1=\"8\" x2=\"280.0\" y2=\"32\"/><text class=\"po\" x=\"280.0\" y=\"46.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">100</text></svg>", "expr": "dec"}, {"t": "c) __B1__%", "a": {"B1": "15"}, "fig": "<svg class=\"figsvg\" viewBox=\"0 0 300 64\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><rect class=\"cell\" style=\"stroke:var(--ink)\" x=\"20\" y=\"8\" width=\"260\" height=\"24\"/><rect class=\"shd\" x=\"20\" y=\"8\" width=\"39.0\" height=\"24\"/><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:.8\" x1=\"20.0\" y1=\"8\" x2=\"20.0\" y2=\"32\"/><text class=\"po\" x=\"20.0\" y=\"46.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">0</text><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:.8\" x1=\"46.0\" y1=\"8\" x2=\"46.0\" y2=\"32\"/><text class=\"po\" x=\"46.0\" y=\"46.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">10</text><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:.8\" x1=\"72.0\" y1=\"8\" x2=\"72.0\" y2=\"32\"/><text class=\"po\" x=\"72.0\" y=\"46.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">20</text><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:.8\" x1=\"98.0\" y1=\"8\" x2=\"98.0\" y2=\"32\"/><text class=\"po\" x=\"98.0\" y=\"46.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">30</text><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:.8\" x1=\"124.0\" y1=\"8\" x2=\"124.0\" y2=\"32\"/><text class=\"po\" x=\"124.0\" y=\"46.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">40</text><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:.8\" x1=\"150.0\" y1=\"8\" x2=\"150.0\" y2=\"32\"/><text class=\"po\" x=\"150.0\" y=\"46.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">50</text><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:.8\" x1=\"176.0\" y1=\"8\" x2=\"176.0\" y2=\"32\"/><text class=\"po\" x=\"176.0\" y=\"46.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">60</text><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:.8\" x1=\"202.0\" y1=\"8\" x2=\"202.0\" y2=\"32\"/><text class=\"po\" x=\"202.0\" y=\"46.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">70</text><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:.8\" x1=\"228.0\" y1=\"8\" x2=\"228.0\" y2=\"32\"/><text class=\"po\" x=\"228.0\" y=\"46.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">80</text><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:.8\" x1=\"254.0\" y1=\"8\" x2=\"254.0\" y2=\"32\"/><text class=\"po\" x=\"254.0\" y=\"46.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">90</text><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:.8\" x1=\"280.0\" y1=\"8\" x2=\"280.0\" y2=\"32\"/><text class=\"po\" x=\"280.0\" y=\"46.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">100</text></svg>", "expr": "dec"}], "sol": "Read where the shading ends on the scale.\na) 40%\nb) 75%\nc) 15%"}, {"kind": "blank", "p": "Waste thrown away by a city: food and garden 44%, paper 17%, plastic 12%, glass 5%, metal 5%, wood 2%, rubber and leather 2%, other 13%.", "tag": "", "marks": "", "flat": [{"t": "a) What percentage is either wood or metal? __B1__%", "a": {"B1": "7"}, "expr": "dec"}, {"t": "b) Which is greater, plastic or glass? __B1__", "a": {"B1": "plastic"}}, {"t": "c) The sum of all the percentages is __B1__%", "a": {"B1": "100"}, "expr": "dec"}], "sol": "a) 2 + 5 = 7%\nb) plastic (12% > 5%)\nc) 100%: together they make the whole"}]}, {"id": "s2", "label": "Ex 12B", "sub": "Percentages to fractions", "slides": [{"kind": "blank", "p": "Write as a fraction with denominator 100:", "tag": "", "marks": "", "flat": [{"t": "a) 59% = __B1__", "a": {"B1": "59/100"}, "expr": "fe"}, {"t": "b) 13% = __B1__", "a": {"B1": "13/100"}, "expr": "fe"}, {"t": "c) 3% = __B1__", "a": {"B1": "3/100"}, "expr": "fe"}, {"t": "d) 97% = __B1__", "a": {"B1": "97/100"}, "expr": "fe"}], "sol": "x% = {x/100}"}, {"kind": "blank", "p": "Write as a fraction in lowest terms:", "tag": "", "marks": "", "flat": [{"t": "a) 10% = __B1__", "a": {"B1": "1/10"}, "expr": "fl"}, {"t": "b) 50% = __B1__", "a": {"B1": "1/2"}, "expr": "fl"}, {"t": "c) 90% = __B1__", "a": {"B1": "9/10"}, "expr": "fl"}, {"t": "d) 5% = __B1__", "a": {"B1": "1/20"}, "expr": "fl"}, {"t": "e) 22% = __B1__", "a": {"B1": "11/50"}, "expr": "fl"}, {"t": "f) 74% = __B1__", "a": {"B1": "37/50"}, "expr": "fl"}, {"t": "g) 15% = __B1__", "a": {"B1": "3/20"}, "expr": "fl"}, {"t": "h) 65% = __B1__", "a": {"B1": "13/20"}, "expr": "fl"}, {"t": "i) 25% = __B1__", "a": {"B1": "1/4"}, "expr": "fl"}, {"t": "j) 80% = __B1__", "a": {"B1": "4/5"}, "expr": "fl"}, {"t": "k) 35% = __B1__", "a": {"B1": "7/20"}, "expr": "fl"}, {"t": "l) 75% = __B1__", "a": {"B1": "3/4"}, "expr": "fl"}, {"t": "m) 4% = __B1__", "a": {"B1": "1/25"}, "expr": "fl"}, {"t": "n) 48% = __B1__", "a": {"B1": "12/25"}, "expr": "fl"}, {"t": "o) 56% = __B1__", "a": {"B1": "14/25"}, "expr": "fl"}, {"t": "p) 64% = __B1__", "a": {"B1": "16/25"}, "expr": "fl"}], "sol": "Write over 100, then divide top and bottom by the HCF.\na) {10/100} = {1/10}\nb) {50/100} = {1/2}\nc) {90/100} = {9/10}\nd) {5/100} = {1/20}\ne) {22/100} = {11/50}\nf) {74/100} = {37/50}\ng) {15/100} = {3/20}\nh) {65/100} = {13/20}\ni) {25/100} = {1/4}\nj) {80/100} = {4/5}\nk) {35/100} = {7/20}\nl) {75/100} = {3/4}\nm) {4/100} = {1/25}\nn) {48/100} = {12/25}\no) {56/100} = {14/25}\np) {64/100} = {16/25}"}]}, {"id": "s3", "label": "Ex 12C", "sub": "Fractions to percentages", "slides": [{"kind": "blank", "p": "Write as a percentage:", "tag": "", "marks": "", "flat": [{"t": "a) {21/100} = __B1__%", "a": {"B1": "21"}, "expr": "dec"}, {"t": "b) {53/100} = __B1__%", "a": {"B1": "53"}, "expr": "dec"}, {"t": "c) {8/100} = __B1__%", "a": {"B1": "8"}, "expr": "dec"}, {"t": "d) {3/10} = __B1__%", "a": {"B1": "30"}, "expr": "dec"}, {"t": "e) {7/10} = __B1__%", "a": {"B1": "70"}, "expr": "dec"}, {"t": "f) {0/10} = __B1__%", "a": {"B1": "0"}, "expr": "dec"}, {"t": "g) {10/10} = __B1__%", "a": {"B1": "100"}, "expr": "dec"}], "sol": "Write with denominator 100; the numerator is the percentage.\na) 21%\nb) 53%\nc) 8%\nd) 30%\ne) 70%\nf) 0%\ng) 100%"}, {"kind": "blank", "p": "Write as a percentage:", "tag": "", "marks": "", "flat": [{"t": "a) {1/2} = __B1__%", "a": {"B1": "50"}, "expr": "dec"}, {"t": "b) {13/50} = __B1__%", "a": {"B1": "26"}, "expr": "dec"}, {"t": "c) {1/5} = __B1__%", "a": {"B1": "20"}, "expr": "dec"}, {"t": "d) {41/50} = __B1__%", "a": {"B1": "82"}, "expr": "dec"}, {"t": "e) {3/20} = __B1__%", "a": {"B1": "15"}, "expr": "dec"}, {"t": "f) {3/5} = __B1__%", "a": {"B1": "60"}, "expr": "dec"}, {"t": "g) {7/25} = __B1__%", "a": {"B1": "28"}, "expr": "dec"}, {"t": "h) {19/20} = __B1__%", "a": {"B1": "95"}, "expr": "dec"}, {"t": "i) {12/25} = __B1__%", "a": {"B1": "48"}, "expr": "dec"}, {"t": "j) {19/25} = __B1__%", "a": {"B1": "76"}, "expr": "dec"}], "sol": "Multiply top and bottom to make the denominator 100 (e.g. {3/20} = {15/100} = 15%).\na) 50%\nb) 26%\nc) 20%\nd) 82%\ne) 15%\nf) 60%\ng) 28%\nh) 95%\ni) 48%\nj) 76%"}, {"kind": "blank", "p": "Write as a percentage:", "tag": "", "marks": "", "flat": [{"t": "a) {29/200} = __B1__%", "a": {"B1": "14.5"}, "expr": "dec"}, {"t": "b) {231/1000} = __B1__%", "a": {"B1": "23.1"}, "expr": "dec"}, {"t": "c) {759/1000} = __B1__%", "a": {"B1": "75.9"}, "expr": "dec"}, {"t": "d) {103/500} = __B1__%", "a": {"B1": "20.6"}, "expr": "dec"}], "sol": "Change the denominator to 100 (divide by 2, 10 or 5), which may give a decimal percentage.\na) 14.5%\nb) 23.1%\nc) 75.9%\nd) 20.6%"}, {"kind": "blank", "p": "Complete these patterns:", "tag": "", "marks": "", "flat": [{"t": "a) {2/5} = __B1__%", "a": {"B1": "40"}, "expr": "dec"}, {"t": "b) {3/5} = __B1__%", "a": {"B1": "60"}, "expr": "dec"}, {"t": "c) {4/5} = __B1__%", "a": {"B1": "80"}, "expr": "dec"}, {"t": "d) {2/4} = __B1__%", "a": {"B1": "50"}, "expr": "dec"}, {"t": "e) {3/4} = __B1__%", "a": {"B1": "75"}, "expr": "dec"}, {"t": "f) {1/8} = __B1__%", "a": {"B1": "12.5"}, "expr": "dec"}, {"t": "g) {1/16} = __B1__%", "a": {"B1": "6.25"}, "expr": "dec"}], "sol": "Each fifth is 20%, each quarter is 25%, and halving the fraction halves the percentage.\na) 40%\nb) 60%\nc) 80%\nd) 50%\ne) 75%\nf) 12.5%\ng) 6.25%"}, {"kind": "blank", "p": "Write 2 as a percentage:", "tag": "", "marks": "", "flat": [{"t": "__B1__%", "a": {"B1": "200"}, "expr": "dec"}], "sol": "2 = {200/100} = 200%"}]}, {"id": "s4", "label": "Ex 12D", "sub": "Percentages to decimals", "slides": [{"kind": "blank", "p": "Write as a decimal:", "tag": "", "marks": "", "flat": [{"t": "a) 10% = __B1__", "a": {"B1": "0.1"}, "expr": "dec"}, {"t": "b) 50% = __B1__", "a": {"B1": "0.5"}, "expr": "dec"}, {"t": "c) 25% = __B1__", "a": {"B1": "0.25"}, "expr": "dec"}, {"t": "d) 5% = __B1__", "a": {"B1": "0.05"}, "expr": "dec"}, {"t": "e) 33% = __B1__", "a": {"B1": "0.33"}, "expr": "dec"}, {"t": "f) 57% = __B1__", "a": {"B1": "0.57"}, "expr": "dec"}, {"t": "g) 94% = __B1__", "a": {"B1": "0.94"}, "expr": "dec"}, {"t": "h) 6% = __B1__", "a": {"B1": "0.06"}, "expr": "dec"}, {"t": "i) 40% = __B1__", "a": {"B1": "0.4"}, "expr": "dec"}, {"t": "j) 11% = __B1__", "a": {"B1": "0.11"}, "expr": "dec"}, {"t": "k) 1% = __B1__", "a": {"B1": "0.01"}, "expr": "dec"}, {"t": "l) 90% = __B1__", "a": {"B1": "0.9"}, "expr": "dec"}], "sol": "Divide by 100: move the decimal point two places left."}, {"kind": "blank", "p": "Write as a decimal:", "tag": "", "marks": "", "flat": [{"t": "a) 17.5% = __B1__", "a": {"B1": "0.175"}, "expr": "dec"}, {"t": "b) 81.6% = __B1__", "a": {"B1": "0.816"}, "expr": "dec"}, {"t": "c) 60.7% = __B1__", "a": {"B1": "0.607"}, "expr": "dec"}, {"t": "d) 9.4% = __B1__", "a": {"B1": "0.094"}, "expr": "dec"}, {"t": "e) 3.9% = __B1__", "a": {"B1": "0.039"}, "expr": "dec"}, {"t": "f) 4.3% = __B1__", "a": {"B1": "0.043"}, "expr": "dec"}, {"t": "g) 1.7% = __B1__", "a": {"B1": "0.017"}, "expr": "dec"}, {"t": "h) 0.8% = __B1__", "a": {"B1": "0.008"}, "expr": "dec"}], "sol": "Divide by 100.\na) 0.175\nb) 0.816\nc) 0.607\nd) 0.094\ne) 0.039\nf) 0.043\ng) 0.017\nh) 0.008"}, {"kind": "blank", "p": "Write each percentage as a decimal, and as a fraction in lowest terms:", "tag": "", "marks": "", "flat": [{"t": "a) 71% as a decimal: __B1__", "a": {"B1": "0.71"}, "expr": "dec"}, {"t": "a) 71% as a fraction: __B1__", "a": {"B1": "71/100"}, "expr": "fl"}, {"t": "b) 30% as a decimal: __B1__", "a": {"B1": "0.3"}, "expr": "dec"}, {"t": "b) 30% as a fraction: __B1__", "a": {"B1": "3/10"}, "expr": "fl"}, {"t": "c) 55% as a decimal: __B1__", "a": {"B1": "0.55"}, "expr": "dec"}, {"t": "c) 55% as a fraction: __B1__", "a": {"B1": "11/20"}, "expr": "fl"}, {"t": "d) 6% as a decimal: __B1__", "a": {"B1": "0.06"}, "expr": "dec"}, {"t": "d) 6% as a fraction: __B1__", "a": {"B1": "3/50"}, "expr": "fl"}, {"t": "e) 28% as a decimal: __B1__", "a": {"B1": "0.28"}, "expr": "dec"}, {"t": "e) 28% as a fraction: __B1__", "a": {"B1": "7/25"}, "expr": "fl"}], "sol": "Divide by 100 for the decimal; write over 100 and simplify for the fraction.\na) 0.71, {71/100}\nb) 0.3, {3/10}\nc) 0.55, {11/20}\nd) 0.06, {3/50}\ne) 0.28, {7/25}"}]}, {"id": "s5", "label": "Ex 12E", "sub": "Decimals to percentages", "slides": [{"kind": "blank", "p": "Write as a percentage:", "tag": "", "marks": "", "flat": [{"t": "a) 0.37 = __B1__%", "a": {"B1": "37"}, "expr": "dec"}, {"t": "b) 0.89 = __B1__%", "a": {"B1": "89"}, "expr": "dec"}, {"t": "c) 0.15 = __B1__%", "a": {"B1": "15"}, "expr": "dec"}, {"t": "d) 0.49 = __B1__%", "a": {"B1": "49"}, "expr": "dec"}, {"t": "e) 0.73 = __B1__%", "a": {"B1": "73"}, "expr": "dec"}, {"t": "f) 0.11 = __B1__%", "a": {"B1": "11"}, "expr": "dec"}, {"t": "g) 0.05 = __B1__%", "a": {"B1": "5"}, "expr": "dec"}, {"t": "h) 0.02 = __B1__%", "a": {"B1": "2"}, "expr": "dec"}, {"t": "i) 0.2 = __B1__%", "a": {"B1": "20"}, "expr": "dec"}, {"t": "j) 0.7 = __B1__%", "a": {"B1": "70"}, "expr": "dec"}, {"t": "k) 0.9 = __B1__%", "a": {"B1": "90"}, "expr": "dec"}, {"t": "l) 0.4 = __B1__%", "a": {"B1": "40"}, "expr": "dec"}, {"t": "m) 0.074 = __B1__%", "a": {"B1": "7.4"}, "expr": "dec"}, {"t": "n) 0.739 = __B1__%", "a": {"B1": "73.9"}, "expr": "dec"}, {"t": "o) 0.086 = __B1__%", "a": {"B1": "8.6"}, "expr": "dec"}, {"t": "p) 0.001 = __B1__%", "a": {"B1": "0.1"}, "expr": "dec"}], "sol": "Multiply by 100: move the decimal point two places right.\na) 37%\nb) 89%\nc) 15%\nd) 49%\ne) 73%\nf) 11%\ng) 5%\nh) 2%\ni) 20%\nj) 70%\nk) 90%\nl) 40%\nm) 7.4%\nn) 73.9%\no) 8.6%\np) 0.1%"}, {"kind": "blank", "p": "Complete the table:", "tag": "", "marks": "", "flat": [{"t": "a) 20% as a decimal: __B1__", "a": {"B1": "0.2"}, "expr": "dec"}, {"t": "b) 40% as a fraction in lowest terms: __B1__", "a": {"B1": "2/5"}, "expr": "fl"}, {"t": "c) 0.25 as a percentage: __B1__%", "a": {"B1": "25"}, "expr": "dec"}, {"t": "d) 3/4 as a percentage: __B1__%", "a": {"B1": "75"}, "expr": "dec"}, {"t": "e) 0.85 as a percentage: __B1__%", "a": {"B1": "85"}, "expr": "dec"}, {"t": "f) 2/25 as a decimal: __B1__", "a": {"B1": "0.08"}, "expr": "dec"}, {"t": "g) 84% as a fraction in lowest terms: __B1__", "a": {"B1": "21/25"}, "expr": "fl"}, {"t": "h) 3/20 as a percentage: __B1__%", "a": {"B1": "15"}, "expr": "dec"}], "sol": "a) 0.2\nb) {2/5}\nc) 25%\nd) 75%\ne) 85%\nf) {8/100} = 0.08\ng) {84/100} = {21/25}\nh) 15%"}]}, {"id": "s6", "label": "Ex 12F", "sub": "Number lines", "slides": [{"kind": "blank", "p": "Write each value shown on the number line as a percentage:", "tag": "", "marks": "", "flat": [{"t": "a) A = __B1__%", "a": {"B1": "15"}, "expr": "dec"}, {"t": "b) B = __B1__%", "a": {"B1": "45"}, "expr": "dec"}, {"t": "c) C = __B1__%", "a": {"B1": "75"}, "expr": "dec"}, {"t": "d) D = __B1__%", "a": {"B1": "95"}, "expr": "dec"}], "sol": "Read the position between the 10% marks.\nA 15%, B 45%, C 75%, D 95%", "fig": "<svg class=\"figsvg\" viewBox=\"0 0 300 70\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><line class=\"ln\" x1=\"10.0\" y1=\"34.0\" x2=\"290.0\" y2=\"34.0\" marker-end=\"url(#ah)\" marker-start=\"url(#ahs)\"/><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:1\" x1=\"20.0\" y1=\"28\" x2=\"20.0\" y2=\"40\"/><text class=\"po\" x=\"20.0\" y=\"54.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">0%</text><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:0.7\" x1=\"33.0\" y1=\"30\" x2=\"33.0\" y2=\"38\"/><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:1\" x1=\"46.0\" y1=\"28\" x2=\"46.0\" y2=\"40\"/><text class=\"po\" x=\"46.0\" y=\"54.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">10%</text><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:0.7\" x1=\"59.0\" y1=\"30\" x2=\"59.0\" y2=\"38\"/><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:1\" x1=\"72.0\" y1=\"28\" x2=\"72.0\" y2=\"40\"/><text class=\"po\" x=\"72.0\" y=\"54.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">20%</text><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:0.7\" x1=\"85.0\" y1=\"30\" x2=\"85.0\" y2=\"38\"/><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:1\" x1=\"98.0\" y1=\"28\" x2=\"98.0\" y2=\"40\"/><text class=\"po\" x=\"98.0\" y=\"54.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">30%</text><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:0.7\" x1=\"111.0\" y1=\"30\" x2=\"111.0\" y2=\"38\"/><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:1\" x1=\"124.0\" y1=\"28\" x2=\"124.0\" y2=\"40\"/><text class=\"po\" x=\"124.0\" y=\"54.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">40%</text><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:0.7\" x1=\"137.0\" y1=\"30\" x2=\"137.0\" y2=\"38\"/><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:1\" x1=\"150.0\" y1=\"28\" x2=\"150.0\" y2=\"40\"/><text class=\"po\" x=\"150.0\" y=\"54.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">50%</text><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:0.7\" x1=\"163.0\" y1=\"30\" x2=\"163.0\" y2=\"38\"/><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:1\" x1=\"176.0\" y1=\"28\" x2=\"176.0\" y2=\"40\"/><text class=\"po\" x=\"176.0\" y=\"54.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">60%</text><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:0.7\" x1=\"189.0\" y1=\"30\" x2=\"189.0\" y2=\"38\"/><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:1\" x1=\"202.0\" y1=\"28\" x2=\"202.0\" y2=\"40\"/><text class=\"po\" x=\"202.0\" y=\"54.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">70%</text><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:0.7\" x1=\"215.0\" y1=\"30\" x2=\"215.0\" y2=\"38\"/><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:1\" x1=\"228.0\" y1=\"28\" x2=\"228.0\" y2=\"40\"/><text class=\"po\" x=\"228.0\" y=\"54.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">80%</text><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:0.7\" x1=\"241.0\" y1=\"30\" x2=\"241.0\" y2=\"38\"/><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:1\" x1=\"254.0\" y1=\"28\" x2=\"254.0\" y2=\"40\"/><text class=\"po\" x=\"254.0\" y=\"54.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">90%</text><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:0.7\" x1=\"267.0\" y1=\"30\" x2=\"267.0\" y2=\"38\"/><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:1\" x1=\"280.0\" y1=\"28\" x2=\"280.0\" y2=\"40\"/><text class=\"po\" x=\"280.0\" y=\"54.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">100%</text><circle class=\"dr\" cx=\"59.0\" cy=\"34\" r=\"4.5\"/><text class=\"al\" x=\"59.0\" y=\"20.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">A</text><circle class=\"dr\" cx=\"137.0\" cy=\"34\" r=\"4.5\"/><text class=\"al\" x=\"137.0\" y=\"20.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">B</text><circle class=\"dr\" cx=\"215.0\" cy=\"34\" r=\"4.5\"/><text class=\"al\" x=\"215.0\" y=\"20.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">C</text><circle class=\"dr\" cx=\"267.0\" cy=\"34\" r=\"4.5\"/><text class=\"al\" x=\"267.0\" y=\"20.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">D</text></svg>"}, {"kind": "blank", "p": "Write each number as a percentage, then write the original numbers in ascending order:", "tag": "", "marks": "", "flat": [{"t": "a) 3/5 = __B1__%", "a": {"B1": "60"}, "expr": "dec"}, {"t": "b) 0.65 = __B1__%", "a": {"B1": "65"}, "expr": "dec"}, {"t": "c) 9/20 = __B1__%", "a": {"B1": "45"}, "expr": "dec"}, {"t": "d) Write 3/5, 70%, 0.65 and 9/20 as percentages in ascending order (e.g. 10, 20): __B1__", "a": {"B1": "45, 60, 65, 70"}, "expr": "dlist"}], "sol": "a) 60%\nb) 65%\nc) 45%\nd) 45%, 60%, 65%, 70% → {9/20}, {3/5}, 0.65, 70%"}, {"kind": "blank", "p": "Write as percentages, then order from smallest to largest (type the percentages, e.g. 45, 60):", "tag": "", "marks": "", "flat": [{"t": "a) 17/25 = __B1__%", "a": {"B1": "68"}, "expr": "dec"}, {"t": "b) 0.43 = __B1__%", "a": {"B1": "43"}, "expr": "dec"}, {"t": "c) 39/50 = __B1__%", "a": {"B1": "78"}, "expr": "dec"}, {"t": "d) 0.627 = __B1__%", "a": {"B1": "62.7"}, "expr": "dec"}, {"t": "e) ascending order of the percentages: __B1__", "a": {"B1": "43, 62.7, 68, 78"}, "expr": "dlist"}], "sol": "a) 68%\nb) 43%\nc) 78%\nd) 62.7%\ne) 43, 62.7, 68, 78"}]}, {"id": "s7", "label": "Ex 12G", "sub": "One quantity as a percentage of another", "slides": [{"kind": "blank", "p": "Express as a percentage:", "tag": "", "marks": "", "flat": [{"t": "a) 76 marks out of 100 = __B1__%", "a": {"B1": "76"}, "expr": "dec"}, {"t": "b) 17 marks out of 20 = __B1__%", "a": {"B1": "85"}, "expr": "dec"}, {"t": "c) 11 marks out of 25 = __B1__%", "a": {"B1": "44"}, "expr": "dec"}, {"t": "d) 37 marks out of 50 = __B1__%", "a": {"B1": "74"}, "expr": "dec"}, {"t": "e) 36 marks out of 40 = __B1__%", "a": {"B1": "90"}, "expr": "dec"}, {"t": "f) 138 marks out of 200 = __B1__%", "a": {"B1": "69"}, "expr": "dec"}], "sol": "Write as a fraction, then change it to a percentage.\na) {76/100} = 76%\nb) {17/20} = 85%\nc) {11/25} = 44%\nd) {37/50} = 74%\ne) {36/40} = 90%\nf) {138/200} = 69%"}, {"kind": "blank", "p": "Express as a percentage:", "tag": "", "marks": "", "flat": [{"t": "a) 72 diners in a restaurant that seats 200 → __B1__%", "a": {"B1": "36"}, "expr": "dec"}, {"t": "b) 405 books sold out of 500 printed → __B1__%", "a": {"B1": "81"}, "expr": "dec"}, {"t": "c) 660 m² of lawn in a 2000 m² garden → __B1__%", "a": {"B1": "33"}, "expr": "dec"}, {"t": "d) 186 points out of 300 → __B1__%", "a": {"B1": "62"}, "expr": "dec"}], "sol": "a) 72 ÷ 200 = 0.36\nb) 405 ÷ 500 = 0.81\nc) 660 ÷ 2000 = 0.33\nd) 186 ÷ 300 = 0.62"}, {"kind": "blank", "p": "In a class of 25 students, 13 have brown eyes. What percentage is that?", "tag": "", "marks": "", "flat": [{"t": "__B1__%", "a": {"B1": "52"}, "expr": "dec"}], "sol": "{13/25} = {52/100} = 52%"}, {"kind": "blank", "p": "Maria must attend at least 80% of 20 classes. She misses 3 classes.", "tag": "", "marks": "", "flat": [{"t": "a) Percentage attended: __B1__%", "a": {"B1": "85"}, "expr": "dec"}, {"t": "b) Does she get her certificate? (yes/no) __B1__", "a": {"B1": "yes"}}], "sol": "a) 17 out of 20 = 85%\nb) 85% ≥ 80%: yes"}, {"kind": "blank", "p": "By writing both quantities in the same units, express the first as a percentage of the second:", "tag": "", "marks": "", "flat": [{"t": "a) 7 mm, 2 cm → __B1__%", "a": {"B1": "35"}, "expr": "dec"}, {"t": "b) 50 g, 1 kg → __B1__%", "a": {"B1": "5"}, "expr": "dec"}, {"t": "c) 84 cm, 4 m → __B1__%", "a": {"B1": "21"}, "expr": "dec"}, {"t": "d) 48 seconds, 5 minutes → __B1__%", "a": {"B1": "16"}, "expr": "dec"}, {"t": "e) 720 kg, 2 tonnes → __B1__%", "a": {"B1": "36"}, "expr": "dec"}, {"t": "f) 63 paise, ₹9 → __B1__%", "a": {"B1": "7"}, "expr": "dec"}, {"t": "g) 24 minutes, 10 hours → __B1__%", "a": {"B1": "4"}, "expr": "dec"}, {"t": "h) 1 mL, 1 L → __B1__%", "a": {"B1": "0.1"}, "expr": "dec"}], "sol": "Change to the smaller unit, then divide.\na) 35%\nb) 5%\nc) 21%\nd) 16%\ne) 36%\nf) 7%\ng) 4%\nh) 0.1%"}, {"kind": "blank", "p": "2 km of pipe must be laid. So far 480 m has been laid. What percentage is that?", "tag": "", "marks": "", "flat": [{"t": "__B1__%", "a": {"B1": "24"}, "expr": "dec"}], "sol": "480 ÷ 2000 = 0.24 = 24%"}, {"kind": "blank", "p": "A choir has 50 singers: 9 in Class 4, 17 in Class 5 and 24 in Class 6.", "tag": "", "marks": "", "flat": [{"t": "a) Class 4: __B1__%", "a": {"B1": "18"}, "expr": "dec"}, {"t": "b) Class 5: __B1__%", "a": {"B1": "34"}, "expr": "dec"}, {"t": "c) Class 6: __B1__%", "a": {"B1": "48"}, "expr": "dec"}], "sol": "a) 18%\nb) 34%\nc) 48% (total 100%)"}, {"kind": "blank", "p": "Pooja made 3.6 L of juice and drank 180 mL. What percentage is left?", "tag": "", "marks": "", "flat": [{"t": "__B1__%", "a": {"B1": "95"}, "expr": "dec"}], "sol": "180 mL is 5% of 3600 mL, so 95% is left"}]}, {"id": "s8", "label": "Ex 12H", "sub": "Finding a percentage of a quantity", "slides": [{"kind": "blank", "p": "Find:", "tag": "", "marks": "", "flat": [{"t": "a) 28% of 100 = __B1__", "a": {"B1": "28"}, "expr": "dec"}, {"t": "b) 60% of 10 = __B1__", "a": {"B1": "6"}, "expr": "dec"}, {"t": "c) 85% of 1000 = __B1__", "a": {"B1": "850"}, "expr": "dec"}, {"t": "d) 15% of 200 = __B1__", "a": {"B1": "30"}, "expr": "dec"}, {"t": "e) 80% of 250 = __B1__", "a": {"B1": "200"}, "expr": "dec"}, {"t": "f) 27% of 30 = __B1__", "a": {"B1": "8.1"}, "expr": "dec"}, {"t": "g) 75% of 320 = __B1__", "a": {"B1": "240"}, "expr": "dec"}, {"t": "h) 7% of 70 = __B1__", "a": {"B1": "4.9"}, "expr": "dec"}, {"t": "i) 45% of 35 = __B1__", "a": {"B1": "15.75"}, "expr": "dec"}], "sol": "Write the percentage as a decimal and multiply.\na) 0.28 × 100 = 28\nb) 0.6 × 10 = 6\nc) 0.85 × 1000 = 850\nd) 0.15 × 200 = 30\ne) 0.8 × 250 = 200\nf) 0.27 × 30 = 8.1\ng) 0.75 × 320 = 240\nh) 0.07 × 70 = 4.9\ni) 0.45 × 35 = 15.75"}, {"kind": "blank", "p": "5% of workers must have first-aid training. How many in:", "tag": "", "marks": "", "flat": [{"t": "a) an office of 20 workers? __B1__", "a": {"B1": "1"}, "expr": "dec"}, {"t": "b) an office of 300 workers? __B1__", "a": {"B1": "15"}, "expr": "dec"}], "sol": "a) 0.05 × 20 = 1\nb) 0.05 × 300 = 15"}, {"kind": "blank", "p": "A school has 485 students. 20% go on a museum trip. How many go?", "tag": "", "marks": "", "flat": [{"t": "__B1__", "a": {"B1": "97"}, "expr": "dec"}], "sol": "0.2 × 485 = 97"}, {"kind": "blank", "p": "A farmer planted 2400 acres: 30% barley and the rest wheat.", "tag": "", "marks": "", "flat": [{"t": "a) Percentage wheat: __B1__%", "a": {"B1": "70"}, "expr": "dec"}, {"t": "b) Acres of barley: __B1__", "a": {"B1": "720"}, "expr": "dec"}, {"t": "c) Acres of wheat: __B1__", "a": {"B1": "1680"}, "expr": "dec"}], "sol": "a) 100 − 30 = 70%\nb) 0.3 × 2400 = 720\nc) 0.7 × 2400 = 1680"}, {"kind": "blank", "p": "Find, giving each answer in the unit shown:", "tag": "", "marks": "", "flat": [{"t": "a) 27% of ₹1 = __B1__ paise", "a": {"B1": "27"}, "expr": "dec"}, {"t": "b) 5% of 9 m = __B1__ cm", "a": {"B1": "45"}, "expr": "dec"}, {"t": "c) 35% of 2 kg = __B1__ g", "a": {"B1": "700"}, "expr": "dec"}, {"t": "d) 10% of 3 hours = __B1__ min", "a": {"B1": "18"}, "expr": "dec"}, {"t": "e) 60% of 8 kL = __B1__ L", "a": {"B1": "4800"}, "expr": "dec"}, {"t": "f) 42% of 4 cm = __B1__ mm", "a": {"B1": "16.8"}, "expr": "dec"}, {"t": "g) 22% of 5 days = __B1__ hours", "a": {"B1": "26.4"}, "expr": "dec"}, {"t": "h) 1.5% of an hour = __B1__ seconds", "a": {"B1": "54"}, "expr": "dec"}], "sol": "Change to the new unit first, then find the percentage.\na) 27 paise\nb) 45 cm\nc) 700 g\nd) 18 min\ne) 4800 L\nf) 16.8 mm\ng) 26.4 hours\nh) 54 seconds"}, {"kind": "blank", "p": "A drink is 8% sugar. How many grams of sugar are in 1.5 kg of it?", "tag": "", "marks": "", "flat": [{"t": "__B1__ g", "a": {"B1": "120"}, "expr": "dec"}], "sol": "0.08 × 1500 = 120 g"}, {"kind": "blank", "p": "A play lasts 2 hours 40 minutes. 12.5% of this time is the interval. How long is the interval?", "tag": "", "marks": "", "flat": [{"t": "__B1__ minutes", "a": {"B1": "20"}, "expr": "dec"}], "sol": "160 × 0.125 = 20 minutes"}]}, {"id": "s9", "label": "Ex 12I", "sub": "Percentage increase or decrease", "slides": [{"kind": "blank", "p": "A laptop costs ₹32 000 plus 18% GST.", "tag": "", "marks": "", "flat": [{"t": "a) Size of the tax: ₹__B1__", "a": {"B1": "5760"}, "expr": "dec"}, {"t": "b) Total price: ₹__B1__", "a": {"B1": "37760"}, "expr": "dec"}], "sol": "a) 0.18 × 32 000 = 5760\nb) 32 000 + 5760 = 37 760"}, {"kind": "blank", "p": "A shop buys a shirt for ₹400 and marks it up by 50%.", "tag": "", "marks": "", "flat": [{"t": "a) Size of the increase: ₹__B1__", "a": {"B1": "200"}, "expr": "dec"}, {"t": "b) Selling price: ₹__B1__", "a": {"B1": "600"}, "expr": "dec"}], "sol": "a) 0.5 × 400 = 200\nb) 400 + 200 = 600"}, {"kind": "blank", "p": "Increase:", "tag": "", "marks": "", "flat": [{"t": "a) 60 cm by 40% → __B1__ cm", "a": {"B1": "84"}, "expr": "dec"}, {"t": "b) 40 L by 70% → __B1__ L", "a": {"B1": "68"}, "expr": "dec"}], "sol": "a) 60 + 24 = 84\nb) 40 + 28 = 68"}, {"kind": "blank", "p": "A ₹8600 microwave is discounted by 25%.", "tag": "", "marks": "", "flat": [{"t": "a) Size of the discount: ₹__B1__", "a": {"B1": "2150"}, "expr": "dec"}, {"t": "b) Sale price: ₹__B1__", "a": {"B1": "6450"}, "expr": "dec"}], "sol": "a) 0.25 × 8600 = 2150\nb) 8600 − 2150 = 6450"}, {"kind": "blank", "p": "Whole milk has 8 g of fat per carton. Low-fat milk has 80% less fat.", "tag": "", "marks": "", "flat": [{"t": "a) How much less fat? __B1__ g", "a": {"B1": "6.4"}, "expr": "dec"}, {"t": "b) Fat in low-fat milk: __B1__ g", "a": {"B1": "1.6"}, "expr": "dec"}], "sol": "a) 0.8 × 8 = 6.4 g\nb) 8 − 6.4 = 1.6 g"}, {"kind": "blank", "p": "Decrease:", "tag": "", "marks": "", "flat": [{"t": "a) 30 minutes by 60% → __B1__ minutes", "a": {"B1": "12"}, "expr": "dec"}, {"t": "b) 200 m² by 35% → __B1__ m²", "a": {"B1": "130"}, "expr": "dec"}], "sol": "a) 30 − 18 = 12\nb) 200 − 70 = 130"}]}, {"id": "s10", "label": "Review 12A", "sub": "Review set 12A", "slides": [{"kind": "blank", "p": "In this pattern of 100 tiles:", "tag": "", "marks": "", "flat": [{"t": "a) shaded as a fraction: __B1__/100", "a": {"B1": "28"}}, {"t": "b) shaded as a percentage: __B1__%", "a": {"B1": "28"}, "expr": "dec"}], "sol": "28 tiles are shaded: {28/100} = 28%", "fig": "<svg class=\"figsvg\" viewBox=\"0 0 220 220\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"10\" y=\"10\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"30\" y=\"10\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"50\" y=\"10\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"70\" y=\"10\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"90\" y=\"10\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"110\" y=\"10\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"130\" y=\"10\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"150\" y=\"10\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"170\" y=\"10\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"190\" y=\"10\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"10\" y=\"30\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"30\" y=\"30\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"50\" y=\"30\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"70\" y=\"30\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"90\" y=\"30\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"110\" y=\"30\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"130\" y=\"30\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"150\" y=\"30\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"170\" y=\"30\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"190\" y=\"30\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"10\" y=\"50\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"30\" y=\"50\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"50\" y=\"50\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"70\" y=\"50\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"90\" y=\"50\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"110\" y=\"50\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"130\" y=\"50\" width=\"20\" height=\"20\"/><rect class=\"shd\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"150\" y=\"50\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"170\" y=\"50\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"190\" y=\"50\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"10\" y=\"70\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"30\" y=\"70\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"50\" y=\"70\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"70\" y=\"70\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"90\" y=\"70\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"110\" y=\"70\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"130\" y=\"70\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"150\" y=\"70\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"170\" y=\"70\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"190\" y=\"70\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"10\" y=\"90\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"30\" y=\"90\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"50\" y=\"90\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"70\" y=\"90\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"90\" y=\"90\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"110\" y=\"90\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"130\" y=\"90\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"150\" y=\"90\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"170\" y=\"90\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"190\" y=\"90\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"10\" y=\"110\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"30\" y=\"110\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"50\" y=\"110\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"70\" y=\"110\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"90\" y=\"110\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"110\" y=\"110\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"130\" y=\"110\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"150\" y=\"110\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"170\" y=\"110\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"190\" y=\"110\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"10\" y=\"130\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"30\" y=\"130\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"50\" y=\"130\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"70\" y=\"130\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"90\" y=\"130\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"110\" y=\"130\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"130\" y=\"130\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"150\" y=\"130\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"170\" y=\"130\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"190\" y=\"130\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"10\" y=\"150\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"30\" y=\"150\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"50\" y=\"150\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"70\" y=\"150\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"90\" y=\"150\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"110\" y=\"150\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"130\" y=\"150\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"150\" y=\"150\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"170\" y=\"150\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"190\" y=\"150\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"10\" y=\"170\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"30\" y=\"170\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"50\" y=\"170\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"70\" y=\"170\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"90\" y=\"170\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"110\" y=\"170\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"130\" y=\"170\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"150\" y=\"170\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"170\" y=\"170\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"190\" y=\"170\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"10\" y=\"190\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"30\" y=\"190\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"50\" y=\"190\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"70\" y=\"190\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"90\" y=\"190\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"110\" y=\"190\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"130\" y=\"190\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"150\" y=\"190\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"170\" y=\"190\" width=\"20\" height=\"20\"/><rect class=\"cell\" style=\"stroke:var(--ink);stroke-width:.8\" x=\"190\" y=\"190\" width=\"20\" height=\"20\"/></svg>"}, {"kind": "blank", "p": "Write as a percentage:", "tag": "", "marks": "", "flat": [{"t": "a) 0.9 = __B1__%", "a": {"B1": "90"}, "expr": "dec"}, {"t": "b) 0.47 = __B1__%", "a": {"B1": "47"}, "expr": "dec"}, {"t": "c) 0.306 = __B1__%", "a": {"B1": "30.6"}, "expr": "dec"}], "sol": "Multiply by 100."}, {"kind": "blank", "p": "Write as a fraction in lowest terms:", "tag": "", "marks": "", "flat": [{"t": "a) 31% = __B1__", "a": {"B1": "31/100"}, "expr": "fl"}, {"t": "b) 16% = __B1__", "a": {"B1": "4/25"}, "expr": "fl"}, {"t": "c) 94% = __B1__", "a": {"B1": "47/50"}, "expr": "fl"}], "sol": "a) {31/100}\nb) {16/100} = {4/25}\nc) {94/100} = {47/50}"}, {"kind": "blank", "p": "Find:", "tag": "", "marks": "", "flat": [{"t": "a) 45% of ₹60 = ₹__B1__", "a": {"B1": "27"}, "expr": "dec"}, {"t": "b) 12% of 4 m = __B1__ cm", "a": {"B1": "48"}, "expr": "dec"}], "sol": "a) 0.45 × 60 = 27\nb) 0.12 × 400 = 48 cm"}, {"kind": "blank", "p": "50 students attended a quiz and 27 won a prize. What percentage won?", "tag": "", "marks": "", "flat": [{"t": "__B1__%", "a": {"B1": "54"}, "expr": "dec"}], "sol": "{27/50} = 54%"}, {"kind": "blank", "p": "Write as a decimal:", "tag": "", "marks": "", "flat": [{"t": "a) 81% = __B1__", "a": {"B1": "0.81"}, "expr": "dec"}, {"t": "b) 2% = __B1__", "a": {"B1": "0.02"}, "expr": "dec"}, {"t": "c) 10.8% = __B1__", "a": {"B1": "0.108"}, "expr": "dec"}], "sol": "Divide by 100."}, {"kind": "blank", "p": "Marcia has travelled 620 km of a 2000 km journey. What percentage is that?", "tag": "", "marks": "", "flat": [{"t": "__B1__%", "a": {"B1": "31"}, "expr": "dec"}], "sol": "620 ÷ 2000 = 0.31"}, {"kind": "blank", "p": "A town has 280 households: 15% use wood fires, 30% electricity and 10% gas. How many use:", "tag": "", "marks": "", "flat": [{"t": "a) electricity? __B1__", "a": {"B1": "84"}, "expr": "dec"}, {"t": "b) wood or gas? __B1__", "a": {"B1": "70"}, "expr": "dec"}], "sol": "a) 0.3 × 280 = 84\nb) 25% of 280 = 70"}, {"kind": "blank", "p": "A truck's stopping distance is 150 m. In wet weather it increases by 30%.", "tag": "", "marks": "", "flat": [{"t": "a) Size of the increase: __B1__ m", "a": {"B1": "45"}, "expr": "dec"}, {"t": "b) Wet-weather stopping distance: __B1__ m", "a": {"B1": "195"}, "expr": "dec"}], "sol": "a) 0.3 × 150 = 45\nb) 150 + 45 = 195"}]}, {"id": "s11", "label": "Review 12B", "sub": "Review set 12B", "slides": [{"kind": "blank", "p": "Estimate the percentage shaded:", "tag": "", "marks": "", "flat": [{"t": "a) __B1__%", "a": {"B1": "70"}, "fig": "<svg class=\"figsvg\" viewBox=\"0 0 300 64\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><rect class=\"cell\" style=\"stroke:var(--ink)\" x=\"20\" y=\"8\" width=\"260\" height=\"24\"/><rect class=\"shd\" x=\"20\" y=\"8\" width=\"182.0\" height=\"24\"/><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:.8\" x1=\"20.0\" y1=\"8\" x2=\"20.0\" y2=\"32\"/><text class=\"po\" x=\"20.0\" y=\"46.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">0</text><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:.8\" x1=\"46.0\" y1=\"8\" x2=\"46.0\" y2=\"32\"/><text class=\"po\" x=\"46.0\" y=\"46.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">10</text><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:.8\" x1=\"72.0\" y1=\"8\" x2=\"72.0\" y2=\"32\"/><text class=\"po\" x=\"72.0\" y=\"46.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">20</text><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:.8\" x1=\"98.0\" y1=\"8\" x2=\"98.0\" y2=\"32\"/><text class=\"po\" x=\"98.0\" y=\"46.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">30</text><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:.8\" x1=\"124.0\" y1=\"8\" x2=\"124.0\" y2=\"32\"/><text class=\"po\" x=\"124.0\" y=\"46.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">40</text><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:.8\" x1=\"150.0\" y1=\"8\" x2=\"150.0\" y2=\"32\"/><text class=\"po\" x=\"150.0\" y=\"46.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">50</text><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:.8\" x1=\"176.0\" y1=\"8\" x2=\"176.0\" y2=\"32\"/><text class=\"po\" x=\"176.0\" y=\"46.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">60</text><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:.8\" x1=\"202.0\" y1=\"8\" x2=\"202.0\" y2=\"32\"/><text class=\"po\" x=\"202.0\" y=\"46.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">70</text><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:.8\" x1=\"228.0\" y1=\"8\" x2=\"228.0\" y2=\"32\"/><text class=\"po\" x=\"228.0\" y=\"46.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">80</text><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:.8\" x1=\"254.0\" y1=\"8\" x2=\"254.0\" y2=\"32\"/><text class=\"po\" x=\"254.0\" y=\"46.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">90</text><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:.8\" x1=\"280.0\" y1=\"8\" x2=\"280.0\" y2=\"32\"/><text class=\"po\" x=\"280.0\" y=\"46.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">100</text></svg>", "expr": "dec"}, {"t": "b) __B1__%", "a": {"B1": "20"}, "fig": "<svg class=\"figsvg\" viewBox=\"0 0 300 64\" role=\"img\"><defs><marker id=\"ah\" viewBox=\"0 0 10 10\" refX=\"9\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M0,1 L10,5 L0,9 z\" class=\"ahd\"/></marker><marker id=\"ahs\" viewBox=\"0 0 10 10\" refX=\"1\" refY=\"5\" markerWidth=\"7\" markerHeight=\"7\" orient=\"auto\"><path d=\"M10,1 L0,5 L10,9 z\" class=\"ahd\"/></marker></defs><rect class=\"cell\" style=\"stroke:var(--ink)\" x=\"20\" y=\"8\" width=\"260\" height=\"24\"/><rect class=\"shd\" x=\"20\" y=\"8\" width=\"52.0\" height=\"24\"/><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:.8\" x1=\"20.0\" y1=\"8\" x2=\"20.0\" y2=\"32\"/><text class=\"po\" x=\"20.0\" y=\"46.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">0</text><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:.8\" x1=\"46.0\" y1=\"8\" x2=\"46.0\" y2=\"32\"/><text class=\"po\" x=\"46.0\" y=\"46.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">10</text><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:.8\" x1=\"72.0\" y1=\"8\" x2=\"72.0\" y2=\"32\"/><text class=\"po\" x=\"72.0\" y=\"46.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">20</text><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:.8\" x1=\"98.0\" y1=\"8\" x2=\"98.0\" y2=\"32\"/><text class=\"po\" x=\"98.0\" y=\"46.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">30</text><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:.8\" x1=\"124.0\" y1=\"8\" x2=\"124.0\" y2=\"32\"/><text class=\"po\" x=\"124.0\" y=\"46.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">40</text><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:.8\" x1=\"150.0\" y1=\"8\" x2=\"150.0\" y2=\"32\"/><text class=\"po\" x=\"150.0\" y=\"46.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">50</text><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:.8\" x1=\"176.0\" y1=\"8\" x2=\"176.0\" y2=\"32\"/><text class=\"po\" x=\"176.0\" y=\"46.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">60</text><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:.8\" x1=\"202.0\" y1=\"8\" x2=\"202.0\" y2=\"32\"/><text class=\"po\" x=\"202.0\" y=\"46.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">70</text><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:.8\" x1=\"228.0\" y1=\"8\" x2=\"228.0\" y2=\"32\"/><text class=\"po\" x=\"228.0\" y=\"46.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">80</text><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:.8\" x1=\"254.0\" y1=\"8\" x2=\"254.0\" y2=\"32\"/><text class=\"po\" x=\"254.0\" y=\"46.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">90</text><line class=\"tk\" style=\"stroke:var(--ink);stroke-width:.8\" x1=\"280.0\" y1=\"8\" x2=\"280.0\" y2=\"32\"/><text class=\"po\" x=\"280.0\" y=\"46.0\" text-anchor=\"middle\" dominant-baseline=\"middle\">100</text></svg>", "expr": "dec"}], "sol": "a) 70%\nb) 20%"}, {"kind": "blank", "p": "In a group of 200 children, 34 are allergic to peanuts. What percentage is that?", "tag": "", "marks": "", "flat": [{"t": "__B1__%", "a": {"B1": "17"}, "expr": "dec"}], "sol": "34 ÷ 200 = 0.17"}, {"kind": "blank", "p": "Write 74% as:", "tag": "", "marks": "", "flat": [{"t": "a) a decimal: __B1__", "a": {"B1": "0.74"}, "expr": "dec"}, {"t": "b) a fraction in lowest terms: __B1__", "a": {"B1": "37/50"}, "expr": "fl"}], "sol": "a) 0.74\nb) {74/100} = {37/50}"}, {"kind": "blank", "p": "8% of the 375 students at a school are left-handed. How many is that?", "tag": "", "marks": "", "flat": [{"t": "__B1__", "a": {"B1": "30"}, "expr": "dec"}], "sol": "0.08 × 375 = 30"}, {"kind": "blank", "p": "Express the first quantity as a percentage of the second:", "tag": "", "marks": "", "flat": [{"t": "a) 13 goals from 25 shots → __B1__%", "a": {"B1": "52"}, "expr": "dec"}, {"t": "b) 58 cm of 2 m → __B1__%", "a": {"B1": "29"}, "expr": "dec"}], "sol": "a) {13/25} = 52%\nb) 58 ÷ 200 = 29%"}, {"kind": "blank", "p": "Kabir spent ₹150 of the ₹500 he was given. What percentage did he spend?", "tag": "", "marks": "", "flat": [{"t": "__B1__%", "a": {"B1": "30"}, "expr": "dec"}], "sol": "150 ÷ 500 = 0.3"}, {"kind": "blank", "p": "An 800 mL bottle of mixture is 15% syrup and 85% water. Find the amount of:", "tag": "", "marks": "", "flat": [{"t": "a) syrup: __B1__ mL", "a": {"B1": "120"}, "expr": "dec"}, {"t": "b) water: __B1__ mL", "a": {"B1": "680"}, "expr": "dec"}], "sol": "a) 0.15 × 800 = 120\nb) 0.85 × 800 = 680"}, {"kind": "blank", "p": "A company with 600 staff reduces its staff by 15%.", "tag": "", "marks": "", "flat": [{"t": "a) Size of the decrease: __B1__", "a": {"B1": "90"}, "expr": "dec"}, {"t": "b) Staff remaining: __B1__", "a": {"B1": "510"}, "expr": "dec"}], "sol": "a) 0.15 × 600 = 90\nb) 600 − 90 = 510"}]}];
/* ================= build slide lists ================= */
var SLIDES = {}; SECTIONS.forEach(function(sec){ SLIDES[sec.id]=sec.slides; });
var TAB_DEFS = SECTIONS.map(function(sec){ return {id:sec.id, label:sec.label, sub:sec.sub}; });

/* ================= state ================= */
function blankItem(slide){
  if(slide.kind==='mcq'||slide.kind==='ar'){
    return {status:'unanswered', attempts:0, choice:undefined};
  }
  return {status:'unanswered', curStep:0, stepStates: slide.flat.map(function(){ return {status:'unanswered', attempts:0, inputs:{}}; })};
}
function defaultState(){
  var s={tabs:{}};
  TAB_DEFS.forEach(function(td){
    s.tabs[td.id] = { idx:0, maxReached:0, items: SLIDES[td.id].map(function(sl){ return blankItem(sl); }) };
  });
  return s;
}
var appState = {mode:null, learning:null, quiz:null};
var state = null;      // alias for appState[appState.mode]
var MODE = null;
var activeTab=TAB_DEFS[0].id;

function setMode(m){
  appState.mode = m;
  if(!appState[m]) appState[m] = defaultState();
  state = appState[m];
  MODE = m;
}
/* ================= student accounts (saved on this device) ================= */
var SHEET_KEY='sopaan-g6-ch12';
var ACC_KEY='sopaan-students-v1';
var storageOK=true;
var MEM={};
function lsGet(k){ var r=null; try{ r=localStorage.getItem(k); }catch(e){ storageOK=false; }
  if(r===null||r===undefined) r=MEM[k]||null; try{ return r?JSON.parse(r):null; }catch(e){ return null; } }
function lsSet(k,v){ var j=JSON.stringify(v); MEM[k]=j; try{ localStorage.setItem(k,j); return true; }catch(e){ storageOK=false; return false; } }
try{ localStorage.setItem('sopaan-probe','1'); localStorage.removeItem('sopaan-probe'); }catch(e){ storageOK=false; }
function hashPin(pin,salt){ var h=2166136261, str=salt+'|'+pin; for(var i=0;i<str.length;i++){ h^=str.charCodeAt(i); h=Math.imul(h,16777619)>>>0; } return h.toString(36); }
function accKey(name,roll){ return (name.trim().toLowerCase().replace(/\s+/g,' ')+'#'+roll.trim().toLowerCase()); }
function accounts(){ return lsGet(ACC_KEY)||{students:{}}; }
var student=null; // {key,name,roll}
var records=[];   // finished-tab history for this student on this sheet
function progKey(){ return SHEET_KEY+'::'+student.key; }

function loadState(){
  appState = {mode:null, learning:null, quiz:null}; records=[]; activeTab=TAB_DEFS[0].id;
  var saved=lsGet(progKey());
  if(!saved) return;
  try{
    ['learning','quiz'].forEach(function(m){
      if(saved[m] && saved[m].tabs){
        var fresh = defaultState();
        TAB_DEFS.forEach(function(td){
          if(saved[m].tabs[td.id] && saved[m].tabs[td.id].items && saved[m].tabs[td.id].items.length===SLIDES[td.id].length){
            fresh.tabs[td.id] = saved[m].tabs[td.id];
          }
        });
        appState[m] = fresh;
      }
    });
    if(saved.mode==='learning' || saved.mode==='quiz') appState.mode = saved.mode;
    if(saved.activeTab && TAB_DEFS.some(function(t){ return t.id===saved.activeTab; })) activeTab = saved.activeTab;
    if(Array.isArray(saved.records)) records = saved.records;
  }catch(e){}
}
function saveState(){
  if(!student) return;
  lsSet(progKey(), {mode:appState.mode, learning:appState.learning, quiz:appState.quiz, activeTab:activeTab, records:records, updated:Date.now()});
  var acc=accounts(); if(acc.students[student.key]){ acc.students[student.key].last=Date.now(); lsSet(ACC_KEY,acc); }
}
function addRecord(mode, tabId, correct, revealed, skipped, total){
  records.unshift({at:Date.now(), mode:mode, tab:tabId, correct:correct, revealed:revealed, skipped:skipped, total:total});
  if(records.length>60) records.length=60;
  saveState();
}
function fmtDate(ms){ try{ return new Date(ms).toLocaleString(undefined,{day:'numeric',month:'short',hour:'2-digit',minute:'2-digit'}); }catch(e){ return ''; } }

function renderWho(){
  var el=document.getElementById('whoBar');
  if(!student){ el.hidden=true; el.innerHTML=''; return; }
  el.hidden=false;
  el.innerHTML='Signed in as <b>'+esc(student.name)+'</b> · Roll '+esc(student.roll)+
    ' <button id="btnRecord">My record</button> <button id="btnSignOut">Sign out</button>';
  document.getElementById('btnRecord').addEventListener('click', renderRecord);
  document.getElementById('btnSignOut').addEventListener('click', signOut);
}
function signOut(){
  saveState(); student=null; state=null; MODE=null;
  var acc=accounts(); delete acc.current; lsSet(ACC_KEY,acc);
  document.getElementById('modePill').hidden=true;
  renderWho(); renderLogin();
}
function signIn(key){
  var acc=accounts(); var st=acc.students[key]; if(!st) return;
  student={key:key, name:st.name, roll:st.roll};
  acc.current=key; st.last=Date.now(); lsSet(ACC_KEY,acc);
  loadState(); renderWho();
  if(appState.mode==='learning' || appState.mode==='quiz'){
    setMode(appState.mode); document.getElementById('modePill').hidden=false; updateModePill();
    showChrome(true); buildTabbar(); renderSlide();
    showToast('Welcome back, '+st.name.split(' ')[0]+'. Picking up where you left off.');
  } else {
    renderModePicker();
  }
}
function renderLogin(msg){
  showChrome(false);
  var acc=accounts(); var keys=Object.keys(acc.students).sort(function(a,b){ return (acc.students[b].last||0)-(acc.students[a].last||0); });
  var h='<div class="login-card"><h2>Student sign-in</h2>'+
    '<p class="lead">Sign in to save your answers, see your record and continue where you left off next time.</p>';
  if(!storageOK) h+='<div class="login-err">This browser is blocking saved data (for example, a private window). You can still practise, but progress will not be kept after you close the page.</div>';
  if(msg) h+='<div class="login-err">'+esc(msg)+'</div>';
  if(keys.length){
    h+='<div class="known"><span class="known-label">Continue as</span>';
    keys.slice(0,6).forEach(function(k){ var st=acc.students[k];
      h+='<button class="known-btn" data-k="'+esc(k)+'"><span>'+esc(st.name)+' <small>· Roll '+esc(st.roll)+'</small></span><small>'+(st.last?'Last active '+fmtDate(st.last):'')+'</small></button>'; });
    h+='</div>';
  }
  h+='<form id="loginForm" novalidate>'+
    '<div class="fld"><label for="lgName">Full name</label><input id="lgName" autocomplete="name" required></div>'+
    '<div class="fld-row"><div class="fld"><label for="lgRoll">Roll no.</label><input id="lgRoll" required></div>'+
    '<div class="fld"><label for="lgPin">4-digit PIN</label><input id="lgPin" type="password" inputmode="numeric" maxlength="4" autocomplete="off" required></div></div>'+
    '<button class="btn btn-primary" type="submit" style="width:100%;">Sign in</button>'+
    '<p class="login-note">New here? Enter your name, roll no. and a PIN you will remember, and your profile is created. Progress is saved on this device, so use the same device and browser to continue.</p>'+
    '</form></div>';
  var wrap=document.getElementById('wrap'); wrap.innerHTML=h;
  wrap.querySelectorAll('.known-btn').forEach(function(b){
    b.addEventListener('click', function(){
      var st=accounts().students[b.dataset.k];
      document.getElementById('lgName').value=st.name; document.getElementById('lgRoll').value=st.roll;
      document.getElementById('lgPin').focus();
    });
  });
  document.getElementById('loginForm').addEventListener('submit', function(e){
    e.preventDefault();
    var name=document.getElementById('lgName').value.trim(), roll=document.getElementById('lgRoll').value.trim(), pin=document.getElementById('lgPin').value.trim();
    if(!name||!roll){ renderLoginErr('Enter your name and roll no.'); return; }
    if(!/^\d{4}$/.test(pin)){ renderLoginErr('Your PIN must be exactly 4 digits.'); return; }
    var k=accKey(name,roll); var acc=accounts();
    if(acc.students[k]){
      if(acc.students[k].pin!==hashPin(pin,k)){ renderLoginErr('That PIN does not match this name and roll no. Try again.'); return; }
    } else {
      acc.students[k]={name:name.replace(/\s+/g,' '), roll:roll, pin:hashPin(pin,k), created:Date.now()};
      lsSet(ACC_KEY,acc);
    }
    signIn(k);
  });
}
function renderLoginErr(m){
  var n=document.getElementById('lgName').value, r=document.getElementById('lgRoll').value;
  renderLogin(m); document.getElementById('lgName').value=n; document.getElementById('lgRoll').value=r; document.getElementById('lgPin').focus();
}
function tabSummary(m){
  var st=appState[m]; if(!st) return null;
  return TAB_DEFS.map(function(td){
    var items=st.tabs[td.id].items, n=items.length;
    var c=items.filter(function(i){return i.status==='correct';}).length;
    var done=items.filter(function(i){return i.status!=='unanswered';}).length;
    return {label:td.label, n:n, done:done, correct:c};
  });
}
function renderRecord(){
  showChrome(false);
  var tabLabel=function(id){ var t=TAB_DEFS.find(function(x){return x.id===id;}); return t?t.label:id; };
  var h='<div class="rec-card"><h2>'+esc(student.name)+'’s record</h2><p class="rec-empty" style="margin:0 0 12px;">Roll '+esc(student.roll)+' · Percentage</p>';
  ['learning','quiz'].forEach(function(m){
    var sum=tabSummary(m);
    h+='<h3>'+(m==='learning'?'📘 Learning Sheet':'📝 Quiz Mode')+'</h3>';
    if(!sum){ h+='<p class="rec-empty">Not started yet.</p>'; return; }
    h+='<div class="rec-table-wrap"><table class="rec-table"><thead><tr><th>Section</th><th>Progress</th><th>Correct first time</th></tr></thead><tbody>';
    sum.forEach(function(r){ var pct=Math.round(r.done/r.n*100);
      h+='<tr><td>'+r.label+'</td><td><span class="rec-bar"><i style="width:'+pct+'%"></i></span>'+r.done+' / '+r.n+'</td><td>'+(m==='quiz'?'—':r.correct+' / '+r.n)+'</td></tr>'; });
    h+='</tbody></table></div>';
  });
  h+='</div><div class="rec-card"><h3>Finished sections</h3>';
  if(!records.length){ h+='<p class="rec-empty">No sections finished yet. Each time you finish a tab, your score is recorded here.</p>'; }
  else {
    h+='<div class="rec-table-wrap"><table class="rec-table"><thead><tr><th>When</th><th>Mode</th><th>Section</th><th>Score</th></tr></thead><tbody>';
    records.forEach(function(r){ h+='<tr><td>'+fmtDate(r.at)+'</td><td>'+(r.mode==='quiz'?'Quiz':'Learning')+'</td><td>'+tabLabel(r.tab)+'</td><td>'+r.correct+' / '+r.total+(r.mode==='learning'?' <span class="rec-empty">('+r.revealed+' revealed, '+r.skipped+' skipped)</span>':'')+'</td></tr>'; });
    h+='</tbody></table></div>';
  }
  h+='</div><button class="btn btn-primary" id="btnBack">'+(MODE?'Back to practice':'Choose a mode')+'</button>';
  document.getElementById('wrap').innerHTML=h;
  document.getElementById('btnBack').addEventListener('click', function(){
    if(MODE){ showChrome(true); buildTabbar(); renderSlide(); } else renderModePicker();
  });
  window.scrollTo({top:0});
}

/* ================= tab bar ================= */
function buildTabbar(){
  var el=document.getElementById('tabbar');
  el.innerHTML = TAB_DEFS.map(function(t){
    return '<button class="tab-btn'+(t.id===activeTab?' active':'')+'" data-tab="'+t.id+'">'+t.label+'<span class="tab-count">'+SLIDES[t.id].length+'</span></button>';
  }).join('');
  el.querySelectorAll('.tab-btn').forEach(function(btn){
    btn.addEventListener('click', function(){ activeTab=btn.dataset.tab; buildTabbar(); renderSlide(); window.scrollTo({top:0,behavior:'smooth'}); });
  });
}

/* ================= rendering ================= */
function canProceed(item){ return item.status==='correct'||item.status==='revealed'||item.status==='skipped'; }

function renderSlide(){
  if(!state.tabs[activeTab]){ activeTab=TAB_DEFS[0].id; }
  var ts = state.tabs[activeTab];
  var slides = SLIDES[activeTab];
  if(ts.idx>=slides.length||ts.idx<0) ts.idx=0;
  var idx = ts.idx;
  var slide = slides[idx];
  var item = ts.items[idx];

  var tdef=TAB_DEFS.find(function(t){return t.id===activeTab;});
  document.getElementById('spLabel').textContent = tdef.label+' · Question '+(idx+1)+' of '+slides.length;
  document.getElementById('secSub').textContent = tdef.label+' — '+tdef.sub;
  document.getElementById('spFill').style.width = Math.round(((idx)/(Math.max(slides.length-1,1)))*100)+'%';

  var h='<div class="qcard">';
  if(slide.kind==='mcq' || slide.kind==='ar'){
    h += renderChoiceBody(slide, item, idx);
  } else {
    h += renderBlankBody(slide, item, idx);
  }
  h += '<div class="feedback" id="feedbackBox"></div>';
  if(MODE==='learning' && (item.status==='correct'||item.status==='revealed')) h += solutionHTML(slide);
  h += '</div>';

  document.getElementById('wrap').innerHTML = h;
  wireSlideEvents(slide, item, idx);
  restoreFeedback(item);
  renderNavbar(item);
  updateFab();
  saveState();
}

function solutionHTML(slide){
  if(!slide.sol) return '';
  return '<div class="solution"><div class="sol-h">Solution</div>'+slide.sol.split('\n').map(function(l){ return '<div class="sol-line">'+fr(esc(l))+'</div>'; }).join('')+'</div>';
}
var LETTERS=['a','b','c','d'];
function chosenHTML(slide,item){
  var opts = slide.kind==='mcq' ? slide.opts : AR_OPTIONS;
  if(item.choice===undefined) return '';
  var ok=item.choice===slide.correct;
  var h='<div class="chosen '+(ok?'ok':'bad')+'"><b>Your answer:</b> ('+LETTERS[item.choice]+') '+fr(esc(opts[item.choice]))+(ok?' ✓':' ✗')+'</div>';
  if(!ok) h+='<div class="chosen ok"><b>Correct answer:</b> ('+LETTERS[slide.correct]+') '+fr(esc(opts[slide.correct]))+'</div>';
  return h;
}
function renderChoiceBody(slide, item, idx){
  var h='<div class="qhead"><div class="qnum">'+(idx+1)+'</div>';
  if(slide.kind==='mcq'){
    h += '<div class="qtext">'+fr(esc(slide.text))+(slide.tag?'<span class="qtag">'+esc(slide.tag)+'</span>':'')+'</div>';
  } else {
    h += '<div class="qtext"><span class="qtag" style="margin-left:0;margin-right:6px;">A / R</span>Assertion (A): '+fr(esc(slide.a))+'<br>Reason (R): '+fr(esc(slide.r))+(slide.tag?'<span class="qtag">'+esc(slide.tag)+'</span>':'')+'</div>';
  }
  h += '</div>';
  if(slide.fig) h += '<div class="fig">'+slide.fig+'</div>';
  var opts = slide.kind==='mcq' ? slide.opts : AR_OPTIONS;
  if(MODE==='quiz') h += '<div class="quiz-hint">Quiz mode — pick an option. The correct answer is revealed once you finish this tab.</div>';
  var locked = MODE==='learning' && (item.status==='correct' || item.status==='revealed');
  h += '<div class="options">';
  opts.forEach(function(opt,i){
    var cls='opt';
    if(locked){
      if(i===slide.correct) cls+=' is-correct';
      else if(item.choice===i) cls+=' is-wrong';
      cls+=' locked';
    }
    if(item.choice===i) cls+=' is-chosen';
    h += '<label class="'+cls+'"><input type="radio" name="choice" value="'+i+'" '+(item.choice===i?'checked':'')+' '+(locked?'disabled':'')+'> <span class="opt-l">('+LETTERS[i]+')</span> <span class="opt-t">'+fr(esc(opt))+'</span>'+(item.choice===i?'<span class="opt-tag">'+(locked?(i===slide.correct?'Your answer ✓':'Your answer ✗'):'Selected')+'</span>':'')+'</label>';
  });
  h += '</div>';
  if(locked) h += chosenHTML(slide,item);
  return h;
}

function renderBlankBody(slide, item, idx){
  var h='<div class="qhead"><div class="qnum">'+(idx+1)+'</div><div class="qtext">';
  if(slide.kind==='case'){ h += '<b>'+esc(slide.title)+'.</b> '+esc(slide.body); }
  else { h += fr(esc(slide.p)); }
  h += (slide.tag?'<span class="qtag">'+esc(slide.tag)+'</span>':'')+'</div>';
  if(slide.marks) h += '<div class="marks-pill">'+slide.marks+'</div>';
  h += '</div>';
  if(slide.fig) h += '<div class="fig">'+slide.fig+'</div>';

  var total = slide.flat.length;
  var hasExpr = slide.flat.some(function(s){ return s.expr===true; });
  var hasFrac = slide.flat.some(function(s){ return ['fv','fe','fl','fm','fi','flist'].indexOf(s.expr)>=0; });
  var blankCount=0; slide.flat.forEach(function(s){ blankCount+=Object.keys(s.a).length; });

  if(MODE==='quiz'){
    h += '<div class="step-badge">'+blankCount+' blank'+(blankCount===1?'':'s')+' in this question</div>';
    h += '<div class="quiz-hint">Quiz mode — fill in what you can. Correct answers are revealed once you finish this tab.</div>';
    if(hasFrac) h += '<div class="quiz-hint">Type fractions like <b>3/4</b> and mixed numbers like <b>2 3/4</b> (whole number, space, fraction).</div>';
    if(hasExpr) h += '<div class="quiz-hint">Type expressions like <b>(P-2w)/2</b>, <b>2A/b</b> or <b>V/(pi*r^2)</b>. Use ^ for powers and pi for π. Any equivalent form is accepted.</div>';
    h += '<div class="steps">';
    for(var qi=0; qi<total; qi++){
      var qstep = slide.flat[qi];
      var qss = item.stepStates[qi];
      if(qstep.partLabel) h += '<div class="subpart-label">'+esc(qstep.partLabel)+'</div>';
      if(qstep.orDivider) h += '<div class="or-divider">OR</div>';
      var qline = fr(qstep.t);
      Object.keys(qstep.a).forEach(function(bkey){
        var val = qss.inputs[bkey]||'';
        var inp='<input class="blank-input'+(['fv','fe','fl','fm','fi','dec'].indexOf(qstep.expr)>=0?' fr':(qstep.expr==='flist'||qstep.expr==='dlist')?' wide':qstep.expr===true?' expr':(qstep.expr==='words'||qstep.expr==='list'||qstep.expr==='expanded'||qstep.expr==='set'||qstep.expr==='primes'?' wide':''))+'" data-step="'+qi+'" data-bkey="'+bkey+'" value="'+esc(val)+'">';
        qline = qline.replace('__'+bkey+'__', inp);
      });
      if(qstep.fig) h += '<div class="fig">'+qstep.fig+'</div>';
      h += '<div class="step-line">'+qline+'</div>';
    }
    h += '</div>';
    return h;
  }

  if(hasFrac) h += '<div class="quiz-hint">Type fractions like <b>3/4</b> and mixed numbers like <b>2 3/4</b> (whole number, space, fraction).</div>';
  if(hasExpr) h += '<div class="quiz-hint">Type expressions like <b>(P-2w)/2</b>, <b>2A/b</b> or <b>V/(pi*r^2)</b>. Use ^ for powers and pi for π. Any equivalent form is accepted.</div>';
  var locked = item.status==='correct' || item.status==='revealed';
  var upto = locked ? total-1 : item.curStep;
  h += '<div class="step-badge">Step '+(Math.min(item.curStep,total-1)+1)+' of '+total+'</div>';
  h += '<div class="steps">';
  for(var i=0;i<=upto;i++){
    var step = slide.flat[i];
    var ss = item.stepStates[i];
    if(step.partLabel) h += '<div class="subpart-label">'+esc(step.partLabel)+'</div>';
    if(step.orDivider) h += '<div class="or-divider">OR</div>';
    var resolved = ss.status==='correct' || ss.status==='revealed';
    var line = fr(step.t);
    Object.keys(step.a).forEach(function(bkey){
      var fs = ss.inputs['fs_'+bkey];
      var cls = fs==='correct'?'is-correct':(fs==='wrong'?'is-wrong':'');
      var val = ss.inputs[bkey]||'';
      var dis = resolved ? 'disabled':'';
      var inp='<input class="blank-input '+cls+(['fv','fe','fl','fm','fi','dec'].indexOf(step.expr)>=0?' fr':(step.expr==='flist'||step.expr==='dlist')?' wide':step.expr===true?' expr':(step.expr==='words'||step.expr==='list'||step.expr==='expanded'||step.expr==='set'||step.expr==='primes'?' wide':''))+'" data-step="'+i+'" data-bkey="'+bkey+'" value="'+esc(val)+'" '+dis+'>';
      line = line.replace('__'+bkey+'__', inp);
    });
    if(step.fig) h += '<div class="fig">'+step.fig+'</div>';
    h += '<div class="step-line'+(resolved?' resolved':'')+'">'+line+'</div>';
    if(ss.status==='revealed'){
      var reveals=[];
      Object.keys(step.a).forEach(function(bkey){ reveals.push(bkey+' = '+esc(step.a[bkey])); });
      h += '<div class="reveal-note">correct: '+reveals.join(', ')+'</div>';
    }
  }
  h += '</div>';
  return h;
}

var __flash=null;
function restoreFeedback(item){
  var fb=document.getElementById('feedbackBox'); if(!fb) return;
  if(__flash){ fb.className='feedback show '+__flash.c; fb.innerHTML=__flash.h; __flash=null; return; }
  if(MODE==='quiz'){ fb.className='feedback'; fb.innerHTML=''; return; }
  if(item.status==='correct'){ fb.className='feedback show ok'; fb.innerHTML='<b>All done — correct!</b>'; }
  else if(item.status==='revealed'){ fb.className='feedback show reveal'; fb.innerHTML='<b>Answer revealed above.</b> Move on whenever you’re ready.'; }
  else if(item.status==='skipped'){ fb.className='feedback show retry'; fb.innerHTML='Skipped — revisit it anytime from the Question Palette.'; }
  else { fb.className='feedback'; fb.innerHTML=''; }
}

function slideIsAnswered(slide,item){
  if(slide.kind==='mcq'||slide.kind==='ar') return item.choice!==undefined;
  return item.stepStates.some(function(ss){ return Object.keys(ss.inputs).some(function(k){ return k.indexOf('fs_')!==0 && ss.inputs[k] && String(ss.inputs[k]).trim()!==''; }); });
}
function renderNavbar(item){
  var ts = state.tabs[activeTab];
  var slides = SLIDES[activeTab];
  var slide = slides[ts.idx];
  var isLast = ts.idx === slides.length-1;
  var h='';
  h += '<button class="btn" id="btnPrev" '+(ts.idx===0?'disabled':'')+'>&larr; Previous</button>';

  if(MODE==='quiz'){
    h += '<button class="btn" id="btnSkip">Skip</button>';
    h += '<span class="spacer"></span>';
    h += '<button class="btn btn-primary" id="btnNext">'+(isLast?'Finish':'Next →')+'</button>';
  } else {
    h += '<button class="btn" id="btnSkip" '+(item.status!=='unanswered'?'disabled':'')+'>Skip</button>';
    h += '<span class="spacer"></span>';
    h += '<button class="btn btn-primary" id="btnCheck" '+(item.status!=='unanswered'?'disabled':'')+'>Check</button>';
    h += '<button class="btn btn-primary" id="btnNext" '+(canProceed(item)?'':'disabled')+'>'+(isLast?'Finish':'Next →')+'</button>';
  }
  document.getElementById('navbarInner').innerHTML = h;

  document.getElementById('btnPrev').addEventListener('click', function(){ if(ts.idx>0){ ts.idx--; renderSlide(); } });

  if(MODE==='quiz'){
    document.getElementById('btnSkip').addEventListener('click', function(){
      item.status='skipped';
      advanceQuiz(ts, slides);
    });
    document.getElementById('btnNext').addEventListener('click', function(){
      item.status = slideIsAnswered(slide,item) ? 'answered' : 'unanswered';
      advanceQuiz(ts, slides);
    });
  } else {
    document.getElementById('btnSkip').addEventListener('click', function(){
      if(item.status==='unanswered'){ item.status='skipped'; renderSlide(); }
    });
    document.getElementById('btnNext').addEventListener('click', function(){
      if(!canProceed(item)) return;
      if(ts.idx < slides.length-1){ ts.idx++; ts.maxReached=Math.max(ts.maxReached, ts.idx); renderSlide(); }
      else { renderFinished(); }
    });
    document.getElementById('btnCheck').addEventListener('click', function(){ handleCheck(); });
  }
}
function advanceQuiz(ts, slides){
  if(ts.idx < slides.length-1){ ts.idx++; ts.maxReached=Math.max(ts.maxReached, ts.idx); renderSlide(); }
  else { renderFinished(); }
}

function wireSlideEvents(slide, item, idx){
  document.querySelectorAll('input[type="radio"][name="choice"]').forEach(function(r){
    r.addEventListener('change', function(){ item.choice=parseInt(r.value,10); saveState();
      document.querySelectorAll('.opt').forEach(function(l){ l.classList.remove('is-chosen'); var t=l.querySelector('.opt-tag'); if(t) t.remove(); });
      var lab=r.closest('.opt'); lab.classList.add('is-chosen'); var tg=document.createElement('span'); tg.className='opt-tag'; tg.textContent='Selected'; lab.appendChild(tg); });
  });
  document.querySelectorAll('.blank-input').forEach(function(inp){
    inp.addEventListener('input', function(){
      var si=parseInt(inp.dataset.step,10), bk=inp.dataset.bkey;
      item.stepStates[si].inputs[bk]=inp.value;
      saveState();
    });
  });
}

function handleCheck(){
  var ts = state.tabs[activeTab];
  var slide = SLIDES[activeTab][ts.idx];
  var item = ts.items[ts.idx];
  var fb = document.getElementById('feedbackBox');

  if(slide.kind==='mcq' || slide.kind==='ar'){
    if(item.choice===undefined){ fb.className='feedback show err'; fb.innerHTML='Please choose an option first.'; return; }
    var ok = item.choice===slide.correct;
    if(ok){
      item.status='correct'; playSuccess();
      fb.className='feedback show ok'; fb.innerHTML='<b>Correct!</b>';
    } else {
      item.attempts=(item.attempts||0)+1;
      if(item.attempts>=2){ item.status='revealed'; playReveal(); }
      else { playWrong(); fb.className='feedback show retry'; fb.innerHTML='<b>Not quite — try again</b> (attempt 1 of 2) <span class="attempts-dots"><span class="used"></span><span></span></span>'; __flash={c:'retry',h:'<b>Not quite — try again</b> (attempt 1 of 2) <span class="attempts-dots"><span class="used"></span><span></span></span>'}; }
    }
    renderSlide();
    return;
  }

  // blank / case
  var step = slide.flat[item.curStep];
  var ss = item.stepStates[item.curStep];
  var blanks = Object.keys(step.a);
  var missing = blanks.some(function(k){ return !ss.inputs[k] || String(ss.inputs[k]).trim()===''; });
  if(missing){ fb.className='feedback show err'; fb.innerHTML='Fill in every blank in this step before checking.'; return; }

  var allGood=true;
  blanks.forEach(function(k){
    var good=answerMatches(ss.inputs[k], step.a[k], step.accept, step.expr);
    ss.inputs['fs_'+k]=good?'correct':'wrong';
    if(!good) allGood=false;
  });

  if(allGood){
    ss.status='correct'; playSuccess();
    advanceStepOrFinish(item, slide);
  } else {
    ss.attempts=(ss.attempts||0)+1;
    if(ss.attempts>=2){
      ss.status='revealed'; playReveal();
      advanceStepOrFinish(item, slide);
    } else {
      playWrong();
      fb.className='feedback show retry';
      fb.innerHTML='<b>Not quite — try again</b> (attempt 1 of 2) <span class="attempts-dots"><span class="used"></span><span></span></span>'; __flash={c:'retry',h:'<b>Not quite — try again</b> (attempt 1 of 2) <span class="attempts-dots"><span class="used"></span><span></span></span>'};
      renderSlide();
      return;
    }
  }
  renderSlide();
}

function advanceStepOrFinish(item, slide){
  var total = slide.flat.length;
  var hasExpr = slide.flat.some(function(s){ return s.expr===true; });
  var hasFrac = slide.flat.some(function(s){ return ['fv','fe','fl','fm','fi','flist'].indexOf(s.expr)>=0; });
  if(item.curStep < total-1){
    item.curStep++;
  } else {
    var anyRevealed = item.stepStates.some(function(ss){ return ss.status==='revealed'; });
    item.status = anyRevealed ? 'revealed' : 'correct';
  }
}

/* ================= palette ================= */
var overlay=document.getElementById('overlay');
function statusOf(tabId,i){
  var ts=state.tabs[tabId];
  if(i>ts.maxReached) return 'locked';
  if(i===ts.idx) return 'current';
  return ts.items[i].status==='unanswered' ? 'locked' : ts.items[i].status;
}
function buildPalette(){
  var slides=SLIDES[activeTab];
  document.getElementById('paletteTitle').textContent = TAB_DEFS.find(function(t){return t.id===activeTab;}).label+' · Question palette';
  var body=document.getElementById('paletteBody');
  var html='';
  for(var i=0;i<slides.length;i++){
    html += '<div class="chip" data-status="'+statusOf(activeTab,i)+'" data-idx="'+i+'">'+(i+1)+'</div>';
  }
  body.innerHTML = html;
  body.querySelectorAll('.chip').forEach(function(chip){
    chip.addEventListener('click', function(){
      var i=parseInt(chip.dataset.idx,10);
      var ts=state.tabs[activeTab];
      if(i>ts.maxReached){ showToast('Finish the earlier questions to unlock this one.'); return; }
      ts.idx=i; closePalette(); renderSlide();
    });
  });
}
function openPalette(){ buildPalette(); overlay.classList.add('show'); }
function closePalette(){ overlay.classList.remove('show'); }
var toastTimer;
function showToast(msg){
  var t=document.getElementById('toast'); t.textContent=msg; t.classList.add('show');
  clearTimeout(toastTimer); toastTimer=setTimeout(function(){ t.classList.remove('show'); },2200);
}
document.getElementById('paletteFab').addEventListener('click', openPalette);
document.getElementById('paletteClose').addEventListener('click', closePalette);
overlay.addEventListener('click', function(e){ if(e.target===overlay) closePalette(); });

function updateFab(){
  var slides=SLIDES[activeTab];
  var done=state.tabs[activeTab].items.filter(function(it){ return it.status==='correct'||it.status==='revealed'||it.status==='skipped'; }).length;
  document.getElementById('fabBadge').textContent = done+'/'+slides.length;
}

/* ================= overall progress + finish ================= */
function updateChapterProgress(){
  var total=0, done=0;
  TAB_DEFS.forEach(function(td){
    state.tabs[td.id].items.forEach(function(it){
      total++;
      if(it.status==='correct'||it.status==='revealed'||it.status==='skipped') done++;
    });
  });
  var pct = total>0 ? Math.round((done/total)*100) : 0;
  document.getElementById('cpFill').style.width=pct+'%';
  document.getElementById('cpLabel').textContent=pct+'% complete';
}
function isSlideCorrect(tabId,i){
  var slide=SLIDES[tabId][i], item=state.tabs[tabId].items[i];
  if(slide.kind==='mcq'||slide.kind==='ar') return item.choice===slide.correct;
  return slide.flat.every(function(step,si){
    var ss=item.stepStates[si];
    return Object.keys(step.a).every(function(k){ return answerMatches(ss.inputs[k], step.a[k], step.accept, step.expr); });
  });
}
function isSlideAttempted(tabId,i){
  var slide=SLIDES[tabId][i], item=state.tabs[tabId].items[i];
  if(slide.kind==='mcq'||slide.kind==='ar') return item.choice!==undefined;
  return slide.flat.some(function(step,si){
    var ss=item.stepStates[si];
    return Object.keys(step.a).some(function(k){ return ss.inputs[k] && String(ss.inputs[k]).trim()!==''; });
  });
}
function slideLabel(slide){
  var t = slide.kind==='case' ? slide.title : (slide.kind==='ar' ? slide.a : (slide.p||slide.text||''));
  t = String(t);
  return t.length>90 ? t.slice(0,90)+'…' : t;
}
function slideAnswerText(slide, item, correctSide){
  if(slide.kind==='mcq'||slide.kind==='ar'){
    var opts = slide.kind==='mcq' ? slide.opts : AR_OPTIONS;
    if(correctSide) return '('+LETTERS[slide.correct]+') '+opts[slide.correct];
    return item.choice!==undefined ? '('+LETTERS[item.choice]+') '+opts[item.choice] : '— not attempted —';
  }
  return slide.flat.map(function(step,si){
    var ss=item.stepStates[si];
    return Object.keys(step.a).map(function(k){
      return correctSide ? step.a[k] : (ss.inputs[k] || '—');
    }).join(', ');
  }).join('  |  ');
}

function renderFinished(){
  if(MODE==='quiz'){ renderQuizResults(); return; }
  var ts=state.tabs[activeTab];
  var correct=ts.items.filter(function(i){return i.status==='correct';}).length;
  var revealed=ts.items.filter(function(i){return i.status==='revealed';}).length;
  var skipped=ts.items.filter(function(i){return i.status==='skipped';}).length;
  var h='<div class="qcard done-card"><div class="big">✨</div><h2>Tab complete</h2>';
  h+='<p style="color:var(--ink-soft);font-size:14px;">You worked through all '+ts.items.length+' questions in this tab.</p>';
  if(!ts.recorded){ ts.recorded=true; addRecord('learning', activeTab, correct, revealed, skipped, ts.items.length); }
  h+='<div class="score-pills">'+
     '<span class="score-pill" style="background:var(--success-soft);color:var(--success);">'+correct+' correct</span>'+
     '<span class="score-pill" style="background:var(--danger-soft);color:var(--danger);">'+revealed+' revealed</span>'+
     '<span class="score-pill" style="background:var(--gold-soft);color:var(--retry-text);">'+skipped+' skipped</span></div>'+
     '<button class="btn btn-primary" id="btnReview">Review from question 1</button></div>';
  document.getElementById('wrap').innerHTML=h;
  document.getElementById('navbarInner').innerHTML='';
  document.getElementById('btnReview').addEventListener('click', function(){ ts.idx=0; ts.recorded=false; renderSlide(); });
  updateChapterProgress(); saveState();
}

function renderQuizResults(){
  var ts=state.tabs[activeTab];
  var slides=SLIDES[activeTab];
  var correctCount=0, attemptedCount=0;
  var rowsHtml = slides.map(function(slide,i){
    var item=ts.items[i];
    var ok=isSlideCorrect(activeTab,i);
    var att=isSlideAttempted(activeTab,i);
    if(ok) correctCount++;
    if(att) attemptedCount++;
    var tagCls = ok?'ok':(att?'bad':'na');
    var tagText = ok?'Correct':(att?'Incorrect':'Not attempted');
    var row='<div class="review-row">';
    row+='<span class="review-tag '+tagCls+'">Q'+(i+1)+' · '+tagText+'</span>';
    row+='<div class="review-q">'+fr(esc(slideLabel(slide)))+'</div>';
    row+='<div class="review-ans"><b>Your answer:</b> '+fr(esc(slideAnswerText(slide,item,false)))+'</div>';
    if(!ok) row+='<div class="review-ans" style="color:var(--success);"><b>Correct answer:</b> '+fr(esc(slideAnswerText(slide,item,true)))+'</div>';
    if(slide.sol) row+='<details class="rev-sol"><summary>Show solution</summary>'+solutionHTML(slide)+'</details>';
    row+='</div>';
    return row;
  }).join('');

  addRecord('quiz', activeTab, correctCount, 0, 0, slides.length);
  var h='<div class="qcard done-card" style="text-align:left;">';
  h+='<div style="text-align:center;"><div class="big">🏁</div><h2>Quiz complete</h2>';
  h+='<p style="color:var(--ink-soft);font-size:14px;">'+correctCount+' / '+slides.length+' correct · '+attemptedCount+' attempted</p></div>';
  h+='<div style="margin-top:16px;">'+rowsHtml+'</div>';
  h+='<div style="text-align:center;margin-top:6px;"><button class="btn btn-primary" id="btnReview">Review from question 1</button></div>';
  h+='</div>';
  document.getElementById('wrap').innerHTML=h;
  document.getElementById('navbarInner').innerHTML='';
  document.getElementById('btnReview').addEventListener('click', function(){ ts.idx=0; renderSlide(); });
  playSuccess();
  updateChapterProgress(); saveState();
}

/* ================= mode picker ================= */
function updateModePill(){
  var btn=document.getElementById('modePill');
  if(!btn) return;
  btn.textContent = MODE==='quiz' ? '📝 Quiz Mode · switch' : '📘 Learning Sheet · switch';
}
function showChrome(show){
  document.querySelector('.tabbar').style.display = show?'':'none';
  document.querySelector('.slide-progress').style.display = show?'':'none';
  document.querySelector('.navbar').style.display = show?'':'none';
  document.getElementById('paletteFab').style.display = show?'':'none';
}
function renderModePicker(){
  showChrome(false);
  var wrap=document.getElementById('wrap');
  wrap.innerHTML =
    '<div class="mode-pick">'+
      '<div class="mode-card" data-pick="learning"><div class="mode-icon">📘</div><h3>Learning Sheet</h3>'+
      '<p>Work through each question step by step with instant feedback — two tries, then the correct value is revealed right there so you can keep moving.</p></div>'+
      '<div class="mode-card" data-pick="quiz"><div class="mode-icon">📝</div><h3>Quiz Mode</h3>'+
      '<p>Attempt every question with no hints along the way. Your score and the full answer key are shown together once you finish the tab — just like the real exam.</p></div>'+
    '</div>';
  wrap.querySelectorAll('[data-pick]').forEach(function(card){
    card.addEventListener('click', function(){
      setMode(card.dataset.pick);
      document.getElementById('modePill').hidden=false;
      updateModePill();
      showChrome(true);
      buildTabbar();
      renderSlide();
    });
  });
}
document.getElementById('modePill').addEventListener('click', function(){
  if(!appState.mode){ return; }
  setMode(appState.mode==='quiz' ? 'learning' : 'quiz');
  updateModePill();
  showChrome(true);
  buildTabbar();
  renderSlide();
});

/* ================= boot ================= */
var _origRenderSlide = renderSlide;
renderSlide = function(){ _origRenderSlide(); updateChapterProgress(); updateModePill(); };

renderLogin();
})();
</script>
</body>
</html>
  
