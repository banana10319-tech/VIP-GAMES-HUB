<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>VIP GAME</title>

<style>
*{box-sizing:border-box;margin:0;padding:0}
body{
  font-family:Arial,sans-serif;
  background:#070b10;
  color:#fff;
  min-height:100vh;
}
header{
  position:sticky;top:0;z-index:10;
  padding:15px 20px;
  background:rgba(10,15,22,.82);
  backdrop-filter:blur(18px);
  border-bottom:1px solid #1d2935;
  display:flex;
  justify-content:space-between;
  align-items:center;
}
.logo{
  font-size:22px;
  font-weight:800;
  color:#48ff9b;
}
button{
  border:0;
  border-radius:12px;
  padding:10px 15px;
  color:#fff;
  background:#17222d;
  cursor:pointer;
}
button:hover{background:#243544}
.hero{
  padding:55px 20px 30px;
  text-align:center;
}
.hero h1{
  font-size:42px;
  margin-bottom:10px;
}
.hero h1 span{color:#48ff9b}
.hero p{color:#9ca9b5}
.container{max-width:1050px;margin:auto;padding:20px}
.search{
  width:100%;
  padding:15px;
  border-radius:15px;
  border:1px solid #253341;
  background:#101820;
  color:white;
  outline:none;
  margin-bottom:15px;
}
.filters{
  display:flex;
  gap:8px;
  overflow:auto;
  padding-bottom:15px;
}
.filters button.active{
  background:#48ff9b;
  color:#07110c;
}
.games{
  display:grid;
  grid-template-columns:repeat(auto-fit,minmax(230px,1fr));
  gap:18px;
}
.card{
  background:rgba(18,27,36,.8);
  border:1px solid #243442;
  border-radius:20px;
  overflow:hidden;
  box-shadow:0 10px 30px rgba(0,0,0,.25);
}
.card img{
  width:100%;
  height:150px;
  object-fit:cover;
  background:#101820;
}
.card-body{padding:16px}
.card h3{margin-bottom:8px}
.card p{
  color:#9eabb6;
  font-size:14px;
  margin-bottom:8px;
}
.meta{
  font-size:12px;
  color:#7f8d99;
  margin:8px 0 12px;
}
.download{
  width:100%;
  background:#48ff9b;
  color:#06110b;
  font-weight:bold;
}
.delete{
  width:100%;
  margin-top:8px;
  background:#402027;
}
.modal{
  display:none;
  position:fixed;
  inset:0;
  z-index:30;
  background:rgba(0,0,0,.7);
  backdrop-filter:blur(8px);
  padding:20px;
  overflow:auto;
}
.modal-box{
  max-width:500px;
  margin:40px auto;
  background:#111a23;
  border:1px solid #293946;
  border-radius:22px;
  padding:22px;
}
.modal-box h2{margin-bottom:18px}
input,textarea,select{
  width:100%;
  padding:13px;
  margin:7px 0;
  border-radius:12px;
  border:1px solid #293946;
  background:#0a1118;
  color:#fff;
  outline:none;
}
textarea{min-height:90px;resize:vertical}
.form-btn{
  width:100%;
  margin-top:10px;
  background:#48ff9b;
  color:#06110b;
  font-weight:bold;
}
.close{
  float:right;
  background:#26323d;
}
.admin-panel{display:none;margin-bottom:20px}
footer{
  text-align:center;
  padding:35px 15px;
  color:#71808d;
}
a{color:inherit;text-decoration:none}
@media(max-width:600px){
  .hero h1{font-size:34px}
  header{padding:13px}
  .container{padding:15px}
}
</style>
</head>

<body>

<header>
  <div class="logo" id="siteLogo">VIP GAME</div>
  <button onclick="openLogin()">Admin</button>
</header>

<section class="hero">
  <h1 id="heroTitle">Welcome to <span>VIP GAME</span></h1>
  <p id="heroBio">Discover • Download • Play</p>
</section>

<main class="container">

  <div id="adminPanel" class="admin-panel">
    <button onclick="openAddGame()">＋ Add Game</button>
    <button onclick="openProfile()">✎ Edit Profile</button>
    <button onclick="logout()">Logout</button>
  </div>

  <input
    id="search"
    class="search"
    type="text"
    placeholder="Search games..."
    oninput="showGames()"
  >

  <div class="filters">
    <button class="active" onclick="setCategory('All',this)">All</button>
    <button onclick="setCategory('Android',this)">Android</button>
    <button onclick="setCategory('PC',this)">PC</button>
    <button onclick="setCategory('Action',this)">Action</button>
    <button onclick="setCategory('Racing',this)">Racing</button>
  </div>

  <div id="games" class="games"></div>

</main>

<footer>
  <p>© 2026 <span id="footerName">VIP GAME</span></p>
  <p>Creator — <span id="creator">VIP|•KIRA</span></p>
  <p id="telegramArea"></p>
</footer>


<!-- LOGIN -->
<div id="loginModal" class="modal">
  <div class="modal-box">
    <button class="close" onclick="closeModal('loginModal')">✕</button>
    <h2>Admin Login</h2>

    <input id="username" placeholder="Username">
    <input id="password" type="password" placeholder="Password">

    <button class="form-btn" onclick="login()">Login</button>
  </div>
</div>


<!-- ADD GAME -->
<div id="gameModal" class="modal">
  <div class="modal-box">
    <button class="close" onclick="closeModal('gameModal')">✕</button>
    <h2>Add Game</h2>

    <input id="gameName" placeholder="Game Name">
    <textarea id="gameDesc" placeholder="Description"></textarea>
    <input id="gameSize" placeholder="Size e.g. 500 MB">

    <select id="gameCategory">
      <option>Android</option>
      <option>PC</option>
      <option>Action</option>
      <option>Racing</option>
    </select>

    <input id="gameLink" placeholder="Download Link">
    <input id="gameImage" type="file" accept="image/*">

    <button class="form-btn" onclick="addGame()">Save Game</button>
  </div>
</div>


<!-- PROFILE -->
<div id="profileModal" class="modal">
  <div class="modal-box">
    <button class="close" onclick="closeModal('profileModal')">✕</button>
    <h2>Edit Profile</h2>

    <input id="profileName" placeholder="Website Name">
    <input id="profileTitle" placeholder="Hero Title">
    <textarea id="profileBio" placeholder="Bio"></textarea>
    <input id="profileCreator" placeholder="Creator">
    <input id="profileTelegram" placeholder="Telegram Link">
    <input id="profileImage" type="file" accept="image/*">

    <button class="form-btn" onclick="saveProfile()">Save Profile</button>
  </div>
</div>


<script>
const ADMIN_USER = "Vip Game members";
const ADMIN_PASS = "2864981";

let isAdmin = false;
let currentCategory = "All";

let games = JSON.parse(localStorage.getItem("vipGames") || "[]");

let profile = JSON.parse(
  localStorage.getItem("vipProfile") ||
  '{"name":"VIP GAME","title":"Welcome to VIP GAME","bio":"Discover • Download • Play","creator":"VIP|•KIRA","telegram":""}'
);


function saveGames(){
  localStorage.setItem("vipGames", JSON.stringify(games));
}


function formatPostDate(value){
  if(!value) return "Date not available";

  const d = new Date(value);

  return d.toLocaleString([],{
    month:"short",
    day:"numeric",
    year:"numeric",
    hour:"numeric",
    minute:"2-digit"
  });
}


function showGames(){

  const box = document.getElementById("games");
  const search = document.getElementById("search").value.toLowerCase();

  let list = [...games];

  list.sort((a,b)=>{
    return new Date(b.date || 0) - new Date(a.date || 0);
  });

  list = list.filter(game=>{
    const matchSearch =
      game.name.toLowerCase().includes(search) ||
      game.desc.toLowerCase().includes(search);

    const matchCategory =
      currentCategory === "All" ||
      game.category === currentCategory;

    return matchSearch && matchCategory;
  });

  box.innerHTML = "";

  if(list.length === 0){
    box.innerHTML =
      '<p style="color:#7f8d99">No games found.</p>';
    return;
  }

  list.forEach(game=>{

    const card = document.createElement("div");
    card.className = "card";

    card.innerHTML = `
      <img src="${game.image || ''}" alt="">
      <div class="card-body">
        <h3>${escapeHTML(game.name)}</h3>

        <p>${escapeHTML(game.desc)}</p>

        <p>📦 Size: ${escapeHTML(game.size)}</p>
        <p>🎮 Category: ${escapeHTML(game.category)}</p>

        <div class="meta">
          📅 Posted • ${formatPostDate(game.date)}
        </div>

        <a href="${escapeAttr(game.link)}" target="_blank">
          <button class="download">Download</button>
        </a>

        ${
          isAdmin
          ? `<button class="delete" onclick="deleteGame('${game.id}')">Delete</button>`
          : ""
        }
      </div>
    `;

    box.appendChild(card);
  });
}


function escapeHTML(text){
  return String(text || "")
    .replaceAll("&","&amp;")
    .replaceAll("<","&lt;")
    .replaceAll(">","&gt;")
    .replaceAll('"',"&quot;")
    .replaceAll("'","&#039;");
}


function escapeAttr(text){
  return String(text || "").replaceAll('"',"&quot;");
}


function setCategory(category,btn){

  currentCategory = category;

  document.querySelectorAll(".filters button")
    .forEach(b=>b.classList.remove("active"));

  btn.classList.add("active");

  showGames();
}


function openLogin(){
  document.getElementById("loginModal").style.display="block";
}


function login(){

  const u = document.getElementById("username").value;
  const p = document.getElementById("password").value;

  if(u === ADMIN_USER && p === ADMIN_PASS){

    isAdmin = true;

    closeModal("loginModal");

    document.getElementById("adminPanel").style.display="block";

    showGames();

    alert("Admin Login Successful ✅");

  }else{
    alert("Wrong username or password ❌");
  }
}


function logout(){

  isAdmin = false;

  document.getElementById("adminPanel").style.display="none";

  showGames();
}


function openAddGame(){

  if(!isAdmin) return;

  document.getElementById("gameModal").style.display="block";
}


function addGame(){

  if(!isAdmin) return;

  const name =
    document.getElementById("gameName").value.trim();

  const desc =
    document.getElementById("gameDesc").value.trim();

  const size =
    document.getElementById("gameSize").value.trim();

  const category =
    document.getElementById("gameCategory").value;

  const link =
    document.getElementById("gameLink").value.trim();

  const file =
    document.getElementById("gameImage").files[0];

  if(!name || !link){

    alert("Game Name and Download Link are required.");

    return;
  }

  const save = imageData => {

    games.push({
      id: Date.now().toString(),
      name,
      desc,
      size,
      category,
      link,
      image:imageData || "",
      date:new Date().toISOString()
    });

    saveGames();

    closeModal("gameModal");

    clearGameForm();

    showGames();

    alert("Game Added Successfully 🎮");
  };


  if(file){

    const reader = new FileReader();

    reader.onload = e => save(e.target.result);

    reader.readAsDataURL(file);

  }else{

    save("");
  }
}


function deleteGame(id){

  if(!isAdmin) return;

  if(confirm("Delete this game?")){

    games = games.filter(g=>g.id !== id);

    saveGames();

    showGames();
  }
}


function clearGameForm(){

  document.getElementById("gameName").value="";
  document.getElementById("gameDesc").value="";
  document.getElementById("gameSize").value="";
  document.getElementById("gameLink").value="";
  document.getElementById("gameImage").value="";
}


function openProfile(){

  if(!isAdmin) return;

  document.getElementById("profileName").value=profile.name;
  document.getElementById("profileTitle").value=profile.title;
  document.getElementById("profileBio").value=profile.bio;
  document.getElementById("profileCreator").value=profile.creator;
  document.getElementById("profileTelegram").value=profile.telegram;

  document.getElementById("profileModal").style.display="block";
}


function saveProfile(){

  if(!isAdmin) return;

  profile.name =
    document.getElementById("profileName").value.trim() || "VIP GAME";

  profile.title =
    document.getElementById("profileTitle").value.trim() || "Welcome to VIP GAME";

  profile.bio =
    document.getElementById("profileBio").value.trim() || "Discover • Download • Play";

  profile.creator =
    document.getElementById("profileCreator").value.trim() || "VIP|•KIRA";

  profile.telegram =
    document.getElementById("profileTelegram").value.trim();

  localStorage.setItem("vipProfile",JSON.stringify(profile));

  applyProfile();

  closeModal("profileModal");

  alert("Profile Saved ✅");
}


function applyProfile(){

  document.getElementById("siteLogo").textContent=profile.name;

  document.getElementById("heroTitle").textContent=profile.title;

  document.getElementById("heroBio").textContent=profile.bio;

  document.getElementById("footerName").textContent=profile.name;

  document.getElementById("creator").textContent=profile.creator;

  const tg =
    document.getElementById("telegramArea");

  if(profile.telegram){

    tg.innerHTML =
      `<a href="${escapeAttr(profile.telegram)}" target="_blank">Telegram</a>`;

  }else{

    tg.innerHTML="";
  }
}


function closeModal(id){
  document.getElementById(id).style.display="none";
}


window.onclick = function(e){

  document.querySelectorAll(".modal").forEach(modal=>{

    if(e.target === modal){
      modal.style.display="none";
    }

  });
};


applyProfile();
showGames();
</script>

</body>
</html>
