<!DOCTYPE html>
<html lang="ja">
<head>
<meta charset="UTF-8">
<meta name="robots" content="noindex"> 
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0">
<title>CoC 6版→7版 変換ツール</title>
<style>
*{box-sizing:border-box;margin:0;padding:0;-webkit-tap-highlight-color:transparent}
:root{
  --bg:#ffffff;--bg2:#f5f4f0;--bg3:#eeede8;
  --text:#1a1a18;--text2:#5a5a55;--text3:#999990;
  --border:rgba(0,0,0,0.12);--border2:rgba(0,0,0,0.22);
  --success:#1d9e75;--success-bg:#e1f5ee;
  --radius:8px;--radius-lg:12px;
}
@media(prefers-color-scheme:dark){:root{
  --bg:#1e1e1c;--bg2:#2a2a27;--bg3:#323230;
  --text:#e8e6de;--text2:#9a9890;--text3:#666660;
  --border:rgba(255,255,255,0.1);--border2:rgba(255,255,255,0.2);
}}
body{background:var(--bg);color:var(--text);font-family:-apple-system,BlinkMacSystemFont,'Hiragino Sans','Noto Sans JP',sans-serif;font-size:16px;min-height:100vh}
.app{max-width:680px;margin:0 auto;padding:20px 16px 60px}
h1{font-size:17px;font-weight:500;margin-bottom:4px}
.subtitle{font-size:13px;color:var(--text2);margin-bottom:24px}
.name-wrap{margin-bottom:20px}
label.field-label{display:block;font-size:12px;color:var(--text2);margin-bottom:6px}
input[type=text],input[type=number]{background:var(--bg2);border:0.5px solid var(--border2);border-radius:var(--radius);color:var(--text);font-family:inherit;font-size:15px;padding:10px 12px;outline:none;transition:border .15s;-moz-appearance:textfield;width:100%}
input[type=number]::-webkit-outer-spin-button,input[type=number]::-webkit-inner-spin-button{-webkit-appearance:none}
input:focus{border-color:var(--text2)}
.tabs{display:flex;gap:2px;border-bottom:0.5px solid var(--border);margin-bottom:20px;overflow-x:auto;-webkit-overflow-scrolling:touch}
.tab{background:none;border:none;border-bottom:2px solid transparent;color:var(--text2);cursor:pointer;font-family:inherit;font-size:13px;padding:10px 14px;white-space:nowrap;transition:color .15s}
.tab.active{color:var(--text);border-bottom-color:var(--text);font-weight:500}
.col-headers{display:grid;grid-template-columns:90px 72px 1fr 1fr 1fr;gap:6px;padding:0 10px 6px;font-size:11px;color:var(--text3)}
.col-headers span:not(:first-child){text-align:center}
.stat-row{display:grid;grid-template-columns:90px 72px 1fr 1fr 1fr;gap:6px;align-items:center;background:var(--bg2);border-radius:var(--radius);padding:10px;margin-bottom:4px}
.stat-name{display:flex;align-items:baseline;gap:5px}
.stat-name strong{font-size:14px;font-weight:500}
.stat-name span{font-size:11px;color:var(--text2)}
.stat-val{text-align:center;font-size:16px;font-weight:500}
.stat-half,.stat-fifth{text-align:center;font-size:14px;color:var(--text2)}
.stat-empty{text-align:center;color:var(--text3)}
.derived{margin-top:20px}
.derived-title{font-size:11px;color:var(--text3);letter-spacing:.05em;margin-bottom:10px}
.derived-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:8px}
.metric{background:var(--bg2);border-radius:var(--radius);padding:10px 8px;text-align:center}
.metric-label{font-size:10px;color:var(--text3);margin-bottom:4px}
.metric-val{font-size:20px;font-weight:500}
.metric-desc{font-size:10px;color:var(--text3);margin-top:2px}
.skill-headers{display:grid;grid-template-columns:1fr 76px 58px 58px 36px;gap:6px;padding:0 4px 8px;font-size:11px;color:var(--text3)}
.skill-headers span:not(:first-child){text-align:center}
.skill-row{display:grid;grid-template-columns:1fr 76px 58px 58px 36px;gap:6px;align-items:center;margin-bottom:6px}
.skill-val{text-align:center;font-size:14px;color:var(--text2);background:var(--bg2);border-radius:var(--radius);padding:10px 4px}
.skill-empty{text-align:center;color:var(--text3)}
.btn-remove{background:none;border:0.5px solid var(--border2);border-radius:var(--radius);color:var(--text2);cursor:pointer;font-family:inherit;font-size:18px;height:42px;width:36px;display:flex;align-items:center;justify-content:center;transition:background .12s}
.btn-remove:active{background:var(--bg2)}
.btn-add{background:none;border:0.5px solid var(--border2);border-radius:var(--radius);color:var(--text2);cursor:pointer;font-family:inherit;font-size:13px;padding:10px 14px;margin-top:8px;display:flex;align-items:center;gap:6px;transition:background .12s}
.btn-add:active{background:var(--bg2)}
.dice-hint{font-size:13px;color:var(--text2);line-height:1.7;margin-bottom:6px}
.dice-hint small{font-size:12px;color:var(--text3)}
.dice-section-title{font-size:11px;color:var(--text3);letter-spacing:.05em;margin:16px 0 10px}
.dice-blocks{display:grid;grid-template-columns:repeat(auto-fill,minmax(180px,1fr));gap:8px}
.dice-block{background:var(--bg2);border-radius:var(--radius);padding:12px}
.dice-block-name{font-size:12px;color:var(--text2);font-weight:500;margin-bottom:10px}
.dice-row{display:flex;align-items:center;justify-content:space-between;margin-bottom:6px}
.dice-row:last-child{margin-bottom:0}
.dice-row-label{font-size:12px;color:var(--text2)}
.cmd-chip{display:inline-flex;align-items:center;gap:5px;background:var(--bg);border:0.5px solid var(--border2);border-radius:var(--radius);color:var(--text);cursor:pointer;font-family:monospace;font-size:13px;padding:5px 9px;transition:background .12s;user-select:none;white-space:nowrap}
.cmd-chip:active{background:var(--bg3)}
.cmd-chip.copied{border-color:var(--success);color:var(--success)}
.bonus-block{background:var(--bg2);border-radius:var(--radius);padding:12px;margin-top:8px}
.bonus-title{font-size:11px;color:var(--text3);letter-spacing:.05em;margin-bottom:10px}
.bonus-grid{display:grid;grid-template-columns:1fr 1fr;gap:8px}
.bonus-row{display:flex;flex-direction:column;gap:5px}
.bonus-label{font-size:11px;color:var(--text2)}
.dice-empty{font-size:13px;color:var(--text3);text-align:center;padding:40px 0}
.ref-row{display:grid;grid-template-columns:1fr 20px 1fr;gap:8px;align-items:center;background:var(--bg2);border-radius:var(--radius);padding:10px 12px;margin-bottom:4px}
.ref-v6{font-size:13px;color:var(--text2)}
.ref-v7{font-size:13px;font-weight:500}
.ref-arrow{font-size:13px;color:var(--text3);text-align:center}
.combat-row{background:var(--bg2);border-radius:var(--radius);padding:10px 12px;margin-bottom:4px}
.combat-label{font-size:11px;color:var(--text3);margin-bottom:6px}
.combat-inner{display:grid;grid-template-columns:1fr 20px 1fr;gap:8px;align-items:center}
.combat-v6{font-size:12px;color:var(--text2)}
.combat-v7{font-size:12px}
.db-row{display:grid;grid-template-columns:1fr 90px 70px;gap:6px;align-items:center;background:var(--bg2);border-radius:var(--radius);padding:8px 12px;margin-bottom:3px}
.db-range{font-size:12px;color:var(--text2)}
.db-val{font-size:14px;font-weight:500;text-align:center}
.db-build{font-size:12px;color:var(--text2);text-align:center}
.section-title{font-size:11px;color:var(--text3);letter-spacing:.05em;margin:0 0 10px}
.section-gap{margin-top:20px}
@media(max-width:400px){
  .stat-row{grid-template-columns:80px 64px 1fr 1fr 1fr}
  .col-headers{grid-template-columns:80px 64px 1fr 1fr 1fr}
  .derived-grid{grid-template-columns:repeat(3,1fr)}
}
</style>
</head>
<body>
<div class="app">
  <h1>CoC 6版 → 7版 変換ツール</h1>
  <p class="subtitle">NPC・モンスターのステータス変換＆ここふぉりあ用ダイスコマンド生成</p>

  <div class="name-wrap">
    <label class="field-label" for="npc-name">NPC / モンスター名</label>
    <input type="text" id="npc-name" placeholder="名前を入力...">
  </div>

  <div class="tabs">
    <button class="tab active" data-tab="stats">ステータス変換</button>
    <button class="tab" data-tab="skills">技能</button>
    <button class="tab" data-tab="dice">ダイスコマンド</button>
    <button class="tab" data-tab="ref">判定リファレンス</button>
  </div>

  <div id="tab-stats">
    <div class="col-headers">
      <span>能力値</span><span>6版入力</span><span>7版</span><span>1/2</span><span>1/5</span>
    </div>
    <div id="stat-rows"></div>
    <div class="derived" id="derived" style="display:none">
      <div class="derived-title">派生ステータス</div>
      <div class="derived-grid" id="derived-grid"></div>
    </div>
  </div>

  <div id="tab-skills" style="display:none">
    <div class="skill-headers">
      <span>技能名</span><span>値</span><span>1/2</span><span>1/5</span><span></span>
    </div>
    <div id="skill-rows"></div>
    <button class="btn-add" id="add-skill">＋ 技能を追加</button>
  </div>

  <div id="tab-dice" style="display:none">
    <p class="dice-hint">クリックでコピー → ここふぉりあにそのまま貼り付けて振れます<br><small>CC(n) = d100を振ってnと比較し、成功レベルを自動判定</small></p>
    <div id="dice-content"></div>
    <div class="bonus-block">
      <div class="bonus-title">ボーナス・ペナルティダイス</div>
      <div class="bonus-grid">
        <div class="bonus-row"><span class="bonus-label">ボーナス1個</span><button class="cmd-chip" data-cmd="(2D100H)">(2D100H)</button></div>
        <div class="bonus-row"><span class="bonus-label">ボーナス2個</span><button class="cmd-chip" data-cmd="(3D100H)">(3D100H)</button></div>
        <div class="bonus-row"><span class="bonus-label">ペナルティ1個</span><button class="cmd-chip" data-cmd="(2D100L)">(2D100L)</button></div>
        <div class="bonus-row"><span class="bonus-label">ペナルティ2個</span><button class="cmd-chip" data-cmd="(3D100L)">(3D100L)</button></div>
      </div>
    </div>
  </div>

  <div id="tab-ref" style="display:none">
    <div class="section-title">判定難易度の変換</div>
    <div class="ref-row"><span class="ref-v6">能力値 ×5（通常）</span><span class="ref-arrow">→</span><span class="ref-v7">通常成功（そのまま）</span></div>
    <div class="ref-row"><span class="ref-v6">能力値 ×3</span><span class="ref-arrow">→</span><span class="ref-v7">困難成功（値の1/2以下）</span></div>
    <div class="ref-row"><span class="ref-v6">能力値 ×1</span><span class="ref-arrow">→</span><span class="ref-v7">極限成功（値の1/5以下）</span></div>
    <div class="ref-row"><span class="ref-v6">抵抗ロール</span><span class="ref-arrow">→</span><span class="ref-v7">対抗ロール（POW vs POW など）</span></div>

    <div class="section-gap">
      <div class="section-title">戦闘ルールの主な変更点</div>
      <div class="combat-row"><div class="combat-label">回避</div><div class="combat-inner"><span class="combat-v6">6版: 技能ロールのみ</span><span class="ref-arrow">→</span><span class="combat-v7">7版: 攻撃者との対抗ロール</span></div></div>
      <div class="combat-row"><div class="combat-label">受け流し</div><div class="combat-inner"><span class="combat-v6">6版: 武器強度で限界ダメージ</span><span class="ref-arrow">→</span><span class="combat-v7">7版: ビルド差で限界ダメージ変動</span></div></div>
      <div class="combat-row"><div class="combat-label">反撃</div><div class="combat-inner"><span class="combat-v6">6版: なし</span><span class="ref-arrow">→</span><span class="combat-v7">7版: 受け流し成功時に反撃可</span></div></div>
      <div class="combat-row"><div class="combat-label">組み付き</div><div class="combat-inner"><span class="combat-v6">6版: DEX対抗</span><span class="ref-arrow">→</span><span class="combat-v7">7版: ビルド値を使用して解決</span></div></div>
      <div class="combat-row"><div class="combat-label">コンバットマヌーバー</div><div class="combat-inner"><span class="combat-v6">6版: なし</span><span class="ref-arrow">→</span><span class="combat-v7">7版: 転倒・武装解除・押しつぶし</span></div></div>
    </div>

    <div class="section-gap">
      <div class="section-title">ダメージボーナス表（STR+SIZ合計）</div>
      <div class="db-row"><span class="db-range">2〜64</span><span class="db-val">−2</span><span class="db-build">ビルド −2</span></div>
      <div class="db-row"><span class="db-range">65〜84</span><span class="db-val">−1</span><span class="db-build">ビルド −1</span></div>
      <div class="db-row"><span class="db-range">85〜124</span><span class="db-val">なし</span><span class="db-build">ビルド 0</span></div>
      <div class="db-row"><span class="db-range">125〜164</span><span class="db-val">+1D4</span><span class="db-build">ビルド 1</span></div>
      <div class="db-row"><span class="db-range">165〜204</span><span class="db-val">+1D6</span><span class="db-build">ビルド 2</span></div>
      <div class="db-row"><span class="db-range">205〜284</span><span class="db-val">+2D6</span><span class="db-build">ビルド 3</span></div>
      <div class="db-row"><span class="db-range">285〜364</span><span class="db-val">+3D6</span><span class="db-build">ビルド 4</span></div>
      <div class="db-row"><span class="db-range">365〜444</span><span class="db-val">+4D6</span><span class="db-build">ビルド 5</span></div>
      <div class="db-row"><span class="db-range">445+</span><span class="db-val">+5D6</span><span class="db-build">ビルド 6</span></div>
    </div>
  </div>
