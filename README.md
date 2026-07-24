<!DOCTYPE html>
<html lang="de">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Wettpropheten Taktik Board Pro</title>

<style>

*{
    box-sizing:border-box;
}

body{
    margin:0;
    min-height:100vh;
    padding:25px;
    font-family:Arial, Helvetica, sans-serif;
    color:white;

    background:
    linear-gradient(
        135deg,
        rgba(255,255,255,.04) 25%,
        transparent 25%,
        transparent 50%,
        rgba(255,255,255,.04) 50%
    );

    background-size:45px 45px;
    background-color:#061936;
}


.board{

    max-width:1400px;
    margin:auto;

}


/* =========================
 HEADER
========================= */


.top-header{

    display:flex;
    align-items:center;
    justify-content:center;
    gap:25px;
    margin-bottom:40px;

}



.team-box{

    height:70px;
    width:42%;

    background:white;
    border-radius:40px;

    display:flex;
    align-items:center;

    padding:10px 25px;

    box-shadow:
    0 10px 30px rgba(0,0,0,.5);

}



.team-box.right{

    flex-direction:row-reverse;

}


.logo{

    width:55px;
    height:55px;

    border-radius:50%;

    background:
    linear-gradient(
    135deg,
    #eeeeee,
    #aaaaaa
    );

    display:flex;
    align-items:center;
    justify-content:center;

    overflow:hidden;

    position:relative;

}



.logo span{

    font-size:25px;

}



.logo img{

    width:100%;
    height:100%;

    object-fit:cover;

}



.logo input{

    position:absolute;
    width:100%;
    height:100%;

    opacity:0;
    cursor:pointer;

}



.team-name{

    width:100%;

    border:0;
    outline:0;

    text-align:center;

    font-size:28px;

    font-weight:900;

    color:#12305c;

    text-transform:uppercase;

}



.vs{

    background:
    linear-gradient(
    #008cff,
    #004bdb
    );

    padding:15px 35px;

    border-radius:20px;

    font-size:32px;

    font-weight:900;

    box-shadow:
    0 0 25px #008cff;

}




/* =========================
 SPIELFELDER
========================= */


.pitch-container{

    display:grid;

    grid-template-columns:1fr 1fr;

    gap:40px;

}



.pitch-card{

    background:#102952;

    padding:20px;

    border-radius:20px;

    box-shadow:
    0 15px 40px rgba(0,0,0,.5);

}



.pitch{


    height:500px;

    border:4px solid rgba(255,255,255,.8);

    border-radius:12px;


    background:

    repeating-linear-gradient(
    0deg,
    #309b32 0px,
    #309b32 60px,
    #28862c 60px,
    #28862c 120px
    );


    position:relative;

    overflow:hidden;

}



/* Mittellinie */


.pitch:before{

content:"";

position:absolute;

left:50%;
top:0;

width:3px;
height:100%;

background:white;

transform:translateX(-50%);

opacity:.7;

}



.pitch:after{

content:"";

position:absolute;

left:50%;
top:50%;

width:100px;
height:100px;

border:3px solid white;

border-radius:50%;

transform:translate(-50%,-50%);

}



/* Strafräume */


.goal-area{

position:absolute;

width:180px;
height:80px;

border:3px solid white;

left:50%;

transform:translateX(-50%);

}



.top{

top:0;

}



.bottom{

bottom:0;

}




/* =========================
 SPIELER
========================= */


.player{

position:absolute;

width:80px;

text-align:center;

}



.shirt{


width:38px;
height:38px;

border-radius:50%;

display:flex;

align-items:center;
justify-content:center;

margin:auto;


border:2px solid white;

font-size:12px;

font-weight:bold;


}



.home .shirt{

background:
linear-gradient(
#2196f3,
#0756a8
);

}



.away .shirt{

background:
linear-gradient(
#ffd740,
#ffb300
);

color:#222;

}



