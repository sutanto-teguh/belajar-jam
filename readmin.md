# BELAJAR MEMBUAT TIMER

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
