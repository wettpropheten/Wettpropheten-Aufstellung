<!DOCTYPE html>
<html lang="de">
<head>
    <meta charset="UTF-8">
    <title>Wettpropheten-Aufstellung - Final</title>
    <style>
        body {
            background-color: #071739;
            background-image: linear-gradient(135deg, rgba(255,255,255,0.03) 25%, transparent 25%, transparent 50%, rgba(255,255,255,0.03) 50%, rgba(255,255,255,0.03) 75%, transparent 75%, transparent);
            background-size: 40px 40px;
            color: #ffffff;
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 20px;
        }
        .main-container {
            width: 100%;
            max-width: 1100px;
            margin: 0 auto;
        }
        /* VS HEADER */
        .header-table {
            width: 100%;
            margin-bottom: 30px;
        }
        .team-box {
            background: #ffffff;
            border-radius: 40px;
            height: 60px;
            padding: 0 20px;
            width: 45%;
        }
        .team-container {
            display: flex;
            align-items: center;
            justify-content: space-between;
        }
        .team-container.right {
            flex-direction: row-reverse;
        }
        .logo-upload {
            width: 44px;
            height: 44px;
            background: #15294a;
            border-radius: 50%;
            position: relative;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
        }
        .logo-upload::before { content: '⚽'; font-size: 18px; }
        .logo-upload img { position: absolute; width:100%; height:100%; object-fit:cover; border-radius:50%; top:0; left:0; }
        .logo-upload input { position: absolute; opacity:0; width:100%; height:100%; cursor:pointer; }
        .team-input {
            background: transparent;
            border: none;
            color: #0d295c;
            font-size: 24px;
            font-weight: 900;
            text-transform: uppercase;
            width: 80%;
        }
        .team-container.right .team-input { text-align: right; }
        .team-input:focus { outline: none; }
        .vs-title {
            background: #0072ff;
            color: white;
            font-size: 24px;
            font-weight: bold;
            padding: 10px 25px;
            border-radius: 30px;
            border: 2px solid #fff;
            text-align: center;
        }
        /* GRID SYSTEM FÜR DIE ZWEI SPALTEN */
        .grid-layout {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 30px;
            width: 100%;
        }
        /* SPIELFELDER */
        .field-card {
            background: #132a4f;
            padding: 15px;
            border-radius: 8px;
            box-shadow: 0 8px 20px rgba(0,0,0,0.4);
        }
        .pitch {
            background-color: #2e7d32;
            height: 380px;
            border: 3px solid rgba(255,255,255,0.5);
            border-radius: 4px;
            box-sizing: border-box;
            display: flex;
            flex-direction: column;
            justify-content: space-around;
            padding: 10px 0;
        }
        .line {
            display: flex;
            justify-content: space-around;
            width: 100%;
        }
        .player {
            display: flex;
            flex-direction: column;
            align-items: center;
        }
        .icon {
            width: 28px;
            height: 28px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 11px;
            font-weight: bold;
            border: 2px solid white;
            box-shadow: 0 4px 4px rgba(0,0,0,0.4);
        }
        .left-side .icon { background: #1e88e5; color: white; }
        .left-side .gk { background: #e0e0e0; color: black; }
        .right-side .icon { background: #fdd835; color: black; border-color: #333; }
        .right-side .gk { background: #e53935; color: white; }
        .p-name {
            background: white;
            border: none;
            border-radius: 2px;
            color: black;
            font-size: 9px;
            font-weight: bold;
            width: 70px;
            text-align: center;
            margin-top: 3px;
            text-transform: uppercase;
        }
        /* MANNSCHAFTSKARTEN */
        .roster-card {
            background: #0f306e;
            border-radius: 6px;
            padding: 15px;
            box-shadow: 0 4px 15px rgba(0,0,0,0.3);
            display: grid;
            grid-template-columns: 1.2fr 1fr;
            gap: 15px;
            border-top: 4px solid #1e88e5;
        }
        .roster-card.right-card { border-top-color: #fdd835; }
        .p-list {
            display: flex;
            flex-direction: column;
            gap: 4px;
        }
        .p-row {
            display: flex;
            align-items: center;
            background: rgba(255,255,255,0.06);
            padding: 4px 8px;
            border-radius: 3px;
        }
        .p-num {
            font-weight: bold;
            font-size: 12px;
            color: #64b5f6;
            width: 20px;
        }
        .right-card .p-num { color: #fff176; }
        .p-input {
            background: transparent;
            border: none;
            color: white;
            font-size: 12px;
            width: 100%;
            text-transform: uppercase;
        }
        .p-input:focus { outline: none; }
        .m-box {
            display: flex;
            flex-direction: column;
        }
        .f-title {
            font-size: 36px;
            font-weight: 900;
            margin-bottom: 10px;
        }
        .s-title {
            font-size: 11px;
            font-weight: bold;
            color: #90caf9;
            text-transform: uppercase;
            margin: 8px 0 4px 0;
        }
        .right-card .s-title { color: #fff59d; }
    </style>
</head>
<body>

<div class="main-container">

    <!-- VS HEADER -->
    <table class="header-table">
        <tr>
            <td class="team-box">
                <div class="team-container">
                    <div class="logo-upload"><input type="file" accept="image/*" onchange="loadImg(this)"></div>
                    <input type="text" class="team-input" value="TEAM HEIM">
                </div>
            </td>
            <td style="width: 10%; text-align: center;">
                <span class="vs-title">VS</span>
            </td>
            <td class="team-box">
                <div class="team-container right">
                    <div class="logo-upload"><input type="file" accept="image/*" onchange="loadImg(this)"></div>
                    <input type="text" class="team-input" value="TEAM GAST">
                </div>
            </td>
        </tr>
    </table>

    <!-- SPIELFELDER ROW -->
    <div class="grid-layout" style="margin-bottom: 30px;">
        <!-- Links (4-4-2) -->
        <div class="field-card left-side">
            <div class="pitch">
                <div class="line">
                    <div class="player"><div class="icon">10</div><input type="text" class="p-name" value="SPIELER 10" data-sync="l10"></div>
                    <div class="player"><div class="icon">11</div><input type="text" class="p-name" value="SPIELER 11" data-sync="l11"></div>
                </div>
                <div class="line">
                    <div class="player"><div class="icon">06</div><input type="text" class="p-name" value="SPIELER 06" data-sync="l6"></div>
                    <div class="player"><div class="icon">07</div><input type="text" class="p-name" value="SPIELER 07" data-sync="l7"></div>
                    <div class="player"><div class="icon">08</div><input type="text" class="p-name" value="SPIELER 08" data-sync="l8"></div>
                    <div class="player"><div class="icon">09</div><input type="text" class="p-name" value="SPIELER 09" data-sync="l9"></div>
                </div>
                <div class="line">
                    <div class="player"><div class="icon">02</div><input type="text" class="p-name" value="SPIELER 02" data-sync="l2"></div>
                    <div class="player"><div class="icon">03</div><input type="text" class="p-name" value="SPIELER 03" data-sync="l3"></div>
                    <div class="player"><div class="icon">04</div><input type="text" class="p-name" value="SPIELER 04" data-sync="l4"></div>
                    <div class="player"><div class="icon">05</div><input type="text" class="p-name" value="SPIELER 05" data-sync="l5"></div>
                </div>
                <div class="line">
                    <div class="player"><div class="icon gk">01</div><input type="text" class="p-name" value="TORWART" data-sync="l1"></div>
                </div>
            </div>
        </div>

        <!-- Rechts (4-3-3) -->
        <div class="field-card right-side">
            <div class="pitch">
                <div class="line">
                    <div class="player"><div class="icon">09</div><input type="text" class="p-name" value="SPIELER 09" data-sync="r9"></div>
                    <div class="player"><div class="icon">10</div><input type="text" class="p-name" value="SPIELER 10" data-sync="r10"></div>
                    <div class="player"><div class="icon">11</div><input type="text" class="p-name" value="SPIELER 11" data-sync="r11"></div>
                </div>
                <div class="line">
                    <div class="player"><div class="icon">06</div><input type="text" class="p-name" value="SPIELER 06" data-sync="r6"></div>
                    <div class="player"><div class="icon">07覆</div><input type="text" class="p-name" value="SPIELER 07" data-sync="r7"></div>
