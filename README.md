<!DOCTYPE html>
<html lang="de">

<head>

<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Match App</title>

<style>

body{

    margin:0;
    background:#020b12;
    font-family:Arial,sans-serif;
    color:white;

}


.container{

    width:420px;
    margin:40px auto;

}


.box{

    background:#06151f;
    padding:20px;
    border-radius:10px;

}
.status{

    text-align:center;
    color:#e90046;
    font-weight:bold;
    margin-bottom:20px;

}


.teams{

    display:flex;
    justify-content:space-between;
    align-items:center;
    text-align:center;

}


.logo{

    width:65px;
    height:65px;
    border-radius:50%;
    background:#1b3445;

    display:flex;
    align-items:center;
    justify-content:center;

    font-size:24px;
    font-weight:bold;

}


.name{

    margin-top:10px;
    font-weight:bold;

}


.score{

    font-size:40px;
    font-weight:bold;

}


.time{

    color:#9aaab5;
    margin-top:5px;

}



.stat{

    margin-bottom:18px;

}



.stat-header{

    display:grid;
    grid-template-columns:70px 1fr 70px;
    align-items:center;
    text-align:center;

    font-size:14px;
    font-weight:bold;

    margin-bottom:8px;

}



.stat-header span:first-child{

    text-align:left;

}


.stat-header span:last-child{

    text-align:right;

}



.bar{

    height:8px;
    background:#092536;

    position:relative;
    overflow:hidden;

    border-radius:3px;

}



.home-bar{

    position:absolute;

    right:50%;

    height:100%;

    background:#f1f3f5;

}



.away-bar{

    position:absolute;

    left:50%;

    height:100%;

    background:#e90046;

}



.bar::after{

    content:"";

    position:absolute;

    left:50%;

    top:0;

    width:2px;

    height:100%;

    background:#07131c;

}

</style>

</head>


<body>


<div class="container">


<div class="box">


<h2>

Match Statistik

</h2>


<p>

Start

</p>


</div>


</div>

<div class="box">

<div class="status">
● LIVE 67'
</div>


<div class="teams">


<div>

<div class="logo">
H
</div>

<div class="name">
Heim FC
</div>

</div>



<div>

<div class="score">
2 : 1
</div>

<div class="time">
2. Halbzeit
</div>

</div>



<div>

<div class="logo">
A
</div>

<div class="name">
Auswärts FC
</div>

</div>


</div>

</div>
<div class="box">


<div class="stat">


<div class="stat-header">

<span>1.24</span>

<strong>Expected Goals (xG)</strong>

<span>0.80</span>

</div>


<div class="bar">

<div class="home-bar" style="width:61%;"></div>

<div class="away-bar" style="width:39%;"></div>

</div>


</div>




<div class="stat">


<div class="stat-header">

<span>50%</span>

<strong>Ballbesitz</strong>

<span>50%</span>

</div>


<div class="bar">

<div class="home-bar" style="width:50%;"></div>

<div class="away-bar" style="width:50%;"></div>

</div>


</div>


</div>
</body>

</html>
