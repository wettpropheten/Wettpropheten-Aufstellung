<!DOCTYPE html>
<html lang="de">
<head>
<meta charset="UTF-8">
<title>Football 3D Pitch</title>

<style>

*{
    margin:0;
    padding:0;
    box-sizing:border-box;
}

body{
    min-height:100vh;
    background:#111;
    display:flex;
    justify-content:center;
    align-items:center;
    font-family:Arial, sans-serif;
}


.wrapper{

    width:1200px;
    padding:40px;

    background:#181818;
    border-radius:25px;

}



.header{

    display:flex;
    justify-content:space-between;
    align-items:center;

    margin-bottom:80px;

}


.team{

    width:35%;
    height:70px;

    background:#222;

    color:white;

    display:flex;
    justify-content:center;
    align-items:center;

    border-radius:15px;

    font-size:26px;
    font-weight:bold;

}


.vs{

    color:white;
    font-size:35px;
    font-weight:bold;

}



/* 3D BÜHNE */

.pitch-area{

    height:650px;

    display:flex;
    justify-content:center;
    align-items:center;

    perspective:1400px;

}



/* ECHTES 3D OBJEKT */

.pitch{

    width:430px;
    height:650px;

    position:relative;

    transform-style:preserve-3d;


    transform:

        rotateX(52deg)
        translateZ(0);


    background:

    repeating-linear-gradient(
        0deg,
        #24713d 0px,
        #24713d 50px,
        #2c7d47 50px,
        #2c7d47 100px
    );


    border:3px solid white;


    box-shadow:

    0 100px 90px rgba(0,0,0,.9);



}



/* Seiten-Tiefe */

.pitch:after{

    content:"";

    position:absolute;

    left:0;

    bottom:-35px;

    width:100%;

    height:35px;


    background:#12351f;


    transform:

    rotateX(90deg)

    translateZ(18px);


}



/* MITTELLINIE */

.pitch .middle{

    position:absolute;

    top:50%;

    left:0;

    width:100%;

    height:3px;

    background:white;

    transform:translateY(-50%);

}



/* MITTELKREIS */

.pitch .circle{

    position:absolute;

    top:50%;

    left:50%;

    width:110px;

    height:110px;

    border:3px solid white;

    border-radius:50%;

    transform:

    translate(-50%,-50%);

}



/* STRAFRÄUME */

.box{

    position:absolute;

    left:50%;

    width:230px;

    height:100px;

    border:3px solid white;

    transform:translateX(-50%);

}


.box.top{

    top:0;

}


.box.bottom{

    bottom:0;

}



/* TORLINIEN */

.goal{

    position:absolute;

    left:50%;

    width:100px;

    height:25px;

    border:3px solid white;

    transform:translateX(-50%);

}


.goal.top{

    top:0;

}


.goal.bottom{

    bottom:0;

}


</style>

</head>


<body>


<div class="wrapper">


<div class="header">

<div class="team">
HEIMTEAM
</div>

<div class="vs">
VS
</div>

<div class="team">
GASTTEAM
</div>

</div>



<div class="pitch-area">


<div class="pitch">


<div class="middle"></div>

<div class="circle"></div>

<div class="box top"></div>

<div class="box bottom"></div>

<div class="goal top"></div>

<div class="goal bottom"></div>


</div>


</div>


</div>


</body>
</html>
