<!DOCTYPE html>
<html lang="de">
<head>
    <meta charset="UTF-8">
    <title>Wettpropheten Taktik Board Pro</title>
    <style>
        body {
            background-color: #071739;
            background-image: linear-gradient(135deg, rgba(255,255,255,0.03) 25%, transparent 25%, transparent 50%, rgba(255,255,255,0.03) 50%, rgba(255,255,255,0.03) 75%, transparent 75%, transparent);
            background-size: 40px 40px;
            color: #ffffff;
            font-family: 'Arial', sans-serif;
            margin: 0;
            padding: 30px 20px;
            display: flex;
            justify-content: center;
        }

        .main-container {
            width: 100%;
            max-width: 1200px;
            display: flex;
            flex-direction: column;
            gap: 30px;
        }

        /* 1. TOP HEADER BANNER (WIE IM BILD) */
        .vs-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            gap: 20px;
            width: 100%;
        }

        .team-banner {
            background: #ffffff;
            border-radius: 40px;
            height: 65px;
            display: flex;
            align-items: center;
            padding: 0 20px;
            width: 43%;
            box-shadow: 0 5px 15px rgba(0,0,0,0.3);
            box-sizing: border-box;
        }

        .team-banner.right { flex-direction: row-reverse; }

        .logo-upload {
            width: 48px;
            height: 48px;
            background: linear-gradient(135deg, #1e3c72, #2a5298);
            border-radius: 50%;
            position: relative;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            box-shadow: inset 0 2px 5px rgba(0,0,0,0.5);
        }
        .logo-upload::before { content: '⚽'; font-size: 20px; }
        .logo-upload img { position: absolute; width: 100%; height: 100%; object-fit: cover; border-radius: 50%; top: 0; left: 0; }
        .logo-upload input { position: absolute; opacity: 0; width: 100%; height: 100%; cursor: pointer; }

        .team-input {
            background: transparent;
            border: none;
            color: #0d295c;
            font-size: 26px;
            font-weight: 900;
            text-transform: uppercase;
            width: 80%;
            padding: 5px 10px;
        }
        .team-banner.right .team-input { text-align: right; }
        .team-input:focus { outline: none; background: rgba(0,0,0,0.03); border-radius: 5px; }

        .vs-badge {
            background: linear-gradient(to bottom, #00c6ff, #0072ff);
            color: white;
            font-size: 26px;
            font-weight: 900;
            padding: 10px 30px;
            border-radius: 35px;
            border: 2px solid #fff;
            box-shadow: 0 0 20px rgba(0, 114, 255, 0.5);
            font-style: italic;
        }

        /* ROW CONTAINER FÜR SPIELFELDER & KARTEN */
        .grid-row {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 40px;
            width: 100%;
        }

        /* 2. SPIELFELDER (FLACHES MODERNES DESIGN) */
        .field-card {
            background: #132a4f;
            padding: 20px;
            border-radius: 12px;
            box-shadow: 0 10px 25px rgba(0,0,0,0.4);
            border: 1px solid #1f3d6b;
        }

        .football-pitch {
            background-color: #2e7d32;
            height: 420px;
            border: 3px solid rgba(255,255,255,0.6);
            border-radius: 6px;
            position: relative;
            background-image: linear-gradient(to bottom, rgba(255,255,255,0.04) 50%, transparent 50%);
            background-size: 100% 50px;
            display: flex;
            flex-direction: column;
            justify-content: space-around;
            padding: 15px 0;
            box-sizing: border-box;
        }

        .pitch-line {
            display: flex;
            justify-content: space-around;
            width: 100%;
            min-height: 55px;
        }

        .player-token {
            display: flex;
            flex-direction: column;
            align-items: center;
            width: 85px;
        }

        .jersey-circle {
            width: 30px;
            height: 30px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 12px;
            font-weight: bold;
            border: 2px solid white;
            box-shadow: 0 4px 6px rgba(0,0,0,0.4);
        }
        .left-side .jersey-circle { background: linear-gradient(135deg, #1e88e5, #1565c0); color: white; }
        .left-side .gk-unit { background: linear-gradient(135deg, #e0e0e0, #9e9e9e); color: black; }
        .right-side .jersey-circle { background: linear-gradient(135deg, #fdd835, #fbc02d); color: black; border-color: #333; }
        .right-side .gk-unit { background: linear-gradient(135deg, #e53935, #b71c1c); color: white; border-color: white; }

        .pitch-name-display {
            background: rgba(255, 255, 255, 0.95);
            border: none;
            border-radius: 3px;
            color: #000000;
            font-size: 10px;
            font-weight: bold;
            width: 80px;
            text-align: center;
            margin-top: 4px;
            box-shadow: 0 2px 5px rgba(0,0,0,0.3);
            text-transform: uppercase;
        }

        /* 3. MANNSCHAFTSKARTEN UNTEN */
        .roster-card {
            background: #0f306e;
            border-radius: 8px;
            padding: 20px;
            box-shadow: 0 8px 20px rgba(0,0,0,0.4);
            display: grid;
            grid-template-columns: 1.2fr 1fr;
            gap: 20px;
            border-top: 5px solid #1e88e5;
            border-bottom: 1px solid #1f3d6b;
        }
        .roster-card.right-card { border-top-color: #fdd835; }

        .lineup-list {
            display: flex;
            flex-direction: column;
            gap: 5px;
        }

        .player-input-row {
            display: flex;
            align-items: center;
            background: rgba(255,255,255,0.06);
            padding: 5px 10px;
            border-radius: 4px;
            border: 1px solid rgba(255,255,255,0.03);
        }

        .number-badge {
            font-weight: bold;
            font-size: 13px;
            color: #64b5f6;
            width: 24px;
        }
        .right-card .number-badge { color: #fff176; }

        .card-name-input {
            background: transparent;
            border: none;
            color: #ffffff;
            font-size: 13px;
            width: 100%;
            text-transform: uppercase;
            font-weight: 600;
        }
        .card-name-input:focus { outline: none; background: rgba(255,255,255,0.05); }

        .controls-sidebar {
            display: flex;
            flex-direction: column;
        }

        /* DROPKLICK STYLING (DROP-DOWNS) */
        .dropdown-label {
            font-size: 11px;
            font-weight: bold;
            color: #90caf9;
            text-transform: uppercase;
            margin-bottom: 5px;
            letter-spacing: 1px;
        }
        .right-card .dropdown-label { color: #fff59d; }

        .dropklick-select {
            background: #15294a;
            color: white;
            border: 2px solid #23467c;
            padding: 8px 12px;
            font-size: 16px;
            font-weight: bold;
            border-radius: 6px;
            cursor: pointer;
            width: 100%;
            margin-bottom: 20px;
            outline: none;
        }
        .dropklick-select:focus { border-color: #0072ff; }

        .sub-header {
            font-size: 12px;
            font-weight: bold;
            color: #90caf9;
            text-transform: uppercase;
            margin: 5px 0;
            letter-spacing: 0.5px;
        }
        .right-card .sub-header { color: #fff59d; }

        .sub-box {
            display: flex;
            flex-direction: column;
            gap: 5px;
            margin-bottom: 15px;
        }
    </style>
</head>
<body>

<div class="main-container">

    <!-- VS HEADER BANNER MIT LOGO-UPLOAD -->
    <div class="vs-header">
        <div class="team-banner left">
            <div class="logo-upload"><input type="file" accept="image/*" onchange="previewLogo(this)"></div>
            <input type="text" class="team-input" value="TEAM HEIM">
        </div>
        <div class="vs-badge">VS</div>
        <div class="team-banner right">
            <div class="logo-upload"><input type="file" accept="image/*" onchange="previewLogo(this)"></div>
            <input type="text" class="team-input" value="TEAM GAST">
        </div>
    </div>

    <!-- SPIELFELDER ZEILE -->
    <div class="grid-row">
        <!-- Links Spielfeld Container -->
        <div class="field-card left-side">
            <div class="football-pitch" id="pitch-left">
                <!-- Wird dynamisch per JavaScript befüllt -->
            </div>
        </div>

        <!-- Rechts Spielfeld Container -->
        <div class="field-card right-side">
            <div class="football-pitch" id="pitch-right">
                <!-- Wird dynamisch per JavaScript befüllt -->
            </div>
        </div>
    </div>

    <!-- MANNSCHAFTSKARTEN ZEILE -->
    <div class="grid-row">
        <!-- Karte Links -->
        <div class="roster-card">
            <div class="lineup-list" id="list-left">
                <!-- 11 Startspieler Inputs -->
            </div>
            <div class="controls-sidebar">
                <div class="dropdown-label">Formation (Dropklick)</div>
                <select class="dropklick-select" onchange="changeFormation('left', this.value)">
                    <option value="4-4-2">4-4-2</option>
                    <option value="4-3-3">4-3-3</option>
