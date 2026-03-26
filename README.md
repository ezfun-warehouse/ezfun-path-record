# ezfun-path-record
EZFUN出貨通路紀錄回報

<!DOCTYPE html>
<html lang="zh-TW">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>EZFUN 出貨通路紀錄回報</title>
<style>
*{box-sizing:border-box;margin:0;padding:0}
body{font-family:-apple-system,BlinkMacSystemFont,'Segoe UI',sans-serif;background:#f5f5f5;color:#333}
.app{padding:1rem;max-width:1200px;margin:0 auto}
h1{font-size:18px;font-weight:600;color:#1a1a1a;margin-bottom:1rem}
select,input[type="date"],input[type="text"],input[type="number"]{height:36px;padding:0 10px;border:1px solid #ddd;border-radius:8px;background:#fff;color:#333;font-size:14px}
button{height:36px;padding:0 14px;border:1px solid #ddd;border-radius:8px;background:#fff;color:#333;font-size:13px;cursor:pointer}
button:hover{background:#f0f0f0}
button.primary{background:#1a73e8;color:#fff;border-color:#1a73e8}
button.primary:hover{background:#1558b0}
button.danger{color:#d32f2f;border-color:#f5c6c6}
button.success{background:#e8f5e9;color:#2e7d32;border-color:#a5d6a7}
.sec-title{font-size:12px;font-weight:600;color:#666;margin-bottom:6px;text-transform:uppercase;letter-spacing:.5px}
.chips{display:flex;flex-wrap:wrap;gap:5px;margin-bottom:8px}
.chip{display:flex;align-items:center;gap:4px;padding:3px 10px;border-radius:20px;background:#e8f0fe;border:1px solid #c5d5f8;font-size:12px;color:#1a56a8}
.chip .del{cursor:pointer;color:#d32f2f;font-size:14px;line-height:1;margin-left:2px}
.add-row{display:flex;gap:6px;margin-bottom:12px}
.table-wrap{overflow-x:auto;border:1px solid #e0e0e0;border-radius:12px;margin-bottom:1rem;background:#fff}
table{width:100%;border-collapse:collapse;font-size:13px}
th{background:#f8f9fa;color:#666;font-weight:600;padding:10px 10px;text-align:center;border-bottom:1px solid #e0e0e0;white-space:nowrap}
th.left{text-align:left;min-width:90px}
td{padding:7px 8px;text-align:center;border-bottom:1px solid #f0f0f0;color:#333}
td.name{text-align:left;font-weight:600;white-space:nowrap;padding:7px 14px}
td.total{font-weight:600;background:#f8f9fa;color:#1a73e8}
tr.total-row td{background:#e8f0fe;font-weight:600;border-top:2px solid #c5d5f8;color:#1a56a8}
tr:last-child td{border-bottom:none}
input.cell{width:68px;height:30px;padding:0 4px;border:1px solid #e0e0e0;border-radius:6px;background:#fff;color:#333;font-size:13px;text-align:center}
input.cell:focus{outline:none;border-color:#1a73e8;box-shadow:0 0 0 2px rgba(26,115,232,.15)}
.tabs{display:flex;gap:5px;flex-wrap:wrap;margin-bottom:12px}
.tab{padding:6px 14px;border-radius:20px;border:1px solid #ddd;background:#fff;font-size:13px;cursor:pointer;color:#666}
.tab.active{background:#1a73e8;color:#fff;border-color:#1a73e8}
.saved-badge{font-size:12px;color:#2e7d32;font-weight:500}
.report-box{background:#f8f9fa;border:1px solid #e0e0e0;border-radius:8px;padding:14px;font-size:13px;white-space:pre-wrap;word-break:break-all;line-height:1.8;color:#333;margin-bottom:8px;font-family:'Courier New',monospace}
.report-section{margin-bottom:20px}
.report-label{font-size:12px;font-weight:600;color:#666;margin-bottom:6px;text-transform:uppercase}
.copy-btn{font-size:12px;height:30px;padding:0 14px;background:#e8f0fe;color:#1a56a8;border-color:#c5d5f8}
.copy-btn:hover{background:#c5d5f8}
.history-row{display:flex;align-items:center;gap:8px;padding:10px 14px;border-bottom:1px solid #f0f0f0;font-size:13px}
.history-row:last-child{border-bottom:none}
.empty{color:#aaa;text-align:center;padding:2rem;font-size:13px}
.top-bar{display:flex;flex-wrap:wrap;gap:8px;align-items:center;margin-bottom:12px}
.row-2col{display:grid;grid-template-columns:1fr 1fr;gap:12px;margin-bottom:12px}
.card{background:#fff;border:1px solid #e0e0e0;border-radius:12px;padding:1rem 1.25rem;margin-bottom:12px}
@media(max-width:600px){.row-2col{grid-template-columns:1fr}}
/* Login */
#login-view{display:flex;flex-direction:column;align-items:center;justify-content:center;min-height:80vh;text-align:center}
.login-card{background:#fff;border:1px solid #e0e0e0;border-radius:16px;padding:2.5rem 2rem;max-width:360px;width:100%}
.login-logo{font-size:28px;font-weight:700;color:#1a73e8;margin-bottom:6px}
.login-sub{font-size:14px;color:#888;margin-bottom:2rem}
.google-btn{display:flex;align-items:center;gap:10px;padding:10px 20px;border:1px solid #ddd;border-radius:8px;background:#fff;font-size:14px;cursor:pointer;width:100%;justify-content:center;font-weight:500}
.google-btn:hover{background:#f5f5f5;border-color:#bbb}
.google-icon{width:20px;height:20px}
.user-bar{display:flex;align-items:center;gap:8px;padding:6px 12px;background:#fff;border:1px solid #e0e0e0;border-radius:20px;font-size:13px;color:#333}
.user-avatar{width:26px;height:26px;border-radius:50%;object-fit:cover}
.user-avatar-placeholder{width:26px;height:26px;border-radius:50%;background:#1a73e8;display:flex;align-items:center;justify-content:center;color:#fff;font-size:11px;font-weight:600}
</style>
</head>
<body>
<div class="app">

  <!-- Login View -->
  <div id="login-view">
    <div class="login-card">
      <div class="login-logo">📦 EZFUN</div>
      <div style="font-size:15px;font-weight:600;color:#333;margin-bottom:4px">出貨通路紀錄回報</div>
      <div class="login-sub">請使用 Google 帳號登入</div>
      <button class="google-btn" onclick="signInWithGoogle()">
        <svg class="google-icon" viewBox="0 0 24 24"><path fill="#4285F4" d="M22.56 12.25c0-.78-.07-1.53-.2-2.25H12v4.26h5.92c-.26 1.37-1.04 2.53-2.21 3.31v2.77h3.57c2.08-1.92 3.28-4.74 3.28-8.09z"/><path fill="#34A853" d="M12 23c2.97 0 5.46-.98 7.28-2.66l-3.57-2.77c-.98.66-2.23 1.06-3.71 1.06-2.86 0-5.29-1.93-6.16-4.53H2.18v2.84C3.99 20.53 7.7 23 12 23z"/><path fill="#FBBC05" d="M5.84 14.09c-.22-.66-.35-1.36-.35-2.09s.13-1.43.35-2.09V7.07H2.18C1.43 8.55 1 10.22 1 12s.43 3.45 1.18 4.93l3.66-2.84z"/><path fill="#EA4335" d="M12 5.38c1.62 0 3.06.56 4.21 1.64l3.15-3.15C17.45 2.09 14.97 1 12 1 7.7 1 3.99 3.47 2.18 7.07l3.66 2.84c.87-2.6 3.3-4.53 6.16-4.53z"/></svg>
        使用 Google 帳號登入
      </button>
      <div id="login-error" style="color:#d32f2f;font-size:12px;margin-top:12px;display:none"></div>
    </div>
  </div>

  <!-- Main App View -->
  <div id="app-view" style="display:none">
    <div class="top-bar">
      <h1>📦 EZFUN 出貨通路紀錄回報</h1>
      <div style="margin-left:auto;display:flex;align-items:center;gap:8px">
        <div class="user-bar" id="user-bar"></div>
        <button onclick="signOut()" style="font-size:12px;color:#888">登出</button>
      </div>
    </div>

    <div id="main-view">
      <div class="top-bar">
        <div style="display:flex;gap:6px;align-items:center;flex-wrap:wrap">
          <input type="date" id="date-picker" onchange="loadData()">
          <button onclick="goToday()" style="font-size:12px">今天</button>
          <span class="saved-badge" id="save-badge"></span>
        </div>
      </div>
      <div class="tabs" id="warehouse-tabs"></div>
      <div class="card">
        <div class="row-2col">
          <div>
            <div class="sec-title">廠商（直列）</div>
            <div class="chips" id="vendor-chips"></div>
            <div class="add-row">
              <input type="text" id="new-vendor" placeholder="新增廠商" style="width:140px" onkeydown="if(event.key==='Enter')addVendor()">
              <button onclick="addVendor()">+</button>
              <button onclick="showManage('vendor')" class="danger" style="font-size:12px">管理</button>
            </div>
          </div>
          <div>
            <div class="sec-title">通路物流（橫列）</div>
            <div class="chips" id="channel-chips"></div>
            <div class="add-row">
              <input type="text" id="new-channel" placeholder="新增通路" style="width:140px" onkeydown="if(event.key==='Enter')addChannel()">
              <button onclick="addChannel()">+</button>
              <button onclick="showManage('channel')" class="danger" style="font-size:12px">管理</button>
            </div>
          </div>
        </div>
      </div>
      <div class="table-wrap" id="table-wrap"></div>
      <div style="display:flex;gap:8px;flex-wrap:wrap;margin-bottom:1rem">
        <button class="primary" onclick="saveData()">儲存今日紀錄</button>
        <button onclick="clearTable()">清空表格</button>
        <button class="success" onclick="showReport()">產生 LINE 回報</button>
        <button onclick="showHistory()" style="font-size:12px">歷史紀錄</button>
        <button onclick="exportCSV()" style="font-size:12px">匯出 CSV</button>
      </div>
    </div>

    <div id="history-view" style="display:none">
      <div style="display:flex;gap:8px;margin-bottom:1rem;align-items:center">
        <button onclick="showMain()">← 返回</button>
        <span style="font-size:14px;font-weight:600" id="history-title"></span>
      </div>
      <div id="history-list" class="table-wrap" style="background:#fff"></div>
    </div>

    <div id="manage-view" style="display:none">
      <div style="display:flex;gap:8px;margin-bottom:1rem;align-items:center">
        <button onclick="showMain()">← 返回</button>
        <span style="font-size:14px;font-weight:600" id="manage-title"></span>
      </div>
      <div id="manage-list" class="table-wrap" style="background:#fff"></div>
      <div class="add-row" style="margin-top:10px">
        <input type="text" id="manage-input" placeholder="" style="width:200px" onkeydown="if(event.key==='Enter')manageAdd()">
        <button onclick="manageAdd()">+ 新增</button>
      </div>
    </div>

    <div id="report-modal" style="display:none">
      <div style="display:flex;gap:8px;margin-bottom:1rem;align-items:center">
        <button onclick="showMain()">← 返回</button>
        <span style="font-size:14px;font-weight:600" id="report-modal-title"></span>
      </div>
      <div id="report-content"></div>
    </div>
  </div>
</div>

<!-- Google Identity Services -->
<script src="https://accounts.google.com/gsi/client" async defer></script>
<script>
// ===================== AUTH =====================
const ALLOWED_DOMAINS = []; // 留空 = 所有 Gmail 都可登入；或填 ['yourcompany.com']
let currentUser = null;

function signInWithGoogle() {
  google.accounts.id.initialize({
    client_id: 'YOUR_GOOGLE_CLIENT_ID', // <-- Step 4 會換掉這行
    callback: handleCredentialResponse,
    auto_select: false,
  });
  google.accounts.id.prompt();
}

function handleCredentialResponse(response) {
  const payload = parseJwt(response.credential);
  if (ALLOWED_DOMAINS.length && !ALLOWED_DOMAINS.includes(payload.email.split('@')[1])) {
    document.getElementById('login-error').textContent = '此帳號無使用權限，請洽管理員。';
    document.getElementById('login-error').style.display = '';
    return;
  }
  currentUser = payload;
  localStorage.setItem('ezfun_user', JSON.stringify({name: payload.name, email: payload.email, picture: payload.picture}));
  showApp();
}

function parseJwt(token) {
  return JSON.parse(atob(token.split('.')[1].replace(/-/g,'+').replace(/_/g,'/')));
}

function signOut() {
  currentUser = null;
  localStorage.removeItem('ezfun_user');
  document.getElementById('app-view').style.display = 'none';
  document.getElementById('login-view').style.display = 'flex';
}

function showApp() {
  document.getElementById('login-view').style.display = 'none';
  document.getElementById('app-view').style.display = '';
  const u = currentUser;
  const bar = document.getElementById('user-bar');
  if (u.picture) {
    bar.innerHTML = `<img src="${u.picture}" class="user-avatar"> <span>${u.name}</span>`;
  } else {
    const initials = u.name.split(' ').map(n=>n[0]).join('').slice(0,2).toUpperCase();
    bar.innerHTML = `<div class="user-avatar-placeholder">${initials}</div> <span>${u.name}</span>`;
  }
  init();
}

// 自動恢復登入
window.addEventListener('load', () => {
  const saved = localStorage.getItem('ezfun_user');
  if (saved) {
    currentUser = JSON.parse(saved);
    showApp();
  }
});

// ===================== APP =====================
const KEY_W='ezfun_warehouses',KEY_C='ezfun_channels',KEY_V='ezfun_vendors',KEY_D='ezfun_data';
let warehouses,channels,vendors,tableData,currentWH,currentDate,manageType;

function ls_get(k){try{const r=localStorage.getItem(k);return r?JSON.parse(r):null}catch(e){return null}}
function ls_set(k,v){try{localStorage.setItem(k,JSON.stringify(v))}catch(e){}}

function init(){
  warehouses=ls_get(KEY_W)||['倉庫A','倉庫B','倉庫C','倉庫D','倉庫E','倉庫F','倉庫G'];
  channels=ls_get(KEY_C)||['7-11','全家','蝦皮','momo','PChome'];
  vendors=ls_get(KEY_V)||['廠商甲','廠商乙','廠商丙'];
  currentWH=warehouses[0];
  currentDate=new Date().toISOString().slice(0,10);
  document.getElementById('date-picker').value=currentDate;
  renderTabs();loadData();
}

function renderTabs(){
  const el=document.getElementById('warehouse-tabs');
  el.innerHTML=warehouses.map(w=>`<div class="tab${w===currentWH?' active':''}" onclick="switchWH('${w}')">${w}</div>`).join('')
    +`<button onclick="showManage('warehouse')" style="font-size:12px;height:32px;margin-left:4px">+ 管理倉庫</button>`;
}

function switchWH(w){currentWH=w;renderTabs();loadData()}
function getTodayKey(){return `${KEY_D}_${currentWH}_${currentDate}`}

function loadData(){
  currentDate=document.getElementById('date-picker').value;
  tableData=ls_get(getTodayKey())||{};
  renderChips();renderTable();
  document.getElementById('save-badge').textContent='';
}

function renderChips(){
  document.getElementById('vendor-chips').innerHTML=vendors.map(v=>`<div class="chip">${v}<span class="del" onclick="removeVendor('${v}')">×</span></div>`).join('');
  document.getElementById('channel-chips').innerHTML=channels.map(c=>`<div class="chip">${c}<span class="del" onclick="removeChannel('${c}')">×</span></div>`).join('');
}

function renderTable(){
  const wrap=document.getElementById('table-wrap');
  if(!channels.length||!vendors.length){wrap.innerHTML='<div class="empty">請先新增廠商和通路</div>';return}
  let html=`<table><thead><tr><th class="left">通路 \\ 廠商</th>`;
  vendors.forEach(v=>html+=`<th>${v}</th>`);
  html+=`<th>小計</th></tr></thead><tbody>`;
  let rowTotals=vendors.map(()=>0),grand=0;
  channels.forEach(c=>{
    html+=`<tr><td class="name">${c}</td>`;
    let colTotal=0;
    vendors.forEach((v,vi)=>{
      const val=parseInt((tableData[v]&&tableData[v][c])||0)||0;
      colTotal+=val;rowTotals[vi]+=val;
      html+=`<td><input class="cell" type="number" min="0" value="${val||''}" placeholder="0" oninput="updateCell('${esc(v)}','${esc(c)}',this.value)"></td>`;
    });
    grand+=colTotal;
    html+=`<td class="total">${colTotal||'—'}</td></tr>`;
  });
  html+=`<tr class="total-row"><td class="name">廠商合計</td>`;
  rowTotals.forEach(t=>html+=`<td class="total">${t||'—'}</td>`);
  html+=`<td class="total">${grand||'—'}</td></tr></tbody></table>`;
  wrap.innerHTML=html;
}

function esc(s){return s.replace(/\\/g,'\\\\').replace(/'/g,"\\'")}

function updateCell(v,c,val){
  if(!tableData[v])tableData[v]={};
  tableData[v][c]=parseInt(val)||0;
  renderTable();
  document.getElementById('save-badge').textContent='（未儲存）';
}

function addChannel(){const el=document.getElementById('new-channel'),v=el.value.trim();if(v&&!channels.includes(v)){channels.push(v);ls_set(KEY_C,channels);el.value='';renderChips();renderTable()}}
function addVendor(){const el=document.getElementById('new-vendor'),v=el.value.trim();if(v&&!vendors.includes(v)){vendors.push(v);ls_set(KEY_V,vendors);el.value='';renderChips();renderTable()}}
function removeChannel(c){if(confirm(`確定刪除通路「${c}」？`)){channels=channels.filter(x=>x!==c);ls_set(KEY_C,channels);renderChips();renderTable()}}
function removeVendor(v){if(confirm(`確定刪除廠商「${v}」？`)){vendors=vendors.filter(x=>x!==v);ls_set(KEY_V,vendors);renderChips();renderTable()}}

function saveData(){
  ls_set(getTodayKey(),tableData);
  const badge=document.getElementById('save-badge');
  badge.textContent='已儲存 ✓';
  setTimeout(()=>badge.textContent='',2500);
}
function clearTable(){if(confirm('確定清空今日表格？')){tableData={};renderTable();document.getElementById('save-badge').textContent='（未儲存）'}}
function goToday(){document.getElementById('date-picker').value=new Date().toISOString().slice(0,10);loadData()}

function showReport(){
  ['main-view','history-view','manage-view'].forEach(id=>document.getElementById(id).style.display='none');
  document.getElementById('report-modal').style.display='';
  document.getElementById('report-modal-title').textContent=`LINE 回報 － ${currentWH}　${currentDate}`;
  const dateStr=currentDate.replace(/-/g,'/');
  let html='';
  vendors.forEach((v,vi)=>{
    const row=tableData[v]||{};
    let total=0;const lines=[];
    channels.forEach(c=>{const val=parseInt(row[c])||0;if(val>0){lines.push(`　📦 ${c}：${val} 單`);total+=val;}});
    if(total===0)return;
    const msg=`📋 出貨通知｜${dateStr}\n━━━━━━━━━━━━━━\n🏭 廠商：${v}\n🏬 倉庫：${currentWH}\n\n${lines.join('\n')}\n\n✅ 今日處理單數：${total} 單\n━━━━━━━━━━━━━━\n感謝配合，出貨順利！🙏`;
    html+=`<div class="report-section"><div class="report-label">▶ 廠商：${v}</div><div class="report-box" id="rpt_v_${vi}">${escHtml(msg)}</div><button class="copy-btn" onclick="copyReport('rpt_v_${vi}')">複製此則</button></div>`;
  });
  let whTotal=0,whLines=[],vendorLines=[];
  channels.forEach(c=>{let ct=0;vendors.forEach(v=>{ct+=parseInt((tableData[v]&&tableData[v][c])||0)||0});if(ct>0){whLines.push(`　📦 ${c}：${ct} 單`);whTotal+=ct;}});
  vendors.forEach(v=>{let vt=0;channels.forEach(c=>{vt+=parseInt((tableData[v]&&tableData[v][c])||0)||0});if(vt>0)vendorLines.push(`　🏭 ${v}：${vt} 單`);});
  const whMsg=`📊 倉庫日報｜${dateStr}\n━━━━━━━━━━━━━━\n🏬 ${currentWH} 今日出庫總覽\n\n【各通路處理單數】\n${whLines.join('\n')||'　（無出貨）'}\n\n【各廠商處理單數】\n${vendorLines.join('\n')||'　（無出貨）'}\n\n✅ 全倉今日處理單數：${whTotal} 單\n━━━━━━━━━━━━━━`;
  html+=`<div class="report-section"><div class="report-label">▶ 倉庫總報（回報給公司）</div><div class="report-box" id="rpt_wh">${escHtml(whMsg)}</div><button class="copy-btn" onclick="copyReport('rpt_wh')">複製此則</button></div>`;
  if(!html)html='<div class="empty">今日尚無出貨資料，請先填寫表格並儲存。</div>';
  document.getElementById('report-content').innerHTML=html;
}

function escHtml(s){return s.replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;')}
function copyReport(id){
  const el=document.getElementById(id);
  const text=el.innerText||el.textContent;
  navigator.clipboard.writeText(text).then(()=>flashCopy(id)).catch(()=>{
    const r=document.createRange();r.selectNode(el);window.getSelection().removeAllRanges();window.getSelection().addRange(r);document.execCommand('copy');window.getSelection().removeAllRanges();flashCopy(id);
  });
}
function flashCopy(id){const btn=document.getElementById(id).nextElementSibling;btn.textContent='已複製 ✓';setTimeout(()=>btn.textContent='複製此則',2000);}

function showHistory(){
  ['main-view','report-modal','manage-view'].forEach(id=>document.getElementById(id).style.display='none');
  document.getElementById('history-view').style.display='';
  document.getElementById('history-title').textContent=`${currentWH} 歷史紀錄`;
  const prefix=`${KEY_D}_${currentWH}_`;
  const keys=[];
  for(let i=0;i<localStorage.length;i++){const k=localStorage.key(i);if(k&&k.startsWith(prefix))keys.push(k)}
  keys.sort().reverse();
  if(!keys.length){document.getElementById('history-list').innerHTML='<div class="empty">尚無歷史紀錄</div>';return}
  let html='';
  keys.forEach(k=>{
    const date=k.replace(prefix,'');const d=ls_get(k);let total=0;
    Object.values(d||{}).forEach(row=>Object.values(row||{}).forEach(v=>{total+=parseInt(v)||0}));
    html+=`<div class="history-row"><span style="min-width:100px;font-weight:600;font-size:13px">${date}</span><span style="flex:1;font-size:13px;color:#888">共處理 ${total} 單</span><button onclick="loadHistoryDate('${date}')" style="font-size:12px;height:30px">查看</button><button class="danger" onclick="deleteHistory('${k}','${date}')" style="font-size:12px;height:30px">刪除</button></div>`;
  });
  document.getElementById('history-list').innerHTML=html;
}
function loadHistoryDate(date){document.getElementById('date-picker').value=date;currentDate=date;loadData();showMain()}
function deleteHistory(k,date){if(confirm(`確定刪除 ${date} 的紀錄？`)){localStorage.removeItem(k);showHistory()}}

function showManage(type){
  manageType=type;
  ['main-view','history-view','report-modal'].forEach(id=>document.getElementById(id).style.display='none');
  document.getElementById('manage-view').style.display='';
  document.getElementById('manage-title').textContent={warehouse:'管理倉庫',channel:'管理通路物流',vendor:'管理廠商'}[type];
  document.getElementById('manage-input').placeholder=type==='warehouse'?'新增倉庫名稱':type==='channel'?'新增通路名稱':'新增廠商名稱';
  renderManageList();
}
function renderManageList(){
  const arr=manageType==='warehouse'?warehouses:manageType==='channel'?channels:vendors;
  if(!arr.length){document.getElementById('manage-list').innerHTML='<div class="empty">尚無項目</div>';return}
  document.getElementById('manage-list').innerHTML=arr.map((item,i)=>`<div class="history-row"><span style="flex:1;font-size:13px">${item}</span><button class="danger" onclick="manageDelete(${i})" style="font-size:12px;height:30px">刪除</button></div>`).join('');
}
function manageAdd(){
  const el=document.getElementById('manage-input'),v=el.value.trim();if(!v)return;
  if(manageType==='warehouse'){if(!warehouses.includes(v)){warehouses.push(v);ls_set(KEY_W,warehouses)}}
  else if(manageType==='channel'){if(!channels.includes(v)){channels.push(v);ls_set(KEY_C,channels)}}
  else{if(!vendors.includes(v)){vendors.push(v);ls_set(KEY_V,vendors)}}
  el.value='';renderManageList();
}
function manageDelete(i){
  const arr=manageType==='warehouse'?warehouses:manageType==='channel'?channels:vendors;
  if(!confirm(`確定刪除「${arr[i]}」？`))return;
  arr.splice(i,1);
  if(manageType==='warehouse'){ls_set(KEY_W,warehouses);if(!warehouses.includes(currentWH))currentWH=warehouses[0]||'';}
  else if(manageType==='channel')ls_set(KEY_C,channels);
  else ls_set(KEY_V,vendors);
  renderManageList();
}
function showMain(){
  document.getElementById('main-view').style.display='';
  ['history-view','manage-view','report-modal'].forEach(id=>document.getElementById(id).style.display='none');
  renderTabs();renderChips();renderTable();
}
function exportCSV(){
  if(!channels.length||!vendors.length)return;
  let csv='通路,'+vendors.join(',')+',小計\n';
  let colTotals=vendors.map(()=>0),grand=0;
  channels.forEach(c=>{
    let row=c,ct=0;
    vendors.forEach((v,i)=>{const val=parseInt((tableData[v]&&tableData[v][c])||0)||0;row+=','+val;ct+=val;colTotals[i]+=val});
    grand+=ct;csv+=row+','+ct+'\n';
  });
  csv+='廠商合計,'+colTotals.join(',')+','+grand+'\n';
  const blob=new Blob(['\uFEFF'+csv],{type:'text/csv;charset=utf-8'});
  const a=document.createElement('a');a.href=URL.createObjectURL(blob);
  a.download=`出貨記錄_${currentWH}_${currentDate}.csv`;a.click();
}
</script>
</body>
</html>
