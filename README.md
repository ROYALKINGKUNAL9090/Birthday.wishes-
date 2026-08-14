<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Birthday Card Animation 🌙💗</title>
  <style>
    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }

    body {
      background-color: #000;
      display: flex;
      justify-content: center;
      align-items: center;
      min-height: 100vh;
      font-family: 'Poppins', 'Georgia', sans-serif;
      overflow: hidden;
    }

    /* Outer Card Stage */
    .card-container {
      width: 360px;
      height: 220px;
      perspective: 1200px;
      position: relative;
    }

    /* Flip Card */
    .card {
      width: 100%;
      height: 100%;
      position: relative;
      transform-style: preserve-3d;
      transition: transform 0.9s cubic-bezier(0.4, 0, 0.2, 1);
      border-radius: 20px;
      box-shadow: 0 15px 35px rgba(255, 105, 180, 0.2);
    }

    .card.flipped {
      transform: rotateY(180deg);
    }

    .card-face {
      position: absolute;
      width: 100%;
      height: 100%;
      backface-visibility: hidden;
      border-radius: 20px;
      overflow: hidden;
    }

    /* --- COVER FRONT --- */
    .card-front {
      background: linear-gradient(135deg, #fff0f3 0%, #ffccd5 100%);
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: space-between;
      padding: 20px;
    }

    .cover-title {
      font-size: 0.8rem;
      color: #ff4d6d;
      font-weight: 500;
      letter-spacing: 0.5px;
    }

    /* Panda Centerpiece */
    .panda-center {
      position: relative;
      display: flex;
      justify-content: center;
      align-items: center;
    }

    .panda-avatar {
      font-size: 3.5rem;
      animation: bouncePanda 2s infinite ease-in-out;
      filter: drop-shadow(0 4px 8px rgba(0,0,0,0.1));
    }

    .floating-pink-heart {
      position: absolute;
      font-size: 1.2rem;
      animation: floatHeart 2s infinite ease-in-out alternate;
    }

    .heart-left { left: -25px; top: -5px; animation-delay: 0.2s; }
    .heart-right { right: -25px; top: 10px; animation-delay: 0.7s; }

    @keyframes bouncePanda {
      0%, 100% { transform: translateY(0) scale(1); }
      50% { transform: translateY(-8px) scale(1.05); }
    }

    @keyframes floatHeart {
      0% { transform: translateY(0) scale(0.9); }
      100% { transform: translateY(-12px) scale(1.2); }
    }

    /* Pull Tab */
    .pull-tab {
      align-self: flex-start;
      display: flex;
      align-items: center;
      gap: 8px;
      cursor: pointer;
    }

    .pull-arrow {
      width: 32px;
      height: 14px;
      position: relative;
    }

    .pull-line {
      position: absolute;
      left: 0;
      top: 6px;
      width: 24px;
      height: 2px;
      background: #ff4d6d;
      transition: width 0.3s ease;
    }

    .pull-head {
      position: absolute;
      right: 4px;
      top: 3px;
      width: 8px;
      height: 8px;
      border-top: 2px solid #ff4d6d;
      border-right: 2px solid #ff4d6d;
      transform: rotate(45deg);
    }

    .pull-tab:hover .pull-line { width: 28px; }

    .pull-label {
      font-size: 0.6rem;
      letter-spacing: 1.5px;
      text-transform: uppercase;
      color: #ff4d6d;
      font-weight: 600;
    }

    /* --- INSIDE FACES --- */
    .card-back {
      transform: rotateY(180deg);
      position: relative;
    }

    /* Scene 1: Birthday Banner */
    .scene-birthday {
      position: absolute;
      inset: 0;
      background: linear-gradient(135deg, #ff4d6d 0%, #c9184a 100%);
      color: #fff;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      text-align: center;
      gap: 6px;
      transition: opacity 0.8s ease, transform 0.8s ease;
      z-index: 2;
    }

    .scene-birthday.fade-out {
      opacity: 0;
      transform: scale(0.95);
      pointer-events: none;
    }

    .birthday-heading {
      font-size: 2.2rem;
      font-family: 'Georgia', serif;
      font-weight: bold;
      line-height: 1.1;
      text-shadow: 0 2px 8px rgba(0,0,0,0.2);
    }

    .small-caption {
      font-size: 0.7rem;
      font-style: italic;
      opacity: 0.9;
    }

    /* Scene 2: Panda & Hearts Blossom */
    .scene-tree {
      position: absolute;
      inset: 0;
      background: linear-gradient(to top, #ffccd5 0%, #fff0f3 100%);
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: space-between;
      padding: 15px;
      z-index: 1;
    }

    .tree-caption {
      font-size: 0.7rem;
      font-style: italic;
      color: #ff4d6d;
      font-weight: 600;
    }

    .tree-container {
      position: relative;
      width: 140px;
      height: 110px;
      display: flex;
      justify-content: center;
      align-items: flex-end;
    }

    /* Floating Heart Particles */
    .particle-heart {
      position: absolute;
      font-size: 14px;
      opacity: 0;
      animation: floatUp 2.8s infinite ease-out;
    }

    @keyframes floatUp {
      0% {
        transform: translateY(0) scale(0.6) rotate(0deg);
        opacity: 0;
      }
      30% { opacity: 1; }
      100% {
        transform: translateY(-90px) scale(1.3) rotate(25deg);
        opacity: 0;
      }
    }

    .replay-btn {
      font-size: 0.6rem;
      letter-spacing: 1px;
      text-transform: uppercase;
      background: #ff4d6d;
      border: none;
      color: #fff;
      padding: 6px 14px;
      border-radius: 12px;
      cursor: pointer;
      font-weight: bold;
    }
  </style>
</head>
<body>

  <!-- Card Container -->
  <div class="card-container">
    <div class="card" id="card">
      
      <!-- FRONT COVER -->
      <div class="card-face card-front">
        <span class="cover-title">a special wish for you 💗</span>
        
        <div class="panda-center">
          <span class="floating-pink-heart heart-left">💗</span>
          <div class="panda-avatar">🌙</div>
          <span class="floating-pink-heart heart-right">💓</span>
        </div>

        <div class="pull-tab" id="pullTab">
          <div class="pull-arrow">
            <div class="pull-line"></div>
            <div class="pull-head"></div>
          </div>
          <span class="pull-label">Pull &amp; Release</span>
        </div>
      </div>

      <!-- INSIDE CARD -->
      <div class="card-face card-back">
        
        <!-- Scene 1: Birthday Banner -->
        <div class="scene-birthday" id="sceneBirthday">
          <span class="small-caption">make a wish...</span>
          <h1 class="birthday-heading">Happy<br>Birthday</h1>
          <span class="small-caption">to someone worth celebrating 💓</span>
        </div>

        <!-- Scene 2: Panda & Hearts Blossom -->
        <div class="scene-tree" id="sceneTree">
          <span class="tree-caption">may all your wishes come true! ✨</span>
          
          <div class="tree-container" id="treeContainer">
            <div style="font-size: 3rem;">🌙🌸</div>
          </div>

          <button class="replay-btn" id="replayBtn">Close Card</button>
        </div>

      </div>

    </div>
  </div>

  <script>
    const card = document.getElementById('card');
    const pullTab = document.getElementById('pullTab');
    const sceneBirthday = document.getElementById('sceneBirthday');
    const treeContainer = document.getElementById('treeContainer');
    const replayBtn = document.getElementById('replayBtn');

    let timer = null;

    // Open Card Action
    pullTab.addEventListener('click', () => {
      card.classList.add('flipped');

      timer = setTimeout(() => {
        sceneBirthday.classList.add('fade-out');
        createHeartParticles();
      }, 2200);
    });

    // Generate Floating 💗💓 Hearts
    function createHeartParticles() {
      const hearts = ['💗', '💓', '🌸', '✨'];
      const oldParticles = treeContainer.querySelectorAll('.particle-heart');
      oldParticles.forEach(p => p.remove());

      for (let i = 0; i < 14; i++) {
        const particle = document.createElement('div');
        particle.className = 'particle-heart';
        particle.innerHTML = hearts[Math.floor(Math.random() * hearts.length)];
        
        const left = 10 + Math.random() * 80; 
        const delay = Math.random() * 2.5;
        const duration = 2 + Math.random() * 1.5;
        
        particle.style.left = `${left}%`;
        particle.style.bottom = `${30 + Math.random() * 20}%`;
        particle.style.animationDelay = `${delay}s`;
        particle.style.animationDuration = `${duration}s`;

        treeContainer.appendChild(particle);
      }
    }

    // Close Card Action
    replayBtn.addEventListener('click', () => {
      clearTimeout(timer);
      card.classList.remove('flipped');
      setTimeout(() => {
        sceneBirthday.classList.remove('fade-out');
      }, 900);
    });
  </script>

</body>
</html>
