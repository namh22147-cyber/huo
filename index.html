<!DOCTYPE html>
<html lang="vi">
<head>
<meta charset="UTF-8">
<title>Vòng Quay May Mắn</title>

<style>
body{
 margin:0;
 font-family:Arial;
 background:radial-gradient(circle,#111,#000);
 color:#fff;
 text-align:center;
}

/* BOX */
.box{
 background:#111;
 padding:15px;
 margin:15px auto;
 width:92%;
 max-width:540px;
 border-radius:14px;
 box-shadow:0 0 20px gold;
}

/* WHEEL */
#wheel-wrap{
 position:relative;
 width:320px;
 margin:20px auto;
}
#wheel{
 width:320px;
 height:320px;
 border-radius:50%;
 border:10px solid gold;
 transition:transform 4s cubic-bezier(.17,.67,.12,.99);
 background:conic-gradient(
  #4caf50 0deg 180deg,
  #2196f3 180deg 270deg,
  #ff9800 270deg 324deg,
  #f44336 324deg 342deg,
  #9c27b0 342deg 352.8deg,
  #ff1744 352.8deg 356.4deg,
  #444 356.4deg 360deg
 );
}
#pointer{
 position:absolute;
 top:-15px;
 left:50%;
 transform:translateX(-50%);
 width:0;height:0;
 border-left:18px solid transparent;
 border-right:18px solid transparent;
 border-bottom:30px solid gold;
}

/* INPUT & BUTTON */
input{
 padding:10px;
 width:80%;
 font-size:16px;
 margin:5px 0;
}
button{
 padding:12px 26px;
 font-size:16px;
 border:none;
 border-radius:8px;
 background:gold;
 color:#000;
 font-weight:bold;
 margin:5px;
}

/* MONEY */
#moneyBox{
 font-size:22px;
 font-weight:bold;
 color:gold;
 margin:10px 0;
}

/* BELL */
#bell{
 position:fixed;
 top:12px;
 right:14px;
 font-size:28px;
 cursor:pointer;
 z-index:999;
}
#notiBox{
 position:fixed;
 top:60px;
 right:14px;
 width:260px;
 max-height:300px;
 overflow:auto;
 background:#111;
 border:2px solid gold;
 border-radius:12px;
 padding:10px;
 display:none;
 z-index:999;
}
.noti{
 font-size:14px;
 padding:6px;
 border-bottom:1px solid #333;
}

/* FIREWORK */
#fireworks{
 position:fixed;
 top:0;left:0;
 width:100%;
 height:100%;
 pointer-events:none;
 z-index:998;
 display:none;
}
</style>
</head>

<body>

<!-- 🔔 CHUÔNG -->
<div id="bell" onclick="toggleNoti()">🔔</div>
<div id="notiBox">
<h4 style="color:gold">📢 Trúng thưởng</h4>
<div id="notiList"></div>
</div>

<canvas id="fireworks"></canvas>

<!-- LOGIN -->
<div class="box">
<h2>🎰 VÒNG QUAY MAY MẮN</h2>
<input id="code" placeholder="Nhập mã đăng nhập">
<br>
<button onclick="login()">Vào chơi</button>
</div>

<!-- GAME -->
<div class="box" id="game" style="display:none">
<div id="wheel-wrap">
<div id="pointer"></div>
<div id="wheel"></div>
</div>

<h3>Lượt còn lại: <span id="turns">0</span></h3>

<h3>💰 Tổng tiền đã nhận</h3>
<div id="moneyBox">0₫</div>

<button onclick="spin()">QUAY</button>
<p id="result"></p>
</div>

<!-- MISSIONS -->
<div class="box" id="missionBox" style="display:none">
<h3>🎯 NHIỆM VỤ KIẾM LƯỢT</h3>

<div id="q1">
<p>1️⃣ Ad bao nhiêu tuổi?</p>
<input id="a1">
<button onclick="checkMission(1)">Trả lời</button>
</div>

<div id="q2" style="display:none">
<p>2️⃣ Sinh nhật của ad?</p>
<input id="a2">
<button onclick="checkMission(2)">Trả lời</button>
</div>

<div id="q3" style="display:none">
<p>3️⃣ Bố mẹ ad tên gì?</p>
<input id="a3">
<button onclick="checkMission(3)">Trả lời</button>
</div>

<p id="missionMsg"></p>
</div>

<!-- RANK -->
<div class="box">
<h3>🏆 BẢNG XẾP HẠNG</h3>
<table width="100%">
<thead>
<tr style="color:gold">
<th>#</th><th>Mã</th><th>Tổng tiền</th>
</tr>
</thead>
<tbody id="rankTable"></tbody>
</table>
</div>

<script>
/* DATA */
const players={
 "16378":6,"17385":3,"18374":3,
 "18246":1,"19264":1,
 "12345":7,"12012008":3,"99999":999
};

const rewards=[
 {name:"10,000₫",rate:50,value:10000,angle:180},
 {name:"20,000₫",rate:25,value:20000,angle:90},
 {name:"50,000₫",rate:15,value:50000,angle:54},
 {name:"100,000₫",rate:5,value:100000,angle:18},
 {name:"200,000₫",rate:3,value:200000,angle:10.8},
 {name:"500,000₫",rate:1,value:500000,angle:3.6},
 {name:"Không trúng",rate:1,value:0,angle:3.6}
];

