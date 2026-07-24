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

padding:10px;

font-family:Arial,Helvetica,sans-serif;

background:
linear-gradient(135deg,#071522,#075b36);

color:white;

overflow-x:hidden;

}



.container{

width:100%;

max-width:2200px;

margin:auto;

}



h1{

text-align:center;

font-size:38px;

margin:10px;

text-shadow:
0 8px 25px black;

}



/* HAUPTAUFTEILUNG */


.layout{


display:grid;


grid-template-columns:

210px minmax(500px,1fr) minmax(500px,1fr) 210px;


gap:15px;


align-items:center;


width:100%;


}



/* MANNSCHAFTSKARTEN */


.card{


background:

rgba(255,255,255,.12);


border:

1px solid rgba(255,255,255,.3);


border-radius:18px;


padding:12px;


box-shadow:

0 15px 40px black;


height:fit-content;


}


.card h2{

text-align:center;

font-size:20px;

margin:5px;

}



select,
input{


width:100%;

padding:8px;

margin-top:8px;

border-radius:8px;

border:none;

background:#111;

color:white;


}



label{

font-size:12px;

margin-top:8px;

display:block;

}





/* FELD BEREICH */


.field-container{


display:flex;


justify-content:center;


}





.field{


position:relative;


height:720px;


width:100%;


background:

repeating-linear-gradient(

0deg,

#16833d 0px,

#16833d 50px,

#1b9347 50px,

#1b9347 100px

);



border:

3px solid white;


box-shadow:

0 25px 60px black;


overflow:hidden;


}



/* HEIM HALBES FELD */


.home-field{


border-radius:

20px 0 0 20px;


transform:

perspective(1200px)

rotateY(7deg)

rotateX(8deg);


}



/* GAST HALBES FELD */


.away-field{


border-radius:

0 20px 20px 0;


transform:

perspective(1200px)

rotateY(-7deg)

rotateX(8deg);


}



/* MITTELLINIE */


.home-field:after{


content:"";


position:absolute;


right:0;


top:0;


width:3px;


height:100%;


background:white;


}





.away-field:before{


content:"";


position:absolute;


left:0;


top:0;


width:3px;


height:100%;


background:white;


}





/* MITTELKREIS HALB */


.home-field:before{


content:"";


position:absolute;


right:-75px;


top:50%;


width:150px;


height:150px;


border:

3px solid white;


border-radius:50%;


transform:

translateY(-50%);


}





.away-field:after{


content:"";


position:absolute;


left:-75px;


top:50%;


width:150px;


height:150px;


border:

3px solid white;


border-radius:50%;


transform:

translateY(-50%);


}





/* SPIELER VORBEREITUNG */


.player{


position:absolute;


transform:

translate(-50%,-50%);


text-align:center;


}



.jersey{


width:55px;


height:65px;


border-radius:

15px 15px 10px 10px;


background:#c40000;


display:flex;


align-items:center;


justify-content:center;


font-size:22px;


font-weight:bold;


box-shadow:

0 15px 30px black;


transform:

rotateX(35deg);


}



.player-name{


margin-top:5px;


background:

rgba(0,0,0,.7);


padding:4px 7px;


border-radius:6px;


font-size:12px;


white-space:nowrap;


}





/* SPIELERLISTE */


.players{


margin-top:10px;


font-size:13px;


}



.player-line{


padding:5px;


background:

rgba(0,0,0,.35);


margin-top:3px;


border-radius:5px;


}





@media(max-width:1200px){


.layout{

grid-template-columns:

180px 1fr 1fr 180px;

gap:8px;

}


.field{

height:600px;

}


}





</style>


</head>



<body>


<div class="container">



<h1>
Wettpropheten Aufstellung
</h1>



<div class="layout">





<!-- HEIM KARTE -->


<div class="card">


<h2>Heim</h2>


<select id="homeTeam">

<option>Bayern München</option>

<option>Borussia Dortmund</option>

<option>Bayer Leverkusen</option>

</select>


<label>
Formation
</label>


<select id="homeFormation">

<option>4-3-3</option>

<option>4-4-2</option>

<option>3-5-2</option>

</select>


<label>
Trikotfarbe
</label>


<input type="color" value="#d00000">


<div class="players">


<div class="player-line">
1 Torwart
</div>

<div class="player-line">
2 Abwehr
</div>

<div class="player-line">
3 Abwehr
</div>

</div>


</div>








<!-- HEIM FELD -->


<div class="field-container">


<div class="field home-field"

id="homeField">


</div>


</div>








<!-- GAST FELD -->


<div class="field-container">


<div class="field away-field"

id="awayField">


</div>


</div>








<!-- GAST KARTE -->


<div class="card">


<h2>Gast</h2>


<select id="awayTeam">


<option>Borussia Dortmund</option>

<option>Bayern München</option>

<option>RB Leipzig</option>

</select>



<label>
Formation
</label>


<select id="awayFormation">


<option>4-3-3</option>

