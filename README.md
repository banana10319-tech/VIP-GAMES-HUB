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
  font-family:Arial,sans-serif;
  background:#070b10;
  color:#fff;
  min-height:100vh;
}

header{
  position:sticky;
  top:0;
  z-index:10;
  height:56px;
  padding:8px 12px;
  background:rgba(8,13,19,.9);
  backdrop-filter:blur(18px);
  border-bottom:1px solid #202c36;
  display:flex;
  align-items:center;
  justify-content:space-between;
}

.logo{
  font-size:18px;
  font-weight:800;
  color:#48ff9b;
}

button{
  border:0;
  border-radius:9px;
  padding:8px 11px;
  color:#fff;
  background:#17222d;
  cursor:pointer;
  font-size:12px;
}

.hero{
  text-align:center;
  padding:24px 10px 15px;
}

.hero h1{
  font-size:28px;
  margin-bottom:6px;
}

.hero h1 span{
  color:#48ff9b;
}

.hero p{
  color:#8795a1;
  font-size:12px;
}

.container{
  width:100%;
  max-width:900px;
  margin:auto;
  padding:10px;
}

/* SEARCH */
.search-wrap{
  display:flex;
  justify-content:center;
  width:100%;
  margin-bottom:10px;
}

.search{
  width:60%;
  max-width:350px;
  min-width:190px;
  height:38px;
  padding:0 13px;
  border-radius:10px;
  border:1px solid #263540;
  background:#101820;
  color:#fff;
  outline:none;
  font-size:12px;
}

.search::placeholder{
  color:#71808d;
}

/* CATEGORY */
.filters{
  display:flex;
  justify-content:center;
  gap:5px;
  overflow-x:auto;
  padding-bottom:10px;
  scrollbar-width:none;
}

.filters::-webkit-scrollbar{
  display:none;
}

.filters button{
  white-space:nowrap;
  padding:7px 10px;
  font-size:11px;
}

.filters button.active{
  background:#48ff9b;
  color:#06110b;
}

/* ADMIN */
.admin-panel{
  display:none;
  justify-content:center;
  flex-wrap:wrap;
  gap:5px;
  margin-bottom:10px;
}

.admin-panel button{
  font-size:11px;
  padding:7px 9px;
}

/* GAME GRID */
.games{
  display:grid;
  grid-template-columns:repeat(2,minmax(0,1fr));
  gap:9px;
}

.card{
  background:#111a23;
  border:1px solid #24333f;
  border-radius:14px;
  overflow:hidden;
}

.card img{
  width:100%;
  height:105px;
  object-fit:cover;
  background:#0c131a;
}

.card-body{
  padding:9px;
}

.card h3{
  font-size:14px;
  margin-bottom:5px;
  white-space:nowrap;
  overflow:hidden;
  text-overflow:ellipsis;
}

.card p{
  color:#9ba8b3;
  font-size:10px;
  line-height:1.35;
  margin-bottom:4px;
}

.meta{
  color:#697986;
  font-size:8px;
  margin:6px 0;
}

.download{
  display:block;
  width:100%;
  padding:8px;
  background:#48ff9b;
  color:#06110b;
  font-weight:bold;
  font-size:11px;
}

.delete{
  width:100%;
  margin-top:5px;
  padding:7px;
  background:#49232b;
  font-size:10px;
}

/* MODAL */
.modal{
  display:none;
  position:fixed;
  inset:0;
  z-index:50;
  padding:15px;
  background:rgba(0,0,0,.75);
  backdrop-filter:blur(8px);
  overflow:auto;
}

.modal-box{
  width:100%;
  max-width:430px;
  margin:35px auto;
  padding:17px;
  background:#111a23;
  border:1px solid #293946;
  border-radius:18px;
}

.modal-box h2{
  font-size:19px;
  margin-bottom:12px;
}

.close{
  float:right;
  padding:6px 9px;
}

input,
textarea,
select{
  width:100%;
  padding:10px;
  margin:5px 0;
  border-radius:9px;
  border:1px solid #293946;
  background:#0a1118;
  color:#fff;
  outline:none;
  font-size:12px;
}

textarea{
  min-height:70px;
  resize:vertical;
}

.form-btn{
  width:100%;
  margin-top:8px;
  padding:10px;
  background:#48ff9b;
  color:#06110b;
  font-weight:bold;
}

/* FOOTER */
footer{
  text-align:center;
  padding:25px 10px;
  color:#71808d;
  font-size:10px;
}

