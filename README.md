
<!DOCTYPE html>
<html lang="he" dir="rtl">
<head>
<meta charset="UTF-8">
<title>האחים מכונית 🚗💦</title>
<meta name="viewport" content="width=device-width, initial-scale=1">
<style>
body{
  font-family:Arial;
  margin:0;
  background:#f2f2f2;
}
header{
  background:#0a74da;
  color:white;
  padding:40px;
  text-align:center;
}
section{
  background:white;
  max-width:900px;
  margin:20px auto;
  padding:20px;
  border-radius:10px;
}
h2{color:#0a74da}

.rating-box{
  position:fixed;
  top:120px;
  right:20px;
  width:230px;
  background:white;
  padding:12px;
  border-radius:12px;
  box-shadow:0 0 10px rgba(0,0,0,0.2);
}
.stars span{
  font-size:24px;
  cursor:pointer;
  filter:grayscale(100%);
}
.stars span.active{filter:none}

.review{
  border-bottom:1px solid #eee;
  padding:8px 0;
}
</style>
</head>

<body>

<header>
<h1>האחים מכונית 🚗💦🧽</h1>
<p style="color:black;font-weight:bold;">
(🚗💦🧽 יהיו ימי שישי שלא תתקיים שטיפה בשל סיבות פרטיות – אנא הבינו זאת 🙂)
</p>
</header>

<div class="rating-box">
<h3>דרגו אותנו ⭐</h3>
<div class="stars">
<span data-v="1">⭐</span>
<span data-v="2">⭐</span>
<span data-v="3">⭐</span>
<span data-v="4">⭐</span>
<span data-v="5">⭐</span>
</div>
<input id="rname" placeholder="השם שלכם" style="width:100%;margin-top:5px">
<textarea id="rtext" placeholder="משוב קצר" style="width:100%;margin-top:5px"></textarea>
<button onclick="sendReview()" style="width:100%;margin-top:5px">שלח</button>

<h3>חוות דעת</h3>
<div id="reviews"></div>
</div>

<section>
<h2>מחירים</h2>
<ul>
<li>🚗 פנים + חוץ – 60 ₪</li>
<li>🚿 חוץ בלבד – 25 ₪</li>
<li>🧼 פנים בלבד – 35 ₪</li>
</ul>
</section>

<section>
<h2>זמן שטיפה</h2>
<ul>
<li>פנים + חוץ: 30–35 דק</li>
<li>חוץ בלבד: 15–20 דק</li>
<li>פנים בלבד: 20–25 דק</li>
</ul>
</section>

<section>
<h2>הזמנת תור</h2>
<p style="color:red;font-weight:bold">
(כשאתם מזמינים – לא רואים אם תפוס. תבחרו שעה ואנחנו נעדכן)
</p>

<form onsubmit="sendWA(event)">
<input required placeholder="שם מלא"><br><br>
<input required placeholder="טלפון"><br><br>
<select>
<option>פנים וחוץ</option>
<option>חוץ בלבד</option>
<option>פנים בלבד</option>
</select><br><br>
<select>
<option>09:00</option>
<option>09:35</option>
<option>10:10</option>
<option>10:45</option>
<option>11:20</option>
<option>11:55</option>
<option>12:30</option>
<option>13:05</option>
<option>13:40</option>
</select><br><br>
<button>שלח בוואטסאפ</button>
</form>
</section>

<script>
let rating=0;
document.querySelectorAll('.stars span').forEach((s,i)=>{
  s.onclick=()=>{
    rating=i+1;
    document.querySelectorAll('.stars span')
    .forEach((x,j)=>x.classList.toggle('active',j<=i));
  }
});

function sendReview(){
  if(!rating){alert('בחר כוכבים');return;}
  let name=rname.value||'אנונימי';
  let text=rtext.value||'—';
  let all=JSON.parse(localStorage.getItem('rev')||'[]');
  all.push({name,rating,text});
  localStorage.setItem('rev',JSON.stringify(all));
  rname.value='';rtext.value='';rating=0;
  document.querySelectorAll('.stars span').forEach(x=>x.classList.remove('active'));
  load();
}
function load(){
  reviews.innerHTML='';
  (JSON.parse(localStorage.getItem('rev')||'[]')).forEach(r=>{
    reviews.innerHTML+=<div class="review"><b>${r.name}</b><br>${'⭐'.repeat(r.rating)}<br>${r.text}</div>;
  });
}
load();

function sendWA(e){
  e.preventDefault();
  alert('נשלח לוואטסאפ (דוגמה)');
}
</script>

</body> אתה יכול להכין לי מהקוד הזה קישור  
