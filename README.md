<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>

<title>ANGELSTAR FAMILY OPK PORTAL</title>

<link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800;900&display=swap" rel="stylesheet">

<style>

*{
  margin:0;
  padding:0;
  box-sizing:border-box;
  font-family:'Inter',sans-serif;
}

html{scroll-behavior:smooth;}

body{
  background:#030712;
  color:white;
  overflow-x:hidden;
  min-height:100vh;
}

body::before{
  content:'';
  position:fixed;
  inset:0;
  background:
  radial-gradient(circle at top right,#7c3aed55,transparent 30%),
  radial-gradient(circle at bottom left,#06b6d455,transparent 30%);
  z-index:-1;
}

.container{
  width:100%;
  max-width:1450px;
  margin:auto;
  padding:20px;
}

.header{
  text-align:center;
  margin-bottom:35px;
}

.badge{
  display:inline-flex;
  align-items:center;
  gap:10px;
  background:rgba(255,255,255,0.08);
  border:1px solid rgba(255,255,255,0.08);
  padding:12px 22px;
  border-radius:999px;
  backdrop-filter:blur(14px);
  margin-bottom:22px;
}

.dot{
  width:10px;
  height:10px;
  border-radius:50%;
  background:#22d3ee;
  animation:pulse 1.5s infinite;
}

@keyframes pulse{
  0%{opacity:0.4;transform:scale(1)}
  50%{opacity:1;transform:scale(1.2)}
  100%{opacity:0.4;transform:scale(1)}
}

.title{
  font-size:72px;
  font-weight:900;
  background:linear-gradient(90deg,#8b5cf6,#22d3ee,#ec4899);
  -webkit-background-clip:text;
  color:transparent;
}

.subtitle{
  max-width:900px;
  margin:auto;
  margin-top:18px;
  color:#9ca3af;
}

.grid{
  display:grid;
  grid-template-columns:2fr 1.1fr;
  gap:24px;
}

.card{
  background:rgba(255,255,255,0.06);
  border:1px solid rgba(255,255,255,0.08);
  border-radius:30px;
  padding:26px;
  backdrop-filter:blur(18px);
}

.section-title{
  font-size:30px;
  font-weight:900;
}

.input-grid{
  display:grid;
  grid-template-columns:1fr 1fr;
  gap:16px;
}

input,select{
  width:100%;
  padding:17px;
  border-radius:18px;
  border:1px solid rgba(255,255,255,0.08);
  background:rgba(0,0,0,0.35);
  color:white;
}

.slot-btn{
  padding:15px;
  border-radius:14px;
  border:1px solid rgba(255,255,255,0.1);
  background:rgba(255,255,255,0.05);
  color:white;
  cursor:pointer;
}

.book-btn,.login-btn,.logout-btn{
  width:100%;
  margin-top:15px;
  padding:16px;
  border:none;
  border-radius:20px;
  font-weight:900;
  background:linear-gradient(90deg,#8b5cf6,#22d3ee,#ec4899);
  cursor:pointer;
}

.sidebar{display:flex;flex-direction:column;gap:20px;}

.record{
  background:rgba(255,255,255,0.05);
  padding:16px;
  border-radius:18px;
  margin-bottom:12px;
}

.announcement-card{
  background:rgba(255,255,255,0.05);
  padding:18px;
  border-radius:18px;
  margin-bottom:12px;
  border-left:4px solid #22d3ee;
}

.live{
  display:inline-block;
  background:#22c55e;
  padding:4px 10px;
  border-radius:999px;
  font-size:12px;
  font-weight:900;
  margin-top:8px;
}

</style>
</head>

<body>

<div class="container">

<div class="header">
<div class="badge"><div class="dot"></div> ANGELSTAR OPK SYSTEM</div>
<h1 class="title">BOOKING PORTAL</h1>
<p class="subtitle">OPK scheduling + live announcements system</p>
</div>

<!-- 🔥 ANNOUNCEMENTS -->
<div class="card" style="margin-bottom:20px;">
<h2 class="section-title">🔥 TODAY'S OPK MATCHES</h2>
<div id="announcementBoard"></div>
</div>

<div class="grid">

<!-- LEFT -->
<div class="card">

<h2 class="section-title">Reserve Slot</h2>

<div class="input-grid">
<input id="name" placeholder="Bigo Name">
<input id="bigoId" placeholder="Bigo ID">
<input id="agency" placeholder="Agency">
<input id="level" placeholder="Level">
<input id="PrevQuota" placeholder="Last Month Quota" class="full">
<select id="eventType" class="full">
<option>Select Event</option>
<option>OPK TASK BLITZ</option>
<option>BLAZE PK</option>
<option>ALL STAR PK</option>
</select>
<input type="date" id="date" class="full">
</div>

<h3>Select Time</h3>
<div id="slots"></div>

<button class="book-btn" id="bookBtn">Reserve Now</button>

</div>

<!-- RIGHT -->
<div class="sidebar">

<div class="card">
<h2 class="section-title">Admin Login</h2>
<input id="adminEmail" placeholder="Email">
<input id="adminPassword" type="password" placeholder="Password">
<button class="login-btn" id="loginBtn">Login</button>
<button class="logout-btn" id="logoutBtn">Logout</button>
</div>

<!-- ANNOUNCEMENT ADMIN -->
<div class="card" id="adminDashboard" style="display:none;">

<h2 class="section-title">📢 OPK ANNOUNCEMENT</h2>

<input id="hostNameAnnouncement" placeholder="Host Name">
<input id="hostIdAnnouncement" placeholder="Host BIGO ID" style="margin-top:10px">
<input id="opponentNameAnnouncement" placeholder="Opponent Name" style="margin-top:10px">
<input id="opponentIdAnnouncement" placeholder="Opponent BIGO ID" style="margin-top:10px">
<input id="announcementDate" type="date" style="margin-top:10px">
<input id="announcementTime" type="time" style="margin-top:10px">

<button class="login-btn" id="publishAnnouncementBtn">
Publish Match
</button>

</div>

</div>
</div>

</div>

<script type="module">

import { initializeApp } from "https://www.gstatic.com/firebasejs/10.7.1/firebase-app.js";
import {
getFirestore,
collection,
addDoc,
getDocs,
deleteDoc,
doc,
serverTimestamp
} from "https://www.gstatic.com/firebasejs/10.7.1/firebase-firestore.js";

import {
getAuth,
signInWithEmailAndPassword,
signOut,
onAuthStateChanged
} from "https://www.gstatic.com/firebasejs/10.7.1/firebase-auth.js";

const app = initializeApp({
apiKey: "AIzaSyBJBT_BAeos1hb_fKJzSontJVgBub9Wjhc",
  authDomain: "opk-system-cn.firebaseapp.com",
  projectId: "opk-system-cn",
  storageBucket: "opk-system-cn.firebasestorage.app",
  messagingSenderId: "1098097772017",
  appId: "1:1098097772017:web:4e015378c786d6b404f050",
});

const db = getFirestore(app);
const auth = getAuth(app);

let bookings = [];
let selectedSlot="";

const slots=[
'8:00 PM','8:15 PM','8:30 PM','8:45 PM',
'9:00 PM','9:15 PM','9:30 PM','9:45 PM',
'10:00 PM','10:15 PM'
];

function renderSlots(){
const container=document.getElementById("slots");
container.innerHTML="";
slots.forEach(s=>{
const b=document.createElement("button");
b.innerText=s;
b.className="slot-btn";
b.onclick=()=>selectedSlot=s;
container.appendChild(b);
});
}

async function publishAnnouncement(){

await addDoc(collection(db,"announcements"),{
hostName:hostNameAnnouncement.value,
hostId:hostIdAnnouncement.value,
opponentName:opponentNameAnnouncement.value,
opponentId:opponentIdAnnouncement.value,
date:announcementDate.value,
time:announcementTime.value,
createdAt:serverTimestamp()
});

loadAnnouncements();
}

async function loadAnnouncements(){

const board=document.getElementById("announcementBoard");
board.innerHTML="";

const snap=await getDocs(collection(db,"announcements"));

const now=new Date();

for(const d of snap.docs){

const data=d.data();
const match=new Date(`${data.date}T${data.time}`);

if(now-match>3600000){
await deleteDoc(doc(db,"announcements",d.id));
continue;
}

let badge="";
if(match<=now && now-match<3600000){
badge=`<div class="live">🔴 LIVE NOW</div>`;
}

board.innerHTML+=`
<div class="announcement-card">
<h3>${data.hostName} VS ${data.opponentName}</h3>
${badge}
<p>Host ID: ${data.hostId}</p>
<p>Opponent ID: ${data.opponentId}</p>
<p>${data.date} ${data.time}</p>
</div>`;
}
}

document.getElementById("publishAnnouncementBtn")
.addEventListener("click",publishAnnouncement);

setInterval(loadAnnouncements,60000);
loadAnnouncements();

</script>

</body>
</html>
