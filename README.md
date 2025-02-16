# sans-birthday
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Happy Birthday Sansrita!</title>
    <style>
        body {
            margin: 0;
            overflow: hidden;
            background-color: #ffccff;
            text-align: center;
            font-family: 'Comic Sans MS', cursive, sans-serif;
        }

        h1 {
            margin-top: 50px;
            color: #fff;
            text-shadow: 2px 2px #000;
            font-size: 3em;
        }

        .balloon {
            position: absolute;
            bottom: -100px;
            width: 50px;
            height: 70px;
            background: radial-gradient(circle at 30% 30%, #ff4d4d, #c40000);
            border-radius: 50% 50% 60% 60%;
            animation: floatBalloon 5s linear infinite;
        }

        @keyframes floatBalloon {
            0% { transform: translateY(0); opacity: 1; }
            100% { transform: translateY(-110vh); opacity: 0; }
        }

        .candle {
            position: absolute;
            bottom: 30px;
            width: 20px;
            height: 60px;
            background-color: #fff;
            border: 2px solid #000;
            border-radius: 5px;
        }

        .flame {
            position: absolute;
            top: -20px;
            left: 5px;
            width: 10px;
            height: 20px;
            background: radial-gradient(circle, #ffcc00, #ff6600);
            border-radius: 50%;
            animation: flicker 0.5s infinite;
        }

        @keyframes flicker {
            0%, 100% { transform: scaleY(1); opacity: 1; }
            50% { transform: scaleY(1.3); opacity: 0.7; }
        }

        #message {
            position: absolute;
            top: 45%;
            width: 100%;
            font-size: 2em;
            color: #fff;
            text-shadow: 2px 2px #000;
            display: none;
        }
    </style>
</head>
<body>
    <h1>🎂 Happy 26th Birthday Sansrita! 🎉</h1>
    <div id="message">🎊 Wishing you a day as magical as you are! May your dreams float higher than these balloons and your happiness shine brighter than these candles! 🎊</div>

    <audio id="song" src="https://www.soundhelix.com/examples/mp3/SoundHelix-Song-1.mp3" loop></audio>

    <script>
        function createBalloons() {
            for (let i = 0; i < 30; i++) {
                const balloon = document.createElement('div');
                balloon.className = 'balloon';
                balloon.style.left = `${Math.random() * 100}vw`;
                balloon.style.background = `radial-gradient(circle at 30% 30%, hsl(${Math.random() * 360}, 70%, 60%), hsl(${Math.random() * 360}, 70%, 40%))`;
                balloon.style.animationDuration = `${3 + Math.random() * 3}s`;
                document.body.appendChild(balloon);
            }
        }

        function createCandles() {
            for (let i = 0; i < 10; i++) {
                const candle = document.createElement('div');
                candle.className = 'candle';
                candle.style.left = `${10 + i * 8}vw`;

                const flame = document.createElement('div');
                flame.className = 'flame';
                candle.appendChild(flame);

                candle.addEventListener('click', () => {
                    flame.style.display = 'none';
                    checkCandles();
                });
                document.body.appendChild(candle);
            }
        }

        function checkCandles() {
            const flames = document.querySelectorAll('.flame');
            const allOut = [...flames].every(f => f.style.display === 'none');
            if (allOut) {
                document.getElementById('message').style.display = 'block';
                document.getElementById('song').play();
            }
        }

        createBalloons();
        createCandles();
    </script>
</body>
</html>
