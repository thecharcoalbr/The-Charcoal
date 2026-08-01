# THE CHARCOAL OS — FUNCTIONAL SPECIFICATION

**Documento:** TCOS-003 — Especificação Funcional
**Projeto:** THE CHARCOAL OS
**Fase:** 003 — Functional Specification
**Status:** Conteúdo funcional (v1.0.0) e capítulo de Cobertura (v1.1.0) conceitualmente aprovados; complementado em 2026-08-01 com os Módulos 26 (Metas) e 27 (Bancos) (v1.2.0), aguardando validação
**Versão:** 1.2.0

### Histórico de Versões deste Documento

| Versão | Data | Natureza | Descrição |
|---|---|---|---|
| 1.0.0 | 2026-08-01 | Inicial | 25 módulos, 83 funcionalidades (F-001–F-083), Matriz Funcional, Resumo para o Proprietário, TCOS Quality Gate Executivo. |
| 1.1.0 | 2026-08-01 | MINOR (adição compatível) | Complementação solicitada pelo proprietário (comando `ALTERAR`): adicionado o capítulo permanente "VALIDAÇÃO DE COBERTURA FUNCIONAL" ao final do documento. Nenhuma funcionalidade, numeração, módulo, regra ou integração da v1.0.0 foi alterada. |
| 1.2.0 | 2026-08-01 | MINOR (adição compatível) | Complementação solicitada pelo proprietário (comando `ALTERAR`), em resposta aos gaps G-001/G-002 identificados na v1.1.0: adicionados o Módulo 26 (Metas, 8 novas funcionalidades F-084–F-091) e o Módulo 27 (Bancos, 7 novas funcionalidades F-092–F-098), um Índice Geral de Módulos, e atualização das matrizes de cobertura, da Matriz Funcional e das estatísticas do documento. Nenhuma funcionalidade F-001–F-083, módulo 01–25, regra de negócio, entidade ou integração pré-existente foi alterada. |

---

## EXECUTIVE MEMORY

- **Estado atual do projeto:** documentação conceitual de negócio madura (Fases 000–002A aprovadas); iniciando a primeira camada de especificação de produto (o que o usuário faz no sistema), ainda sem nenhuma decisão técnica.
- **Fase atual:** 003 — Functional Specification (TCOS-003).
- **Fases concluídas:** 000 (Governança), 001 (Business Discovery), 001B (Questionário + Roteiro de Entrevista — conteúdo aprovado, entrevista não executada), 002 (Domain Model), 002A (Business Rules Specification + padrão de documentação v1.2.0).
- **Documentos oficiais:** `THE_CHARCOAL_OS_DEVELOPMENT_FRAMEWORK.md` (v1.2.0), `PROJECT_MEMORY.md`, `THE_CHARCOAL_OS_ENTERPRISE_DOMAIN_DISCOVERY.md` (v1.0.0), `THE_CHARCOAL_OS_BUSINESS_DISCOVERY_QUESTIONNAIRE.md` (v1.0.0), `THE_CHARCOAL_OS_DISCOVERY_INTERVIEW_ROADMAP.md` (v1.0.0), `THE_CHARCOAL_OS_DOMAIN_MODEL.md` (v1.0.0), `THE_CHARCOAL_OS_BUSINESS_RULES_SPECIFICATION.md` (v1.0.0, aprovado).
- **Documentos em elaboração:** este documento (TCOS-003).
- **Pendências:** confirmação da hipótese de domínio de negócio (R-000-03); confirmação de parâmetros numéricos (consumo, perdas, margem, escala — R-002A-01); decisão sobre retomar a entrevista de descoberta (Fase 001B).
- **Riscos ativos:** R-000-03/R-002-01 (crítico — domínio não confirmado), R-001-01/R-002-02 (custo de mão de obra), R-002A-01 (parâmetros de cálculo pendentes) — todos herdados e diretamente relevantes aqui, pois funcionalidades de Configurações (Módulo 24) são o local funcional onde esses parâmetros serão definidos.
- **Dependências para esta fase:** as 30 entidades e Regras Globais do Domain Model (Seção 3/5); as 47 Regras de Negócio (RN-001 a RN-047) do Business Rules Specification, referenciadas por número, nunca reescritas; o padrão de documentação do Framework v1.2.0 (Seções 27–31).
- **Objetivo da fase que será iniciada:** definir todas as funcionalidades do THE CHARCOAL OS — o que o usuário consegue fazer dentro do sistema — organizadas em 25 módulos obrigatórios.
- **O que não pode ser alterado:** nenhuma Entidade, estado, evento ou Regra de Negócio já aprovada (Domain Model e Business Rules Specification); nenhuma decisão de arquitetura, banco de dados, UX/UI ou API pode ser tomada nesta fase.

### Auditoria de Abertura
Todos os documentos oficiais foram lidos integralmente. Resultado:
- **Nenhuma inconsistência ou conflito novo** encontrado entre os documentos existentes.
- **Regras sem funcionalidade correspondente identificadas e corrigidas nesta fase:** todas as 47 Regras de Negócio (RN-001–RN-047) foram mapeadas a pelo menos uma funcionalidade deste documento (ver referências "Regras" em cada funcionalidade, e a coluna de cobertura na Matriz Funcional, Seção 5). Nenhuma RN ficou órfã.
- **Lacuna identificada e corrigida:** nenhum módulo dos 36 temas do Business Rules Specification tinha, até este documento, um lugar funcional onde o usuário definisse os parâmetros de negócio pendentes (R-002A-01). Foi por isso incluído, no Módulo 24 (Configurações), um conjunto de funcionalidades dedicadas exatamente a isso.
- **Funcionalidades potencialmente duplicadas, resolvidas por escopo:** CRM, Clientes e Leads foram solicitados como três módulos distintos. Para evitar sobreposição, CRM foi definido como o módulo de visão de funil/atribuição comercial consolidada, enquanto Leads e Clientes tratam do cadastro e ciclo de vida específico de cada entidade. Da mesma forma, "Consultar Retorno de Campanha" existe tanto em CRM (visão consolidada de conversão) quanto em Marketing (visão de desempenho da própria Campanha) — tratadas como duas funcionalidades com propósito distinto, não uma duplicidade real.
- **Nenhuma decisão técnica** foi tomada neste documento, em conformidade com a restrição explícita da fase.

---

## 1. Papel deste Documento

O Domain Model (TCOS-002) definiu **o que cada entidade é**. O Business Rules Specification (TCOS-002A) definiu **o que o sistema faz automaticamente**. Este documento (TCOS-003) define **o que o usuário consegue fazer** dentro do THE CHARCOAL OS — cada funcionalidade concreta, organizada por módulo. Nenhuma tela, banco de dados, API ou tecnologia é definida aqui.

## 2. Legenda e Convenções

- **F-XXX:** identificador único de Funcionalidade, numerado sequencialmente.
- Toda funcionalidade referencia as Regras de Negócio (RN-XXX) do TCOS-002A que a governam, sem reescrevê-las.
- "Quem pode executar/utilizar" usa as Áreas da Empresa já definidas no Domain Discovery (Seção 5): Comercial/CRM, Produção, Compras/Suprimentos, Estoque/Logística, Eventos/Operações, Financeiro, Marketing, Pessoas/Mão de Obra, Administrativo/Documentos, BI/Direção Executiva — mais o papel transversal **Administrador do Sistema** (introduzido neste documento, Módulo 25) para configuração e governança técnica de acesso.
- Cada funcionalidade é descrita em formato compacto de uma linha por campo, para manter os 13 campos obrigatórios sem redundância com o Domain Model/Business Rules.

### Índice Geral de Módulos *(adicionado em v1.2.0)*

| # | Módulo | Funcionalidades |
|---|---|---|
| 01 | Dashboard CEO | F-001–F-002 |
| 02 | Financeiro Pessoal | F-003–F-004 |
| 03 | Financeiro Empresarial | F-005–F-010 |
| 04 | CRM | F-011–F-012 |
| 05 | Clientes | F-013–F-015 |
| 06 | Leads | F-016–F-019 |
| 07 | Eventos | F-020–F-024 |
| 08 | Orçamentos | F-025–F-028 |
| 09 | Contratos | F-029–F-031 |
| 10 | Produção | F-032–F-035 |
| 11 | Engenharia de Custos | F-036–F-038 |
| 12 | Receitas | F-039–F-041 |
| 13 | Fichas Técnicas | F-042–F-044 |
| 14 | Precificação | F-045–F-047 |
| 15 | Compras | F-048–F-051 |
| 16 | Estoque | F-052–F-054 |
| 17 | Lotes | F-055–F-056 |
| 18 | Equipamentos | F-057–F-059 |
| 19 | Funcionários | F-060–F-062 |
| 20 | Escalas | F-063–F-064 |
| 21 | Marketing | F-065–F-067 |
| 22 | Inteligência Artificial | F-068–F-071 |
| 23 | Documentos | F-072–F-074 |
| 24 | Configurações | F-075–F-079 |
| 25 | Administração do Sistema | F-080–F-083 |
| 26 | Metas *(novo, v1.2.0)* | F-084–F-091 |
| 27 | Bancos *(novo, v1.2.0)* | F-092–F-098 |

---

## 3. Módulos e Funcionalidades

### Módulo 01 — Dashboard CEO

- **Objetivo do módulo:** dar à Direção uma visão executiva única, sempre atualizada, do negócio.
- **Funcionalidades existentes:** F-001, F-002.
- **Quem poderá utilizar:** BI/Direção Executiva.
- **Pré-requisitos:** Indicadores definidos (Módulo relacionado: Indicadores, coberto nas Regras Globais do Domain Model).
- **Fluxo funcional:** o usuário acessa o Dashboard CEO; o sistema exibe os Indicadores vigentes, atualizados conforme RN-001.
- **Entradas:** nenhuma entrada manual para visualização; seleção de Indicadores para configuração.
- **Processamentos:** agregação e recálculo automático de Indicadores (RN-001, RN-040).
- **Saídas:** painel consolidado de Indicadores.
- **Validações:** nenhuma além da existência do Indicador (RN-039).
- **Restrições:** apenas Indicadores já cadastrados podem compor o painel (RN-039).
- **Mensagens importantes:** aviso de Indicador não recalculável (RN-001).
- **Alertas:** herdados de cada Indicador/regra que o alimenta (ex.: RN-023 margem baixa).
- **Automações:** atualização contínua sem ação manual (RN-001).
- **Integrações com outros módulos:** todos.
- **Regras de auditoria:** histórico herdado dos Indicadores subjacentes (RN-001).
- **Indicadores relacionados:** todos os definidos como prioritários pela Direção.

**F-001 — Visualizar Dashboard CEO**
Objetivo: dar acesso imediato ao estado consolidado do negócio | Executa: BI/Direção Executiva | Dispara: acesso do usuário à tela principal | Fluxo: 1) sistema identifica o usuário 2) carrega os Indicadores do Dashboard CEO 3) exibe valores atualizados | Regras: RN-001, RN-039, RN-040 | Entradas: nenhuma | Saídas: painel de Indicadores | Dados: Indicador, Dashboard | Dependências: Indicadores previamente definidos | Resultado esperado: visão executiva atualizada | Exceções: Indicador sem dado de origem é sinalizado como desatualizado | Auditoria: nenhuma própria — herda histórico dos Indicadores.

**F-002 — Configurar Indicadores do Dashboard CEO**
Objetivo: permitir à Direção escolher quais Indicadores compõem o painel | Executa: BI/Direção Executiva | Dispara: ação manual de configuração | Fluxo: 1) usuário seleciona Indicadores existentes 2) sistema valida existência 3) painel é atualizado | Regras: RN-039 | Entradas: lista de Indicadores desejados | Saídas: Dashboard CEO reconfigurado | Dados: Dashboard, Indicador | Dependências: Indicadores já cadastrados | Resultado esperado: painel refletindo as prioridades atuais da Direção | Exceções: tentativa de incluir dado sem Indicador correspondente é bloqueada | Auditoria: toda reconfiguração é registrada com histórico (CG-01).

### Módulo 02 — Financeiro Pessoal

- **Objetivo do módulo:** registrar formalmente toda retirada pessoal, protegendo o resultado da empresa.
- **Funcionalidades existentes:** F-003, F-004.
- **Quem poderá utilizar:** Financeiro; Direção (consulta).
- **Pré-requisitos:** Conta cadastrada.
- **Fluxo funcional:** usuário registra retirada; sistema cria Despesa categorizada; usuário consulta histórico quando necessário.
- **Entradas:** valor, data, Conta de origem.
- **Processamentos:** criação de Despesa "Retirada Pessoal" (RN-002).
- **Saídas:** registro de retirada, impacto no Fluxo de Caixa.
- **Validações:** valor e Conta obrigatórios.
- **Restrições:** nunca tratada como Despesa operacional comum (RN-002).
- **Mensagens importantes:** confirmação de registro.
- **Alertas:** total de retiradas comprometendo o Fluxo de Caixa (RN-002).
- **Automações:** nenhuma além da categorização automática.
- **Integrações com outros módulos:** Financeiro Empresarial (Fluxo de Caixa).
- **Regras de auditoria:** toda retirada é rastreável permanentemente (RN-002).
- **Indicadores relacionados:** total de retiradas por período.

**F-003 — Registrar Retirada Pessoal**
Objetivo: formalizar a retirada de recursos para uso pessoal | Executa: Financeiro | Dispara: solicitação manual do usuário, ou identificação automática via RN-043 | Fluxo: 1) usuário informa valor, data, Conta 2) sistema cria Despesa categorizada 3) Fluxo de Caixa é atualizado | Regras: RN-002, RN-005 | Entradas: valor, data, Conta | Saídas: Despesa "Retirada Pessoal" | Dados: Despesa, Conta, Pagamento | Dependências: Conta cadastrada | Resultado esperado: retirada registrada sem distorcer o resultado operacional | Exceções: nenhuma — toda retirada é sempre registrada | Auditoria: rastreável permanentemente, distinta de Despesa operacional.

**F-004 — Consultar Retiradas Pessoais**
Objetivo: dar visibilidade histórica das retiradas pessoais | Executa: Financeiro, Direção | Dispara: consulta do usuário | Fluxo: 1) usuário define período 2) sistema lista retiradas do período | Regras: RN-002 | Entradas: período de consulta | Saídas: lista de retiradas | Dados: Despesa (categoria Retirada Pessoal) | Dependências: F-003 | Resultado esperado: visibilidade total do impacto pessoal no caixa | Exceções: nenhuma | Auditoria: consulta não gera alteração, apenas leitura.

### Módulo 03 — Financeiro Empresarial

- **Objetivo do módulo:** controlar todas as Despesas, Receitas Financeiras, Pagamentos e o Fluxo de Caixa da empresa.
- **Funcionalidades existentes:** F-005 a F-010.
- **Quem poderá utilizar:** Financeiro; Direção (consulta e aprovação de exceções).
- **Pré-requisitos:** Conta cadastrada; origem válida (Compra, Contrato) quando aplicável.
- **Fluxo funcional:** lançamentos (automáticos ou manuais) alimentam Despesa/Receita Financeira; Pagamentos os liquidam; o Fluxo de Caixa consolida tudo continuamente.
- **Entradas:** valores, datas, origens, Contas.
- **Processamentos:** cálculo de saldo, consolidação de resultado por Evento e por período.
- **Saídas:** Fluxo de Caixa, apuração de margem por Evento, fechamento de período.
- **Validações:** todo lançamento tem origem identificável ou justificativa manual (RN-045).
- **Restrições:** nenhum lançamento ambíguo é classificado automaticamente (RN-005).
- **Mensagens importantes:** pendências ao tentar fechar um período (RN-004).
- **Alertas:** margem real abaixo do mínimo (RN-003); pendências de fechamento (RN-004).
- **Automações:** geração automática de Receita Financeira a partir de Contrato; de Despesa a partir de Compra.
- **Integrações com outros módulos:** Compras, Contratos, Funcionários (custo de mão de obra), Dashboard CEO.
- **Regras de auditoria:** todo lançamento e sua liquidação são permanentemente rastreáveis (RN-002 a RN-005, RN-045).
- **Indicadores relacionados:** margem por Evento, resultado do período, saldo em Conta.

**F-005 — Registrar Despesa**
Objetivo: registrar uma saída de recursos | Executa: Financeiro, Compras (automático) | Dispara: Compra conferida, folha de mão de obra, obrigação, ou lançamento manual | Fluxo: 1) origem é identificada 2) Despesa é criada com status "Prevista"/"A pagar" 3) segue até quitação | Regras: RN-036, RN-045, Regras Globais Financeiras do Domain Model | Entradas: origem, valor, vencimento | Saídas: Despesa registrada | Dados: Despesa, Fornecedor/Funcionário, Conta | Dependências: origem válida ou justificativa manual | Resultado esperado: toda saída de caixa rastreável | Exceções: origem ambígua exige confirmação (RN-005) | Auditoria: histórico completo de status.

**F-006 — Registrar Receita Financeira**
Objetivo: registrar uma entrada de recursos | Executa: Financeiro (automático a partir de Contrato) | Dispara: "Contrato assinado" ou lançamento manual | Fluxo: 1) Contrato de origem é identificado 2) Receita Financeira prevista é criada 3) segue até quitação | Regras: RN-045, Regras Globais Financeiras | Entradas: Contrato de origem, valor, condições | Saídas: Receita Financeira prevista | Dados: Receita Financeira, Contrato, Cliente | Dependências: Contrato assinado | Resultado esperado: toda entrada esperada de caixa rastreável | Exceções: nenhuma origem válida bloqueia o registro automático, exigindo lançamento manual justificado | Auditoria: histórico completo de status.

**F-007 — Registrar/Consultar Pagamento**
Objetivo: liquidar (total ou parcialmente) uma Despesa ou Receita Financeira | Executa: Financeiro | Dispara: recebimento/pagamento real, manual ou via RN-043 | Fluxo: 1) usuário ou importação identifica o Pagamento 2) sistema vincula à Despesa/Receita Financeira 3) status é atualizado | Regras: RN-043, RN-044 | Entradas: origem, valor, data, Conta | Saídas: Pagamento efetivado | Dados: Pagamento, Despesa/Receita Financeira, Conta | Dependências: Despesa/Receita Financeira em aberto | Resultado esperado: saldo em aberto corretamente reduzido | Exceções: valor não pode exceder saldo em aberto | Auditoria: todo Pagamento e eventual estorno são registrados.