footer a{
  color:#48ff9b;
  text-decoration:none;
}

/* MOBILE */
@media(max-width:380px){

  .search{
    width:58%;
    min-width:175px;
  }

  .games{
    gap:7px;
  }

  .card img{
    height:90px;
  }

  .card-body{
    padding:8px;
  }

  .card h3{
    font-size:13px;
  }

  .hero h1{
    font-size:25px;
  }
}

/* PC */
@media(min-width:700px){

  .games{
    grid-template-columns:repeat(3,minmax(0,1fr));
  }

  .search{
    width:40%;
  }
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
    <button onclick="openProfile()">✎ Profile</button>
    <button onclick="logout()">Logout</button>
  </div>

  <div class="search-wrap">
    <input
      id="search"
      class="search"
      type="text"
      placeholder="🔎 Search games..."
      oninput="showGames()"
    >
  </div>

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

    <textarea
      id="gameDesc"
      placeholder="Description"
    ></textarea>

    <input
      id="gameSize"
      placeholder="Size e.g. 500 MB"
    >

    <select id="gameCategory">
      <option>Android</option>
      <option>PC</option>
      <option>Action</option>
      <option>Racing</option>
    </select>

    <input
      id="gameLink"
      placeholder="Download Link"
    >

    <input
      id="gameImage"
      type="file"
      accept="image/*"
    >

    <button class="form-btn" onclick="addGame()">
      Save Game
    </button>

  </div>
</div>


<!-- PROFILE -->
<div id="profileModal" class="modal">
  <div class="modal-box">

    <button class="close" onclick="closeModal('profileModal')">✕</button>

    <h2>Edit Profile</h2>

    <input
      id="profileName"
      placeholder="Website Name"
    >

    <input
      id="profileTitle"
      placeholder="Hero Title"
    >

    <textarea
      id="profileBio"
      placeholder="Bio"
    ></textarea>

    <input
      id="profileCreator"
      placeholder="Creator"
    >

    <input
      id="profileTelegram"
      placeholder="Telegram Link"
    >

    <input
      id="profileImage"
      type="file"
      accept="image/*"
    >

    <button class="form-btn" onclick="saveProfile()">
      Save Profile
    </button>

  </div>
</div>


<script>

const ADMIN_USER = "Vip Game members";
const ADMIN_PASS = "2864981";

let isAdmin = false;
let currentCategory = "All";

let games =
  JSON.parse(localStorage.getItem("vipGames") || "[]");

let profile =
  JSON.parse(
    localStorage.getItem("vipProfile") ||
    '{"name":"VIP GAME","title":"Welcome to VIP GAME","bio":"Discover • Download • Play","creator":"VIP|•KIRA","telegram":""}'
  );


function saveGames(){
  localStorage.setItem(
    "vipGames",
    JSON.stringify(games)
  );
}


function formatPostDate(value){

  if(!value)
    return "Date not available";

  const d = new Date(value);

  return d.toLocaleString([],{
    month:"short",
    day:"numeric",
    year:"numeric",
    hour:"numeric",
    minute:"2-digit"
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

  return String(text || "")
    .replaceAll('"',"&quot;");
}


function showGames(){

  const box =
    document.getElementById("games");

  const search =
    document.getElementById("search")
    .value
    .toLowerCase();

  let list = [...games];

  list.sort((a,b)=>{
    return new Date(b.date || 0)
      - new Date(a.date || 0);
  });

  list = list.filter(game=>{

    const searchMatch =
      game.name.toLowerCase().includes(search) ||
      game.desc.toLowerCase().includes(search);

    const categoryMatch =
      currentCategory === "All" ||
      game.category === currentCategory;

    return searchMatch && categoryMatch;
  });

  box.innerHTML = "";

  if(list.length === 0){

    box.innerHTML =
      '<p style="color:#71808d;font-size:12px;padding:10px">No games found.</p>';

    return;
  }

  list.forEach(game=>{

    const card =
      document.createElement("div");

    card.className = "card";

    card.innerHTML = `

      <img
        src="${game.image || ''}"
        alt=""
      >

      <div class="card-body">

        <h3>
          ${escapeHTML(game.name)}
        </h3>

        <p>
          ${escapeHTML(game.desc)}
        </p>

        <p>
          📦 ${escapeHTML(game.size)}
        </p>

        <p>
          🎮 ${escapeHTML(game.category)}
        </p>

        <div class="meta">
          📅 Posted • ${formatPostDate(game.date)}
        </div>

        <a
          href="${escapeAttr(game.link)}"
          target="_blank"
        >
          <button class="download">
            Download
          </button>
        </a>

        ${
          isAdmin
          ?
          `<button
            class="delete"
            onclick="deleteGame('${game.id}')"
          >
            Delete
          </button>`
          :
          ""
        }

      </div>
    `;

    box.appendChild(card);

  });
}


function setCategory(category,button){

  currentCategory = category;

  document
    .querySelectorAll(".filters button")
    .forEach(b=>{
      b.classList.remove("active");
    });

  button.classList.add("active");

  showGames();
}


function openLogin(){

  document
    .getElementById("loginModal")
    .style.display = "block";
}


function login(){

  const u =
    document.getElementById("username").value;

  const p =
    document.getElementById("password").value;

  if(
    u === ADMIN_USER &&
    p === ADMIN_PASS
  ){

    isAdmin = true;

    closeModal("loginModal");

    document
      .getElementById("adminPanel")
      .style.display = "flex";

    showGames();

    alert("Admin Login Successful ✅");

  }else{

    alert("Wrong username or password ❌");

  }
}


function logout(){

  isAdmin = false;

  document
    .getElementById("adminPanel")
    .style.display = "none";

  showGames();
}


function openAddGame(){

  if(!isAdmin)
    return;

  document
    .getElementById("gameModal")
    .style.display = "block";
}


function addGame(){

  if(!isAdmin)
    return;

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

  const file =
    document.getElementById("gameImage")
    .files[0];

  if(!name || !link){

    alert(
      "Game Name and Download Link are required."
    );

    return;
  }

  const saveGame = imageData => {

    games.push({

      id:Date.now().toString(),

      name:name,

      desc:desc,

      size:size,

      category:category,

      link:link,

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

    const reader =
      new FileReader();

    reader.onload = e=>{
      saveGame(e.target.result);
    };

    reader.readAsDataURL(file);

  }else{

    saveGame("");

  }
}


function deleteGame(id){

  if(!isAdmin)
    return;

  if(
    confirm("Delete this game?")
  ){

    games =
      games.filter(
        g=>g.id !== id
      );

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

  if(!isAdmin)
    return;

  document.getElementById("profileName").value =
    profile.name;

  document.getElementById("profileTitle").value =
    profile.title;

  document.getElementById("profileBio").value =
    profile.bio;

  document.getElementById("profileCreator").value =
    profile.creator;

  document.getElementById("profileTelegram").value =
    profile.telegram;

  document
    .getElementById("profileModal")
    .style.display = "block";
}


function saveProfile(){

  if(!isAdmin)
    return;

  profile.name =
    document.getElementById("profileName")
    .value.trim()
    || "VIP GAME";

  profile.title =
    document.getElementById("profileTitle")
    .value.trim()
    || "Welcome to VIP GAME";

  profile.bio =
    document.getElementById("profileBio")
    .value.trim()
    || "Discover • Download • Play";

  profile.creator =
    document.getElementById("profileCreator")
    .value.trim()
    || "VIP|•KIRA";

  profile.telegram =
    document.getElementById("profileTelegram")
    .value.trim();

  localStorage.setItem(
    "vipProfile",
    JSON.stringify(profile)
  );

  applyProfile();

  closeModal("profileModal");

  alert("Profile Saved ✅");
}


function applyProfile(){

  document.getElementById("siteLogo")
    .textContent = profile.name;

  document.getElementById("heroTitle")
    .innerHTML =
    escapeHTML(profile.title)
    .replace(
      "VIP GAME",
      "<span>VIP GAME</span>"
    );

  document.getElementById("heroBio")
    .textContent = profile.bio;

  document.getElementById("footerName")
    .textContent = profile.name;

  document.getElementById("creator")
    .textContent = profile.creator;

  const tg =
    document.getElementById("telegramArea");

  if(profile.telegram){

    tg.innerHTML =
      `<a href="${escapeAttr(profile.telegram)}" target="_blank">Telegram</a>`;

  }else{

    tg.innerHTML = "";

  }
}


function closeModal(id){

  document
    .getElementById(id)
    .style.display = "none";
}


window.onclick = function(event){

  document
    .querySelectorAll(".modal")
    .forEach(modal=>{

      if(event.target === modal){

        modal.style.display = "none";

      }

    });

};


applyProfile();
showGames();

</script>

</body>
</html>
