<!DOCTYPE html>
<html lang="de">

<head>

<meta charset="UTF-8">

<title>Wettpropheten Ansicht</title>


<style>

*{
box-sizing:border-box;
font-family:Arial, sans-serif;
}


body{

margin:0;

background:#050505;

color:white;

}


.app{

display:flex;

width:100vw;

height:100vh;

}



/* LINKS */

.sidebar{

width:300px;

background:#111;

border-right:2px solid #444;

padding:20px;

}



.sidebar h2{

text-align:center;

color:#f5c542;

}


.match{

background:#222;

border:1px solid #555;

border-radius:15px;

padding:15px;

margin-top:15px;

text-align:center;

}





/* RECHTS */

.main{


flex:1;


background:#181818;


padding:30px;


}




.header{


width:100%;


height:180px;


background:#222;


border-radius:25px;


display:flex;


align-items:center;


justify-content:space-around;


font-size:40px;


font-weight:bold;


border:1px solid #555;


}



.box{


margin-top:30px;


height:120px;


background:#222;


border-radius:25px;


border:1px solid #555;


padding:25px;


font-size:25px;


color:#f5c542;


}



</style>


</head>


<body>


<div class="app">


<!-- SPIELTAG -->

<div class="sidebar">


<h2>

SPIELTAG

</h2>



<div class="match">

29.08. 15:30

<br>

1. FC Köln

<br>

VS

<br>

TSG Hoffenheim

</div>



<div class="match">

RB Leipzig

<br>

VS

<br>

Gladbach

</div>



</div>







<!-- HAUPTFENSTER -->


<div class="main">


<div class="header">


<span>

1. FC Köln

</span>


<span>

0 : 0

</span>


<span>

TSG Hoffenheim

</span>


</div>




<div class="box">

Expected Goals (xG) Balken kommt hier

</div>



<div class="box">

Ballbesitz Balken kommt hier

</div>



<div class="box">

Statistik Kästchen kommen hier

</div>



<div class="box">

Spieldaten Tabelle kommt hier

</div>



</div>



</div>


</body>

</html>
