<!DOCTYPE html>
<html lang="ru">
<head><link rel="manifest" href="/Zametvibe/manifest.json">
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover, interactive-widget=resizes-content">
<meta name="theme-color" content="#000000">
<title>Vibe</title>
<link href="https://fonts.googleapis.com/css2?family=Onest:wght@400;500;600;700&family=Literata:wght@400;600&family=Caveat:wght@500;700&display=swap" rel="stylesheet">
<style>
/*1 Токены: чёрный и его оттенки, жёлтый только для главного*/
:root{--bg:#000;--s1:#141414;--s2:#1f1f1f;--s3:#2b2b2b;--tx:#f4f4f1;--mu:#8d8d88;--ln:#262626;--ac:#f2b800;--acx:#1a1400;--dg:#ff5d4f;
--ui:'Onest',system-ui,-apple-system,'Segoe UI',Roboto,sans-serif;--nf:'Onest',system-ui,sans-serif;--fs:17px;--L:32px;--kb:0px;
--ease:cubic-bezier(.2,.8,.2,1);
box-sizing:border-box;padding-top:env(safe-area-inset-top,0px);padding-bottom:env(safe-area-inset-bottom,0px)}
html{scroll-padding-top:env(safe-area-inset-top,0px)}
*{box-sizing:border-box;-webkit-tap-highlight-color:transparent}
html,body{height:100%;margin:0;background:#000;color:var(--tx);font:16px/1.4 var(--ui);overscroll-behavior:none;-webkit-font-smoothing:antialiased;color-scheme:dark}
body{position:relative;overflow:hidden}
button,input,textarea{font:inherit;color:inherit;border:0;background:none;padding:0;margin:0}
button{cursor:pointer;touch-action:manipulation}
svg{width:26px;height:26px;flex:none;display:block}
:focus-visible{outline:2px solid var(--ac);outline-offset:2px}
input:focus-visible,textarea:focus-visible,[contenteditable]:focus-visible{outline:0}
::selection{background:rgba(242,184,0,.35)}
[hidden]{display:none!important}
.noanim *,.noanim *::before,.noanim *::after{animation-duration:.01ms!important;transition-duration:.01ms!important}
@media(prefers-reduced-motion:reduce){*,*::before,*::after{animation-duration:.01ms!important;transition-duration:.01ms!important}}
@keyframes rise{from{opacity:0;transform:translateY(10px)}}
@keyframes pop{0%{transform:scale(.7)}60%{transform:scale(1.12)}100%{transform:scale(1)}}
@keyframes shake{20%,60%{transform:translateX(-8px)}40%,80%{transform:translateX(8px)}}
@keyframes unveil{from{opacity:0;filter:blur(14px);transform:scale(.96)}}
@keyframes fnext{from{opacity:0;transform:translateX(46px)}}
@keyframes fprev{from{opacity:0;transform:translateX(-46px)}}
@keyframes strike{from{text-decoration-color:transparent}}

/*2 Каркас и главный экран*/
#app{position:relative;height:100%;overflow:hidden}
.screen{position:absolute;inset:0;display:flex;flex-direction:column;background:#000}
#home{transition:transform .38s var(--ease),opacity .38s}
#home.under{transform:translateX(-16%);opacity:.45}
.top{display:flex;align-items:center;justify-content:space-between;padding:8px 16px 4px;flex:none}
.cbtn{width:48px;height:48px;border-radius:50%;background:var(--s1);border:1px solid var(--ln);display:grid;place-items:center;flex:none;transition:transform .15s var(--ease),background .2s}
.cbtn:active{transform:scale(.9);background:var(--s2)}
.cbtn.pri{background:var(--ac);border-color:var(--ac);color:var(--acx)}
.seg{position:relative;display:flex;background:var(--s1);border:1px solid var(--ln);border-radius:99px;padding:4px}
.seg i{position:absolute;top:4px;bottom:4px;left:0;border-radius:99px;background:var(--s2);transition:transform .32s var(--ease),width .32s var(--ease)}
.seg button{position:relative;z-index:1;padding:10px 18px;border-radius:99px;color:var(--mu);font-weight:600;transition:color .25s}
.seg button.on{color:var(--ac)}
#hscroll{flex:1;overflow-y:auto;overflow-x:hidden;padding:0 16px 130px;-webkit-overflow-scrolling:touch}
#hscroll.swap #hlist{animation:rise .3s var(--ease)}
h1{font-size:38px;line-height:1.1;margin:16px 0 6px;font-weight:700;letter-spacing:-.02em}
h2.g{font-size:20px;margin:22px 0 10px;font-weight:700}
.cards{display:flex;flex-direction:column;gap:10px}
.grid .cards{display:grid;grid-template-columns:1fr 1fr}
.card{position:relative;display:flex;gap:14px;background:var(--s1);border-radius:22px;padding:16px 18px;min-height:96px;user-select:none;-webkit-user-select:none;-webkit-touch-callout:none;transition:transform .18s var(--ease),opacity .2s,background .2s;animation:rise .35s var(--ease) both;animation-delay:calc(var(--i)*22ms)}
.card:active{transform:scale(.985)}
.card.armed{transform:scale(1.03);background:var(--s2)}
.card.src{opacity:.25}
.cb{flex:1;min-width:0;display:flex;flex-direction:column}
.card h3{margin:0;font-size:17px;font-weight:600;white-space:nowrap;overflow:hidden;text-overflow:ellipsis}
.card p{margin:4px 0 0;color:var(--mu);font-size:15px;line-height:1.35;display:-webkit-box;-webkit-line-clamp:2;-webkit-box-orient:vertical;overflow:hidden;word-break:break-word}
.meta{display:flex;align-items:center;gap:8px;margin-top:auto;padding-top:10px;color:var(--mu);font-size:13px;min-width:0}
.meta svg{width:18px;height:18px}
.meta .fl{display:flex;align-items:center;gap:6px;min-width:0;overflow:hidden;white-space:nowrap;text-overflow:ellipsis}
.chip{background:var(--s2);border-radius:8px;padding:3px 8px;font-size:12px;color:var(--mu);flex:none}
.th{width:84px;height:84px;border-radius:14px;flex:none;align-self:center;display:grid;place-items:center;overflow:hidden}
.th img{width:100%;height:100%;object-fit:cover}
.th.cvr{width:64px;height:84px;background:none;overflow:visible}
.grid .card{flex-direction:column;padding:14px}
.grid .th{order:-1;width:100%;height:90px;align-self:stretch}
.grid .th.cvr{width:100%;display:flex;justify-content:flex-start}
.grid .th.cvr .cover{height:90px;width:auto}
.empty{margin:80px 20px;text-align:center;color:var(--mu);font-size:16px;line-height:1.5}
.empty svg{margin:0 auto 14px;width:44px;height:44px;opacity:.6}
.reveal .card{animation:unveil .6s var(--ease) both;animation-delay:calc(var(--i)*70ms)}
.bar{position:absolute;left:0;right:0;bottom:0;padding:34px 16px 14px;display:flex;gap:10px;background:linear-gradient(transparent,#000 55%);pointer-events:none}
.bar>*{pointer-events:auto}
.pill{flex:1;min-width:0;display:flex;align-items:center;gap:10px;height:48px;padding:0 16px;border-radius:99px;background:var(--s1);border:1px solid var(--ln);color:var(--mu)}
.pill input{flex:1;min-width:0;height:100%;color:var(--tx);outline:0;font-size:17px}
.pill input::placeholder{color:var(--mu)}

/*3 Обложки как у книг*/
.cover{position:relative;aspect-ratio:3/4;height:100%;border-radius:3px 9px 9px 3px;background:linear-gradient(90deg,rgba(0,0,0,.4) 0 7%,rgba(255,255,255,.14) 7% 9%,transparent 9%),var(--c);box-shadow:0 6px 16px #0008;overflow:hidden;transition:transform .25s var(--ease),box-shadow .25s}
.cover::before{content:"";position:absolute;inset:0}
.cover[data-p=lines]::before{background:repeating-linear-gradient(0deg,rgba(255,255,255,.09) 0 1px,transparent 1px 9px)}
.cover[data-p=grid]::before{background:linear-gradient(rgba(255,255,255,.08) 1px,transparent 1px) 0 0/10px 10px,linear-gradient(90deg,rgba(255,255,255,.08) 1px,transparent 1px) 0 0/10px 10px}
.cover[data-p=dots]::before{background:radial-gradient(rgba(255,255,255,.16) 1.2px,transparent 1.6px) 0 0/10px 10px}
.cover b{position:absolute;left:19%;right:11%;top:20%;background:#efe6cf;color:#2a2318;font:700 .72em/1.15 Literata,Georgia,serif;padding:.55em .5em;border-radius:2px;text-align:center;overflow:hidden;display:-webkit-box;-webkit-line-clamp:3;-webkit-box-orient:vertical;min-height:2.2em;word-break:break-word}
.cover.mini b{padding:0;min-height:0;height:16%;font-size:0}
.cover.big{width:132px;height:176px;font-size:15px;margin:0 auto}

/*4 Меню слева, шторки, меню зажатия*/
.scrim{position:fixed;inset:0;background:rgba(0,0,0,.72);opacity:0;transition:opacity .3s;z-index:70}
.scrim.on{opacity:1}
.drawer{position:fixed;z-index:71;left:10px;top:calc(env(safe-area-inset-top,0px) + 10px);bottom:calc(env(safe-area-inset-bottom,0px) + 10px);width:min(86vw,340px);background:#1a1a1a;border-radius:32px;padding:16px 12px;display:flex;flex-direction:column;overflow-y:auto;transform:translateX(calc(-100% - 24px));transition:transform .4s var(--ease)}
.drawer.on{transform:none}
.drawer .lbl{display:flex;justify-content:space-between;align-items:center;padding:14px 14px 8px;color:var(--mu);font-size:15px}
.drawer .lbl button{color:var(--ac);font-weight:600;font-size:16px}
.dr{display:flex;align-items:center;gap:14px;padding:13px 14px;border-radius:18px;font-size:17px;font-weight:500;user-select:none;-webkit-user-select:none;transition:background .2s}
.dr:active{background:var(--s3)}
.dr.on{background:var(--s3)}
.dr>svg{color:var(--mu)}
.dr.on>svg{color:var(--tx)}
.dr .n{margin-left:auto;color:var(--mu);font-weight:500;font-size:16px}
.dr .mc{width:26px;height:34px;flex:none}
.dr .mc .cover{width:26px;height:34px;aspect-ratio:auto;border-radius:2px 4px 4px 2px;box-shadow:none}
.dr .mc .cover b{left:22%;right:12%;top:22%;height:18%}
.sp{flex:1}
.sh{position:fixed;left:0;right:0;bottom:0;z-index:73;background:#171717;border-radius:30px 30px 0 0;padding:10px 18px calc(env(safe-area-inset-bottom,0px) + 20px);max-height:88%;overflow-y:auto;transform:translateY(100%);transition:transform .4s var(--ease)}
.sh.on{transform:none}
.sh .hd{width:40px;height:5px;border-radius:9px;background:var(--s3);margin:0 auto 14px;touch-action:none}
.sh h3{margin:0 0 14px;font-size:22px;font-weight:700}
.sh .sub{color:var(--mu);font-size:15px;margin:-6px 0 14px}
.sh .lbl{color:var(--mu);font-size:14px;margin:18px 0 8px}
.row{display:flex;gap:10px;margin-top:14px}
.row>*{flex:1;min-width:0}
.row .btn{padding:0 10px;white-space:nowrap}
.btn{height:50px;padding:0 20px;border-radius:16px;background:var(--s2);font-weight:600;transition:transform .15s var(--ease)}
.btn:active{transform:scale(.97)}
.btn.pri{background:var(--ac);color:var(--acx)}
.btn.dg{color:var(--dg)}
.in{width:100%;height:54px;border-radius:16px;background:var(--s2);padding:0 16px;font-size:17px;outline:0;margin-bottom:10px}
.in.shake,.shake{animation:shake .4s}
.hint{min-height:20px;color:var(--dg);font-size:14px;margin:-2px 0 6px}
.mo{position:fixed;inset:0;z-index:80;background:rgba(0,0,0,.55);backdrop-filter:blur(16px);-webkit-backdrop-filter:blur(16px);opacity:0;transition:opacity .25s;display:flex;overflow:auto}
.mo.on{opacity:1}
.mcol{margin:auto;display:flex;flex-direction:column;gap:12px;align-items:stretch;width:min(320px,88vw);padding:16px 0}
.mo.tr .mcol{margin:calc(env(safe-area-inset-top,0px) + 66px) 12px auto auto;align-items:flex-end}
.mcol .card{pointer-events:none;transform:scale(1.02);box-shadow:0 24px 60px #000c;animation:none;width:100%}
.mp{background:#222;border-radius:24px;padding:6px;box-shadow:0 20px 50px #000a;transform-origin:top center;transform:scale(.92) translateY(-8px);opacity:0;transition:transform .3s var(--ease),opacity .2s;width:100%}
.mo.tr .mp{transform-origin:top right;width:260px}
.mo.on .mp{transform:none;opacity:1}
.mi{display:flex;align-items:center;gap:14px;height:50px;padding:0 14px;border-radius:16px;font-size:17px;font-weight:500;width:100%;text-align:left}
.mi:active{background:var(--s3)}
.mi svg{width:24px;height:24px;color:var(--mu)}
.mi.dg,.mi.dg svg{color:var(--dg)}
.mo.on .mi{animation:rise .3s var(--ease) both;animation-delay:calc(var(--i)*20ms)}
.md{height:1px;background:var(--ln);margin:4px 12px}
.shelf{position:fixed;left:0;right:0;top:0;z-index:60;padding:calc(env(safe-area-inset-top,0px) + 12px) 16px 20px;background:linear-gradient(#000 72%,transparent);transform:translateY(-110%);transition:transform .35s var(--ease);pointer-events:none}
.shelf.on{transform:none}
.shelf .sk{pointer-events:auto}
.shelf .st{color:var(--mu);font-size:14px;margin-bottom:10px}
.shelf .sr{display:flex;gap:14px;overflow:hidden}
.sk{width:76px;flex:none;text-align:center;font-size:12px;color:var(--mu)}
.sk .cover{height:100px;width:76px;margin-bottom:6px}
.sk.hot{color:var(--tx)}
.sk.hot .cover{transform:scale(1.14) translateY(-4px);box-shadow:0 0 0 2px var(--ac),0 10px 24px #000a}
.sk .nw{height:100px;border:2px dashed var(--s3);border-radius:10px;display:grid;place-items:center;margin-bottom:6px;color:var(--mu)}
.sk.hot .nw{border-color:var(--ac);color:var(--ac)}
.ghost{position:fixed;left:0;top:0;z-index:90;pointer-events:none;box-shadow:0 24px 50px #000c;background:var(--s2);animation:none;margin:0}
#toast{position:fixed;left:50%;bottom:calc(env(safe-area-inset-bottom,0px) + 90px);z-index:100;transform:translate(-50%,20px);opacity:0;pointer-events:none;background:#2a2a2a;border-radius:16px;padding:12px 18px;font-size:15px;display:flex;gap:16px;align-items:center;max-width:90vw;transition:transform .3s var(--ease),opacity .25s}
#toast.on{transform:translate(-50%,0);opacity:1;pointer-events:auto}
#toast button{color:var(--ac);font-weight:700}

/*5 Листы выбора: обложки, бумага, настройки*/
.sw{display:flex;gap:12px;flex-wrap:wrap}
.sw button{width:46px;height:46px;border-radius:50%;border:3px solid transparent;transition:transform .2s var(--ease),border-color .2s}
.sw button.on{border-color:var(--ac);transform:scale(1.08)}
.pat{display:flex;gap:10px}
.pat button,.rl button{flex:1;height:64px;border-radius:14px;background:var(--s2);border:2px solid transparent;color:var(--mu);font-size:13px;display:flex;flex-direction:column;gap:6px;align-items:center;justify-content:center;transition:border-color .2s}
.pat button.on,.rl button.on{border-color:var(--ac);color:var(--tx)}
.rl{display:flex;gap:8px}
.rl button i{width:34px;height:22px;border-radius:5px;background:#f0e6cc}
.rl button[data-r=lines] i{background:linear-gradient(transparent 6px,rgba(95,70,20,.45) 6px 7px) 0 0/100% 7px,#f0e6cc}
.rl button[data-r=grid] i{background:linear-gradient(transparent 6px,rgba(95,70,20,.45) 6px 7px) 0 0/7px 7px,linear-gradient(90deg,transparent 6px,rgba(95,70,20,.45) 6px 7px) 0 0/7px 7px,#f0e6cc}
.rl button[data-r=dots] i{background:radial-gradient(rgba(95,70,20,.6) 1.1px,transparent 1.5px) 0 0/7px 7px,#f0e6cc}
.pgr{display:flex;align-items:center;gap:10px}
.pgr b{flex:1;text-align:center;font-size:17px}
.lst{display:flex;flex-direction:column}
.fr{display:flex;align-items:center;gap:14px;padding:10px 6px;border-radius:16px;font-size:17px;font-weight:500;width:100%;text-align:left}
.fr:active{background:var(--s2)}
.fr .mc{width:34px;height:44px;flex:none}
.fr .mc .cover{width:34px;height:44px;aspect-ratio:auto}
.fr svg.ok{margin-left:auto;color:var(--ac)}
.setr{display:flex;align-items:center;gap:12px;min-height:54px;border-bottom:1px solid var(--ln);font-size:17px}
.setr:last-child{border:0}
.setr>span{flex:1}
.setr .btn{height:40px;padding:0 14px;font-size:15px;flex:none}
.tg{width:54px;height:32px;border-radius:99px;background:var(--s3);position:relative;transition:background .25s;flex:none}
.tg::after{content:"";position:absolute;left:4px;top:4px;width:24px;height:24px;border-radius:50%;background:#fff;transition:transform .3s var(--ease)}
.tg.on{background:var(--ac)}
.tg.on::after{transform:translateX(22px);background:var(--acx)}
.opt{display:flex;background:var(--s2);border-radius:12px;padding:3px}
.opt button{padding:8px 12px;border-radius:10px;color:var(--mu);font-size:14px;font-weight:600}
.opt button.on{background:var(--s3);color:var(--tx)}
textarea.in{height:140px;padding:14px;resize:none;font-size:14px}
.ptiles{display:grid;grid-template-columns:repeat(3,1fr);gap:12px}
.pt{aspect-ratio:3/4;border-radius:12px;padding:10px;font-size:11px;line-height:1.3;overflow:hidden;text-align:left;border:2px solid transparent;position:relative;transition:transform .2s var(--ease)}
.pt:active{transform:scale(.96)}
.pt.on{border-color:var(--ac)}
.pt em{position:absolute;right:8px;bottom:6px;font-style:normal;font-weight:700;font-size:13px;opacity:.6}
.pt.add{background:var(--s2);display:grid;place-items:center;color:var(--mu)}
.vz{height:130px;display:flex;align-items:center;justify-content:center;gap:5px;margin:6px 0 10px}
.vz i{width:6px;height:8px;border-radius:4px;background:var(--ac);opacity:.85;transition:height .09s linear}
.vt{text-align:center;font-size:30px;font-weight:600;font-variant-numeric:tabular-nums;margin-bottom:4px}
.vl{text-align:center;color:var(--mu);font-size:15px;min-height:44px;margin-bottom:10px;line-height:1.35}
.vm{display:flex;justify-content:center;margin-bottom:16px}
.vgo{width:76px;height:76px;border-radius:50%;background:var(--ac);color:var(--acx);display:grid;place-items:center;margin:0 auto;transition:transform .2s var(--ease)}
.vgo:active{transform:scale(.92)}
.vgo svg{width:32px;height:32px}

/*6 Задачи*/
.task{display:flex;align-items:flex-start;gap:14px;padding:14px 4px;border-bottom:1px solid var(--ln);animation:rise .3s var(--ease) both;animation-delay:calc(var(--i)*20ms);transition:opacity .3s,transform .3s var(--ease)}
.task.out{opacity:0;transform:translateX(24px)}
.ck{width:30px;height:30px;border-radius:50%;border:2.5px solid #5b5b5b;flex:none;margin-top:-1px;position:relative;transition:background .25s,border-color .25s}
.ck::after{content:"";position:absolute;inset:0;background:url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 24 24' fill='none' stroke='%231a1400' stroke-width='3.4' stroke-linecap='round' stroke-linejoin='round'%3E%3Cpath d='M6 12.5l4 4L18 8'/%3E%3C/svg%3E") center/20px no-repeat;transform:scale(0);transition:transform .3s var(--ease)}
.task.d .ck{background:var(--ac);border-color:var(--ac)}
.task.d .ck::after{transform:scale(1)}
.tl{font-size:18px;line-height:1.35;word-break:break-word;background:linear-gradient(currentColor,currentColor) no-repeat 0 60%/0 2px;-webkit-box-decoration-break:clone;box-decoration-break:clone;transition:background-size .38s var(--ease),color .3s}
.task.d .tl{background-size:100% 2px;color:var(--mu)}
.dh{display:flex;align-items:center;gap:8px;margin:24px 0 4px;color:var(--mu);font-weight:600;font-size:16px}
.dh svg{width:20px;height:20px;transition:transform .3s var(--ease)}
.dh.open svg{transform:rotate(90deg)}
.dl{display:none}
.dl.open{display:block}

/*7 Редактор*/
#ed{transform:translateX(100%);transition:transform .38s var(--ease);z-index:20}
#ed.on{transform:none}
.etop{display:flex;align-items:center;gap:10px;padding:8px 14px;flex:none;transition:opacity .25s,transform .3s var(--ease)}
.etop .sp{flex:1}
.ur{display:flex;background:var(--s1);border:1px solid var(--ln);border-radius:99px;height:48px;padding:0 4px}
.ur button{width:46px;display:grid;place-items:center;color:var(--mu);transition:color .2s}
.ur button:active{color:var(--tx)}
.done{display:none;height:48px;padding:0 20px;border-radius:99px;background:var(--ac);color:var(--acx);font-weight:700}
.editing .done{display:block;animation:pop .3s var(--ease)}
#escroll{flex:1;overflow-y:auto;overflow-x:hidden;padding:4px 12px 0;display:flex;flex-direction:column;-webkit-overflow-scrolling:touch}
.sheet{position:relative;flex:1 0 auto;border-radius:22px;background:var(--pbg);color:var(--pink);padding:calc(var(--L)*.5) 0 190px;transform-origin:left center;transition:background .35s,color .35s}
.sheet.fn{animation:fnext .45s var(--ease)}
.sheet.fq{animation:fprev .45s var(--ease)}
.sheet[data-paper=cream]{--pbg:#f0e6cc;--pink:#2b2418;--pmu:#8b7d5e;--pr:rgba(95,70,20,.22)}
.sheet[data-paper=white]{--pbg:#fbfbf8;--pink:#1b1b1b;--pmu:#8d8d88;--pr:rgba(0,0,0,.12)}
.sheet[data-paper=dark]{--pbg:#141414;--pink:#ececea;--pmu:#7d7d79;--pr:rgba(255,255,255,.1)}
.tt{display:block;width:100%;height:calc(var(--L)*2);padding:0 20px;font:700 calc(var(--fs)*1.5)/calc(var(--L)*2) var(--nf);color:var(--pink);outline:0}
.tt::placeholder{color:var(--pmu);opacity:.7}
.ed{position:relative;padding:0 20px;min-height:calc(var(--L)*14);font-family:var(--nf);font-size:var(--fs);line-height:var(--L);outline:0;word-break:break-word;caret-color:var(--ac);-webkit-user-select:text;user-select:text}
.sheet[data-rule=lines] .ed{background:linear-gradient(transparent calc(var(--L) - 1px),var(--pr) calc(var(--L) - 1px)) 0 0/100% var(--L)}
.sheet[data-rule=grid] .ed{background:linear-gradient(transparent calc(var(--L) - 1px),var(--pr) calc(var(--L) - 1px)) 0 0/100% var(--L),linear-gradient(90deg,transparent calc(var(--L) - 1px),var(--pr) calc(var(--L) - 1px)) 0 0/var(--L) var(--L)}
.sheet[data-rule=dots] .ed{background:radial-gradient(circle at calc(100% - 1px) calc(100% - 1px),var(--pmu) 1.3px,transparent 1.8px) 0 0/var(--L) var(--L)}
.ed.empty::before{content:"Начните писать";position:absolute;left:20px;top:0;color:var(--pmu);opacity:.7;pointer-events:none}
.ed h2{font-size:1.45em;line-height:var(--L);margin:0;font-weight:700}
.ed ul,.ed ol{margin:0;padding-left:30px}
.ed li::marker{color:var(--pmu)}
.ed mark{background:rgba(242,184,0,.5);color:inherit;border-radius:3px}
.ed .td{position:relative;padding-left:42px;transition:color .3s}
.ed .td::before{content:"";position:absolute;left:8px;top:calc((var(--L) - 24px)/2);width:24px;height:24px;border-radius:8px;border:2.5px solid var(--pmu);transition:background-color .25s,border-color .25s}
.ed .td[data-d="1"]{color:var(--pmu);text-decoration:line-through;text-decoration-color:currentColor;text-decoration-thickness:2px;animation:strike .4s var(--ease)}
.ed .td[data-d="1"]::before{border-color:var(--ac);background:var(--ac) url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 24 24' fill='none' stroke='%231a1400' stroke-width='3.6' stroke-linecap='round' stroke-linejoin='round'%3E%3Cpath d='M5 12.5l4.5 4.5L19 7'/%3E%3C/svg%3E") center/16px no-repeat;animation:pop .32s var(--ease)}
#cv{position:absolute;left:0;top:0;pointer-events:none;border-radius:22px;z-index:2}
.drawing #cv{pointer-events:auto;touch-action:none}
.aus{padding:12px 20px 0;display:flex;flex-direction:column;gap:8px}
.au{display:flex;align-items:center;gap:12px;height:54px;padding:0 8px 0 6px;border-radius:18px;background:rgba(127,127,127,.14);position:relative;overflow:hidden}
.au .pl{width:42px;height:42px;border-radius:50%;background:var(--ac);color:var(--acx);display:grid;place-items:center;flex:none}
.au .pl svg{width:20px;height:20px}
.au .wv{flex:1;height:30px;display:flex;align-items:center;gap:2px;position:relative}
.au .wv s{flex:1;max-width:4px;border-radius:2px;background:var(--pmu);opacity:.5;transition:background .2s,opacity .2s}
.au .wv s.p{background:var(--ac);opacity:1}
.au small{font-size:13px;color:var(--pmu);font-variant-numeric:tabular-nums}
.au .rm{width:34px;height:34px;display:grid;place-items:center;color:var(--pmu)}
.au .rm svg{width:18px;height:18px}
.tools,.dtools{position:absolute;left:12px;right:12px;bottom:calc(10px + var(--kb));z-index:6;display:flex;justify-content:space-between;align-items:center;background:rgba(22,22,22,.94);backdrop-filter:blur(16px);-webkit-backdrop-filter:blur(16px);border:1px solid var(--ln);border-radius:30px;padding:6px 8px;transition:transform .35s var(--ease),opacity .25s}
.dtools{display:none}
.drawing .tools{display:none}
.drawing .dtools{display:flex;animation:rise .3s var(--ease)}
.tools button,.dtools button{width:56px;height:52px;display:grid;place-items:center;border-radius:20px;transition:color .2s,background .2s,transform .15s var(--ease)}
.tools button:active,.dtools button:active{transform:scale(.9)}
.tools button svg,.dtools button svg{width:28px;height:28px}
.tools button.on,.dtools button.on{color:var(--ac);background:var(--s2)}
.dtools .dot{width:30px;height:30px;border-radius:50%;border:3px solid transparent;background-clip:padding-box;transition:transform .2s var(--ease)}
.dtools button.cl{width:44px}
.dtools button.cl.on{background:none;transform:scale(1.15)}
.dtools button.cl.on .dot{border-color:var(--ac)}
.dtools .sz i{display:block;border-radius:50%;background:currentColor}
.fp,.pg{position:absolute;bottom:calc(84px + var(--kb));z-index:6;transition:transform .3s var(--ease),opacity .2s}
.fp{left:12px;right:12px;background:rgba(22,22,22,.96);backdrop-filter:blur(16px);-webkit-backdrop-filter:blur(16px);border:1px solid var(--ln);border-radius:26px;padding:6px;display:grid;grid-template-columns:repeat(5,1fr);transform:translateY(14px) scale(.97);opacity:0;pointer-events:none}
.fp.on{transform:none;opacity:1;pointer-events:auto}
.fp button{height:50px;display:grid;place-items:center;border-radius:18px;transition:color .2s,background .2s}
.fp button:active{background:var(--s3)}
.fp button.on{color:var(--ac);background:var(--s2)}
.pg{left:50%;transform:translateX(-50%);display:flex;align-items:center;background:rgba(22,22,22,.94);border:1px solid var(--ln);border-radius:99px;height:46px;padding:0 4px;backdrop-filter:blur(16px);-webkit-backdrop-filter:blur(16px)}
.pg button{width:44px;height:38px;display:grid;place-items:center;color:var(--tx);transition:opacity .2s}
.pg button:disabled{opacity:.25}
.pg button svg{width:22px;height:22px}
.pg b{padding:0 8px;font-size:15px;font-variant-numeric:tabular-nums;min-width:64px;text-align:center}
.fpopen .pg,.drawing .pg{opacity:0;pointer-events:none}
.sb{position:fixed;z-index:30;display:flex;background:#242424;border-radius:18px;padding:4px;box-shadow:0 12px 30px #000a;opacity:0;pointer-events:none;transform:translateY(6px) scale(.96);transition:opacity .15s,transform .2s var(--ease)}
.sb.on{opacity:1;pointer-events:auto;transform:none}
.sb button{width:44px;height:44px;display:grid;place-items:center;border-radius:14px}
.sb button svg{width:23px;height:23px}
.sb button.on{color:var(--ac)}
.sb button:active{background:var(--s3)}
.fx{position:absolute;right:16px;bottom:calc(16px + env(safe-area-inset-bottom,0px));z-index:7;display:none}
.focus .fx{display:grid}
.focus .etop,.focus .tools,.focus .pg,.focus .fp{opacity:0;pointer-events:none;transform:translateY(-10px)}
.focus .tools,.focus .pg,.focus .fp{transform:translateY(20px)}
</style>
<style id="vx">
html,body,.screen{background-color:var(--bg);background-image:var(--wp,none);background-size:var(--wps,64px)}
.bar{background:linear-gradient(transparent,var(--bg) 55%)}
.shelf{background:linear-gradient(var(--bg) 72%,transparent)}
.drawer,.sh{background:var(--s1)}
.tools,.dtools,.fp,.pg{background:var(--glass)}
#toast{background:var(--s3)}.mp{background:var(--s2)}
::selection{background:var(--sel,rgba(242,184,0,.35))}
svg{width:var(--isz);height:var(--isz);stroke-width:var(--sw)}
.tools button svg,.dtools button svg{width:calc(var(--isz) + 2px);height:calc(var(--isz) + 2px)}
.cbtn{width:var(--cb);height:var(--cb)}
.card{border-radius:var(--r);padding:var(--pd) 18px}
.sheet{border-radius:var(--r);--pbg:#f0e6cc;--pink:#2b2418;--pmu:#8b7d5e;--pr:rgba(95,70,20,.22)}
.btn,.in{border-radius:calc(var(--r)*.7)}
.sheet .ed,.sheet .tt{color:var(--ntx,var(--pink))}
.sheet .ed{font-weight:var(--fw,400)}
#sb{display:none!important}
.tools{overflow:visible}
.tools::before{content:"";position:absolute;top:-9px;left:50%;width:38px;height:4px;border-radius:4px;background:var(--s3);transform:translateX(-50%)}
#vst{position:fixed;top:calc(env(safe-area-inset-top,0px) + 3px);right:14px;z-index:5;font-size:11px;color:var(--mu);opacity:.6;pointer-events:none}
.setr input[type=color]{width:46px;height:34px;border:0;padding:0;background:none}
.setr .sw button{width:34px;height:34px}
.setr .btn,.setr[data-i] .btn{min-width:44px;padding:0 8px}
</style>
<style id="v3">
:root{--glass:rgba(22,22,22,.94)}
.fp{max-height:46vh;overflow-y:auto}
.pinov{position:fixed;inset:0;z-index:300;background:var(--bg);display:flex;flex-direction:column;align-items:center;padding:calc(env(safe-area-inset-top,0px) + 14px) 20px calc(env(safe-area-inset-bottom,0px) + 24px);opacity:0;transition:opacity .25s}
.pinov.on{opacity:1}.pinov>.cbtn{align-self:flex-start}
.pt{font-size:24px;font-weight:700;margin-top:6vh;text-align:center}.ps{color:var(--mu);min-height:22px;margin:8px 0 22px;text-align:center;font-size:15px}
.pd{display:flex;gap:18px;margin-bottom:4vh}.pd i{width:16px;height:16px;border-radius:50%;border:2px solid var(--mu);transition:.15s}.pd i.on{background:var(--ac);border-color:var(--ac);transform:scale(1.15)}
.pk{display:grid;grid-template-columns:repeat(3,1fr);gap:14px 22px;width:min(300px,90%);margin-top:auto}
.pk button{height:68px;border-radius:50%;background:var(--s1);font-size:28px;font-weight:600;color:var(--tx)}.pk button:active{background:var(--s3)}
.vw{position:fixed;inset:0;z-index:20;background-color:var(--bg);background-image:var(--wp,none);background-size:var(--wps,64px);display:flex;flex-direction:column;transform:translateX(30px);opacity:0;transition:.25s}
.vw.on{transform:none;opacity:1}
.vh{display:flex;align-items:center;justify-content:space-between;padding:calc(env(safe-area-inset-top,0px) + 10px) 14px 8px}.vh h2{margin:0;font-size:22px}
.vb{flex:1;overflow-y:auto;padding:6px 16px calc(env(safe-area-inset-bottom,0px) + 28px)}
.wg{background:var(--s1);border-radius:var(--r);padding:14px;margin-bottom:10px}.wg b{display:block;font-size:22px}.wg small,.mu{color:var(--mu);font-size:13px}
.g2{display:grid;grid-template-columns:1fr 1fr;gap:10px}
.fcs{display:flex;gap:12px;overflow-x:auto;scroll-snap-type:x mandatory;padding-bottom:10px;margin-bottom:6px}
.fcd{flex:0 0 250px;height:150px;border-radius:22px;padding:16px;color:#fff;display:flex;flex-direction:column;justify-content:space-between;text-align:left;scroll-snap-align:start}
.ch{width:100%;height:auto;stroke-width:initial}
.li{display:flex;align-items:center;gap:10px;padding:11px 0;border-bottom:1px solid var(--ln)}.li>span{flex:1;min-width:0}.li>.r{flex:0 0 auto;text-align:right}
.pg2{height:8px;border-radius:8px;background:var(--s3);overflow:hidden;margin:8px 0}.pg2 i{display:block;height:100%;background:var(--ac)}
.cd{display:grid;grid-template-columns:repeat(7,1fr);gap:6px}.cd small{text-align:center;color:var(--mu);font-size:12px}
.cd button{aspect-ratio:1;border-radius:14px;background:var(--s1);font-weight:600;position:relative}.cd button.td{box-shadow:inset 0 0 0 2px var(--ac)}
.cd button.ev{background:color-mix(in srgb,var(--ev) 32%,var(--s1))}.cd button.sl{background:var(--ac);color:var(--acx)}
.cd button i{position:absolute;bottom:5px;left:0;right:0;display:flex;gap:3px;justify-content:center}.cd i b{width:5px;height:5px;border-radius:50%;display:block}
.cm{display:grid;grid-template-columns:1fr 1fr;gap:10px}.cm button{display:flex;flex-direction:column;align-items:center;gap:8px;padding:16px 8px;border-radius:24px;background:var(--s2);font-weight:600}
.kp{display:grid;grid-template-columns:repeat(5,1fr);gap:8px}.kp button{height:54px;border-radius:18px;background:var(--s1);font-size:19px}.kp .op{background:var(--s3)}.kp .eq{background:var(--ac);color:var(--acx)}
.wpb.on{border-color:var(--ac);color:var(--ac)}
</style>
</head>
<body>
<!--1 Главный экран: три кнопки сверху, поиск и две кнопки снизу-->
<div id="app">
  <section class="screen" id="home">
    <header class="top">
      <button class="cbtn" id="bmenu" aria-label="Папки и меню" data-i="panel"></button>
      <div class="seg" id="seg"><i></i><button data-v="notes" class="on">Заметки</button><button data-v="tasks">Задачи</button></div>
      <button class="cbtn" id="blay" aria-label="Список или плитки" data-i="rows"></button>
    </header>
    <div id="hscroll"><h1 id="htitle">Все заметки</h1><div id="hlist"></div></div>
    <div class="bar">
      <label class="pill"><span id="qi" data-i="search"></span><input id="q" placeholder="Поиск" enterkeyhint="search" autocomplete="off"></label>
      <button class="cbtn" id="bmic" aria-label="Надиктовать заметку" data-i="mic"></button>
      <button class="cbtn pri" id="bnew" aria-label="Новая заметка" data-i="pencil"></button>
    </div>
  </section>

<!--2 Редактор: лист, нижняя панель инструментов-->
  <section class="screen" id="ed" inert>
    <header class="etop">
      <button class="cbtn" id="eback" aria-label="Назад" data-i="back"></button>
      <span class="sp"></span>
      <div class="ur"><button id="eundo" aria-label="Отменить" data-i="undo"></button><button id="eredo" aria-label="Вернуть" data-i="redo"></button></div>
      <button class="done" id="edone">Готово</button>
      <button class="cbtn" id="emore" aria-label="Ещё" data-i="more"></button>
    </header>
    <div id="escroll">
      <div class="sheet" id="sheet" data-paper="cream" data-rule="lines">
        <input class="tt" id="tt" placeholder="Название" autocomplete="off" enterkeyhint="next">
        <div class="ed empty" id="e" contenteditable="false" spellcheck="false"></div>
        <div class="aus" id="aus"></div>
        <canvas id="cv"></canvas>
      </div>
    </div>
    <div class="pg" id="pg"><button id="pprev" aria-label="Предыдущая страница" data-i="back"></button><b id="pnum">1 / 1</b><button id="pnext" aria-label="Следующая страница" data-i="chev"></button></div>
    <div class="fp" id="fp">
      <button data-c="bold" aria-label="Жирный" data-i="bold"></button>
      <button data-c="italic" aria-label="Курсив" data-i="italic"></button>
      <button data-c="underline" aria-label="Подчёркнутый" data-i="underline"></button>
      <button data-c="strike" aria-label="Зачёркнутый" data-i="strike"></button>
      <button data-c="mark" aria-label="Маркер" data-i="mark"></button>
      <button data-c="h" aria-label="Заголовок" data-i="heading"></button>
      <button data-c="ul" aria-label="Список" data-i="list"></button>
      <button data-c="ol" aria-label="Нумерованный список" data-i="olist"></button>
      <button data-c="date" aria-label="Вставить дату" data-i="calendar"></button>
      <button data-c="time" aria-label="Вставить время" data-i="clock"></button>
    </div>
    <div class="tools" id="tools">
      <button id="tfmt" aria-label="Формат" data-i="aa"></button>
      <button id="ttodo" aria-label="Чек-лист" data-i="todo"></button>
      <button id="tdraw" aria-label="Рисовать" data-i="draw"></button>
      <button id="tmic" aria-label="Голос" data-i="mic"></button>
      <button id="tpage" aria-label="Страница и бумага" data-i="paper"></button>
    </div>
    <div class="dtools" id="dtools">
      <button class="cl on" data-col="auto" aria-label="Чернила"><span class="dot" style="background:#9a9a9a"></span></button>
      <button class="cl" data-col="#f2b800" aria-label="Жёлтый"><span class="dot" style="background:#f2b800"></span></button>
      <button class="cl" data-col="#e5483b" aria-label="Красный"><span class="dot" style="background:#e5483b"></span></button>
      <button class="cl" data-col="#3a7bd5" aria-label="Синий"><span class="dot" style="background:#3a7bd5"></span></button>
      <button id="dsz" aria-label="Толщина"><span class="sz"><i></i></span></button>
      <button id="der" aria-label="Ластик" data-i="eraser"></button>
      <button id="dun" aria-label="Отменить штрих" data-i="undo"></button>
      <button id="ddone" aria-label="Готово" data-i="check"></button>
    </div>
    <div class="sb" id="sb">
      <button data-c="bold" aria-label="Жирный" data-i="bold"></button>
      <button data-c="italic" aria-label="Курсив" data-i="italic"></button>
      <button data-c="underline" aria-label="Подчёркнутый" data-i="underline"></button>
      <button data-c="strike" aria-label="Зачёркнутый" data-i="strike"></button>
      <button data-c="mark" aria-label="Маркер" data-i="mark"></button>
      <button data-c="h" aria-label="Заголовок" data-i="heading"></button>
      <button data-c="td" aria-label="Сделать задачей" data-i="todo"></button>
    </div>
    <button class="cbtn fx" id="fx" aria-label="Выйти из режима фокуса" data-i="focus"></button>
  </section>
</div>
<div id="layer"></div>
<div id="toast"></div>

<script>
//1 Помощники//
const $=(s,r=document)=>r.querySelector(s),$$=(s,r=document)=>[...r.querySelectorAll(s)];
const el=(t,c,h)=>{const e=document.createElement(t);if(c)e.className=c;if(h!=null)e.innerHTML=h;return e};
const esc=s=>String(s==null?'':s).replace(/[&<>"]/g,c=>({'&':'&amp;','<':'&lt;','>':'&gt;','"':'&quot;'}[c]));
const uid=()=>Date.now().toString(36)+Math.random().toString(36).slice(2,6);
const wait=ms=>new Promise(r=>setTimeout(r,ms));
const clamp=(v,a,b)=>Math.max(a,Math.min(b,v));
const txt=h=>{const d=document.createElement('div');d.innerHTML=String(h||'').replace(/<\/(div|h2|h3|li|p)>|<br\s*\/?>/gi,'$& ');return (d.textContent||'').replace(/\s+/g,' ').trim()};
const LS={g(k){try{return localStorage.getItem(k)}catch(e){return null}},s(k,v){try{localStorage.setItem(k,v);return true}catch(e){return false}}};
const buzz=n=>{if(D&&D.set.vib&&navigator.vibrate){try{navigator.vibrate(n||8)}catch(e){}}};

//2 Иконки: толстые линии, крупный размер//
const P={
back:"M15 18l-6-6 6-6",chev:"M9 18l6-6-6-6",panel:"M3 5h18v14H3zM9 5v14",rows:"M4 4h16v7H4zM4 13h16v7H4z",cols:"M4 4h7v7H4zM13 4h7v7h-7zM4 13h7v7H4zM13 13h7v7h-7z",
search:"M21 21l-4.3-4.3M11 3a8 8 0 100 16 8 8 0 000-16z",plus:"M5 12h14M12 5v14",pencil:"M4 20h4L19 9l-4-4L4 16zM13 7l4 4",
mic:"M12 2a3 3 0 00-3 3v7a3 3 0 006 0V5a3 3 0 00-3-3zM19 10v2a7 7 0 01-14 0v-2M12 19v3",
lock:"M5 11h14v10H5zM8 11V7a4 4 0 018 0v4",unlock:"M5 11h14v10H5zM8 11V7a4 4 0 017.5-1",
folder:"M3 7a2 2 0 012-2h4l2 2h8a2 2 0 012 2v8a2 2 0 01-2 2H5a2 2 0 01-2-2z",
inbox:"M3 13l3-8h12l3 8v6H3zM3 13h5l1 3h6l1-3h5",doc:"M14 2H6a2 2 0 00-2 2v16a2 2 0 002 2h12a2 2 0 002-2V8zM14 2v6h6M8 13h8M8 17h6",
trash:"M3 6h18M19 6l-1 14a2 2 0 01-2 2H8a2 2 0 01-2-2L5 6M8 6V4a2 2 0 012-2h4a2 2 0 012 2v2",
star:"M12 2l3.1 6.3 6.9 1-5 4.9 1.2 6.9L12 17.8 5.8 21l1.2-6.9-5-4.9 6.9-1z",
pin:"M12 17v5M9 10.8a2 2 0 01-1.1 1.8l-1.8.9A2 2 0 005 15.2V17h14v-1.8a2 2 0 00-1.1-1.8l-1.8-.9a2 2 0 01-1.1-1.8V7a1 1 0 011-1 2 2 0 000-4H8a2 2 0 000 4 1 1 0 011 1z",
check:"M5 12.5l4.5 4.5L19 7",todo:"M3 4h7v7H3zM4.8 7.6l1.5 1.5 2.4-2.8M14 7h7M3 14h7v7H3zM14 18h7",
more:'<circle cx="12" cy="5" r="2" fill="currentColor" stroke="none"/><circle cx="12" cy="12" r="2" fill="currentColor" stroke="none"/><circle cx="12" cy="19" r="2" fill="currentColor" stroke="none"/>',
aa:"M3 19l5-13 5 13M5 14h6M15 19l3.5-9L22 19M16.2 16h4.6",paper:"M5 3h14v18H5zM5 9h14M5 15h14",
share:"M4 12v7a2 2 0 002 2h12a2 2 0 002-2v-7M16 6l-4-4-4 4M12 2v14",cover:"M3 4h18v16H3zM3 15l5-5 4 4 3-3 6 6",
rename:"M12 20h9M16.5 3.5a2.1 2.1 0 013 3L7 19l-4 1 1-4z",move:"M3 7a2 2 0 012-2h4l2 2h8a2 2 0 012 2v8a2 2 0 01-2 2H5a2 2 0 01-2-2zM9 13h6M13 11l2 2-2 2",
restore:"M3 12a9 9 0 109-9 9 9 0 00-6.7 3L3 8M3 3v5h5",focus:"M3 8V5a2 2 0 012-2h3M16 3h3a2 2 0 012 2v3M21 16v3a2 2 0 01-2 2h-3M8 21H5a2 2 0 01-2-2v-3",
undo:"M9 14L4 9l5-5M4 9h10.5a5.5 5.5 0 010 11H11",redo:"M15 14l5-5-5-5M20 9H9.5a5.5 5.5 0 000 11H13",x:"M18 6L6 18M6 6l12 12",
sliders:"M4 21v-7M4 10V3M12 21v-9M12 8V3M20 21v-5M20 12V3M1 14h6M9 8h6M17 16h6",
bold:"M6 12h9a4 4 0 010 8H7a1 1 0 01-1-1V5a1 1 0 011-1h7a4 4 0 010 8",italic:"M19 4h-9M14 20H5M15 4L9 20",underline:"M6 4v6a6 6 0 0012 0V4M4 20h16",
strike:"M16 4H9a3 3 0 00-2.83 4M14 12a4 4 0 010 8H6M4 12h16",mark:"M9 11l-6 6v3h9l3-3M22 12l-4.6 4.6a2 2 0 01-2.8 0l-5.2-5.2a2 2 0 010-2.8L14 4",
heading:"M6 4v16M18 4v16M6 12h12",list:"M8 6h13M8 12h13M8 18h13M3 6h.01M3 12h.01M3 18h.01",olist:"M10 6h11M10 12h11M10 18h11M4 6h1v4M4 10h2M6 18H4c0-1 2-2 2-3s-1-1.5-2-1",
calendar:"M3 5h18v16H3zM3 10h18M8 2v4M16 2v4",clock:"M12 3a9 9 0 100 18 9 9 0 000-18zM12 7v5l3 2",
eraser:"M7 21l-4.3-4.3c-1-1-1-2.5 0-3.4l9.6-9.6c1-1 2.5-1 3.4 0l5.6 5.6c1 1 1 2.5 0 3.4L13 21M22 21H7M5 11l9 9",
draw:"M17 3a2.85 2.83 0 114 4L7.5 20.5 2 22l1.5-5.5z",play:"M7 4l13 8-13 8z",pause:"M8 5v14M16 5v14",
stop:'<rect x="6" y="6" width="12" height="12" rx="2.5" fill="currentColor" stroke="none"/>'};
const ic=(n,s)=>{const d=P[n]||'';return '<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.4" stroke-linecap="round" stroke-linejoin="round"'+(s?' style="width:'+s+'px;height:'+s+'px"':'')+'>'+(d[0]=='<'?d:'<path d="'+d+'"/>')+'</svg>'};
const icons=r=>$$('[data-i]',r).forEach(e=>{if(!e.querySelector('svg'))e.insertAdjacentHTML('afterbegin',ic(e.dataset.i))});

//3 Данные и сохранение//
const CC=['#2f3136','#27406b','#21473a','#6a2a38','#9a7414','#98512f','#4a3558','#a89873'];
const CP=[['plain','Гладкая'],['lines','Линии'],['grid','Клетка'],['dots','Точки']];
const rndCv=()=>({c:CC[Math.floor(Math.random()*CC.length)],p:CP[Math.floor(Math.random()*CP.length)][0]});
const coverHTML=(cv,title,mini,big)=>'<div class="cover'+(mini?' mini':'')+(big?' big':'')+'" data-p="'+cv.p+'" style="--c:'+cv.c+'"><b>'+(mini?'':esc(title||''))+'</b></div>';
const PAPERS={cream:'#f0e6cc',white:'#fbfbf8',dark:'#141414'};
const mkPage=()=>({id:uid(),h:'<div><br></div>',paper:D.set.paper,rule:D.set.rule,dr:0,au:[]});
let KEY=null,D=null;
function loadData(){let d=null;try{d=JSON.parse(LS.g('vibe:v2')||LS.g('kor:v1')||'null')}catch(e){}
 if(!d||!d.notes){d={notes:[],folders:[],tasks:[],vault:null,set:{}};}
 d.set=Object.assign({font:'onest',fs:17,paper:'cream',rule:'lines',anim:true,vib:true},d.set||{});
 d.folders=d.folders||[];d.tasks=d.tasks||[];
 D=d;
 if(!d.notes.length&&!LS.g('kor:seen')){
  const p=mkPage();p.h='<h2>Тихие заметки</h2><div>Нажмите на текст, чтобы писать. Пока не нажали, клавиатура не мешает.</div><div class="td">Отметьте эту задачу</div><div class="td">Выделите слово: появится быстрая панель</div><div>Зажмите заметку в списке: откроется меню. Потяните её дальше, чтобы положить в папку.</div>';
  d.notes.push({id:uid(),t:'Добро пожаловать',pg:[p],ci:0,pin:0,fav:0,del:0,fo:'',cv:null,lk:0,enc:null,up:Date.now(),cr:Date.now()});
  LS.s('kor:seen','1');}
 const lim=Date.now()-30*864e5;d.notes=d.notes.filter(n=>!(n.del&&n.del<lim));
}
let svT=0;
function save(){vxSt('Сохраняется…');clearTimeout(svT);svT=setTimeout(persist,250)}
async function persist(){
 try{
  const notes=[];
  for(const n of D.notes){
   if(n.lk){if(KEY){n.enc=await enc({t:n.t,pg:n.pg})}
    notes.push(Object.assign({},n,{t:D.set.lkt===false?'':n.t,pg:[]}));}
   else notes.push(n);}
  await vxStore(Object.assign({},D,{notes,ver:2,ts:Date.now()}));
 }catch(e){vxSt('Ошибка сохранения',1);toast('Не удалось сохранить')}}

//4 Шифрование для заметок под паролем//
const te=new TextEncoder(),tdc=new TextDecoder();
const b64=a=>{a=new Uint8Array(a);let s='';for(let i=0;i<a.length;i+=8192)s+=String.fromCharCode.apply(null,a.subarray(i,i+8192));return btoa(s)};
const unb=s=>Uint8Array.from(atob(s),c=>c.charCodeAt(0));
async function derive(pw,salt){const k=await crypto.subtle.importKey('raw',te.encode(pw),'PBKDF2',false,['deriveKey']);return crypto.subtle.deriveKey({name:'PBKDF2',salt,iterations:150000,hash:'SHA-256'},k,{name:'AES-GCM',length:256},false,['encrypt','decrypt'])}
async function enc(o){const iv=crypto.getRandomValues(new Uint8Array(12));const ct=await crypto.subtle.encrypt({name:'AES-GCM',iv},KEY,te.encode(JSON.stringify(o)));return {iv:b64(iv),ct:b64(ct)}}
async function dec(e,k){return JSON.parse(tdc.decode(await crypto.subtle.decrypt({name:'AES-GCM',iv:unb(e.iv)},k||KEY,unb(e.ct))))}
async function setupVault(pw){const salt=crypto.getRandomValues(new Uint8Array(16));KEY=await derive(pw,salt);D.vault={salt:b64(salt),chk:await enc({ok:1})};await persist()}
async function tryUnlock(pw){if(!D.vault)return false;try{const k=await derive(pw,unb(D.vault.salt));await dec(D.vault.chk,k);KEY=k;
 for(const n of D.notes){if(n.lk&&n.enc){try{const o=await dec(n.enc);n.t=o.t;n.pg=o.pg}catch(e){}}}return true}catch(e){return false}}
async function relock(){if(!KEY)return;if(ED.n&&ED.n.lk)closeEditor();await persist();KEY=null;D.notes.forEach(n=>{if(n.lk){if(D.set.lkt===false)n.t='';n.pg=[]}});if(fById(F)&&fById(F).lk)F='all';render()}
async function needKey(){
 if(KEY)return true;
 if(!D.vault){if(!crypto||!crypto.subtle){toast('Шифрование недоступно в этом браузере');return false}
  const pw=await askPass({title:'Придумайте код из 4 цифр',hint:'Он защитит все заметки под замком. Восстановить его нельзя.',confirm:1,ok:'Создать'});
  if(!pw)return false;await setupVault(pw);toast('Пароль создан');return true}
 const pw=await askPass({title:'Введите код-пароль',verify:tryUnlock,ok:'Открыть'});
 return !!pw}

//5 Хранилище рисунков и аудио//
let _db=null;const mem=new Map();
const idb=()=>_db||(_db=new Promise((res,rej)=>{try{const r=indexedDB.open('koreshok',1);r.onupgradeneeded=()=>r.result.createObjectStore('b');r.onsuccess=()=>res(r.result);r.onerror=()=>rej(r.error)}catch(e){rej(e)}}));
async function bget(k){try{const d=await idb();return await new Promise((res,rej)=>{const q=d.transaction('b').objectStore('b').get(k);q.onsuccess=()=>res(q.result);q.onerror=()=>rej(q.error)})}catch(e){return mem.get(k)}}
async function bset(k,v){mem.set(k,v);try{const d=await idb();await new Promise((res,rej)=>{const t=d.transaction('b','readwrite');t.objectStore('b').put(v,k);t.oncomplete=res;t.onerror=()=>rej(t.error)})}catch(e){}}
async function bdel(k){mem.delete(k);try{const d=await idb();d.transaction('b','readwrite').objectStore('b').delete(k)}catch(e){}}

//6 Общие окна: шторка, тосты, ввод текста и пароля//
const layer=$('#layer');let tT=0;
function toast(t,o){const e=$('#toast');e.innerHTML='<span>'+esc(t)+'</span>'+(o&&o.act?'<button>'+esc(o.act)+'</button>':'');if(o&&o.act)e.querySelector('button').onclick=()=>{e.classList.remove('on');o.f()};e.classList.add('on');clearTimeout(tT);tT=setTimeout(()=>e.classList.remove('on'),o&&o.act?4500:2200)}
function sheet(html,onClose){
 const sc=el('div','scrim'),s=el('div','sh','<div class="hd"></div>'+html);layer.append(sc,s);icons(s);
 let closed=0;const api={el:s,close(){if(closed)return;closed=1;sc.classList.remove('on');s.classList.remove('on');setTimeout(()=>{sc.remove();s.remove()},400);if(onClose)onClose()}};
 sc.onclick=api.close;requestAnimationFrame(()=>requestAnimationFrame(()=>{sc.classList.add('on');s.classList.add('on')}));
 const hd=$('.hd',s);let y0=null;
 hd.addEventListener('pointerdown',e=>{y0=e.clientY;hd.setPointerCapture(e.pointerId);s.style.transition='none'});
 hd.addEventListener('pointermove',e=>{if(y0!=null)s.style.transform='translateY('+Math.max(0,e.clientY-y0)+'px)'});
 const up=e=>{if(y0==null)return;const dy=e.clientY-y0;y0=null;s.style.transition='';s.style.transform='';if(dy>90)api.close()};
 hd.addEventListener('pointerup',up);hd.addEventListener('pointercancel',up);
 return api}
function askText(o){return new Promise(res=>{let done=0;const fin=v=>{if(!done){done=1;res(v)}};
 const sh=sheet('<h3>'+esc(o.title)+'</h3><input class="in" id="ti" value="'+esc(o.value||'')+'" placeholder="'+esc(o.ph||'')+'" autocomplete="off"><div class="row">'+(o.extra?'<button class="btn dg" data-x>'+esc(o.extra)+'</button>':'')+'<button class="btn pri" data-ok>'+esc(o.ok||'Готово')+'</button></div>',()=>fin(null));
 const i=$('#ti',sh.el),go=()=>{const v=i.value.trim();if(!v&&!o.empty){i.classList.remove('shake');void i.offsetWidth;i.classList.add('shake');return}fin(v);sh.close()};
 $('[data-ok]',sh.el).onclick=go;i.onkeydown=e=>{if(e.key=='Enter')go()};
 if(o.extra)$('[data-x]',sh.el).onclick=()=>{fin('\u0000x');sh.close()};
 setTimeout(()=>{i.focus();i.select()},380)})}
function askPass(o){return new Promise(res=>{let done=0;const fin=v=>{if(!done){done=1;res(v)}};
 const sh=sheet('<h3>'+esc(o.title)+'</h3>'+(o.hint?'<p class="sub">'+esc(o.hint)+'</p>':'')+'<input class="in" id="p1" type="password" placeholder="Пароль" autocomplete="off">'+(o.confirm?'<input class="in" id="p2" type="password" placeholder="Ещё раз" autocomplete="off">':'')+'<div class="hint" id="ph"></div><button class="btn pri" style="width:100%" data-ok>'+esc(o.ok||'Готово')+'</button>',()=>fin(null));
 const p1=$('#p1',sh.el),p2=$('#p2',sh.el),ph=$('#ph',sh.el);
 const bad=(m,t)=>{ph.textContent=m;t.classList.remove('shake');void t.offsetWidth;t.classList.add('shake');buzz([20,40,20])};
 const go=async()=>{const v=p1.value;if(v.length<4)return bad('Минимум 4 символа',p1);
  if(o.confirm&&p2.value!==v)return bad('Пароли не совпадают',p2);
  if(o.verify&&!(await o.verify(v)))return bad('Неверный пароль',p1);
  fin(v);sh.close()};
 $('[data-ok]',sh.el).onclick=go;[p1,p2].forEach(x=>x&&(x.onkeydown=e=>{if(e.key=='Enter')go()}));
 setTimeout(()=>p1.focus(),380)})}
function press(e,o){let t=0,s=null,fired=0;
 e.addEventListener('pointerdown',ev=>{s=[ev.clientX,ev.clientY];fired=0;if(o.long)t=setTimeout(()=>{fired=1;s=null;buzz(12);o.long(ev)},HOLD())});
 e.addEventListener('pointermove',ev=>{if(s&&Math.hypot(ev.clientX-s[0],ev.clientY-s[1])>10){clearTimeout(t);s=null}});
 e.addEventListener('pointerup',ev=>{clearTimeout(t);if(s&&o.tap){s=null;o.tap(ev)}s=null});
 ['pointercancel','pointerleave'].forEach(k=>e.addEventListener(k,()=>{clearTimeout(t);s=null}));
 e.addEventListener('contextmenu',ev=>ev.preventDefault())}

//7 Главный экран: списки, группы, карточки//
let V_='notes',F='all',LAY=LS.g('kor:lay')||'list',Q='',showDone=false;
const FN={all:'Все заметки',none:'Без категории',fav:'Избранное',locked:'Заблокированные',trash:'Недавно удалённые'};
const folderName=f=>FN[f]||(D.folders.find(x=>x.id==f)||{}).name||'Заметки';
const fById=id=>D.folders.find(x=>x.id==id);
const ntext=n=>n.pg.map(p=>txt(p.h)).join(' ');
const MON=['янв','фев','мар','апр','мая','июн','июл','авг','сен','окт','ноя','дек'];
function tm(ts){const d=new Date(ts),n=new Date();if(d.toDateString()==n.toDateString())return String(d.getHours()).padStart(2,'0')+':'+String(d.getMinutes()).padStart(2,'0');return d.getDate()+' '+MON[d.getMonth()]+(d.getFullYear()!=n.getFullYear()?' '+d.getFullYear():'')}
function grp(ts){const d=new Date(ts),n=new Date(),a=new Date(n.getFullYear(),n.getMonth(),n.getDate()).getTime(),df=Math.floor((a-new Date(d.getFullYear(),d.getMonth(),d.getDate()).getTime())/864e5);
 return df<=0?'Сегодня':df==1?'Вчера':df<=7?'За 7 дней':df<=30?'За 30 дней':'Раньше'}
function noteList(){
 let a=D.notes.filter(n=>F=='trash'?n.del:!n.del);
 if(F!='trash'){if(F=='locked')a=a.filter(n=>n.lk);else{const lf=fById(F)&&fById(F).lk;a=a.filter(n=>!n.lk||(lf&&KEY));
  if(F=='fav')a=a.filter(n=>n.fav);else if(F=='none')a=a.filter(n=>!n.fo||!fById(n.fo));else if(F!='all')a=a.filter(n=>n.fo==F)}}
 if(Q){const q=Q.toLowerCase();a=a.filter(n=>(n.t+' '+ntext(n)+' '+(n.tags||[]).map(t=>'#'+t).join(' ')).toLowerCase().includes(q))}
 return a.sort((x,y)=>(y.pin|0)-(x.pin|0)||(typeof vxCmp=='function'?vxCmp(x,y):y.up-x.up))}
const prCache=new Map();
function card(n,i){
 const hide=n.lk&&!KEY,fo=fById(n.fo),p=n.pg[0];
 let th='';
 if(n.cv)th='<div class="th cvr">'+coverHTML(n.cv,n.t,true)+'</div>';
 else if(p&&p.dr&&!n.lk)th='<div class="th" data-pid="'+p.id+'" style="background:'+PAPERS[p.paper]+'"><img alt=""></div>';
 return '<div class="card" data-id="'+n.id+'" style="--i:'+Math.min(i,14)+'"><div class="cb"><h3>'+esc(n.lk&&D.set.lkt===false?'Заблокированная заметка':(n.t||'Без названия'))+'</h3><p>'+esc(n.lk?'Содержимое скрыто':(ntext(n).slice(0,140)||'Пусто'))+'</p><div class="meta"><span class="fl">'+ic('folder')+esc(fo?fo.name:'Без категории')+'</span><span class="chip">'+tm(n.up)+'</span>'+(n.tags||[]).slice(0,2).map(t=>'<span class="chip">#'+esc(t)+'</span>').join('')+(n.pin?ic('pin'):'')+(n.fav?ic('star'):'')+(n.lk?ic('lock'):'')+'</div></div>'+th+'</div>'}
function emptyHTML(){
 if(Q)return '<div class="empty">Ничего не найдено</div>';
 if(F=='trash')return '<div class="empty">'+ic('trash')+'Корзина пуста</div>';
 if(F=='locked')return '<div class="empty">'+ic('lock')+'Здесь будут заметки под паролем.<br>Зажмите заметку и выберите «Запаролить».</div>';
 if(F=='fav')return '<div class="empty">'+ic('star')+'Здесь будут избранные заметки</div>';
 return '<div class="empty">'+ic('pencil')+'Пока пусто.<br>Нажмите на карандаш внизу.</div>'}
function renderNotes(reveal){
 const box=$('#hlist'),a=noteList();box.className=(LAY=='grid'?'grid':'')+(reveal?' reveal':'');
 if(!a.length){box.innerHTML=emptyHTML();return}
 const gs=[];a.forEach(n=>{const g=(F=='trash'||Q)?'':(n.pin?'Закреплённые':grp(n.up));let o=gs.find(x=>x.g==g);if(!o)gs.push(o={g,a:[]});o.a.push(n)});
 let i=0;box.innerHTML=gs.map(o=>(o.g?'<h2 class="g">'+o.g+'</h2>':'')+'<div class="cards">'+o.a.map(n=>card(n,i++)).join('')+'</div>').join('');
 $$('.th[data-pid]',box).forEach(async t=>{const pid=t.dataset.pid;let u=prCache.get(pid);if(!u){const b=await bget('dr:'+pid);if(!b)return;u=URL.createObjectURL(b);prCache.set(pid,u)}$('img',t).src=u})}
function taskRow(t,i){return '<div class="task'+(t.d?' d':'')+'" data-id="'+t.id+'" style="--i:'+Math.min(i,12)+'"><button class="ck" aria-label="Отметить"></button><span class="tl">'+esc(t.t)+'</span></div>'}
function renderTasks(){
 const box=$('#hlist');box.className='';const op=D.tasks.filter(t=>!t.d),dn=D.tasks.filter(t=>t.d).sort((a,b)=>b.d-a.d);
 if(!D.tasks.length){box.innerHTML='<div class="empty">'+ic('todo')+'Задач нет.<br>Напишите первую внизу.</div>';return}
 box.innerHTML=op.map(taskRow).join('')+(dn.length?'<button class="dh'+(showDone?' open':'')+'">'+ic('chev')+'Выполнено · '+dn.length+'</button><div class="dl'+(showDone?' open':'')+'">'+dn.map(taskRow).join('')+'</div>':'')}
function render(reveal){
 $('#htitle').textContent=V_=='tasks'?'Задачи':folderName(F);
 $('#blay').hidden=V_=='tasks';$('#blay').innerHTML=ic(LAY=='grid'?'rows':'cols');
 $('#bmic').hidden=V_=='tasks';$('#q').placeholder=V_=='tasks'?'Новая задача':'Поиск';$('#qi').innerHTML=ic(V_=='tasks'?'plus':'search');
 $('#bnew').innerHTML=ic(V_=='tasks'?'plus':'pencil');
 V_=='tasks'?renderTasks():renderNotes(reveal)}
function segPos(){const s=$('#seg'),b=$('button.on',s),i=$('i',s);i.style.width=b.offsetWidth+'px';i.style.transform='translateX('+b.offsetLeft+'px)'}
$('#seg').onclick=e=>{const b=e.target.closest('button');if(!b||b.dataset.v==V_)return;V_=b.dataset.v;$$('#seg button').forEach(x=>x.classList.toggle('on',x==b));segPos();buzz(6);Q='';$('#q').value='';
 const h=$('#hscroll');h.classList.remove('swap');void h.offsetWidth;h.classList.add('swap');h.scrollTop=0;render()};
$('#blay').onclick=()=>{LAY=LAY=='grid'?'list':'grid';LS.s('kor:lay',LAY);render()};
let qT=0;$('#q').oninput=e=>{if(V_=='tasks')return;clearTimeout(qT);qT=setTimeout(()=>{Q=e.target.value.trim();render()},120)};
$('#q').onkeydown=e=>{if(e.key!='Enter')return;
 if(V_=='tasks'){const v=e.target.value.trim();if(!v)return;D.tasks.unshift({id:uid(),t:v,d:0,up:Date.now()});e.target.value='';save();render();buzz(8)}else e.target.blur()};
$('#bnew').onclick=()=>{if(V_!='tasks'&&D.set.pen!='note'){createMenu();return}if(V_=='tasks'){const q=$('#q');const v=q.value.trim();if(v){D.tasks.unshift({id:uid(),t:v,d:0,up:Date.now()});q.value='';save();render();buzz(8)}else q.focus()}else newNote()};
$('#bmic').onclick=()=>{newNote(null,1);setTimeout(()=>openVoice('dict'),420)};

//8 Задачи: линия зачёркивания рисуется слева направо//
let rT=0;
$('#hlist').addEventListener('click',e=>{
 if(V_!='tasks')return;
 const dh=e.target.closest('.dh');if(dh){showDone=!showDone;dh.classList.toggle('open',showDone);$('.dl',$('#hlist')).classList.toggle('open',showDone);return}
 const row=e.target.closest('.task');if(!row)return;const t=D.tasks.find(x=>x.id==row.dataset.id);if(!t)return;
 if(e.target.closest('.ck')){t.d=t.d?0:Date.now();row.classList.toggle('d',!!t.d);buzz(10);save();clearTimeout(rT);
  rT=setTimeout(()=>{$$('.task',$('#hlist')).forEach(r=>{const x=D.tasks.find(y=>y.id==r.dataset.id);if(x&&(!!x.d)!=!!r.closest('.dl'))r.classList.add('out')});
   setTimeout(renderTasks,300)},700);return}
 if(e.target.closest('.tl'))editTask(t)});
async function editTask(t){const v=await askText({title:'Задача',value:t.t,extra:'Удалить'});if(v==null)return;
 if(v=='\u0000x'){D.tasks=D.tasks.filter(x=>x!==t);toast('Задача удалена');}else t.t=v;save();renderTasks()}

//9 Зажатие карточки: меню, перетаскивание в папку//
let G=null;const list=$('#hlist');
function noteById(id){return D.notes.find(n=>n.id==id)}
list.addEventListener('pointerdown',e=>{
 if(V_!='notes'||e.button>0)return;const c=e.target.closest('.card');if(!c)return;
 G={c,id:c.dataset.id,x:e.clientX,y:e.clientY,armed:0,drag:0,t:setTimeout(()=>{if(!G)return;G.armed=1;c.classList.add('armed');buzz(14)},HOLD())}});
list.addEventListener('pointermove',e=>{
 if(!G)return;const dx=e.clientX-G.x,dy=e.clientY-G.y;
 if(!G.armed){if(Math.hypot(dx,dy)>12){clearTimeout(G.t);G=null}return}
 if(!G.drag&&Math.hypot(dx,dy)>14&&!noteById(G.id).del)startDrag();
 if(G.drag)moveDrag(e)});
document.addEventListener('touchmove',e=>{if(G&&G.armed)e.preventDefault()},{passive:false});
list.addEventListener('pointerup',e=>{
 if(!G)return;clearTimeout(G.t);const g=G;G=null;g.c.classList.remove('armed');
 if(g.drag)return endDrag(g,e);
 const n=noteById(g.id);if(!n)return;
 if(g.armed||n.del)openMenu(n,g.c);else openNote(n)});
list.addEventListener('pointercancel',()=>{if(!G)return;clearTimeout(G.t);if(G.drag)endDrag(G,null,1);else G.c.classList.remove('armed');G=null});
list.addEventListener('contextmenu',e=>e.preventDefault());
function startDrag(){
 const c=G.c,r=c.getBoundingClientRect();G.drag=1;G.ox=G.x-r.left;G.oy=G.y-r.top;G.r=r;buzz(10);
 const g=c.cloneNode(true);g.classList.remove('armed');g.classList.add('ghost');g.style.width=r.width+'px';document.body.append(g);G.g=g;c.classList.add('src');
 const sh=el('div','shelf','<div class="st">Положить в папку</div><div class="sr"></div>');
 const items=[{id:'',name:'Без категории',cv:{c:'#3a3a3a',p:'plain'}}].concat(D.folders.map(f=>({id:f.id,name:f.name,cv:f.cv})));
 $('.sr',sh).innerHTML=items.map(f=>'<div class="sk" data-f="'+f.id+'">'+coverHTML(f.cv,f.name,0)+esc(f.name.slice(0,12))+'</div>').join('')+'<div class="sk" data-f="+"><div class="nw">'+ic('plus')+'</div>Новая</div>';
 document.body.append(sh);G.sh=sh;requestAnimationFrame(()=>sh.classList.add('on'));$('#hscroll').style.overflow='hidden'}
function moveDrag(e){G.g.style.transform='translate('+(e.clientX-G.ox)+'px,'+(e.clientY-G.oy)+'px) scale(.9) rotate(-2deg)';
 const t=document.elementFromPoint(e.clientX,e.clientY),sk=t&&t.closest?t.closest('.sk'):null;
 $$('.sk',G.sh).forEach(x=>x.classList.toggle('hot',x===sk));if(sk!==G.last){G.last=sk;if(sk)buzz(6)}}
async function endDrag(g,e,cancel){
 const sk=!cancel&&e?$('.sk.hot',g.sh):null,gh=g.g,n=noteById(g.id);$('#hscroll').style.overflow='';
 gh.style.transition='transform .3s var(--ease),opacity .3s';
 if(sk){const r=sk.getBoundingClientRect();gh.style.transform='translate('+(r.left+r.width/2-g.r.width/2)+'px,'+(r.top+30-g.r.height/2)+'px) scale(.12)';gh.style.opacity='0'}
 else gh.style.transform='translate('+g.r.left+'px,'+g.r.top+'px)';
 g.sh.classList.remove('on');await wait(300);gh.remove();g.sh.remove();g.c.classList.remove('src');
 if(sk&&n){let id=sk.dataset.f;
  if(id=='+'){const v=await askText({title:'Новая папка',ph:'Название'});if(!v)return;const f={id:uid(),name:v,cv:rndCv()};D.folders.push(f);id=f.id}
  if(!(await moveTo(n,id)))return;toast(id?'В папке «'+fById(id).name+'»':'Без категории')}}

//10 Меню заметки и папки//
function menuOverlay(items,o){
 o=o||{};const mo=el('div','mo'+(o.tr?' tr':'')),col=el('div','mcol');
 if(o.card){const c=o.card.cloneNode(true);c.classList.remove('armed','src');c.style.width='';col.append(c)}
 const p=el('div','mp');
 items.forEach((it,i)=>{if(it=='-'){p.append(el('div','md'));return}
  const b=el('button','mi'+(it.d?' dg':''),ic(it.i)+'<span>'+esc(it.t)+'</span>');b.style.setProperty('--i',i);b.onclick=()=>{close();setTimeout(it.f,60)};p.append(b)});
 col.append(p);mo.append(col);layer.append(mo);
 const close=()=>{mo.classList.remove('on');setTimeout(()=>mo.remove(),260)};
 mo.onclick=e=>{if(e.target===mo||e.target===col)close()};requestAnimationFrame(()=>requestAnimationFrame(()=>mo.classList.add('on')));return close}
function noteItems(n){
 if(n.del)return [{i:'restore',t:'Восстановить',f:()=>{n.del=0;n.up=Date.now();save();render()}},{i:'trash',t:'Удалить навсегда',d:1,f:()=>purge(n)}];
 return [
  {i:'pin',t:n.pin?'Открепить':'Закрепить',f:()=>{n.pin=n.pin?0:1;save();render()}},
  {i:'star',t:n.fav?'Убрать из избранного':'В избранное',f:()=>{n.fav=n.fav?0:1;save();render()}},
  {i:'rename',t:'Переименовать',f:()=>rename(n)},{i:'list',t:'Теги',f:()=>tagSheet(n)},{i:'doc',t:'Дублировать',f:()=>dupNote(n)},
  {i:'move',t:'В папку',f:()=>moveSheet(n)},
  {i:'cover',t:'Обложка',f:()=>coverSheet(n,0)},
  {i:n.lk?'unlock':'lock',t:n.lk?'Снять пароль':'Запаролить',f:()=>toggleLock(n)},
  {i:'share',t:'Поделиться',f:()=>share(n)},'-',
  {i:'trash',t:'Удалить',d:1,f:()=>trash(n)}]}
function openMenu(n,card){menuOverlay(noteItems(n),{card})}
async function rename(n){const v=await askText({title:'Название',value:n.t,ph:'Без названия',empty:1});if(v==null)return;n.t=v;n.up=Date.now();save();if(ED.n===n)tt.value=v;render()}
function trash(n){n.del=Date.now();if(ED.n===n)closeEditor();save();render();toast('Заметка удалена',{act:'Отменить',f:()=>{n.del=0;save();render()}})}
function purge(n){D.notes=D.notes.filter(x=>x!==n);n.pg.forEach(p=>{bdel('dr:'+p.id);p.au.forEach(a=>bdel('au:'+a.id))});save();render();toast('Удалено навсегда')}
async function toggleLock(n){
 if(!(await needKey()))return;
 if(n.lk){n.lk=0;n.enc=null;toast('Пароль снят')}else{n.lk=1;toast('Заметка под паролем')}
 n.up=Date.now();await persist();if(ED.n===n&&n.lk&&!KEY)closeEditor();render()}
async function share(n){const t=(n.t?n.t+'\n\n':'')+n.pg.map(p=>{const d=document.createElement('div');d.innerHTML=p.h.replace(/<\/(div|h2|li|p)>|<br\s*\/?>/gi,'$&\n');return d.textContent.trim()}).join('\n\n');
 try{if(navigator.share){await navigator.share({title:n.t||'Заметка',text:t});return}}catch(e){if(e&&e.name=='AbortError')return}
 try{await navigator.clipboard.writeText(t);toast('Текст скопирован')}catch(e){toast('Не удалось поделиться')}}
function moveSheet(n){
 const rows=[{id:'',name:'Без категории',cv:{c:'#3a3a3a',p:'plain'}}].concat(D.folders.map(f=>({id:f.id,name:f.name,cv:f.cv})));
 const sh=sheet('<h3>В папку</h3><div class="lst">'+rows.map(f=>'<button class="fr" data-f="'+f.id+'"><span class="mc">'+coverHTML(f.cv,f.name,1)+'</span>'+esc(f.name)+((n.fo||'')==f.id?ic('check').replace('<svg','<svg class="ok"'):'')+'</button>').join('')+'<button class="fr" data-f="+"><span class="mc" style="display:grid;place-items:center;color:var(--ac)">'+ic('plus')+'</span>Новая папка</button></div>');
 sh.el.onclick=async e=>{const b=e.target.closest('.fr');if(!b)return;let id=b.dataset.f;sh.close();
  if(id=='+'){const v=await askText({title:'Новая папка',ph:'Название'});if(!v)return;const f={id:uid(),name:v,cv:rndCv()};D.folders.push(f);id=f.id}
  if(!(await moveTo(n,id)))return;toast(id?'В папке «'+fById(id).name+'»':'Без категории')}}
function coverSheet(t,isF){
 if(!t.cv)t.cv=rndCv();const cv=t.cv;
 const sh=sheet('<h3>Обложка</h3><div id="cvp" style="margin-bottom:6px"></div><div class="lbl">Цвет</div><div class="sw" id="csw">'+CC.map(c=>'<button data-c="'+c+'" style="background:'+c+'" aria-label="Цвет"></button>').join('')+'</div><div class="lbl">Узор</div><div class="pat" id="cpt">'+CP.map(p=>'<button data-p="'+p[0]+'">'+p[1]+'</button>').join('')+'</div><div class="row">'+(isF?'':'<button class="btn" data-no>Без обложки</button>')+'<button class="btn pri" data-ok>Готово</button></div>');
 const draw=()=>{$('#cvp',sh.el).innerHTML=coverHTML(t.cv,t.name||t.t||'Название',0,1);$$('#csw button',sh.el).forEach(b=>b.classList.toggle('on',b.dataset.c==t.cv.c));$$('#cpt button',sh.el).forEach(b=>b.classList.toggle('on',b.dataset.p==t.cv.p))};
 draw();
 sh.el.onclick=e=>{const b=e.target.closest('button');if(!b)return;
  if(b.dataset.c){t.cv.c=b.dataset.c;buzz(5)}else if(b.dataset.p){t.cv.p=b.dataset.p;buzz(5)}
  else if('no' in b.dataset){t.cv=null;save();render();sh.close();return}
  else if('ok' in b.dataset){save();render();renderDrawer();sh.close();return}
  draw();save();render()}}

//11 Меню слева: папки, избранное, пароль, корзина//
let drawerOn=0;
function counts(){const a=D.notes.filter(n=>!n.del);return{all:a.filter(n=>!n.lk).length,none:a.filter(n=>!n.lk&&(!n.fo||!fById(n.fo))).length,fav:a.filter(n=>!n.lk&&n.fav).length,locked:a.filter(n=>n.lk).length,trash:D.notes.filter(n=>n.del).length}}
function renderDrawer(){const d=$('.drawer');if(!d)return;const c=counts();
 const row=(f,i,n,cls)=>'<div class="dr'+(F==f?' on':'')+'" data-f="'+f+'">'+i+'<span>'+esc(folderName(f))+'</span><span class="n">'+n+'</span></div>';
 d.innerHTML=
  row('all',ic('inbox'),c.all)+row('none',ic('doc'),c.none)+row('fav',ic('star'),c.fav)+row('locked',ic('lock'),c.locked)+row('trash',ic('trash'),c.trash)+
  '<div class="lbl"><span>Папки</span><button id="nf">Новая папка</button></div>'+
  D.folders.map(f=>'<div class="dr'+(F==f.id?' on':'')+'" data-f="'+f.id+'" data-fo="1"><span class="mc">'+coverHTML(f.cv,f.name,1)+'</span><span>'+esc(f.name)+(f.lk?ic('lock',16):'')+'</span><span class="n">'+(c.fo&&0||D.notes.filter(n=>!n.del&&!n.lk&&n.fo==f.id).length)+'</span></div>').join('')+
  '<div class="sp"></div><div class="dr" id="dset">'+ic('sliders')+'<span>Настройки</span></div>';
 $$('.dr[data-f]',d).forEach(r=>{const f=r.dataset.f;press(r,{tap:()=>{closeDrawer();setTimeout(()=>gotoF(f),120)},long:r.dataset.fo?()=>folderMenu(fById(f)):null})});
 $('#nf',d).onclick=async()=>{const v=await askText({title:'Новая папка',ph:'Название'});if(!v)return;const f={id:uid(),name:v,cv:rndCv()};D.folders.push(f);save();renderDrawer()};
 $('#dset',d).onclick=()=>{closeDrawer();setTimeout(settingsSheet,200)}}
function openDrawer(){if(drawerOn)return;drawerOn=1;const sc=el('div','scrim'),d=el('aside','drawer');sc.dataset.d=1;layer.append(sc,d);renderDrawer();sc.onclick=closeDrawer;requestAnimationFrame(()=>requestAnimationFrame(()=>{sc.classList.add('on');d.classList.add('on')}))}
function closeDrawer(){if(!drawerOn)return;drawerOn=0;const sc=$('.scrim[data-d]'),d=$('.drawer');sc.classList.remove('on');d.classList.remove('on');setTimeout(()=>{sc.remove();d.remove()},400)}
$('#bmenu').onclick=openDrawer;
async function gotoF(f){const _f=fById(f);if(_f&&_f.lk&&!KEY&&!(await needKey()))return;if(KEY&&D.set.relock!==false&&f!='locked'&&!(_f&&_f.lk)&&(F=='locked'||(fById(F)&&fById(F).lk)))await relock();
 if(f=='locked'){
  if(!D.vault&&!D.notes.some(n=>n.lk)){F='locked';V_='notes';syncSeg();render();return}
  F='locked';V_='notes';syncSeg();Q='';$('#q').value='';render(true);return}
 F=f;V_='notes';Q='';$('#q').value='';syncSeg();$('#hscroll').scrollTop=0;render()}
function syncSeg(){$$('#seg button').forEach(b=>b.classList.toggle('on',b.dataset.v==V_));segPos()}
function folderMenu(f){menuOverlay([
 {i:'rename',t:'Переименовать',f:async()=>{const v=await askText({title:'Название папки',value:f.name});if(!v)return;f.name=v;save();renderDrawer();render()}},
 {i:'cover',t:'Обложка',f:()=>coverSheet(f,1)},{i:f.lk?'unlock':'lock',t:f.lk?'Снять пароль с папки':'Запаролить папку',f:()=>lockFolder(f)},'-',
 {i:'trash',t:'Удалить папку',d:1,f:()=>{D.notes.forEach(n=>{if(n.fo==f.id)n.fo=''});D.folders=D.folders.filter(x=>x!==f);if(F==f.id)F='all';save();renderDrawer();render();toast('Папка удалена, заметки сохранены')}}])}

//12 Редактор: чтение, правка, форматирование//
const ED={n:null,pi:0,editing:0,drawing:0,dirty:0,hist:0,rng:null};
const e_=$('#e'),tt=$('#tt'),sheetEl=$('#sheet'),edEl=$('#ed');
function newNote(o,ne){
 const fo=(F!='all'&&F!='none'&&F!='fav'&&F!='locked'&&F!='trash')?F:'';
 const n=Object.assign({id:uid(),t:'',pg:[mkPage()],ci:0,pin:0,fav:F=='fav'?1:0,del:0,fo,cv:null,lk:(F=='locked'||(fById(F)&&fById(F).lk))&&KEY?1:0,enc:null,up:Date.now(),cr:Date.now()},o||{});
 D.notes.unshift(n);save();openEditor(n,{edit:!ne});return n}
async function openNote(n){if(n.lk&&!KEY){if(!(await needKey()))return}openEditor(n)}
function openEditor(n,o){
 ED.n=n;ED.pi=clamp(n.ci||0,0,n.pg.length-1);ED.dirty=0;ED.rng=null;
 tt.value=n.t;loadPage();setTools();
 edEl.inert=false;edEl.classList.remove('editing','drawing','focus','fpopen');$('#fp').classList.remove('on');$('#tfmt').classList.remove('on');$('#escroll').scrollTop=0;
 requestAnimationFrame(()=>{edEl.classList.add('on');$('#home').classList.add('under')});
 try{history.pushState({e:1},'');ED.hist=1}catch(e){ED.hist=0}
 if(o&&o.edit)setTimeout(()=>enterEdit(1),380)}
function curP(){return ED.n.pg[ED.pi]}
function loadPage(){const p=curP();e_.dataset.pid=p.id;e_.innerHTML=p.h||'<div><br></div>';markEmpty();applyPaper(p);loadDraw(p);renderAudio();pager()}
function applyPaper(p){vxPaper(p)}
function markEmpty(){e_.classList.toggle('empty',!e_.textContent.trim()&&!e_.querySelector('.td,li'))}
function pager(){const n=ED.n,m=n.pg.length;$('#pg').style.display=m>1?'flex':'none';$('#pnum').textContent=(ED.pi+1)+' / '+m;$('#pprev').disabled=ED.pi==0;$('#pnext').disabled=ED.pi==m-1}
function saveHtml(){if(ED.n){const p=ED.n.pg.find(x=>x.id==e_.dataset.pid);if(p)p.h=e_.innerHTML}}
let tcT=0;
function touch(){ED.dirty=1;saveHtml();clearTimeout(tcT);tcT=setTimeout(()=>{if(ED.n){ED.n.up=Date.now()}save()},350)}
function onInput(){markEmpty();touch();selUI()}
e_.addEventListener('input',onInput);
tt.addEventListener('input',()=>{ED.n.t=tt.value;touch()});
tt.addEventListener('keydown',e=>{if(e.key=='Enter'){e.preventDefault();enterEdit(0,null,1)}});
tt.addEventListener('focus',()=>{edEl.classList.add('editing')});
tt.addEventListener('blur',()=>setTimeout(()=>{if(document.activeElement!==e_&&document.activeElement!==tt&&!ED.voice&&!$('.sh.on')&&!TB())exitEdit()},160));
function isEmptyNote(n){return !n.t&&n.pg.length==1&&!txt(n.pg[0].h)&&!n.pg[0].dr&&!n.pg[0].au.length&&!n.lk}
function closeEditor(){
 if(!ED.n)return;const n=ED.n,wasLk=n.lk;stopVoice(true);exitEdit();if(DR.on)drawOff();flushDraw();saveHtml();closeSheetsFor();
 if(isEmptyNote(n))D.notes=D.notes.filter(x=>x!==n);else if(ED.dirty)n.up=Date.now();
 ED.n=null;edEl.classList.remove('on','focus');$('#home').classList.remove('under');setTimeout(()=>{if(!ED.n)edEl.inert=true},400);
 if(ED.hist){ED.hist=0;try{history.back()}catch(e){}}
 save();render();if(wasLk&&KEY&&D.set.relock!==false)setTimeout(relock,350)}
function closeSheetsFor(){$$('.sh.on').forEach(s=>{const sc=s.previousElementSibling;s.classList.remove('on');setTimeout(()=>{s.remove();sc&&sc.remove()},400)})}
window.addEventListener('popstate',()=>{if(ED.n){ED.hist=0;closeEditor()}});
$('#eback').onclick=closeEditor;
$('#edone').onclick=()=>exitEdit();
function setTools(){const on=ED.editing;edEl.classList.toggle('editing',!!on)}
function caretAt(x,y){let r=null;try{if(document.caretPositionFromPoint){const p=document.caretPositionFromPoint(x,y);if(p){r=document.createRange();r.setStart(p.offsetNode,p.offset)}}else if(document.caretRangeFromPoint)r=document.caretRangeFromPoint(x,y)}catch(e){}
 if(r&&e_.contains(r.startContainer)){r.collapse(true);const s=getSelection();s.removeAllRanges();s.addRange(r);return true}return false}
function caretEnd(){const r=document.createRange();r.selectNodeContents(e_);r.collapse(false);const s=getSelection();s.removeAllRanges();s.addRange(r)}
function enterEdit(atEnd,ev,noFocus){
 if(DR.on)drawOff();
 e_.contentEditable='true';ED.editing=1;edEl.classList.add('editing');
 e_.focus({preventScroll:true});
 if(ev&&caretAt(ev.clientX,ev.clientY)){}else if(atEnd||!ev)caretEnd();
 refreshTools()}
function exitEdit(){ED.editing=0;e_.contentEditable='false';edEl.classList.remove('editing');
 if(document.activeElement===e_||document.activeElement===tt)document.activeElement.blur()}
e_.addEventListener('blur',()=>setTimeout(()=>{const a=document.activeElement;if(a!==e_&&a!==tt&&!ED.voice&&!$('.sh.on')&&!TB()&&ED.editing)exitEdit()},160));
//Тап по тексту: галочка, иначе вход в правку (клавиатура только тут)//
e_.addEventListener('click',e=>{
 const t=e.target;
 if(t.classList&&t.classList.contains('td')){const r=t.getBoundingClientRect();if(e.clientX-r.left<44){
  t.dataset.d=t.dataset.d=='1'?'0':'1';if(t.dataset.d=='0')t.removeAttribute('data-d');buzz(10);touch();return}}
 if(!ED.editing)enterEdit(0,e)});
e_.addEventListener('mousedown',e=>{const t=e.target;if(ED.editing&&t.classList&&t.classList.contains('td')&&e.clientX-t.getBoundingClientRect().left<44)e.preventDefault()});
//Enter и Backspace в чек-листе//
function curBlock(){const s=getSelection();if(!s.rangeCount)return null;let n=s.anchorNode;if(!n||!e_.contains(n))return null;if(n.nodeType==3)n=n.parentElement;while(n&&n.parentElement!==e_)n=n.parentElement;return n}
function atStart(b){const s=getSelection();if(!s.rangeCount||!s.isCollapsed)return false;const r=document.createRange();r.setStart(b,0);r.setEnd(s.anchorNode,s.anchorOffset);return r.toString()==''}
function atEndB(b){const s=getSelection();if(!s.rangeCount||!s.isCollapsed)return false;const r=document.createRange();r.setStart(s.anchorNode,s.anchorOffset);r.setEnd(b,b.childNodes.length);return r.toString()==''}
e_.addEventListener('beforeinput',e=>{
 const b=curBlock();if(!b||!b.classList.contains('td'))return;
 if(e.inputType=='insertParagraph'){
  if(!b.textContent.trim()){e.preventDefault();b.classList.remove('td');b.removeAttribute('data-d');onInput();return}
  if(atEndB(b)){e.preventDefault();const n=document.createElement('div');n.className='td';n.innerHTML='<br>';b.after(n);const r=document.createRange();r.setStart(n,0);r.collapse(true);const s=getSelection();s.removeAllRanges();s.addRange(r);onInput();return}
  setTimeout(()=>{const c=curBlock();if(c&&c.classList.contains('td'))c.removeAttribute('data-d');onInput()})}
 if(e.inputType=='deleteContentBackward'&&atStart(b)){e.preventDefault();b.classList.remove('td');b.removeAttribute('data-d');onInput()}});
//Команды форматирования//
function restoreSel(){if(document.activeElement!==e_){e_.focus({preventScroll:true});if(ED.rng){const s=getSelection();s.removeAllRanges();s.addRange(ED.rng)}else caretEnd()}}
function exec(c,v){if(!ED.editing)enterEdit(1);restoreSel();document.execCommand(c,false,v);onInput()}
function blk(tag){restoreSel();const cur=(document.queryCommandValue('formatBlock')||'').toLowerCase();document.execCommand('formatBlock',false,cur==tag?'div':tag);onInput()}
function todo(){if(!ED.editing)enterEdit(1);restoreSel();let b=curBlock();
 if(!b){document.execCommand('formatBlock',false,'div');b=curBlock()}
 if(!b)return;if(b.tagName=='UL'||b.tagName=='OL'){return}
 b.classList.toggle('td');b.removeAttribute('data-d');buzz(8);onInput()}
function insText(t){exec('insertText',t)}
const CMD={bold:()=>exec('bold'),italic:()=>exec('italic'),underline:()=>exec('underline'),strike:()=>exec('strikeThrough'),
 mark:()=>{if(!ED.editing)enterEdit(1);restoreSel();const v=document.queryCommandValue('hiliteColor')||'';document.execCommand('hiliteColor',false,/242,\s*184/.test(v)?'transparent':'rgba(242,184,0,.5)');onInput()},
 h:()=>blk('h2'),ul:()=>exec('insertUnorderedList'),ol:()=>exec('insertOrderedList'),td:todo,
 date:()=>insText(new Date().toLocaleDateString('ru',{day:'numeric',month:'long',year:'numeric'})+' '),
 time:()=>insText(new Date().toLocaleTimeString('ru',{hour:'2-digit',minute:'2-digit'})+' ')};
['#fp','#sb','#tools','#dtools','.etop','#pg'].forEach(s=>$$(s).forEach(x=>x.addEventListener('mousedown',e=>{if(e.target.closest('button')&&!e.target.closest('#emore,#eback,#edone'))e.preventDefault()})));
$$('#fp [data-c],#sb [data-c]').forEach(b=>b.addEventListener('click',()=>{buzz(5);CMD[b.dataset.c]();refreshTools()}));
$('#eundo').onclick=()=>{if(!ED.editing&&!DR.on){return}if(DR.on)return drawUndo();exec('undo')};
$('#eredo').onclick=()=>{if(ED.editing)exec('redo')};
$('#tfmt').onclick=()=>{buzz(5);if(!ED.editing)enterEdit(1);const fp=$('#fp'),on=!fp.classList.contains('on');fp.classList.toggle('on',on);$('#tfmt').classList.toggle('on',on);edEl.classList.toggle('fpopen',on);refreshTools()};
$('#ttodo').onclick=()=>{buzz(5);todo()};
$('#tmic').onclick=()=>openVoice('dict');
$('#tpage').onclick=pageSheet;
function refreshTools(){
 const q=c=>{try{return document.queryCommandState(c)}catch(e){return false}};
 const st={bold:q('bold'),italic:q('italic'),underline:q('underline'),strike:q('strikeThrough'),ul:q('insertUnorderedList'),ol:q('insertOrderedList')};
 let hv='';try{hv=(document.queryCommandValue('formatBlock')||'').toLowerCase()}catch(e){}st.h=hv=='h2';
 const b=curBlock();st.td=!!(b&&b.classList.contains('td'));
 $$('#fp [data-c],#sb [data-c]').forEach(x=>x.classList.toggle('on',!!st[x.dataset.c]))}
//Панель над выделенным текстом//
function selUI(){{const s=getSelection();if(s.rangeCount&&e_.contains(s.anchorNode))ED.rng=s.getRangeAt(0).cloneRange();refreshTools();return}}function _selOld(){
 const s=getSelection(),sb=$('#sb');
 if(s.rangeCount&&e_.contains(s.anchorNode))ED.rng=s.getRangeAt(0).cloneRange();
 if(!ED.editing||!s.rangeCount||s.isCollapsed||!e_.contains(s.anchorNode)){sb.classList.remove('on');return}
 const r=s.getRangeAt(0).getBoundingClientRect(),w=sb.offsetWidth||316,vh=(window.visualViewport?visualViewport.height:innerHeight);
 let top=r.bottom+46;if(top>vh-150)top=Math.max(70,r.top-62);
 sb.style.left=clamp(r.left+r.width/2-w/2,8,innerWidth-w-8)+'px';sb.style.top=top+'px';sb.classList.add('on');refreshTools()}
document.addEventListener('selectionchange',()=>{if(ED.n)selUI()});
//Клавиатура: панель поднимается над ней//
if(window.visualViewport){const f=()=>{const kb=Math.max(0,innerHeight-visualViewport.height-visualViewport.offsetTop);document.documentElement.style.setProperty('--kb',kb+'px')};visualViewport.addEventListener('resize',f);visualViewport.addEventListener('scroll',f)}
//Листание страниц: свайп по листу, пока не печатаете//
let sw0=null;
$('#escroll').addEventListener('touchstart',e=>{sw0=e.touches.length==1?[e.touches[0].clientX,e.touches[0].clientY]:null},{passive:true});
$('#escroll').addEventListener('touchend',e=>{if(!sw0||!ED.n||ED.editing||DR.on||ED.n.pg.length<2)return;const t=e.changedTouches[0],dx=t.clientX-sw0[0],dy=t.clientY-sw0[1];sw0=null;
 if(Math.abs(dx)>70&&Math.abs(dy)<50)goPage(ED.pi+(dx<0?1:-1),dx<0?1:-1)},{passive:true});
function goPage(i,dir){const n=ED.n;if(i<0||i>=n.pg.length)return;flushDraw();saveHtml();exitEdit();const prev=ED.pi;ED.pi=i;n.ci=i;loadPage();buzz(8);
 const c=sheetEl.classList;c.remove('fn','fq');void sheetEl.offsetWidth;c.add((dir||(i>prev?1:-1))>0?'fn':'fq');$('#escroll').scrollTop=0;save()}
$('#pprev').onclick=()=>goPage(ED.pi-1,-1);$('#pnext').onclick=()=>goPage(ED.pi+1,1);$('#pnum').parentElement.addEventListener('click',e=>{if(e.target.id=='pnum')pagesGrid()});
function addPage(){const n=ED.n,p=mkPage();p.paper=curP().paper;p.rule=curP().rule;n.pg.splice(ED.pi+1,0,p);goPage(ED.pi+1,1);toast('Страница '+(ED.pi+1))}
function pagesGrid(){
 const n=ED.n;saveHtml();
 const sh=sheet('<h3>Страницы</h3><div class="ptiles">'+n.pg.map((p,i)=>'<button class="pt'+(i==ED.pi?' on':'')+'" data-i="'+i+'" style="background:'+PAPERS[p.paper]+';color:'+(p.paper=='dark'?'#ddd':'#2b2418')+'">'+esc(txt(p.h).slice(0,60))+'<em>'+(i+1)+'</em></button>').join('')+'<button class="pt add" data-a="add">'+ic('plus')+'</button></div>');
 sh.el.onclick=e=>{const b=e.target.closest('.pt');if(!b)return;sh.close();if(b.dataset.a=='add')setTimeout(addPage,200);else setTimeout(()=>goPage(+b.dataset.i),200)}}
function pageSheet(){
 const n=ED.n,p=curP();saveHtml();const w=txt(p.h).split(' ').filter(Boolean).length;
 const sh=sheet('<h3>Страница</h3><div class="lbl" style="margin-top:0">Бумага</div><div class="sw" id="pps">'+Object.keys(PAPERS).map(k=>'<button data-p="'+k+'" style="background:'+PAPERS[k]+';box-shadow:inset 0 0 0 1px #3a3a3a" aria-label="'+({cream:'Кремовая',white:'Белая',dark:'Тёмная'})[k]+'"></button>').join('')+'</div><div class="lbl">Разметка</div><div class="rl" id="prl">'+[['lines','Линейка'],['grid','Клетка'],['dots','Точки'],['none','Чистая']].map(r=>'<button data-r="'+r[0]+'"><i></i>'+r[1]+'</button>').join('')+'</div><div class="lbl">Блокнот</div><div class="pgr"><button class="btn" data-a="prev" style="width:50px;padding:0">'+ic('back')+'</button><b id="pgn"></b><button class="btn" data-a="next" style="width:50px;padding:0">'+ic('chev')+'</button></div><div class="row"><button class="btn" data-a="add">Новая страница</button><button class="btn" data-a="all">Все страницы</button></div>'+(n.pg.length>1?'<div class="row"><button class="btn dg" data-a="del">Удалить страницу</button></div>':'')+'<p class="sub" style="margin:16px 0 0;text-align:center">'+w+' сл. · ~'+Math.max(1,Math.round(w/200))+' мин чтения</p>');
 const paint=()=>{$$('#pps button',sh.el).forEach(b=>b.classList.toggle('on',b.dataset.p==p.paper));$$('#prl button',sh.el).forEach(b=>b.classList.toggle('on',b.dataset.r==p.rule));$('#pgn',sh.el).textContent=(ED.pi+1)+' из '+n.pg.length};paint();
 sh.el.onclick=e=>{const b=e.target.closest('button');if(!b)return;
  if(b.dataset.p){p.paper=b.dataset.p;applyPaper(p);paint();save();buzz(5)}
  else if(b.dataset.r){p.rule=b.dataset.r;applyPaper(p);paint();save();buzz(5)}
  else if(b.dataset.a=='add'){sh.close();setTimeout(addPage,250)}
  else if(b.dataset.a=='all'){sh.close();setTimeout(pagesGrid,300)}
  else if(b.dataset.a=='prev'){goPage(ED.pi-1,-1);sh.close()}
  else if(b.dataset.a=='next'){if(ED.pi==n.pg.length-1){sh.close();setTimeout(addPage,250)}else{goPage(ED.pi+1,1);sh.close()}}
  else if(b.dataset.a=='del'){sh.close();const i=ED.pi;const pp=n.pg[i];n.pg.splice(i,1);bdel('dr:'+pp.id);ED.pi=Math.min(i,n.pg.length-1);n.ci=ED.pi;loadPage();save();toast('Страница удалена')}}}
$('#emore').onclick=()=>{const n=ED.n;if(!n)return;saveHtml();
 menuOverlay([{i:'focus',t:'Режим фокуса',f:()=>{exitEdit();edEl.classList.add('focus')}}].concat(noteItems(n)),{tr:1})};
$('#fx').onclick=()=>edEl.classList.remove('focus');

//13 Рисование поверх листа//
const cv=$('#cv'),cx=cv.getContext('2d');
const DR={on:0,col:'auto',sz:1,er:0,base:null,strokes:[],cur:null,tm:0};
const SZ=[3,6,12];
function inkCol(){return sheetEl.dataset.paper=='dark'?'#ececea':'#1b1b1b'}
function sizeCv(){const w=sheetEl.offsetWidth,h=sheetEl.offsetHeight,r=2;if(!w||!h||(cv.width==w*r&&cv.height==h*r))return;
 let old=null;if(cv.width){old=document.createElement('canvas');old.width=cv.width;old.height=cv.height;old.getContext('2d').drawImage(cv,0,0)}
 cv.width=w*r;cv.height=h*r;cv.style.width=w+'px';cv.style.height=h+'px';if(old)cx.drawImage(old,0,0)}
new ResizeObserver(sizeCv).observe(sheetEl);
function paintStroke(s){
 if(s.clear){cx.clearRect(0,0,cv.width,cv.height);return}
 cx.save();cx.globalCompositeOperation=s.er?'destination-out':'source-over';cx.strokeStyle=s.col;cx.fillStyle=s.col;cx.lineWidth=s.w*2;cx.lineCap='round';cx.lineJoin='round';
 const p=s.pts;if(p.length==1){cx.beginPath();cx.arc(p[0][0],p[0][1],s.w,0,7);cx.fill()}
 else{cx.beginPath();cx.moveTo(p[0][0],p[0][1]);for(let i=1;i<p.length-1;i++){const mx=(p[i][0]+p[i+1][0])/2,my=(p[i][1]+p[i+1][1])/2;cx.quadraticCurveTo(p[i][0],p[i][1],mx,my)}const l=p[p.length-1];cx.lineTo(l[0],l[1]);cx.stroke()}
 cx.restore()}
function redraw(){cx.clearRect(0,0,cv.width,cv.height);if(DR.base)cx.drawImage(DR.base,0,0);DR.strokes.forEach(paintStroke)}
async function loadDraw(p){DR.strokes=[];DR.base=null;sizeCv();cx.clearRect(0,0,cv.width,cv.height);
 if(!p.dr)return;const b=await bget('dr:'+p.id);if(!b||curP()!==p)return;
 try{DR.base=await createImageBitmap(b);redraw()}catch(e){}}
function flushDraw(){clearTimeout(DR.tm);if(!ED.n||!DR.dirty)return;DR.dirty=0;const p=curP();cv.toBlob(async b=>{if(!b)return;await bset('dr:'+p.id,b);p.dr=1;prCache.delete(p.id);save()},'image/png')}
function pt(e){const r=cv.getBoundingClientRect();return [(e.clientX-r.left)*cv.width/r.width,(e.clientY-r.top)*cv.height/r.height]}
cv.addEventListener('pointerdown',e=>{if(!DR.on)return;cv.setPointerCapture(e.pointerId);const w=SZ[DR.sz]*(DR.er?3:1);
 DR.cur={er:DR.er,col:DR.col=='auto'?inkCol():DR.col,w,pts:[pt(e)]};paintStroke(DR.cur)});
cv.addEventListener('pointermove',e=>{if(!DR.cur)return;(e.getCoalescedEvents?e.getCoalescedEvents():[e]).forEach(x=>DR.cur.pts.push(pt(x)));redraw();paintStroke(DR.cur)});
const pend=()=>{if(!DR.cur)return;DR.strokes.push(DR.cur);DR.cur=null;DR.dirty=1;ED.dirty=1;clearTimeout(DR.tm);DR.tm=setTimeout(flushDraw,700)};
cv.addEventListener('pointerup',pend);cv.addEventListener('pointercancel',pend);
function drawOn(){exitEdit();DR.on=1;edEl.classList.add('drawing');edEl.classList.remove('fpopen');$('#fp').classList.remove('on');$('#tfmt').classList.remove('on');$('#tdraw').classList.add('on');updDraw()}
function drawOff(){DR.on=0;flushDraw();edEl.classList.remove('drawing');$('#tdraw').classList.remove('on')}
function drawUndo(){if(!DR.strokes.length)return;DR.strokes.pop();redraw();DR.dirty=1;clearTimeout(DR.tm);DR.tm=setTimeout(flushDraw,500)}
function updDraw(){$$('#dtools .cl').forEach(b=>b.classList.toggle('on',!DR.er&&b.dataset.col==DR.col));$('#der').classList.toggle('on',!!DR.er);const i=$('#dsz i');i.style.width=i.style.height=(6+DR.sz*5)+'px'}
$('#tdraw').onclick=()=>{buzz(6);DR.on?drawOff():drawOn()};
$('#ddone').onclick=drawOff;$('#dun').onclick=drawUndo;
$('#der').onclick=()=>{DR.er=DR.er?0:1;updDraw()};
$('#dsz').onclick=()=>{DR.sz=(DR.sz+1)%3;updDraw();buzz(5)};
$$('#dtools .cl').forEach(b=>b.onclick=()=>{DR.col=b.dataset.col;DR.er=0;updDraw();buzz(5)});
$('#eundo').addEventListener('pointerdown',()=>{});

//14 Голос: диктовка и запись, бары прыгают от звука//
const V={on:0,m:'dict',stream:null,ctx:null,an:null,rec:null,ch:[],raf:0,t0:0,sr:null,fake:0,sheet:null};
const SRC=window.SpeechRecognition||window.webkitSpeechRecognition;
function openVoice(mode){
 if(!ED.n)return;saveHtml();if(ED.editing&&ED.rng)ED.rng=ED.rng;
 const keep=ED.rng;exitEdit();ED.rng=keep;V.m=mode||'dict';ED.voice=1;
 const bars=Array.from({length:29},()=>'<i></i>').join('');
 const sh=sheet('<h3>Голос</h3><div class="vm"><div class="opt" id="vopt"><button data-m="dict">Диктовка</button><button data-m="rec">Запись</button></div></div><div class="vz" id="vz">'+bars+'</div><div class="vt" id="vt">0:00</div><div class="vl" id="vl"></div><button class="vgo" id="vgo" aria-label="Начать">'+ic('mic')+'</button>',()=>{stopVoice();ED.voice=0});
 V.sheet=sh;const opt=$('#vopt',sh.el);
 const setM=m=>{if(V.on)return;V.m=m;$$('button',opt).forEach(b=>b.classList.toggle('on',b.dataset.m==m));$('#vl',sh.el).textContent=m=='dict'?'Говорите, текст появится в заметке':'Запись сохранится на листе'};
 setM(V.m);opt.onclick=e=>{const b=e.target.closest('button');if(b)setM(b.dataset.m)};
 $('#vgo',sh.el).onclick=()=>V.on?stopVoice():startVoice()}
async function startVoice(){
 const sh=V.sheet;if(!sh)return;V.ch=[];V.fake=0;
 try{V.stream=await navigator.mediaDevices.getUserMedia({audio:true})}catch(e){V.stream=null}
 if(V.stream){try{V.ctx=new (window.AudioContext||window.webkitAudioContext)();const s=V.ctx.createMediaStreamSource(V.stream);V.an=V.ctx.createAnalyser();V.an.fftSize=128;V.an.smoothingTimeConstant=.6;s.connect(V.an)}catch(e){V.an=null}}
 if(V.m=='rec'){
  if(!V.stream||!window.MediaRecorder){toast('Нет доступа к микрофону');return}
  V.rec=new MediaRecorder(V.stream);V.rec.ondataavailable=e=>{if(e.data&&e.data.size)V.ch.push(e.data)};V.rec.start()}
 else{
  if(!SRC){toast('Диктовка не поддерживается этим браузером');if(V.stream)V.stream.getTracks().forEach(t=>t.stop());V.stream=null;return}
  const sr=new SRC();sr.lang='ru-RU';sr.continuous=true;sr.interimResults=true;V.sr=sr;
  sr.onresult=e=>{let fin='',itm='';for(let i=e.resultIndex;i<e.results.length;i++){const r=e.results[i];if(r.isFinal)fin+=r[0].transcript;else itm+=r[0].transcript}
   const vl=$('#vl',sh.el);if(vl)vl.textContent=itm||vl.textContent;if(fin)insertDictated(fin.trim()+' ')};
  sr.onspeechstart=()=>{V.fake=1};sr.onspeechend=()=>{V.fake=0};sr.onsoundstart=()=>{V.fake=1};sr.onsoundend=()=>{V.fake=0};
  sr.onerror=e=>{if(e.error=='not-allowed'||e.error=='service-not-allowed'){toast('Разрешите доступ к микрофону');stopVoice()}else if(e.error=='audio-capture'){toast('Микрофон занят')}};
  sr.onend=()=>{if(V.on&&V.sr===sr){try{sr.start()}catch(e){}}};
  try{sr.start()}catch(e){toast('Не удалось включить диктовку');return}}
 V.on=1;V.t0=Date.now();buzz(14);
 const g=$('#vgo',sh.el);g.innerHTML=ic('stop');g.setAttribute('aria-label','Остановить');$('#vopt',sh.el).style.opacity='.4';
 if(V.m=='dict')$('#vl',sh.el).textContent='Слушаю…';else $('#vl',sh.el).textContent='Идёт запись…';
 vLoop()}
function vLoop(){
 const sh=V.sheet;if(!sh||!V.on)return;const bs=$$('#vz i',sh.el),n=bs.length,arr=V.an?new Uint8Array(V.an.frequencyBinCount):null;
 const f=()=>{if(!V.on)return;
  if(arr)V.an.getByteFrequencyData(arr);const t=Date.now();
  bs.forEach((b,i)=>{const d=Math.abs(i-(n-1)/2)/((n-1)/2);let v;
   if(arr){const k=Math.floor(2+(1-d)*26);v=(arr[k]||0)/255}
   else v=V.fake?(.25+.75*Math.abs(Math.sin(t/110+i*.9)))*(1-d*.6):.05;
   b.style.height=(8+v*v*110*(1-d*.45))+'px'});
  const s=Math.floor((t-V.t0)/1000),tm_=$('#vt',sh.el);if(tm_)tm_.textContent=Math.floor(s/60)+':'+String(s%60).padStart(2,'0');
  V.raf=requestAnimationFrame(f)};f()}
function insertDictated(t){
 if(!ED.n||!t)return;const r=ED.rng;
 if(r&&e_.contains(r.startContainer)){r.deleteContents();const tn=document.createTextNode(t);r.insertNode(tn);r.setStartAfter(tn);r.collapse(true);ED.rng=r}
 else{let b=e_.lastElementChild;if(!b){b=document.createElement('div');e_.append(b)}b.append(document.createTextNode(t));const r2=document.createRange();r2.selectNodeContents(b);r2.collapse(false);ED.rng=r2}
 markEmpty();touch()}
async function stopVoice(silent){
 const wasOn=V.on;V.on=0;cancelAnimationFrame(V.raf);
 if(V.sr){const s=V.sr;V.sr=null;try{s.stop()}catch(e){}}
 const dur=Math.round((Date.now()-V.t0)/1000);
 if(V.rec&&V.rec.state!='inactive'){const rec=V.rec;V.rec=null;await new Promise(res=>{rec.onstop=res;try{rec.stop()}catch(e){res()}});
  if(V.ch.length&&ED.n){const id=uid(),b=new Blob(V.ch,{type:rec.mimeType||'audio/webm'});await bset('au:'+id,b);const p=curP();p.au.push({id,d:dur});renderAudio();touch();toast('Запись добавлена')}V.ch=[]}
 if(V.stream){V.stream.getTracks().forEach(t=>t.stop());V.stream=null}
 if(V.ctx){try{V.ctx.close()}catch(e){}V.ctx=null}V.an=null;
 const sh=V.sheet;
 if(wasOn&&sh&&sh.el.isConnected){const g=$('#vgo',sh.el);if(g){g.innerHTML=ic('mic');g.setAttribute('aria-label','Начать')}const o=$('#vopt',sh.el);if(o)o.style.opacity='';$$('#vz i',sh.el).forEach(b=>b.style.height='');if(!silent&&V.m=='dict'){const vl=$('#vl',sh.el);if(vl)vl.textContent='Готово'}}}
//Аудиозаписи на листе//
let AUD=null;
function renderAudio(){
 const box=$('#aus'),p=ED.n?curP():null;box.innerHTML='';if(!p||!p.au.length)return;
 p.au.forEach((a,i)=>{
  const row=el('div','au','<button class="pl" aria-label="Играть">'+ic('play')+'</button><div class="wv">'+Array.from({length:34},(_,k)=>'<s style="height:'+(6+Math.abs(Math.sin((k+a.id.charCodeAt(a.id.length-1))*.8))*20)+'px"></s>').join('')+'</div><small>'+Math.floor(a.d/60)+':'+String(a.d%60).padStart(2,'0')+'</small><button class="rm" aria-label="Удалить">'+ic('x')+'</button>');
  const pl=$('.pl',row),wv=$$('.wv s',row);
  pl.onclick=async()=>{
   if(AUD&&AUD.id==a.id){AUD.a.pause();AUD=null;pl.innerHTML=ic('play');wv.forEach(s=>s.classList.remove('p'));return}
   if(AUD){AUD.a.pause();AUD=null;renderAudio();return setTimeout(()=>$$('.au .pl')[i].click(),30)}
   const b=await bget('au:'+a.id);if(!b){toast('Запись не найдена');return}
   const au=new Audio(URL.createObjectURL(b));AUD={id:a.id,a:au};pl.innerHTML=ic('pause');
   au.ontimeupdate=()=>{const k=Math.floor(wv.length*au.currentTime/(au.duration||a.d||1));wv.forEach((s,j)=>s.classList.toggle('p',j<=k))};
   au.onended=()=>{AUD=null;pl.innerHTML=ic('play');wv.forEach(s=>s.classList.remove('p'))};au.play()};
  $('.rm',row).onclick=()=>{p.au.splice(i,1);bdel('au:'+a.id);renderAudio();touch()};
  box.append(row)})}

//15 Настройки: коротко и по делу//
function applySet(){const s=D.set,r=document.documentElement;
 const ff={onest:"'Onest',system-ui,sans-serif",serif:"'Literata',Georgia,serif",hand:"'Caveat','Segoe Print',cursive"}[s.font];
 r.style.setProperty('--nf',ff);const fs=s.font=='hand'?s.fs+4:s.fs;r.style.setProperty('--fs',fs+'px');r.style.setProperty('--L',Math.round(fs*(s.lh||1.9))+'px');
 document.body.classList.toggle('noanim',!s.anim);r.classList.toggle('noanim',!s.anim);setTimeout(sizeCv,60);if(window.applyVx)applyVx()}
function settingsSheet(){
 const s=D.set;
 const sh=sheet('<h3>Настройки</h3>'+
  '<div class="setr"><span>Шрифт</span><div class="opt" id="sf"><button data-v="onest">Прямой</button><button data-v="serif">Книжный</button><button data-v="hand">Рукописный</button></div></div>'+
  '<div class="setr"><span>Размер текста</span><div class="opt" id="ss"><button data-v="15">Мелкий</button><button data-v="17">Обычный</button><button data-v="20">Крупный</button></div></div>'+
  '<div class="setr"><span>Бумага для новых страниц</span><div class="sw" id="sp" style="gap:8px">'+Object.keys(PAPERS).map(k=>'<button data-v="'+k+'" style="width:34px;height:34px;background:'+PAPERS[k]+';box-shadow:inset 0 0 0 1px #3a3a3a" aria-label="'+k+'"></button>').join('')+'</div></div>'+
  '<div class="setr"><span>Анимации</span><button class="tg" id="sa" aria-label="Анимации"></button></div>'+
  '<div class="setr"><span>Вибрация</span><button class="tg" id="sv" aria-label="Вибрация"></button></div>'+
  '<div class="setr"><span>Пароль для заметок</span><button class="btn" id="spw">'+(D.vault?'Сменить':'Создать')+'</button></div>'+
  (D.vault?'<div class="setr"><span>Закрыть хранилище сейчас</span><button class="btn" id="sl">Закрыть</button></div>':'')+
  '<div class="setr"><span>Резервная копия</span><button class="btn" id="sb2">Открыть</button></div>'+
  '<div class="setr"><span>Очистить корзину</span><button class="btn dg" id="sc">Очистить</button></div>');
 const e=sh.el,paint=()=>{$$('#sf button',e).forEach(b=>b.classList.toggle('on',b.dataset.v==s.font));$$('#ss button',e).forEach(b=>b.classList.toggle('on',+b.dataset.v==s.fs));$$('#sp button',e).forEach(b=>b.classList.toggle('on',b.dataset.v==s.paper));$('#sa',e).classList.toggle('on',s.anim);$('#sv',e).classList.toggle('on',s.vib)};paint();
 const set=(k,v)=>{s[k]=v;applySet();paint();save()};
 $('#sf',e).onclick=x=>{const b=x.target.closest('button');if(b)set('font',b.dataset.v)};
 $('#ss',e).onclick=x=>{const b=x.target.closest('button');if(b)set('fs',+b.dataset.v)};
 $('#sp',e).onclick=x=>{const b=x.target.closest('button');if(b)set('paper',b.dataset.v)};
 $('#sa',e).onclick=()=>set('anim',!s.anim);$('#sv',e).onclick=()=>{set('vib',!s.vib);buzz(15)};
 $('#spw',e).onclick=async()=>{sh.close();await wait(300);
  if(!D.vault){await needKey();return}
  const cur=await askPass({title:'Введите текущий код',verify:tryUnlock,ok:'Далее'});if(!cur)return;
  const pw=await askPass({title:'Новый код-пароль',confirm:1,ok:'Сменить'});if(!pw)return;await setupVault(pw);toast('Пароль изменён')};
 const sl=$('#sl',e);if(sl)sl.onclick=async()=>{sh.close();await relock();toast('Хранилище закрыто')};
 $('#sc',e).onclick=()=>{const k=D.notes.filter(n=>n.del);k.forEach(n=>n.pg.forEach(p=>{bdel('dr:'+p.id);p.au.forEach(a=>bdel('au:'+a.id))}));D.notes=D.notes.filter(n=>!n.del);save();render();toast('Корзина очищена')};
 $('#sb2',e).onclick=()=>{sh.close();setTimeout(backupSheet,300)}}
function backupSheet(){
 const sh=sheet('<h3>Резервная копия</h3><p class="sub">Копируется текст заметок и папки. Рисунки и записи не входят.</p><textarea class="in" id="bt" spellcheck="false"></textarea><div class="row"><button class="btn" data-a="copy">Скопировать</button><button class="btn pri" data-a="res">Восстановить</button></div>');
 const ta=$('#bt',sh.el);ta.value=JSON.stringify({notes:D.notes,folders:D.folders,tasks:D.tasks,vault:D.vault});
 sh.el.onclick=async e=>{const b=e.target.closest('button');if(!b||!b.dataset.a)return;
  if(b.dataset.a=='copy'){try{await navigator.clipboard.writeText(ta.value);toast('Скопировано')}catch(x){ta.select();toast('Выделено, скопируйте вручную')}}
  else{try{const o=JSON.parse(ta.value);if(!o.notes)throw 0;const have=new Set(D.notes.map(n=>n.id));let c=0;o.notes.forEach(n=>{if(!have.has(n.id)){D.notes.push(n);c++}});(o.folders||[]).forEach(f=>{if(!fById(f.id))D.folders.push(f)});(o.tasks||[]).forEach(t=>{if(!D.tasks.some(x=>x.id==t.id))D.tasks.push(t)});(o.cal||[]).forEach(x=>{if(x&&x.id&&!D.cal.some(y=>y.id==x.id))D.cal.push(x)});(o.items||[]).forEach(x=>{if(x&&x.id&&!D.items.some(y=>y.id==x.id))D.items.push(x)});if(o.fin)['cards','tx','subs','goals'].forEach(k=>(o.fin[k]||[]).forEach(x=>{if(x&&x.id&&!D.fin[k].some(y=>y.id==x.id))D.fin[k].push(x)}));if(!D.vault&&o.vault)D.vault=o.vault;save();render();sh.close();toast('Добавлено заметок: '+c)}catch(x){toast('Не удалось прочитать копию')}}}}

//16 Запуск//
document.addEventListener('visibilitychange',()=>{if(document.hidden){flushDraw();if(KEY)relock()}});
window.addEventListener('pagehide',()=>{saveHtml();persist()});
loadData();applySet();icons(document);render();setTimeout(segPos,30);setTimeout(segPos,400);
if(document.fonts&&document.fonts.ready)document.fonts.ready.then(segPos);
</script>
<script>
//Vibe: слой улучшений//
const HOLD=()=>+D.set.hold||2000;
const TB=()=>Date.now()-(window.vxTb||0)<500;
const hex=h=>{h=(h||'#000').replace('#','');if(h.length==3)h=h.replace(/./g,'$&$&');const n=parseInt(h,16)||0;return[n>>16&255,n>>8&255,n&255]};
const lum=h=>{const[r,g,b]=hex(h);return(.299*r+.587*g+.114*b)/255};
const shade=(h,a)=>'#'+hex(h).map(v=>Math.round(clamp(v+(a>0?255-v:v)*a,0,255)).toString(16).padStart(2,'0')).join('');
//Хранилище: IndexedDB + localStorage, статус//
function vxSt(t,bad){const e=$('#vst');if(!e)return;e.textContent=t;e.style.color=bad?'var(--dg)':'';e.style.opacity=bad?1:.6}
const vdb=()=>new Promise((res,rej)=>{try{const r=indexedDB.open('vibe',1);r.onupgradeneeded=()=>r.result.createObjectStore('s');r.onsuccess=()=>res(r.result);r.onerror=()=>rej(r.error)}catch(e){rej(e)}});
const vput=async j=>{const d=await vdb();await new Promise((res,rej)=>{const t=d.transaction('s','readwrite');t.objectStore('s').put(j,'state');t.oncomplete=res;t.onerror=()=>rej(t.error)})};
const vget=async()=>{const d=await vdb();return new Promise((res,rej)=>{const q=d.transaction('s').objectStore('s').get('state');q.onsuccess=()=>res(q.result);q.onerror=()=>rej(q.error)})};
async function vxStore(o){D.ts=o.ts;const j=JSON.stringify(o);let ok=0;
 try{localStorage.setItem('vibe:v2',j);ok=1}catch(e){}
 try{await vput(j);ok=1}catch(e){}
 vxSt(ok?'Сохранено':'Ошибка сохранения',!ok);
 if(!ok)toast('Не сохранено: память недоступна или заполнена. Сделайте копию.')}
//Тема и оформление//
function applyVx(){const s=D.set,r=document.documentElement,st=r.style,th=s.theme||'dark',ac=s.ac||'#f2b800',P=(k,v)=>st.setProperty(k,v),X=k=>st.removeProperty(k);
 P('--ac',ac);P('--acx',lum(ac)>.55?'#1a1400':'#fff');P('--sel',(s.sel||ac)+'59');
 ['--bg','--s1','--s2','--s3','--tx','--mu','--ln','--glass'].forEach(X);let cs='dark';
 if(th=='light'){cs='light';Object.entries({'--bg':'#f5f3ee','--s1':'#ffffff','--s2':'#eceae4','--s3':'#dcd9d1','--tx':'#1b1b1a','--mu':'#6f6e69','--ln':'#e0ddd5','--glass':'rgba(255,255,255,.94)'}).forEach(([k,v])=>P(k,v))}
 else if(th=='custom'){const b=s.bgc||'#101820',f=s.sfc||'#1b2733',d=lum(b)<.5;cs=d?'dark':'light';
  P('--bg',b);P('--s1',f);P('--s2',shade(f,d?.07:-.06));P('--s3',shade(f,d?.14:-.12));P('--ln',shade(f,d?.1:-.1));P('--tx',d?'#f4f4f1':'#1b1b1a');P('--mu',d?'#9a9a95':'#6f6e69');P('--glass','rgba('+hex(f).join(',')+',.94)')}
 P('color-scheme',cs);{const w=WP[s.wp];P('--wp',w?'url("'+wpURL(w,ac)+'")':'none');P('--wps',(w?w[1]:64)+'px')}P('--fw',s.fw||400);P('--isz',(s.isz||24)+'px');P('--sw',s.isw||1.9);P('--r',(s.rad||22)+'px');P('--cb',(s.cb||48)+'px');P('--pd',(s.pd||16)+'px');
 if(s.ntx)P('--ntx',s.ntx);else X('--ntx');
 const m=document.querySelector('meta[name=theme-color]');if(m)m.content=getComputedStyle(r).getPropertyValue('--bg').trim()||'#000'}
function vxPaper(p){sheetEl.dataset.paper=p.paper||'cream';sheetEl.dataset.rule=p.rule||'lines';const s=sheetEl.style;
 if(p.bg){const L=lum(p.bg)>.5;s.setProperty('--pbg',p.bg);s.setProperty('--pink',L?'#1b1b1b':'#ececea');s.setProperty('--pmu',L?'#6f6e69':'#a0a09b');s.setProperty('--pr',L?'rgba(0,0,0,.14)':'rgba(255,255,255,.14)')}
 else['--pbg','--pink','--pmu','--pr'].forEach(x=>s.removeProperty(x))}
const DEF={theme:'dark',fw:'400',pd:'16',sort:'up',hold:'2000',pen:'menu'};
const vxCmp=(x,y)=>D.set.sort=='title'?(x.t||'').localeCompare(y.t||'','ru'):D.set.sort=='cr'?y.cr-x.cr:y.up-x.up;
const _ss=settingsSheet;
settingsSheet=function(){_ss();const e=$$('.sh').pop(),s=D.set;
 const sw=(k,a)=>a.map(c=>'<button data-k="'+k+'" data-v="'+c+'" style="background:'+c+'"></button>').join('');
 const rg=(k,l,a,b,st,d)=>'<div class="setr"><span>'+l+'</span><input type="range" data-r="'+k+'" min="'+a+'" max="'+b+'" step="'+st+'" value="'+(s[k]!=null?s[k]:d)+'" style="width:42%;accent-color:var(--ac)"></div>';
 const op=(k,l,o)=>'<div class="setr"><span>'+l+'</span><div class="opt" data-o="'+k+'">'+o.map(x=>'<button data-v="'+x[0]+'">'+x[1]+'</button>').join('')+'</div></div>';
 const co=(k,l,d)=>'<div class="setr"><span>'+l+'</span><input type="color" data-c="'+k+'" value="'+(s[k]||d)+'"></div>';
 const tg=(k,l)=>'<div class="setr"><span>'+l+'</span><button class="tg" data-t="'+k+'"></button></div>';
 e.insertAdjacentHTML('beforeend','<div class="lbl">Оформление Vibe</div>'
  +op('theme','Тема',[['dark','Тёмная'],['light','Светлая'],['custom','Своя']])
  +'<div class="setr"><span>Акцент</span><div class="sw" style="gap:8px">'+sw('ac',['#f2b800','#ff7a45','#ef476f','#b36bff','#4c8dff','#22c3a6','#7ccf4a'])+'</div></div>'
  +co('ac','Свой акцент','#f2b800')+co('bgc','Фон (своя тема)','#101820')+co('sfc','Цвет интерфейса (своя тема)','#1b2733')
  +co('ntx','Цвет текста заметок','#222222')+co('sel','Цвет выделения','#f2b800')
  +op('fw','Жирность текста',[['400','Обычная'],['500','Средняя'],['600','Жирная']])
  +rg('lh','Межстрочный интервал',1.5,2.4,.1,1.9)+rg('isz','Размер иконок',20,32,1,24)+rg('isw','Толщина иконок',1.2,2.6,.1,1.9)
  +rg('rad','Скругление',8,32,1,22)+rg('cb','Размер кнопок',44,60,1,48)
  +op('pd','Плотность',[['10','Плотно'],['16','Обычно'],['22','Свободно']])
  +op('sort','Сортировка',[['up','Изменено'],['cr','Создано'],['title','Название']])
  +op('hold','Удержание для меню',[['200','0,2 с'],['400','0,4 с'],['600','0,6 с'],['1000','1 с'],['2000','2 с']])
  +tg('cdel','Подтверждать удаление страниц')+tg('relock','Закрывать хранилище после заметки')+tg('lkt','Название и обложка защищённых видны в списке')+op('pen','Кнопка карандаша',[['menu','Меню создания'],['note','Новая заметка']])+'<div class="lbl">Главный экран</div>'+tg('dfin','Финансы')+tg('drate','Курсы валют')+tg('dcal','События')+tg('dfav','Избранные заметки')+'<div class="lbl">Обои</div><div style="display:flex;flex-wrap:wrap;gap:8px;padding-bottom:12px"><button class="btn wpb" data-k="wp" data-v="0" style="height:40px;padding:0 14px">Нет</button>'+WPK.map(k=>'<button class="btn wpb" data-k="wp" data-v="'+k+'" style="height:40px;padding:0 14px">'+WP[k][0]+'</button>').join('')+'</div>');
 const paint=()=>{$$('[data-o]',e).forEach(o=>$$('button',o).forEach(b=>b.classList.toggle('on',String(s[o.dataset.o]!=null?s[o.dataset.o]:DEF[o.dataset.o])==b.dataset.v)));
  $$('[data-t]',e).forEach(b=>b.classList.toggle('on',s[b.dataset.t]!==false));$$('[data-k]',e).forEach(b=>b.classList.toggle('on',(s[b.dataset.k]||(b.dataset.k=='ac'?'#f2b800':'0'))==b.dataset.v))};paint();
 e.addEventListener('click',x=>{const b=x.target.closest('button');if(!b)return;const o=b.closest('[data-o]');
  if(b.dataset.k)s[b.dataset.k]=b.dataset.v;
  else if(o){const k=o.dataset.o;s[k]=k=='hold'?+b.dataset.v:b.dataset.v}
  else if(b.dataset.t){const k=b.dataset.t;s[k]=s[k]===false}else return;
  applySet();paint();save();buzz(5)});
 e.addEventListener('input',x=>{const t=x.target,k=t.dataset.r||t.dataset.c;if(!k)return;s[k]=t.dataset.r?+t.value:t.value;if(k=='bgc'||k=='sfc')s.theme='custom';applySet();paint();save()})};
//Папки и пароли//
async function moveTo(n,id){const f=fById(id);
 if((f&&f.lk)||(n.flk&&!(f&&f.lk))){if(!(await needKey()))return false}
 n.fo=id;if(f&&f.lk){n.lk=1;n.flk=1}else if(n.flk){n.lk=0;n.flk=0;n.enc=null}
 n.up=Date.now();save();render();return true}
async function lockFolder(f){if(!(await needKey()))return;f.lk=f.lk?0:1;
 D.notes.forEach(n=>{if(n.fo!=f.id)return;if(f.lk){if(!n.lk){n.lk=1;n.flk=1}}else if(n.flk){n.lk=0;n.flk=0;n.enc=null}});
 await persist();renderDrawer();render();toast(f.lk?'Папка под паролем':'Пароль с папки снят')}
//Теги и копии//
function tagSheet(n){const sh=sheet('<h3>Теги</h3><div id="tgl" style="display:flex;flex-wrap:wrap;gap:8px;margin-bottom:12px"></div><input class="in" id="tgi" placeholder="Новый тег" autocomplete="off"><button class="btn pri" style="width:100%" id="tgo">Добавить</button>');
 const e=sh.el,paint=()=>{const all=[...new Set(D.notes.flatMap(x=>x.tags||[]))];$('#tgl',e).innerHTML=all.map(t=>'<button class="btn'+((n.tags||[]).includes(t)?' pri':'')+'" data-t="'+esc(t)+'" style="height:40px;padding:0 14px">#'+esc(t)+'</button>').join('')||'<span class="sub">Тегов пока нет</span>'};paint();
 const add=()=>{const v=$('#tgi',e).value.trim().replace(/^#/,'');if(!v)return;n.tags=n.tags||[];if(!n.tags.includes(v))n.tags.push(v);$('#tgi',e).value='';save();render();paint()};
 $('#tgo',e).onclick=add;$('#tgi',e).onkeydown=x=>{if(x.key=='Enter')add()};
 $('#tgl',e).onclick=x=>{const b=x.target.closest('[data-t]');if(!b)return;n.tags=n.tags||[];const t=b.dataset.t,i=n.tags.indexOf(t);i<0?n.tags.push(t):n.tags.splice(i,1);save();render();paint()}}
async function dupNote(n){if(n.lk&&!KEY){toast('Сначала откройте хранилище');return}
 const c=JSON.parse(JSON.stringify(n));c.id=uid();c.t=(n.t||'Без названия')+' (копия)';c.pin=0;c.cr=c.up=Date.now();
 for(const p of c.pg){const o=p.id;p.id=uid();if(p.dr){const b=await bget('dr:'+o);if(b)await bset('dr:'+p.id,b);else p.dr=0}p.au=[]}
 D.notes.unshift(c);save();render();toast('Копия создана')}
//Страницы: защита, подтверждение, отмена, порядок//
const guard=()=>{if(ED.n&&ED.n.pgl){toast('Страницы защищены. Снимите защиту в меню «Страница»');buzz([15,40,15]);return true}return false};
const askOk=(title,sub,ok)=>new Promise(res=>{let d=0;const f=v=>{if(!d){d=1;res(v)}};
 const sh=sheet('<h3>'+esc(title)+'</h3><p class="sub">'+esc(sub)+'</p><div class="row"><button class="btn" data-n>Отмена</button><button class="btn pri" data-y>'+esc(ok)+'</button></div>',()=>f(false));
 $('[data-n]',sh.el).onclick=()=>sh.close();$('[data-y]',sh.el).onclick=()=>{f(true);sh.close()}});
function rmPage(p){const n=ED.n,i=n.pg.indexOf(p);if(i<0||n.pg.length<2)return -1;saveHtml();flushDraw();n.pg.splice(i,1);ED.pi=clamp(ED.pi>i?ED.pi-1:ED.pi,0,n.pg.length-1);n.ci=ED.pi;loadPage();save();return i}
function addPage(){if(guard())return;const n=ED.n,c=curP(),p=mkPage();p.paper=c.paper;p.rule=c.rule;p.bg=c.bg;n.pg.splice(ED.pi+1,0,p);goPage(ED.pi+1,1);save();
 toast('Страница '+(ED.pi+1)+' добавлена',{act:'Отменить',f:()=>{if(ED.n===n)rmPage(p)}})}
async function delPage(p){if(guard())return;const n=ED.n;if(n.pg.length<2){toast('Нельзя удалить единственную страницу');return}
 if(D.set.cdel!==false&&!(await askOk('Удалить страницу?','Текст страницы будет удалён. Сразу после этого удаление можно отменить.','Удалить')))return;
 const i=rmPage(p);if(i<0)return;
 toast('Страница удалена',{act:'Вернуть',f:()=>{n.pg.splice(i,0,p);if(ED.n===n){ED.pi=i;n.ci=i;loadPage()}save()}})}
async function dupPage(p){if(guard())return;const n=ED.n;saveHtml();const q=JSON.parse(JSON.stringify(Object.assign({},p,{au:[]})));q.id=uid();
 if(p.dr){const b=await bget('dr:'+p.id);if(b)await bset('dr:'+q.id,b);else q.dr=0}n.pg.splice(n.pg.indexOf(p)+1,0,q);save();toast('Страница продублирована')}
function movePage(q,d){if(guard())return;const n=ED.n,i=n.pg.indexOf(q),j=i+d;if(j<0||j>=n.pg.length)return;const cur=curP();saveHtml();[n.pg[i],n.pg[j]]=[n.pg[j],n.pg[i]];ED.pi=n.pg.indexOf(cur);n.ci=ED.pi;pager();save()}
function pageSheet(){const n=ED.n;saveHtml();
 const sh=sheet('<h3>Страница</h3><div class="lbl" style="margin-top:0">Бумага и цвет</div><div class="sw" id="pps"></div><div class="lbl">Разметка</div><div class="rl" id="prl"></div><div class="setr" style="margin-top:8px"><span>Защитить страницы от изменений</span><button class="tg" id="pgl" aria-label="Защита"></button></div><div class="lbl">Страницы блокнота</div><div id="pgm"></div><div class="row"><button class="btn pri" id="pga">Новая страница</button></div>');
 const e=sh.el,paint=()=>{const p=curP();
  $('#pps',e).innerHTML=Object.keys(PAPERS).map(k=>'<button data-p="'+k+'" class="'+(!p.bg&&p.paper==k?'on':'')+'" style="background:'+PAPERS[k]+';box-shadow:inset 0 0 0 1px #3a3a3a"></button>').join('')+'<input type="color" id="pbg" value="'+(p.bg||'#f0e6cc')+'" style="width:46px;height:46px;border:0;padding:0;border-radius:50%;background:none">';
  $('#prl',e).innerHTML=[['lines','Линейка'],['grid','Клетка'],['dots','Точки'],['none','Чистая']].map(r=>'<button data-r="'+r[0]+'" class="'+(p.rule==r[0]?'on':'')+'"><i></i>'+r[1]+'</button>').join('');
  $('#pgl',e).classList.toggle('on',!!n.pgl);
  $('#pgm',e).innerHTML=n.pg.map((q,i)=>'<div class="setr" data-i="'+i+'"><span data-go>'+(i+1)+'. '+esc(q.name||txt(q.h).slice(0,22)||'Пустая')+(q===p?' ●':'')+'</span><button class="btn" data-a="up" aria-label="Выше">↑</button><button class="btn" data-a="dn" aria-label="Ниже">↓</button><button class="btn" data-a="du" aria-label="Дублировать">⧉</button><button class="btn" data-a="rn" aria-label="Переименовать">✎</button><button class="btn dg" data-a="de" aria-label="Удалить">✕</button></div>').join('')};paint();
 e.addEventListener('input',x=>{if(x.target.id=='pbg'){const p=curP();p.bg=x.target.value;vxPaper(p);save()}});
 e.addEventListener('click',async x=>{const b=x.target.closest('button,[data-go]');if(!b)return;const p=curP();
  if(b.dataset.p){p.paper=b.dataset.p;p.bg='';applyPaper(p)}
  else if(b.dataset.r){p.rule=b.dataset.r;applyPaper(p)}
  else if(b.id=='pgl'){n.pgl=n.pgl?0:1}
  else if(b.id=='pga'){sh.close();setTimeout(addPage,250);return}
  else if('go' in b.dataset)goPage(+b.closest('[data-i]').dataset.i);
  else if(b.dataset.a){const q=n.pg[+b.closest('[data-i]').dataset.i],a=b.dataset.a;
   if(a=='up'||a=='dn')movePage(q,a=='up'?-1:1);else if(a=='du')await dupPage(q);
   else if(a=='rn'){if(!guard()){const v=await askText({title:'Название страницы',value:q.name||'',empty:1});if(v!=null)q.name=v}}
   else if(a=='de')await delPage(q)}
  else return;save();paint()})}
$('#tpage').onclick=pageSheet;
//Нижняя панель форматирования: свайп, цвет текста//
function fpSet(on){$('#fp').classList.toggle('on',on);$('#tfmt').classList.toggle('on',on);edEl.classList.toggle('fpopen',on);if(on)refreshTools()}
$('#tfmt').onclick=()=>{buzz(5);fpSet(!$('#fp').classList.contains('on'))};
$('#fp').insertAdjacentHTML('beforeend',['','#d64541','#2f6fd6','#2e9e5b','#8a4fd1'].map(c=>'<button data-fc="'+c+'" aria-label="Цвет текста"><span style="width:26px;height:26px;border-radius:50%;display:block;margin:auto;background:'+(c||'#999')+';box-shadow:inset 0 0 0 2px var(--ln)"></span></button>').join(''));
$$('#fp [data-fc]').forEach(b=>b.addEventListener('click',()=>{buzz(5);exec('foreColor',b.dataset.fc||getComputedStyle(sheetEl).getPropertyValue('--pink').trim()||'#222');refreshTools()}));
['#fp','#tools','.etop','#pg'].forEach(s=>$$(s).forEach(x=>x.addEventListener('pointerdown',()=>{window.vxTb=Date.now()},true)));
//Свайпы: боковое меню и панель//
let tx0=null;
document.addEventListener('touchstart',e=>{tx0=e.touches.length==1?{x:e.touches[0].clientX,y:e.touches[0].clientY,t:e.target}:null},{passive:true});
document.addEventListener('touchend',e=>{if(!tx0)return;const t=e.changedTouches[0],dx=t.clientX-tx0.x,dy=t.clientY-tx0.y,s=tx0;tx0=null;
 if(Math.abs(dx)>70&&Math.abs(dx)>Math.abs(dy)*2){
  if(drawerOn&&dx<0)closeDrawer();
  else if(!drawerOn&&dx>0&&!ED.n&&!(G&&G.armed)&&!$('.sh.on')&&!$('.mo')&&!$('.vw')&&!$('.pinov'))openDrawer()}
 else if(ED.n&&Math.abs(dy)>45&&Math.abs(dy)>Math.abs(dx)*1.5&&s.t.closest&&s.t.closest('#tools,#fp'))fpSet(dy<0)},{passive:true});
//Резервная копия: файл, проверка, вложения//
const b2s=b=>new Promise(r=>{const f=new FileReader();f.onload=()=>r(f.result);f.readAsDataURL(b)});
async function exportData(){if(KEY)for(const n of D.notes)if(n.lk)n.enc=await enc({t:n.t,pg:n.pg});
 const bl={};for(const n of D.notes){if(n.lk)continue;for(const p of n.pg){if(p.dr){const b=await bget('dr:'+p.id);if(b)bl['dr:'+p.id]=await b2s(b)}for(const a of p.au||[]){const b=await bget('au:'+a.id);if(b)bl['au:'+a.id]=await b2s(b)}}}
 return{app:'vibe',ver:2,ts:Date.now(),notes:D.notes.map(n=>n.lk?Object.assign({},n,{t:D.set.lkt===false?'':n.t,pg:[]}):n),folders:D.folders,tasks:D.tasks,cal:D.cal,fin:D.fin,items:D.items,vault:D.vault,set:D.set,blobs:bl}}
async function importData(t,sh){let o;try{o=JSON.parse(t)}catch(e){toast('Файл повреждён: это не копия Vibe');return}
 if(!o||!Array.isArray(o.notes)||o.notes.some(n=>!n||!n.id||!Array.isArray(n.pg))||(o.folders&&!Array.isArray(o.folders))||(o.tasks&&!Array.isArray(o.tasks))){toast('Файл не похож на копию заметок');return}
 const have=new Set(D.notes.map(n=>n.id));let add=o.notes.filter(n=>!have.has(n.id)),skip=0;
 if(o.vault&&D.vault&&o.vault.salt!=D.vault.salt){const k=add.filter(n=>!n.lk);skip=add.length-k.length;add=k}
 if(!(await askOk('Восстановить копию?','Будет добавлено заметок: '+add.length+(skip?'. Пропущено защищённых (другой пароль): '+skip:'')+'. Существующие заметки не изменятся.','Добавить')))return;
 if(!D.vault&&o.vault)D.vault=o.vault;
 for(const k in(o.blobs||{})){try{await bset(k,await (await fetch(o.blobs[k])).blob())}catch(e){}}
 add.forEach(n=>D.notes.push(n));(o.folders||[]).forEach(f=>{if(f&&f.id&&!fById(f.id))D.folders.push(f)});(o.tasks||[]).forEach(t=>{if(t&&t.id&&!D.tasks.some(x=>x.id==t.id))D.tasks.push(t)});
 save();render();renderDrawer();sh.close();toast('Добавлено заметок: '+add.length)}
function backupSheet(){const sh=sheet('<h3>Резервная копия</h3><p class="sub">Заметки, папки, задачи, настройки, рисунки и записи. Защищённые заметки остаются зашифрованными.</p><div class="row"><button class="btn pri" data-a="ex">Сохранить файл</button><button class="btn" data-a="im">Открыть файл</button></div><input type="file" id="bf" accept="application/json,.json" hidden><div class="lbl">Или вставьте текст копии</div><textarea class="in" id="bt" spellcheck="false"></textarea><button class="btn" style="width:100%" data-a="pi">Восстановить из текста</button>');
 const e=sh.el;e.onclick=async x=>{const b=x.target.closest('button');if(!b||!b.dataset.a)return;const a=b.dataset.a;
  if(a=='ex'){try{const o=await exportData(),u=URL.createObjectURL(new Blob([JSON.stringify(o)],{type:'application/json'})),l=document.createElement('a');l.href=u;l.download='vibe-backup-'+new Date().toISOString().slice(0,10)+'.json';document.body.append(l);l.click();l.remove();setTimeout(()=>URL.revokeObjectURL(u),4000);toast('Копия сохранена в загрузки')}catch(err){toast('Не удалось создать копию')}}
  else if(a=='im')$('#bf',e).click();else if(a=='pi')importData($('#bt',e).value,sh)};
 $('#bf',e).onchange=async x=>{const f=x.target.files[0];if(f)importData(await f.text(),sh)}}
//Запуск слоя//
document.body.insertAdjacentHTML('beforeend','<div id="vst">Сохранено</div>');
D.notes.forEach(n=>n.pg.forEach(p=>{if(!p.id)p.id=uid()}));
document.addEventListener('visibilitychange',()=>{if(document.hidden){saveHtml();persist()}});
(async()=>{try{navigator.storage&&navigator.storage.persist&&navigator.storage.persist()}catch(e){}
 try{const j=await vget();if(j){const o=JSON.parse(j);if(o&&o.notes&&(o.ts||0)>(D.ts||0)&&!ED.n){D=o;D.set=Object.assign({font:'onest',fs:17,paper:'cream',rule:'lines',anim:true,vib:true},o.set||{});D.folders=o.folders||[];D.tasks=o.tasks||[];vxInit();applySet();render();renderDrawer()}}vxSt('Сохранено')}
 catch(e){let ls=1;try{localStorage.setItem('vibe:t','1')}catch(x){ls=0}if(!ls){vxSt('Хранилище недоступно',1);toast('Браузер не даёт сохранять данные. Откройте Vibe по обычному адресу и делайте копии.')}}})();
//Vibe v3: PIN, разделы, обои//
Object.assign(P,{wallet:'M3 7h16a2 2 0 012 2v9a2 2 0 01-2 2H5a2 2 0 01-2-2zM3 7l2-3h12v3M16 13h3',calc:'M5 3h14v18H5zM8 7h8M8 12h2M14 12h2M8 16h2M14 16h2',chart:'M4 20V4M4 20h16M8 16v-4M12 16V8M16 16v-6',sched:'M4 5h16v15H4zM4 10h16M9 3v4M15 3v4M8 14h4',aL:'M4 6h16M4 10h10M4 14h16M4 18h10',aC:'M4 6h16M7 10h10M4 14h16M7 18h10',aR:'M4 6h16M10 10h10M4 14h16M10 18h10',quote:'M6 8h5v5H6zM6 13c0 3 1 4 3 5M14 8h5v5h-5zM14 13c0 3 1 4 3 5',hr:'M3 12h18M7 7h10M7 17h10',indent:'M4 6h16M10 10h10M10 14h10M4 18h16M4 9l3 3-3 3',link:'M10 14a4 4 0 005.7 0l3-3a4 4 0 00-5.7-5.7l-1 1M14 10a4 4 0 00-5.7 0l-3 3a4 4 0 005.7 5.7l1-1',clr:'M4 7h10M9 7v10M14 14l6 6M20 14l-6 6',big:'M5 18l4-12 4 12M6.5 14h5M17 6v6M14 9h6',small:'M5 18l4-12 4 12M6.5 14h5M14 15h6'});
//PIN-панель (как код в Telegram)//
function askPass(o){return new Promise(res=>{let v='',st=0,f1='';
 const ov=el('div','pinov','<button class="cbtn" aria-label="Назад">'+ic('back')+'</button><div class="pt"></div><div class="ps"></div><div class="pd">'+'<i></i>'.repeat(4)+'</div><div class="pk">'+[1,2,3,4,5,6,7,8,9,'',0,'⌫'].map(k=>k===''?'<span></span>':'<button data-k="'+k+'">'+k+'</button>').join('')+'</div>'),
 T=$('.pt',ov),S=$('.ps',ov),PD=$('.pd',ov),ds=$$('i',ov);
 const txt=()=>{T.textContent=st?'Повторите код':o.title;S.textContent=st?'':(o.hint||'')},draw=()=>ds.forEach((d,i)=>d.classList.toggle('on',i<v.length));
 const end=r=>{document.removeEventListener('keydown',kd);ov.classList.remove('on');setTimeout(()=>ov.remove(),250);res(r)};
 const bad=m=>{S.textContent=m;PD.classList.add('shake');buzz([20,40,20]);setTimeout(()=>{PD.classList.remove('shake');v='';draw()},420)};
 const go=async()=>{if(v.length<4)return;
  if(o.confirm){if(!st){f1=v;v='';st=1;txt();draw();return}if(v!==f1){st=0;f1='';txt();bad('Коды не совпали. Попробуйте снова');return}}
  else if(o.verify&&!(await o.verify(v)))return bad('Неверный код');end(v)};
 const key=k=>{if(k=='⌫')v=v.slice(0,-1);else if(v.length<4)v+=k;draw();if(v.length==4)setTimeout(go,140)};
 const kd=e=>{if(/^\d$/.test(e.key))key(e.key);else if(e.key=='Backspace')key('⌫');else if(e.key=='Escape')end(null)};
 ov.onclick=e=>{const b=e.target.closest('button');if(!b)return;buzz(6);b.dataset.k?key(b.dataset.k):end(null)};
 document.addEventListener('keydown',kd);txt();document.body.append(ov);requestAnimationFrame(()=>ov.classList.add('on'))})}
//Больше инструментов форматирования//
$('#fp').insertAdjacentHTML('beforeend',[['aL','justifyLeft'],['aC','justifyCenter'],['aR','justifyRight'],['quote','formatBlock','blockquote'],['hr','insertHorizontalRule'],['indent','indent'],['link','link'],['clr','removeFormat'],['big','fontSize','5'],['small','fontSize','2']].map(x=>'<button data-x="'+x[1]+'" data-a="'+(x[2]||'')+'" aria-label="'+x[1]+'">'+ic(x[0])+'</button>').join(''));
$$('#fp [data-x]').forEach(b=>b.addEventListener('click',async()=>{buzz(5);const c=b.dataset.x;if(c=='link'){const u=await askText({title:'Ссылка',ph:'https://'});if(u)exec('createLink',/^https?:/.test(u)?u:'https://'+u)}else exec(c,b.dataset.a||null);refreshTools()}));
//Обои//
const WP={snow:['Снег',64,'<g fill="@"><circle cx="10" cy="12" r="2"/><circle cx="40" cy="30" r="1.6"/><circle cx="24" cy="50" r="2.2"/></g><path d="M52 8v10M47 13h10M49 10l6 6M55 10l-6 6" stroke="@" fill="none" stroke-linecap="round"/>'],tree:['Ёлки',64,'<path d="M16 6l8 12h-5l7 10H6l7-10H8z" fill="@"/><path d="M48 36l6 9h-4l6 8H38l6-8h-4z" fill="@"/>'],sun:['Лето',60,'<path d="M0 22q10-10 20 0t20 0t20 0M0 46q10-10 20 0t20 0t20 0" fill="none" stroke="@" stroke-width="2"/><circle cx="50" cy="8" r="4" fill="@"/>'],spr:['Весна',64,'<g fill="@"><circle cx="20" cy="14" r="4"/><circle cx="26" cy="20" r="4"/><circle cx="20" cy="26" r="4"/><circle cx="14" cy="20" r="4"/><circle cx="48" cy="46" r="3"/><circle cx="53" cy="51" r="3"/><circle cx="48" cy="56" r="3"/><circle cx="43" cy="51" r="3"/></g>'],leaf:['Листья',56,'<path d="M10 42c0-14 10-24 26-26 0 16-10 26-26 26zM10 42l16-16" fill="none" stroke="@" stroke-width="2"/>'],game:['Игры',56,'<g fill="@"><rect x="8" y="8" width="8" height="8"/><rect x="32" y="24" width="8" height="8"/><rect x="16" y="40" width="8" height="8"/></g><path d="M46 6v12M40 12h12" stroke="@" stroke-width="3"/>'],space:['Космос',64,'<path d="M12 8v8M8 12h8M44 36v6M41 39h6" stroke="@" stroke-width="2"/><g fill="@"><circle cx="36" cy="10" r="1.5"/><circle cx="10" cy="44" r="2"/><circle cx="52" cy="56" r="1.5"/></g>'],heart:['Сердца',56,'<path d="M20 34l-9-9a5 5 0 017-7l2 2 2-2a5 5 0 017 7z" fill="@"/>'],geo:['Геометрия',64,'<path d="M8 8h16L16 22zM40 36h16L48 50z" fill="none" stroke="@" stroke-width="2"/><circle cx="46" cy="14" r="5" fill="none" stroke="@" stroke-width="2"/>'],dots:['Точки',32,'<circle cx="8" cy="8" r="2" fill="@"/><circle cx="24" cy="24" r="2" fill="@"/>']};
const WPK=Object.keys(WP),wpURL=(w,c)=>'data:image/svg+xml,'+encodeURIComponent('<svg xmlns="http://www.w3.org/2000/svg" width="'+w[1]+'" height="'+w[1]+'" opacity=".16">'+w[2].replace(/@/g,'rgb('+hex(c).join(',')+')')+'</svg>');
//Общие помощники//
const SYM={RUB:'₽',USD:'$',EUR:'€',UAH:'₴',KZT:'₸',BYN:'Br',GBP:'£',CNY:'¥',JPY:'¥',TRY:'₺',PLN:'zł'},FB={USD:1,EUR:.92,RUB:92,UAH:41,KZT:480,BYN:3.3,GBP:.79,CNY:7.2,JPY:150,TRY:34,PLN:4};
const PAL=['#f2b800','#ff7a45','#ef476f','#b36bff','#4c8dff','#22c3a6','#7ccf4a','#8d99ae'],pcol=i=>PAL[i%PAL.length],evCols=PAL.map((c,i)=>[c,['Жёлтый','Оранжевый','Красный','Фиолетовый','Синий','Бирюзовый','Зелёный','Серый'][i]]);
const ymd=d=>d.getFullYear()+'-'+String(d.getMonth()+1).padStart(2,'0')+'-'+String(d.getDate()).padStart(2,'0'),mk=d=>d.slice(0,7),dm=d=>d.slice(5).split('-').reverse().join('.');
const RT=()=>(D.rates&&D.rates.r)||FB,cvt=(a,f,t)=>a/RT()[f]*RT()[t],fm=n=>Math.round(n).toLocaleString('ru-RU')+' '+SYM[D.fin.cur];
function vxInit(){D.cal=D.cal||[];D.items=D.items||[];const f=D.fin=D.fin||{};['cards','tx','subs','goals'].forEach(k=>f[k]=f[k]||[]);f.cur=f.cur||'RUB'}
vxInit();
async function loadRates(){if(D.rates&&Date.now()-D.rates.t<216e5)return;try{const j=await(await fetch('https://open.er-api.com/v6/latest/USD')).json(),o={};for(const k in FB)if(j.rates&&j.rates[k])o[k]=j.rates[k];if(o.RUB){D.rates={r:o,t:Date.now()};save();dash()}}catch(e){}}
function form(title,fs,ok,extra){return new Promise(res=>{let d=0;const fin=v=>{if(!d){d=1;res(v)}};
 const sh=sheet('<h3>'+esc(title)+'</h3>'+fs.map(f=>'<div class="lbl" style="margin:10px 0 4px">'+f.l+'</div>'+(f.t=='sel'?'<select class="in" data-k="'+f.k+'">'+f.o.map(o=>'<option value="'+esc(o[0])+'"'+(o[0]==f.v?' selected':'')+'>'+esc(o[1])+'</option>').join('')+'</select>':f.t=='area'?'<textarea class="in" data-k="'+f.k+'" rows="6">'+esc(f.v||'')+'</textarea>':'<input class="in" data-k="'+f.k+'" type="'+(f.t||'text')+'" value="'+esc(f.v==null?'':f.v)+'"'+(f.t=='number'?' inputmode="decimal" step="any"':'')+'>')).join('')+'<div class="row">'+(extra?'<button class="btn dg" data-x>'+extra+'</button>':'')+'<button class="btn pri" data-ok>'+ok+'</button></div>',()=>fin(null));
 $('[data-ok]',sh.el).onclick=()=>{const o={};$$('[data-k]',sh.el).forEach(i=>o[i.dataset.k]=i.type=='number'?parseFloat(String(i.value).replace(',','.')):i.value);fin(o);sh.close()};
 const x=$('[data-x]',sh.el);if(x)x.onclick=()=>{fin('del');sh.close()}})}
function VW(title,build,act){const v=el('div','vw','<div class="vh"><button class="cbtn" aria-label="Назад">'+ic('back')+'</button><h2>'+esc(title)+'</h2>'+(act?'<button class="cbtn pri" data-act aria-label="Добавить">'+ic('plus')+'</button>':'<span style="width:var(--cb)"></span>')+'</div><div class="vb"></div>'),b=$('.vb',v);
 const rf=()=>{const y=b.scrollTop;build(b,rf);b.scrollTop=y};
 $('.cbtn',v).onclick=()=>{v.classList.remove('on');setTimeout(()=>{v.remove();dash()},250)};
 if(act)$('[data-act]',v).onclick=()=>act(rf);
 document.body.append(v);rf();requestAnimationFrame(()=>v.classList.add('on'));return v}
//Графики (SVG)//
function donut(a){const T=a.reduce((s,x)=>s+x.v,0)||1,C=2*Math.PI*40;let o=0;return'<svg class="ch" viewBox="0 0 120 120" style="max-width:190px;display:block;margin:auto">'+a.map(x=>{const l=x.v/T*C,s='<circle cx="60" cy="60" r="40" fill="none" stroke="'+x.c+'" stroke-width="18" stroke-dasharray="'+l+' '+(C-l)+'" stroke-dashoffset="'+(-o)+'" transform="rotate(-90 60 60)"/>';o+=l;return s}).join('')+'<text x="60" y="64" text-anchor="middle" font-size="12" font-weight="700" fill="currentColor" stroke="none">'+Math.round(T).toLocaleString('ru-RU')+'</text></svg>'}
function bars(a,two){const mx=Math.max(1,...a.flatMap(x=>two?[x.v,x.w]:[x.v])),W=300/a.length,h=v=>v/mx*100;return'<svg class="ch" viewBox="0 0 300 150">'+a.map((x,i)=>{const bw=two?W*.32:W*.55,x0=i*W+(two?W*.14:W*.22);return'<rect x="'+x0+'" y="'+(118-h(x.v))+'" width="'+bw+'" height="'+h(x.v)+'" rx="4" fill="'+(two?'#2e9e5b':x.c)+'" stroke="none"/>'+(two?'<rect x="'+(x0+bw+2)+'" y="'+(118-h(x.w))+'" width="'+bw+'" height="'+h(x.w)+'" rx="4" fill="#d64541" stroke="none"/>':'<text x="'+(x0+bw/2)+'" y="'+(114-h(x.v))+'" font-size="9" text-anchor="middle" fill="currentColor" stroke="none">'+x.v+'</text>')+'<text x="'+(i*W+W/2)+'" y="136" font-size="10" text-anchor="middle" fill="var(--mu)" stroke="none">'+esc(x.l)+'</text>'}).join('')+'</svg>'}
function line(a){const mx=Math.max(1,...a.map(x=>x.v)),mn=Math.min(0,...a.map(x=>x.v)),W=280/Math.max(1,a.length-1),p=a.map((x,i)=>[10+i*W,112-(x.v-mn)/(mx-mn||1)*92]),d=p.map(q=>q.join(',')).join('L');return'<svg class="ch" viewBox="0 0 300 150"><path d="M'+d+'L'+p[p.length-1][0]+',118L10,118z" fill="var(--ac)" opacity=".18" stroke="none"/><path d="M'+d+'" fill="none" stroke="var(--ac)" stroke-width="3" stroke-linejoin="round"/>'+p.map((q,i)=>'<circle cx="'+q[0]+'" cy="'+q[1]+'" r="3.5" fill="var(--ac)" stroke="none"/><text x="'+q[0]+'" y="138" font-size="10" text-anchor="middle" fill="var(--mu)" stroke="none">'+esc(a[i].l)+'</text>').join('')+'</svg>'}
const dot=c=>'<b style="width:10px;height:10px;border-radius:50%;background:'+c+';display:block;font-size:0"></b>',lg=a=>a.map(x=>'<div class="li" style="padding:5px 0;border:0">'+dot(x.c)+'<span>'+esc(x.l)+'</span><span class="r">'+x.t+'</span></div>').join('');
//Календарь//
const evOn=(e,d)=>e.d==d||(e.y&&e.d.slice(5)==d.slice(5));
async function evEd(e,d){const n=!e;e=e||{id:uid(),d:d||ymd(new Date()),t:'',c:PAL[0],y:0};
 const r=await form(n?'Событие':'Изменить',[{k:'t',l:'Название',v:e.t},{k:'d',l:'Дата',t:'date',v:e.d},{k:'c',l:'Цвет',t:'sel',v:e.c,o:evCols},{k:'y',l:'Повтор',t:'sel',v:e.y?'1':'0',o:[['0','Не повторять'],['1','Каждый год (день рождения)']]}],'Сохранить',n?'':'Удалить');if(!r)return;
 if(r=='del')D.cal=D.cal.filter(x=>x!==e);else{if(!r.t.trim()||!r.d)return toast('Введите название и дату');Object.assign(e,{t:r.t.trim(),d:r.d,c:r.c,y:+r.y});if(n)D.cal.push(e)}save()}
function openCal(){let t=new Date(),y=t.getFullYear(),m=t.getMonth(),sel=ymd(t);
 VW('Календарь',(b,rf)=>{const off=(new Date(y,m,1).getDay()+6)%7,n=new Date(y,m+1,0).getDate(),td=ymd(new Date());
  let h='<div class="li" style="border:0"><button class="cbtn" data-n="-1">'+ic('back')+'</button><span style="text-align:center;font-weight:700;text-transform:capitalize">'+new Date(y,m,1).toLocaleDateString('ru-RU',{month:'long',year:'numeric'})+'</span><button class="cbtn" data-n="1">'+ic('chev')+'</button></div><div class="cd">'+['Пн','Вт','Ср','Чт','Пт','Сб','Вс'].map(x=>'<small>'+x+'</small>').join('')+'<span></span>'.repeat(off);
  for(let i=1;i<=n;i++){const d=y+'-'+String(m+1).padStart(2,'0')+'-'+String(i).padStart(2,'0'),es=D.cal.filter(e=>evOn(e,d));h+='<button data-d="'+d+'" class="'+(d==td?'td ':'')+(d==sel?'sl ':'')+(es.length?'ev':'')+'"'+(es.length?' style="--ev:'+es[0].c+'"':'')+'>'+i+(es.length?'<i>'+es.slice(0,3).map(e=>'<b style="background:'+e.c+'"></b>').join('')+'</i>':'')+'</button>'}
  const L=D.cal.filter(e=>evOn(e,sel));
  b.innerHTML=h+'</div><div class="lbl" style="margin-top:18px">'+new Date(sel+'T00:00').toLocaleDateString('ru-RU',{day:'numeric',month:'long'})+'</div>'+(L.length?L.map(e=>'<div class="li" data-e="'+e.id+'">'+dot(e.c)+'<span>'+esc(e.t)+(e.y?' <small class="mu">· каждый год</small>':'')+'</span>'+ic('chev')+'</div>').join(''):'<p class="mu">Событий нет</p>')+'<button class="btn pri" style="width:100%;margin-top:10px" data-add>Добавить событие</button>';
  b.onclick=async x=>{const q=s=>x.target.closest(s),N=q('[data-n]'),Dd=q('[data-d]'),E=q('[data-e]');
   if(N){m+=+N.dataset.n;if(m<0){m=11;y--}if(m>11){m=0;y++}rf()}else if(Dd){sel=Dd.dataset.d;rf()}else if(E){await evEd(D.cal.find(z=>z.id==E.dataset.e));rf()}else if(q('[data-add]')){await evEd(null,sel);rf()}}},async rf=>{await evEd(null,sel);rf()})}
//Финансы//
const CATS=['Еда','Транспорт','Дом','Развлечения','Здоровье','Покупки','Подписки','Накопления','Прочее','Доход'],bal=c=>c.bal+D.fin.tx.filter(t=>t.card==c.id).reduce((a,t)=>a+t.amt,0);
const cardOpts=()=>[['','Без карты']].concat(D.fin.cards.map(c=>[c.id,c.name]));
function chargeSubs(){const f=D.fin,now=new Date(),cm=ymd(now).slice(0,7),td=ymd(now);let ch=0;
 f.subs.forEach(s=>{let[y,m]=(s.last||cm).split('-').map(Number);for(let k=0;k<24;k++){m++;if(m>12){m=1;y++}const key=y+'-'+String(m).padStart(2,'0');if(key>cm)break;const dd=key+'-'+String(Math.min(s.day,28)).padStart(2,'0');if(dd>td)break;f.tx.push({id:uid(),card:s.card,amt:-s.amt,cat:'Подписки',d:dd,n:s.name,sub:s.id});s.last=key;ch++}});if(ch)save()}
async function cardEd(c){const n=!c;c=c||{id:uid(),name:'',bal:0,col:PAL[4]};const r=await form(n?'Новая карта':'Карта',[{k:'name',l:'Название',v:c.name},{k:'bal',l:'Начальный баланс',t:'number',v:c.bal},{k:'col',l:'Цвет',t:'sel',v:c.col,o:evCols}],'Сохранить',n?'':'Удалить');if(!r)return 0;
 if(r=='del'){if(!(await askOk('Удалить карту?','Операции по ней тоже будут удалены.','Удалить')))return 0;D.fin.cards=D.fin.cards.filter(x=>x!==c);D.fin.tx=D.fin.tx.filter(t=>t.card!=c.id);return 1}
 Object.assign(c,{name:r.name.trim()||'Карта',bal:r.bal||0,col:r.col});if(n)D.fin.cards.push(c);return 1}
async function txEd(t){const f=D.fin,n=!t;t=t||{id:uid(),card:(f.cards[0]||{}).id||'',amt:0,cat:'Еда',d:ymd(new Date()),n:''};
 const r=await form(n?'Операция':'Изменить',[{k:'k',l:'Тип',t:'sel',v:t.amt>0?'+':'-',o:[['-','Трата'],['+','Пополнение']]},{k:'a',l:'Сумма',t:'number',v:Math.abs(t.amt)||''},{k:'card',l:'Карта',t:'sel',v:t.card,o:cardOpts()},{k:'cat',l:'Категория',t:'sel',v:t.cat,o:CATS.map(c=>[c,c])},{k:'d',l:'Дата',t:'date',v:t.d},{k:'n',l:'Заметка',v:t.n}],'Сохранить',n?'':'Удалить');if(!r)return 0;
 if(r=='del'){f.tx=f.tx.filter(x=>x!==t);return 1}
 if(!(r.a>0)){toast('Введите сумму');return 0}Object.assign(t,{amt:(r.k=='+'?1:-1)*r.a,card:r.card,cat:r.cat,d:r.d,n:r.n.trim()});if(n)f.tx.push(t);return 1}
async function subEd(s){const n=!s;s=s||{id:uid(),name:'',amt:0,day:1,card:(D.fin.cards[0]||{}).id||''};const r=await form(n?'Подписка':'Изменить',[{k:'name',l:'Название',v:s.name},{k:'amt',l:'Сумма в месяц',t:'number',v:s.amt||''},{k:'day',l:'День списания (1–28)',t:'number',v:s.day},{k:'card',l:'Карта',t:'sel',v:s.card,o:cardOpts()}],'Сохранить',n?'':'Удалить');if(!r)return 0;
 if(r=='del'){D.fin.subs=D.fin.subs.filter(x=>x!==s);return 1}
 if(!(r.amt>0)||!r.name.trim()){toast('Укажите название и сумму');return 0}
 Object.assign(s,{name:r.name.trim(),amt:r.amt,day:clamp(Math.round(r.day)||1,1,28),card:r.card});if(n){const p=new Date();p.setDate(1);p.setMonth(p.getMonth()-1);s.last=ymd(p).slice(0,7);D.fin.subs.push(s)}chargeSubs();return 1}
async function goalEd(g){const n=!g;g=g||{id:uid(),name:'',target:0,saved:0,date:ymd(new Date(Date.now()+365*864e5))};const r=await form(n?'Цель накопления':'Изменить цель',[{k:'name',l:'На что копите',v:g.name},{k:'target',l:'Нужная сумма',t:'number',v:g.target||''},{k:'saved',l:'Уже накоплено',t:'number',v:g.saved},{k:'date',l:'К какой дате',t:'date',v:g.date}],'Сохранить',n?'':'Удалить');if(!r)return 0;
 if(r=='del'){D.fin.goals=D.fin.goals.filter(x=>x!==g);return 1}
 if(!(r.target>0)||!r.name.trim()||!r.date){toast('Заполните название, сумму и дату');return 0}Object.assign(g,{name:r.name.trim(),target:r.target,saved:r.saved||0,date:r.date});if(n)D.fin.goals.push(g);return 1}
function openFin(){chargeSubs();loadRates();
 VW('Финансы',(b,rf)=>{const f=D.fin,now=new Date(),cm=ymd(now).slice(0,7),mt=f.tx.filter(t=>mk(t.d)==cm),sm=a=>a.reduce((s,t)=>s+t.amt,0),inc=sm(mt.filter(t=>t.amt>0)),exp=-sm(mt.filter(t=>t.amt<0)),tot=f.cards.reduce((s,c)=>s+bal(c),0),sub=f.subs.reduce((s,x)=>s+x.amt,0),cat={};
  mt.filter(t=>t.amt<0).forEach(t=>cat[t.cat]=(cat[t.cat]||0)-t.amt);const cs=Object.entries(cat).sort((a,c)=>c[1]-a[1]).map(([k,v],i)=>({l:k,v,c:pcol(i),t:fm(v)})),mo=[];
  for(let i=5;i>=0;i--){const d=new Date(now.getFullYear(),now.getMonth()-i,1),x=f.tx.filter(t=>mk(t.d)==ymd(d).slice(0,7));mo.push({l:d.toLocaleDateString('ru-RU',{month:'short'}),v:Math.round(sm(x.filter(t=>t.amt>0))),w:Math.round(-sm(x.filter(t=>t.amt<0)))})}
  const H=t=>'<b style="font-size:16px;margin-bottom:6px">'+t+'</b>';
  b.innerHTML='<div class="fcs">'+f.cards.map(c=>'<button class="fcd" data-c="'+c.id+'" style="background:linear-gradient(135deg,'+c.col+','+shade(c.col,-.5)+')"><b style="font-size:15px">'+esc(c.name)+'</b><div><small style="color:#fff;opacity:.8">Баланс</small><b style="font-size:26px">'+fm(bal(c))+'</b></div></button>').join('')+'<button class="fcd" data-ac style="background:var(--s1);color:var(--ac);align-items:center;justify-content:center;font-weight:700">'+ic('plus')+'Добавить карту</button></div>'
  +'<div class="g2"><div class="wg"><small>Всего</small><b>'+fm(tot)+'</b></div><div class="wg"><small>Подписки / мес</small><b>'+fm(sub)+'</b></div><div class="wg"><small>Доход за месяц</small><b style="color:#2e9e5b">+'+fm(inc)+'</b></div><div class="wg"><small>Расход за месяц</small><b style="color:#d64541">−'+fm(exp)+'</b></div></div><button class="btn pri" style="width:100%;margin:2px 0 14px" data-op>Добавить операцию</button>'
  +'<div class="wg">'+H('Расходы по категориям')+(cs.length?donut(cs)+'<div style="margin-top:10px">'+lg(cs)+'</div>':'<p class="mu">Трат в этом месяце пока нет</p>')+'</div>'
  +'<div class="wg">'+H('Доходы и расходы, 6 месяцев')+bars(mo,1)+'<div class="mu"><span style="color:#2e9e5b">■</span> доход &nbsp;<span style="color:#d64541">■</span> расход</div></div>'
  +'<div class="wg">'+H('Подписки')+(f.subs.map(s=>'<div class="li" data-s="'+s.id+'"><span>'+esc(s.name)+' <small class="mu">· '+s.day+'-го числа</small></span><span class="r">'+fm(s.amt)+'</span></div>').join('')||'<p class="mu">Подписок нет. Они будут списываться сами каждый месяц.</p>')+'<button class="btn" style="width:100%;margin-top:8px" data-as>Добавить подписку</button></div>'
  +'<div class="wg">'+H('Цели накопления')+(f.goals.map(g=>{const gd=new Date(g.date+'T00:00'),ml=Math.max(1,Math.ceil((gd-now)/2629800000)),need=Math.max(0,g.target-g.saved),pm=need/ml;return'<div style="margin:12px 0" data-g="'+g.id+'"><div class="li" style="border:0;padding:0"><span><b style="font-size:16px">'+esc(g.name)+'</b></span><span class="r">'+fm(g.saved)+' / '+fm(g.target)+'</span></div><div class="pg2"><i style="width:'+Math.min(100,g.saved/g.target*100)+'%"></i></div><small class="mu">'+(need?'Откладывайте ~'+fm(pm)+' в месяц ('+ml+' мес. до '+gd.toLocaleDateString('ru-RU')+')'+(inc?', это '+Math.round(pm/inc*100)+'% дохода за месяц':''):'Цель достигнута')+'</small></div>'}).join('')||'<p class="mu">Укажите, на что копите, сумму и дату — посчитаю, сколько откладывать в месяц.</p>')+'<button class="btn" style="width:100%" data-ag>Новая цель</button></div>'
  +'<div class="wg">'+H('Последние операции')+(f.tx.slice().sort((a,c)=>c.d.localeCompare(a.d)).slice(0,12).map(t=>'<div class="li" data-t="'+t.id+'"><span>'+esc(t.n||t.cat)+' <small class="mu">· '+t.cat+' · '+dm(t.d)+'</small></span><span class="r" style="color:'+(t.amt>0?'#2e9e5b':'inherit')+'">'+(t.amt>0?'+':'−')+fm(Math.abs(t.amt))+'</span></div>').join('')||'<p class="mu">Операций нет</p>')+'</div>'
  +'<div class="setr"><span>Валюта учёта (подпись и курсы)</span><select class="in" data-cur style="width:auto">'+Object.keys(SYM).map(c=>'<option'+(c==f.cur?' selected':'')+'>'+c+'</option>').join('')+'</select></div>';
  b.onchange=x=>{if(x.target.dataset.cur!=null){f.cur=x.target.value;save();rf()}};
  b.onclick=async x=>{const q=s=>x.target.closest(s),g=(s,k)=>f[k].find(z=>z.id==q(s).dataset[s=='[data-c]'?'c':s=='[data-s]'?'s':s=='[data-t]'?'t':'g']);let ch=0;
   if(q('[data-ac]'))ch=await cardEd(null);else if(q('[data-c]'))ch=await cardEd(g('[data-c]','cards'));else if(q('[data-op]'))ch=await txEd(null);else if(q('[data-t]'))ch=await txEd(g('[data-t]','tx'));
   else if(q('[data-as]'))ch=await subEd(null);else if(q('[data-s]'))ch=await subEd(g('[data-s]','subs'));else if(q('[data-ag]'))ch=await goalEd(null);else if(q('[data-g]'))ch=await goalEd(g('[data-g]','goals'));
   if(ch){save();rf()}}},rf=>txEd(null).then(c=>{if(c){save();rf()}}))}
//Калькулятор и валюты//
function vcalc(s){const t=s.replace(/π/g,'('+Math.PI+')').replace(/\be\b/g,'('+Math.E+')').replace(/×/g,'*').replace(/÷/g,'/').replace(/−/g,'-').replace(/√\(/g,'sqrt(').replace(/\^/g,'**').replace(/(\d+(?:\.\d+)?)%/g,'($1/100)').replace(/\b(sin|cos|tan)\(/g,'$1d(').replace(/\blog\(/g,'log10(');
 if(!/^(?:[\d+\-*/().\s]|sqrt|sind|cosd|tand|ln|log10)*$/.test(t))throw 0;const g=f=>x=>f(x*Math.PI/180);return Function('sqrt','sind','cosd','tand','ln','log10','"use strict";return('+t+')')(Math.sqrt,g(Math.sin),g(Math.cos),g(Math.tan),Math.log,Math.log10)}
function openCalc(){loadRates();let ex='',tab=0,hist='',am=100,fr='USD',to=D.fin.cur;
 const ev=s=>{let o=0;for(const c of s)o+=c=='('?1:c==')'?-1:0;try{const r=vcalc(s+')'.repeat(Math.max(0,o)));return isFinite(r)?String(+r.toPrecision(12)):''}catch(e){return''}},
 tabs=()=>'<div style="display:flex;gap:8px;margin-bottom:12px"><button class="btn'+(tab?'':' pri')+'" data-tab="0" style="flex:1">Калькулятор</button><button class="btn'+(tab?' pri':'')+'" data-tab="1" style="flex:1">Валюты</button></div>',
 sl=(k,v)=>'<select class="in" data-'+k+'>'+Object.keys(SYM).map(c=>'<option'+(c==v?' selected':'')+'>'+c+'</option>').join('')+'</select>';
 VW('Калькулятор',(b,rf)=>{
  if(!tab){const K=[['sin','cos','tan','ln','log'],['√','^','(',')','π'],['7','8','9','÷','AC'],['4','5','6','×','⌫'],['1','2','3','−','%'],['0','.','e','+','=']].flat(),r=ev(ex);
   b.innerHTML=tabs()+'<div class="wg" style="text-align:right;min-height:96px"><div class="mu" style="min-height:20px;word-break:break-all">'+esc(hist)+'</div><b style="font-size:30px;word-break:break-all">'+(esc(ex)||'0')+'</b><div class="mu" style="min-height:20px">'+(ex&&r&&r!=ex?'= '+r:'')+'</div></div><div class="kp">'+K.map(k=>'<button class="'+(/[÷×−+^%]/.test(k)?'op':k=='='?'eq':'')+'" data-k="'+k+'">'+k+'</button>').join('')+'</div>';
   $('.kp',b).onclick=x=>{const e=x.target.closest('[data-k]');if(!e)return;const v=e.dataset.k;buzz(4);
    if(v=='AC'){ex='';hist=''}else if(v=='⌫')ex=ex.slice(0,-1);else if(v=='='){if(r){hist=ex+' =';ex=r}}else ex+=/^(sin|cos|tan|ln|log|√)$/.test(v)?v+'(':v;rf()}}
  else b.innerHTML=tabs()+'<div class="wg"><input class="in" type="number" inputmode="decimal" step="any" data-am value="'+am+'" style="font-size:24px;font-weight:700"><div class="row">'+sl('fr',fr)+'<button class="btn" data-sw style="flex:0 0 56px">⇄</button>'+sl('to',to)+'</div><b style="font-size:30px;margin-top:14px">'+cvt(am||0,fr,to).toLocaleString('ru-RU',{maximumFractionDigits:2})+' '+SYM[to]+'</b><small class="mu">1 '+fr+' = '+cvt(1,fr,to).toFixed(4)+' '+to+'</small></div><div class="mu">'+(D.rates?'Курсы обновлены: '+new Date(D.rates.t).toLocaleString('ru-RU'):'Курсы примерные (офлайн). Подключитесь к интернету и нажмите «Обновить».')+'</div><button class="btn" style="width:100%;margin-top:10px" data-rf>Обновить курсы</button>';
  b.onchange=x=>{const t=x.target.dataset;if('am'in t)am=parseFloat(x.target.value)||0;else if('fr'in t)fr=x.target.value;else if('to'in t)to=x.target.value;else return;rf()};
  b.addEventListener('click',async x=>{const q=s=>x.target.closest(s);if(q('[data-tab]')){tab=+q('[data-tab]').dataset.tab;rf()}else if(q('[data-sw]')){[fr,to]=[to,fr];rf()}else if(q('[data-rf]')){const o=D.rates;D.rates=null;await loadRates();toast(D.rates?'Курсы обновлены':'Не удалось обновить курсы');if(!D.rates)D.rates=o;rf()}})})}
//Графики и расписания//
const DAYS=['Пн','Вт','Ср','Чт','Пт','Сб','Вс'];
const parseCh=t=>t.split('\n').map(l=>l.split(/[:;=]/)).filter(p=>p.length>1&&!isNaN(parseFloat(p[1].replace(',','.')))).map((p,i)=>({l:p[0].trim().slice(0,8),v:parseFloat(p[1].replace(',','.')),c:pcol(i),t:p[1].trim()}));
const chSVG=it=>{const a=parseCh(it.txt||'');return!a.length?'<p class="mu">Нет данных</p>':it.ty=='pie'?donut(a)+'<div style="margin-top:10px">'+lg(a)+'</div>':it.ty=='line'?line(a):bars(a)};
async function chEd(it){const n=!it;it=it||{id:uid(),k:'chart',t:'',ty:'bar',txt:'Янв: 10\nФев: 25\nМар: 18'};const r=await form(n?'Новый график':'График',[{k:'t',l:'Название',v:it.t},{k:'ty',l:'Вид',t:'sel',v:it.ty,o:[['bar','Столбцы'],['line','Линия'],['pie','Круговая']]},{k:'txt',l:'Данные: «Подпись: число» в каждой строке',t:'area',v:it.txt}],'Сохранить',n?'':'Удалить');if(!r)return 0;
 if(r=='del'){D.items=D.items.filter(x=>x!==it);return 1}Object.assign(it,{t:r.t.trim()||'График',ty:r.ty,txt:r.txt});if(n)D.items.unshift(it);return 1}
async function rowEd(it,r0){const n=!r0;r0=r0||{d:0,tm:'09:00',tx:''};const r=await form(n?'Занятие':'Изменить',[{k:'d',l:'День',t:'sel',v:String(r0.d),o:DAYS.map((x,i)=>[String(i),x])},{k:'tm',l:'Время',t:'time',v:r0.tm},{k:'tx',l:'Что',v:r0.tx}],'Сохранить',n?'':'Удалить');if(!r)return 0;
 if(r=='del'){it.rows=it.rows.filter(x=>x!==r0);return 1}if(!r.tx.trim())return 0;Object.assign(r0,{d:+r.d,tm:r.tm||'00:00',tx:r.tx.trim()});if(n)it.rows.push(r0);return 1}
async function schNew(){const r=await form('Новое расписание',[{k:'t',l:'Название',v:''}],'Создать');if(!r)return;const it={id:uid(),k:'sch',t:r.t.trim()||'Расписание',rows:[]};D.items.unshift(it);save();openItem(it)}
function openItem(it){let v;v=VW(it.t,(b,rf)=>{
  b.innerHTML=it.k=='chart'?'<div class="wg">'+chSVG(it)+'</div><button class="btn" style="width:100%" data-ed>Изменить график</button>':DAYS.map((d,i)=>{const rs=it.rows.filter(r=>r.d==i).sort((a,c)=>a.tm.localeCompare(c.tm));return rs.length?'<div class="wg"><b style="font-size:16px">'+d+'</b>'+rs.map(r=>'<div class="li" data-r="'+it.rows.indexOf(r)+'"><span class="mu" style="flex:0 0 52px">'+r.tm+'</span><span>'+esc(r.tx)+'</span></div>').join('')+'</div>':''}).join('')+(it.rows.length?'':'<p class="mu">Добавьте первое занятие кнопкой «+»</p>')+'<button class="btn dg" style="width:100%" data-ed>Удалить расписание</button>';
  b.onclick=async x=>{const r=x.target.closest('[data-r]');let ch=0;
   if(r)ch=await rowEd(it,it.rows[+r.dataset.r]);else if(x.target.closest('[data-ed]')){if(it.k=='chart')ch=await chEd(it);else if(await askOk('Удалить расписание?','Оно будет удалено без возможности вернуть.','Удалить')){D.items=D.items.filter(z=>z!==it);save();$('.cbtn',v).click();return}}
   if(ch){save();D.items.includes(it)?rf():$('.cbtn',v).click()}}},rf=>{(it.k=='chart'?chEd(it):rowEd(it,null)).then(c=>{if(c){save();D.items.includes(it)?rf():$('.cbtn',v).click()}})})}
function openItems(){VW('Графики и расписания',(b,rf)=>{b.innerHTML=D.items.map(it=>'<div class="wg" data-i="'+it.id+'"><div class="li" style="border:0;padding:0"><span><b style="font-size:17px">'+esc(it.t)+'</b><small class="mu">'+(it.k=='chart'?'График':'Расписание · занятий: '+it.rows.length)+'</small></span>'+ic(it.k=='chart'?'chart':'sched')+'</div></div>').join('')||'<p class="mu" style="text-align:center;margin-top:40px">Здесь будут графики и расписания. Нажмите «+».</p>';
  b.onclick=x=>{const e=x.target.closest('[data-i]');if(e)openItem(D.items.find(i=>i.id==e.dataset.i))}},rf=>{const sh=sheet('<h3>Создать</h3><div class="cm"><button data-k="c">'+ic('chart')+'График</button><button data-k="s">'+ic('sched')+'Расписание</button></div>');
  sh.el.onclick=async e=>{const q=e.target.closest('[data-k]');if(!q)return;sh.close();await wait(260);if(q.dataset.k=='c'){if(await chEd(null)){save();rf()}}else await schNew()}})}
//Меню создания, боковая панель, главный экран//
function createMenu(){const O=[['pencil','Заметка',()=>newNote()],['todo','Задача',()=>{V_='tasks';syncSeg();render();$('#q').focus()}],['calendar','Событие',()=>evEd(null).then(dash)],['wallet','Трата / доход',()=>txEd(null).then(c=>{if(c){save();dash()}})],['chart','График',()=>chEd(null).then(c=>{if(c){save();openItems()}})],['sched','Расписание',schNew]];
 const sh=sheet('<h3>Создать</h3><div class="cm">'+O.map((o,i)=>'<button data-o="'+i+'">'+ic(o[0])+o[1]+'</button>').join('')+'</div>');sh.el.onclick=async e=>{const b=e.target.closest('[data-o]');if(!b)return;sh.close();await wait(260);O[b.dataset.o][2]()}}
const SEC={cal:openCal,fin:openFin,calc:openCalc,items:openItems},_rd=renderDrawer;
renderDrawer=function(){_rd();const d=$('.drawer'),sp=d&&$('.sp',d);if(!sp)return;sp.insertAdjacentHTML('beforebegin','<div class="lbl"><span>Разделы</span></div>'+[['cal','calendar','Календарь'],['fin','wallet','Финансы'],['calc','calc','Калькулятор'],['items','chart','Графики и расписания']].map(r=>'<div class="dr" data-s="'+r[0]+'">'+ic(r[1])+'<span>'+r[2]+'</span></div>').join(''));
 $$('.dr[data-s]',d).forEach(r=>r.onclick=()=>{closeDrawer();setTimeout(SEC[r.dataset.s],200)})};
function dash(){let d=$('#dash');if(!d){d=el('div');d.id='dash';$('#hscroll').insertBefore(d,$('#hlist'))}
 if(V_!='notes'||F!='all'||Q){d.className='';d.innerHTML='';return}const s=D.set,f=D.fin,now=new Date(),cm=ymd(now).slice(0,7);let h='';
 if(s.dfin!==false){const tot=f.cards.reduce((a,c)=>a+bal(c),0),net=f.tx.filter(t=>mk(t.d)==cm).reduce((a,t)=>a+t.amt,0);h+='<div class="wg" data-go="fin"><small>Финансы</small><b>'+fm(tot)+'</b><small>'+(net<0?'−':'+')+fm(Math.abs(net))+' за месяц</small></div>'}
 if(s.drate!==false){const c=f.cur;h+='<div class="wg" data-go="calc"><small>Курс к '+c+'</small>'+['USD','EUR','GBP'].filter(k=>k!=c).map(k=>'<div><small>'+k+'</small> <b style="display:inline;font-size:16px">'+cvt(1,k,c).toFixed(2)+'</b></div>').join('')+'</div>'}
 if(s.dcal!==false){const up=[];for(let i=0;i<30&&up.length<2;i++){const dd=ymd(new Date(now.getFullYear(),now.getMonth(),now.getDate()+i));D.cal.filter(e=>evOn(e,dd)).forEach(e=>up.length<2&&up.push([dd,e]))}
  h+='<div class="wg" data-go="cal" style="grid-column:1/-1"><small>Ближайшие события</small>'+(up.length?up.map(([dd,e])=>'<div class="li" style="padding:6px 0;border:0">'+dot(e.c)+'<span>'+esc(e.t)+'</span><span class="r mu">'+(dd==ymd(now)?'сегодня':dm(dd))+'</span></div>').join(''):'<div class="mu" style="padding-top:4px">На 30 дней вперёд событий нет</div>')+'</div>'}
 if(s.dfav!==false)h+=D.notes.filter(n=>n.fav&&!n.del&&!n.lk).slice(0,2).map(n=>'<div class="wg" data-n="'+n.id+'"><small>Избранное</small><b style="font-size:16px">'+esc(n.t||'Без названия')+'</b><small>'+esc(ntext(n).slice(0,60))+'</small></div>').join('');
 d.className=h?'g2':'';d.style.margin='0 0 14px';d.innerHTML=h;d.onclick=e=>{const g=e.target.closest('[data-go]'),n=e.target.closest('[data-n]');if(g)SEC[g.dataset.go]();else if(n)openNote(D.notes.find(x=>x.id==n.dataset.n))}}
const _rn=render;render=function(a){_rn(a);dash()};
vxInit();chargeSubs();

applySet();render();
</script>
</body>
</html>