let data=JSON.parse(localStorage.getItem("spinData")||"{}");
let notifications=JSON.parse(localStorage.getItem("notifications")||"[]");
let current=null,angle=0;

/* LOGIN */
function login(){
 let c=code.value;
 if(!(c in players)){alert("Mã không hợp lệ");return;}
 if(!data[c]){
  data[c]={turns:players[c],total:0,log:[],missions:{1:false,2:false,3:false},bonus:false};
 }
 current=c;
 game.style.display="block";
 missionBox.style.display="block";
 update();
 showMissions();
 renderNoti();
}

/* SPIN */
function pick(){
 let r=Math.random()*100,sum=0;
 for(let i=0;i<rewards.length;i++){
  sum+=rewards[i].rate;
  if(r<=sum) return i;
 }
 return rewards.length-1;
}

function spin(){
 if(data[current].turns<=0){alert("Hết lượt");return;}
 data[current].turns--;
 let i=pick();
 let start=0;
 for(let j=0;j<i;j++) start+=rewards[j].angle;
 angle+=360*5+(360-(start+rewards[i].angle/2));
 wheel.style.transform=`rotate(${angle}deg)`;

 setTimeout(()=>{
  let w=rewards[i];
  data[current].log.push(w.name);
  data[current].total+=w.value;
  addNotification(current,w.name);
  if(w.value===500000) launchFireworks(3);
  result.innerText="🎯 Trúng: "+w.name;
  save();update();
 },4000);
}

/* UPDATE */
function update(){
 turns.innerText=data[current].turns;
 moneyBox.innerText=data[current].total.toLocaleString("vi-VN")+"₫";
 renderRanking();
}

/* MISSIONS */
const missionAnswers={
 1:["20"],
 2:["13-11-2005","13-11"],
 3:["han mau","hân mầu"]
};
function normalize(t){
 return t.toLowerCase().trim().replace(/[^\w\s\-]/g,"");
}
function showMissions(){
 if(data[current].missions[1]) q2.style.display="block";
 if(data[current].missions[2]) q3.style.display="block";
}
function checkMission(n){
 let ans=document.getElementById("a"+n).value;
 let ok=missionAnswers[n].some(x=>normalize(x)==normalize(ans));
 if(ok && !data[current].missions[n]){
  data[current].missions[n]=true;
  data[current].turns++;
 }
 if(n===1) q2.style.display="block";
 if(n===2) q3.style.display="block";
 let m=data[current].missions;
 if(m[1]&&m[2]&&m[3]&&!data[current].bonus){
  data[current].turns+=2;
  data[current].bonus=true;
 }
 save();update();
}

/* RANK */
function renderRanking(){
 let arr=Object.keys(data)
 .map(c=>({c,total:data[c].total}))
 .sort((a,b)=>b.total-a.total);
 rankTable.innerHTML=arr.map((p,i)=>{
  let show=current==="99999"?p.c:"***"+p.c.slice(-2);
  return `<tr><td>${i+1}</td><td>${show}</td><td style="color:gold">${p.total.toLocaleString("vi-VN")}₫</td></tr>`;
 }).join("");
}

/* NOTI */
function maskCode(c){return c==="99999"?c:"***"+c.slice(-2);}
function addNotification(c,p){
 notifications.unshift(`${maskCode(c)} trúng ${p}`);
 notifications.splice(20);
 localStorage.setItem("notifications",JSON.stringify(notifications));
 renderNoti();
}
function renderNoti(){
 notiList.innerHTML=notifications.map(n=>`<div class="noti">${n}</div>`).join("");
}
function toggleNoti(){
 notiBox.style.display=notiBox.style.display==="none"?"block":"none";
}

/* FIREWORK */
const fw=document.getElementById("fireworks"),ctx=fw.getContext("2d");
fw.width=innerWidth;fw.height=innerHeight;
let particles=[];
function launchFireworks(t){
 fw.style.display="block";
 let c=0;
 let i=setInterval(()=>{
  explode();c++;
  if(c>=t){clearInterval(i);
   setTimeout(()=>{ctx.clearRect(0,0,fw.width,fw.height);fw.style.display="none";},1000);}
 },700);
}
function explode(){
 let x=Math.random()*fw.width,y=Math.random()*fw.height/2;
 for(let i=0;i<80;i++)
 particles.push({x,y,vx:(Math.random()-.5)*6,vy:(Math.random()-.5)*6,life:60});
}
(function anim(){
 ctx.clearRect(0,0,fw.width,fw.height);
 particles.forEach(p=>{
  p.x+=p.vx;p.y+=p.vy;p.life--;
  ctx.fillStyle=`hsl(${Math.random()*360},100%,60%)`;
  ctx.fillRect(p.x,p.y,3,3);
 });
 particles=particles.filter(p=>p.life>0);
 requestAnimationFrame(anim);
})();

function save(){
 localStorage.setItem("spinData",JSON.stringify(data));
}
</script>

</body>
</html>
