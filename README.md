<!DOCTYPE html>
<html lang="de">

<head>

<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Wettpropheten Aufstellung TV</title>


<style>


*{
box-sizing:border-box;
}


body{

margin:0;

padding:20px;

font-family:Arial,Helvetica,sans-serif;

background:
linear-gradient(135deg,#04101c,#075b35);

color:white;

}




.container{

max-width:1800px;

margin:auto;

}



h1{

text-align:center;

font-size:44px;

text-shadow:
0 10px 30px black;

margin-bottom:30px;

}




.main{

display:grid;

grid-template-columns:

360px 1fr 360px;

gap:35px;

align-items:start;

}






.panel{


background:

rgba(255,255,255,.12);


border:

1px solid rgba(255,255,255,.25);


border-radius:25px;


padding:25px;


box-shadow:

0 25px 60px black;


}





h2{

text-align:center;

}





label{

display:block;

margin-top:15px;

font-weight:bold;

}





select,
input{


width:100%;

padding:12px;

border-radius:10px;

border:none;

background:#111;

color:white;

font-size:16px;


}




input[type=color]{


height:45px;


padding:5px;


}






.player-list{


margin-top:20px;


}



.player-row{


display:grid;

grid-template-columns:

45px 1fr;


gap:8px;


margin-bottom:8px;


}





.number{


background:#222;


text-align:center;


padding:10px;


border-radius:8px;


}






/* SPIELFELD BEREICH */



.tv-area{


display:flex;

justify-content:center;

gap:40px;

}




.field-box{

text-align:center;

}





.field{


width:430px;

height:680px;


background:

linear-gradient(
90deg,
#158542,
#09612f
);


border:

4px solid white;


border-radius:25px;


position:relative;


box-shadow:

0 40px 80px black;


overflow:hidden;


}







/* Linien */



.field:before{


content:"";


position:absolute;


left:5%;


right:5%;


top:50%;


height:2px;


background:white;


}





.field:after{


content:"";


position:absolute;


width:140px;


height:140px;


border:

3px solid white;


border-radius:50%;


left:50%;


top:50%;


transform:

translate(-50%,-50%);


}








/* Perspektive */




.home-field{


transform:

perspective(1200px)

rotateX(52deg)

rotateY(20deg)

rotateZ(-4deg);


}



.away-field{


transform:

perspective(1200px)

rotateX(52deg)

rotateY(-20deg)

rotateZ(4deg);


}








/* TRIKOT PLATZHALTER */


.player{


position:absolute;


transform:

translate(-50%,-50%);


text-align:center;


}



.jersey{


width:65px;


height:80px;


background:#d00000;


border-radius:

18px 18px 12px 12px;


display:flex;


align-items:center;


justify-content:center;


font-size:26px;


font-weight:bold;


box-shadow:


0 25px 35px black;


border:

2px solid white;


}





.player-name{


margin-top:10px;


font-size:15px;


font-weight:bold;


text-shadow:

0 3px 8px black;


}







/* Überschrift Feld */


.team-title{


font-size:22px;

font-weight:bold;

margin-bottom:20px;


}







@media(max-width:1400px){


.main{


grid-template-columns:

1fr;


}



.tv-area{


flex-direction:column;


align-items:center;


}


}



</style>


</head>


<body>


<div class="container">


<h1>
Wettpropheten Aufstellung TV
</h1>




<div class="main">





<!-- HEIM -->

<div class="panel">


<h2>
Heim
</h2>



<label>
Mannschaft
</label>


<select id="homeTeam">

<option>
Bayern München
</option>

</select>





<label>
Formation
</label>


<select id="homeFormation">

<option>4-3-3</option>
<option>4-4-2</option>
<option>4-2-3-1</option>
<option>3-5-2</option>
<option>3-4-3</option>


</select>





<label>
Trikotfarbe
</label>


<input 
type="color"
id="homeKit"
value="#d00000">





<label>
Nummernfarbe
</label>


<input 
type="color"
id="homeNumber"
value="#ffffff">





<h3>
Spieler
</h3>


<div class="player-list" id="homePlayers">

</div>



</div>








<!-- MITTE -->



<div class="tv-area">



<div class="field-box">


<div class="team-title">
Heim
</div>



<div class="field home-field" id="homeField">


</div>


</div>






<div class="field-box">


<div class="team-title">
Gast
</div>



<div class="field away-field" id="awayField">


</div>


</div>





</div>








<!-- GAST -->



<div class="panel">


<h2>
Gast
</h2>



<label>
Mannschaft
</label>


<select id="awayTeam">


<option>
Borussia Dortmund
</option>


</select>





<label>
Formation
</label>


<select id="awayFormation">


<option>4-3-3</option>
<option>4-4-2</option>
<option>4-2-3-1</option>
<option>3-5-2</option>
<option>3-4-3</option>


</select>





<label>
Trikotfarbe
</label>


<input 
type="color"
id="awayKit"
value="#111111">





<label>
Nummernfarbe
</label>


<input 
type="color"
id="awayNumber"
value="#ffffff">





<h3>
Spieler
</h3>



<div class="player-list" id="awayPlayers">


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
"Hummels",
"Schlotterbeck",
"Bensebaini",
"Can",
"Brandt",
"Sabitzer",
"Adeyemi",
"Malen",
"Füllkrug"
],


