# Play Audio dengan label
Tentu! Berikut adalah contoh kode HTML dan JavaScript yang telah diperbarui untuk menampilkan nama file yang sedang dimainkan:

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
    <br><br>
    <p id="currentTrack">Current Track: None</p>

    <script>
        const audioFiles = [
            'audio1.mp3',
            'audio2.mp3',
            'audio3.mp3'
        ];

        let currentIndex = 0;
        const audioPlayer = document.getElementById('audioPlayer');
        const currentTrack = document.getElementById('currentTrack');

        function updateCurrentTrack() {
            currentTrack.textContent = `Current Track: ${audioFiles[currentIndex]}`;
        }

        function playSequential() {
            audioPlayer.src = audioFiles[currentIndex];
            updateCurrentTrack();
            audioPlayer.play();
            audioPlayer.onended = () => {
                currentIndex = (currentIndex + 1) % audioFiles.length;
                playSequential();
            };
        }

        function playRandom() {
            currentIndex = Math.floor(Math.random() * audioFiles.length);
            audioPlayer.src = audioFiles[currentIndex];
            updateCurrentTrack();
            audioPlayer.play();
            audioPlayer.onended = playRandom;
        }

        function playSelected() {
            const index = document.getElementById('audioIndex').value;
            if (index >= 0 && index < audioFiles.length) {
                currentIndex = index;
                audioPlayer.src = audioFiles[currentIndex];
                updateCurrentTrack();
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
- **updateCurrentTrack()**: Fungsi baru untuk memperbarui teks yang menampilkan nama file yang sedang dimainkan.
- **currentTrack**: Elemen paragraf (`<p>`) untuk menampilkan nama file yang sedang dimainkan.

Dengan penambahan ini, nama file yang sedang dimainkan akan ditampilkan di bawah kontrol audio. Jika ada pertanyaan lebih lanjut atau butuh penyesuaian, beri tahu saya! 😊
