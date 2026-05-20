<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>

<title>PH-FRAGILE2 OPK PORTAL</title>

<link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800;900&display=swap" rel="stylesheet">

<style>

*{
  margin:0;
  padding:0;
  box-sizing:border-box;
  font-family:'Inter',sans-serif;
}

html{
  scroll-behavior:smooth;
}

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
  line-height:1;
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
  font-size:17px;
  line-height:1.7;
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
  box-shadow:0 0 30px rgba(0,0,0,0.25);
}

.section-title{
  font-size:30px;
  font-weight:900;
  margin-bottom:12px;
}

.section-sub{
  color:#9ca3af;
  margin-bottom:25px;
}

.input-grid{
  display:grid;
  grid-template-columns:1fr 1fr;
  gap:16px;
}

input,
select{
  width:100%;
  padding:17px;
  border-radius:18px;
  border:1px solid rgba(255,255,255,0.08);
  background:rgba(0,0,0,0.35);
  color:white;
  outline:none;
  transition:0.25s;
  font-size:15px;
}

input:focus,
select:focus{
  border-color:#22d3ee;
  box-shadow:0 0 18px rgba(34,211,238,0.25);
}

option{
  background:#111827;
}

.full{
  grid-column:1/-1;
}

.slot-title{
  margin-top:28px;
  margin-bottom:18px;
  font-size:22px;
  font-weight:800;
}

.slots{
  display:grid;
  grid-template-columns:repeat(auto-fit,minmax(120px,1fr));
  gap:12px;
}

.slot-btn{
  border:none;
  border-radius:18px;
  padding:17px 10px;
  background:rgba(255,255,255,0.05);
  border:1px solid rgba(255,255,255,0.08);
  color:white;
  font-weight:800;
  cursor:pointer;
  transition:0.25s;
}

.slot-btn:hover{
  transform:translateY(-3px);
  border-color:#22d3ee;
  background:rgba(34,211,238,0.15);
}

.selected{
  border:2px solid #22d3ee;
  background:rgba(34,211,238,0.25);
}

.booked{
  background:#ef444450;
  border:1px solid #ef4444;
  opacity:0.55;
  cursor:not-allowed;
}

