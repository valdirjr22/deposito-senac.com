<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <title>Sistema de Controle de Equipamentos - V5 (Ocupação Adicionada)</title>
    <style>
        /* Estilos Comuns e Reset */
        body { 
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; 
            margin: 0; 
            padding: 0; 
            background-color: #e9ecef; /* Fundo suave */
            color: #343a40;
        }
        .container { 
            background-color: #ffffff; /* Fundo branco para conteúdo */
            padding: 30px; 
            border-radius: 12px; 
            box-shadow: 0 6px 12px rgba(0,0,0,0.1); 
            margin: 30px auto; 
            max-width: 1000px;
        }
        h1 { 
            color: #0056b3; /* Azul mais escuro para cabeçalho principal */
            text-align: center; 
            margin-bottom: 25px; 
            border-bottom: 2px solid #007bff;
            padding-bottom: 10px;
        }
        h2 {
            color: #495057;
            border-bottom: 1px solid #dee2e6;
            padding-bottom: 10px;
        }
        
        /* Estilos de Formulário */
        label { display: block; margin-top: 15px; font-weight: 600; color: #495057; }
        input, select, textarea { 
            width: 100%; padding: 10px; margin-top: 5px; 
            box-sizing: border-box; border: 1px solid #ced4da; 
            border-radius: 6px;
            transition: border-color 0.3s;
        }
        input:focus, select:focus, textarea:focus {
            border-color: #007bff;
            box-shadow: 0 0 0 0.2rem rgba(0, 123, 255, 0.25);
            outline: none;
        }
        
        /* Estilos dos Botões Principais */
        .btn-principal { 
            background-color: #28a745; /* Verde vibrante */
            color: white; padding: 12px 20px; 
            border: none; border-radius: 6px; cursor: pointer; 
            margin-top: 20px; font-size: 16px; 
            transition: background-color 0.3s, transform 0.1s; 
            font-weight: bold;
        }
        .btn-principal:hover { background-color: #1e7e34; transform: translateY(-1px); }

        /* Estilos dos Botões de Navegação (Aba) */
        .nav-bar { 
            display: flex; 
            justify-content: flex-start; 
            margin-bottom: 0;
            border-bottom: 2px solid #dee2e6;
        }
        .nav-button { 
            background-color: #f8f9fa; /* Fundo claro para abas inativas */
            color: #495057; 
            padding: 10px 20px; 
            border: 1px solid #dee2e6; 
            border-bottom: none;
            border-radius: 6px 6px 0 0; 
            cursor: pointer; 
            margin-left: 5px; 
            transition: background-color 0.3s, color 0.3s; 
            font-weight: 600;
        }
        .nav-button:hover:not(.active) { background-color: #e9ecef; }
        .nav-button.active { 
            background-color: #ffffff; /* Fundo branco para a aba ativa */
            color: #007bff; /* Texto azul para a aba ativa */
            border-bottom: 2px solid #ffffff; /* Esconde a linha de baixo */
            margin-bottom: -2px; /* Ajuste para sobrepor a borda */
        }

        /* Estilos da Tabela */
        table { width: 100%; border-collapse: collapse; margin-top: 20px; }
        th, td { border: 1px solid #dee2e6; padding: 12px; text-align: left; font-size: 0.9em; }
        th { background-color: #e9ecef; color: #495057; font-weight: 700; }
        
        /* Estilos dos botões de ação na tabela */
        .btn-acao { 
            padding: 6px 10px; margin: 3px; border: none; 
            border-radius: 4px; cursor: pointer; color: white; 
            font-size: 0.85em; font-weight: 600;
            transition: opacity 0.2s;
        }
        .btn-acao:hover { opacity: 0.8; }
        .btn-editar { background-color: #ffc107; color: #333; } /* Amarelo */
        .btn-excluir { background-color: #dc3545; } /* Vermelho */
        .btn-emprestar { background-color: #007bff; } /* Azul */
        .btn-devolver { background-color: #20c997; } /* Verde Água */

        /* Cores de Status na Tabela */
        .status-cell { font-weight: bold; padding: 5px 10px; border-radius: 4px; display: inline-block; }
        .status-estoque { background-color: #d4edda; color: #155724; border: 1px solid #c3e6cb; } 
        .status-emprestado { background-color: #f8d7da; color: #721c24; border: 1px solid #f5c6cb; } 
        .status-manutencao { background-color: #fff3cd; color: #856404; border: 1px solid #ffeeba; } 
        .status-baixas { background-color: #e2e3e5; color: #495057; border: 1px solid #d6d8db; } 
        .status-emuso { background-color: #d1ecf1; color: #0c5460; border: 1px solid #bee5eb; } 


        /* Estilos para o Modal de Edição (manter o mesmo) */
        .modal { display: none; position: fixed; z-index: 1000; left: 0; top: 0; width: 100%; height: 100%; overflow: auto; background-color: rgba(0,0,0,0.6); }
        .modal-content { background-color: #fefefe; margin: 5% auto; padding: 25px; border: none; box-shadow: 0 5px 15px rgba(0,0,0,0.3); width: 80%; max-width: 550px; border-radius: 8px; }
        .close { color: #aaa; float: right; font-size: 32px; font-weight: bold; }
        .close:hover, .close:focus { color: #333; text-decoration: none; cursor: pointer; }
        #editForm button { width: 100%; margin-top: 15px; }

        /* Esconde as seções que não são a inicial */
        #secaoHistorico, #secaoGerenciar, #secaoEmprestimo { display: none; }
        
        /* Estilos para o Termo de Empréstimo (Impressão) */
        @media print {
            body { background: none; }
            .container, .nav-bar, .modal { display: none !important; }
            .termo-impressao {
                font-family: 'Times New Roman', serif;
                padding: 30px;
                margin: 0;
                line-height: 1.8;
                color: #000;
                display: block !important;
                page-break-after: always;
            }
        }
    </style>
</head>
<body>

    <div class="container" style="padding-bottom: 0; margin-bottom: 0; max-width: 900px;">
        <h1>Controle de Materiais de Informática</h1>

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
        </div>
    </div>

    <div class="container" id="secaoCadastro" style="max-width: 600px;">
        <h2>Cadastrar Novo Equipamento</h2>
        <form id="cadastroForm">
            <label for="nome">Nome do Equipamento:</label>
            <input type="text" id="nome" required placeholder="Ex: Notebook Dell Latitude">

            <label for="patrimonio">Nº de Tombamento/Série (Chave Única):</label>
            <input type="text" id="patrimonio" required placeholder="Ex: PATR-00123 ou Serial XYZ">

            <label for="localizacao">Localização Inicial:</label>
            <input type="text" id="localizacao" required placeholder="Ex: Estoque Principal">
            
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
                </tr>
            </thead>
            <tbody>
                </tbody>
        </table>
    </div>
    
    <div class="container" id="secaoGerenciar" style="max-width: 900px;">
        <h2>Gerenciar e Realizar Ações (Editar, Devolver, etc.)</h2>
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

            <label for="emprestimo_previsao">Previsão de Devolução:</label>
            <input type="date" id="emprestimo_previsao" required>

            <button type="submit" class="btn-principal">Registrar e Imprimir Termo</button>
        </form>
    </div>
    
    <div id="editModal" class="modal">
        <div class="modal-content">
            <span class="close" onclick="fecharModal()">&times;</span>
            <h2>Editar Equipamento</h2>
            <form id="editForm">
                <input type="hidden" id="editId">
                
                <label for="editNome">Nome:</label>
                <input type="text" id="editNome" required>
                
                <label for="editPatrimonio">Tombamento:</label>
                <input type="text" id="editPatrimonio" required>
                
                <label for="editLocalizacao">Localização:</label>
                <input type="text" id="editLocalizacao" required>
                
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


    <script>
        // Variável de controle global para o modal de edição
        let equipamentoSendoEditado = null; 
        
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

        // --- Função de Navegação ---
        function mudarSecao(secao) {
            // Esconde todas as seções e remove a classe 'active'
            document.getElementById('secaoCadastro').style.display = 'none';
            document.getElementById('secaoHistorico').style.display = 'none';
            document.getElementById('secaoGerenciar').style.display = 'none';
            document.getElementById('secaoEmprestimo').style.display = 'none';
            document.querySelectorAll('.nav-button').forEach(btn => btn.classList.remove('active'));

            // Exibe a seção solicitada
            if (secao === 'cadastro') {
                document.getElementById('secaoCadastro').style.display = 'block';
                document.getElementById('btnCadastro').classList.add('active');
            } else if (secao === 'historico') {
                document.getElementById('secaoHistorico').style.display = 'block';
                document.getElementById('btnHistorico').classList.add('active');
                carregarTabelaHistorico(); 
            } else if (secao === 'gerenciar') {
                document.getElementById('secaoGerenciar').style.display = 'block';
                document.getElementById('btnGerenciar').classList.add('active');
                carregarTabelaGerenciar(); 
            } else if (secao === 'emprestimo') {
                document.getElementById('secaoEmprestimo').style.display = 'block';
                document.getElementById('btnEmprestimo').classList.add('active');
                document.getElementById('emprestimo_datahora').value = new Date().toLocaleString('pt-BR');
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
                default: statusClass = 'status-baixas';
            }
            return `<span class="status-cell ${statusClass}">${status}</span>`;
        }

        // --- Lógica da Seção de Histórico (Visualização) ---
        function carregarTabelaHistorico() {
            const equipamentos = getEquipamentos();
            const tbody = document.querySelector('#tabelaHistorico tbody');
            if (!tbody) return; 

            tbody.innerHTML = ''; 

            equipamentos.forEach(equipamento => {
                const row = tbody.insertRow();
                
                row.insertCell().textContent = equipamento.nome;
                row.insertCell().textContent = equipamento.patrimonio;
                row.insertCell().innerHTML = getStatusHtml(equipamento.status);
                row.insertCell().textContent = equipamento.localizacao;
            });
        }
        
        // --- Lógica da Seção de Gerenciamento (Ações/Edição) ---
        function carregarTabelaGerenciar() {
            const equipamentos = getEquipamentos();
            const tbody = document.querySelector('#tabelaGerenciar tbody');
            if (!tbody) return; 

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
                    acoesHtml += `<button class="btn-acao btn-devolver" onclick="devolverEquipamento('${equipamento.patrimonio}', ${equipamento.id})">Devolver</button>`;
                } else if (equipamento.status === 'Estoque' || equipamento.status === 'Em Uso') {
                    acoesHtml += `<button class="btn-acao btn-emprestar" onclick="mudarSecao('emprestimo'); document.getElementById('emprestimo_tombamento').value = '${equipamento.patrimonio}';">Emprestar</button>`;
                }
                
                acoesCell.innerHTML = acoesHtml;
            });
        }

        // --- Lógica da Seção de Cadastro (Não alterada) ---
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
                    nome: document.getElementById('nome').value.trim(),
                    patrimonio: patrimonio,
                    localizacao: document.getElementById('localizacao').value.trim(),
                    status: document.getElementById('status').value,
                    obs: document.getElementById('obs').value.trim(),
                    dataCadastro: new Date().toLocaleDateString('pt-BR')
                };

                equipamentos.push(novoEquipamento);
                saveEquipamentos(equipamentos);

                alert(`Equipamento "${novoEquipamento.nome}" cadastrado com sucesso!`);
                cadastroForm.reset();
            });
        }

        // --- Funções de Devolução (Não alterada) ---
        window.devolverEquipamento = function(patrimonio, id) {
             if (!confirm(`Confirmar devolução do equipamento Tombamento: ${patrimonio}?`)) return;

             let equipamentos = getEquipamentos();
             let equipamento = equipamentos.find(e => e.id === id);
             
             if (equipamento) {
                 equipamento.status = 'Estoque';
                 equipamento.localizacao = 'Estoque Principal';
                 
                 saveEquipamentos(equipamentos);
                 
                 alert(`Devolução do equipamento ${patrimonio} registrada. Status atualizado para ESTOQUE.`);
                 carregarTabelaGerenciar();
             }
        }
        
        // --- Lógica do Modal de Edição/Exclusão (Não alterada) ---
        const editModal = document.getElementById('editModal');
        const editForm = document.getElementById('editForm');
        
        window.abrirModalEdicao = function(id) {
            const equipamentos = getEquipamentos();
            equipamentoSendoEditado = equipamentos.find(e => e.id === id);

            if (equipamentoSendoEditado) {
                document.getElementById('editId').value = equipamentoSendoEditado.id;
                document.getElementById('editNome').value = equipamentoSendoEditado.nome;
                document.getElementById('editPatrimonio').value = equipamentoSendoEditado.patrimonio;
                document.getElementById('editLocalizacao').value = equipamentoSendoEditado.localizacao;
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
                    equipamentoSendoEditado.nome = document.getElementById('editNome').value.trim();
                    equipamentoSendoEditado.patrimonio = document.getElementById('editPatrimonio').value.trim();
                    equipamentoSendoEditado.localizacao = document.getElementById('editLocalizacao').value.trim();
                    equipamentoSendoEditado.status = document.getElementById('editStatus').value;
                    equipamentoSendoEditado.obs = document.getElementById('editObs').value.trim();

                    const equipamentos = getEquipamentos();
                    const index = equipamentos.findIndex(e => e.id === equipamentoSendoEditado.id);
                    
                    if (index !== -1) {
                        equipamentos[index] = equipamentoSendoEditado;
                        saveEquipamentos(equipamentos);
                        
                        carregarTabelaGerenciar();
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
                alert('Equipamento excluído.');
            }
        }
        
        // --- Lógica da Seção de Empréstimo (Atualizada) ---
        
        const emprestimoForm = document.getElementById('emprestimoForm');
        if (emprestimoForm) {
            emprestimoForm.addEventListener('submit', function(event) {
                event.preventDefault();

                const tombamento = document.getElementById('emprestimo_tombamento').value.trim();
                const nomeFuncionario = document.getElementById('emprestimo_nome').value.trim();
                const matricula = document.getElementById('emprestimo_matricula').value.trim();
                const ocupacao = document.getElementById('emprestimo_ocupacao').value.trim(); // NOVO CAMPO
                const dataHora = document.getElementById('emprestimo_datahora').value;
                const previsaoDevolucao = document.getElementById('emprestimo_previsao').value;
                
                // 1. Validar Equipamento
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
                
                // 2. Criar Registro de Empréstimo
                const novoEmprestimo = {
                    id: Date.now(),
                    equipamentoId: equipamento.id,
                    tombamento: tombamento,
                    nome: equipamento.nome,
                    funcionario: nomeFuncionario,
                    matricula: matricula,
                    ocupacao: ocupacao, // SALVANDO OCUPAÇÃO
                    dataEmprestimo: dataHora,
                    previsaoDevolucao: previsaoDevolucao,
                    status: 'Ativo'
                };
                
                // 3. Salvar Empréstimo
                const emprestimos = getEmprestimos();
                emprestimos.push(novoEmprestimo);
                saveEmprestimos(emprestimos);

                // 4. Atualizar Status do Equipamento Principal
                equipamento.status = 'Emprestado';
                equipamento.localizacao = `Emprestado para ${nomeFuncionario}`;
                saveEquipamentos(equipamentos);

                // 5. Gerar Impressão
                gerarImpressao(novoEmprestimo);
                
                alert(`Empréstimo de "${equipamento.nome}" para ${nomeFuncionario} registrado com sucesso!`);
                emprestimoForm.reset();
                document.getElementById('emprestimo_datahora').value = new Date().toLocaleString('pt-BR'); // Resetar data
            });
        }
        
        // --- Função de Impressão (Atualizada) ---

        function gerarImpressao(dadosEmprestimo) {
            const termoHtml = `
                <div class="termo-impressao" style="padding: 30px; line-height: 1.8;">
                    <h2 style="text-align: center; border-bottom: 2px solid #000; padding-bottom: 10px; color: #000;">TERMO DE EMPRÉSTIMO DE EQUIPAMENTO</h2>

                    <p>Eu, <strong>${dadosEmprestimo.funcionario.toUpperCase()}</strong>, Matrícula <strong>${dadosEmprestimo.matricula}</strong>, Cargo/Ocupação <strong>${dadosEmprestimo.ocupacao.toUpperCase()}</strong>, declaro ter recebido o seguinte equipamento em regime de empréstimo:</p>
                    
                    <table style="width: 100%; margin: 25px 0; border: 1px solid #000; border-collapse: collapse;">
                        <tr>
                            <th style="border: 1px solid #000; padding: 10px; background-color: #f0f0f0;">Equipamento</th>
                            <th style="border: 1px solid #000; padding: 10px; background-color: #f0f0f0;">Nº de Tombamento</th>
                            <th style="border: 1px solid #000; padding: 10px; background-color: #f0f0f0;">Data Prevista de Devolução</th>
                        </tr>
                        <tr>
                            <td style="border: 1px solid #000; padding: 10px;">${dadosEmprestimo.nome}</td>
                            <td style="border: 1px solid #000; padding: 10px;">${dadosEmprestimo.tombamento}</td>
                            <td style="border: 1px solid #000; padding: 10px;">${new Date(dadosEmprestimo.previsaoDevolucao).toLocaleDateString('pt-BR')}</td>
                        </tr>
                    </table>

                    <p style="margin-top: 30px;"><strong>Condições:</strong> Declaro estar ciente das responsabilidades de uso, conservação e devolução do item em perfeitas condições. Em caso de dano, perda ou furto, o funcionário será responsável pela substituição integral do bem.</p>
                    
                    <br><br><br>

                    <table style="width: 100%;">
                        <tr>
                            <td style="width: 50%; text-align: center; padding: 40px 0; border-top: 1px solid #000;">
                                Assinatura do Funcionário
                            </td>
                            <td style="width: 50%; text-align: center; padding: 40px 0; border-top: 1px solid #000;">
                                Assinatura do Responsável (TI/Estoque)
                            </td>
                        </tr>
                    </table>

                    <p style="text-align: right; margin-top: 30px; font-size: 0.9em;">Emissão: ${dadosEmprestimo.dataEmprestimo}</p>
                </div>
            `;

            const printWindow = window.open('', '', 'height=700,width=800');
            printWindow.document.write('<html><head><title>Termo de Empréstimo</title>');
            printWindow.document.write('<style>@media print { body{ margin: 0; } .termo-impressao{ font-family: \'Times New Roman\', serif; } }</style>');
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
            mudarSecao('cadastro');
        });
    </script>

</body>
</html>
