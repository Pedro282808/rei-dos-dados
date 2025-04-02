<!DOCTYPE html>
<html lang="pt">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Rei dos Dados</title>
    <style>
        body {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background: linear-gradient(to right, red 50%, blue 50%);
            font-family: Arial, sans-serif;
            flex-direction: column;
            position: relative;
            overflow: hidden;
        }
        .title {
            font-size: 60px;
            font-weight: bold;
            text-transform: uppercase;
            letter-spacing: 3px;
            color: gold;
            text-shadow: 3px 3px 10px black;
            width: 100%;
            background-color: rgba(0, 0, 0, 0.7);
            padding: 20px 0;
            text-align: center;
        }
        .login-container {
            display: flex;
            flex-direction: column;
            align-items: center;
            margin-top: 20px;
        }
        .login-container input {
            padding: 10px;
            margin: 10px;
            border-radius: 5px;
            border: none;
            width: 250px;
        }
        .login-container button {
            background-color: #007bff;
            color: white;
            padding: 10px 20px;
            font-size: 18px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }
        .login-container button:hover {
            background-color: #0056b3;
        }
        .action-buttons {
            position: absolute;
            bottom: 20px;
            display: flex;
            justify-content: center;
            align-items: center;
            gap: 20px;
            z-index: 1;
            width: 100%;
        }
        .action-buttons a {
            background-color: #25D366;
            padding: 15px;
            border-radius: 5px;
            color: white;
            font-size: 16px;
            text-align: center;
            text-decoration: none;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 8px;
            cursor: pointer;
        }
        .action-buttons .whatsapp {
            background-color: #25D366;
        }
        .action-buttons .purchase {
            background-color: #28a745;
        }
        .game-container {
            text-align: center;
            margin-top: 150px;
            display: none; /* Inicialmente escondido */
        }
        #dice {
            font-size: 200px; /* Aumentando o tamanho do dado */
            margin-bottom: 20px;
        }
        .side-bar {
            width: 35%;
            height: 100vh;
            padding: 20px;
            background-color: rgba(0, 0, 0, 0.7);
            border-radius: 10px;
            position: absolute;
            right: 10px;
            top: 20px;
            color: white;
        }
        .exit-button {
            background-color: #dc3545;
            padding: 10px 20px;
            font-size: 18px;
            border: none;
            border-radius: 5px;
            color: white;
            cursor: pointer;
            margin-top: 20px;
        }
        .exit-button:hover {
            background-color: #c82333;
        }
    </style>
</head>
<body>
    <div class="title">Rei dos Dados</div>

    <!-- Formulário de login -->
    <div class="login-container" id="loginContainer">
        <input type="email" id="email" placeholder="Digite seu e-mail" required>
        <input type="password" id="password" placeholder="Digite sua senha" required>
        <button onclick="login()">Entrar</button>
    </div>

    <!-- Jogo do Dado (escondido inicialmente) -->
    <div class="game-container" id="gameContainer">
        <div id="dice" class="dice">🎲</div>
        <button onclick="startRolling()">Play</button>
        <div id="result" class="winner"></div>

        <!-- Botão de sair -->
        <button class="exit-button" onclick="exitGame()">Sair</button>
    </div>

    <!-- Botões de Ação (WhatsApp e Compra) -->
    <div class="action-buttons">
        <!-- Botão de WhatsApp -->
        <a href="https://wa.me/21977349485" class="whatsapp" target="_blank">
            📱 Contato
        </a>
        <!-- Botão de Compra -->
        <a href="https://pay.kiwify.com.br/c4GZUfI" class="purchase" target="_blank">
            💳 Compra
        </a>
    </div>

    <!-- Barra lateral - link para a Casa de Apostas -->
    <div class="side-bar">
        <h3>Casa de Apostas - Em Tempo Real</h3>
        <a href="https://7k.bet.br/?src=gmbvqeyrhgkzjracuyzkdaxcw&utm_source=342488&utm_campaign=branding&utm_content=pliupprrih&gclid=Cj0KCQjwna6_BhCbARIsALId2Z19MPmWSgZbyyfzixUhLSBWZh3mZLFhPttuxda-B1FWu--ETZEPXfUaAvWtEALw_wcB" target="_blank" style="color: white; text-decoration: none; padding: 10px; background-color: #007bff; border-radius: 5px;">
            Visite a Casa de Apostas
        </a>
    </div>

    <script>
        let rolling;

        // Função de login
        function login() {
            const email = document.getElementById("email").value;
            const password = document.getElementById("password").value;
            
            // A senha e o e-mail são válidos?
            if (email && password === '272707') {
                document.getElementById("loginContainer").style.display = 'none';
                document.getElementById("gameContainer").style.display = 'block';
            } else {
                alert("E-mail ou senha incorretos!");
            }
        }

        // Função para iniciar o rolar do dado
        function startRolling() {
            document.getElementById("result").textContent = "";
            let count = 0;
            rolling = setInterval(() => {
                document.getElementById("dice").textContent = Math.floor(Math.random() * 6) + 1;
                count++;
                if (count >= 20) {
                    stopRolling();
                }
            }, 100);
        }

        // Função para parar o rolar do dado
        function stopRolling() {
            clearInterval(rolling);
            rolling = null;
            let result = parseInt(document.getElementById("dice").textContent);
            let winnerText = result > 3 ? "Vermelho Ganhou!" : "Azul Ganhou!";
            document.getElementById("result").textContent = winnerText;
        }

        // Função para sair do jogo
        function exitGame() {
            document.getElementById("gameContainer").style.display = 'none';
            document.getElementById("loginContainer").style.display = 'block';
        }
    </script>
</body>
</html>