"Bayer 04 Leverkusen":[
"Hradecky",
"Frimpong",
"Tah",
"Tapsoba",
"Grimaldo",
"Xhaka",
"Wirtz",
"Hofmann",
"Adli",
"Schick",
"Boniface"
],


"RB Leipzig":[
"Gulacsi",
"Henrichs",
"Simakan",
"Orban",
"Raum",
"Schlager",
"Olmo",
"Simons",
"Openda",
"Sesko",
"Poulsen"
],


"Eintracht Frankfurt":[
"Trapp",
"Tuta",
"Koch",
"Pacho",
"Ebimbe",
"Skhiri",
"Larsson",
"Marmoush",
"Chaibi",
"Knauff",
"Kalajdzic"
],


"VfB Stuttgart":[
"Nübel",
"Vagnoman",
"Anton",
"Zagadou",
"Mittelstädt",
"Karazor",
"Millot",
"Führich",
"Undav",
"Guirassy",
"Silas"
],


"SC Freiburg":[
"Atubolu",
"Kübler",
"Ginter",
"Lienhart",
"Günter",
"Eggestein",
"Doan",
"Grifo",
"Höler",
"Gregoritsch",
"Adamu"
],


"Mainz 05":[
"Zentner",
"Bell",
"Kohr",
"Caci",
"Amiri",
"Barreiro",
"Lee",
"Gruda",
"Burkardt",
"Ajorque",
"Onisiwo"
],


"Werder Bremen":[
"Pavlenka",
"Weiser",
"Stark",
"Friedl",
"Jung",
"Stage",
"Schmid",
"Ducksch",
"Füllkrug",
"Bittencourt",
"Demirovic"
],


"Borussia Mönchengladbach":[
"Omlin",
"Scally",
"Elvedi",
"Itakura",
"Netz",
"Weigl",
"Neuhaus",
"Pleá",
"Reitz",
"Ngoumou",
"Hack"
],


"FC Augsburg":[
"Dahmen",
"Mbabu",
"Gouweleeuw",
"Uduokhai",
"Iago",
"Jakic",
"Maier",
"Vargas",
"Demirovic",
"Michel",
"Rexhbecaj"
],


"Union Berlin":[
"Rönnow",
"Juranovic",
"Knoche",
"Leite",
"Roussillon",
"Khedira",
"Laidouni",
"Behrens",
"Becker",
"Volland",
"Hollerbach"
],


"Hoffenheim":[
"Baumann",
"Kabak",
"Akpoguma",
"Brooks",
"Bülter",
"Stach",
"Prömel",
"Kramaric",
"Beier",
"Berisha",
"Grillitsch"
],


