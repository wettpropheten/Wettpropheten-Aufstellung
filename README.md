<!DOCTYPE html>
<html lang="de">
<head>
<meta charset="UTF-8">
<title>Wettpropheten Analyse</title>

<style>

*{
    margin:0;
    padding:0;
    box-sizing:border-box;
    font-family:Arial,sans-serif;
}


body{
    min-height:100vh;
    background:#111;
    display:flex;
    justify-content:center;
    align-items:center;
}



.container{

    width:1400px;
    padding:40px;

    background:#181818;
    border-radius:25px;

    display:flex;
    flex-direction:column;
    align-items:center;

}



/* Kopf */

.header{

    width:920px;

    display:grid;

    grid-template-columns:430px 60px 430px;

    align-items:center;

    margin-bottom:30px;

}


.team{

    color:white;

    font-size:28px;

    font-weight:bold;

    text-align:center;

}


.vs{

    justify-self:center;

    color:white;

    font-size:36px;

    font-weight:bold;

}



/* FELDER */

.fields{

    width:920px;

    display:flex;

    justify-content:space-between;

    align-items:center;

}



/* 3D Feld */

.field{

    width:430px;

    height:650px;

    position:relative;


    background:

    repeating-linear-gradient(
        0deg,
        #267541 0px,
        #267541 45px,
        #2f8249 45px,
        #2f8249 90px
    );


    border:3px solid white;


    transform-style:preserve-3d;


    transform:

    rotateX(52deg)
    translateZ(30px);


    box-shadow:

    0 90px 120px rgba(0,0,0,.85);

}



/* Mittellinie */

.middle{

    position:absolute;

    left:0;

    top:50%;

    width:100%;

    height:3px;

    background:white;

    transform:translateY(-50%);

}



/* Kreis */

.circle{

    position:absolute;

    left:50%;

    top:50%;


    width:120px;

    height:120px;


    border:3px solid white;

    border-radius:50%;


    transform:translate(-50%,-50%);

}



/* Strafräume */

.penalty{

    position:absolute;

    left:50%;

    width:240px;

    height:100px;

    border:3px solid white;

    transform:translateX(-50%);

}


.top{

    top:0;

}


.bottom{

    bottom:0;

}


</style>

</head>


<body>


<div class="container">


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




    <div class="fields">


        <div class="field">

            <div class="middle"></div>

            <div class="circle"></div>

            <div class="penalty top"></div>

            <div class="penalty bottom"></div>

        </div>




        <div class="field">

            <div class="middle"></div>

            <div class="circle"></div>

            <div class="penalty top"></div>

            <div class="penalty bottom"></div>

        </div>


    </div>



</div>


</body>
</html>
