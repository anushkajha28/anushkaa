<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mood Analyser</title>
    <style>
        :root {
            --bg-gradient: linear-gradient(135deg, #a8edea 0%, #fed6e3 100%);
            --card-border: linear-gradient(to bottom right, #b2e2f2, #fbc2eb, #a6c1ee);
            --text-blue: #7fb3d5;
            --text-orange: #ffab91;
            --happy-green: #c8e6c9;
        }

        body {
            margin: 0;
            padding: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            background: var(--bg-gradient);
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        /* The Main Glassmorphism Card */
        .card-container {
            position: relative;
            padding: 10px;
            background: var(--card-border);
            border-radius: 50px;
            box-shadow: 0 20px 40px rgba(0,0,0,0.1);
        }

        .card {
            background: white;
            border-radius: 40px;
            padding: 40px;
            width: 400px;
            text-align: center;
            position: relative;
        }

        h1 {
            font-size: 2rem;
            margin-bottom: 30px;
        }

        .title-how { color: #5dade2; }
        .title-feel { color: #f1948a; }
        .title-today { color: #f8c471; }

        /* Input Styles */
        .input-group {
            position: relative;
            margin-bottom: 15px;
        }

        .input-group input {
            width: 85%;
            padding: 12px 20px 12px 40px;
            border-radius: 25px;
            border: 2px solid #ffe082;
            outline: none;
            font-size: 1rem;
            color: #555;
        }

        .input-group::before {
            content: '🔍';
            position: absolute;
            left: 25px;
            top: 50%;
            transform: translateY(-50%);
            font-size: 0.9rem;
            opacity: 0.5;
        }

        .secondary-input {
            border: 1px solid #eee !important;
            color: #aaa !important;
        }

        /* Result Section */
        .result-area {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-top: 30px;
            min-height: 120px;
        }

        .sun-icon {
            font-size: 80px;
            animation: rotate 10s linear infinite;
        }

        @keyframes rotate {
            from { transform: rotate(0deg); }
            to { transform: rotate(360deg); }
        }

        .mood-badge {
            background: #e8f5e9;
            padding: 15px 25px;
            border-radius: 15px;
            display: flex;
            align-items: center;
            gap: 10px;
            box-shadow: inset 0 0 10px rgba(255,255,255,0.8);
            border: 1px solid #c8e6c9;
        }

        .check-mark {
            background: #4caf50;
            color: white;
            width: 30px;
            height: 30px;
            border-radius: 50%;
            display: flex;
            justify-content: center;
            align-items: center;
            font-weight: bold;
        }

        .mood-text {
            color: #ff7043;
            font-weight: 800;
            font-size: 1.2rem;
            letter-spacing: 1px;
        }

        .footer-msg {
            margin-top: 10px;
            color: #777;
            font-size: 0.9rem;
        }
    </style>
</head>
<body>

    <div class="card-container">
        <div class="card">
            <h1>
                <span class="title-how">How dou</span> 
                <span class="title-feel">feel</span> 
                <span class="title-today">today?</span>
            </h1>

            <div class="input-group">
                <input type="text" id="moodInput" placeholder="The weather is nice today!" oninput="updateMood()">
            </div>

            <div class="input-group">
                <input type="text" class="secondary-input" placeholder="Type weather here..." disabled>
            </div>

            <div class="result-area">
                <div class="sun-icon">☀️</div>
                <div class="mood-container">
                    <div class="mood-badge">
                        <div class="check-mark">✓</div>
                        <div class="mood-text" id="moodLabel">HAPPY!</div>
                    </div>
                    <p class="footer-msg">Yay! Keep smiling!</p>
                </div>
            </div>
        </div>
    </div>

    <script>
        function updateMood() {
            const input = document.getElementById('moodInput').value.toLowerCase();
            const label = document.getElementById('moodLabel');
            
            // Simple logic to change text based on input
            if(input.includes('sad') || input.includes('bad')) {
                label.innerText = "HOPEFUL!";
            } else if (input.includes('angry') || input.includes('mad')) {
                label.innerText = "CALM!";
            } else {
                label.innerText = "HAPPY!";
            }
        }
    </script>
</body>
</html>
