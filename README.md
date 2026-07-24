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



/* Hauptaufteilung */

.layout{


height:100vh;

width:100vw;


display:grid;


grid-template-columns:

170px

1fr

1fr

170px;


gap:20px;


padding:25px;


align-items:center;


}




/* Mannschaftskarten */


.team-card{


height:65vh;


background:

linear-gradient(

145deg,

#252525,

#090909

);


border-radius:20px;


box-shadow:

0 20px 50px black;


display:flex;


flex-direction:column;


justify-content:center;


align-items:center;


}




.logo{


width:80px;

height:80px;


border-radius:50%;


background:#444;


display:flex;


align-items:center;


justify-content:center;


font-size:32px;


font-weight:bold;


}



.team-name{


font-size:22px;


margin-top:20px;


font-weight:bold;


}




/* Felder */


.field{


height:65vh;


position:relative;


background:


linear-gradient(

90deg,

#16833d,

#239653

);


border:

3px solid white;


box-shadow:

0 25px 60px black;


overflow:hidden;


}





/* Heimfeld */

.home-field{


border-radius:

25px 0 0 25px;


transform:

perspective(1400px)

rotateY(7deg)

rotateX(5deg);


}





/* Gastfeld */

.away-field{


border-radius:

0 25px 25px 0;


transform:

perspective(1400px)

rotateY(-7deg)

rotateX(5deg);


}





/* Mittellinie */


.home-field:after,


.away-field:before{


content:"";


position:absolute;


top:0;


height:100%;


width:3px;


background:white;


}




.home-field:after{

right:0;

}



.away-field:before{

left:0;

}




/* Mittelkreis */


.home-field:before,


.away-field:after{


content:"";


position:absolute;


top:50%;


width:130px;


height:130px;


border:

3px solid white;


border-radius:50%;


transform:translateY(-50%);


}



.home-field:before{


right:-65px;


}



.away-field:after{


left:-65px;


}



</style>

</head>



<body>



<div class="layout">



<!-- Heim Karte -->

<div class="team-card">


<div class="logo">

H

</div>


<div class="team-name">

HEIM

</div>


</div>





<!-- Heim Spielfeld -->

<div class="field home-field">

</div>





<!-- Gast Spielfeld -->

<div class="field away-field">

</div>





<!-- Gast Karte -->

<div class="team-card">


<div class="logo">

G

</div>


<div class="team-name">

GAST

</div>


</div>



</div>

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




.layout{


height:100vh;

width:100vw;


display:grid;


grid-template-columns:

170px

1fr

1fr

170px;


gap:20px;


padding:25px;


align-items:center;


}





.team-card{


height:65vh;


background:

linear-gradient(

145deg,

#252525,

#090909

);


border-radius:20px;


box-shadow:

0 20px 50px black;


display:flex;


flex-direction:column;


justify-content:center;


align-items:center;


}




.logo{


width:80px;

height:80px;


border-radius:50%;


background:#444;


display:flex;


align-items:center;


justify-content:center;


font-size:32px;


font-weight:bold;


}




.team-name{


font-size:22px;

font-weight:bold;

margin-top:20px;


}





.field{


height:65vh;


position:relative;


background:

linear-gradient(

90deg,

#16833d,

#239653

);


border:

3px solid white;


overflow:hidden;


box-shadow:

0 25px 60px black;


}





.home-field{


border-radius:

25px 0 0 25px;


transform:

perspective(1400px)

rotateY(7deg)

rotateX(5deg);


}




.away-field{


border-radius:

0 25px 25px 0;


transform:

perspective(1400px)

rotateY(-7deg)

rotateX(5deg);


}






/* Mittellinie */


.home-field:after,

.away-field:before{


content:"";


position:absolute;


top:0;


height:100%;


width:3px;


background:white;


}




.home-field:after{

right:0;

}



.away-field:before{

left:0;

}






/* Mittelkreis */


.home-field:before,

.away-field:after{


content:"";


position:absolute;


top:50%;


width:130px;


height:130px;


border:

3px solid white;


border-radius:50%;


transform:translateY(-50%);


}



.home-field:before{

right:-65px;

}



.away-field:after{

left:-65px;

}





/* Strafraum */


.penalty{


position:absolute;


top:50%;


width:120px;


height:260px;


border:

3px solid white;


transform:translateY(-50%);


}




.home-field .penalty{


right:0;

}



.away-field .penalty{


left:0;

}





/* Torraum */


.goal-area{


position:absolute;


top:50%;


width:55px;


height:120px;


border:

3px solid white;


transform:translateY(-50%);


}





.home-field .goal-area{


right:0;

}



.away-field .goal-area{


left:0;

}





/* Tor */


.goal{


position:absolute;


top:50%;


width:12px;


height:90px;


background:white;


transform:translateY(-50%);


}





.home-field .goal{


right:-12px;

}



