
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>CN OPK Booking Portal</title>

<link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800;900&display=swap" rel="stylesheet">

<style>
*{
  margin:0;
  padding:0;
  box-sizing:border-box;
  font-family:'Inter',sans-serif;
}

body{
  background:#030712;
  color:white;
  overflow-x:hidden;
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
  max-width:1200px;
  margin:auto;
  padding:25px;
}

.grid{
  display:grid;
  grid-template-columns:2fr 1fr;
  gap:25px;
}

@media(max-width:900px){
  .grid{grid-template-columns:1fr;}
  .slots{grid-template-columns:repeat(2,1fr);}
  .input-grid{grid-template-columns:1fr;}
}

.card{
  background:rgba(255,255,255,0.06);
  border:1px solid rgba(255,255,255,0.08);
  border-radius:30px;
  padding:25px;
  backdrop-filter:blur(16px);
}

.input-grid{
  display:grid;
  grid-template-columns:1fr 1fr;
  gap:15px;
}

input,select{
  width:100%;
  padding:16px;
  border-radius:18px;
  background:rgba(0,0,0,0.35);
  border:1px solid rgba(255,255,255,0.08);
  color:white;
}

.full{grid-column:1/-1;}

.slots{
  display:grid;
  grid-template-columns:repeat(5,1fr);
  gap:12px;
  margin-top:20px;
}

.slot-btn{
  padding:15px;
  border-radius:16px;
  background:rgba(255,255,255,0.05);
  border:1px solid rgba(255,255,255,0.08);
  color:white;
  cursor:pointer;
  font-weight:700;
  transition:0.3s;
}

.slot-btn.disabled{
  background:rgba(239,68,68,0.25);
  border:1px solid #ef4444;
  cursor:not-allowed;
  opacity:0.5;
}

.selected{
  border:2px solid #22d3ee;
  background:rgba(34,211,238,0.2);
}

