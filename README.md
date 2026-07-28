<!DOCTYPE html>
<html lang="de">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Live Statistik Dashboard</title>

<style>
*{
    box-sizing:border-box;
    margin:0;
    padding:0;
    font-family:Arial,Helvetica,sans-serif;
}

body{
    background:#041822;
    color:white;
    padding:20px;
}

.dashboard{
    max-width:1200px;
    margin:auto;
    display:grid;
    grid-template-columns:320px 1fr;
    gap:25px;
}

/* ================= PANEL ================= */

.panel{
    background:#06202d;
    border-radius:16px;
    padding:20px;
    height:fit-content;
}

.panel h2{
    margin-bottom:18px;
    text-align:center;
    font-size:22px;
}

.input-group{
    margin-bottom:14px;
}

.input-group label{
    display:block;
    margin-bottom:6px;
    font-size:14px;
    color:#c7d8e6;
}

.input-group input{
    width:100%;
    padding:10px 12px;
    border-radius:10px;
    border:none;
    background:#0b3142;
    color:white;
    font-size:15px;
}

button{
    width:100%;
    padding:12px;
    border:none;
    border-radius:12px;
    background:#0f8cff;
    color:white;
    font-weight:bold;
    cursor:pointer;
    margin-top:10px;
}

/* ================= PREVIEW ================= */

.preview{
    background:#06202d;
    border-radius:16px;
    padding:25px;
}

.preview h1{
    text-align:center;
    margin-bottom:22px;
    font-size:28px;
}

.category{
    text-align:center;
    margin:22px 0 12px;
    font-size:14px;
    color:#c7d8e6;
    letter-spacing:1px;
    text-transform:uppercase;
}

.stat{
    padding:14px 0;
    border-bottom:1px solid rgba(255,255,255,.06);
}

.stat-header{
    display:flex;
    align-items:center;
    justify-content:space-between;
    margin-bottom:8px;
}

.value{
    width:72px;
    font-weight:bold;
    font-size:18px;
}

.value.right{
    text-align:right;
}

.title{
    flex:1;
    text-align:center;
    color:#d9e6f0;
    font-size:15px;
}

.bar{
    height:10px;
    background:#0b3142;
    border-radius:999px;
    overflow:hidden;
    display:flex;
}

.homeBar{
    background:#00b4ff;
    width:50%;
    transition:width .5s ease;
}

.awayBar{
    background:#e6eef5;
    width:50%;
    transition:width .5s ease;
}

.pass-line{
    text-align:center;
    margin-top:6px;
    color:#c7d8e6;
    font-size:13px;
}

@media(max-width:900px){
    .dashboard{
        grid-template-columns:1fr;
    }
}
</style>
</head>

<body>