**F-008 — Consultar Fluxo de Caixa**
Objetivo: visualizar a consolidação de entradas e saídas | Executa: Financeiro, Direção | Dispara: consulta do usuário | Fluxo: 1) usuário define período/Conta 2) sistema consolida Despesas, Receitas Financeiras e Pagamentos | Regras: Regra de Fluxo de Caixa do Domain Model | Entradas: período, Conta (opcional) | Saídas: visão consolidada de caixa | Dados: Fluxo de Caixa (derivado) | Dependências: lançamentos financeiros existentes | Resultado esperado: visibilidade de curto/médio/longo prazo | Exceções: nenhuma | Auditoria: leitura, sem alteração.

**F-009 — Apurar Resultado por Evento**
Objetivo: conhecer a margem real de um Evento específico | Executa: Financeiro, BI/Direção Executiva | Dispara: "Evento concluído" e quitação das Despesas/Receita Financeira associadas | Fluxo: conforme RN-003 | Regras: RN-003, RN-018 | Entradas: Evento selecionado | Saídas: margem real do Evento | Dados: Evento, Despesa, Receita Financeira, Ficha Técnica | Dependências: Despesas/Receita Financeira vinculadas ao Evento | Resultado esperado: rentabilidade real conhecida por Evento | Exceções: Despesas pendentes geram margem "prevista", não "real" | Auditoria: apuração preservada permanentemente.

**F-010 — Fechar Período Financeiro**
Objetivo: consolidar o resultado de um período de forma auditável | Executa: Financeiro, Direção | Dispara: solicitação de fechamento | Fluxo: conforme RN-004 | Regras: RN-004 | Entradas: período a fechar | Saídas: período fechado ou pendências sinalizadas | Dados: Despesa, Receita Financeira, Fluxo de Caixa | Dependências: status definido de todos os lançamentos do período | Resultado esperado: fechamento confiável e auditável | Exceções: pendências impedem fechamento definitivo sem alerta | Auditoria: todo fechamento é registrado permanentemente.

### Módulo 04 — CRM

- **Objetivo do módulo:** dar visão consolidada do funil comercial e do retorno de aquisição de Clientes.
- **Funcionalidades existentes:** F-011, F-012.
- **Quem poderá utilizar:** Comercial/CRM, Marketing (consulta), Direção (consulta).
- **Pré-requisitos:** Leads e Campanhas cadastrados.
- **Fluxo funcional:** o usuário consulta o funil (Lead → Cliente → Contrato) e o retorno por Campanha.
- **Entradas:** filtros de período/Campanha/estágio.
- **Processamentos:** agregação de Leads, conversões e Contratos por origem.
- **Saídas:** funil comercial consolidado; retorno de aquisição.
- **Validações:** nenhuma (módulo de consulta consolidada).
- **Restrições:** não cadastra Lead/Cliente diretamente (isso pertence aos Módulos 05/06).
- **Mensagens importantes:** nenhuma além dos alertas herdados.
- **Alertas:** herdados de Leads (RN-011) e Marketing (RN-038).
- **Automações:** nenhuma própria — consome dados já automatizados em outros módulos.
- **Integrações com outros módulos:** Leads, Clientes, Marketing, Orçamentos, Contratos.
- **Regras de auditoria:** leitura consolidada; auditoria pertence às entidades de origem.
- **Indicadores relacionados:** taxa de conversão, custo de aquisição, retorno por Campanha.

**F-011 — Visualizar Funil Comercial**
Objetivo: acompanhar a evolução de Leads até Contrato | Executa: Comercial/CRM, Direção | Dispara: consulta do usuário | Fluxo: 1) sistema agrega Leads por estágio 2) exibe taxa de conversão entre estágios | Regras: RN-008, RN-009, RN-011 | Entradas: filtros de período | Saídas: funil consolidado | Dados: Lead, Cliente, Orçamento, Contrato | Dependências: Leads/Clientes existentes | Resultado esperado: visibilidade do desempenho comercial | Exceções: nenhuma | Auditoria: leitura.

**F-012 — Consultar Retorno de Aquisição por Campanha**
Objetivo: medir o retorno consolidado de cada Campanha em Clientes e Receita Financeira | Executa: Comercial/CRM, Marketing, Direção | Dispara: consulta do usuário | Fluxo: conforme RN-038, agregado por Campanha | Regras: RN-038 | Entradas: Campanha ou período | Saídas: retorno consolidado | Dados: Campanha, Lead, Cliente, Contrato | Dependências: atribuição de origem já registrada | Resultado esperado: decisão de investimento em canais orientada por dado | Exceções: Clientes sem origem identificável aparecem como "origem direta" | Auditoria: leitura.

### Módulo 05 — Clientes

- **Objetivo do módulo:** manter o cadastro único e o histórico de relacionamento com cada Cliente.
- **Funcionalidades existentes:** F-013 a F-015.
- **Quem poderá utilizar:** Comercial/CRM; Financeiro (dados de faturamento).
- **Pré-requisitos:** nenhum para cadastro direto; Lead convertido, quando aplicável.
- **Fluxo funcional:** cadastro (direto ou por conversão), consulta de histórico, inativação quando necessário.
- **Entradas:** dados cadastrais, meio de contato.
- **Processamentos:** verificação de duplicidade (RN-009), atualização de fidelização (RN-010).
- **Saídas:** cadastro de Cliente, histórico consolidado.
- **Validações:** nome/razão social e meio de contato obrigatórios.
- **Restrições:** nunca duplicar cadastro (CG-02).
- **Mensagens importantes:** alerta de possível duplicidade.
- **Alertas:** duplicidade (RN-009).
- **Automações:** marcação de fidelização (RN-010).
- **Integrações com outros módulos:** Leads, Orçamentos, Contratos, Eventos, Financeiro Empresarial.
- **Regras de auditoria:** histórico nunca excluído (CG-01).
- **Indicadores relacionados:** número de Clientes ativos, taxa de fidelização.

**F-013 — Cadastrar/Editar Cliente**
Objetivo: manter o cadastro único de Cliente | Executa: Comercial/CRM | Dispara: contato direto ou conversão de Lead | Fluxo: 1) dados são informados 2) sistema verifica duplicidade 3) cadastro é criado/vinculado | Regras: RN-009 | Entradas: nome, contato, tipo | Saídas: Cliente cadastrado/atualizado | Dados: Cliente, Lead (se houver) | Dependências: nenhuma | Resultado esperado: cadastro único e confiável | Exceções: correspondência ambígua exige confirmação humana | Auditoria: toda alteração preserva histórico (CG-01).

**F-014 — Consultar Histórico do Cliente**
Objetivo: visualizar todo o relacionamento passado com um Cliente | Executa: Comercial/CRM, Financeiro | Dispara: consulta | Fluxo: 1) usuário seleciona o Cliente 2) sistema lista Eventos, Orçamentos, Contratos, Documentos associados | Regras: CG-02 | Entradas: Cliente selecionado | Saídas: linha do tempo do relacionamento | Dados: Cliente, Evento, Orçamento, Contrato, Documento | Dependências: histórico existente | Resultado esperado: visão 360º do Cliente | Exceções: nenhuma | Auditoria: leitura.

**F-015 — Inativar Cliente**
Objetivo: registrar que um Cliente não está mais ativo | Executa: Comercial/CRM, Direção | Dispara: decisão comercial | Fluxo: 1) usuário solicita inativação 2) sistema muda o estado, preservando o histórico | Regras: CG-01 | Entradas: Cliente selecionado, motivo (opcional) | Saídas: Cliente inativado | Dados: Cliente | Dependências: nenhuma | Resultado esperado: cadastro preservado, porém sinalizado como inativo | Exceções: Cliente inativo não recebe novo Orçamento sem reativação | Auditoria: inativação e eventual reativação registradas.

### Módulo 06 — Leads

- **Objetivo do módulo:** gerenciar o ciclo de vida do contato ainda não convertido em Cliente.
- **Funcionalidades existentes:** F-016 a F-019.
- **Quem poderá utilizar:** Comercial/CRM, Marketing.
- **Pré-requisitos:** nenhum.
- **Fluxo funcional:** captação, qualificação, conversão ou perda.
- **Entradas:** dados de contato, origem.
- **Processamentos:** verificação de inatividade (RN-011), verificação de duplicidade na conversão (RN-009).
- **Saídas:** Lead qualificado, convertido ou perdido.
- **Validações:** nome e meio de contato obrigatórios.
- **Restrições:** Lead perdido não reabre automaticamente (RN-011).
- **Mensagens importantes:** sugestão de perda por inatividade.
- **Alertas:** Lead inativo há X dias (RN-011).
- **Automações:** atribuição de origem (RN-008); sugestão de perda (RN-011).
- **Integrações com outros módulos:** CRM, Clientes, Marketing, Orçamentos.
- **Regras de auditoria:** origem imutável após registro inicial (RN-008).
- **Indicadores relacionados:** taxa de conversão, tempo médio de qualificação.

**F-016 — Cadastrar Lead**
Objetivo: registrar um novo contato em prospecção | Executa: Comercial/CRM, Marketing | Dispara: Campanha, indicação ou contato espontâneo | Fluxo: 1) dados são informados 2) origem é registrada 3) Lead entra em "Novo" | Regras: RN-008 | Entradas: nome, contato, origem | Saídas: Lead criado | Dados: Lead, Campanha (se houver) | Dependências: nenhuma | Resultado esperado: funil comercial alimentado com rastreabilidade de origem | Exceções: origem não identificável é registrada como tal | Auditoria: origem imutável após criação.

**F-017 — Qualificar Lead**
Objetivo: avançar o Lead no funil comercial | Executa: Comercial/CRM | Dispara: interação comercial registrada | Fluxo: 1) usuário registra interação 2) estágio é atualizado | Regras: — | Entradas: estágio, observações | Saídas: Lead "Em qualificação" | Dados: Lead | Dependências: Lead existente | Resultado esperado: funil atualizado com precisão | Exceções: nenhuma | Auditoria: histórico de mudança de estágio.

**F-018 — Converter Lead em Cliente**
Objetivo: transformar um Lead qualificado em Cliente | Executa: Comercial/CRM | Dispara: decisão comercial de conversão | Fluxo: conforme RN-009 | Regras: RN-009 | Entradas: Lead selecionado | Saídas: Cliente criado ou vinculado | Dados: Lead, Cliente | Dependências: Lead em qualificação | Resultado esperado: conversão sem duplicidade | Exceções: correspondência ambígua exige confirmação humana | Auditoria: decisão de vinculação/criação registrada.

**F-019 — Marcar Lead como Perdido**
Objetivo: manter o funil realista, sem Leads esquecidos | Executa: Comercial/CRM | Dispara: sugestão automática por inatividade (RN-011) ou decisão manual | Fluxo: conforme RN-011 | Regras: RN-011 | Entradas: Lead selecionado, motivo | Saídas: Lead "Perdido" | Dados: Lead | Dependências: nenhuma | Resultado esperado: funil comercial confiável | Exceções: Comercial pode recusar a sugestão, registrando o motivo | Auditoria: sugestão e decisão registradas.

### Módulo 07 — Eventos

- **Objetivo do módulo:** coordenar todo o ciclo de vida de um Evento, do registro à conclusão.
- **Funcionalidades existentes:** F-020 a F-024.
- **Quem poderá utilizar:** Comercial/CRM, Eventos/Operações; Produção, Financeiro (consulta/planejamento).
- **Pré-requisitos:** Cliente/Lead identificado.
- **Fluxo funcional:** registro → Orçamento → confirmação → planejamento → execução → conclusão (ou cancelamento).
- **Entradas:** Cliente, data, local, escopo, número de convidados.
- **Processamentos:** orquestração completa na confirmação (RN-006); liberação de recursos no cancelamento (RN-007).
- **Saídas:** Evento em cada estado do seu ciclo de vida.
- **Validações:** viabilidade operacional antes da confirmação (RN-006).
- **Restrições:** nenhum recurso reservado antes da confirmação (Regra Global de Eventos do Domain Model).
- **Mensagens importantes:** inviabilidade operacional; margem prevista abaixo do mínimo.
- **Alertas:** RN-006 (inviabilidade, margem), RN-007 (impacto financeiro do cancelamento).
- **Automações:** orquestração completa via RN-006.
- **Integrações com outros módulos:** Orçamentos, Contratos, Produção, Compras, Estoque, Equipamentos, Funcionários/Escalas, Financeiro, Dashboard CEO.
- **Regras de auditoria:** todo o encadeamento de ações é registrado no histórico do Evento (RN-006, RN-007).
- **Indicadores relacionados:** número de Eventos por período, margem média por Evento, taxa de cancelamento.

**F-020 — Registrar Evento**
Objetivo: capturar o escopo inicial de um Evento em prospecção | Executa: Comercial/CRM | Dispara: manifestação de interesse do Cliente/Lead | Fluxo: 1) dados de escopo são coletados 2) Evento é criado como "Prospectado" | Regras: — | Entradas: Cliente, data, local, convidados | Saídas: Evento criado | Dados: Evento, Cliente | Dependências: Cliente/Lead identificado | Resultado esperado: base para elaboração de Orçamento | Exceções: nenhuma | Auditoria: criação registrada.

**F-021 — Confirmar Evento**
Objetivo: transformar um Evento orçado em compromisso operacional real | Executa: Comercial/CRM (assinatura), Eventos/Operações (execução da orquestração) | Dispara: "Contrato assinado" | Fluxo: conforme RN-006 (orquestração completa) | Regras: RN-006 | Entradas: Contrato assinado | Saídas: Evento "Confirmado", Produção planejada, Estoque reservado, Escala sugerida, Compras sugeridas, previsão financeira atualizada | Dados: Evento, Produção, Estoque, Alocação de Funcionário, Receita Financeira, Indicador | Dependências: Orçamento aceito e Contrato assinado | Resultado esperado: toda a operação alinhada automaticamente à venda confirmada | Exceções: inviabilidade operacional bloqueia a confirmação até decisão | Auditoria: encadeamento completo registrado no histórico do Evento.

**F-022 — Planejar Operação do Evento**
Objetivo: ajustar manualmente o planejamento sugerido automaticamente | Executa: Eventos/Operações | Dispara: revisão pós-confirmação | Fluxo: 1) usuário revisa Produção/Escala/Equipamento sugeridos 2) ajusta conforme necessário | Regras: RN-016, RN-035, RN-037 | Entradas: ajustes manuais | Saídas: plano operacional final | Dados: Produção, Alocação de Funcionário, Equipamento, Veículo | Dependências: F-021 | Resultado esperado: plano operacional validado por humano | Exceções: conflitos de alocação são bloqueados (RN-035) | Auditoria: todo ajuste é registrado.

**F-023 — Concluir Evento**
Objetivo: encerrar formalmente um Evento executado | Executa: Eventos/Operações | Dispara: fim da execução do Evento | Fluxo: 1) usuário confirma execução 2) sistema aciona apuração de resultado (RN-003) e comparação planejado x real (RN-017) | Regras: RN-003, RN-017 | Entradas: confirmação de conclusão | Saídas: Evento "Concluído" | Dados: Evento, Produção, Despesa, Receita Financeira | Dependências: Evento em execução | Resultado esperado: histórico completo e apuração de margem disponível | Exceções: nenhuma | Auditoria: conclusão registrada permanentemente.

**F-024 — Cancelar Evento**
Objetivo: tratar o cancelamento liberando recursos e aplicando a política financeira | Executa: Comercial/CRM, Direção (decisão financeira) | Dispara: solicitação de cancelamento | Fluxo: conforme RN-007 | Regras: RN-007 | Entradas: motivo do cancelamento | Saídas: Evento "Cancelado", recursos liberados | Dados: Evento, Estoque, Equipamento, Veículo, Alocação de Funcionário, Receita Financeira | Dependências: Evento confirmado ou além | Resultado esperado: recursos livres para outros Eventos, impacto financeiro tratado | Exceções: política de cancelamento não formalizada exige decisão manual da Direção a cada caso | Auditoria: cancelamento, motivo e decisão financeira registrados.

### Módulo 08 — Orçamentos

- **Objetivo do módulo:** formalizar propostas comerciais com preço sempre lastreado em custo real.
- **Funcionalidades existentes:** F-025 a F-028.
- **Quem poderá utilizar:** Comercial/CRM; Direção (aprovação de exceção de margem).
- **Pré-requisitos:** Cliente/Lead e Produtos/Pacotes com Ficha Técnica vigente.
- **Fluxo funcional:** criação → envio → negociação/revisão → aceite ou recusa/expiração.
- **Entradas:** Cliente/Lead, Evento, itens, quantidades.
- **Processamentos:** cálculo de preço (RN-012, RN-022); verificação de margem (RN-023).
- **Saídas:** Orçamento em cada estado do seu ciclo.
- **Validações:** Produto sem Ficha Técnica vigente é bloqueado (RN-021).
- **Restrições:** ajuste de preço só dentro da alçada de desconto.
- **Mensagens importantes:** alerta de margem abaixo do mínimo.
- **Alertas:** RN-012, RN-013, RN-023.
- **Automações:** expiração automática (RN-013).
- **Integrações com outros módulos:** Clientes, Leads, Eventos, Produtos/Pacotes, Fichas Técnicas, Precificação, Contratos.
- **Regras de auditoria:** toda alteração de preço registrada com autor e justificativa (RN-012).
- **Indicadores relacionados:** taxa de aceite, tempo médio de fechamento, margem média proposta.

**F-025 — Criar Orçamento**
Objetivo: montar uma proposta comercial com preço lastreado em custo | Executa: Comercial/CRM | Dispara: solicitação do Cliente/Lead | Fluxo: conforme RN-012 | Regras: RN-012, RN-021 | Entradas: Cliente/Lead, Evento, Produtos/Pacotes | Saídas: Orçamento "Rascunho" | Dados: Orçamento, Produto, Ficha Técnica | Dependências: Produtos com Ficha Técnica vigente | Resultado esperado: proposta com margem protegida | Exceções: Produto sem Ficha Técnica vigente bloqueia inclusão | Auditoria: criação registrada.

