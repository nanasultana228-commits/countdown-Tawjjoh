# countdown-Tawjjoh
<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>العد التنازلي لتوجُّه</title>
<style>
:root{
  box-sizing:border-box;
  padding-top:env(safe-area-inset-top,0px);
  padding-bottom:env(safe-area-inset-bottom,0px);
  color-scheme:light;
  --bg:#ffffff;--card:#f1eafd;--text:#6d44b8;--muted:#8a78ad;--accent:#9b6fe0;--border:#ddd0f5;
}
html,body{height:100%;margin:0}
body{background:var(--bg);color:var(--text);font-family:"Segoe UI",Tahoma,"Noto Sans Arabic",Arial,sans-serif;display:flex;align-items:center;justify-content:center;padding:16px;box-sizing:border-box}
.wrap{width:100%;max-width:560px;text-align:center}
h1{font-size:clamp(28px,8vw,44px);margin:0 0 6px;color:var(--accent)}
p.sub{margin:0 0 28px;color:var(--muted);font-size:16px}
.grid{display:grid;grid-template-columns:repeat(4,1fr);gap:10px;direction:ltr}
.box{background:var(--card);border:1px solid var(--border);border-radius:16px;padding:18px 4px}
.num{font-size:clamp(28px,9vw,48px);font-weight:700;font-variant-numeric:tabular-nums}
.lbl{font-size:13px;color:var(--muted);margin-top:4px}
.done{display:none;font-size:28px;font-weight:700;color:var(--accent)}
.foot{margin-top:24px;color:var(--muted);font-size:14px}
</style>
</head>
<body>
<div class="wrap">
  <h1>توجُّه 🥳</h1>
  <p class="sub">انطلاق أقوى برنامج</p>
  <div class="grid" id="grid">
    <div class="box"><div class="num" id="d">0</div><div class="lbl">يوم</div></div>
    <div class="box"><div class="num" id="h">0</div><div class="lbl">ساعة</div></div>
    <div class="box"><div class="num" id="m">0</div><div class="lbl">دقيقة</div></div>
    <div class="box"><div class="num" id="s">0</div><div class="lbl">ثانية</div></div>
  </div>
  <div class="done" id="done">حان الوقت! 🎉</div>
  <div class="foot">29 نوفمبر 2026 – الساعة 6:00 مساءً بتوقيت السعودية</div>
</div>
<script>
var target = new Date("2026-11-29T18:00:00+03:00").getTime();
function pad(n){return String(n).padStart(2,"0");}
function tick(){
  var diff = target - Date.now();
  if(diff <= 0){
    document.getElementById("grid").style.display="none";
    document.getElementById("done").style.display="block";
    return;
  }
  var s = Math.floor(diff/1000);
  document.getElementById("d").textContent = Math.floor(s/86400);
  document.getElementById("h").textContent = pad(Math.floor(s%86400/3600));
  document.getElementById("m").textContent = pad(Math.floor(s%3600/60));
  document.getElementById("s").textContent = pad(s%60);
  setTimeout(tick, 1000);
}
tick();
</script>
</body>
</html>
