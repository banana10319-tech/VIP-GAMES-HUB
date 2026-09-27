<!--
VIP GAME
Single-file website
Admin:
Username: Vip Game members
Password: 2864981

NOTE:
This is a frontend/localStorage website.
For a real public website, use a backend for secure admin authentication.
-->

<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>VIP GAME</title>

<style>
*{
  box-sizing:border-box;
  margin:0;
  padding:0;
}

body{
  font-family:Inter,-apple-system,BlinkMacSystemFont,"SF Pro Display",
  "Segoe UI",sans-serif;
  background:
    radial-gradient(circle at 10% 0%,rgba(0,255,170,.12),transparent 30%),
    radial-gradient(circle at 90% 10%,rgba(0,120,255,.13),transparent 30%),
    #050607;
  color:#fff;
  min-height:100vh;
}

button,input,textarea,select{
  font:inherit;
}

button{
  cursor:pointer;
}

.header{
  position:sticky;
  top:12px;
  z-index:100;
  width:calc(100% - 24px);
  max-width:1200px;
  margin:12px auto 0;
  padding:12px 16px;
  display:flex;
  justify-content:space-between;
  align-items:center;
  border:1px solid rgba(255,255,255,.09);
  border-radius:24px;
  background:rgba(20,22,24,.68);
  backdrop-filter:blur(24px);
  -webkit-backdrop-filter:blur(24px);
  box-shadow:0 12px 40px rgba(0,0,0,.35);
}

.brand{
  display:flex;
  align-items:center;
  gap:10px;
}

.logo,
.logoImg{
  width:42px;
  height:42px;
  border-radius:14px;
}