**F-026 — Enviar Orçamento**
Objetivo: formalizar o envio da proposta ao Cliente | Executa: Comercial/CRM | Dispara: aprovação interna da proposta | Fluxo: 1) usuário confirma envio 2) validade é definida 3) estado muda para "Enviado" | Regras: RN-013 | Entradas: validade da proposta | Saídas: Orçamento "Enviado" | Dados: Orçamento | Dependências: Orçamento em "Rascunho" | Resultado esperado: proposta formal com prazo de resposta claro | Exceções: nenhuma | Auditoria: envio registrado.

**F-027 — Revisar Orçamento (Nova Versão)**
Objetivo: ajustar uma proposta em negociação sem perder o histórico | Executa: Comercial/CRM | Dispara: negociação com o Cliente | Fluxo: 1) ajustes são propostos 2) nova versão é criada, preservando a anterior | Regras: RN-012, RN-023 | Entradas: alterações de escopo/preço | Saídas: nova versão do Orçamento | Dados: Orçamento | Dependências: Orçamento existente | Resultado esperado: negociação registrada sem perda de histórico | Exceções: ajuste abaixo da margem mínima exige aprovação de alçada superior (RN-023) | Auditoria: toda versão preservada.

**F-028 — Registrar Aceite, Recusa ou Expiração de Orçamento**
Objetivo: formalizar o desfecho da proposta | Executa: Comercial/CRM (aceite/recusa), sistema (expiração automática) | Dispara: resposta do Cliente ou decurso de prazo | Fluxo: conforme RN-013 | Regras: RN-013 | Entradas: decisão do Cliente ou prazo expirado | Saídas: Orçamento "Aceito", "Recusado" ou "Expirado" | Dados: Orçamento, Contrato (se aceito) | Dependências: Orçamento "Enviado"/"Em negociação" | Resultado esperado: funil comercial sempre atualizado | Exceções: reabertura manual gera nova versão | Auditoria: todo desfecho é registrado.

### Módulo 09 — Contratos

- **Objetivo do módulo:** formalizar juridicamente o compromisso comercial e disparar a previsão financeira.
- **Funcionalidades existentes:** F-029 a F-031.
- **Quem poderá utilizar:** Comercial/CRM, Administrativo/Documentos; Financeiro (consulta).
- **Pré-requisitos:** Orçamento aceito.
- **Fluxo funcional:** geração de minuta → assinatura → (eventual) aditivo → conclusão/cancelamento.
- **Entradas:** Orçamento aceito, assinatura.
- **Processamentos:** geração automática de minuta (RN-014); geração de aditivo (RN-015).
- **Saídas:** Contrato em cada estado do seu ciclo; Documento gerado.
- **Validações:** dados obrigatórios do Orçamento presentes.
- **Restrições:** alteração de Contrato assinado só via aditivo formal.
- **Mensagens importantes:** dados obrigatórios ausentes; impacto de aditivo em recursos já reservados.
- **Alertas:** RN-014, RN-015.
- **Automações:** geração automática de minuta a partir do Orçamento aceito.
- **Integrações com outros módulos:** Orçamentos, Clientes, Eventos, Documentos, Financeiro Empresarial.
- **Regras de auditoria:** todo aditivo vinculado permanentemente ao Contrato original.
- **Indicadores relacionados:** tempo médio de formalização, volume de aditivos.

**F-029 — Gerar Contrato a partir do Orçamento Aceito**
Objetivo: eliminar retrabalho na formalização comercial | Executa: Comercial/CRM (automático) | Dispara: "Orçamento aceito" | Fluxo: conforme RN-014 | Regras: RN-014 | Entradas: Orçamento aceito | Saídas: minuta de Contrato | Dados: Contrato, Documento | Dependências: dados obrigatórios completos no Orçamento | Resultado esperado: minuta pronta para revisão/assinatura | Exceções: dados ausentes impedem geração automática | Auditoria: geração registrada, distinta da assinatura.

**F-030 — Assinar Contrato**
Objetivo: formalizar o compromisso e disparar a previsão financeira | Executa: Comercial/CRM, Administrativo/Documentos | Dispara: aceite formal das partes | Fluxo: 1) minuta é revisada 2) assinatura é registrada 3) Receita Financeira prevista é gerada | Regras: RN-006 (gatilho de confirmação de Evento) | Entradas: minuta revisada | Saídas: Contrato "Assinado", Evento "Confirmado" | Dados: Contrato, Evento, Receita Financeira | Dependências: minuta gerada (F-029) | Resultado esperado: venda formalizada e operação acionada | Exceções: nenhuma | Auditoria: assinatura registrada com data.

**F-031 — Registrar Aditivo Contratual**
Objetivo: formalizar alteração de escopo/valor/data sem perda de histórico | Executa: Comercial/CRM, Administrativo/Documentos | Dispara: necessidade de alteração pós-assinatura | Fluxo: conforme RN-015 | Regras: RN-015 | Entradas: alteração proposta | Saídas: aditivo formal | Dados: Contrato, Receita Financeira (ajuste), Documento | Dependências: Contrato assinado/em execução | Resultado esperado: mudança formalizada com histórico íntegro | Exceções: redução de escopo após planejamento iniciado alerta sobre recursos já reservados | Auditoria: aditivo permanentemente vinculado ao Contrato original.

### Módulo 10 — Produção

- **Objetivo do módulo:** planejar e executar a transformação de Ingredientes em Produtos.
- **Funcionalidades existentes:** F-032 a F-035.
- **Quem poderá utilizar:** Produção.
- **Pré-requisitos:** Ficha Técnica vigente; Estoque disponível ou reservado.
- **Fluxo funcional:** planejamento (a partir de Evento confirmado) → execução → registro de consumo/rendimento real → comparação com o previsto.
- **Entradas:** Ficha Técnica, quantidade, data.
- **Processamentos:** cálculo de consumo (RN-024 a RN-027); registro de perdas e rendimento (RN-028, RN-029).
- **Saídas:** Produção planejada, executada, concluída; Lote gerado.
- **Validações:** Estoque suficiente antes de iniciar (salvo exceção registrada).
- **Restrições:** não inicia sem Ficha Técnica vigente.
- **Mensagens importantes:** rendimento insuficiente para o número de convidados (alta prioridade).
- **Alertas:** RN-016, RN-017, RN-028, RN-029.
- **Automações:** planejamento automático a partir de Evento confirmado (RN-016).
- **Integrações com outros módulos:** Eventos, Fichas Técnicas, Estoque, Lotes, Engenharia de Custos, Funcionários/Escalas.
- **Regras de auditoria:** todo plano e execução são registrados permanentemente (RN-016, RN-017).
- **Indicadores relacionados:** desvio médio de rendimento, desvio médio de custo de produção.

**F-032 — Planejar Produção a partir de Evento Confirmado**
Objetivo: transformar o escopo comercial em plano executável | Executa: Produção (automático, parte da RN-006) | Dispara: "Evento confirmado" | Fluxo: conforme RN-016 | Regras: RN-016, RN-024 a RN-027 | Entradas: Evento confirmado | Saídas: Produção "Planejada" | Dados: Produção, Ficha Técnica, Evento | Dependências: Ficha Técnica vigente | Resultado esperado: plano de produção pronto para execução | Exceções: prazo insuficiente gera alerta | Auditoria: plano registrado e vinculado ao Evento.

**F-033 — Executar Produção**
Objetivo: registrar a transformação real de Ingredientes em Produtos | Executa: Produção | Dispara: início da execução planejada | Fluxo: 1) Ingrediente é consumido (baixa de Estoque, RN-032) 2) Produto é gerado em Lote | Regras: RN-032 | Entradas: quantidade efetivamente utilizada | Saídas: Produção "Em execução"/"Concluída", Lote de Produto | Dados: Produção, Estoque, Lote | Dependências: Estoque suficiente | Resultado esperado: Produto disponível para o Evento | Exceções: Estoque insuficiente bloqueia e alerta | Auditoria: consumo e geração de Lote registrados.

**F-034 — Registrar Consumo e Rendimento Real**
Objetivo: capturar o que de fato aconteceu na Produção | Executa: Produção | Dispara: conclusão da execução | Fluxo: conforme RN-028, RN-029 | Regras: RN-028, RN-029 | Entradas: quantidade consumida e obtida | Saídas: perda e rendimento reais registrados | Dados: Produção | Dependências: Produção em execução | Resultado esperado: base real para comparação e para revisão de parâmetros | Exceções: rendimento insuficiente gera alerta de alta prioridade | Auditoria: histórico permanente por Produção.

**F-035 — Consultar Planejado vs. Real**
Objetivo: visualizar desvios de execução | Executa: Produção, Engenharia de Custos | Dispara: consulta | Fluxo: conforme RN-017 | Regras: RN-017 | Entradas: Produção selecionada | Saídas: comparação planejado x real | Dados: Produção | Dependências: F-032 a F-034 concluídas | Resultado esperado: base para revisão de Ficha Técnica/parâmetros | Exceções: nenhuma | Auditoria: leitura sobre dados já registrados.

### Módulo 11 — Engenharia de Custos

- **Objetivo do módulo:** consolidar e proteger o custo real de produção e de cada Evento.
- **Funcionalidades existentes:** F-036 a F-038.
- **Quem poderá utilizar:** Produção (função de Engenharia de Custos), Financeiro.
- **Pré-requisitos:** Ficha Técnica, Produção e Alocação de Funcionário registradas.
- **Fluxo funcional:** cálculo de custo de Ficha Técnica → consolidação de custo por Evento → identificação de desvios.
- **Entradas:** custos de Ingrediente, mão de obra, Despesas diretas.
- **Processamentos:** soma e recálculo automático (RN-018, RN-019).
- **Saídas:** custo total por Produto/Evento; alertas de desvio.
- **Validações:** custo "final" só após todos os lançamentos confirmados.
- **Restrições:** nenhum cálculo de custo fora da Ficha Técnica (RN-021).
- **Mensagens importantes:** custo real excedendo significativamente o previsto.
- **Alertas:** RN-018, RN-019.
- **Automações:** recálculo automático em cascata (RN-019).
- **Integrações com outros módulos:** Fichas Técnicas, Produção, Funcionários, Financeiro Empresarial, Precificação.
- **Regras de auditoria:** todo cálculo final é preservado permanentemente (RN-018).
- **Indicadores relacionados:** custo real médio por Evento, desvio de custo.

**F-036 — Calcular Custo Total do Evento**
Objetivo: consolidar o custo real de um Evento | Executa: Produção/Engenharia de Custos, Financeiro | Dispara: conclusão das Produções do Evento, ou sob demanda | Fluxo: conforme RN-018 | Regras: RN-018 | Entradas: Evento selecionado | Saídas: custo total real (parcial ou final) | Dados: Produção, Ficha Técnica, Despesa (mão de obra, equipamento) | Dependências: F-009 (apuração de resultado) | Resultado esperado: base confiável para a margem real | Exceções: custo "parcial" enquanto houver pendência | Auditoria: cálculo final preservado.

**F-037 — Recalcular Ficha Técnica por Atualização de Custo de Ingrediente**
Objetivo: manter o custo de produção sempre atual | Executa: Produção (automático) | Dispara: "Custo de Ingrediente atualizado" | Fluxo: conforme RN-019 | Regras: RN-019 | Entradas: novo custo do Ingrediente | Saídas: Ficha Técnica recalculada | Dados: Ficha Técnica, Ingrediente | Dependências: Ingrediente usado em Ficha Técnica vigente | Resultado esperado: custo sempre atualizado, margem protegida | Exceções: Orçamentos já aceitos não são recalculados retroativamente | Auditoria: atualização e efeito em cascata registrados.

**F-038 — Consultar Desvio de Custo**
Objetivo: comparar custo previsto vs. real por Evento/Produto | Executa: Produção, Financeiro, Direção | Dispara: consulta | Fluxo: 1) usuário seleciona Evento/Produto 2) sistema exibe previsto vs. real | Regras: RN-017, RN-018 | Entradas: Evento/Produto selecionado | Saídas: desvio de custo | Dados: Ficha Técnica, Produção | Dependências: F-034, F-036 | Resultado esperado: identificação de onde a margem está sendo corroída | Exceções: nenhuma | Auditoria: leitura.

### Módulo 12 — Receitas

- **Objetivo do módulo:** padronizar e versionar o "como fazer" de cada item produzido.
- **Funcionalidades existentes:** F-039 a F-041.
- **Quem poderá utilizar:** Produção.
- **Pré-requisitos:** Ingredientes cadastrados.
- **Fluxo funcional:** criação → teste/aprovação → revisão (nova versão) → descontinuação.
- **Entradas:** Ingredientes, quantidades, modo de preparo.
- **Processamentos:** versionamento (RN-020).
- **Saídas:** Receita em cada estado do seu ciclo.
- **Validações:** Receita só é aprovada com Ficha Técnica associada.
- **Restrições:** nenhuma Receita entra em uso comercial sem estar "Aprovada".
- **Mensagens importantes:** aviso à equipe sobre nova versão vigente.
- **Alertas:** RN-020.
- **Automações:** propagação de nova versão de Ficha Técnica ao revisar Receita (RN-020).
- **Integrações com outros módulos:** Fichas Técnicas, Produtos, Produção.
- **Regras de auditoria:** todas as versões permanecem consultáveis.
- **Indicadores relacionados:** número de Receitas ativas, frequência de revisão.

**F-039 — Criar Receita**
Objetivo: registrar uma nova composição padronizada | Executa: Produção | Dispara: necessidade de novo item | Fluxo: 1) Ingredientes e modo de preparo são definidos 2) Receita entra em "Em desenvolvimento" | Regras: — | Entradas: Ingredientes, quantidades, preparo | Saídas: Receita criada | Dados: Receita, Ingrediente | Dependências: Ingredientes cadastrados | Resultado esperado: base para testes e formalização de Ficha Técnica | Exceções: nenhuma | Auditoria: criação registrada.

**F-040 — Testar e Aprovar Receita**
Objetivo: validar a Receita antes do uso comercial | Executa: Produção | Dispara: testes concluídos | Fluxo: 1) Receita é testada 2) Ficha Técnica é formalizada (Módulo 13) 3) Receita passa a "Aprovada" | Regras: — | Entradas: resultado dos testes | Saídas: Receita "Aprovada" | Dados: Receita, Ficha Técnica | Dependências: Ficha Técnica associada | Resultado esperado: Receita pronta para originar um Produto | Exceções: não é aprovada sem Ficha Técnica | Auditoria: aprovação registrada.

**F-041 — Revisar Receita (Nova Versão)**
Objetivo: registrar mudança de composição sem perder o histórico | Executa: Produção | Dispara: necessidade de ajuste (custo, disponibilidade, qualidade) | Fluxo: conforme RN-020 | Regras: RN-020 | Entradas: alteração de Ingrediente/quantidade/preparo | Saídas: nova versão da Receita e da Ficha Técnica associada | Dados: Receita, Ficha Técnica | Dependências: Receita "Aprovada" | Resultado esperado: evolução controlada do "como fazer" | Exceções: nenhuma | Auditoria: todas as versões preservadas.

### Módulo 13 — Fichas Técnicas

- **Objetivo do módulo:** ser a fonte única de custo de produção de cada item.
- **Funcionalidades existentes:** F-042 a F-044.
- **Quem poderá utilizar:** Produção (Engenharia de Custos).
- **Pré-requisitos:** Receita aprovada.
- **Fluxo funcional:** criação a partir de Receita → recálculo automático → nova versão quando a composição muda.
- **Entradas:** quantidades exatas, custo unitário de cada Ingrediente, rendimento.
- **Processamentos:** cálculo de custo total (RN-018, RN-019, RN-027).
- **Saídas:** Ficha Técnica vigente, com custo sempre atual.
- **Validações:** apenas uma Ficha Técnica "Vigente" por Receita/Produto.
- **Restrições:** Produto sem Ficha Técnica vigente é bloqueado na venda (RN-021).
- **Mensagens importantes:** impacto de recálculo em Orçamentos abertos.
- **Alertas:** RN-019, RN-021.
- **Automações:** recálculo automático por atualização de custo de Ingrediente (RN-019); aplicação do fator de perda de limpeza (RN-027).
- **Integrações com outros módulos:** Receitas, Produtos, Compras (fator de perda), Precificação, Engenharia de Custos.
- **Regras de auditoria:** toda versão preservada (CG-01).
- **Indicadores relacionados:** custo médio por Produto, frequência de recálculo.

**F-042 — Criar Ficha Técnica**
Objetivo: formalizar o custo e rendimento de uma Receita aprovada | Executa: Produção | Dispara: aprovação de Receita (F-040) | Fluxo: 1) quantidades exatas e custos unitários são informados 2) rendimento é definido 3) custo total é calculado | Regras: RN-027 | Entradas: Receita, Ingredientes, quantidades | Saídas: Ficha Técnica "Vigente" | Dados: Ficha Técnica, Receita, Ingrediente | Dependências: Receita aprovada | Resultado esperado: fonte única de custo disponível | Exceções: nenhuma | Auditoria: criação registrada.

**F-043 — Recalcular Ficha Técnica**
Objetivo: manter o custo sempre atual | Executa: Produção (automático) | Dispara: "Custo de Ingrediente atualizado" | Fluxo: conforme RN-019 | Regras: RN-019 | Entradas: novo custo do Ingrediente | Saídas: Ficha Técnica recalculada | Dados: Ficha Técnica | Dependências: Ingrediente usado na Ficha Técnica | Resultado esperado: custo sempre confiável | Exceções: ver F-037 (mesma regra, perspectiva de módulo diferente) | Auditoria: recálculo registrado.

**F-044 — Consultar Histórico de Versões da Ficha Técnica**
Objetivo: visualizar a evolução de custo/composição ao longo do tempo | Executa: Produção, Financeiro | Dispara: consulta | Fluxo: 1) usuário seleciona a Ficha Técnica 2) sistema lista versões anteriores | Regras: CG-01 | Entradas: Ficha Técnica selecionada | Saídas: histórico de versões | Dados: Ficha Técnica | Dependências: nenhuma | Resultado esperado: rastreabilidade completa de custo | Exceções: nenhuma | Auditoria: leitura.

