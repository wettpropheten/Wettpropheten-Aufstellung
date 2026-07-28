<!DOCTYPE html>
<html lang="de">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Wettpropheten Live Stats Pro</title>

<style>

*{
margin:0;
padding:0;
box-sizing:border-box;
font-family:Arial,Helvetica,sans-serif;
}

body{

background:#041822;
color:white;
padding:25px;

}

.container{

max-width:950px;
margin:auto;

}

/* ================= HEADER ================= */

.header{

background:#072534;
border-radius:15px;
padding:20px;
margin-bottom:25px;

display:flex;
justify-content:space-between;
align-items:center;

}

.team{

width:35%;
text-align:center;

}

.team h2{

font-size:28px;
font-weight:bold;

}

.score{

text-align:center;

}

.score h1{

font-size:55px;

}

.live{

margin-top:8px;

display:inline-block;

padding:6px 15px;

background:#e40046;

border-radius:30px;

font-size:14px;

font-weight:bold;

animation:pulse 1.2s infinite;

}

.minute{

margin-top:10px;
font-size:22px;

}

@keyframes pulse{

0%{opacity:.5;}
50%{opacity:1;}
100%{opacity:.5;}

}

/* ================= KATEGORIE ================= */

.category{

margin-top:25px;

background:#06202d;

padding:12px;

border-radius:8px;

text-align:center;

font-weight:bold;

text-transform:uppercase;

letter-spacing:1px;

color:#d5e9ff;

}

/* ================= STATISTIK ================= */

.stat{

padding:18px 0;

}

.stat-header{

display:flex;

justify-content:space-between;

font-weight:bold;

margin-bottom:10px;

}

.stat-title{

text-align:center;
flex:1;

}

/* ================= BALKEN ================= */

.bar{

height:10px;

background:#0d2d3b;

border-radius:20px;

overflow:hidden;

display:flex;

}

.homeBar{

background:#e40046;

width:50%;

transition:1s;

}

.awayBar{

background:#e5e5e5;

width:50%;

transition:1s;

}

/* ================= RESPONSIVE ================= */

@media(max-width:700px){

.header{

flex-direction:column;
gap:15px;

}

.team{

width:100%;

}

.score h1{

font-size:38px;

}

}

</style>

</head>

<body>

<div class="container">

<div class="header">

<div class="team">
<h2>FC Bayern</h2>
</div>

<div class="score">

<h1>1 : 0</h1>

<div class="live">
LIVE
</div>

<div class="minute">
58'
</div>

</div>

<div class="team">
<h2>Borussia Dortmund</h2>
</div>

</div>

<div class="category">
TOP-STATISTIKEN
</div>

<!-- Ballbesitz -->

<div class="stat">

<div class="stat-header">

<div>53%</div>

<div class="stat-title">
Ballbesitz
</div>

<div>47%</div>

</div>

<div class="bar">

<div class="homeBar" style="width:53%"></div>

<div class="awayBar" style="width:47%"></div>

</div>

</div>

<!-- Schüsse -->

<div class="stat">

<div class="stat-header">

<div>4</div>

<div class="stat-title">
Schüsse insgesamt
</div>

<div>3</div>

</div>

<div class="bar">

<div class="homeBar" style="width:57%"></div>

<div class="awayBar" style="width:43%"></div>

</div>

</div>

<!-- Schüsse aufs Tor -->

<div class="stat">

<div class="stat-header">

<div>3</div>

<div class="stat-title">
Schüsse aufs Tor
</div>

<div>2</div>

</div>

<div class="bar">

<div class="homeBar" style="width:60%"></div>

<div class="awayBar" style="width:40%"></div>

</div>

</div>

<!-- Eckbälle -->

<div class="stat">

<div class="stat-header">

<div>3</div>

<div class="stat-title">
Eckbälle
</div>

<div>1</div>

</div>

<div class="bar">

<div class="homeBar" style="width:75%"></div>

<div class="awayBar" style="width:25%"></div>

</div>

</div>

<!-- Gelbe Karten -->

<div class="stat">

<div class="stat-header">

<div>1</div>

<div class="stat-title">
Gelbe Karten
</div>

<div>0</div>

</div>

<div class="bar">

<div class="homeBar" style="width:100%"></div>

<div class="awayBar" style="width:0%"></div>

</div>

</div>

</div>

</body>
</html>
