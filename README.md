<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Calculadoras</title>
    <style>
        body {
            font-family: Arial, sans-serif;
        }
        .tabs {
            display: flex;
            cursor: pointer;
            margin-bottom: 20px;
        }
        .tabs div {
            padding: 10px 20px;
            background-color: #f4f4f4;
            margin-right: 5px;
            border-radius: 5px;
            transition: background 0.3s;
        }
        .tabs div.active {
            background-color: #007BFF;
            color: white;
        }
        .content {
            display: none;
        }
        .content.active {
            display: block;
        }
        table, th, td {
            border: 1px solid black;
            border-collapse: collapse;
        }
        th, td {
            padding: 8px;
            text-align: left;
        }
        table {
            width: 100%;
            margin-top: 20px;
        }
        .calculator {
            background: #fff;
            border-radius: 10px;
            box-shadow: 0 0 20px rgba(0, 0, 0, 0.2);
            padding: 20px;
            width: 300px;
            margin: 20px auto;
        }
        #display {
            width: 100%;
            height: 40px;
            text-align: right;
            font-size: 24px;
            margin-bottom: 10px;
            padding: 5px;
            border: 1px solid #ccc;
            border-radius: 5px;
        }
        .button {
            width: 60px;
            height: 60px;
            margin: 5px;
            font-size: 20px;
            border: none;
            border-radius: 5px;
            background-color: #007BFF;
            color: white;
            cursor: pointer;
            transition: background 0.3s;
        }
        .button:hover {
            background-color: #0056b3;
        }
        .button.operation {
            background-color: #28a745;
        }
        .button.operation:hover {
            background-color: #218838;
        }
    </style>
</head>
<body>
    <div class="tabs">
        <div onclick="showTab('calculator')" class="active">Calculadora de Juros</div>
        <div onclick="showTab('study')">Área de Estudo</div>
        <div onclick="showTab('avalie')">Avalie</div>
        <div onclick="showTab('calculadoraPadrao')">Calculadora Padrão</div>
    </div>

    <div id="calculator" class="content active">
        <h2>Calculadora de Juros</h2>
        <label for="principal">Principal (R$):</label>
        <input type="number" id="principal" placeholder="Digite o valor principal" required>
        <br>
        <label for="taxa">Taxa de juros (% ao ano):</label>
        <input type="number" id="taxa" placeholder="Digite a taxa de juros" required>
        <br>
        <label for="anos">Número de anos:</label>
        <input type="number" id="anos" placeholder="Digite o número de anos" required>
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
<br>Taxas de Juros
As taxas de juros representam o custo do dinheiro ao longo do tempo, sendo fundamentais para empréstimos, investimentos e na política monetária.
<br>
Definição<br>
- Taxa de Juros é um percentual aplicado sobre um valor inicial (principal) para determinar o retorno ou o custo do dinheiro em determinado período.  <br>
<br>  - Exemplo: Se você investe R$ 1.000,00 a uma taxa de 5% ao ano, ao final de um ano terá R$ 1.050,00 (sem considerar a inflação).