</div>

<script>
const STATS=[
  {key:"str",label:"STR",jp:"筋力"},{key:"con",label:"CON",jp:"体力"},
  {key:"siz",label:"SIZ",jp:"体格"},{key:"int",label:"INT",jp:"知性"},
  {key:"pow",label:"POW",jp:"精神力"},{key:"dex",label:"DEX",jp:"敏捷性"},
  {key:"app",label:"APP",jp:"外見"},{key:"edu",label:"EDU",jp:"教育"},
];

const vals={};
STATS.forEach(s=>vals[s.key]="");

function getDB(t){
  if(t<=64)return{db:"−2",build:"−2"};if(t<=84)return{db:"−1",build:"−1"};
  if(t<=124)return{db:"なし",build:"0"};if(t<=164)return{db:"+1D4",build:"1"};
  if(t<=204)return{db:"+1D6",build:"2"};if(t<=284)return{db:"+2D6",build:"3"};
  if(t<=364)return{db:"+3D6",build:"4"};if(t<=444)return{db:"+4D6",build:"5"};
  return{db:"+5D6",build:"6"};
}
function getMOV(s,d,sz){
  if(!s&&!d&&!sz)return"—";
  if(s<sz&&d<sz)return"7";if(s>sz&&d>sz)return"9";return"8";
}

