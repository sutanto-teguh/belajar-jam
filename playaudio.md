# Memainkan Audio
Tentu! Berikut adalah contoh kode HTML dan JavaScript untuk membuat pemutar audio yang dapat memainkan daftar file MP3 secara berurutan atau acak:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Audio Player</title>
</head>
<body>
    <h1>Audio Player</h1>
    <audio id="audioPlayer" controls></audio>
    <br>
    <button onclick="playSequential()">Play Sequential</button>
    <button onclick="playRandom()">Play Random</button>

    <script>
        const audioFiles = [
            'audio1.mp3',
            'audio2.mp3',
            'audio3.mp3'
        ];

        let currentIndex = 0;
        const audioPlayer = document.getElementById('audioPlayer');

        function playSequential() {
            audioPlayer.src = audioFiles[currentIndex];
            audioPlayer.play();
            audioPlayer.onended = () => {
                currentIndex = (currentIndex + 1) % audioFiles.length;
                playSequential();
            };
        }

        function playRandom() {
            currentIndex = Math.floor(Math.random() * audioFiles.length);
            audioPlayer.src = audioFiles[currentIndex];
            audioPlayer.play();
            audioPlayer.onended = playRandom;
        }
    </script>
</body>
</html>
```

Penjelasan:
- **HTML**: Membuat elemen audio dan tombol untuk memulai pemutaran berurutan atau acak.
- **JavaScript**: 
  - `audioFiles` adalah array yang berisi daftar file MP3.
  - `playSequential()` memutar file audio secara berurutan.
  - `playRandom()` memutar file audio secara acak.

Anda bisa mengganti `'audio1.mp3'`, `'audio2.mp3'`, dan `'audio3.mp3'` dengan nama file MP3 yang Anda miliki. Jika ada pertanyaan lebih lanjut atau butuh penyesuaian, beri tahu saya! 😊

# Modifikasi
Tentu! Berikut adalah contoh kode HTML dan JavaScript yang telah diperbarui untuk memungkinkan pengguna memilih dan memainkan audio berdasarkan indeks yang dipilih:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Audio Player</title>
</head>
<body>
    <h1>Audio Player</h1>
    <audio id="audioPlayer" controls></audio>
    <br>
    <button onclick="playSequential()">Play Sequential</button>
    <button onclick="playRandom()">Play Random</button>
    <br><br>
    <label for="audioIndex">Select Audio Index:</label>
    <input type="number" id="audioIndex" min="0" max="2">
    <button onclick="playSelected()">Play Selected</button>

    <script>
        const audioFiles = [
            'audio1.mp3',
            'audio2.mp3',
            'audio3.mp3'
        ];

        let currentIndex = 0;
        const audioPlayer = document.getElementById('audioPlayer');

        function playSequential() {
            audioPlayer.src = audioFiles[currentIndex];
            audioPlayer.play();
            audioPlayer.onended = () => {
                currentIndex = (currentIndex + 1) % audioFiles.length;
                playSequential();
            };
        }

        function playRandom() {
            currentIndex = Math.floor(Math.random() * audioFiles.length);
            audioPlayer.src = audioFiles[currentIndex];
            audioPlayer.play();
            audioPlayer.onended = playRandom;
        }

        function playSelected() {
            const index = document.getElementById('audioIndex').value;
            if (index >= 0 && index < audioFiles.length) {
                currentIndex = index;
                audioPlayer.src = audioFiles[currentIndex];
                audioPlayer.play();
            } else {
                alert('Invalid index. Please select a valid index.');
            }
        }
    </script>
</body>
</html>
```

Penjelasan tambahan:
- **Input Number**: Menambahkan input number untuk memilih indeks audio.
- **playSelected()**: Fungsi baru untuk memainkan audio berdasarkan indeks yang dipilih oleh pengguna.

Anda bisa mengganti `'audio1.mp3'`, `'audio2.mp3'`, dan `'audio3.mp3'` dengan nama file MP3 yang Anda miliki. Jika ada pertanyaan lebih lanjut atau butuh penyesuaian, beri tahu saya! 😊
