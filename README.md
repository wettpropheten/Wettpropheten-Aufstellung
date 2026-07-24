<!DOCTYPE html>
<html lang="de">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Wettpropheten-Aufstellung</title>
    <style>
        body {
            font-family: 'Arial', sans-serif;
            background-color: #071739;
            background-image: linear-gradient(135deg, rgba(255,255,255,0.03) 25%, transparent 25%, transparent 50%, rgba(255,255,255,0.03) 50%, rgba(255,255,255,0.03) 75%, transparent 75%, transparent);
            background-size: 40px 40px;
            color: #ffffff;
            margin: 0;
            padding: 20px;
            display: flex;
            justify-content: center;
        }

        .dashboard {
            width: 100%;
            max-width: 1100px;
            display: flex;
            flex-direction: column;
            gap: 30px;
        }

        /* HEADER */
        .vs-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            gap: 15px;
        }

        .team-banner {
            background: #ffffff;
            border-radius: 40px;
            height: 60px;
            display: flex;
            align-items: center;
            padding: 0 20px;
            width: 42%;
            box-shadow: 0 4px 15px rgba(0,0,0,0.3);
            box-sizing: border-box;
        }

        .team-banner.right { flex-direction: row-reverse; }

        .logo-box {
            width: 44px;
            height: 44px;
            background: #15294a;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            position: relative;
            cursor: pointer;
            overflow: hidden;
        }

        .logo-box::before { content: '⚽'; font-size: 18px; }
        .logo-box img { position: absolute; width: 100%; height: 100%; object-fit: cover; top:0; left:0; }
        .logo-box input { position: absolute; opacity: 0; width: 100%; height: 100%; cursor: pointer; }

        .team-name-input {
            background: transparent;
            border: none;
            color: #0d295c;
            font-size: 24px;
            font-weight: 900;
            text-transform: uppercase;
            width: 80%;
            padding: 5px 10px;
        }
        .team-banner.right .team-name-input { text-align: right; }
        .team-name-input:focus { outline: none; }

        .vs-badge {
            background: #0072ff;
            color: white;
            font-size: 24px;
            font-weight: bold;
            padding: 10px 25px;
            border-radius: 30px;
            border: 2px solid #fff;
        }

        /* ZWEI SPALTEN FÜR DIE SPIELFELDER (STABILE PERSPEKTIVE) */
        .fields-container {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 30px;
        }

        .field-box {
            background: #132a4f;
            padding: 15px;
            border-radius: 8px;
            box-shadow: 0 8px 20px rgba(0,0,0,0.4);
            /* Saubere, flache 3D-Neigung ohne Layout-Verschiebungen */
            transform: perspective(800px) rotateX(25deg);
        }

        .football-field {
            background-color: #2e7d32;
            height: 380px;
            border: 3px solid rgba(255,255,255,0.5);
            border-radius: 4px;
            position: relative;
            background-image: linear-gradient(to bottom, rgba(255,255,255,0.05) 50%, transparent 50%);
            background-size: 100% 40px;
            display: flex;
            flex-direction: column;
            justify-content: space-around;
            padding: 10px 0;
            box-sizing: border-box;
        }

        .formation-row {
            display: flex;
            justify-content: space-around;
            width: 100%;
        }

        .player-node {
            display: flex;
            flex-direction: column;
            align-items: center;
        }

        .jersey {
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
        .left-field .jersey { background: #1e88e5; color: white; }
        .left-field .gk { background: #e0e0e0; color: black; }
        .right-field .jersey { background: #fdd835; color: black; border-color: #333; }
        .right-field .gk { background: #e53935; color: white; }

        .player-input {
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

        /* MANNSCHAFTSKARTEN DIREKT DARUNTER */
        .cards-container {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 30px;
        }

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

        .player-list {
            display: flex;
            flex-direction: column;
            gap: 4px;
        }

        .player-row {
            display: flex;
            align-items: center;
            background: rgba(255,255,255,0.06);
            padding: 4px 8px;
            border-radius: 3px;
        }

        .player-num {
            font-weight: bold;
            font-size: 12px;
            color: #64b5f6;
            width: 20px;
        }
        .right-card .player-num { color: #fff176; }

        .row-input {
            background: transparent;
            border: none;
            color: white;
            font-size: 12px;
            width: 100%;
            text-transform: uppercase;
        }
        .row-input:focus { outline: none; background: rgba(255,255,255,0.05); }

        .meta-box {
            display: flex;
            flex-direction: column;
        }

        .formation-title {
            font-size: 36px;
            font-weight: 900;
            margin-bottom: 10px;
        }

        .section-title {
            font-size: 11px;
            font-weight: bold;
            color: #90caf9;
            text-transform: uppercase;
            margin: 8px 0 4px 0;
        }
        .right-card .section-title { color: #fff59d; }
    </style>
</head>
<body>

<div class="dashboard">

    <!-- VS HEADER -->
    <div class="vs-header">
        <div class="team-banner">
            <div class="logo-box"><input type="file" accept="image/*" onchange="loadImg(this)"></div>
            <input type="text" class="team-name-input" value="TEAM HEIM">
        </div>
        <div class="vs-badge">VS</div>
        <div class="team-banner right">
            <div class="logo-box"><input type="file" accept="image/*" onchange="loadImg(this)"></div>
            <input type="text" class="team-name-input" value="TEAM GAST">
        </div>
    </div>

    <!-- SPIELFELDER -->
    <div class="fields-container">
        <!-- Links (4-4-2) -->
        <div class="field-box left-field">
            <div class="football-field">
                <div class="formation-row">
                    <div class="player-node"><div class="jersey">10</div><input type="text" class="player-input" value="SPIELER 10" data-sync="l10"></div>
                    <div class="player-node"><div class="jersey">11</div><input type="text" class="player-input" value="SPIELER 11" data-sync="l11"></div>
                </div>
                <div class="formation-row">
                    <div class="player-node"><div class="jersey">06</div><input type="text" class="player-input" value="SPIELER 06" data-sync="l6"></div>
                    <div class="player-node"><div class="jersey">07</div><input type="text" class="player-input" value="SPIELER 07" data-sync="l7"></div>
                    <div class="player-node"><div class="jersey">08</div><input type="text" class="player-input" value="SPIELER 08" data-sync="l8"></div>
                    <div class="player-node"><div class="jersey">09</div><input type="text" class="player-input" value="SPIELER 09" data-sync="l9"></div>
                </div>
                <div class="formation-row">
                    <div class="player-node"><div class="jersey">02</div><input type="text" class="player-input" value="SPIELER 02" data-sync="l2"></div>
                    <div class="player-node"><div class="jersey">03</div><input type="text" class="player-input" value="SPIELER 03" data-sync="l3"></div>
                    <div class="player-node"><div class="jersey">04</div><input type="text" class="player-input" value="SPIELER 04" data-sync="l4"></div>
                    <div class="player-node"><div class="jersey">05</div><input type="text" class="player-input" value="SPIELER 05" data-sync="l5"></div>
                </div>
                <div class="formation-row">
                    <div class="player-node"><div class="jersey gk">01</div><input type="text" class="player-input" value="TORWART" data-sync="l1"></div>
                </div>
            </div>
        </div>

        <!-- Rechts (4-3-3) -->
        <div class="field-box right-field">
            <div class="football-field">
                <div class="formation-row">
                    <div class="player-node"><div class="jersey">09</div><input type="text" class="player-input" value="SPIELER 09" data-sync="r9"></div>

