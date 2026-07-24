<!DOCTYPE html>
<html lang="de">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Wettpropheten Analyse</title>

<style>

* {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
    font-family: Arial, Helvetica, sans-serif;
}

body {
    background: #111;
    min-height: 100vh;
    color: white;
    display: flex;
    justify-content: center;
    align-items: center;
}


.container {
    width: 1400px;
    min-height: 850px;
    padding: 35px;
    background: linear-gradient(145deg,#151515,#090909);
    border-radius: 25px;
    box-shadow: 0 0 40px rgba(0,0,0,.8);
}


/* HEADER */

.header {
    display:flex;
    justify-content:space-between;
    align-items:center;
    margin-bottom:40px;
}


.team {
    width:35%;
    height:90px;
    border-radius:18px;
    background:#1d1d1d;
    display:flex;
    justify-content:center;
    align-items:center;
    font-size:28px;
    font-weight:bold;
}


.vs {
    width:120px;
    height:70px;
    background:#222;
    border-radius:50px;
    display:flex;
    align-items:center;
    justify-content:center;
    font-size:32px;
    font-weight:900;
}


/* FELDER */

.fields {
    display:flex;
    justify-content:center;
    gap:45px;
    perspective:1200px;
}


.field {
    width:520px;
    height:520px;
    background:
    linear-gradient(
        90deg,
        rgba(255,255,255,.04) 50%,
        transparent 50%
    ),
    #1f5f35;

    border:4px solid rgba(255,255,255,.5);
    position:relative;

    transform:rotateX(45deg);
    box-shadow:
    0 40px 50px rgba(0,0,0,.7);

}


/* Spielfeld Linien */

.field:before {
    content:"";
    position:absolute;
    left:50%;
    top:0;
    width:3px;
    height:100%;
    background:white;
    transform:translateX(-50%);
}


.field:after {
    content:"";
    position:absolute;
    left:50%;
    top:50%;
    width:120px;
    height:120px;
    border:3px solid white;
    border-radius:50%;
    transform:translate(-50%,-50%);
}


/* Strafräume */

.box {
    position:absolute;
    width:180px;
    height:70px;
    border:3px solid white;
    left:50%;
    transform:translateX(-50%);
}

.top {
    top:0;
}

.bottom {
    bottom:0;
}


/* BOTTOM PANEL */


.bottom-panel {

    margin-top:40px;
    display:grid;
    grid-template-columns:1fr 180px 1fr;
    gap:20px;

}


.card {

    height:130px;
    background:#1a1a1a;
    border-radius:18px;
    display:flex;
    align-items:center;
    justify-content:center;
    font-size:22px;
    font-weight:bold;

}


.center-card {
    display:flex;
    flex-direction:column;
    gap:10px;
}


</style>

</head>


<body>


<div class="container">


<div class="header">

<div class="team">
HEIMTEAM
</div>


<div class="vs">
VS
</div>


<div class="team">
GASTTEAM
</div>

</div>



<div class="fields">


<div class="field">

<div class="box top"></div>
<div class="box bottom"></div>

</div>


<div class="field">

<div class="box top"></div>
<div class="box bottom"></div>

</div>


</div>



<div class="bottom-panel">


<div class="card">
START XI
</div>


<div class="center-card">

<div class="card">
4-3-3
</div>

<div class="card">
TRAINER
</div>

</div>


<div class="card">
START XI
</div>


</div>



</div>


</body>
</html>