function buildStatRows(){
  const wrap=document.getElementById("stat-rows");
  wrap.innerHTML="";
  STATS.forEach(({key,label,jp})=>{
    const row=document.createElement("div");
    row.className="stat-row";
    row.innerHTML=`
      <div class="stat-name"><strong>${label}</strong><span>${jp}</span></div>
      <div><input type="number" min="0" max="99" placeholder="—" data-key="${key}" style="text-align:center;padding:9px 4px"></div>
      <div class="stat-val" id="v7-${key}">—</div>
      <div class="stat-half" id="half-${key}">—</div>
      <div class="stat-fifth" id="fifth-${key}">—</div>
    `;
    wrap.appendChild(row);
    row.querySelector("input").addEventListener("input",e=>{
      const v=e.target.value.replace(/[^\d]/g,"");
      e.target.value=v;
      vals[key]=v;
      updateStats();
    });
  });
}

function updateStats(){
  STATS.forEach(({key})=>{
    const raw=parseInt(vals[key])||0;
    const v7=raw*5;
    document.getElementById(`v7-${key}`).textContent=v7>0?v7:"—";
    document.getElementById(`half-${key}`).textContent=v7>0?Math.floor(v7/2):"—";
    document.getElementById(`fifth-${key}`).textContent=v7>0?Math.floor(v7/5):"—";
  });
  updateDerived();
  updateDice();
}