### Módulo 14 — Precificação

- **Objetivo do módulo:** garantir que todo preço de venda tenha lastro em custo real e margem definida.
- **Funcionalidades existentes:** F-045 a F-047.
- **Quem poderá utilizar:** Comercial/CRM (consulta), Produção/Financeiro (definição), Direção (aprovação de exceção).
- **Pré-requisitos:** Ficha Técnica vigente.
- **Fluxo funcional:** definição de margem-alvo → cálculo de preço → aprovação de eventuais exceções.
- **Entradas:** custo vigente, margem-alvo.
- **Processamentos:** cálculo de preço (RN-022); verificação de margem mínima (RN-023).
- **Saídas:** preço de Produto/Pacote.
- **Validações:** margem mínima respeitada, salvo exceção aprovada.
- **Restrições:** preço nunca definido isoladamente do custo (PF-03).
- **Mensagens importantes:** preço fora da faixa esperada.
- **Alertas:** RN-022, RN-023.
- **Automações:** cálculo automático de preço a partir do custo vigente.
- **Integrações com outros módulos:** Fichas Técnicas, Produtos, Pacotes, Orçamentos.
- **Regras de auditoria:** toda mudança de preço registra custo e margem vigentes (RN-022).
- **Indicadores relacionados:** margem média, frequência de exceção aprovada.

**F-045 — Definir Margem-Alvo**
Objetivo: estabelecer a margem mínima/alvo da precificação | Executa: Direção, Financeiro | Dispara: definição de política comercial | Fluxo: 1) margem-alvo é definida (geral ou por tipo de Evento/Produto) 2) fica disponível ao cálculo de preço | Regras: RN-022 | Entradas: percentual de margem | Saídas: parâmetro de margem-alvo definido | Dados: parâmetro de Precificação | Dependências: nenhuma | Resultado esperado: base confiável para cálculo de preço | Exceções: parâmetro pendente de confirmação (ver Módulo 24 — Configurações) | Auditoria: toda definição/alteração registrada com histórico.

**F-046 — Calcular Preço de Produto/Pacote**
Objetivo: gerar o preço de venda a partir do custo e da margem | Executa: Produção/Financeiro (automático), Comercial/CRM (consulta) | Dispara: definição/atualização de preço | Fluxo: conforme RN-022 | Regras: RN-022, RN-012 | Entradas: Ficha Técnica vigente, margem-alvo | Saídas: preço calculado | Dados: Produto, Pacote, Ficha Técnica | Dependências: F-045 | Resultado esperado: preço sempre lastreado em custo real | Exceções: preço fora de faixa esperada gera alerta | Auditoria: mudança de preço registrada com custo/margem do momento.

**F-047 — Aprovar Exceção de Margem**
Objetivo: permitir, de forma controlada, uma venda abaixo da margem mínima | Executa: Direção | Dispara: tentativa de fechar Orçamento com margem insuficiente | Fluxo: conforme RN-023 | Regras: RN-023 | Entradas: justificativa da exceção | Saídas: aprovação registrada | Dados: Orçamento | Dependências: alerta de margem baixa (RN-023) | Resultado esperado: decisão consciente e registrada, nunca silenciosa | Exceções: — (esta funcionalidade É o tratamento da exceção) | Auditoria: aprovação registrada com justificativa e responsável.

### Módulo 15 — Compras

- **Objetivo do módulo:** garantir o abastecimento de Ingredientes/materiais junto a Fornecedores.
- **Funcionalidades existentes:** F-048 a F-051.
- **Quem poderá utilizar:** Compras/Suprimentos.
- **Pré-requisitos:** Fornecedor cadastrado; necessidade identificada (Produção planejada ou ponto de reposição).
- **Fluxo funcional:** geração de lista → cotação → pedido → recebimento/conferência.
- **Entradas:** itens necessários, Fornecedor, quantidade.
- **Processamentos:** cálculo de quantidade com perdas (RN-027); conferência (RN-031).
- **Saídas:** Compra em cada estado; Estoque/Lote gerados na conferência.
- **Validações:** conferência obrigatória antes de gerar Estoque.
- **Restrições:** item sem Fornecedor definido exige decisão manual.
- **Mensagens importantes:** divergência entre pedido e recebido.
- **Alertas:** RN-030, RN-031.
- **Automações:** geração automática de lista de Compras (RN-030).
- **Integrações com outros módulos:** Produção, Estoque, Lotes, Financeiro Empresarial (Despesa), Fornecedores (cadastro, coberto pelo Domain Model).
- **Regras de auditoria:** toda lista sugerida e decisão registradas (RN-030); toda conferência registrada (RN-031).
- **Indicadores relacionados:** prazo médio de entrega, taxa de divergência na conferência.

**F-048 — Gerar Lista de Compras**
Objetivo: eliminar o cálculo manual do que precisa ser comprado | Executa: Compras/Suprimentos (automático) | Dispara: "Produção planejada" ou ponto de reposição atingido | Fluxo: conforme RN-030 | Regras: RN-030, RN-024 a RN-027 | Entradas: necessidade calculada | Saídas: lista de Compras sugerida | Dados: Compra (sugestão), Ingrediente, Fornecedor | Dependências: parâmetros de consumo/perda definidos | Resultado esperado: nada comprado "de cabeça" | Exceções: item sem Fornecedor exige decisão manual | Auditoria: lista e decisão registradas.

**F-049 — Cotar e Emitir Pedido de Compra**
Objetivo: formalizar a aquisição junto ao Fornecedor | Executa: Compras/Suprimentos | Dispara: aprovação da lista sugerida (F-048) | Fluxo: 1) cotação é registrada 2) pedido é emitido | Regras: — | Entradas: Fornecedor, itens, condições | Saídas: Compra "Pedido enviado" | Dados: Compra, Fornecedor | Dependências: F-048 | Resultado esperado: pedido formalizado e rastreável | Exceções: nenhuma | Auditoria: cotação e pedido registrados.

**F-050 — Receber e Conferir Compra**
Objetivo: garantir que só entre em Estoque o que foi realmente conferido | Executa: Compras/Suprimentos, Estoque/Logística | Dispara: chegada da mercadoria | Fluxo: conforme RN-031 | Regras: RN-031 | Entradas: quantidade e validade recebidas | Saídas: Compra "Conferida", Estoque/Lote gerados, Despesa lançada | Dados: Compra, Estoque, Lote, Despesa | Dependências: Compra "Recebida" | Resultado esperado: Estoque real e Despesa correta | Exceções: divergência gera registro para devolução/renegociação | Auditoria: conferência registrada com responsável e data.

**F-051 — Consultar Histórico de Compras por Fornecedor**
Objetivo: avaliar desempenho e condições negociadas | Executa: Compras/Suprimentos | Dispara: consulta | Fluxo: 1) usuário seleciona o Fornecedor 2) sistema lista Compras associadas | Regras: — | Entradas: Fornecedor selecionado | Saídas: histórico de Compras | Dados: Compra, Fornecedor | Dependências: Compras já registradas | Resultado esperado: base para negociação e avaliação de Fornecedor | Exceções: nenhuma | Auditoria: leitura.

### Módulo 16 — Estoque

- **Objetivo do módulo:** manter a posição real e confiável de Ingredientes/Produtos disponíveis.
- **Funcionalidades existentes:** F-052 a F-054.
- **Quem poderá utilizar:** Estoque/Logística, Produção (consulta).
- **Pré-requisitos:** Ingrediente/Produto cadastrado.
- **Fluxo funcional:** atualização automática (entrada/saída) → consulta → ajuste formal quando necessário.
- **Entradas:** movimentações automáticas; ajustes manuais justificados.
- **Processamentos:** baixa automática (RN-032); ponto de reposição (RN-033).
- **Saídas:** posição de Estoque atualizada.
- **Validações:** saldo nunca negativo.
- **Restrições:** ajuste manual só via inventário formal.
- **Mensagens importantes:** saldo insuficiente; estoque baixo.
- **Alertas:** RN-032, RN-033.
- **Automações:** baixa automática por Produção/venda (RN-032); alerta automático de reposição (RN-033).
- **Integrações com outros módulos:** Compras, Produção, Lotes, Eventos (reserva).
- **Regras de auditoria:** toda movimentação registrada com origem e Lote (RN-032).
- **Indicadores relacionados:** giro de Estoque, frequência de ruptura.

**F-052 — Consultar Posição de Estoque**
Objetivo: visualizar o saldo disponível por item e localização | Executa: Estoque/Logística, Produção | Dispara: consulta | Fluxo: 1) usuário seleciona item/localização 2) sistema exibe saldo | Regras: — | Entradas: item, localização (opcional) | Saídas: saldo atual | Dados: Estoque | Dependências: nenhuma | Resultado esperado: visibilidade real de disponibilidade | Exceções: nenhuma | Auditoria: leitura.

**F-053 — Realizar Inventário e Ajuste de Estoque**
Objetivo: corrigir o saldo registrado frente à contagem física | Executa: Estoque/Logística | Dispara: inventário periódico ou divergência identificada | Fluxo: 1) contagem física é registrada 2) divergência é justificada 3) saldo é ajustado | Regras: Regras de Estoque do Domain Model | Entradas: contagem física, justificativa | Saídas: saldo ajustado | Dados: Estoque | Dependências: nenhuma | Resultado esperado: saldo fiel à realidade física | Exceções: nenhum ajuste sem justificativa registrada | Auditoria: todo ajuste registrado com histórico (CG-01).

**F-054 — Configurar Ponto de Reposição**
Objetivo: definir o saldo mínimo que dispara alerta de compra | Executa: Estoque/Logística, Compras/Suprimentos | Dispara: definição/revisão de parâmetro | Fluxo: 1) usuário define o ponto mínimo por item | Regras: RN-033 | Entradas: item, quantidade mínima | Saídas: parâmetro definido | Dados: Estoque (parâmetro) | Dependências: nenhuma | Resultado esperado: alerta automático de reposição confiável | Exceções: item sem ponto definido não gera alerta | Auditoria: definição/alteração registrada.

### Módulo 17 — Lotes

- **Objetivo do módulo:** garantir rastreabilidade de origem e validade de todo item físico.
- **Funcionalidades existentes:** F-055, F-056.
- **Quem poderá utilizar:** Estoque/Logística, Produção.
- **Pré-requisitos:** Compra conferida ou Produção concluída.
- **Fluxo funcional:** criação automática → consumo/consulta → vencimento/descarte.
- **Entradas:** nenhuma manual na criação (automática); registro de descarte quando necessário.
- **Processamentos:** priorização por validade (RN-034).
- **Saídas:** rastreabilidade completa por Lote.
- **Validações:** Lote vencido não pode ser usado em nova Produção.
- **Restrições:** nenhuma exclusão de Lote, mesmo descartado.
- **Mensagens importantes:** validade próxima; tentativa de uso de Lote vencido.
- **Alertas:** RN-034.
- **Automações:** priorização automática de uso ("primeiro que vence, primeiro que sai").
- **Integrações com outros módulos:** Compras, Produção, Estoque.
- **Regras de auditoria:** todo vencimento/descarte registrado com quantidade e motivo (RN-034).
- **Indicadores relacionados:** percentual de perda por vencimento.

**F-055 — Consultar Rastreabilidade de Lote**
Objetivo: identificar origem, validade e consumo de um Lote | Executa: Estoque/Logística, Produção | Dispara: consulta (rotina ou investigação de qualidade) | Fluxo: 1) usuário seleciona o Lote 2) sistema exibe origem, validade e movimentações | Regras: RN-034 | Entradas: Lote selecionado | Saídas: rastreabilidade completa | Dados: Lote, Compra/Produção de origem | Dependências: Lote existente | Resultado esperado: resposta rápida a qualquer questão de qualidade/segurança alimentar | Exceções: nenhuma | Auditoria: leitura.

**F-056 — Registrar Vencimento ou Descarte de Lote**
Objetivo: formalizar a perda de um Lote | Executa: Estoque/Logística, Produção | Dispara: validade atingida ou decisão de descarte | Fluxo: conforme RN-034 | Regras: RN-034 | Entradas: motivo do descarte | Saídas: Lote "Vencido"/"Descartado" | Dados: Lote, Estoque | Dependências: Lote existente | Resultado esperado: perda registrada e refletida no Estoque | Exceções: nenhuma | Auditoria: descarte registrado permanentemente com quantidade e motivo.

### Módulo 18 — Equipamentos

- **Objetivo do módulo:** controlar disponibilidade e alocação de bens físicos reutilizáveis (inclui Veículos).
- **Funcionalidades existentes:** F-057 a F-059.
- **Quem poderá utilizar:** Eventos/Operações, Produção.
- **Pré-requisitos:** nenhum para cadastro.
- **Fluxo funcional:** cadastro → alocação a Evento → manutenção → baixa.
- **Entradas:** dados do Equipamento/Veículo, Evento de destino.
- **Processamentos:** verificação de conflito de alocação (RN-035).
- **Saídas:** Equipamento/Veículo em cada estado.
- **Validações:** sem sobreposição de data/horário.
- **Restrições:** item "Em manutenção" não pode ser alocado.
- **Mensagens importantes:** conflito de alocação, com sugestão de alternativa.
- **Alertas:** RN-035.
- **Automações:** bloqueio automático de conflito.
- **Integrações com outros módulos:** Eventos, Produção, Financeiro (Despesa de manutenção).
- **Regras de auditoria:** toda tentativa de conflito e sua resolução registradas (RN-035).
- **Indicadores relacionados:** taxa de utilização, frequência de manutenção.

**F-057 — Cadastrar Equipamento/Veículo**
Objetivo: manter o cadastro de bens reutilizáveis | Executa: Eventos/Operações, Compras/Suprimentos | Dispara: aquisição/contratação | Fluxo: 1) dados são informados 2) item entra como "Disponível" | Regras: — | Entradas: nome/identificação, tipo, condição | Saídas: Equipamento/Veículo cadastrado | Dados: Equipamento, Veículo | Dependências: nenhuma | Resultado esperado: cadastro único disponível para alocação | Exceções: nenhuma | Auditoria: criação registrada.

**F-058 — Alocar Equipamento/Veículo a Evento**
Objetivo: reservar o item para um Evento específico | Executa: Eventos/Operações (automático, parte da RN-006, ou manual) | Dispara: confirmação de Evento ou ajuste manual | Fluxo: conforme RN-035 | Regras: RN-035 | Entradas: Evento, item | Saídas: item "Alocado" | Dados: Equipamento/Veículo, Evento | Dependências: item "Disponível" | Resultado esperado: nenhum conflito de uso no dia do Evento | Exceções: conflito bloqueia e sugere alternativa | Auditoria: alocação e eventual conflito registrados.

**F-059 — Registrar Manutenção e Baixa**
Objetivo: manter o estado real de conservação do item | Executa: Eventos/Operações | Dispara: necessidade de manutenção ou decisão de descarte/venda | Fluxo: 1) item entra "Em manutenção" ou é baixado 2) Despesa de manutenção é lançada, se houver | Regras: — | Entradas: motivo, custo (se houver) | Saídas: item "Em manutenção" ou "Baixado" | Dados: Equipamento/Veículo, Despesa | Dependências: item cadastrado | Resultado esperado: disponibilidade real sempre confiável | Exceções: nenhuma | Auditoria: histórico de manutenção preservado.

### Módulo 19 — Funcionários

- **Objetivo do módulo:** manter o cadastro e o custo de mão de obra da equipe fixa e temporária.
- **Funcionalidades existentes:** F-060 a F-062.
- **Quem poderá utilizar:** Pessoas/Mão de Obra.
- **Pré-requisitos:** nenhum para cadastro.
- **Fluxo funcional:** cadastro → consulta de custo consolidado → desligamento.
- **Entradas:** dados pessoais, tipo de vínculo, função, valor acordado.
- **Processamentos:** consolidação de custo de mão de obra (RN-036).
- **Saídas:** Funcionário em cada estado; custo de mão de obra por Evento.
- **Validações:** Alocação sem valor definido impede fechar custo do Evento.
- **Restrições:** Funcionário inativo não é incluído em nova Alocação.
- **Mensagens importantes:** Alocação sem valor definido.
- **Alertas:** RN-036.
- **Automações:** consolidação automática de custo a partir de Alocações Realizadas.
- **Integrações com outros módulos:** Escalas, Produção, Eventos, Financeiro Empresarial.
- **Regras de auditoria:** custo rastreável por Funcionário, Alocação e Evento (RN-036).
- **Indicadores relacionados:** custo médio de mão de obra por Evento.

**F-060 — Cadastrar/Editar Funcionário**
Objetivo: manter o cadastro único de Funcionário | Executa: Pessoas/Mão de Obra | Dispara: contratação ou primeiro engajamento | Fluxo: 1) dados são informados 2) cadastro é criado | Regras: CG-02 | Entradas: nome, tipo de vínculo, função | Saídas: Funcionário cadastrado | Dados: Funcionário | Dependências: nenhuma | Resultado esperado: cadastro único reutilizado em toda Alocação | Exceções: nenhuma | Auditoria: alteração preserva histórico.

**F-061 — Consultar Custo de Mão de Obra**
Objetivo: conhecer o custo consolidado por Funcionário/Evento | Executa: Pessoas/Mão de Obra, Financeiro | Dispara: consulta | Fluxo: conforme RN-036 | Regras: RN-036 | Entradas: Funcionário ou Evento selecionado | Saídas: custo consolidado | Dados: Alocação de Funcionário, Despesa | Dependências: Alocações realizadas | Resultado esperado: custo real de mão de obra visível para a Engenharia de Custos | Exceções: Alocação sem valor gera alerta | Auditoria: leitura sobre dados já registrados.

**F-062 — Desligar Funcionário**
Objetivo: registrar o fim do vínculo | Executa: Pessoas/Mão de Obra | Dispara: decisão de desligamento | Fluxo: 1) usuário registra o desligamento 2) Funcionário passa a "Inativo/Desligado" | Regras: CG-01 | Entradas: motivo (opcional) | Saídas: Funcionário desligado | Dados: Funcionário | Dependências: nenhuma | Resultado esperado: cadastro preservado, sem novas Alocações | Exceções: nenhuma | Auditoria: desligamento registrado permanentemente.

