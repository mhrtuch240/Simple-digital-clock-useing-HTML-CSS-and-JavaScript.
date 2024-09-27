<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Digital Clock with Lighting Effect and Date</title>
    <style>
        body {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background-color: #000;
            margin: 0;
            color: #fff;
            font-family: 'Arial', sans-serif;
        }
        .clock-container {
            width: 728px;
            height: 90px;
            text-align: center;
            padding: 20px;
            border: 10px solid;
            border-image: linear-gradient(to right, red, green, blue, yellow) 1;
            border-radius: 15px;
            box-shadow: 0 0 20px rgba(255, 255, 255, 0.5), 0 0 30px rgba(255, 255, 255, 0.5), 0 0 40px rgba(255, 255, 255, 0.5);
        }
        .clock {
            font-size: 2em;
            font-weight: bold;
            text-shadow: 0 0 20px rgba(255, 255, 255, 0.5), 0 0 30px rgba(255, 255, 255, 0.5), 0 0 40px rgba(255, 255, 255, 0.5);
        }
        .date {
            font-size: 1.5em;
            margin-top: 10px;
        }
    </style>
</head>
<body>
    <div class="clock-container">
        <div class="clock" id="clock"></div>
        <div class="date" id="date"></div>
        <div class="date" id="bengali-date"></div>
    </div>

    <script>
        function updateClock() {
            const now = new Date();
            const hours = String(now.getHours()).padStart(2, '0');
            const minutes = String(now.getMinutes()).padStart(2, '0');
            const seconds = String(now.getSeconds()).padStart(2, '0');
            const timeString = `${hours}:${minutes}:${seconds}`;
            document.getElementById('clock').textContent = timeString;

            const year = now.getFullYear();
            const month = String(now.getMonth() + 1).padStart(2, '0');
            const day = String(now.getDate()).padStart(2, '0');
            const dateString = `${day}-${month}-${year}`;
            document.getElementById('date').textContent = `Date: ${dateString}`;

            // Bengali Date
            const bengaliDate = new Intl.DateTimeFormat('bn-BD', { day: 'numeric', month: 'long', year: 'numeric' }).format(now);
            document.getElementById('bengali-date').textContent = `Bengali Date: ${bengaliDate}`;
        }

        setInterval(updateClock, 1000);
        updateClock();
    </script>
</body>
</html>
