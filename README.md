<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=no">
    <meta name="apple-mobile-web-app-capable" content="yes">
    <meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">
    <title>Sonder</title>
    
    <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,700;1,400&family=Montserrat:wght@200;400&display=swap" rel="stylesheet">
    
    <style>
        :root {
            --primary: #1a1a1a;
            --accent: #c5a059; /* Luxury Gold Hint */
            --text: #ffffff;
            --glass: rgba(255, 255, 255, 0.03);
        }

        * { margin: 0; padding: 0; box-sizing: border-box; -webkit-tap-highlight-color: transparent; }

        body {
            background-color: var(--primary);
            color: var(--text);
            font-family: 'Montserrat', sans-serif;
            overflow-x: hidden;
        }

        .serif { font-family: 'Playfair Display', serif; }

        /* --- LOADING SCREEN --- */
        #loader {
            height: 100vh; display: flex; align-items: center; justify-content: center;
            background: #000; position: fixed; width: 100%; z-index: 100;
        }

        .symbol { font-size: 2rem; letter-spacing: 5px; animation: pulse 2s infinite; }

        /* --- GATEKEEPER --- */
        .screen {
            min-height: 100vh; padding: 40px 20px;
            display: flex; flex-direction: column; align-items: center;
            transition: 1s ease;
        }

        .hidden { display: none; opacity: 0; }

        .lock-input {
            background: transparent; border: none; border-bottom: 1px solid var(--accent);
            color: white; text-align: center; padding: 10px; font-size: 1.2rem;
            margin-bottom: 20px; outline: none; width: 200px;
        }

        /* --- MAIN APP --- */
        #main-app { justify-content: flex-start; }

        .app-nav {
            width: 100%; display: flex; justify-content: space-between;
            font-size: 0.6rem; letter-spacing: 3px; padding: 20px 0;
            border-bottom: 1px solid rgba(255,255,255,0.1); margin-bottom: 40px;
        }

        .vignette {
            width: 100%; max-width: 450px; background: var(--glass);
            border: 1px solid rgba(255,255,255,0.05); border-radius: 2px;
            padding: 30px; margin-bottom: 25px; position: relative;
        }

        video { width: 100%; border-radius: 2px; filter: contrast(1.1) brightness(0.9); }

        .memory-btn {
            background: transparent; border: 1px solid var(--accent);
            color: var(--accent); padding: 10px 20px; font-size: 0.7rem;
            letter-spacing: 2px; cursor: pointer; margin-top: 15px;
        }

        /* THE HINT: A subtle glowing text */
        .hint-text {
            font-size: 0.8rem; line-height: 1.8; color: rgba(255,255,255,0.6);
        }

        .special-word {
            color: var(--text); position: relative; cursor: pointer;
            transition: 0.3s;
        }

        .special-word:active { color: var(--accent); }

        @keyframes pulse {
            0% { opacity: 0.3; }
            50% { opacity: 1; }
            100% { opacity: 0.3; }
        }
    </style>
</head>
<body>

    <div id="loader" onclick="this.style.display='none'">
        <div class="symbol serif">SONDER</div>
    </div>

    <div id="lock-screen" class="screen">
        <div style="margin-top: 20vh; text-align: center;">
            <p class="serif" style="font-style: italic; margin-bottom: 30px;">Access Private Server</p>
            <input type="password" id="passCode" class="lock-input" placeholder="••••">
            <br>
            <button class="memory-btn" onclick="unlock()">Enter</button>
        </div>
    </div>

    <div id="main-app" class="screen hidden">
        <div class="app-nav">
            <span>VERSION 1.0.4</span>
            <span class="serif">SONDER</span>
            <span>INDEX: 001</span>
        </div>

        <div class="vignette">
            <h2 class="serif" style="margin-bottom: 20px; font-weight: 400;">The Edit.</h2>
            <video controls playsinline poster="your-thumb.jpg">
                <source src="your-video.mp4" type="video/mp4">
            </video>
        </div>

        <div class="vignette" style="text-align: center;">
            <p id="memText" class="hint-text" style="min-height: 50px;">A digital space for the moments that matter.</p>
            <button class="memory-btn" onclick="newMem()">FETCH MEMORY</button>
        </div>

        <div class="vignette">
            <p class="hint-text">
                I built this because some connections aren't meant for the noise of social media. 
                They deserve a <span class="special-word" onclick="alert('You really are one of one.')">dedicated space</span>. 
                Thanks for being the person you are.
            </p>
        </div>

        <p style="font-size: 0.5rem; letter-spacing: 2px; margin-top: 40px; opacity: 0.3;">DESIGNED BY [YOUR NAME] — 2026</p>
    </div>

    <script>
        function unlock() {
            const code = "0000"; // SET YOUR 4-DIGIT OR WORD CODE HERE
            if(document.getElementById('passCode').value.toLowerCase() === code) {
                document.getElementById('lock-screen').style.display = 'none';
                document.getElementById('main-app').classList.remove('hidden');
            }
        }

        const memos = [
            "The way you handle everything is honestly impressive.",
            "That specific conversation that changed how I see things.",
            "A reminder that you're probably the coolest person in my circle.",
            "The energy you bring is actually unmatched."
        ];

        function newMem() {
            const m = memos[Math.floor(Math.random() * memos.length)];
            document.getElementById('memText').innerText = m;
        }
    </script>
</body>
</html>
