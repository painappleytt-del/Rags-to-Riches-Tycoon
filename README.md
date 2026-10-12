<!doctype html>
<html lang="en"><head><meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>Empire Rush</title>
<link href="https://fonts.googleapis.com/css2?family=Fredoka:wght@400;500;600&display=swap" rel="stylesheet">
<style>
:root{--bg:#07142b;--card:#10264a;--card2:#173560;--line:#24457a;--txt:#eaf2ff;--dim:#8ba5cf;--gold:#ffc83d;--green:#35d489;--red:#ff6b6b;--blue:#3d8bff;color-scheme:dark;box-sizing:border-box;padding-top:env(safe-area-inset-top,0px)}
*{box-sizing:border-box;-webkit-tap-highlight-color:transparent}
html,body{margin:0;background:var(--bg);color:var(--txt);font-family:'Fredoka',system-ui,sans-serif}
body{padding-bottom:calc(84px + env(safe-area-inset-bottom,0px));user-select:none;-webkit-user-select:none}
.wrap{max-width:480px;margin:0 auto;padding:12px 14px}
.bal{background:linear-gradient(135deg,#1b3f7a,#0e2349);border:1px solid var(--line);border-radius:20px;padding:14px 18px}
.bal{position:relative}
#snd{position:absolute;top:10px;right:12px;width:38px;height:38px;border-radius:50%;border:1px solid var(--line);background:#0e2349;color:var(--gold);display:grid;place-items:center;cursor:pointer;padding:0}
#snd.off{color:var(--dim)}
.bal small{color:var(--dim);font-size:13px}
.bal b{display:block;font-size:34px;font-weight:600;color:var(--gold);line-height:1.1}
.bal .r{display:flex;justify-content:space-between;margin-top:6px;color:var(--dim);font-size:14px}
.bal .r span b{display:inline;font-size:14px;color:var(--green)}
h2{font-size:18px;font-weight:500;margin:16px 2px 8px}
.dim{color:var(--dim);font-size:14px;margin:0 2px 10px}
.row{display:flex;align-items:center;gap:12px;background:var(--card);border:1px solid var(--line);border-radius:16px;padding:12px;margin-bottom:10px}
.row.lock{opacity:.5}.row.ok{border-color:var(--green)}
.row .i{font-size:26px;width:46px;height:46px;border-radius:50%;background:var(--card2);display:grid;place-items:center;flex:none;box-shadow:0 2px 6px #0006}.row .i svg{width:100%;height:100%;display:block}
.row .m{flex:1;min-width:0}
.row .m b{display:block;font-weight:500;font-size:16px}
.row .m span{color:var(--dim);font-size:13px;display:block}
.btn{border:0;border-radius:12px;padding:9px 14px;font:inherit;font-weight:500;font-size:15px;background:var(--blue);color:#fff;min-width:84px;cursor:pointer}
.btn.off{background:#223a63;color:#6f86ad}
.btn.sell{background:#3a2d4f;color:#ffb0b0}
.btn.done{background:#1d4f3a;color:var(--green)}
.btn.gold{background:var(--gold);color:#241a00}
.tap{margin:16px 0;height:250px;border-radius:24px;background:radial-gradient(circle at 50% 40%,#1c4585,#0c1f40);border:2px dashed var(--line);display:grid;place-items:center;text-align:center;position:relative;overflow:hidden;touch-action:manipulation}
.tap .big{font-size:64px}.tap p{margin:0;color:var(--dim)}
.tap.hit{border-color:var(--gold)}
.fl{position:absolute;color:var(--gold);font-weight:600;font-size:22px;pointer-events:none;animation:up .8s ease-out forwards}
@keyframes up{to{transform:translateY(-70px);opacity:0}}
.fl.a{color:var(--green);font-size:16px}
.rip{position:absolute;width:44px;height:44px;margin:-22px 0 0 -22px;border-radius:50%;border:3px solid var(--green);pointer-events:none;animation:rp .5s ease-out forwards}
@keyframes rp{from{transform:scale(.3);opacity:1}to{transform:scale(1.5);opacity:0}}
.seg{display:flex;gap:8px;margin-bottom:12px}
.pill{flex:1;text-align:center;padding:8px 4px;border-radius:12px;background:var(--card);border:1px solid var(--line);color:var(--dim);font-size:14px;cursor:pointer}
.pill.on{background:var(--blue);border-color:var(--blue);color:#fff}
.up-c{color:var(--green)}.dn-c{color:var(--red)}
.stat{display:flex;justify-content:space-between;padding:11px 14px;background:var(--card);border-radius:14px;margin-bottom:8px;border:1px solid var(--line)}
.stat span{color:var(--dim)}
.grid{display:grid;grid-template-columns:1fr 1fr;gap:8px;margin-bottom:10px}
.grid .stat{margin:0;flex-direction:column;gap:2px;border-left-width:6px}
.bar{display:flex;height:12px;border-radius:8px;overflow:hidden;gap:2px;margin:10px 0 12px}
nav{position:fixed;left:0;right:0;bottom:0;background:#0b1d3b;border-top:1px solid var(--line);display:flex;padding:6px 4px calc(6px + env(safe-area-inset-bottom,0px));z-index:5}
nav div{flex:1;text-align:center;padding:6px 0;border-radius:12px;color:var(--dim);font-size:11px;cursor:pointer}
nav div i{display:block;font-style:normal;font-size:20px}
nav div.on{color:var(--gold);background:#16305c}
#toast{position:fixed;left:50%;top:calc(14px + env(safe-area-inset-top,0px));transform:translateX(-50%);background:var(--gold);color:#1a1200;padding:10px 16px;border-radius:14px;font-weight:500;opacity:0;transition:opacity .3s;z-index:9;max-width:90%;text-align:center;pointer-events:none}
</style></head>
<body>
<div class="wrap">
  <div class="bal"><button id="snd" aria-label="Toggle sound"></button><small id="pl">Balance</small><b id="bal">$0.00</b>
    <div class="r"><span>Income <b id="inc">$0/s</b></span><span>Per tap <b id="ptap">$1</b></span></div></div>
  <div id="main"></div>
</div>
<nav id="nav"></nav>
<div id="toast"></div>
<script>
const TY=[["🥤","Street stall",250,0],["🧺","Shop",4899,0],["🚕","Taxi company",9999,0],["🚚","Shipping company",19899,0],["🏭","Factory",24999,0],["🏗️","Construction",35400,0],["🚘","Car dealership",4e4,0],["💻","IT company",35e4,0],["🏦","Bank",1e7,1],["⚽","Sports club",4e7,2],["🛢️","Oil & gas",1.5e9,3],["✈️","Airlines",1.3e10,4],["🚀","Space agency",1e11,5]];
const MG=[["Retail empire","🛍️",3e6,.2,0,[[1,10],[3,8],[4,5]]],["Aerospace group","🛰️",4.5e8,.5,2,[[4,10],[5,10],[3,10]]],["Holding company","🏛️",5e9,1,3,[[8,10],[7,10],[9,5]]]];
const ST=[["Veloxa Motors",37.95,.05,.2,"s",0],["Kiyota",18.05,.04,.25,"s",0],["Nordwagen",188.5,.06,.1,"s",0],["Auric Benz",89.82,.05,.15,"s",0],["Halden Energy",103.51,.03,.5,"s",0],["Ferro Auto",16.13,.07,.05,"s",0],["Solvane",157.68,.08,0,"s",0],["Bitcore",42000,.12,0,"c",2],["Ethrium",2800,.12,0,"c",2],["Dogecoyn",.25,.2,0,"c",2],["Solarium",140,.14,0,"c",2]];
const RE=[["🏠","Studio flat",15000],["🏢","Apartment",9e4],["🏘️","Townhouse",45e4],["🏡","Villa",3e6],["🌆","Penthouse",2.5e7],["🏙️","Skyscraper",4e8]];
const IT=[["car","🚗","Garage",6,2250,2.6,.03,0,["Old hatchback","City sedan","Family wagon","Sport coupe","Luxury sedan","Supercar"]],["air","🛩️","Hangar",4,5e6,3,.05,1,["Light plane","Turboprop","Private jet","Airliner"]],["yacht","🛥️","Harbor",4,2e7,3,.05,2,["Day boat","Cruiser","Superyacht","Mega yacht"]],["coin","🪙","Coins",20,5e4,1.4,.01,3],["paint","🎨","Paintings",25,2e5,1.35,.01,3],["jewel","💎","Jewels",20,1e6,1.45,.01,4],["stamp","📮","Stamps",15,5e5,1.4,.01,4],["isle","🏝️","Islands",1,5e9,1,.25,5],["badge","🎖️","Insignia",5,5e7,3,.03,6],["nft","🖼️","NFTs",21,1e7,1.5,.01,6]];
const SK=[["t1","Firm grip","+50% tap value",1,[],"Taps"],["t2","Double tap","+100% tap value",1,["t1"],"Taps"],["t3","Tap storm","Each tap adds 1% of your income per second",2,["t2"],"Taps"],["t4","Golden finger","10% of taps pay ×10",3,["t3"],"Taps"],["b1","Good deals","+10% business income",1,[],"Business"],["b2","Team work","+20% business income",1,["b1"],"Business"],["b3","Cheap upgrades","Company upgrades cost 20% less",2,["b2"],"Business"],["b4","Expansion","+2 company slots",3,["b3"],"Business"],["b5","Corporate empire","+50% business income",3,["b4"],"Business"],["i1","Dividend fan","+50% dividends",1,[],"Investing"],["i2","Reinvest","+100% dividends",1,["i1"],"Investing"],["i3","Landlord","+50% rent",2,["i2"],"Investing"],["i4","Collector's eye","+50% item bonuses",2,["i3"],"Investing"],["i5","Long haul","Offline earnings last 6h longer",2,["i4"],"Investing"],["m1","Tycoon","×2 all income",4,["t4","b5","i5"],"Master"]];
const PU=["Real estate, Bank, Hangar","Crypto, Sports club, Harbor, Aerospace merger","Oil & gas, Coins, Paintings, Holding merger","Airlines, Jewels, Stamps","Space agency, Islands","Insignia, NFTs","+2 company slots","Taps worth ×3","Offline earnings up to 24h","Legend status: ×2 all income"];
const KEY="empireRush2";
const fresh=(P=0,k={})=>Object.assign({money:P?250*5**P:100,run:0,cl:0,ac:0,co:[],mg:MG.map(()=>0),st:ST.map(()=>0),sp:ST.map(()=>0),p:ST.map(s=>s[1]),pc:ST.map(()=>0),re:RE.map(()=>0),g:{},sk:{},P,total:0,taps:0,bu:0,bc:0,q:1,t:Date.now()},k);
let S=fresh();
try{const r=JSON.parse(localStorage.getItem(KEY));if(r)S=Object.assign(S,r)}catch(e){}
let tab="earn",sub="s",resetArm=false,presArm=false,sellArm=-1;
const $=s=>document.querySelector(s);
const nf=(n,d)=>n.toLocaleString("en-US",{minimumFractionDigits:d,maximumFractionDigits:d});
function fmt(n){const u=["","K","M","B","T","Qa","Qi"];if(n<100000)return "$"+nf(n,n<1000?2:0);let i=0;while(n>=1000&&i<6){n/=1000;i++}return "$"+nf(n,2)+u[i]}
const tm=ms=>{const s=Math.ceil(ms/1000);return Math.floor(s/60)+":"+String(s%60).padStart(2,"0")};
const sk=id=>S.sk[id]?1:0;
const ig=g=>S.g[g[0]]||0;
const IB=()=>IT.reduce((a,g)=>a+ig(g)*g[6]*(1+.5*sk("i4"))+(ig(g)>=g[3]?.1:0),0);
const MB=()=>MG.reduce((a,m,i)=>a+(S.mg[i]?m[3]:0),0);
const mult=()=>(1+IB())*(1+MB())*(1+.75*S.P)*(Date.now()<S.bu?1.3:1)*(sk("m1")?2:1)*(S.P>=10?2:1);
const bizI=()=>S.co.reduce((a,c)=>a+TY[c[0]][2]/600*c[1],0)*(1+.1*sk("b1")+.2*sk("b2")+.5*sk("b5"));
const stV=k=>ST.reduce((a,s,i)=>a+(s[4]===k?S.st[i]*S.p[i]:0),0);
const divM=()=>1+.5*sk("i1")+sk("i2");
const divH=()=>ST.reduce((a,s,i)=>a+S.st[i]*S.p[i]*s[3],0)*divM();
const reI=()=>RE.reduce((a,r,i)=>a+S.re[i]*r[2]/1200,0)*(1+.5*sk("i3"));
const income=()=>(bizI()+divH()/3600+reI())*mult();
const tapV=()=>(1+S.cl*(1+S.cl*.1))*(1+.5*sk("t1")+sk("t2"))*(S.P>=8?3:1)*mult()+(sk("t3")?income()*.01:0);
const slots=()=>10+2*sk("b4")+(S.P>=7?2:0);
const upC=c=>Math.ceil(TY[c[0]][2]*.6*c[1]*(1-.2*sk("b3")));
const sellV=c=>Math.floor(TY[c[0]][2]*(1+.3*c[1]*(c[1]-1))*.5);
const acCost=()=>Math.ceil(400*1.2**S.ac);const acRate=()=>S.ac*.2;
const clCost=()=>Math.ceil(20*1.4**S.cl);
const gCost=g=>Math.ceil(g[4]*g[5]**ig(g));
const gVal=g=>g[5]===1?g[4]*ig(g):g[4]*(g[5]**ig(g)-1)/(g[5]-1);
const reC=i=>Math.ceil(RE[i][2]*1.12**S.re[i]);
const pts=()=>Math.max(0,Math.floor(Math.log10(S.run+1)*5)-13);
const spX=()=>Math.log10(S.run+1)*5;
const spPct=()=>{const p=pts(),lo=p?p+13:0;return Math.max(0,Math.min(100,(spX()-lo)/(p+14-lo)*100))};
const spNext=()=>10**((pts()+14)/5);
const avail=()=>pts()-SK.reduce((a,k)=>a+(S.sk[k[0]]?k[3]:0),0);
const reqOK=m=>m[5].every(r=>S.co.some(c=>c[0]===r[0]&&c[1]>=r[1]));
function cats(){const veh=["car","air","yacht"];return[["Balance","#3d8bff",S.money],["Businesses","#ef5350",S.co.reduce((a,c)=>a+TY[c[0]][2]*c[1],0)],["Stocks","#ffc83d",stV("s")],["Crypto","#5fe3a1",stV("c")],["Real estate","#a86bd8",RE.reduce((a,r,i)=>a+r[2]*S.re[i],0)],["Transport","#4caf50",IT.reduce((a,g)=>a+(veh.includes(g[0])?gVal(g):0),0)],["Collections","#7c5cff",IT.reduce((a,g)=>a+(veh.includes(g[0])?0:gVal(g)),0)]]}
const worth=()=>cats().reduce((a,c)=>a+c[2],0);
function toast(t){const e=$("#toast");e.textContent=t;e.style.opacity=1;setTimeout(()=>e.style.opacity=0,2800)}
function save(){S.t=Date.now();try{localStorage.setItem(KEY,JSON.stringify(S))}catch(e){}}
function gain(n){S.money+=n;S.total+=n;S.run+=n}

/* ---------- Sound: generated live with Web Audio, no audio files needed ---------- */
const SND=(()=>{
  const PK="empireRushSnd",pref={m:1,s:1};
  try{Object.assign(pref,JSON.parse(localStorage.getItem(PK)))}catch(e){}
  let ctx,master,mus,sfx,step=0,tapN=0,lastTap=-1,lastAuto=-1,started=0;
  const hz=m=>440*Math.pow(2,(m-69)/12);
  const PENT=[72,74,76,79,81,84];                                   // C major pentatonic: always sounds pleasant
  const CH=[[48,55,59,64],[45,52,55,64],[41,48,57,64],[43,50,55,62]]; // Cmaj7 · Am7 · Fmaj7 · G6
  function tone(bus,f,t,hold,type,vol,atk,rel,det){
    const o=ctx.createOscillator(),g=ctx.createGain();
    o.type=type;o.frequency.value=f;if(det)o.detune.value=det;
    g.gain.setValueAtTime(0,t);g.gain.linearRampToValueAtTime(vol,t+atk);
    g.gain.setTargetAtTime(0,t+atk+hold,rel);
    o.connect(g);g.connect(bus);o.start(t);o.stop(t+atk+hold+rel*7);
  }
  function bar(){
    if(!ctx||ctx.state!=="running"||!pref.m)return;
    const t=ctx.currentTime+.05,c=CH[step++%CH.length];
    c.forEach((m,i)=>[-5,5].forEach(dt=>tone(mus,hz(m),t,4,i?"triangle":"sine",.016,2.8,1.4,dt)));
    tone(mus,hz(c[0]-12),t,5,"sine",.05,2,1.5);
    for(let k=0;k<8;k++)if(Math.random()<.4){
      const n=PENT[Math.random()*PENT.length|0],tt=t+.8+k*.95;
      tone(mus,hz(n),tt,.05,"sine",.045,.01,.6);
      if(Math.random()<.3)tone(mus,hz(n+12),tt+.01,.03,"sine",.015,.01,.4);
    }
  }
  function init(){
    if(ctx)return;
    const AC=window.AudioContext||window.webkitAudioContext;if(!AC)return;
    ctx=new AC();
    const comp=ctx.createDynamicsCompressor();master=ctx.createGain();master.gain.value=.9;
    master.connect(comp);comp.connect(ctx.destination);
    // dreamy echo shared by music and effects
    const dly=ctx.createDelay(1),fb=ctx.createGain(),lp=ctx.createBiquadFilter(),wet=ctx.createGain();
    dly.delayTime.value=.45;fb.gain.value=.4;lp.type="lowpass";lp.frequency.value=1600;wet.gain.value=.55;
    dly.connect(lp);lp.connect(fb);fb.connect(dly);lp.connect(wet);wet.connect(master);
    mus=ctx.createGain();sfx=ctx.createGain();mus.gain.value=pref.m?.8:0;sfx.gain.value=pref.s?1:0;
    const ms=ctx.createGain(),ss=ctx.createGain();ms.gain.value=.6;ss.gain.value=.3;
    mus.connect(master);mus.connect(ms);ms.connect(dly);sfx.connect(master);sfx.connect(ss);ss.connect(dly);
    // soft ocean-wave bed: brown noise with a slow volume swell
    const len=ctx.sampleRate*4,nb=ctx.createBuffer(1,len,ctx.sampleRate),d=nb.getChannelData(0);let l=0;
    for(let i=0;i<len;i++){l=(l+.02*(Math.random()*2-1))/1.02;d[i]=l*3.5*Math.min(1,i/3000,(len-i)/3000)}
    const ns=ctx.createBufferSource(),nf=ctx.createBiquadFilter(),ng=ctx.createGain(),lfo=ctx.createOscillator(),lg=ctx.createGain();
    ns.buffer=nb;ns.loop=true;nf.type="lowpass";nf.frequency.value=500;ng.gain.value=.05;lfo.frequency.value=.07;lg.gain.value=.035;
    lfo.connect(lg);lg.connect(ng.gain);ns.connect(nf);nf.connect(ng);ng.connect(mus);ns.start();lfo.start();
    ctx.resume().then(()=>{started=1;bar();setInterval(bar,8000)}).catch(()=>{});
  }
  const ok=()=>ctx&&ctx.state==="running"&&pref.s;
  const arp=(a,gap,vol)=>{if(!ok())return;const t=ctx.currentTime;a.forEach((m,i)=>tone(sfx,hz(m),t+i*gap,.04,"sine",vol,.005,.18))};
  function apply(){
    try{localStorage.setItem(PK,JSON.stringify(pref))}catch(e){}
    if(ctx){mus.gain.setTargetAtTime(pref.m?.8:0,ctx.currentTime,.3);sfx.gain.setTargetAtTime(pref.s?1:0,ctx.currentTime,.1);if(pref.m)bar()}
    api.ui();
  }
  const api={
    pref,ui(){},
    unlock(){init();if(ctx&&ctx.state==="suspended"&&!document.hidden)ctx.resume()},
    suspend(){if(ctx&&ctx.state==="running")ctx.suspend()},
    resume(){if(ctx&&started)ctx.resume()},
    set(k){pref[k]=pref[k]?0:1;apply()},
    toggleAll(){const on=pref.m||pref.s;pref.m=pref.s=on?0:1;apply()},
    tap(){if(!ok())return;const t=ctx.currentTime;if(t-lastTap<.04)return;if(t-lastTap>.7)tapN=0;lastTap=t;tone(sfx,hz(PENT[tapN++%PENT.length]),t,.02,"sine",.05,.004,.1)},
    auto(){if(!ok())return;const t=ctx.currentTime;if(t-lastAuto<.5)return;lastAuto=t;tone(sfx,hz(PENT[Math.random()*PENT.length|0]+12),t,.02,"sine",.02,.004,.15)},
    buy(){arp([79,86],.07,.07)},
    sell(){arp([86,79],.07,.06)},
    skill(){arp([84,88,91],.06,.06)},
    boost(){arp([72,79,84,91],.08,.06)},
    win(){arp([72,76,79,84,88,91,96],.11,.07)},
    tick(){if(ok())tone(sfx,hz(88),ctx.currentTime,.01,"sine",.02,.003,.06)},
    err(){if(ok())tone(sfx,170,ctx.currentTime,.05,"triangle",.07,.005,.1)}
  };
  return api;
})();
const SPK='<svg viewBox="0 0 24 24" width="22" height="22" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M4 9v6h4l5 4V5L8 9z"/>';
SND.ui=()=>{const b=$("#snd"),on=SND.pref.m||SND.pref.s;b.innerHTML=SPK+(on?'<path d="M16 9a4 4 0 0 1 0 6M18.5 6.5a8 8 0 0 1 0 11"/>':'<path d="M16 9l5 6M21 9l-5 6"/>')+'</svg>';b.classList.toggle("off",!on)};
$("#snd").addEventListener("click",()=>SND.toggleAll());
document.addEventListener("pointerdown",()=>SND.unlock(),{passive:true,capture:true});
document.addEventListener("visibilitychange",()=>document.hidden?SND.suspend():SND.resume());
let down=0;
["pointerdown"].forEach(v=>document.addEventListener(v,()=>down=1,true));
["pointerup","pointercancel"].forEach(v=>document.addEventListener(v,()=>down=0,true));

const TABS=[["inv","📈","Invest"],["biz","🏢","Business"],["earn","💲","Earn"],["items","🚗","Items"],["skill","🌳","Skills"],["me","👤","Profile"]];
$("#nav").innerHTML=TABS.map(t=>`<div data-t="${t[0]}"><i>${t[1]}</i>${t[2]}</div>`).join("");
document.body.insertAdjacentHTML('beforeend','<svg width="0" height="0" style="position:absolute"><defs><linearGradient id="gl" x1="0" y1="0" x2="0" y2="1"><stop offset="0" stop-color="#fff" stop-opacity=".3"/><stop offset=".6" stop-color="#fff" stop-opacity="0"/><stop offset="1" stop-color="#000" stop-opacity=".3"/></linearGradient></defs></svg>');
const CAR='<path d="M3 15v-3l2.5-4h8l3 4h2.5v3"/><path d="M3 15h18"/><circle cx="7.5" cy="16" r="2"/><circle cx="16.5" cy="16" r="2"/><path d="M6 12h10"/>';
const PLANE='<path d="M12 2c1 0 1.7 1 1.7 2.5V9l8 4.5v2l-8-2.2V18l2.3 1.7V21.5L12 20.5l-4 1v-1.8L10.3 18v-4.7l-8 2.2v-2L10.3 9V4.5C10.3 3 11 2 12 2z"/>';
const ICONS={};
[['🥤','#e53935','#fff','<path d="M6 7h12l-1.5 13h-9z"/><path d="M5 7h14"/><path d="M13 7l2-4h3"/><path d="M7.2 12h9.6"/>'],
['🧺','#43a047','#fff','<path d="M3 10h18l-2 10H5z"/><path d="M8 10l3-6M16 10l-3-6"/><path d="M9 14v3M12 14v3M15 14v3"/>'],
['🚕','#fbc02d','#2b2200','<path d="M5 15l1.6-5.5A2 2 0 0 1 8.5 8h7a2 2 0 0 1 1.9 1.5L19 15"/><rect x="3.5" y="15" width="17" height="4" rx="1.5"/><circle cx="7.5" cy="17" r=".6" fill="currentColor"/><circle cx="16.5" cy="17" r=".6" fill="currentColor"/><path d="M10.5 8V6h3v2"/>'],
['🚚','#ef7d3c','#fff','<path d="M2.5 7h11v9h-11z"/><path d="M13.5 10h4l3 3v3h-7"/><circle cx="7" cy="17.5" r="1.8"/><circle cx="17" cy="17.5" r="1.8"/>'],
['🏭','#4a78c2','#fff','<path d="M3 20V10l6 3V10l6 3V4h3v16z"/><path d="M3 20h18"/><path d="M7 17h2M12 17h2"/>'],
['🏗️','#d84315','#fff','<path d="M8 21V4M5 21h6M3 6h17M17 6v5M15 11h4v3h-4z"/><path d="M8 4L3 6M8 4l8 2"/>'],
['🚘','#212121','#fff',CAR],
['💻','#5e35b1','#fff','<rect x="3" y="4" width="18" height="12" rx="1.5"/><path d="M9 20h6M12 16v4"/><path d="M8 9l-2 2 2 2M16 9l2 2-2 2"/>'],
['🏦','#78808f','#fff','<path d="M3 9l9-5 9 5z"/><path d="M5 10v8M9.5 10v8M14.5 10v8M19 10v8"/><path d="M3 20h18"/>'],
['⚽','#8e1b4b','#fff','<circle cx="12" cy="12" r="9"/><path d="M12 8l3.5 2.5-1.3 4H9.8l-1.3-4z"/><path d="M12 3v5M20.5 9.5l-5 1M17.5 19l-3.3-4.5M6.5 19l3.3-4.5M3.5 9.5l5 1"/>'],
['🛢️','#1c2833','#fff','<path d="M12 3L7 20h10z"/><path d="M8.5 11h7M7.8 15.5h8.4"/><path d="M4 20h16"/>'],
['✈️','#1e88e5','#fff',PLANE],
['🚀','#1a237e','#fff','<path d="M12 2c3 2.5 4.5 6 4.5 10l-2 3h-5l-2-3c0-4 1.5-7.5 4.5-10z"/><circle cx="12" cy="9.5" r="1.7"/><path d="M7.5 13l-3 3 1 3 3-2M16.5 13l3 3-1 3-3-2"/><path d="M10 18l2 4 2-4"/>'],
['🛍️','#8e24aa','#fff','<path d="M5 8h14l-1 12H6z"/><path d="M9 8V6.5a3 3 0 0 1 6 0V8"/>'],
['🛰️','#283593','#fff','<circle cx="12" cy="12" r="4.5"/><ellipse cx="12" cy="12" rx="10" ry="3.5" transform="rotate(-25 12 12)"/>'],
['🏛️','#212121','#ffc83d','<path d="M3 9l9-5 9 5z"/><path d="M6 10v7M12 10v7M18 10v7"/><path d="M3 20h18"/>'],
['🏠','#2e7d6b','#fff','<path d="M3 11l9-7 9 7"/><path d="M5.5 10v10h13V10"/><path d="M10 20v-5h4v5"/>'],
['🏢','#3949ab','#fff','<rect x="5" y="3" width="14" height="18" rx="1"/><path d="M9 7h2M13 7h2M9 11h2M13 11h2M9 15h2M13 15h2M10.5 21v-3h3v3"/>'],
['🏘️','#6d4c41','#fff','<path d="M2 12l5-4 5 4M3.5 11.5V19h7v-7.5"/><path d="M12 14l5-4 5 4M13.5 13.5V19h7v-5.5"/>'],
['🏡','#2e7d32','#fff','<path d="M3 12l7-6 7 6"/><path d="M5 11v8h10v-8"/><circle cx="19" cy="11" r="2.5"/><path d="M19 13.5V19"/>'],
['🌆','#00838f','#fff','<path d="M8 21V9l4-5 4 5v12z"/><path d="M12 4V2M3 21h18M5 21v-8h3M16 21v-8h3v8"/>'],
['🏙️','#455a64','#fff','<path d="M9 21V3h6v18"/><path d="M4 21v-9h5M15 21v-6h5v6"/><path d="M11 7h2M11 11h2M11 15h2M3 21h18"/>'],
['🚗','#c62828','#fff',CAR],
['🛩️','#0288d1','#fff',PLANE],
['🛥️','#006064','#fff','<path d="M3 15h18l-3 5H6z"/><path d="M6 15v-4h9l3 4"/><path d="M9 11V8h4v3"/>'],
['🪙','#f9a825','#3a2a00','<circle cx="12" cy="12" r="9"/><circle cx="12" cy="12" r="6"/><path d="M13.5 9.5c-.4-.6-1.2-1-2.2-1-1.2 0-2 .6-2 1.4 0 2 4.5 1 4.5 3.2 0 .9-.9 1.5-2.2 1.5-1 0-1.9-.4-2.3-1M12 7v1.5M12 15.5V17"/>'],
['🎨','#ad1457','#fff','<path d="M12 3a9 9 0 1 0 0 18c1.5 0 2-1 1.5-2-.6-1.2 0-2.5 1.5-2.5H17a4 4 0 0 0 4-4c0-5-4-9.5-9-9.5z"/><circle cx="7.5" cy="11" r="1" fill="currentColor"/><circle cx="10" cy="7" r="1" fill="currentColor"/><circle cx="15" cy="7.5" r="1" fill="currentColor"/>'],
['💎','#00acc1','#fff','<path d="M6 4h12l4 5-10 12L2 9z"/><path d="M2 9h20M8 4l-1 5 5 12M16 4l1 5-5 12"/>'],
['📮','#1565c0','#fff','<rect x="5" y="4" width="14" height="16" rx="1" stroke-dasharray="2 1.5"/><rect x="8" y="7" width="8" height="10"/><path d="M8 14l2.5-3 2 2 1.5-1.5 2 2.5"/>'],
['🏝️','#26a69a','#fff','<path d="M12 20V10"/><path d="M12 10c-3-.5-5-2-6-4 3-1 5 0 6 4zM12 10c3-.5 5-2 6-4-3-1-5 0-6 4zM12 10c-1-3 0-5 3-6 1 3-1 5-3 6z"/><path d="M4 20c3-2 5 0 8 0s5-2 8 0"/>'],
['🎖️','#b71c1c','#ffd54f','<circle cx="12" cy="9" r="5.5"/><path d="M8.5 13.5L7 21l5-2.5 5 2.5-1.5-7.5"/>'],
['🖼️','#7e57c2','#fff','<rect x="3" y="4" width="18" height="16" rx="2"/><circle cx="9" cy="10" r="1.6"/><path d="M3 17l5-5 4 4 3-3 6 5"/>']
,['\ud83e\udd16','#00897b','#fff','<path d="M5 3l14 7-6 2-2 6z"/><path d="M13 12l5 6"/>']
].forEach(a=>ICONS[a[0].replace(/\uFE0F/g,'')]=a);
const ic=e=>{const a=ICONS[e.replace(/\uFE0F/g,'')];return a?`<svg viewBox="0 0 48 48" style="color:${a[2]}"><circle cx="24" cy="24" r="24" fill="${a[1]}"/><circle cx="24" cy="24" r="24" fill="url(#gl)"/><g transform="translate(9 9) scale(1.25)" fill="none" stroke="currentColor" stroke-width="1.6" stroke-linecap="round" stroke-linejoin="round">${a[3]}</g></svg>`:e};
const R=(i,t,s,b,c="")=>`<div class="row ${c}"><div class="i">${ic(i)}</div><div class="m"><b>${t}</b><span>${s}</span></div>${b}</div>`;
const B=(a,i,c,l,x="")=>`<button class="btn buy" data-a="${a}" data-i="${i}" data-cost="${c}" ${x}>${l}</button>`;
const LK=(i,t,p)=>R("🔒",t,"Unlocks at prestige "+p,"","lock");

function view(){
  document.querySelectorAll("nav div").forEach(d=>d.classList.toggle("on",d.dataset.t===tab));
  let h="";
  if(tab==="earn"){
    h=`<div class="tap" id="tap"><div><div class="big">💵</div><p>Tap here to earn money</p></div></div>
    ${R("👆","Stronger taps · level "+S.cl,"Next level: "+fmt(tapV()*(1+(S.cl+1)*(1+(S.cl+1)*.1))/(1+S.cl*(1+S.cl*.1))),B("cl",0,clCost(),fmt(clCost())))}
    ${R("⚡","Income boost +30%","Lasts 5 min, ready every 15 min",`<button class="btn gold" id="bst" data-a="bst" data-cost="0">Activate</button>`)}
    ${R("\ud83e\udd16","Auto clicker · level "+S.ac+"/100",S.ac?`${nf(acRate(),1)} taps/s · +${fmt(acRate()*tapV())}/s`:"Taps for you automatically. +0.2 taps/s per level",S.ac>=100?`<button class="btn done">Max</button>`:B("ac",0,acCost(),fmt(acCost())))}`;
  }else if(tab==="biz"){
    h=`<h2>My companies <span style="float:right;color:var(--dim)">${S.co.length}/${slots()}</span></h2>`;
    h+=S.co.length?S.co.map((c,i)=>{const t=TY[c[0]];return R(t[0],t[1],`Level ${c[1]} of 10 · ${fmt(t[2]/600*c[1])}/s base`,`<div style="display:flex;flex-direction:column;gap:6px">${c[1]>=10?`<button class="btn done">Max</button>`:B("up",i,upC(c),fmt(upC(c)))}<button class="btn sell" style="padding:6px 10px;min-width:92px" data-a="csell" data-i="${i}">${sellArm===i?"Confirm "+fmt(sellV(c)):"Sell "+fmt(sellV(c))}</button></div>`)}).join(""):`<p class="dim">No companies yet. Start one below.</p>`;
    h+=`<h2>Start a business</h2>`+TY.map((t,i)=>t[3]>S.P?LK(0,t[1],t[3]):R(t[0],t[1],"Earns "+fmt(t[2]/600)+"/s at level 1",B("start",i,t[2],fmt(t[2])))).join("");
    h+=`<h2>Business mergers</h2><p class="dim">Reach the levels, pay the investment, and earn a permanent income bonus.</p>`+MG.map((m,i)=>{
      if(m[4]>S.P)return LK(0,m[0],m[4]);const ok=reqOK(m);
      const rq=m[5].map(r=>(S.co.some(c=>c[0]===r[0]&&c[1]>=r[1])?"✓ ":"○ ")+TY[r[0]][1]+" lvl "+r[1]).join(", ");
      return R(m[1],m[0]+" · +"+m[3]*100+"%",rq,S.mg[i]?`<button class="btn done">Owned</button>`:B("mg",i,m[2],fmt(m[2]),ok?"":'data-nok="1"'),S.mg[i]?"ok":"")}).join("");
  }else if(tab==="inv"){
    h=`<div class="seg">${[["s","Shares"],["r","Real estate"],["c","Crypto"]].map(p=>`<div class="pill ${sub===p[0]?"on":""}" data-a="sub" data-i="${p[0]}">${p[1]}</div>`).join("")}</div>`;
    if(sub==="r"){
      h+=`<div class="bal" style="margin-bottom:12px"><small>Property value</small><b style="font-size:26px">${fmt(RE.reduce((a,r,i)=>a+r[2]*S.re[i],0))}</b><div class="r"><span>Rent <b>${fmt(reI()*mult()*3600)}/h</b></span></div></div>`;
      h+=S.P<1?LK(0,"Real estate",1):RE.map((r,i)=>R(r[0],r[1],`Owned ${S.re[i]} · rent ${fmt(r[2]/1200*(1+.5*sk("i3"))*mult())}/s each`,B("re",i,reC(i),fmt(reC(i))))).join("");
    }else if(sub==="c"&&S.P<2){h+=LK(0,"Cryptocurrency",2)}
    else{
      h+=`<div class="bal" style="margin-bottom:12px"><small>Portfolio value</small><b id="pv" style="font-size:26px"></b><div class="r"><span>All-time <b id="pp"></b></span><span>Yield <b id="py"></b>/h</span></div></div>
      <div class="seg">${[1,10,100].map(q=>`<div class="pill ${S.q===q?"on":""}" data-a="q" data-i="${q}">×${q}</div>`).join("")}</div>`;
      h+=ST.map((s,i)=>s[4]!==sub?"":`<div class="row"><div class="m"><b>${s[0]}</b><span id="h${i}"></span><span>${s[2]<.045?"Stable":"Growth"} · ${s[3]?s[3]*100+"%/h dividend":"no dividend"}</span></div><div style="text-align:right"><b id="p${i}"></b><span id="c${i}" style="display:block;font-size:13px"></span></div><div style="display:flex;flex-direction:column;gap:6px"><button class="btn buy" style="min-width:64px;padding:6px 10px" data-a="buy" data-i="${i}">Buy</button><button class="btn sell" style="min-width:64px;padding:6px 10px" data-a="sell" data-i="${i}">Sell</button></div></div>`).join("");
    }
  }else if(tab==="items"){
    h=`<p class="dim">Item bonus: +${nf(IB()*100,0)}% to all income. Finish a set for +10%.</p>`;
    h+=IT.map((g,j)=>{
      if(g[7]>S.P)return LK(0,g[2],g[7]);const n=ig(g);
      const nx=g[8]?g[8][n]:"Piece "+(n+1);
      return R(g[1],g[2],`${n} of ${g[3]} · +${nf(g[6]*100*(1+.5*sk("i4")),0)}% each`+(n<g[3]?" · next: "+nx:""),n>=g[3]?`<button class="btn done">Complete</button>`:B("g",j,gCost(g),fmt(gCost(g))),n>=g[3]?"ok":"")}).join("");
  }else if(tab==="skill"){
    const own=SK.filter(k=>S.sk[k[0]]).length;
    h=`<div class="bal"><small>Skill points</small><b id="pts">${avail()}</b><div style="height:12px;background:#0b1d3b;border-radius:8px;overflow:hidden;margin-top:10px"><div id="spb" style="height:100%;width:${spPct()}%;background:linear-gradient(90deg,var(--gold),var(--green))"></div></div><div class="r"><span id="spt">Next point: ${fmt(S.run)} of ${fmt(spNext())} earned this run</span></div></div>`;
    ["Taps","Business","Investing","Master"].forEach(br=>{
      h+=`<h2>${br}</h2>`+SK.filter(k=>k[5]===br).map(k=>{
        if(S.sk[k[0]])return R("✅",k[1],k[2],"","ok");
        const need=k[4].filter(r=>!S.sk[r]).map(r=>SK.find(x=>x[0]===r)[1]);
        if(need.length)return R("🔒",k[1],"Needs: "+need.join(", "),"","lock");
        return R("🌟",k[1],k[2],`<button class="btn" data-a="sk" data-i="${k[0]}" data-sc="${k[3]}">${k[3]} pt</button>`)}).join("")});
    h+=`<h2>Prestige ${S.P} of 10</h2><p class="dim">Skills unlocked: ${own} of ${SK.length}. Unlock every skill to prestige.</p>`;
    if(S.P>=10)h+=R("👑","Legend","You reached the maximum prestige.","","ok");
    else{const all=own===SK.length;h+=R("🔁","Prestige to level "+(S.P+1),"Resets everything except your auto clicker level. +75% income per prestige, bigger start cash. Unlocks: "+PU[S.P],`<button class="btn ${all?"gold":"off"}" data-a="pres" data-nok="${all?0:1}">${presArm?"Confirm":"Prestige"}</button>`)}
  }else{
    const c=cats(),w=c.reduce((a,x)=>a+x[2],0);
    h=`<h2>Fortune</h2><div class="bal"><b>${fmt(w)}</b><div class="r"><span>Prestige <b>${S.P}/10</b></span><span>Multiplier <b>×${nf(mult(),2)}</b></span></div></div>
    <div class="bar">${c.map(x=>`<div style="flex:${Math.max(x[2],1e-4)};background:${x[1]}"></div>`).join("")}</div>
    <div class="grid">${c.map(x=>`<div class="stat" style="border-left-color:${x[1]}"><span>${x[0]}</span><b>${fmt(x[2])}</b></div>`).join("")}</div>`
    +[["Total earned (all time)",fmt(S.total)],["Earned this run",fmt(S.run)],["Taps",S.taps.toLocaleString()],["Companies",S.co.length]].map(r=>`<div class="stat"><span>${r[0]}</span><b>${r[1]}</b></div>`).join("")
    +`<h2>Sound</h2><div class="seg">${[["m","🎵 Music"],["s","🔔 Effects"]].map(p=>`<div class="pill ${SND.pref[p[0]]?"on":""}" data-a="snd" data-i="${p[0]}">${p[1]} ${SND.pref[p[0]]?"on":"off"}</div>`).join("")}</div>`
    +`<button class="btn sell" style="width:100%;margin-top:10px;padding:12px" data-a="reset">${resetArm?"Tap again to erase everything":"Reset game"}</button>`;
  }
  $("#main").innerHTML=h;
  if(tab==="inv")stocksUI();
  afford();
}
function stocksUI(){
  const e=$("#pv");if(!e)return;
  const v=stV(sub),sp=ST.reduce((a,s,i)=>a+(s[4]===sub?S.sp[i]:0),0),pr=v-sp;
  e.textContent=fmt(v);const pp=$("#pp");pp.textContent=(pr>=0?"+":"-")+fmt(Math.abs(pr));pp.style.color=pr>=0?"var(--green)":"var(--red)";
  $("#py").textContent=fmt(ST.reduce((a,s,i)=>a+(s[4]===sub?S.st[i]*S.p[i]*s[3]:0),0)*divM()*mult());
  ST.forEach((s,i)=>{const p=$("#p"+i);if(!p)return;p.textContent=fmt(S.p[i]);const c=S.pc[i],ce=$("#c"+i);ce.textContent=(c>=0?"▲ ":"▼ ")+fmt(Math.abs(c));ce.className=c>=0?"up-c":"dn-c";const r=S.st[i]*S.p[i]-S.sp[i];$("#h"+i).textContent=S.st[i]?`${S.st[i]} held · ${r>=0?"+":"-"}${fmt(Math.abs(r))}`:"Not owned"});
}
function afford(){
  document.querySelectorAll(".buy[data-cost]").forEach(b=>b.classList.toggle("off",S.money<+b.dataset.cost||b.dataset.nok==="1"));
  document.querySelectorAll("[data-sc]").forEach(b=>b.classList.toggle("off",+b.dataset.sc>avail()));
  const p=$("#pts");if(p)p.textContent=avail();
  const sb=$("#spb");if(sb){sb.style.width=spPct()+"%";$("#spt").textContent="Next point: "+fmt(S.run)+" of "+fmt(spNext())+" earned this run"}
}
$("#nav").addEventListener("click",e=>{const d=e.target.closest("[data-t]");if(d){tab=d.dataset.t;resetArm=presArm=false;sellArm=-1;SND.tick();view()}});
$("#main").addEventListener("pointerdown",e=>{
  const t=e.target.closest("#tap");if(!t)return;
  let v=tapV(),lb="+";if(sk("t4")&&Math.random()<.1){v*=10;lb="×10 +"}
  gain(v);S.taps++;SND.tap();
  const r=t.getBoundingClientRect(),f=document.createElement("div");f.className="fl";f.textContent=lb+fmt(v);f.style.left=Math.max(4,e.clientX-r.left-30)+"px";f.style.top=(e.clientY-r.top-20)+"px";t.appendChild(f);setTimeout(()=>f.remove(),800);
  t.classList.add("hit");setTimeout(()=>t.classList.remove("hit"),80);
});
$("#main").addEventListener("click",e=>{
  const b=e.target.closest("[data-a]");if(!b)return;const a=b.dataset.a,i=b.dataset.i,n=+i;
  if(a!=="csell")sellArm=-1;
  const m0=S.money,pr0=S.P,sk0=Object.keys(S.sk).length,bu0=S.bu;
  const pay=c=>{if(S.money<c)return false;S.money-=c;return true};
  if(a==="cl"){pay(clCost())&&S.cl++}
  else if(a==="ac"){if(S.ac<100&&pay(acCost()))S.ac++}
  else if(a==="bst"){if(Date.now()>=S.bc){S.bu=Date.now()+3e5;S.bc=Date.now()+9e5}}
  else if(a==="start"){if(S.co.length>=slots())toast("All company slots are full");else if(pay(TY[n][2]))S.co.push([n,1])}
  else if(a==="up"){const c=S.co[n];if(c&&c[1]<10&&pay(upC(c)))c[1]++}
  else if(a==="mg"){const m=MG[n];if(!S.mg[n]&&reqOK(m)&&pay(m[2]))S.mg[n]=1;else if(!reqOK(m))toast("Reach the required company levels first")}
  else if(a==="csell"){if(sellArm!==n){sellArm=n;view();return}const c=S.co[n];if(c){S.money+=sellV(c);S.co.splice(n,1)}sellArm=-1}
  else if(a==="sub"){sub=i}
  else if(a==="q"){S.q=n}
  else if(a==="buy"){const q=Math.min(S.q,Math.floor(S.money/S.p[n]));if(q>0){const c=q*S.p[n];S.money-=c;S.sp[n]+=c;S.st[n]+=q}else toast("Not enough money")}
  else if(a==="sell"){const q=Math.min(S.q,S.st[n]);if(q>0){const avg=S.sp[n]/S.st[n];S.money+=q*S.p[n];S.sp[n]-=avg*q;S.st[n]-=q;if(!S.st[n])S.sp[n]=0}}
  else if(a==="re"){pay(reC(n))&&S.re[n]++}
  else if(a==="g"){const g=IT[n];if(ig(g)<g[3]&&pay(gCost(g)))S.g[g[0]]=ig(g)+1}
  else if(a==="sk"){const k=SK.find(x=>x[0]===i);if(k&&!S.sk[i]&&k[4].every(r=>S.sk[r])&&avail()>=k[3])S.sk[i]=1}
  else if(a==="pres"){
    if(SK.some(k=>!S.sk[k[0]])){toast("Unlock every skill first");return}
    if(!presArm){presArm=true;view();return}
    S=fresh(S.P+1,{total:S.total,taps:S.taps,ac:S.ac});presArm=false;tab="earn";toast("Prestige "+S.P+"! Unlocked: "+PU[S.P-1]);
  }
  else if(a==="snd"){SND.set(i)}
  else if(a==="reset"){if(!resetArm){resetArm=true;view();return}try{localStorage.removeItem(KEY)}catch(x){}location.reload();return}
  const dm=S.money-m0;
  if(S.P>pr0)SND.win();
  else if(a==="sk"){Object.keys(S.sk).length>sk0?SND.skill():SND.err()}
  else if(a==="bst"){S.bu!==bu0?SND.boost():SND.err()}
  else if(a==="sub"||a==="q"||a==="snd")SND.tick();
  else if(dm<0)SND.buy();
  else if(dm>0)SND.sell();
  else if(b.classList.contains("off")||a==="buy"||a==="start")SND.err();
  view();head();save();
});
function head(){$("#bal").textContent=fmt(S.money);$("#inc").textContent=fmt(income()+acRate()*tapV())+"/s";$("#ptap").textContent=fmt(tapV());$("#pl").textContent="Balance · Prestige "+S.P}
setInterval(()=>{ST.forEach((s,i)=>{const p=S.p[i],d=(Math.random()-.5)*s[2]*1.2+(s[1]-p)/s[1]*.02;const n=Math.max(s[1]*.3,p*(1+d));S.pc[i]=n-p;S.p[i]=n});if(tab==="inv")stocksUI()},2500);
let last=Date.now(),meT=0;
setInterval(()=>{
  const n=Date.now(),dt=(n-last)/1000;last=n;gain(income()*dt+acRate()*tapV()*dt);head();afford();
  if(tab==="me"&&!resetArm&&!down&&++meT%4===0)view();
  const b=$("#bst");if(b){const w=S.bc-n;b.dataset.nok=w>0?1:0;b.textContent=n<S.bu?"Active "+tm(S.bu-n):w>0?"Ready in "+tm(w):"Activate";b.style.opacity=w>0?.6:1}
},250);
let acAcc=0;
function autoFx(n){const t=$("#tap");if(!t||!n)return;SND.auto();const w=t.clientWidth,h=t.clientHeight,v="+"+fmt(tapV());for(let k=0;k<Math.min(n,4);k++){const x=30+Math.random()*(w-90),y=40+Math.random()*(h-100),r=document.createElement("div"),f=document.createElement("div");r.className="rip";r.style.left=x+"px";r.style.top=y+"px";f.className="fl a";f.textContent=v;f.style.left=(x-20)+"px";f.style.top=(y-10)+"px";t.append(r,f);setTimeout(()=>{r.remove();f.remove()},800)}t.classList.add("hit");setTimeout(()=>t.classList.remove("hit"),60)}
setInterval(()=>{acAcc+=acRate()*.1;const n=Math.floor(acAcc);acAcc-=n;autoFx(n)},100);
setInterval(save,5000);
document.addEventListener("visibilitychange",()=>{if(document.hidden)save()});
const cap=S.P>=9?86400:7200+21600*sk("i5");
const away=Math.min((Date.now()-S.t)/1000,cap);
if(away>60&&income()>0){const g=income()*away;gain(g);toast("While you were away: +"+fmt(g))}
SND.ui();view();head();
</script>
</body></html>
