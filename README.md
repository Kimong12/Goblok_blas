
<html lang="id">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Kenangan Lucu Bareng Pacar</title>
  <style>
    body {
      margin: 0;
      font-family: 'Comic Sans MS', cursive;
      background: url('naila.jpg') center/cover no-repeat;
      overflow-x: hidden;
      transition: background 2s ease;
    }

    .gate {
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      min-height: 100vh;
      padding: 20px;
      animation: fadeIn 1s ease;
    }

    .hidden {
      display: none;
    }

    .question {
      margin: 10px 0;
      background-color: #add8e6;
      padding: 20px;
      border-radius: 50% 50% 40% 40% / 60% 60% 40% 40%;
      text-align: center;
      color: black;
      max-width: 90%;
      animation: fadeIn 1s ease;
    }

    .button {
      padding: 10px 20px;
      margin: 5px;
      border: none;
      border-radius: 8px;
      background-color: #FFFFD0;
      color: black;
      cursor: pointer;
    }

    .falling-hearts {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      pointer-events: none;
      z-index: 999;
    }

    .heart {
      position: absolute;
      width: 30px;
      height: 30px;
      background: url('https://cdn-icons-png.flaticon.com/512/833/833472.png') no-repeat center/contain;
      animation: fall 5s linear infinite;
    }

    @keyframes fall {
      0% { transform: translateY(-100px); opacity: 1; }
      100% { transform: translateY(100vh); opacity: 0; }
    }

    @keyframes fadeIn {
      from {opacity: 0; transform: translateY(20px);}
      to {opacity: 1; transform: translateY(0);}
    }

    @keyframes slideUp {
      0% {opacity: 0; transform: translateY(100px);}
      100% {opacity: 1; transform: translateY(0);}
    }

    .content {
      position: relative;
      padding: 10px;
      z-index: 1;
      min-height: 100vh;
      animation: slideUp 1s ease forwards;
      background: url('Begron2.png') center/cover no-repeat;
      color: black;
    }

    .text-box {
      background-color: #f0f8ff;
      display: inline-block;
      padding: 15px 20px;
      border-radius: 16px;
      border: 3px solid #00bfff;
      margin: 10px 0;
      animation: fadeIn 2s ease;
      box-shadow: 2px 2px 10px rgba(0,0,0,0.1);
    }

    .photo-grid {
      display: flex;
      flex-wrap: wrap;
      gap: 15px;
      justify-content: center;
      perspective: 1000px;
    }

    .photo {
      position: relative;
      width: 150px;
      transform: rotateZ(calc(-10deg + 20deg * var(--rotate))) scale(1);
      margin: 10px;
      background: white;
      padding: 5px;
      border-radius: 10px;
      box-shadow: 0 10px 20px rgba(0,0,0,0.2);
      transition: transform 0.3s ease;
      z-index: calc(1 + var(--rotate));
    }

    .photo:hover {
      transform: scale(1.05) rotateZ(0deg);
      z-index: 10;
    }

    .photo img {
      width: 100%;
      border-radius: 8px;
    }

    .caption {
      font-size: 12px;
      text-align: center;
      margin-top: 4px;
    }

    .wa-button {
      display: inline-block;
      padding: 12px 20px;
      background-color: #25D366;
      color: white;
      border: none;
      border-radius: 10px;
      text-decoration: none;
      font-weight: bold;
      margin-top: 30px;
    }

  </style>
</head>
<body>
  <div class="gate" id="gate">
    <div class="question">
      <p>1. Apakah sudah mendapatkan izin dari orangnya?</p>
      <button class="button" onclick="checkGate(1, true)">Ya</button>
      <button class="button" onclick="checkGate(1, false)">Tidak</button>
    </div>
    <div class="question hidden">
      <p>2. Apakah kamu mantan pacar si cowo?</p>
      <button class="button" onclick="checkGate(2, true)">Ya</button>
      <button class="button" onclick="checkGate(2, false)">Tidak</button>
    </div>
    <div class="question hidden">
      <p>3. Kepo banget ya?</p>
      <button class="button" onclick="checkGate(3, true)">Iya banget</button>
      <button class="button" onclick="checkGate(3, false)">Biasa aja</button>
    </div>
  </div>

  <div class="falling-hearts" id="hearts"></div>

  <div class="content hidden" id="content">
    <h2 class="text-box">Hai semuanya kalian kenapa si kepo bngt!!!</h2>
    <p class="text-box">Tanggal Jadian: 29 September 2023</p>
    <p class="text-box">Tanggal Nikah (Aamiin!): 29 september 2032</p>

    <div class="photo-grid">
      <div class="photo" style="--rotate: 0.2;">
        <img src="man1.jpg" alt="foto1" />
        <div class="caption">12 Jan 2023 - Taman Kota</div>
      </div>
      <div class="photo" style="--rotate: -0.2;">
        <img src="man2.jpg" alt="foto2" />
        <div class="caption">20 Feb 2023 - Nonton Bareng</div>
      </div>
      <div class="photo" style="--rotate: 0;">
        <img src="man3.jpg" />
        <div class="caption">5 Mar 2023 - Makan Es Krim</div>
      </div>
    </div>

    <div style="text-align: center;">
      <a href="https://wa.me/6283877486039?text=Wah%20semoga%20langgeng%20yaaa" target="_blank" class="wa-button">
        Kirim Ucapan via WhatsApp
      </a>
    </div>
  </div>

  <script>
    let currentStep = 0;
    function checkGate(step, answer) {
      const questions = document.querySelectorAll('.question');
      if (!answer) {
        alert("Maaf, kamu tidak bisa mengakses halaman ini.");
        return;
      }
      questions[currentStep].classList.add('hidden');
      currentStep++;
      if (currentStep < questions.length) {
        setTimeout(() => {
          questions[currentStep].classList.remove('hidden');
        }, 700);
      } else {
        document.getElementById('gate').classList.add('hidden');
        document.getElementById('content').classList.remove('hidden');
        createHearts();
      }
    }

    function createHearts() {
      const heartsContainer = document.getElementById('hearts');
      for (let i = 0; i < 30; i++) {
        const heart = document.createElement('div');
        heart.className = 'heart';
        heart.style.left = Math.random() * 100 + 'vw';
        heart.style.animationDuration = (Math.random() * 3 + 3) + 's';
        heart.style.filter = `hue-rotate(${Math.random() * 360}deg)`;
        heartsContainer.appendChild(heart);
      }
    }
  </script>
</body>
</html>
