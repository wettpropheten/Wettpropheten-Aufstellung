<!DOCTYPE html>
<html lang="de">

<head>

<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Wettpropheten Aufstellung V2</title>

<style>

*{
box-sizing:border-box;
}


body{

margin:0;
height:100vh;
overflow:hidden;

background:
linear-gradient(135deg,#071521,#064d2c);

font-family:Arial,Helvetica,sans-serif;

color:white;

}


/* Gesamtlayout */

.layout{

height:100vh;
width:100vw;

display:grid;

grid-template-columns:
190px
1fr
1fr
190px;

gap:20px;

padding:25px;

align-items:center;

}



/* Mannschaftskarten */

.team-card{

height:70vh;

background:
linear-gradient(145deg,#252525,#090909);

border-radius:20px;

box-shadow:
0 20px 50px black;

display:flex;

flex-direction:column;

align-items:center;

justify-content:center;

padding:15px;

}



.logo{

width:85px;
height:85px;

border-radius:50%;

background:#444;

display:flex;

align-items:center;

justify-content:center;

font-size:30px;

font-weight:bold;

}



.team-name{

font-size:22px;

font-weight:bold;

margin-top:20px;

}





/* Spielfelder */


.field{

height:70vh;

position:relative;

background:

linear-gradient(
90deg,
#16833d,
#239653
);

border:3px solid white;

overflow:hidden;

box-shadow:

0 25px 60px black;

}




.home-field{

border-radius:25px 0 0 25px;

transform:

perspective(1400px)

rotateY(7deg)

rotateX(5deg);

}



.away-field{

border-radius:0 25px 25px 0;

transform:

perspective(1400px)

rotateY(-7deg)

rotateX(5deg);

}




/* Mittellinie */

.home-field::after,
.away-field::before{

content:"";

position:absolute;

top:0;

height:100%;

width:3px;

background:white;

}



.home-field::after{

right:0;

}


.away-field::before{

left:0;

}



/* Mittelkreis */

.home-field::before,
.away-field::after{

content:"";

position:absolute;

top:50%;

width:130px;

height:130px;

border:3px solid white;

border-radius:50%;

transform:translateY(-50%);

}



.home-field::before{

right:-65px;

}



.away-field::after{

left:-65px;

}



/* Spieler */


.player{

position:absolute;

transform:
translate(-50%,-50%);

text-align:center;

z-index:5;

}



.shirt{

width:38px;

height:38px;

border-radius:50%;

background:white;

color:black;

display:flex;

align-items:center;

justify-content:center;

font-weight:bold;

box-shadow:

0 5px 15px black;

}



.player-name{

margin-top:5px;

font-size:12px;

background:rgba(0,0,0,.7);

padding:3px 7px;

border-radius:8px;

white-space:nowrap;

}


</style>

</head>



<body>


<div class="layout">



<div class="team-card">

<div class="logo">
H
</div>

<div class="team-name">
HEIM
</div>

</div>





<div class="field home-field" id="homeField">

</div>





<div class="field away-field" id="awayField">

</div>





<div class="team-card">

<div class="logo">
G
</div>

<div class="team-name">
GAST
</div>

</div>



</div>





<script>


const homePlayers=[

"Neuer",
"Kimmich",
"Upamecano",
"Kim",
"Davies",
"Goretzka",
"Musiala",
"Pavlovic",
"Sane",
"Müller",
"Kane"

];


const awayPlayers=[

"Kobel",
"Ryerson",
"Schlotterbeck",
"Anton",
"Bensebaini",
"Can",
"Brandt",
"Sabitzer",
"Adeyemi",
"Guirassy",
"Gittens"

];



const positions=[

[50,90],

[20,70],

[40,75],

[60,75],

[80,70],

[35,55],

[50,50],

[65,55],

[25,25],

[50,18],

[75,25]

];





function createPlayer(name,number,x,y){


const player=document.createElement("div");

player.className="player";


player.style.left=x+"%";

player.style.top=y+"%";


player.innerHTML=`

<div class="shirt">
${number}
</div>

<div class="player-name">
${name}
</div>

`;

return player;

}





function drawTeams(){


const home=document.getElementById("homeField");

const away=document.getElementById("awayField");


home.innerHTML="";

away.innerHTML="";



positions.forEach((pos,index)=>{


home.appendChild(

createPlayer(

homePlayers[index],

index+1,

pos[0],

pos[1]

)

);



away.appendChild(

createPlayer(

awayPlayers[index],

index+1,

100-pos[0],

pos[1]

)

);



});


}



drawTeams();


</script>


</body>

</html>
