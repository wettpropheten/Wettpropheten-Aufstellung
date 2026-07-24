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
linear-gradient(135deg,#071522,#075c35);

color:white;

overflow:hidden;

}



h1{

text-align:center;

font-size:34px;

margin:0 0 15px;

}



/* HAUPTAUFTEILUNG */

.layout{


width:100%;

height:85vh;


display:grid;


grid-template-columns:

170px

minmax(0,1fr)

35px

minmax(0,1fr)

170px;


gap:10px;


align-items:center;


}



/* MANNSCHAFTSKARTEN */


.card{


height:520px;


background:

rgba(255,255,255,.12);


border:

1px solid rgba(255,255,255,.3);


border-radius:20px;


padding:15px;


box-shadow:

0 20px 50px black;


}



.card h2{

text-align:center;

margin-top:0;

}



select,
input{


width:100%;

padding:10px;

margin-bottom:12px;

border-radius:10px;

border:none;

background:#111;

color:white;

}





/* SPIELFELDER */


.field{


height:700px;


position:relative;


overflow:hidden;


background:

linear-gradient(

90deg,

#16833d,

#22964e

);


border:

3px solid white;


box-shadow:

0 25px 60px black;


}



/* HEIM */

.home-field{


border-radius:

25px 0 0 25px;


transform:

perspective(1200px)

rotateY(10deg)

rotateX(10deg);


}



/* GAST */

.away-field{


border-radius:

0 25px 25px 0;


transform:

perspective(1200px)

rotateY(-10deg)

rotateX(10deg);


}



/* MITTELLINIE */


.home-field::after{


content:"";

position:absolute;

right:0;

top:0;

width:3px;

height:100%;

background:white;


}



.away-field::before{


content:"";

position:absolute;

left:0;

top:0;

width:3px;

height:100%;

background:white;


}



/* MITTELKREIS */


.home-field::before{


content:"";

position:absolute;

right:-85px;

top:50%;

width:170px;

height:170px;


border:

3px solid white;


border-radius:50%;


transform:

translateY(-50%);


}



.away-field::after{


content:"";

position:absolute;

left:-85px;

top:50%;

width:170px;

height:170px;


border:

3px solid white;


border-radius:50%;


transform:

translateY(-50%);


}



</style>

</head>



<body>



<h1>
Wettpropheten Aufstellung
</h1>




<div class="layout">





<!-- HEIM KARTE -->

<div class="card">


<h2>Heim</h2>


<select>

<option>Bayern München</option>
<option>Borussia Dortmund</option>
<option>Bayer Leverkusen</option>

</select>



<label>
Formation
</label>


<select>

<option>4-3-3</option>
<option>4-4-2</option>
<option>3-5-2</option>

</select>



<label>
Trikotfarbe
</label>


<input type="color" value="#cc0000">


</div>







<!-- HEIM FELD -->


<div class="field home-field">


</div>








<!-- ABSTAND -->


<div></div>








<!-- GAST FELD -->


<div class="field away-field">


</div>








<!-- GAST KARTE -->


<div class="card">


<h2>Gast</h2>


<select>

<option>Borussia Dortmund</option>
<option>Bayern München</option>
<option>RB Leipzig</option>

</select>



<label>
Formation
</label>


<select>

<option>4-3-3</option>
<option>4-4-2</option>
<option>3-5-2</option>

</select>



<label>
Trikotfarbe
</label>


<input type="color" value="#004cff">


</div>




</div>
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
linear-gradient(135deg,#071522,#075c35);

color:white;

overflow:hidden;

}


h1{

text-align:center;

font-size:34px;

margin:0 0 15px;

}



.layout{

width:100%;

height:85vh;

display:grid;


grid-template-columns:

170px

minmax(0,1fr)

35px

minmax(0,1fr)

170px;


gap:10px;


align-items:center;

}





.card{


height:520px;


background:

rgba(255,255,255,.12);


border:

1px solid rgba(255,255,255,.3);


border-radius:20px;


padding:15px;


box-shadow:

0 20px 50px black;


}


.card h2{

text-align:center;

}



select,
input{

width:100%;

padding:10px;

margin-bottom:12px;

border-radius:10px;

border:none;

background:#111;

color:white;

}





.field{


height:700px;

position:relative;

overflow:hidden;


background:

linear-gradient(

90deg,

#16833d,

#22964e

);


border:

3px solid white;


box-shadow:

0 25px 60px black;


}




.home-field{


border-radius:

25px 0 0 25px;


transform:

perspective(1200px)

rotateY(10deg)

rotateX(10deg);


}





.away-field{


border-radius:

0 25px 25px 0;


transform:

perspective(1200px)

rotateY(-10deg)

rotateX(10deg);


}




.home-field::after{

content:"";

position:absolute;

right:0;

top:0;

width:3px;

height:100%;

background:white;

}



.away-field::before{

content:"";

position:absolute;

left:0;

top:0;

width:3px;

height:100%;

background:white;

}




.home-field::before{

content:"";

position:absolute;

right:-85px;

top:50%;

width:170px;

height:170px;

border:

3px solid white;

border-radius:50%;

transform:

translateY(-50%);

}





.away-field::after{

content:"";

position:absolute;

left:-85px;

top:50%;

width:170px;

height:170px;

border:

3px solid white;

border-radius:50%;

transform:

translateY(-50%);

}





.player{


position:absolute;

transform:

translate(-50%,-50%);


text-align:center;


z-index:5;


}



.jersey{


width:62px;

height:72px;


display:flex;

align-items:center;

justify-content:center;


font-size:24px;

font-weight:bold;


color:white;


border-radius:

18px 18px 12px 12px;


box-shadow:

0 20px 35px black;


transform:

perspective(500px)

rotateX(55deg);


}



.player-name{


margin-top:8px;


background:

rgba(0,0,0,.85);


padding:

5px 8px;


border-radius:8px;


font-size:13px;


white-space:nowrap;


}
</style>

</head>


<body>


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


<label>Formation</label>

<select id="homeFormation">

<option>4-3-3</option>
<option>4-4-2</option>
<option>3-5-2</option>

</select>



<label>Trikotfarbe</label>

<input id="homeColor" type="color" value="#cc0000">



</div>





<!-- HEIM FELD -->

<div class="field home-field" id="homeField">


</div>





<!-- ABSTAND -->

<div></div>





<!-- GAST FELD -->

<div class="field away-field" id="awayField">


</div>





<!-- GAST KARTE -->


<div class="card">

<h2>Gast</h2>


<select id="awayTeam">

<option>Borussia Dortmund</option>
<option>Bayern München</option>
<option>RB Leipzig</option>

</select>


<label>Formation</label>


<select id="awayFormation">

<option>4-3-3</option>
<option>4-4-2</option>
<option>3-5-2</option>

</select>



<label>Trikotfarbe</label>

<input id="awayColor" type="color" value="#004cff">


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
"Pavlovic",
"Sane",
"Müller",
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
"Tah",
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
"Simakan",
"Raum",
"Schlager",
"Seiwald",
"Olmo",
"Simons",
"Openda",
"Sesko"

]


};