<br>Tipos de Juros  
<br>
<br>1. Juros Simples
<br>Os juros simples são calculados somente sobre o valor principal inicial, sem considerar os períodos anteriores.  
<br>
<br>Fórmula do Montante (M): 
<br>M = P + (P * i * n)  
<br>
<br>Ou simplesmente:  
<br>J = P * i * n  
<br>
<br>Onde:  
<br>- \( P \) = principal (valor inicial)  
<br>- \( i \) = taxa de juros por período (em decimal)  
<br>- \( n \) = número de períodos  
<br>
<br>Exemplo:
<br>Um empréstimo de R$ 1.000,00 com uma taxa de 10% ao ano (0,10) por 3 anos:  
<br>J = 1000 * 0,10 * 3 = 300  
<br>M = 1000 + 300 = 1300  
<br>
<br>2. Juros Compostos  
<br>Os juros compostos consideram não apenas o valor principal, mas também os juros acumulados dos períodos anteriores.  
<br>
<br>Fórmula do Montante (M):
<br>M = P * (1 + i)^n  
<br>
<br>Onde:  
<br>- \( P \) = principal  
<br>- \( i \) = taxa de juros por período (em decimal)  
<br>- \( n \) = número de períodos  
<br>
<br>Exemplo: 
<br>Se você investe R$ 1.000,00 a uma taxa de 10% ao ano (0,10) por 3 anos:  
<br>M = 1000 * (1 + 0,10)^3  
<br>M = 1000 * 1,1^3 = 1000 * 1,331 = 1331  
<br>
<br>Os juros acumulados seriam:  
<br>J = M - P  
<br>J = 1331 - 1000 = 331  
<br>
<br>
<br>
<br>Modos de Economizar Dinheiro
<br>Economizar dinheiro é essencial para construir um patrimônio sólido. Aqui estão algumas dicas práticas:
<br>
<br>1. Crie um orçamento
<br>   - Liste receitas e despesas mensais.
<br>   - Use a regra 50/30/20:
<br>     - 50% para necessidades.
<br>     - 30% para desejos.
<br>     - 20% para poupança ou investimentos.
<br>
<br>2. Reduza custos supérfluos
<br>   - Substitua gastos com lazer caro por opções mais acessíveis.
<br>   - Faça refeições em casa em vez de comer fora regularmente.
<br>
<br>3. Planeje compras maiores
<br>   - Compare preços e aguarde promoções.
<br>   - Use cashback ou cupons de desconto.
<br>
<br>4. Automatize suas economias
<br>   - Configure uma transferência automática mensal para uma conta poupança ou investimento.
<br>
<br>5. Evite dívidas com juros altos
<br>   - Priorize pagar cartões de crédito ou empréstimos antes de começar a poupar.
<br>
<br>
<br>
<br>Melhores Formas de Investir Dinheiro
<br>Investimentos podem ser divididos entre **renda fixa** e **renda variável**, e sua escolha depende do perfil de risco e objetivos.
<br>
<br>Renda Fixa 
<br>Indicada para perfis conservadores ou iniciantes, com retornos previsíveis e baixo risco.
<br>- Tesouro Direto: Títulos públicos emitidos pelo governo.
<br>  - Tesouro Selic: Ideal para reserva de emergência.
<br>  - Tesouro IPCA+: Proteção contra inflação.
<br>- CDB (Certificado de Depósito Bancário): Oferecido por bancos, geralmente garantido pelo FGC (até R$ 250.000,00).
<br>- LCI/LCA: Isentos de imposto de renda, voltados ao setor imobiliário e agrícola.
<br>
<br>Renda Variável 
<br>Indicada para quem busca maiores retornos e aceita mais riscos.
<br>- Ações: Participações em empresas negociadas na bolsa.
<br>- Fundos Imobiliários (FIIs): Investimentos em imóveis com boa liquidez.
<br>- ETFs:** Fundos negociados em bolsa que replicam índices, como o Ibovespa.
<br>- Criptomoedas:** Alternativa volátil, mas potencialmente lucrativa para quem compreende o mercado.
<br>
<br>Dica: Diversificação 
<br>Nunca invista todo o dinheiro em um único tipo de aplicação. Divida entre renda fixa e variável para reduzir riscos.
<br>
<br>
<br>
<br>Melhores Cursos de Graduação para Especialização em Finanças  
<br>Se você deseja atuar ou se especializar no mercado financeiro, existem graduações que oferecem base teórica e prática nessa área:
<br>
<br>1. Administração 
<br>Foco em gestão empresarial e finanças corporativas, ideal para análise de investimentos e planejamento estratégico.
<br>
<br>2. Economia
<br>Estuda o comportamento de mercados, políticas monetárias e análise macro e microeconômica.
<br>
<br>3. Ciências Contábeis
<br>Aborda contabilidade empresarial, análise de balanços e gestão tributária.
<br>
<br>4.Matemática Aplicada ou Estatística 
<br>Excelente para áreas quantitativas, como análise de risco e modelagem financeira.
<br>
<br>5. Engenharia de Produção
<br>Combina gestão e otimização de recursos com economia corporativa e finanças.
<br>
<br>Cursos Complementares 
<br>- MBA em Finanças ou Gestão de Investimentos: Essencial para cargos de liderança.  
<br>- Certificações:  
<br>  - CPA-10/CPA-20:** Introdução ao mercado financeiro.  
 <br> - CFA (Chartered Financial Analyst): Certificação global em finanças.  
 <br> - CFP (Certified Financial Planner): Voltada para planejamento financeiro pessoal.
