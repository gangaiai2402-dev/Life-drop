# Life-drop
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>LifeDrop</title>

<style>
body {
  margin: 0;
  font-family: Arial, sans-serif;
  background: linear-gradient(180deg, #FF0000, #FFFFFF);
  color: #fff;
  text-align: center;
}

.section {
  padding: 40px 20px;
}

.card {
  background: rgba(255,255,255,0.2);
  padding: 20px;
  border-radius: 12px;
  margin: 20px auto;
  max-width: 350px;
}

input, select, button {
  width: 90%;
  padding: 12px;
  margin-top: 10px;
  border-radius: 8px;
  border: none;
  font-size: 16px;
}

button {
  background: #fff;
  color: #d00;
  font-weight: bold;
  cursor: pointer;
}

button:hover {
  background: #ffd5d5;
}

.hidden {
  display: none;
}

.hospital-btn {
  background: #fff;
  color: #c00;
  padding: 15px;
  margin: 10px 0;
  border-radius: 10px;
  font-weight: bold;
}
</style>
</head>

<body>

<!-- INTRO -->
<div id="intro" class="section">
  <h1>LifeDrop</h1>
  <p>Your blood can save lives.</p>
  <img src="https://i.imgur.com/lhP0PeT.png" width="200">
  <button onclick="showPhone()">Continue</button>
</div>

<!-- PHONE -->
<div id="phonePage" class="section hidden">
  <div class="card">
    <h2>Enter Phone Number</h2>
    <input type="tel" id="phone" placeholder="Phone Number">
    <button onclick="showOTP()">Next</button>
  </div>
</div>

<!-- OTP -->
<div id="otpPage" class="section hidden">
  <div class="card">
    <h2>Enter OTP</h2>
    <input id="otp" placeholder="1234">
    <button onclick="showBlood()">Verify</button>
  </div>
</div>

<!-- BLOOD GROUP -->
<div id="bloodPage" class="section hidden">
  <div class="card">
    <h2>Select Blood Group</h2>
    <select id="bloodGroup">
      <option value="">Choose</option>
      <option>A+</option><option>A-</option>
      <option>B+</option><option>B-</option>
      <option>O+</option><option>O-</option>
      <option>AB+</option><option>AB-</option>
    </select>
    <button onclick="showLocation()">Next</button>
  </div>
</div>

<!-- LOCATION -->
<div id="locationPage" class="section hidden">
  <div class="card">
    <h2>Location Access</h2>
    <p>We need your location to find nearest hospitals.</p>
    <button onclick="findHospitals()">Allow Location</button>
  </div>
</div>

<!-- HOME -->
<div id="homePage" class="section hidden">
  <h2>Hospitals Requesting Your Blood Group</h2>
  <div id="hospitalList"></div>
</div>

<!-- APPOINTMENT -->
<div id="appointmentPage" class="section hidden">
  <div class="card">
    <h2>Book Appointment</h2>
    <p id="selectedHospital"></p>
    <button onclick="finish()">Confirm Appointment</button>
  </div>
</div>

<!-- THANK YOU -->
<div id="donePage" class="section hidden">
  <h1>Thank You!</h1>
  <p>You have successfully booked your blood donation appointment.</p>
</div>


<script>
function hideAll() {
  document.querySelectorAll('.section').forEach(s => s.classList.add('hidden'));
}

function showPhone() { hideAll(); phonePage.classList.remove('hidden'); }
function showOTP() { hideAll(); otpPage.classList.remove('hidden'); }
function showBlood() { hideAll(); bloodPage.classList.remove('hidden'); }
function showLocation() { hideAll(); locationPage.classList.remove('hidden'); }

function findHospitals() {
  hideAll();
  homePage.classList.remove('hidden');

  let hospitals = [
    "Chennai Parvathi Hospital",
    "Global Hospital",
    "Apollo Main Hospital",
    "Vijaya Hospital",
    "Stanley Government Hospital"
  ];

  let listDiv = document.getElementById("hospitalList");
  listDiv.innerHTML = "";

  hospitals.forEach(h => {
    let btn = document.createElement("button");
    btn.innerHTML = h;
    btn.className = "hospital-btn";
    btn.onclick = () => bookHospital(h);
    listDiv.appendChild(btn);
  });
}

function bookHospital(name) {
  hideAll();
  appointmentPage.classList.remove('hidden');
  document.getElementById("selectedHospital").innerHTML =
      "Hospital: <b>" + name + "</b>";
}

function finish() {
  hideAll();
  donePage.classList.remove('hidden');
}
</script>

</body>
</html>
 