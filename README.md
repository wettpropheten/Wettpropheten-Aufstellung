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

padding:20px;

font-family:Arial,Helvetica,sans-serif;

background:
linear-gradient(135deg,#071522,#063d28);

color:white;

}



.container{

max-width:1700px;

margin:auto;

}



h1{

text-align:center;

font-size:38px;

margin-bottom:25px;

text-shadow:0 10px 30px black;

}



/* HAUPTAUFTEILUNG */

.main{

display:grid;

grid-template-columns:

260px 430px 430px 260px;

gap:25px;

align-items:center;

justify-content:center;

}



/* GLAS KARTEN */


.card{

background:

rgba(255,255,255,.12);

border:

1px solid rgba(255,255,255,.25);

border-radius:25px;

padding:18px;

box-shadow:

0 20px 50px black;

backdrop-filter:blur(15px);

}




.card h2{

text-align:center;

font-size:22px;

}



/* MANNSCHAFTSAUSWAHL */


select,
input{

width:100%;

padding:10px;

margin-top:8px;

border-radius:10px;

border:none;

background:#111;

color:white;

}



label{

display:block;

margin-top:12px;

font-size:14px;

}



/* SPIELFELDER */


.field-box{

display:flex;

justify-content:center;

align-items:center;

}



.field{

position:relative;

width:430px;

height:680px;

background:

linear-gradient(
90deg,
#16843a,
#21a34d
);

border-radius:25px;

border:5px solid white;

box-shadow:

0 25px 60px black;

overflow:hidden;

}



/* Spielfeldlinien */


.field:before{

content:"";

position:absolute;

left:50%;

top:0;

height:100%;

width:3px;

background:white;

transform:translateX(-50%);

}



.field:after{

content:"";

position:absolute;

left:50%;

top:50%;

width:130px;

height:130px;

border:3px solid white;

border-radius:50%;

transform:translate(-50%,-50%);

}



/* Heimfeld leichte Neigung */


.home-field{

transform:

perspective(900px)
rotateY(-8deg)
rotateX(8deg);

}



/* Gastfeld spiegelverkehrt */


.away-field{

transform:

perspective(900px)
rotateY(8deg)
rotateX(8deg);

}



/* SPIELER */


.player{

position:absolute;

transform:

translate(-50%,-50%);

text-align:center;

}



.jersey{


width:55px;

height:55px;

border-radius:18px 18px 10px 10px;

display:flex;

align-items:center;

justify-content:center;

font-size:22px;

font-weight:bold;

box-shadow:

0 15px 25px black;

transform:

rotateX(35deg);

}



.player-name{

margin-top:8px;

font-size:14px;

font-weight:bold;

background:

rgba(0,0,0,.65);

padding:4px 8px;

border-radius:8px;

white-space:nowrap;

}



/* SPIELERLISTE */


.players{

margin-top:20px;

}



.player-row{

display:grid;

grid-template-columns:35px 1fr;

gap:8px;

margin-bottom:6px;

}



.number{

background:#000;

padding:8px;

border-radius:8px;

text-align:center;

}




/* BUTTONS */


button{

width:100%;

padding:12px;

margin-top:12px;

border-radius:10px;

border:none;

background:#008c45;

color:white;

font-weight:bold;

cursor:pointer;

}



button:hover{

opacity:.8;

}





/* UNTEN */

.bottom{

margin-top:30px;

display:grid;

grid-template-columns:1fr 1fr;

gap:30px;

}



/* RESPONSIVE */


@media(max-width:1400px){


.main{

grid-template-columns:220px 1fr;

}


.field{

width:360px;

height:580px;

}


}



@media(max-width:900px){


.main{

grid-template-columns:1fr;

}


.bottom{

grid-template-columns:1fr;

}


}



</style>

</head>



<body>


<div class="container">


<h1>
Wettpropheten Aufstellung
</h1>



<div class="main">



<!-- HEIM MANNSCHAFTSKARTE -->


<div class="card">


<h2>Heim</h2>


<select id="homeTeam"></select>


<label>
Formation
</label>


<select id="homeFormation">

<option>4-3-3</option>

<option>4-4-2</option>

<option>3-5-2</option>

</select>



<label>
Trikot Farbe
</label>


<input 
type="color"
id="homeKit"
value="#cc0000">



<label>
Nummern Farbe
</label>


<input
type="color"
id="homeNumber"
value="#ffffff">



<div id="homePlayers"
class="players">

</div>


</div>






<!-- HEIM FELD -->


<div class="field-box">


<div id="homeField"

class="field home-field">


</div>


</div>








<!-- GAST FELD -->


<div class="field-box">


<div id="awayField"

class="field away-field">


</div>


</div>








<!-- GAST MANNSCHAFTSKARTE -->


<div class="card">


<h2>Gast</h2>


<select id="awayTeam"></select>



<label>
Formation
</label>


<select id="awayFormation">

<option>4-3-3</option>

<option>4-4-2</option>

<option>3-5-2</option>

</select>




<label>
Trikot Farbe
</label>


<input

type="color"

id="awayKit"

value="#0066cc">



<label>
Nummern Farbe
</label>


<input

type="color"

id="awayNumber"

value="#ffffff">



<div id="awayPlayers"

class="players">

</div>



</div>



</div>



</div>



<!-- HIER KOMMT TEIL 2 -->
<script>


// ======================================
// MANNSCHAFTSDATEN
// ======================================


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
"Bensebaini",
"Couto",
"Can",
"Brandt",
"Sabitzer",
"Adeyemi",
"Guirassy",
"Gittens"

],


"Bayer Leverkusen":[

"Hradecky",
"Frimpong",
"Tah",
"Grimaldo",
"Xhaka",
"Wirtz",
"Palacios",
"Hofmann",
"Boniface",
"Adli",
"Schick"

],