function updateDerived(){
  const con=(parseInt(vals.con)||0)*5;
  const siz=(parseInt(vals.siz)||0)*5;
  const pow=parseInt(vals.pow)||0;
  const str=(parseInt(vals.str)||0)*5;
  const dex=(parseInt(vals.dex)||0)*5;
  const hasAny=STATS.some(s=>vals[s.key]!=="");
  const derived=document.getElementById("derived");
  derived.style.display=hasAny?"":"none";
  if(!hasAny)return;
  const hp=(con+siz)>0?Math.floor((con+siz)/10):null;
  const mp=pow>0?pow:null;
  const san=pow>0?pow*5:null;
  const strSiz=str+siz;
  const{db,build}=getDB(strSiz);
  const mov=getMOV(str,dex,siz);
  document.getElementById("derived-grid").innerHTML=[
    {label:"HP",value:hp!==null?hp:"—",desc:"(CON+SIZ)÷10"},
    {label:"MP",value:mp!==null?mp:"—",desc:"= POW"},
    {label:"SAN",value:san!==null?san:"—",desc:"= POW"},
    {label:"ダメボ",value:strSiz>0?db:"—",desc:`STR+SIZ=${strSiz}`},
    {label:"ビルド",value:strSiz>0?build:"—",desc:"組み付き判定"},
    {label:"MOV",value:mov,desc:"移動力"},
  ].map(m=>`<div class="metric"><div class="metric-label">${m.label}</div><div class="metric-val">${m.value}</div><div class="metric-desc">${m.desc}</div></div>`).join("");
}

