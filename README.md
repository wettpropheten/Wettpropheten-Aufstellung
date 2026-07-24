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
linear-gradient(135deg,#06101d,#075c35);

color:white;

}



.container{

max-width:1600px;

margin:auto;

}



h1{

text-align:center;

font-size:42px;

text-shadow:0 10px 30px black;

}



.layout{

display:grid;

grid-template-columns:350px 1fr 350px;

gap:30px;

align-items:start;

}




.card{

background:

rgba(255,255,255,.12);

border:

1px solid rgba(255,255,255,.25);

border-radius:25px;

padding:25px;

box-shadow:

0 20px 50px black;

}



select,
input{

width:100%;

padding:12px;

margin-top:8px;

border-radius:10px;

border:none;

background:#111;

color:white;

font-size:16px;

}



label{

display:block;

margin-top:15px;

}




button{

width:100%;

margin-top:15px;

padding:12px;

border:none;

border-radius:10px;

background:#008f45;

color:white;

font-weight:bold;

cursor:pointer;

}





/* SPIELFELDER */


.center{

display:flex;

justify-content:center;

gap:40px;

}



.pitch{

width:400px;

height:600px;

background:

linear-gradient(

90deg,

#12833d,

#0c632e

);


border:4px solid white;

border-radius:20px;

position:relative;

box-shadow:

0 50px 80px black;


}




.pitch:before{

content:"";

position:absolute;

width:90%;

height:2px;

background:white;

left:5%;

top:50%;

}




.pitch:after{

content:"";

position:absolute;

width:120px;

height:120px;

border:3px solid white;

border-radius:50%;

left:50%;

top:50%;

transform:translate(-50%,-50%);

}





/* MEHR NACH HINTEN GENEIGT */


.homePitch{

transform:

perspective(1000px)

rotateX(45deg)

rotateY(25deg)

rotateZ(-5deg);

}



.awayPitch{


transform:

perspective(1000px)

rotateX(45deg)

rotateY(-25deg)

rotateZ(5deg);


}





/* TRIKOT */


.player{

position:absolute;

transform:

translate(-50%,-50%);

text-align:center;

z-index:5;

}



.jersey{


width:55px;

height:70px;


border-radius:

15px 15px 8px 8px;


display:flex;

align-items:center;

justify-content:center;


font-size:24px;

font-weight:bold;


box-shadow:

0 25px 25px rgba(0,0,0,.8);


border:

2px solid white;


transform:

rotateX(25deg);


}



.playerName{

margin-top:8px;

font-size:14px;

font-weight:bold;

text-shadow:

0 3px 5px black;

}





/* FORMATION */


.formationTitle{

margin-top:20px;

font-size:18px;

font-weight:bold;

}




/* SPIELERLISTE */


.playerInput{

display:grid;

grid-template-columns:50px 1fr;

gap:10px;

margin-top:8px;

}




/* FARBE */


.colorBox{

height:40px;

padding:3px;

}




