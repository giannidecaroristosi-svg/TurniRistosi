[TurniRistosi.html](https://github.com/user-attachments/files/27755806/TurniRistosi.html)
<!DOCTYPE html>
<html lang="it">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>TurniRistosi — Gestione Turni Ristoranti</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=DM+Sans:wght@300;400;500;600&family=DM+Mono:wght@400;500&display=swap" rel="stylesheet">
<style>
:root {
  --bg:       #0a1a0a;
  --bg2:      #0f2310;
  --bg3:      #153018;
  --bg4:      #1c3d1e;
  --border:   #1e4a20;
  --border2:  #2a6b2c;
  --text:     #e8f5e9;
  --text2:    #81c784;
  --text3:    #4caf50;
  --accent:   #FFC72C;
  --accent2:  #e6b000;
  --accent-bg:#2a2000;
  --green:    #27ae60;
  --green-bg: #0a2010;
  --coral:    #f97066;
  --coral-bg: #2a1215;
  --amber:    #FFC72C;
  --amber-bg: #2a2000;
  --teal:     #26c6da;
  --teal-bg:  #003d45;
  --pink:     #f472b6;
  --pink-bg:  #250d1e;
  --r:        8px;
  --r2:       12px;
  --r3:       16px;
}
*{box-sizing:border-box;margin:0;padding:0}
body{font-family:'DM Sans',system-ui,sans-serif;background:var(--bg);color:var(--text);font-size:14px;min-height:100vh;overflow-x:hidden}
::-webkit-scrollbar{width:5px;height:5px}
::-webkit-scrollbar-track{background:var(--bg2)}
::-webkit-scrollbar-thumb{background:var(--border2);border-radius:3px}

/* TOPBAR */
.topbar{display:flex;align-items:center;gap:10px;padding:0 20px;height:54px;background:var(--bg2);border-bottom:1px solid var(--border);position:sticky;top:0;z-index:100;flex-wrap:wrap}
.logo{font-family:'DM Mono',monospace;font-size:14px;font-weight:500;color:var(--accent);letter-spacing:-0.3px;display:flex;align-items:center;gap:8px;white-space:nowrap}
.logo-dot{width:8px;height:8px;border-radius:50%;background:var(--accent);box-shadow:0 0 8px var(--accent)}
.user-select{background:var(--bg3);border:1px solid var(--border);color:var(--text);font-family:'DM Sans',sans-serif;font-size:13px;padding:5px 10px;border-radius:var(--r);cursor:pointer;outline:none;max-width:200px}
.user-select:focus{border-color:var(--accent)}
.lbadge{font-size:11px;padding:3px 10px;border-radius:20px;font-weight:500;white-space:nowrap;font-family:'DM Mono',monospace;letter-spacing:0.3px}
.lv-ufficio  {background:var(--accent-bg);color:var(--accent);border:1px solid var(--accent2)}
.lv-supervisore{background:var(--green-bg);color:var(--green);border:1px solid #1a5c32}
.lv-direttore{background:var(--coral-bg);color:var(--coral);border:1px solid #5c1a1a}
.lv-mng      {background:var(--teal-bg);color:var(--teal);border:1px solid #0f3832}
.rest-info{font-size:11px;color:var(--text3);white-space:nowrap;overflow:hidden;text-overflow:ellipsis;max-width:200px}
.nav{display:flex;gap:2px;margin-left:auto}
.nav-btn{padding:6px 12px;border:1px solid transparent;border-radius:var(--r);background:transparent;color:var(--text2);font-family:'DM Sans',sans-serif;font-size:12px;cursor:pointer;display:flex;align-items:center;gap:6px;transition:all .15s;white-space:nowrap}
.nav-btn:hover{background:var(--bg3);color:var(--text)}
.nav-btn.active{background:var(--accent-bg);color:var(--accent);border-color:var(--border2)}
.nav-btn svg{width:14px;height:14px;flex-shrink:0}

/* LAYOUT */
.layout{display:flex;height:calc(100vh - 54px)}
.sidebar{width:200px;flex-shrink:0;border-right:1px solid var(--border);background:var(--bg2);padding:16px 12px;display:flex;flex-direction:column;gap:16px;overflow-y:auto}
.main{flex:1;overflow-y:auto;padding:20px}

/* SIDEBAR */
.s-title{font-size:10px;font-weight:600;color:var(--text3);text-transform:uppercase;letter-spacing:1px;margin-bottom:8px}
.shift-legend{display:grid;grid-template-columns:auto 1fr;gap:3px 8px;align-items:center}
.stag{font-size:10px;padding:2px 7px;border-radius:4px;font-weight:600;font-family:'DM Mono',monospace}
.s-ap  {background:#1a2a4a;color:#60a5fa}
.s-m   {background:#0d2318;color:#4ade80}
.s-sw  {background:#1a1d3a;color:#a78bfa}
.s-s   {background:#2a1a08;color:#fbbf24}
.s-n   {background:#2a1215;color:#f87171}
.s-off {background:#1e2030;color:#94a3b8}
.s-pir {background:#2a1215;color:#f97066}
.s-fer {background:#081e1c;color:#2dd4bf}
.s-mal {background:#2a1215;color:#fb923c}
.s-cong{background:#250d1e;color:#f472b6}
.s-label{font-size:10px;color:var(--text3)}
.rest-pill{display:flex;align-items:center;gap:6px;padding:4px 8px;border-radius:var(--r);background:var(--bg3);border:1px solid var(--border);font-size:11px;color:var(--text2);margin-bottom:4px}
.today-block{margin-top:auto;padding:10px;background:var(--bg3);border-radius:var(--r2);border:1px solid var(--border)}
.today-shift{display:flex;align-items:center;gap:6px;margin-top:5px;font-size:12px;color:var(--text2)}
.today-act{font-size:11px;color:var(--text3);margin-top:2px;margin-left:6px;font-style:italic}

/* CALENDAR */
.cal-header{display:flex;align-items:center;justify-content:space-between;margin-bottom:16px;flex-wrap:wrap;gap:10px}
.cal-title{font-family:'DM Mono',monospace;font-size:16px;color:var(--text);font-weight:500}
.cal-nav-row{display:flex;align-items:center;gap:6px}
.cal-nav-btn{width:30px;height:30px;border-radius:var(--r);border:1px solid var(--border);background:var(--bg3);color:var(--text2);cursor:pointer;display:flex;align-items:center;justify-content:center;font-size:14px;transition:all .15s}
.cal-nav-btn:hover{border-color:var(--accent);color:var(--accent)}
.today-btn{padding:0 12px;height:30px;border-radius:var(--r);border:1px solid var(--border);background:var(--bg3);color:var(--text2);cursor:pointer;font-family:'DM Sans',sans-serif;font-size:12px;transition:all .15s}
.today-btn:hover{border-color:var(--accent);color:var(--accent)}
.export-btn{padding:0 14px;height:30px;border-radius:var(--r);border:1px solid #1a5c32;background:var(--green-bg);color:var(--green);cursor:pointer;font-family:'DM Sans',sans-serif;font-size:12px;display:flex;align-items:center;gap:6px;transition:all .15s}
.export-btn:hover{background:#0d2318;border-color:var(--green)}
.cal-grid{display:grid;grid-template-columns:repeat(7,1fr);gap:3px}
.cal-dn{font-size:10px;font-weight:600;color:var(--text3);text-align:center;padding:4px 0;font-family:'DM Mono',monospace;letter-spacing:0.5px}
.cal-day{min-height:82px;background:var(--bg2);border:1px solid var(--border);border-radius:var(--r);padding:6px;cursor:pointer;transition:border-color .15s,background .15s;position:relative;overflow:hidden}
.cal-day:hover{border-color:var(--accent2);background:var(--bg3)}
.cal-day.today{border-color:var(--accent);background:var(--accent-bg)}
.cal-day.other-month{opacity:.3}
.day-num{font-size:11px;font-weight:600;font-family:'DM Mono',monospace;margin-bottom:4px;color:var(--text2)}
.cal-day.today .day-num{color:var(--accent)}
.day-pill{font-size:9px;padding:2px 5px;border-radius:3px;margin-bottom:2px;display:flex;align-items:center;gap:3px;white-space:nowrap;overflow:hidden;text-overflow:ellipsis;font-family:'DM Mono',monospace}
.day-pill-dot{width:4px;height:4px;border-radius:50%;flex-shrink:0}
.day-more{font-size:9px;color:var(--text3);padding:1px 4px}

/* LIST */
.day-card{background:var(--bg2);border:1px solid var(--border);border-radius:var(--r2);margin-bottom:8px;overflow:hidden}
.day-card-header{padding:10px 14px;border-bottom:1px solid var(--border);display:flex;align-items:center;justify-content:space-between;background:var(--bg3)}
.day-card-date{font-family:'DM Mono',monospace;font-size:13px;font-weight:500;color:var(--text)}
.day-card-count{font-size:11px;padding:2px 8px;border-radius:10px;background:var(--accent-bg);color:var(--accent);font-family:'DM Mono',monospace}
.add-day-btn{padding:4px 10px;border-radius:var(--r);border:1px solid var(--border);background:transparent;color:var(--text3);font-size:11px;cursor:pointer;transition:all .15s;display:flex;align-items:center;gap:4px;font-family:'DM Sans',sans-serif}
.add-day-btn:hover{border-color:var(--accent);color:var(--accent)}
.day-card-body{padding:10px 14px;display:flex;flex-direction:column;gap:5px}
.entry-row{display:flex;align-items:center;gap:8px;padding:7px 10px;border-radius:var(--r);border:1px solid var(--border);background:var(--bg);font-size:12px;flex-wrap:wrap;gap:6px}
.entry-avatar{width:26px;height:26px;border-radius:50%;display:flex;align-items:center;justify-content:center;font-size:10px;font-weight:600;flex-shrink:0;font-family:'DM Mono',monospace}
.entry-name{font-weight:500;flex:1;min-width:100px;color:var(--text)}
.entry-rest-tag{font-size:10px;padding:2px 8px;border-radius:4px;background:var(--coral-bg);color:var(--coral);border:1px solid #3d1a1a;display:flex;align-items:center;gap:4px;white-space:nowrap}
.entry-act-tag{font-size:10px;padding:2px 8px;border-radius:4px;display:flex;align-items:center;gap:4px;white-space:nowrap;font-style:italic}
.entry-sub{font-size:10px;color:var(--text3);font-style:italic}
.del-btn{background:none;border:none;cursor:pointer;color:var(--text3);font-size:16px;padding:0 2px;line-height:1;transition:color .15s;margin-left:auto;flex-shrink:0}
.del-btn:hover{color:var(--coral)}
.empty-day{font-size:12px;color:var(--text3);font-style:italic;padding:6px 0;text-align:center}

/* MODAL */
.modal-overlay{position:fixed;inset:0;background:rgba(0,0,0,.7);display:flex;align-items:center;justify-content:center;z-index:200;padding:20px;backdrop-filter:blur(4px)}
.modal{background:var(--bg2);border:1px solid var(--border2);border-radius:var(--r3);padding:24px;width:420px;max-width:100%;max-height:90vh;overflow-y:auto}
.modal-title{font-size:15px;font-weight:600;margin-bottom:18px;display:flex;align-items:center;gap:8px;color:var(--text)}
.modal-title svg{color:var(--accent)}
.frow{margin-bottom:12px;display:flex;flex-direction:column;gap:5px}
.frow label{font-size:11px;font-weight:600;color:var(--text3);text-transform:uppercase;letter-spacing:0.5px}
.frow input,.frow select,.frow textarea{background:var(--bg3);border:1px solid var(--border);color:var(--text);font-family:'DM Sans',sans-serif;font-size:13px;padding:8px 10px;border-radius:var(--r);outline:none;width:100%;transition:border-color .15s}
.frow input:focus,.frow select:focus,.frow textarea:focus{border-color:var(--accent)}
.frow select option{background:var(--bg3)}
.frow textarea{min-height:60px;resize:vertical}
.section-sep{height:1px;background:var(--border);margin:12px 0}
.section-mini-label{font-size:10px;font-weight:600;color:var(--text3);text-transform:uppercase;letter-spacing:0.8px;margin-bottom:10px}
.mact{display:flex;gap:8px;justify-content:flex-end;margin-top:18px}
.btn-primary{background:var(--accent);color:var(--bg);border:none;border-radius:var(--r);padding:8px 20px;font-family:'DM Sans',sans-serif;font-size:13px;font-weight:600;cursor:pointer;transition:opacity .15s}
.btn-primary:hover{opacity:.85}
.btn-secondary{background:transparent;color:var(--text2);border:1px solid var(--border);border-radius:var(--r);padding:8px 16px;font-family:'DM Sans',sans-serif;font-size:13px;cursor:pointer;transition:all .15s}
.btn-secondary:hover{border-color:var(--border2);color:var(--text)}
.warn-msg{font-size:11px;color:var(--coral);margin-top:3px}

/* ANAGRAFICHE */
.tabs{display:flex;gap:4px;margin-bottom:16px;flex-wrap:wrap}
.tab-btn{padding:6px 14px;border:1px solid var(--border);border-radius:var(--r);background:transparent;color:var(--text2);font-family:'DM Sans',sans-serif;font-size:12px;cursor:pointer;transition:all .15s;display:flex;align-items:center;gap:6px}
.tab-btn:hover{border-color:var(--border2);color:var(--text)}
.tab-btn.active{background:var(--accent-bg);color:var(--accent);border-color:var(--border2)}
.anag-header{display:flex;align-items:center;justify-content:space-between;margin-bottom:14px}
.anag-section-title{font-family:'DM Mono',monospace;font-size:13px;font-weight:500;color:var(--text);display:flex;align-items:center;gap:8px}
.add-btn{padding:6px 14px;border-radius:var(--r);border:1px solid var(--accent2);background:var(--accent-bg);color:var(--accent);font-family:'DM Sans',sans-serif;font-size:12px;cursor:pointer;display:flex;align-items:center;gap:6px;transition:all .15s}
.add-btn:hover{background:var(--accent2)}
.anag-group{margin-bottom:16px}
.anag-group-label{font-size:10px;font-weight:600;color:var(--text3);text-transform:uppercase;letter-spacing:1px;padding:4px 0;border-bottom:1px solid var(--border);margin-bottom:8px;display:flex;align-items:center;gap:6px}
.anag-row{display:flex;align-items:center;gap:8px;padding:8px 10px;border-radius:var(--r);border:1px solid var(--border);background:var(--bg2);margin-bottom:5px;flex-wrap:wrap}
.anag-name{font-weight:500;flex:1;min-width:120px}
.anag-meta{font-size:11px;color:var(--text3);display:flex;flex-wrap:wrap;gap:4px;align-items:center}
.btn-icon{width:28px;height:28px;border-radius:var(--r);border:1px solid var(--border);background:transparent;color:var(--text3);cursor:pointer;display:flex;align-items:center;justify-content:center;transition:all .15s;flex-shrink:0}
.btn-icon:hover{border-color:var(--accent);color:var(--accent)}
.btn-icon.danger:hover{border-color:var(--coral);color:var(--coral)}
.tag-small{font-size:10px;padding:1px 7px;border-radius:3px;font-family:'DM Mono',monospace}

/* COLOR SWATCHES */
.color-swatches{display:flex;gap:6px;flex-wrap:wrap;margin-top:4px}
.color-swatch{width:24px;height:24px;border-radius:50%;cursor:pointer;border:2px solid transparent;transition:border-color .15s,transform .1s}
.color-swatch:hover{transform:scale(1.1)}
.color-swatch.selected{border-color:var(--text)!important}
.act-preview{display:inline-flex;align-items:center;gap:5px;font-size:11px;padding:3px 10px;border-radius:4px;margin-top:6px;font-style:italic}

/* FLAG */
.flag-section{margin-bottom:18px}
.flag-group-label{font-size:10px;font-weight:600;color:var(--text3);text-transform:uppercase;letter-spacing:0.8px;padding:6px 0;border-bottom:1px solid var(--border);margin-bottom:8px;display:flex;align-items:center;gap:8px}
.flag-item{display:flex;align-items:center;gap:8px;padding:6px 0;border-bottom:1px solid var(--border);font-size:12px}
.flag-item:last-child{border-bottom:none}
.flag-item label{cursor:pointer;flex:1;color:var(--text2)}
.flag-meta{font-size:10px;color:var(--text3)}
input[type=checkbox]{accent-color:var(--accent);cursor:pointer;width:14px;height:14px}

/* EXPORT */
.export-card{background:var(--bg2);border:1px solid var(--border);border-radius:var(--r2);padding:20px;margin-bottom:12px}
.export-card-title{font-size:13px;font-weight:600;margin-bottom:14px;display:flex;align-items:center;gap:8px;color:var(--text)}
.export-grid{display:grid;grid-template-columns:1fr 1fr 1fr;gap:10px;margin-bottom:14px}
.export-actions{display:flex;gap:8px;flex-wrap:wrap}
.dl-btn{padding:8px 16px;border-radius:var(--r);border:none;font-family:'DM Sans',sans-serif;font-size:12px;font-weight:600;cursor:pointer;display:flex;align-items:center;gap:6px;transition:opacity .15s}
.dl-btn:hover{opacity:.85}
.dl-csv{background:var(--green);color:#0a1a10}
.dl-pdf{background:var(--accent);color:var(--bg)}
.preview-box{background:var(--bg);border:1px solid var(--border);border-radius:var(--r);padding:12px;margin-top:10px;font-size:12px;color:var(--text2)}

/* STATUS BAR */
.statusbar{position:fixed;bottom:0;left:0;right:0;height:26px;background:var(--bg2);border-top:1px solid var(--border);display:flex;align-items:center;padding:0 16px;font-size:11px;color:var(--text3);font-family:'DM Mono',monospace;z-index:100}
.status-dot{width:6px;height:6px;border-radius:50%;background:var(--green);margin-right:8px;flex-shrink:0}

/* CHECK GRID */
.check-grid{display:grid;grid-template-columns:1fr 1fr;gap:5px;margin-top:4px}
.check-item{display:flex;align-items:center;gap:6px;font-size:12px;color:var(--text2);padding:3px 0}

/* MNG CARDS */
.mng-card{background:var(--bg3);border:1px solid var(--border);border-radius:var(--r2);padding:12px;margin-bottom:8px;display:flex;align-items:center;gap:10px}
.mng-avatar{width:38px;height:38px;border-radius:50%;background:var(--teal-bg);color:var(--teal);display:flex;align-items:center;justify-content:center;font-size:13px;font-weight:700;font-family:'DM Mono',monospace;border:1px solid #0f3832;flex-shrink:0}
.mng-info{flex:1}
.mng-name{font-weight:600;font-size:13px;color:var(--text)}
.mng-tel{font-size:11px;color:var(--text3);margin-top:2px;display:flex;align-items:center;gap:5px}

/* EMPTY STATE */
.empty-state{text-align:center;padding:40px 20px;color:var(--text3)}
.empty-icon{font-size:40px;margin-bottom:12px}
.empty-text{font-size:13px}

/* VISITS BLOCK */
.visits-block{border:1px solid var(--border);border-radius:var(--r2);padding:10px;background:var(--bg3)}
.visit-row{display:grid;grid-template-columns:1fr 1fr;gap:8px;margin-bottom:8px;padding-bottom:8px;border-bottom:1px solid var(--border)}
.visit-row:last-child{border-bottom:none;margin-bottom:0;padding-bottom:0}
.visit-num{font-size:10px;font-weight:600;color:var(--text3);text-transform:uppercase;letter-spacing:0.5px;margin-bottom:5px;grid-column:1/-1}
.visit-entry-tags{display:flex;flex-wrap:wrap;gap:4px;margin-top:3px}

/* ── MOBILE RESPONSIVE ── */
@media (max-width: 768px) {

  /* Topbar compatta */
  .topbar{height:auto;padding:6px 10px;gap:6px}
  .logo{font-size:13px}
  .rest-info{display:none}
  .user-select{font-size:12px;padding:4px 7px;max-width:130px}
  .nav-btn{padding:5px 7px;font-size:11px;gap:3px}
  .nav-btn svg{width:13px;height:13px}

  /* Layout: sidebar nascosta su mobile, nav bottom */
  .layout{flex-direction:column;height:auto;min-height:calc(100vh - 80px)}
  .sidebar{display:none}
  .main{padding:10px;overflow-y:visible}

  /* Barra navigazione bottom su mobile */
  #appShell .topbar .nav{
    position:fixed;bottom:26px;left:0;right:0;
    background:var(--bg2);border-top:1px solid var(--border);
    padding:6px 4px;justify-content:space-around;margin:0;
    z-index:99;gap:0;
  }
  .nav-btn{flex-direction:column;gap:2px;padding:4px 8px;font-size:10px;border:none;border-radius:var(--r)}
  .nav-btn svg{width:18px;height:18px}
  .nav-btn.active{background:var(--accent-bg);color:var(--accent);border:none}

  /* Spazio per la nav bottom */
  .main{padding-bottom:80px}
  .statusbar{bottom:56px}

  /* Calendario compatto */
  .cal-header{flex-direction:column;align-items:flex-start;gap:6px;margin-bottom:8px}
  .cal-title{font-size:14px}
  .cal-nav-row{width:100%;justify-content:space-between;flex-wrap:wrap;gap:4px}
  .cal-nav-row > div{flex-wrap:wrap;gap:3px}
  .today-btn{font-size:11px;padding:0 8px;height:26px}
  .cal-nav-btn{width:26px;height:26px;font-size:12px}
  .export-btn{font-size:11px;padding:0 8px;height:26px}

  .cal-grid{gap:1px}
  .cal-dn{font-size:9px;padding:2px 0}
  .cal-day{min-height:50px;padding:3px;border-radius:4px}
  .day-num{font-size:10px;margin-bottom:1px}
  .day-pill{font-size:8px;padding:1px 3px;margin-bottom:1px;gap:2px;border-radius:2px}
  .day-pill-dot{width:3px;height:3px}
  .day-more{font-size:8px;padding:0 2px}

  /* Lista attività */
  .day-card-header{padding:7px 10px}
  .day-card-date{font-size:12px}
  .day-card-body{padding:7px 10px;gap:4px}
  .entry-row{padding:5px 7px;gap:5px}
  .entry-name{font-size:11px;min-width:70px}
  .entry-avatar{width:22px;height:22px;font-size:9px}
  .entry-rest-tag{font-size:9px;padding:1px 5px}
  .entry-act-tag{font-size:9px;padding:1px 5px}

  /* Modal a tutto schermo */
  .modal-overlay{padding:0;align-items:flex-end}
  .modal{width:100%;max-width:100%;border-radius:var(--r3) var(--r3) 0 0;max-height:88vh;padding:18px 16px}

  /* Visit rows in modal */
  .visit-row{grid-template-columns:1fr 1fr}
  .visits-block{padding:8px}

  /* Anagrafiche */
  .tabs{gap:3px}
  .tab-btn{padding:5px 8px;font-size:11px}
  .anag-row{padding:6px 8px}
  .anag-name{font-size:12px}
  .export-grid{grid-template-columns:1fr}

  /* Login */
  .login-box{padding:24px 18px;width:100%;max-width:360px}

  /* Status bar */
  .statusbar{font-size:10px;padding:0 10px}
}

@media (max-width: 400px) {
  .cal-day{min-height:42px;padding:2px}
  .day-pill{display:none}
  .day-num{font-size:10px}
  /* Mostra solo numero di entries */
  .cal-day::after{content:attr(data-count);font-size:8px;color:var(--text3)}
  .nav-btn span{display:none}
  .nav-btn{padding:6px 6px}
}

@keyframes fadeIn{from{opacity:0;transform:translateY(6px)}to{opacity:1;transform:translateY(0)}}
.fade-in{animation:fadeIn .2s ease}

/* LOGIN SCREEN */
#loginScreen{display:none;align-items:center;justify-content:center;min-height:100vh;background:var(--bg);padding:20px;flex-direction:column;gap:0}
#loginScreen.active{display:flex}
.login-box{background:var(--bg2);border:1px solid var(--border2);border-radius:20px;padding:36px 32px;width:360px;max-width:100%}
.login-logo{text-align:center;margin-bottom:6px}
.login-logo-title{font-family:'DM Mono',monospace;font-size:22px;color:var(--accent);font-weight:500;display:flex;align-items:center;justify-content:center;gap:10px}
.login-logo-dot{width:11px;height:11px;border-radius:50%;background:var(--accent);box-shadow:0 0 14px var(--accent);flex-shrink:0}
.login-sub{font-size:12px;color:var(--text3);text-align:center;margin-bottom:26px}
.login-frow{margin-bottom:14px;display:flex;flex-direction:column;gap:5px}
.login-label{font-size:10px;font-weight:600;color:var(--text3);text-transform:uppercase;letter-spacing:0.8px}
.login-select{background:var(--bg3);border:1px solid var(--border);color:var(--text);font-family:'DM Sans',sans-serif;font-size:14px;padding:10px 12px;border-radius:var(--r);outline:none;width:100%;cursor:pointer;transition:border-color .15s}
.login-select:focus{border-color:var(--accent)}
.pin-dots{display:flex;gap:14px;justify-content:center;margin:10px 0 6px}
.pin-dot{width:14px;height:14px;border-radius:50%;border:2px solid var(--border2);transition:all .2s}
.pin-dot.filled{background:var(--accent);border-color:var(--accent);box-shadow:0 0 8px var(--accent)}
.pin-pad{display:grid;grid-template-columns:repeat(3,1fr);gap:8px;margin-top:10px}
.pin-btn{height:52px;border-radius:var(--r2);border:1px solid var(--border);background:var(--bg3);color:var(--text);font-size:20px;font-family:'DM Mono',monospace;cursor:pointer;transition:all .1s;display:flex;align-items:center;justify-content:center}
.pin-btn:hover{background:var(--bg4);border-color:var(--accent);color:var(--accent)}
.pin-btn:active{transform:scale(.95)}
.pin-btn.del{font-size:16px;color:var(--text3)}
.pin-btn.empty{background:transparent;border-color:transparent;cursor:default}
.login-error{color:var(--coral);font-size:12px;text-align:center;margin-top:10px;min-height:18px}
.remember-row{display:flex;align-items:center;gap:8px;margin-top:14px;font-size:12px;color:var(--text3);cursor:pointer}
.remember-row input{accent-color:var(--accent);cursor:pointer}
.login-sep{display:flex;align-items:center;gap:10px;margin:14px 0;color:var(--text3);font-size:11px}
.login-sep::before,.login-sep::after{content:'';flex:1;height:1px;background:var(--border)}
#appShell{display:none}
#appShell.active{display:block}


</style>
</head>
<body>

<!-- LOGIN SCREEN -->
<div id="loginScreen">
  <div class="login-box">
    <div class="login-logo">
      <div class="login-logo-title"><div class="login-logo-dot"></div>TurniRistosi</div>
    </div>
    <div class="login-sub">Gestione turni e attività ristoranti</div>
    <div class="login-frow">
      <label class="login-label">Utente</label>
      <select class="login-select" id="loginUserSel"></select>
    </div>
    <div class="login-frow">
      <label class="login-label">PIN (4 cifre)</label>
      <input type="password" id="loginPin" maxlength="4" placeholder="••••"
        style="background:var(--bg3);border:1px solid var(--border);color:var(--text);font-family:'DM Mono',monospace;font-size:28px;letter-spacing:8px;padding:12px 16px;border-radius:var(--r);outline:none;width:100%;text-align:center;transition:border-color .15s"
        oninput="this.value=this.value.replace(/[^0-9]/g,'')"
        onkeydown="if(event.key==='Enter')doLoginBtn()">
    </div>
    <div style="font-size:11px;color:var(--text3);text-align:center;margin-bottom:4px">
      Primo accesso? Inserisci qualsiasi PIN — diventerà il tuo PIN permanente
    </div>
    <button onclick="doLoginBtn()" style="width:100%;padding:13px;border-radius:var(--r);border:none;background:var(--accent);color:var(--bg);font-family:'DM Sans',sans-serif;font-size:14px;font-weight:600;cursor:pointer;margin-top:10px">
      Accedi
    </button>
    <label class="remember-row"><input type="checkbox" id="rememberMe"> Ricorda accesso su questo dispositivo</label>
    <div class="login-error" id="loginError"></div>
  </div>
</div>

<div id="appShell">
<!-- TOPBAR -->
<div class="topbar">
  <div class="logo">
    <div class="logo-dot"></div>
    TurniRistosi
  </div>
  <select class="user-select" id="userSel" onchange="switchUser(this.value)"></select>
  <span class="lbadge" id="lvBadge"></span>
  <span class="rest-info" id="restInfo"></span>
  <nav class="nav" id="mainNav"></nav>
  <button onclick="logout()" style="margin-left:6px;padding:5px 10px;border:1px solid var(--border);border-radius:var(--r);background:transparent;color:var(--text3);font-size:11px;cursor:pointer;font-family:'DM Sans',sans-serif" title="Esci">⎋ Esci</button>
</div>

<!-- LAYOUT -->
<div class="layout">
  <!-- SIDEBAR -->
  <aside class="sidebar">
    <div>
      <div class="s-title" style="display:flex;align-items:center;justify-content:space-between">
        Turni
        <span id="editLegendBtn" style="display:none;font-size:10px;color:var(--accent);cursor:pointer" onclick="openLegendEditor()">✏️ modifica</span>
      </div>
      <div class="shift-legend" id="shiftLegendSidebar"></div>
    </div>
    <div id="sideRests"></div>
    <div class="today-block" id="todayBlock">
      <div class="s-title">Oggi</div>
      <div id="todayContent"><span style="font-size:11px;color:var(--text3)">Nessun turno</span></div>
    </div>
  </aside>

  <!-- MAIN -->
  <main class="main" id="mainContent"></main>
</div>

</div><!-- /appShell -->

<!-- STATUS BAR -->
<div class="statusbar">
  <div class="status-dot" id="syncDot"></div>
  <span id="statusMsg">TurniApp — caricamento in corso...</span>
  <span id="syncLabel" style="margin-left:auto;font-size:10px;color:var(--text3)"></span>
</div>

<script>
// ─── CONSTANTS ──────────────────────────────────────────────────────────────
// LOGIN

function buildLoginSelect() {
  const sel = document.getElementById('loginUserSel');
  if (!sel) return;
  sel.innerHTML = '<option value="">— Seleziona utente —</option>';
  ['ufficio','supervisore','direttore'].forEach(lv => {
    const us = DB.users.filter(u => u.level === lv);
    if (!us.length) return;
    const g = document.createElement('optgroup'); g.label = LN[lv];
    us.forEach(u => {
      const o = document.createElement('option');
      o.value = u.id; o.textContent = u.name;
      g.appendChild(o);
    });
    sel.appendChild(g);
  });
}

function doLoginBtn() {
  const uid = document.getElementById('loginUserSel').value;
  const pin = document.getElementById('loginPin').value.trim();
  const err = document.getElementById('loginError');
  err.textContent = '';

  if (!uid) { err.textContent = 'Seleziona un utente'; return; }
  if (pin.length !== 4 || !/^\d{4}$/.test(pin)) { err.textContent = 'Inserisci esattamente 4 cifre'; return; }

  const u = DB.users.find(x => x.id === uid);
  if (!u) { err.textContent = 'Utente non trovato'; return; }

  // Primo accesso: nessun PIN impostato → il PIN inserito diventa quello definitivo
  if (!u.pin || u.pin === '') {
    u.pin = pin;
    save();
  } else if (u.pin !== pin) {
    err.textContent = 'PIN non corretto';
    document.getElementById('loginPin').value = '';
    return;
  }

  // Login ok
  const remember = document.getElementById('rememberMe').checked;
  if (remember) {
    try { localStorage.setItem('turniapp_cred', JSON.stringify({uid, pin: u.pin})); } catch(e){}
  }
  doLogin(uid);
}

function doLogin(uid) {
  ST.uid = uid;
  document.getElementById('loginScreen').classList.remove('active');
  document.getElementById('appShell').classList.add('active');
  buildUserSelect();
  renderNav(); renderBadges(); renderAll();
  save();
}

function logout() {
  try { localStorage.removeItem('turniapp_cred'); } catch(e){}
  document.getElementById('appShell').classList.remove('active');
  document.getElementById('loginScreen').classList.add('active');
  document.getElementById('loginPin').value = '';
  document.getElementById('loginError').textContent = '';
  buildLoginSelect();
}

const SHIFT_ALL   = ['AP','M','SW','S','CH','OFF','PIR','FER','MAL','CONG'];
const SHIFT_PRES  = ['AP','M','SW','S','CH'];
const SHIFT_ASSENZA=['OFF','PIR','FER','MAL','CONG'];
const SHIFT_MNG   = ['AP','M','S','CH'];
const MN = ['Gennaio','Febbraio','Marzo','Aprile','Maggio','Giugno','Luglio','Agosto','Settembre','Ottobre','Novembre','Dicembre'];
const DN = ['Dom','Lun','Mar','Mer','Gio','Ven','Sab'];
const LC  = {ufficio:'#FFC72C',supervisore:'#27ae60',direttore:'#f97066',mng:'#26c6da'};
const LBG = {ufficio:'var(--accent-bg)',supervisore:'var(--green-bg)',direttore:'var(--coral-bg)',mng:'var(--teal-bg)'};
const LN  = {ufficio:'Ufficio',supervisore:'Supervisore',direttore:'Direttore',mng:'MNG'};
const ACT_COLORS = ['#a78bfa','#60a5fa','#4ade80','#fbbf24','#f97066','#f472b6','#26c6da','#fb923c','#94a3b8','#34d399'];
const SHIFT_CSS  = {AP:'s-ap',M:'s-m',SW:'s-sw',S:'s-s',CH:'s-n',OFF:'s-off',PIR:'s-pir',FER:'s-fer',MAL:'s-mal',CONG:'s-cong'};

// ─── STATE ───────────────────────────────────────────────────────────────────
let DB = {
  users: [
    {id:'u1',name:'Anna Rossi',level:'ufficio',rests:[],canInsert:true,canView:true,pin:'0001'},
    {id:'u2',name:'Marco Bianchi',level:'ufficio',rests:[],canInsert:true,canView:true,pin:'0002'},
  ],
  restaurants: [
    {id:'r1',name:'Ristorante Roma'},
    {id:'r2',name:'Ristorante Milano'},
    {id:'r3',name:'Ristorante Napoli'},
  ],
  activities: [
    {id:'a1',name:'Audit cassa',color:'#a78bfa'},
    {id:'a2',name:'Formazione staff',color:'#60a5fa'},
    {id:'a3',name:'Ispezione cucina',color:'#4ade80'},
    {id:'a4',name:'Riunione direttori',color:'#fbbf24'},
    {id:'a5',name:'Affiancamento',color:'#f472b6'},
  ],
  mngAnag: {},
  shifts:  {},
  flags:   {},
  shiftLabels: {AP:'Apertura',M:'Mattina',SW:'Smart W.',S:'Sera',CH:'Chiusura',OFF:'Riposo',PIR:'Permesso',FER:'Ferie',MAL:'Malattia',CONG:'Congedo'}
};
let ST = {
  uid: 'u1',
  view: 'cal',
  month: new Date().getMonth(),
  year:  new Date().getFullYear(),
  anagTab: 'users',
  flagTab: 'view'
};

// ─── SUPABASE CONFIG ─────────────────────────────────────────────────────────
// ⚠️  INSERISCI QUI LE TUE CREDENZIALI SUPABASE
const SUPABASE_URL = 'https://wcqpbkrkzedqkadzeagr.supabase.co';
const SUPABASE_KEY = 'sb_publishable_XIeTMA05rM9Em8qZlEb3TQ_1HhV1xtm';

const SUPABASE_ENABLED = !SUPABASE_URL.includes('INSERISCI');
const SB_ENDPOINT = `${SUPABASE_URL}/rest/v1/turniapp?id=eq.main`;
const SB_HEADERS = {
  'Content-Type': 'application/json',
  'apikey': SUPABASE_KEY,
  'Authorization': `Bearer ${SUPABASE_KEY}`,
  'Prefer': 'return=minimal'
};

let syncTimer = null;
let lastSyncTime = null;
let isSyncing = false;

function setSyncStatus(state, msg) {
  const dot = document.getElementById('syncDot');
  const lbl = document.getElementById('syncLabel');
  if (!dot || !lbl) return;
  const colors = { ok:'var(--green)', syncing:'var(--amber)', error:'var(--coral)', local:'var(--text3)' };
  dot.style.background = colors[state] || 'var(--text3)';
  lbl.textContent = msg;
}

// ─── PERSISTENCE ─────────────────────────────────────────────────────────────
function saveLocal() {
  try { localStorage.setItem('turniapp_v1', JSON.stringify({...DB, _st: ST})); } catch(e) {}
}

function loadLocal() {
  try {
    const s = localStorage.getItem('turniapp_v1');
    if (s) {
      const p = JSON.parse(s);
      ['users','restaurants','activities','mngAnag','shifts','flags','shiftLabels'].forEach(k => {
        if (p[k] !== undefined) DB[k] = p[k];
      });
      if (p._st) ST = {...ST, ...p._st};
    }
  } catch(e) {}
}

async function syncFromSupabase() {
  if (!SUPABASE_ENABLED) return false;
  try {
    setSyncStatus('syncing', 'Sincronizzazione...');
    const res = await fetch(SB_ENDPOINT, { headers: SB_HEADERS });
    if (!res.ok) throw new Error('HTTP ' + res.status);
    const rows = await res.json();
    if (rows && rows.length && rows[0].data) {
      const p = rows[0].data;
      ['users','restaurants','activities','mngAnag','shifts','flags','shiftLabels'].forEach(k => {
        if (p[k] !== undefined) DB[k] = p[k];
      });
      saveLocal();
      lastSyncTime = new Date();
      setSyncStatus('ok', '✓ Sincronizzato ' + lastSyncTime.toLocaleTimeString('it-IT'));
      return true;
    }
    setSyncStatus('ok', '✓ Online');
    return true;
  } catch(e) {
    setSyncStatus('error', '⚠ Offline — dati locali');
    return false;
  }
}

async function saveToSupabase() {
  saveLocal(); // sempre salva in locale
  if (!SUPABASE_ENABLED) { setSyncStatus('local', '💾 Salvato (locale)'); return; }
  if (isSyncing) return;
  isSyncing = true;
  setSyncStatus('syncing', 'Salvataggio...');
  try {
    // Upsert: aggiorna se esiste, inserisce se no
    const res = await fetch(`${SUPABASE_URL}/rest/v1/turniapp`, {
      method: 'POST',
      headers: {...SB_HEADERS, 'Prefer': 'resolution=merge-duplicates,return=minimal'},
      body: JSON.stringify({ id: 'main', data: DB, updated_at: new Date().toISOString() })
    });
    if (!res.ok) throw new Error('HTTP ' + res.status);
    lastSyncTime = new Date();
    setSyncStatus('ok', '✓ Salvato ' + lastSyncTime.toLocaleTimeString('it-IT'));
  } catch(e) {
    setSyncStatus('error', '⚠ Salvataggio fallito — riprovando...');
    // Riprova dopo 5 secondi
    setTimeout(saveToSupabase, 5000);
  } finally {
    isSyncing = false;
  }
}

// Funzione save pubblica usata da tutta l'app
function save() {
  // Debounce: aspetta 800ms prima di inviare (evita troppe chiamate rapide)
  clearTimeout(syncTimer);
  syncTimer = setTimeout(saveToSupabase, 800);
  saveLocal(); // locale immediato
}

function load() {
  loadLocal();
}

// Polling: rilegge da Supabase ogni 30 secondi per aggiornamenti da altri utenti
function startPolling() {
  if (!SUPABASE_ENABLED) return;
  setInterval(async () => {
    const wasOnline = await syncFromSupabase();
    if (wasOnline) {
      // Aggiorna l'interfaccia solo se i dati sono cambiati
      renderAll();
    }
  }, 30000);
}

// ─── HELPERS ─────────────────────────────────────────────────────────────────
const me = () => DB.users.find(u => u.id === ST.uid) || DB.users[0];
const ini = n => (n||'').split(' ').map(p=>p[0]).join('').slice(0,2).toUpperCase();
const setStatus = msg => { document.getElementById('statusMsg').textContent = msg; };

// ─── LEGENDA TURNI DINAMICA ───────────────────────────────────────────────────
function getShiftLabel(code) {
  if (!DB.shiftLabels) DB.shiftLabels = {AP:'Apertura',M:'Mattina',SW:'Smart W.',S:'Sera',CH:'Chiusura',OFF:'Riposo',PIR:'Permesso',FER:'Ferie',MAL:'Malattia',CONG:'Congedo'};
  return DB.shiftLabels[code] || code;
}

function renderShiftLegend() {
  const el = document.getElementById('shiftLegendSidebar');
  const btn = document.getElementById('editLegendBtn');
  if (!el) return;
  if (btn) btn.style.display = me().level==='ufficio' ? 'block' : 'none';
  el.innerHTML = SHIFT_ALL.map(s =>
    `<span class="stag ${SHIFT_CSS[s]||'s-off'}">${s}</span><span class="s-label">${getShiftLabel(s)}</span>`
  ).join('');
}

function openLegendEditor() {
  const rows = SHIFT_ALL.map(s => `
    <div style="display:flex;align-items:center;gap:8px;margin-bottom:7px">
      <span class="stag ${SHIFT_CSS[s]||'s-off'}" style="min-width:40px;text-align:center">${s}</span>
      <input type="text" id="lbl_${s}" value="${getShiftLabel(s)}"
        style="flex:1;background:var(--bg3);border:1px solid var(--border);color:var(--text);font-family:'DM Sans',sans-serif;font-size:13px;padding:6px 8px;border-radius:var(--r);outline:none">
    </div>`).join('');
  showModal(`
    <div class="modal-title">✏️ Modifica nomi turni</div>
    <div style="font-size:12px;color:var(--text3);margin-bottom:12px">Cambia il nome descrittivo di ogni codice turno. I codici (AP, M, ecc.) restano invariati.</div>
    ${rows}
    <div class="mact">
      <button class="btn-secondary" onclick="closeModal()">Annulla</button>
      <button class="btn-primary" onclick="saveLegendLabels()">Salva</button>
    </div>`);
}

function saveLegendLabels() {
  if (!DB.shiftLabels) DB.shiftLabels = {};
  SHIFT_ALL.forEach(s => {
    const v = document.getElementById('lbl_'+s)?.value.trim();
    if (v) DB.shiftLabels[s] = v;
  });
  closeModal(); save(); renderShiftLegend(); setStatus('Nomi turni aggiornati');
}

// ─── MODIFICA TURNO ESISTENTE ─────────────────────────────────────────────────
function openEditModal(dk, idx) {
  const entries = DB.shifts[dk] || [];
  const e = entries[idx];
  if (!e) return;
  const m = me();
  // Solo l'autore o l'ufficio può modificare
  const isOwner = (!e.isMng && e.userId === m.id) || m.level === 'ufficio';
  const isDirOwner = e.isMng && (e.dirId === m.id || m.level === 'ufficio');
  if (!isOwner && !isDirOwner) { setStatus('Non puoi modificare questo turno'); return; }

  const parts = dk.split('-');
  const lbl = `${parts[2]}/${parts[1]}/${parts[0]}`;
  const shiftOpts = SHIFT_ALL.map(s=>`<option value="${s}"${e.shift===s?' selected':''}>${s} — ${getShiftLabel(s)}</option>`).join('');
  const allRestOpts = DB.restaurants.map(r=>`<option value="${r.id}">${r.name}</option>`).join('');
  const actOpts = `<option value="">— Nessuna —</option>` + DB.activities.map(a=>`<option value="${a.id}">${a.name}</option>`).join('');

  let body = '';
  if (e.isMng) {
    // Modifica turno MNG: solo il turno
    const mg = DB.mngAnag[e.mngId];
    body = `
      <div style="font-size:13px;font-weight:500;margin-bottom:12px;color:var(--text)">MNG: ${mg?.nome||'—'}</div>
      <div class="frow"><label>Turno</label>
        <select id="editShift">${SHIFT_MNG.map(s=>`<option value="${s}"${e.shift===s?' selected':''}>${s} — ${getShiftLabel(s)}</option>`).join('')}</select>
      </div>`;
  } else if (e.userId === (e.userId) && DB.users.find(u=>u.id===e.userId)?.level==='direttore') {
    // Modifica turno direttore
    const mngOptsAll = `<option value="">— Nessuno —</option>` + getMNGs(e.userId||m.id).map(mg=>`<option value="${mg.id}"${e.subMngId===mg.id?' selected':''}>${mg.nome}</option>`).join('');
    body = `
      <div class="frow"><label>Turno</label><select id="editShift" onchange="onEditDirShift()">${shiftOpts}</select></div>
      <div id="editSubRow" class="frow" style="${SHIFT_ASSENZA.includes(e.shift)?'':'display:none'}">
        <label>MNG sostituto</label><select id="editSubSel">${mngOptsAll}</select>
      </div>`;
  } else {
    // Modifica turno ufficio/supervisore: turno + visite
    const visite = e.visite && e.visite.length ? e.visite : (e.restId ? [{restId:e.restId,activityId:e.activityId||''}] : [{restId:'',activityId:''},{restId:'',activityId:''},{restId:'',activityId:''},{restId:'',activityId:''}]);
    while (visite.length < 4) visite.push({restId:'',activityId:''});
    const visiteRows = [0,1,2,3].map(i => `
      <div class="visit-row">
        <div class="visit-num">Visita ${i+1}</div>
        <div class="frow" style="margin:0"><label style="font-size:10px">Ristorante</label>
          <select id="evRest${i}" style="font-size:12px;padding:5px 8px">
            <option value="">— Nessuno —</option>${DB.restaurants.map(r=>`<option value="${r.id}"${visite[i].restId===r.id?' selected':''}>${r.name}</option>`).join('')}
          </select></div>
        <div class="frow" style="margin:0"><label style="font-size:10px">Attività</label>
          <select id="evAct${i}" style="font-size:12px;padding:5px 8px">
            <option value="">— Nessuna —</option>${DB.activities.map(a=>`<option value="${a.id}"${visite[i].activityId===a.id?' selected':''}>${a.name}</option>`).join('')}
          </select></div>
      </div>`).join('');
    body = `
      <div class="frow"><label>Turno</label>
        <select id="editShift" onchange="onEditAdminShift()">${shiftOpts}</select>
      </div>
      <div id="editVisiteBlock" style="${SHIFT_PRES.includes(e.shift)?'':'display:none'}">
        <div style="font-size:10px;font-weight:600;color:var(--text3);text-transform:uppercase;letter-spacing:0.5px;margin-bottom:8px">Ristoranti da visitare</div>
        <div class="visits-block">${visiteRows}</div>
      </div>`;
  }

  showModal(`
    <div class="modal-title">${ICON.edit} Modifica turno — ${lbl}</div>
    ${body}
    <div class="mact">
      <button class="btn-secondary" onclick="closeModal()">Annulla</button>
      <button class="btn-primary" onclick="saveEditEntry('${dk}',${idx})">Salva modifiche</button>
    </div>`);
}

function onEditAdminShift() {
  const s = document.getElementById('editShift')?.value;
  const vb = document.getElementById('editVisiteBlock');
  if (vb) vb.style.display = SHIFT_PRES.includes(s) ? 'block' : 'none';
}
function onEditDirShift() {
  const s = document.getElementById('editShift')?.value;
  const sr = document.getElementById('editSubRow');
  if (sr) sr.style.display = SHIFT_ASSENZA.includes(s) ? 'flex' : 'none';
}

function saveEditEntry(dk, idx) {
  const entries = DB.shifts[dk] || [];
  const e = entries[idx];
  if (!e) return;
  const shift = document.getElementById('editShift')?.value;
  if (!shift) { setStatus('Seleziona un turno'); return; }

  if (e.isMng) {
    e.shift = shift;
  } else {
    const u = DB.users.find(x=>x.id===e.userId);
    if (u?.level === 'direttore') {
      e.shift = shift;
      if (SHIFT_ASSENZA.includes(shift)) {
        e.subMngId = document.getElementById('editSubSel')?.value || '';
      } else {
        delete e.subMngId;
      }
    } else {
      e.shift = shift;
      const isPres = SHIFT_PRES.includes(shift);
      const visite = [];
      if (isPres) {
        for (let i=0; i<4; i++) {
          const r = document.getElementById('evRest'+i)?.value;
          const a = document.getElementById('evAct'+i)?.value;
          if (r) visite.push({restId:r, activityId:a||''});
        }
      }
      e.visite = visite;
      e.restId = visite.length ? visite[0].restId : '';
      e.activityId = visite.length ? visite[0].activityId : '';
    }
  }
  closeModal(); save(); setStatus('Turno modificato'); renderAll();
}
const getRestsFor = uid => {
  const u = DB.users.find(x => x.id === uid) || me();
  if (u.level === 'ufficio') return DB.restaurants;
  return DB.restaurants.filter(r => u.rests && u.rests.includes(r.id));
};
const getMNGs = dirId => Object.entries(DB.mngAnag).filter(([,v]) => v.dir === dirId).map(([k,v]) => ({id:k,...v}));
const getDirsForRest = rid => DB.users.filter(u => u.level==='direttore' && u.rests && u.rests.includes(rid));
const getSupsForRest = rid => DB.users.filter(u => u.level==='supervisore' && u.rests && u.rests.includes(rid));

function canSeeEntry(entry) {
  const m = me();
  if (!m.canView) return false;

  // UFFICIO: vede tutto
  if (m.level === 'ufficio') return true;

  // DIRETTORE: vede solo se stesso e i propri MNG
  if (m.level === 'direttore') {
    if (entry.isMng) return entry.dirId === m.id;
    return entry.userId === m.id;
  }

  // SUPERVISORE: vede i propri turni + turni dei direttori assegnati via flag
  if (m.level === 'supervisore') {
    // I propri turni: sempre visibili
    if (!entry.isMng && entry.userId === m.id) return true;

    // Turni di un direttore: controlla flag (ufficio assegna quali dir il sup può vedere)
    if (!entry.isMng) {
      const u = DB.users.find(x => x.id === entry.userId);
      if (!u || u.level !== 'direttore') return false;
      // Il direttore deve essere assegnato allo stesso ristorante del supervisore
      const myR = m.rests || [];
      const sharedRest = myR.some(r => u.rests && u.rests.includes(r));
      if (!sharedRest) return false;
      // Controlla flag di visibilità impostato dall'ufficio
      const flags = DB.flags[m.id] || {};
      return flags[u.id] !== false;
    }

    // Turni MNG: visibili se il direttore genitore è visibile a questo supervisore
    if (entry.isMng) {
      const dir = DB.users.find(x => x.id === entry.dirId);
      if (!dir) return false;
      const myR = m.rests || [];
      const sharedRest = myR.some(r => dir.rests && dir.rests.includes(r));
      if (!sharedRest) return false;
      const flags = DB.flags[m.id] || {};
      return flags[dir.id] !== false;
    }
    return false;
  }

  return false;
}

const getVisible = dk => (DB.shifts[dk] || []).filter(e => canSeeEntry(e));
const canInsert = uid => { const u = DB.users.find(x => x.id === uid); return u && u.canInsert !== false; };

function addEntry(dk, entry) {
  if (!DB.shifts[dk]) DB.shifts[dk] = [];
  DB.shifts[dk].push({...entry, ts: Date.now()});
}

// SVG icons (inline, no CDN)
const ICON = {
  cal:  `<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8"><rect x="3" y="4" width="18" height="18" rx="2"/><path d="M16 2v4M8 2v4M3 10h18"/></svg>`,
  list: `<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8"><path d="M9 6h11M9 12h11M9 18h11M5 6v.01M5 12v.01M5 18v.01"/></svg>`,
  users:`<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8"><path d="M17 21v-2a4 4 0 0 0-4-4H5a4 4 0 0 0-4 4v2"/><circle cx="9" cy="7" r="4"/><path d="M23 21v-2a4 4 0 0 0-3-3.87M16 3.13a4 4 0 0 1 0 7.75"/></svg>`,
  flag: `<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8"><path d="M4 15s1-1 4-1 5 2 8 2 4-1 4-1V3s-1 1-4 1-5-2-8-2-4 1-4 1z"/><line x1="4" y1="22" x2="4" y2="15"/></svg>`,
  exp:  `<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8"><path d="M14 2H6a2 2 0 0 0-2 2v16a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V8z"/><polyline points="14 2 14 8 20 8"/><line x1="16" y1="13" x2="8" y2="13"/><line x1="16" y1="17" x2="8" y2="17"/><polyline points="10 9 9 9 8 9"/></svg>`,
  book: `<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8"><path d="M4 19.5A2.5 2.5 0 0 1 6.5 17H20"/><path d="M6.5 2H20v20H6.5A2.5 2.5 0 0 1 4 19.5v-15A2.5 2.5 0 0 1 6.5 2z"/></svg>`,
  plus: `<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><line x1="12" y1="5" x2="12" y2="19"/><line x1="5" y1="12" x2="19" y2="12"/></svg>`,
  edit: `<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8"><path d="M11 4H4a2 2 0 0 0-2 2v14a2 2 0 0 0 2 2h14a2 2 0 0 0 2-2v-7"/><path d="M18.5 2.5a2.121 2.121 0 0 1 3 3L12 15l-4 1 1-4 9.5-9.5z"/></svg>`,
  trash:`<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8"><polyline points="3 6 5 6 21 6"/><path d="M19 6l-1 14H6L5 6"/><path d="M10 11v6M14 11v6"/><path d="M9 6V4h6v2"/></svg>`,
  x:    `<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><line x1="18" y1="6" x2="6" y2="18"/><line x1="6" y1="6" x2="18" y2="18"/></svg>`,
  rest: `<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8"><path d="M3 9l9-7 9 7v11a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2z"/><polyline points="9 22 9 12 15 12 15 22"/></svg>`,
  tag:  `<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8"><path d="M20.59 13.41l-7.17 7.17a2 2 0 0 1-2.83 0L2 12V2h10l8.59 8.59a2 2 0 0 1 0 2.82z"/><line x1="7" y1="7" x2="7.01" y2="7"/></svg>`,
  dl:   `<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8"><path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4"/><polyline points="7 10 12 15 17 10"/><line x1="12" y1="15" x2="12" y2="3"/></svg>`,
  print:`<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8"><polyline points="6 9 6 2 18 2 18 9"/><path d="M6 18H4a2 2 0 0 1-2-2v-5a2 2 0 0 1 2-2h16a2 2 0 0 1 2 2v5a2 2 0 0 1-2 2h-2"/><rect x="6" y="14" width="12" height="8"/></svg>`,
  phone:`<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8"><path d="M22 16.92v3a2 2 0 0 1-2.18 2 19.79 19.79 0 0 1-8.63-3.07A19.5 19.5 0 0 1 4.69 12 19.79 19.79 0 0 1 1.61 3.41 2 2 0 0 1 3.6 1h3a2 2 0 0 1 2 1.72 12.84 12.84 0 0 0 .7 2.81 2 2 0 0 1-.45 2.11L8.09 8.91a16 16 0 0 0 6 6l1.27-1.27a2 2 0 0 1 2.11-.45 12.84 12.84 0 0 0 2.81.7A2 2 0 0 1 22 16.92z"/></svg>`,
};

// ─── INIT UI ─────────────────────────────────────────────────────────────────
function switchUser(id) {
  ST.uid = id;
  renderNav();
  renderBadges();
  renderAll();
  save();
}

function renderBadges() {
  const m = me();
  const lb = document.getElementById('lvBadge');
  lb.textContent = LN[m.level];
  lb.className = 'lbadge lv-' + m.level;
  const ri = document.getElementById('restInfo');
  const rests = getRestsFor(m.id);
  ri.textContent = rests.length ? rests.map(r => r.name).join(' · ') : 'Nessun ristorante assegnato';
}

function renderNav() {
  const m = me();
  const nav = document.getElementById('mainNav');
  const views = [
    {id:'cal',  label:'Calendario', icon:ICON.cal,  always:true},
    {id:'list', label:'Attività',   icon:ICON.list, always:true},
    {id:'anag', label:'MNG',        icon:ICON.book, show: m.level==='direttore'},
    {id:'anag', label:'Anagrafiche',icon:ICON.users,show: m.level==='ufficio'},
    {id:'flag', label:'Flag',       icon:ICON.flag, show: m.level==='ufficio'},
    {id:'export',label:'Esporta',   icon:ICON.exp,  show: m.level==='ufficio'},
  ];
  nav.innerHTML = views
    .filter(v => v.always || v.show)
    .map(v => `<button class="nav-btn${ST.view===v.id&&v.label===views.find(x=>x.id===ST.view&&x.label)?.label?' active':ST.view===v.id?' active':''}" onclick="setView('${v.id}')">${v.icon} ${v.label}</button>`)
    .join('');
  // re-render active state correctly
  nav.querySelectorAll('.nav-btn').forEach((btn, i) => {
    const vd = views.filter(v => v.always || v.show)[i];
    btn.classList.toggle('active', ST.view === vd.id);
  });
}

function setView(v) {
  ST.view = v;
  renderNav();
  renderAll();
}

function renderAll() {
  renderBadges();
  renderShiftLegend();
  renderSide();
  const mc = document.getElementById('mainContent');
  mc.className = 'main fade-in';
  if      (ST.view === 'cal')    renderCal(mc);
  else if (ST.view === 'list')   renderList(mc);
  else if (ST.view === 'anag')   { me().level==='direttore' ? renderAnagMNG(mc) : renderAnag(mc); }
  else if (ST.view === 'flag')   renderFlag(mc);
  else if (ST.view === 'export') renderExport(mc);
}

function renderSide() {
  const m = me();
  const rests = getRestsFor(m.id);
  let rhtml = `<div class="s-title">I miei ristoranti</div>`;
  if (rests.length) {
    rhtml += rests.map(r => {
      const isActive = ST.calMode==='ristorante' && ST.calRest===r.id;
      return `<div class="rest-pill" onclick="selectRestView('${r.id}')" style="cursor:pointer;${isActive?'border-color:var(--accent);background:var(--accent-bg);color:var(--accent)':''}" title="Visualizza calendario per ${r.name}">
        ${ICON.rest}<span style="flex:1">${r.name}</span>
        ${isActive?'<span style="font-size:9px;font-weight:600">●</span>':''}
      </div>`;
    }).join('');
  } else {
    rhtml += `<span style="font-size:11px;color:var(--text3)">Nessuno assegnato</span>`;
  }
  document.getElementById('sideRests').innerHTML = rhtml;

  const t = new Date();
  const dk = t.getFullYear()+'-'+(t.getMonth()+1)+'-'+t.getDate();
  const myS = (DB.shifts[dk]||[]).filter(e => !e.isMng && e.userId === m.id);
  let tc = '';
  if (myS.length) {
    myS.forEach(s => {
      const rest = DB.restaurants.find(r => r.id === s.restId);
      const act  = DB.activities.find(a => a.id === s.activityId);
      tc += `<div class="today-shift"><span class="stag ${SHIFT_CSS[s.shift]||'s-off'}">${s.shift}</span>`;
      if (rest) tc += `<span style="font-size:11px;color:var(--text3)">${rest.name}</span>`;
      tc += `</div>`;
      if (act) tc += `<div class="today-act" style="color:${act.color}">${act.name}</div>`;
    });
  } else {
    tc = `<span style="font-size:11px;color:var(--text3)">Nessun turno oggi</span>`;
  }
  document.getElementById('todayContent').innerHTML = tc;
}

function selectRestView(restId) {
  ST.calMode = 'ristorante';
  ST.calRest = restId;
  if (ST.view !== 'cal') setView('cal');
  else renderAll();
}

// ─── CALENDAR ─────────────────────────────────────────────────────────────────
if (!ST.calMode) ST.calMode = 'turni';
if (!ST.calRest) ST.calRest = '';

function renderCal(mc) {
  const y = ST.year, mo = ST.month, today = new Date();
  const first = new Date(y,mo,1).getDay();
  const dim   = new Date(y,mo+1,0).getDate();
  const prev  = new Date(y,mo,0).getDate();
  const m = me();
  const myRests = getRestsFor(m.id);
  if (ST.calMode==='ristorante' && !ST.calRest && myRests.length) ST.calRest = myRests[0].id;

  const modeBar = `
    <div style="display:flex;gap:4px">
      <button onclick="setCalMode('turni')" class="today-btn" style="${ST.calMode==='turni'?'border-color:var(--accent);color:var(--accent)':''}">
        👤 Per turno
      </button>
      <button onclick="setCalMode('ristorante')" class="today-btn" style="${ST.calMode==='ristorante'?'border-color:var(--accent);color:var(--accent)':''}">
        🏠 Per ristorante
      </button>
    </div>`;

  // Nome ristorante selezionato (solo vista ristorante)
  const selectedRest = ST.calMode==='ristorante' ? DB.restaurants.find(r=>r.id===ST.calRest) : null;
  const restLabel = selectedRest
    ? `<div style="display:flex;align-items:center;gap:8px;margin-bottom:12px;padding:7px 12px;background:var(--accent-bg);border:1px solid var(--border2);border-radius:var(--r2)">
        <span style="color:var(--coral)">${ICON.rest}</span>
        <span style="font-size:13px;font-weight:500;color:var(--text)">${selectedRest.name}</span>
        <span style="font-size:11px;color:var(--text3);margin-left:auto">← clicca un ristorante nella sidebar per cambiare</span>
      </div>` : '';

  let h = `<div class="cal-header">
    <div class="cal-title">${MN[mo]} ${y}</div>
    <div class="cal-nav-row">
      ${modeBar}
      ${m.level==='ufficio'?`<button class="export-btn" onclick="setView('export')">${ICON.dl} Export</button>`:''}
      <button class="cal-nav-btn" onclick="prevM()">&#8592;</button>
      <button class="today-btn" onclick="goToday()">Oggi</button>
      <button class="cal-nav-btn" onclick="nextM()">&#8594;</button>
    </div>
  </div>
  ${restLabel}
  <div class="cal-grid">`;

  DN.forEach(d => h += `<div class="cal-dn">${d}</div>`);
  for (let i=first-1; i>=0; i--) h += `<div class="cal-day other-month"><div class="day-num">${prev-i}</div></div>`;

  for (let d=1; d<=dim; d++) {
    const dk = y+'-'+(mo+1)+'-'+d;
    const isT = today.getFullYear()===y && today.getMonth()===mo && today.getDate()===d;

    if (ST.calMode === 'turni') {
      // ── VISTA TURNI: supervisori e direttori ──
      const entries = getVisible(dk).filter(e => !e.isMng);
      let pills = entries.slice(0,4).map(e => {
        const u = DB.users.find(x=>x.id===e.userId); if (!u) return '';
        const col = LC[u.level] || '#FFC72C';
        return `<div class="day-pill" style="background:${col}18;color:${col};cursor:pointer"
          onclick="event.stopPropagation();openDaySummary('${dk}')"
          title="Clicca per dettagli">
          <div class="day-pill-dot" style="background:${col}"></div>
          ${u.name.split(' ')[0]}: <strong>${e.shift}</strong>
        </div>`;
      }).join('');
      if (entries.length > 4) pills += `<div class="day-more">+${entries.length-4} altri</div>`;
      h += `<div class="cal-day${isT?' today':''}" data-count="${entries.length||''}" onclick="openDaySummary('${dk}')">
        <div class="day-num">${d}</div>${pills}
      </div>`;

    } else {
      // ── VISTA RISTORANTE: turni direttore + MNG del ristorante scelto ──
      const rid = ST.calRest;
      const allShifts = DB.shifts[dk] || [];

      // Direttore del ristorante
      const dirUser = DB.users.find(u => u.level==='direttore' && u.rests && u.rests.includes(rid));
      const dirEntry = dirUser ? allShifts.find(e => !e.isMng && e.userId===dirUser.id) : null;

      // MNG in turno per questo ristorante (quelli senza restId = inseriti dal direttore di quel ristorante)
      const mngEntries = allShifts.filter(e => {
        if (!e.isMng) return false;
        // Se ha restId, filtra per ristorante; se non ce l'ha, appartiene al dir di quel ristorante
        if (e.restId && e.restId !== rid) return false;
        if (!e.restId && dirUser && e.dirId !== dirUser.id) return false;
        return canSeeEntry(e);
      });

      let pills = '';
      if (dirEntry) {
        const col = LC['direttore'];
        pills += `<div class="day-pill" style="background:${col}18;color:${col};cursor:pointer"
          onclick="event.stopPropagation();openEntryDetail('${dk}',${allShifts.indexOf(dirEntry)})"
          title="${dirUser.name}">
          <div class="day-pill-dot" style="background:${col}"></div>
          <strong>DIR</strong> ${dirEntry.shift}
        </div>`;
      }
      mngEntries.slice(0,3).forEach(e => {
        const mg = DB.mngAnag[e.mngId]; if (!mg) return;
        pills += `<div class="day-pill" style="background:var(--teal-bg);color:var(--teal);cursor:pointer"
          onclick="event.stopPropagation();openRestDetail('${dk}','${rid}')"
          title="${mg.nome}: ${e.shift}">
          <div class="day-pill-dot" style="background:var(--teal)"></div>
          ${mg.nome.split(' ')[0]}: <strong>${e.shift}</strong>
        </div>`;
      });
      if (mngEntries.length > 3) pills += `<div class="day-more">+${mngEntries.length-3}</div>`;

      h += `<div class="cal-day${isT?' today':''}" onclick="openDaySummary('${dk}')">
        <div class="day-num">${d}</div>${pills||'<div style="font-size:9px;color:var(--text3);padding:2px">—</div>'}
      </div>`;
    }
  }

  const tot = first+dim; const rem = tot%7 ? 7-tot%7 : 0;
  for (let i=1; i<=rem; i++) h += `<div class="cal-day other-month"><div class="day-num">${i}</div></div>`;
  h += '</div>';
  mc.innerHTML = h;
}

function setCalMode(mode) {
  ST.calMode = mode;
  renderAll();
}

// ── Popup riepilogo giorno: tutti i turni con Modifica/Elimina + Aggiungi ──
function openDaySummary(dk) {
  const m = me();
  const parts = dk.split('-');
  const lbl = `${parts[2]}/${parts[1]}/${parts[0]}`;
  const allShifts = DB.shifts[dk] || [];
  const visible = getVisible(dk);

  function entryRow(e, realIdx) {
    const canEdit = m.level==='ufficio' ||
      (!e.isMng && e.userId===m.id) ||
      (e.isMng && e.dirId===m.id);

    if (e.isMng) {
      const mg = DB.mngAnag[e.mngId]; if (!mg) return '';
      return `<div style="display:flex;align-items:center;gap:8px;padding:8px 10px;border-radius:var(--r);border:1px solid var(--border);background:var(--bg);margin-bottom:5px;flex-wrap:wrap">
        <div style="width:28px;height:28px;border-radius:50%;background:var(--teal-bg);color:var(--teal);display:flex;align-items:center;justify-content:center;font-size:10px;font-weight:700;flex-shrink:0">${ini(mg.nome)}</div>
        <span style="font-weight:500;flex:1;font-size:13px">${mg.nome}</span>
        <span class="lbadge" style="background:var(--teal-bg);color:var(--teal);font-size:10px">MNG</span>
        <span class="stag ${SHIFT_CSS[e.shift]||'s-off'}">${e.shift}</span>
        ${canEdit?`<button class="btn-icon" onclick="closeModal();openEditModal('${dk}',${realIdx})" title="Modifica">${ICON.edit}</button>
        <button class="btn-icon danger" onclick="closeModal();delEntry('${dk}',${realIdx})" title="Elimina">${ICON.trash}</button>`:''}
      </div>`;
    } else {
      const u = DB.users.find(x=>x.id===e.userId); if (!u) return '';
      const visite = e.visite&&e.visite.length ? e.visite : (e.restId?[{restId:e.restId,activityId:e.activityId||''}]:[]);
      const visiteTags = visite.map(v=>{
        const vr=DB.restaurants.find(r=>r.id===v.restId);
        const va=v.activityId?DB.activities.find(a=>a.id===v.activityId):null;
        return vr?`<span class="entry-rest-tag" style="font-size:10px">${ICON.rest}${vr.name}</span>${va?`<span class="entry-act-tag" style="background:${va.color}20;color:${va.color};border:1px solid ${va.color}40;font-size:10px">${ICON.tag}${va.name}</span>`:''}`:'';
      }).join('');
      const sub = e.subMngId&&DB.mngAnag[e.subMngId];
      return `<div style="display:flex;align-items:center;gap:8px;padding:8px 10px;border-radius:var(--r);border:1px solid var(--border);background:var(--bg);margin-bottom:5px;flex-wrap:wrap">
        <div class="entry-avatar" style="background:${LBG[u.level]};color:${LC[u.level]};width:28px;height:28px;font-size:10px">${ini(u.name)}</div>
        <span style="font-weight:500;flex:1;font-size:13px">${u.name}</span>
        <span class="lbadge lv-${u.level}" style="font-size:10px">${LN[u.level]}</span>
        <span class="stag ${SHIFT_CSS[e.shift]||'s-off'}">${e.shift}</span>
        ${sub?`<span style="font-size:10px;color:var(--text3);font-style:italic">sost.${sub.nome.split(' ')[0]}</span>`:''}
        <div style="display:flex;flex-wrap:wrap;gap:3px;width:100%">${visiteTags}</div>
        ${canEdit?`<div style="display:flex;gap:4px;margin-left:auto">
          <button class="btn-icon" onclick="closeModal();openEditModal('${dk}',${realIdx})" title="Modifica">${ICON.edit}</button>
          <button class="btn-icon danger" onclick="closeModal();delEntry('${dk}',${realIdx})" title="Elimina">${ICON.trash}</button>
        </div>`:''}
      </div>`;
    }
  }

  let rows = '';
  visible.forEach(e => {
    const realIdx = allShifts.indexOf(e);
    rows += entryRow(e, realIdx);
  });

  const canAdd = canInsert(m.id);
  showModal(`
    <div class="modal-title">${ICON.cal} ${lbl}</div>
    ${visible.length===0
      ? `<div style="font-size:12px;color:var(--text3);font-style:italic;padding:10px 0;text-align:center">Nessun turno inserito</div>`
      : `<div style="font-size:10px;font-weight:600;color:var(--text3);text-transform:uppercase;letter-spacing:0.5px;margin-bottom:8px">Turni del giorno (${visible.length})</div>${rows}`}
    <div class="mact" style="margin-top:14px;border-top:1px solid var(--border);padding-top:12px">
      ${canAdd?`<button class="btn-primary" onclick="closeModal();openShiftModal('${dk}')">${ICON.plus} Aggiungi turno</button>`:''}
      <button class="btn-secondary" onclick="closeModal()">Chiudi</button>
    </div>`);
}

// ── Popup dettaglio singola entry (da pill calendario) ──
function openEntryDetail(dk, idx) {
  const entries = DB.shifts[dk] || [];
  const e = entries[idx];
  if (!e) return;
  const u = DB.users.find(x=>x.id===e.userId);
  if (!u) return;
  const parts = dk.split('-');
  const lbl = `${parts[2]}/${parts[1]}/${parts[0]}`;

  const visite = e.visite && e.visite.length ? e.visite : (e.restId ? [{restId:e.restId,activityId:e.activityId||''}] : []);
  let visiteHtml = '';
  if (visite.length) {
    visiteHtml = `<div style="margin-top:12px">
      <div style="font-size:10px;font-weight:600;color:var(--text3);text-transform:uppercase;letter-spacing:0.5px;margin-bottom:8px">Ristoranti da visitare</div>`;
    visite.forEach((v,i) => {
      const vr = DB.restaurants.find(r=>r.id===v.restId);
      const va = v.activityId ? DB.activities.find(a=>a.id===v.activityId) : null;
      if (!vr) return;
      visiteHtml += `<div style="display:flex;align-items:center;gap:8px;padding:7px 10px;border-radius:var(--r);border:1px solid var(--border);background:var(--bg);margin-bottom:5px;">
        <span style="font-size:11px;font-weight:600;color:var(--text3);font-family:'DM Mono',monospace;width:14px">${i+1}</span>
        <span class="entry-rest-tag">${ICON.rest}${vr.name}</span>
        ${va?`<span class="entry-act-tag" style="background:${va.color}20;color:${va.color};border:1px solid ${va.color}40">${ICON.tag}${va.name}</span>`:'<span style="font-size:10px;color:var(--text3);font-style:italic">Nessuna attività</span>'}
      </div>`;
    });
    visiteHtml += '</div>';
  } else {
    visiteHtml = `<div style="font-size:12px;color:var(--text3);font-style:italic;margin-top:10px">Nessuna visita pianificata</div>`;
  }

  const sub = e.subMngId && DB.mngAnag[e.subMngId];

  showModal(`
    <div class="modal-title" style="gap:10px">
      <div class="entry-avatar" style="background:${LBG[u.level]};color:${LC[u.level]};width:32px;height:32px;font-size:11px;border-radius:50%;display:flex;align-items:center;justify-content:center;font-weight:700;flex-shrink:0">${ini(u.name)}</div>
      <div>
        <div style="font-size:15px;font-weight:600">${u.name}</div>
        <div style="font-size:11px;color:var(--text3)">${lbl}</div>
      </div>
    </div>
    <div style="display:flex;align-items:center;gap:8px;flex-wrap:wrap">
      <span class="lbadge lv-${u.level}">${LN[u.level]}</span>
      <span class="stag ${SHIFT_CSS[e.shift]||'s-off'}" style="font-size:13px;padding:4px 12px">${e.shift}</span>
      ${sub?`<span style="font-size:11px;color:var(--text3);font-style:italic">Sost: ${sub.nome}</span>`:''}
    </div>
    ${visiteHtml}
    <div class="mact" style="margin-top:14px">
      <button class="btn-primary" onclick="closeModal();openEditModal('${dk}',${idx})">${ICON.edit} Modifica</button>
      <button class="btn-secondary" onclick="closeModal()">Chiudi</button>
    </div>`);
} 
// ── Popup dettaglio ristorante (vista RISTORANTE): mostra Direttore + MNG in turno ──
function openRestDetail(dk, restId) {
  const rest = DB.restaurants.find(r=>r.id===restId);
  if (!rest) return;
  const parts = dk.split('-');
  const lbl = `${parts[2]}/${parts[1]}/${parts[0]}`;
  const allShifts = DB.shifts[dk] || [];

  // Direttore del ristorante
  const dirUser = DB.users.find(u => u.level==='direttore' && u.rests && u.rests.includes(restId));
  const dirEntry = dirUser ? allShifts.find(e => !e.isMng && e.userId===dirUser.id) : null;

  // MNG in turno (collegati al direttore di questo ristorante)
  const mngEntries = allShifts.filter(e => {
    if (!e.isMng) return false;
    if (e.restId && e.restId !== restId) return false;
    if (!e.restId && dirUser && e.dirId !== dirUser.id) return false;
    return canSeeEntry(e);
  });

  let html = '';

  // Sezione Direttore
  if (dirUser) {
    const col = LC['direttore'];
    html += `<div style="margin-bottom:14px">
      <div style="font-size:10px;font-weight:600;color:var(--text3);text-transform:uppercase;letter-spacing:0.5px;margin-bottom:8px">Direttore</div>
      <div style="display:flex;align-items:center;gap:10px;padding:10px;border-radius:var(--r2);border:1px solid var(--border);background:var(--bg)">
        <div style="width:34px;height:34px;border-radius:50%;background:var(--coral-bg);color:var(--coral);display:flex;align-items:center;justify-content:center;font-size:12px;font-weight:700;font-family:'DM Mono',monospace;border:1px solid #5c1a1a;flex-shrink:0">${ini(dirUser.name)}</div>
        <span style="font-weight:600;flex:1;color:var(--text)">${dirUser.name}</span>
        ${dirEntry
          ? `<span class="stag ${SHIFT_CSS[dirEntry.shift]||'s-off'}" style="font-size:13px;padding:4px 12px">${dirEntry.shift}</span>`
          : `<span style="font-size:11px;color:var(--text3);font-style:italic">Turno non inserito</span>`}
      </div>
    </div>`;
  }

  // Sezione MNG
  html += `<div>
    <div style="font-size:10px;font-weight:600;color:var(--text3);text-transform:uppercase;letter-spacing:0.5px;margin-bottom:8px">MNG in turno (${mngEntries.length})</div>`;
  if (!mngEntries.length) {
    html += `<div style="font-size:12px;color:var(--text3);font-style:italic;padding:10px 0;text-align:center">Nessun MNG in turno</div>`;
  } else {
    mngEntries.forEach(e => {
      const mg = DB.mngAnag[e.mngId]; if (!mg) return;
      const hasTel = mg.tel && mg.tel.trim();
      const tel = hasTel ? mg.tel.trim().replace(/\s/g,'') : '';
      html += `<div style="display:flex;align-items:center;gap:10px;padding:10px;border-radius:var(--r2);border:1px solid var(--border);background:var(--bg);margin-bottom:6px">
        <div style="width:34px;height:34px;border-radius:50%;background:var(--teal-bg);color:var(--teal);display:flex;align-items:center;justify-content:center;font-size:12px;font-weight:700;font-family:'DM Mono',monospace;border:1px solid #0f3832;flex-shrink:0">${ini(mg.nome)}</div>
        <div style="flex:1">
          <div style="font-weight:600;font-size:13px;color:var(--text)">${mg.nome}</div>
          <div style="font-size:11px;color:var(--text3);margin-top:2px;display:flex;align-items:center;gap:5px">
            ${ICON.phone}
            ${hasTel ? `<a href="tel:${tel}" style="color:var(--green);text-decoration:none;font-weight:500">${mg.tel}</a>` : '<span style="font-style:italic">Telefono non inserito</span>'}
          </div>
        </div>
        <span class="stag ${SHIFT_CSS[e.shift]||'s-off'}" style="font-size:13px;padding:4px 12px">${e.shift}</span>
        ${hasTel ? `<a href="tel:${tel}" style="display:flex;align-items:center;justify-content:center;width:36px;height:36px;border-radius:50%;background:var(--green-bg);color:var(--green);border:1px solid #1a5c32;text-decoration:none;flex-shrink:0;font-size:18px" title="Chiama ${mg.nome}">📞</a>` : ''}
        <button class="btn-icon" onclick="closeModal();openEditModal('${dk}',${allShifts.indexOf(e)})" title="Modifica">${ICON.edit}</button>
      </div>`;
    });
  }
  html += '</div>';

  showModal(`
    <div class="modal-title">
      <div style="width:32px;height:32px;border-radius:var(--r);background:var(--coral-bg);color:var(--coral);display:flex;align-items:center;justify-content:center;flex-shrink:0">${ICON.rest}</div>
      <div>
        <div style="font-size:15px;font-weight:600">${rest.name}</div>
        <div style="font-size:11px;color:var(--text3)">${lbl}</div>
      </div>
    </div>
    ${html}
    <div class="mact" style="margin-top:14px">
      <button class="btn-primary" onclick="closeModal();openShiftModal('${dk}')">+ Aggiungi turno</button>
      <button class="btn-secondary" onclick="closeModal()">Chiudi</button>
    </div>`);
}



// ─── LIST ─────────────────────────────────────────────────────────────────────
function renderList(mc) {
  const y=ST.year, mo=ST.month, dim=new Date(y,mo+1,0).getDate();
  let h = `<div class="cal-header">
    <div class="cal-title">${MN[mo]} ${y} — Attività</div>
    <div class="cal-nav-row">
      <button class="cal-nav-btn" onclick="prevM()">&#8592;</button>
      <button class="today-btn" onclick="goToday()">Oggi</button>
      <button class="cal-nav-btn" onclick="nextM()">&#8594;</button>
    </div>
  </div>`;
  for (let d=1; d<=dim; d++) {
    const dk = y+'-'+(mo+1)+'-'+d;
    const entries = getVisible(dk);
    const dow = new Date(y,mo,d).getDay();
    h += `<div class="day-card">
      <div class="day-card-header">
        <div class="day-card-date">${DN[dow]} ${d} ${MN[mo]}</div>
        <div style="display:flex;align-items:center;gap:8px">
          ${entries.length ? `<span class="day-card-count">${entries.length}</span>` : ''}
          <button class="add-day-btn" onclick="openShiftModal('${dk}')">${ICON.plus} Aggiungi</button>
        </div>
      </div>
      <div class="day-card-body">`;
    if (!entries.length) {
      h += `<div class="empty-day">Nessuna attività</div>`;
    } else {
      entries.forEach((e, i) => {
        const rest = DB.restaurants.find(r => r.id === e.restId);
        if (e.isMng) {
          const mg = DB.mngAnag[e.mngId]; if (!mg) return;
          const sub = e.subMngId && DB.mngAnag[e.subMngId];
          h += `<div class="entry-row">
            <div class="entry-avatar" style="background:var(--teal-bg);color:var(--teal)">${ini(mg.nome)}</div>
            <span class="entry-name">${mg.nome}</span>
            <span class="tag-small lv-mng">MNG</span>
            ${rest ? `<span class="entry-rest-tag">${ICON.rest}${rest.name}</span>` : ''}
            <span class="stag ${SHIFT_CSS[e.shift]||'s-off'}">${e.shift}</span>
            ${sub ? `<span class="entry-sub">sost. ${sub.nome.split(' ')[0]}</span>` : ''}
            <button class="btn-icon" onclick="openEditModal('${dk}',${i})" title="Modifica" style="flex-shrink:0">${ICON.edit}</button>
            <button class="del-btn" onclick="delEntry('${dk}',${i})" title="Elimina">${ICON.x}</button>
          </div>`;
        } else {
          const u = DB.users.find(x=>x.id===e.userId); if (!u) return;
          const sub = e.subMngId && DB.mngAnag[e.subMngId];
          // Build visits display - support both old single and new multi-visit
          const visite = e.visite && e.visite.length ? e.visite : (e.restId ? [{restId:e.restId,activityId:e.activityId||''}] : []);
          const visiteTags = visite.map(v => {
            const vr = DB.restaurants.find(r=>r.id===v.restId);
            const va = v.activityId ? DB.activities.find(a=>a.id===v.activityId) : null;
            return `<span class="entry-rest-tag">${ICON.rest}${vr?vr.name:'?'}</span>${va?`<span class="entry-act-tag" style="background:${va.color}20;color:${va.color};border:1px solid ${va.color}40">${ICON.tag}${va.name}</span>`:''}`;
          }).join('');
          h += `<div class="entry-row">
            <div class="entry-avatar" style="background:${LBG[u.level]};color:${LC[u.level]}">${ini(u.name)}</div>
            <span class="entry-name">${u.name}</span>
            <span class="tag-small lv-${u.level}">${LN[u.level]}</span>
            <span class="stag ${SHIFT_CSS[e.shift]||'s-off'}">${e.shift}</span>
            <div class="visit-entry-tags">${visiteTags}</div>
            ${sub ? `<span class="entry-sub">sost. ${sub.nome.split(' ')[0]}</span>` : ''}
            <button class="btn-icon" onclick="openEditModal('${dk}',${i})" title="Modifica" style="flex-shrink:0">${ICON.edit}</button>
            <button class="del-btn" onclick="delEntry('${dk}',${i})" title="Elimina">${ICON.x}</button>
          </div>`;
        }
      });
    }
    h += '</div></div>';
  }
  mc.innerHTML = h;
}

function delEntry(dk, idx) {
  if (!DB.shifts[dk]) return;
  DB.shifts[dk].splice(idx, 1);
  renderAll(); save(); setStatus('Turno eliminato');
}

// ─── SHIFT MODAL ──────────────────────────────────────────────────────────────
let pendDate = null;
// turni MNG pendenti (aggiunti nel modal prima di salvare)
let pendMngRows = [];

function openShiftModal(dk) {
  const m = me();
  if (!canInsert(m.id)) { setStatus('Non hai il permesso di inserire turni'); return; }
  pendDate = dk;
  pendMngRows = [];
  const parts = dk.split('-');
  const lbl = `${parts[2]}/${parts[1]}/${parts[0]}`;
  const myRests = getRestsFor(m.id);
  const allRestOpts = myRests.map(r => `<option value="${r.id}">${r.name}</option>`).join('');
  const actOpts = `<option value="">— Nessuna —</option>` + DB.activities.map(a=>`<option value="${a.id}">${a.name}</option>`).join('');
  const shiftOpts = SHIFT_ALL.map(s=>`<option value="${s}">${s}</option>`).join('');

  let body = '';

  // ── DIRETTORE: proprio turno + 4 box fissi cliccabili AP/M/S/CH ──
  if (m.level === 'direttore') {
    const mngs = getMNGs(m.id);
    const mngOptsAll = `<option value="">— Nessuno —</option>` + mngs.map(mg=>`<option value="${mg.id}">${mg.nome}</option>`).join('');
    const selfShiftOpts = SHIFT_ALL.map(s=>`<option value="${s}">${s} — ${getShiftLabel(s)}</option>`).join('');

    // MNG usati ieri (da escludere nei turni di oggi)
    const prevDk = getPrevDayKey(dk);
    const usedYesterday = prevDk ? (DB.shifts[prevDk]||[]).filter(e=>e.isMng&&e.dirId===m.id).map(e=>e.mngId) : [];

    const turniMNG = ['AP','M','S','CH'];
    const turniColors = {AP:'#1565C0',M:'#2e7d32',S:'#e65100',CH:'#6a1b9a'};
    const turniDesc = {AP:'Apertura',M:'Mattina',S:'Sera',CH:'Chiusura'};

    const mngBoxes = turniMNG.map(t => {
      const dbMngs = (DB.shifts[dk]||[]).filter(e=>e.isMng&&e.dirId===m.id&&e.shift===t);
      const dbChips = dbMngs.map(e=>{const mg=DB.mngAnag[e.mngId];return mg?`<span style="background:${turniColors[t]}30;color:${turniColors[t]};padding:2px 8px;border-radius:4px;font-size:11px;border:1px solid ${turniColors[t]}50">${mg.nome}</span>`:''}).join('');
      return `<div id="mngBox_${t}" onclick="toggleMngBox('${t}')"
        style="border:2px solid ${turniColors[t]};border-radius:var(--r2);padding:12px;cursor:pointer;background:${turniColors[t]}10;transition:all .15s">
        <div style="display:flex;align-items:center;gap:8px;margin-bottom:6px">
          <span style="font-family:'DM Mono',monospace;font-weight:700;font-size:18px;color:${turniColors[t]}">${t}</span>
          <span style="font-size:11px;color:var(--text2)">${turniDesc[t]}</span>
          <span style="margin-left:auto;font-size:10px;color:var(--text3)">▼</span>
        </div>
        <div style="display:flex;flex-wrap:wrap;gap:4px;min-height:20px" id="mngBoxChips_${t}">${dbChips||`<span style="font-size:10px;color:var(--text3);font-style:italic">Nessuno</span>`}</div>
        <div id="mngBoxDropdown_${t}" style="display:none;margin-top:8px;border-top:1px solid ${turniColors[t]}40;padding-top:8px" onclick="event.stopPropagation()">
          <div id="mngList_${t}" style="display:flex;flex-direction:column;gap:5px"></div>
          <button type="button" onclick="event.stopPropagation();addMngToShift('${t}')"
            style="margin-top:6px;width:100%;padding:6px;border:1px dashed ${turniColors[t]};border-radius:var(--r);background:transparent;color:${turniColors[t]};font-size:12px;cursor:pointer;font-family:'DM Sans',sans-serif">
            + Aggiungi MNG
          </button>
        </div>
      </div>`;
    }).join('');

    body = `
      <div style="font-size:10px;font-weight:600;color:var(--accent);text-transform:uppercase;letter-spacing:0.8px;margin-bottom:8px;padding-bottom:6px;border-bottom:1px solid var(--border)">Il mio turno</div>
      <div class="frow">
        <label>Turno</label>
        <select id="dirSelfShift" onchange="onDirSelfShiftChange()">
          <option value="">— Seleziona —</option>${selfShiftOpts}
        </select>
      </div>
      <div id="dirSubRow" class="frow" style="display:none">
        <label>MNG sostituto (obbligatorio)</label>
        <select id="dirSubSel">${mngOptsAll}</select>
        <div class="warn-msg" id="dirSubWarn" style="display:none">Seleziona il sostituto MNG</div>
      </div>
      <div style="font-size:10px;font-weight:600;color:var(--accent);text-transform:uppercase;letter-spacing:0.8px;margin:14px 0 10px;padding-top:10px;border-top:1px solid var(--border)">Turni MNG — clicca un box per assegnare</div>
      ${usedYesterday.length ? `<div style="font-size:11px;color:var(--amber);margin-bottom:8px;padding:5px 10px;background:var(--amber-bg);border-radius:var(--r)">⚠ Ieri in turno: ${usedYesterday.map(id=>DB.mngAnag[id]?.nome||'').filter(Boolean).join(', ')} — esclusi oggi</div>` : ''}
      ${!mngs.length
        ? `<div style="font-size:12px;color:var(--text3);font-style:italic">Nessun MNG in anagrafica.</div>`
        : `<div style="display:grid;grid-template-columns:1fr 1fr;gap:8px">${mngBoxes}</div>`}`;

  // ── UFFICIO e SUPERVISORE: turno + fino a 4 visite ──
  } else {
    const visiteRows = [1,2,3,4].map(i => `
      <div class="visit-row">
        <div class="visit-num">Visita ${i}</div>
        <div class="frow" style="margin:0">
          <label style="font-size:10px">Ristorante</label>
          <select id="vRest${i}" style="font-size:12px;padding:5px 8px">
            <option value="">— Nessuno —</option>${allRestOpts}
          </select>
        </div>
        <div class="frow" style="margin:0">
          <label style="font-size:10px">Attività</label>
          <select id="vAct${i}" style="font-size:12px;padding:5px 8px">${actOpts}</select>
        </div>
      </div>`).join('');
    body = `
      <div class="frow"><label>Turno</label>
        <select id="mdShift" onchange="onAdminShiftChange()">
          <option value="">— Seleziona —</option>${shiftOpts}
        </select>
      </div>
      <div id="mdVisiteBlock" style="display:none">
        <div style="font-size:10px;font-weight:600;color:var(--text3);text-transform:uppercase;letter-spacing:0.5px;margin-bottom:8px">
          Ristoranti da visitare (fino a 4)
        </div>
        <div class="visits-block">${visiteRows}</div>
      </div>`;
  }

  showModal(`
    <div class="modal-title">${ICON.plus} ${m.level==='direttore'?'Inserimento turni':'Nuovo turno'} — ${lbl}</div>
    ${body}
    <div class="mact">
      <button class="btn-secondary" onclick="closeModal()">Annulla</button>
      <button class="btn-primary" onclick="saveShift()">Salva</button>
    </div>`);
}

function getPrevDayKey(dk) {
  const [y,mo,d] = dk.split('-').map(Number);
  const prev = new Date(y, mo-1, d-1);
  if (prev.getMonth() !== mo-1 && d === 1) return null;
  return `${prev.getFullYear()}-${prev.getMonth()+1}-${prev.getDate()}`;
}

function toggleMngBox(turno) {
  const dropdown = document.getElementById('mngBoxDropdown_'+turno);
  const box = document.getElementById('mngBox_'+turno);
  if (!dropdown) return;
  const isOpen = dropdown.style.display !== 'none';
  // Chiudi tutti gli altri
  ['AP','M','S','CH'].forEach(t => {
    const d = document.getElementById('mngBoxDropdown_'+t);
    if (d) d.style.display = 'none';
  });
  if (!isOpen) {
    dropdown.style.display = 'block';
    // Se non ci sono ancora righe, aggiunge una automaticamente
    const list = document.getElementById('mngList_'+turno);
    if (list && list.children.length === 0) addMngToShift(turno);
  }
}

// Aggiunge una riga MNG al turno fisso (esclude usati nello stesso turno + usati ieri)
function addMngToShift(turno) {
  const m = me();
  const mngs = getMNGs(m.id);
  const dk = pendDate;

  // MNG esclusi: già in questo turno oggi + usati ieri in qualsiasi turno
  const usedInDb = (DB.shifts[dk]||[]).filter(e=>e.isMng&&e.dirId===m.id&&e.shift===turno).map(e=>e.mngId);
  const prevDk = getPrevDayKey(dk);
  const usedYesterday = prevDk ? (DB.shifts[prevDk]||[]).filter(e=>e.isMng&&e.dirId===m.id).map(e=>e.mngId) : [];
  const container = document.getElementById('mngList_'+turno);
  const alreadyInModal = Array.from(container?.querySelectorAll('select')||[]).map(s=>s.value).filter(Boolean);
  const used = [...new Set([...usedInDb, ...usedYesterday, ...alreadyInModal])];
  const available = mngs.filter(mg=>!used.includes(mg.id));

  if (!available.length) {
    setStatus(`Nessun MNG disponibile per ${turno} (tutti in turno ieri o già assegnati)`);
    return;
  }
  if (!container) return;

  const rowId = `mngr_${turno}_${Date.now()}`;
  const opts = available.map(mg=>`<option value="${mg.id}">${mg.nome}</option>`).join('');
  const row = document.createElement('div');
  row.id = rowId;
  row.style.cssText = 'display:flex;align-items:center;gap:8px;margin-bottom:4px';
  row.innerHTML = `
    <select onchange="refreshShiftMngMenus()" style="flex:1;font-size:12px;padding:5px 8px;border:1px solid var(--border);border-radius:var(--r);background:var(--bg3);color:var(--text);outline:none">
      <option value="">— Seleziona MNG —</option>${opts}
    </select>
    <button type="button" onclick="document.getElementById('${rowId}').remove();refreshShiftMngMenus();checkMngEmpty('${turno}')"
      style="width:26px;height:26px;border-radius:var(--r);border:1px solid var(--border);background:transparent;color:var(--text3);cursor:pointer;display:flex;align-items:center;justify-content:center;flex-shrink:0;font-size:14px">✕</button>`;
  container.appendChild(row);
}

function checkMngEmpty(turno) {
  const container = document.getElementById('mngList_'+turno);
  if (!container) return;
  const rows = container.querySelectorAll('[id^="mngr_"]');
  const emptyMsg = document.getElementById('mngEmpty_'+turno);
  if (emptyMsg) emptyMsg.style.display = rows.length===0 ? 'block' : 'none';
}

function refreshShiftMngMenus() {
  // Esclude solo MNG già selezionati NELLO STESSO turno (non tra turni diversi)
  ['AP','M','S','CH'].forEach(turno => {
    const container = document.getElementById('mngList_'+turno);
    if (!container) return;
    const selects = Array.from(container.querySelectorAll('select'));
    selects.forEach((sel, idx) => {
      const currentVal = sel.value;
      // Solo gli altri select dello STESSO turno
      const otherInSameShift = selects.filter((_,i)=>i!==idx).map(s=>s.value).filter(Boolean);
      const m = me();
      const mngs = getMNGs(m.id);
      const dk = pendDate;
      // MNG già salvati in DB per questo stesso turno
      const usedInDb = (DB.shifts[dk]||[]).filter(e=>e.isMng&&e.dirId===m.id&&e.shift===turno).map(e=>e.mngId);
      const allUsed = [...usedInDb, ...otherInSameShift];
      const available = mngs.filter(mg=>!allUsed.includes(mg.id)||mg.id===currentVal);
      sel.innerHTML = `<option value="">— Seleziona MNG —</option>`+available.map(mg=>`<option value="${mg.id}"${mg.id===currentVal?' selected':''}>${mg.nome}</option>`).join('');
    });
  });
}

// compatibilità: funzioni vecchie non più usate ma potrebbero restare nel DOM
function addMngRow(){}
function onMngRowChange(){}
function removeMngRow(rowId){const el=document.getElementById(rowId);if(el)el.remove();}
function refreshMngMenus(){}

function onAdminShiftChange() {
  const s = document.getElementById('mdShift')?.value;
  const isPres = SHIFT_PRES.includes(s);
  const vb = document.getElementById('mdVisiteBlock');
  if (vb) vb.style.display = isPres ? 'block' : 'none';
}

function onDirSelfShiftChange() {
  const s = document.getElementById('dirSelfShift')?.value;
  const row = document.getElementById('dirSubRow');
  if (row) row.style.display = SHIFT_ASSENZA.includes(s) ? 'flex' : 'none';
  if (document.getElementById('dirSubWarn')) document.getElementById('dirSubWarn').style.display = 'none';
}

function saveShift() {
  const m = me();

  // ── DIRETTORE: salva proprio turno + MNG dai 4 pannelli fissi ──
  if (m.level === 'direttore') {
    const selfShift = document.getElementById('dirSelfShift')?.value;
    if (!selfShift) { setStatus('Seleziona il tuo turno'); return; }

    if (SHIFT_ASSENZA.includes(selfShift)) {
      const subId = document.getElementById('dirSubSel')?.value;
      if (!subId) {
        const w = document.getElementById('dirSubWarn');
        if (w) w.style.display = 'block';
        setStatus('Seleziona il MNG sostituto');
        return;
      }
      addEntry(pendDate, {isMng:false, userId:m.id, shift:selfShift, subMngId:subId, restId:''});
    } else {
      addEntry(pendDate, {isMng:false, userId:m.id, shift:selfShift, restId:''});
    }

    // Leggi i 4 pannelli fissi AP/M/S/N
    ['AP','M','S','CH'].forEach(turno => {
      const container = document.getElementById('mngList_'+turno);
      if (!container) return;
      container.querySelectorAll('select').forEach(sel => {
        const mngId = sel.value;
        if (mngId) addEntry(pendDate, {isMng:true, mngId, dirId:m.id, shift:turno, restId:''});
      });
    });

  // ── UFFICIO e SUPERVISORE ──
  } else {
    const shift = document.getElementById('mdShift')?.value;
    if (!shift) { setStatus('Seleziona un turno'); return; }
    const isPres = SHIFT_PRES.includes(shift);
    const visite = [];
    if (isPres) {
      for (let i=1; i<=4; i++) {
        const r = document.getElementById('vRest'+i)?.value;
        const a = document.getElementById('vAct'+i)?.value;
        if (r) visite.push({restId:r, activityId:a||''});
      }
    }
    const restId = visite.length ? visite[0].restId : '';
    const activityId = visite.length ? visite[0].activityId : '';
    addEntry(pendDate, {isMng:false, userId:m.id, shift, restId, activityId, visite: isPres ? visite : []});
  }
  closeModal(); save(); setStatus('Turno salvato'); renderAll();
}

// ─── MODAL SYSTEM ─────────────────────────────────────────────────────────────
function showModal(html) {
  let ov = document.getElementById('modalOverlay');
  if (!ov) { ov = document.createElement('div'); ov.id='modalOverlay'; ov.className='modal-overlay'; document.body.appendChild(ov); }
  ov.innerHTML = `<div class="modal fade-in" onclick="event.stopPropagation()">${html}</div>`;
  ov.style.display = 'flex';
  ov.onclick = closeModal;
}
function closeModal() {
  const ov = document.getElementById('modalOverlay');
  if (ov) ov.style.display = 'none';
  pendDate = null; editUid = null; editRid = null; editAid = null; editMid = null;
  if (ST.view !== 'cal' && ST.view !== 'list') renderAll();
}

// ─── ANAGRAFICHE (UFFICIO) ────────────────────────────────────────────────────
let editUid=null, editRid=null, editAid=null, editMid=null;

function renderAnag(mc) {
  const tab = ST.anagTab || 'users';
  mc.innerHTML = `
    <div class="anag-header" style="margin-bottom:0">
      <div class="cal-title">Anagrafiche</div>
    </div>
    <div class="tabs" style="margin-top:14px">
      <button class="tab-btn${tab==='users'?' active':''}" onclick="setAnagTab('users')">${ICON.users} Utenti</button>
      <button class="tab-btn${tab==='rests'?' active':''}" onclick="setAnagTab('rests')">${ICON.rest} Ristoranti</button>
      <button class="tab-btn${tab==='acts'?' active':''}" onclick="setAnagTab('acts')">${ICON.tag} Attività</button>
      <button class="tab-btn${tab==='pins'?' active':''}" onclick="setAnagTab('pins')" style="border-color:${tab==='pins'?'var(--amber)':'var(--border)'};${tab==='pins'?'background:var(--amber-bg);color:var(--amber)':''}">🔑 PIN accesso</button>
    </div>
    <div id="anagContent"></div>`;

  const ac = document.getElementById('anagContent');
  if      (tab==='users') renderAnagUsers(ac);
  else if (tab==='rests') renderAnagRests(ac);
  else if (tab==='acts')  renderAnagActs(ac);
  else                    renderAnagPins(ac);
}

function setAnagTab(t) { ST.anagTab=t; renderAll(); }

function renderAnagPins(ac) {
  let h = `<div style="font-size:12px;color:var(--text3);margin-bottom:14px;padding:10px;background:var(--amber-bg);border:1px solid var(--amber);border-radius:var(--r);display:flex;align-items:center;gap:8px">
    <span style="font-size:16px">🔑</span>
    <span>Qui puoi vedere e modificare i PIN di accesso di tutti gli utenti. I PIN sono numerici a 4 cifre.</span>
  </div>`;
  ['ufficio','supervisore','direttore'].forEach(lv => {
    const us = DB.users.filter(u=>u.level===lv);
    if (!us.length) return;
    h += `<div class="anag-group">
      <div class="anag-group-label"><div style="width:7px;height:7px;border-radius:50%;background:${LC[lv]}"></div>${LN[lv]}</div>`;
    us.forEach(u => {
      const pinDisplay = u.pin && u.pin !== '' ? u.pin : '—';
      const pinSet = u.pin && u.pin !== '';
      h += `<div class="anag-row" style="align-items:center">
        <div class="entry-avatar" style="background:${LBG[u.level]};color:${LC[u.level]}">${ini(u.name)}</div>
        <span class="anag-name">${u.name}</span>
        <span class="lbadge lv-${u.level}" style="font-size:10px;padding:1px 7px">${LN[u.level]}</span>
        <div style="display:flex;align-items:center;gap:6px;margin-left:auto">
          <span style="font-family:'DM Mono',monospace;font-size:15px;letter-spacing:4px;color:${pinSet?'var(--text)':'var(--text3)'};background:var(--bg3);padding:4px 10px;border-radius:var(--r);border:1px solid var(--border);min-width:60px;text-align:center">
            ${pinSet?pinDisplay:'N/D'}
          </span>
          <button class="btn-icon" onclick="quickEditPin('${u.id}')" title="Modifica PIN" style="border-color:var(--amber);color:var(--amber)">✏️</button>
          ${!pinSet?`<span style="font-size:10px;color:var(--coral)">Non impostato</span>`:''}
        </div>
      </div>`;
    });
    h += '</div>';
  });
  ac.innerHTML = h;
}

function quickEditPin(uid) {
  const u = DB.users.find(x=>x.id===uid);
  if (!u) return;
  showModal(`
    <div class="modal-title">🔑 Modifica PIN — ${u.name}</div>
    <div style="font-size:12px;color:var(--text3);margin-bottom:14px">PIN attuale: <strong style="font-family:'DM Mono',monospace;font-size:15px;color:var(--text)">${u.pin||'Non impostato'}</strong></div>
    <div class="frow">
      <label>Nuovo PIN (4 cifre)</label>
      <input type="text" id="quickPin" maxlength="4" placeholder="es. 1234"
        style="font-family:'DM Mono',monospace;font-size:22px;letter-spacing:8px;text-align:center"
        oninput="this.value=this.value.replace(/[^0-9]/g,'')" autofocus>
    </div>
    <div class="mact">
      <button class="btn-secondary" onclick="closeModal()">Annulla</button>
      <button class="btn-primary" onclick="saveQuickPin('${uid}')">Salva PIN</button>
    </div>`);
  setTimeout(()=>document.getElementById('quickPin')?.focus(),100);
}

function saveQuickPin(uid) {
  const pin = document.getElementById('quickPin').value.trim();
  if (!/^\d{4}$/.test(pin)) { setStatus('Il PIN deve essere esattamente 4 cifre'); return; }
  const u = DB.users.find(x=>x.id===uid);
  if (u) { u.pin=pin; save(); setStatus('PIN aggiornato per '+u.name); closeModal(); renderAll(); }
}

function renderAnagUsers(ac) {
  let h = `<div class="anag-header"><div class="anag-section-title">${ICON.users} Gestione utenti</div>
    <button class="add-btn" onclick="openUserModal(null)">${ICON.plus} Nuovo utente</button></div>`;
  ['ufficio','supervisore','direttore'].forEach(lv => {
    const us = DB.users.filter(u=>u.level===lv);
    h += `<div class="anag-group"><div class="anag-group-label"><div style="width:7px;height:7px;border-radius:50%;background:${LC[lv]}"></div>${LN[lv]} (${us.length})</div>`;
    if (!us.length) h += `<div class="empty-day">Nessun utente</div>`;
    us.forEach(u => {
      const rests = getRestsFor(u.id);
      h += `<div class="anag-row">
        <div class="entry-avatar" style="background:${LBG[u.level]};color:${LC[u.level]}">${ini(u.name)}</div>
        <span class="anag-name">${u.name}</span>
        <div class="anag-meta">${rests.map(r=>`<span class="tag-small" style="background:var(--bg3);color:var(--text2);border:1px solid var(--border)">${r.name}</span>`).join('') || '<span style="color:var(--text3);font-size:11px">—</span>'}
          ${u.canInsert!==false?`<span style="font-size:10px;color:var(--green)">✎ ins.</span>`:''}
          ${u.canView!==false?`<span style="font-size:10px;color:var(--accent)">👁 vis.</span>`:''}
        </div>
        <button class="btn-icon" onclick="openUserModal('${u.id}')" title="Modifica">${ICON.edit}</button>
        ${u.id!=='u1'&&u.id!=='u2'?`<button class="btn-icon danger" onclick="delUser('${u.id}')" title="Elimina">${ICON.trash}</button>`:''}
      </div>`;
    });
    h += '</div>';
  });
  ac.innerHTML = h;
}

function renderAnagRests(ac) {
  let h = `<div class="anag-header"><div class="anag-section-title">${ICON.rest} Ristoranti</div>
    <button class="add-btn" onclick="openRestModal(null)">${ICON.plus} Nuovo ristorante</button></div>`;
  if (!DB.restaurants.length) h += `<div class="empty-state"><div class="empty-icon">🍽️</div><div class="empty-text">Nessun ristorante inserito</div></div>`;
  DB.restaurants.forEach(r => {
    const dirs = getDirsForRest(r.id);
    const sups = getSupsForRest(r.id);
    h += `<div class="anag-row">
      <div style="width:34px;height:34px;border-radius:var(--r);background:var(--coral-bg);border:1px solid var(--coral-bg);display:flex;align-items:center;justify-content:center;color:var(--coral);flex-shrink:0">${ICON.rest}</div>
      <span class="anag-name">${r.name}</span>
      <div class="anag-meta">
        <span style="font-size:10px;color:var(--text3)">Dir: ${dirs.map(d=>d.name.split(' ')[0]).join(', ')||'—'}</span>
        <span style="font-size:10px;color:var(--text3)">·</span>
        <span style="font-size:10px;color:var(--text3)">Sup: ${sups.map(s=>s.name.split(' ')[0]).join(', ')||'—'}</span>
      </div>
      <button class="btn-icon" onclick="openRestModal('${r.id}')">${ICON.edit}</button>
      <button class="btn-icon danger" onclick="delRest('${r.id}')">${ICON.trash}</button>
    </div>`;
  });
  ac.innerHTML = h;
}

function renderAnagActs(ac) {
  let h = `<div class="anag-header"><div class="anag-section-title">${ICON.tag} Tipi di attività</div>
    <button class="add-btn" onclick="openActModal(null)">${ICON.plus} Nuova attività</button></div>
    <div style="font-size:12px;color:var(--text3);margin-bottom:12px">Queste attività appaiono nel menu durante l'inserimento turno per Ufficio e Supervisori (solo turni di presenza: AP, M, SW, S, N).</div>`;
  if (!DB.activities.length) h += `<div class="empty-state"><div class="empty-icon">🏷️</div><div class="empty-text">Nessuna attività definita</div></div>`;
  DB.activities.forEach(a => {
    h += `<div class="anag-row">
      <div class="color-dot" style="width:14px;height:14px;border-radius:50%;background:${a.color};flex-shrink:0"></div>
      <span class="anag-name">${a.name}</span>
      <span class="entry-act-tag" style="background:${a.color}20;color:${a.color};border:1px solid ${a.color}40">${a.name}</span>
      <button class="btn-icon" onclick="openActModal('${a.id}')">${ICON.edit}</button>
      <button class="btn-icon danger" onclick="delAct('${a.id}')">${ICON.trash}</button>
    </div>`;
  });
  ac.innerHTML = h;
}

// ─── MNG (DIRETTORE) ─────────────────────────────────────────────────────────
function renderAnagMNG(mc) {
  const m = me();
  const mngs = getMNGs(m.id);
  let h = `<div class="anag-header">
    <div class="cal-title">MNG — ${m.name}</div>
    <button class="add-btn" onclick="openMNGModal(null)">${ICON.plus} Nuovo MNG</button>
  </div>
  <div style="font-size:12px;color:var(--text3);margin-bottom:16px">Gestisci l'anagrafica dei tuoi MNG. Potrai poi assegnarli ai turni e come sostituti.</div>`;
  if (!mngs.length) {
    h += `<div class="empty-state"><div class="empty-icon">👥</div><div class="empty-text">Nessun MNG inserito<br><span style="font-size:11px">Clicca "+ Nuovo MNG" per aggiungere</span></div></div>`;
  } else {
    mngs.forEach(mg => {
      h += `<div class="mng-card">
        <div class="mng-avatar">${ini(mg.nome)}</div>
        <div class="mng-info">
          <div class="mng-name">${mg.nome}</div>
          <div class="mng-tel">${ICON.phone}<span>${mg.tel||'Telefono non inserito'}</span></div>
        </div>
        <button class="btn-icon" onclick="openMNGModal('${mg.id}')">${ICON.edit}</button>
        <button class="btn-icon danger" onclick="delMNG('${mg.id}')">${ICON.trash}</button>
      </div>`;
    });
  }
  mc.innerHTML = h;
}

// ─── FLAG ─────────────────────────────────────────────────────────────────────
function renderFlag(mc) {
  const tab = ST.flagTab || 'view';
  mc.innerHTML = `
    <div class="cal-title" style="margin-bottom:14px">${ICON.flag} Pannello flag</div>
    <div class="tabs">
      <button class="tab-btn${tab==='view'?' active':''}" onclick="setFlagTab('view')">Visibilità supervisori</button>
      <button class="tab-btn${tab==='insert'?' active':''}" onclick="setFlagTab('insert')">Permessi inserimento</button>
    </div>
    <div id="flagContent"></div>`;
  const fc = document.getElementById('flagContent');
  if (tab==='view') renderFlagView(fc);
  else              renderFlagInsert(fc);
}
function setFlagTab(t) { ST.flagTab=t; renderAll(); }

function renderFlagView(fc) {
  let h = `<div style="font-size:12px;color:var(--text3);margin-bottom:16px">Controlla quali utenti ogni supervisore può vedere nel calendario. Basato sui ristoranti condivisi.</div>`;
  const sups = DB.users.filter(u=>u.level==='supervisore');
  if (!sups.length) { fc.innerHTML = h + `<div class="empty-state"><div class="empty-icon">🔍</div><div class="empty-text">Nessun supervisore in anagrafica</div></div>`; return; }
  sups.forEach(sup => {
    const myR = getRestsFor(sup.id);
    const visible = DB.users.filter(u => (u.level==='direttore'||u.level==='supervisore') && myR.some(r=>u.rests&&u.rests.includes(r.id)));
    h += `<div class="flag-section">
      <div class="flag-group-label"><div style="width:7px;height:7px;border-radius:50%;background:${LC.supervisore}"></div>${sup.name}</div>`;
    if (!visible.length) { h += `<div class="empty-day">Nessun utente collegato ai suoi ristoranti</div>`; }
    visible.forEach(u => {
      const flags   = DB.flags[sup.id] || {};
      const checked = flags[u.id] !== false;
      h += `<div class="flag-item"><input type="checkbox" id="fv_${sup.id}_${u.id}" ${checked?'checked':''} onchange="setVisFlag('${sup.id}','${u.id}',this.checked)">
        <label for="fv_${sup.id}_${u.id}">${u.name} <span class="tag-small lv-${u.level}">${LN[u.level]}</span></label></div>`;
    });
    h += '</div>';
  });
  fc.innerHTML = h;
}

function renderFlagInsert(fc) {
  let h = `<div style="font-size:12px;color:var(--text3);margin-bottom:16px">Abilita o disabilita il permesso di inserimento turni per ogni utente.</div>`;
  ['ufficio','supervisore','direttore'].forEach(lv => {
    const us = DB.users.filter(u=>u.level===lv);
    h += `<div class="flag-section"><div class="flag-group-label"><div style="width:7px;height:7px;border-radius:50%;background:${LC[lv]}"></div>${LN[lv]}</div>`;
    if (!us.length) { h += `<div class="empty-day">Nessun utente</div>`; }
    us.forEach(u => {
      h += `<div class="flag-item">
        <input type="checkbox" id="fi_${u.id}" ${u.canInsert!==false?'checked':''} onchange="setInsertFlag('${u.id}',this.checked)">
        <label for="fi_${u.id}">${u.name}</label>
        <div class="flag-meta">${getRestsFor(u.id).map(r=>r.name).join(', ')||'—'}</div>
      </div>`;
    });
    h += '</div>';
  });
  fc.innerHTML = h;
}

function setVisFlag(supId, uid, val) {
  if (!DB.flags[supId]) DB.flags[supId] = {};
  DB.flags[supId][uid] = val; save(); setStatus('Flag visibilità aggiornato');
}
function setInsertFlag(uid, val) {
  const u = DB.users.find(x=>x.id===uid);
  if (u) u.canInsert=val; save(); setStatus('Permesso inserimento aggiornato');
}

// ─── EXPORT ───────────────────────────────────────────────────────────────────
function renderExport(mc) {
  const curM=ST.month+1, curY=ST.year;
  let mOpts=''; for(let mo=1;mo<=12;mo++) mOpts+=`<option value="${mo}"${mo===curM?' selected':''}>${MN[mo-1]}</option>`;
  let yOpts=''; const y0=curY; for(let y=y0-1;y<=y0+1;y++) yOpts+=`<option value="${y}"${y===curY?' selected':''}>${y}</option>`;
  const rOpts=`<option value="all">Tutti i ristoranti</option>`+DB.restaurants.map(r=>`<option value="${r.id}">${r.name}</option>`).join('');
  mc.innerHTML = `
    <div class="cal-title" style="margin-bottom:16px">${ICON.exp} Esportazione dati</div>
    <div class="export-card">
      <div class="export-card-title">${ICON.exp} Parametri</div>
      <div class="export-grid">
        <div class="frow" style="margin:0"><label>Mese</label><select id="expM">${mOpts}</select></div>
        <div class="frow" style="margin:0"><label>Anno</label><select id="expY">${yOpts}</select></div>
        <div class="frow" style="margin:0"><label>Ristorante</label><select id="expR">${rOpts}</select></div>
      </div>
      <div class="export-actions">
        <button class="dl-btn dl-csv" onclick="doCSV()">${ICON.dl} Scarica CSV (Excel)</button>
        <button class="dl-btn dl-pdf" onclick="doPDF()">${ICON.print} Stampa PDF</button>
      </div>
      <div id="expMsg" style="font-size:11px;color:var(--green);margin-top:10px;min-height:18px"></div>
    </div>
    <div class="export-card">
      <div class="export-card-title">Anteprima mese corrente</div>
      <div id="expPreview">${buildPreview(curM,curY,'all')}</div>
    </div>`;
  document.getElementById('expM').onchange = document.getElementById('expY').onchange = document.getElementById('expR').onchange = updatePreview;
}

function updatePreview() {
  const mo=parseInt(document.getElementById('expM').value);
  const y=parseInt(document.getElementById('expY').value);
  const rid=document.getElementById('expR').value;
  document.getElementById('expPreview').innerHTML = buildPreview(mo,y,rid);
}

function buildPreview(mo,y,rid) {
  const dim=new Date(y,mo,0).getDate(); let tot=0; const summary={};
  for (let d=1;d<=dim;d++) {
    const dk=`${y}-${mo}-${d}`;
    (DB.shifts[dk]||[]).forEach(e=>{
      if (rid!=='all'&&e.restId!==rid) return;
      tot++; const s=e.shift; summary[s]=(summary[s]||0)+1;
    });
  }
  if (!tot) return `<div style="font-size:12px;color:var(--text3);font-style:italic">Nessun turno inserito per questo periodo.</div>`;
  let h=`<div style="font-size:12px;color:var(--text2);margin-bottom:10px">Totale: <strong style="color:var(--text)">${tot}</strong> turni su ${dim} giorni</div>`;
  h += `<div style="display:flex;gap:6px;flex-wrap:wrap">`;
  SHIFT_ALL.forEach(s => { if(summary[s]) h+=`<span class="stag ${SHIFT_CSS[s]}">${s} ×${summary[s]}</span>`; });
  h += '</div>';
  const rests = rid==='all' ? DB.restaurants : DB.restaurants.filter(r=>r.id===rid);
  h += `<div style="margin-top:12px;display:flex;flex-direction:column;gap:4px">`;
  rests.forEach(r => {
    let cnt=0; for(let d=1;d<=dim;d++) cnt+=(DB.shifts[`${y}-${mo}-${d}`]||[]).filter(e=>e.restId===r.id).length;
    h += `<div style="font-size:11px;color:var(--text3)">${ICON.rest} ${r.name}: ${cnt} turni</div>`;
  });
  h += '</div>';
  return h;
}

function doCSV() {
  const mo=parseInt(document.getElementById('expM').value);
  const y=parseInt(document.getElementById('expY').value);
  const rid=document.getElementById('expR').value;
  const dim=new Date(y,mo,0).getDate();
  const rests=rid==='all'?DB.restaurants:DB.restaurants.filter(r=>r.id===rid);
  let csv=`\uFEFFTurniApp — ${MN[mo-1]} ${y}\n\n`;
  csv+=`Ristorante,Livello,Nome,Turno,Ristorante Visitato,Attività,Sostituto,Data\n`;
  for (let d=1;d<=dim;d++) {
    const dk=`${y}-${mo}-${d}`;
    (DB.shifts[dk]||[]).forEach(e=>{
      if (rid!=='all'&&e.restId!==rid) return;
      const rest=DB.restaurants.find(r=>r.id===e.restId);
      const act=e.activityId?DB.activities.find(a=>a.id===e.activityId):null;
      const sub=e.subMngId?DB.mngAnag[e.subMngId]:null;
      if (e.isMng) {
        const mg=DB.mngAnag[e.mngId]; if(!mg) return;
        csv+=`"${rest?.name||''}",MNG,"${mg.nome}",${e.shift},,,,${d}/${mo}/${y}\n`;
      } else {
        const u=DB.users.find(x=>x.id===e.userId); if(!u) return;
        const vr=DB.restaurants.find(r=>r.id===e.restId);
        csv+=`"${rest?.name||''}",${u.level},"${u.name}",${e.shift},"${vr?.name||''}","${act?.name||''}","${sub?.nome||''}",${d}/${mo}/${y}\n`;
      }
    });
  }
  const blob=new Blob([csv],{type:'text/csv;charset=utf-8'});
  const url=URL.createObjectURL(blob);
  const a=document.createElement('a'); a.href=url; a.download=`TurniApp_${MN[mo-1]}_${y}.csv`;
  document.body.appendChild(a); a.click(); document.body.removeChild(a); URL.revokeObjectURL(url);
  document.getElementById('expMsg').textContent='✓ File scaricato: TurniApp_'+MN[mo-1]+'_'+y+'.csv';
  setStatus('Export CSV completato');
}

function doPDF() {
  const mo=parseInt(document.getElementById('expM').value);
  const y=parseInt(document.getElementById('expY').value);
  const rid=document.getElementById('expR').value;
  const dim=new Date(y,mo,0).getDate();
  const rests=rid==='all'?DB.restaurants:DB.restaurants.filter(r=>r.id===rid);
  const SC={AP:'#dbeafe',M:'#dcfce7',SW:'#ede9fe',S:'#fef3c7',N:'#fee2e2',OFF:'#f1f5f9',PIR:'#fee2e2',FER:'#d1fae5',MAL:'#fee2e2',CONG:'#fce7f3'};
  const ST2={AP:'#1e40af',M:'#166534',SW:'#4c1d95',S:'#78350f',N:'#9f1239',OFF:'#374151',PIR:'#991b1b',FER:'#065f46',MAL:'#991b1b',CONG:'#831843'};
  let html=`<!DOCTYPE html><html><head><meta charset="utf-8"><title>TurniApp — ${MN[mo-1]} ${y}</title>
  <style>*{box-sizing:border-box;margin:0;padding:0}body{font-family:'Helvetica Neue',Arial,sans-serif;font-size:9px;color:#1a1a1a;padding:10mm}
  h1{font-size:16px;font-weight:700;color:#0f172a;margin-bottom:2px}
  .sub{font-size:10px;color:#64748b;margin-bottom:14px}
  h2{font-size:11px;font-weight:700;padding:4px 8px;background:#0f172a;color:#fff;margin:14px 0 6px;border-radius:4px}
  table{width:100%;border-collapse:collapse;margin-bottom:4px;table-layout:fixed}
  th{background:#334155;color:#fff;padding:3px 2px;font-size:8px;text-align:center;font-weight:600}
  th.name-col{text-align:left;width:100px}th.lv-col{width:40px}
  td{border:0.5px solid #cbd5e1;padding:2px;text-align:center;font-size:8px;overflow:hidden}
  td.name-col{text-align:left;font-weight:600;overflow:hidden;text-overflow:ellipsis;white-space:nowrap}
  td.tot{font-weight:700;background:#f8fafc}td.abs{font-weight:700}
  @media print{@page{size:A3 landscape;margin:8mm}h2{break-before:page}}</style></head><body>
  <h1>TurniApp — ${MN[mo-1]} ${y}</h1>
  <div class="sub">Generato il ${new Date().toLocaleDateString('it-IT')} · ${rests.length} ristorante/i</div>`;

  rests.forEach(rest => {
    html += `<h2>${rest.name}</h2>`;
    const people={};
    for (let d=1;d<=dim;d++) {
      const dk=`${y}-${mo}-${d}`;
      (DB.shifts[dk]||[]).filter(e=>e.restId===rest.id).forEach(e=>{
        const pid=e.isMng?e.mngId:e.userId;
        if (!people[pid]) {
          if (e.isMng) { const mg=DB.mngAnag[pid]; if(mg) people[pid]={name:mg.nome,level:'MNG'}; }
          else { const u=DB.users.find(x=>x.id===pid); if(u) people[pid]={name:u.name,level:u.level}; }
        }
      });
    }
    const pids=Object.keys(people);
    if (!pids.length) { html+=`<p style="color:#94a3b8;font-style:italic;font-size:11px">Nessun turno per questo ristorante.</p>`; return; }
    const dows=Array.from({length:dim},(_,i)=>new Date(y,mo-1,i+1).getDay());
    html+=`<table><tr><th class="name-col">Nome</th><th class="lv-col">Liv.</th>`;
    for(let d=1;d<=dim;d++) html+=`<th style="${dows[d-1]===0||dows[d-1]===6?'background:#92400e':''}">${DN[dows[d-1]][0]}${d}</th>`;
    html+=`<th class="tot">Tot</th><th class="tot">Ass</th><th style="width:80px">Attività</th></tr>`;
    pids.forEach(pid => {
      const p=people[pid]; const lc={ufficio:'#7c3aed',supervisore:'#15803d',direttore:'#c2410c',mng:'#0f766e'}[p.level]||'#475569';
      const acts={};
      html+=`<tr><td class="name-col">${p.name}</td><td class="lv-col" style="color:${lc};font-weight:700;font-size:7px">${p.level.toUpperCase()}</td>`;
      let tot=0,abs=0;
      for(let d=1;d<=dim;d++){
        const dk=`${y}-${mo}-${d}`;
        const e=(DB.shifts[dk]||[]).find(e2=>e2.restId===rest.id&&(e2.isMng?e2.mngId:e2.userId)===pid);
        const s=e?e.shift:'';
        if(s){tot++;if(SHIFT_ASSENZA.includes(s))abs++;if(e.activityId){const a=DB.activities.find(x=>x.id===e.activityId);if(a)acts[a.name]=(acts[a.name]||0)+1;}}
        html+=`<td style="background:${s?SC[s]:'#fff'};color:${s?ST2[s]:'#cbd5e1'};font-weight:600">${s||'·'}</td>`;
      }
      const al=Object.entries(acts).map(([n,c])=>`${n}(${c})`).join(', ');
      html+=`<td class="tot">${tot}</td><td class="abs" style="color:${abs>0?'#991b1b':'#166534'}">${abs}</td><td style="text-align:left;font-size:7px;color:#475569">${al}</td></tr>`;
    });
    html+='</table>';
  });
  html+='</body></html>';
  const blob=new Blob([html],{type:'text/html;charset=utf-8'});
  const url=URL.createObjectURL(blob);
  const w=window.open(url,'_blank');
  if(w) setTimeout(()=>{w.print();URL.revokeObjectURL(url);},800);
  setStatus('PDF aperto per la stampa');
}

// ─── MODALS: UTENTE ──────────────────────────────────────────────────────────
function openUserModal(uid) {
  editUid = uid;
  const ex = uid ? DB.users.find(u=>u.id===uid) : null;
  const lvOpts = ['ufficio','supervisore','direttore'].map(lv=>`<option value="${lv}"${ex&&ex.level===lv?' selected':''}>${LN[lv]}</option>`).join('');
  const rChk = DB.restaurants.map(r => {
    const c = ex && ex.rests && ex.rests.includes(r.id);
    return `<div class="check-item"><input type="checkbox" id="ur_${r.id}" ${c?'checked':''} style="accent-color:var(--accent)"><label for="ur_${r.id}" style="cursor:pointer">${r.name}</label></div>`;
  }).join('');
  showModal(`
    <div class="modal-title">${ICON.users} ${uid?'Modifica utente':'Nuovo utente'}</div>
    <div class="frow"><label>Nome e Cognome (username)</label><input type="text" id="uName" value="${ex?ex.name:''}" placeholder="Mario Rossi"></div>
    <div class="frow"><label>Livello</label><select id="uLevel">${lvOpts}</select></div>
    <div class="frow"><label>PIN accesso (4 cifre)</label><input type="text" id="uPin" value="${ex?ex.pin||'':'0000'}" placeholder="es. 1234" maxlength="4" pattern="[0-9]{4}" style="font-family:'DM Mono',monospace;letter-spacing:6px;font-size:18px"></div>
    <div class="frow"><label>Ristoranti assegnati</label><div class="check-grid">${rChk||'<div style="font-size:12px;color:var(--text3)">Nessun ristorante disponibile</div>'}</div></div>
    <div class="section-sep"></div>
    <div class="section-mini-label">Permessi</div>
    <div class="frow"><label><input type="checkbox" id="uCanInsert" ${ex?ex.canInsert!==false?'checked':'':'checked'} style="accent-color:var(--accent)"> Può inserire turni</label></div>
    <div class="frow"><label><input type="checkbox" id="uCanView" ${ex?ex.canView!==false?'checked':'':'checked'} style="accent-color:var(--accent)"> Può visualizzare il calendario</label></div>
    <div class="mact">
      <button class="btn-secondary" onclick="closeModal()">Annulla</button>
      <button class="btn-primary" onclick="saveUser()">Salva</button>
    </div>`);
}
function saveUser() {
  const name=document.getElementById('uName').value.trim();
  const level=document.getElementById('uLevel').value;
  const pin=document.getElementById('uPin').value.trim();
  const canInsert=document.getElementById('uCanInsert').checked;
  const canView=document.getElementById('uCanView').checked;
  if (!name) { setStatus('Inserisci nome e cognome'); return; }
  if (!/^\d{4}$/.test(pin)) { setStatus('Il PIN deve essere esattamente 4 cifre numeriche'); return; }
  const rests=DB.restaurants.filter(r=>document.getElementById('ur_'+r.id)?.checked).map(r=>r.id);
  if (editUid) { const u=DB.users.find(x=>x.id===editUid); if(u){u.name=name;u.level=level;u.pin=pin;u.rests=rests;u.canInsert=canInsert;u.canView=canView;} }
  else DB.users.push({id:'u'+Date.now(),name,level,pin,rests,canInsert,canView});
  closeModal(); save(); setStatus('Utente salvato: '+name); buildLoginSelect(); renderAll();
}
function delUser(uid) {
  if (!confirm('Eliminare questo utente?')) return;
  DB.users=DB.users.filter(u=>u.id!==uid); save(); buildLoginSelect(); renderAll(); setStatus('Utente eliminato');
}

// ─── MODALS: RISTORANTE ───────────────────────────────────────────────────────
function openRestModal(rid) {
  editRid=rid;
  const ex=rid?DB.restaurants.find(r=>r.id===rid):null;
  showModal(`
    <div class="modal-title">${ICON.rest} ${rid?'Modifica ristorante':'Nuovo ristorante'}</div>
    <div class="frow"><label>Nome ristorante</label><input type="text" id="rName" value="${ex?ex.name:''}" placeholder="Ristorante Roma"></div>
    <div class="mact">
      <button class="btn-secondary" onclick="closeModal()">Annulla</button>
      <button class="btn-primary" onclick="saveRest()">Salva</button>
    </div>`);
}
function saveRest() {
  const name=document.getElementById('rName').value.trim();
  if(!name){setStatus('Inserisci il nome');return;}
  if(editRid){const r=DB.restaurants.find(x=>x.id===editRid);if(r)r.name=name;}
  else DB.restaurants.push({id:'r'+Date.now(),name});
  closeModal();save();setStatus('Ristorante salvato: '+name);renderAll();
}
function delRest(rid) {
  if(!confirm('Eliminare questo ristorante?'))return;
  DB.restaurants=DB.restaurants.filter(r=>r.id!==rid);
  DB.users.forEach(u=>{if(u.rests)u.rests=u.rests.filter(x=>x!==rid);});
  save();renderAll();setStatus('Ristorante eliminato');
}

// ─── MODALS: ATTIVITÀ ─────────────────────────────────────────────────────────
function openActModal(aid) {
  editAid=aid;
  const ex=aid?DB.activities.find(a=>a.id===aid):null;
  const initColor=ex?ex.color:ACT_COLORS[0];
  const swatches=ACT_COLORS.map(c=>`<div class="color-swatch${c===initColor?' selected':''}" style="background:${c};border-color:${c===initColor?'#fff':'transparent'}" onclick="selectActColor('${c}')" id="sw${c.replace('#','')}"></div>`).join('');
  showModal(`
    <div class="modal-title">${ICON.tag} ${aid?'Modifica attività':'Nuova attività'}</div>
    <div class="frow"><label>Nome attività</label><input type="text" id="aName" value="${ex?ex.name:''}" placeholder="es. Audit cassa" oninput="updateActPreview()"></div>
    <div class="frow"><label>Colore etichetta</label>
      <input type="hidden" id="aColor" value="${initColor}">
      <div class="color-swatches">${swatches}</div>
      <div class="act-preview" id="actPreview" style="background:${initColor}20;color:${initColor};border:1px solid ${initColor}40">${ex?ex.name:'Anteprima etichetta'}</div>
    </div>
    <div class="mact">
      <button class="btn-secondary" onclick="closeModal()">Annulla</button>
      <button class="btn-primary" onclick="saveAct()">Salva</button>
    </div>`);
}
function selectActColor(c) {
  document.getElementById('aColor').value=c;
  document.querySelectorAll('.color-swatch').forEach(s=>{ s.classList.remove('selected'); s.style.borderColor='transparent'; });
  const sw=document.getElementById('sw'+c.replace('#',''));
  if(sw){sw.classList.add('selected');sw.style.borderColor='#fff';}
  updateActPreview();
}
function updateActPreview() {
  const c=document.getElementById('aColor')?.value;
  const n=document.getElementById('aName')?.value;
  const p=document.getElementById('actPreview');
  if(p&&c){p.textContent=n||'Anteprima etichetta';p.style.background=c+'20';p.style.color=c;p.style.borderColor=c+'40';}
}
function saveAct() {
  const name=document.getElementById('aName').value.trim();
  const color=document.getElementById('aColor').value;
  if(!name){setStatus("Inserisci il nome dell'attività");return;}
  if(editAid){const a=DB.activities.find(x=>x.id===editAid);if(a){a.name=name;a.color=color;}}
  else DB.activities.push({id:'a'+Date.now(),name,color});
  closeModal();save();setStatus('Attività salvata: '+name);renderAll();
}
function delAct(aid) {
  if(!confirm('Eliminare questa attività?'))return;
  DB.activities=DB.activities.filter(a=>a.id!==aid);save();renderAll();setStatus('Attività eliminata');
}

// ─── MODALS: MNG ─────────────────────────────────────────────────────────────
function openMNGModal(mid) {
  editMid=mid;
  const ex=mid?DB.mngAnag[mid]:null;
  showModal(`
    <div class="modal-title">${ICON.users} ${mid?'Modifica MNG':'Nuovo MNG'}</div>
    <div class="frow"><label>Nome e Cognome</label><input type="text" id="mNome" value="${ex?ex.nome:''}" placeholder="Mario Rossi"></div>
    <div class="frow"><label>Telefono</label><input type="text" id="mTel" value="${ex?ex.tel:''}" placeholder="+39 333 1234567"></div>
    <div class="mact">
      <button class="btn-secondary" onclick="closeModal()">Annulla</button>
      <button class="btn-primary" onclick="saveMNG()">Salva</button>
    </div>`);
}
function saveMNG() {
  const m=me();
  const nome=document.getElementById('mNome').value.trim();
  const tel=document.getElementById('mTel').value.trim();
  if(!nome){setStatus('Inserisci nome e cognome');return;}
  const id=editMid||('mng_'+Date.now());
  DB.mngAnag[id]={nome,tel,dir:m.id};
  closeModal();save();setStatus('MNG salvato: '+nome);renderAll();
}
function delMNG(id) {
  if(!confirm('Eliminare questo MNG?'))return;
  delete DB.mngAnag[id];save();renderAll();setStatus('MNG eliminato');
}

// ─── NAV ─────────────────────────────────────────────────────────────────────
function prevM(){if(ST.month===0){ST.month=11;ST.year--;}else ST.month--;renderAll();}
function nextM(){if(ST.month===11){ST.month=0;ST.year++;}else ST.month++;renderAll();}
function goToday(){const t=new Date();ST.month=t.getMonth();ST.year=t.getFullYear();renderAll();}

// ─── BOOTSTRAP ───────────────────────────────────────────────────────────────
function buildUserSelect() {
  const sel=document.getElementById('userSel');
  sel.innerHTML='';
  ['ufficio','supervisore','direttore'].forEach(lv=>{
    const us=DB.users.filter(u=>u.level===lv);
    if(!us.length)return;
    const g=document.createElement('optgroup');g.label=LN[lv];
    us.forEach(u=>{
      const o=document.createElement('option');o.value=u.id;o.textContent=u.name;
      if(u.id===ST.uid)o.selected=true;
      g.appendChild(o);
    });
    sel.appendChild(g);
  });
}

async function init() {
  // 1. Carica dati locali subito (per risposta istantanea)
  load();
  DB.users.forEach(u => { if (u.pin === undefined || u.pin === null) u.pin = ''; });

  // 2. Prova a scaricare da Supabase (se configurato)
  if (SUPABASE_ENABLED) {
    setSyncStatus('syncing', 'Connessione...');
    await syncFromSupabase();
    DB.users.forEach(u => { if (u.pin === undefined || u.pin === null) u.pin = ''; });
    startPolling();
  } else {
    setSyncStatus('local', '💾 Modalità locale — configura Supabase per la sync');
    setStatus('TurniApp pronto — modalità locale');
  }

  // 3. Controlla credenziali salvate
  try {
    const cred = JSON.parse(localStorage.getItem('turniapp_cred') || 'null');
    if (cred && cred.uid && cred.pin) {
      const u = DB.users.find(x => x.id === cred.uid);
      if (u && u.pin === cred.pin) {
        buildLoginSelect();
        doLogin(cred.uid);
        return;
      }
    }
  } catch(e) {}

  // 4. Mostra login
  buildLoginSelect();
  document.getElementById('loginScreen').classList.add('active');
}

init();
</script>
</body>
</html>