"1. FC Köln":[
"Schwäbe",
"Schmitz",
"Hübers",
"Chabot",
"Heintz",
"Martel",
"Kainz",
"Maina",
"Waldschmidt",
"Selke",
"Tigges"
],


"Hamburger SV":[
"Heuer",
"Muheim",
"Schonlau",
"Hadzikadunic",
"Jatta",
"Meffert",
"Benes",
"Reis",
"Glatzel",
"Dompe",
"Pherai"
],


"Schalke 04":[
"Müller",
"Brunner",
"Kaminski",
"Seguin",
"Mohr",
"Schallenberg",
"Karaman",
"Terodde",
"Lasme",
"Tempelmann",
"Ouwejan"
],


"SC Paderborn":[
"Huth",
"Curda",
"Musliu",
"Hoffmeier",
"Obermair",
"Schuster",
"Bilbija",
"Conteh",
"Muslija",
"Platte",
"Klement"
],


"SV Elversberg":[
"Kristof",
"Pinckert",
"Le Joncour",
"Correia",
"Neubauer",
"Fellhauer",
"Feil",
"Rochelt",
"Petkov",
"Stock",
"Sickinger"
]


};





const formations={


"4-3-3":[

[50,90],

[20,70],
[40,78],
[60,78],
[80,70],

[35,55],
[50,50],
[65,55],

[20,25],
[50,18],
[80,25]

],



"4-4-2":[

[50,90],

[20,70],
[40,78],
[60,78],
[80,70],

[20,50],
[40,55],
[60,55],
[80,50],

[35,25],
[65,25]

],




"3-5-2":[

[50,90],

[30,75],
[50,80],
[70,75],

[15,55],
[35,50],
[50,55],
[65,50],
[85,55],

[35,25],
[65,25]

]


};






function createPlayers(id,team){


let box=document.getElementById(id);


box.innerHTML="";


teams[team].forEach((p,i)=>{


box.innerHTML+=`

<div class="player-row">

<div class="number">
${i+1}
</div>

<input value="${p}" 
oninput="updateAll()">

</div>


`;

});


}








function drawField(fieldId,playerId,formationId,kitId,numId,flip=false){



let field=document.getElementById(fieldId);

field.innerHTML="";


let pos=formations[
document.getElementById(formationId).value
];


let players=document.querySelectorAll(
"#"+playerId+" input"
);


pos.forEach((p,i)=>{


let name=
players[i]?.value || "Spieler";



let x=p[0];

let y=p[1];



if(flip){

y=100-y;

}



let div=document.createElement("div");


div.className="player";


div.style.left=x+"%";

div.style.top=y+"%";



div.innerHTML=`

<div class="jersey"

style="
background:${document.getElementById(kitId).value};
color:${document.getElementById(numId).value};
">

${i+1}

</div>


<div class="player-name">

${name}

</div>

`;



field.appendChild(div);



});



}





function updateAll(){


let home=
document.getElementById("homeTeam").value;


let away=
document.getElementById("awayTeam").value;



createPlayers(
"homePlayers",
home
);



createPlayers(
"awayPlayers",
away
);



drawField(
"homeField",
"homePlayers",
"homeFormation",
"homeKit",
"homeNumber"
);



drawField(
"awayField",
"awayPlayers",
"awayFormation",
"awayKit",
"awayNumber",
true
);



}






function loadTeams(){


let h=document.getElementById("homeTeam");

let a=document.getElementById("awayTeam");



Object.keys(teams).forEach(t=>{


let o=document.createElement("option");

o.text=t;

h.add(o);



let o2=document.createElement("option");

o2.text=t;

a.add(o2);


});


h.value="Bayern München";

a.value="Borussia Dortmund";


}






document.querySelectorAll("select,input").forEach(e=>{


e.addEventListener(
"change",
updateAll
);


});



loadTeams();

updateAll();



</script>
</body>

</html>
