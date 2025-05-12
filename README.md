<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Code Barbe à Papa 🍭</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: linear-gradient(135deg, #fceabb, #f8b500);
      text-align: center;
      padding: 2em;
    }
    .container {
      background-color: #fff;
      border-radius: 15px;
      padding: 2em;
      max-width: 500px;
      margin: auto;
      box-shadow: 0 4px 12px rgba(0,0,0,0.1);
    }
    input, select, button {
      padding: 10px;
      margin: 10px 0;
      width: 100%;
      border: 1px solid #ccc;
      border-radius: 8px;
    }
    button {
      background-color: #f8b500;
      color: white;
      font-weight: bold;
      cursor: pointer;
    }
    .code-output {
      font-size: 2em;
      font-weight: bold;
      color: #d35400;
      margin-top: 1.5em;
      animation: pop 0.6s ease-out forwards;
    }
    .thank-you {
      font-size: 1.5em;
      font-weight: bold;
      margin-top: 1em;
      color: #2c3e50;
    }
    .logo {
      width: 120px;
      margin-bottom: 1em;
    }
    .video-intro {
      width: 100%;
      max-width: 500px;
      margin: 0 auto 1.5em;
      border-radius: 12px;
      box-shadow: 0 4px 12px rgba(0,0,0,0.2);
    }
    @keyframes pop {
      0% { transform: scale(0); opacity: 0; }
      80% { transform: scale(1.1); opacity: 1; }
      100% { transform: scale(1); }
    }
  </style>
</head>
<body>
  <audio id="dingSound" src="https://www.soundjay.com/button/sounds/button-16.mp3" preload="auto"></audio>

  <video class="video-intro" autoplay muted loop playsinline>
    <source src="https://www.videvo.net/videvo_files/converted/2015_08/preview/Cartoon_Burst_Party_Confetti.mp468961.webm" type="video/webm">
    Votre navigateur ne supporte pas la lecture vidéo.
  </video>

  <div class="container" id="formContainer">
    <img src="https://cdn.pixabay.com/photo/2021/07/02/20/26/cotton-candy-6382674_960_720.png" alt="Barbe à papa" class="logo">
    <h1>🎉 CODE BARBE À PAPA 🍭</h1>
    <p>Remplissez ce formulaire et cliquez sur “Obtenir mon code”<br>Un partage Facebook s’ouvrira automatiquement. Merci de le valider 🙏</p>

    <form id="barbeForm">
      <input type="text" id="nom" placeholder="Nom" required>
      <input type="text" id="prenom" placeholder="Prénom" required>
      <input type="email" id="email" placeholder="Adresse e-mail" required>
      <input type="tel" id="gsm" placeholder="Numéro de GSM" required>
      <label><input type="checkbox" required> Je m’engage à partager l’événement sur Facebook</label>
      <button type="submit">Obtenir mon code</button>
    </form>
  </div>

  <div class="container" id="codeContainer" style="display: none;">
    <div class="thank-you">Merci 🙏</div>
    <div class="code-output" id="codeOutput">Votre code arrive...</div>
    <p>Montrez ce code à la personne qui distribue les barbes à papa 🍭</p>
  </div>

  <script>
    function generateCode() {
      const digits = Math.floor(1000 + Math.random() * 9000);
      return 'CBP-' + digits;
    }

    function openFacebookShare() {
      const shareUrl = 'https://www.facebook.com/sharer/sharer.php?u=https%3A%2F%2Fwww.facebook.com%2Fjulienpaginpvdour%2Fabout&quote=Bonheur & couleurs 🌈 Une de plus offerte à la Braderie Dour Centre ! Merci à Julien P. Assurances Dour pour cette barbe à papa gratuite 🍭 #BraderieDour #JulienPAssurances';
      window.open(shareUrl, '_blank', 'width=600,height=400');
    }

    document.getElementById('barbeForm').addEventListener('submit', function(event) {
      event.preventDefault();
      const code = generateCode();
      document.getElementById('codeOutput').innerHTML = code;
      document.getElementById('formContainer').style.display = 'none';
      document.getElementById('codeContainer').style.display = 'block';
      document.getElementById('dingSound').play();
      openFacebookShare();
    });
  </script>
</body>
</html>
