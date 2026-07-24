<!DOCTYPE html>
<html lang="de">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Fußball Taktik Board</title>
    <style>
        :root {
            --bg-color: #0b1a30;
            --field-green: #2e7d32;
            --field-lines: rgba(255, 255, 255, 0.5);
            --card-bg: #15294a;
            --text-color: #ffffff;
            --blue-team: #1e88e5;
            --yellow-team: #fdd835;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: var(--bg-color);
            color: var(--text-color);
            margin: 0;
            padding: 20px;
            display: flex;
            flex-direction: column;
            align-items: center;
        }

        .dashboard {
            width: 100%;
            max-width: 1200px;
            background: #0f2342;
            padding: 20px;
            border-radius: 15px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.5);
        }

        /* Header / Scoreboard style */
        .vs-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            background: linear-gradient(90deg, #16325c, #0b1a30, #16325c);
            padding: 15px 30px;
            border-radius: 10px;
            margin-bottom: 30px;
            border: 1px solid #23467c;
        }

        .team-input-zone {
            display: flex;
            align-items: center;
            gap: 15px;
            width: 40%;
        }

        .team-input-zone.right {
            flex-direction: row-reverse;
        }

        .logo-uploader {
            width: 60px;
            height: 60px;
            background: #fff;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            overflow: hidden;
            border: 3px solid #fff;
            position: relative;
        }

        .logo-uploader img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }

        .logo-uploader input {
            position: absolute;
            opacity: 0;
            width: 100%;
            height: 100%;
            cursor: pointer;
        }

        .team-name-input {
            background: transparent;
            border: none;
            border-bottom: 2px solid #fff;
            color: #fff;
            font-size: 24px;
            font-weight: bold;
            text-transform: uppercase;
            width: 100%;
            padding: 5px;
        }

        .vs-badge {
            background: #1e88e5;
            padding: 10px 20px;
            font-weight: bold;
            font-size: 22px;
            border-radius: 5px;
            box-shadow: 0 0 15px rgba(30, 136, 229, 0.6);
        }

        /* Spielfelder Container */
        .fields-container {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 30px;
            margin-bottom: 30px;
        }

        .field-box {
            background: #132a4f;
            padding: 15px;
            border-radius: 10px;
            box-shadow: inset 0 0 20px rgba(0,0,0,0.4);
        }

        .football-field {
            background-color: var(--field-green);
            height: 450px;
            border: 3px solid var(--field-lines);
            border-radius: 5px;
            position: relative;
            overflow: hidden;
            background-image: linear-gradient(to bottom, rgba(255,255,255,0.05) 50%, transparent 50%);
            background-size: 100% 50px;
        }

        /* Strafraum & Mittellinie */
        .football-field::before {
            content: '';
            position: absolute;
            top: 0; left: 10%; right: 10%; bottom: 0;
            border-left: 3px solid var(--field-lines);
            border-right: 3px solid var(--field-lines);
            pointer-events: none;
        }

        /* Spieler-System (Flex/Grid-Anordnung simuliert Formation) */
        .formation-grid {
            position: absolute;
            width: 100%;
            height: 100%;
            display: flex;
            flex-direction: column-reverse; /* Von Torwart zu Sturm */
            justify-content: space-around;
            padding: 10px 0;
            box-sizing: border-box;
        }

        .formation-row {
            display: flex;
            justify-content: space-around;
            width: 100%;
        }

        .player-token {
            display: flex;
            flex-direction: column;
            align-items: center;
            width: 80px;
        }

        .shirt {
            width: 35px;
            height: 35px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: bold;
            font-size: 12px;
            box-shadow: 0 4px 6px rgba(0,0,0,0.3);
            border: 2px solid #fff;
        }

        .blue-team .shirt { background-color: var(--blue-team); color: white; }
        .blue-team .gk { background-color: #e0e0e0; color: #333; }

        .yellow-team .shirt { background-color: var(--yellow-team); color: black; border-color: #000; }
        .yellow-team .gk { background-color: #ff5722; color: white; }

        .player-name-field {
            background: rgba(255, 255, 255, 0.9);
            border: none;
            border-radius: 3px;
            color: #000;
            font-size: 11px;
            width: 75px;
            text-align: center;
            margin-top: 5px;
            font-weight: bold;
        }

        /* Roster & Listen unten */
        .roster-container {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 30px;
        }

        .roster-box {
            background: var(--card-bg);
            padding: 20px;
            border-radius: 10px;
            border: 1px solid #23467c;
        }

        .roster-title-row {
            display: flex;
            justify-content: space-between;
            align-items: center;
            border-bottom: 2px solid #23467c;
            padding-bottom: 10px;
            margin-bottom: 15px;
        }

        .formation-title {
            font-size: 32px;
            font-weight: bold;
            color: #4ba3ff;
        }

        .player-list {
            display: grid;
            grid-template-columns: 1fr;
            gap: 5px;
            margin-bottom: 15px;
        }

        .list-row {
            display: flex;
            align-items: center;
            background: rgba(255,255,255,0.05);
            padding: 4px 10px;
            border-radius: 4px;
        }

        .list-num {
            font-weight: bold;
            width: 30px;
            color: #8da2c4;
        }

        .list-input {
            background: transparent;
            border: none;
            color: #fff;
            width: 100%;
            font-size: 14px;
        }
        .list-input:focus {
            outline: 1px solid #1e88e5;
            background: rgba(255,255,255,0.1);
        }

        .section-label {
            font-size: 14px;
            text-transform: uppercase;
            color: #8da2c4;
            letter-spacing: 1px;
            margin-top: 15px;
            margin-bottom: 5px;
            font-weight: bold;
        }
    </style>
</head>
<body>

<div class="dashboard">
    
    <!-- VS HEADER MIT LOGO UPLOAD -->
    <div class="vs-header">
        <div class="team-input-zone">
            <div class="logo-uploader">
                <span>➕</span>
                <input type="file" accept="image/*" onchange="previewImage(this)">
            </div>
            <input type="text" class="team-name-input" value="TEAM HEIM">
        </div>
        
        <div class="vs-badge">VS</div>
        
        <div class="team-input-zone right">
            <div class="logo-uploader">
                <span>➕</span>
                <input type="file" accept="image/*" onchange="previewImage(this)">
            </div>
            <input type="text" class="team-name-input" value="TEAM GAST" style="text-align: right;">
        </div>
    </div>

    <!-- SPIELFELDER -->
    <div class="fields-container">
        <!-- Team Blau (4-4-2) -->
        <div class="field-box blue-team">
            <div class="football-field">
                <div class="formation-grid">
                    <!-- Torwart -->
                    <div class="formation-row">
                        <div class="player-token"><div class="shirt gk">1</div><input type="text" class="player-name-field" value="Spieler 1" data-sync="b1"></div>
                    </div>
                    <!-- Abwehr -->
                    <div class="formation-row">
                        <div class="player-token"><div class="shirt">2</div><input type="text" class="player-name-field" value="Spieler 2" data-sync="b2"></div>
                        <div class="player-token"><div class="shirt">3</div><input type="text" class="player-name-field" value="Spieler 3" data-sync="b3"></div>
                        <div class="player-token"><div class="shirt">4</div><input type="text" class="player-name-field" value="Spieler 4" data-sync="b4"></div>
                        <div class="player-token"><div class="shirt">5</div><input type="text" class="player-name-field" value="Spieler 5" data-sync="b5"></div>
                    </div>
                    <!-- Mittelfeld -->
                    <div class="formation-row">
                        <div class="player-token"><div class="shirt">6</div><input type="text" class="player-name-field" value="Spieler 6" data-sync="b6"></div>
                        <div class="player-token"><div class="shirt">7</div><input type="text" class="player-name-field" value="Spieler 7" data-sync="b7"></div>
