<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Olhou Achou? - Projeto de Vida</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: Arial, sans-serif;
        }
        body {
            background-color: #f8f9fa;
            color: #333;
        }
        /* Tela de Cadastro */
        .cadastro-tela {
            width: 100%;
            max-width: 400px;
            margin: 50px auto;
            padding: 30px;
            background-color: white;
            border-radius: 15px;
            box-shadow: 0 0 10px rgba(0,0,0,0.1);
            text-align: center;
        }
        .logo {
            font-size: 28px;
            font-weight: bold;
            color: #2ecc71;
            margin-bottom: 30px;
        }
        .botao-cadastro {
            display: block;
            width: 100%;
            padding: 15px;
            margin: 10px 0;
            border: none;
            border-radius: 10px;
            font-size: 16px;
            cursor: pointer;
            color: white;
        }
        .google { background-color: #db4437; }
        .facebook { background-color: #4267b2; }
        .telefone { background-color: #2ecc71; }

        /* Tela Inicial */
        .tela-inicial {
            display: none;
            width: 100%;
            height: 100vh;
            background-color: white;
            position: relative;
        }
        .topo {
            padding: 20px;
            text-align: center;
            background-color: #2ecc71;
            color: white;
        }
        .botao-foto {
            width: 80px;
            height: 80px;
            border-radius: 50%;
            background-color: #f39c12;
            color: white;
            border: none;
            font-size: 30px;
            margin: 30px auto;
            display: block;
            cursor: pointer;
        }
        .texto-inicial {
            text-align: center;
            font-size: 18px;
            margin-bottom: 20px;
        }
        .navegacao {
            position: fixed;
            bottom: 0;
            width: 100%;
            background-color: white;
            border-top: 1px solid #eee;
            display: flex;
            justify-content: space-around;
            padding: 15px 0;
        }
        .navegacao button {
            border: none;
            background: none;
            font-size: 14px;
            cursor: pointer;
            color: #333;
        }
        .navegacao button.ativo {
            color: #2ecc71;
            font-weight: bold;
        }

        /* Tela de Receitas */
        .tela-receitas {
            display: none;
            width: 100%;
            height: 100vh;
            background-color: white;
            position: relative;
        }
        .receita-item {
            display: flex;
            padding: 15px;
            border-bottom: 1px solid #eee;
        }
        .receita-foto {
            width: 80px;
            height: 80px;
            border-radius: 10px;
            object-fit: cover;
            margin-right: 15px;
        }
        .receita-detalhes h3 {
            font-size: 18px;
            margin-bottom: 5px;
        }
        .receita-detalhes p {
            font-size: 14px;
            color: #666;
        }

        /* Tela Exclusivo */
        .tela-exclusivo {
            display: none;
            width: 100%;
            height: 100vh;
            background-color: white;
            position: relative;
        }
        .chat-area {
            padding: 20px;
            height: calc(100vh - 120px);
            overflow-y: auto;
        }
        .mensagem {
            max-width: 70%;
            padding: 10px 15px;
            border-radius: 20px;
            margin-bottom: 15px;
        }
        .mensagem-usuario {
            background-color: #2ecc71;
            color: white;
            margin-left: auto;
        }
        .mensagem-nutri {
            background-color: #eee;
            color: #333;
        }
        .input-chat {
            position: fixed;
            bottom: 70px;
            width: 100%;
            padding: 10px 20px;
            display: flex;
        }
        .input-chat input {
            flex: 1;
            padding: 10px;
            border-radius: 20px;
            border: 1px solid #ddd;
            margin-right: 10px;
        }
        .input-chat button {
            padding: 10px 20px;
            border-radius: 20px;
            border: none;
            background-color: #2ecc71;
            color: white;
            cursor: pointer;
        }

        /* Tela Conta */
        .tela-conta {
            display: none;
            width: 100%;
            height: 100vh;
            background-color: white;
            position: relative;
        }
        .conta-item {
            padding: 20px;
            border-bottom: 1px solid #eee;
            font-size: 16px;
        }
    </style>
</head>
<body>
    <!-- Tela de Cadastro -->
    <div class="cadastro-tela" id="cadastro">
        <div class="logo">OLHOU ACHOU?</div>
        <h2>Cadastre-se ou entre</h2>
        <button class="botao-cadastro google" onclick="irParaInicial()">Entrar com Google</button>
        <button class="botao-cadastro facebook" onclick="irParaInicial()">Entrar com Facebook</button>
        <button class="botao-cadastro telefone" onclick="irParaInicial()">Entrar com Telefone</button>
        <p style="margin-top: 20px; font-size: 14px; color: #666;">Projeto de Vida - Escola</p>
    </div>

    <!-- Tela Inicial -->
    <div class="tela-inicial" id="inicial">
        <div class="topo">
            <h1>OLHOU ACHOU?</h1>
        </div>
        <div class="texto-inicial">
            <p>Tire uma foto dos ingredientes que tem em casa e descubra receitas incríveis!</p>
        </div>
        <button class="botao-foto" onclick="mostrarReceitas()">📸 Tirar Foto</button>
        
        <div class="navegacao">
            <button class="ativo" onclick="mostrarTela('inicial')">Início</button>
            <button onclick="mostrarTela('receitas')">Receitas</button>
            <button onclick="mostrarTela('conta')">Conta</button>
            <button onclick="mostrarTela('salvos')">Salvos</button>
            <button onclick="mostrarTela('exclusivo')">Exclusivo</button>
        </div>
    </div>

    <!-- Tela de Receitas -->
    <div class="tela-receitas" id="receitas">
        <div class="topo">
            <h1>RECEITAS SUGERIDAS</h1>
        </div>
        <div class="receita-item" onclick="mostrarDetalhes()">
            <img src="https://picsum.photos/80/80?random=1" class="receita-foto" alt="Salada de Frutas">
            <div class="receita-detalhes">
                <h3>Salada de Frutas Colorida</h3>
                <p>Preparo: 15min | Ingredientes: Banana, Maçã, Morango</p>
            </div>
        </div>
        <div class="receita-item" onclick="mostrarDetalhes()">
            <img src="https://picsum.photos/80/80?random=2" class="receita-foto" alt="Sopa de Legumes">
            <div class="receita-detalhes">
                <h3>Sopa de Legumes Cremosa</h3>
                <p>Preparo: 30min | Ingredientes: Cenoura, Batata, Cebola</p>
            </div>
        </div>
        <div class="receita-item" onclick="mostrarDetalhes()">
            <img src="https://picsum.photos/80/80?random=3" class="receita-foto" alt="Torta de Abóbora">
            <div class="receita-detalhes">
                <h3>Torta de Abóbora Simples</h3>
                <p>Preparo: 45min | Ingredientes: Abóbora, Farinha, Ovo</p>
            </div>
        </div>
        
        <div class="navegacao">
            <button onclick="mostrarTela('inicial')">Início</button>
            <button class="ativo" onclick="mostrarTela('receitas')">Receitas</button>
            <button onclick="mostrarTela('conta')">Conta</button>
            <button onclick="mostrarTela('salvos')">Salvos</button>
            <button onclick="mostrarTela('exclusivo')">Exclusivo</button>
        </div>
    </div>

    <!-- Tela Exclusivo -->
    <div class="tela-exclusivo" id="exclusivo">
        <div class="topo">
            <h1>EXCLUSIVO - NUTRICIONISTA</h1>
        </div>
        <div class="chat-area">
            <div class="mensagem mensagem-nutri">Olá! Eu sou a Dra. Ana, sua nutricionista. Em que posso ajudar você hoje?</div>
            <div class="mensagem mensagem-usuario">Oi! Quero saber como melhorar minha dieta para emagrecer.</div>
            <div class="mensagem mensagem-nutri">Ótima pergunta! Primeiro, é importante incluir muitas frutas e vegetais no dia a dia - eles são ricos em fibras e vitaminas. Evite alimentos processados e beba bastante água. Também recomendo comer pequenas porções ao longo do dia e praticar atividade física regularmente. Quer que eu faça uma sugestão de cardápio?</div>
        </div>
        <div class="input-chat">
            <input type="text" placeholder="Digite sua mensagem...">
            <button>Enviar</button>
        </div>
        
        <div class="navegacao">
            <button onclick="mostrarTela('inicial')">Início</button>
            <button onclick="mostrarTela('receitas')">Receitas</button>
            <button onclick="mostrarTela('conta')">Conta</button>
            <button onclick="mostrarTela('salvos')">Salvos</button>
            <button class="ativo" onclick="mostrarTela('exclusivo')">Exclusivo</button>
        </div>
    </div>

    <!-- Tela Conta -->
    <div class="tela-conta" id="conta">
        <div class="topo">
            <h1>MINHA CONTA</h1>
        </div>
        <div class="conta-item">Nome: João da Silva</div>
        <div class="conta-item">Email: joao@email.com</div>
        <div class="conta-item">Telefone: (21) 99999-9999</div>
        <div class="conta-item">Configurações do App</div>
        <div class="conta-item">Alterar Senha</div>
        <div class="conta-item">Adicionar Outra Conta</div>
        <div class="conta-item" style="color: red; margin-top: 30px;" onclick="voltarParaCadastro()">Sair da Conta</div>
        
        <div class="navegacao">
            <button onclick="mostrarTela('inicial')">Início</button>
            <button onclick="mostrarTela('receitas')">Receitas</button>
            <button class="ativo" onclick="mostrarTela('conta')">Conta</button>
            <button onclick="mostrarTela('salvos')">Salvos</button>
            <button onclick="mostrarTela('exclusivo')">Exclusivo</button>
        </div>
    </div>

    <!-- Tela Salvos -->
    <div class="tela-receitas" id="salvos">
        <div class="topo">
            <h1>RECEITAS SALVAS</h1>
        </div>
        <div class="receita-item">
            <img src="https://picsum.photos/80/80?random=4" class="receita-foto" alt="Suco Detox">
            <div class="receita-detalhes">
                <h3>Suco Detox de Limão e Gengibre</h3>
                <p>Preparo: 10min | Já feito ✔️</p>
            </div>
        </div>
        <div class="receita-item">
            <img src="https://picsum.photos/80/80?random=5" class="receita-foto" alt="Quiche de Brócolis">
            <div class="receita-detalhes">
                <h3>Quiche de Brócolis</h3>
                <p>Preparo: 40min | Já feito ✔️</p>
            </div>
        </div>
        
        <div class="navegacao">
            <button onclick="mostrarTela('inicial')">Início</button>
            <button onclick="mostrarTela('receitas')">Receitas</button>
            <button onclick="mostrarTela('conta')">Conta</button>
            <button class="ativo" onclick="mostrarTela('salvos')">Salvos</button>
            <button onclick="mostrarTela('exclusivo')">Exclusivo</button>
        </div>
    </div>

    <script>
        function irParaInicial() {
            document.getElementById('cadastro').style.display = 'none';
            document.getElementById('inicial').style.display = 'block';
        }
        function voltarParaCadastro() {
            document.getElementById('cadastro').style.display = 'block';
            document.getElementById('inicial').style.display = 'none';
            document.getElementById('receitas').style.display = 'none';
            document.getElementById('exclusivo').style.display = 'none';
