<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>VIP GAME</title><style>
*{
box-sizing:border-box;
margin:0;
padding:0;
}

body{
font-family:Arial,sans-serif;
background:#070b10;
color:white;
min-height:100vh;
}

header{
position:sticky;
top:0;
z-index:100;
height:58px;
display:flex;
align-items:center;
justify-content:space-between;
padding:0 13px;
background:rgba(8,13,19,.94);
backdrop-filter:blur(18px);
border-bottom:1px solid #202c36;
}

.logo{
font-size:18px;
font-weight:800;
color:#48ff9b;
}

button{
border:0;
border-radius:9px;
padding:8px 12px;
background:#17222d;
color:white;
font-size:12px;
cursor:pointer;
}

.hero{
text-align:center;
padding:30px 10px 18px;
}

.hero h1{
font-size:28px;
margin-bottom:7px;
}

.hero h1 span{
color:#48ff9b;
}

.hero p{
font-size:12px;
color:#82909c;
}

.container{
width:100%;
max-width:950px;
margin:auto;
padding:10px;
}

.search-box{
display:flex;
justify-content:center;
margin-bottom:11px;
}

.search{
width:60%;
max-width:340px;
min-width:175px;
height:39px;
padding:0 13px;
border-radius:11px;
border:1px solid #263540;
background:#101820;
color:white;
outline:none;
font-size:12px;
}

.categories{
display:flex;
justify-content:center;
gap:5px;
overflow-x:auto;
padding-bottom:12px;
scrollbar-width:none;
}

.categories::-webkit-scrollbar{
display:none;
}

.categories button{
white-space:nowrap;
font-size:11px;
padding:7px 10px;
}

.categories .active{
background:#48ff9b;
color:#06110b;
}

.admin{
display:none;
justify-content:center;
gap:6px;
margin-bottom:11px;
flex-wrap:wrap;
}

.games{
display:grid;
grid-template-columns:repeat(2,1fr);
gap:9px;
}

.card{
overflow:hidden;
border:1px solid #24333f;
border-radius:14px;
background:#111a23;
}

.card img{
width:100%;
height:105px;
object-fit:cover;
display:block;
background:#0c131a;
}

.card-content{
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
font-size:10px;
line-height:1.4;
color:#9ba8b3;
margin-bottom:4px;
}

.date{
font-size:8px;
color:#657582;
margin:7px 0;
}

.download{
width:100%;
background:#48ff9b;
color:#06110b;
font-weight:bold;
font-size:11px;
}

.delete{
width:100%;
margin-top:5px;
background:#4b222a;
font-size:10px;
}

.modal{
display:none;
position:fixed;
inset:0;
z-index:200;
padding:15px;
background:rgba(0,0,0,.78);
backdrop-filter:blur(8px);
overflow:auto;
}

.modal-box{
width:100%;
max-width:430px;
margin:35px auto;
padding:18px;
border-radius:18px;
border:1px solid #293946;
background:#111a23;
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
color:white;
outline:none;
font-size:12px;
}

textarea{
min-height:75px;
resize:vertical;
}

.save{
width:100%;
margin-top:8px;
padding:10px;
background:#48ff9b;
color:#06110b;
font-weight:bold;
}

footer{
text-align:center;
padding:28px 10px;
font-size:10px;
color:#71808d;
}

footer a{
color:#48ff9b;
text-decoration:none;
}

@media(max-width:380px){

.search{
width:58%;
min-width:165px;
}

.card img{
height:90px;
}

.hero h1{
font-size:25px;
}
}

