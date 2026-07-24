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

padding:15px;

font-family:Arial,Helvetica,sans-serif;

background:
linear-gradient(135deg,#071421,#064b2d);

color:white;

}



.container{

width:100%;

max-width:1900px;

margin:auto;

}



h1{

text-align:center;

font-size:40px;

margin-bottom:20px;

text-shadow:0 10px 30px black;

}



/* HAUPT TV LAYOUT */


.main{

display:grid;

grid-template-columns:

230px minmax(420px,1fr) minmax(420px,1fr) 230px;

gap:25px;

align-items:center;

width:100%;

}



/* GLAS KARTEN */


.card{

background:

rgba(255,255,255,.13);

border:

1px solid rgba(255,255,255,.25);

border-radius:20px;

padding:14px;

box-shadow:

0 20px 50px black;

backdrop-filter:blur(12px);

}



.card h2{

text-align:center;

font-size:22px;

margin:5px;

}



/* AUSWAHL */


select,
input{

width:100%;

padding:9px;

margin-top:7px;

border-radius:8px;

border:none;

background:#111;

color:white;

}



label{

font-size:13px;

display:block;

margin-top:10px;

}



/* FELD */


.field-box{

width:100%;

display:flex;

justify-content:center;

}



.field{

position:relative;

width:100%;

height:720px;

background:

linear-gradient(
90deg,
#12833c,
#20a94e
);

border:

4px solid white;

border-radius:25px;

box-shadow:

0 25px 60px black;

overflow:hidden;

}



/* MITTELLINIE */


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



/* MITTELKREIS */


.field:after{

content:"";

position:absolute;

left:50%;

top:50%;

width:120px;

height:120px;

border:

3px solid white;

border-radius:50%;

transform:translate(-50%,-50%);

}



/* PERSPEKTIVE */


.home-field{

transform:

perspective(1300px)

rotateY(8deg)

rotateX(10deg);

}



.away-field{

transform:

perspective(1300px)

rotateY(-8deg)

rotateX(10deg);

}





/* TRIKOTS */


.player{

position:absolute;

transform:

translate(-50%,-50%);

text-align:center;

}



.jersey{

width:58px;

height:65px;

border-radius:

15px 15px 12px 12px;

display:flex;

align-items:center;

justify-content:center;

font-size:23px;

font-weight:bold;

box-shadow:

0 18px 30px black;

transform:

rotateX(35deg);

}



.player-name{

margin-top:8px;

font-size:13px;

background:

rgba(0,0,0,.7);

padding:4px 8px;

border-radius:8px;

white-space:nowrap;

}





/* SPIELERLISTE */


.players{

margin-top:15px;

}



.player-row{

display:grid;

grid-template-columns:

35px 1fr;

gap:5px;

margin-bottom:5px;

}



.number{

background:black;

padding:6px;

border-radius:6px;

text-align:center;

font-weight:bold;

}




button{

width:100%;

padding:10px;

margin-top:10px;

border:none;

border-radius:10px;

background:#008c45;

color:white;

font-weight:bold;

}





/* UNTERE BEREICHE */


.bottom{

margin-top:25px;

display:grid;

grid-template-columns:1fr 1fr;

gap:25px;

}



/* TABLET */


@media(max-width:1400px){


.main{

grid-template-columns:

200px 1fr;

}


.away-field,
.home-field{

margin-top:20px;

}


}



/* HANDY */


