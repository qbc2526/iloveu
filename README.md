<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Khusus Gahar dari Nala</title>
  <style>
    * {
      box-sizing: border-box;
    }
    body {
      background-color: #888888;
      font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
      margin: 0;
      padding: 0;
      height: 100vh;
      display: flex;
      justify-content: center;
      align-items: center;
      overflow: hidden;
    }
    .popup {
      position: relative;
      background-color: white;
      border-radius: 12px;
      box-shadow: 0 0 15px rgba(0,0,0,0.25);
      width: 90vw;
      max-width: 360px;
      max-height: 70vh;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: flex-start; /* rata kiri */
      padding: 20px;
      text-align: left; /* rata kiri */
      font-size: 16px;
      font-weight: 600;
      opacity: 0;
      transform: scale(0.95);
      transition: opacity 0.3s ease, transform 0.3s ease;
      overflow-y: auto;
    }
    .popup.show {
      opacity: 1;
      transform: scale(1);
    }
 .btn-next {
      position: absolute;
      bottom: 10px;
      right: 15px;
      font-size: 12px;
      color: #007aff;
      font-weight: normal;
      cursor: pointer;
      opacity: 0.8;
    }
 .love-animation {
      position: fixed;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%) scale(0);
      font-size: 60px;
      opacity: 0;
      transition: transform 0.6s ease, opacity 0.6s ease;
      color: white;
      z-index: 10;
    }
 .love-animation.show {
      transform: translate(-50%, -50%) scale(1);
      opacity: 1;
    }
  </style>
</head>
<body>

  <div class="popup" id="popup">
    <div id="message">haiii</div>
    <div class="btn-next" id="btnNext" onclick="nextPopup()">Lanjut</div>
  </div>

  <div class="love-animation" id="love">🩷</div>

  <audio id="bgm" autoplay loop>
    <source src="/mnt/data/Andra_And_The_Backbone_Sempurna.hd.mp3" type="audio/mpeg">
    Browser kamu nggak support audio.
  </audio>

  <script>
    const messages = [
      "haiii",
      "inii text khusus gaharr",
      "kalo bukan gahar, skip aja",
      "udh di ingetin yaa, ini khusus gahar",
      "ok",
      "haiii sayanggg",
      "udaa bangun?",
      "udaa makan?",
      "udaa mandi?",
      "udaa sayang sama aku?",
      "HAHAHA",
      "harus uda sih",
      "udaaaa kannn?",
      "xixixi",
  "sayangg",
      "makasiii yaa",
      "makasii udaa mau nerimaa nala apa adanyaa",
      "semogaaa gahar bisa bertahan di baik buruk nyaa hubungan kitaaa, yaa",
      "i lovee youu sayang",
      "i love youuu sooo sooo sooo much <3"
    ];

    let i = 0;
    const popup = document.getElementById("popup");
    const messageDiv = document.getElementById("message");
    const btnNext = document.getElementById("btnNext");
    const love = document.getElementById("love");

    function nextPopup() {
      i++;
      if (i < messages.length) {
        popup.classList.remove("show");

        setTimeout(() => {
          messageDiv.innerHTML = messages[i];
          popup.classList.add("show");

          // sembunyikan tombol di pesan terakhir
          if (i === messages.length - 1) {
            btnNext.style.display = 'none';

            // munculkan animasi love
            setTimeout(() => {
              love.classList.add("show");
            }, 500);
          }
        }, 100);
      }
    }

    window.addEventListener("load", () => {
      popup.classList.add("show");
    });

    window.addEventListener("click", () => {
      const audio = document.getElementById("bgm");
      if (audio.paused) audio.play();
    });
  </script>

</body>
</html>
