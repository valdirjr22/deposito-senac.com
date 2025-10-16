<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <title>SENAC - PAULISTA | Controle de Equipamentos e Materiais</title>
    <style>
        /* Variáveis de Cores SENAC/Sistema */
        :root {
            --primary-blue: #0056b3; /* Azul Escuro */
            --secondary-orange: #ff6600; /* Laranja SENAC */
            --light-bg: #f8f9fa; /* Branco Sujo / Off-White */
            --white: #ffffff;
            --text-dark: #343a40;
        }

        /* Estilos Comuns e Reset */
        body { 
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; 
            margin: 0; 
            padding: 0; 
            background-color: var(--light-bg); 
            color: var(--text-dark);
        }
        .container { 
            background-color: var(--white); 
            padding: 30px; 
            border-radius: 12px; 
            box-shadow: 0 6px 12px rgba(0,0,0,0.1); 
            margin: 30px auto; 
            max-width: 1000px;
        }
        h1 { 
            color: var(--primary-blue);
            text-align: center; 
            margin-bottom: 25px; 
            border-bottom: 3px solid var(--secondary-orange); /* Destaque Laranja */
            padding-bottom: 10px;
        }
        h2 {
            color: var(--primary-blue);
            border-bottom: 1px solid #dee2e6;
            padding-bottom: 10px;
        }
        
        /* Estilos de Formulário */
        label { display: block; margin-top: 15px; font-weight: 600; color: var(--text-dark); }
        input, select, textarea { 
            width: 100%; padding: 10px; margin-top: 5px; 
            box-sizing: border-box; border: 1px solid #ced4da; 
            border-radius: 6px;
            transition: border-color 0.3s;
        }
        input:focus, select:focus, textarea:focus {
            border-color: var(--primary-blue);
            box-shadow: 0 0 0 0.2rem rgba(0, 86, 179, 0.25);
            outline: none;
        }
        
        /* Estilos dos Botões Principais */
        .btn-principal { 
            background-color: var(--secondary-orange); /* Laranja SENAC */
            color: white; padding: 12px 20px; 
            border: none; border-radius: 6px; cursor: pointer; 
            margin-top: 20px; font-size: 16px; 
            font-weight: bold;
            transition: background-color 0.3s, transform 0.1s; 
        }
        .btn-principal:hover { background-color: #e65c00; transform: translateY(-1px); }

        /* Estilos dos Botões de Navegação (Aba) */
        .nav-bar { 
            display: flex; 
            justify-content: flex-start; 
            margin-bottom: 0;
            border-bottom: 2px solid #dee2e6;
            overflow-x: auto; 
            white-space: nowrap;
        }
        .nav-button { 
            background-color: var(--light-bg); 
            color: var(--primary-blue); 
            padding: 10px 20px; 
            border: 1px solid #dee2e6; 
            border-bottom: none;
            border-radius: 6px 6px 0 0; 
            cursor: pointer; 
            margin-left: 5px; 
            font-weight: 600;
            transition: background-color 0.3s, color 0.3s; 
            font-size: 0.95em; 
        }
        .nav-button:hover:not(.active) { background-color: #e9ecef; }
        .nav-button.active { 
            background-color: var(--white); 
            color: var(--secondary-orange); /* Laranja na aba ativa */
            border-bottom: 2px solid var(--white); 
            margin-bottom: -2px; 
        }

        /* Estilos da Tabela */
        table { width: 100%; border-collapse: collapse; margin-top: 20px; }
        th, td { border: 1px solid #dee2e6; padding: 12px; text-align: left; font-size: 0.9em; }
        th { background-color: var(--light-bg); color: var(--primary-blue); font-weight: 700; }
        
        /* Estilos dos botões de ação na tabela */
        .btn-acao { 
            padding: 6px 10px; margin: 3px; border: none; 
            border-radius: 4px; cursor: pointer; color: white; 
            font-size: 0.85em; font-weight: 600;
            transition: opacity 0.2s;
        }
        .btn-acao:hover { opacity: 0.8; }
        .btn-editar { background-color: #ffc107; color: #333; } 
        .btn-excluir { background-color: #dc3545; } 
        .btn-emprestar { background-color: var(--primary-blue); } 
        .btn-devolver { background-color: #20c997; } 
        .btn-reimprimir { background-color: #6c757d; } 
        .btn-visualizar { background-color: #17a2b8; } 
        .btn-limpar-busca { background-color: #6c757d; } /* Botão Limpar Busca */

        /* Cores de Status na Tabela */
        .status-cell { font-weight: bold; padding: 5px 10px; border-radius: 4px; display: inline-block; }
        .status-estoque { background-color: #d4edda; color: #155724; border: 1px solid #c3e6cb; } 
        .status-emprestado { background-color: #f8d7da; color: #721c24; border: 1px solid #f5c6cb; } 
        .status-manutencao, .status-em-andamento { background-color: #fff3cd; color: #856404; border: 1px solid #ffeeba; } 
        .status-baixas, .status-cancelada { background-color: #e2e3e5; color: #495057; border: 1px solid #d6d8db; } 
        .status-finalizada { background-color: #d1ecf1; color: #0c5460; border: 1px solid #bee5eb; } 
        .status-emuso { background-color: #d1ecf1; color: #0c5460; border: 1px solid #bee5eb; } 

        /* Esconder seções inicialmente */
        #secaoHistorico, #secaoGerenciar, #secaoEmprestimo, #secaoManutencao, #secaoOrdensManutencao { display: none; }

        /* Modal e Impressão (Manteve-se) */
        .modal { display: none; position: fixed; z-index: 1000; left: 0; top: 0; width: 100%; height: 100%; overflow: auto; background-color: rgba(0,0,0,0.6); }
        .modal-content { background-color: #fefefe; margin: 5% auto; padding: 25px; border: none; box-shadow: 0 5px 15px rgba(0,0,0,0.3); width: 80%; max-width: 550px; border-radius: 8px; }
        .close { color: #aaa; float: right; font-size: 32px; font-weight: bold; }
        .close:hover, .close:focus { color: #333; text-decoration: none; cursor: pointer; }

        
        /* Estilos de Impressão */
        @media print {
            body { background: none; }
            .container, .nav-bar, .modal { display: none !important; }
            .termo-impressao {
                font-family: 'Times New Roman', serif;
                padding: 15px; 
                margin: 0;
                line-height: 1.5; 
                color: #000;
                display: block !important;
                page-break-after: always;
                position: relative;
                overflow: hidden;
            }
            .assinaturas-devolucao { margin-top: 30px; border-top: 2px solid #000; padding-top: 15px;} 
            .assinaturas-devolucao p { margin: 5px 0; }
            .cabecalho-print { text-align: center; font-size: 1.0em; font-weight: bold; margin-bottom: 5px; } 

            /* MARCA D'ÁGUA */
            .termo-impressao::before {
                content: "SENAC PAULISTA";
                position: absolute;
                top: 50%;
                left: 50%;
                transform: translate(-50%, -50%) rotate(-45deg);
                font-size: 3em; 
                color: rgba(0, 0, 0, 0.08); 
                pointer-events: none; 
                white-space: nowrap; 
                z-index: -1; 
            }
            
            /* Ajuste de quebra de página para a tabela de itens na impressão */
            .discriminação-servicos {
                page-break-inside: avoid;
            }
        }
    </style>
</head>
<body>

    <div class="container" style="padding-bottom: 0; margin-bottom: 0; max-width: 900px;">
        <h1>Controle de Equipamentos e Materiais - SENAC - PAULISTA</h1>

        <div class="nav-bar">
            <button class="nav-button active" id="btnCadastro" onclick="mudarSecao('cadastro')">
                Cadastro
            </button>
            <button class="nav-button" id="btnHistorico" onclick="mudarSecao('historico')">
                Histórico de Equipamentos
            </button>
            <button class="nav-button" id="btnGerenciar" onclick="mudarSecao('gerenciar')">
                Gerenciar/Ações
            </button>
            <button class="nav-button" id="btnEmprestimo" onclick="mudarSecao('emprestimo')">
                Empréstimo
            </button>
            <button class="nav-button" id="btnManutencao" onclick="mudarSecao('manutencao')">
                Saída para Manutenção
            </button>
             <button class="nav-button" id="btnOrdensManutencao" onclick="mudarSecao('ordensManutencao')">
                Ordens de Manutenção
            </button>
        </div>
    </div>

    <div class="container" id="secaoCadastro" style="max-width: 600px;">
        <h2>Cadastrar Novo Equipamento</h2>
        <form id="cadastroForm">
            <label for="nome">Nome do Equipamento:</label>
            <select id="nome" required>
                </select>

            <label for="patrimonio">Nº de Tombamento/Série (Chave Única):</label>
            <input type="text" id="patrimonio" required placeholder="Ex: PATR-00123 ou Serial XYZ">

            <label for="localizacao">Localização Inicial:</label>
            <select id="localizacao" required>
                </select>
            
            <label for="status">Status:</label>
            <select id="status" required>
                <option value="Em Uso">Em Uso</option>
                <option value="Estoque" selected>Estoque</option>
                <option value="Manutenção">Manutenção</option>
                <option value="Baixado">Baixado</option>
            </select>

            <label for="obs">Observações:</label>
            <textarea id="obs" rows="3"></textarea>

            <button type="submit" class="btn-principal">Cadastrar Equipamento</button>
        </form>
    </div>

    <div class="container" id="secaoHistorico" style="max-width: 900px;">
        <h2>Visualização do Histórico de Equipamentos</h2>
        <table id="tabelaHistorico">
            <thead>
                <tr>
                    <th>Nome</th>
                    <th>Tombamento</th>
                    <th>Status</th>
                    <th>Localização Atual</th>
                    <th>Última Atualização</th> 
                </tr>
            </thead>
            <tbody>
                </tbody>
        </table>
    </div>
    
    <div class="container" id="secaoGerenciar" style="max-width: 900px;">
        <h2>Gerenciar e Realizar Ações (Editar, Devolver, etc.)</h2>
        
        <div style="display: flex; gap: 10px; margin-bottom: 20px;">
            <input type="text" id="patrimonioBusca" placeholder="Pesquisar por Nº de Tombamento/Série..." style="flex-grow: 1; margin-top: 0;">
            <button type="button" class="btn-principal" onclick="iniciarBuscaEquipamentos()" style="width: 150px; margin-top: 0;">Pesquisar</button>
            <button type="button" class="btn-acao btn-limpar-busca" onclick="limparBuscaEquipamentos()" style="width: 100px; margin-top: 0;">Limpar</button>
        </div>

        <table id="tabelaGerenciar">
            <thead>
                <tr>
                    <th>Nome</th>
                    <th>Tombamento</th>
                    <th>Status</th>
                    <th>Ações</th>
                </tr>
            </thead>
            <tbody>
                </tbody>
        </table>
    </div>

    <div class="container" id="secaoEmprestimo" style="max-width: 600px;">
        <h2>Registrar Empréstimo</h2>
        <form id="emprestimoForm">
            <label for="emprestimo_nome">Nome Completo do Funcionário:</label>
            <input type="text" id="emprestimo_nome" required placeholder="Ex: Maria da Silva">

            <label for="emprestimo_matricula">Matrícula do Funcionário:</label>
            <input type="text" id="emprestimo_matricula" required placeholder="Ex: 12345">
            
            <label for="emprestimo_ocupacao">Cargo/Ocupação do Funcionário:</label>
            <input type="text" id="emprestimo_ocupacao" required placeholder="Ex: Analista Financeiro">

            <label for="emprestimo_tombamento">Nº de Tombamento do Equipamento:</label>
            <input type="text" id="emprestimo_tombamento" required placeholder="Digite o Tombamento (PATR-00123)">

            <label>Data e Hora do Empréstimo:</label>
            <input type="text" id="emprestimo_datahora" readonly style="background-color: #f8f9fa;">

            <label for="emprestimo_previsao">Previsão de Devolução (Apenas Data):</label>
            <input type="date" id="emprestimo_previsao" required>

            <button type="submit" class="btn-principal">Registrar e Imprimir Termo</button>
        </form>
    </div>
    
    <div class="container" id="secaoManutencao" style="max-width: 800px;">
        <h2>Registrar Saída de Equipamentos para Manutenção</h2>
        <form id="manutencaoForm">
            <label for="manutencao_fornecedor">Fornecedor / Técnico Responsável:</label>
            <input type="text" id="manutencao_fornecedor" required placeholder="Ex: TecService Ltda.">
            
            <label for="manutencao_previsao">Previsão de Retorno (Apenas Data):</label>
            <input type="date" id="manutencao_previsao" required>
            
            <hr style="margin: 25px 0;">
            <h3>Adicionar Equipamento(s) à Ordem</h3>
            
            <label for="manutencao_descricao_item">Descrição Específica do Problema/Serviço *</label>
            <textarea id="manutencao_descricao_item" rows="2" required placeholder="Ex: Reparo de tela touch e substituição da porta USB."></textarea>

            <label for="manutencao_tombamento_item">Nº de Tombamento do Equipamento *</label>
            <div style="display: flex; gap: 10px;">
                <input type="text" id="manutencao_tombamento_item" required placeholder="Digite o Tombamento (PATR-00123)" style="flex-grow: 1;">
                <button type="button" class="btn-principal" onclick="adicionarEquipamentoManutencao()" style="width: 150px; margin-top: 5px;">Adicionar</button>
            </div>

            <h4 style="margin-top: 20px;">Lista de Equipamentos nesta Ordem:</h4>
            <table id="tabelaItensManutencao" style="margin-top: 10px;">
                <thead>
                    <tr>
                        <th>Tombamento</th>
                        <th>Nome</th>
                        <th>Serviço/Problema</th>
                        <th>Ação</th>
                    </tr>
                </thead>
                <tbody>
                    </tbody>
            </table>

            <button type="submit" class="btn-principal" style="width: 100%; margin-top: 30px;" id="btnFinalizarManutencao" disabled>Registrar Saída e Imprimir Ordem</button>
        </form>
    </div>
    
    <div class="container" id="secaoOrdensManutencao" style="max-width: 900px;">
        <h2>Ordens de Saída para Manutenção Registradas</h2>
        <table id="tabelaOrdensManutencao">
            <thead>
                <tr>
                    <th>Ordem Nº</th>
                    <th>Data Saída</th>
                    <th>Fornecedor</th>
                    <th>Total Itens</th>
                    <th>Previsão Retorno</th>
                    <th>Status Ordem</th>
                    <th>Ações</th>
                </tr>
            </thead>
            <tbody>
                </tbody>
        </table>
    </div>

    <div id="editModal" class="modal">
        <div class="modal-content">
            <span class="close" onclick="fecharModal()">&times;</span>
            <h2>Editar Equipamento</h2>
            <form id="editForm">
                <input type="hidden" id="editId">
                
                <label for="editNome">Nome:</label>
                <select id="editNome" required>
                    </select>
                
                <label for="editPatrimonio">Tombamento:</label>
                <input type="text" id="editPatrimonio" required>
                
                <label for="editLocalizacao">Localização:</label>
                <select id="editLocalizacao" required>
                    </select>
                
                <label for="editStatus">Status:</label>
                <select id="editStatus" required>
                    <option value="Em Uso">Em Uso</option>
                    <option value="Estoque">Estoque</option>
                    <option value="Manutenção">Manutenção</option>
                    <option value="Baixado">Baixado</option>
                    <option value="Emprestado">Emprestado</option>
                </select>

                <label for="editObs">Observações:</label>
                <textarea id="editObs" rows="3"></textarea>

                <button type="submit" class="btn-principal">Salvar Alterações</button>
            </form>
        </div>
    </div>
    
    <div id="editOrdemManutencaoModal" class="modal">
        <div class="modal-content" style="max-width: 600px;">
            <span class="close" onclick="fecharModalOrdemManutencao()">&times;</span>
            <h2>Visualizar/Editar Ordem de Manutenção</h2>
            <form id="editOrdemManutencaoForm">
                <input type="hidden" id="editOrdemId">
                
                <label for="editFornecedor">Fornecedor / Técnico Responsável:</label>
                <input type="text" id="editFornecedor" required>
                
                <label for="editPrevisao">Previsão de Retorno (Data):</label>
                <input type="date" id="editPrevisao" required>
                
                <label for="editStatusOrdem">Status da Ordem:</label>
                <select id="editStatusOrdem" required>
                    <option value="Em Andamento">Em Andamento</option>
                    <option value="Finalizada">Finalizada (Retornou)</option>
                    <option value="Cancelada">Cancelada</option>
                </select>
                
                <hr>
                <h4 style="color: #007bff;">Discriminação dos Serviços por Equipamento (Editável)</h4>
                <div id="itensDescricaoVisualizacao">
                    </div>
                

                <button type="submit" class="btn-principal">Salvar Alterações da Ordem</button>
            </form>
        </div>
    </div>


    <script>
        // Variável de controle global para o modal de edição
        let equipamentoSendoEditado = null; 
        // Variável temporária para armazenar itens antes de submeter o formulário de manutenção
        let itensManutencaoTemp = []; 
        
        // --- Listas de Seleção Personalizadas ---
        const listaNomesEquipamentos = [
            'Not Gamer Dell', 'Not Book Dell', 'Not Book Dell Vastro', 'Data show', 
            'Mini Pc Dell', 'Oculos VR Meta', 'Impressora 3D', 'Impressora Laser',
            'Pc Gabinete Positivo', 'Monitor Positivo', 'Monitor Dell', 'Not Book HP',
            'Crome Book', 'Smart TV'
        ];
        
        const listaLocalizacoes = [
            'Biblioteca', 'Sala Maker', 'Sala Nova', 'Sala 01', 'Sala 02', 'Sala 03', 
            'Sala 04', 'Sala 05', 'Sala 06', 'Sala 07', 'Sala 08', 'Sala 09', 'Sala 10', 
            'Sala 11', 'Sala 12', 'Sala Financeiro', 'Secretaria', 'CAS (Recepção)', 
            'Copa', 'Gerência', 'Coordenação', 'Sala Dos professores', 'Sala Maker Nova', 
            'Sala de Inovação', 'Cozinha Didática', 'Auditório', 'Sala do Administrativo', 
            'Sala de Vidro', 'Salão Escola', 'Estoque Principal' 
        ];
        
        // --- Funções Auxiliares de População de Select ---
        function populateSelect(selectId, optionsList, selectedValue = null) {
            const select = document.getElementById(selectId);
            if (!select) return;
            select.innerHTML = '';
            
            const defaultOption = document.createElement('option');
            defaultOption.value = '';
            defaultOption.textContent = '-- Selecione --';
            select.appendChild(defaultOption);

            optionsList.forEach(optionText => {
                const option = document.createElement('option');
                option.value = optionText;
                option.textContent = optionText;
                if (optionText === selectedValue) {
                    option.selected = true;
                }
                select.appendChild(option);
            });
        }
        
        // --- Funções de Persistência (LocalStorage) ---

        function getEquipamentos() {
            const equipamentosString = localStorage.getItem('equipamentos');
            return equipamentosString ? JSON.parse(equipamentosString) : [];
        }
        function saveEquipamentos(equipamentos) {
            localStorage.setItem('equipamentos', JSON.stringify(equipamentos));
        }
        
        function getEmprestimos() {
            const emprestimosString = localStorage.getItem('emprestimos');
            return emprestimosString ? JSON.parse(emprestimosString) : [];
        }
        function saveEmprestimos(emprestimos) {
            localStorage.setItem('emprestimos', JSON.stringify(emprestimos));
        }
        
        function getOrdensManutencao() {
            const ordensString = localStorage.getItem('ordensManutencao');
            return ordensString ? JSON.parse(ordensString) : [];
        }
        function saveOrdensManutencao(ordens) {
            localStorage.setItem('ordensManutencao', JSON.stringify(ordens));
        }

        // --- Função de Seeding (Pré-carregamento de dados) ---
        function seedInitialData() {
            let equipamentos = getEquipamentos();
            let ordens = getOrdensManutencao();
            const dataAtual = new Date().toLocaleString('pt-BR');

            // ID CONSTANTE para a Ordem inicial, para evitar duplicação em seeds subsequentes
            const SEED_ORDER_ID = 99999; 
            const ID_A_REMOVER = 1760635664747; // Ordem a ser removida conforme solicitação do usuário.

            // 1. REMOVE A ORDEM SOLICITADA PELO USUÁRIO
            const ordemRemovida = ordens.find(o => o.id === ID_A_REMOVER);
            ordens = ordens.filter(o => o.id !== ID_A_REMOVER);
            
            // 2. ATUALIZA STATUS DOS EQUIPAMENTOS QUE ESTAVAM NA ORDEM REMOVIDA
            if (ordemRemovida) {
                 ordemRemovida.itens.forEach(itemRemovido => {
                     const equipamento = equipamentos.find(e => e.patrimonio === itemRemovido.patrimonio);
                     if (equipamento) {
                          // Verifica se o equipamento não está em nenhuma outra ordem "Em Andamento"
                          const estaEmOutraOrdemAtiva = ordens.some(o => o.status === 'Em Andamento' && o.itens.some(item => item.patrimonio === equipamento.patrimonio));
                          
                          if (!estaEmOutraOrdemAtiva && equipamento.status === 'Manutenção') {
                              // Se não está, volta para o estado anterior/Estoque
                              equipamento.status = equipamento.localizacaoAnterior || 'Estoque'; 
                              equipamento.localizacao = equipamento.localizacaoAnterior || 'Estoque Principal';
                              equipamento.dataCadastro = dataAtual; 
                          }
                     }
                 });
                 saveEquipamentos(equipamentos);
            }
            // FIM DA LÓGICA DE REMOÇÃO ESPECÍFICA
            
            const ordemJaExiste = ordens.some(o => o.id === SEED_ORDER_ID);

            if (ordemJaExiste) {
                saveOrdensManutencao(ordens); // Salva as ordens após a remoção/filtro
                return; // Se a ordem inicial já existe, não refaz o seed.
            }
            
            // Lista de equipamentos a serem semeados (Incluindo o novo 59986)
            const itensParaSeed = [
                { patrimonio: '60802', nome: 'Not Gamer Dell', localizacaoInicial: 'Sala Maker', descricaoServico: 'Carcaça Danificada solicito reparo podendo danificar o Display' },
                { patrimonio: '61009', nome: 'Not Gamer Dell', localizacaoInicial: 'Sala Maker', descricaoServico: 'Carcaça Danificada solicito reparo podendo danificar o Display' },
                { patrimonio: '59986', nome: 'Not Book Dell', localizacaoInicial: 'Sala Meker', descricaoServico: 'solicito Formatação ADM' } // NOVO ITEM (59986)
            ];
            
            const fornecedor = 'Senac-Recife GTI'; 
            const previsaoRetornoData = '2025-10-30'; // Data solicitada
            let ordemItens = [];
            
            // 1. Processa os itens e cadastra os equipamentos se não existirem
            itensParaSeed.forEach(itemSeed => {
                const patrimonio = itemSeed.patrimonio;
                let equipamentoId;
                
                let equipamentoExistente = equipamentos.find(e => e.patrimonio === patrimonio);
                
                if (!equipamentoExistente) {
                    // Cria ID único (simulando, pois Date.now() pode ser o mesmo)
                    // Garantir que os IDs sejam únicos para o find funcionar
                    equipamentoId = Date.now() + parseInt(patrimonio); 
                    
                    const novoEquipamento = {
                        id: equipamentoId,
                        nome: itemSeed.nome, 
                        patrimonio: patrimonio,
                        localizacao: `Saída para ${fornecedor}`,
                        status: 'Manutenção',
                        obs: `Saída para Manutenção (OS: ${fornecedor}). Detalhe: ${itemSeed.descricaoServico}.`,
                        dataCadastro: dataAtual,
                        localizacaoAnterior: itemSeed.localizacaoInicial
                    };
                    equipamentos.push(novoEquipamento);
                    
                } else {
                    equipamentoId = equipamentoExistente.id;
                    // Garante que o equipamento existente tenha o status e localização corretos para a Ordem
                    equipamentoExistente.status = 'Manutenção';
                    equipamentoExistente.localizacao = `Saída para ${fornecedor}`;
                }
                
                // Adiciona o item à lista da Ordem de Manutenção
                ordemItens.push({
                    equipamentoId: equipamentoId,
                    patrimonio: patrimonio,
                    nome: itemSeed.nome,
                    localizacaoAnterior: itemSeed.localizacaoInicial,
                    descricaoItem: itemSeed.descricaoServico,
                    statusRetorno: null
                });
            });
            
            // 2. Cria a nova ordem de manutenção com os três itens
            const novaOrdem = {
                id: SEED_ORDER_ID, // Usando o ID constante
                dataSaida: dataAtual,
                previsaoRetorno: previsaoRetornoData, 
                fornecedor: fornecedor, 
                status: 'Em Andamento',
                itens: ordemItens
            };
            ordens.push(novaOrdem);
            
            saveOrdensManutencao(ordens);
            saveEquipamentos(equipamentos);
        }
        // --- Fim Função de Seeding ---


        // --- Função de Navegação ---
        function mudarSecao(secao) {
            // Esconde todas as seções e remove a classe 'active'
            document.getElementById('secaoCadastro').style.display = 'none';
            document.getElementById('secaoHistorico').style.display = 'none';
            document.getElementById('secaoGerenciar').style.display = 'none';
            document.getElementById('secaoEmprestimo').style.display = 'none';
            document.getElementById('secaoManutencao').style.display = 'none'; 
            document.getElementById('secaoOrdensManutencao').style.display = 'none'; 
            document.querySelectorAll('.nav-button').forEach(btn => btn.classList.remove('active'));

            // Exibe a seção solicitada
            if (secao === 'cadastro') {
                document.getElementById('secaoCadastro').style.display = 'block';
                document.getElementById('btnCadastro').classList.add('active');
                populateSelect('nome', listaNomesEquipamentos);
                populateSelect('localizacao', listaLocalizacoes);
                document.getElementById('status').value = 'Estoque';
            } else if (secao === 'historico') {
                document.getElementById('secaoHistorico').style.display = 'block';
                document.getElementById('btnHistorico').classList.add('active');
                carregarTabelaHistorico(); 
            } else if (secao === 'gerenciar') {
                document.getElementById('secaoGerenciar').style.display = 'block';
                document.getElementById('btnGerenciar').classList.add('active');
                document.getElementById('patrimonioBusca').value = ''; 
                carregarTabelaGerenciar(); 
            } else if (secao === 'emprestimo') {
                document.getElementById('secaoEmprestimo').style.display = 'block';
                document.getElementById('btnEmprestimo').classList.add('active');
                document.getElementById('emprestimo_datahora').value = new Date().toLocaleString('pt-BR');
            } else if (secao === 'manutencao') {
                document.getElementById('secaoManutencao').style.display = 'block';
                document.getElementById('btnManutencao').classList.add('active');
                itensManutencaoTemp = []; 
                atualizarTabelaItensManutencao();
                document.getElementById('manutencaoForm').reset();
            } else if (secao === 'ordensManutencao') {
                document.getElementById('secaoOrdensManutencao').style.display = 'block';
                document.getElementById('btnOrdensManutencao').classList.add('active');
                carregarTabelaOrdensManutencao();
            }
        }
        
        // Função auxiliar para aplicar cores de status
        function getStatusHtml(status) {
            let statusClass = '';
            switch (status) {
                case 'Estoque': statusClass = 'status-estoque'; break;
                case 'Emprestado': statusClass = 'status-emprestado'; break;
                case 'Manutenção': statusClass = 'status-manutencao'; break;
                case 'Baixado': statusClass = 'status-baixas'; break;
                case 'Em Uso': statusClass = 'status-emuso'; break;
                case 'Em Andamento': statusClass = 'status-em-andamento'; break;
                case 'Finalizada': statusClass = 'status-finalizada'; break;
                case 'Cancelada': statusClass = 'status-cancelada'; break;
                default: statusClass = 'status-baixas';
            }
            return `<span class="status-cell ${statusClass}">${status}</span>`;
        }

        // --- FUNÇÃO AUXILIAR PARA PARSEAR DATAS COM HORAS ---
        const parseLocalToDate = (localString) => {
            if (!localString) return new Date(0); 
            
            const parts = localString.split(' ');
            const datePart = parts[0];
            const timePart = parts[1] || '00:00:00'; 

            const [day, month, year] = datePart.split('/').map(Number);
            const [hour, minute, second] = timePart.split(':').map(Number);

            return new Date(year, month - 1, day, hour, minute, second);
        };

        // --- Lógica das Tabelas (Histórico e Gerenciar) ---
        function carregarTabelaHistorico() {
            const equipamentos = getEquipamentos();
            const emprestimos = getEmprestimos(); 
            const ordens = getOrdensManutencao(); 
            const tbody = document.querySelector('#tabelaHistorico tbody');
            if (!tbody) return; 

            tbody.innerHTML = ''; 

            equipamentos.forEach(equipamento => {
                const row = tbody.insertCell();
                
                // 1. Encontrar a Última Movimentação (com hora)
                const movimentos = emprestimos.filter(e => e.tombamento === equipamento.patrimonio);
                const movimentosManutencao = ordens.flatMap(o => o.itens.filter(i => i.patrimonio === equipamento.patrimonio).map(i => ({ dataSaida: o.dataSaida, id: o.id, dataRetorno: i.dataRetorno }))); 

                let dataUltimaAtualizacao = equipamento.dataCadastro;
                let ultimaDataEmMilisegundos = parseLocalToDate(equipamento.dataCadastro).getTime();

                if (movimentos.length > 0) {
                    movimentos.forEach(mov => {
                        if (mov.dataEmprestimo) {
                            const dataMovimento = parseLocalToDate(mov.dataEmprestimo);
                            if (dataMovimento.getTime() > ultimaDataEmMilisegundos) {
                                ultimaDataEmMilisegundos = dataMovimento.getTime();
                                dataUltimaAtualizacao = mov.dataEmprestimo;
                            }
                        }
                        if (mov.dataDevolucao) {
                            const dataMovimento = parseLocalToDate(mov.dataDevolucao);
                            if (dataMovimento.getTime() > ultimaDataEmMilisegundos) {
                                ultimaDataEmMilisegundos = dataMovimento.getTime();
                                dataUltimaAtualizacao = mov.dataDevolucao;
                            }
                        }
                    });
                }
                
                if (movimentosManutencao.length > 0) {
                     movimentosManutencao.forEach(mov => {
                        if (mov.dataSaida) {
                            const dataMovimento = parseLocalToDate(mov.dataSaida);
                            if (dataMovimento.getTime() > ultimaDataEmMilisegundos) {
                                ultimaDataEmMilisegundos = dataMovimento.getTime();
                                dataUltimaAtualizacao = mov.dataSaida;
                            }
                        }
                        if (mov.dataRetorno) {
                            const dataMovimento = parseLocalToDate(mov.dataRetorno);
                            if (dataMovimento.getTime() > ultimaDataEmMilisegundos) {
                                ultimaDataEmMilisegundos = dataMovimento.getTime();
                                dataUltimaAtualizacao = mov.dataRetorno;
                            }
                        }
                    });
                }
                
                // 2. Cria as Células da Tabela
                row.insertCell().textContent = equipamento.nome;
                row.insertCell().textContent = equipamento.patrimonio;
                row.insertCell().innerHTML = getStatusHtml(equipamento.status);
                row.insertCell().textContent = equipamento.localizacao;
                row.insertCell().textContent = dataUltimaAtualizacao; 
            });
        }
        
        /**
         * Carrega a tabela de gerenciamento, permitindo filtragem por tombamento.
         * @param {string} filtroTombamento - O termo de busca para filtrar por tombamento.
         */
        function carregarTabelaGerenciar(filtroTombamento = '') {
            let equipamentos = getEquipamentos();
            const tbody = document.querySelector('#tabelaGerenciar tbody');
            if (!tbody) return; 

            // Filtro por Tombamento (Case-insensitive)
            if (filtroTombamento) {
                equipamentos = equipamentos.filter(e => 
                    e.patrimonio.toUpperCase().includes(filtroTombamento.toUpperCase())
                );
            }
            
            tbody.innerHTML = ''; 

            equipamentos.forEach(equipamento => {
                const row = tbody.insertRow();
                
                row.insertCell().textContent = equipamento.nome;
                row.insertCell().textContent = equipamento.patrimonio;
                row.insertCell().innerHTML = getStatusHtml(equipamento.status);
                
                const acoesCell = row.insertCell();
                
                let acoesHtml = `
                    <button class="btn-acao btn-editar" onclick="abrirModalEdicao(${equipamento.id})">Editar</button>
                    <button class="btn-acao btn-excluir" onclick="excluirEquipamento(${equipamento.id})">Excluir</button>
                `;

                if (equipamento.status === 'Emprestado') {
                    acoesHtml += `
                        <button class="btn-acao btn-devolver" onclick="devolverEquipamento('${equipamento.patrimonio}', ${equipamento.id})">Devolver</button>
                        <button class="btn-acao btn-reimprimir" onclick="reimprimirTermo('${equipamento.patrimonio}')">Reimprimir Termo</button>
                    `;
                } else if (equipamento.status === 'Estoque' || equipamento.status === 'Em Uso') {
                    acoesHtml += `<button class="btn-acao btn-emprestar" onclick="mudarSecao('emprestimo'); document.getElementById('emprestimo_tombamento').value = '${equipamento.patrimonio}';">Emprestar</button>`;
                    acoesHtml += `<button class="btn-acao btn-emprestar" style="background-color: #007bff;" onclick="mudarSecao('manutencao'); document.getElementById('manutencao_tombamento_item').value = '${equipamento.patrimonio}';">Manutenção</button>`;
                } else if (equipamento.status === 'Manutenção') {
                     acoesHtml += `<button class="btn-acao btn-devolver" onclick="retornoManutencao('${equipamento.patrimonio}', ${equipamento.id})">Receber Retorno</button>`;
                }
                
                acoesCell.innerHTML = acoesHtml;
            });
        }
        
        // --- Lógica da Pesquisa ---
        window.iniciarBuscaEquipamentos = function() {
            const termo = document.getElementById('patrimonioBusca').value.trim();
            carregarTabelaGerenciar(termo);
        }
        
        window.limparBuscaEquipamentos = function() {
            document.getElementById('patrimonioBusca').value = '';
            carregarTabelaGerenciar(); 
        }

        // --- Lógica da Seção de Cadastro ---
        const cadastroForm = document.getElementById('cadastroForm');
        if (cadastroForm) {
            cadastroForm.addEventListener('submit', function(event) {
                event.preventDefault();

                const patrimonio = document.getElementById('patrimonio').value.trim();
                const equipamentos = getEquipamentos();
                
                if (equipamentos.some(e => e.patrimonio === patrimonio)) {
                    alert(`ERRO: O Nº de Tombamento/Série "${patrimonio}" já está cadastrado.`);
                    return;
                }

                const novoEquipamento = {
                    id: Date.now(),
                    nome: document.getElementById('nome').value, 
                    patrimonio: patrimonio,
                    localizacao: document.getElementById('localizacao').value, 
                    status: document.getElementById('status').value,
                    obs: document.getElementById('obs').value.trim(),
                    dataCadastro: new Date().toLocaleString('pt-BR') 
                };

                equipamentos.push(novoEquipamento);
                saveEquipamentos(equipamentos);

                alert(`Equipamento "${novoEquipamento.nome}" cadastrado com sucesso!`);
                cadastroForm.reset();
                mudarSecao('cadastro'); 
            });
        }
        
        // --- Lógica da Seção de Empréstimo (Registro) ---
        
        const emprestimoForm = document.getElementById('emprestimoForm');
        if (emprestimoForm) {
            emprestimoForm.addEventListener('submit', function(event) {
                event.preventDefault();

                const tombamento = document.getElementById('emprestimo_tombamento').value.trim();
                const nomeFuncionario = document.getElementById('emprestimo_nome').value.trim();
                const matricula = document.getElementById('emprestimo_matricula').value.trim();
                const ocupacao = document.getElementById('emprestimo_ocupacao').value.trim();
                const dataHora = document.getElementById('emprestimo_datahora').value; 
                const previsaoDevolucao = document.getElementById('emprestimo_previsao').value;
                
                let equipamentos = getEquipamentos();
                let equipamento = equipamentos.find(e => e.patrimonio === tombamento);

                if (!equipamento) {
                    alert(`ERRO: Equipamento com tombamento "${tombamento}" não encontrado.`);
                    return;
                }
                if (equipamento.status === 'Emprestado') {
                    alert(`ERRO: O equipamento "${equipamento.nome}" já se encontra emprestado.`);
                    return;
                }
                if (equipamento.status === 'Manutenção' || equipamento.status === 'Baixado') {
                    alert(`ERRO: O equipamento "${equipamento.nome}" está indisponível (Status: ${equipamento.status}).`);
                    return;
                }
                
                // 1. Atualiza o status do Equipamento
                equipamento.status = 'Emprestado';
                equipamento.localizacao = `Empréstimo: ${nomeFuncionario}`;
                equipamento.dataCadastro = dataHora;
                saveEquipamentos(equipamentos);

                // 2. Cria e salva o registro de Empréstimo
                const novoEmprestimo = {
                    id: Date.now(),
                    equipamentoId: equipamento.id,
                    tombamento: tombamento,
                    nome: equipamento.nome,
                    funcionario: nomeFuncionario,
                    matricula: matricula,
                    ocupacao: ocupacao,
                    dataEmprestimo: dataHora,
                    previsaoDevolucao: previsaoDevolucao,
                    status: 'Ativo'
                };
                
                const emprestimos = getEmprestimos();
                emprestimos.push(novoEmprestimo);
                saveEmprestimos(emprestimos);

                // 3. Imprime e finaliza
                gerarImpressao(novoEmprestimo);
                
                alert(`Empréstimo do equipamento ${equipamento.nome} para ${nomeFuncionario} registrado e impresso!`);
                emprestimoForm.reset();
                document.getElementById('emprestimo_datahora').value = new Date().toLocaleString('pt-BR');
                
                carregarTabelaGerenciar();
                carregarTabelaHistorico();
                mudarSecao('gerenciar');
            });
        }
        
        // --- Funções de Devolução / Retorno ---
        window.devolverEquipamento = function(patrimonio, id) {
             if (!confirm(`Confirmar devolução do equipamento Tombamento: ${patrimonio}?`)) return;

             let equipamentos = getEquipamentos();
             let equipamento = equipamentos.find(e => e.id === id);
             
             if (equipamento) {
                 const dataHoraDevolucao = new Date().toLocaleString('pt-BR');
                 
                 equipamento.status = 'Estoque';
                 equipamento.localizacao = 'Estoque Principal';
                 equipamento.dataCadastro = dataHoraDevolucao; 
                 
                 saveEquipamentos(equipamentos);
                 
                 let emprestimos = getEmprestimos();
                 const emprestimoIndex = emprestimos.slice().reverse().findIndex(e => e.tombamento === patrimonio && e.status === 'Ativo');
                 
                 if (emprestimoIndex !== -1) {
                     const indexOriginal = emprestimos.length - 1 - emprestimoIndex;
                     emprestimos[indexOriginal].status = 'Finalizado';
                     emprestimos[indexOriginal].dataDevolucao = dataHoraDevolucao; 
                     saveEmprestimos(emprestimos);
                 }


                 alert(`Devolução do equipamento ${patrimonio} registrada. Status atualizado para ESTOQUE.`);
                 carregarTabelaGerenciar();
                 carregarTabelaHistorico(); 
             }
        }
        
        window.retornoManutencao = function(patrimonio, id) {
             if (!confirm(`Confirmar o retorno da manutenção para o equipamento Tombamento: ${patrimonio}?`)) return;

             let equipamentos = getEquipamentos();
             let equipamento = equipamentos.find(e => e.id === id);
             
             if (equipamento) {
                 const dataHoraRetorno = new Date().toLocaleString('pt-BR');
                 
                 equipamento.status = 'Estoque';
                 equipamento.localizacao = 'Estoque Principal';
                 equipamento.dataCadastro = dataHoraRetorno; 
                 
                 saveEquipamentos(equipamentos);
                 
                 let ordens = getOrdensManutencao();
                 for (let i = ordens.length - 1; i >= 0; i--) {
                     const ordem = ordens[i];
                     if (ordem.status === 'Em Andamento') {
                         const itemIndex = ordem.itens.findIndex(item => item.patrimonio === patrimonio);
                         if (itemIndex !== -1) {
                             ordem.itens[itemIndex].statusRetorno = 'Retornado';
                             ordem.itens[itemIndex].dataRetorno = dataHoraRetorno;
                             
                             const todosRetornados = ordem.itens.every(item => item.statusRetorno === 'Retornado');
                             if (todosRetornados) {
                                 ordem.status = 'Finalizada';
                             }
                             
                             saveOrdensManutencao(ordens);
                             break;
                         }
                     }
                 }
                 
                 alert(`Retorno do equipamento ${patrimonio} da manutenção registrado. Status atualizado para ESTOQUE.`);
                 carregarTabelaGerenciar();
                 carregarTabelaHistorico(); 
                 carregarTabelaOrdensManutencao();
             }
        }


        // --- Lógica do Modal de Edição de Equipamento ---
        const editModal = document.getElementById('editModal');
        const editForm = document.getElementById('editForm');
        
        window.abrirModalEdicao = function(id) {
            const equipamentos = getEquipamentos();
            equipamentoSendoEditado = equipamentos.find(e => e.id === id);

            if (equipamentoSendoEditado) {
                document.getElementById('editId').value = equipamentoSendoEditado.id;
                
                populateSelect('editNome', listaNomesEquipamentos, equipamentoSendoEditado.nome);
                populateSelect('editLocalizacao', listaLocalizacoes, equipamentoSendoEditado.localizacao);
                
                document.getElementById('editPatrimonio').value = equipamentoSendoEditado.patrimonio;
                document.getElementById('editStatus').value = equipamentoSendoEditado.status;
                document.getElementById('editObs').value = equipamentoSendoEditado.obs;
                
                editModal.style.display = 'block';
            }
        }

        window.fecharModal = function() {
            editModal.style.display = 'none';
        }

        if (editForm) {
            editForm.addEventListener('submit', function(event) {
                event.preventDefault();

                if (equipamentoSendoEditado) {
                    
                    equipamentoSendoEditado.nome = document.getElementById('editNome').value;
                    equipamentoSendoEditado.patrimonio = document.getElementById('editPatrimonio').value.trim();
                    equipamentoSendoEditado.localizacao = document.getElementById('editLocalizacao').value;
                    equipamentoSendoEditado.status = document.getElementById('editStatus').value;
                    equipamentoSendoEditado.obs = document.getElementById('editObs').value.trim();

                    equipamentoSendoEditado.dataCadastro = new Date().toLocaleString('pt-BR'); 
                    
                    const equipamentos = getEquipamentos();
                    const index = equipamentos.findIndex(e => e.id === equipamentoSendoEditado.id);
                    
                    if (index !== -1) {
                        equipamentos[index] = equipamentoSendoEditado;
                        saveEquipamentos(equipamentos);
                        
                        carregarTabelaGerenciar();
                        carregarTabelaHistorico(); 
                        fecharModal();
                        alert('Equipamento atualizado com sucesso!');
                    }
                }
            });
        }

        window.excluirEquipamento = function(id) {
            if (confirm("Tem certeza que deseja excluir este equipamento?")) {
                let equipamentos = getEquipamentos();
                equipamentos = equipamentos.filter(e => e.id !== id); 
                
                saveEquipamentos(equipamentos);
                carregarTabelaGerenciar(); 
                carregarTabelaHistorico(); 
                alert('Equipamento excluído.');
            }
        }
        
        
        // --- Lógica: TABELA DE ORDENS DE MANUTENÇÃO ---
        function carregarTabelaOrdensManutencao() {
            const ordens = getOrdensManutencao();
            const tbody = document.querySelector('#tabelaOrdensManutencao tbody');
            if (!tbody) return;

            tbody.innerHTML = '';

            ordens.slice().reverse().forEach(ordem => { 
                const row = tbody.insertRow();

                const dataSaidaFormatada = ordem.dataSaida.split(' ')[0]; 
                const previsaoFormatada = new Date(ordem.previsaoRetorno + 'T00:00:00').toLocaleDateString('pt-BR');

                row.insertCell().textContent = ordem.id;
                row.insertCell().textContent = dataSaidaFormatada;
                row.insertCell().textContent = ordem.fornecedor;
                row.insertCell().textContent = ordem.itens.length;
                row.insertCell().textContent = previsaoFormatada;
                row.insertCell().innerHTML = getStatusHtml(ordem.status);

                const acoesCell = row.insertCell();
                acoesCell.innerHTML = `
                    <button class="btn-acao btn-visualizar" onclick="abrirModalEdicaoOrdemManutencao(${ordem.id})">Visualizar/Editar</button>
                    <button class="btn-acao btn-reimprimir" onclick="reimprimirOrdemManutencao(${ordem.id})">Reimprimir</button>
                `;
            });
        }
        
        // --- Lógica: MODAL DE EDIÇÃO DE ORDEM DE MANUTENÇÃO ---
        const editOrdemManutencaoModal = document.getElementById('editOrdemManutencaoModal');
        const editOrdemManutencaoForm = document.getElementById('editOrdemManutencaoForm');

        window.fecharModalOrdemManutencao = function() {
            editOrdemManutencaoModal.style.display = 'none';
        }

        window.abrirModalEdicaoOrdemManutencao = function(id) {
            const ordens = getOrdensManutencao();
            const ordem = ordens.find(o => o.id === id);

            if (ordem) {
                document.getElementById('editOrdemId').value = ordem.id;
                document.getElementById('editFornecedor').value = ordem.fornecedor;
                document.getElementById('editPrevisao').value = ordem.previsaoRetorno;
                document.getElementById('editStatusOrdem').value = ordem.status;
                
                const visualizacaoDiv = document.getElementById('itensDescricaoVisualizacao');
                let htmlEdicao = '';
                
                if (ordem.itens.length > 0) {
                    ordem.itens.forEach((item, index) => {
                        htmlEdicao += `
                            <div style="margin-bottom: 20px; padding: 10px; border: 1px solid #e9ecef; border-radius: 4px; background-color: #fff;">
                                <label style="margin-top: 0;">Equipamento:</label>
                                <p style="margin: 5px 0 10px 0; font-weight: bold; color: var(--text-dark);">
                                    [${item.patrimonio}] - ${item.nome}
                                </p>
                                <label for="editDescricaoItem_${index}" style="margin-top: 0;">Descrição do Serviço (Editável):</label>
                                <textarea id="editDescricaoItem_${index}" rows="3" style="font-size: 0.9em; resize: vertical;">${item.descricaoItem}</textarea>
                                <p style="margin-top: 10px; font-size: 0.8em; color: ${item.statusRetorno === 'Retornado' ? '#20c997' : '#dc3545'};">
                                    Status Item: ${item.statusRetorno || 'Aguardando Retorno'}
                                </p>
                            </div>
                        `;
                    });
                } else {
                    htmlEdicao = '<p style="color: #6c757d;">Nenhum item encontrado nesta ordem.</p>';
                }
                visualizacaoDiv.innerHTML = htmlEdicao;
                
                editOrdemManutencaoModal.style.display = 'block';
            } else {
                alert('Ordem de Manutenção não encontrada.');
            }
        }
        
        if (editOrdemManutencaoForm) {
            editOrdemManutencaoForm.addEventListener('submit', function(event) {
                event.preventDefault();

                const id = parseInt(document.getElementById('editOrdemId').value);
                let ordens = getOrdensManutencao();
                const ordemIndex = ordens.findIndex(o => o.id === id);

                if (ordemIndex !== -1) {
                    ordens[ordemIndex].fornecedor = document.getElementById('editFornecedor').value.trim();
                    ordens[ordemIndex].previsaoRetorno = document.getElementById('editPrevisao').value;
                    ordens[ordemIndex].status = document.getElementById('editStatusOrdem').value;
                    
                    // Atualiza a descrição de serviço de cada item
                    ordens[ordemIndex].itens.forEach((item, index) => {
                        const newDescriptionElement = document.getElementById(`editDescricaoItem_${index}`);
                        if (newDescriptionElement) {
                            item.descricaoItem = newDescriptionElement.value.trim();
                        }
                    });

                    saveOrdensManutencao(ordens);
                    carregarTabelaOrdensManutencao();
                    fecharModalOrdemManutencao();
                    alert('Ordem de Manutenção atualizada com sucesso!');
                } else {
                    alert('Erro ao salvar: Ordem de Manutenção não encontrada.');
                }
            });
        }
        
        // --- Lógica da Seção de Manutenção (Adicionar Itens) ---
        
        function atualizarTabelaItensManutencao() {
            const tbody = document.querySelector('#tabelaItensManutencao tbody');
            if (!tbody) return;
            
            tbody.innerHTML = '';
            
            itensManutencaoTemp.forEach((item, index) => {
                const row = tbody.insertRow();
                row.insertCell().textContent = item.patrimonio;
                row.insertCell().textContent = item.nome;
                row.insertCell().textContent = item.descricaoItem.length > 50 ? item.descricaoItem.substring(0, 50) + '...' : item.descricaoItem;
                row.insertCell().innerHTML = `<button class="btn-acao btn-excluir" onclick="removerEquipamentoManutencao(${index})">Remover</button>`;
            });

            const btnFinalizar = document.getElementById('btnFinalizarManutencao');
            if (btnFinalizar) {
                btnFinalizar.disabled = itensManutencaoTemp.length === 0;
            }
        }
        
        window.adicionarEquipamentoManutencao = function() {
            const tombamentoInput = document.getElementById('manutencao_tombamento_item');
            const descricaoItemInput = document.getElementById('manutencao_descricao_item');
            
            const tombamento = tombamentoInput.value.trim();
            const descricaoItem = descricaoItemInput.value.trim(); 
            
            if (!tombamento) {
                alert('Por favor, insira o Nº de Tombamento.');
                return;
            }
            if (!descricaoItem) {
                alert('Por favor, preencha a Descrição Específica do Problema/Serviço.');
                return;
            }

            const equipamentos = getEquipamentos();
            const equipamento = equipamentos.find(e => e.patrimonio === tombamento);
            
            if (!equipamento) {
                alert(`ERRO: Equipamento com tombamento "${tombamento}" não encontrado.`);
                return;
            }
            if (equipamento.status === 'Emprestado') {
                alert(`ERRO: O equipamento "${equipamento.nome}" está emprestado e não pode ir para manutenção.`);
                return;
            }
            if (equipamento.status === 'Manutenção') {
                alert(`ERRO: O equipamento "${equipamento.nome}" já está registrado em manutenção.`);
                return;
            }
            if (itensManutencaoTemp.some(item => item.patrimonio === tombamento)) {
                alert(`ERRO: O equipamento "${equipamento.nome}" já foi adicionado a esta lista.`);
                return;
            }

            itensManutencaoTemp.push({
                equipamentoId: equipamento.id,
                patrimonio: equipamento.patrimonio,
                nome: equipamento.nome,
                localizacaoAnterior: equipamento.localizacao,
                descricaoItem: descricaoItem,
                statusRetorno: null 
            });

            tombamentoInput.value = ''; 
            descricaoItemInput.value = ''; 
            
            atualizarTabelaItensManutencao();
        }

        window.removerEquipamentoManutencao = function(index) {
            itensManutencaoTemp.splice(index, 1);
            atualizarTabelaItensManutencao();
        }
        
        const manutencaoForm = document.getElementById('manutencaoForm');
        if (manutencaoForm) {
            manutencaoForm.addEventListener('submit', function(event) {
                event.preventDefault();

                if (itensManutencaoTemp.length === 0) {
                    alert('ERRO: Adicione pelo menos um equipamento à lista antes de registrar a saída.');
                    return;
                }
                
                const fornecedor = document.getElementById('manutencao_fornecedor').value.trim();
                const previsaoRetorno = document.getElementById('manutencao_previsao').value;
                if (!fornecedor || !previsaoRetorno) {
                     alert('Por favor, preencha o Fornecedor e a Previsão de Retorno.');
                     return;
                }

                const dataHoraSaida = new Date().toLocaleString('pt-BR');
                
                const novaOrdem = {
                    id: Date.now(),
                    dataSaida: dataHoraSaida,
                    previsaoRetorno: previsaoRetorno,
                    fornecedor: fornecedor,
                    status: 'Em Andamento',
                    itens: itensManutencaoTemp 
                };
                
                const ordens = getOrdensManutencao();
                ordens.push(novaOrdem);
                saveOrdensManutencao(ordens);

                let equipamentos = getEquipamentos();
                novaOrdem.itens.forEach(item => {
                    const equipamento = equipamentos.find(e => e.id === item.equipamentoId);
                    if (equipamento) {
                        equipamento.status = 'Manutenção';
                        equipamento.localizacao = `Saída para ${fornecedor}`;
                        equipamento.dataCadastro = dataHoraSaida; 
                    }
                });
                saveEquipamentos(equipamentos);

                gerarImpressaoOrdemManutencao(novaOrdem);
                
                alert(`Ordem de Manutenção nº ${novaOrdem.id} com ${novaOrdem.itens.length} equipamentos registrada com sucesso!`);
                
                manutencaoForm.reset();
                itensManutencaoTemp = []; 
                atualizarTabelaItensManutencao();
                carregarTabelaHistorico(); 
                carregarTabelaGerenciar(); 
                mudarSecao('ordensManutencao'); 
            });
        }

        
        // --- Função de Impressão (Ordem de Manutenção) ---
        window.reimprimirOrdemManutencao = function(id) {
            const ordens = getOrdensManutencao();
            const ordem = ordens.find(o => o.id === id);

            if (ordem) {
                gerarImpressaoOrdemManutencao(ordem);
            } else {
                alert(`Erro: Ordem de Manutenção ID ${id} não encontrada.`);
            }
        };

        function gerarImpressaoOrdemManutencao(dadosOrdem) {
            const dataPrevisaoFormatada = new Date(dadosOrdem.previsaoRetorno + 'T00:00:00').toLocaleDateString('pt-BR');
            
            let itensDescriminadosHtml = '';
            
            dadosOrdem.itens.forEach((item, index) => {
                itensDescriminadosHtml += `
                    <div class="discriminação-servicos" style="margin-bottom: 15px; border: 1px solid #ccc; padding: 8px; border-radius: 4px;">
                        <p style="margin: 0; font-size: 0.95em;"><strong>ITEM ${index + 1}: ${item.nome.toUpperCase()}</strong></p>
                        <p style="margin: 5px 0 10px 0; font-size: 0.85em;">Nº de Tombamento: <strong>${item.patrimonio}</strong> | Localização Anterior: ${item.localizacaoAnterior}</p>
                        <h5 style="margin: 5px 0; border-bottom: 1px dashed #eee; padding-bottom: 3px; font-size: 0.85em;">Discriminação do Serviço:</h5>
                        <p style="white-space: pre-wrap; margin: 0; font-style: italic; font-size: 0.8em;">${item.descricaoItem}</p>
                    </div>
                `;
            });
            
            const termoHtml = `
                <div class="termo-impressao" style="padding: 15px; line-height: 1.5;">
                    <div class="cabecalho-print">SENAC - PAULISTA</div>
                    <h2 style="text-align: center; border-bottom: 2px solid #000; padding-bottom: 5px; color: #000; margin-top: 5px; font-size: 1.1em;">ORDEM DE SAÍDA PARA MANUTENÇÃO</h2>

                    <p style="margin-bottom: 5px; font-size: 0.9em;"><strong>Ordem Nº:</strong> ${dadosOrdem.id}</p>
                    <p style="margin-bottom: 5px; font-size: 0.9em;"><strong>Data e Hora da Saída:</strong> ${dadosOrdem.dataSaida}</p>
                    <p style="margin-bottom: 5px; font-size: 0.9em;"><strong>Previsão de Retorno:</strong> ${dataPrevisaoFormatada}</p>
                    <p style="margin-bottom: 5px; font-size: 0.9em;"><strong>Fornecedor/Técnico:</strong> ${dadosOrdem.fornecedor.toUpperCase()}</p>
                    
                    <h3 style="margin-top: 15px; border-bottom: 2px solid #000; padding-bottom: 5px; font-size: 1em;">DETALHAMENTO DOS SERVIÇOS POR EQUIPAMENTO (${dadosOrdem.itens.length} ITENS)</h3>
                    
                    ${itensDescriminadosHtml}
                    

                    <p style="margin-top: 20px; font-size: 0.85em;">Declaro que os equipamentos acima listados foram liberados para manutenção externa com a finalidade descrita. O retorno deve ser verificado e registrado no sistema.</p>
                    
                    <br>

                    <table style="width: 100%; margin-top: 15px;">
                        <tr>
                            <td style="width: 50%; text-align: center; padding: 30px 0; border-top: 1px solid #000; font-size: 0.85em;">
                                Assinatura do Responsável (SENAC)
                            </td>
                            <td style="width: 50%; text-align: center; padding: 30px 0; border-top: 1px solid #000; font-size: 0.85em;">
                                Assinatura do Fornecedor / Técnico (Retirada)
                            </td>
                        </tr>
                    </table>

                    <p style="text-align: right; margin-top: 10px; font-size: 0.7em;">Emissão: ${dadosOrdem.dataSaida}</p>
                    
                </div>
            `;

            const printWindow = window.open('', '', 'height=700,width=800');
            printWindow.document.write('<html><head><title>Ordem de Manutenção</title>');
            printWindow.document.write('<style>@media print { body{ margin: 0; } .termo-impressao{ font-family: \'Times New Roman\', serif; line-height: 1.5; padding: 15px; } .assinaturas-devolucao{ margin-top: 30px; border-top: 2px solid #000; padding-top: 15px; } .assinaturas-devolucao p { margin: 5px 0; } .cabecalho-print { text-align: center; font-size: 1.0em; font-weight: bold; margin-bottom: 5px; } .discriminação-servicos { page-break-inside: avoid; } /* MARCA D\'ÁGUA */ .termo-impressao::before { content: "SENAC PAULISTA"; position: absolute; top: 50%; left: 50%; transform: translate(-50%, -50%) rotate(-45deg); font-size: 3em; color: rgba(0, 0, 0, 0.08); pointer-events: none; white-space: nowrap; z-index: -1; } }</style>');
            printWindow.document.write('</head><body>');
            printWindow.document.write(termoHtml);
            printWindow.document.write('</body></html>');
            printWindow.document.close();
            
            printWindow.onload = function() {
                printWindow.print();
            };
        }
        
        // --- Função de Reimpressão (Empréstimo) ---
        window.reimprimirTermo = function(tombamento) {
            const emprestimos = getEmprestimos();
            const emprestimoAtual = emprestimos.slice().reverse().find(e => e.tombamento === tombamento && e.status === 'Ativo');

            if (emprestimoAtual) {
                gerarImpressao(emprestimoAtual);
            } else {
                alert(`Erro: Não foi encontrado um registro de empréstimo ATIVO para o tombamento ${tombamento}.`);
            }
        };

        // --- Função de Impressão (Termo de Empréstimo) ---
        function gerarImpressao(dadosEmprestimo) {
            const dataPrevisaoFormatada = new Date(dadosEmprestimo.previsaoDevolucao + 'T00:00:00').toLocaleDateString('pt-BR');
            const dataEmprestimoFormatada = dadosEmprestimo.dataEmprestimo;
            
            const termoHtml = `
                <div class="termo-impressao" style="padding: 30px; line-height: 1.8;">
                    <div class="cabecalho-print">SENAC - PAULISTA</div>
                    <h2 style="text-align: center; border-bottom: 2px solid #000; padding-bottom: 10px; color: #000; margin-top: 5px;">TERMO DE EMPRÉSTIMO DE EQUIPAMENTO</h2>

                    <p>Eu, <strong>${dadosEmprestimo.funcionario.toUpperCase()}</strong>, Matrícula <strong>${dadosEmprestimo.matricula}</strong>, Cargo/Ocupação <strong>${dadosEmprestimo.ocupacao.toUpperCase()}</strong>, declaro ter recebido o seguinte equipamento em regime de empréstimo:</p>
                    
                    <table style="width: 100%; margin: 25px 0; border: 1px solid #000; border-collapse: collapse;">
                        <tr>
                            <th style="border: 1px solid #000; padding: 10px; background-color: #f0f0f0;">Equipamento</th>
                            <th style="border: 1px solid #000; padding: 10px; background-color: #f0f0f0;">Nº de Tombamento</th>
                            <th style="border: 1px solid #000; padding: 10px; background-color: #f0f0f0;">Previsão de Devolução</th>
                        </tr>
                        <tr>
                            <td style="border: 1px solid #000; padding: 10px;">${dadosEmprestimo.nome}</td>
                            <td style="border: 1px solid #000; padding: 10px;">${dadosEmprestimo.tombamento}</td>
                            <td style="border: 1px solid #000; padding: 10px;">${dataPrevisaoFormatada}</td>
                        </tr>
                    </table>

                    <p><strong>Registro de Empréstimo:</strong> O equipamento foi retirado em <strong>${dataEmprestimoFormatada}</strong>.</p>
                    
                    <p style="margin-top: 30px;"><strong>Condições:</strong> Declaro estar ciente das responsabilidades de uso, conservação e devolução do item em perfeitas condições. Em caso de dano, perda ou furto, o funcionário será responsável pela substituição integral do bem.</p>
                    
                    <br><br><br>

                    <table style="width: 100%;">
                        <tr>
                            <td style="width: 50%; text-align: center; padding: 40px 0; border-top: 1px solid #000;">
                                Assinatura do Funcionário (Empréstimo)
                            </td>
                            <td style="width: 50%; text-align: center; padding: 40px 0; border-top: 1px solid #000;">
                                Assinatura do Responsável (TI/Estoque)
                            </td>
                        </tr>
                    </table>

                    <p style="text-align: right; margin-top: 20px; font-size: 0.9em;">Emissão: ${dataEmprestimoFormatada}</p>
                    
                    <br><br>
                    
                    <div class="assinaturas-devolucao">
                        <h3 style="text-align: center; color: #000; margin-bottom: 25px;">REGISTRO DE DEVOLUÇÃO</h3>
                        <p>Declaro que o equipamento foi devolvido na data e hora: _____ / _____ / _________ às ______:______</p>
                        <p>Observações sobre o estado do equipamento (se houver): ____________________________________________________________________</p>
                        <br>
                        <table style="width: 100%;">
                            <tr>
                                <td style="width: 50%; text-align: center; padding: 40px 0; border-top: 1px solid #000;">
                                    Assinatura do Funcionário (Devolução)
                                </td>
                                <td style="width: 50%; text-align: center; padding: 40px 0; border-top: 1px solid #000;">
                                    Assinatura do Responsável (Recebimento)
                                </td>
                            </tr>
                        </table>
                    </div>
                </div>
            `;

            const printWindow = window.open('', '', 'height=700,width=800');
            printWindow.document.write('<html><head><title>Termo de Empréstimo</title>');
            printWindow.document.write('<style>@media print { body{ margin: 0; } .termo-impressao{ font-family: \'Times New Roman\', serif; } .assinaturas-devolucao{ margin-top: 50px; border-top: 2px solid #000; padding-top: 20px; } .assinaturas-devolucao p { margin: 5px 0; } .cabecalho-print { text-align: center; font-size: 1.1em; font-weight: bold; margin-bottom: 10px; } /* MARCA D\'ÁGUA */ .termo-impressao::before { content: "SENAC PAULISTA"; position: absolute; top: 50%; left: 50%; transform: translate(-50%, -50%) rotate(-45deg); font-size: 4em; color: rgba(0, 0, 0, 0.08); pointer-events: none; white-space: nowrap; z-index: -1; } }</style>');
            printWindow.document.write('</head><body>');
            printWindow.document.write(termoHtml);
            printWindow.document.write('</body></html>');
            printWindow.document.close();
            
            printWindow.onload = function() {
                printWindow.print();
            };
        }
        
        // --- Inicialização ---
        document.addEventListener('DOMContentLoaded', () => {
            seedInitialData(); // Pré-carrega o equipamento e a Ordem de Manutenção
            mudarSecao('cadastro');
        });
    </script>

</body>
</html>