.player-name{

margin-top:4px;

background:white;

color:#111;

font-size:10px;

font-weight:bold;

padding:2px;

border-radius:3px;

text-transform:uppercase;

}



/* =========================
 KADER
========================= */


.rosters{


display:grid;

grid-template-columns:1fr 1fr;

gap:40px;

margin-top:40px;


}



.roster{


background:#08265a;

padding:25px;

border-radius:15px;

}



.roster h2{


text-align:center;

margin-top:0;

font-size:32px;

}



.player-row{


display:flex;

align-items:center;

background:
rgba(255,255,255,.08);

margin-bottom:5px;

padding:5px;

}



.number{


width:35px;

font-weight:bold;

color:#6bbcff;

}



.player-input{

width:100%;

background:none;

border:0;

color:white;

font-weight:bold;

}



.player-input:focus{

outline:none;

background:rgba(255,255,255,.1);

}




@media(max-width:900px){

.pitch-container,
.rosters{

grid-template-columns:1fr;

}


.team-name{

font-size:18px;

}


.vs{

font-size:20px;

padding:10px 20px;

}

}



</style>

</head>


<body>


<div class="board">


<!-- HEADER -->

<div class="top-header">


<div class="team-box">

<div class="logo">

<span>⚽</span>

<input type="file" accept="image/*">

</div>


<input class="team-name" value="TEAM HEIM">


</div>



<div class="vs">
VS
</div>




<div class="team-box right">

<div class="logo">

<span>⚽</span>

<input type="file" accept="image/*">

</div>


<input class="team-name" value="TEAM GAST">


</div>


</div>





<!-- SPIELFELDER -->


<div class="pitch-container">


<div class="pitch-card">

<div class="pitch" id="homePitch">


<div class="goal-area top"></div>
<div class="goal-area bottom"></div>


</div>

</div>




<div class="pitch-card">


<div class="pitch" id="awayPitch">


<div class="goal-area top"></div>
<div class="goal-area bottom"></div>


</div>


</div>



</div>





<!-- KADER -->

<div class="rosters">


<div class="roster">


<h2>HEIM TEAM</h2>


<div id="homeRoster">


</div>


</div>





<div class="roster">


<h2>GAST TEAM</h2>


<div id="awayRoster">


</div>


</div>



</div>




</div>
<script>


/* =========================
 LOGO UPLOAD
========================= */


document.querySelectorAll(".logo input").forEach(input=>{


input.addEventListener("change",function(e){


const file=e.target.files[0];


if(!file) return;


const reader=new FileReader();


reader.onload=function(event){


const logo=input.parentElement;


logo.innerHTML=
`
<img src="${event.target.result}">
<input type="file" accept="image/*">
`;


logo.querySelector("input")
.addEventListener("change",arguments.callee);


}


reader.readAsDataURL(file);


});


});





/* =========================
 SPIELER DATEN
========================= */


const formations = {


"4-4-2":[

[50,90],

[20,75],
[40,75],
[60,75],
[80,75],

[15,55],
[38,55],
[62,55],
[85,55],

[35,25],
[65,25]

],



"4-3-3":[

[50,90],

[20,75],
[40,75],
[60,75],
[80,75],


[30,55],
[50,55],
[70,55],


[25,25],
[50,20],
[75,25]

],




"3-5-2":[

[50,90],

[25,75],
[50,75],
[75,75],


[15,55],
[35,55],
[50,50],
[65,55],
[85,55],


[40,25],
[60,25]

],



"5-3-2":[

[50,90],

[15,75],
[30,75],
[50,75],
[70,75],
[85,75],


[30,50],
[50,50],
[70,50],


[40,25],
[60,25]

]


};







let homePlayers=[];
let awayPlayers=[];





/* =========================
 KADER ERSTELLEN
========================= */