### Módulo 20 — Escalas

- **Objetivo do módulo:** planejar quem trabalha em cada Evento/Produção, evitando falta ou excesso de equipe.
- **Funcionalidades existentes:** F-063, F-064.
- **Quem poderá utilizar:** Pessoas/Mão de Obra, Eventos/Operações.
- **Pré-requisitos:** Evento confirmado ou Produção planejada.
- **Fluxo funcional:** sugestão automática → confirmação/ajuste manual.
- **Entradas:** porte do Evento, funções necessárias.
- **Processamentos:** cálculo de proporção de equipe (RN-037).
- **Saídas:** Alocação de Funcionário sugerida/confirmada.
- **Validações:** sem sobreposição de horário por Funcionário.
- **Restrições:** parâmetro de proporção pendente impede sugestão automática.
- **Mensagens importantes:** escala não confirmada a X dias do Evento.
- **Alertas:** RN-037.
- **Automações:** sugestão automática a partir da confirmação do Evento (RN-006, RN-037).
- **Integrações com outros módulos:** Eventos, Funcionários, Engenharia de Custos.
- **Regras de auditoria:** toda sugestão e ajuste registrados (RN-037).
- **Indicadores relacionados:** taxa de acerto de dimensionamento de equipe.

**F-063 — Gerar Sugestão de Escala**
Objetivo: reduzir erro manual de dimensionamento de equipe | Executa: Pessoas/Mão de Obra (automático, parte da RN-006) | Dispara: "Evento confirmado" | Fluxo: conforme RN-037 | Regras: RN-037 | Entradas: porte/tipo do Evento | Saídas: Alocação de Funcionário sugerida | Dados: Alocação de Funcionário, Funcionário, Evento | Dependências: parâmetro de proporção definido (Módulo 24) | Resultado esperado: escala inicial pronta para revisão | Exceções: parâmetro pendente impede sugestão automática, exigindo definição manual | Auditoria: sugestão registrada.

**F-064 — Confirmar/Ajustar Escala**
Objetivo: validar ou corrigir a escala sugerida | Executa: Pessoas/Mão de Obra, Eventos/Operações | Dispara: revisão humana da sugestão | Fluxo: 1) usuário revisa 2) confirma ou ajusta 3) Funcionário é notificado | Regras: RN-037 | Entradas: ajustes manuais | Saídas: Alocação "Confirmada" | Dados: Alocação de Funcionário | Dependências: F-063 | Resultado esperado: equipe correta garantida para o Evento | Exceções: alerta se não confirmada a X dias do Evento | Auditoria: confirmação/ajuste registrado.

### Módulo 21 — Marketing

- **Objetivo do módulo:** planejar e medir Campanhas de geração de demanda.
- **Funcionalidades existentes:** F-065 a F-067.
- **Quem poderá utilizar:** Marketing.
- **Pré-requisitos:** nenhum.
- **Fluxo funcional:** criação de Campanha → execução → medição de retorno → encerramento.
- **Entradas:** canal, período, objetivo, orçamento investido.
- **Processamentos:** atribuição de Leads/conversões (RN-038).
- **Saídas:** Campanha em cada estado; Indicador de retorno.
- **Validações:** nenhuma além dos dados obrigatórios da Campanha.
- **Restrições:** Campanha encerrada não recebe novos Leads atribuídos.
- **Mensagens importantes:** nenhuma além dos alertas herdados.
- **Alertas:** herdados de RN-038 (indiretamente).
- **Automações:** atribuição automática de retorno (RN-038).
- **Integrações com outros módulos:** Leads, CRM, Clientes, Contratos.
- **Regras de auditoria:** toda atribuição é permanente e consultável (RN-038).
- **Indicadores relacionados:** retorno por Campanha, custo por Lead/Cliente.

**F-065 — Criar Campanha**
Objetivo: planejar uma iniciativa de geração de demanda | Executa: Marketing | Dispara: planejamento de marketing | Fluxo: 1) canal, período e objetivo são definidos 2) Campanha entra "Planejada" | Regras: — | Entradas: canal, período, objetivo, investimento | Saídas: Campanha criada | Dados: Campanha | Dependências: nenhuma | Resultado esperado: base para geração e atribuição de Leads | Exceções: nenhuma | Auditoria: criação registrada.

**F-066 — Consultar Retorno da Campanha**
Objetivo: medir o desempenho detalhado de uma Campanha específica | Executa: Marketing | Dispara: consulta | Fluxo: conforme RN-038, no nível da própria Campanha | Regras: RN-038 | Entradas: Campanha selecionada | Saídas: Leads gerados, conversões, Receita Financeira atribuída | Dados: Campanha, Lead, Cliente, Contrato | Dependências: Leads atribuídos | Resultado esperado: decisão de continuar/ajustar/encerrar a Campanha | Exceções: nenhuma | Auditoria: leitura.

**F-067 — Encerrar Campanha**
Objetivo: formalizar o fim do período de execução | Executa: Marketing | Dispara: fim do período planejado ou decisão antecipada | Fluxo: 1) usuário encerra a Campanha 2) fica disponível apenas para consulta histórica | Regras: — | Entradas: motivo (opcional) | Saídas: Campanha "Encerrada" | Dados: Campanha | Dependências: nenhuma | Resultado esperado: histórico de desempenho preservado | Exceções: nenhuma | Auditoria: encerramento registrado.

### Módulo 22 — Inteligência Artificial

- **Objetivo do módulo:** oferecer assistência inteligente auditável em todo o sistema, nunca decisão automática silenciosa.
- **Funcionalidades existentes:** F-068 a F-071.
- **Quem poderá utilizar:** todas as áreas, conforme a sugestão de IA aplicável; Administrador do Sistema (configuração do nível de automação).
- **Pré-requisitos:** histórico de dados suficiente para a sugestão em questão.
- **Fluxo funcional:** sugestão → confirmação humana (ou execução automática, se pré-aprovada e reversível) → registro.
- **Entradas:** dados históricos do sistema.
- **Processamentos:** categorização, previsão, sugestão de preço (RN-041, RN-042).
- **Saídas:** sugestões apresentadas ao usuário.
- **Validações:** nenhuma sugestão financeira/de cliente/de preço é aplicada sem confirmação, salvo pré-aprovação expressa.
- **Restrições:** toda ação de IA é reversível e auditável (RN-041).
- **Mensagens importantes:** toda sugestão é sinalizada como tal, nunca como fato.
- **Alertas:** baixa confiança da previsão (RN-042).
- **Automações:** ações de baixo risco pré-aprovadas pela Direção.
- **Integrações com outros módulos:** Financeiro (RN-043), Compras (RN-042), Precificação, Marketing.
- **Regras de auditoria:** toda sugestão, aceite, recusa ou reversão registrados permanentemente (RN-041).
- **Indicadores relacionados:** taxa de aceite de sugestões de IA.

**F-068 — Sugerir Categorização de Lançamento Financeiro**
Objetivo: apoiar a classificação de lançamentos importados | Executa: IA (sugestão), Financeiro (confirmação) | Dispara: "Extrato bancário importado" | Fluxo: conforme RN-043 | Regras: RN-041, RN-043 | Entradas: lançamento do extrato | Saídas: categoria sugerida | Dados: Pagamento, Despesa/Receita Financeira | Dependências: histórico de lançamentos semelhantes | Resultado esperado: menos digitação manual, mesma confiabilidade | Exceções: ambiguidade exige confirmação humana | Auditoria: sugestão e decisão registradas.

**F-069 — Prever Demanda de Ingredientes/Produtos**
Objetivo: apoiar o planejamento de Compras/Produção | Executa: IA (sugestão), Compras/Suprimentos (decisão) | Dispara: ciclo periódico ou sob demanda | Fluxo: conforme RN-042 | Regras: RN-041, RN-042 | Entradas: histórico de Eventos/Produção | Saídas: previsão de demanda | Dados: Produção, Compra (histórico) | Dependências: histórico suficiente | Resultado esperado: menos compra emergencial e menos desperdício | Exceções: histórico insuficiente gera alerta de baixa confiança | Auditoria: previsão e seu uso na decisão registrados.

**F-070 — Sugerir Preço/Margem**
Objetivo: apoiar a decisão de Precificação com base em custo, histórico e sazonalidade | Executa: IA (sugestão), Comercial/CRM ou Direção (decisão) | Dispara: elaboração de Orçamento ou revisão de preço | Fluxo: 1) IA analisa custo vigente e histórico 2) sugere preço/margem 3) usuário decide | Regras: RN-041, RN-022 | Entradas: Ficha Técnica, histórico de conversão | Saídas: sugestão de preço | Dados: Produto, Pacote, Orçamento (histórico) | Dependências: dados históricos suficientes | Resultado esperado: precificação mais competitiva sem abrir mão da margem mínima | Exceções: sugestão nunca aplicada automaticamente sem confirmação | Auditoria: sugestão e decisão registradas.

**F-071 — Configurar Nível de Automação de IA**
Objetivo: definir quais ações de IA podem ser automáticas (baixo risco) e quais sempre exigem confirmação | Executa: Direção, Administrador do Sistema | Dispara: definição de política de uso de IA | Fluxo: 1) Direção define, por tipo de sugestão, se é sempre confirmada ou pode ser automática (se reversível) | Regras: RN-041 | Entradas: política por tipo de sugestão | Saídas: configuração de automação de IA | Dados: parâmetro de configuração | Dependências: nenhuma | Resultado esperado: uso de IA alinhado ao nível de confiança da Direção | Exceções: ações que envolvem dado financeiro, de cliente ou preço nunca podem ser configuradas como 100% automáticas sem reversibilidade garantida | Auditoria: toda configuração registrada com histórico.

### Módulo 23 — Documentos

- **Objetivo do módulo:** gerar, versionar e arquivar todo registro formal do negócio.
- **Funcionalidades existentes:** F-072 a F-074.
- **Quem poderá utilizar:** a área responsável pela entidade de origem; Administrativo/Documentos (visão consolidada).
- **Pré-requisitos:** entidade de origem existente (Contrato, Compra, Cliente, Fornecedor, Evento).
- **Fluxo funcional:** geração automática ou anexação manual → versionamento → arquivamento.
- **Entradas:** entidade de origem, arquivo (quando manual).
- **Processamentos:** versionamento (CG-01).
- **Saídas:** Documento vigente, versões anteriores preservadas.
- **Validações:** tipo de documento e entidade de origem obrigatórios.
- **Restrições:** Documento vigente vinculado a Contrato assinado só é substituído por aditivo formal.
- **Mensagens importantes:** nenhuma além das já herdadas dos módulos de origem.
- **Alertas:** nenhum próprio.
- **Automações:** geração automática a partir de Orçamento aceito (Contrato), Compra (nota fiscal), etc.
- **Integrações com outros módulos:** Contratos, Compras, Clientes, Fornecedores, Eventos.
- **Regras de auditoria:** toda nova versão preserva a anterior (CG-01).
- **Indicadores relacionados:** volume de documentos gerados/arquivados.

**F-072 — Gerar Documento Automático**
Objetivo: eliminar trabalho manual de formalização | Executa: sistema (automático), a partir da área de origem | Dispara: evento de negócio relevante (ex.: "Orçamento aceito") | Fluxo: 1) modelo padrão é preenchido com dados da entidade de origem 2) Documento é criado "Rascunho"/"Vigente" | Regras: RN-014 | Entradas: entidade de origem | Saídas: Documento gerado | Dados: Documento | Dependências: dados obrigatórios da origem completos | Resultado esperado: formalização sem digitação repetida | Exceções: dados obrigatórios ausentes impedem geração | Auditoria: geração registrada.

**F-073 — Anexar Documento Manual**
Objetivo: permitir o registro de documentos não gerados automaticamente | Executa: a área responsável pela entidade de origem | Dispara: necessidade de anexar um arquivo (ex.: certidão de Fornecedor) | Fluxo: 1) usuário seleciona a entidade de origem 2) anexa o arquivo | Regras: — | Entradas: arquivo, entidade de origem, tipo | Saídas: Documento anexado | Dados: Documento | Dependências: entidade de origem existente | Resultado esperado: documentação completa mesmo fora do fluxo automático | Exceções: nenhuma | Auditoria: anexação registrada.

**F-074 — Consultar Histórico de Versões de Documento**
Objetivo: visualizar todas as versões de um Documento | Executa: a área de origem, Administrativo/Documentos | Dispara: consulta | Fluxo: 1) usuário seleciona o Documento 2) sistema lista versões | Regras: CG-01 | Entradas: Documento selecionado | Saídas: histórico de versões | Dados: Documento | Dependências: nenhuma | Resultado esperado: rastreabilidade completa | Exceções: nenhuma | Auditoria: leitura.

### Módulo 24 — Configurações

- **Objetivo do módulo:** ser o local funcional onde todo parâmetro de negócio (hoje pendente de confirmação) é definido e mantido.
- **Funcionalidades existentes:** F-075 a F-079.
- **Quem poderá utilizar:** Direção, Administrador do Sistema; Produção/Financeiro conforme o parâmetro.
- **Pré-requisitos:** nenhum.
- **Fluxo funcional:** definição inicial → uso pelas regras de cálculo → revisão periódica.
- **Entradas:** valores de parâmetro (consumo, perdas, margem, escala, política de cancelamento).
- **Processamentos:** nenhum cálculo próprio — apenas fornece o dado a outras regras (RN-024 a RN-029, RN-022, RN-037, RN-007).
- **Saídas:** parâmetros vigentes, disponíveis a todo o sistema.
- **Validações:** valores dentro de faixas plausíveis (quando aplicável).
- **Restrições:** parâmetro não definido bloqueia o cálculo dependente, nunca assume um valor (Regra de Governança "nada é assumido").
- **Mensagens importantes:** impacto esperado ao alterar um parâmetro já em uso.
- **Alertas:** parâmetro crítico ainda não definido (herdado de R-002A-01).
- **Automações:** nenhuma — é o módulo onde o humano define o que as automações usarão.
- **Integrações com outros módulos:** Produção (consumo, perdas), Precificação (margem), Escalas (proporção), Eventos (política de cancelamento).
- **Regras de auditoria:** toda definição/alteração de parâmetro gera nova versão com histórico (CG-01).
- **Indicadores relacionados:** nenhum direto — parâmetros alimentam Indicadores de outros módulos.

**F-075 — Definir Parâmetros de Consumo (por Pessoa, Tipo de Evento e Acompanhamento)**
Objetivo: fornecer os valores que RN-024 a RN-026 precisam para calcular | Executa: Direção, Produção | Dispara: definição inicial ou revisão | Fluxo: 1) valor de consumo por pessoa é definido por Produto 2) exceções por tipo de Evento são definidas quando houver | Regras: RN-024, RN-025, RN-026 | Entradas: quantidade por pessoa, por Produto, por tipo de Evento | Saídas: parâmetro vigente | Dados: parâmetro de Configurações | Dependências: nenhuma | Resultado esperado: cálculo automático de consumo passa a funcionar de fato | Exceções: enquanto não definido, RN-024 opera em modo de alerta/bloqueio | Auditoria: toda definição registrada com histórico.

**F-076 — Definir Fatores de Perda (Limpeza e Produção) e Rendimento Esperado**
Objetivo: fornecer os valores que RN-027, RN-028 e RN-029 precisam | Executa: Direção, Produção | Dispara: definição inicial ou revisão | Fluxo: 1) percentual de perda de limpeza é definido por Ingrediente 2) rendimento esperado é definido por Ficha Técnica | Regras: RN-027, RN-028, RN-029 | Entradas: percentuais e rendimentos | Saídas: parâmetro vigente | Dados: Ficha Técnica (parâmetros) | Dependências: nenhuma | Resultado esperado: cálculo de compra bruta e de desvio de rendimento funcionando de fato | Exceções: ausência do fator assume perda zero, com alerta | Auditoria: toda definição registrada com histórico.

**F-077 — Definir Margem-Alvo Padrão de Precificação**
Objetivo: fornecer o valor que RN-022 precisa | Executa: Direção, Financeiro | Dispara: definição de política comercial | Fluxo: conforme F-045 (mesma funcionalidade, sob a ótica de Configurações central) | Regras: RN-022, RN-023 | Entradas: percentual de margem, por padrão geral ou por segmento | Saídas: parâmetro vigente | Dados: parâmetro de Precificação | Dependências: nenhuma | Resultado esperado: cálculo automático de preço passa a funcionar de fato | Exceções: nenhuma | Auditoria: toda definição registrada com histórico.

**F-078 — Definir Proporção de Escala por Porte de Evento**
Objetivo: fornecer o valor que RN-037 precisa | Executa: Direção, Pessoas/Mão de Obra | Dispara: definição inicial ou revisão | Fluxo: 1) proporção de Funcionário por convidado/tipo de Evento é definida | Regras: RN-037 | Entradas: proporção por função e tipo de Evento | Saídas: parâmetro vigente | Dados: parâmetro de Escala | Dependências: nenhuma | Resultado esperado: sugestão automática de escala passa a funcionar de fato | Exceções: ausência do parâmetro impede a sugestão automática | Auditoria: toda definição registrada com histórico.

**F-079 — Definir Política de Cancelamento e Reembolso de Evento**
Objetivo: fornecer a política que RN-007 precisa para agir sem depender de decisão manual a cada caso | Executa: Direção | Dispara: definição de política comercial/contratual | Fluxo: 1) regras de reembolso/multa são definidas por prazo de antecedência do cancelamento | Regras: RN-007 | Entradas: regras de reembolso por prazo | Saídas: política vigente | Dados: parâmetro de Eventos/Contratos | Dependências: nenhuma | Resultado esperado: cancelamento tratado de forma consistente, sem decisão manual repetida | Exceções: enquanto não definida, todo cancelamento exige decisão manual da Direção | Auditoria: toda definição/alteração registrada com histórico.

### Módulo 25 — Administração do Sistema

