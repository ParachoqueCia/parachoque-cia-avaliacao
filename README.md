<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Avaliação - Autopeças Parachoque & Cia</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #f4f4f4;
      display: flex;
      flex-direction: column;
      align-items: center;
      padding: 30px;
    }
    h1 {
      color: #222;
    }
    .stars {
      display: flex;
      gap: 10px;
      margin: 20px 0;
    }
    .star {
      font-size: 32px;
      cursor: pointer;
      color: #ccc;
    }
    .star.selected {
      color: #f5b301;
    }
    textarea {
      width: 100%;
      max-width: 400px;
      height: 100px;
      margin-top: 10px;
      resize: none;
      padding: 10px;
    }
    input[type="text"] {
      width: 100%;
      max-width: 400px;
      padding: 10px;
      margin-top: 10px;
    }
    button {
      margin-top: 20px;
      padding: 12px 24px;
      background-color: #f5b301;
      border: none;
      color: #000;
      font-weight: bold;
      cursor: pointer;
    }
    .thanks {
      display: none;
      margin-top: 20px;
      color: green;
      font-weight: bold;
    }
  </style>
</head>
<body>
  <h1>Avalie a Autopeças Parachoque & Cia</h1>

  <div class="stars">
    <span class="star" data-value="1">★</span>
    <span class="star" data-value="2">★</span>
    <span class="star" data-value="3">★</span>
    <span class="star" data-value="4">★</span>
    <span class="star" data-value="5">★</span>
  </div>

  <textarea id="comentario" placeholder="Deixe seu comentário aqui..."></textarea>
  <input type="text" id="nome" placeholder="Seu nome (opcional)"/>

  <button onclick="enviarAvaliacao()">Enviar Avaliação</button>

  <div class="thanks" id="thanks">Obrigado pela sua avaliação! 😊</div>

  <script>
    let selectedStars = 0;

    const stars = document.querySelectorAll('.star');
    stars.forEach(star => {
      star.addEventListener('click', () => {
        selectedStars = star.dataset.value;
        stars.forEach(s => {
          s.classList.toggle('selected', s.dataset.value <= selectedStars);
        });
      });
    });

    function enviarAvaliacao() {
      const comentario = document.getElementById("comentario").value;
      const nome = document.getElementById("nome").value;

      if (selectedStars == 0) {
        alert("Por favor, selecione uma quantidade de estrelas.");
        return;
      }

      // Aqui você poderá salvar os dados futuramente
      console.log({
        estrelas: selectedStars,
        comentario,
        nome
      });

      // Limpa os campos
      document.getElementById("comentario").value = "";
      document.getElementById("nome").value = "";
      stars.forEach(s => s.classList.remove('selected'));
      selectedStars = 0;

      // Mostra mensagem de agradecimento
      document.getElementById("thanks").style.display = "block";
    }
  </script>
</body>
</html>
