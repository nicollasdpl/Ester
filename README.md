<html>
<head>
    <style>
        body {
            background-color: #FF1493; /* Alterar a cor de fundo aqui */
            font-family: Arial, sans-serif;
        }

        h1 {
            text-align: center;
            font-size: 36px;
            margin-top: 100px;
        }

        .container {
            display: flex;
            flex-direction: row;
            justify-content: center;
            align-items: center;
            height: 100vh;
        }

        .box {
            width: 200px;
            height: 100px;
            margin: 20px;
            border-radius: 10px;
            color: white;
            font-size: 24px;
            font-weight: bold;
            display: flex;
            justify-content: center;
            align-items: center;
            cursor: pointer;
            box-shadow: 5px 5px 10px rgba(0,0,0,0.5);
        }

        .yes {
            background-color: #ff00ff;
        }

        .no {
            background-color: #ff0000;
        }
    </style>
    <script>
        // Função para gerar um número aleatório entre min e max
        function random(min, max) {
            return Math.floor(Math.random() * (max - min + 1)) + min;
        }

         // Função para mover a caixa do não para uma posição aleatória na tela
         function moveNo() {
             // Pegar a caixa do não pelo id
             var no = document.getElementById("no");
            
             // Gerar uma posição aleatória dentro da largura e altura da tela
             var x = random(0, window.innerWidth - no.offsetWidth);
             var y = random(0, window.innerHeight - no.offsetHeight);

             // Atribuir a posição à caixa do não
             no.style.left = x + "px";
             no.style.top = y + "px";
         }

         // Função para redirecionar para o site quando clicar na caixa do sim
         function redirectYes() {
             // Pegar o link do site pelo id
             var link = document.getElementById("link").value;

             // Verificar se o link é válido
             if (link.startsWith("http://") || link.startsWith("https://")) {
                 // Redirecionar para o site
                 window.location.href = link;
             } else {
                 // Mostrar um alerta de erro
                 alert("Por favor, digite um link válido.");
             }
         }

         // Função para adicionar os eventos de clique e mouseover nas caixas
         function addEvents() {
             // Pegar as caixas pelo id
             var yes = document.getElementById("yes");
             var no = document.getElementById("no");

             // Adicionar o evento de clique na caixa do sim
             yes.addEventListener("click", redirectYes);

             // Adicionar o evento de mouseover na caixa do não
             no.addEventListener("mouseover", moveNo);
            
             // Adicionar o evento de click na caixa do não
             no.addEventListener("click", moveNo);
         }

         // Executar a função addEvents quando a página carregar
         window.onload = addEvents;
    </script>
</head>
<body>
    <h1>Bora assistir Barbie?</h1>
    <div class="container">
        <div id="yes" class="box">SIM</div>
        <div id="no" class="box" style="position: absolute;">NÃO</div>
    </div>
    <!-- Esse input é invisível, mas guarda o valor do link do site -->
    <input id="link" type="hidden" value="https://www.netflix.com/br/title/70264888">
</body>
</html>