const formations = {


"4-3-3":[

[50,88],

[20,70],
[40,75],
[60,75],
[80,70],

[35,52],
[50,45],
[65,52],

[25,25],
[50,18],
[75,25]

],



"4-4-2":[

[50,88],

[20,70],
[40,75],
[60,75],
[80,70],

[20,50],
[40,45],
[60,45],
[80,50],

[40,25],
[60,25]

],



"3-5-2":[

[50,88],

[30,70],
[50,76],
[70,70],

[20,52],
[35,45],
[50,55],
[65,45],
[80,52],

[40,25],
[60,25]

]


};

function drawTeam(side){


let field;

let teamName;

let formation;

let color;



if(side==="home"){


field=document.getElementById("homeField");

teamName=document.getElementById("homeTeam").value;

formation=document.getElementById("homeFormation").value;

color=document.getElementById("homeColor").value;


}

else{


field=document.getElementById("awayField");

teamName=document.getElementById("awayTeam").value;

formation=document.getElementById("awayFormation").value;

color=document.getElementById("awayColor").value;


}



field.innerHTML="";



let players=teams[teamName];



formations[formation].forEach((pos,index)=>{


let x=pos[0];

let y=pos[1];



/* Gast spiegeln */


if(side==="away"){

x=100-x;

}




let player=document.createElement("div");


player.className="player";


player.style.left=x+"%";

player.style.top=y+"%";



player.innerHTML=`

<div class="jersey"

style="background:${color}">

${index+1}

</div>


<div class="player-name">

${players[index]}

</div>

`;



field.appendChild(player);


});



}





/* Aktualisierung bei Änderung */


document

.querySelectorAll("select,input")

.forEach(element=>{


element.addEventListener("change",()=>{


drawTeam("home");

drawTeam("away");


});


});





/* Startanzeige */


drawTeam("home");

drawTeam("away");



</script>

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

linear-gradient(135deg,#061522,#075c35);

color:white;

overflow:hidden;

}




h1{

text-align:center;

font-size:34px;

margin:0 0 15px;

}





.layout{


width:100%;

height:85vh;


display:grid;


grid-template-columns:

170px

minmax(0,1fr)

35px

minmax(0,1fr)

170px;


gap:10px;


align-items:center;


}







.card{


height:540px;


background:

rgba(255,255,255,.12);


border:

1px solid rgba(255,255,255,.3);


border-radius:20px;


padding:15px;


box-shadow:

0 20px 50px black;


}




.card h2{

text-align:center;

}



select,
input{


width:100%;

padding:10px;

margin-bottom:10px;

border-radius:10px;

border:none;

background:#111;

color:white;


}






.field{


height:700px;


position:relative;


overflow:hidden;


background:

linear-gradient(

90deg,

#16833d,

#239950

);



border:

3px solid white;


box-shadow:

0 25px 60px black;


}





.home-field{


border-radius:

25px 0 0 25px;


transform:

perspective(1200px)

rotateY(10deg)

rotateX(10deg);


}






.away-field{


border-radius:

0 25px 25px 0;


transform:

perspective(1200px)

rotateY(-10deg)

rotateX(10deg);


}







.home-field::after{

content:"";

position:absolute;

right:0;

top:0;

height:100%;

width:3px;

background:white;

}





.away-field::before{

content:"";

position:absolute;

left:0;

top:0;

height:100%;

width:3px;

background:white;

}






.home-field::before{


content:"";

position:absolute;

right:-85px;

top:50%;


width:170px;

height:170px;


border:

3px solid white;


border-radius:50%;


transform:

translateY(-50%);


}





.away-field::after{


content:"";

position:absolute;

left:-85px;

top:50%;


width:170px;

height:170px;


border:

3px solid white;


border-radius:50%;


transform:

translateY(-50%);


}
/* SPIELER UND TRIKOTS */

.player{

position:absolute;

transform:

translate(-50%,-50%);


text-align:center;


z-index:5;


transition:.3s;


}



.player:hover{

transform:

translate(-50%,-50%)

scale(1.12);


}





.jersey{


width:70px;

height:82px;


position:relative;


display:flex;


align-items:center;


justify-content:center;


font-size:26px;


font-weight:bold;


color:white;


border-radius:

22px 22px 15px 15px;



box-shadow:


0 25px 45px rgba(0,0,0,.9);



transform:


perspective(600px)

rotateX(55deg);


text-shadow:

0 3px 5px black;


}




/* Ärmel */


.jersey::before{


content:"";


position:absolute;


top:-7px;


left:10px;


width:50px;


height:15px;


background:inherit;


border-radius:12px;


}



/* Schatten unter Trikot */


.jersey::after{


content:"";


position:absolute;


bottom:-15px;


left:5px;


width:60px;


height:15px;


background:

rgba(0,0,0,.5);


filter:blur(8px);


border-radius:50%;


}




.player-name{


margin-top:10px;


background:

rgba(0,0,0,.85);


padding:

6px 12px;


border-radius:10px;


font-size:14px;


font-weight:bold;


white-space:nowrap;


box-shadow:

0 5px 15px black;


}







</style>

</head>


<body>



<h1>
Wettpropheten Aufstellung
</h1>



<div class="layout">



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


<input id="homeColor" type="color" value="#cc0000">



<label>
Nummernfarbe
</label>


<input id="homeNumberColor" type="color" value="#ffffff">


</div>





<div class="field home-field" id="homeField">

</div>




<div></div>




<div class="field away-field" id="awayField">

</div>





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


<input id="awayColor" type="color" value="#004cff">



<label>
Nummernfarbe
</label>


<input id="awayNumberColor" type="color" value="#ffffff">


</div>
</div>


<script>


const teams={


"Bayern München":[

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
"Tah",
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
"Simakan",
"Raum",
"Schlager",
"Seiwald",
"Olmo",
"Simons",
"Openda",
"Sesko"

]


};





const formations={


"4-3-3":[

[50,88],

[20,70],
[40,75],
[60,75],
[80,70],

[35,52],
[50,45],
[65,52],

[25,25],
[50,18],
[75,25]

],



"4-4-2":[

[50,88],

[20,70],
[40,75],
[60,75],
[80,70],

[20,50],
[40,45],
[60,45],
[80,50],

[40,25],
[60,25]

],



"3-5-2":[

[50,88],

[30,70],
[50,76],
[70,70],

[20,52],
[35,45],
[50,55],
[65,45],
[80,52],

[40,25],
[60,25]

]


};