@media(min-width:700px){

.games{
grid-template-columns:repeat(3,1fr);
}

.search{
width:40%;
}
}
</style></head><body><header>
<div class="logo" id="logo">VIP GAME</div>
<button onclick="openModal('loginModal')">Admin</button>
</header><section class="hero">
<h1 id="heroTitle">Welcome to <span>VIP GAME</span></h1>
<p id="heroBio">Discover • Download • Play</p>
</section><main class="container"><div class="admin" id="adminPanel">
<button onclick="openModal('gameModal')">＋ Add Game</button>
<button onclick="openProfile()">✎ Profile</button>
<button onclick="logout()">Logout</button>
</div><div class="search-box">
<input
class="search"
id="search"
type="text"
placeholder="🔎 Search games..."
oninput="showGames()">
</div><div class="categories">
<button class="active" onclick="category('All',this)">All</button>
<button onclick="category('Android',this)">Android</button>
<button onclick="category('PC',this)">PC</button>
<button onclick="category('Action',this)">Action</button>
<button onclick="category('Racing',this)">Racing</button>
</div><div class="games" id="games"></div></main><footer>
<p>© 2026 <span id="footerName">VIP GAME</span></p>
<p>Creator — <span id="creator">VIP|•KIRA</span></p>
<p id="telegram"></p>
</footer><div class="modal" id="loginModal">
<div class="modal-box"><button class="close" onclick="closeModal('loginModal')">✕</button>

<h2>Admin Login</h2><input id="username" placeholder="Username"><input
id="password"
type="password"
placeholder="Password">

<button class="save" onclick="login()">Login</button>

</div>
</div><div class="modal" id="gameModal">
<div class="modal-box"><button class="close" onclick="closeModal('gameModal')">✕</button>

<h2>Add Game</h2><input id="gameName" placeholder="Game Name"><textarea
id="gameDescription"
placeholder="Game Description"></textarea><input
id="gameSize"
placeholder="Size e.g. 500 MB">

<select id="gameCategory">
<option value="Android">Android</option>
<option value="PC">PC</option>
<option value="Action">Action</option>
<option value="Racing">Racing</option>
</select><input
id="gameLink"
placeholder="Download Link">

<input
id="gameImage"
type="file"
accept="image/*">

<button class="save" onclick="addGame()">Add Game</button>

</div>
</div><div class="modal" id="profileModal">
<div class="modal-box"><button class="close" onclick="closeModal('profileModal')">✕</button>

<h2>Edit Profile</h2><input id="profileName" placeholder="Website Name"><input id="profileTitle" placeholder="Hero Title"><textarea id="profileBio" placeholder="Bio"></textarea><input id="profileCreator" placeholder="Creator"><input id="profileTelegram" placeholder="Telegram Link"><button class="save" onclick="saveProfile()">Save Profile</button>

</div>
</div><script>

const ADMIN_USER = "Vip Game members";
const ADMIN_PASS = "2864981";

let admin = false;
let currentCategory = "All";

let games = JSON.parse(
localStorage.getItem("vipGames") || "[]"
);

let profile = JSON.parse(
localStorage.getItem("vipProfile") ||
'{"name":"VIP GAME","title":"Welcome to VIP GAME","bio":"Discover • Download • Play","creator":"VIP|•KIRA","telegram":""}'
);


function saveGames(){
localStorage.setItem(
"vipGames",
JSON.stringify(games)
);
}


function escapeHTML(text){

return String(text || "")
.replaceAll("&","&amp;")
.replaceAll("<","&lt;")
.replaceAll(">","&gt;")
.replaceAll('"',"&quot;")
.replaceAll("'","&#039;");
}


function formatDate(date){

if(!date){
return "Date not available";
}

return new Date(date).toLocaleString([],{
month:"short",
day:"numeric",
year:"numeric",
hour:"numeric",
minute:"2-digit"
});
}


function showGames(){

const box=document.getElementById("games");

const search=
document.getElementById("search")
.value
.toLowerCase();

let list=[...games];

list.sort(
(a,b)=>
new Date(b.date || 0) -
new Date(a.date || 0)
);

list=list.filter(game=>{

const searchMatch=
game.name.toLowerCase().includes(search) ||
game.description.toLowerCase().includes(search);

const categoryMatch=
currentCategory==="All" ||
game.category===currentCategory;

return searchMatch && categoryMatch;

});

box.innerHTML="";

if(list.length===0){

box.innerHTML=
'<p style="color:#71808d;font-size:12px;padding:12px">No games found.</p>';

return;
}


list.forEach(game=>{

const card=document.createElement("div");

card.className="card";

card.innerHTML=`

<img src="${game.image || ""}" alt="">

<div class="card-content">

<h3>${escapeHTML(game.name)}</h3>

<p>${escapeHTML(game.description)}</p>

<p>📦 ${escapeHTML(game.size)}</p>

<p>🎮 ${escapeHTML(game.category)}</p>

<div class="date">
📅 Posted • ${formatDate(game.date)}
</div>

<a
href="${escapeHTML(game.link)}"
target="_blank"
rel="noopener">

<button class="download">
Download
</button>

</a>

${
admin
?
`<button class="delete" onclick="deleteGame('${game.id}')">Delete</button>`
:
""
}

</div>
`;

box.appendChild(card);

});

}


