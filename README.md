<!DOCTYPE html>
<html lang="de">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Wettpropheten Dashboard</title>
    <style>
        /* =========================
           FARB SYSTEM (:root)
        ========================= */
        :root {
            --heim-farbe: #0099ff;
            --gast-farbe: #ff3344;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: Arial, Helvetica, sans-serif;
        }

        body {
            width: 100vw;
            height: 100vh;
            background: #050505;
            color: white;
            overflow: hidden;
        }

        /* =========================
           GESAMT LAYOUT
        ========================= */
        .app {
            display: flex;
            width: 100vw;
            height: 100vh;
        }

        /* =========================
           LINKER SPIELTAG
        ========================= */
        .sidebar {
            width: 280px;
            min-width: 280px;
            height: 100vh;
            background: linear-gradient(180deg, #252525, #080808);
            border-right: 2px solid #444;
            padding: 15px;
        }

        .sidebar h1 {
            text-align: center;
            color: #f5c542;
            font-size: 28px;
            margin-bottom: 20px;
        }

        .spieltag-box {
            height: calc(100vh - 90px);
            background: #111;
            border-radius: 20px;
            border: 1px solid #444;
            padding: 15px;
            overflow-y: auto;
        }

        textarea {
            width: 100%;
            height: 220px;
            background: #050505;
            color: white;
            border: 1px solid #555;
            border-radius: 15px;
            padding: 15px;
            resize: none;
        }

        button {
            width: 100%;
            margin-top: 12px;
            padding: 14px;
            border-radius: 15px;
            border: 1px solid #777;
            background: linear-gradient(#555, #111);
            color: white;
            font-weight: bold;
            cursor: pointer;
        }

        /* =========================
           SPIELKARTEN
        ========================= */
        .spielkarte {
            margin-top: 15px;
            padding: 15px;
            background: linear-gradient(145deg, #333, #111);
            border-radius: 18px;
            border: 1px solid #555;
            text-align: center;
            cursor: pointer;
            transition: .2s;
        }

        .spielkarte:hover {
            border-color: #f5c542;
            transform: scale(1.02);
        }

        .spielzeit {
            color: #aaa;
            font-size: 13px;
            margin-bottom: 8px;
        }

        .verein {
            font-size: 17px;
            font-weight: bold;
            margin: 5px;
        }

        /* =========================
           RECHTER BEREICH & PANELS
        ========================= */
        .main {
            flex: 1;
            height: 100vh;
            padding: 0;
            overflow-y: auto;
            background: linear-gradient(145deg, #191919, #050505);
        }

        .xg-panel, .ballbesitz-panel, .live-bereich {
            margin: 20px;
            padding: 25px;
            background: linear-gradient(145deg, #252525, #101010);
            border-radius: 25px;
            border: 1px solid #333;
        }

        .xg-panel h2, .ballbesitz-panel h2, .live-bereich h2 {
            color: #f5c542;
            margin-bottom: 15px;
        }

        /* =========================
           SPIELKOPF
        ========================= */
        .spielkopf {
            margin: 20px;
            height: 190px;
            display: grid;
            grid-template-columns: 1fr 220px 1fr;
            align-items: center;
            background: #111;
            border: 1px solid #333;
            border-radius: 30px;
        }

        .team {
            text-align: center;
            font-size: 40px;
            font-weight: bold;
        }

        .team.heim {
            color: var(--heim-farbe) !important;
        }

        .team.gast {
            color: var(--gast-farbe) !important;
        }

        .ergebnis {
            text-align: center;
            font-size: 85px;
            font-weight: bold;
            color: #f5c542;
        }

        /* =========================
           VISUELLE BALKEN & ANZEIGEN
        ========================= */
        .balken, .ballbalken {
            width: 100%;
            height: 45px;
            display: flex;
            background: #000;
            border-radius: 25px;
            overflow: hidden;
        }

        .heim-balken {
            background: var(--heim-farbe) !important;
        }

        .gast-balken {
            background: var(--gast-farbe) !important;
        }

        .heim-balken, .gast-balken {
            width: 50%;
        }

        #ballHeim, #ballGast, #xgBalkenHeim, #xgBalkenGast {
            width: 50%;
        }

        .xg-werte, .ballwerte {
            display: flex;
            justify-content: space-between;
            font-size: 28px;
            font-weight: bold;
            margin-bottom: 12px;
        }

        /* =========================
           TOP STATISTIKEN (GRID)
        ========================= */
        .top-statistik {
            margin: 20px;
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 20px;
        }

        .stat-box {
            background: linear-gradient(145deg, #333, #111);
            border-radius: 20px;
            border: 1px solid #444;
            padding: 20px;
            text-align: center;
        }

        .stat-box h3 {
            color: #aaa;
            font-size: 15px;
            margin-bottom: 15px;
        }

        .stat-werte {
            display: flex;
            justify-content: center;
            align-items: center;
            gap: 15px;
            font-size: 32px;
            font-weight: bold;
        }

        .heim-stat {
            color: var(--heim-farbe);
        }

        .gast-stat {
            color: var(--gast-farbe);
        }

        .stat-info {
            color: #777;
            margin-top: 8px;
            font-size: 13px;
        }

        /* =========================
           LIVE DATEN BEREICH
        ========================= */
        #liveDaten {
            width: 100%;
            height: 260px;
            background: #050505;
            color: white;
            border: 1px solid #555;
            border-radius: 15px;
            padding: 15px;
            resize: none;
            font-size: 16px;
        }
    </style>
</head>
<body>

<div class="app">

    <!-- LINKS -->
    <div class="sidebar">
        <h1>SPIELTAG</h1>
        <div class="spieltag-box">
            <textarea id="spieltagInput" placeholder="08.08.2026&#10;Bayern München&#10;Borussia Dortmund&#10;-"></textarea>
            <button onclick="spieltagLaden()">SPIELTAG LADEN</button>
            <div id="spielListe"></div>
        </div>
    </div>

    <!-- RECHTS -->
    <div class="main">
        <!-- Spielkopf -->
        <div class="spielkopf">
            <div class="team heim">HEIM</div>
            <div class="ergebnis">0 : 0</div>
            <div class="team gast">GAST</div>
        </div>

        <!-- xG Panel -->
        <div class="xg-panel">
            <h2>Expected Goals (xG)</h2>
            <div class="xg-werte">
                <span class="heim-wert" id="xgHeim">0.00</span>
                <span class="gast-wert" id="xgGast">0.00</span>
            </div>
            <div class="balken">
                <div id="xgBalkenHeim" class="heim-balken"></div>
                <div id="xgBalkenGast" class="gast-balken"></div>
            </div>
        </div>

        <!-- Ballbesitz Panel -->
        <div class="ballbesitz-panel">
            <h2>Ballbesitz</h2>
            <div class="ballwerte">
                <span class="heim-wert" id="ballTextHeim">50%</span>
                <span class="gast-wert" id="ballTextGast">50%</span>
            </div>
            <div class="ballbalken">
                <div id="ballHeim" class="heim-balken"></div>
                <div id="ballGast" class="gast-balken"></div>
            </div>
        </div>

        <!-- Top Statistiken Grid -->
        <div class="top-statistik">
            <!-- 1: Schüsse -->
            <div class="stat-box">
                <h3>SCHÜSSE</h3>
                <div class="stat-werte">
                    <span class="heim-stat" id="statSchuesseHeim">0</span>
                    :
                    <span class="gast-stat" id="statSchuesseGast">0</span>
                </div>
            </div>

            <!-- 2: Schüsse aufs Tor -->
            <div class="stat-box">
                <h3>SCHÜSSE AUFS TOR</h3>
                <div class="stat-werte">
                    <span class="heim-stat" id="statTorHeim">0</span>
                    :
                    <span class="gast-stat" id="statTorGast">0</span>
                </div>
            </div>

            <!-- 3: Grosschancen -->
            <div class="stat-box">
                <h3>GROSSCHANCEN</h3>
                <div class="stat-werte">
                    <span class="heim-stat" id="statChanceHeim">0</span>
                    :
                    <span class="gast-stat" id="statChanceGast">0</span>
                </div>
            </div>

            <!-- 4: Eckbälle -->
            <div class="stat-box">
                <h3>ECKBÄLLE</h3>
                <div class="stat-werte">
                    <span class="heim-stat" id="statEckenHeim">0</span>
                    :
                    <span class="gast-stat" id="statEckenGast">0</span>