function drawTeam(side){


let field;

let team;

let formation;

let color;

let numberColor;




if(side==="home"){


field=document.getElementById("homeField");

team=document.getElementById("homeTeam").value;

formation=document.getElementById("homeFormation").value;

color=document.getElementById("homeColor").value;

numberColor=document.getElementById("homeNumberColor").value;


}


else{


field=document.getElementById("awayField");

team=document.getElementById("awayTeam").value;

formation=document.getElementById("awayFormation").value;

color=document.getElementById("awayColor").value;

numberColor=document.getElementById("awayNumberColor").value;


}




field.innerHTML="";




formations[formation].forEach((pos,index)=>{


let x=pos[0];

let y=pos[1];



if(side==="away"){


x=100-x;


}



let div=document.createElement("div");


div.className="player";


div.style.left=x+"%";

div.style.top=y+"%";



div.innerHTML=`

<div class="jersey"

style="background:${color};color:${numberColor}">

${index+1}

</div>


<div class="player-name">

${teams[team][index]}

</div>

`;



field.appendChild(div);


});



}






document

.querySelectorAll("select,input")

.forEach(item=>{


item.addEventListener("change",()=>{


drawTeam("home");

drawTeam("away");


});


});





drawTeam("home");

drawTeam("away");

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

linear-gradient(135deg,#061522,#075c35);

color:white;

}




h1{

text-align:center;

font-size:34px;

margin:0 0 15px;

}





.layout{


width:100%;


height:85vh;


display:grid;


grid-template-columns:


190px

minmax(0,1fr)

35px

minmax(0,1fr)

190px;


gap:10px;


align-items:center;


}





.card{


height:560px;


background:

rgba(255,255,255,.12);


border:

1px solid rgba(255,255,255,.3);


border-radius:20px;


padding:15px;


box-shadow:

0 20px 50px black;


}




.card h2{

text-align:center;

margin:5px 0 15px;

}




.logo-box{


height:70px;


display:flex;


align-items:center;


justify-content:center;


font-size:24px;


font-weight:bold;


margin-bottom:15px;


background:

rgba(0,0,0,.3);


border-radius:12px;


}





label{

display:block;

margin-top:8px;

font-size:14px;

}



select,
input{


width:100%;


padding:10px;


margin-top:5px;


margin-bottom:10px;


border-radius:10px;


border:none;


background:#111;


color:white;


}






.field{


height:700px;


position:relative;


overflow:hidden;


background:


linear-gradient(

90deg,

#16833d,

#22964e

);



border:

3px solid white;


box-shadow:

0 25px 60px black;


}




.home-field{


border-radius:

25px 0 0 25px;


transform:

perspective(1200px)

rotateY(10deg)

rotateX(10deg);


}




.away-field{


border-radius:

0 25px 25px 0;


transform:

perspective(1200px)

rotateY(-10deg)

rotateX(10deg);


}




.home-field::after{

content:"";

position:absolute;

right:0;

top:0;

height:100%;

width:3px;

background:white;

}




.away-field::before{

content:"";

position:absolute;

left:0;

top:0;

height:100%;

width:3px;

background:white;

}

.home-field::before{

content:"";

position:absolute;

right:-85px;

top:50%;

width:170px;

height:170px;


border:

3px solid white;


border-radius:50%;


transform:

translateY(-50%);

}





.away-field::after{

content:"";

position:absolute;

left:-85px;

top:50%;

width:170px;

height:170px;


border:

3px solid white;


border-radius:50%;


transform:

translateY(-50%);

}







.player{


position:absolute;


transform:

translate(-50%,-50%);


text-align:center;


z-index:5;


}



.jersey{


width:70px;


height:82px;


display:flex;


align-items:center;


justify-content:center;


font-size:26px;


font-weight:bold;


border-radius:


22px 22px 15px 15px;


box-shadow:

0 25px 45px black;


transform:

perspective(600px)

rotateX(55deg);


}



.player-name{


margin-top:10px;


background:

rgba(0,0,0,.85);


padding:

6px 12px;


border-radius:10px;


font-size:14px;


font-weight:bold;


white-space:nowrap;


}





</style>


</head>



<body>



<h1>
Wettpropheten Aufstellung
</h1>




<div class="layout">





<!-- HEIM KARTE -->


<div class="card">


<h2>Heim</h2>



<div class="logo-box" id="homeLogo">

HEIM

</div>



<label>
Verein
</label>



<select id="homeTeam">


<option>Bayern München</option>

<option>Borussia Dortmund</option>

<option>Bayer Leverkusen</option>

<option>RB Leipzig</option>

<option>Eintracht Frankfurt</option>

<option>VfB Stuttgart</option>

<option>SC Freiburg</option>

<option>Mainz 05</option>

<option>Werder Bremen</option>

<option>FC Augsburg</option>

<option>VfL Wolfsburg</option>

<option>Union Berlin</option>

<option>Gladbach</option>

<option>Hoffenheim</option>

<option>St. Pauli</option>

<option>Heidenheim</option>

<option>Hamburg</option>

<option>Köln</option>


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



<input id="homeColor" type="color" value="#cc0000">



<label>
Nummernfarbe
</label>



<input id="homeNumberColor" type="color" value="#ffffff">


</div>







<!-- HEIM FELD -->

<div class="field home-field" id="homeField">

</div>







<div></div>







<!-- GAST FELD -->


<div class="field away-field" id="awayField">

</div>








<!-- GAST KARTE -->

<div class="card">


<h2>Gast</h2>




<div class="logo-box" id="awayLogo">

GAST

</div>



<label>
Verein
</label>



<select id="awayTeam">


<option>Borussia Dortmund</option>

<option>Bayern München</option>

<option>Bayer Leverkusen</option>

<option>RB Leipzig</option>

<option>Eintracht Frankfurt</option>

<option>VfB Stuttgart</option>

<option>SC Freiburg</option>

<option>Mainz 05</option>

<option>Werder Bremen</option>

<option>FC Augsburg</option>

<option>VfL Wolfsburg</option>

<option>Union Berlin</option>

<option>Gladbach</option>

<option>Hoffenheim</option>

<option>St. Pauli</option>

<option>Heidenheim</option>

<option>Hamburg</option>

<option>Köln</option>


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


<input id="awayColor" type="color" value="#004cff">



<label>
Nummernfarbe
</label>


<input id="awayNumberColor" type="color" value="#ffffff">



</div>




</div>





<script>



const teams={


"Bayern München":[

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
"Tah",
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
"Simakan",
"Raum",
"Schlager",
"Seiwald",
"Simons",
"Openda",
"Sesko",
"Olmo"

]

};



const formations={


"4-3-3":[

[50,88],

[20,70],
[40,75],
[60,75],
[80,70],

[35,52],
[50,45],
[65,52],

[25,25],
[50,18],
[75,25]

],



"4-4-2":[

[50,88],

[20,70],
[40,75],
[60,75],
[80,70],

[20,50],
[40,45],
[60,45],
[80,50],

[40,25],
[60,25]

],



"3-5-2":[

[50,88],

[30,70],
[50,76],
[70,70],

[20,52],
[35,45],
[50,55],
[65,45],
[80,52],

[40,25],
[60,25]

]


};