<option>4-4-2</option>

<option>3-5-2</option>


</select>


<label>
Trikotfarbe
</label>


<input type="color" value="#0055cc">


<div class="players">


<div class="player-line">
1 Torwart
</div>

<div class="player-line">
2 Abwehr
</div>

<div class="player-line">
3 Abwehr
</div>


</div>


</div>





</div>



</div>
<script>


const teams = {


"Bayern München":[

"Neuer",
"Kimmich",
"Upamecano",
"Kim",
"Davies",
"Goretzka",
"Musiala",
"Sane",
"Müller",
"Gnabry",
"Kane"

],


"Borussia Dortmund":[

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

],


"Bayer Leverkusen":[

"Hradecky",
"Tapsoba",
"Jonathan Tah",
"Grimaldo",
"Frimpong",
"Xhaka",
"Wirtz",
"Hofmann",
"Boniface",
"Schick",
"Adli"

],


"RB Leipzig":[

"Gulacsi",
"Henrichs",
"Orban",
"Lukeba",
"Raum",
"Seiwald",
"Simons",
"Olmo",
"Openda",
"Sessegnon",
"Poulsen"

],


"Eintracht Frankfurt":[

"Trapp",
"Kristensen",
"Tuta",
"Koch",
"Theate",
"Larsson",
"Skhiri",
"Chaibi",
"Marmoush",
"Ekitike",
"Knauff"

],


"SC Freiburg":[

"Atubolu",
"Kübler",
"Ginter",
"Lienhart",
"Günter",
"Höfler",
"Eggestein",
"Grifo",
"Doan",
"Gregoritsch",
"Adamu"

],


"VfB Stuttgart":[

"Nübel",
"Vagnoman",
"Chabot",
"Rouault",
"Mittelstädt",
"Stiller",
"Karazor",
"Millot",
"Undav",
"Demirovic",
"Führich"

]


};


// fehlende Teams werden automatisch ergänzt

[
"FC Augsburg",
"1. FC Union Berlin",
"Werder Bremen",
"SV Elversberg",
"Hamburger SV",
"TSG Hoffenheim",
"1. FC Köln",
"1. FSV Mainz 05",
"Borussia Mönchengladbach",
"SC Paderborn 07",
"FC Schalke 04"

].forEach(t=>{

if(!teams[t]){

teams[t]=[

"Torwart",
"Abwehr 1",
"Abwehr 2",
"Abwehr 3",
"Mittelfeld 1",
"Mittelfeld 2",
"Mittelfeld 3",
"Stürmer 1",
"Stürmer 2",
"Stürmer 3",
"Stürmer 4"

];

}

});




// Spielerpositionen

const formations={


"4-3-3":[

[50,90],
[20,70],
[40,75],
[60,75],
[80,70],

[35,50],
[50,55],
[65,50],

[25,25],
[50,20],
[75,25]

],


"4-4-2":[

[50,90],

[20,70],
[40,75],
[60,75],
[80,70],

[20,50],
[40,55],
[60,55],
[80,50],

[40,25],
[60,25]

],


"3-5-2":[

[50,90],

[25,70],
[50,75],
[75,70],

[20,50],
[35,45],
[50,55],
[65,45],
[80,50],

[40,25],
[60,25]

]

};





function drawPlayers(side){


let field =
document.getElementById(side+"Field");


field.innerHTML="";


let select =
document.getElementById(side+"Team");


let formation =
document.getElementById(side+"Formation").value;


let color =
side==="home"

? document.querySelectorAll("input[type=color]")[0].value

: document.querySelectorAll("input[type=color]")[1].value;



let players =
teams[select.value];



formations[formation].forEach((pos,index)=>{


let p =
document.createElement("div");


p.className="player";



let x=pos[0];

let y=pos[1];


// Gast spiegeln

if(side==="away"){

x=100-x;

}




p.style.left=x+"%";

p.style.top=y+"%";



p.innerHTML=`

<div class="jersey"

style="background:${color}">

${index+1}

</div>


<div class="player-name">

${players[index]}

</div>

`;



field.appendChild(p);



});


}





function loadTeams(){


let selects=[

document.getElementById("homeTeam"),

document.getElementById("awayTeam")

];



selects.forEach(s=>{


s.innerHTML="";


Object.keys(teams).forEach(t=>{


let option=document.createElement("option");


option.textContent=t;


s.appendChild(option);


});


});



}



loadTeams();


document
.getElementById("homeTeam")
.value="Bayern München";


document
.getElementById("awayTeam")
.value="Borussia Dortmund";





document.querySelectorAll("select")
.forEach(s=>{


s.onchange=()=>{


drawPlayers("home");

drawPlayers("away");


};


});



document.querySelectorAll("input[type=color]")
.forEach(c=>{


c.onchange=()=>{


drawPlayers("home");

drawPlayers("away");


};


});





drawPlayers("home");

drawPlayers("away");



</script>

</body>

</html>
