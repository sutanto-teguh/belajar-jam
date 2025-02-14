# BELAJAR MEMBUAT TIMER

## Timer 1
Tentu! Berikut adalah contoh kode HTML, CSS, dan JavaScript untuk menampilkan countdown timer:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Countdown Timer</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background-color: #f0f0f0;
        }
        .countdown {
            text-align: center;
            background: #fff;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
        }
        .countdown h1 {
            font-size: 48px;
            margin: 0;
        }
        .countdown p {
            font-size: 24px;
            margin: 10px 0 0;
        }
    </style>
</head>
<body>
    <div class="countdown">
        <h1 id="timer">00:00:00</h1>
        <p>Time remaining</p>
    </div>

    <script>
        function startCountdown(duration) {
            let timer = duration, hours, minutes, seconds;
            setInterval(function () {
                hours = parseInt(timer / 3600, 10);
                minutes = parseInt((timer % 3600) / 60, 10);
                seconds = parseInt(timer % 60, 10);

                hours = hours < 10 ? "0" + hours : hours;
                minutes = minutes < 10 ? "0" + minutes : minutes;
                seconds = seconds < 10 ? "0" + seconds : seconds;

                document.getElementById('timer').textContent = hours + ":" + minutes + ":" + seconds;

                if (--timer < 0) {
                    timer = duration;
                }
            }, 1000);
        }

        window.onload = function () {
            let countdownTime = 60 * 60; // 1 hour in seconds
            startCountdown(countdownTime);
        };
    </script>
</body>
</html>
```

Kode ini akan menampilkan countdown timer yang menghitung mundur dari 1 jam. Anda bisa mengubah nilai `countdownTime` di bagian JavaScript untuk mengatur durasi countdown sesuai kebutuhan Anda. Selamat mencoba! 😊

## Timer 2 - tanggal spesifik
Sure! Here's an updated version of the code that counts down to a specific date:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Countdown Timer</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background-color: #f0f0f0;
        }
        .countdown {
            text-align: center;
            background: #fff;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
        }
        .countdown h1 {
            font-size: 48px;
            margin: 0;
        }
        .countdown p {
            font-size: 24px;
            margin: 10px 0 0;
        }
    </style>
</head>
<body>
    <div class="countdown">
        <h1 id="timer">00:00:00</h1>
        <p>Time remaining</p>
    </div>

    <script>
        function startCountdown(targetDate) {
            const countdownDate = new Date(targetDate).getTime();

            const interval = setInterval(function () {
                const now = new Date().getTime();
                const distance = countdownDate - now;

                const days = Math.floor(distance / (1000 * 60 * 60 * 24));
                const hours = Math.floor((distance % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
               .floor((distance % (1000 * 60 * 60)) / (1000 * 60));
                const seconds = Math.floor((distance % (1000 * 60)) / 1000);

                document.getElementById('timer').textContent = days + "d " + hours + "h " + minutes + "m " + seconds + "s ";

                if (distance < 0) {
                    clearInterval(interval);
                    document.getElementById('timer').textContent = "EXPIRED";
                }
            }, 1000);
        }

        window.onload {
            const targetDate = "2025-12-31T00:00:00"; // Set your target date here
            startCountdown(targetDate);
        };
    </script>
</body>
</html>
```

This code will count down to the specified date and time. You can change the `targetDate` variable in the JavaScript section to the date and time you want the countdown to end. Enjoy! 😊