.book-btn,
.login-btn,
.logout-btn{
  width:100%;
  margin-top:22px;
  border:none;
  border-radius:22px;
  padding:18px;
  font-size:16px;
  font-weight:900;
  cursor:pointer;
  color:black;
  background:linear-gradient(90deg,#8b5cf6,#22d3ee,#ec4899);
  transition:0.25s;
}

.book-btn:hover,
.login-btn:hover,
.logout-btn:hover{
  transform:scale(1.01);
}

.book-btn:disabled{
  opacity:0.6;
  cursor:not-allowed;
}

.sidebar{
  display:flex;
  flex-direction:column;
  gap:24px;
}

.stat-box{
  background:rgba(0,0,0,0.35);
  border-radius:20px;
  padding:20px;
  margin-top:16px;
  display:flex;
  justify-content:space-between;
  align-items:center;
}

.stat-number{
  font-size:35px;
  font-weight:900;
}

.records{
  margin-top:18px;
  max-height:420px;
  overflow:auto;
  display:flex;
  flex-direction:column;
  gap:12px;
}

.records::-webkit-scrollbar{
  width:5px;
}

.records::-webkit-scrollbar-thumb{
  background:#22d3ee;
  border-radius:20px;
}

.record{
  background:rgba(255,255,255,0.05);
  border-radius:18px;
  padding:16px;
}

.footer{
  text-align:center;
  margin-top:35px;
  color:#6b7280;
}

.receipt-modal{
  position:fixed;
  inset:0;
  background:rgba(0,0,0,0.75);
  display:none;
  justify-content:center;
  align-items:center;
  z-index:9999;
  padding:20px;
}

.receipt-box{
  width:100%;
  max-width:520px;
  background:#0f172a;
  border:2px solid #22d3ee;
  border-radius:30px;
  padding:30px;
  animation:pop .25s ease;
}

@keyframes pop{
  from{
    opacity:0;
    transform:scale(0.9);
  }
  to{
    opacity:1;
    transform:scale(1);
  }
}

.receipt-title{
  text-align:center;
  font-size:34px;
  font-weight:900;
  margin-bottom:24px;
  background:linear-gradient(90deg,#8b5cf6,#22d3ee,#ec4899);
  -webkit-background-clip:text;
  color:transparent;
}

.receipt-info{
  background:rgba(255,255,255,0.05);
  border-radius:18px;
  padding:16px;
  margin-bottom:12px;
}

.receipt-buttons{
  display:flex;
  gap:14px;
  margin-top:25px;
}

.receipt-btn{
  flex:1;
  border:none;
  padding:16px;
  border-radius:18px;
  font-weight:900;
  cursor:pointer;
}

.print-btn{
  background:linear-gradient(90deg,#8b5cf6,#22d3ee);
  color:black;
}

.close-btn{
  background:#ef4444;
  color:white;
}

@media(max-width:1100px){

  .grid{
    grid-template-columns:1fr;
  }

}

@media(max-width:700px){

  .container{
    padding:15px;
  }

  .title{
    font-size:45px;
  }

  .subtitle{
    font-size:15px;
  }

  .input-grid{
    grid-template-columns:1fr;
  }

  .slots{
    grid-template-columns:repeat(2,1fr);
  }

  .card{
    padding:20px;
  }

  .receipt-buttons{
    flex-direction:column;
  }

}

</style>
</head>

<body>

<div class="container">

<div class="header">

<div class="badge">
<div class="dot"></div>
<span>CN OPK BOOKING SYSTEM</span>
</div>

<h1 class="title">
PH-FRAGILE 2 AGENCY
<br>
BOOKING PORTAL
</h1>

<p class="subtitle">
Premium futuristic OPK reservation dashboard designed for seamless booking, real-time slot management, secure admin controls, fast reservation system, and advanced host scheduling experience.
</p>

</div>

<div class="grid">

<div class="card">

<h2 class="section-title">
Reserve Your Slot 🚀
</h2>

<p class="section-sub">
Choose your preferred OPK event and schedule.
</p>

<div class="input-grid">

<input id="name" placeholder="Bigo Name">

<input id="bigoId" placeholder="Bigo ID">

<input id="agency" placeholder="Agency">

<input id="level" placeholder="Level">

<input id="Last Month Quota" class="full" placeholder="Last MOnth Quota">

<select id="eventType" class="full">
<option value="">Select Event</option>
<option>OPK TASK BLITZ</option>
<option>BLAZE PK</option>
<option>ALL STAR PK</option>
</select>

<input id="date" type="date" class="full">

</div>

<h3 class="slot-title">
Select Time
</h3>

<div class="slots" id="slots"></div>

<button class="book-btn" id="bookBtn">
Reserve Now
</button>

</div>

<div class="sidebar">

<div class="card">

<h2 class="section-title">
Admin Login
</h2>

<input id="adminEmail" placeholder="Admin Email">

<input id="adminPassword" type="password" placeholder="Password" style="margin-top:15px">

<button class="login-btn" id="loginBtn">
Login
</button>

<button class="logout-btn" id="logoutBtn">
Logout
</button>

</div>

<div class="card">

<h2 class="section-title">
Live Stats
</h2>

<div class="stat-box">
<span>Total Bookings</span>
<span class="stat-number" id="totalBookings">0</span>
</div>

<div class="stat-box">
<span>Today</span>
<span class="stat-number" id="todayBookings">0</span>
</div>

</div>

<div class="card" id="adminDashboard" style="display:none;">

<h2 class="section-title">
Admin Dashboard
</h2>

<input id="bigoSearchInput" placeholder="Search Bigo ID">

<button class="login-btn" id="downloadExcelBtn">
Download Excel Report
</button>

<button class="logout-btn" id="clearBookingsBtn">
Delete All Bookings
</button>

<div class="records" id="records"></div>

<h3 style="margin-top:20px;font-size:22px;">
Deleted Bookings
</h3>

<div class="records" id="deletedRecords"></div>

</div>

</div>

</div>

<div class="footer">
PH-FRAGILE2 OPK DASHBOARD © 2026
</div>

</div>

<!-- RECEIPT -->

<div class="receipt-modal" id="receiptModal">

<div class="receipt-box">

<div class="receipt-title">
BOOKING RECEIPT
</div>

<div class="receipt-info">
<strong>Name:</strong>
<div id="receiptName"></div>
</div>

<div class="receipt-info">
<strong>Bigo ID:</strong>
<div id="receiptBigoId"></div>
</div>

<div class="receipt-info">
<strong>Agency:</strong>
<div id="receiptAgency"></div>
</div>

<div class="receipt-info">
<strong>Level:</strong>
<div id="receiptLevel"></div>
</div>

<div class="receipt-info">
<strong>Event:</strong>
<div id="receiptEvent"></div>
</div>

<div class="receipt-info">
<strong>Date:</strong>
<div id="receiptDate"></div>
</div>

<div class="receipt-info">
<strong>Time:</strong>
<div id="receiptSlot"></div>
</div>

<div class="receipt-buttons">

<button class="receipt-btn print-btn" onclick="window.print()">
Print
</button>

<button class="receipt-btn close-btn" onclick="closeReceipt()">
Close
</button>

</div>

</div>

</div>

<script src="https://cdn.jsdelivr.net/npm/xlsx/dist/xlsx.full.min.js"></script>

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
}
from "https://www.gstatic.com/firebasejs/10.7.1/firebase-firestore.js";

import {
getAuth,
signInWithEmailAndPassword,
signOut,
onAuthStateChanged
}
from "https://www.gstatic.com/firebasejs/10.7.1/firebase-auth.js";

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

const auth = getAuth(app);

const slotsContainer = document.getElementById("slots");

const records = document.getElementById("records");

let bookings = [];

let selectedSlot = "";

const slots = [
'8:00 PM',
'8:15 PM',
'8:30 PM',
'8:45 PM',
'9:00 PM',
'9:15 PM',
'9:30 PM',
'9:45 PM',
'10:00 PM',
'10:15 PM'
];

function renderSlots(){

slotsContainer.innerHTML = "";

const selectedDate =
document.getElementById("date").value;

slots.forEach(slot=>{

const btn = document.createElement("button");

btn.className = "slot-btn";

btn.innerText = slot;

const booked = bookings.find(
x => x.date === selectedDate &&
x.slot === slot
);

if(booked){

btn.classList.add("booked");

btn.innerText = slot + " BOOKED";

btn.disabled = true;

}

btn.onclick = ()=>{

if(booked) return;

document.querySelectorAll(".slot-btn")
.forEach(x=>x.classList.remove("selected"));

btn.classList.add("selected");

selectedSlot = slot;

}

slotsContainer.appendChild(btn);

});

}

async function loadBookings(){

const snap =
await getDocs(collection(db,"bookings"));

bookings = [];

records.innerHTML = "";

snap.forEach(docSnap=>{

const data = docSnap.data();

bookings.push(data);

records.innerHTML += `

<div class="record">

<div style="display:flex;justify-content:space-between;gap:10px;align-items:flex-start;">

<div>
<strong>${data.name}</strong><br>
🆔 ${data.bigoId}<br>
🎯 ${data.eventType}<br>
📅 ${data.date}<br>
🕒 ${data.slot}
</div>

<button
onclick="deleteBooking('${docSnap.id}','${data.name}','${data.bigoId}')"
style="
background:#ef4444;
border:none;
padding:10px 12px;
border-radius:12px;
color:white;
font-weight:800;
cursor:pointer;
">
Delete
</button>

</div>

</div>

`;

});

document.getElementById("totalBookings")
.innerText = bookings.length;

const today =
new Date().toISOString().split("T")[0];

document.getElementById("todayBookings")
.innerText =
bookings.filter(x=>x.date===today).length;

renderSlots();

}

async function loadDeletedBookings(){

const deletedContainer =
document.getElementById("deletedRecords");

deletedContainer.innerHTML = "";

const snap =
await getDocs(collection(db,"deletedBookings"));

snap.forEach(docSnap=>{

const data = docSnap.data();

deletedContainer.innerHTML += `

<div class="record"
style="border-left:4px solid #ef4444;">

❌ <strong>${data.name}</strong><br>
🆔 ${data.bigoId}<br>
🕒 Deleted: ${data.deletedAt}

</div>

`;

});

}

let bookingLoading = false;

async function bookSlot(){

if(bookingLoading) return;

bookingLoading = true;

const bookBtn =
document.getElementById("bookBtn");

bookBtn.disabled = true;

bookBtn.innerText = "Processing...";

const booking = {

name:document.getElementById("name").value.trim(),
bigoId:document.getElementById("bigoId").value.trim(),
agency:document.getElementById("agency").value.trim(),
level:document.getElementById("level").value.trim(),
gmail:document.getElementById("gmail").value.trim(),
eventType:document.getElementById("eventType").value,
date:document.getElementById("date").value,
slot:selectedSlot,
createdAt:serverTimestamp()

};

if(
!booking.name ||
!booking.bigoId ||
!booking.agency ||
!booking.level ||
!booking.gmail ||
!booking.eventType ||
!booking.date ||
!booking.slot
){

alert("Complete all fields.");

bookBtn.disabled = false;

bookBtn.innerText = "Reserve Now";

bookingLoading = false;

return;

}

const alreadyBooked =
bookings.find(
x => x.date === booking.date &&
x.slot === booking.slot
);

if(alreadyBooked){

alert("Slot already booked.");

renderSlots();

bookBtn.disabled = false;

bookBtn.innerText = "Reserve Now";

bookingLoading = false;

return;

}

try{

await addDoc(
collection(db,"bookings"),
booking
);

showReceipt(booking);

await loadBookings();

document.getElementById("name").value = "";
document.getElementById("bigoId").value = "";
document.getElementById("agency").value = "";
document.getElementById("level").value = "";
document.getElementById("gmail").value = "";
document.getElementById("eventType").value = "";
document.getElementById("date").value = "";

selectedSlot = "";

}catch(error){

console.error(error);

alert("Booking failed.");

}

bookBtn.disabled = false;

bookBtn.innerText = "Reserve Now";

bookingLoading = false;

}

function showReceipt(data){

document.getElementById("receiptName")
.innerText = data.name;

document.getElementById("receiptBigoId")
.innerText = data.bigoId;

document.getElementById("receiptAgency")
.innerText = data.agency;

document.getElementById("receiptLevel")
.innerText = data.level;

document.getElementById("receiptEvent")
.innerText = data.eventType;

document.getElementById("receiptDate")
.innerText = data.date;

document.getElementById("receiptSlot")
.innerText = data.slot;

document.getElementById("receiptModal")
.style.display = "flex";

}

window.closeReceipt = function(){

document.getElementById("receiptModal")
.style.display = "none";

}

window.deleteBooking = async function(id,name,bigoId){

const confirmDelete =
confirm("Delete booking?");

if(!confirmDelete) return;

await addDoc(
collection(db,"deletedBookings"),
{
name:name,
bigoId:bigoId,
deletedAt:new Date().toLocaleString()
}
);

await deleteDoc(doc(db,"bookings",id));

loadBookings();

loadDeletedBookings();

}

async function login(){

const email =
document.getElementById("adminEmail").value;

const password =
document.getElementById("adminPassword").value;

try{

await signInWithEmailAndPassword(
auth,
email,
password
);

alert("Admin Login Success");

}catch{

alert("Login Failed");

}

}

async function logout(){

await signOut(auth);

}

async function clearAllBookings(){

const confirmDelete =
confirm("Delete ALL bookings?");

if(!confirmDelete) return;

const snap =
await getDocs(collection(db,"bookings"));

for(const item of snap.docs){

await deleteDoc(doc(db,"bookings",item.id));

}

loadBookings();

}

function downloadExcel(){

const worksheet =
XLSX.utils.json_to_sheet(bookings);

const workbook =
XLSX.utils.book_new();

XLSX.utils.book_append_sheet(
workbook,
worksheet,
"Bookings"
);

XLSX.writeFile(
workbook,
"BOOKINGS.xlsx"
);

}

document.getElementById("bookBtn")
.addEventListener("click",bookSlot);

document.getElementById("loginBtn")
.addEventListener("click",login);

document.getElementById("logoutBtn")
.addEventListener("click",logout);

document.getElementById("downloadExcelBtn")
.addEventListener("click",downloadExcel);

document.getElementById("clearBookingsBtn")
.addEventListener("click",clearAllBookings);

document.getElementById("date")
.addEventListener("change",renderSlots);

document.getElementById("bigoSearchInput")
.addEventListener("input",(e)=>{

const value =
e.target.value.toLowerCase();

const allRecords =
document.querySelectorAll(".record");

allRecords.forEach(record=>{

if(
record.innerText.toLowerCase().includes(value)
){

record.style.display = "block";

}else{

record.style.display = "none";

}

});

});

onAuthStateChanged(auth,(user)=>{

if(user){

document.getElementById("adminDashboard")
.style.display = "block";

}else{

document.getElementById("adminDashboard")
.style.display = "none";

}

});

loadBookings();

loadDeletedBookings();

</script>

</body>
</html>