.logo{
  display:flex;
  align-items:center;
  justify-content:center;
  font-size:20px;
  font-weight:900;
  background:linear-gradient(135deg,#19ffb0,#158cff);
}

.logoImg{
  display:none;
  object-fit:cover;
}

.brandName{
  font-size:17px;
  font-weight:800;
  letter-spacing:.4px;
}

.headerBtns{
  display:flex;
  gap:8px;
}

.btn{
  border:1px solid rgba(255,255,255,.1);
  background:rgba(255,255,255,.07);
  color:#fff;
  padding:10px 14px;
  border-radius:14px;
  font-weight:700;
  transition:.2s;
}

.btn:hover{
  background:rgba(255,255,255,.13);
  transform:translateY(-1px);
}

.redBtn{
  background:rgba(255,60,70,.13);
  color:#ff6972;
}

.container{
  width:calc(100% - 28px);
  max-width:1200px;
  margin:auto;
}

.hero{
  padding:75px 10px 35px;
  text-align:center;
}

.hero h1{
  font-size:clamp(42px,8vw,78px);
  line-height:1;
  font-weight:900;
  letter-spacing:-3px;
  background:linear-gradient(135deg,#fff,#a9fff0,#75aaff);
  -webkit-background-clip:text;
  color:transparent;
}

.hero p{
  margin:18px auto 0;
  max-width:620px;
  color:#999da5;
  font-size:15px;
  line-height:1.7;
}

.heroCreator{
  margin-top:12px;
  color:#62ffc9;
  font-size:13px;
  font-weight:700;
}

.adminPanel{
  display:none;
  margin:15px 0 24px;
  padding:18px;
  border:1px solid rgba(0,255,170,.15);
  border-radius:25px;
  background:rgba(0,255,170,.045);
}

.adminPanel.show{
  display:flex;
  align-items:center;
  justify-content:space-between;
  gap:15px;
}

.adminText{
  color:#8affd5;
  font-size:13px;
  font-weight:700;
}

.searchBox{
  margin:10px 0 15px;
}

.searchBox input{
  width:100%;
  padding:16px 18px;
  border-radius:18px;
  border:1px solid rgba(255,255,255,.09);
  background:rgba(255,255,255,.055);
  color:#fff;
  outline:none;
}

.searchBox input:focus{
  border-color:rgba(0,255,170,.4);
}

.categories{
  display:flex;
  gap:8px;
  overflow-x:auto;
  padding-bottom:8px;
  scrollbar-width:none;
}

.categories::-webkit-scrollbar{
  display:none;
}

.category{
  white-space:nowrap;
  padding:10px 15px;
  border-radius:14px;
  border:1px solid rgba(255,255,255,.08);
  background:rgba(255,255,255,.05);
  color:#a8abb1;
  font-size:13px;
  font-weight:700;
}

.category.active{
  background:#fff;
  color:#000;
}

.sectionTitle{
  margin:25px 0 14px;
  display:flex;
  align-items:center;
  justify-content:space-between;
}

.sectionTitle h2{
  font-size:20px;
}

.sectionTitle span{
  color:#777b82;
  font-size:12px;
}

.games{
  display:grid;
  grid-template-columns:repeat(3,1fr);
  gap:16px;
}

.game{
  overflow:hidden;
  border:1px solid rgba(255,255,255,.08);
  border-radius:27px;
  background:rgba(255,255,255,.045);
  box-shadow:0 15px 45px rgba(0,0,0,.22);
  transition:.25s;
}

.game:hover{
  transform:translateY(-4px);
  border-color:rgba(255,255,255,.15);
}

.gameImageWrap{
  position:relative;
  aspect-ratio:16/9;
  overflow:hidden;
  background:#101214;
}

.gameImage{
  width:100%;
  height:100%;
  object-fit:cover;
  display:block;
}

.gameCategory{
  position:absolute;
  top:10px;
  right:10px;
  padding:7px 10px;
  border-radius:11px;
  background:rgba(0,0,0,.55);
  backdrop-filter:blur(12px);
  font-size:10px;
  font-weight:800;
}

.gameBody{
  padding:17px;
}

.gameName{
  font-size:18px;
  font-weight:850;
}

.gameDesc{
  margin-top:8px;
  color:#8d9198;
  font-size:12px;
  line-height:1.55;
  min-height:38px;
}

.tags{
  display:flex;
  flex-wrap:wrap;
  gap:7px;
  margin-top:12px;
}

.tag{
  padding:7px 9px;
  border-radius:10px;
  background:rgba(255,255,255,.055);
  color:#aeb1b7;
  font-size:10px;
  font-weight:700;
}

/* POST DATE */
.postedDate{
  margin-top:11px;
  display:flex;
  align-items:center;
  gap:5px;
  color:#777c84;
  font-size:10px;
  font-weight:650;
}

.postedDate .calendar{
  font-size:11px;
}

.actions{
  display:flex;
  gap:8px;
  margin-top:15px;
}

.download{
  flex:1;
  border:0;
  padding:12px;
  border-radius:14px;
  background:#fff;
  color:#000;
  font-weight:850;
}

.delete{
  width:44px;
  border:1px solid rgba(255,70,80,.2);
  border-radius:14px;
  background:rgba(255,50,60,.08);
  color:#ff6871;
}

.empty{
  grid-column:1/-1;
  padding:50px 20px;
  text-align:center;
  border:1px dashed rgba(255,255,255,.1);
  border-radius:25px;
  color:#70747b;
}

footer{
  margin-top:70px;
  padding:30px 15px;
  text-align:center;
  color:#666a71;
  font-size:11px;
  border-top:1px solid rgba(255,255,255,.06);
}

.footerCreator{
  margin-top:7px;
  color:#8a8e95;
}

/* MODAL */
.modal{
  display:none;
  position:fixed;
  inset:0;
  z-index:999;
  align-items:center;
  justify-content:center;
  padding:18px;
  background:rgba(0,0,0,.72);
  backdrop-filter:blur(15px);
}

.modal.show{
  display:flex;
}

.modalBox{
  width:100%;
  max-width:470px;
  max-height:90vh;
  overflow:auto;
  padding:22px;
  border:1px solid rgba(255,255,255,.1);
  border-radius:28px;
  background:#111315;
  box-shadow:0 30px 100px rgba(0,0,0,.6);
}

.modalHead{
  display:flex;
  justify-content:space-between;
  align-items:center;
  margin-bottom:18px;
}

.modalHead h3{
  font-size:19px;
}

.close{
  width:35px;
  height:35px;
  border:0;
  border-radius:12px;
  background:rgba(255,255,255,.07);
  color:#fff;
}

.field{
  margin-bottom:13px;
}

.field label{
  display:block;
  margin-bottom:7px;
  color:#a2a6ad;
  font-size:11px;
  font-weight:700;
}

.field input,
.field textarea,
.field select{
  width:100%;
  padding:13px;
  border:1px solid rgba(255,255,255,.09);
  border-radius:14px;
  outline:none;
  background:rgba(255,255,255,.055);
  color:#fff;
}

.field textarea{
  min-height:80px;
  resize:vertical;
}

.field select option{
  background:#111315;
}

.submit{
  width:100%;
  padding:14px;
  border:0;
  border-radius:15px;
  background:linear-gradient(135deg,#fff,#c9fff1);
  color:#000;
  font-weight:900;
}

.profilePreview{
  width:80px;
  height:80px;
  margin:0 auto 15px;
  border-radius:24px;
  object-fit:cover;
  display:block;
  background:linear-gradient(135deg,#19ffb0,#158cff);
}

/* MOBILE */
@media(max-width:850px){
  .games{
    grid-template-columns:repeat(2,1fr);
  }
}

@media(max-width:600px){
  .header{
    top:8px;
    margin-top:8px;
  }

  .brandName{
    font-size:14px;
  }

  .logo,
  .logoImg{
    width:38px;
    height:38px;
  }

  .header .btn{
    padding:9px 10px;
    font-size:11px;
  }

  .hero{
    padding-top:60px;
  }

  .hero h1{
    letter-spacing:-2px;
  }

  .games{
    grid-template-columns:1fr;
  }

  .adminPanel.show{
    align-items:flex-start;
    flex-direction:column;
  }
}
</style>
</head>

<body>

<header class="header">
  <div class="brand">
    <div class="logo" id="logoText">V</div>
    <img class="logoImg" id="logoImg">
    <div class="brandName" id="brandName">VIP GAME</div>
  </div>

  <div class="headerBtns">
    <button class="btn" id="loginBtn" onclick="openModal('loginModal')">
      🔐 Admin
    </button>

    <button class="btn redBtn" id="logoutBtn"
      style="display:none"
      onclick="logout()">
      Logout
    </button>
  </div>
</header>

<main class="container">

  <section class="hero">
    <h1 id="heroTitle">VIP GAME</h1>

    <p id="heroBio">
      Discover your next favorite game.
    </p>

    <div class="heroCreator" id="heroCreator">
      VIP|•KIRA
    </div>
  </section>

  <section class="adminPanel" id="adminPanel">
    <div>
      <div class="adminText">✓ Admin Mode Active</div>
      <div style="color:#6f747b;font-size:11px;margin-top:5px">
        You can manage games and profile.
      </div>
    </div>

    <div style="display:flex;gap:8px">
      <button class="btn" onclick="openModal('addModal')">
        ＋ Add Game
      </button>

      <button class="btn" onclick="openProfile()">
        ✎ Edit Profile
      </button>
    </div>
  </section>

  <section class="searchBox">
    <input
      type="text"
      id="search"
      placeholder="Search games..."
      oninput="showGames()"
    >
  </section>

  <div class="categories">
    <button class="category active" onclick="setCategory('all',this)">
      All
    </button>

    <button class="category" onclick="setCategory('Android',this)">
      Android
    </button>

    <button class="category" onclick="setCategory('PC',this)">
      PC
    </button>

    <button class="category" onclick="setCategory('Action',this)">
      Action
    </button>

    <button class="category" onclick="setCategory('Racing',this)">
      Racing
    </button>
  </div>

  <div class="sectionTitle">
    <h2>Games</h2>
    <span id="gameCount">0 Games</span>
  </div>

  <section class="games" id="games"></section>

</main>

<footer>
  <div>© 2026 <span id="footerName">VIP GAME</span></div>
  <div class="footerCreator">
    Creator — <span id="footerCreator">VIP|•KIRA</span>
  </div>

  <div id="telegramFooter" style="margin-top:12px"></div>
</footer>


<!-- LOGIN MODAL -->
<div class="modal" id="loginModal">
  <div class="modalBox">

    <div class="modalHead">
      <h3>Admin Login</h3>
      <button class="close" onclick="closeModal('loginModal')">×</button>
    </div>

    <div class="field">
      <label>Username</label>
      <input id="loginUser" type="text" placeholder="Username">
    </div>

    <div class="field">
      <label>Password</label>
      <input id="loginPass" type="password" placeholder="Password">
    </div>

    <button class="submit" onclick="login()">
      Login
    </button>

  </div>
</div>


<!-- ADD GAME MODAL -->
<div class="modal" id="addModal">
  <div class="modalBox">

    <div class="modalHead">
      <h3>Add Game</h3>
      <button class="close" onclick="closeModal('addModal')">×</button>
    </div>

    <div class="field">
      <label>Game Name</label>
      <input id="gameName" type="text" placeholder="Game name">
    </div>

    <div class="field">
      <label>Description</label>
      <textarea id="gameDesc"
        placeholder="Game description"></textarea>
    </div>

    <div class="field">
      <label>Size</label>
      <input id="gameSize" type="text" placeholder="Example: 1.5 GB">
    </div>

    <div class="field">
      <label>Category</label>

      <select id="gameCategory">
        <option>Android</option>
        <option>PC</option>
        <option>Action</option>
        <option>Racing</option>
      </select>
    </div>

    <div class="field">
      <label>Download Link</label>
      <input id="gameLink"
        type="url"
        placeholder="https://...">
    </div>

    <div class="field">
      <label>Game Image</label>
      <input
        id="gameImage"
        type="file"
        accept="image/*"
        onchange="previewGameImage(event)"
      >
    </div>

    <div id="gameImagePreview"
      style="display:none;margin-bottom:14px">
      <img
        id="gamePreviewImg"
        style="
          width:100%;
          max-height:180px;
          object-fit:cover;
          border-radius:17px;
        "
      >
    </div>

    <button class="submit" onclick="addGame()">
      ＋ Publish Game
    </button>

  </div>
</div>


<!-- PROFILE MODAL -->
<div class="modal" id="profileModal">
  <div class="modalBox">

    <div class="modalHead">
      <h3>Edit Profile</h3>
      <button class="close" onclick="closeModal('profileModal')">
        ×
      </button>
    </div>

    <img
      class="profilePreview"
      id="profilePreview"
      src=""
    >

    <div class="field">
      <label>Website / Profile Name</label>
      <input id="profileName">
    </div>

    <div class="field">
      <label>Hero Title</label>
      <input id="profileHero">
    </div>

    <div class="field">
      <label>Bio / Description</label>
      <textarea id="profileBio"></textarea>
    </div>

    <div class="field">
      <label>Creator</label>
      <input id="profileCreator">
    </div>

    <div class="field">
      <label>Telegram Link</label>
      <input id="profileTelegram"
        type="url"
        placeholder="https://t.me/...">
    </div>

    <div class="field">
      <label>Profile Logo / Image</label>
      <input
        id="profileImage"
        type="file"
        accept="image/*"
        onchange="previewProfile(event)"
      >
    </div>

    <button class="submit" onclick="saveProfile()">
      Save Profile
    </button>

  </div>
</div>


<script>

const ADMIN_USERNAME = "Vip Game members";
const ADMIN_PASSWORD = "2864981";

let isAdmin = false;
let selectedCategory = "all";

let gameImageData = "";
let profileImageData = "";

const defaultProfile = {
  name:"VIP GAME",
  hero:"VIP GAME",
  bio:"Discover your next favorite game.",
  creator:"VIP|•KIRA",
  telegram:"",
  image:""
};

let profile =
  JSON.parse(localStorage.getItem("vipProfile")) ||
  {...defaultProfile};

let games =
  JSON.parse(localStorage.getItem("vipGames")) ||
  [];


/* =========================
   MODAL
========================= */

function openModal(id){
  document.getElementById(id).classList.add("show");
}

function closeModal(id){
  document.getElementById(id).classList.remove("show");
}


/* =========================
   ADMIN LOGIN
========================= */

function login(){

  const user =
    document.getElementById("loginUser").value.trim();

  const pass =
    document.getElementById("loginPass").value;

  if(user === ADMIN_USERNAME &&
     pass === ADMIN_PASSWORD){

    isAdmin = true;

    closeModal("loginModal");

    document.getElementById("loginBtn")
      .style.display = "none";

    document.getElementById("logoutBtn")
      .style.display = "block";

    document.getElementById("adminPanel")
      .classList.add("show");

    alert("Admin login successful.");

    showGames();

  }else{

    alert("Wrong username or password.");

  }
}


function logout(){

  isAdmin = false;

  document.getElementById("loginBtn")
    .style.display = "block";

  document.getElementById("logoutBtn")
    .style.display = "none";

  document.getElementById("adminPanel")
    .classList.remove("show");

  showGames();
}


/* =========================
   IMAGE PREVIEW
========================= */

function previewGameImage(event){

  const file = event.target.files[0];

  if(!file) return;

  const reader = new FileReader();

  reader.onload = function(e){

    gameImageData = e.target.result;

    document.getElementById("gamePreviewImg")
      .src = gameImageData;

    document.getElementById("gameImagePreview")
      .style.display = "block";

  };

  reader.readAsDataURL(file);
}


function previewProfile(event){

  const file = event.target.files[0];

  if(!file) return;

  const reader = new FileReader();

  reader.onload = function(e){

    profileImageData = e.target.result;

    document.getElementById("profilePreview")
      .src = profileImageData;

  };

  reader.readAsDataURL(file);
}


/* =========================
   ADD GAME
========================= */

function addGame(){

  if(!isAdmin){

    alert("Admin only.");
    return;

  }

  const name =
    document.getElementById("gameName")
    .value.trim();

  const desc =
    document.getElementById("gameDesc")
    .value.trim();

  const size =
    document.getElementById("gameSize")
    .value.trim();

  const category =
    document.getElementById("gameCategory")
    .value;

  const link =
    document.getElementById("gameLink")
    .value.trim();

  if(!name || !link){

    alert("Game Name and Download Link are required.");
    return;

  }


  /*
    IMPORTANT:
    The exact date/time is saved automatically
    when the game is published.
  */

  games.push({

    id:Date.now(),

    name:name,

    desc:desc || "No description.",

    size:size || "Unknown",

    category:category,

    link:link,

    image:gameImageData || "",

    date:new Date().toISOString()

  });


  localStorage.setItem(
    "vipGames",
    JSON.stringify(games)
  );


  document.getElementById("gameName").value = "";
  document.getElementById("gameDesc").value = "";
  document.getElementById("gameSize").value = "";
  document.getElementById("gameLink").value = "";

  document.getElementById("gameImage").value = "";

  document.getElementById("gameImagePreview")
    .style.display = "none";

  gameImageData = "";

  closeModal("addModal");

  showGames();

  alert("Game published successfully.");

}


/* =========================
   DATE FORMAT
========================= */

function formatPostDate(value){

  if(!value){

    return "Date not available";

  }

  const date = new Date(value);

  if(isNaN(date.getTime())){

    return "Date not available";

  }

  return date.toLocaleString([],{

    year:"numeric",

    month:"short",

    day:"numeric",

    hour:"numeric",

    minute:"2-digit"

  });

}


/* =========================
   SHOW GAMES
========================= */

function showGames(){

  const container =
    document.getElementById("games");

  const search =
    document.getElementById("search")
    .value
    .toLowerCase()
    .trim();


  /*
    Filter first, then sort by post date.
    Newest game = top.
  */

  const filtered = games

    .filter(game => {

      const categoryMatch =
        selectedCategory === "all" ||
        game.category === selectedCategory;

      const searchMatch =
        !search ||
        game.name.toLowerCase().includes(search) ||
        (game.desc || "")
          .toLowerCase()
          .includes(search);

      return categoryMatch && searchMatch;

    })

    .sort((a,b)=>{

      const dateA =
        a.date
          ? new Date(a.date).getTime()
          : 0;

      const dateB =
        b.date
          ? new Date(b.date).getTime()
          : 0;

      return dateB - dateA;

    });


  document.getElementById("gameCount")
    .textContent =
    filtered.length +
    (filtered.length === 1 ? " Game" : " Games");


  if(filtered.length === 0){

    container.innerHTML = `
      <div class="empty">
        No games found.
      </div>
    `;

    return;

  }


  container.innerHTML = filtered.map(game => `

    <article class="game">

      <div class="gameImageWrap">

        <img
          class="gameImage"
          src="${game.image || placeholder()}"
          alt="${esc(game.name)}"
        >

        <div class="gameCategory">
          ${esc(game.category)}
        </div>

      </div>


      <div class="gameBody">

        <div class="gameName">
          ${esc(game.name)}
        </div>


        <div class="gameDesc">
          ${esc(game.desc)}
        </div>


        <div class="tags">

          <span class="tag">
            📦 ${esc(game.size)}
          </span>

          <span class="tag">
            🎮 ${esc(game.category)}
          </span>

        