let skillList=[{id:0,name:"",value:""}];
let nextId=1;

function buildSkillRows(){
  const wrap=document.getElementById("skill-rows");
  wrap.innerHTML="";
  skillList.forEach(sk=>{
    const n=parseInt(sk.value)||0;
    const row=document.createElement("div");
    row.className="skill-row";
    row.innerHTML=`
      <input type="text" placeholder="技能名..." value="${sk.name}" data-id="${sk.id}" data-field="name" style="padding:10px 10px">
      <input type="number" min="0" max="100" placeholder="—" value="${sk.value}" data-id="${sk.id}" data-field="value" style="text-align:center;padding:10px 4px">
      <div class="${n>0?'skill-val':'skill-val skill-empty'}">${n>0?Math.floor(n/2):"—"}</div>
      <div class="${n>0?'skill-val':'skill-val skill-empty'}">${n>0?Math.floor(n/5):"—"}</div>
      <button class="btn-remove" data-id="${sk.id}" aria-label="削除">×</button>
    `;
    wrap.appendChild(row);
  });
  wrap.querySelectorAll("input").forEach(inp=>{
    inp.addEventListener("input",e=>{
      const id=parseInt(e.target.dataset.id);
      const field=e.target.dataset.field;
      skillList=skillList.map(s=>s.id===id?{...s,[field]:e.target.value}:s);
      buildSkillRows();
      updateDice();
    });
  });
  wrap.querySelectorAll(".btn-remove").forEach(btn=>{
    btn.addEventListener("click",e=>{
      const id=parseInt(e.target.dataset.id);
      if(skillList.length>1){skillList=skillList.filter(s=>s.id!==id);buildSkillRows();updateDice();}
    });
  });
}