@media(max-width:900px){


.main{

grid-template-columns:1fr;

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



<div class="main">



<!-- HEIM KARTE -->


<div class="card">


<h2>Heim</h2>


<select id="homeTeam"></select>


<label>
Formation
</label>


<select id="homeFormation">

<option value="4-3-3">
4-3-3
</option>

<option value="4-4-2">
4-4-2
</option>

<option value="3-5-2">
3-5-2
</option>


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







<!-- GAST KARTE -->


<div class="card">


<h2>Gast</h2>


<select id="awayTeam"></select>



<label>
Formation
</label>


<select id="awayFormation">

<option value="4-3-3">
4-3-3
</option>

<option value="4-4-2">
4-4-2
</option>

<option value="3-5-2">
3-5-2
</option>

</select>




<label>
Trikotfarbe
</label>


<input
type="color"
id="awayKit"
value="#0055cc">



<label>
Nummernfarbe
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


<script>


// ==========================================
// MANNSCHAFTEN + SPIELER
// ==========================================


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
"Süle",
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
"Palacios",
"Hofmann",
"Boniface",
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
"Simons"
],


"Eintracht Frankfurt":[
"Trapp",
"Tuta",
"Koch",
"Theate",
"Nkounkou",
"Larsson",
"Skhiri",
"Chaibi",
"Knauff",
"Marmoush",
"Ekitike"
],


"VfB Stuttgart":[
"Nübel",
"Vagnoman",
"Chabot",
"Karazor",
"Mittelstädt",
"Stiller",
"Millot",
"Führich",
"Undav",
"Demirovic",
"Silas"
],


"SC Freiburg":[
"Atubolu",
"Kübler",
"Ginter",
"Lienhart",
"Günter",
"Eggestein",
"Höler",
"Grifo",
"Doan",
"Röhl",
"Adamu"
],


"Borussia Mönchengladbach":[
"Omlin",
"Scally",
"Itakura",
"Elvedi",
"Netz",
"Weigl",
"Reitz",
"Honorat",
"Pleá",
"Hack",
"Ngoumou"
],


"Mainz 05":[
"Zentner",
"da Costa",
"Bell",
"Kohr",
"Caci",
"Amiri",
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
"Njinmah",
"Bittencourt",
"Woltemade"
],


"TSG Hoffenheim":[
"Baumann",
"Kaderabek",
"Akpoguma",
"Brooks",
"Bischof",
"Stach",
"Prömel",
"Kramaric",
"Beier",
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
"Vargas",
"Demirovic",
"Tietz",
"Rexhbecaj"
],


"1. FC Köln":[
"Schwäbe",
"Schmitz",
"Hübers",
"Chabot",
"Paqarada",
"Martel",
"Kainz",
"Maina",
"Waldschmidt",
"Selke",
"Adamyan"
],


"Union Berlin":[
"Rönnow",
"Doekhi",
"Leite",
"Knoche",
"Juranovic",
"Khedira",
"Laidouni",
"Volland",
"Behrens",
"Hollerbach",
"Fofana"
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
"Ouwejan",
"Seguin",
"Krauss",
"Zalazar",
"Mohr",
"Karaman",
"Terodde",
"Polter"
],


"SC Paderborn 07":[
"Huth",
"Curda",
"Musliu",
"Schuster",
"Klepinger",
"Bilbija",
"Conteh",
"Grimaldi",
"Platte",
"Justvan",
"Ansah"
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
"Schnellbacher",
"Asllani",
"Petkovic"
]


};





// ==========================================
// FORMATIONEN
// ==========================================


const formations={


"4-3-3":[

[50,90],

[20,70],
[40,75],
[60,75],
[80,70],

[30,55],
[50,50],
[70,55],

[25,30],
[50,25],
[75,30]

],



"4-4-2":[

[50,90],

[20,70],
[40,75],
[60,75],
[80,70],

[20,50],
[40,50],
[60,50],
[80,50],

[40,25],
[60,25]

],



"3-5-2":[

[50,90],

[30,70],
[50,75],
[70,70],

[20,50],
[40,55],
[50,45],
[60,55],
[80,50],

[40,25],
[60,25]

]


};





// ==========================================
// DROPDOWN
// ==========================================


const homeTeam =
document.getElementById("homeTeam");


const awayTeam =
document.getElementById("awayTeam");



Object.keys(teams).forEach(t=>{


let a=document.createElement("option");

a.text=t;

homeTeam.add(a);



let b=document.createElement("option");

b.text=t;

awayTeam.add(b);


});



homeTeam.value="Bayern München";

awayTeam.value="Borussia Dortmund";





// ==========================================
// SPIELER AUF FELD
// ==========================================



function drawField(
field,
team,
formation,
kit,
numberColor
){


let box=document.getElementById(field);

box.innerHTML="";



teams[team].forEach((player,index)=>{


let pos=formations[formation][index];


let div=document.createElement("div");

div.className="player";


div.style.left=pos[0]+"%";

div.style.top=pos[1]+"%";



div.innerHTML=`

<div class="jersey"

style="
background:${kit};
color:${numberColor};
">

${index+1}

</div>


<div class="player-name">

${player}

</div>

`;



box.appendChild(div);


});


}






// ==========================================
// MANNSCHAFTSKARTE
// ==========================================


function drawList(
id,
team
){


let box=document.getElementById(id);

box.innerHTML="";



teams[team].forEach((p,i)=>{


box.innerHTML+=`

<div class="player-row">

<div class="number">

${i+1}

</div>


<div>

${p}

</div>


</div>

`;


});


}






// ==========================================
// AKTUALISIERUNG
// ==========================================


function update(){



drawField(

"homeField",

homeTeam.value,

document.getElementById("homeFormation").value,

document.getElementById("homeKit").value,

document.getElementById("homeNumber").value

);



drawField(

"awayField",

awayTeam.value,

document.getElementById("awayFormation").value,

document.getElementById("awayKit").value,

document.getElementById("awayNumber").value

);



drawList(
"homePlayers",
homeTeam.value
);


drawList(
"awayPlayers",
awayTeam.value
);



}



document.querySelectorAll("select,input")
.forEach(e=>{

e.onchange=update;

});



update();



</script>



</body>

</html>