.away-field .goal{


left:-12px;

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





<div class="field home-field">


<div class="penalty"></div>

<div class="goal-area"></div>

<div class="goal"></div>


</div>





<div class="field away-field">


<div class="penalty"></div>

<div class="goal-area"></div>

<div class="goal"></div>


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




.controls{


position:absolute;


top:15px;


left:50%;


transform:translateX(-50%);


z-index:20;


background:rgba(0,0,0,.5);


padding:10px;


border-radius:15px;


}



select{


padding:8px 15px;


border-radius:10px;


font-size:16px;


}





.layout{


height:100vh;

width:100vw;


display:grid;


grid-template-columns:

170px

1fr

1fr

170px;


gap:20px;


padding:25px;


align-items:center;


}






.team-card{


height:65vh;


background:

linear-gradient(

145deg,

#252525,

#090909

);


border-radius:20px;


display:flex;


align-items:center;


justify-content:center;


flex-direction:column;


box-shadow:

0 20px 50px black;


}





.logo{


width:80px;


height:80px;


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


margin-top:20px;


}





.field{


height:65vh;


position:relative;


background:

linear-gradient(

90deg,

#16833d,

#239653

);


border:

3px solid white;


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





.home-field:after,

.away-field:before{


content:"";


position:absolute;


top:0;


height:100%;


width:3px;


background:white;


}



.home-field:after{

right:0;

}



.away-field:before{

left:0;

}





.home-field:before,

.away-field:after{


content:"";


position:absolute;


top:50%;


width:130px;


height:130px;


border:3px solid white;


border-radius:50%;


transform:translateY(-50%);


}



.home-field:before{

right:-65px;

}


.away-field:after{

left:-65px;

}






.player{


position:absolute;


width:34px;


height:34px;


background:white;


border-radius:50%;


color:black;


font-weight:bold;


display:flex;


align-items:center;


justify-content:center;


transform:translate(-50%,-50%);


box-shadow:0 5px 15px black;


}





</style>

</head>



<body>




<div class="controls">


Formation:


<select id="formation">


<option value="433">

4-3-3

</option>


<option value="442">

4-4-2

</option>


<option value="352">

3-5-2

</option>


</select>


</div>






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


const formations={



433:[

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

],



442:[

[50,90],

[20,70],

[40,75],

[60,75],

[80,70],

[20,45],

[40,50],

[60,50],

[80,45],

[35,20],

[65,20]

],



352:[

[50,90],

[30,70],

[50,75],

[70,70],

[25,50],

[45,55],

[55,55],

[75,50],

[35,25],

[50,18],

[65,25]

]

};





function draw(){


let type=

formation.value;


homeField.innerHTML="";

awayField.innerHTML="";



formations[type].forEach((p,i)=>{


let h=document.createElement("div");


h.className="player";


h.style.left=p[0]+"%";


h.style.top=p[1]+"%";


h.innerHTML=i+1;


homeField.appendChild(h);





let a=document.createElement("div");


a.className="player";


a.style.left=(100-p[0])+"%";


a.style.top=p[1]+"%";


a.innerHTML=i+1;


awayField.appendChild(a);



});



}





formation.onchange=draw;


draw();



</script>

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



.controls{


position:absolute;


top:15px;


left:50%;


transform:translateX(-50%);


z-index:20;


background:rgba(0,0,0,.6);


padding:10px;


border-radius:15px;


}





select{


padding:8px 15px;


border-radius:10px;


font-size:16px;


}




.layout{


height:100vh;


width:100vw;


display:grid;


grid-template-columns:

170px

1fr

1fr

170px;


gap:20px;


padding:25px;


align-items:center;


}






.team-card{


height:65vh;


background:

linear-gradient(145deg,#252525,#090909);


border-radius:20px;


display:flex;


align-items:center;


justify-content:center;


flex-direction:column;


box-shadow:0 20px 50px black;


}





.logo{


width:80px;


height:80px;


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


margin-top:20px;


}







.field{


height:65vh;


position:relative;


background:

linear-gradient(90deg,#16833d,#239653);


border:3px solid white;


overflow:hidden;


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






.home-field:after,

.away-field:before{


content:"";


position:absolute;


top:0;


height:100%;


width:3px;


background:white;


}



.home-field:after{

right:0;

}



.away-field:before{

left:0;

}





.player{


position:absolute;


transform:translate(-50%,-50%);


text-align:center;


z-index:5;


}




.shirt{


width:38px;


height:38px;


border-radius:50%;


background:#fff;


color:#000;


display:flex;


align-items:center;


justify-content:center;


font-weight:bold;


box-shadow:0 5px 15px black;


}



.name{


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



<div class="controls">


Formation:

<select id="formation">


<option value="433">4-3-3</option>

<option value="442">4-4-2</option>

<option value="352">3-5-2</option>


</select>


</div>




<div class="layout">



<div class="team-card">


<div class="logo">H</div>


<div class="team-name">

HEIM

</div>


</div>





<div class="field home-field" id="homeField"></div>





<div class="field away-field" id="awayField"></div>





<div class="team-card">


<div class="logo">G</div>


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





const formations={



433:[

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

],




442:[

[50,90],

[20,70],

[40,75],

[60,75],

[80,70],

[20,50],

[40,50],

[60,50],

[80,50],

[35,20],

[65,20]

],




352:[

[50,90],

[30,70],

[50,75],

[70,70],

[25,50],

[45,55],

[55,55],

[75,50],

[35,25],

[50,18],

[65,25]

]

};






function createPlayer(name,number,x,y){


let div=document.createElement("div");


div.className="player";


div.style.left=x+"%";


div.style.top=y+"%";



div.innerHTML=

`

<div class="shirt">

${number}

</div>


<div class="name">

${name}

</div>

`;



return div;


}





function draw(){



let f=formations[formation.value];



homeField.innerHTML="";

awayField.innerHTML="";



f.forEach((p,i)=>{


homeField.appendChild(

createPlayer(

homePlayers[i],

i+1,

p[0],

p[1]

)

);





awayField.appendChild(

createPlayer(

awayPlayers[i],

i+1,

100-p[0],

p[1]

)

);



});


}




formation.onchange=draw;


draw();

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




.team-card{


height:75vh;


background:

linear-gradient(

145deg,

#252525,

#080808

);


border-radius:22px;


padding:15px;


box-shadow:

0 20px 50px black;


display:flex;


flex-direction:column;


align-items:center;


overflow:hidden;


}





.logo{


width:85px;


height:85px;


border-radius:50%;


background:#444;


display:flex;


align-items:center;


justify-content:center;


font-size:32px;


font-weight:bold;


}




.team-title{


font-size:21px;


font-weight:bold;


margin:15px 0;


text-align:center;


}




.info{


width:100%;


background:

rgba(255,255,255,.08);


border-radius:12px;


padding:10px;


font-size:14px;


line-height:1.8;


}





.bank{


margin-top:15px;


width:100%;


background:

rgba(0,0,0,.35);


padding:10px;


border-radius:12px;


font-size:13px;


}



.bank div{


padding:4px;


border-bottom:

1px solid rgba(255,255,255,.2);


}






.field{


height:70vh;


position:relative;


background:

linear-gradient(90deg,#16833d,#239653);


border:3px solid white;


overflow:hidden;


box-shadow:

0 25px 60px black;


}



.home-field{


border-radius:25px 0 0 25px;


}



.away-field{


border-radius:0 25px 25px 0;


}






.player{


position:absolute;


transform:translate(-50%,-50%);


text-align:center;


}




.shirt{


width:38px;


height:38px;


background:white;


color:black;


border-radius:50%;


display:flex;


align-items:center;


justify-content:center;


font-weight:bold;


box-shadow:0 5px 15px black;


}




.name{


font-size:12px;


background:rgba(0,0,0,.7);


padding:3px 6px;


border-radius:6px;


margin-top:5px;


white-space:nowrap;


}




</style>

</head>



<body>



<div class="layout">



<div class="team-card">


<div class="logo">

FCB

</div>


<div class="team-title" id="homeName">

Bayern München

</div>



<div class="info">


Trainer:

<br>

<b id="homeCoach">

Vincent Kompany

</b>


<br><br>


Kapitän:

<br>

<b id="homeCaptain">

Manuel Neuer

</b>


</div>



<div class="bank">


<b>Bank</b>


<div>Ulreich</div>

<div>Laimer</div>

<div>Boey</div>

<div>Tel</div>

<div>Coman</div>


</div>


</div>







<div class="field home-field" id="homeField">


</div>






<div class="field away-field" id="awayField">


</div>








<div class="team-card">


<div class="logo">

BVB

</div>



<div class="team-title">

Borussia Dortmund

</div>



<div class="info">


Trainer:

<br>

<b>

Nuri Sahin

</b>


<br><br>


Kapitän:

<br>

<b>

Emre Can

</b>


</div>



<div class="bank">


<b>Bank</b>


<div>Meyer</div>

<div>Gross</div>

<div>Beier</div>

<div>Reyna</div>

<div>Duranville</div>


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





const pos=[


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






function draw(){



homeField.innerHTML="";

awayField.innerHTML="";



pos.forEach((p,i)=>{



let h=document.createElement("div");


h.className="player";


h.style.left=p[0]+"%";


h.style.top=p[1]+"%";



h.innerHTML=

`

<div class="shirt">

${i+1}

</div>

<div class="name">

${homePlayers[i]}

</div>

`;



homeField.appendChild(h);






let a=document.createElement("div");


a.className="player";


a.style.left=(100-p[0])+"%";


a.style.top=p[1]+"%";



a.innerHTML=

`

<div class="shirt">

${i+1}

</div>

<div class="name">

${awayPlayers[i]}

</div>

`;



awayField.appendChild(a);



});



}



draw();




</script>

</body>

</html>