document.getElementById("add-skill").addEventListener("click",()=>{
  skillList.push({id:nextId++,name:"",value:""});
  buildSkillRows();
});

function makeDiceBlock(name,value){
  const half=Math.floor(value/2);
  const fifth=Math.floor(value/5);
  return `<div class="dice-block">
    <div class="dice-block-name">${name}</div>
    <div class="dice-row"><span class="dice-row-label">通常成功</span><button class="cmd-chip" data-cmd="CC(${value})">CC(${value})</button></div>
    <div class="dice-row"><span class="dice-row-label">困難成功</span><button class="cmd-chip" data-cmd="CC(${half})">CC(${half})</button></div>
    <div class="dice-row"><span class="dice-row-label">極限成功</span><button class="cmd-chip" data-cmd="CC(${fifth})">CC(${fifth})</button></div>
  </div>`;
}

function updateDice(){
  const activeStats=STATS.filter(({key})=>(parseInt(vals[key])||0)>0);
  const activeSkills=skillList.filter(s=>s.name&&(parseInt(s.value)||0)>0);
  const content=document.getElementById("dice-content");
  if(activeStats.length===0&&activeSkills.length===0){
    content.innerHTML=`<p class="dice-empty">ステータスか技能を入力してください</p>`;
    return;
  }
  let html="";
  if(activeStats.length>0){
    html+=`<div class="dice-section-title">能力値</div><div class="dice-blocks">`;
    activeStats.forEach(({key,label,jp})=>{
      html+=makeDiceBlock(`${label}（${jp}）`,(parseInt(vals[key])||0)*5);
    });
    html+="</div>";
  }
  if(activeSkills.length>0){
    html+=`<div class="dice-section-title">技能</div><div class="dice-blocks">`;
    activeSkills.forEach(sk=>{
      html+=makeDiceBlock(sk.name,parseInt(sk.value));
    });
    html+="</div>";
  }
  content.innerHTML=html;
  bindCopy(content);
}

function bindCopy(root){
  root.querySelectorAll(".cmd-chip").forEach(btn=>{
    btn.addEventListener("click",e=>{
      const cmd=e.currentTarget.dataset.cmd;
      navigator.clipboard.writeText(cmd).then(()=>{
        e.currentTarget.classList.add("copied");
        const orig=e.currentTarget.textContent;
        e.currentTarget.textContent="コピーしました";
        setTimeout(()=>{e.currentTarget.classList.remove("copied");e.currentTarget.textContent=cmd;},1400);
      });
    });
  });
}

document.querySelectorAll(".cmd-chip[data-cmd]").forEach(btn=>{
  btn.addEventListener("click",e=>{
    const cmd=e.currentTarget.dataset.cmd;
    navigator.clipboard.writeText(cmd).then(()=>{
      const orig=e.currentTarget.textContent;
      e.currentTarget.classList.add("copied");
      e.currentTarget.textContent="コピーしました";
      setTimeout(()=>{e.currentTarget.classList.remove("copied");e.currentTarget.textContent=orig;},1400);
    });
  });
});

document.querySelectorAll(".tab").forEach(btn=>{
  btn.addEventListener("click",()=>{
    document.querySelectorAll(".tab").forEach(b=>b.classList.remove("active"));
    btn.classList.add("active");
    const t=btn.dataset.tab;
    ["stats","skills","dice","ref"].forEach(id=>{
      document.getElementById(`tab-${id}`).style.display=id===t?"":"none";
    });
  });
});

buildStatRows();
buildSkillRows();
updateDice();
</script>
</body>
</html>