function createRoster(container,type){


let html="";


for(let i=1;i<=16;i++){


html+=
`

<div class="player-row">


<div class="number">
${i}
</div>


<input 
class="player-input"
data-team="${type}"
data-number="${i}"
value="${type=="home"?"Spieler":"Spieler"} ${i}"
>


</div>

`;

}


container.innerHTML=html;


}





createRoster(
document.getElementById("homeRoster"),
"home"
);


createRoster(
document.getElementById("awayRoster"),
"away"
);







/* =========================
 SPIELER AUF FELD SETZEN
========================= */


function drawPlayers(
pitch,
team,
formation
){


pitch.querySelectorAll(".player")
.forEach(p=>p.remove());



let positions=
formations[formation];



positions.forEach((pos,index)=>{


let div=document.createElement("div");


div.className=
"player "+team;



div.style.left=
"calc("+pos[0]+"% - 40px)";


div.style.top=
"calc("+pos[1]+"% - 20px)";



let name=
team=="home"
?
"Spieler "+(index+1)
:
"Spieler "+(index+1);



div.innerHTML=
`

<div class="shirt">

${index+1}

</div>


<div class="player-name">

${name}

</div>

`;



pitch.appendChild(div);



});


}





drawPlayers(
document.getElementById("homePitch"),
"home",
"4-4-2"
);



drawPlayers(
document.getElementById("awayPitch"),
"away",
"4-4-2"
);







/* =========================
 NAMEN LIVE ÄNDERN
========================= */


document.addEventListener(
"input",
function(e){



if(
!e.target.classList.contains("player-input")
)
return;



let team=
e.target.dataset.team;



let number=
e.target.dataset.number;



let pitch=
team=="home"
?
document.getElementById("homePitch")
:
document.getElementById("awayPitch");



let players=
pitch.querySelectorAll(".player-name");



if(players[number-1])

players[number-1].innerText=
e.target.value;



});






/* =========================
 FORMATIONS DROPDOWN
========================= */


/*

wird in Teil 3 sichtbar gemacht

API vorbereitet

*/


function changeFormation(
team,
formation
){



if(team=="home"){


drawPlayers(
document.getElementById("homePitch"),
"home",
formation
);


}

else{


drawPlayers(
document.getElementById("awayPitch"),
"away",
formation
);


}


}



<script>


/* =========================
 STEUERUNG EINBAUEN
========================= */


const controlBox=document.createElement("div");


controlBox.innerHTML=
`

<div style="
margin-top:40px;
background:#08265a;
padding:25px;
border-radius:20px;
box-shadow:0 10px 30px rgba(0,0,0,.5);
">


<h2 style="text-align:center">
⚽ Taktik Steuerung
</h2>


<div style="
display:grid;
grid-template-columns:1fr 1fr;
gap:20px;
">


<div>


<h3>Heim Formation</h3>


<select id="homeFormation"
style="
width:100%;
padding:12px;
border-radius:10px;
font-size:18px;
">


<option>4-4-2</option>
<option>4-3-3</option>
<option>3-5-2</option>
<option>5-3-2</option>


</select>


</div>




<div>


<h3>Gast Formation</h3>


<select id="awayFormation"
style="
width:100%;
padding:12px;
border-radius:10px;
font-size:18px;
">


<option>4-4-2</option>
<option>4-3-3</option>
<option>3-5-2</option>
<option>5-3-2</option>


</select>


</div>


</div>




<div style="
display:flex;
gap:15px;
margin-top:25px;
flex-wrap:wrap;
justify-content:center;
">


<button onclick="saveBoard()">
💾 Speichern
</button>


<button onclick="loadBoard()">
📂 Laden
</button>


<button onclick="exportBoard()">
📸 Bild Export
</button>


<button onclick="window.print()">
🖨 Drucken
</button>


</div>


</div>

`;



document
.querySelector(".board")
.appendChild(controlBox);





/* BUTTON DESIGN */


