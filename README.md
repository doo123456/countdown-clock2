<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>24-Hour Countdown</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            background-color: #282c34;
            color: white;
        }
        #logo {
            width: 200px; /* Adjust the size as needed */
            height: auto;
            margin-bottom: 20px;
        }
        #countdown {
            font-size: 48px;
            color: #FFD700;
        }
    </style>
</head>
<body>
    <!-- Logo Image -->
    <img id="logo" src="Listo_SM+Post_Logo-annimation.jpg" alt="Listo Burrito Logo">

    <!-- Countdown Timer -->
    <div id="countdown"></div>

    <script>
        function startCountdown(targetTime) {
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

        // Set the target time to 24 hours from a specific time (e.g., Sept 5, 2024, 10:00 AM)
        const targetTime = new Date("Sep 3, 2024 14:21:00").getTime();
        startCountdown(targetTime);
    </script>
</body>
</html>
