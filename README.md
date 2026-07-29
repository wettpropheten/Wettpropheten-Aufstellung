<style>

*{
box-sizing:border-box;
font-family:Arial,Helvetica,sans-serif;
}


body{

margin:0;

background:
radial-gradient(circle at top,#333,#050505 80%);

color:white;

overflow-x:hidden;

}



/* GANZER BEREICH */

.app{

display:grid;

grid-template-columns:300px 1fr;

min-height:100vh;

width:100%;

gap:15px;

}





/* ======================
   SPIELTAG GANZ LINKS
====================== */


.sidebar{

height:100vh;

position:sticky;

top:0;


background:

linear-gradient(145deg,#252525,#080808);


padding:18px;


border-right:2px solid #555;


overflow:auto;


}



.sidebar h2{

text-align:center;

color:#f5c542;

font-size:28px;

}





/* ======================
   HAUPTFENSTER MAXIMAL
====================== */


.main{


width:100%;


min-height:100vh;


padding:30px 40px 50px 25px;


background:

linear-gradient(145deg,#171717,#050505);


border-radius:30px 0 0 30px;


box-shadow:

-20px 0 60px #000;


}





/* SPIELKOPF */

.game-header{


width:100%;


display:grid;

grid-template-columns:1fr 220px 1fr;


align-items:center;


padding:45px;


border-radius:30px;


background:

linear-gradient(

90deg,

#ffffff12,

transparent,

#ffffff12

);


}



.team{

font-size:42px;

font-weight:bold;

text-align:center;

}



.score{

font-size:100px;

font-weight:bold;

text-align:center;

}





/* spätere Module volle Breite */


.module{


width:100%;


margin-top:30px;


background:

linear-gradient(145deg,#222,#090909);


border-radius:25px;


padding:30px;


}


</style>
