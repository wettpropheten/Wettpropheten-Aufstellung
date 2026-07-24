<!DOCTYPE html>
<html lang="de">

<head>

<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Wettpropheten Starting XI</title>

<style>

*{
box-sizing:border-box;
}

body{

margin:0;

height:100vh;

background:

linear-gradient(135deg,#071521,#0b5a32);

font-family:Arial,Helvetica,sans-serif;

color:white;

display:flex;

justify-content:center;

align-items:center;

}


/* komplette Grafik */

.lineup-card{

width:900px;

height:95vh;

background:#111;

border-radius:25px;

box-shadow:

0 20px 60px black;

overflow:hidden;

}



/* Kopf */

.header{

height:90px;

display:flex;

align-items:center;

justify-content:space-between;

padding:20px 35px;

background:

linear-gradient(90deg,#222,#080808);

}


.logo{

width:60px;

height:60px;

border-radius:50%;

background:#333;

display:flex;

align-items:center;

justify-content:center;

font-size:22px;

font-weight:bold;

}


.team{

font-size:28px;

font-weight:bold;

}



.formation{

font-size:22px;

background:#333;

padding:10px 18px;

border-radius:12px;

}



/* Feld */


.pitch{

position:relative;

height:calc(100% - 180px);

margin:20px;

border-radius:20px;

background:

linear-gradient(

90deg,

#16833d,

#239653

);

border:3px solid white;

overflow:hidden;

}



/* Linien */


.pitch:before{

content:"";

position:absolute;

left:50%;

top:0;

height:100%;

width:3px;

background:white;

transform:translateX(-50%);

}


.pitch:after{

content:"";

position:absolute;

left:50%;

top:50%;

width:120px;

height:120px;

border:3px solid white;

border-radius:50%;

transform:translate(-50%,-50%);

}




.player{

position:absolute;

transform:translate(-50%,-50%);

text-align:center;

z-index:5;

}



.circle{

width:55px;

height:55px;

border-radius:50%;

background:white;

color:#111;

display:flex;

align-items:center;

justify-content:center;

font-size:20px;

font-weight:bold;

box-shadow:

0 5px 15px black;

}



.name{

margin-top:8px;

background:rgba(0,0,0,.7);

padding:5px 10px;

border-radius:8px;

font-size:14px;

white-space:nowrap;

}



/* unten */

.footer{

height:70px;

background:#090909;

display:flex;

justify-content:space-around;

align-items:center;

font-size:16px;

}


</style>

</head>


<body>


<div class="lineup-card">



<div class="header">


<div class="logo">
WP
</div>


<div class="team">
FC Bayern München
</div>


<div class="formation">
4-3-3
</div>


</div>





<div class="pitch" id="pitch">


</div>






<div class="footer">

<div>
Trainer: Kompany
</div>

<div>
Kapitän: Neuer
</div>

<div>
Bank: 5 Spieler
</div>

</div>



</div>





<script>


const players=[


{
name:"Neuer",
number:1,
x:50,
y:90
},


{
name:"Kimmich",
number:6,
x:80,
y:72
},


{
name:"Upamecano",
number:2,
x:60,
y:75
},


{
name:"Kim",
number:3,
x:40,
y:75
},


{
name:"Davies",
number:19,
x:20,
y:72
},


{
name:"Pavlovic",
number:45,
x:35,
y:52
},


{
name:"Musiala",
number:42,
x:50,
y:45
},


{
name:"Goretzka",
number:8,
x:65,
y:52
},


{
name:"Sane",
number:10,
x:25,
y:25
},


{
name:"Kane",
number:9,
x:50,
y:18
},


{
name:"Müller",
number:25,
x:75,
y:25
}


];





const pitch=document.getElementById("pitch");



players.forEach(player=>{


const div=document.createElement("div");


div.className="player";


div.style.left=player.x+"%";

div.style.top=player.y+"%";



div.innerHTML=`

<div class="circle">
${player.number}
</div>

<div class="name">
${player.name}
</div>

`;



pitch.appendChild(div);


});


</script>


</body>

</html>
