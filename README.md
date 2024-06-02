<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Calculadora de Juros</title>
    <style>
        .content { display: none; }
        .active { display: block; }
        table, th, td { border: 1px solid black; border-collapse: collapse; }
        th, td { padding: 8px; text-align: left; }
        table { width: 100%; margin-top: 20px; }
    </style>
</head>
<body>
    <div class="container">
        <button onclick="showCalculator()">Calculadora</button>
        <button onclick="showStudy()">Área de Estudo</button>
        <button onclick="showAvalie()">Avalie</button>
    </div>

    <div id="calculator" class="content active">
        <h2>Calculadora de Juros</h2>
        <label for="principal">Principal (R$):</label>
        <input type="number" id="principal" placeholder="Digite o valor principal">
        <br>
        <label for="taxa">Taxa de juros (% ao ano):</label>
        <input type="number" id="taxa" placeholder="Digite a taxa de juros">
        <br>
        <label for="anos">Número de anos:</label>
        <input type="number" id="anos" placeholder="Digite o número de anos">
        <br>
        <label for="periodicidade">Periodicidade dos juros:</label>
        <select id="periodicidade">
            <option value="anual">Anual</option>
            <option value="mensal">Mensal</option>
        </select>
        <br>
        <label for="tipo">Tipo de juros:</label>
        <select id="tipo">
            <option value="simples">Juros Simples</option>
            <option value="compostos">Juros Compostos</option>
        </select>
        <br>
        <button onclick="calcularParcelas()">Calcular</button>
        <br>
        <div id="tabelaParcelas"></div>
        <p>Valor total: R$ <span id="valorTotal"></span></p>
        <p>Valor das parcelas: R$ <span id="valorParcelas"></span></p>
    </div>

    <div id="study" class="content">
        <h2>Área de Estudo</h2>
        <h3>Taxa de Juros</h3>
        <p>A taxa de juros representa o custo do dinheiro ao longo do tempo. Ela é expressa em percentual ao ano.</p>
        
        <h3>Financiamento</h3>
        <p>O financiamento é uma forma de empréstimo em que o devedor recebe dinheiro do credor, que deve ser pago ao longo do tempo, geralmente com juros.</p>
        
        <h3>Tipos de Juros</h3>
        <ul>
            <li><strong>Juros Simples:</strong> Calculados apenas sobre o valor inicial.</li>
            <li><strong>Juros Compostos:</strong> Calculados sobre o valor inicial e sobre os juros acumulados.</li>
        </ul>
        
        <h3>Opções de Investimento</h3>
        <p>Existem diversas formas de investir seu dinheiro, cada uma com características próprias de risco e retorno:</p>
        <ul>
            <li><strong>Renda Fixa:</strong> Investimentos com retorno previsível, como CDB, Tesouro Direto.</li>
            <li><strong>Renda Variável:</strong> Investimentos com retorno variável, como ações e fundos imobiliários.</li>
            <li><strong>Fundos de Investimento:</strong> Cestas de investimentos geridas por profissionais.</li>
            <li><strong>Investimentos Imobiliários:</strong> Compra de imóveis para renda ou valorização.</li>
        </ul>
    </div>

    <div id="avalie" class="content">
        <h2>Avalie</h2>
        <p>Nos avalie por esse link: <a href="https://docs.google.com/forms/d/e/1FAIpQLSfsyddQqiOWcciUysCwdAv2frYUlUaXRrp1-x9fBj974ebCJw/viewform?usp=sf_link" target="_blank">Formulário de Avaliação</a></p>
    </div>

    <script>
        function showCalculator() {
            document.getElementById("calculator").style.display = "block";
            document.getElementById("study").style.display = "none";
            document.getElementById("avalie").style.display = "none";
            document.querySelector('.container button:nth-child(1)').classList.add('active');
            document.querySelector('.container button:nth-child(2)').classList.remove('active');
            document.querySelector('.container button:nth-child(3)').classList.remove('active');
        }

        function showStudy() {
            document.getElementById("calculator").style.display = "none";
            document.getElementById("study").style.display = "block";
            document.getElementById("avalie").style.display = "none";
            document.querySelector('.container button:nth-child(2)').classList.add('active');
            document.querySelector('.container button:nth-child(1)').classList.remove('active');
            document.querySelector('.container button:nth-child(3)').classList.remove('active');
        }

        function showAvalie() {
            document.getElementById("calculator").style.display = "none";
            document.getElementById("study").style.display = "none";
            document.getElementById("avalie").style.display = "block";
            document.querySelector('.container button:nth-child(3)').classList.add('active');
            document.querySelector('.container button:nth-child(1)').classList.remove('active');
            document.querySelector('.container button:nth-child(2)').classList.remove('active');
        }

        function calcularParcelas() {
            var principal = parseFloat(document.getElementById("principal").value);
            var taxa = parseFloat(document.getElementById("taxa").value);
            var anos = parseFloat(document.getElementById("anos").value);
            var tipo = document.getElementById("tipo").value;
            var periodicidade = document.getElementById("periodicidade").value;

            var valorTotal;
            var valorParcelas;

            if (periodicidade === "mensal") {
                taxa = taxa / 12; // converte taxa anual para mensal
                anos = anos * 12; // converte anos para meses
            }

            var tabela = '<table>';
            tabela += '<tr><th>Mês</th><th>Valor Parcela</th><th>Juros</th><th>Total Pago</th></tr>';
            var valorParcela = 0;
            var totalPago = 0;
            var totalJuros = 0;

            if (tipo === "simples") {
                valorTotal = principal * (1 + (taxa / 100) * anos);
                valorParcela = valorTotal / anos; // Divide pelo total de meses
                for (var i = 1; i <= anos; i++) {
                    var juros = principal * (taxa / 100);
                    totalJuros += juros;
                    totalPago += valorParcela;
                    tabela += '<tr><td>' + i + '</td><td>' + valorParcela.toFixed(2) + '</td><td>' + juros.toFixed(2) + '</td><td>' + totalPago.toFixed(2) + '</td></tr>';
                }
            } else if (tipo === "compostos") {
                valorTotal = principal * Math.pow(1 + (taxa / 100), anos);
                valorParcela = valorTotal / anos; // Divide pelo total de meses
                var saldoDevedor = principal;
                for (var j = 1; j <= anos; j++) {
                    var juros = saldoDevedor * (taxa / 100);
                    saldoDevedor *= (1 + taxa / 100);
                    totalJuros += juros;
                    totalPago += valorParcela;
                    tabela += '<tr><td>' + j + '</td><td>' + valorParcela.toFixed(2) + '</td><td>' + juros.toFixed(2) + '</td><td>' + totalPago.toFixed(2) + '</td></tr>';
                }
            }

            tabela += '</table>';

            document.getElementById("tabelaParcelas").innerHTML = tabela;
            document.getElementById("valorTotal").innerText = valorTotal.toFixed(2);
            document.getElementById("valorParcelas").innerText = valorParcela.toFixed(2);
        }
    </script>
</body>
</html>