function drawTeam(side){


let field;

let team;

let formation;

let color;

let numberColor;



if(side==="home"){


field=document.getElementById("homeField");

team=document.getElementById("homeTeam").value;

formation=document.getElementById("homeFormation").value;

color=document.getElementById("homeColor").value;

numberColor=document.getElementById("homeNumberColor").value;


}

else{


field=document.getElementById("awayField");

team=document.getElementById("awayTeam").value;

formation=document.getElementById("awayFormation").value;

color=document.getElementById("awayColor").value;

numberColor=document.getElementById("awayNumberColor").value;


}



field.innerHTML="";



formations[formation].forEach((pos,index)=>{


let x=pos[0];

let y=pos[1];



if(side==="away"){

x=100-x;

}




let player=document.createElement("div");


player.className="player";


player.style.left=x+"%";

player.style.top=y+"%";



player.innerHTML=`

<div class="jersey"

style="background:${color};color:${numberColor}">

${index+1}

</div>


<div class="player-name">

${teams[team][index] || "Spieler"}

</div>

`;



field.appendChild(player);



});



}




document

.querySelectorAll("select,input")

.forEach(element=>{


element.addEventListener("change",()=>{


drawTeam("home");

drawTeam("away");


});


});





drawTeam("home");

drawTeam("away");


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

linear-gradient(135deg,#061522,#075c35);

color:white;

}




h1{

text-align:center;

font-size:34px;

margin:0 0 15px;

}





.layout{


width:100%;

height:85vh;


display:grid;


grid-template-columns:


220px

minmax(0,1fr)

35px

minmax(0,1fr)

220px;


gap:10px;


align-items:center;


}





.card{


height:600px;


background:

rgba(255,255,255,.12);


border:

1px solid rgba(255,255,255,.3);


border-radius:20px;


padding:15px;


box-shadow:

0 20px 50px black;


overflow:auto;


}





.card h2{


text-align:center;


}




select,
input,
button{


width:100%;


padding:10px;


margin-top:8px;


border-radius:10px;


border:none;


background:#111;


color:white;


}




button{


background:#0b8f45;


cursor:pointer;


font-weight:bold;


}





.field{


height:700px;


position:relative;


overflow:hidden;


background:

linear-gradient(

90deg,

#16833d,

#22964e

);


border:

3px solid white;


box-shadow:

0 25px 60px black;


}





.home-field{


border-radius:

25px 0 0 25px;


transform:

perspective(1200px)

rotateY(10deg)

rotateX(10deg);


}



.away-field{


border-radius:

0 25px 25px 0;


transform:

perspective(1200px)

rotateY(-10deg)

rotateX(10deg);


}




.home-field::after{

content:"";

position:absolute;

right:0;

height:100%;

width:3px;

background:white;

}




.away-field::before{

content:"";

position:absolute;

left:0;

height:100%;

width:3px;

background:white;

}

.home-field::before{

content:"";

position:absolute;

right:-85px;

top:50%;

width:170px;

height:170px;

border:

3px solid white;

border-radius:50%;


transform:

translateY(-50%);

}



.away-field::after{

content:"";

position:absolute;

left:-85px;

top:50%;

width:170px;

height:170px;

border:

3px solid white;

border-radius:50%;


transform:

translateY(-50%);

}




.player{


position:absolute;


transform:

translate(-50%,-50%);


text-align:center;


z-index:5;


}



.jersey{


width:70px;


height:82px;


display:flex;


align-items:center;


justify-content:center;


font-size:26px;


font-weight:bold;


border-radius:


22px 22px 15px 15px;


box-shadow:

0 25px 45px black;


transform:

perspective(600px)

rotateX(55deg);


}



.player-name{


margin-top:10px;


background:

rgba(0,0,0,.85);


padding:

6px 12px;


border-radius:10px;


font-size:14px;


font-weight:bold;


white-space:nowrap;


}





</style>

</head>



<body>



<h1>
Wettpropheten Aufstellung
</h1>




<div class="layout">





<div class="card">


<h2>Heim</h2>



<select id="homeTeam">


<option>Bayern München</option>

<option>Borussia Dortmund</option>

<option>Bayer Leverkusen</option>

<option>RB Leipzig</option>

</select>



<label>
Formation
</label>


<select id="homeFormation">


<option>4-3-3</option>

<option>4-4-2</option>

<option>3-5-2</option>


</select>




<h3>Spieler ändern</h3>


<input id="h1" placeholder="Spieler 1">

<input id="h2" placeholder="Spieler 2">

<input id="h3" placeholder="Spieler 3">

<input id="h4" placeholder="Spieler 4">

<input id="h5" placeholder="Spieler 5">



</div>






<div class="field home-field" id="homeField">


</div>






<div></div>






<div class="field away-field" id="awayField">


</div>







<div class="card">


<h2>Gast</h2>




<select id="awayTeam">


<option>Borussia Dortmund</option>

<option>Bayern München</option>

<option>Bayer Leverkusen</option>

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




<h3>Spieler ändern</h3>


<input id="a1" placeholder="Spieler 1">

<input id="a2" placeholder="Spieler 2">

<input id="a3" placeholder="Spieler 3">

<input id="a4" placeholder="Spieler 4">

<input id="a5" placeholder="Spieler 5">


<button id="save">

Speichern

</button>



</div>



</div>

<script>


const defaultPlayers={


"Bayern München":[

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
"Tah",
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
"Simakan",
"Raum",
"Schlager",
"Seiwald",
"Simons",
"Openda",
"Sesko",
"Olmo"

]


};




const positions={


"4-3-3":[

[50,88],

[20,70],
[40,75],
[60,75],
[80,70],

[35,52],
[50,45],
[65,52],

[25,25],
[50,18],
[75,25]

],



"4-4-2":[

[50,88],

[20,70],
[40,75],
[60,75],
[80,70],

[20,50],
[40,45],
[60,45],
[80,50],

[40,25],
[60,25]

],



"3-5-2":[

[50,88],

[30,70],
[50,76],
[70,70],

[20,52],
[35,45],
[50,55],
[65,45],
[80,52],

[40,25],
[60,25]

]


};





function getPlayers(team,side){


let players=[...defaultPlayers[team]];



if(side==="home"){


for(let i=0;i<5;i++){


let value=document.getElementById("h"+(i+1)).value;


if(value){

players[i]=value;

}


}


}



else{


for(let i=0;i<5;i++){


let value=document.getElementById("a"+(i+1)).value;


if(value){

players[i]=value;

}


}


}



return players;


}





function draw(side){



let field;

let team;

let formation;



if(side==="home"){


field=document.getElementById("homeField");

team=document.getElementById("homeTeam").value;

formation=document.getElementById("homeFormation").value;


}

else{


field=document.getElementById("awayField");

team=document.getElementById("awayTeam").value;

formation=document.getElementById("awayFormation").value;


}



field.innerHTML="";



let players=getPlayers(team,side);




positions[formation].forEach((p,i)=>{


let x=p[0];

let y=p[1];



if(side==="away"){

x=100-x;

}




let player=document.createElement("div");


player.className="player";


player.style.left=x+"%";

player.style.top=y+"%";



player.innerHTML=`

<div class="jersey">

${i+1}

</div>

<div class="player-name">

${players[i]}

</div>

`;



field.appendChild(player);



});



}




