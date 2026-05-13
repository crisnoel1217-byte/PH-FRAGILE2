<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>PH-FRAGILE 2 AGENCY BOOKING PORTAL</title>

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

.header{
text-align:center;
margin-bottom:40px;
}

.badge{
display:inline-flex;
align-items:center;
gap:10px;
background:rgba(255,255,255,0.08);
border:1px solid rgba(255,255,255,0.08);
padding:12px 22px;
border-radius:999px;
backdrop-filter:blur(12px);
margin-bottom:20px;
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
font-size:70px;
font-weight:900;
line-height:1;
background:linear-gradient(90deg,#a855f7,#22d3ee,#ec4899);
-webkit-background-clip:text;
color:transparent;
}

.subtitle{
color:#9ca3af;
margin-top:20px;
font-size:18px;
}

.grid{
display:grid;
grid-template-columns:2fr 1fr;
gap:25px;
}

.card{
background:rgba(255,255,255,0.06);
border:1px solid rgba(255,255,255,0.08);
border-radius:30px;
backdrop-filter:blur(16px);
padding:25px;
box-shadow:0 0 30px rgba(0,0,0,0.25);
}

.input-grid{
display:grid;
grid-template-columns:1fr 1fr;
gap:15px;
}

input,
select{
width:100%;
background:rgba(0,0,0,0.35);
border:1px solid rgba(255,255,255,0.08);
border-radius:18px;
padding:16px;
color:white;
outline:none;
transition:0.3s;
}

input:focus,
select:focus{
border-color:#22d3ee;
box-shadow:0 0 15px rgba(34,211,238,0.3);
}

select option{
background:#111827;
}

.full{
grid-column:1/-1;
}

.slots{
display:grid;
grid-template-columns:repeat(5,1fr);
gap:12px;
margin-top:20px;
}

.slot-btn{
background:rgba(255,255,255,0.05);
border:1px solid rgba(255,255,255,0.08);
border-radius:18px;
padding:18px 10px;
color:white;
cursor:pointer;
transition:0.3s;
font-weight:700;
white-space:pre-line;
}

.slot-btn:hover{
transform:translateY(-3px) scale(1.03);
border-color:#22d3ee;
background:rgba(34,211,238,0.15);
}

.selected{
border:2px solid #22d3ee;
background:rgba(34,211,238,0.2);
}

.book-btn,
.login-btn,
.logout-btn{
width:100%;
border:none;
margin-top:20px;
padding:18px;
border-radius:20px;
font-weight:800;
font-size:16px;
cursor:pointer;
transition:0.3s;
color:black;
background:linear-gradient(90deg,#8b5cf6,#22d3ee,#ec4899);
}

.book-btn:hover,
.login-btn:hover,
.logout-btn:hover{
transform:scale(1.02);
}

.sidebar{
display:flex;
flex-direction:column;
gap:25px;
}

.stat-box{
background:rgba(0,0,0,0.3);
border-radius:20px;
padding:20px;
display:flex;
justify-content:space-between;
align-items:center;
margin-top:15px;
}

.stat-number{
font-size:34px;
font-weight:900;
}

.records{
margin-top:20px;
display:flex;
flex-direction:column;
gap:10px;
max-height:350px;
overflow:auto;
}

.record{
background:rgba(255,255,255,0.05);
padding:15px;
border-radius:18px;
}

.footer{
margin-top:40px;
text-align:center;
color:#6b7280;
}

.receipt-popup{
position:fixed;
inset:0;
background:rgba(0,0,0,0.7);
display:none;
justify-content:center;
align-items:center;
z-index:9999;
padding:20px;
}

.receipt-card{
width:100%;
max-width:420px;
background:#0f172a;
border:1px solid rgba(255,255,255,0.08);
border-radius:30px;
padding:30px;
}

.receipt-title{
font-size:30px;
font-weight:900;
margin-bottom:20px;
text-align:center;
background:linear-gradient(90deg,#8b5cf6,#22d3ee,#ec4899);
-webkit-background-clip:text;
color:transparent;
}

.receipt-info{
margin-top:15px;
background:rgba(255,255,255,0.05);
padding:14px;
border-radius:16px;
}

.receipt-label{
color:#9ca3af;
font-size:13px;
}

.receipt-value{
font-size:17px;
font-weight:700;
margin-top:5px;
}

.receipt-close{
width:100%;
margin-top:25px;
border:none;
padding:16px;
border-radius:18px;
font-weight:800;
cursor:pointer;
color:black;
background:linear-gradient(90deg,#8b5cf6,#22d3ee,#ec4899);
}

@media(max-width:900px){

.grid{
grid-template-columns:1fr;
}

.title{
font-size:50px;
}

.slots{
grid-template-columns:repeat(2,1fr);
}

.input-grid{
grid-template-columns:1fr;
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
PH-FRAGILE 2 AGENCY <br>
BOOKING PORTAL
</h1>

<p class="subtitle">
Secure your premium PK schedule with the official PH-FRAGILE AGENCY booking system.
</p>

</div>

<div class="grid">

<div class="card">

<h2 style="font-size:30px;font-weight:800;margin-bottom:10px">
Reserve Your Slot 🚀
</h2>

<p style="color:#9ca3af;margin-bottom:25px">
Choose your preferred OPK schedule.
</p>

<div class="input-grid">

<input id="name" placeholder="Bigo Name">
<input id="bigoId" placeholder="Bigo ID">
<input id="agency" placeholder="Agency">
<input id="level" placeholder="Level">

<select id="opkType" class="full">
<option value="">Select OPK Type</option>
<option>PK TASK BLITZ</option>
<option>BLAZE PK</option>
<option>ALL STAR PK</option>
</select>

<input id="gmail" class="full" placeholder="Gmail">
<input id="date" type="date" class="full">

</div>

<h3 style="margin-top:30px;font-size:22px">
Select Time
</h3>

<div class="slots" id="slots"></div>

<button class="book-btn" id="bookBtn">
Reserve Now
</button>

</div>

<div class="sidebar">

<div class="card">

<h2 style="font-size:28px;font-weight:800;margin-bottom:20px">
Admin Login
</h2>

<input id="adminEmail" placeholder="Admin Email">

<input
id="adminPassword"
type="password"
placeholder="Password"
style="margin-top:15px"
>

<button class="login-btn" id="loginBtn">
Login
</button>

<button class="logout-btn" id="logoutBtn">
Logout
</button>

</div>

<div class="card">

<h2 style="font-size:28px;font-weight:800">
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

<h2 style="font-size:28px;font-weight:800;margin-bottom:15px">
Professional Admin Dashboard
</h2>

<button
class="login-btn"
id="downloadExcelBtn"
style="margin-top:0;">
Download Excel Report
</button>

<input
id="searchBooking"
placeholder="Search booking..."
style="
width:100%;
margin-top:15px;
background:rgba(0,0,0,0.35);
border:1px solid rgba(255,255,255,0.08);
border-radius:18px;
padding:16px;
color:white;
outline:none;
"
/>

<div class="records" id="records"></div>

</div>

</div>

</div>

<div class="footer">
CN OPK PRO DASHBOARD © 2026
</div>

</div>

<div class="receipt-popup" id="receiptPopup">

<div class="receipt-card">

<div class="receipt-title">
BOOKING RECEIPT
</div>

<div class="receipt-info">
<div class="receipt-label">Bigo Name</div>
<div class="receipt-value" id="receiptName"></div>
</div>

<div class="receipt-info">
<div class="receipt-label">Booking Date</div>
<div class="receipt-value" id="receiptDate"></div>
</div>

<div class="receipt-info">
<div class="receipt-label">Booking Time</div>
<div class="receipt-value" id="receiptSlot"></div>
</div>

<button class="receipt-close" onclick="closeReceipt()">
Close Receipt
</button>

</div>

</div>

<script src="https://cdn.jsdelivr.net/npm/xlsx/dist/xlsx.full.min.js"></script>

<script type="module">

import { initializeApp }
from "https://www.gstatic.com/firebasejs/10.7.1/firebase-app.js";

import {
getFirestore,
collection,
addDoc,
getDocs,
deleteDoc,
doc
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
const adminDashboard = document.getElementById("adminDashboard");

const totalBookings = document.getElementById("totalBookings");
const todayBookings = document.getElementById("todayBookings");

let selectedSlot = "";
let bookings = [];

const slots = [
'8:00 PM','8:15 PM','8:30 PM','8:45 PM',
'9:00 PM','9:15 PM','9:30 PM','9:45 PM',
'10:00 PM','10:15 PM'
];

function renderSlots(selectedDate = ""){

slotsContainer.innerHTML = "";

slots.forEach(slot => {

const btn = document.createElement("button");

const alreadyBooked = bookings.find(
x =>
x.date === selectedDate &&
x.slot === slot
);

btn.className = "slot-btn";

if(alreadyBooked){

btn.innerText = slot + "\nNOT AVAILABLE";
btn.style.background = "rgba(239,68,68,0.25)";
btn.style.border = "1px solid #ef4444";
btn.style.cursor = "not-allowed";
btn.disabled = true;

}else{

btn.innerText = slot;

btn.onclick = () => {

document.querySelectorAll(".slot-btn")
.forEach(x => x.classList.remove("selected"));

btn.classList.add("selected");

selectedSlot = slot;

};

}

slotsContainer.appendChild(btn);

});

}

document.getElementById("date")
.addEventListener("change", function(){

renderSlots(this.value);

});

async function loadBookings(){

const snap = await getDocs(collection(db,"bookings"));

bookings = [];

records.innerHTML = "";

snap.forEach(docItem => {

const data = docItem.data();

bookings.push(data);

records.innerHTML += `

<div class="record">

<div style="display:flex;justify-content:space-between;gap:15px;align-items:flex-start;">

<div>
<strong>${data.name}</strong><br>
🆔 ${data.bigoId}<br>
🏢 ${data.agency}<br>
⭐ ${data.level}<br>
🔥 ${data.opkType}<br>
📧 ${data.gmail}<br>
📅 ${data.date}<br>
🕒 ${data.slot}
</div>

<button
onclick="deleteBooking('${docItem.id}')"
style="
background:#ef4444;
border:none;
padding:10px 14px;
border-radius:12px;
color:white;
font-weight:700;
cursor:pointer;
">
Delete
</button>

</div>

</div>

`;

});

totalBookings.innerText = bookings.length;

const today = new Date().toISOString().split("T")[0];

const todayCount = bookings.filter(
x => x.date === today
).length;

todayBookings.innerText = todayCount;

renderSlots(document.getElementById("date").value);

}

async function bookSlot(){

const booking = {

name:document.getElementById("name").value,
bigoId:document.getElementById("bigoId").value,
agency:document.getElementById("agency").value,
level:document.getElementById("level").value,
opkType:document.getElementById("opkType").value,
gmail:document.getElementById("gmail").value,
date:document.getElementById("date").value,
slot:selectedSlot

};

if(
!booking.name ||
!booking.bigoId ||
!booking.agency ||
!booking.level ||
!booking.opkType ||
!booking.gmail ||
!booking.date ||
!booking.slot
){
alert("Complete all fields");
return;
}

const alreadyBooked = bookings.find(
x =>
x.date === booking.date &&
x.slot === booking.slot
);

if(alreadyBooked){
alert("Time slot already booked");
return;
}

await addDoc(collection(db,"bookings"),booking);

showReceipt(booking);

setTimeout(()=>{
location.reload();
},3000);

}

function showReceipt(data){

document.getElementById("receiptName").innerText = data.name;
document.getElementById("receiptDate").innerText = data.date;
document.getElementById("receiptSlot").innerText = data.slot;

document.getElementById("receiptPopup")
.style.display = "flex";

}

window.closeReceipt = function(){

document.getElementById("receiptPopup")
.style.display = "none";

}

window.deleteBooking = async function(id){

const confirmDelete =
confirm("Delete this booking?");

if(!confirmDelete) return;

await deleteDoc(doc(db,"bookings",id));

alert("Booking Deleted ✅");

loadBookings();

}

function downloadExcel(){

const exportData = bookings.map(x => ({
Name:x.name,
BigoID:x.bigoId,
Agency:x.agency,
Level:x.level,
OPK:x.opkType,
Gmail:x.gmail,
Date:x.date,
Time:x.slot
}));

const worksheet =
XLSX.utils.json_to_sheet(exportData);

const workbook =
XLSX.utils.book_new();

XLSX.utils.book_append_sheet(
workbook,
worksheet,
"Bookings"
);

XLSX.writeFile(
workbook,
"CN_OPK_BOOKINGS.xlsx"
);

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

alert("Admin Login Success ✅");

}catch(error){

alert(error.message);

}

}

async function logout(){

await signOut(auth);

adminDashboard.style.display = "none";

}

onAuthStateChanged(auth,(user)=>{

if(user){

adminDashboard.style.display = "block";

}else{

adminDashboard.style.display = "none";

}

});

document.getElementById("bookBtn")
.addEventListener("click",bookSlot);

document.getElementById("downloadExcelBtn")
.addEventListener("click",downloadExcel);

document.getElementById("loginBtn")
.addEventListener("click",login);

document.getElementById("logoutBtn")
.addEventListener("click",logout);

document.getElementById("searchBooking")
.addEventListener("input", function(){

const value = this.value.toLowerCase();

const allRecords =
document.querySelectorAll(".record");

allRecords.forEach(record => {

const text =
record.innerText.toLowerCase();

if(text.includes(value)){

record.style.display = "block";

}else{

record.style.display = "none";

}

});

});

renderSlots();
loadBookings();

</script>

</body>
</html>
