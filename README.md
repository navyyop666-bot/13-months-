# 13-months-
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no" />
  <title>13 Moons 3D Cosmic Universe ✨ | Mrs. Teena Soni ji</title>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Cinzel+Decorative:wght@700;900&family=Cormorant+Garamond:ital,wght@0,600;0,700;1,600&family=Plus+Jakarta+Sans:wght@400;500;600;700&display=swap" rel="stylesheet">
  <script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
  <style>
    :root {
      --gold: #f5d076;
      --gold-bright: #fff1b8;
      --rose: #ff6b9d;
      --glass: rgba(8, 13, 36, 0.78);
      --border: rgba(245, 208, 118, 0.38);
    }

    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
      -webkit-tap-highlight-color: transparent;
    }

    html, body {
      width: 100%;
      height: 100%;
      overflow: hidden;
      background: #02040d;
      font-family: 'Plus Jakarta Sans', sans-serif;
      color: #f8fafc;
      user-select: none;
    }

    #webgl-canvas {
      position: fixed;
      inset: 0;
      width: 100%;
      height: 100%;
      z-index: 1;
      display: block;
    }

    .serif-royal {
      font-family: 'Cinzel Decorative', serif;
    }

    .script-romantic {
      font-family: 'Cormorant Garamond', serif;
    }

    /* Opening Cinematic Curtain */
    #intro-curtain {
      position: fixed;
      inset: 0;
      z-index: 100;
      background: radial-gradient(circle at center, #141f54 0%, #030614 85%);
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      text-align: center;
      padding: 24px;
      transition: opacity 1s ease, transform 1s ease;
    }

    #intro-curtain.hidden {
      opacity: 0;
      pointer-events: none;
      transform: scale(1.08);
    }

    .moon-crest {
      width: 110px;
      height: 110px;
      border-radius: 50%;
      box-shadow: -22px 14px 0 0 var(--gold), 0 0 60px rgba(245, 208, 118, 0.6);
      margin-bottom: 26px;
      animation: floatCrescent 3.8s ease-in-out infinite;
    }

    @keyframes floatCrescent {
      0%, 100% { transform: translateY(0) rotate(-8deg); }
      50% { transform: translateY(-12px) rotate(0deg); }
    }

    .milestone-row {
      display: flex;
      gap: 12px;
      flex-wrap: wrap;
      justify-content: center;
      margin: 18px 0 28px;
    }

    .pill-stat {
      background: rgba(255, 255, 255, 0.06);
      border: 1px solid var(--border);
      border-radius: 16px;
      padding: 10px 16px;
      backdrop-filter: blur(10px);
    }

    .pill-stat strong {
      display: block;
      color: var(--gold-bright);
      font-size: 1.15rem;
    }

    .pill-stat span {
      font-size: 0.72rem;
      color: #cbd5e1;
    }

    .btn-gold {
      background: linear-gradient(135deg, #ffe599 0%, #e5a93c 100%);
      color: #090d22;
      border: none;
      padding: 14px 30px;
      border-radius: 999px;
      font-weight: 800;
      font-size: 0.96rem;
      cursor: pointer;
      box-shadow: 0 0 32px rgba(245, 208, 118, 0.55);
      transition: transform 0.25s ease, box-shadow 0.25s ease;
    }

    .btn-gold:hover {
      transform: translateY(-2px) scale(1.04);
      box-shadow: 0 0 44px rgba(245, 208, 118, 0.85);
    }

    /* Top HUD */
    .top-hud {
      position: fixed;
      top: 0;
      left: 0;
      right: 0;
      z-index: 20;
      padding: 14px 18px;
      display: flex;
      justify-content: space-between;
      align-items: center;
      flex-wrap: wrap;
      gap: 10px;
      pointer-events: none;
    }

    .top-hud > * {
      pointer-events: auto;
    }

    .title-chip {
      background: var(--glass);
      border: 1px solid var(--border);
      border-radius: 999px;
      padding: 8px 16px;
      backdrop-filter: blur(12px);
      font-size: 0.84rem;
      font-weight: 700;
      color: var(--gold-bright);
      box-shadow: 0 8px 24px rgba(0, 0, 0, 0.4);
    }

    .hud-group {
      display: flex;
      gap: 8px;
      flex-wrap: wrap;
    }

    .btn-hud {
      background: var(--glass);
      color: #f8fafc;
      border: 1px solid var(--border);
      border-radius: 999px;
      padding: 8px 14px;
      font-size: 0.8rem;
      font-weight: 600;
      cursor: pointer;
      backdrop-filter: blur(12px);
      transition: all 0.2s ease;
    }

    .btn-hud:hover, .btn-hud.active {
      background: rgba(245, 208, 118, 0.24);
      border-color: var(--gold-bright);
      color: var(--gold-bright);
    }

    /* Story Tour Caption Overlay */
    #story-caption {
      position: fixed;
      top: 72px;
      left: 50%;
      transform: translateX(-50%);
      z-index: 22;
      width: min(92vw, 540px);
      background: rgba(7, 11, 30, 0.84);
      border: 1px solid var(--gold);
      border-radius: 18px;
      padding: 14px 20px;
      text-align: center;
      backdrop-filter: blur(14px);
      box-shadow: 0 12px 35px rgba(0, 0, 0, 0.6);
      display: none;
    }

    #story-caption.visible {
      display: block;
      animation: popUp 0.45s ease;
    }

    @keyframes popUp {
      from { opacity: 0; transform: translate(-50%, -10px); }
      to { opacity: 1; transform: translate(-50%, 0); }
    }

    /* Bottom Controls & Moon Selector */
    .bottom-hud {
      position: fixed;
      bottom: 0;
      left: 0;
      right: 0;
      z-index: 20;
      padding: 12px 14px 18px;
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 10px;
      pointer-events: none;
      background: linear-gradient(to top, rgba(2, 4, 13, 0.88) 0%, transparent 100%);
    }

    .bottom-hud > * {
      pointer-events: auto;
    }

    .moon-strip {
      display: flex;
      gap: 6px;
      overflow-x: auto;
      max-width: 96vw;
      padding: 4px 6px;
      scrollbar-width: none;
    }

    .moon-strip::-webkit-scrollbar {
      display: none;
    }

    .moon-pill {
      background: rgba(13, 21, 52, 0.82);
      border: 1px solid var(--border);
      color: var(--gold-bright);
      border-radius: 999px;
      padding: 6px 12px;
      font-size: 0.76rem;
      font-weight: 700;
      cursor: pointer;
      white-space: nowrap;
      transition: all 0.2s ease;
    }

    .moon-pill:hover, .moon-pill.active {
      background: var(--gold);
      color: #080c20;
      transform: translateY(-2px);
    }

    .action-dock {
      display: flex;
      gap: 8px;
      flex-wrap: wrap;
      justify-content: center;
    }

    /* Modals */
    .overlay-modal {
      position: fixed;
      inset: 0;
      z-index: 60;
      background: rgba(2, 4, 14, 0.82);
      backdrop-filter: blur(12px);
      display: none;
      align-items: center;
      justify-content: center;
      padding: 18px;
    }

    .overlay-modal.open {
      display: flex;
    }

    /* 3D Flip Polaroid Card */
    .card-stage {
      width: min(92vw, 390px);
      height: 500px;
      perspective: 1200px;
    }

    .flip-inner {
      width: 100%;
      height: 100%;
      position: relative;
      transform-style: preserve-3d;
      transition: transform 0.75s cubic-bezier(0.22, 1, 0.36, 1);
      cursor: pointer;
    }

    .flip-inner.flipped {
      transform: rotateY(180deg);
    }

    .card-side {
      position: absolute;
      inset: 0;
      backface-visibility: hidden;
      border-radius: 24px;
      background: linear-gradient(160deg, #131e4d 0%, #080d24 100%);
      border: 1.5px solid var(--gold);
      box-shadow: 0 24px 65px rgba(0, 0, 0, 0.75);
      padding: 16px;
      display: flex;
      flex-direction: column;
      justify-content: space-between;
    }

    .card-back-side {
      transform: rotateY(180deg);
      background: radial-gradient(circle at top right, #1f2e6e 0%, #080d24 85%);
      text-align: center;
      justify-content: center;
      padding: 28px;
    }

    .photo-box {
      width: 100%;
      height: 345px;
      border-radius: 16px;
      overflow: hidden;
      background: #040714;
      border: 1px solid rgba(255, 255, 255, 0.15);
      display: flex;
      align-items: center;
      justify-content: center;
    }

    .photo-box img {
      width: 100%;
      height: 100%;
      object-fit: cover;
    }

    /* Royal Panel (Letter & Quiz) */
    .royal-card {
      background: linear-gradient(160deg, #101942 0%, #070b20 100%);
      border: 1.5px solid var(--gold);
      border-radius: 24px;
      width: min(94vw, 480px);
      max-height: 86vh;
      overflow-y: auto;
      padding: 24px;
      text-align: center;
      box-shadow: 0 24px 65px rgba(0, 0, 0, 0.75);
    }

    .wax-seal-btn {
      width: 68px;
      height: 68px;
      border-radius: 50%;
      background: radial-gradient(circle at 30% 30%, #fb7185, #9f1239);
      color: #fff;
      font-size: 1.6rem;
      display: flex;
      align-items: center;
      justify-content: center;
      margin: 14px auto;
      cursor: pointer;
      box-shadow: 0 0 28px rgba(244, 63, 94, 0.65);
      border: 2px solid #fecdd3;
      transition: transform 0.25s ease;
    }

    .wax-seal-btn:hover {
      transform: scale(1.1);
    }

    .letter-body {
      display: none;
      text-align: left;
      font-family: 'Cormorant Garamond', serif;
      font-size: 1.3rem;
      line-height: 1.65;
      color: #fef3c7;
      margin-top: 14px;
      padding-top: 14px;
      border-top: 1px solid rgba(245, 208, 118, 0.3);
    }

    .letter-body.open {
      display: block;
    }

    .scratch-box {
      position: relative;
      width: 100%;
      height: 112px;
      border-radius: 16px;
      overflow: hidden;
      margin-top: 16px;
      border: 1.5px solid var(--gold);
      background: linear-gradient(135deg, #fffbeb 0%, #fde68a 100%);
      color: #1e1b4b;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      padding: 10px;
    }

    #vip-scratch {
      position: absolute;
      inset: 0;
      width: 100%;
      height: 100%;
      cursor: crosshair;
      touch-action: none;
    }
  </style>
</head>
<body>
  <canvas id="webgl-canvas"></canvas>

  <!-- Cinematic Intro Curtain -->
  <div id="intro-curtain">
    <div class="moon-crest"></div>
    <p style="letter-spacing: 0.2em; text-transform: uppercase; font-size: 0.76rem; color: var(--gold);">3D Celestial Milestone Edition</p>
    <h1 class="serif-royal" style="font-size: clamp(1.7rem, 5vw, 2.9rem); color: #fffbeb; margin: 10px 0;">
      13 Moons With You,<br>Mrs. Teena Soni ji
    </h1>
    <p style="max-width: 480px; color: #cbd5e1; font-size: 0.94rem;">
      Aapke liye banaya gaya ek poora 3D universe—jahan har chaand aur sitara hamare 13 mahinon ki mohabbat ki kahani sunata hai.
    </p>
    <div class="milestone-row">
      <div class="pill-stat"><strong>13</strong><span>3D Moons</span></div>
      <div class="pill-stat"><strong>395</strong><span>Starry Nights</span></div>
      <div class="pill-stat"><strong>∞</strong><span>Forever Love</span></div>
    </div>
    <button class="btn-gold" id="enter-3d-btn">Enter Our 3D Universe ✨</button>
  </div>

  <!-- Top HUD -->
  <div class="top-hud">
    <div class="title-chip">🌙 Teena ❤️ Navu • 13th Month 3D Universe</div>
    <div class="hud-group">
      <button class="btn-hud" id="tour-btn">🎬 Auto Story Tour</button>
      <button class="btn-hud" id="piano-btn">🎵 Cosmic Piano: Off</button>
      <button class="btn-hud" id="fireworks-btn">🎆 Fireworks</button>
    </div>
  </div>

  <!-- Auto-Tour Story Caption -->
  <div id="story-caption">
    <strong id="caption-title" style="color: var(--gold-bright); font-size: 0.95rem;">Moon 1</strong>
    <p id="caption-text" class="script-romantic" style="font-size: 1.2rem; color: #fffbeb; margin-top: 4px;"></p>
  </div>

  <!-- Bottom HUD -->
  <div class="bottom-hud">
    <div class="moon-strip" id="moon-strip"></div>
    <div class="action-dock">
      <button class="btn-hud" id="open-letter-btn">💌 3D Love Letter</button>
      <button class="btn-hud" id="open-quiz-btn">✨ Star Quiz &amp; VIP Pass</button>
      <button class="btn-hud" id="download-btn">⬇️ Download 3D HTML</button>
    </div>
    <span style="font-size: 0.72rem; color: #94a3b8;">👆 Drag 360° to rotate • Tap any 3D photo frame to open</span>
  </div>

  <!-- 3D Flip Photo Modal -->
  <div class="overlay-modal" id="photo-modal">
    <div style="display:flex; flex-direction:column; align-items:center; gap:12px;">
      <div class="card-stage">
        <div class="flip-inner" id="flip-inner">
          <div class="card-side">
            <div class="photo-box" id="modal-photo-box"></div>
            <div>
              <h3 id="card-heading" style="color: var(--gold-bright); font-size: 1.12rem;">Moon 1</h3>
              <p style="font-size: 0.8rem; color: #cbd5e1;">👆 Card par tap karke peeche ka love note padhein</p>
            </div>
          </div>
          <div class="card-side card-back-side">
            <span style="color: var(--gold); font-size: 0.82rem; letter-spacing: 0.14em;">✨ 13 MOONS MEMORY ✨</span>
            <p id="card-shayari" class="script-romantic" style="font-size: 1.48rem; line-height: 1.55; color: #fffbeb; margin: 18px 0;"></p>
            <span style="font-size: 0.78rem; color: #94a3b8;">(Tap again to flip back)</span>
          </div>
        </div>
      </div>
      <div style="display:flex; gap:10px;">
        <button class="btn-hud" id="prev-card">⬅️ Prev</button>
        <button class="btn-gold" id="close-photo-modal" style="padding: 8px 22px;">Close ✨</button>
        <button class="btn-hud" id="next-card">Next ➡️</button>
      </div>
    </div>
  </div>

  <!-- Love Letter Modal -->
  <div class="overlay-modal" id="letter-modal">
    <div class="royal-card">
      <h2 class="serif-royal" style="color: var(--gold-bright); font-size: 1.3rem;">💌 Royal 13th Month Letter</h2>
      <p style="font-size: 0.85rem; color: #cbd5e1; margin-top: 6px;">Red wax seal par tap karke apna letter kholein:</p>
      <div class="wax-seal-btn" id="break-seal-btn">❤️</div>
      <div class="letter-body" id="royal-letter-body">
        Meri pyaari <strong>Mrs. Teena Soni ji</strong>,<br><br>
        Aaj hamare saath ke <strong>13 khoobsurat mahine</strong> poore ho gaye hain. Is poore 3D universe ke sabhi sitare bhi aapki muskurahat ke saamne pheeke hain. Chahe dooriyan kitni bhi hon, aap har raat ke chaand ki tarah mere dil mein roshni bankar rehti hain.<br><br>
        Happy 13th Month Anniversary meri jaan! Hamesha mere saath rehna. ❤️🌙<br><br>
        — Aapka <strong>Navu</strong>
      </div>
      <button class="btn-hud" id="close-letter-modal" style="margin-top: 16px;">Close</button>
    </div>
  </div>

  <!-- Star Quiz & VIP Scratch Pass Modal -->
  <div class="overlay-modal" id="quiz-modal">
    <div class="royal-card">
      <h2 class="serif-royal" style="color: var(--gold-bright); font-size: 1.25rem;">✨ Written in the Stars</h2>
      <p style="font-size: 0.9rem; color: #e2e8f0; margin-top: 8px;">
        Kya aap is poore universe mein sabse zyada pyaar apne pati se karti hain?
      </p>
      <div style="display:flex; gap:12px; justify-content:center; margin-top:16px; position:relative; min-height:48px; align-items:center;">
        <button class="btn-gold" id="quiz-yes" style="padding: 10px 22px;">Haan, Sabse Zyada! ❤️</button>
        <button class="btn-hud" id="quiz-no">Nahi 😜</button>
      </div>
      <p id="quiz-msg" style="color: var(--gold-bright); font-weight: 700; font-size: 0.9rem; margin-top: 12px;"></p>

      <div class="scratch-box">
        <strong style="font-size: 0.98rem;">🎟️ 13TH MONTH VIP DATE PASS</strong>
        <span style="font-size: 0.78rem; margin-top: 4px;">Unlimited Ice Cream, Long Drive &amp; Tight Hugs ❤️</span>
        <canvas id="vip-scratch"></canvas>
      </div>
      <p style="font-size: 0.74rem; color: #94a3b8; margin-top: 6px;">👆 Golden card scratch karein!</p>
      <button class="btn-hud" id="close-quiz-modal" style="margin-top: 14px;">Close</button>
    </div>
  </div>

  <script>
    // All 13 ImgBB Photos Permanently Embedded
    const MEMORIES = [
      { title: "Moon 1 • Pehli Jhalak", img: "https://ibb.co/tw6v53pk", note: "Month 1: Hamari khoobsurat shuruat, jab pehli baar laga ki meri duniya poori ho gayi. ❤️" },
      { title: "Moon 2 • Pyaari Baatein", img: "https://ibb.co/99V3H4K5", note: "Month 2: Har roz aapki baatein aur aapki pyaari si hansi meri aadat banti gayi. ✨" },
      { title: "Moon 3 • Chaand Si Khoobsurti", img: "https://ibb.co/4RDmyf8R", note: "Month 3: Chaand bhi sharma jaaye itni khoobsurat hain aap, Mrs. Teena Soni ji. 🌙" },
      { title: "Moon 4 • Haseen Pal", img: "https://ibb.co/TBbTS4HW", note: "Month 4: Saath bitaya har ek pal mere dil ke sabse kareeb hai. 💖" },
      { title: "Moon 5 • Khushiyon Ka Tyohar", img: "https://ibb.co/4g3tB1qY", note: "Month 5: Aapke saath har din ek naya tyohar jaisa lagta hai. 🌟" },
      { title: "Moon 6 • Aadha Saal", img: "https://ibb.co/7xjPKX3H", note: "Month 6: Aadha saal poora hua, aur mera pyaar aapke liye aur gehra hota gaya. 💫" },
      { title: "Moon 7 • Har Dhadkan Mein Aap", img: "https://ibb.co/273WBLqV", note: "Month 7: Dooriyon ke baawajood aap har dhadkan mein mere paas hain. ❤️" },
      { title: "Moon 8 • Meri Har Dua", img: "https://ibb.co/R4QsnKZC", note: "Month 8: Meri har khushi aur har dua mein sirf aapka naam hai. 🌹" },
      { title: "Moon 9 • Sitaaron Si Chamak", img: "https://ibb.co/pBBHzgNp", note: "Month 9: Aapki aankhon ki chamak mere liye kisi bhi sitare se badhkar hai. ✨" },
      { title: "Moon 10 • Das Mahinon Ka Safar", img: "https://ibb.co/F4qtHTq8", note: "Month 10: Das mahine ka yeh safar aapke bina adhoora hota, meri jaan. 💞" },
      { title: "Moon 11 • Hamesha Saath", img: "https://ibb.co/KjvFtScP", note: "Month 11: Har mushkil aasan lagti hai jab aapka haath mere haath mein hota hai. 🌙" },
      { title: "Moon 12 • Ek Poora Saal", img: "https://ibb.co/WW60WtFb", note: "Month 12: Ek poora saal aapke sang—meri zindagi ka sabse haseen saal! 🎉❤️" },
      { title: "Moon 13 • Forever & Always", img: "https://ibb.co/0pqMT42q", note: "Month 13: Happy 13th Month Anniversary Mrs. Teena Soni ji! Abhi poori zindagi baaki hai. 💍✨" }
    ];

    // Helper: Resolve ImgBB viewer URL to direct image with multi-extension fallback
    function getImgCandidates(url) {
      const m = url.match(/^https?:\/\/ibb\.co\/([a-zA-Z0-9]+)\/?$/);
      if (!m) return [url];
      const id = m[1];
      return [
        `https://i.ibb.co/${id}/image.jpg`,
        `https://i.ibb.co/${id}/image.png`,
        `https://i.ibb.co/${id}/image.jpeg`,
        `https://i.ibb.co/${id}/image.webp`
      ];
    }

    // ================= THREE.JS 3D UNIVERSE =================
    const canvas = document.getElementById("webgl-canvas");
    const scene = new THREE.Scene();
    scene.fog = new THREE.FogExp2(0x02040d, 0.014);

    const camera = new THREE.PerspectiveCamera(58, window.innerWidth / window.innerHeight, 0.1, 250);
    camera.position.set(0, 4.5, 22);

    const renderer = new THREE.WebGLRenderer({ canvas, antialias: true, alpha: false });
    renderer.setSize(window.innerWidth, window.innerHeight);
    renderer.setPixelRatio(Math.min(window.devicePixelRatio, 2));

    // Lights
    const ambientLight = new THREE.AmbientLight(0xdbeafe, 0.85);
    scene.add(ambientLight);

    const moonLight = new THREE.PointLight(0xffe599, 2.4, 70);
    moonLight.position.set(0, 2, 0);
    scene.add(moonLight);

    const rimLight = new THREE.DirectionalLight(0xff7eb3, 0.9);
    rimLight.position.set(12, 15, 10);
    scene.add(rimLight);

    // Procedural Cratered 3D Full Moon Texture
    function createMoonTexture() {
      const c = document.createElement("canvas");
      c.width = 512; c.height = 256;
      const ctx = c.getContext("2d");
      const grad = ctx.createLinearGradient(0, 0, 512, 256);
      grad.addColorStop(0, "#fffbeb");
      grad.addColorStop(0.5, "#f5d076");
      grad.addColorStop(1, "#d99b26");
      ctx.fillStyle = grad;
      ctx.fillRect(0, 0, 512, 256);

      for (let i = 0; i < 65; i++) {
        const x = Math.random() * 512;
        const y = Math.random() * 256;
        const r = Math.random() * 16 + 3;
        ctx.beginPath();
        ctx.arc(x, y, r, 0, Math.PI * 2);
        ctx.fillStyle = `rgba(146, 94, 20, ${Math.random() * 0.18 + 0.05})`;
        ctx.fill();
      }
      return new THREE.CanvasTexture(c);
    }

    // Central 3D Moon + Double Golden Orbital Rings
    const moonMesh = new THREE.Mesh(
      new THREE.SphereGeometry(2.7, 48, 48),
      new THREE.MeshStandardMaterial({
        map: createMoonTexture(),
        emissive: 0xf5d076,
        emissiveIntensity: 0.28,
        roughness: 0.65
      })
    );
    scene.add(moonMesh);

    const ring1 = new THREE.Mesh(
      new THREE.TorusGeometry(4.3, 0.045, 16, 120),
      new THREE.MeshBasicMaterial({ color: 0xf5d076, transparent: true, opacity: 0.65 })
    );
    ring1.rotation.x = Math.PI / 2.4;
    ring1.rotation.y = 0.25;
    scene.add(ring1);

    const ring2 = new THREE.Mesh(
      new THREE.TorusGeometry(5.1, 0.03, 16, 120),
      new THREE.MeshBasicMaterial({ color: 0xff85b3, transparent: true, opacity: 0.45 })
    );
    ring2.rotation.x = Math.PI / 1.9;
    ring2.rotation.y = -0.35;
    scene.add(ring2);

    // 3D Starfield Galaxy
    const starGeo = new THREE.BufferGeometry();
    const starCount = 2400;
    const starPos = new Float32Array(starCount * 3);
    for (let i = 0; i < starCount * 3; i++) {
      starPos[i] = (Math.random() - 0.5) * 160;
    }
    starGeo.setAttribute("position", new THREE.BufferAttribute(starPos, 3));
    const starField = new THREE.Points(
      starGeo,
      new THREE.PointsMaterial({ color: 0xfff8dc, size: 0.28, transparent: true, opacity: 0.9 })
    );
    scene.add(starField);

    // 3D Floating Crystal Hearts
    const heartShape = new THREE.Shape();
    heartShape.moveTo(0, 0.35);
    heartShape.bezierCurveTo(0, 0.35, -0.45, 0.75, -0.85, 0.35);
    heartShape.bezierCurveTo(-1.25, -0.05, -0.75, -0.65, 0, -1.1);
    heartShape.bezierCurveTo(0.75, -0.65, 1.25, -0.05, 0.85, 0.35);
    heartShape.bezierCurveTo(0.45, 0.75, 0, 0.35, 0, 0.35);

    const heartGeo = new THREE.ExtrudeGeometry(heartShape, { depth: 0.18, bevelEnabled: true, bevelSize: 0.06, bevelThickness: 0.06 });
    const hearts = [];
    for (let i = 0; i < 16; i++) {
      const h = new THREE.Mesh(
        heartGeo,
        new THREE.MeshStandardMaterial({ color: i % 2 === 0 ? 0xff5e94 : 0xf5d076, emissive: 0x6b1434, roughness: 0.3 })
      );
      const ang = (i / 16) * Math.PI * 2;
      const rad = 6.5 + Math.random() * 8;
      h.position.set(Math.cos(ang) * rad, (Math.random() - 0.5) * 9, Math.sin(ang) * rad);
      h.scale.setScalar(0.35);
      scene.add(h);
      hearts.push({ mesh: h, baseY: h.position.y, phase: Math.random() * Math.PI * 2 });
    }

    // 13 Orbiting 3D Golden Photo Frames
    const galleryGroup = new THREE.Group();
    scene.add(galleryGroup);

    const frameMeshes = [];
    const orbitRadius = 11.2;

    function createFallbackCardTexture(label) {
      const c = document.createElement("canvas");
      c.width = 256; c.height = 320;
      const ctx = c.getContext("2d");
      const g = ctx.createLinearGradient(0, 0, 256, 320);
      g.addColorStop(0, "#17255a");
      g.addColorStop(1, "#090d24");
      ctx.fillStyle = g;
      ctx.fillRect(0, 0, 256, 320);
      ctx.fillStyle = "#f5d076";
      ctx.font = "bold 26px sans-serif";
      ctx.textAlign = "center";
      ctx.fillText("🌙 " + label, 128, 150);
      ctx.font = "16px sans-serif";
      ctx.fillStyle = "#e2e8f0";
      ctx.fillText("Mrs. Teena Soni ji", 128, 185);
      return new THREE.CanvasTexture(c);
    }

    function loadTextureWithFallback(mesh, urls, fallbackLabel) {
      const loader = new THREE.TextureLoader();
      loader.setCrossOrigin("anonymous");
      let idx = 0;
      function tryNext() {
        if (idx >= urls.length) {
          mesh.material.map = createFallbackCardTexture(fallbackLabel);
          mesh.material.needsUpdate = true;
          return;
        }
        loader.load(
          urls[idx],
          tex => {
            mesh.material.map = tex;
            mesh.material.needsUpdate = true;
          },
          undefined,
          () => {
            idx++;
            tryNext();
          }
        );
      }
      tryNext();
    }

    MEMORIES.forEach((mem, i) => {
      const angle = (i / MEMORIES.length) * Math.PI * 2;
      const holder = new THREE.Group();
      holder.position.set(
        Math.cos(angle) * orbitRadius,
        Math.sin(i * 0.9) * 1.35,
        Math.sin(angle) * orbitRadius
      );
      holder.lookAt(0, 0, 0);
      holder.rotateY(Math.PI);

      // Gold backing border
      const borderMesh = new THREE.Mesh(
        new THREE.BoxGeometry(2.55, 3.25, 0.12),
        new THREE.MeshStandardMaterial({ color: 0xf5d076, metalness: 0.65, roughness: 0.25 })
      );
      holder.add(borderMesh);

      // Photo plane
      const photoMesh = new THREE.Mesh(
        new THREE.PlaneGeometry(2.3, 3.0),
        new THREE.MeshBasicMaterial({ map: createFallbackCardTexture(`Moon ${i + 1}`) })
      );
      photoMesh.position.z = 0.07;
      photoMesh.userData = { index: i };
      holder.add(photoMesh);

      loadTextureWithFallback(photoMesh, getImgCandidates(mem.img), `Moon ${i + 1}`);

      galleryGroup.add(holder);
      frameMeshes.push(photoMesh);
    });

    // Shooting Stars & 3D Fireworks System
    const bursts = [];
    function spawnFirework(x = (Math.random() - 0.5) * 14, y = 4 + Math.random() * 5, z = (Math.random() - 0.5) * 10) {
      const count = 90;
      const geo = new THREE.BufferGeometry();
      const positions = new Float32Array(count * 3);
      const velocities = [];
      for (let i = 0; i < count; i++) {
        positions[i * 3] = x;
        positions[i * 3 + 1] = y;
        positions[i * 3 + 2] = z;
        const theta = Math.random() * Math.PI * 2;
        const phi = Math.acos(2 * Math.random() - 1);
        const speed = 0.08 + Math.random() * 0.16;
        velocities.push({
          x: Math.sin(phi) * Math.cos(theta) * speed,
          y: Math.cos(phi) * speed,
          z: Math.sin(phi) * Math.sin(theta) * speed
        });
      }
      geo.setAttribute("position", new THREE.BufferAttribute(positions, 3));
      const mat = new THREE.PointsMaterial({
        color: Math.random() > 0.5 ? 0xf5d076 : 0xff6b9d,
        size: 0.35,
        transparent: true,
        opacity: 1
      });
      const pts = new THREE.Points(geo, mat);
      scene.add(pts);
      bursts.push({ pts, velocities, life: 1.0 });
    }

    // Orbit Drag & Raycaster Tap Detection
    let isDragging = false, prevX = 0, prevY = 0, downX = 0, downY = 0;
    let targetRotY = 0, targetCamY = 4.5, targetCamZ = 22;
    let tourActive = false, tourIndex = 0, tourTimer = null;

    const raycaster = new THREE.Raycaster();
    const pointer = new THREE.Vector2();

    function onPointerDown(e) {
      isDragging = true;
      const clientX = e.touches ? e.touches[0].clientX : e.clientX;
      const clientY = e.touches ? e.touches[0].clientY : e.clientY;
      prevX = downX = clientX;
      prevY = downY = clientY;
    }

    function onPointerMove(e) {
      if (!isDragging) return;
      const clientX = e.touches ? e.touches[0].clientX : e.clientX;
      const clientY = e.touches ? e.touches[0].clientY : e.clientY;
      const dx = clientX - prevX;
      const dy = clientY - prevY;
      targetRotY += dx * 0.0065;
      targetCamY = Math.max(-4, Math.min(11, targetCamY + dy * 0.03));
      prevX = clientX;
      prevY = clientY;
    }

    function onPointerUp(e) {
      isDragging = false;
      const clientX = e.changedTouches ? e.changedTouches[0].clientX : e.clientX;
      const clientY = e.changedTouches ? e.changedTouches[0].clientY : e.clientY;
      if (Math.hypot(clientX - downX, clientY - downY) < 8) {
        pointer.x = (clientX / window.innerWidth) * 2 - 1;
        pointer.y = -(clientY / window.innerHeight) * 2 + 1;
        raycaster.setFromCamera(pointer, camera);
        const hits = raycaster.intersectObjects(frameMeshes);
        if (hits.length > 0) {
          openPhotoCard(hits[0].object.userData.index);
        } else {
          spawnFirework((Math.random() - 0.5) * 12, 3 + Math.random() * 5, (Math.random() - 0.5) * 8);
        }
      }
    }

    canvas.addEventListener("mousedown", onPointerDown);
    window.addEventListener("mousemove", onPointerMove);
    window.addEventListener("mouseup", onPointerUp);
    canvas.addEventListener("touchstart", onPointerDown, { passive: true });
    canvas.addEventListener("touchmove", onPointerMove, { passive: true });
    canvas.addEventListener("touchend", onPointerUp);

    window.addEventListener("wheel", e => {
      targetCamZ = Math.max(12, Math.min(32, targetCamZ + e.deltaY * 0.01));
    }, { passive: true });

    // Animation Loop
    const clock = new THREE.Clock();
    function animate() {
      requestAnimationFrame(animate);
      const t = clock.getElapsedTime();

      moonMesh.rotation.y += 0.0035;
      ring1.rotation.z += 0.004;
      ring2.rotation.z -= 0.003;
      starField.rotation.y += 0.0005;

      if (!isDragging && !tourActive) {
        targetRotY += 0.0022;
      }
      galleryGroup.rotation.y += (targetRotY - galleryGroup.rotation.y) * 0.07;
      camera.position.y += (targetCamY - camera.position.y) * 0.06;
      camera.position.z += (targetCamZ - camera.position.z) * 0.06;
      camera.lookAt(0, 0, 0);

      hearts.forEach(h => {
        h.mesh.rotation.y += 0.015;
        h.mesh.position.y = h.baseY + Math.sin(t * 1.6 + h.phase) * 0.45;
      });

      for (let i = bursts.length - 1; i >= 0; i--) {
        const b = bursts[i];
        b.life -= 0.018;
        b.pts.material.opacity = Math.max(0, b.life);
        const arr = b.pts.geometry.attributes.position.array;
        for (let j = 0; j < b.velocities.length; j++) {
          arr[j * 3] += b.velocities[j].x;
          arr[j * 3 + 1] += b.velocities[j].y;
          arr[j * 3 + 2] += b.velocities[j].z;
          b.velocities[j].y -= 0.0025;
        }
        b.pts.geometry.attributes.position.needsUpdate = true;
        if (b.life <= 0) {
          scene.remove(b.pts);
          bursts.splice(i, 1);
        }
      }

      renderer.render(scene, camera);
    }
    animate();

    window.addEventListener("resize", () => {
      camera.aspect = window.innerWidth / window.innerHeight;
      camera.updateProjectionMatrix();
      renderer.setSize(window.innerWidth, window.innerHeight);
    });

    // ================= UI & INTERACTIONS =================
    let activeCardIndex = 0;
    const moonStrip = document.getElementById("moon-strip");
    MEMORIES.forEach((m, idx) => {
      const btn = document.createElement("button");
      btn.className = "moon-pill";
      btn.textContent = `M${idx + 1}`;
      btn.onclick = () => {
        focusMoon(idx);
        openPhotoCard(idx);
      };
      moonStrip.appendChild(btn);
    });

    function focusMoon(idx) {
      const angle = (idx / MEMORIES.length) * Math.PI * 2;
      targetRotY = -angle + Math.PI / 2;
      document.querySelectorAll(".moon-pill").forEach((p, i) => p.classList.toggle("active", i === idx));
    }

    const photoModal = document.getElementById("photo-modal");
    const flipInner = document.getElementById("flip-inner");
    const modalPhotoBox = document.getElementById("modal-photo-box");
    const cardHeading = document.getElementById("card-heading");
    const cardShayari = document.getElementById("card-shayari");

    function openPhotoCard(idx) {
      activeCardIndex = idx;
      const item = MEMORIES[idx];
      flipInner.classList.remove("flipped");
      cardHeading.textContent = `${item.title} — Mrs. Teena Soni ji`;
      cardShayari.textContent = item.note;

      modalPhotoBox.innerHTML = "";
      const img = document.createElement("img");
      const candidates = getImgCandidates(item.img);
      let attempt = 0;
      img.src = candidates[attempt];
      img.onerror = () => {
        attempt++;
        if (attempt < candidates.length) img.src = candidates[attempt];
      };
      modalPhotoBox.appendChild(img);
      photoModal.classList.add("open");
    }

    flipInner.onclick = () => flipInner.classList.toggle("flipped");
    document.getElementById("close-photo-modal").onclick = () => photoModal.classList.remove("open");
    document.getElementById("prev-card").onclick = () => openPhotoCard((activeCardIndex - 1 + MEMORIES.length) % MEMORIES.length);
    document.getElementById("next-card").onclick = () => openPhotoCard((activeCardIndex + 1) % MEMORIES.length);

    // Auto Story Tour
    const tourBtn = document.getElementById("tour-btn");
    const storyCaption = document.getElementById("story-caption");
    const captionTitle = document.getElementById("caption-title");
    const captionText = document.getElementById("caption-text");

    function runTourStep() {
      const m = MEMORIES[tourIndex];
      focusMoon(tourIndex);
      targetCamZ = 16.5;
      captionTitle.textContent = m.title;
      captionText.textContent = m.note;
      storyCaption.classList.add("visible");
      spawnFirework(0, 5, 0);
      tourIndex = (tourIndex + 1) % MEMORIES.length;
    }

    tourBtn.onclick = () => {
      tourActive = !tourActive;
      tourBtn.classList.toggle("active", tourActive);
      tourBtn.textContent = tourActive ? "⏹️ Stop Story Tour" : "🎬 Auto Story Tour";
      if (tourActive) {
        tourIndex = 0;
        runTourStep();
        tourTimer = setInterval(runTourStep, 3600);
      } else {
        clearInterval(tourTimer);
        storyCaption.classList.remove("visible");
        targetCamZ = 22;
      }
    };

    // Enter 3D Universe
    document.getElementById("enter-3d-btn").onclick = () => {
      document.getElementById("intro-curtain").classList.add("hidden");
      spawnFirework(-4, 5, 2);
      spawnFirework(4, 6, -2);
    };

    document.getElementById("fireworks-btn").onclick = () => {
      spawnFirework(-5, 5, 2);
      spawnFirework(5, 6, -1);
      spawnFirework(0, 7, 3);
    };

    // Letter & Quiz Modals
    document.getElementById("open-letter-btn").onclick = () => document.getElementById("letter-modal").classList.add("open");
    document.getElementById("close-letter-modal").onclick = () => document.getElementById("letter-modal").classList.remove("open");
    document.getElementById("break-seal-btn").onclick = () => {
      document.getElementById("royal-letter-body").classList.add("open");
      spawnFirework(0, 5, 2);
    };

    document.getElementById("open-quiz-btn").onclick = () => {
      document.getElementById("quiz-modal").classList.add("open");
      setTimeout(initScratchCard, 120);
    };
    document.getElementById("close-quiz-modal").onclick = () => document.getElementById("quiz-modal").classList.remove("open");

    const quizNo = document.getElementById("quiz-no");
    const quizYes = document.getElementById("quiz-yes");
    let yesScale = 1;
    function moveNoBtn() {
      quizNo.style.transform = `translate(${(Math.random() - 0.5) * 140}px, ${(Math.random() - 0.5) * 70}px)`;
      yesScale = Math.min(1.4, yesScale + 0.1);
      quizYes.style.transform = `scale(${yesScale})`;
    }
    quizNo.addEventListener("mouseenter", moveNoBtn);
    quizNo.addEventListener("touchstart", e => { e.preventDefault(); moveNoBtn(); });
    quizYes.onclick = () => {
      document.getElementById("quiz-msg").textContent = "I knew it! Sitaaron ne bhi yahi likha hai — Love you forever Teena ji! ❤️✨";
      quizNo.style.display = "none";
      spawnFirework(0, 5, 0);
    };

    // Golden Scratch Pass
    const vipCanvas = document.getElementById("vip-scratch");
    const vCtx = vipCanvas.getContext("2d");
    function initScratchCard() {
      const r = vipCanvas.parentElement.getBoundingClientRect();
      vipCanvas.width = r.width || 320;
      vipCanvas.height = r.height || 112;
      const g = vCtx.createLinearGradient(0, 0, vipCanvas.width, vipCanvas.height);
      g.addColorStop(0, "#d97706");
      g.addColorStop(0.5, "#f5d076");
      g.addColorStop(1, "#b45309");
      vCtx.fillStyle = g;
      vCtx.fillRect(0, 0, vipCanvas.width, vipCanvas.height);
      vCtx.fillStyle = "#1e1b4b";
      vCtx.font = "bold 14px Plus Jakarta Sans, sans-serif";
      vCtx.textAlign = "center";
      vCtx.fillText("✨ SCRATCH FOR VIP SURPRISE ✨", vipCanvas.width / 2, vipCanvas.height / 2 + 5);
    }
    let isScratching = false;
    function doScratch(x, y) {
      vCtx.globalCompositeOperation = "destination-out";
      vCtx.beginPath();
      vCtx.arc(x, y, 22, 0, Math.PI * 2);
      vCtx.fill();
    }
    vipCanvas.addEventListener("mousedown", () => isScratching = true);
    window.addEventListener("mouseup", () => isScratching = false);
    vipCanvas.addEventListener("mousemove", e => {
      if (!isScratching) return;
      const r = vipCanvas.getBoundingClientRect();
      doScratch(e.clientX - r.left, e.clientY - r.top);
    });
    vipCanvas.addEventListener("touchmove", e => {
      e.preventDefault();
      const r = vipCanvas.getBoundingClientRect();
      doScratch(e.touches[0].clientX - r.left, e.touches[0].clientY - r.top);
    }, { passive: false });

    // Ambient Cosmic Piano Synthesizer
    let audioCtx = null, pianoOn = false, pianoInterval = null;
    const pianoBtn = document.getElementById("piano-btn");
    pianoBtn.onclick = () => {
      if (!audioCtx) audioCtx = new (window.AudioContext || window.webkitAudioContext)();
      pianoOn = !pianoOn;
      pianoBtn.classList.toggle("active", pianoOn);
      pianoBtn.textContent = pianoOn ? "🎵 Cosmic Piano: On" : "🎵 Cosmic Piano: Off";
      if (pianoOn) {
        const melody = [261.63, 329.63, 392.0, 493.88, 523.25, 493.88, 392.0, 329.63];
        let step = 0;
        pianoInterval = setInterval(() => {
          const osc = audioCtx.createOscillator();
          const gain = audioCtx.createGain();
          osc.type = "sine";
          osc.frequency.value = melody[step % melody.length];
          gain.gain.setValueAtTime(0.04, audioCtx.currentTime);
          gain.gain.exponentialRampToValueAtTime(0.0001, audioCtx.currentTime + 1.1);
          osc.connect(gain);
          gain.connect(audioCtx.destination);
          osc.start();
          osc.stop(audioCtx.currentTime + 1.15);
          step++;
        }, 700);
      } else {
        clearInterval(pianoInterval);
      }
    };

    // Direct HTML File Download
    document.getElementById("download-btn").onclick = () => {
      const blob = new Blob(["<!DOCTYPE html>\n" + document.documentElement.outerHTML], { type: "text/html" });
      const a = document.createElement("a");
      a.href = URL.createObjectURL(blob);
      a.download = "index.html";
      a.click();
    };
  </script>
</body>
</html>
