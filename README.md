<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Matriz de Responsabilidade Interativa</title>
    <style>
        /* Importando uma fonte moderna do Google Fonts */
        @import url('https://fonts.googleapis.com/css2?family=Poppins:wght@400;500;600&display=swap');

        /* Estilos Gerais */
        body {
            font-family: 'Poppins', sans-serif;
            background-color: #f4f7fa;
            color: #333;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            margin: 0;
            padding: 20px;
        }

        /* O container principal da matriz */
        .matriz-container {
            background-color: #ffffff;
            border-radius: 12px;
            box-shadow: 0 8px 30px rgba(0, 70, 150, 0.1);
            padding: 30px;
            width: 100%;
            max-width: 900px;
            overflow: hidden;
            border: 1px solid #e0e0e0;
        }

        .matriz-header h2 {
            margin: 0 0 5px 0;
            color: #004a91; /* Cor primária, similar a um azul corporativo */
            font-size: 24px;
        }

        .matriz-header p {
            margin: 0 0 25px 0;
            color: #667;
            font-size: 16px;
        }
        
        /* Layout principal em colunas (Grid) */
        .matriz-corpo {
            display: grid;
            grid-template-columns: 1fr 2fr; /* Coluna de cargos é menor que a de detalhes */
            gap: 30px;
        }

        .coluna-cargos h3, .coluna-detalhes h3 {
            margin-top: 0;
            margin-bottom: 15px;
            color: #004a91;
            border-bottom: 2px solid #e0e0e0;
            padding-bottom: 8px;
            font-size: 18px;
        }

        /* Estilo dos Cards de Cargos - A parte interativa */
        .cargo-card {
            background-color: #f8f9fa;
            border: 1px solid #e9ecef;
            border-radius: 8px;
            padding: 15px;
            margin-bottom: 10px;
            cursor: pointer;
            transition: all 0.3s ease;
            position: relative;
        }

        .cargo-card:hover {
            transform: translateX(5px);
            box-shadow: 0 4px 15px rgba(0, 70, 150, 0.08);
            border-left: 4px solid #007bff; /* Destaque azul no hover */
        }
        
        /* Estilo para o cargo que está ATIVO (selecionado) */
        .cargo-card.active {
            background-color: #e6f2ff;
            border-left: 4px solid #007bff;
            color: #004a91;
            font-weight: 600;
        }

        /* Conteúdo dos detalhes que aparece/desaparece */
        .detalhes-conteudo {
            display: none; /* Escondido por padrão */
            animation: fadeIn 0.5s ease;
        }

        .detalhes-conteudo.active {
            display: block; /* Visível quando ativo */
        }

        /* Animação de Fade In */
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }

        .detalhes-secao {
            margin-bottom: 20px;
        }

        .detalhes-secao h4 {
            margin: 0 0 10px 0;
            color: #333;
            font-size: 16px;
        }

        .tags-list {
            list-style: none;
            padding: 0;
            margin: 0;
            display: flex;
            flex-wrap: wrap;
            gap: 8px;
        }

        .tags-list li {
            background-color: #e9ecef;
            color: #495057;
            padding: 5px 12px;
            border-radius: 15px;
            font-size: 14px;
        }
    </style>
</head>
<body>

    <div class="matriz-container">
        <div class="matriz-header">
            <h2>Área: Orçamento/Cotação</h2>
            <p>Passe o mouse sobre um cargo para ver seus detalhes.</p>
        </div>
        
        <div class="matriz-corpo">
            <!-- COLUNA 1: CARGOS (OS GATILHOS) -->
            <div class="coluna-cargos">
                <h3>Cargos</h3>
                <div class="cargo-card" data-target="analista">Analista Orçamento</div>
                <div class="cargo-card" data-target="especialista">Especialista</div>
            </div>

            <!-- COLUNA 2: DETALHES (OS ALVOS) -->
            <div class="coluna-detalhes">
                <h3>Detalhes do Cargo</h3>

                <!-- Detalhes do Analista -->
                <div id="analista" class="detalhes-conteudo">
                    <div class="detalhes-secao">
                        <h4>Atribuições e Responsabilidades</h4>
                        <ul class="tags-list">
                            <li>Orçamento</li>
                        </ul>
                    </div>
                    <div class="detalhes-secao">
                        <h4>Interage com</h4>
                        <ul class="tags-list">
                            <li>Comercial</li>
                        </ul>
                    </div>
                    <div class="detalhes-secao">
                        <h4>Carreira e Desenvolvimento</h4>
                        <ul class="tags-list">
                            <li>Níveis: I, II e III</li>
                            <li>Trilha LMS: Negócios</li>
                            <li>Trilha LMS: Produtos</li>
                        </ul>
                    </div>
                </div>

                <!-- Detalhes do Especialista -->
                <div id="especialista" class="detalhes-conteudo">
                    <div class="detalhes-secao">
                        <h4>Atribuições e Responsabilidades</h4>
                        <ul class="tags-list">
                            <li>Cotação</li>
                            <li>Cadastro de Produto</li>
                        </ul>
                    </div>
                    <div class="detalhes-secao">
                        <h4>Interage com</h4>
                        <ul class="tags-list">
                            <li>Compras/Facilities</li>
                        </ul>
                    </div>
                     <div class="detalhes-secao">
                        <h4>Carreira e Desenvolvimento</h4>
                        <ul class="tags-list">
                            <li>Níveis: I, II e III</li>
                            <li>Trilha LMS: Protheus</li>
                        </ul>
                    </div>
                </div>
                
            </div>
        </div>
    </div>

    <script>
        document.addEventListener('DOMContentLoaded', function () {
            const cargoCards = document.querySelectorAll('.cargo-card');
            const detalhesConteudos = document.querySelectorAll('.detalhes-conteudo');

            // Função para mostrar os detalhes de um cargo específico
            function mostrarDetalhes(targetId) {
                // Esconde todos os outros detalhes
                detalhesConteudos.forEach(conteudo => {
                    conteudo.classList.remove('active');
                });
                // Remove a classe 'active' de todos os cards
                cargoCards.forEach(card => {
                    card.classList.remove('active');
                });

                // Mostra o detalhe e o card correspondente como ativo
                const targetElement = document.getElementById(targetId);
                const targetCard = document.querySelector(`[data-target="${targetId}"]`);
                
                if (targetElement && targetCard) {
                    targetElement.classList.add('active');
                    targetCard.classList.add('active');
                }
            }

            // Adiciona o evento de 'mouseenter' (passar o mouse) para cada card
            cargoCards.forEach(card => {
                card.addEventListener('mouseenter', () => {
                    const targetId = card.getAttribute('data-target');
                    mostrarDetalhes(targetId);
                });
            });

            // Inicia a visualização com o primeiro cargo já selecionado
            if (cargoCards.length > 0) {
                const primeiroTarget = cargoCards[0].getAttribute('data-target');
                mostrarDetalhes(primeiroTarget);
            }
        });
    </script>

</body>
</html>
