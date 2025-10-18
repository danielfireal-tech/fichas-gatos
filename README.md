# <!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <title>Fichas dos Gatos</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 20px;
      background-color: #f2f2f2;
      color: #333;
    }
    .gato {
      background-color: white;
      border-radius: 8px;
      padding: 15px 20px;
      margin-bottom: 20px;
      box-shadow: 0 2px 5px rgba(0,0,0,0.1);
      max-width: 400px;
    }
    h2 {
      color: #2c3e50;
      margin-top: 0;
    }
    p {
      margin: 6px 0;
    }
    .dias-vida {
      font-weight: bold;
      color: #e67e22;
    }
    img {
      width: 200px;
      border-radius: 8px;
      margin-bottom: 10px;
      display: block;
    }
  </style>
</head>
<body>
  <h1>Fichas dos Gatos</h1>

  <div class="gato" id="frajola">
    <h2>Frajola Copinho</h2>
    <img src="frajola.jpg" alt="Frajola Copinho" />
    <p><strong>Data de nascimento:</strong> 27 de agosto de 2025</p>
    <p><strong>Idade atual:</strong> <span class="dias-vida" id="dias-frajola"></span> dias de vida</p>
    <p><strong>Alimentação:</strong> Ração para filhotes (até 12 meses)</p>
    <p><strong>Observações:</strong> Gato preto com patas brancas e olhos cinzas</p>
  </div>

  <div class="gato" id="nial">
    <h2>Nial Caixinha</h2>
    <img src="nial.jpg" alt="Nial Caixinha" />
    <p><strong>Data de nascimento:</strong> 27 de agosto de 2025</p>
    <p><strong>Idade atual:</strong> <span class="dias-vida" id="dias-nial"></span> dias de vida</p>
    <p><strong>Alimentação:</strong> Ração para filhotes (até 12 meses)</p>
    <p><strong>Observações:</strong> Gato branco com manchas cinzas claras</p>
  </div>

  <script>
    function calcularDiasVida(dataNascimentoStr) {
      const dataNascimento = new Date(dataNascimentoStr + 'T00:00:00');
      const hoje = new Date();
      const diffTime = hoje - dataNascimento;
      const diffDays = Math.floor(diffTime / (1000 * 60 * 60 * 24));
      return diffDays >= 0 ? diffDays : 0;
    }

    document.getElementById('dias-frajola').textContent = calcularDiasVida('2025-08-27');
    document.getElementById('dias-nial').textContent = calcularDiasVida('2025-08-27');
  </script>
</body>
</html>
