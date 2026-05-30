<!DOCTYPE html>
<html lang="vi">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Bé Măng Thức Giấc — NhiLe Team</title>
<link href="https://fonts.googleapis.com/css2?family=Be+Vietnam+Pro:wght@400;500;600;700&family=Playfair+Display:ital,wght@0,700;1,700&family=Dancing+Script:wght@500;700&display=swap" rel="stylesheet">
<style>
*{box-sizing:border-box;margin:0;padding:0}
:root{
  --g:#C9973A;--gl:#F0C870;--br:#3D2008;--cr:#FFFFFF;
  --rd:#C0392B;--gn:#1E6B2E;--dk:#1A0E06;--mt:#6B4E2A;
  --bg-dark:#160C04;--bg-mid:#231207;
  --text-primary:#1A0E06;
  --text-secondary:#5C3D1E;
  --text-muted:#8B6540;
  --border-light:#EDE0CC;
  --border-gold:#D4A43E;
  --surface:#FFFCF7;
  --surface-warm:#FFF8EE;
}
html,body{height:100%;font-family:'Be Vietnam Pro',sans-serif;color:var(--text-primary);background:#160C04;font-size:15px;-webkit-font-smoothing:antialiased}

/* ── LAYOUT ── */
.shell{display:grid;grid-template-columns:400px 1fr;min-height:100vh}
.left{background:#141414;position:sticky;top:0;height:100vh;overflow:hidden;position:relative}
.right{background:url('01_deskop_background_sang.png') center/cover no-repeat,#FBF5EC;display:flex;flex-direction:column;min-height:100vh;overflow-y:auto}

/* ── LEFT PANEL ── */
.parallax-layer{position:absolute;top:-5%;left:-5%;width:110%;height:110%;pointer-events:none;background-size:cover;background-position:center;transition:transform .1s cubic-bezier(.2,.8,.2,1);will-change:transform}
.layer-2{background-image:url('01_deskop_layout2.png');opacity:.5}
.layer-aura{display:flex;align-items:center;justify-content:center}
.aura-glow{width:380px;height:380px;border-radius:50%;background:radial-gradient(circle,rgba(201,151,58,.25) 0%,rgba(201,151,58,0) 65%);animation:aura-pulse 3s infinite alternate}
@keyframes aura-pulse{0%{transform:scale(.9);opacity:.6}100%{transform:scale(1.1);opacity:1}}
.layer-4{display:flex;align-items:flex-start;justify-content:center;padding-top:160px}
.char-float{animation:char-float 4s infinite ease-in-out}
.char-float img{width:260px;height:auto;object-fit:contain;filter:drop-shadow(0 15px 30px rgba(0,0,0,.5))}
@keyframes char-float{0%,100%{transform:translateY(-12px)}50%{transform:translateY(12px)}}
.left-content{position:relative;z-index:10;height:100%;display:flex;flex-direction:column;justify-content:flex-start;padding:280px 40px 48px;pointer-events:none}
.left-art{pointer-events:auto;display:flex;flex-direction:column;align-items:center;text-align:center;gap:24px;padding-bottom:20px}
.brand{font-family:'Playfair Display',serif;color:#F0C870;font-size:26px;letter-spacing:.5px;text-shadow:0 2px 10px rgba(0,0,0,.6)}

/* vertical stepper in left panel */
.left-progress{width:100%;max-width:260px;margin-top:16px}
.vstepper{display:flex;flex-direction:column;gap:0}
.vstep{display:flex;align-items:flex-start;gap:12px;position:relative;padding-bottom:18px}
.vstep:last-child{padding-bottom:0}
.vstep:not(:last-child)::after{
  content:'';position:absolute;left:13px;top:28px;bottom:0;width:1.5px;
  background:rgba(201,151,58,.18);
}
.vstep.done::after{background:rgba(201,151,58,.45)}
.vs-icon{width:28px;height:28px;border-radius:50%;flex-shrink:0;margin-top:1px;
  display:flex;align-items:center;justify-content:center;font-size:11px;font-weight:700;
  transition:all .4s ease}
.vstep.done .vs-icon{background:var(--g);color:#fff;box-shadow:0 0 10px rgba(201,151,58,.35)}
.vstep.cur .vs-icon{background:#F0C870;color:#3D2008;box-shadow:0 0 14px rgba(240,200,112,.5)}
.vstep.todo .vs-icon{background:rgba(255,255,255,.06);color:#4A3020;border:1.5px solid rgba(201,151,58,.2)}
.vs-label{font-size:12.5px;line-height:1.4;padding-top:5px;transition:color .3s}
.vstep.done .vs-label{color:#8A6A40}
.vstep.cur .vs-label{color:#F0C870;font-weight:600}
.vstep.todo .vs-label{color:#3A2510}

/* HR companion chip */
.hr-chip{background:rgba(201,151,58,.12);border:1px solid rgba(201,151,58,.3);
  border-radius:40px;padding:8px 16px 8px 10px;display:flex;align-items:center;gap:10px;
  margin-top:8px}
.hr-chip-av{width:34px;height:34px;border-radius:50%;background:linear-gradient(135deg,#E8B86D,#A07428);
  display:flex;align-items:center;justify-content:center;font-size:16px;flex-shrink:0}
.hr-chip-txt{text-align:left}
.hr-chip-name{font-size:12px;font-weight:700;color:var(--gl)}
.hr-chip-role{font-size:10px;color:#7A5A3A}

/* ── RIGHT PANEL — screens ── */
.screen{display:none;flex-direction:column;flex:1;animation:fi .3s ease;align-items:stretch;background:transparent}
.screen.active{display:flex}
@keyframes fi{from{opacity:0;transform:translateX(10px)}to{opacity:1;transform:translateX(0)}}

/* content area */
.content{flex:1;padding:56px 64px;display:flex;flex-direction:column;justify-content:center;max-width:760px;width:100%;align-self:center}
.foot{padding:24px 64px 40px;max-width:760px;width:100%;align-self:center}
.foot-col{display:flex;flex-direction:column;gap:10px}

/* typography */
.h1{font-family:'Playfair Display',serif;font-size:34px;color:var(--br);line-height:1.25;margin-bottom:12px;letter-spacing:-.3px}
.h2{font-family:'Playfair Display',serif;font-size:26px;color:var(--br);margin-bottom:10px;letter-spacing:-.2px}
.sub{font-size:14px;color:var(--text-secondary);line-height:1.7;margin-bottom:20px}

/* s1 splash override for light bg */
#s1 .content .h1{color:var(--br)}
#s1 .content .h1 em{color:var(--g)}

/* ── BUTTONS ── */
.btn{width:100%;max-width:380px;padding:16px 24px;border:none;border-radius:12px;
  background:linear-gradient(135deg,#D4A43E,#8A6020);color:white;
  font-family:'Be Vietnam Pro',sans-serif;font-size:15px;font-weight:700;
  cursor:pointer;transition:opacity .15s,transform .1s;text-align:center}
.btn:hover{opacity:.92}
.btn:active{transform:scale(.98)}
.btn:disabled{opacity:.3;pointer-events:none}
.btn-ghost{width:100%;max-width:380px;padding:14px 24px;border:2px solid var(--br);border-radius:12px;
  background:transparent;color:var(--br);font-family:'Be Vietnam Pro',sans-serif;
  font-size:14px;font-weight:600;cursor:pointer;transition:.15s}
.btn-ghost:hover{background:var(--br);color:white}

/* ── INPUTS ── */
.inp{width:100%;max-width:380px;padding:14px 18px;border:2px solid #E0D0B0;border-radius:10px;
  background:white;font-family:'Be Vietnam Pro',sans-serif;font-size:16px;
  color:var(--text-primary);outline:none;transition:border-color .2s}
.inp:focus{border-color:var(--g)}
.inp.ok{border-color:var(--gn);background:#F8FFF8}
.inp::placeholder{color:#C4A880}

/* ── CARDS ── */
.card{background:white;border:1px solid var(--border-light);border-radius:16px;padding:24px;
  box-shadow:0 2px 20px rgba(0,0,0,.06)}
.card-gold{background:white;border:2px solid var(--border-gold);border-radius:16px;padding:24px;
  box-shadow:0 4px 24px rgba(201,151,58,.18)}

/* ── S1 SPLASH (right panel override) ── */
#s1 .content{justify-content:center;align-items:flex-start}
.splash-hint{display:inline-block;color:var(--text-muted);font-size:13px;padding:8px 18px;
  border:1px solid #E0D0B0;border-radius:20px;cursor:pointer;transition:.2s;margin-top:8px}
.splash-hint:hover{border-color:var(--g);color:var(--br)}

/* ── S2 NAME ── */
.name-area{display:flex;flex-direction:column;gap:14px;max-width:400px}
.bubble{background:var(--bg-mid);border:none;border-radius:16px 16px 16px 4px;
  padding:12px 18px;font-size:15px;font-weight:500;color:#C4A880;
  display:inline-block;margin-bottom:12px}

/* ── S3 WELCOME ── */
#s3{background:transparent}
#s3 .content{justify-content:flex-start;align-items:center;padding:20px 60px 40px;max-width:none;gap:24px}
.letter-wrap{width:100%;max-width:900px;position:relative;display:flex;align-items:center;justify-content:center;margin-bottom:0}
.letter-bg{width:auto;height:80vh;display:block;filter:drop-shadow(0 20px 50px rgba(0,0,0,0.5))}
.letter-text-overlay{position:absolute;top:0;left:0;right:0;bottom:0;padding:15% 33% 20% 33%;display:flex;flex-direction:column;justify-content:center;align-items:center;text-align:center;font-family:'Dancing Script',cursive}
.letter-title{font-size:22px;margin-bottom:12px;line-height:1.2;color:#3D2008;font-weight:700}
.letter-body{font-size:15px;line-height:1.6;margin-bottom:12px;color:#3D2008;font-weight:500;text-align:justify}
.letter-sign{font-size:20px;margin-top:10px;font-weight:700;color:#3D2008;text-align:right;margin-left:auto;width:fit-content}
.noted-box{background:rgba(255,248,238,.92);backdrop-filter:blur(8px);border:1.5px solid var(--border-gold);border-radius:14px;padding:22px 32px;margin-top:-40px;position:relative;z-index:10;max-width:540px;width:100%;box-shadow:0 8px 32px rgba(0,0,0,.25);display:flex;flex-direction:column;align-items:center;text-align:center}

/* ── S4 STEPS ── */
.steps-grid{display:grid;grid-template-columns:1fr 1fr;gap:12px;margin-bottom:24px}
.step-card{background:white;border:1px solid var(--border-light);border-radius:14px;padding:16px 18px;display:flex;gap:14px;align-items:flex-start;transition:box-shadow .2s}
.step-card:hover{box-shadow:0 4px 16px rgba(0,0,0,.07)}
.step-card.active-c{border-color:var(--border-gold);background:var(--surface-warm)}
.step-card.dim{opacity:.45}
.snum{width:32px;height:32px;border-radius:50%;background:var(--g);color:white;
  font-weight:700;font-size:13px;display:flex;align-items:center;justify-content:center;flex-shrink:0}
.snum.gray{background:#D0C0A0}

/* ── S5 MAP ── */
#s5 .content{padding:40px 64px;max-width:none;align-self:stretch}
.map-bar{display:flex;align-items:center;justify-content:space-between;margin-bottom:24px}
.map-grid{display:grid;grid-template-columns:repeat(4,minmax(0,1fr));gap:12px;margin-bottom:20px;background:white}
.mroom{background:white;border:1.5px solid #E8DDD0;border-radius:14px;padding:20px 14px;
  text-align:center;cursor:pointer;transition:transform .2s,border-color .2s,box-shadow .2s;position:relative}
.mroom:hover{transform:translateY(-4px);box-shadow:0 8px 24px rgba(0,0,0,.1);border-color:var(--g)}
.mroom.vis{border-color:var(--gn);background:#F0FFF4;pointer-events:none}
.mroom.vis::after{content:'✓';position:absolute;top:8px;right:10px;font-size:13px;color:var(--gn);font-weight:700}
.mroom.maxed{opacity:.35;pointer-events:none}
.mroom.hint{border-color:var(--g);animation:glow 1.6s ease-in-out infinite}
@keyframes glow{0%,100%{box-shadow:0 0 0 0 rgba(201,151,58,0)}50%{box-shadow:0 0 0 6px rgba(201,151,58,.2)}}
.remoji{font-size:32px;margin-bottom:6px;display:block}
.rlbl{font-size:13px;font-weight:700;color:var(--text-primary)}
.rsub{font-size:11px;color:var(--text-muted);margin-top:2px}
.map-note-bar{font-size:13px;color:var(--text-muted);margin-bottom:16px}

/* ── MODAL overlay ── */
.modal-bg{position:fixed;inset:0;background:rgba(44,26,14,.55);display:none;
  align-items:center;justify-content:center;z-index:200;padding:24px}
.modal-bg.show{display:flex}
.modal{background:white;border-radius:20px;padding:32px;max-width:500px;width:100%;
  box-shadow:0 24px 64px rgba(0,0,0,.25);animation:popin .25s ease}
@keyframes popin{from{transform:scale(.95);opacity:0}to{transform:scale(1);opacity:1}}
.modal-head{display:flex;align-items:flex-start;gap:16px;margin-bottom:20px}
.modal-close{margin-left:auto;background:none;border:none;font-size:24px;cursor:pointer;
  color:var(--text-muted);padding:0 4px;line-height:1;border-radius:6px}
.modal-close:hover{background:#F0E8D8}
.ibox{background:#FFFBF2;border:1px solid #E8D8B8;border-radius:10px;padding:14px 16px;
  font-size:13px;color:var(--text-primary);line-height:1.65;margin-bottom:10px}
.ibox strong{color:var(--text-muted);display:block;font-size:10px;text-transform:uppercase;letter-spacing:.8px;margin-bottom:5px;font-weight:700}
.mail-note{background:#F0FBF2;border:1px solid #A8D8B0;border-radius:10px;
  padding:12px 16px;font-size:13px;color:#1E6B2E;line-height:1.7;margin-bottom:16px}
.modal-btns{display:flex;flex-direction:column;gap:8px}
.modal-btns .btn,.modal-btns .btn-ghost{max-width:100%}

/* ── S6 CẢMM NHẬN ── */
#s6 .content{max-width:800px}
.sensing-grid{display:grid;grid-template-columns:1fr 1fr;gap:24px;margin-bottom:20px}
.timer-box{background:var(--surface-warm);border:1.5px solid var(--border-gold);border-radius:14px;padding:16px 20px;
  display:flex;align-items:center;gap:16px;margin-bottom:20px;max-width:440px}
.tnum{font-size:28px;font-weight:700;color:var(--br);min-width:60px;font-variant-numeric:tabular-nums}
.tnum.red{color:var(--rd)}
.q-lbl{font-size:14px;font-weight:600;color:var(--text-primary);margin-bottom:10px}
.opt{width:100%;padding:13px 16px;border:2px solid #E0D0B0;border-radius:11px;
  background:white;font-family:'Be Vietnam Pro',sans-serif;font-size:13px;color:var(--text-primary);
  cursor:pointer;text-align:left;transition:.15s;line-height:1.4;display:block;margin-bottom:7px}
.opt:last-child{margin-bottom:0}
.opt:hover{border-color:var(--g);background:#FFFBF2}
.opt.sel{border-color:var(--br);background:#FFF8EC;color:var(--br);font-weight:600}

/* ── S7 REWARD ── */
#s7 .content{align-items:center;text-align:center;max-width:none}
.rfloat{font-size:100px;animation:float 2s ease-in-out infinite;display:block;line-height:1}
@keyframes float{0%,100%{transform:translateY(0)}50%{transform:translateY(-10px)}}
.rbadge{background:var(--surface-warm);border:1.5px solid var(--border-gold);border-radius:14px;
  padding:16px 32px;display:inline-block;text-align:center}

/* ── S8 INVITE ── */
#s8 .content{justify-content:center}
.scroll-wrap{background:linear-gradient(180deg,#FDF4E0,#F5E5B8);border:2px solid var(--border-gold);
  border-radius:8px;padding:36px 40px;max-width:560px;width:100%;position:relative}
.scroll-wrap::before{content:'';display:block;height:16px;background:var(--g);
  position:absolute;top:0;left:0;right:0;border-radius:6px 6px 0 0}
.scroll-wrap::after{content:'';display:block;height:16px;background:var(--g);
  position:absolute;bottom:0;left:0;right:0;border-radius:0 0 6px 6px}
.scroll-in{padding:4px 0}
.invite-btns{display:flex;gap:12px;margin-top:4px;max-width:560px}
.invite-btns .btn,.invite-btns .btn-ghost{flex:1;max-width:none}

/* ── STHANKS ── */
#sthanks .content{align-items:flex-start}
.thanks-card{background:white;border:2px solid var(--g);border-radius:16px;padding:24px 28px;max-width:420px;margin-top:8px}

/* ── S9 CALENDAR ── */
#s9 .content{max-width:800px}
.cal-grid{display:grid;grid-template-columns:1fr 1fr;gap:32px;margin-bottom:24px}
.slbl{font-size:11px;font-weight:700;color:var(--text-muted);text-transform:uppercase;letter-spacing:.6px;margin-bottom:8px}
.days-grid{display:grid;grid-template-columns:repeat(3,minmax(0,1fr));gap:8px}
.cday{padding:12px 8px;border:2px solid #E0D0B0;border-radius:10px;background:white;
  font-family:'Be Vietnam Pro',sans-serif;font-size:12px;color:var(--text-primary);cursor:pointer;
  text-align:center;transition:.15s;font-weight:500}
.cday:hover{border-color:var(--g)}
.cday.sel{border-color:var(--br);background:#FFF8EC;color:var(--br);font-weight:700}
.times-grid{display:grid;grid-template-columns:repeat(2,minmax(0,1fr));gap:8px}
.ctime{padding:14px;border:1.5px solid var(--border-gold);border-radius:10px;background:white;
  font-family:'Be Vietnam Pro',sans-serif;font-size:15px;font-weight:700;color:var(--br);
  cursor:pointer;text-align:center;transition:.15s}
.ctime:hover{background:var(--g);color:white;border-color:var(--g)}
.ctime.sel{background:var(--g);color:white;border-color:var(--g)}
.confirm-chip{background:var(--surface-warm);border:1.5px solid var(--border-gold);border-radius:12px;padding:14px 18px;max-width:400px;display:none}

/* ── CULTURE CHAT UI ── */
.chat-wrap{display:flex;flex-direction:column;gap:12px;max-width:600px}
.chat-bot{display:flex;align-items:flex-end;gap:10px}
.chat-bot-av{width:32px;height:32px;border-radius:50%;background:linear-gradient(135deg,#E8B86D,#A07428);display:flex;align-items:center;justify-content:center;font-size:15px;flex-shrink:0}
.chat-bubble-bot{background:#F2F2F2;color:#1A1A1A;border-radius:18px 18px 18px 4px;padding:12px 16px;font-size:14px;line-height:1.6;max-width:420px}
.chat-user{display:flex;justify-content:flex-end}
.chat-bubble-user{background:#2D6A4F;color:#fff;border-radius:18px 18px 4px 18px;padding:12px 16px;font-size:14px;line-height:1.6;max-width:380px;word-break:break-word}
.chat-typing{display:flex;align-items:center;gap:5px;padding:10px 14px;background:#F2F2F2;border-radius:18px 18px 18px 4px;width:fit-content}
.chat-typing span{width:7px;height:7px;border-radius:50%;background:#999;display:inline-block;animation:typing-dot 1.2s infinite}
.chat-typing span:nth-child(2){animation-delay:.2s}
.chat-typing span:nth-child(3){animation-delay:.4s}
@keyframes typing-dot{0%,60%,100%{transform:translateY(0);opacity:.4}30%{transform:translateY(-5px);opacity:1}}

/* textarea for chat */
.chat-input-area{background:#fff;border:1.5px solid #E0D0B0;border-radius:14px;padding:14px 16px;max-width:600px;transition:border-color .2s}
.chat-input-area:focus-within{border-color:var(--g)}
.chat-input-area textarea{width:100%;border:none;outline:none;font-family:'Be Vietnam Pro',sans-serif;font-size:14px;color:var(--text-primary);resize:none;line-height:1.6;background:transparent}
.chat-send-row{display:flex;justify-content:flex-end;margin-top:10px}
.chat-send-btn{background:linear-gradient(135deg,#D4A43E,#8A6020);color:white;border:none;border-radius:10px;padding:10px 22px;font-family:'Be Vietnam Pro',sans-serif;font-size:14px;font-weight:700;cursor:pointer;transition:opacity .15s}
.chat-send-btn:disabled{opacity:.3;pointer-events:none}

/* next btn disabled until read */
.cv-next-btn{width:100%;max-width:380px;padding:16px 24px;border:none;border-radius:12px;background:linear-gradient(135deg,#D4A43E,#8A6020);color:white;font-family:'Be Vietnam Pro',sans-serif;font-size:15px;font-weight:700;cursor:pointer;transition:opacity .15s,transform .1s}
.cv-next-btn:disabled{opacity:.3;pointer-events:none;cursor:default}
.cv-next-btn:not(:disabled):hover{opacity:.92}
.cv-next-btn:not(:disabled):active{transform:scale(.98)}

/* completion inline */
.cv-complete{background:linear-gradient(135deg,#FFF8EE,#FFF3DC);border:2px solid var(--border-gold);border-radius:20px;padding:32px 36px;max-width:520px;text-align:center}
#s10 .content{align-items:center;text-align:center;max-width:none}
.score-box{background:var(--surface-warm);border:1.5px solid var(--border-gold);border-radius:16px;padding:16px 48px;margin:8px 0}
.badges{display:flex;gap:8px;justify-content:center;flex-wrap:wrap;max-width:500px}
.badge{background:var(--surface-warm);border:1px solid var(--border-light);
  border-radius:20px;padding:5px 12px;font-size:12px;color:var(--text-secondary)}

/* ── MAP ROADMAP ── */
#s5.active {
  background: url('01_deskop_background_basic.png') center/cover no-repeat !important;
  display: flex !important;
  align-items: center;
  justify-content: center;
}
#s5 {
  padding: 20px;
  position: relative;
  overflow: hidden;
}
.map-frame {
  position: relative;
  width: 95%;
  max-width: 1200px;
  aspect-ratio: 1920/1080;
  background: white;
  border-radius: 16px;
  box-shadow: 0 40px 100px rgba(0,0,0,0.4);
  border: 10px solid white;
  display: flex;
  align-items: center;
  justify-content: center;
}
.map-img-content {
  width: 100%;
  height: 100%;
  border-radius: 4px;
  object-fit: contain;
}
.hotspot {
  position: absolute;
  transform: translate(-50%, -50%);
  cursor: pointer;
  z-index: 10;
}
.team-tag {
  background: rgba(255, 255, 255, 0.98);
  color: var(--br);
  padding: 8px 18px;
  border-radius: 40px;
  font-size: 13px;
  font-weight: 700;
  white-space: nowrap;
  border: 2px solid var(--g);
  box-shadow: 0 6px 20px rgba(0,0,0,0.15);
  transition: all 0.25s ease;
}
.hotspot:hover .team-tag {
  transform: scale(1.1);
  background: var(--br);
  color: white;
  border-color: var(--br);
  box-shadow: 0 10px 30px rgba(0,0,0,0.3);
}
.hotspot.vis .team-tag {
  background: #E0FFE8;
  border-color: var(--gn);
  color: var(--gn);
}
.hotspot.vis .team-tag::after {
  content: ' ✓';
}
.hotspot.maxed { opacity: 0.3; pointer-events: none; }

.divider{height:1px;background:linear-gradient(90deg,transparent,#E0D0B0,transparent);margin:20px 0}
</style>
</head>
<body>

<!-- MODAL -->
<div class="modal-bg" id="overlay" onclick="closeOvr(event)">
  <div class="modal" onclick="event.stopPropagation()">
    <div class="modal-head">
      <div style="font-size:48px;line-height:1" id="rdIcon">🌳</div>
      <div style="flex:1">
        <div style="font-family:'Playfair Display',serif;font-size:20px;color:var(--br)" id="rdName">HR Team</div>
        <div style="font-size:13px;color:var(--text-muted);margin-top:3px" id="rdSub">—</div>
      </div>
      <button class="modal-close" id="rdClose" onclick="closeOvrDirect()">✕</button>
    </div>
    <div class="ibox" id="rdAboutBox"><strong>VỀ TEAM NÀY</strong><span id="rdAbout">—</span></div>
    <div class="ibox" id="rdDateBox"><strong>📅 ZOOM TOUR SẮP TỚI</strong><span id="rdDate">—</span></div>
    <div class="mail-note" id="rdMailNote">✉️ Sau khi đăng ký, link zoom sẽ về email của bạn. <strong>Minh Thư</strong> sẽ cùng bạn trong buổi tham quan này.</div>
    <div class="modal-btns" id="rdBtns">
      <button class="btn" onclick="joinRoom()">Minh đăng ký tham quan này</button>
      <div style="text-align:center;margin-top:6px"><a onclick="closeOvrDirect()" style="font-size:14px;color:var(--text-muted);text-decoration:underline;cursor:pointer">Xem team khác trước</a></div>
    </div>
    <div class="modal-btns" id="guideBtns" style="display:none">
      <button class="btn" onclick="closeOvrDirect()">Hiểu rồi, bắt đầu thôi!</button>
    </div>
  </div>
</div>

<div class="shell">

<!-- ═══════ LEFT PANEL ═══════ -->
<div class="left" id="parallax-container">
  <div class="parallax-layer layer-2" id="px-layer-2"></div>
  <div class="parallax-layer layer-aura" id="px-layer-aura"><div class="aura-glow"></div></div>
  <div class="parallax-layer layer-4" id="px-layer-4"><div class="char-float"><img src="00_bemang_goc.png" alt="Bé Măng"></div></div>
  <div class="left-content">
    <div class="left-art">
      <div>
        <div class="brand">Bé Măng Thức Giấc</div>
      </div>
      <div class="left-progress" id="leftProgress" style="display:none">
        <div class="vstepper" id="vstepper">
          <div class="vstep todo" id="vsS1">
            <div class="vs-icon" id="vsI1">1</div>
            <div class="vs-label">Chào mừng</div>
          </div>
          <div class="vstep todo" id="vsS2">
            <div class="vs-icon" id="vsI2">2</div>
            <div class="vs-label">Khám phá team</div>
          </div>
          <div class="vstep todo" id="vsS3">
            <div class="vs-icon" id="vsI3">3</div>
            <div class="vs-label">Quyết định của bạn</div>
          </div>
          <div class="vstep todo" id="vsS4">
            <div class="vs-icon" id="vsI4">4</div>
            <div class="vs-label">Hiểu về văn hóa NhiLe Team</div>
          </div>
          <div class="vstep todo" id="vsS5">
            <div class="vs-icon" id="vsI5">5</div>
            <div class="vs-label">Đặt lịch phỏng vấn</div>
          </div>
        </div>
      </div>
    <div class="hr-chip" id="hrChip" style="display:none">
      <div class="hr-chip-av">👩</div>
      <div class="hr-chip-txt">
        <div class="hr-chip-name">Minh Thư</div>
        <div class="hr-chip-role">Người đồng hành của bạn</div>
      </div>
    </div>
    </div>
  </div>
</div>

<!-- ═══════ RIGHT PANEL ═══════ -->
<div class="right">

<!-- Back button — fixed top left, hidden on s1 -->
<div id="backBar" style="display:none;position:sticky;top:0;z-index:50;padding:12px 24px;background:rgba(251,245,236,.92);backdrop-filter:blur(8px);border-bottom:1px solid #EDE0CC">
  <button onclick="goBack()" style="background:none;border:none;cursor:pointer;display:flex;align-items:center;gap:8px;color:var(--text-muted);font-family:'Be Vietnam Pro',sans-serif;font-size:14px;font-weight:500;padding:4px 0;transition:color .15s" onmouseover="this.style.color='var(--br)'" onmouseout="this.style.color='var(--text-muted)'">
    <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><polyline points="15 18 9 12 15 6"/></svg>
    Quay lại
  </button>
</div>

<!-- S1 SPLASH -->
<div class="screen active" id="s1">
  <div class="content" style="justify-content:center">
    <div style="font-size:12px;color:#B8A080;letter-spacing:2.5px;text-transform:uppercase;margin-bottom:20px;font-weight:600">NhiLe Team</div>
    <div class="h1" style="font-size:40px;margin-bottom:16px">Bạn đã tới rồi —<br>Bé Măng chờ<br><em style="color:var(--g)">lâu lắm rồi đó.</em></div>
    <div class="sub" style="max-width:380px">NhiLe Team là nơi bạn vừa học, vừa làm, vừa lớn lên cùng hàng trăm người cùng chí hướng. Hành trình này sẽ giúp bạn hiểu mình có phù hợp không — trước khi quyết định bất cứ điều gì.</div>
    <button class="btn" onclick="go('s2')" style="margin-top:8px">Mình bắt đầu thôi →</button>
  </div>
</div>

<!-- S2 NAME -->
<div class="screen" id="s2">
  <div class="content">
    <div class="bubble">Bạn... là ai vậy?</div>
    <div class="h1" style="color:var(--gl)">Cho Bé Măng biết<br>tên của bạn nhé!</div>
    <div class="name-area">
      <input class="inp" id="nameInp" placeholder="Tên của bạn..." maxlength="40"
        oninput="onName()" onkeydown="if(event.key==='Enter'&&S.name&&S.returning!==null)go('s3')"
        style="margin-bottom:20px">
      
      <div id="returningQ" style="display:none;animation:fi .4s ease">
        <div style="font-size:14px;color:var(--text-muted);margin-bottom:12px">Bạn đã từng tham gia NhiLe Team chưa?</div>
        <div style="display:flex;flex-direction:column;gap:8px">
          <button class="opt" id="opt-new" onclick="setReturning(false)">🌱 Lần đầu mình tham gia NLT</button>
          <button class="opt" id="opt-old" onclick="setReturning(true)">🌿 Mình đã từng tham gia team rồi</button>
        </div>
      </div>
    </div>
  </div>
  <div class="foot"><button class="btn" id="nameBtn" onclick="go('s3')" disabled>Tiếp tục →</button></div>
</div>

<!-- S3 WELCOME -->
<div class="screen" id="s3">
  <div class="content">
    <div class="letter-wrap">
      <img src="03_deskop_thu.png" class="letter-bg" alt="Letter Background">
      <div class="letter-text-overlay">
        <div class="letter-title">Chào <span id="nameShow">bạn</span>,<br>mình đã chờ bạn!</div>
        <div class="letter-body" id="letterBody">
          Cảm ơn bạn đã dành thời gian tìm hiểu về NhiLe Team.<br><br>Chúng mình tin rằng đây chính là khởi đầu của một hành trình ý nghĩa mà bạn dành cho bản thân.<br><br>Người sắp đồng hành cùng bạn là <strong>Minh Thư</strong> — bạn ấy luôn ở đây nếu bạn có bất kỳ câu hỏi nào.<br><br>Hãy giữ vững niềm tin vào bản thân và tiếp tục nhé!
        </div>
        <div class="letter-sign">
          Yêu thương,<br>
          NhiLe Team & Bé Măng
        </div>
      </div>
    </div>
    <div class="noted-box">
      <div style="font-size:13px;color:var(--text-muted);margin-bottom:10px">Nhập <strong style="color:var(--br)">"noted"</strong> để xác nhận đã đọc và tiếp tục hành trình</div>
      <div style="display:flex;gap:12px;align-items:center">
        <input class="inp" id="notedInp" placeholder="noted..." style="max-width:220px"
          oninput="onNoted(this)"
          onkeydown="if(event.key==='Enter'&&document.getElementById('notedInp').value.trim().toLowerCase()==='noted')go('s5')"
          autocomplete="off">
        <button class="btn" id="notedBtn" onclick="go('s5')" disabled style="max-width:200px;padding:14px">Bắt đầu hành trình →</button>
      </div>
    </div>
  </div>
</div>

<!-- S4 REMOVED -->

<!-- S5 MAP -->
<div class="screen" id="s5">
  <div class="map-frame">
    <div style="position: absolute; top: -70px; right: 0; display: flex; align-items: center; gap: 15px; pointer-events: auto;">
       <div style="background: white; padding: 8px 20px; border-radius: 50px; box-shadow: 0 5px 15px rgba(0,0,0,0.1); border: 1px solid #E0D0B0; font-weight: 700; color: var(--br)">
         🎋 <span id="vcnt">0</span>/3
       </div>
    </div>

    <img src="04_roadmap_team.png" class="map-img-content">
    
    <!-- Admin: Đờn ca tài tử -->
    <div class="hotspot" id="r-admin" style="top: 22%; left: 19%;" onclick="openRoom('admin')">
      <div class="team-tag">Admin</div>
    </div>
    
    <!-- Design: Làng tranh Đông Hồ -->
    <div class="hotspot" id="r-design" style="top: 18%; left: 50%;" onclick="openRoom('design')">
      <div class="team-tag">Design</div>
    </div>
    
    <!-- Academy: Tàng Thư lâu -->
    <div class="hotspot" id="r-academy" style="top: 24%; left: 81%;" onclick="openRoom('academy')">
      <div class="team-tag">Academy</div>
    </div>
    
    <!-- N-Edu: Văn Miếu Xích Đằng -->
    <div class="hotspot" id="r-nedu" style="top: 48%; left: 39%;" onclick="openRoom('nedu')">
      <div class="team-tag">N-Edu</div>
    </div>
    
    <!-- Editor: Nhã nhạc Cung đình Huế -->
    <div class="hotspot" id="r-editor" style="top: 78%; left: 16%;" onclick="openRoom('editor')">
      <div class="team-tag">Editor</div>
    </div>
    
    <!-- HR: Bưu điện Trung tâm SG -->
    <div class="hotspot" id="r-hr" style="top: 80%; left: 42%;" onclick="openRoom('hr')">
      <div class="team-tag">HR</div>
    </div>
    
    <!-- Social: Phố cổ Hội An -->
    <div class="hotspot" id="r-social" style="top: 80%; left: 65%;" onclick="openRoom('social')">
      <div class="team-tag">Social Event</div>
    </div>
    
    <!-- IT Team: Landmark 81 -->
    <div class="hotspot" id="r-it" style="top: 74%; left: 90%;" onclick="openRoom('it')">
      <div class="team-tag">IT Team</div>
    </div>
  </div>

  <div class="foot" id="mapCta" style="display:none; position: absolute; bottom: 30px; left: 50%; transform: translateX(-50%); z-index: 25; width: auto;">
    <button class="btn" style="padding: 16px 40px; box-shadow: 0 15px 40px rgba(138, 96, 32, 0.4)" onclick="openInvite()">Tiếp tục nhận thư →</button>
  </div>
</div>

<!-- S6 CẢM NHẬN -->
<div class="screen" id="s6">
  <div class="content" style="padding-top:48px;justify-content:flex-start">
    <div style="display:flex;align-items:center;gap:12px;margin-bottom:24px">
      <button onclick="go('s5')" style="background:none;border:1.5px solid #E0D0B0;border-radius:8px;cursor:pointer;font-size:20px;color:var(--br);padding:6px 12px;font-family:'Be Vietnam Pro',sans-serif">← Bản đồ</button>
      <div>
        <div style="font-size:12px;color:var(--text-muted)">Chia sẻ cảm nhận · <span id="sRoomName">HR Team</span></div>
        <div style="font-size:15px;font-weight:700;color:var(--br)">Sau buổi tham quan</div>
      </div>
    </div>
    <div style="display:flex;align-items:center;gap:20px;margin-bottom:20px">
      <div style="display:flex;align-items:center;gap:14px;background:white;border:1.5px solid var(--g);border-radius:14px;padding:14px 20px">
        <div style="font-size:40px" id="sIcon">🌳</div>
        <div>
          <div style="font-weight:700;font-size:16px;color:var(--br)" id="sName">HR Team</div>
          <div style="font-size:12px;color:var(--text-muted);margin-top:2px" id="sDesc">—</div>
        </div>
      </div>
      <div class="timer-box" style="margin:0;flex:1;max-width:280px">
        <div>
          <div class="tnum" id="tnum">15:00</div>
          <div style="font-size:10px;color:var(--text-muted)">còn lại</div>
        </div>
        <div style="font-size:12px;color:var(--text-muted);line-height:1.5">Điền trước khi hết giờ để kết quả được ghi nhận nhé.</div>
      </div>
    </div>
    <div class="sensing-grid">
      <div>
        <div class="q-lbl">1. Bạn cảm nhận team này thế nào?</div>
        <div id="opts1">
          <button class="opt" onclick="pick(this,1)">Đây là nơi tôi muốn đóng góp</button>
          <button class="opt" onclick="pick(this,1)">Cần thêm thông tin để quyết định</button>
          <button class="opt" onclick="pick(this,1)">Team này chưa phù hợp với tôi</button>
        </div>
      </div>
      <div>
        <div class="q-lbl">2. Trải nghiệm zoom vừa rồi như thế nào?</div>
        <div id="opts2">
          <button class="opt" onclick="pick(this,2)">Rõ ràng và ấn tượng</button>
          <button class="opt" onclick="pick(this,2)">Ổn, còn một số câu hỏi</button>
          <button class="opt" onclick="pick(this,2)">Chưa đủ thông tin</button>
        </div>
      </div>
    </div>
  </div>
  <div class="foot"><button class="btn" id="sBtn" onclick="submitS()" disabled>Nộp & nhận phần thưởng 🎁</button></div>
</div>

<!-- S7 REWARD -->
<div class="screen" id="s7">
  <div class="content">
    <span class="rfloat">🎁</span>
    <div style="font-family:'Playfair Display',serif;color:var(--br);font-size:28px;margin:12px 0 6px">Bé Măng nhận Bao Thư Đỏ!</div>
    <div style="color:var(--text-muted);font-size:13px;margin-bottom:20px">Magic Moment ✨</div>
    <div class="rbadge">
      <div style="color:var(--text-primary);font-size:15px">Phụ kiện mới: <strong id="rItem">Nón Lá Vàng</strong></div>
      <div style="font-size:12px;color:var(--text-muted);margin-top:4px">Từ team <span id="rTeam">HR</span></div>
    </div>
    <div style="color:var(--text-muted);font-size:13px;margin-top:20px;margin-bottom:16px">Bạn muốn xem tiếp hay nhận thư?</div>
    <div style="display:flex;flex-direction:column;gap:10px;max-width:380px;align-items:center">
      <button class="btn" id="continueBtn" onclick="go('s5')" style="max-width:100%">Xem team tiếp theo</button>
      <a onclick="openInvite()" style="font-size:14px;color:var(--text-muted);text-decoration:underline;cursor:pointer;margin-top:4px">Nhận thư & quyết định</a>
    </div>
  </div>
</div>

<!-- S8 INVITE LETTER -->
<div class="screen" id="s8">
  <div class="content" style="justify-content:center;align-items:flex-start">
    <div style="font-size:11px;color:var(--text-muted);letter-spacing:2px;text-transform:uppercase;margin-bottom:16px;font-weight:600">Thư Đặc Biệt</div>
    <div class="scroll-wrap">
      <div class="scroll-in">
        <div style="font-family:'Playfair Display',serif;font-size:17px;color:#2C1200;margin-bottom:14px">Gửi <span id="iName">bạn</span> thân mến,</div>
        <div style="font-size:13px;line-height:1.85;color:var(--text-primary);margin-bottom:14px" id="inviteBody">—</div>
        <div style="font-size:12px;color:var(--text-muted);font-style:italic">Trân trọng, Nhi Lê & NhiLe Team</div>
      </div>
    </div>
    <div class="invite-btns" id="inviteBtns" style="margin-top:20px;max-width:480px"></div>
  </div>
</div>

<!-- S-THANKS -->
<div class="screen" id="sthanks">
  <div class="content">
    <div style="font-size:64px;margin-bottom:16px">🙏</div>
    <div class="h1">Cảm ơn bạn!</div>
    <div class="sub" style="max-width:380px">Bạn đã dành thời gian tham quan và tìm hiểu về NhiLe Team. Đây là một hành trình đáng nhớ với Bé Măng.<br><br>Khi bạn đã sẵn sàng, NhiLe Team luôn ở đây chờ bạn.</div>
    <div class="thanks-card">
      <div style="font-size:14px;color:var(--text-primary);line-height:1.7">Liên hệ tại <strong><a href="https://nlt.nhi.sg" style="color:var(--g)">nlt.nhi.sg</a></strong> 🌿</div>
    </div>
  </div>
</div>

<!-- S9 CALENDAR -->
<div class="screen" id="s9">
  <div class="content" style="justify-content:flex-start;padding-top:48px">
    <div class="h2" style="margin-bottom:6px">Đặt lịch gặp gỡ</div>
    <div class="sub">Chọn thời gian phù hợp với bạn — Minh Thư xác nhận qua email trong 2 tiếng.</div>
    <div class="cal-grid">
      <div>
        <div class="slbl">Chọn ngày</div>
        <div class="days-grid">
          <button class="cday" onclick="pDay(this,'T2 15/7')">Thứ Hai 15/7</button>
          <button class="cday" onclick="pDay(this,'T3 16/7')">Thứ Ba 16/7</button>
          <button class="cday" onclick="pDay(this,'T4 17/7')">Thứ Tư 17/7</button>
          <button class="cday" onclick="pDay(this,'T5 18/7')">Thứ Năm 18/7</button>
          <button class="cday" onclick="pDay(this,'T6 19/7')">Thứ Sáu 19/7</button>
          <button class="cday" onclick="pDay(this,'T7 20/7')">Thứ Bảy 20/7</button>
        </div>
      </div>
      <div>
        <div class="slbl">Chọn giờ</div>
        <div class="times-grid">
          <button class="ctime" onclick="pTime(this,'10:00')">10:00 AM</button>
          <button class="ctime" onclick="pTime(this,'14:00')">14:00 PM</button>
          <button class="ctime" onclick="pTime(this,'16:00')">16:00 PM</button>
          <button class="ctime" onclick="pTime(this,'18:00')">18:00 PM</button>
        </div>
      </div>
    </div>
    <div class="confirm-chip" id="cchip">
      <div style="font-size:14px;color:var(--br)">📅 Lịch của bạn: <strong id="csel">—</strong></div>
      <div style="font-size:12px;color:var(--gn);margin-top:5px">✉️ Minh Thư xác nhận qua email trong 2 tiếng</div>
    </div>
  </div>
  <div class="foot"><button class="btn" id="calBtn" onclick="goWaiting()" disabled>Đồng ý đặt lịch này ✓</button></div>
</div>

<!-- S_WAITING — sau đặt lịch -->
<div class="screen" id="s_waiting">
  <div class="content" style="align-items:center;text-align:center;max-width:520px">
    <div style="font-size:72px;margin-bottom:20px">🌱</div>
    <div style="font-family:'Playfair Display',serif;color:var(--br);font-size:30px;margin-bottom:14px">Hẹn gặp bạn sớm thôi!</div>
    <div style="font-size:15px;color:var(--text-secondary);line-height:1.85;margin-bottom:28px">
      Lịch của bạn đã được ghi nhận.<br>
      <strong>Minh Thư</strong> sẽ xác nhận qua email trong vòng 2 tiếng nhé.
    </div>
    <div style="background:var(--surface-warm);border:1.5px solid var(--border-gold);border-radius:14px;padding:18px 24px;margin-bottom:28px;max-width:380px;width:100%">
      <div style="font-size:11px;color:var(--text-muted);font-weight:700;letter-spacing:1px;text-transform:uppercase;margin-bottom:8px">Lịch của bạn</div>
      <div style="font-size:17px;font-weight:700;color:var(--br)" id="wDay">—</div>
      <div style="font-size:14px;color:var(--text-muted);margin-top:4px" id="wTime">—</div>
    </div>
    <div style="font-size:13px;color:var(--text-muted);line-height:1.9">
      Nếu cần đổi lịch, nhắn cho HR tại<br>
      <a href="https://t.me/HRNhiLeTeam02" target="_blank" style="color:var(--g);font-weight:700">@HRNhiLeTeam02</a> trên Telegram
    </div>
  </div>
</div>

<!-- S_PREPARE -->
<div class="screen" id="s_prepare">
  <div class="content" style="justify-content:flex-start;padding-top:48px;max-width:560px">

    <!-- Avatar + name -->
    <div style="display:flex;align-items:center;gap:10px;margin-bottom:24px;padding-bottom:16px;border-bottom:1px solid #EDE0CC">
      <div style="width:40px;height:40px;border-radius:50%;background:linear-gradient(135deg,#E8B86D,#A07428);display:flex;align-items:center;justify-content:center;font-size:20px;flex-shrink:0">🌱</div>
      <div>
        <div style="font-size:14px;font-weight:700;color:var(--br)">Bé Măng</div>
        <div style="font-size:12px;color:var(--gn)">● Đang hoạt động</div>
      </div>
    </div>

    <!-- Chat bubbles container -->
    <div id="prepareChat" style="display:flex;flex-direction:column;gap:10px;width:100%"></div>

    <!-- Action buttons — hidden until all bubbles shown -->
    <div id="prepareActions" style="display:none;margin-top:24px;display:none;flex-direction:column;gap:10px;max-width:380px">
      <button onclick="startCulture()" style="width:100%;padding:16px 24px;border:none;border-radius:12px;background:linear-gradient(135deg,#2D6A4F,#1B4332);color:white;font-family:'Be Vietnam Pro',sans-serif;font-size:15px;font-weight:700;cursor:pointer;transition:opacity .15s">Mình sẵn sàng rồi →</button>
      <button onclick="go('s_pause')" style="width:100%;padding:14px 24px;border:1.5px solid #D0C8BC;border-radius:12px;background:transparent;color:#8B7355;font-family:'Be Vietnam Pro',sans-serif;font-size:14px;font-weight:500;cursor:pointer;transition:.15s">Để lúc khác nhé</button>
    </div>

  </div>
</div>

<!-- S_PAUSE — chưa rảnh -->
<div class="screen" id="s_pause">
  <div class="content" style="justify-content:center;max-width:560px">
    <div style="font-size:48px;margin-bottom:20px">🌿</div>
    <div class="h2" style="margin-bottom:16px">Không sao cả!</div>
    <div style="font-size:15px;color:var(--text-secondary);line-height:1.85;margin-bottom:28px">
      30 phút mà không tập trung thì xem cũng như không.<br><br>
      Bé Măng vẫn ở đây — hành trình chưa đi đâu cả.<br>
      Khi nào bạn thấy sẵn sàng, quay lại nhé.<br><br>
      <span style="font-size:13px;color:var(--text-muted)">💡 Bookmark trang này lại để dễ tìm hơn.</span>
    </div>
    <button class="btn" onclick="go('s_prepare')" style="max-width:280px">Mình rảnh rồi, bắt đầu thôi →</button>
  </div>
</div>
<div class="screen" id="s_culture">
  <div class="content" style="justify-content:flex-start;padding-top:40px;max-width:680px">

    <!-- Progress -->
    <div style="display:flex;align-items:center;gap:12px;margin-bottom:28px">
      <div style="font-size:13px;color:var(--text-muted)">Video <span id="cvNum">1</span>/10</div>
      <div style="flex:1;height:4px;background:#E8DDD0;border-radius:2px;overflow:hidden">
        <div id="cvBar" style="height:100%;background:linear-gradient(90deg,var(--g),#A07428);border-radius:2px;transition:width .5s ease;width:10%"></div>
      </div>
      <div id="cvDone" style="font-size:12px;color:var(--gn);font-weight:600;display:none">✓ Hoàn thành</div>
    </div>

    <!-- Video title -->
    <div style="margin-bottom:16px">
      <div style="font-size:11px;color:var(--text-muted);letter-spacing:1.5px;text-transform:uppercase;margin-bottom:6px;font-weight:600">Văn hóa & Nguyên tắc</div>
      <div class="h2" id="cvTitle" style="margin-bottom:0;font-size:22px">—</div>
    </div>

    <!-- Video placeholder -->
    <div id="cvEmbed" style="width:100%;aspect-ratio:16/9;background:#1A0E06;border-radius:12px;overflow:hidden;margin-bottom:20px;position:relative;display:flex;align-items:center;justify-content:center">
      <iframe id="cvFrame" width="100%" height="100%" src="" frameborder="0" allow="accelerometer;autoplay;clipboard-write;encrypted-media;gyroscope;picture-in-picture" allowfullscreen style="border:none;display:block"></iframe>
      <div id="cvPlaceholder" style="position:absolute;inset:0;display:flex;flex-direction:column;align-items:center;justify-content:center;gap:12px;background:#1A0E06">
        <div style="font-size:52px">🎬</div>
        <div style="font-size:13px;color:#6B4E2A;text-align:center;max-width:240px;line-height:1.6">Video sẽ được cập nhật sớm.<br>Bạn có thể đọc nội dung bên dưới và chia sẻ cảm nhận.</div>
      </div>
    </div>

    <!-- Video description - hidden, used only by JS -->
    <div id="cvDesc" style="display:none"></div>

    <!-- Chat container -->
    <div id="cvChatWrap" class="chat-wrap">
      <!-- Bot question will be injected here -->
    </div>

    <!-- Input area (shown after question appears) -->
    <div id="cvInputArea" style="display:none;margin-top:16px;max-width:600px">
      <div class="chat-input-area">
        <textarea id="cvAns" placeholder="Chia sẻ suy nghĩ của bạn..." rows="3"
          oninput="document.getElementById('cvSendBtn').disabled=this.value.trim().length<10"></textarea>
        <div class="chat-send-row">
          <button class="chat-send-btn" id="cvSendBtn" onclick="submitCultureAnswer()" disabled>Gửi →</button>
        </div>
      </div>
    </div>

    <!-- Next button (locked until reply is fully read) -->
    <div id="cvNextBox" style="display:none;margin-top:20px">
      <button class="cv-next-btn" id="cvNextBtn" onclick="nextCultureVideo()" disabled>—</button>
      <div id="cvReadHint" style="font-size:12px;color:var(--text-muted);margin-top:8px;display:none">
        📖 Kéo xuống đọc hết phản hồi để tiếp tục
      </div>
    </div>

    <!-- Completion handled by popup -->
    <div id="cvUnlock" style="display:none"></div>

  </div>
</div>

</div><!-- .right -->

</div><!-- .shell -->

<script>
const rooms={
  hr:{n:'HR Team',i:'✉️',d:'Bưu điện Trung tâm Sài Gòn',about:'Biểu tượng của sự kết nối, thấu hiểu và chăm sóc con người. Đây là nơi tiếp nhận thông tin và gắn kết mọi thành viên, đảm bảo sự trơn tru trong bộ máy nhân sự.',date:'Thứ Ba 16/7 lúc 14:00 · Thứ Sáu 19/7 lúc 10:00',r:'Nón Lá Vàng'},
  design:{n:'Design Team',i:'🎨',d:'Làng tranh Đông Hồ',about:'Đại diện cho sự sáng tạo nghệ thuật dựa trên chất liệu dân gian. Team Design là những nghệ nhân hiện đại, thổi hồn vào các sản phẩm hình ảnh mang đậm bản sắc và tính thẩm mỹ cao.',date:'Thứ Tư 17/7 lúc 16:00 · Thứ Bảy 20/7 lúc 10:00',r:'Áo Tứ Thân'},
  it:{n:'IT Team',i:'🏙️',d:'Landmark 81',about:'Biểu tượng của công nghệ hiện đại, tầm vóc và sự đột phá. Đây là nền tảng kỹ thuật vững chắc, thúc đẩy toàn bộ hệ thống vươn tới những đỉnh cao mới.',date:'Thứ Hai 15/7 lúc 18:00 · Thứ Năm 18/7 lúc 14:00',r:'Trống Đồng Mini'},
  social:{n:'Social Event',i:'🏮',d:'Phố cổ Hội An',about:'Tượng trưng cho sự giao thoa văn hóa và không gian kết nối cộng đồng nồng ấm. Hình ảnh đèn lồng và phố cổ phản ánh tính chất sôi nổi, gắn kết của các hoạt động sự kiện.',date:'Thứ Ba 16/7 lúc 10:00 · Chủ Nhật 21/7 lúc 16:00',r:'Đèn Lồng Hội An'},
  academy:{n:'Academy Team',i:'📚',d:'Tàng Thư Lâu',about:'Biểu tượng của kho tàng tri thức và sự lưu trữ bền vững. Đây là trung tâm đào tạo, nơi bảo tồn và phát triển các giá trị học thuật cho cộng đồng nhân tài.',date:'Thứ Tư 17/7 lúc 10:00 · Thứ Sáu 19/7 lúc 18:00',r:'Cuộn Thư Cổ'},
  admin:{n:'Admin Team',i:'🎻',d:'Đờn ca tài tử',about:'Tượng trưng cho sự kết nối cộng đồng và khả năng điều phối linh hoạt. Đây là nơi khởi nguồn của những giá trị truyền thống, phản ánh vai trò "gốc rễ" trong việc quản lý dữ liệu và vận hành hệ thống.',date:'Thứ Năm 18/7 lúc 10:00 · Thứ Bảy 20/7 lúc 14:00',r:'Ấn Triện'},
  nedu:{n:'N-Edu Team',i:'🎓',d:'Văn Miếu Xích Đằng',about:'Tượng trưng cho tinh thần hiếu học và nền tảng giáo dục chuẩn mực. Địa danh này phản ánh sứ mệnh dẫn dắt và khai sáng tri thức của team giáo dục.',date:'Thứ Hai 15/7 lúc 14:00 · Thứ Tư 17/7 lúc 18:00',r:'Mũ Cử Nhân'},
  editor:{n:'Editor Team',i:'🎵',d:'Nhã nhạc Cung đình Huế',about:'Đại diện cho sự chỉn chu, tinh tế và đẳng cấp trong từng sản phẩm. Team Editor như những nhạc công điều phối âm thanh và hình ảnh để tạo nên một tác phẩm nghệ thuật hoàn hảo, lan tỏa thương hiệu.',date:'Thứ Ba 16/7 lúc 18:00 · Thứ Sáu 19/7 lúc 16:00',r:'Phim Trường Thu Nhỏ'}
};
let S={name:'',returning:null,visited:[],day:'',time:'',a1:false,a2:false,tmr:null,tv:900,cur:''};

const progressMap={
  s1: {steps:['','','','','']},
  s2: {steps:['cur','','','','']},
  s3: {steps:['cur','','','','']},
  s5: {steps:['done','cur','','','']},
  s6: {steps:['done','cur','','','']},
  s7: {steps:['done','cur','','','']},
  s8: {steps:['done','done','cur','','']},
  s_prepare:{steps:['done','done','done','cur','']},
  s_pause:  {steps:['done','done','done','cur','']},
  s_culture:{steps:['done','done','done','cur','']},
  s9: {steps:['done','done','done','done','cur']},
  s_waiting:{steps:['done','done','done','done','done']},
  sthanks:{steps:['done','done','done','','']},
};

// Screen history for back button
let screenHistory=[];

function updateStepper(pm){
  if(!pm||!pm.steps) return;
  pm.steps.forEach((state,i)=>{
    const step=document.getElementById('vsS'+(i+1));
    const icon=document.getElementById('vsI'+(i+1));
    if(!step||!icon) return;
    step.className='vstep '+(state||'todo');
    icon.textContent=state==='done'?'✓':(i+1);
  });
}

function go(id){
  const current=document.querySelector('.screen.active');
  if(current && current.id && current.id!==id) screenHistory.push(current.id);
  if(screenHistory.length>20) screenHistory.shift();
  document.querySelectorAll('.screen').forEach(s=>s.classList.remove('active'));
  if(id==='s3') setupLetter();
  if(id==='s_prepare') runPrepareChat();
  if(['s5','s9'].includes(id)) showGuide(id);
  document.getElementById(id).classList.add('active');
  const rightPanel=document.querySelector('.right');
  if(rightPanel) rightPanel.scrollTop=0;
  const backBar=document.getElementById('backBar');
  if(backBar) backBar.style.display=(id==='s1'||id==='s_waiting')?'none':'block';
  const pm=progressMap[id]||{};
  document.getElementById('leftProgress').style.display=id!=='s1'?'block':'none';
  document.getElementById('hrChip').style.display=(id!=='s1'&&id!=='s2')?'flex':'none';
  updateStepper(pm);
}

function goBack(){
  if(screenHistory.length===0) return;
  const prev=screenHistory.pop();
  document.querySelectorAll('.screen').forEach(s=>s.classList.remove('active'));
  if(prev==='s3') setupLetter();
  document.getElementById(prev).classList.add('active');
  const rightPanel=document.querySelector('.right');
  if(rightPanel) rightPanel.scrollTop=0;
  const backBar=document.getElementById('backBar');
  if(backBar) backBar.style.display=prev==='s1'?'none':'block';
  const pm=progressMap[prev]||{};
  document.getElementById('leftProgress').style.display=prev!=='s1'?'block':'none';
  document.getElementById('hrChip').style.display=(prev!=='s1'&&prev!=='s2')?'flex':'none';
  updateStepper(pm);
}


function onName(){
  const v=document.getElementById('nameInp').value.trim();
  const q=document.getElementById('returningQ');
  if(v){
    S.name=v;
    document.getElementById('nameShow').textContent=v;
    document.getElementById('iName').textContent=v;
    if(q.style.display==='none') q.style.display='block';
  }
  updateNameBtn();
}
function setReturning(val){
  S.returning=val;
  document.getElementById('opt-new').className='opt'+(!val?' sel':'');
  document.getElementById('opt-old').className='opt'+(val?' sel':'');
  updateNameBtn();
}
function updateNameBtn(){
  document.getElementById('nameBtn').disabled=!(S.name && S.returning!==null);
}
const guides={
  s5:{t:'Khám phá 8 team 🗺️',b:'NhiLe có 8 team — mỗi team là một thế giới khác nhau. Bạn chọn tối đa 3 team mình thấy hứng thú, đăng ký zoom tour để gặp trực tiếp và hiểu rõ hơn nhé!',i:'🧭'},
  s9:{t:'Đặt lịch phỏng vấn 🤝',b:'Bạn đã đi đến đây — và mình rất vui vì điều đó. Bước cuối là chọn thời gian phù hợp để mình gặp nhau trực tiếp. Minh Thư sẽ xác nhận lịch qua email của bạn nhé!',i:'📅'}
};
function showGuide(id){
  const g=guides[id]; if(!g) return;
  document.getElementById('rdIcon').textContent=g.i;
  document.getElementById('rdName').textContent=g.t;
  document.getElementById('rdSub').textContent='Hành trình NhiLe Team';
  document.getElementById('rdAbout').innerHTML=g.b;
  document.getElementById('rdAboutBox').querySelector('strong').textContent='Thông tin';
  document.getElementById('rdDateBox').style.display='none';
  document.getElementById('rdMailNote').style.display='none';
  document.getElementById('rdBtns').style.display='none';
  document.getElementById('guideBtns').style.display='flex';
  document.getElementById('overlay').classList.add('show');
}
function setupLetter(){
  const body=document.getElementById('letterBody');
  const name=S.name||'bạn';
  if(S.returning){
    body.innerHTML=`Chào ${name}, mình vui vì bạn quay lại!<br><br>Bé Măng không ngờ lại được gặp bạn lần nữa — nhưng thật ra, mình vẫn luôn ở đây chờ.<br><br>Mình biết quay lại không phải quyết định dễ. Cảm ơn bạn đã tin tưởng và cho NhiLe Team thêm một lần nữa.<br><br>Người đồng hành cùng bạn vẫn là <strong>Minh Thư</strong> — bạn ấy luôn ở đây nếu bạn có bất kỳ câu hỏi nào.<br><br>Hãy giữ vững niềm tin vào bản thân và tiếp tục nhé!`;
  }else{
    body.innerHTML=`Chào ${name}, mình đã chờ bạn!<br><br>Cảm ơn bạn đã dành thời gian tìm hiểu về NhiLe Team.<br><br>Chúng mình tin rằng đây chính là khởi đầu của một hành trình ý nghĩa mà bạn dành cho bản thân.<br><br>Người sắp đồng hành cùng bạn là <strong>Minh Thư</strong> — bạn ấy luôn ở đây nếu bạn có bất kỳ câu hỏi nào.<br><br>Hãy giữ vững niềm tin vào bản thân và tiếp tục nhé!`;
  }
}
function onNoted(el){
  const ok=el.value.trim().toLowerCase()==='noted';
  document.getElementById('notedBtn').disabled=!ok;
  el.className='inp'+(ok?' ok':'');
}
function openRoom(id){
  if(document.getElementById('r-'+id).classList.contains('vis'))return;
  S.cur=id;const r=rooms[id];
  document.getElementById('rdIcon').textContent=r.i;
  document.getElementById('rdName').textContent=r.n;
  document.getElementById('rdSub').textContent=r.d;
  document.getElementById('rdAbout').textContent=r.about;
  document.getElementById('rdDate').textContent=r.date;
  document.getElementById('overlay').classList.add('show');
}
function closeOvr(e){if(e.target===document.getElementById('overlay'))closeOvrDirect();}
function closeOvrDirect(){
  document.getElementById('overlay').classList.remove('show');
  // Reset modal state
  document.getElementById('rdDateBox').style.display='block';
  document.getElementById('rdMailNote').style.display='block';
  document.getElementById('rdBtns').style.display='flex';
  document.getElementById('guideBtns').style.display='none';
  document.getElementById('rdAboutBox').querySelector('strong').textContent='Về team này';
}
function joinRoom(){
  closeOvrDirect();
  const id=S.cur;const r=rooms[id];
  ['sRoomName','sName'].forEach(x=>document.getElementById(x).textContent=r.n);
  document.getElementById('sIcon').textContent=r.i;
  document.getElementById('sDesc').textContent=r.d;
  document.getElementById('rItem').textContent=r.r;
  document.getElementById('rTeam').textContent=r.n;
  document.querySelectorAll('.opt').forEach(o=>o.classList.remove('sel'));
  S.a1=false;S.a2=false;
  document.getElementById('sBtn').disabled=true;
  startTmr();go('s6');
}
function startTmr(){
  if(S.tmr)clearInterval(S.tmr);
  S.tv=900;
  S.tmr=setInterval(()=>{
    S.tv--;
    const m=Math.floor(S.tv/60),s=S.tv%60;
    const el=document.getElementById('tnum');
    el.textContent=m+':'+(s<10?'0':'')+s;
    el.className='tnum'+(S.tv<60?' red':'');
    if(S.tv<=0)clearInterval(S.tmr);
  },1000);
}
function pick(el,q){
  document.querySelectorAll('#opts'+q+' .opt').forEach(o=>o.classList.remove('sel'));
  el.classList.add('sel');
  if(q===1)S.a1=true;else S.a2=true;
  document.getElementById('sBtn').disabled=!(S.a1&&S.a2);
}
function submitS(){
  clearInterval(S.tmr);
  const id=S.cur;
  if(!S.visited.includes(id)){
    S.visited.push(id);
    document.getElementById('r-'+id).classList.add('vis');
    document.getElementById('r-'+id).classList.remove('hint');
    const c=S.visited.length;
    document.getElementById('vcnt').textContent=c;
    if(c>=3){
      document.getElementById('mapStatus').textContent='Đã chọn đủ 3 ✓';
      document.getElementById('mapStatus').style.color='#F0C870';
      document.querySelectorAll('.hotspot:not(.vis)').forEach(r=>r.classList.add('maxed'));
    }
    document.getElementById('mapCta').style.display='block';
    document.getElementById('mapNote').textContent=c<3?'Bạn có thể tham quan thêm hoặc nhận thư ngay':'Đã chọn đủ 3 team — nhận thư & quyết định bước tiếp theo';
  }
  document.getElementById('continueBtn').style.display=S.visited.length<3?'block':'none';
  go('s7');
}
function openInvite(){
  const c=S.visited.length;
  const body=`Bạn vừa hoàn thành hành trình khám phá${c>=3?' cả ba team':' các team'}.<br><br>Bé Măng thấy sự kiên trì của bạn trong từng bước — không phải ai cũng làm được điều đó.<br><br>Nếu bạn vẫn muốn tiếp tục, bước tiếp theo là cùng nhau tìm hiểu về những giá trị và nguyên tắc mà NhiLe Team được xây dựng từ đó.<br><br><em>Đây là quyết định của bạn.</em>`;
  const btns=c<3
    ?`<button class="btn" onclick="go('s_prepare')" style="max-width:100%">Mình muốn tiếp tục →</button><div style="text-align:center;margin-top:10px"><a onclick="go('s5')" style="font-size:14px;color:var(--text-muted);text-decoration:underline;cursor:pointer">Tham quan thêm team khác</a></div>`
    :`<button class="btn" onclick="go('s_prepare')" style="max-width:100%">Mình muốn tiếp tục →</button><div style="text-align:center;margin-top:10px"><a onclick="go('sthanks')" style="font-size:14px;color:var(--text-muted);text-decoration:underline;cursor:pointer">Mình cần thêm thời gian</a></div>`;
  document.getElementById('inviteBody').innerHTML=body;
  document.getElementById('inviteBtns').innerHTML=btns;
  go('s8');
}
function pDay(el,d){document.querySelectorAll('.cday').forEach(x=>x.classList.remove('sel'));el.classList.add('sel');S.day=d;updCal();}
function pTime(el,t){document.querySelectorAll('.ctime').forEach(x=>x.classList.remove('sel'));el.classList.add('sel');S.time=t;updCal();}
function updCal(){
  if(S.day&&S.time){
    document.getElementById('csel').textContent=S.day+' lúc '+S.time;
    document.getElementById('cchip').style.display='block';
    document.getElementById('calBtn').disabled=false;
  }
}
function restart(){
  S={name:'',returning:null,visited:[],day:'',time:'',a1:false,a2:false,tmr:null,tv:900,cur:''};
  ['nameInp','notedInp'].forEach(id=>{const el=document.getElementById(id);if(el){el.value='';el.className='inp';}});
  document.getElementById('returningQ').style.display='none';
  document.querySelectorAll('#returningQ .opt').forEach(o=>o.classList.remove('sel'));
  document.getElementById('nameBtn').disabled=true;
  document.getElementById('notedBtn').disabled=true;
  document.getElementById('calBtn').disabled=true;
  document.getElementById('cchip').style.display='none';
  document.getElementById('mapCta').style.display='none';
  document.getElementById('vcnt').textContent='0';
  document.getElementById('mapStatus').textContent='Tối đa 3 team';
  document.getElementById('mapStatus').style.color='var(--rd)';
  document.getElementById('mapNote').textContent='Chạm vào team bất kỳ để xem thông tin và đăng ký tham quan';
  document.querySelectorAll('.hotspot').forEach(r=>r.classList.remove('vis','maxed','hint'));
  document.getElementById('r-hr').classList.add('hint');
  go('s1');
}

// ── PREPARE CHAT ──
const prepMsgs = [
  'Trước khi mình bắt đầu…',
  'Phía trước có <strong>10 video ngắn</strong> — mỗi video khoảng 1 phút — giới thiệu về văn hóa và nguyên tắc vận hành của NhiLe Team.',
  'Tổng thời gian khoảng <strong>30 phút</strong>, bao gồm cả phần bạn chia sẻ suy nghĩ sau mỗi video.',
  'Mình không kỳ vọng bạn phải "trả lời đúng" hay gây ấn tượng với ai.',
  'Những video này để bạn thực sự hiểu NhiLe Team là tổ chức như thế nào — trước khi quyết định có muốn đồng hành lâu dài không.',
  'Nếu bạn thấy cộng hưởng, mình tin hành trình phía sau sẽ rất đáng.\nNếu không — đây cũng là một thông tin quý, để bạn tìm được nơi phù hợp hơn.',
  '💡 Hãy chọn lúc bạn thực sự tập trung — không vội, không bị làm phiền. 30 phút cho một quyết định quan trọng là xứng đáng lắm.',
];

// Reading speed: ~200ms per word, min 600ms, max 2200ms
function readDelay(text){
  const words = text.replace(/<[^>]+>/g,'').split(/\s+/).length;
  return Math.min(Math.max(words * 210, 700), 2200);
}
// Typing delay before next bubble: shorter ~600-900ms
function typingDelay(){ return 700; }

function runPrepareChat(){
  const wrap = document.getElementById('prepareChat');
  wrap.innerHTML = '';
  document.getElementById('prepareActions').style.display = 'none';

  let totalDelay = 400;

  prepMsgs.forEach((msg, i) => {
    const prevMsg = i > 0 ? prepMsgs[i-1] : '';
    const rd = i === 0 ? 0 : readDelay(prevMsg);
    const td = typingDelay();
    const showTypingAt = totalDelay + rd;
    const showMsgAt   = showTypingAt + td;
    totalDelay = showMsgAt;

    // Show typing indicator
    setTimeout(() => {
      // Remove previous typing row if exists
      const old = document.getElementById('prepTyping');
      if(old) old.remove();
      const row = document.createElement('div');
      row.id = 'prepTyping';
      row.className = 'chat-bot';
      row.innerHTML = '<div class="chat-bot-av">🌱</div><div class="chat-typing"><span></span><span></span><span></span></div>';
      wrap.appendChild(row);
      row.scrollIntoView({behavior:'smooth', block:'nearest'});
    }, showTypingAt);

    // Show bubble
    setTimeout(() => {
      const old = document.getElementById('prepTyping');
      if(old) old.remove();
      const row = document.createElement('div');
      row.className = 'chat-bot';
      const isHint = msg.startsWith('💡');
      row.innerHTML = isHint
        ? `<div class="chat-bot-av">🌱</div><div class="chat-bubble-bot" style="background:#FFFBF0;border:1px solid rgba(201,151,58,.3);font-size:13px;color:var(--text-muted)">${msg}</div>`
        : `<div class="chat-bot-av" style="visibility:${i===0?'visible':'hidden'}">🌱</div><div class="chat-bubble-bot">${msg}</div>`;
      // Only show avatar on first bubble
      wrap.appendChild(row);
      row.scrollIntoView({behavior:'smooth', block:'nearest'});
    }, showMsgAt);
  });

  // Show action buttons after all bubbles
  const lastRead = readDelay(prepMsgs[prepMsgs.length - 1]);
  setTimeout(() => {
    const old = document.getElementById('prepTyping');
    if(old) old.remove();
    const actions = document.getElementById('prepareActions');
    actions.style.display = 'flex';
    actions.scrollIntoView({behavior:'smooth', block:'nearest'});
  }, totalDelay + lastRead + 400);
}


const cVideos=[
  {title:'Tại sao NhiLe Team tồn tại?',desc:'Mỗi tổ chức đều có một lý do để tồn tại — không phải doanh thu, không phải tăng trưởng. NhiLe Team được xây dựng từ một câu hỏi: Làm thế nào để tạo ra môi trường mà mỗi người đều thực sự phát triển?',q:'Xem xong rồi nhé! Điều gì khiến bạn tìm đến NhiLe Team? Và bạn kỳ vọng tìm thấy gì ở đây?',reply:'Mình thích cách bạn đặt câu hỏi cho bản thân. Ở NhiLe, lý do bạn ở đây quan trọng hơn kỹ năng bạn mang theo rất nhiều — và mình thấy bạn đang nghĩ đến điều đó một cách thật sự. Tiếp tục nhé!'},
  {title:'Fail Fast, Learn Faster',desc:'Sai không phải là điều đáng xấu hổ — sai mà không rút ra bài học mới là vấn đề. NhiLe xây dựng môi trường mà thử nghiệm được khuyến khích, và mỗi thất bại là một bước học.',q:'Xem xong rồi nhé! Kể lại một lần bạn làm sai và học được điều gì từ đó. Bạn cảm thấy thế nào lúc đó?',reply:'Bạn vừa chia sẻ một khoảnh khắc rất thật — không phải ai cũng dám làm vậy. Ở NhiLe, người dám thừa nhận sai và học từ đó phát triển nhanh hơn nhiều. Mình thấy bạn đã hiểu điều này rồi đấy.'},
  {title:'Trách nhiệm không cần nhắc',desc:'Khi bạn nhận một việc, NhiLe tin tưởng bạn sẽ làm đến cùng — không cần ai nhắc, không cần deadline mới thúc. Đây là nguyên tắc nền tảng để đội ngũ vận hành trơn tru.',q:'Xem xong rồi nhé! Bạn thường xử lý thế nào khi có quá nhiều việc cùng lúc? Bạn ưu tiên ra sao?',reply:'Mình đọc được sự thành thật trong cách bạn mô tả. Không có công thức hoàn hảo — quan trọng là bạn có hệ thống của riêng mình và biết nói ra khi cần hỗ trợ. Đó là điều mình trân trọng lắm.'},
  {title:'Nói thẳng — Không vòng vo',desc:'NhiLe coi giao tiếp thẳng thắn là tôn trọng — tôn trọng thời gian của nhau, tôn trọng sự thật. Không nói sau lưng, không im lặng chịu đựng. Có vấn đề thì nói ra.',q:'Xem xong rồi nhé! Bạn đã bao giờ phải nói điều khó nói với ai đó chưa? Bạn xử lý tình huống đó thế nào?',reply:'Đó là khoảnh khắc cần can đảm — và bạn đã làm. Ở NhiLe, những cuộc trò chuyện khó như vậy là bình thường và được coi là dấu hiệu trưởng thành. Cảm ơn bạn đã chia sẻ thật lòng.'},
  {title:'Chất lượng hơn số lượng',desc:'NhiLe không chạy theo "làm nhiều". Mình chạy theo "làm tốt". Mỗi sản phẩm, mỗi nội dung, mỗi quyết định đều được cân nhắc kỹ — vì chất lượng mới tạo ra giá trị bền vững.',q:'Xem xong rồi nhé! Kể về một việc bạn đã làm mà bạn thực sự tự hào về chất lượng. Điều gì làm bạn hài lòng nhất?',reply:'Bạn vừa mô tả cảm giác khi làm một việc đúng với tiêu chuẩn của mình — không phải tiêu chuẩn của ai khác. Ở NhiLe, đó là cảm giác mình muốn mọi người được trải nghiệm mỗi ngày. Nghe hay lắm.'},
  {title:'Tự học — Không chờ được dạy',desc:'Ở NhiLe, không ai chờ sẵn để dạy bạn từng bước. Bạn cần chủ động tìm tài nguyên, hỏi đúng người, và tự xây dựng năng lực. Môi trường ở đây hỗ trợ bạn — nhưng engine phải là bạn.',q:'Xem xong rồi nhé! Gần đây bạn tự học điều gì mới? Tại sao bạn học điều đó và bạn học bằng cách nào?',reply:'Mình thích cách bạn chủ động với việc học của mình. Ở NhiLe, sự tò mò và tự học không phải là điểm cộng — đó là điều kiện cơ bản để phát triển. Và rõ ràng bạn đã có tư duy đó rồi.'},
  {title:'Cộng đồng — Không chỉ đồng nghiệp',desc:'Những người ở NhiLe không chỉ làm việc cùng nhau. Mình xây dựng, hỗ trợ và quan tâm đến nhau thực sự. Giá trị không chỉ ở công việc — mà ở mối quan hệ được vun đắp lâu dài.',q:'Xem xong rồi nhé! Mối quan hệ với đồng nghiệp quan trọng như thế nào với bạn? Bạn muốn có môi trường làm việc như thế nào?',reply:'Bạn nói về kết nối con người theo cách rất chân thật — không phải ai cũng làm được. Ở NhiLe, những người coi trọng mối quan hệ thường là người ở lại lâu nhất và đóng góp nhiều nhất. Mình thấy bạn thuộc về nhóm đó.'},
  {title:'Phản hồi — Cho và nhận',desc:'Phản hồi là món quà — dù có đau một chút. NhiLe xây dựng văn hóa feedback thẳng thắn, xây dựng, không mang tính cá nhân. Mục tiêu là giúp nhau tốt hơn, không phải thắng nhau.',q:'Xem xong rồi nhé! Bạn đón nhận phản hồi tiêu cực như thế nào? Có lần nào bạn nhận feedback rồi thực sự thay đổi không?',reply:'Cảm ơn bạn đã thành thật — đây là câu hỏi không dễ trả lời. Mình thấy bạn đang phản tư thực sự chứ không chỉ nói những gì người khác muốn nghe. Ở NhiLe, đó là phẩm chất quý hơn nhiều kỹ năng kỹ thuật.'},
  {title:'Dài hạn — Không phải sprint',desc:'NhiLe không tìm người chạy nhanh rồi kiệt sức. Mình tìm người đồng hành bền vững — hiểu rằng phát triển cần thời gian, và cam kết với quá trình dài hơn kết quả ngắn hạn.',q:'Xem xong rồi nhé! Bạn thấy mình đang ở đâu trong 2–3 năm tới? NhiLe Team có thể đóng vai trò gì trong hành trình đó?',reply:'Bạn vừa chia sẻ điều gì đó rất cá nhân và có chiều sâu. Mình thấy bạn không tìm kiếm một điểm đến — bạn đang tìm một hành trình. Và đó chính xác là cách NhiLe được xây dựng. Chỉ còn một video cuối nữa thôi!'},
  {title:'Bạn và NhiLe Team — Câu hỏi cuối',desc:'Bạn vừa dành 30 phút để lắng nghe và suy nghĩ. Đây là khoảnh khắc để nhìn lại — với bản thân, với NhiLe, với hành trình phía trước.',q:'Xem xong rồi nhé! Sau tất cả những gì bạn vừa xem — điều gì khiến bạn vẫn muốn tiếp tục? Và có điều gì bạn còn băn khoăn không?',reply:'Bạn đã đi đến đây — và mình rất vui vì điều đó. Những băn khoăn bạn chia sẻ hoàn toàn tự nhiên, và sẽ có không gian để nói thêm trong buổi gặp gỡ. Cảm ơn bạn đã dành thời gian thực sự suy nghĩ — đó là điều ý nghĩa nhất bạn có thể làm cho chính mình.'}
];

let cIdx=0;

function startCulture(){
  cIdx=0;
  // Navigate directly — skip s_prepare entirely
  document.querySelectorAll('.screen').forEach(s=>s.classList.remove('active'));
  document.getElementById('s_culture').classList.add('active');
  const rp=document.querySelector('.right');
  if(rp) rp.scrollTop=0;
  // Update stepper
  const pm=progressMap['s_culture']||{};
  document.getElementById('leftProgress').style.display='block';
  document.getElementById('hrChip').style.display='flex';
  if(pm.steps){
    pm.steps.forEach((state,i)=>{
      const step=document.getElementById('vsS'+(i+1));
      const icon=document.getElementById('vsI'+(i+1));
      if(!step||!icon) return;
      step.className='vstep '+(state||'todo');
      icon.textContent=state==='done'?'✓':(i+1);
    });
  }
  loadCultureVideo(0);
}

function loadCultureVideo(i){
  const v=cVideos[i];
  document.getElementById('cvNum').textContent=i+1;
  document.getElementById('cvBar').style.width=((i+1)/10*100)+'%';
  document.getElementById('cvTitle').textContent=v.title;
  // Set description in chat as context
  const descEl=document.getElementById('cvDesc');
  if(descEl) descEl.textContent=v.desc;
  // Reset chat
  document.getElementById('cvChatWrap').innerHTML='';
  const ans=document.getElementById('cvAns');
  ans.value=''; ans.disabled=false;
  document.getElementById('cvSendBtn').disabled=true;
  document.getElementById('cvInputArea').style.display='none';
  document.getElementById('cvNextBox').style.display='none';
  document.getElementById('cvUnlock').style.display='none';
  document.getElementById('cvDone').style.display='none';
  document.getElementById('cvPlaceholder').style.display='flex';
  document.getElementById('cvFrame').src='';
  const rp=document.querySelector('.right');
  if(rp) rp.scrollTop=0;
  // Show question bubble after 2s
  setTimeout(()=>{
    appendBotBubble(v.q);
    document.getElementById('cvInputArea').style.display='block';
    document.getElementById('cvInputArea').scrollIntoView({behavior:'smooth',block:'nearest'});
  },2000);
}

function appendBotBubble(text){
  const wrap=document.getElementById('cvChatWrap');
  const row=document.createElement('div');
  row.className='chat-bot';
  row.innerHTML='<div class="chat-bot-av">🌱</div><div class="chat-bubble-bot">'+text+'</div>';
  wrap.appendChild(row);
}

function appendUserBubble(text){
  const wrap=document.getElementById('cvChatWrap');
  const row=document.createElement('div');
  row.className='chat-user';
  row.innerHTML='<div class="chat-bubble-user">'+text+'</div>';
  wrap.appendChild(row);
}

function appendTypingBubble(){
  const wrap=document.getElementById('cvChatWrap');
  const row=document.createElement('div');
  row.className='chat-bot';
  row.id='cvTypingRow';
  row.innerHTML='<div class="chat-bot-av">🌱</div><div class="chat-typing"><span></span><span></span><span></span></div>';
  wrap.appendChild(row);
  row.scrollIntoView({behavior:'smooth',block:'nearest'});
  return row;
}

function submitCultureAnswer(){
  const ans=document.getElementById('cvAns').value.trim();
  if(ans.length<10) return;
  document.getElementById('cvSendBtn').disabled=true;
  document.getElementById('cvAns').disabled=true;
  appendUserBubble(ans);
  document.getElementById('cvInputArea').style.display='none';
  const typingRow=appendTypingBubble();
  setTimeout(()=>{
    typingRow.remove();
    appendBotBubble(cVideos[cIdx].reply);
    const isLast=cIdx===9;
    const nb=document.getElementById('cvNextBtn');
    nb.textContent=isLast?'Xem kết quả 🎉':'Video tiếp theo →';
    nb.disabled=true;
    document.getElementById('cvNextBox').style.display='block';
    document.getElementById('cvReadHint').style.display='block';
    setTimeout(()=>{
      const wrap=document.getElementById('cvChatWrap');
      const last=wrap.lastElementChild;
      if(last) last.scrollIntoView({behavior:'smooth',block:'nearest'});
      setupReadUnlock();
    },200);
  },1500);
}

function setupReadUnlock(){
  const rp=document.querySelector('.right');
  const nextBox=document.getElementById('cvNextBox');
  function checkScroll(){
    const nb=document.getElementById('cvNextBtn');
    if(!nb||!nb.disabled) return;
    const rect=nextBox.getBoundingClientRect();
    if(rect.top < window.innerHeight + 80){
      nb.disabled=false;
      document.getElementById('cvReadHint').style.display='none';
      rp.removeEventListener('scroll',checkScroll);
    }
  }
  rp.addEventListener('scroll',checkScroll);
  setTimeout(checkScroll,400);
}

function goWaiting(){
  document.getElementById('wDay').textContent=S.day||'—';
  document.getElementById('wTime').textContent=S.time?'Lúc '+S.time:'—';
  go('s_waiting');
}
function nextCultureVideo(){
  cIdx++;
  if(cIdx>=10){
    document.getElementById('cvDone').style.display='block';
    document.getElementById('cvBar').style.width='100%';
    document.getElementById('cvNum').textContent='10';
    document.getElementById('cvNextBox').style.display='none';
    setTimeout(()=> go('s9'), 600);
    return;
  }
  loadCultureVideo(cIdx);
}

go('s1');
</script>
</body>
</html>