document.querySelectorAll("button")
.forEach(btn=>{


btn.style.padding="12px 25px";
btn.style.border="0";
btn.style.borderRadius="25px";
btn.style.cursor="pointer";
btn.style.fontWeight="bold";
btn.style.fontSize="16px";


});






/* =========================
 FORMATION ÄNDERN
========================= */


document
.getElementById("homeFormation")
.addEventListener(
"change",
function(){


changeFormation(
"home",
this.value
);


});





document
.getElementById("awayFormation")
.addEventListener(
"change",
function(){


changeFormation(
"away",
this.value
);


});







/* =========================
 DRAG & DROP SPIELER
========================= */


function enableDrag(){


document
.querySelectorAll(".player")
.forEach(player=>{


player.draggable=true;



player.addEventListener(
"dragstart",
function(e){


e.dataTransfer.setData(
"text/plain",
""
);


window.dragged=this;


});




player.addEventListener(
"dragend",
function(){


window.dragged=null;


});


});




document
.querySelectorAll(".pitch")
.forEach(pitch=>{


pitch.addEventListener(
"dragover",
e=>e.preventDefault()
);



pitch.addEventListener(
"drop",
function(e){


if(!window.dragged)
return;



let rect=this.getBoundingClientRect();



let x=
e.clientX-rect.left;


let y=
e.clientY-rect.top;



window.dragged.style.left=
(x-40)+"px";


window.dragged.style.top=
(y-20)+"px";



});



});


}



setTimeout(
enableDrag,
500
);








/* =========================
 SPEICHERN
========================= */


function saveBoard(){


let data={


homeFormation:
document.getElementById("homeFormation").value,


awayFormation:
document.getElementById("awayFormation").value,


homeName:
document.querySelectorAll(".team-name")[0].value,


awayName:
document.querySelectorAll(".team-name")[1].value,


homeRoster:[],


awayRoster:[]


};




document
.querySelectorAll(".player-input")
.forEach(input=>{


data[
input.dataset.team+"Roster"
]
.push(input.value);


});




localStorage.setItem(
"WettprophetenBoard",
JSON.stringify(data)
);



alert(
"Taktik gespeichert!"
);



}







/* =========================
 LADEN
========================= */


function loadBoard(){


let data=
JSON.parse(
localStorage.getItem(
"WettprophetenBoard"
)
);



if(!data)
{

alert(
"Keine Speicherung gefunden"
);

return;

}




document
.querySelectorAll(".team-name")[0]
.value=data.homeName;


document
.querySelectorAll(".team-name")[1]
.value=data.awayName;



document.getElementById(
"homeFormation"
)
.value=data.homeFormation;



document.getElementById(
"awayFormation"
)
.value=data.awayFormation;





document
.querySelectorAll(".player-input")
.forEach(input=>{


let list=
data[input.dataset.team+"Roster"];



input.value=
list[input.dataset.number-1];


});



changeFormation(
"home",
data.homeFormation
);


changeFormation(
"away",
data.awayFormation
);



alert(
"Taktik geladen!"
);


}








/* =========================
 EXPORT BILD
========================= */


function exportBoard(){


let board=
document.querySelector(".board");



alert(
"Export vorbereitet.\nNutze im Browser: Drucken → Als PDF speichern"
);



}





/* =========================
 BANK ERWEITERN
========================= */


function addBench(){


document
.querySelectorAll(".roster")
.forEach(roster=>{


let bench=document.createElement("div");


bench.innerHTML=
`

<hr>

<h3>
🪑 Ersatzbank
</h3>


12. Ersatzspieler<br>
13. Ersatzspieler<br>
14. Ersatzspieler<br>
15. Ersatzspieler<br>
16. Ersatzspieler



<br><br>


<h3>
👔 Trainer / Manager
</h3>


<input 
class="player-input"
value="Trainer Name"
>


`;


roster.appendChild(bench);



});


}



addBench();




</script>

</script>

</body>

</html>