"RB Leipzig":[

"Gulacsi",
"Henrichs",
"Orban",
"Simakan",
"Raum",
"Schlager",
"Seiwald",
"Olmo",
"Openda",
"Sesko",
"Forsberg"

],


"Eintracht Frankfurt":[

"Trapp",
"Tuta",
"Koch",
"Theate",
"Larsson",
"Skhiri",
"Chaibi",
"Knauff",
"Marmoush",
"Ekitike",
"Gotze"

],


"VfB Stuttgart":[

"Nubel",
"Vagnoman",
"Anton",
"Chabot",
"Mittelstadt",
"Stiller",
"Karazor",
"Millot",
"Führich",
"Undav",
"Guirassy"

],


"SC Freiburg":[

"Atubolu",
"Kubler",
"Lienhart",
"Ginter",
"Günter",
"Höler",
"Eggestein",
"Grifo",
"Doan",
"Röhl",
"Adamu"

],


"Borussia Mönchengladbach":[

"Omlin",
"Scally",
"Elvedi",
"Itakura",
"Netz",
"Weigl",
"Reitz",
"Hack",
"Honorat",
"Pleá",
"Ngoumou"

],


"Mainz 05":[

"Zentner",
"da Costa",
"Bell",
"Kohr",
"Caci",
"Amiri",
"Barreiro",
"Lee",
"Gruda",
"Burkardt",
"Ajorque"

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
"Woltemade",
"Njinmah",
"Bittencourt"

],


"TSG Hoffenheim":[

"Baumann",
"Kaderabek",
"Akpoguma",
"Brooks",
"Bischof",
"Geiger",
"Stach",
"Beier",
"Kramaric",
"Berisha",
"Skarke"

],


"FC Augsburg":[

"Dahmen",
"Gumny",
"Gouweleeuw",
"Matsima",
"Iago",
"Maier",
"Jakic",
"Demirovic",
"Vargas",
"Rexhbecaj",
"Tietz"

],


"1. FC Köln":[

"Schwabe",
"Schmitz",
"Hübers",
"Chabot",
"Paqarada",
"Martel",
"Kainz",
"Maina",
"Waldschmidt",
"Adamyan",
"Selke"

],


"Union Berlin":[

"Rönnow",
"Doekhi",
"Knoche",
"Leite",
"Trimmel",
"Khedira",
"Laidouni",
"Juranovic",
"Behrens",
"Volland",
"Hollerbach"

],


"Hamburger SV":[

"Heuer",
"Heyer",
"Schonlau",
"Muheim",
"Meffert",
"Reis",
"Dompe",
"Jatta",
"Glatzel",
"Benes",
"Selke"

],


"FC Schalke 04":[

"Müller",
"Brunner",
"Kaminski",
"Seguin",
"Ouwejan",
"Krauss",
"Zalazar",
"Mohr",
"Terodde",
"Polter",
"Karaman"

],


"SC Paderborn 07":[

"Huth",
"Curda",
"Musliu",
"Humme",
"Schuster",
"Klepinger",
"Bilbija",
"Conteh",
"Grimaldi",
"Platte",
"Justvan"

],


"SV Elversberg":[

"Kristof",
"Neubauer",
"Pinckert",
"Le Joncour",
"Feil",
"Fellhauer",
"Rochelt",
"Stock",
"Schmahl",
"Schnellbacher",
"Asllani"

]


};





// ======================================
// AUSWAHL LADEN
// ======================================


const homeTeam =
document.getElementById("homeTeam");


const awayTeam =
document.getElementById("awayTeam");



Object.keys(teams).forEach(team=>{


let a=document.createElement("option");

a.value=team;

a.textContent=team;

homeTeam.appendChild(a);



let b=document.createElement("option");

b.value=team;

b.textContent=team;

awayTeam.appendChild(b);



});



homeTeam.value="Bayern München";

awayTeam.value="Borussia Dortmund";






// ======================================
// FELDAUFSTELLUNG
// ======================================



const positions=[


[50,92],

[20,75],

[40,75],

[60,75],

[80,75],

[25,55],

[50,55],

[75,55],

[25,30],

[50,25],

[75,30]


];





function createField(id,team,kit,numColor){


let field=document.getElementById(id);


field.innerHTML="";



teams[team].forEach((player,index)=>{


let p=document.createElement("div");


p.className="player";


p.style.left=positions[index][0]+"%";

p.style.top=positions[index][1]+"%";



p.innerHTML=`

<div class="jersey"

style="
background:${kit};
color:${numColor};
">

${index+1}

</div>


<div class="player-name">

${player}

</div>


`;



field.appendChild(p);



});



}







// ======================================
// SPIELERKARTEN
// ======================================



function createPlayerList(id,team){


let box=document.getElementById(id);


box.innerHTML="";



teams[team].forEach((player,index)=>{


box.innerHTML += `

<div class="player-row">

<div class="number">

${index+1}

</div>


<input value="${player}">


</div>


`;

});


}






// ======================================
// UPDATE
// ======================================



function update(){



createField(

"homeField",

homeTeam.value,

document.getElementById("homeKit").value,

document.getElementById("homeNumber").value

);



createField(

"awayField",

awayTeam.value,

document.getElementById("awayKit").value,

document.getElementById("awayNumber").value

);



createPlayerList(
"homePlayers",
homeTeam.value
);



createPlayerList(
"awayPlayers",
awayTeam.value
);



}







homeTeam.onchange=update;

awayTeam.onchange=update;


document.getElementById("homeKit").onchange=update;

document.getElementById("awayKit").onchange=update;

document.getElementById("homeNumber").onchange=update;

document.getElementById("awayNumber").onchange=update;





update();



</script>



</body>

</html>
