# Birtanemmm
<!DOCTYPE html><html lang="tr">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Birtanem İçin</title>  <style>
    body{
      margin:0;
      font-family:Arial,sans-serif;
      background:linear-gradient(135deg,#800020,#ff9a9e);
      color:white;
      text-align:center;
      overflow-x:hidden;
      transition:0.6s ease;
    }

    h1{
      margin-top:20px;
      font-size:2.8rem;
      animation: glow 2s infinite alternate;
    }

    @keyframes glow{
      from{ text-shadow:0 0 10px #fff; }
      to{ text-shadow:0 0 25px #ff4d6d; }
    }

    .card{
      background:rgba(255,255,255,0.15);
      backdrop-filter:blur(10px);
      border-radius:20px;
      padding:20px;
      margin:20px auto;
      max-width:500px;
      box-shadow:0 10px 25px rgba(0,0,0,0.2);
    }

    img{
      width:45%;
      border-radius:15px;
      margin-top:10px;
    }

    button{
      padding:10px 16px;
      border:none;
      border-radius:999px;
      cursor:pointer;
      font-weight:bold;
      margin:5px;
    }

    #counter{
      font-size:1.4rem;
      font-weight:bold;
    }

    .heart{
      position:fixed;
      top:100vh;
      color:white;
      animation:float 6s linear infinite;
      font-size:18px;
    }

    @keyframes float{
      0%{transform:translateY(0);opacity:1;}
      100%{transform:translateY(-120vh);opacity:0;}
    }

    .player{
      display:flex;
      flex-direction:column;
      gap:10px;
      align-items:center;
    }

    .bar{
      width:80%;
      height:6px;
      background:#ffffff55;
      border-radius:10px;
      overflow:hidden;
    }

    .progress{
      height:100%;
      width:0%;
      background:#fff;
    }

  </style></head><body><h1>Birtanem ❤️</h1><div class="card">
  <h2>Bizim Hikayemiz</h2>
  <p>28 Mart 23:17 ❤️</p>
</div><div class="card">
  <h2>Ne Kadar Oldu?</h2>
  <p id="counter"></p>
</div><div class="card">
  <h2>📸</h2>
  <img src="https://i.imgur.com/ZMtIWnY.jpeg" alt="Bizim fotoğrafımız" class="heart-frame" width="300">
</div><style>
.heart-frame{
  border-radius:20px;
  border:3px solid #ff4d6d;
  box-shadow:0 0 20px #ff4d6d;
  padding:5px;
  background:white;
}
</style><div class="card">
  <button onclick="mesaj()">Tıkla 💬</button>
  <p id="msg"></p>
</div><div class="card">
  <h2>Spotify Tarzı Müzik 🎵</h2>  <div class="player">
    <div id="songName">Şarkı 1</div><div class="bar">
  <div class="progress" id="progress"></div>
</div>

<div>
  <button onclick="playPause()">▶️ / ⏸</button>
  <button onclick="nextSong()">⏭</button>
</div>

  </div>
</div><audio id="music"></audio>

<script>
let songs=[
  {name:"Mey", artist:"", file:"sarki1.mp3", color:"#800020"},
  {name:"Toprak Yağmura", artist:"", file:"sarki2.mp3", color:"#ff4fa3"},
  {name:"Koca Yaşlı Şişko Dünya", artist:"", file:"sarki3.mp3", color:"#6a0dad"},
  {name:"Beni Al", artist:"", file:"sarki4.mp3", color:"#800020"},
  {name:"Neyin Nesi", artist:"", file:"sarki5.mp3", color:"#ff4fa3"},
  {name:"Aç Kapıyı Gir İçeri", artist:"", file:"sarki6.mp3", color:"#6a0dad"},
  {name:"İmkansızım", artist:"", file:"sarki7.mp3", color:"#800020"},
  {name:"Köprü Altı", artist:"", file:"sarki8.mp3", color:"#ff4fa3"},
  {name:"Benimki", artist:"", file:"sarki9.mp3", color:"#6a0dad"},
  {name:"Elleri Ellerime", artist:"", file:"sarki10.mp3", color:"#800020"},
  {name:"Plüton", artist:"", file:"sarki11.mp3", color:"#ff4fa3"}
];

let index=0;
let music=document.getElementById("music");
let isPlaying=false;

function setTheme(i){
  document.body.style.background="linear-gradient(135deg,"+songs[i].color+",#222)";
}

function loadSong(){
  music.src=songs[index].file;
  document.getElementById("songName").innerText=songs[index].name + (songs[index].artist ? " - " + songs[index].artist : "");
  setTheme(index);
  music.load();
  if(isPlaying) music.play();
}

function playPause(){
  if(music.paused){
    music.play();
    isPlaying=true;
  }else{
    music.pause();
    isPlaying=false;
  }
}

function nextSong(){
  index=(index+1)%songs.length;
  loadSong();
}

music.ontimeupdate=function(){
  let p=(music.currentTime/music.duration)*100;
  document.getElementById("progress").style.width=p+"%";
};

loadSong();

function mesaj(){
  const msgs=[
    "İyi ki varsın ❤️",
    "Seni her gün daha çok seviyorum",
    "Sen benim en güzel tesadüfümsün",
    "Uzak olsak da kalbim hep seninle",
    "Birtanem ❤️",
    "Gülüşün her şeye değer",
    "Sen benim huzurumsun",
    "İyi ki karşıma çıktın",
    "Sonsuza kadar sen",
    "Sen benim en özelimsin",
    "Her şeyim sensin"
  ];
  document.getElementById("msg").innerText = msgs[Math.floor(Math.random()*msgs.length)];
}

function counter(){
  const start=new Date("2026-03-28T23:17:00");
  const now=new Date();
  const diff=now-start;

  const d=Math.floor(diff/86400000);
  const h=Math.floor((diff/3600000)%24);
  const m=Math.floor((diff/60000)%60);
  const s=Math.floor((diff/1000)%60);

  document.getElementById("counter").innerText=
    d+" gün "+h+" saat "+m+" dakika "+s+" saniye ❤️";
}
setInterval(counter,1000);
counter();

function heart(){
  const h=document.createElement("div");
  h.className="heart";
  h.innerHTML="❤️";
  h.style.left=Math.random()*100+"vw";
  h.style.fontSize=(Math.random()*20+10)+"px";
  document.body.appendChild(h);
  setTimeout(()=>h.remove(),6000);
}
setInterval(heart,300);
</script></body>
</html>
