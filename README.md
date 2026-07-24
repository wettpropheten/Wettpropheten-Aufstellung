<!DOCTYPE html>
<html lang="de">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Wettpropheten-Aufstellung</title>
    <style>
        :root {
            --bg-dark: #071739;
            --field-green: #388e3c;
            --field-lines: rgba(255, 255, 255, 0.6);
            --banner-white: #ffffff;
            --box-blue: #0f306e;
            --text-light: #ffffff;
        }

        body {
            font-family: 'Arial', sans-serif;
            background-color: var(--bg-dark);
            /* Diagonale Streifen exakt wie in deinem Hintergrund */
            background-image: linear-gradient(135deg, rgba(255,255,255,0.03) 25%, transparent 25%, transparent 50%, rgba(255,255,255,0.03) 50%, rgba(255,255,255,0.03) 75%, transparent 75%, transparent);
            background-size: 40px 40px;
            color: var(--text-light);
            margin: 0;
            padding: 40px 20px;
            display: flex;
            justify-content: center;
        }

        .dashboard {
            width: 100%;
            max-width: 1100px;
        }

        /* BANNER OBEN */
        .vs-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 60px;
            gap: 10px;
        }

        .team-banner {
            background: var(--banner-white);
            border-radius: 40px;
            height: 65px;
            display: flex;
            align-items: center;
            padding: 0 15px;
            width: 42%;
            box-shadow: 0 8px 20px rgba(0,0,0,0.3);
            box-sizing: border-box;
        }

        .team-banner.left { justify-content: flex-start; }
        .team-banner.right { justify-content: flex-end; flex-direction: row-reverse; }

        .logo-box {
            width: 50px;
            height: 50px;
            background: radial-gradient(circle, #3a7bd5, #3a6073);
            border-radius: 50%;
            border: 3px solid #ccc;
            display: flex;
            align-items: center;
            justify-content: center;
            position: relative;
            cursor: pointer;
            overflow: hidden;
        }

        .logo-box::before {
            content: '⚽';
            color: rgba(255,255,255,0.7);
            font-size: 20px;
        }

        .logo-box img {
            position: absolute;
            width: 100%;
            height: 100%;
            object-fit: cover;
            top: 0; left: 0;
        }

        .logo-box input {
            position: absolute;
            opacity: 0;
            width: 100%;
            height: 100%;
            cursor: pointer;
            z-index: 2;
        }

        .team-name-input {
            background: transparent;
            border: none;
            color: #0d295c;
            font-size: 26px;
            font-weight: 900;
            text-transform: uppercase;
            width: 75%;
            padding: 5px 15px;
            font-family: 'Impact', sans-serif;
        }
        .team-banner.right .team-name-input { text-align: right; }
        .team-name-input:focus { outline: none; }

        .vs-badge {
            background: linear-gradient(to bottom, #00c6ff, #0072ff);
            color: white;
            font-size: 32px;
            font-weight: 900;
            padding: 8px 25px;
            border-radius: 10px;
            box-shadow: 0 0 25px rgba(0, 114, 255, 0.7);
            font-style: italic;
            border: 2px solid #fff;
        }

        /* 3D CONTAINER STAGE */
        .fields-stage {
            perspective: 1200px;
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 50px;
            margin-bottom: 60px;
        }

        .field-3d-container {
            position: relative;
            transform: rotateX(55deg) rotateZ(-25deg);
            transform-style: preserve-3d;
        }

        .football-field {
            background-color: var(--field-green);
            height: 480px;
            border: 5px solid var(--field-lines);
            box-shadow: -15px 15px 0px #1b5e20, -30px 30px 30px rgba(0,0,0,0.6);
            position: relative;
            background-image: linear-gradient(to bottom, rgba(255,255,255,0.08) 50%, transparent 50%);
            background-size: 100% 60px;
        }

        .field-lines-overlay {
            position: absolute;
            top: 0; left: 0; width: 100%; height: 100%;
            border-bottom: 3px solid var(--field-lines);
            pointer-events: none;
        }
        .field-lines-overlay::before {
            content: ''; position: absolute; bottom: 0; left: 20%; right: 20%; height: 80px;
            border: 4px solid var(--field-lines); border-bottom: none;
        }
        .field-lines-overlay::after {
            content: ''; position: absolute; top: 0; left: 20%; right: 20%; height: 80px;
            border: 4px solid var(--field-lines); border-top: none;
        }

        /* SPIELER POSITIONEN */
        .formation-layout {
            position: absolute;
            width: 100%; height: 100%;
            display: flex;
            flex-direction: column;
            justify-content: space-around;
            padding: 20px 0;
            box-sizing: border-box;
            transform-style: preserve-3d;
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
            transform: rotateZ(25deg) rotateX(-55deg) scale(0.9); 
        }

        .jersey {
            width: 32px;
            height: 32px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 12px;
            font-weight: bold;
            box-shadow: 0 5px 5px rgba(0,0,0,0.5);
            border: 2px solid white;
        }
        .left-side .jersey { background: linear-gradient(90deg, #1e88e5 50%, #1565c0 50%); color: white; }
        .left-side .gk-jersey { background: linear-gradient(90deg, #e0e0e0 50%, #9e9e9e 50%); color: black; }
        
        .right-side .jersey { background: #fdd835; color: black; border-color: #333; }
        .right-side .gk-jersey { background: linear-gradient(90deg, #e53935 50%, #b71c1c 50%); color: white; }

        .player-input {
            background: white;
            border: none;
            border-radius: 3px;
            color: black;
            font-size: 10px;
            font-weight: bold;
            width: 75px;
            text-align: center;
            margin-top: 4px;
            box-shadow: 0 2px 4px rgba(0,0,0,0.3);
            text-transform: uppercase;
        }

        /* FOOTER / LISTEN */
        .roster-stage {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 40px;
        }

        .roster-card {
            background: var(--box-blue);
            border-radius: 6px;
            padding: 20px;
            box-shadow: 0 10px 25px rgba(0,0,0,0.4);
            display: grid;
            grid-template-columns: 1.2fr 1fr;
            gap: 15px;
            border-top: 4px solid #1e88e5;
        }
        .roster-card.right-card { border-top-color: #fdd835; }

        .main-lineup {
            display: flex;
            flex-direction: column;
            gap: 4px;
        }

        .player-row {
            display: flex;
            align-items: center;
            background: rgba(255,255,255,0.08);
            padding: 3px 8px;
            border-radius: 3px;
        }

        .player-number {
            font-weight: bold;
            font-size: 13px;
            color: #64b5f6;
            margin-right: 10px;
            width: 18px;
        }
        .right-card .player-number { color: #fff176; }

        .row-input {
            background: transparent;
            border: none;
            color: white;
            font-size: 13px;
            width: 100%;
            text-transform: uppercase;
        }
        .row-input:focus { outline: none; }

        .meta-section {
            display: flex;
            flex-direction: column;
        }

        .formation-badge {
            font-size: 42px;
            font-weight: 900;
            font-family: 'Impact', sans-serif;
            color: white;
            line-height: 1;
            margin-bottom: 10px;
            letter-spacing: 2px;
        }

        .sub-label {
            font-size: 11px;
            font-weight: bold;
            color: #90caf9;
            text-transform: uppercase;
            letter-spacing: 1px;
            margin-top: 5px;
            margin-bottom: 3px;
        }
        .right-card .sub-label { color: #fff59d; }

        .sub-box {
            display: flex;
            flex-direction: column;
            gap: 3px;
            margin-bottom: 10px;
        }
    </style>
</head>
<body>

<div class="dashboard">

    <!-- TOP HEADER -->
    <div class="vs-header">
        <div class="team-banner left">
            <div class="logo-box"><input type="file" accept="image/*" onchange="uploadLogo(this)"></div>
            <input type="text" class="team-name-input" value="TEAM NAME">
        </div>
        <div class="vs-badge">VS</div>
        <div class="team-banner right">
            <div class="logo-box"><input type="file" accept="image/*" onchange="uploadLogo(this)"></div>
            <input type="text" class="team-name-input" value="TEAM NAME">
        </div>
    </div>

    <!-- 3D SPIELFELDER -->
    <div class="fields-stage">
        <!-- Team Links -->
        <div class="field-3d-container left-side">
            <div class="football-field">
                <div class="field-lines-overlay"></div>
