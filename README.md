<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>24-Hour Countdown Clock</title>
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
            text-align: center;
        }
    </style>
</head>
<body>
    <div id="countdown"></div>

    <script>
        function startCountdown() {
            // Calculate the target time 24 hours from now
            const targetTime = new Date().getTime() + 24 * 60 * 60 * 1000;

            const countdownInterval = setInterval(function() {
                const now = new Date().getTime();
                const distance = targetTime - now;

                const hoursLeft = Math.floor((distance % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
                const minutesLeft = Math.floor((distance % (1000 * 60 * 60)) / (1000 * 60));
                const secondsLeft = Math.floor((distance % (1000 * 60)) / 1000);

                document.getElementById("countdown").innerHTML =
                    hoursLeft + "h " + minutesLeft + "m " + secondsLeft + "s ";

                if (distance < 0) {
                    clearInterval(countdownInterval);
                    document.getElementById("countdown").innerHTML = "EXPIRED";
                }
            }, 1000);
        }

        // Start the countdown now
        startCountdown();
    </script>
</body>
</html>