function category(name,button){

currentCategory=name;

document
.querySelectorAll(".categories button")
.forEach(b=>b.classList.remove("active"));

button.classList.add("active");

showGames();

}


function openModal(id){

document.getElementById(id).style.display="block";

}


function closeModal(id){

document.getElementById(id).style.display="none";

}


function login(){

const username=
document.getElementById("username").value;

const password=
document.getElementById("password").value;


if(
username===ADMIN_USER &&
password===ADMIN_PASS
){

admin=true;

document.getElementById("adminPanel")
.style.display="flex";

closeModal("loginModal");

showGames();

alert("Admin Login Successful ✅");

}else{

alert("Wrong username or password ❌");

}

}


function logout(){

admin=false;

document.getElementById("adminPanel")
.style.display="none";

showGames();

}


function addGame(){

if(!admin)return;


const name=
document.getElementById("gameName").value.trim();

const description=
document.getElementById("gameDescription").value.trim();

const size=
document.getElementById("gameSize").value.trim();

const categoryName=
document.getElementById("gameCategory").value;

const link=
document.getElementById("gameLink").value.trim();

const file=
document.getElementById("gameImage").files[0];


if(!name || !link){

alert("Game Name and Download Link are required.");

return;

}


function save(image){

games.push({

id:Date.now().toString(),

name:name,

description:description,

size:size,

category:categoryName,

link:link,

image:image || "",

date:new Date().toISOString()

});

saveGames();

document.getElementById("gameName").value="";
document.getElementById("gameDescription").value="";
document.getElementById("gameSize").value="";
document.getElementById("gameLink").value="";
document.getElementById("gameImage").value="";

closeModal("gameModal");

showGames();

alert("Game Added Successfully 🎮");

}


if(file){

const reader=new FileReader();

reader.onload=function(e){

save(e.target.result);

};

reader.readAsDataURL(file);

}else{

save("");

}

}


function deleteGame(id){

if(!admin)return;

if(confirm("Delete this game?")){

games=
games.filter(game=>game.id!==id);

saveGames();

showGames();

}

}


function openProfile(){

if(!admin)return;


document.getElementById("profileName").value=
profile.name;

document.getElementById("profileTitle").value=
profile.title;

document.getElementById("profileBio").value=
profile.bio;

document.getElementById("profileCreator").value=
profile.creator;

document.getElementById("profileTelegram").value=
profile.telegram;


openModal("profileModal");

}


function saveProfile(){

if(!admin)return;


profile.name=
document.getElementById("profileName")
.value.trim() || "VIP GAME";

profile.title=
document.getElementById("profileTitle")
.value.trim() || "Welcome to VIP GAME";

profile.bio=
document.getElementById("profileBio")
.value.trim() || "Discover • Download • Play";

profile.creator=
document.getElementById("profileCreator")
.value.trim() || "VIP|•KIRA";

profile.telegram=
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

document.getElementById("logo")
.textContent=profile.name;

document.getElementById("heroTitle")
.textContent=profile.title;

document.getElementById("heroBio")
.textContent=profile.bio;

document.getElementById("footerName")
.textContent=profile.name;

document.getElementById("creator")
.textContent=profile.creator;


const telegram=
document.getElementById("telegram");


if(profile.telegram){

telegram.innerHTML=
`<a href="${escapeHTML(profile.telegram)}" target="_blank">Telegram</a>`;

}else{

telegram.innerHTML="";

}

}


window.onclick=function(event){

document
.querySelectorAll(".modal")
.forEach(modal=>{

if(event.target===modal){

modal.style.display="none";

}

});

};


applyProfile();

showGames();

</script></body>
</html>