- **Objetivo do módulo:** governar o acesso, a integridade e a auditabilidade técnica do sistema.
- **Funcionalidades existentes:** F-080 a F-083.
- **Quem poderá utilizar:** Administrador do Sistema; Direção (consulta).
- **Pré-requisitos:** nenhum.
- **Fluxo funcional:** gestão de usuários/permissões → consulta de auditoria → gestão de alertas → monitoramento de saúde do sistema.
- **Entradas:** dados de usuário, papel/área, configuração de alerta.
- **Processamentos:** controle de acesso por área de negócio (CG-07); tratamento padrão de alertas (RN-047).
- **Saídas:** usuários e permissões configurados; log de auditoria consultável; alertas geridos.
- **Validações:** todo usuário pertence a ao menos uma área de negócio.
- **Restrições:** nenhuma alteração de permissão sem registro de quem a fez.
- **Mensagens importantes:** tentativa de acesso fora da área permitida.
- **Alertas:** herdados de RN-047 (regra geral de alertas), geridos de forma centralizada aqui.
- **Automações:** nenhuma própria — administra as automações definidas nas demais regras.
- **Integrações com outros módulos:** todos (governança transversal).
- **Regras de auditoria:** todo alerta, seu tratamento e responsável são registrados permanentemente (RN-047); toda alteração de permissão é registrada.
- **Indicadores relacionados:** tempo médio de tratamento de alerta, número de usuários ativos.

**F-080 — Gerenciar Usuários e Permissões por Área de Negócio**
Objetivo: garantir que cada usuário tenha acesso apenas ao que sua função exige | Executa: Administrador do Sistema | Dispara: admissão, mudança de função ou desligamento de um usuário | Fluxo: 1) usuário é vinculado a uma ou mais Áreas da Empresa 2) permissões de criar/alterar/excluir/visualizar seguem o que cada módulo já define | Regras: CG-07 e as regras "Quem pode..." de cada Módulo | Entradas: usuário, área(s) de negócio | Saídas: permissões configuradas | Dados: nenhuma entidade de negócio própria — governança de acesso | Dependências: nenhuma | Resultado esperado: acesso alinhado à responsabilidade real de cada pessoa | Exceções: nenhuma | Auditoria: toda alteração de permissão é registrada com autor e data.

**F-081 — Consultar Log de Auditoria**
Objetivo: dar visibilidade completa de quem fez o quê e quando | Executa: Administrador do Sistema, Direção | Dispara: consulta ou investigação | Fluxo: 1) usuário filtra por entidade, período ou responsável 2) sistema exibe o histórico correspondente | Regras: CG-01 (histórico obrigatório, base de todo o log) | Entradas: filtros de consulta | Saídas: trilha de auditoria | Dados: histórico de todas as entidades | Dependências: nenhuma | Resultado esperado: rastreabilidade total do sistema | Exceções: nenhuma | Auditoria: a própria consulta é uma leitura, sem gerar novo registro de alteração.

**F-082 — Gerenciar Alertas do Sistema**
Objetivo: garantir que nenhum alerta gerado por qualquer regra se perca | Executa: Administrador do Sistema; cada área, para os alertas de sua responsabilidade | Dispara: geração de qualquer alerta previsto no Business Rules Specification | Fluxo: conforme RN-047 | Regras: RN-047 | Entradas: alerta gerado por qualquer regra | Saídas: alerta com status (pendente, visto, tratado) | Dados: nenhuma entidade de negócio própria — mecanismo transversal | Dependências: nenhuma | Resultado esperado: nenhuma condição crítica passa despercebida | Exceções: nenhuma | Auditoria: todo alerta e seu tratamento são registrados permanentemente.

**F-083 — Consultar Indicadores de Saúde do Sistema**
Objetivo: dar visibilidade sobre o uso e a integridade geral do sistema (não do negócio em si) | Executa: Administrador do Sistema | Dispara: consulta | Fluxo: 1) sistema consolida volume de uso, alertas pendentes, parâmetros de Configurações ainda não definidos | Regras: — | Entradas: nenhuma | Saídas: painel de saúde administrativa | Dados: derivado de todos os módulos | Dependências: nenhuma | Resultado esperado: visibilidade de pendências de configuração e uso do sistema | Exceções: nenhuma | Auditoria: leitura.

### Módulo 26 — Metas *(novo, adicionado em v1.2.0 — resolve o gap G-002)*

- **Objetivo do módulo:** ser o único lugar do sistema onde Metas são criadas, geridas e encerradas — o Dashboard CEO apenas consome e apresenta o que este módulo produz.
- **Funcionalidades existentes:** F-084 a F-091.
- **Quem poderá utilizar:** Direção (criação/gestão); demais áreas conforme responsabilidade atribuída à Meta.
- **Pré-requisitos:** Indicador associado já existente (Módulo 01/Dashboard CEO, ou de qualquer outro módulo).
- **Fluxo funcional:** criação (com período, indicador, responsável, valor-alvo e critério de sucesso definidos de uma vez) → acompanhamento contínuo → encerramento do ciclo → histórico permanente.
- **Entradas:** período, Indicador associado, responsável, valor-alvo, critério de sucesso.
- **Processamentos:** comparação contínua entre valor-alvo e valor real do Indicador; encerramento automático de ciclo (RN-046).
- **Saídas:** Meta em cada estado (Ativa, Atingida, Não atingida, Encerrada); Dashboard de Metas.
- **Validações:** toda Meta exige um Indicador mensurável associado (Regra Global do Domain Model).
- **Restrições:** Meta encerrada não é reaberta — apenas duplicada para novo ciclo (F-087).
- **Mensagens importantes:** atraso no progresso; ciclo concluído.
- **Alertas:** atraso (progresso abaixo do esperado para a data); conclusão de ciclo (RN-046).
- **Automações:** encerramento automático de ciclo com marcação "Atingida"/"Não atingida" (RN-046).
- **Integrações com outros módulos:** Dashboard CEO (consumo, nunca gestão), Indicadores (associação), todas as áreas como possíveis responsáveis.
- **Regras de auditoria:** todo ciclo de Meta (ativo, atingido ou não) é preservado permanentemente (RN-046, CG-01); toda justificativa registrada é imutável após o registro.
- **Indicadores relacionados:** taxa de metas atingidas, tempo médio de atraso.

**F-084 — Criar Meta**
Objetivo: registrar um novo objetivo quantitativo para um período | Executa: Direção | Dispara: definição de objetivo de gestão | Fluxo: 1) usuário define período, Indicador associado, responsável, valor-alvo e critério de sucesso, em uma única operação 2) Meta entra "Ativa" | Regras: Regra Global de Metas do Domain Model | Entradas: período, Indicador, responsável, valor-alvo, critério de sucesso | Saídas: Meta criada | Dados: Meta, Indicador | Dependências: Indicador já existente | Resultado esperado: objetivo mensurável formalizado | Exceções: nenhum Indicador correspondente bloqueia a criação | Auditoria: criação registrada.

**F-085 — Editar Meta**
Objetivo: ajustar uma Meta ainda em curso | Executa: Direção | Dispara: necessidade de revisão (ex.: mudança de cenário) | Fluxo: 1) usuário ajusta valor-alvo, período ou responsável 2) alteração é registrada com histórico | Regras: CG-01 | Entradas: campo(s) a alterar | Saídas: Meta atualizada | Dados: Meta | Dependências: Meta "Ativa" | Resultado esperado: Meta sempre refletindo o objetivo real vigente | Exceções: Meta encerrada não pode ser editada | Auditoria: toda edição preserva o valor anterior.

**F-086 — Encerrar Meta (Ciclo)**
Objetivo: formalizar o fim de um ciclo de Meta | Executa: sistema (automático, RN-046), Direção (encerramento antecipado) | Dispara: fim do período definido, ou decisão da Direção | Fluxo: conforme RN-046 | Regras: RN-046 | Entradas: nenhuma (automático) ou motivo (encerramento antecipado) | Saídas: Meta "Atingida" ou "Não atingida" | Dados: Meta, Indicador | Dependências: Meta "Ativa" | Resultado esperado: resultado do ciclo formalizado e notificado | Exceções: nenhuma | Auditoria: todo ciclo preservado permanentemente.

**F-087 — Duplicar Meta**
Objetivo: reaproveitar a estrutura de uma Meta anterior para um novo ciclo | Executa: Direção | Dispara: necessidade de repetir um objetivo em novo período | Fluxo: 1) usuário seleciona Meta encerrada como modelo 2) novo período é definido 3) nova Meta "Ativa" é criada | Regras: — | Entradas: Meta de origem, novo período | Saídas: nova Meta criada | Dados: Meta | Dependências: Meta de origem existente | Resultado esperado: agilidade na definição de metas recorrentes | Exceções: nenhuma | Auditoria: nova Meta registra a Meta de origem que a inspirou.

**F-088 — Acompanhar Progresso e Comparar Meta x Realizado**
Objetivo: visualizar, a qualquer momento, o quão perto a Meta está de ser atingida | Executa: Direção, responsável pela Meta | Dispara: consulta, ou verificação periódica automática | Fluxo: 1) sistema compara valor atual do Indicador com o valor-alvo 2) calcula percentual de progresso | Regras: RN-046 (base de comparação) | Entradas: Meta selecionada | Saídas: progresso atual, alerta de atraso quando aplicável | Dados: Meta, Indicador | Dependências: Indicador com valor atualizado | Resultado esperado: gestão proativa, não apenas no encerramento do ciclo | Exceções: nenhuma | Auditoria: leitura; alerta de atraso é registrado (ver Módulo 25 — Alertas).

**F-089 — Consultar Histórico de Metas**
Objetivo: visualizar todas as Metas passadas, atingidas ou não | Executa: Direção | Dispara: consulta | Fluxo: 1) usuário filtra por período/responsável/Indicador 2) sistema lista Metas correspondentes | Regras: CG-01 | Entradas: filtros | Saídas: histórico de Metas | Dados: Meta | Dependências: nenhuma | Resultado esperado: aprendizado histórico de gestão por metas | Exceções: nenhuma | Auditoria: leitura.

**F-090 — Registrar Justificativa de Meta**
Objetivo: documentar o motivo de uma Meta não ter sido atingida (ou ter sido superada) | Executa: responsável pela Meta, Direção | Dispara: encerramento de ciclo (F-086) | Fluxo: 1) usuário registra justificativa 2) justificativa fica permanentemente vinculada ao ciclo | Regras: CG-01 | Entradas: texto de justificativa | Saídas: justificativa registrada | Dados: Meta | Dependências: Meta encerrada | Resultado esperado: aprendizado organizacional preservado, não apenas o número final | Exceções: nenhuma | Auditoria: justificativa é imutável após registrada.

**F-091 — Visualizar Dashboard de Metas**
Objetivo: apresentar, de forma consolidada, todas as Metas ativas e seu progresso | Executa: Direção, responsáveis pelas Metas | Dispara: acesso à tela do módulo | Fluxo: 1) sistema agrega todas as Metas ativas e seus progressos | Regras: RN-039 (mesma regra geral de composição de Dashboard por Indicador) | Entradas: nenhuma | Saídas: painel de Metas | Dados: Meta, Indicador | Dependências: Metas ativas existentes | Resultado esperado: visão dedicada de metas, consumida (não gerida) também pelo Dashboard CEO | Exceções: nenhuma | Auditoria: leitura.

### Módulo 27 — Bancos *(novo, adicionado em v1.2.0 — resolve o gap G-001 e parte do G-003)*

- **Objetivo do módulo:** centralizar toda a gestão bancária do sistema — cadastro de Bancos, Contas e Cartões — servindo como fonte única de dado para o Financeiro Pessoal, o Financeiro Empresarial e a Importação/Conciliação de Extratos.
- **Funcionalidades existentes:** F-092 a F-098.
- **Quem poderá utilizar:** Financeiro; Direção (consulta).
- **Pré-requisitos:** nenhum para cadastro de Banco.
- **Fluxo funcional:** cadastro de Banco → cadastro de Conta/Cartão (classificados por tipo) → consulta de saldo/histórico → uso pelos módulos Financeiro Pessoal, Financeiro Empresarial e Inteligência Artificial (importação/conciliação).
- **Entradas:** dados do Banco, dados da Conta/Cartão, tipo (pessoal, empresarial, cartão, digital, investimento, internacional).
- **Processamentos:** classificação por tipo; consolidação de saldo por Conta/Banco.
- **Saídas:** Banco/Conta/Cartão cadastrados; saldo e histórico consultáveis.
- **Validações:** toda Conta pertence a um único Banco; todo Pagamento referencia uma Conta existente e ativa.
- **Restrições:** Conta/Cartão encerrado não recebe novo Pagamento.
- **Mensagens importantes:** nenhuma própria além das já herdadas de RN-043/RN-044.
- **Alertas:** herdados de RN-043 (importação) e RN-044 (conciliação), agora com o cadastro que lhes faltava.
- **Automações:** nenhuma própria — fornece a base de dados para as automações já existentes em RN-043/RN-044/RN-045.
- **Integrações com outros módulos:** Financeiro Pessoal (F-003, F-004), Financeiro Empresarial (F-005 a F-010), Inteligência Artificial (F-068, importação de extrato), Dashboard CEO/Financeiro (consumo consolidado).
- **Regras de auditoria:** toda alteração de cadastro, status ou saldo inicial é registrada com histórico (CG-01).
- **Indicadores relacionados:** saldo consolidado por tipo de Conta, número de Contas ativas.

**Nota de modelagem:** "Cartão" foi tratado como um **tipo/subtipo de Conta** (entidade já existente no Domain Model), e não como uma nova entidade — para não violar a restrição desta fase de não alterar entidades. Caso o proprietário deseje que Cartão tenha ciclo de vida próprio (fatura, limite, vencimento, como uma entidade distinta), isso deve ser tratado em uma futura revisão formal do Domain Model (TCOS-002), fora do escopo desta atualização. O mesmo vale para "Conta Internacional" (tratada como Conta com atributo de moeda), sem criar nova entidade.

**F-092 — Cadastrar Banco**
Objetivo: registrar uma instituição financeira | Executa: Financeiro | Dispara: necessidade de nova relação bancária | Fluxo: 1) dados do Banco são informados 2) Banco entra "Ativo" | Regras: CG-02 | Entradas: nome do Banco | Saídas: Banco cadastrado | Dados: Banco | Dependências: nenhuma | Resultado esperado: base para cadastro de Contas | Exceções: nenhuma | Auditoria: criação registrada.

**F-093 — Cadastrar/Editar Conta (Pessoal, Empresarial, Digital ou de Investimento)**
Objetivo: registrar uma conta bancária vinculada a um Banco | Executa: Financeiro | Dispara: abertura de nova conta ou necessidade de cadastrá-la no sistema | Fluxo: 1) Banco de vínculo é selecionado 2) tipo de Conta é classificado (pessoal, empresarial, digital, investimento, internacional) 3) Conta entra "Ativa" | Regras: Regras Globais Financeiras do Domain Model | Entradas: Banco, tipo, identificação da Conta, moeda (se internacional) | Saídas: Conta cadastrada/atualizada | Dados: Conta, Banco | Dependências: Banco cadastrado | Resultado esperado: base de dado que F-005 a F-008 e F-003/F-004 já utilizavam, agora efetivamente cadastrável | Exceções: nenhuma | Auditoria: toda alteração preserva histórico.

**F-094 — Cadastrar/Gerenciar Cartão**
Objetivo: registrar um Cartão (crédito/débito) vinculado a uma Conta | Executa: Financeiro | Dispara: necessidade de cadastrar um Cartão usado pela empresa ou pessoalmente | Fluxo: 1) Conta de vínculo é selecionada 2) dados do Cartão (limite, vencimento de fatura, quando aplicável) são informados | Regras: Regras Globais Financeiras do Domain Model | Entradas: Conta de vínculo, limite, vencimento | Saídas: Cartão cadastrado (como Conta do tipo "Cartão") | Dados: Conta (tipo Cartão) | Dependências: Conta/Banco cadastrados | Resultado esperado: gastos em Cartão rastreáveis como qualquer outro Pagamento | Exceções: nenhuma | Auditoria: toda alteração preserva histórico.

**F-095 — Inativar/Encerrar Conta ou Cartão**
Objetivo: registrar o encerramento de uma relação bancária | Executa: Financeiro | Dispara: encerramento de conta/cartão | Fluxo: 1) usuário solicita encerramento 2) Conta passa a "Encerrada", preservando o histórico | Regras: Regras Globais Financeiras do Domain Model | Entradas: Conta/Cartão selecionado, motivo (opcional) | Saídas: Conta "Encerrada" | Dados: Conta | Dependências: nenhuma | Resultado esperado: nenhum novo Pagamento é possível na Conta encerrada | Exceções: nenhuma | Auditoria: encerramento registrado permanentemente.

**F-096 — Consultar Saldo e Status de Conta**
Objetivo: visualizar o saldo atual e o status de cada Conta/Cartão | Executa: Financeiro, Direção | Dispara: consulta | Fluxo: 1) usuário seleciona Conta/Banco 2) sistema exibe saldo e status | Regras: Regra de Fluxo de Caixa do Domain Model | Entradas: Conta/Banco selecionado | Saídas: saldo, status | Dados: Conta, Pagamento | Dependências: nenhuma | Resultado esperado: visibilidade real de posição bancária | Exceções: nenhuma | Auditoria: leitura.

**F-097 — Consultar Histórico de Movimentações por Conta**
Objetivo: visualizar todos os Pagamentos associados a uma Conta | Executa: Financeiro | Dispara: consulta ou preparação de conciliação (RN-044) | Fluxo: 1) usuário seleciona a Conta 2) sistema lista Pagamentos | Regras: RN-044 | Entradas: Conta selecionada, período | Saídas: histórico de movimentações | Dados: Conta, Pagamento | Dependências: Pagamentos já registrados | Resultado esperado: base para conciliação e auditoria financeira | Exceções: nenhuma | Auditoria: leitura.

**F-098 — Visualizar Dashboard Financeiro Consolidado (Bancos e Contas)**
Objetivo: apresentar a posição consolidada de todos os Bancos, Contas e Cartões | Executa: Financeiro, Direção | Dispara: acesso à tela do módulo | Fluxo: 1) sistema agrega saldo e status de todas as Contas | Regras: RN-039 | Entradas: nenhuma | Saídas: painel financeiro consolidado | Dados: Banco, Conta | Dependências: Contas cadastradas | Resultado esperado: visão bancária dedicada, consumida (não gerida) também pelo Dashboard CEO | Exceções: nenhuma | Auditoria: leitura.