.book-btn,.login-btn,.logout-btn{
  width:100%;
  padding:18px;
  border:none;
  border-radius:20px;
  font-weight:800;
  cursor:pointer;
  background:linear-gradient(90deg,#8b5cf6,#22d3ee,#ec4899);
}

.records{
  max-height:300px;
  overflow:auto;
}

.receipt-popup{
  position:fixed;
  inset:0;
  background:rgba(0,0,0,0.75);
  display:none;
  justify-content:center;
  align-items:center;
  z-index:9999;
}

.receipt-card{
  width:90%;
  max-width:420px;
  background:#0f172a;
  border-radius:25px;
  padding:25px;
}

.receipt-title{
  font-size:26px;
  font-weight:900;
  text-align:center;
  color:#22d3ee;
  margin-bottom:15px;
}

.receipt-info{
  background:rgba(255,255,255,0.05);
  padding:12px;
  border-radius:14px;
  margin-bottom:10px;
}

.receipt-label{
  font-size:12px;
  color:#9ca3af;
}

.receipt-value{
  font-size:16px;
  font-weight:700;
}

.receipt-close{
  width:100%;
  margin-top:10px;
  padding:14px;
  border:none;
  border-radius:14px;
  font-weight:800;
  background:linear-gradient(90deg,#8b5cf6,#22d3ee,#ec4899);
  cursor:pointer;
}

</style>
</head>

<body>

<div class="container">

<div class="grid">

<!-- FORM -->
<div class="card">

<h2>Reserve Slot</h2>

<div class="input-grid">

<input id="name" placeholder="Bigo Name">
<input id="bigoId" placeholder="Bigo ID">
<input id="agency" placeholder="Agency">
<input id="level" placeholder="Level">

<select id="opkType" class="full">
<option value="">OPK TYPE</option>
<option>PK TASK BLITZ</option>
<option>BLAZE PK</option>
<option>ALL STAR PK</option>
</select>

<input id="gmail" class="full" placeholder="Gmail">
<input id="date" type="date" class="full">

</div>

<div class="slots" id="slots"></div>

<button class="book-btn" id="bookBtn">Reserve Now</button>

</div>

<!-- ADMIN -->
<div class="card">

<input id="searchBooking" placeholder="Search booking..." style="width:100%;margin-bottom:10px;padding:12px;border-radius:12px;background:#111;color:white;">

<button class="login-btn" id="loginBtn">Login</button>
<button class="logout-btn" id="logoutBtn">Logout</button>

<div class="records" id="records"></div>

</div>

</div>
</div>

<!-- RECEIPT -->
<div class="receipt-popup" id="receiptPopup">
  <div class="receipt-card">

    <div class="receipt-title">BOOKING RECEIPT</div>

    <div class="receipt-info"><div class="receipt-label">Name</div><div class="receipt-value" id="rName"></div></div>
    <div class="receipt-info"><div class="receipt-label">Bigo ID</div><div class="receipt-value" id="rBigo"></div></div>
    <div class="receipt-info"><div class="receipt-label">OPK Type</div><div class="receipt-value" id="rType"></div></div>
    <div class="receipt-info"><div class="receipt-label">Agency</div><div class="receipt-value" id="rAgency"></div></div>
    <div class="receipt-info"><div class="receipt-label">Level</div><div class="receipt-value" id="rLevel"></div></div>
    <div class="receipt-info"><div class="receipt-label">Date</div><div class="receipt-value" id="rDate"></div></div>
    <div class="receipt-info"><div class="receipt-label">Time</div><div class="receipt-value" id="rSlot"></div></div>
    <div class="receipt-info"><div class="receipt-label">Booked At</div><div class="receipt-value" id="rTime"></div></div>

    <button class="receipt-close" onclick="closeReceipt()">Close</button>

  </div>
</div>

<script type="module">

import { initializeApp } from "https://www.gstatic.com/firebasejs/10.7.1/firebase-app.js";
import { getFirestore, collection, addDoc, getDocs } from "https://www.gstatic.com/firebasejs/10.7.1/firebase-firestore.js";

const firebaseConfig = {
  apiKey: "AIzaSyCYd1Lxf9BVL7AxhC8EyNZNzrbHamaxp8I",
  authDomain: "fragile2opksystem.firebaseapp.com",
  projectId: "fragile2opksystem",
  storageBucket: "fragile2opksystem.firebasestorage.app",
  messagingSenderId: "497109961796",
  appId: "1:497109961796:web:56279c0e0ae57efdc50011",
};

const app = initializeApp(firebaseConfig);
const db = getFirestore(app);

let bookings = [];
let selectedSlot = "";

const slots = [
'8:00 PM','8:15 PM','8:30 PM','8:45 PM',
'9:00 PM','9:15 PM','9:30 PM','9:45 PM',
'10:00 PM','10:15 PM'
];

function renderSlots(date){

const box = document.getElementById("slots");
box.innerHTML = "";

slots.forEach(s=>{

const booked = bookings.find(b=>b.date===date && b.slot===s);

const btn = document.createElement("button");
btn.className = "slot-btn";

if(booked){
btn.innerText = s + "\nBOOKED";
btn.classList.add("disabled");
btn.disabled = true;
}else{
btn.innerText = s;
btn.onclick = ()=>{
document.querySelectorAll(".slot-btn").forEach(b=>b.classList.remove("selected"));
btn.classList.add("selected");
selectedSlot = s;
};
}

box.appendChild(btn);

});

}

async function load(){

const snap = await getDocs(collection(db,"bookings"));
bookings = [];

let html = "";

snap.forEach(d=>{
const data = d.data();
bookings.push(data);

html += `<div>
<b>${data.name}</b><br>
${data.date} - ${data.slot}<br>
${data.opkType}
</div><hr>`;
});

document.getElementById("records").innerHTML = html;

renderSlots(document.getElementById("date").value);

}

document.getElementById("date").addEventListener("change",(e)=>{
renderSlots(e.target.value);
});

async function book(){

const data = {
name:document.getElementById("name").value,
bigoId:document.getElementById("bigoId").value,
agency:document.getElementById("agency").value,
level:document.getElementById("level").value,
opkType:document.getElementById("opkType").value,
gmail:document.getElementById("gmail").value,
date:document.getElementById("date").value,
slot:selectedSlot,
time:new Date().toLocaleString()
};

await addDoc(collection(db,"bookings"),data);

showReceipt(data);
load();

}

function showReceipt(d){

document.getElementById("rName").innerText=d.name;
document.getElementById("rBigo").innerText=d.bigoId;
document.getElementById("rType").innerText=d.opkType;
document.getElementById("rAgency").innerText=d.agency;
document.getElementById("rLevel").innerText=d.level;
document.getElementById("rDate").innerText=d.date;
document.getElementById("rSlot").innerText=d.slot;
document.getElementById("rTime").innerText=d.time;

document.getElementById("receiptPopup").style.display="flex";

setTimeout(()=>closeReceipt(),5000);

}

window.closeReceipt=()=>{
document.getElementById("receiptPopup").style.display="none";
}

document.getElementById("bookBtn").onclick=book;

load();

</script>

</body>
</html>