@media(max-width:1200px){


.layout{

grid-template-columns:1fr;

}


.center{

flex-direction:column;

align-items:center;

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



<!-- HEIM -->

<div class="card">


<h2>
Heim Mannschaft
</h2>



<label>
Verein
</label>


<select id="homeTeam"></select>



<label>
Formation
</label>


<select id="homeFormation">

<option>4-4-2</option>
<option>4-3-3</option>
<option>4-2-3-1</option>
<option>3-5-2</option>
<option>5-3-2</option>
<option>3-4-3</option>

</select>




<label>
Trikotfarbe
</label>

<input 
type="color"
id="homeColor"
value="#d00000"
class="colorBox">



<label>
Nummernfarbe
</label>

<input 
type="color"
id="homeNumberColor"
value="#ffffff"
class="colorBox">



<h3>
Spieler
</h3>


<div id="homePlayers"></div>



</div>






<!-- FELDER -->

<div class="center">


<div>

<h2 align="center">
Heim
</h2>

<div class="pitch homePitch" id="homeField"></div>

</div>




<div>

<h2 align="center">
Gast
</h2>

<div class="pitch awayPitch" id="awayField"></div>

</div>



</div>







<!-- GAST -->


<div class="card">


<h2>
Gast Mannschaft
</h2>



<label>
Verein
</label>


<select id="awayTeam"></select>



<label>
Formation
</label>


<select id="awayFormation">

<option>4-4-2</option>
<option>4-3-3</option>
<option>4-2-3-1</option>
<option>3-5-2</option>
<option>5-3-2</option>
<option>3-4-3</option>

</select>




<label>
Trikotfarbe
</label>


<input 
type="color"
id="awayColor"
value="#000000"
class="colorBox">



<label>
Nummernfarbe
</label>


<input 
type="color"
id="awayNumberColor"
value="#ffffff"
class="colorBox">



<h3>
Spieler
</h3>


<div id="awayPlayers"></div>




</div>


</div>


</div>
<script>


const vereine = {


"Bayern München":[
"Neuer",
"Davies",
"Upamecano",
"de Ligt",
"Kimmich",
"Goretzka",
"Musiala",
"Sané",
"Gnabry",
"Kane",
"Müller"
],


"Borussia Dortmund":[
"Kobel",
"Ryerson",
"Schlotterbeck",
"Can",
"Bensebaini",
"Sabitzer",
"Brandt",
"Adeyemi",
"Malen",
"Füllkrug",
"Reus"
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
"Höler",
"Eggestein",
"Doan",
"Grifo",
"Gregoritsch",
"Adamu"
],


"Mainz 05":[
"Zentner",
"da Costa",
"Bell",
"Kohr",
"Caci",
"Barreiro",
"Lee",
"Gruda",
"Onisiwo",
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
"Füllkrug",
"Demirovic",
"Bittencourt"
],


"Borussia Mönchengladbach":[
"Omlin",
"Scally",
"Elvedi",
"Itakura",
"Netz",
"Weigl",
"Neuhaus",
"Ngoumou",
"Pleá",
"Honorát",
"Reitz"
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
"Volland",
"Becker",
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
"Klement",
"Platte"
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






let positionen={


"4-4-2":[

[50,90],

[20,75],
[40,80],
[60,80],
[80,75],

[20,55],
[40,55],
[60,55],
[80,55],

[35,25],
[65,25]

],


"4-3-3":[

[50,90],

[20,75],
[40,80],
[60,80],
[80,75],

[30,55],
[50,50],
[70,55],

[25,25],
[50,20],
[75,25]

],


"3-5-2":[

[50,90],

[30,75],
[50,80],
[70,75],

[20,55],
[35,50],
[50,55],
[65,50],
[80,55],

[35,25],
[65,25]

]

};





function vereineLaden(){


let h=document.getElementById("homeTeam");

let a=document.getElementById("awayTeam");


Object.keys(vereine).forEach(v=>{


let o=document.createElement("option");

o.text=v;

h.add(o);



let o2=document.createElement("option");

o2.text=v;

a.add(o2);


});


h.value="Bayern München";

a.value="Borussia Dortmund";


}




function spielerListe(id,verein){


let box=document.getElementById(id);


box.innerHTML="";


vereine[verein].forEach((name,i)=>{


box.innerHTML+=`

<div class="playerInput">

<input value="${i+1}" disabled>

<input value="${name}" 
onchange="updateAll()"
>

</div>

`;


});


}





function anzeigen(fieldId,teamId,formationId,colorId,numColorId,spielerId){


let field=document.getElementById(fieldId);


field.innerHTML="";


let formation=document.getElementById(formationId).value;


let pos=positionen[formation];


let spieler=document.querySelectorAll(
"#"+spielerId+" .playerInput input:nth-child(2)"
);



pos.forEach((p,i)=>{


let name=spieler[i] ? spieler[i].value:"Spieler";


let nr=i+1;



let div=document.createElement("div");


div.className="player";


div.style.left=p[0]+"%";

div.style.top=p[1]+"%";



div.innerHTML=`

<div class="jersey"

style="background:${document.getElementById(colorId).value};
color:${document.getElementById(numColorId).value};">

${nr}

</div>


<div class="playerName">

${name}

</div>

`;



field.appendChild(div);


});


}





function updateAll(){


let ht=document.getElementById("homeTeam").value;

let at=document.getElementById("awayTeam").value;



spielerListe(
"homePlayers",
ht
);


spielerListe(
"awayPlayers",
at
);



anzeigen(
"homeField",
"homeTeam",
"homeFormation",
"homeColor",
"homeNumberColor",
"homePlayers"
);



anzeigen(
"awayField",
"awayTeam",
"awayFormation",
"awayColor",
"awayNumberColor",
"awayPlayers"
);



}






document.querySelectorAll("select,input").forEach(e=>{


e.addEventListener(

"change",

updateAll

);


});



vereineLaden();

updateAll();



</script>

</body>

</html>