<br>
<br> Instituições Recomendadas  
No Brasil:  
<br>- FGV (Fundação Getulio Vargas) Excelência em Administração e Economia.  
<br>- Insper: Foco em negócios e finanças.  
<br>- USP: Referência em Economia e Contabilidade.  
<br>
<br>No exterior:  
<br>- Harvard Business School: Líder global em MBA.  
<br>- London School of Economics: Foco em economia e políticas financeiras.  
<br>
<br>Com planejamento, economia e conhecimento, você estará preparado para conquistar o sucesso no mercado financeiro! 
    </div>

    <div id="avalie" class="content">
        <h2>Avalie</h2>
        <!-- Conteúdo da aba Avalie -->
    </div>

    <div id="calculadoraPadrao" class="content">
        <div class="calculator">
            <input type="text" id="display" disabled>
            <div>
                <button class="button" onclick="clearDisplay()">C</button>
                <button class="button" onclick="appendToDisplay('7')">7</button>
                <button class="button" onclick="appendToDisplay('8')">8</button>
                <button class="button" onclick="appendToDisplay('9')">9</button>
                <button class="button operation" onclick="appendToDisplay('/')">/</button>
            </div>
            <div>
                <button class="button" onclick="appendToDisplay('4')">4</button>
                <button class="button" onclick="appendToDisplay('5')">5</button>
                <button class="button" onclick="appendToDisplay('6')">6</button>
                <button class="button operation" onclick="appendToDisplay('*')">*</button>
            </div>
            <div>
                <button class="button" onclick="appendToDisplay('1')">1</button>
                <button class="button" onclick="appendToDisplay('2')">2</button>
                <button class="button" onclick="appendToDisplay('3')">3</button>
                <button class="button operation" onclick="appendToDisplay('-')">-</button>
            </div>
            <div>
                <button class="button" onclick="appendToDisplay('0')">0</button>
                <button class="button" onclick="calculate()">=</button>
                <button class="button operation" onclick="appendToDisplay('+')">+</button>
            </div>
        </div>
    </div>

    <script>
        function showTab(tabId) {
            document.querySelectorAll('.content').forEach(tab => tab.classList.remove('active'));
            document.querySelectorAll('.tabs div').forEach(tab => tab.classList.remove('active'));
            document.getElementById(tabId).classList.add('active');
            document.querySelector(`.tabs div[onclick="showTab('${tabId}')"]`).classList.add('active');
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
                taxa = taxa / 12;
                anos = anos * 12;
            }

            var tabela = '<table>';
            tabela += '<tr><th>Período</th><th>Valor Parcela</th><th>Juros</th><th>Total Pago</th><th>Total de Juros Pagos</th></tr>';
            var totalPago = 0;
            var totalJuros = 0;

            if (tipo === "simples") {
                valorTotal = principal * (1 + (taxa / 100) * anos);
                valorParcelas = valorTotal / anos;
                for (var i = 1; i <= anos; i++) {
                    var juros = principal * (taxa / 100);
                    totalJuros += juros;
                    totalPago += valorParcelas;
                    tabela += `<tr><td>${i}</td><td>${valorParcelas.toFixed(2)}</td><td>${juros.toFixed(2)}</td><td>${totalPago.toFixed(2)}</td><td>${totalJuros.toFixed(2)}</td></tr>`;
                }
            } else if (tipo === "compostos") {
                valorTotal = principal * Math.pow(1 + (taxa / 100), anos);
                valorParcelas = valorTotal / anos;
                var saldoDevedor = principal;
                for (var j = 1; j <= anos; j++) {
                    var juros = saldoDevedor * (taxa / 100);
                    saldoDevedor += juros;
                    totalJuros += juros;
                    totalPago += valorParcelas;
                    tabela += `<tr><td>${j}</td><td>${valorParcelas.toFixed(2)}</td><td>${juros.toFixed(2)}</td><td>${totalPago.toFixed(2)}</td><td>${totalJuros.toFixed(2)}</td></tr>`;
                }
            }

            tabela += '</table>';

            document.getElementById("tabelaParcelas").innerHTML = tabela;
            document.getElementById("valorTotal").innerText = valorTotal.toFixed(2);
            document.getElementById("valorParcelas").innerText = valorParcelas.toFixed(2);
        }

        function appendToDisplay(value) {
            document.getElementById("display").value += value;
        }

        function clearDisplay() {
            document.getElementById("display").value = '';
        }

        function calculate() {
            const display = document.getElementById("display");
            try {
                display.value = eval(display.value);
            } catch (error) {
                display.value = 'Erro';
            }
        }
    </script>
</body>
</html>