function saveData(){


localStorage.setItem(

"heimSpieler",

JSON.stringify(

[

h1.value,

h2.value,

h3.value,

h4.value,

h5.value

]

)

);



localStorage.setItem(

"gastSpieler",

JSON.stringify(

[

a1.value,

a2.value,

a3.value,

a4.value,

a5.value

]

)

);



alert("Gespeichert");


}





save.onclick=saveData;




document

.querySelectorAll("select,input")

.forEach(e=>{


e.addEventListener("change",()=>{


draw("home");

draw("away");


});


});



draw("home");

draw("away");


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

linear-gradient(135deg,#061522,#075c35);


color:white;


}




h1{


text-align:center;


font-size:34px;


margin:0 0 10px;


}





.topbar{


width:100%;


display:flex;


justify-content:center;


gap:15px;


margin-bottom:10px;


}



.topbar select{


width:300px;


}




.layout{


width:100%;


height:82vh;


display:grid;


grid-template-columns:


220px

minmax(0,1fr)

35px

minmax(0,1fr)

220px;


gap:10px;


align-items:center;


}





.card{


height:600px;


background:

rgba(255,255,255,.12);


border:

1px solid rgba(255,255,255,.3);


border-radius:20px;


padding:15px;


box-shadow:

0 20px 50px black;


overflow:auto;


}




.card h2{

text-align:center;

}




select,
input,
button{


width:100%;


padding:10px;


margin-top:8px;


border-radius:10px;


border:none;


background:#111;


color:white;


}





button{


background:#0b8f45;


font-weight:bold;


cursor:pointer;


}

.field{


height:700px;


position:relative;


overflow:hidden;


background:

linear-gradient(

90deg,

#16833d,

#22964e

);


border:

3px solid white;


box-shadow:

0 25px 60px black;


}



.home-field{


border-radius:

25px 0 0 25px;


transform:

perspective(1200px)

rotateY(10deg)

rotateX(10deg);


}




.away-field{


border-radius:

0 25px 25px 0;


transform:

perspective(1200px)

rotateY(-10deg)

rotateX(10deg);


}





.home-field::after{

content:"";

position:absolute;

right:0;

height:100%;

width:3px;

background:white;

}




.away-field::before{

content:"";

position:absolute;

left:0;

height:100%;

width:3px;

background:white;

}




.home-field::before{


content:"";


position:absolute;


right:-85px;


top:50%;


width:170px;


height:170px;


border:

3px solid white;


border-radius:50%;


transform:

translateY(-50%);


}




.away-field::after{


content:"";


position:absolute;


left:-85px;


top:50%;


width:170px;


height:170px;


border:

3px solid white;


border-radius:50%;


transform:

translateY(-50%);


}






.player{


position:absolute;


transform:

translate(-50%,-50%);


text-align:center;


z-index:5;


}



.jersey{


width:70px;


height:82px;


display:flex;


align-items:center;


justify-content:center;


font-size:26px;


font-weight:bold;


border-radius:


22px 22px 15px 15px;


box-shadow:

0 25px 45px black;


transform:

perspective(600px)

rotateX(55deg);


}



.player-name{


margin-top:10px;


background:

rgba(0,0,0,.85);


padding:

6px 12px;


border-radius:10px;


font-size:14px;


font-weight:bold;


white-space:nowrap;


}



</style>


</head>



<body>


<h1>
Wettpropheten Konferenz
</h1>



<div class="topbar">


<select id="gameSelect">


<option value="game1">

Bayern München - Borussia Dortmund

</option>


<option value="game2">

Bayer Leverkusen - RB Leipzig

</option>


<option value="game3">

Eintracht Frankfurt - VfB Stuttgart

</option>


</select>


</div>





<div class="layout">



<div class="card">


<h2 id="homeTitle">

Heim

</h2>



<select id="homeTeam">

<option>Bayern München</option>

<option>Bayer Leverkusen</option>

<option>Eintracht Frankfurt</option>

</select>



<label>
Formation
</label>


<select id="homeFormation">

<option>4-3-3</option>

<option>4-4-2</option>

<option>3-5-2</option>


</select>




</div>





<div class="field home-field" id="homeField">


</div>





<div></div>




<div class="field away-field" id="awayField">


</div>





<div class="card">


<h2 id="awayTitle">

Gast

</h2>



<select id="awayTeam">


<option>Borussia Dortmund</option>

<option>RB Leipzig</option>

<option>VfB Stuttgart</option>

</select>



<label>
Formation
</label>


<select id="awayFormation">


<option>4-3-3</option>

<option>4-4-2</option>

<option>3-5-2</option>


</select>


</div>

<script>


const games={


game1:{


home:"Bayern München",

away:"Borussia Dortmund"


},



game2:{


home:"Bayer Leverkusen",

away:"RB Leipzig"


},



game3:{


home:"Eintracht Frankfurt",

away:"VfB Stuttgart"


}



};





const squads={


"Bayern München":[

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
"Tah",
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
"Simakan",
"Raum",
"Schlager",
"Seiwald",
"Simons",
"Openda",
"Sesko",
"Olmo"

],



"Eintracht Frankfurt":[

"Trapp",
"Tuta",
"Koch",
"Theate",
"Larsson",
"Skhiri",
"Gotze",
"Chaibi",
"Marmoush",
"Ekitike",
"Knauff"

],



"VfB Stuttgart":[

"Nubel",
"Vagnoman",
"Chabot",
"Rouault",
"Mittelstadt",
"Stiller",
"Karazor",
"Millot",
"Undav",
"Demirovic",
"Fuhrich"

]


};






const formation={


"4-3-3":[

[50,88],

[20,70],
[40,75],
[60,75],
[80,70],

[35,52],
[50,45],
[65,52],

[25,25],
[50,18],
[75,25]

]


};






function draw(side){


let field;


let team;



if(side==="home"){


field=document.getElementById("homeField");

team=document.getElementById("homeTeam").value;


}

else{


field=document.getElementById("awayField");

team=document.getElementById("awayTeam").value;


}



field.innerHTML="";



formation["4-3-3"].forEach((p,i)=>{


let x=p[0];

let y=p[1];



if(side==="away"){

x=100-x;

}



let div=document.createElement("div");


div.className="player";


div.style.left=x+"%";

div.style.top=y+"%";



div.innerHTML=`

<div class="jersey"

style="background:${side==="home"?"#c90000":"#004cff"}">

${i+1}

</div>


<div class="player-name">

${squads[team][i] || "Spieler"}

</div>

`;



field.appendChild(div);


});



}






function loadGame(){


let game=

games[gameSelect.value];



homeTeam.value=game.home;

awayTeam.value=game.away;



homeTitle.innerHTML=game.home;


awayTitle.innerHTML=game.away;



draw("home");

draw("away");


}





gameSelect.addEventListener(

"change",

loadGame

);




homeTeam.addEventListener(

"change",

()=>draw("home")

);



awayTeam.addEventListener(

"change",

()=>draw("away")

);



loadGame();

