<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Countdown Clock</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            background-color: #282c34;
            color: white;
            position: relative;
        }
        #countdown {
            font-size: 48px;
            color: #FFD700;
            position: absolute;
            top: 20px;
            right: 20px;
        }
        .buttons {
            position: absolute;
            top: 20px;
            left: 20px;
        }
        .buttons button {
            margin: 5px;
            padding: 10px 20px;
            font-size: 16px;
            background-color: #61dafb;
            border: none;
            border-radius: 5px;
            color: black;
            cursor: pointer;
        }
        .buttons button:hover {
            background-color: #21a1f1;
        }
        .clock-container {
            display: flex;
            justify-content: center;
            align-items: center;
            width: 100%;
            height: 100%;
        }
        .clock-image {
            width: 50%;
            height: auto;
            opacity: 0.8;
        }
    </style>
</head>
<body>
    <div class="buttons">
        <button onclick="startCountdown(24)">24 Hours</button>
        <button onclick="startCountdown(48)">48 Hours</button>
        <button onclick="startCountdown(72)">72 Hours</button>
    </div>
    <div id="countdown">Choose an option to start the countdown</div>
    <div class="clock-container">
        <img src="https://example.com/clock-image.jpg" alt="Clock" class="clock-image">
    </div>

    <script>
        let countdownInterval;

        function startCountdown(hours) {
            // Clear any existing countdown
            clearInterval(countdownInterval);

            // Calculate the target time based on the selected hours
            const targetTime = new Date().getTime() + hours * 60 * 60 * 1000;

            countdownInterval = setInterval(function() {
                const now = new Date().getTime();
                const distance = targetTime - now;

                const hoursLeft = Math.floor((distance % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
                const minutesLeft = Math.floor((distance % (1000 * 60 * 60)) / (1000 * 60));
                const secondsLeft = Math.floor((distance % (1000 * 60)) / 1000);

                document.getElementById("countdown").innerHTML =
                    hoursLeft + "h " + minutesLeft + "m " + secondsLeft + "s ";

                // If the countdown is over, stop the interval and show a message
                if (distance < 0) {
                    clearInterval(countdownInterval);
                    document.getElementById("countdown").innerHTML = "EXPIRED";
                }
            }, 1000);
        }
    </script>
</body>
</html>