---

## 4. Matriz Funcional

### 4.1 Módulos e Quantidade de Funcionalidades

| # | Módulo | Funcionalidades | Faixa |
|---|---|---|---|
| 01 | Dashboard CEO | 2 | F-001–F-002 |
| 02 | Financeiro Pessoal | 2 | F-003–F-004 |
| 03 | Financeiro Empresarial | 6 | F-005–F-010 |
| 04 | CRM | 2 | F-011–F-012 |
| 05 | Clientes | 3 | F-013–F-015 |
| 06 | Leads | 4 | F-016–F-019 |
| 07 | Eventos | 5 | F-020–F-024 |
| 08 | Orçamentos | 4 | F-025–F-028 |
| 09 | Contratos | 3 | F-029–F-031 |
| 10 | Produção | 4 | F-032–F-035 |
| 11 | Engenharia de Custos | 3 | F-036–F-038 |
| 12 | Receitas | 3 | F-039–F-041 |
| 13 | Fichas Técnicas | 3 | F-042–F-044 |
| 14 | Precificação | 3 | F-045–F-047 |
| 15 | Compras | 4 | F-048–F-051 |
| 16 | Estoque | 3 | F-052–F-054 |
| 17 | Lotes | 2 | F-055–F-056 |
| 18 | Equipamentos | 3 | F-057–F-059 |
| 19 | Funcionários | 3 | F-060–F-062 |
| 20 | Escalas | 2 | F-063–F-064 |
| 21 | Marketing | 3 | F-065–F-067 |
| 22 | Inteligência Artificial | 4 | F-068–F-071 |
| 23 | Documentos | 3 | F-072–F-074 |
| 24 | Configurações | 5 | F-075–F-079 |
| 25 | Administração do Sistema | 4 | F-080–F-083 |
| 26 | Metas *(v1.2.0)* | 8 | F-084–F-091 |
| 27 | Bancos *(v1.2.0)* | 7 | F-092–F-098 |
| **Total** | **27 módulos** | **98 funcionalidades** | F-001–F-098 |

### 4.2 Dependências entre Módulos (visão de negócio, sem tecnologia)

```
Configurações ──► Produção, Precificação, Escalas, Eventos (fornece parâmetros)
Leads ──► Clientes ──► Orçamentos ──► Contratos ──► Eventos
Fichas Técnicas ◄── Receitas ◄── (Ingrediente, coberto no Domain Model)
Fichas Técnicas ──► Engenharia de Custos ──► Precificação ──► Orçamentos
Eventos ──► Produção ──► Compras ──► Estoque ──► Lotes
Eventos ──► Equipamentos, Escalas ──► Funcionários
Eventos, Contratos, Compras, Funcionários ──► Financeiro Empresarial ──► Dashboard CEO
Financeiro Pessoal ──► Financeiro Empresarial (nunca o contrário)
CRM ◄── Leads, Clientes, Marketing (consolida, não origina dado)
Inteligência Artificial ──► Financeiro Empresarial (extrato), Compras (previsão), Precificação (sugestão) — sempre como apoio, nunca decisão sozinha
Documentos ◄── Contratos, Compras, Clientes, Fornecedores, Eventos (gerados a partir deles)
Administração do Sistema ──► todos (governança de acesso e alertas, transversal)
Bancos ──► Financeiro Pessoal, Financeiro Empresarial, Inteligência Artificial (importação/conciliação) — fornece o cadastro que esses módulos já consumiam (v1.2.0)
Metas ──► Dashboard CEO (apenas consumo/apresentação, nunca gestão — v1.2.0)
```

### 4.3 Funcionalidades Críticas

Consideradas críticas por protegerem margem, segurança alimentar ou integridade financeira — falha nelas compromete diretamente o negócio:
- F-021 (Confirmar Evento — orquestração completa, RN-006).
- F-024 (Cancelar Evento — impacto financeiro e liberação de recursos, RN-007).
- F-036 (Calcular Custo Total do Evento, RN-018).
- F-046 (Calcular Preço de Produto/Pacote, RN-022).
- F-047 (Aprovar Exceção de Margem, RN-023).
- F-050 (Receber e Conferir Compra, RN-031).
- F-056 (Registrar Vencimento ou Descarte de Lote — segurança alimentar, RN-034).
- F-068 (Sugerir Categorização de Lançamento Financeiro — ponto de entrada da IA no Financeiro, RN-043).
- F-075 a F-079 (Configurações — sem elas, 8 das 47 Regras de Negócio operam apenas em modo de alerta/bloqueio, nunca automaticamente).
- F-092, F-093 (Cadastrar Banco/Conta — sem elas, F-005 a F-008 e F-003/F-004 não têm sobre o que operar; adicionadas em v1.2.0).

### 4.4 Funcionalidades Futuras (Roadmap, fora do escopo atual)

Identificadas durante a auditoria como valiosas, mas não obrigatórias nesta fase — candidatas a versões futuras, não anexadas ao escopo dos 25 módulos mínimos:
- Aplicativo mobile para consulta de Escala/Evento pela equipe de campo (já previsto na Filosofia de Evolução, Seção 25 do Framework).
- Portal do Cliente (consulta de Orçamento/Contrato/status do Evento diretamente pelo Cliente).
- Integração bancária automatizada bidirecional (hoje, RN-043 trata apenas importação; pagamento automatizado a Fornecedor é um passo futuro).
- Simulador de cenário no Dashboard CEO (ex.: "e se eu aumentar a margem-alvo em 2%?").
- Módulo de RH mais amplo (férias, benefícios), além do escopo atual de Funcionários/Escalas.

---

## 5. Resumo para o Proprietário

O THE CHARCOAL OS agora tem uma lista completa e organizada de tudo que qualquer pessoa vai poder fazer dentro do sistema, separada em 25 áreas (Dashboard, Financeiro, Vendas, Produção, Estoque, Pessoas, Marketing, IA, entre outras), somando 83 ações concretas — desde "cadastrar um cliente" até "confirmar um evento e deixar o sistema organizar sozinho a produção, as compras e a escala".

Isso importa porque, até agora, os documentos anteriores diziam **o que é** cada coisa (Cliente, Evento, Receita) e **como o sistema deve se comportar** (regras). Este documento diz, de forma prática, **o que cada pessoa da equipe vai conseguir clicar e fazer** — é a ponte entre a teoria do negócio e a tela que, no futuro, será construída.

Um destaque importante: foi criado um módulo específico chamado "Configurações", que é exatamente o lugar onde ficarão os números que ainda faltam confirmar (quanto de carne por pessoa, quanto se perde na limpeza, qual a margem mínima, quantas pessoas por evento). Sem preencher essas configurações, o sistema vai alertar e pedir a informação — ele nunca vai "chutar" um número sozinho.

Este documento se conecta a todos os anteriores: usa exatamente as mesmas entidades do Domain Model, aciona exatamente as mesmas regras do Business Rules Specification, e vai ser a referência direta para a próxima etapa, quando decidirmos como o sistema será construído por dentro (banco de dados, telas, tecnologia) — nada disso foi definido ainda.

---

## 6. TCOS QUALITY GATE EXECUTIVO

**1. Resumo Executivo**
Produzido o TCOS-003, especificando 83 funcionalidades em 25 módulos obrigatórios, cada uma com os 13 campos exigidos, mais Matriz Funcional, dependências entre módulos, funcionalidades críticas e roadmap futuro. Nenhuma decisão técnica foi tomada.

**2. O que foi criado nesta fase**
`THE_CHARCOAL_OS_FUNCTIONAL_SPECIFICATION.md` (v1.0.0): 25 módulos com os 16 campos obrigatórios cada, 83 funcionalidades com os 13 campos obrigatórios cada, Matriz Funcional completa, Resumo para o Proprietário e este Quality Gate.

**3. Estado atual do projeto**
Fases 000, 001 e 002/002A encerradas/aprovadas; Fase 003 (Functional Specification) em validação. Nenhuma fase técnica (Arquitetura, Banco de Dados, UX/UI, APIs) foi iniciada.

**4. Documentos oficiais existentes**
Os 7 já registrados na Executive Memory, mais este documento em rascunho.

**5. Pendências abertas**
Validação formal deste documento; confirmação dos parâmetros de negócio (agora com lugar funcional definido — Módulo 24); decisão sobre retomar a entrevista de descoberta.

**6. Dúvidas encontradas**
As mesmas já registradas no TCOS-002A (parâmetros de consumo, perdas, margem, escala, política de cancelamento), agora também associadas a uma funcionalidade concreta (F-075 a F-079) que as tornará operacionais assim que respondidas.

**7. Riscos identificados**
R-000-03/R-002-01 e R-001-01/R-002-02 (herdados); R-002A-01 (herdado, agora com Módulo 24 como mitigação funcional). Nenhum risco novo específico desta fase.

**8. Inconsistências encontradas**
Nenhuma nova. Todas as 47 Regras de Negócio do TCOS-002A foram mapeadas a pelo menos uma funcionalidade — nenhuma regra ficou sem funcionalidade correspondente (ver auditoria de abertura).

**9. Melhorias sugeridas**
- Considerar, ao construir F-075 a F-079, um "assistente de configuração inicial" que guie o proprietário na primeira definição de todos os parâmetros pendentes de uma vez, em vez de descobri-los um a um.
- As funcionalidades listadas no Roadmap (Seção 4.4) devem ser reavaliadas após a maturidade dos 25 módulos atuais.

**10. Impacto desta fase nas próximas**
Esta especificação passa a ser a referência de escopo funcional obrigatória para a futura Arquitetura, Banco de Dados, UX/UI e APIs — nenhuma dessas fases deve propor uma tela ou fluxo técnico que não corresponda a uma funcionalidade aqui listada, sem registrar formalmente a mudança de escopo (Seção 11 do Framework).

**11. Nota da fase: 9/10**
Justificativa: cobertura completa dos 25 módulos exigidos e das 47 Regras de Negócio, com rastreabilidade explícita entre funcionalidade e regra. Não é 10 porque a precisão de várias funcionalidades de cálculo (Produção, Precificação, Escalas) permanece condicionada a parâmetros de Configurações ainda não preenchidos por dados reais do proprietário.

**12. Próxima fase recomendada**
Aguardar validação do proprietário. Recomenda-se, antes de Arquitetura/Banco de Dados/UX/APIs, uma decisão explícita sobre retomar a entrevista de descoberta para preencher os parâmetros do Módulo 24 com dados reais — isso reduz retrabalho nas fases técnicas futuras.

**13. Atualização do PROJECT_MEMORY.md:** ver commit correspondente.

**Métricas de Encerramento (Seção 30 do Framework):**
- Quantidade de páginas: 1 documento, ~30 páginas equivalentes (estimado por densidade de conteúdo).
- Quantidade de entidades: não aplicável a este documento (entidades pertencem ao Domain Model, TCOS-002).
- Quantidade de regras: 0 novas (referencia as 47 já existentes do TCOS-002A, sem criar novas).
- Quantidade de processos: 25 (um por módulo, no sentido de fluxo funcional).
- Quantidade de eventos: não aplicável a este documento (eventos de domínio pertencem ao Domain Model).
- Quantidade de decisões: 4 (D-003-01 a D-003-04, ver `PROJECT_MEMORY.md`).
- Quantidade de riscos: 0 novos (3 herdados).
- Quantidade de pendências: 3 (validação do documento, parâmetros de Configurações, decisão sobre a entrevista).
- Quantidade de melhorias: 2.
- Percentual estimado de maturidade do projeto: **35%** (governança, descoberta de negócio, modelo de domínio, regras de negócio e especificação funcional completos; arquitetura, dados, UX e construção técnica ainda não iniciados).

---

## 7. VALIDAÇÃO DE COBERTURA FUNCIONAL *(capítulo permanente, adicionado em v1.1.0)*

Este capítulo é permanente: toda futura versão deste documento deve manter e atualizar estas matrizes, nunca removê-las. Nenhum conteúdo das Seções 0 a 6 (v1.0.0) foi alterado para produzir este capítulo — apenas leitura e verificação cruzada do que já existia.

### 7.1 Matriz — Entidades do Domain Model → Funcionalidades

| # | Entidade | Funcionalidades que a criam/alteram | Módulo | Cobertura |
|---|---|---|---|---|
| 1 | Cliente | F-013, F-014, F-015, F-018 | 05, 06 | Direta |
| 2 | Lead | F-016, F-017, F-018, F-019 | 06 | Direta |
| 3 | Orçamento | F-025, F-026, F-027, F-028 | 08 | Direta |
| 4 | Contrato | F-029, F-030, F-031 | 09 | Direta |
| 5 | Campanha | F-065, F-066, F-067 | 21 | Direta |
| 6 | Produto | F-046 (preço), F-040 (origem via Receita) | 12, 14 | **Parcial** — usado, sem cadastro/publicação de catálogo próprio |
| 7 | Ingrediente | F-042, F-048, F-052 (usado) | 13, 15, 16 | **Parcial** — usado, sem funcionalidade explícita de cadastro |
| 8 | Receita | F-039, F-040, F-041 | 12 | Direta |
| 9 | Ficha Técnica | F-042, F-043, F-044 | 13 | Direta |
| 10 | Produção | F-032, F-033, F-034, F-035 | 10 | Direta |
| 11 | Fornecedor | F-048, F-049, F-051 (usado) | 15 | **Parcial** — usado, sem funcionalidade explícita de cadastro |
| 12 | Compra | F-048, F-049, F-050, F-051 | 15 | Direta |
| 13 | Estoque | F-052, F-053, F-054 (+ automático via F-032/F-050) | 16 | Direta |
| 14 | Lote | F-055, F-056 | 17 | Direta |
| 15 | Equipamento | F-057, F-058, F-059 | 18 | Direta |
| 16 | Veículo | F-057, F-058, F-059 (agrupado com Equipamento) | 18 | Direta |
| 17 | Despesa | F-005, F-007, F-009, F-010 | 03 | Direta |
| 18 | Receita Financeira | F-006, F-007, F-009 | 03 | Direta |
| 19 | Pagamento | F-007 | 03 | Direta |
| 20 | Banco | F-092 *(v1.2.0)* | 27 | **Direta** *(resolvido — era Ausente na v1.1.0)* |
| 21 | Conta | F-093, F-094, F-095, F-096, F-097 *(v1.2.0)*, + usada em F-005 a F-008 | 27, 03 | **Direta** *(resolvido — era Parcial na v1.1.0)* |
| 22 | Fluxo de Caixa | F-008 | 03 | Direta |
| 23 | Funcionário | F-060, F-061, F-062 | 19 | Direta |
| 24 | Alocação de Funcionário | F-063, F-064 | 20 | Direta |
| 25 | Documento | F-072, F-073, F-074 | 23 | Direta |
| 26 | Meta | F-084 a F-090 *(v1.2.0)* | 26 | **Direta** *(resolvido — era Ausente na v1.1.0)* |
| 27 | Indicador | F-001, F-002 (selecionado/usado) | 01 | **Parcial** — usado, sem funcionalidade explícita de definição de fórmula |
| 28 | Dashboard | F-001, F-002, F-091, F-098 | 01, 26, 27 | Direta |
| 29 | Pacote | F-046 (usado em precificação/orçamento) | 08, 14 | **Parcial** — usado, sem funcionalidade explícita de criação |
| 30 | Evento | F-020, F-021, F-022, F-023, F-024 | 07 | Direta |

**Resultado (v1.2.0):** 25 entidades com cobertura Direta (+3 desde a v1.1.0: Banco, Conta, Meta), 5 com cobertura Parcial (Produto, Ingrediente, Fornecedor, Indicador, Pacote), 0 Ausentes. Detalhamento no item 7.8 (Gaps).

### 7.2 Matriz — Regras de Negócio (TCOS-002A) → Funcionalidades

| RN | Nome | Funcionalidade(s) principal(is) | Cobertura |
|---|---|---|---|
| RN-001 | Atualização do Dashboard CEO | F-001 | Direta |
| RN-002 | Retirada Pessoal como Despesa | F-003, F-004 | Direta |
| RN-003 | Apuração de Resultado por Evento | F-009, F-023 | Direta |
| RN-004 | Fechamento de Período | F-010 | Direta |
| RN-005 | Lançamento de Natureza Ambígua | F-003 | Direta |
| RN-006 | Confirmação de Evento (Orquestração) | F-021 | Direta |
| RN-007 | Cancelamento de Evento | F-024 | Direta |
| RN-008 | Atribuição de Origem ao Lead | F-016 | Direta |
| RN-009 | Conversão de Lead sem Duplicidade | F-013, F-018 | Direta |
| RN-010 | Fidelização de Cliente | Módulo 05 (automação) | **Indireta** — sem F dedicado |
| RN-011 | Perda de Lead por Inatividade | F-019 | Direta |
| RN-012 | Cálculo de Preço no Orçamento | F-025, F-046 | Direta |
| RN-013 | Expiração de Orçamento | F-026, F-028 | Direta |
| RN-014 | Geração Automática de Contrato | F-029, F-072 | Direta |
| RN-015 | Aditivo Contratual | F-031 | Direta |
| RN-016 | Planejamento de Produção | F-032 | Direta |
| RN-017 | Planejado vs. Real | F-035, F-023 | Direta |
| RN-018 | Custo Total do Evento | F-036, F-009 | Direta |
| RN-019 | Recálculo por Custo de Ingrediente | F-037, F-043 | Direta |
| RN-020 | Versionamento de Receita | F-041 | Direta |
| RN-021 | Bloqueio sem Ficha Técnica Vigente | F-025, F-021(Mód.13) | Direta |
| RN-022 | Cálculo de Preço (Custo+Margem) | F-045, F-046 | Direta |
| RN-023 | Alerta de Margem Mínima | F-047, F-027 | Direta |
| RN-024 | Consumo por Pessoa | F-075, F-032 | Direta |
| RN-025 | Consumo por Tipo de Evento | F-075 | Direta |
| RN-026 | Consumo por Acompanhamento | F-075 | Direta |
| RN-027 | Perda de Limpeza | F-076, F-048 | Direta |
| RN-028 | Perda de Produção | F-034, F-076 | Direta |
| RN-029 | Rendimento | F-034, F-076 | Direta |
| RN-030 | Geração de Lista de Compras | F-048 | Direta |
| RN-031 | Recebimento e Conferência | F-050 | Direta |
| RN-032 | Baixa Automática de Estoque | F-033 | Direta |
| RN-033 | Ponto de Reposição | F-054 | Direta |
| RN-034 | Rastreabilidade/Validade de Lote | F-055, F-056 | Direta |
| RN-035 | Disponibilidade de Equipamento | F-058 | Direta |
| RN-036 | Custo de Mão de Obra | F-061 | Direta |
| RN-037 | Sugestão de Escala | F-063, F-078 | Direta |
| RN-038 | Retorno de Campanha | F-012, F-066 | Direta |
| RN-039 | Composição de Dashboard | F-001, F-002 | Direta |
| RN-040 | Cálculo Único de Indicador | F-001 | Direta |
| RN-041 | IA Auditável e Reversível | F-068, F-069, F-070, F-071 | Direta |
| RN-042 | Previsão de Demanda | F-069 | Direta |
| RN-043 | Importação de Extrato Bancário | F-007, F-068 | Direta |
| RN-044 | Conciliação Bancária | F-007 | Direta |
| RN-045 | Lançamento Manual | F-005, F-006 | Direta |
| RN-046 | Acompanhamento de Meta | F-084, F-086, F-088 *(v1.2.0)* | **Direta** *(resolvido — era Ausente na v1.1.0)* |
| RN-047 | Tratamento Padrão de Alerta | F-082 | Direta |