<!DOCTYPE html>
<html lang="de">

<head>

<meta charset="UTF-8">

<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Wettpropheten Konferenz</title>


<style>


*{
box-sizing:border-box;
}



body{


margin:0;

padding:15px;


font-family:Arial,Helvetica,sans-serif;


background:

linear-gradient(135deg,#061522,#075c35);


color:white;


}




h1{


text-align:center;


font-size:34px;


margin:5px;


}




.conference{


width:100%;


display:grid;


grid-template-columns:

repeat(3,1fr);


gap:15px;


margin-bottom:15px;


}




.match-card{


background:

rgba(255,255,255,.12);


border:

1px solid rgba(255,255,255,.25);


border-radius:18px;


padding:20px;


text-align:center;


cursor:pointer;


box-shadow:

0 15px 40px black;


transition:.3s;


}



.match-card:hover{


transform:scale(1.05);


}




.team{


font-size:22px;


font-weight:bold;


}



.score{


font-size:35px;


margin:15px;


}



.minute{


font-size:18px;


color:#ddd;


}






.main{


display:grid;


grid-template-columns:


220px

minmax(0,1fr)

35px

minmax(0,1fr)

220px;


gap:10px;


height:78vh;


}





.card{


background:

rgba(255,255,255,.12);


border-radius:20px;


padding:15px;


box-shadow:

0 20px 50px black;


overflow:auto;


}

.field{


height:700px;


position:relative;


overflow:hidden;


background:

linear-gradient(

90deg,

#16833d,

#22964e

);


border:

3px solid white;


box-shadow:

0 25px 60px black;


}





.home-field{


border-radius:

25px 0 0 25px;


transform:

perspective(1200px)

rotateY(10deg)

rotateX(10deg);


}





.away-field{


border-radius:

0 25px 25px 0;


transform:

perspective(1200px)

rotateY(-10deg)

rotateX(10deg);


}






.home-field::after{


content:"";


position:absolute;


right:0;


top:0;


height:100%;


width:3px;


background:white;


}






.away-field::before{


content:"";


position:absolute;


left:0;


top:0;


height:100%;


width:3px;


background:white;


}





.home-field::before{


content:"";


position:absolute;


right:-85px;


top:50%;


width:170px;


height:170px;


border:

3px solid white;


border-radius:50%;


transform:

translateY(-50%);


}





.away-field::after{


content:"";


position:absolute;


left:-85px;


top:50%;


width:170px;


height:170px;


border:

3px solid white;


border-radius:50%;


transform:

translateY(-50%);


}





.player{


position:absolute;


transform:

translate(-50%,-50%);


text-align:center;


z-index:5;


}




.jersey{


width:70px;


height:82px;


display:flex;


align-items:center;


justify-content:center;


font-size:25px;


font-weight:bold;


border-radius:


20px 20px 12px 12px;


box-shadow:

0 25px 40px black;


transform:

perspective(600px)

rotateX(55deg);


}





.player-name{


margin-top:8px;


background:

rgba(0,0,0,.85);


padding:5px 10px;


border-radius:8px;


font-size:13px;


white-space:nowrap;


}




</style>


</head>


<body>



<h1>
Wettpropheten Samstag Konferenz
</h1>



<div class="conference">


<div class="match-card" onclick="selectGame(0)">


<div class="team">

Bayern München

</div>


<div class="score">

0 : 0

</div>


<div class="minute">

15. Minute

</div>


</div>





<div class="match-card" onclick="selectGame(1)">


<div class="team">

Bayer Leverkusen

</div>


<div class="score">

0 : 0

</div>


<div class="minute">

15. Minute

</div>


</div>





<div class="match-card" onclick="selectGame(2)">


<div class="team">

Eintracht Frankfurt

</div>


<div class="score">

0 : 0

</div>


<div class="minute">

15. Minute

</div>


</div>



</div>
<div class="main">



<div class="card">

<h2 id="homeName">

Heim

</h2>


<p>

Formation

</p>


<select id="homeFormation">

<option>4-3-3</option>

<option>4-4-2</option>

<option>3-5-2</option>

</select>



</div>





<div class="field home-field" id="homeField">


</div>






<div></div>






<div class="field away-field" id="awayField">


</div>







<div class="card">

<h2 id="awayName">

Gast

</h2>



<p>

Formation

</p>


<select id="awayFormation">

<option>4-3-3</option>

<option>4-4-2</option>

<option>3-5-2</option>

</select>


</div>




</div>





<script>



const games=[



{


home:"Bayern München",

away:"Borussia Dortmund"


},



{


home:"Bayer Leverkusen",

away:"RB Leipzig"


},



{


home:"Eintracht Frankfurt",

away:"VfB Stuttgart"


}



];





const players={



"Bayern München":[

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
"Tah",
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
"Simakan",
"Raum",
"Schlager",
"Seiwald",
"Simons",
"Openda",
"Sesko",
"Olmo"

],



"Eintracht Frankfurt":[

"Trapp",
"Tuta",
"Koch",
"Theate",
"Larsson",
"Skhiri",
"Gotze",
"Chaibi",
"Marmoush",
"Ekitike",
"Knauff"

],



"VfB Stuttgart":[

"Nubel",
"Vagnoman",
"Chabot",
"Rouault",
"Mittelstadt",
"Stiller",
"Karazor",
"Millot",
"Undav",
"Demirovic",
"Fuhrich"

]


};





const pos=[

[50,88],

[20,70],
[40,75],
[60,75],
[80,70],

[35,52],
[50,45],
[65,52],

[25,25],
[50,18],
[75,25]

];





function draw(side,team){


let field=


side==="home"

?

document.getElementById("homeField")

:

document.getElementById("awayField");




field.innerHTML="";




pos.forEach((p,i)=>{


let x=p[0];

let y=p[1];



if(side==="away"){

x=100-x;

}




let d=document.createElement("div");


d.className="player";


d.style.left=x+"%";

d.style.top=y+"%";



d.innerHTML=`

<div class="jersey"

style="background:${side==="home"?"#cc0000":"#004cff"}">

${i+1}

</div>


<div class="player-name">

${players[team][i]}

</div>

`;



field.appendChild(d);



});


}




function selectGame(id){


let game=games[id];



homeName.innerHTML=game.home;

awayName.innerHTML=game.away;



draw("home",game.home);

draw("away",game.away);



}




selectGame(0);

<!DOCTYPE html>
<html lang="de">

<head>

<meta charset="UTF-8">

<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Wettpropheten Live Konferenz</title>


<style>


*{
box-sizing:border-box;
}



body{


margin:0;

padding:15px;


font-family:Arial,Helvetica,sans-serif;


background:

linear-gradient(135deg,#061522,#075c35);


color:white;


}





h1{

text-align:center;

font-size:34px;

margin:5px;

}




.conference{


display:grid;


grid-template-columns:

repeat(3,1fr);


gap:15px;


margin-bottom:15px;


}





.match-card{


background:

rgba(255,255,255,.12);


border-radius:18px;


padding:15px;


text-align:center;


cursor:pointer;


box-shadow:

0 15px 40px black;


}





.match-card:hover{


transform:scale(1.04);


}




.team{


font-size:20px;


font-weight:bold;


}




.score{


font-size:38px;


font-weight:bold;


margin:10px;


}



.minute{


font-size:18px;


color:#ddd;


}




.control{


display:flex;


gap:10px;


justify-content:center;


margin-bottom:15px;


}



.control button{


padding:12px 20px;


border:none;


border-radius:10px;


background:#0b8f45;


color:white;


font-weight:bold;


cursor:pointer;


}




.layout{


display:grid;


grid-template-columns:


220px

minmax(0,1fr)

35px

minmax(0,1fr)

220px;


height:75vh;


gap:10px;


}

.card{


background:

rgba(255,255,255,.12);


border:

1px solid rgba(255,255,255,.25);


border-radius:20px;


padding:15px;


box-shadow:

0 20px 50px black;


overflow:auto;


}




.card h2{


text-align:center;


}




.event-box{


margin-top:20px;


background:

rgba(0,0,0,.35);


border-radius:12px;


padding:10px;


min-height:120px;


}




.event{


padding:8px;


border-bottom:

1px solid rgba(255,255,255,.2);


font-size:14px;


}





.field{


height:700px;


position:relative;


overflow:hidden;


background:

linear-gradient(

90deg,

#16833d,

#22964e

);


border:

3px solid white;


box-shadow:

0 25px 60px black;


}





.home-field{


border-radius:

25px 0 0 25px;


transform:

perspective(1200px)

rotateY(10deg)

rotateX(10deg);


}





.away-field{


border-radius:

0 25px 25px 0;


transform:

perspective(1200px)

rotateY(-10deg)

rotateX(10deg);


}





.home-field::after{


content:"";


position:absolute;


right:0;


height:100%;


width:3px;


background:white;


}





.away-field::before{


content:"";


position:absolute;


left:0;


height:100%;


width:3px;


background:white;


}





.player{


position:absolute;


transform:

translate(-50%,-50%);


text-align:center;


z-index:5;


}





.jersey{


width:70px;


height:82px;


display:flex;


align-items:center;


justify-content:center;


font-size:25px;


font-weight:bold;


border-radius:


22px 22px 15px 15px;


box-shadow:

0 25px 45px black;


transform:

perspective(600px)

rotateX(55deg);


}





.player-name{


margin-top:8px;


background:

rgba(0,0,0,.85);


padding:5px 10px;


border-radius:8px;


font-size:13px;


white-space:nowrap;


}





</style>


</head>



<body>


<h1>
Wettpropheten Live Konferenz
</h1>



<div class="conference">


<div class="match-card" onclick="loadGame(0)">


<div class="team">

Bayern München - Dortmund

</div>


<div class="score" id="score0">

0 : 0

</div>


<div class="minute" id="minute0">

15'

</div>


</div>




<div class="match-card" onclick="loadGame(1)">


<div class="team">

Leverkusen - Leipzig

</div>


<div class="score" id="score1">

0 : 0

</div>


<div class="minute" id="minute1">

15'

</div>


</div>




<div class="match-card" onclick="loadGame(2)">


<div class="team">

Frankfurt - Stuttgart

</div>


<div class="score" id="score2">

0 : 0

</div>


<div class="minute" id="minute2">

15'

</div>


</div>


</div>

<div class="control">


<button onclick="goalHome()">

Tor Heim

</button>


<button onclick="goalAway()">

Tor Gast

</button>


<button onclick="addMinute()">

+ Minute

</button>


</div>





<div class="layout">



<div class="card">


<h2 id="homeTitle">

Heim

</h2>


<div class="event-box" id="homeEvents">

</div>


</div>





<div class="field home-field" id="homeField">


</div>






<div></div>







<div class="field away-field" id="awayField">


</div>








<div class="card">


<h2 id="awayTitle">

Gast

</h2>


<div class="event-box" id="awayEvents">

</div>



</div>




</div>






<script>



const games=[


{

home:"Bayern München",

away:"Borussia Dortmund",

homeScore:0,

awayScore:0,

minute:15,

events:[]

},



{

home:"Bayer Leverkusen",

away:"RB Leipzig",

homeScore:0,

awayScore:0,

minute:15,

events:[]

},



{

home:"Eintracht Frankfurt",

away:"VfB Stuttgart",

homeScore:0,

awayScore:0,

minute:15,

events:[]

}



];




let activeGame=0;





const players={



"Bayern München":[

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
"Tah",
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
"Simakan",
"Raum",
"Schlager",
"Seiwald",
"Simons",
"Openda",
"Sesko",
"Olmo"

],



"Eintracht Frankfurt":[

"Trapp",
"Tuta",
"Koch",
"Theate",
"Larsson",
"Skhiri",
"Gotze",
"Chaibi",
"Marmoush",
"Ekitike",
"Knauff"

],



"VfB Stuttgart":[

"Nubel",
"Vagnoman",
"Chabot",
"Rouault",
"Mittelstadt",
"Stiller",
"Karazor",
"Millot",
"Undav",
"Demirovic",
"Fuhrich"

]


};





const positions=[

[50,88],

[20,70],
[40,75],
[60,75],
[80,70],

[35,52],
[50,45],
[65,52],

[25,25],
[50,18],
[75,25]

];







function draw(side,team){



let field=


side==="home"

?

homeField

:

awayField;



field.innerHTML="";





positions.forEach((p,i)=>{


let x=p[0];

let y=p[1];



if(side==="away"){

x=100-x;

}



let player=document.createElement("div");


player.className="player";


player.style.left=x+"%";

player.style.top=y+"%";



player.innerHTML=`

<div class="jersey"

style="background:${side==="home"?"#cc0000":"#004cff"}">

${i+1}

</div>


<div class="player-name">

${players[team][i]}

</div>

`;



field.appendChild(player);


});



}







function loadGame(id){


activeGame=id;


let game=games[id];


homeTitle.innerHTML=game.home;


awayTitle.innerHTML=game.away;



draw("home",game.home);

draw("away",game.away);



}





function updateScore(){


let g=games[activeGame];


document.getElementById(

"score"+activeGame

).innerHTML=

g.homeScore+" : "+g.awayScore;



document.getElementById(

"minute"+activeGame

).innerHTML=

g.minute+"'";


}




function addEvent(text){


let g=games[activeGame];


g.events.push(text);



homeEvents.innerHTML=

g.events.map(e=>"<div class='event'>"+e+"</div>").join("");



}






function goalHome(){


games[activeGame].homeScore++;


updateScore();


addEvent(

"⚽ Tor Heim "

+games[activeGame].home

);


}





function goalAway(){


games[activeGame].awayScore++;


updateScore();


addEvent(

"⚽ Tor Gast "

+games[activeGame].away

);


}





function addMinute(){


games[activeGame].minute++;


updateScore();


}




loadGame(0);

<!DOCTYPE html>
<html lang="de">

<head>

<meta charset="UTF-8">

<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Wettpropheten TV Aufstellung</title>


<style>


*{

box-sizing:border-box;

}



body{


margin:0;

padding:15px;


font-family:Arial,Helvetica,sans-serif;


background:

linear-gradient(135deg,#061522,#075c35);


color:white;


}





h1{


text-align:center;


font-size:34px;


margin-bottom:20px;


}





.tv-layout{


display:grid;


grid-template-columns:


260px

1fr

260px;


gap:15px;


width:100%;


height:85vh;


}




.team-card{


background:

rgba(255,255,255,.12);


border:

1px solid rgba(255,255,255,.3);


border-radius:22px;


padding:18px;


box-shadow:

0 20px 50px black;


}




.badge{


width:90px;


height:90px;


margin:auto;


display:flex;


align-items:center;


justify-content:center;


background:

rgba(0,0,0,.4);


border-radius:50%;


font-size:32px;


font-weight:bold;


}





.club-name{


text-align:center;


font-size:22px;


font-weight:bold;


margin:15px 0;


}




.info{


background:

rgba(0,0,0,.35);


padding:10px;


border-radius:12px;


margin-top:10px;


}





.info span{


display:block;


margin:5px 0;


}





.bank{


margin-top:15px;


background:

rgba(0,0,0,.3);


border-radius:12px;


padding:10px;


}




.bank h3{


margin:0 0 8px;


}


.bank-player{


padding:6px;


border-bottom:

1px solid rgba(255,255,255,.2);


font-size:14px;


}





.stadium{


background:

rgba(0,0,0,.25);


border-radius:20px;


padding:10px;


height:100%;


}





.scoreboard{


height:80px;


display:flex;


align-items:center;


justify-content:center;


gap:30px;


background:

rgba(0,0,0,.4);


border-radius:15px;


font-size:30px;


font-weight:bold;


}





.field{


margin-top:15px;


height:650px;


position:relative;


background:


linear-gradient(

90deg,

#16833d,

#22964e

);


border:

3px solid white;


box-shadow:

0 25px 60px black;


overflow:hidden;


}




.field::before{


content:"";


position:absolute;


left:50%;


top:0;


height:100%;


width:3px;


background:white;


}





.field::after{


content:"";


position:absolute;


left:50%;


top:50%;


width:150px;


height:150px;


border:

3px solid white;


border-radius:50%;


transform:

translate(-50%,-50%);


}




.player{


position:absolute;


transform:

translate(-50%,-50%);


text-align:center;


z-index:5;


}




.jersey{


width:70px;


height:82px;


display:flex;


align-items:center;


justify-content:center;


font-size:26px;


font-weight:bold;


border-radius:


20px 20px 15px 15px;


box-shadow:

0 25px 45px black;


transform:

perspective(600px)

rotateX(55deg);


}




.captain{


border:

4px solid gold;


}





.player-name{


background:

rgba(0,0,0,.85);


padding:

5px 10px;


margin-top:8px;


border-radius:10px;


font-size:13px;


white-space:nowrap;


}


</style>


</head>



<body>


<h1>
Wettpropheten TV Aufstellung
</h1>





<div class="tv-layout">





<div class="team-card">


<div class="badge" id="homeBadge">

H

</div>



<div class="club-name" id="homeClub">

Heim

</div>




<div class="info">


<span>
Trainer:
<b id="homeCoach">

Trainer

</b>
</span>


<span>
Kapitän:
<b id="homeCaptain">

Kapitän

</b>
</span>


</div>





<div class="bank">


<h3>
Bank
</h3>


<div class="bank-player">

Ersatz 1

</div>


<div class="bank-player">

Ersatz 2

</div>


<div class="bank-player">

Ersatz 3

</div>


<div class="bank-player">

Ersatz 4

</div>


<div class="bank-player">

Ersatz 5

</div>


</div>



</div>





<div class="stadium">



<div class="scoreboard">


<span id="leftScore">

0

</span>


:


<span id="rightScore">

0

</span>



</div>



<div class="field" id="field">


</div>



</div>





<div class="team-card">


<div class="badge" id="awayBadge">

G

</div>



<div class="club-name" id="awayClub">

Gast

</div>



<div class="info">


<span>
Trainer:
<b id="awayCoach">

Trainer

</b>
</span>


<span>
Kapitän:
<b id="awayCaptain">

Kapitän

</b>
</span>


</div>





<div class="bank">


<h3>
Bank
</h3>


<div class="bank-player">

Ersatz 1

</div>


<div class="bank-player">

Ersatz 2

</div>


<div class="bank-player">

Ersatz 3

</div>


<div class="bank-player">

Ersatz 4

</div>


<div class="bank-player">

Ersatz 5

</div>


</div>



</div>

<script>


const clubs={


"Bayern München":{


short:"FCB",

coach:"Vincent Kompany",

captain:"Manuel Neuer",

color:"#cc0000",

players:[

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

],

bank:[

"Ulreich",
"Laimer",
"Boey",
"Tel",
"Coman"

]

},




"Borussia Dortmund":{


short:"BVB",

coach:"Nuri Sahin",

captain:"Emre Can",

color:"#f0d000",

players:[

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

bank:[

"Meyer",
"Gross",
"Duranville",
"Beier",
"Reyna"

]

},





"Bayer Leverkusen":{


short:"B04",

coach:"Xabi Alonso",

captain:"Granit Xhaka",

color:"#e00000",

players:[

"Hradecky",
"Tapsoba",
"Tah",
"Grimaldo",
"Frimpong",
"Xhaka",
"Wirtz",
"Hofmann",
"Boniface",
"Schick",
"Adli"

],

bank:[

"Kovar",
"Andrich",
"Palacios",
"Terrier",
"Garcia"

]

}



};





const position=[


[50,88],

[20,70],
[40,75],
[60,75],
[80,70],

[35,52],
[50,45],
[65,52],

[25,25],
[50,18],
[75,25]


];







function loadTeam(side,name){


let club=clubs[name];



if(side==="home"){


homeClub.innerHTML=name;

homeBadge.innerHTML=club.short;

homeCoach.innerHTML=club.coach;

homeCaptain.innerHTML=club.captain;


}



else{


awayClub.innerHTML=name;

awayBadge.innerHTML=club.short;

awayCoach.innerHTML=club.coach;

awayCaptain.innerHTML=club.captain;


}




}





function draw(){


field.innerHTML="";



let home=clubs["Bayern München"];

let away=clubs["Borussia Dortmund"];





position.forEach((p,i)=>{


let player=document.createElement("div");


player.className="player";


player.style.left=p[0]+"%";

player.style.top=p[1]+"%";



player.innerHTML=`

<div class="jersey ${i===0?"captain":""}"

style="background:${i<11?home.color:"#333"}">

${i+1}

</div>


<div class="player-name">

${home.players[i]}

</div>


`;



field.appendChild(player);


});



}





loadTeam(

"home",

"Bayern München"

);


loadTeam(

"away",

"Borussia Dortmund"

);



draw();



</script>


</body>

</html>
