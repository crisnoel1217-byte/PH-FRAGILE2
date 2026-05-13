
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

input{
  width:100%;
  background:rgba(0,0,0,0.35);
  border:1px solid rgba(255,255,255,0.08);
  border-radius:18px;
  padding:16px;
  color:white;
  outline:none;
  transition:0.3s;
}

input:focus{
  border-color:#22d3ee;
  box-shadow:0 0 15px rgba(34,211,238,0.3);
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
  max-height:300px;
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
    PH-FRAGILE2 AGENCY <br>
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
<input id="adminPassword" type="password" placeholder="Password" style="margin-top:15px">

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

<div style="display:flex;gap:10px;margin-bottom:15px;flex-wrap:wrap;">
<button class="login-btn" id="downloadExcelBtn" style="margin-top:0;flex:1;min-width:180px;">
Download Excel Report
</button>

<button class="logout-btn" id="clearBookingsBtn" style="margin-top:0;flex:1;min-width:180px;">
Delete All Bookings
</button>
</div>

<div class="records" id="records"></div>
</div>

</div>
</div>

<div class="footer">
CN OPK PRO DASHBOARD © 2026
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
  doc
} from "https://www.gstatic.com/firebasejs/10.7.1/firebase-firestore.js";

import {
  getAuth,
  signInWithEmailAndPassword,
  signOut,
  onAuthStateChanged
} from "https://www.gstatic.com/firebasejs/10.7.1/firebase-auth.js";

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

function renderSlots(){

  slotsContainer.innerHTML = "";

  slots.forEach(slot => {

    const btn = document.createElement("button");

    btn.className = "slot-btn";
    btn.innerText = slot;

    btn.onclick = () => {

      document.querySelectorAll(".slot-btn")
      .forEach(x => x.classList.remove("selected"));

      btn.classList.add("selected");
      selectedSlot = slot;
    }

    slotsContainer.appendChild(btn);
  })
}

async function loadBookings(){

  const snap = await getDocs(collection(db,"bookings"));

  bookings = [];

  records.innerHTML = "";

  snap.forEach(doc => {

    const data = doc.data();

    bookings.push(data);

    records.innerHTML += `
<div class="record">
<div style="display:flex;justify-content:space-between;gap:15px;align-items:flex-start;">
<div>
<strong>${data.name}</strong><br>
🆔 ${data.bigoId}<br>
🏢 ${data.agency}<br>
⭐ ${data.level}<br>
📧 ${data.gmail}<br>
🕒 ${data.slot}<br>
📅 ${data.date}
</div>

<button onclick="window.deleteBooking('${doc.id}')"
style="background:#ef4444;border:none;padding:10px 14px;border-radius:12px;color:white;font-weight:700;cursor:pointer;">
Delete
</button>
</div>
</div>
`;
  })

  totalBookings.innerText = bookings.length;

  const today = new Date().toISOString().split("T")[0];

  const todayCount = bookings.filter(
    x => x.date === today
  ).length;

  todayBookings.innerText = todayCount;
}

async function bookSlot(){

  const booking = {
    name:document.getElementById("name").value,
    bigoId:document.getElementById("bigoId").value,
    agency:document.getElementById("agency").value,
    level:document.getElementById("level").value,
    gmail:document.getElementById("gmail").value,
    date:document.getElementById("date").value,
    slot:selectedSlot
  };

  if(
    !booking.name ||
    !booking.bigoId ||
    !booking.agency ||
    !booking.level ||
    !booking.gmail ||
    !booking.date ||
    !booking.slot
  ){
    alert("Complete all fields");
    return;
  }

  const alreadyBooked = bookings.find(
    x => x.date === booking.date &&
    x.slot === booking.slot
  );

  if(alreadyBooked){
    alert("Time slot already booked");
    return;
  }

  await addDoc(collection(db,"bookings"),booking);

  alert("Booking Successful 🚀");

  location.reload();
}

async function login(){

  const email = document.getElementById("adminEmail").value;
  const password = document.getElementById("adminPassword").value;

  try{

    await signInWithEmailAndPassword(
      auth,
      email,
      password
    );

    alert("Admin Login Success");

  }catch(err){

    alert("Login Failed");
  }
}

async function logout(){
  await signOut(auth);
  adminDashboard.style.display = 'none';
  alert("Logged Out");
}

window.deleteBooking = async function(id){

  const confirmDelete = confirm("Delete this booking?");

  if(!confirmDelete) return;

  await deleteDoc(doc(db,"bookings",id));

  alert("Booking Deleted");

  loadBookings();
}

async function clearAllBookings(){

  const confirmDelete = confirm("Delete ALL bookings?");

  if(!confirmDelete) return;

  const snap = await getDocs(collection(db,"bookings"));

  for(const item of snap.docs){
    await deleteDoc(doc(db,"bookings",item.id));
  }

  alert("All bookings deleted");

  loadBookings();
}

function downloadExcel(){

  const exportData = bookings.map(x => ({
    Name:x.name,
    BigoID:x.bigoId,
    Agency:x.agency,
    Level:x.level,
    Gmail:x.gmail,
    Date:x.date,
    Time:x.slot
  }));

  const worksheet = XLSX.utils.json_to_sheet(exportData);

  const workbook = XLSX.utils.book_new();

  XLSX.utils.book_append_sheet(workbook,worksheet,"Bookings");

  XLSX.writeFile(workbook,"CN_OPK_BOOKINGS.xlsx");
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

onAuthStateChanged(auth,(user)=>{

  if(user){
    adminDashboard.style.display = 'block';
    console.log("Admin Online");
  }
  else{
    adminDashboard.style.display = 'none';
    console.log("Guest Mode");
  }
})

renderSlots();
loadBookings();

</script>
  <!-- CONTACT INQUIRIES -->
<div class="card" style="max-width:900px;margin:30px auto;text-align:center;">
  <h2 style="font-size:26px;font-weight:800;margin-bottom:10px;">📩 For Inquiries</h2>
  <p style="color:#9ca3af;">📞 09911530204</p>
  <p style="color:#9ca3af;">📧 CRISNOEL1217@GMAIL.COM</p>
  <p style="color:#9ca3af;">🎯 BIGO ID: TRD10_28</p>
</div>
  <!-- SUCCESS SCREEN -->
<div class="success-overlay" id="successOverlay">
  <div class="success-box">
   
<script>
function showSuccess(){
  const el = document.getElementById('successOverlay');
  el.style.display = 'flex';

  setTimeout(()=>{
    el.style.display = 'none';
  },2500);
}
</script>

</body>
</html>

</body>
</html>

