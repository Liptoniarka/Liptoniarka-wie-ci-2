<!DOCTYPE html>
<html>

<html>
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>liptoniarka</title>

  <style>
    body{
  margin:0;
  font-family:"Quicksand",sans-serif;
  background:linear-gradient(135deg,#fffde7,#fff9c4);
}

body::before{
  content:"";
  position:fixed;
  inset:0;
  background-image:radial-gradient(#fff 1px,transparent 2px);
  background-size:20px 20px;
  opacity:0.12;
  pointer-events:none;
}

.topbar{
  display:flex;
  justify-content:center;
  gap:10px;
  padding:10px;
  background:white;
  position:sticky;
  top:0;
}

button{
  border:none;
  padding:10px;
  border-radius:10px;
  background:#ffd54f;
  cursor:pointer;
}

.main{
  max-width:800px;
  margin:auto;
  padding:20px;
}

.section{display:none;}
.active{display:block;}

.post{
  background:white;
  padding:15px;
  margin-bottom:15px;
  border-radius:15px;
}

.content{display:none;}

.comment{
  background:#eee;
  padding:6px;
  margin-top:5px;
  border-radius:8px;
}

.footerbar{
  position:fixed;
  bottom:0;
  width:100%;
  text-align:center;
  background:white;
  padding:10px;
}
/* ✨ animowane tło */
body{
  animation: bgMove 12s ease-in-out infinite alternate;
}

@keyframes bgMove{
  0%{
    background: linear-gradient(135deg,#fffde7,#fff9c4);
  }
  100%{
    background: linear-gradient(135deg,#fff9c4,#ffe0b2);
  }
}

/* 🌸 lekkie "pływanie" postów */
.post{
  transition:0.3s;
}
.ramka button{
  margin-top:10px;
  padding:8px 12px;
  border:none;
  border-radius:10px;
  background:#ffd54f;
  cursor:pointer;
  transition:0.3s;
}

.ramka button:hover{
  box-shadow:0 0 10px rgba(255,213,79,0.7);
}
function show(id){
  document.querySelectorAll(".section").forEach(s=>s.classList.remove("active"));
  document.getElementById(id).classList.add("active");
}

function toggleBox(id){
  const el=document.getElementById(id);
  el.style.display = el.style.display === "block" ? "none" : "block";
}

/* ❤️ like */
function like(btn){
  if(!btn.dataset.liked){
    btn.innerHTML="❤️ liked";
    btn.dataset.liked="true";
  } else {
    btn.innerHTML="❤️ like";
    btn.dataset.liked="";
  }
}

/* 💬 komentarze */
function addComment(btn){
  const post = btn.closest(".content");
  const input = post.querySelector("input");
  const box = post.querySelector(".comments");

  if(!input.value.trim()) return;

  const c=document.createElement("div");
  c.className="comment";
  c.textContent=input.value;

  box.appendChild(c);
  input.value="";
}

/* ➕ nowy post */
function addPost(){
  const title=document.getElementById("title").value;
  const text=document.getElementById("text").value;

  const post=document.createElement("div");
  post.className="post ramka";

  post.innerHTML=`
    <h3 onclick="toggleBox(this.nextElementSibling.id)" class="toggle">${title}</h3>

    <div class="content" style="display:block">
      <p>${text}</p>

      <button onclick="like(this)">❤️ like</button>

      <div class="comments"></div>
      <input placeholder="napisz komentarz">
      <button onclick="addComment(this)">dodaj</button>
    </div>
  `;

  document.getElementById("posts").prepend(post);
}

<style>
.content{
  display:none;
}

.content.active{
  display:block;
}

.comment{
  font-size:14px;
  margin-top:5px;
  padding:4px;
  background:#f3f3f3;
  border-radius:6px;
}
</style>
  </style>

  
</head>
<body>
  <div class="topbar"> <button onclick="show('blog')">📸 Blog</button> <button onclick="show('about')">🍃 O mnie</button> <button onclick="show('contact')">📩 Kontakt</button> </div> <div class="main"> <!-- BLOG --> <div id="blog" class="section active"> <!-- 🔥 DODAWANIE POSTÓW NA GÓRZE --> <div class="post ramka"> <h3>➕ dodaj post</h3> <input id="title" placeholder="tytuł" /> <textarea id="text" placeholder="treść"></textarea> <input type="file" id="img" accept="image/*" /> <button onclick="addPost()">📤 dodaj</button> </div> <!-- 📸 LEKCJA FOTOGRAFII --> <div class="post ramka"> <h3 onclick="toggleBox('lekcja')" class="toggle"> 🌸 lekcja fotografii (kliknij) </h3> <div id="lekcja" class="content"> <p> Po informatyce mieliśmy 2 godziny PF 🎓📷 Na początku było omówienie sprzętu i światła.<br><br> Potem wyszliśmy na zewnątrz 🌲 i robiliśmy zdjęcia w grupach.<br><br> Używaliśmy dyfuzora elipsy 100x150 cm 🤍✨ i złotej folii 💛 dzięki czemu światło było cieplejsze 🌟<br><br> Robiłam po 2 zdjęcia 📸📸 i było super kreatywnie ✨🌿<br><br> 17.04.2026 </p> <button onclick="like(this)">❤️ like</button> <div class="comments"></div> <input placeholder="napisz komentarz"> <button onclick="addComment(this)">dodaj</button> </div> </div> <!-- 🍋 HEJKA --> <div class="post ramka"> <h3 onclick="toggleBox('hejka')" class="toggle"> 🍋🤍 hejka czesc (kliknij) 🍂🤎 </h3> <div id="hejka" class="content"> <p> znacie mnie jako Liptoniarka 🍋 (albo juannju ktokojarzy niech napisze 🤍)<br> prowadzę yt i tt 🎥<br> mam chomika i kota 🐹🐈<br> lubie spokojne dni 🌿✨<br> 16.04.2026 </p> <button onclick="like(this)">❤️ like</button> <div class="comments"></div> <input placeholder="napisz komentarz"> <button onclick="addComment(this)">dodaj</button> </div> </div> <!-- 📦 POSTY --> <div id="posts"></div> </div> <!-- ABOUT --> <div id="about" class="section"> <div class="post ramka"> <h2>🍃 o mnie</h2> <p> jestem Liptoniarka 🌿<br>Lubię pianino 🎹 i fotografię 📸<br>  rówiez herbatę(czarną) 🍵🤎<br>Mam  chomika i kota 🐹🐈. Uczę się od 7 klasy hiszpanskiego i robie duolingo! </p> </div> </div> <!-- CONTACT --> <div id="contact" class="section"> <div class="post ramka"> <h2>📩 kontakt</h2> <p> IG: liptoniarka123<br> TT: liptoniarka123<br> YT: liptoniarka </p> </div> </div> </div> <div class="footerbar"> ✨ ✨ Liptoniarka • aesthetic blog ✨
</div>
<script>
function show(id){
  document.querySelectorAll(".section").forEach(s=>{
    s.classList.remove("active");
  });

  document.getElementById(id).classList.add("active");
}

function toggleBox(id){
  const el=document.getElementById(id);
  el.style.display = el.style.display === "block" ? "none" : "block";
}

function like(btn){
  if(!btn.dataset.liked){
    btn.innerHTML="❤️ liked";
    btn.dataset.liked="true";
  } else {
    btn.innerHTML="❤️ like";
    btn.dataset.liked="";
  }
}

function addComment(btn){
  const post = btn.closest(".content");
  const input = post.querySelector("input");
  const box = post.querySelector(".comments");

  if(!input.value.trim()) return;

  const c=document.createElement("div");
  c.className="comment";
  c.textContent=input.value;

  box.appendChild(c);
  input.value="";
}

function addPost(){
  const title=document.getElementById("title").value;
  const text=document.getElementById("text").value;

  const post=document.createElement("div");
  post.className="post ramka";

  post.innerHTML=`
    <h3 class="toggle">${title}</h3>

    <div class="content" style="display:block">
      <p>${text}</p>

      <button onclick="like(this)">❤️ like</button>

      <div class="comments"></div>
      <input placeholder="napisz komentarz">
      <button onclick="addComment(this)">dodaj</button>
    </div>
  `;

  document.getElementById("posts").prepend(post);
}
</script>



  <script>
    function show(id){
  document.querySelectorAll('.section').forEach(s=>s.classList.remove('active'));
  document.getElementById(id).classList.add('active');
}

function toggleHome(){
  const el=document.getElementById('homeContent');
  el.style.display = el.style.display === 'block' ? 'none' : 'block';
}

function toggleLesson(){
  const el=document.getElementById('lesson');
  el.style.display = el.style.display === 'block' ? 'none' : 'block';
}

function addPost(){
  const title=document.getElementById('title').value;
  const text=document.getElementById('text').value;

  const post=document.createElement('div');
  post.className='post';
  post.innerHTML=`<h3>${title}</h3><p>${text}</p>`;

  document.getElementById('posts').prepend(post);
}

function addComment(btn){
  const post=btn.closest('.post');
  const input=post.querySelector('input');
  const box=post.querySelector('.comments');

  if(!input.value.trim()) return;

  const c=document.createElement('div');
  c.className='comment';
  c.textContent=input.value;

  box.appendChild(c);
  input.value="";
}
const el = document.getElementById("tekstRamki");
  const random = teksty[Math.floor(Math.random() * teksty.length)];

  el.textContent = random
.ramka{
  background:white;
  padding:15px;
  margin-bottom:15px;
  border-radius:15px;
  box-shadow:0 10px 25px rgba(0,0,0,0.1);
}

.content{
  display:none;
}

.comment{
  background:#eee;
  padding:6px;
  margin-top:5px;
  border-radius:8px;
}

.toggle{
  cursor:pointer;
}
  </script>
</body>
</html>
