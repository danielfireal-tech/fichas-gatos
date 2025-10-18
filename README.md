from datetime import date, datetime

# ---------- Função para calcular dias de vida ----------
def calcular_dias_vida(data_nascimento_str):
    data_nascimento = datetime.strptime(data_nascimento_str, "%Y-%m-%d").date()
    hoje = date.today()
    dias = (hoje - data_nascimento).days
    return max(dias, 0)

# ---------- Dados dos gatos ----------
gatos = [
    {
        "nome": "Frajola Copinho",
        "nascimento": "2025-08-27",
        "alimentacao": "Ração para filhotes (até 12 meses)",
        "observacoes": "Gato preto com patas brancas e olhos cinzas",
        "imagem": "frajola.jpg"
    },
    {
        "nome": "Nial Caixinha",
        "nascimento": "2025-08-27",
        "alimentacao": "Ração para filhotes (até 12 meses)",
        "observacoes": "Gato branco com manchas cinzas claras",
        "imagem": "nial.jpg"
    }
]

# ---------- Montar HTML ----------
html_inicio = """<!DOCTYPE html>
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
"""

html_gatos = ""

for gato in gatos:
    dias = calcular_dias_vida(gato["nascimento"])
    html_gatos += f"""
  <div class="gato">
    <h2>{gato["nome"]}</h2>
    <img src="{gato["imagem"]}" alt="{gato["nome"]}" />
    <p><strong>Data de nascimento:</strong> {datetime.strptime(gato["nascimento"], "%Y-%m-%d").strftime("%d de %B de %Y")}</p>
    <p><strong>Idade atual:</strong> <span class="dias-vida">{dias}</span> dias de vida</p>
    <p><strong>Alimentação:</strong> {gato["alimentacao"]}</p>
    <p><strong>Observações:</strong> {gato["observacoes"]}</p>
  </div>
"""

html_fim = """
</body>
</html>
"""

# ---------- Salvar o arquivo ----------
with open("fichas_gatos.html", "w", encoding="utf-8") as f:
    f.write(html_inicio + html_gatos + html_fim)

print("✅ Arquivo 'fichas_gatos.html' criado com sucesso!")