<div class="dashboard">

    <!-- EINGABE -->

    <div class="panel">

        <h2>Live Eingabe</h2>

        <div class="input-group">
            <label>xGoals Heim</label>
            <input id="hxg" value="1.24">
        </div>

        <div class="input-group">
            <label>xGoals Gast</label>
            <input id="axg" value="0.80">
        </div>

        <div class="input-group">
            <label>Ballbesitz Heim (%)</label>
            <input id="hpos" value="50">
        </div>

        <div class="input-group">
            <label>Ballbesitz Gast (%)</label>
            <input id="apos" value="50">
        </div>

        <div class="input-group">
            <label>Schüsse Heim</label>
            <input id="hshots" value="10">
        </div>

        <div class="input-group">
            <label>Schüsse Gast</label>
            <input id="ashots" value="12">
        </div>

        <div class="input-group">
            <label>Schüsse aufs Tor Heim</label>
            <input id="hsot" value="3">
        </div>

        <div class="input-group">
            <label>Schüsse aufs Tor Gast</label>
            <input id="asot" value="5">
        </div>

        <div class="input-group">
            <label>Großchancen Heim</label>
            <input id="hbig" value="1">
        </div>

        <div class="input-group">
            <label>Großchancen Gast</label>
            <input id="abig" value="2">
        </div>

        <div class="input-group">
            <label>Eckbälle Heim</label>
            <input id="hcorn" value="3">
        </div>

        <div class="input-group">
            <label>Eckbälle Gast</label>
            <input id="acorn" value="4">
        </div>

        <div class="input-group">
            <label>Erfolgreiche Pässe Heim</label>
            <input id="hpass" value="454">
        </div>

        <div class="input-group">
            <label>Passversuche Heim</label>
            <input id="hpasstotal" value="526">
        </div>

        <div class="input-group">
            <label>Erfolgreiche Pässe Gast</label>
            <input id="apass" value="464">
        </div>

        <div class="input-group">
            <label>Passversuche Gast</label>
            <input id="apasstotal" value="524">
        </div>

        <div class="input-group">
            <label>Gelbe Karten Heim</label>
            <input id="hyellow" value="0">
        </div>

        <div class="input-group">
            <label>Gelbe Karten Gast</label>
            <input id="ayellow" value="1">
        </div>

        <button onclick="updateStats()">Aktualisieren</button>

    </div>

    <!-- VORSCHAU -->

    <div class="preview">

        <h1>Top-Statistiken</h1>

        <div class="stat">
            <div class="stat-header">
                <div class="value" id="vxgH">1.24</div>
                <div class="title">Expected Goals (xG)</div>
                <div class="value right" id="vxgA">0.80</div>
            </div>
            <div class="bar">
                <div class="homeBar" id="bxgH"></div>
                <div class="awayBar" id="bxgA"></div>
            </div>
        </div>

        <div class="stat">
            <div class="stat-header">
                <div class="value" id="vposH">50%</div>
                <div class="title">Ballbesitz</div>
                <div class="value right" id="vposA">50%</div>
            </div>
            <div class="bar">
                <div class="homeBar" id="bposH"></div>
                <div class="awayBar" id="bposA"></div>
            </div>
        </div>

        <div class="stat">
            <div class="stat-header">
                <div class="value" id="vshotsH">10</div>
                <div class="title">Schüsse insgesamt</div>
                <div class="value right" id="vshotsA">12</div>
            </div>
            <div class="bar">
                <div class="homeBar" id="bshotsH"></div>
                <div class="awayBar" id="bshotsA"></div>
            </div>
        </div>

        <div class="stat">
            <div class="stat-header">
                <div class="value" id="vsotH">3</div>
                <div class="title">Schüsse aufs Tor</div>
                <div class="value right" id="vsotA">5</div>
            </div>
            <div class="bar">
                <div class="homeBar" id="bsotH"></div>
                <div class="awayBar" id="bsotA"></div>
            </div>
        </div>

        <div class="stat">
            <div class="stat-header">
                <div class="value" id="vbigH">1</div>
                <div class="title">Großchance</div>
                <div class="value right" id="vbigA">2</div>
            </div>
            <div class="bar">
                <div class="homeBar" id="bbigH"></div>
                <div class="awayBar" id="bbigA"></div>
            </div>
        </div>

        <div class="stat">
            <div class="stat-header">
                <div class="value" id="vcornH">3</div>
                <div class="title">Eckbälle</div>
                <div class="value right" id="vcornA">4</div>
            </div>
            <div class="bar">
                <div class="homeBar" id="bcornH"></div>
                <div class="awayBar" id="bcornA"></div>
            </div>
        </div>

        <div class="stat">
            <div class="stat-header">
                <div class="value" id="vpassPctH">86%</div>
                <div class="title">Passquote</div>
                <div class="value right" id="vpassPctA">89%</div>
            </div>
            <div class="bar">
                <div class="homeBar" id="bpassH"></div>
                <div class="awayBar" id="bpassA"></div>
            </div>
            <div class="pass-line">
                <span id="vpassLineH">454/526</span>
                &nbsp;&nbsp;•&nbsp;&nbsp;
                <span id="vpassLineA">464/524</span>
            </div>
        </div>

        <div class="stat">
            <div class="stat-header">
                <div class="value" id="vyellowH">0</div>
                <div class="title">Gelbe Karten</div>
                <div class="value right" id="vyellowA">1</div>
            </div>
            <div class="bar">
                <div class="homeBar" id="byellowH"></div>
                <div class="awayBar" id="byellowA"></div>
            </div>
        </div>

    </div>
</div>

<script>
function ratio(a,b){
    const total=a+b;
    if(total<=0) return [50,50];
    return [(a/total)*100,(b/total)*100];
}

function setPair(prefix,h,a,suffix=''){
    document.getElementById('v'+prefix+'H').textContent = h + suffix;
    document.getElementById('v'+prefix+'A').textContent = a + suffix;
    const [hp,ap] = ratio(Number(h), Number(a));
    document.getElementById('b'+prefix+'H').style.width = hp + '%';
    document.getElementById('b'+prefix+'A').style.width = ap + '%';
}

function updateStats(){
    setPair('xg', parseFloat(hxg.value).toFixed(2), parseFloat(axg.value).toFixed(2));
    setPair('pos', Number(hpos.value), Number(apos.value), '%');
    setPair('shots', Number(hshots.value), Number(ashots.value));
    setPair('sot', Number(hsot.value), Number(asot.value));
    setPair('big', Number(hbig.value), Number(abig.value));
    setPair('corn', Number(hcorn.value), Number(acorn.value));
    setPair('yellow', Number(hyellow.value), Number(ayellow.value));

    const hCompleted = Number(hpass.value);
    const hTotal = Number(hpasstotal.value);
    const aCompleted = Number(apass.value);
    const aTotal = Number(apasstotal.value);

    const hPct = hTotal ? Math.round(hCompleted / hTotal * 100) : 0;
    const aPct = aTotal ? Math.round(aCompleted / aTotal * 100) : 0;

    document.getElementById('vpassPctH').textContent = hPct + '%';
    document.getElementById('vpassPctA').textContent = aPct + '%';
    document.getElementById('vpassLineH').textContent = `${hCompleted}/${hTotal}`;
    document.getElementById('vpassLineA').textContent = `${aCompleted}/${aTotal}`;

    const [hp,ap] = ratio(hPct,aPct);
    document.getElementById('bpassH').style.width = hp + '%';
    document.getElementById('bpassA').style.width = ap + '%';
}

updateStats();
</script>

</body>
</html>