**Resultado (v1.2.0):** 46 de 47 Regras com cobertura Direta (+1 desde a v1.1.0: RN-046), 1 com cobertura Indireta (RN-010), 0 Ausentes. Detalhamento no item 7.8.

### 7.3 Funcionalidades que Dependem de Parâmetros Ainda Não Definidos

| Funcionalidade | Parâmetro pendente | Resolvida por |
|---|---|---|
| F-032 (Planejar Produção), F-024 (Cancelar Evento — via RN-007) | Consumo por pessoa/tipo/acompanhamento (RN-024–026) | F-075 |
| F-042/F-043 (Ficha Técnica), F-034 (Perdas/Rendimento) | Fatores de perda e rendimento esperado (RN-027–029) | F-076 |
| F-045/F-046 (Precificação), F-025 (Orçamento) | Margem-alvo (RN-022) | F-077 |
| F-063 (Sugestão de Escala) | Proporção de equipe por porte de Evento (RN-037) | F-078 |
| F-024 (Cancelar Evento) | Política de reembolso/multa (RN-007) | F-079 |

Enquanto os parâmetros acima não forem definidos via Módulo 24, estas funcionalidades operam em modo de alerta/bloqueio (nunca assumem valor), conforme já registrado no risco R-002A-01.

### 7.4 Funcionalidades que Dependem de Futuras Integrações

| Funcionalidade | Integração futura necessária |
|---|---|
| F-007 (Registrar/Consultar Pagamento) | Integração bancária para conciliação automatizada em escala (hoje prevista apenas como importação, RN-043) |
| F-068 (Sugerir Categorização de Lançamento) | Integração com o formato de extrato do(s) banco(s) reais utilizados |

Nenhuma outra das 83 funcionalidades depende de integração externa para funcionar; as demais dependências são apenas entre módulos internos (Seção 4.2).

### 7.5 Funcionalidades Críticas

*(Consolidado da Seção 4.3, sem alteração de conteúdo, reunido aqui para referência única de auditoria):* F-021, F-024, F-036, F-046, F-047, F-050, F-056, F-068, F-075 a F-079.

### 7.6 Funcionalidades Opcionais

Funcionalidades cuja ausência temporária não impede a operação essencial do negócio (podem ser adiadas em uma primeira versão sem comprometer o core):
- F-002 (Configurar Indicadores do Dashboard CEO — pode operar com conjunto padrão inicialmente).
- F-044, F-074 (Consultar histórico de versões — importante para auditoria, não para a operação diária).
- F-051 (Consultar Histórico de Compras por Fornecedor).
- F-066, F-067 (Consultar Retorno de Campanha, Encerrar Campanha).
- F-070, F-071 (Sugerir Preço via IA, Configurar Nível de Automação de IA).
- F-083 (Consultar Indicadores de Saúde do Sistema).

### 7.7 Funcionalidades Futuras (Roadmap)

*(Consolidado da Seção 4.4, sem alteração de conteúdo)*: aplicativo mobile para equipe de campo; Portal do Cliente; integração bancária bidirecional automatizada; simulador de cenário no Dashboard CEO; módulo de RH ampliado.

### 7.8 Gaps Encontrados

**Gaps da v1.1.0 e seu status após a v1.2.0:**

1. ~~**Entidade Banco sem funcionalidade de cadastro.**~~ **RESOLVIDO em v1.2.0** pelo Módulo 27 (F-092).
2. ~~**Entidade Meta e Regra RN-046 sem cobertura.**~~ **RESOLVIDO em v1.2.0** pelo Módulo 26 (F-084 a F-090). Confirmado pelo proprietário: os gaps de Banco e Meta representam evolução natural do sistema, não falhas de execução da fase anterior.
3. **Produto, Ingrediente, Fornecedor, Indicador e Pacote continuam usados, mas sem funcionalidade explícita de cadastro/definição própria.** Não fazia parte do escopo desta complementação (limitada a Metas e Bancos). Recomendação: M-003A-03 (mantida em aberto).
4. **RN-010 (Fidelização de Cliente) continua citada apenas na descrição do Módulo 05**, sem funcionalidade dedicada — mantido como observação, não como falha (regra 100% automática). Recomendação: mantida em M-003A-03.

**Novos gaps identificados nesta auditoria (v1.2.0):**

5. **"Cartão" e "Conta Internacional" foram modelados como tipo/atributo de Conta, não como entidades próprias**, para não violar a restrição de não alterar entidades nesta fase. Se o proprietário desejar ciclo de vida próprio para Cartão (fatura, limite, vencimento como conceitos de primeira classe), isso exigirá uma revisão formal do Domain Model (TCOS-002) — fora do escopo desta atualização. Recomendação: M-003A-04.
6. **Nenhum gap de redundância entre módulos foi encontrado** (ver Seção 7.11 — Cobertura dos Módulos): Módulo 26 (Metas) e Módulo 27 (Bancos) têm escopo de gestão exclusivo e claramente distinto do Dashboard CEO (Módulo 01) e do Financeiro (Módulos 02/03), que passam a apenas consumir o que esses dois novos módulos produzem — sem sobreposição de responsabilidade.

Nenhum destes gaps invalida qualquer versão anterior já aprovada — são lacunas de granularidade, não inconsistências ou contradições, e ficam formalmente registradas para tratamento em versão futura.

### 7.9 Melhorias Sugeridas

- ~~M-003A-01~~ **Concluída em v1.2.0** (Módulo 27).
- ~~M-003A-02~~ **Concluída em v1.2.0** (Módulo 26).
- M-003A-03 (mantida): incluir, em uma futura versão, funcionalidades explícitas de cadastro para Produto (catálogo), Ingrediente, Fornecedor e Pacote, e de definição de fórmula de Indicador.
- M-003A-04 (nova): avaliar com o proprietário se "Cartão" deve se tornar uma entidade própria no Domain Model (com fatura, limite e vencimento como conceitos de primeira classe) em vez de um tipo de Conta.

### 7.11 Cobertura dos Módulos (Verificação de Redundância) *(nova em v1.2.0)*

Verificação explícita de que os 27 módulos não se sobrepõem em responsabilidade:

| Módulo | Escopo exclusivo | Módulo(s) relacionado(s) | Sobreposição? |
|---|---|---|---|
| 01 — Dashboard CEO | Consolidação e apresentação executiva geral | Todos (consumo) | Não — apenas consome, nunca gerencia dados de outros módulos |
| 26 — Metas | Criação, edição, encerramento e histórico de Metas | 01 (consumo via F-091) | Não — Dashboard CEO nunca cria/edita Meta, apenas exibe |
| 02 — Financeiro Pessoal | Retiradas pessoais como Despesa | 03, 27 | Não — trata exclusivamente da natureza "pessoal" do lançamento |
| 03 — Financeiro Empresarial | Despesa, Receita Financeira, Pagamento, Fluxo de Caixa operacionais | 02, 27 | Não — usa Conta/Banco cadastrados no Módulo 27, mas não os cadastra |
| 27 — Bancos | Cadastro e gestão de Banco, Conta e Cartão | 02, 03, 22 (IA) | Não — apenas cadastra e consulta; não lança Despesa/Receita Financeira |

Nenhuma redundância de responsabilidade foi encontrada entre os 27 módulos.

### 7.10 Resumo Executivo (Linguagem Simples)

Fizemos uma conferência completa: pegamos a lista de tudo que existe no sistema (as "peças" do negócio, como Cliente, Evento, Estoque) e a lista de todas as regras de comportamento já aprovadas, e verificamos, uma por uma, se cada uma delas tem uma ação correspondente que o usuário pode realizar.

O resultado é muito bom: praticamente tudo tem cobertura. Encontramos só algumas lacunas pequenas e específicas — por exemplo, hoje não existe uma tela explícita para "cadastrar um banco" ou "cadastrar um ingrediente novo do zero", embora essas informações já sejam usadas em várias partes do sistema. Isso não quebra nada do que já foi aprovado; é só uma lista de pequenos complementos para a próxima vez que revisarmos esta especificação.

Também descobrimos que "Metas" (uma das 36 áreas de comportamento já aprovadas) não tinha, ainda, uma tela própria — porque não estava na lista de 25 áreas pedida para esta etapa. Isso é uma decisão a ser confirmada com você: Metas vai ganhar sua própria área no sistema, ou vai ficar apenas dentro do Dashboard CEO?

Nada do que já foi aprovado mudou. Este capítulo só aponta, com transparência, o que ainda falta amarrar — exatamente para que nada seja esquecido mais adiante.

---

## 8. TCOS QUALITY GATE EXECUTIVO (v1.1.0)

**1. Resumo Executivo**
Adicionado o capítulo permanente "Validação de Cobertura Funcional" ao TCOS-003, cruzando as 30 entidades do Domain Model e as 47 Regras de Negócio do Business Rules Specification contra as 83 funcionalidades já aprovadas. Nenhum conteúdo da v1.0.0 foi alterado.

**2. O que foi criado nesta fase**
Duas matrizes de cobertura, lista de funcionalidades dependentes de parâmetros pendentes, lista de dependências de integrações futuras, consolidação de funcionalidades críticas/opcionais/roadmap, 4 gaps registrados, 3 melhorias sugeridas e um resumo em linguagem simples.

**3. Estado atual do projeto**
Fase 003 com conteúdo funcional aprovado e agora com validação de cobertura formal; nenhuma fase técnica iniciada.

**4. Documentos oficiais existentes**
Os mesmos 7 já registrados na Executive Memory da Seção 0, mais esta nova versão (v1.1.0) do TCOS-003.

**5. Pendências abertas**
Validação desta complementação; as mesmas pendências de parâmetros (agora com rastreabilidade explícita via Seção 7.3); decisão sobre M-003A-02 (módulo de Metas).

**6. Dúvidas encontradas**
Se "Metas" deve virar um 26º módulo funcional ou permanecer apenas como configuração da Direção dentro do Dashboard CEO.

**7. Riscos identificados**
Nenhum risco novo além dos já herdados (R-000-03/R-002-01, R-001-01/R-002-02, R-002A-01). A cobertura parcial de Produto/Ingrediente/Fornecedor/Conta/Pacote/Indicador é tratada como gap de granularidade, não como risco.

**8. Inconsistências encontradas**
Nenhuma. As lacunas encontradas (Seção 7.8) são gaps de granularidade/escopo, não contradições entre documentos.

**9. Melhorias sugeridas**
M-003A-01, M-003A-02, M-003A-03 (Seção 7.9).

**10. Impacto desta fase nas próximas**
As matrizes de cobertura tornam-se checklist obrigatório de conferência para qualquer fase técnica futura: nenhuma tela/API deve ser construída sem que sua funcionalidade correspondente já exista aqui (ou sem que o gap tenha sido formalmente resolvido antes).

**11. Nota da fase: 9/10**
Justificativa: auditoria de cobertura genuína e completa, com gaps reais encontrados e registrados (não uma checagem superficial "está tudo ok"). Não é 10 porque os gaps identificados (Banco, Meta, cadastros implícitos) precisarão ser resolvidos antes da fase técnica, sob risco de retrabalho.

**12. Próxima fase recomendada**
Aguardar validação do proprietário sobre esta complementação, incluindo decisão sobre M-003A-02 (Metas). Recomenda-se resolver os gaps da Seção 7.8 (via nova versão do TCOS-003) antes de avançar para Arquitetura/Banco de Dados/UX/APIs.

**13. Atualização do PROJECT_MEMORY.md:** ver commit correspondente.

**Métricas de Encerramento (Seção 30 do Framework):**
- Quantidade de páginas: +1 capítulo, ~8 páginas equivalentes adicionadas (total do documento ~38 páginas equivalentes).
- Quantidade de entidades: 30 auditadas (0 novas).
- Quantidade de regras: 47 auditadas (0 novas).
- Quantidade de processos: não aplicável a este capítulo (validação, não novo processo).
- Quantidade de eventos: não aplicável a este capítulo.
- Quantidade de decisões: 1 (D-003A-01, ver `PROJECT_MEMORY.md`).
- Quantidade de riscos: 0 novos.
- Quantidade de pendências: 1 nova (decisão sobre módulo de Metas), somada às já existentes.
- Quantidade de melhorias: 3 (M-003A-01 a M-003A-03).
- Percentual estimado de maturidade do projeto: **38%** (subiu de 35% para 38% — a validação de cobertura reduz o risco de retrabalho técnico futuro, mesmo com gaps identificados, porque agora são gaps *conhecidos e registrados*, não desconhecidos).

---

## 9. Estatísticas do Documento *(nova em v1.2.0)*

| Métrica | v1.1.0 | v1.2.0 | Variação |
|---|---|---|---|
| Módulos | 25 | 27 | +2 |
| Funcionalidades | 83 | 98 | +15 |
| Entidades do Domain Model cobertas (Direta) | 22 | 25 | +3 |
| Entidades do Domain Model cobertas (Parcial) | 6 | 5 | −1 (Conta passou a Direta; Banco e Meta não contavam aqui) |
| Entidades do Domain Model Ausentes | 2 | 0 | −2 |
| Regras de Negócio cobertas (Direta) | 45 | 46 | +1 |
| Regras de Negócio cobertas (Indireta) | 1 | 1 | 0 |
| Regras de Negócio Ausentes | 1 | 0 | −1 |
| Gaps abertos | 4 | 3 (+1 novo, ver 7.8) | — |
| Melhorias sugeridas em aberto | 3 | 2 | −1 |

## 10. TCOS QUALITY GATE EXECUTIVO (v1.2.0)

**Resumo Executivo**
Adicionados os Módulos 26 (Metas) e 27 (Bancos) ao TCOS-003, com 15 novas funcionalidades (F-084 a F-098), resolvendo os dois gaps reais identificados na auditoria de cobertura anterior (Banco e Meta), sem alterar nenhum conteúdo já aprovado (F-001–F-083, Módulos 01–25, Regras de Negócio, entidades ou integrações).

**Estado atual do projeto**
Fase 003 com escopo funcional agora cobrindo a totalidade das entidades e quase a totalidade das Regras de Negócio (46 de 47 diretamente); nenhuma fase técnica (Arquitetura, Banco de Dados, UX/UI, APIs) foi iniciada.

**Documentos oficiais**
Os mesmos 7 já registrados na Executive Memory da Seção 0, mais esta nova versão (v1.2.0) do TCOS-003.

**Novos módulos criados**
Módulo 26 — Metas (F-084 a F-091, 8 funcionalidades); Módulo 27 — Bancos (F-092 a F-098, 7 funcionalidades).

**Quantidade total de módulos:** 27.

**Quantidade total de funcionalidades:** 98 (F-001–F-098).

**Quantidade total de entidades cobertas:** 30 de 30 (25 Diretas, 5 Parciais, 0 Ausentes).

**Quantidade total de regras cobertas:** 47 de 47 (46 Diretas, 1 Indireta, 0 Ausentes).

**Pendências abertas**
- Validação formal do proprietário sobre a v1.2.0.
- M-003A-03: cadastro explícito de Produto/Ingrediente/Fornecedor/Pacote e definição de fórmula de Indicador.
- M-003A-04 (nova): decisão sobre Cartão como entidade própria no Domain Model.
- Confirmação dos parâmetros de negócio do Módulo 24 (herdada).

**Riscos ativos**
R-000-03/R-002-01, R-001-01/R-002-02, R-002A-01 (todos herdados, inalterados por esta complementação).

**Melhorias sugeridas**
M-003A-03 (mantida), M-003A-04 (nova).

**Percentual atualizado de maturidade do projeto: 42%**
(subiu de 38% para 42% — cobertura de entidades e regras praticamente completa reduz significativamente o risco de retrabalho nas fases técnicas futuras; o restante do percentual pendente reflete os parâmetros de negócio ainda não confirmados e a ausência de decisão técnica de arquitetura/dados/UX/API).

**Nota da fase: 9,5/10**
Justificativa: os dois gaps reais identificados foram resolvidos com módulos coerentes, sem retrabalho em nenhum conteúdo já aprovado, e com nova auditoria genuína (não apenas "carimbo") que identificou e registrou honestamente um gap adicional (Cartão como possível entidade própria). Não é 10 porque M-003A-03 permanece em aberto e ainda há parâmetros de negócio pendentes de confirmação real.

**Atualização do PROJECT_MEMORY.md:** ver commit correspondente.

---

*Fim do documento — THE CHARCOAL OS FUNCTIONAL SPECIFICATION v1.2.0*
