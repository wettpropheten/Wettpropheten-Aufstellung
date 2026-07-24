<!DOCTYPE html>
<html lang="de">

<head>

<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Wettpropheten Aufstellung</title>


<style>

*{
box-sizing:border-box;
}


body{

margin:0;
padding:30px;

font-family:Arial,Helvetica,sans-serif;

background:
linear-gradient(135deg,#06101d,#075c35);

color:white;

}



h1{

text-align:center;

font-size:42px;

text-shadow:0 10px 30px black;

}



.container{

max-width:1500px;

margin:auto;

}




.fields{

display:flex;

justify-content:center;

gap:80px;

margin-top:50px;

}



/* SPIELFELDER */


.pitch{

width:420px;

height:620px;

background:

linear-gradient(
90deg,
#159447,
#0c6b32
);


border:

4px solid white;


border-radius:20px;


position:relative;


box-shadow:

0 40px 70px black;


}



.pitch:before{

content:"";

position:absolute;

left:50%;

top:50%;

width:90%;

height:2px;

background:white;

transform:translate(-50%,-50%);

}


.pitch:after{

content:"";

position:absolute;

left:50%;

top:50%;

width:120px;

height:120px;

border:

3px solid white;

border-radius:50%;

transform:

translate(-50%,-50%);

}



/* 3D NEIGUNG */


.homePitch{

transform:

perspective(900px)

rotateX(25deg)

rotateY(18deg)

rotateZ(-3deg);

}



.awayPitch{


transform:

perspective(900px)

rotateX(25deg)

rotateY(-18deg)

rotateZ(3deg);


}




/* SPIELER */


.player{

position:absolute;

transform:

translate(-50%,-50%);

text-align:center;

font-weight:bold;

}



.jersey{


width:55px;

height:65px;


background:

linear-gradient(
135deg,
white,
#bbbbbb
);


border-radius:

12px 12px 8px 8px;


display:flex;

align-items:center;

justify-content:center;


font-size:22px;

color:black;


box-shadow:

0 15px 20px black;


border:

3px solid white;


}




.player span{

display:block;

margin-top:8px;

font-size:14px;

text-shadow:

0 3px 5px black;

}




/* KARTEN */


.cards{

margin-top:70px;

display:grid;

grid-template-columns:

repeat(2,1fr);

gap:30px;

}



.card{

background:

rgba(255,255,255,.12);


padding:25px;

border-radius:25px;


box-shadow:

0 20px 50px black;


text-align:center;


}



.card input{

width:90%;

padding:10px;

margin:5px;

border-radius:10px;

border:none;

}




@media(max-width:900px){


.fields{

flex-direction:column;

align-items:center;

}


.cards{

grid-template-columns:1fr;

}


}


</style>


</head>



<body>


<div class="container">


<h1>
⚽ Wettpropheten Aufstellung
</h1>



<div class="fields">


<div>

<h2 style="text-align:center">
🏠 Heim
</h2>


<div class="pitch homePitch" id="homeField"></div>


</div>



<div>

<h2 style="text-align:center">
✈️ Gast
</h2>


<div class="pitch awayPitch" id="awayField"></div>


</div>


</div>





<div class="cards">


<div class="card">

<h2>
🏠 Heim Mannschaft
</h2>


<img width="100" 
src="https://s.hs-data.com/gfx/emblem/common/150x150/209.png">


<h3>Bayern München</h3>


<input value="Trainer">

<input value="Aufstellung">


</div>



<div class="card">


<h2>
✈️ Gast Mannschaft
</h2>


<img width="100"
src="https://s.hs-data.com/gfx/emblem/common/150x150/258.png">


<h3>Borussia Dortmund</h3>


<input value="Trainer">

<input value="Aufstellung">


</div>



</div>






<script>



const heim=[

["1","Neuer","50%","90%"],

["2","Davies","20%","75%"],

["4","Upamecano","40%","80%"],

["5","de Ligt","60%","80%"],

["6","Kimmich","80%","75%"],


["8","Goretzka","25%","55%"],

["10","Musiala","50%","50%"],

["11","Coman","75%","55%"],


["7","Gnabry","30%","25%"],

["9","Kane","50%","20%"],

["25","Müller","70%","25%"]

];





const gast=[


["1","Kobel","50%","90%"],

["2","Ryerson","20%","75%"],

["4","Schlotterbeck","40%","80%"],

["5","Bensebaini","60%","80%"],

["26","Ribeiro","80%","75%"],


["8","Sabitzer","25%","55%"],

["10","Brandt","50%","50%"],

["11","Adeyemi","75%","55%"],


["7","Malen","30%","25%"],

["9","Füllkrug","50%","20%"],

["21","Donyell","70%","25%"]

];






function createPlayers(field,data){


data.forEach(player=>{


let div=document.createElement("div");


div.className="player";


div.style.left=player[2];

div.style.top=player[3];



div.innerHTML=

`

<div class="jersey">

${player[0]}

</div>


<span>

${player[1]}

</span>

`;



field.appendChild(div);



});


}





createPlayers(

document.getElementById("homeField"),

heim

);



createPlayers(

document.getElementById("awayField"),

gast

);



</script>


</div>


</body>

</html>
