# THE CHARCOAL OS — UX/UI SPECIFICATION

**Documento:** TCOS-005 — Especificação de Experiência e Interface do Usuário
**Projeto:** THE CHARCOAL OS
**Fase:** 005 — UX/UI Specification
**Status:** Rascunho para validação do proprietário
**Versão:** 1.0.0

---

## EXECUTIVE MEMORY

- **Estado atual do projeto:** negócio, domínio, regras, funcionalidades e fluxos operacionais completos e oficiais; iniciando o projeto de experiência e interface, ainda sem nenhuma decisão de arquitetura, banco de dados ou código.
- **Fase atual:** 005 — UX/UI Specification (TCOS-005).
- **Fases concluídas:** 000 a 004, todas aprovadas e oficiais (a mais recente, TCOS-004, congelada nesta mensagem).
- **Documentos oficiais:** Framework (v1.2.0), `PROJECT_MEMORY.md`, Domain Discovery (v1.0.0), Business Discovery Questionnaire (v1.0.0), Discovery Interview Roadmap (v1.0.0), Domain Model (v1.0.0), Business Rules Specification (v1.0.0), Functional Specification (v1.2.0), User Journeys and System Flows (v1.0.0, congelado a partir de agora).
- **Documentos em elaboração:** este documento (TCOS-005).
- **Pendências:** confirmação do domínio de negócio (R-000-03); parâmetros do Módulo 24; M-003A-03/04; M-004-01/02; decisão sobre retomar a entrevista de descoberta.
- **Riscos ativos:** R-000-03/R-002-01, R-001-01/R-002-02, R-002A-01 — herdados; nenhum deles impede o desenho de UX/UI, pois toda tela referente a parâmetro pendente já prevê, nesta especificação, um estado de "parâmetro não definido" (alerta + bloqueio, nunca suposição).
- **Dependências para esta fase:** as 30 entidades e Regras Globais do Domain Model; as 47 Regras de Negócio; os 27 módulos e 98 funcionalidades do Functional Specification; os 30 fluxos e a Matriz de Integração do User Journeys and System Flows — todos referenciados por nome/número, nunca reescritos.
- **Objetivo da fase que será iniciada:** projetar completamente a experiência do usuário do THE CHARCOAL OS — como cada tela se parece, se comporta e se conecta às demais — sem código, arquitetura ou banco de dados.
- **O que não pode ser alterado:** nenhum conteúdo de nenhum dos 8 documentos oficiais já aprovados e congelados.

### Auditoria de Abertura

Todos os documentos oficiais foram lidos integralmente. Resultado:

- **Nenhuma inconsistência ou conflito** entre os documentos existentes.
- **Cobertura de telas vs. 27 módulos:** os 30 componentes de UI solicitados (11 Dashboards + 19 telas) cobrem 26 dos 27 módulos. **Módulo 23 — Documentos** não recebe tela própria nesta lista — decisão consistente com o já registrado no TCOS-004 (Documentos é transversal): documentos são exibidos e gerados contextualmente dentro de Contratos, Compras, Clientes e Fornecedores, por meio de um componente reutilizável "Documentos Anexados" (definido no Design System, Seção 6), nunca como destino de navegação independente. Não é um gap, é uma decisão de design registrada.
- **Módulos consolidados em seu próprio Dashboard, sem tela de gestão separada:** CRM (Módulo 04), Marketing (Módulo 21) e Inteligência Artificial (Módulo 22) não têm uma tela de "gestão" própria na lista de 30 — suas funcionalidades de gestão (F-011/F-012 CRM; F-065 a F-067 Marketing; F-068 a F-071 IA) são incorporadas como componentes de ação dentro dos respectivos Dashboards. Registrado como decisão de design (Seção 3), não como gap.
- **Funcionalidades sem interface:** nenhuma das 98 funcionalidades (F-001–F-098) fica sem um componente de UI correspondente — ver Seção 8 (Quality Gate, itens 11–14) para o mapeamento de cobertura completo.
- **Regras sem tela:** RN-004 (Fechamento de Período) e RN-047 (Alertas) — já identificadas no TCOS-004 como processos periódicos/administrativos — recebem, respectivamente, um componente dentro do Dashboard Financeiro Empresarial e um componente global de Central de Notificações (Design System), em vez de uma tela dedicada própria.
- **Fluxos sem navegação:** nenhum. Os 30 fluxos do TCOS-004 mapeiam diretamente para sequências de tela documentadas na Seção 5 (Navegação do Sistema).
- **Oportunidade de simplificação:** Dashboard Produção, Dashboard Estoque e Dashboard Engenharia de Custos compartilham componentes visuais quase idênticos (KPIs de custo/rendimento) — documentados de forma consistente, com nota explícita de reuso de componente, evitando desenho divergente entre eles.
- **Oportunidade de melhoria de UX:** unificar a barra de busca global (Seção 5.3) para pesquisar simultaneamente Cliente, Evento, Orçamento e Contrato — reduz a necessidade de o usuário saber, de antemão, "onde" um dado está.
- Nenhuma decisão técnica (arquitetura, banco de dados, API, código) foi tomada neste documento.

---

## 1. Papel deste Documento

Este documento traduz tudo que já foi aprovado (entidades, regras, funcionalidades, fluxos) em **experiência concreta de uso**: como cada tela se parece, o que ela mostra, como o usuário navega entre elas, e como o sistema comunica visualmente simplicidade, velocidade, profissionalismo, inteligência, segurança e confiabilidade. Um designer de UX/UI deve conseguir construir todas as telas do THE CHARCOAL OS a partir daqui, sem perguntas adicionais sobre **o que** cada tela contém — apenas sobre **como** implementá-la visualmente em uma tecnologia específica (fora de escopo).

## 2. Legenda e Convenções

- **TL-XXX:** identificador de Tela/Dashboard, numerado sequencialmente pela ordem solicitada no Prompt Oficial (11 Dashboards, depois 19 telas).
- Toda referência a Funcionalidade (F-XXX), Regra (RN-XXX), Fluxo (FL-XXX), Módulo ou Entidade usa exatamente os nomes/números já oficiais.
- Nomes de cor referem-se ao Design System (Seção 6): **Brasa** (laranja-avermelhado, cor de marca/destaque), **Carvão** (grafite escuro, texto/elementos de alta ênfase), **Cinza-claro** (fundo neutro), **Verde-sucesso**, **Amarelo-atenção**, **Vermelho-crítico**.
- Cada tela é documentada nos 25 campos obrigatórios; Dashboards recebem, adicionalmente, o detalhamento de layout/componentes/origem de dado/IA exigido para Dashboards.

---

## 3. Telas e Dashboards

### 3.1 Dashboard CEO *(Módulo 01)*

1. **Objetivo da tela:** dar à Direção uma visão executiva única, sempre atualizada, de todo o negócio.
2. **Quem pode acessar:** BI/Direção Executiva.
3. **Permissões:** somente leitura para a maioria dos usuários; configuração de Indicadores exibidos restrita à Direção (F-002).
4. **Layout geral:** grid de largura total, sem menu lateral de módulo (é a tela inicial padrão do sistema).

**Layout (topo → base):**
1. Cabeçalho: logo, seletor de período (hoje/semana/mês/personalizado), sino de notificações, avatar do usuário.
2. Linha de Cards/KPIs (4 a 6 cards): Faturamento do período, Margem média, Eventos confirmados, Eventos concluídos, Retiradas pessoais do período (Módulo 02), Saldo consolidado (Módulo 27).
3. Gráficos (2 colunas): gráfico de linha (Fluxo de Caixa no tempo, F-008), gráfico de barras (margem por Evento, F-009).
4. Lista/Tabela: próximos Eventos confirmados (data, Cliente, status de planejamento).
5. Widget de Metas (F-091, consumido — nunca gerido aqui): mini-cards de progresso das Metas ativas.
6. Widget de Alertas Críticos: lista consolidada de alertas de alta prioridade de todos os módulos (RN-047).
7. Atalhos rápidos: "Novo Evento", "Ver Financeiro", "Ver Metas".

5. **Componentes existentes:** Cards de KPI, gráfico de linha, gráfico de barras, tabela de próximos Eventos, widget de Metas, widget de Alertas.
6. **Cards:** 4–6 cards de topo (métricas financeiras/operacionais chave).
7. **Indicadores:** margem média, taxa de conversão, taxa de fidelização, custo real médio por Evento.
8. **Gráficos:** linha (Fluxo de Caixa), barras (margem por Evento).
9. **KPIs:** faturamento, margem, número de Eventos, saldo consolidado.
10. **Tabelas:** próximos Eventos confirmados.
11. **Filtros:** período (data inicial/final), tipo de Evento.
12. **Pesquisas:** barra de busca global (Seção 5.3).
13. **Botões:** "Novo Evento", "Ver Financeiro", "Ver Metas", "Exportar" (PDF/planilha).
14. **Menus:** menu lateral principal de navegação entre módulos (fixo em todas as telas — ver Seção 5).
15. **Ações rápidas:** criar Evento, acessar Dashboard de qualquer módulo com um clique.
16. **Alertas:** margem abaixo do mínimo (RN-023), inviabilidade operacional (RN-006), Indicador não recalculável (RN-001).
17. **Notificações:** toast de atualização automática ("Dashboard atualizado agora"); nenhuma notificação bloqueante.
18. **Modais:** modal de configuração de Indicadores exibidos (F-002).
19. **Fluxo de navegação:** tela de entrada padrão após login; qualquer card/gráfico é clicável e leva ao Dashboard/tela do módulo de origem daquele dado.
20. **Ações automáticas:** recálculo contínuo de todos os KPIs/gráficos (RN-001), sem ação do usuário.
21. **Integração com outros módulos:** todos — é a única tela que consome de todos os 27 módulos.
22. **Regras de visibilidade:** dados financeiros sensíveis (custo, margem) visíveis apenas a perfis com acesso Financeiro/Direção (CG-05).
23. **Estados da interface:** carregando (skeleton nos cards), atualizado (normal), erro parcial (card específico sinaliza "dado indisponível", nunca trava a tela toda).
24. **Tratamento de erro:** falha de recálculo de um Indicador não impede a exibição dos demais; card afetado exibe ícone de atenção com tooltip explicativo.
25. **Melhorias futuras:** simulador de cenário ("e se eu aumentar a margem-alvo em 2%?" — já listado como Roadmap no TCOS-003).

**Informações exibidas e origem:** todo valor exibido tem origem rastreável a um Indicador já definido (RN-039) — nunca um número "solto". **Atualização automática:** contínua, a cada Evento de Domínio relevante (RN-001). **Integração com IA:** widget opcional de "insight do dia" gerado por IA (ex.: "3 Eventos este mês tiveram margem abaixo da média"), sempre rotulado como sugestão (RN-041), nunca como fato definitivo.

### 3.2 Dashboard Financeiro Pessoal *(Módulo 02)*

1. **Objetivo:** dar visibilidade às retiradas pessoais, mantendo-as sempre separadas do resultado da empresa.
2. **Quem acessa:** Financeiro, Direção.
3. **Permissões:** leitura e registro restritos a Financeiro; Direção com leitura total.
4. **Layout geral:** grid simples, uma coluna de KPIs + uma tabela.

**Layout (topo → base):** 1) Cabeçalho com seletor de período; 2) Cards: total retirado no período, retirada média mensal; 3) Gráfico de linha: retiradas ao longo do tempo; 4) Tabela: histórico de retiradas (data, valor, Conta de origem); 5) Botão de ação: "Registrar Retirada".

5–15. **Componentes/Cards/Indicadores/Gráficos/KPIs/Tabelas/Filtros/Pesquisas/Botões/Menus/Ações rápidas:** conforme layout acima; filtro por período e por Conta; botão "Registrar Retirada" (F-003) sempre visível.
16. **Alertas:** total de retiradas comprometendo o Fluxo de Caixa da empresa (RN-002).
17. **Notificações:** confirmação de registro de retirada.
18. **Modais:** modal de "Registrar Retirada" (valor, data, Conta).
19. **Fluxo de navegação:** acessível pelo menu lateral (Financeiro → Pessoal); retorno ao Dashboard CEO via breadcrumb.
20. **Ações automáticas:** categorização automática como Despesa "Retirada Pessoal" (RN-002).
21. **Integração com outros módulos:** Módulo 27 (Bancos, origem da Conta), Módulo 03 (impacto indireto no Fluxo de Caixa da empresa, nunca somado ao resultado operacional).
22. **Regras de visibilidade:** restrita a Financeiro/Direção — nunca visível a Comercial/Produção.
23. **Estados da interface:** vazio ("nenhuma retirada registrada ainda"), normal, carregando.
24. **Tratamento de erro:** valor inválido ou Conta inexistente bloqueia o registro com mensagem inline.
25. **Melhorias futuras:** categorização de motivo da retirada (ex.: pró-labore fixo vs. eventual).

### 3.3 Dashboard Financeiro Empresarial *(Módulo 03)*

1. **Objetivo:** controlar Despesas, Receitas Financeiras, Pagamentos e o Fluxo de Caixa da empresa.
2. **Quem acessa:** Financeiro; Direção (leitura e aprovação de exceções).
3. **Permissões:** lançamento restrito a Financeiro; aprovação de exceção de margem restrita à Direção.
4. **Layout geral:** grid denso, com abas internas (Fluxo de Caixa | Despesas | Receitas Financeiras | Fechamento de Período).

**Layout (topo → base):** 1) Cabeçalho com seletor de período e Conta; 2) Cards: saldo consolidado, total a pagar, total a receber, margem média do período; 3) Gráfico de linha: Fluxo de Caixa (F-008); 4) Tabela com abas: Despesas (F-005), Receitas Financeiras (F-006), Pagamentos (F-007); 5) Widget: apuração de resultado por Evento (F-009, lista dos últimos Eventos concluídos com margem); 6) Botão: "Fechar Período" (F-010).

5–15. Cards de saldo/margem; gráfico de linha; tabelas por aba com paginação; filtros por período/Conta/status; pesquisa por Cliente/Fornecedor/Evento; botões "Novo Lançamento Manual" (F-005/F-006), "Registrar Pagamento" (F-007), "Fechar Período"; menu de abas internas; ação rápida "Ver Evento" a partir de uma linha de Despesa/Receita Financeira.
16. **Alertas:** margem real abaixo do mínimo (RN-003); pendências ao tentar fechar período (RN-004); lançamento ambíguo (RN-005).
17. **Notificações:** período fechado com sucesso; pagamento confirmado.
18. **Modais:** "Novo Lançamento Manual", "Registrar Pagamento", "Fechar Período" (com lista de pendências, se houver).
19. **Fluxo de navegação:** menu lateral (Financeiro → Empresarial); links diretos para Módulo 27 (Bancos) a partir de cada Conta citada.
20. **Ações automáticas:** geração automática de Receita Financeira a partir de Contrato assinado; geração automática de Despesa a partir de Compra conferida.
21. **Integração com outros módulos:** 27 (Bancos), 07 (Eventos), 09 (Contratos), 15 (Compras), 19 (Funcionários), 22 (IA — importação/conciliação).
22. **Regras de visibilidade:** restrita a Financeiro/Direção (CG-05).
23. **Estados da interface:** normal, carregando, "período com pendências" (banner amarelo persistente até resolução).
24. **Tratamento de erro:** tentativa de pagamento acima do saldo em aberto é bloqueada com mensagem inline; falha ao fechar período mantém o período aberto e lista as pendências.
25. **Melhorias futuras:** simulação de fechamento ("prévia" antes de fechar de fato).

### 3.4 Dashboard Marketing *(Módulo 21 — inclui gestão de Campanhas)*

1. **Objetivo:** planejar, executar e medir Campanhas de geração de demanda.
2. **Quem acessa:** Marketing; Comercial/Direção (leitura).
3. **Permissões:** criação/edição de Campanha restrita a Marketing.
4. **Layout geral:** grid com lista de Campanhas em destaque.

**Layout (topo → base):** 1) Cabeçalho com filtro de período; 2) Cards: Leads gerados no período, taxa de conversão, custo por Lead, retorno consolidado; 3) Gráfico de barras: retorno por Campanha (F-066); 4) Tabela: Campanhas ativas/encerradas (F-065/F-067), com coluna de status e retorno; 5) Botão: "Nova Campanha".

5–15. Cards de Leads/conversão/retorno; gráfico de barras por Campanha; tabela de Campanhas com filtro por status/canal/período; pesquisa por nome de Campanha; botões "Nova Campanha", "Encerrar Campanha"; ação rápida "Ver Leads desta Campanha" (leva ao Módulo 06 filtrado).
16. **Alertas:** nenhum próprio; consolidação de alertas de Leads inativos (RN-011) exibida como widget secundário.
17. **Notificações:** Campanha encerrada com sucesso.
18. **Modais:** "Nova Campanha" (nome, canal, período, objetivo, investimento).
19. **Fluxo de navegação:** menu lateral (Marketing); drill-down de Campanha → lista de Leads/Clientes atribuídos (Módulos 06/04).
20. **Ações automáticas:** atribuição automática de retorno (RN-038).
21. **Integração com outros módulos:** 06 (Leads), 04 (CRM), 09 (Contratos, para valor de retorno).
22. **Regras de visibilidade:** Marketing edita; Comercial/Direção apenas leem.
23. **Estados da interface:** vazio ("nenhuma Campanha ativa"), normal.
24. **Tratamento de erro:** datas de período inválidas (fim antes do início) bloqueadas no formulário.
25. **Melhorias futuras:** integração com plataformas externas de anúncio (fora de escopo atual, Roadmap do TCOS-003).

**Informações exibidas e origem:** retorno de Campanha vem de RN-038 (Lead → Cliente → Contrato). **Atualização automática:** contínua a cada conversão. **Integração com IA:** nenhuma nesta versão (fora do escopo de RN-041/042 atuais).

### 3.5 Dashboard Produção *(Módulo 10)*

1. **Objetivo:** dar visibilidade ao planejamento e execução da Produção, com foco em consumo, perdas e rendimento.
2. **Quem acessa:** Produção; Direção (leitura).
3. **Permissões:** execução/registro restritos a Produção.
4. **Layout geral:** grid com calendário de Produções planejadas em destaque.

**Layout (topo → base):** 1) Cabeçalho com filtro de período/Evento; 2) Cards: Produções planejadas hoje, desvio médio de rendimento, desvio médio de perda; 3) Calendário/Timeline: Produções planejadas por data, vinculadas a Eventos; 4) Gráfico de barras: planejado vs. real (consumo de Ingrediente) por Produção (F-035); 5) Tabela: Produções em execução/concluídas; 6) Botão: "Executar Produção".

5–15. Cards de desvio; calendário/timeline; gráfico planejado x real; tabela de Produções com filtro por Evento/status; pesquisa por Ficha Técnica/Produto; botões "Planejar Produção" (normalmente automático via RN-016, disponível manualmente como exceção), "Registrar Consumo Real" (F-034); ação rápida "Ver Ficha Técnica" a partir de uma Produção.
16. **Alertas:** rendimento insuficiente (alta prioridade, RN-029); prazo insuficiente (RN-016); Estoque insuficiente para iniciar (RN-032).
17. **Notificações:** Produção concluída com sucesso.
18. **Modais:** "Registrar Consumo e Rendimento Real" (F-034).
19. **Fluxo de navegação:** menu lateral (Produção); drill-down para Ficha Técnica (Módulo 13) e Evento (Módulo 07) a partir de cada Produção.
20. **Ações automáticas:** planejamento automático a partir de "Evento confirmado" (RN-016); baixa automática de Estoque (RN-032).
21. **Integração com outros módulos:** 07 (Eventos), 13 (Fichas Técnicas), 16 (Estoque), 17 (Lotes), 24 (Configurações — parâmetros de consumo/perda).
22. **Regras de visibilidade:** Produção e Direção; custo detalhado restrito a Financeiro/Direção (CG-05).
23. **Estados da interface:** normal, "parâmetro de consumo não definido" (bloqueio com link direto para Configurações).
24. **Tratamento de erro:** tentativa de iniciar Produção sem Estoque suficiente é bloqueada com sugestão de Compra emergencial.
25. **Melhorias futuras:** visão de capacidade produtiva por dia (quantas Produções cabem simultaneamente).

**Informações exibidas e origem:** consumo/rendimento vêm da Ficha Técnica vigente (RN-018/019) e dos registros reais de Produção (RN-028/029). **Atualização automática:** a cada Produção concluída. **Integração com IA:** previsão de demanda (F-069) exibida como widget opcional, sempre como sugestão.

### 3.6 Dashboard Estoque *(Módulo 16, inclui Lotes — Módulo 17)*

1. **Objetivo:** dar visibilidade à posição real de Ingredientes/Produtos e à rastreabilidade por Lote.
2. **Quem acessa:** Estoque/Logística; Compras/Produção (leitura).
3. **Permissões:** ajuste de saldo restrito a Estoque/Logística.
4. **Layout geral:** grid com tabela de itens em destaque e alerta de reposição visível no topo.

**Layout (topo → base):** 1) Cabeçalho com filtro por categoria/localização; 2) Cards: itens abaixo do ponto de reposição, Lotes próximos do vencimento, giro médio de Estoque; 3) Gráfico de barras: saldo por categoria de Ingrediente; 4) Tabela: posição de Estoque por item (F-052); 5) Tabela secundária (aba): Lotes (F-055), com destaque visual para os próximos do vencimento; 6) Botão: "Realizar Inventário".

5–15. Cards de reposição/vencimento; gráfico de saldo; tabela de Estoque com filtro por item/localização; tabela de Lotes com filtro por validade; pesquisa por nome de Ingrediente/Produto; botões "Realizar Inventário" (F-053), "Configurar Ponto de Reposição" (F-054), "Registrar Descarte de Lote" (F-056).
16. **Alertas:** estoque abaixo do ponto de reposição (RN-033); Lote próximo do vencimento (RN-034); tentativa de uso de Lote vencido (bloqueio).
17. **Notificações:** inventário concluído; descarte registrado.
18. **Modais:** "Realizar Inventário/Ajuste" (com justificativa obrigatória), "Registrar Descarte de Lote".
19. **Fluxo de navegação:** menu lateral (Estoque); drill-down de item → Lotes associados → Compra/Produção de origem.
20. **Ações automáticas:** atualização automática de saldo (RN-032); priorização "primeiro que vence, primeiro que sai" (RN-034).
21. **Integração com outros módulos:** 15 (Compras), 10 (Produção), 07 (Eventos — reserva).
22. **Regras de visibilidade:** Estoque/Logística e Compras/Produção; custo de Ingrediente restrito a Financeiro/Direção.
23. **Estados da interface:** normal, "saldo insuficiente" (linha destacada em Vermelho-crítico), "vencimento próximo" (linha em Amarelo-atenção).
24. **Tratamento de erro:** ajuste manual de saldo sem justificativa é bloqueado.
25. **Melhorias futuras:** leitura de código de barras/QR para conferência de Compra e baixa de Produção (fora de escopo atual).

**Informações exibidas e origem:** saldo é derivado de Compra/Produção/venda (RN-032); validade vem do cadastro de Lote (RN-034). **Atualização automática:** contínua, a cada movimentação. **Integração com IA:** previsão de demanda (F-069) compartilhada com o Dashboard de Compras/Produção.

### 3.7 Dashboard Engenharia de Custos *(Módulo 11)*

1. **Objetivo:** consolidar e proteger o custo real de produção e de cada Evento.
2. **Quem acessa:** Produção (função de Engenharia de Custos), Financeiro, Direção.
3. **Permissões:** leitura ampla; edição de Ficha Técnica restrita a Produção.
4. **Layout geral:** grid com foco em comparação previsto vs. real.

**Layout (topo → base):** 1) Cabeçalho com filtro por Evento/Produto/período; 2) Cards: custo real médio por Evento, desvio médio de custo, margem média; 3) Gráfico de barras: custo previsto vs. real por Evento (F-038); 4) Tabela: Fichas Técnicas com custo vigente e data do último recálculo; 5) Botão: "Ver Detalhamento de Custo do Evento".

5–15. Cards de custo/desvio; gráfico previsto x real; tabela de Fichas Técnicas com filtro por Produto/status; pesquisa por nome de Produto/Receita; botão de detalhamento por Evento (F-036).
16. **Alertas:** custo real excedendo significativamente o previsto (RN-018); impacto de recálculo em Orçamentos abertos (RN-019).
17. **Notificações:** Ficha Técnica recalculada.
18. **Modais:** detalhamento de custo de um Evento específico (breakdown por Ingrediente/mão de obra/Despesa direta).
19. **Fluxo de navegação:** menu lateral (Engenharia de Custos); drill-down para Ficha Técnica (Módulo 13) e Evento (Módulo 07).
20. **Ações automáticas:** recálculo automático em cascata ao mudar custo de Ingrediente (RN-019).
21. **Integração com outros módulos:** 13 (Fichas Técnicas), 10 (Produção), 19 (Funcionários), 03 (Financeiro).
22. **Regras de visibilidade:** custo e margem restritos a Produção/Financeiro/Direção (CG-05) — nunca visíveis a Comercial.
23. **Estados da interface:** normal, "custo parcial" (badge cinza enquanto há Despesa pendente).
24. **Tratamento de erro:** nenhuma edição direta de custo total é permitida — sempre derivado da Ficha Técnica (bloqueio com explicação).
25. **Melhorias futuras:** alerta preditivo de "Evento com risco de margem baixa" antes mesmo da confirmação (via IA).

**Informações exibidas e origem:** 100% derivado de Ficha Técnica + Produção real + Alocação de Funcionário (RN-018). **Atualização automática:** a cada atualização de custo de Ingrediente ou conclusão de Produção. **Integração com IA:** sugestão de preço (F-070) referenciada a partir daqui.

### 3.8 Dashboard Eventos *(Módulo 07)*

1. **Objetivo:** dar visibilidade ao pipeline e à operação de todos os Eventos.
2. **Quem acessa:** Comercial/CRM, Eventos/Operações, Produção, Financeiro.
3. **Permissões:** leitura ampla; ações de confirmação/cancelamento restritas conforme alçada (Comercial/Direção).
4. **Layout geral:** grid com calendário de Eventos em destaque.

**Layout (topo → base):** 1) Cabeçalho com filtro de período/status; 2) Cards: Eventos confirmados no período, Eventos em execução, margem média prevista; 3) Calendário: Eventos por data, coloridos por status; 4) Tabela: lista de Eventos com estado do ciclo de vida; 5) Botão: "Novo Evento".

5–15. Cards de contagem/margem; calendário de Eventos; tabela com filtro por status/Cliente/tipo; pesquisa por nome de Cliente/Evento; botões "Novo Evento" (F-020), "Confirmar", "Cancelar"; ação rápida "Ver Orçamento/Contrato vinculado".
16. **Alertas:** inviabilidade operacional na confirmação (RN-006); margem prevista abaixo do mínimo; impacto financeiro de cancelamento (RN-007).
17. **Notificações:** Evento confirmado (com resumo da orquestração executada); Evento concluído.
18. **Modais:** "Novo Evento" (Cliente, data, local, convidados, escopo); "Cancelar Evento" (motivo obrigatório).
19. **Fluxo de navegação:** menu lateral (Eventos); tela de detalhe do Evento (aba única com sub-abas: Orçamento, Contrato, Produção, Equipe, Financeiro) acessível a partir de qualquer linha/card do calendário.
20. **Ações automáticas:** orquestração completa na confirmação (RN-006): reserva de Estoque, planejamento de Produção, sugestão de Escala, lista de Compras, previsão financeira.
21. **Integração com outros módulos:** 08, 09, 10, 15, 16, 18, 19, 20, 03 — o Dashboard com mais integrações do sistema, além do Dashboard CEO.
22. **Regras de visibilidade:** dados comerciais visíveis a Comercial; dados de custo/margem restritos a Financeiro/Direção.
23. **Estados da interface:** "Prospectado" (cinza), "Confirmado" (Brasa), "Em execução" (azul), "Concluído" (verde), "Cancelado" (vermelho, riscado).
24. **Tratamento de erro:** tentativa de confirmar Evento inviável exibe modal explicando exatamente qual recurso está insuficiente (Estoque, Equipamento, mão de obra).
25. **Melhorias futuras:** visão de mapa (localização geográfica dos Eventos do dia), útil para logística.

**Informações exibidas e origem:** cada sub-aba do detalhe do Evento consome diretamente o módulo correspondente (Orçamento, Contrato, Produção etc.). **Atualização automática:** contínua ao longo de todo o ciclo de vida do Evento. **Integração com IA:** nenhuma direta neste Dashboard — IA atua nos módulos que ele consome (Compras, Precificação).

### 3.9 Dashboard CRM *(Módulo 04, inclui Leads e Clientes consolidados)*

1. **Objetivo:** dar visão consolidada do funil comercial e do retorno de aquisição.
2. **Quem acessa:** Comercial/CRM; Direção (leitura).
3. **Permissões:** leitura ampla; ações de Lead/Cliente ocorrem nas telas próprias (Seções 3.12/3.13).
4. **Layout geral:** grid com funil visual em destaque.

**Layout (topo → base):** 1) Cabeçalho com filtro de período/Campanha; 2) Cards: novos Leads, taxa de conversão, Clientes fidelizados; 3) Funil visual (Lead → Qualificação → Conversão → Contrato); 4) Gráfico de barras: retorno por Campanha (F-012); 5) Tabela: Leads recentes precisando de atenção (inativos, RN-011).

5–15. Cards de funil; gráfico de funil (visual dedicado); gráfico de retorno por Campanha; tabela de Leads que precisam de ação; pesquisa por nome de Lead/Cliente; botão "Ir para Leads"/"Ir para Clientes" (navegação para os módulos específicos).
16. **Alertas:** Lead inativo há X dias (RN-011).
17. **Notificações:** nenhuma própria — consolida notificações de Leads/Clientes.
18. **Modais:** nenhum próprio — ações de criação ocorrem nas telas de Leads/Clientes.
19. **Fluxo de navegação:** menu lateral (CRM); é a tela "consolidadora" entre Leads e Clientes, não substitui nenhuma das duas.
20. **Ações automáticas:** cálculo contínuo de taxa de conversão e retorno por Campanha.
21. **Integração com outros módulos:** 06 (Leads), 05 (Clientes), 21 (Marketing), 08/09 (Orçamentos/Contratos, para conversão).
22. **Regras de visibilidade:** Comercial/CRM e Direção.
23. **Estados da interface:** normal, vazio (nenhum Lead no período filtrado).
24. **Tratamento de erro:** nenhum específico — tela somente de consulta.
25. **Melhorias futuras:** funil comparativo entre períodos (mês atual vs. anterior).

**Informações exibidas e origem:** funil deriva de Lead/Cliente/Orçamento/Contrato (RN-008/009/011). **Atualização automática:** contínua. **Integração com IA:** nenhuma direta.

### 3.10 Dashboard Metas *(Módulo 26)*

1. **Objetivo:** ser o único lugar de gestão de Metas — o Dashboard CEO apenas consome esta informação.
2. **Quem acessa:** Direção; responsáveis por Meta (leitura/atualização da própria Meta).
3. **Permissões:** criação/edição/encerramento restritos à Direção.
4. **Layout geral:** grid com cards de progresso em destaque.

**Layout (topo → base):** 1) Cabeçalho com filtro por responsável/status; 2) Cards de progresso por Meta ativa (barra de progresso, valor atual vs. valor-alvo); 3) Gráfico: histórico de Metas atingidas vs. não atingidas por ciclo; 4) Tabela: histórico completo de Metas (F-089); 5) Botão: "Criar Meta".

5–15. Cards de progresso (um por Meta ativa); gráfico de histórico; tabela de histórico com filtro por período/responsável/Indicador; pesquisa por nome de Meta; botões "Criar Meta" (F-084), "Editar" (F-085), "Duplicar" (F-087), "Encerrar Antecipadamente" (F-086).
16. **Alertas:** atraso no progresso; conclusão de ciclo (RN-046).
17. **Notificações:** Meta atingida (celebração visual); Meta não atingida (neutro, sem "gamificação negativa").
18. **Modais:** "Criar/Editar Meta" (período, Indicador, responsável, valor-alvo, critério de sucesso); "Registrar Justificativa" (F-090).
19. **Fluxo de navegação:** menu lateral (Metas); drill-down de cada card para o Indicador associado (fora deste módulo).
20. **Ações automáticas:** encerramento automático de ciclo na data definida (RN-046).
21. **Integração com outros módulos:** 01 (Dashboard CEO, consumo — nunca gestão), Indicadores de qualquer módulo.
22. **Regras de visibilidade:** Direção vê todas; responsável vê as suas.
23. **Estados da interface:** "Ativa" (Brasa), "Atingida" (verde), "Não atingida" (âmbar, nunca vermelho — tom não punitivo), "Encerrada" (cinza).
24. **Tratamento de erro:** criação de Meta sem Indicador associado é bloqueada.
25. **Melhorias futuras:** metas em cascata (Meta da empresa se desdobrando em metas por área).

**Informações exibidas e origem:** progresso vem do Indicador associado (RN-046). **Atualização automática:** contínua. **Integração com IA:** sugestão futura de valor-alvo realista com base em histórico (Roadmap).

### 3.11 Dashboard Inteligência Artificial *(Módulo 22)*

1. **Objetivo:** centralizar toda sugestão de IA do sistema, com transparência total sobre o que foi sugerido, aceito ou recusado.
2. **Quem acessa:** todas as áreas (visão das sugestões relevantes a si); Direção (configuração, F-071).
3. **Permissões:** configuração do nível de automação restrita à Direção.
4. **Layout geral:** grid com feed cronológico de sugestões.

**Layout (topo → base):** 1) Cabeçalho com filtro por tipo de sugestão/módulo de origem; 2) Cards: sugestões pendentes, taxa de aceite, previsões ativas; 3) Feed cronológico: cada sugestão (categorização de extrato, previsão de demanda, sugestão de preço) com origem, confiança e status (aceita/recusada/pendente); 4) Gráfico: taxa de aceite ao longo do tempo; 5) Botão: "Configurar Automação".

5–15. Cards de sugestões/taxa de aceite; feed cronológico (lista); gráfico de taxa de aceite; filtro por módulo de origem/tipo/status; pesquisa por período; botão "Configurar Nível de Automação" (F-071).
16. **Alertas:** baixa confiança de previsão por histórico insuficiente (RN-042).
17. **Notificações:** nova sugestão de alta relevância disponível.
18. **Modais:** "Configurar Nível de Automação" (por tipo de sugestão: sempre confirmar vs. automático se reversível).
19. **Fluxo de navegação:** menu lateral (Inteligência Artificial); cada item do feed leva à tela do módulo de origem (Financeiro, Compras, Precificação).
20. **Ações automáticas:** nenhuma sem confirmação, exceto as explicitamente configuradas como automáticas e reversíveis (RN-041).
21. **Integração com outros módulos:** 03 (Financeiro), 15 (Compras), 14 (Precificação).
22. **Regras de visibilidade:** cada área vê as sugestões relevantes ao seu módulo; configuração de automação restrita à Direção.
23. **Estados da interface:** "Pendente" (Brasa), "Aceita" (verde), "Recusada" (cinza, com motivo visível).
24. **Tratamento de erro:** nenhuma sugestão é aplicada sem confirmação quando há ambiguidade (RN-043) — botão de confirmação desabilitado até resolução.
25. **Melhorias futuras:** explicação detalhada ("por que a IA sugeriu isso") por sugestão — transparência algorítmica ampliada.

**Informações exibidas e origem:** cada sugestão referencia a Regra que a gerou (RN-041/042/043). **Atualização automática:** feed em tempo real. **Integração com IA:** este é o próprio Dashboard de IA — 100% do conteúdo é gerado ou mediado por IA, sempre com rótulo de sugestão.

### 3.12 Leads *(Módulo 06)*

1. **Objetivo da tela:** gerenciar o ciclo de vida do Lead, da captação à conversão/perda.
2. **Quem pode acessar:** Comercial/CRM, Marketing.
3. **Permissões:** criação/qualificação/conversão por Comercial; criação também por Marketing (via Campanha).
4. **Layout geral:** lista/kanban por estágio (Novo, Em qualificação, Convertido, Perdido).
5. **Componentes existentes:** kanban de estágios, tabela alternativa, painel de detalhe do Lead.
6. **Cards:** contagem por estágio no topo do kanban.
7. **Indicadores:** taxa de conversão, tempo médio de qualificação.
8. **Gráficos:** nenhum nesta tela (consolidados no Dashboard CRM).
9. **KPIs:** total de Leads ativos.
10. **Tabelas:** lista alternativa ao kanban, com colunas (nome, origem, estágio, data).
11. **Filtros:** por origem/Campanha, por estágio, por período.
12. **Pesquisas:** por nome/contato do Lead.
13. **Botões:** "Novo Lead" (F-016), "Qualificar" (F-017), "Converter" (F-018), "Marcar como Perdido" (F-019).
14. **Menus:** menu lateral (CRM → Leads).
15. **Ações rápidas:** arrastar card entre colunas do kanban (mudança de estágio).
16. **Alertas:** Lead inativo há X dias (RN-011), exibido como badge no card.
17. **Notificações:** Lead convertido com sucesso.
18. **Modais:** "Novo Lead" (nome, contato, origem); "Converter Lead" (com aviso de possível duplicidade, RN-009).
19. **Fluxo de navegação:** acessível pelo menu ou por drill-down do Dashboard CRM; conversão leva à tela de Clientes.
20. **Ações automáticas:** atribuição de origem (RN-008); sugestão de perda por inatividade (RN-011).
21. **Integração com outros módulos:** 05 (Clientes), 21 (Marketing), 08 (Orçamentos).
22. **Regras de visibilidade:** Comercial/CRM e Marketing.
23. **Estados da interface:** vazio, normal, "correspondência ambígua" (modal de confirmação na conversão).
24. **Tratamento de erro:** cadastro sem meio de contato é bloqueado.
25. **Melhorias futuras:** pontuação automática de qualidade do Lead (lead scoring via IA).

### 3.13 Clientes *(Módulo 05)*

1. **Objetivo:** manter o cadastro único e o histórico de relacionamento com cada Cliente.
2. **Quem acessa:** Comercial/CRM; Financeiro (dados de faturamento).
3. **Permissões:** criação/edição por Comercial; dados financeiros visíveis a Financeiro.
4. **Layout geral:** lista de Clientes + painel de detalhe com abas (Histórico, Eventos, Documentos, Financeiro).
5. **Componentes:** tabela de Clientes, painel de detalhe com abas.
6. **Cards:** no painel de detalhe — total de Eventos, valor total histórico, status de fidelização.
7. **Indicadores:** número de Clientes ativos, taxa de fidelização.
8. **Gráficos:** nenhum nesta tela.
9. **KPIs:** total de Clientes ativos (cabeçalho da lista).
10. **Tabelas:** lista de Clientes (nome, tipo, status, último Evento).
11. **Filtros:** por status (ativo/inativo), por fidelização, por tipo (PF/PJ).
12. **Pesquisas:** por nome/contato.
13. **Botões:** "Novo Cliente" (F-013), "Inativar" (F-015).
14. **Menus:** menu lateral (Clientes); abas internas no painel de detalhe.
15. **Ações rápidas:** "Novo Orçamento para este Cliente" a partir do painel de detalhe.
16. **Alertas:** possível duplicidade no cadastro (RN-009).
17. **Notificações:** Cliente fidelizado (badge visual no card).
18. **Modais:** "Novo/Editar Cliente".
19. **Fluxo de navegação:** lista → painel de detalhe (aba Histórico mostra linha do tempo de Eventos/Orçamentos/Contratos, F-014).
20. **Ações automáticas:** marcação automática de fidelização (RN-010).
21. **Integração com outros módulos:** 06 (Leads), 08 (Orçamentos), 09 (Contratos), 07 (Eventos), 03 (Financeiro).
22. **Regras de visibilidade:** dados de contato para Comercial; dados financeiros restritos a Financeiro/Direção.
23. **Estados da interface:** ativo, inativo (visualmente esmaecido, mas acessível).
24. **Tratamento de erro:** tentativa de criar Orçamento para Cliente inativo sugere reativação primeiro.
25. **Melhorias futuras:** registro estruturado de preferências do Cliente (base para o gap de Pós-venda, FL-030).

### 3.14 Eventos *(Módulo 07 — tela de gestão/detalhe, complementar ao Dashboard Eventos)*

1. **Objetivo:** gerenciar o ciclo de vida operacional de um Evento específico.
2. **Quem acessa:** Comercial/CRM, Eventos/Operações, Produção, Financeiro, Pessoas/Mão de Obra.
3. **Permissões:** conforme a aba (Orçamento por Comercial, Produção por Produção, etc.).
4. **Layout geral:** tela de detalhe com abas: Resumo, Orçamento, Contrato, Produção, Equipe/Escala, Equipamentos, Financeiro.
5. **Componentes:** cabeçalho com status do Evento, abas, linha do tempo do ciclo de vida.
6. **Cards:** margem prevista, número de convidados, dias até o Evento.
7. **Indicadores:** margem prevista/real, taxa de ocupação da equipe.
8. **Gráficos:** nenhum nesta tela (consolidados no Dashboard Eventos).
9. **KPIs:** status atual do ciclo de vida.
10. **Tabelas:** itens do Orçamento (aba Orçamento), lista de Produções (aba Produção), lista de Alocações (aba Equipe).
11. **Filtros:** não aplicável (tela de detalhe de um único Evento).
12. **Pesquisas:** não aplicável.
13. **Botões:** "Confirmar Evento" (F-021), "Ajustar Planejamento" (F-022), "Concluir Evento" (F-023), "Cancelar Evento" (F-024).
14. **Menus:** abas internas (Resumo, Orçamento, Contrato, Produção, Equipe, Equipamentos, Financeiro).
15. **Ações rápidas:** "Ver Orçamento completo", "Ver Contrato", a partir das respectivas abas.
16. **Alertas:** inviabilidade operacional (RN-006); margem abaixo do mínimo; conflito de Equipamento/Escala.
17. **Notificações:** confirmação disparada com sucesso (resumo da orquestração).
18. **Modais:** "Cancelar Evento" (motivo obrigatório); "Ajuste manual de planejamento".
19. **Fluxo de navegação:** acessível a partir do Dashboard Eventos (calendário/tabela) ou da tela de Clientes.
20. **Ações automáticas:** orquestração completa na confirmação (RN-006).
21. **Integração com outros módulos:** 08, 09, 10, 15, 16, 18, 19, 20, 03.
22. **Regras de visibilidade:** cada aba visível conforme a área do usuário.
23. **Estados da interface:** cada estado do ciclo de vida (Prospectado a Cancelado) com cor e ações disponíveis distintas.
24. **Tratamento de erro:** confirmação bloqueada com explicação exata do recurso insuficiente.
25. **Melhorias futuras:** checklist visual de "tudo pronto para o Evento" (Equipamento confirmado, Escala confirmada, Compras recebidas).

### 3.15 Orçamentos *(Módulo 08)*

1. **Objetivo:** montar, enviar e acompanhar propostas comerciais.
2. **Quem acessa:** Comercial/CRM; Direção (aprovação de exceção de margem).
3. **Permissões:** criação/edição por Comercial; aprovação de exceção por Direção.
4. **Layout geral:** lista de Orçamentos + editor de proposta (itens, valores, condições).
5. **Componentes:** tabela de Orçamentos, editor de itens (linha por Produto/Pacote), resumo de valor/margem.
6. **Cards:** valor total, margem calculada (visível a quem tem permissão).
7. **Indicadores:** taxa de aceite, tempo médio de fechamento.
8. **Gráficos:** nenhum nesta tela.
9. **KPIs:** número de Orçamentos abertos.
10. **Tabelas:** lista de Orçamentos (Cliente, valor, status, validade); itens do Orçamento no editor.
11. **Filtros:** por status (Rascunho, Enviado, Aceito, Recusado, Expirado), por Cliente, por período.
12. **Pesquisas:** por nome de Cliente/Evento.
13. **Botões:** "Novo Orçamento" (F-025), "Enviar" (F-026), "Nova Versão" (F-027), "Registrar Aceite/Recusa" (F-028).
14. **Menus:** menu lateral (Orçamentos).
15. **Ações rápidas:** "Duplicar Orçamento" para Evento semelhante.
16. **Alertas:** margem abaixo do mínimo (RN-023, bloqueio com aprovação); Produto sem Ficha Técnica vigente (RN-021).
17. **Notificações:** Orçamento aceito → Contrato gerado automaticamente.
18. **Modais:** "Solicitar Aprovação de Exceção de Margem" (F-047).
19. **Fluxo de navegação:** lista → editor; ao aceitar, navega automaticamente para a tela de Contratos.
20. **Ações automáticas:** cálculo automático de preço (RN-012/022); expiração automática (RN-013).
21. **Integração com outros módulos:** 13 (Fichas Técnicas), 14 (Precificação), 07 (Eventos), 09 (Contratos).
22. **Regras de visibilidade:** valor total visível a todos com acesso; composição de custo restrita a Financeiro/Direção.
23. **Estados da interface:** cores por status (Rascunho cinza, Enviado azul, Aceito verde, Recusado vermelho, Expirado cinza-claro).
24. **Tratamento de erro:** tentativa de enviar Orçamento sem itens é bloqueada.
25. **Melhorias futuras:** modelo de proposta em PDF com identidade visual da marca, gerado automaticamente.

### 3.16 Contratos *(Módulo 09)*

1. **Objetivo:** formalizar e acompanhar o compromisso contratual.
2. **Quem acessa:** Comercial/CRM, Administrativo/Documentos, Financeiro.
3. **Permissões:** geração automática; assinatura registrada por Comercial/Administrativo; aditivo por ambos.
4. **Layout geral:** lista de Contratos + visualizador de documento + linha de aditivos.
5. **Componentes:** tabela de Contratos, visualizador de PDF/documento, histórico de aditivos.
6. **Cards:** valor total, status, data de assinatura.
7. **Indicadores:** tempo médio de formalização, volume de aditivos.
8. **Gráficos:** nenhum nesta tela.
9. **KPIs:** Contratos assinados no período.
10. **Tabelas:** lista de Contratos; histórico de aditivos.
11. **Filtros:** por status, por Cliente, por período.
12. **Pesquisas:** por nome de Cliente/Evento.
13. **Botões:** "Assinar" (F-030), "Registrar Aditivo" (F-031).
14. **Menus:** menu lateral (Contratos).
15. **Ações rápidas:** "Baixar PDF", "Ver Evento vinculado".
16. **Alertas:** dados obrigatórios ausentes (RN-014); impacto de aditivo em recursos já reservados (RN-015).
17. **Notificações:** Contrato assinado (dispara confirmação de Evento).
18. **Modais:** "Registrar Aditivo" (descrição da alteração, novo valor se houver).
19. **Fluxo de navegação:** gerado automaticamente a partir de Orçamento aceito; acessível também pela tela de Eventos.
20. **Ações automáticas:** geração automática de minuta (RN-014); geração de Receita Financeira prevista na assinatura.
21. **Integração com outros módulos:** 08 (Orçamentos), 07 (Eventos), 23 (Documentos), 03 (Financeiro).
22. **Regras de visibilidade:** Comercial/Administrativo/Financeiro; Cliente visualiza o seu próprio (se houver portal — Roadmap futuro).
23. **Estados da interface:** Rascunho, Assinado, Em execução, Concluído, Cancelado.
24. **Tratamento de erro:** tentativa de editar Contrato assinado diretamente é bloqueada — redireciona para "Registrar Aditivo".
25. **Melhorias futuras:** assinatura eletrônica integrada (fora de escopo técnico atual).

### 3.17 Produção *(Módulo 10 — tela operacional, complementar ao Dashboard Produção)*

1. **Objetivo:** executar e registrar a Produção do dia a dia.
2. **Quem acessa:** Produção.
3. **Permissões:** execução e registro restritos a Produção.
4. **Layout geral:** lista de Produções planejadas para o dia/período + tela de execução.
5. **Componentes:** tabela de Produções, formulário de execução (consumo/rendimento real).
6. **Cards:** Produções pendentes hoje, Produções concluídas hoje.
7. **Indicadores:** desvio de rendimento do dia.
8. **Gráficos:** nenhum nesta tela.
9. **KPIs:** quantidade planejada vs. produzida do dia.
10. **Tabelas:** lista de Produções por status.
11. **Filtros:** por Evento, por Ficha Técnica, por status, por data.
12. **Pesquisas:** por nome de Produto/Receita.
13. **Botões:** "Iniciar Execução" (F-033), "Registrar Consumo/Rendimento" (F-034).
14. **Menus:** menu lateral (Produção).
15. **Ações rápidas:** "Ver Ficha Técnica" a partir de uma Produção.
16. **Alertas:** Estoque insuficiente (RN-032); rendimento insuficiente (RN-029, alta prioridade).
17. **Notificações:** Produção concluída.
18. **Modais:** "Registrar Consumo e Rendimento Real".
19. **Fluxo de navegação:** acessível pelo menu ou a partir da aba Produção da tela de Eventos.
20. **Ações automáticas:** baixa automática de Estoque (RN-032); geração de Lote.
21. **Integração com outros módulos:** 13 (Fichas Técnicas), 16 (Estoque), 17 (Lotes), 07 (Eventos).
22. **Regras de visibilidade:** Produção; custo restrito a Financeiro/Direção.
23. **Estados da interface:** Planejada, Em execução, Concluída, Cancelada.
24. **Tratamento de erro:** tentativa de concluir sem registrar consumo real é bloqueada.
25. **Melhorias futuras:** checklist de etapas de preparo por Receita (apoio operacional em tela/tablet de cozinha).

### 3.18 Receitas *(Módulo 12)*

1. **Objetivo:** padronizar e versionar o "como fazer" de cada item.
2. **Quem acessa:** Produção.
3. **Permissões:** criação/edição restritas a Produção.
4. **Layout geral:** lista de Receitas + editor (ingredientes, quantidades, modo de preparo).
5. **Componentes:** tabela de Receitas, editor com lista de Ingredientes.
6. **Cards:** total de Receitas ativas, em desenvolvimento.
7. **Indicadores:** frequência de revisão.
8. **Gráficos:** nenhum.
9. **KPIs:** Receitas aprovadas vs. em desenvolvimento.
10. **Tabelas:** lista de Receitas com estado e versão atual.
11. **Filtros:** por estado (desenvolvimento, aprovada, revisão, descontinuada).
12. **Pesquisas:** por nome de Receita/Ingrediente.
13. **Botões:** "Nova Receita" (F-039), "Aprovar" (F-040), "Revisar/Nova Versão" (F-041).
14. **Menus:** menu lateral (Receitas).
15. **Ações rápidas:** "Criar Ficha Técnica a partir desta Receita".
16. **Alertas:** tentativa de aprovar sem Ficha Técnica associada.
17. **Notificações:** nova versão publicada — aviso à equipe de Produção.
18. **Modais:** "Nova/Editar Receita".
19. **Fluxo de navegação:** aprovação leva à criação de Ficha Técnica (Módulo 13).
20. **Ações automáticas:** propagação de nova versão à Ficha Técnica associada (RN-020).
21. **Integração com outros módulos:** 13 (Fichas Técnicas), 10 (Produção).
22. **Regras de visibilidade:** Produção; modo de preparo não necessariamente visível a Comercial/Financeiro.
23. **Estados da interface:** Em desenvolvimento, Aprovada, Em revisão, Descontinuada.
24. **Tratamento de erro:** edição de Receita Aprovada gera nova versão automaticamente, nunca sobrescreve.
25. **Melhorias futuras:** biblioteca de fotos do resultado esperado por Receita, para padronização visual.

### 3.19 Fichas Técnicas *(Módulo 13)*

1. **Objetivo:** ser a fonte única de custo de produção de cada item.
2. **Quem acessa:** Produção (Engenharia de Custos); leitura por Financeiro/Direção.
3. **Permissões:** criação/edição restritas a Produção.
4. **Layout geral:** lista de Fichas Técnicas + editor de composição/custo.
5. **Componentes:** tabela de Fichas Técnicas, editor com lista de Ingredientes/quantidades/custo, histórico de versões.
6. **Cards:** custo total vigente, rendimento.
7. **Indicadores:** custo médio por Produto.
8. **Gráficos:** evolução de custo ao longo das versões (mini-gráfico de linha).
9. **KPIs:** número de Fichas recalculadas no período.
10. **Tabelas:** lista de Fichas Técnicas; histórico de versões (F-044).
11. **Filtros:** por Produto, por estado (Vigente, Substituída, Descontinuada).
12. **Pesquisas:** por nome de Produto/Receita.
13. **Botões:** "Nova Ficha Técnica" (F-042), "Recalcular" (F-043, normalmente automático).
14. **Menus:** menu lateral (Fichas Técnicas).
15. **Ações rápidas:** "Ver impacto em Orçamentos abertos" após recálculo.
16. **Alertas:** impacto de recálculo em Orçamentos abertos (RN-019).
17. **Notificações:** Ficha Técnica recalculada automaticamente.
18. **Modais:** "Nova Ficha Técnica" (fator de perda de limpeza, rendimento, custos de apoio).
19. **Fluxo de navegação:** criada a partir de Receita aprovada; consultada a partir de Produtos/Orçamentos/Precificação.
20. **Ações automáticas:** recálculo automático por atualização de custo de Ingrediente (RN-019).
21. **Integração com outros módulos:** 12 (Receitas), 24 (Configurações), 14 (Precificação), 11 (Engenharia de Custos).
22. **Regras de visibilidade:** custo restrito a Produção/Financeiro/Direção.
23. **Estados da interface:** Rascunho, Vigente, Substituída, Descontinuada.
24. **Tratamento de erro:** duas Fichas Técnicas Vigentes para o mesmo item não são permitidas simultaneamente.
25. **Melhorias futuras:** simulação de custo ao trocar um Ingrediente por alternativa mais barata, antes de confirmar.

### 3.20 Precificação *(Módulo 14)*

1. **Objetivo:** garantir que todo preço tenha lastro em custo e margem definida.
2. **Quem acessa:** Produção/Financeiro; Direção (exceções).
3. **Permissões:** definição de margem-alvo por Direção/Financeiro; ajuste dentro da alçada por Comercial (na tela de Orçamentos).
4. **Layout geral:** lista de Produtos/Pacotes com preço calculado + painel de margem-alvo.
5. **Componentes:** tabela de Produtos/Pacotes com custo/preço/margem, painel de configuração de margem-alvo.
6. **Cards:** margem média, número de exceções aprovadas no período.
7. **Indicadores:** margem média, frequência de exceção.
8. **Gráficos:** distribuição de margem por Produto (histograma simples).
9. **KPIs:** preço médio, margem-alvo vigente.
10. **Tabelas:** lista de Produtos/Pacotes com custo, margem e preço.
11. **Filtros:** por categoria de Produto, por faixa de margem.
12. **Pesquisas:** por nome de Produto/Pacote.
13. **Botões:** "Definir Margem-Alvo" (F-045/F-077, atalho para Configurações), "Recalcular Preço" (F-046).
14. **Menus:** menu lateral (Precificação).
15. **Ações rápidas:** "Aprovar Exceção de Margem" (F-047).
16. **Alertas:** margem abaixo do mínimo (RN-023); preço fora de faixa esperada.
17. **Notificações:** preço recalculado após mudança de custo.
18. **Modais:** "Aprovar Exceção de Margem" (justificativa obrigatória).
19. **Fluxo de navegação:** consultada a partir de Orçamentos; margem-alvo editada a partir de Configurações (Módulo 24).
20. **Ações automáticas:** cálculo automático de preço a partir do custo vigente (RN-022).
21. **Integração com outros módulos:** 13 (Fichas Técnicas), 24 (Configurações), 08 (Orçamentos).
22. **Regras de visibilidade:** custo restrito a Financeiro/Direção; preço final visível a Comercial.
23. **Estados da interface:** normal, "margem-alvo não definida" (bloqueio com link para Configurações).
24. **Tratamento de erro:** preço não pode ser editado diretamente sem alterar custo ou margem — sempre calculado.
25. **Melhorias futuras:** sugestão de preço via IA (F-070) integrada diretamente nesta tela.

### 3.21 Compras *(Módulo 15)*

1. **Objetivo:** garantir o abastecimento junto a Fornecedores.
2. **Quem acessa:** Compras/Suprimentos.
3. **Permissões:** criação/edição restritas a Compras.
4. **Layout geral:** lista de Compras por status (Solicitada → Cotação → Pedido → Recebida → Conferida) + lista de Fornecedores.
5. **Componentes:** kanban/lista por status, tabela de Fornecedores.
6. **Cards:** Compras pendentes de conferência, valor total do período.
7. **Indicadores:** prazo médio de entrega, taxa de divergência.
8. **Gráficos:** gasto por Fornecedor (barras).
9. **KPIs:** total gasto no período.
10. **Tabelas:** lista de Compras; lista de Fornecedores com histórico (F-051).
11. **Filtros:** por Fornecedor, por status, por período.
12. **Pesquisas:** por nome de Fornecedor/Ingrediente.
13. **Botões:** "Ver Lista de Compras Sugerida" (F-048), "Cotar/Emitir Pedido" (F-049), "Receber e Conferir" (F-050).
14. **Menus:** menu lateral (Compras).
15. **Ações rápidas:** "Registrar divergência" a partir da conferência.
16. **Alertas:** item sem Fornecedor definido; prazo incompatível com data do Evento; divergência na conferência (RN-031).
17. **Notificações:** Compra conferida — Estoque atualizado.
18. **Modais:** "Cotar/Emitir Pedido", "Conferir Compra" (quantidade e validade recebidas).
19. **Fluxo de navegação:** lista sugerida gerada automaticamente a partir de Produção planejada; acessível também pelo Dashboard Estoque.
20. **Ações automáticas:** geração automática de lista de Compras (RN-030); geração de Estoque/Lote/Despesa na conferência.
21. **Integração com outros módulos:** 16 (Estoque), 17 (Lotes), 10 (Produção), 03 (Financeiro).
22. **Regras de visibilidade:** Compras/Suprimentos; custo total visível a Financeiro/Direção.
23. **Estados da interface:** cores por status do ciclo (Solicitada a Conferida).
24. **Tratamento de erro:** conferência com divergência exige decisão explícita antes de prosseguir.
25. **Melhorias futuras:** comparação automática de preço entre Fornecedores para o mesmo Ingrediente.

### 3.22 Estoque *(Módulo 16 — tela operacional, complementar ao Dashboard Estoque)*

1. **Objetivo:** operar o controle diário de saldo de Ingredientes/Produtos.
2. **Quem acessa:** Estoque/Logística.
3. **Permissões:** ajuste manual restrito a Estoque/Logística.
4. **Layout geral:** tabela detalhada por item, com histórico de movimentação.
5. **Componentes:** tabela de itens, painel de detalhe com histórico de movimentações.
6. **Cards:** itens críticos (abaixo do ponto de reposição).
7. **Indicadores:** giro de Estoque.
8. **Gráficos:** histórico de saldo do item (linha).
9. **KPIs:** saldo total valorizado.
10. **Tabelas:** movimentações por item (entrada/saída, origem, Lote).
11. **Filtros:** por item, por localização, por tipo de movimentação.
12. **Pesquisas:** por nome de item.
13. **Botões:** "Realizar Inventário" (F-053), "Configurar Ponto de Reposição" (F-054).
14. **Menus:** menu lateral (Estoque).
15. **Ações rápidas:** "Ver Lotes deste item" (Módulo 17).
16. **Alertas:** saldo insuficiente; abaixo do ponto de reposição.
17. **Notificações:** inventário concluído.
18. **Modais:** "Ajuste de Inventário" (com justificativa).
19. **Fluxo de navegação:** acessível pelo menu ou pelo Dashboard Estoque.
20. **Ações automáticas:** atualização automática de saldo (RN-032).
21. **Integração com outros módulos:** 15 (Compras), 10 (Produção), 17 (Lotes).
22. **Regras de visibilidade:** Estoque/Logística; custo restrito a Financeiro/Direção.
23. **Estados da interface:** normal, crítico (Vermelho-crítico).
24. **Tratamento de erro:** ajuste sem justificativa é bloqueado.
25. **Melhorias futuras:** leitura por código de barras (Roadmap).

### 3.23 Lotes *(Módulo 17)*

1. **Objetivo:** garantir rastreabilidade de origem e validade.
2. **Quem acessa:** Estoque/Logística, Produção.
3. **Permissões:** registro de descarte restrito a Estoque/Logística e Produção.
4. **Layout geral:** tabela de Lotes com destaque visual por proximidade de vencimento.
5. **Componentes:** tabela de Lotes, painel de detalhe (origem, consumo, validade).
6. **Cards:** Lotes vencendo em 7 dias, Lotes vencidos não descartados.
7. **Indicadores:** percentual de perda por vencimento.
8. **Gráficos:** nenhum.
9. **KPIs:** número de Lotes ativos.
10. **Tabelas:** lista de Lotes (item, quantidade, origem, validade, estado).
11. **Filtros:** por item, por validade, por estado.
12. **Pesquisas:** por item ou número de Lote.
13. **Botões:** "Registrar Descarte" (F-056).
14. **Menus:** menu lateral (Lotes).
15. **Ações rápidas:** "Ver Compra/Produção de origem" (F-055).
16. **Alertas:** validade próxima; tentativa de uso de Lote vencido (bloqueio).
17. **Notificações:** descarte registrado.
18. **Modais:** "Registrar Descarte" (motivo obrigatório).
19. **Fluxo de navegação:** acessível pelo Dashboard Estoque ou diretamente pelo menu.
20. **Ações automáticas:** priorização "primeiro que vence, primeiro que sai" (RN-034).
21. **Integração com outros módulos:** 15 (Compras), 10 (Produção), 16 (Estoque).
22. **Regras de visibilidade:** Estoque/Logística, Produção.
23. **Estados da interface:** Ativo, Em consumo, Vencido (Vermelho-crítico), Descartado, Esgotado.
24. **Tratamento de erro:** descarte sem motivo é bloqueado.
25. **Melhorias futuras:** alerta preditivo de vencimento com base em ritmo de consumo histórico.

### 3.24 Equipamentos *(Módulo 18, inclui Veículos)*

1. **Objetivo:** controlar disponibilidade e alocação de bens físicos reutilizáveis.
2. **Quem acessa:** Eventos/Operações, Compras/Suprimentos.
3. **Permissões:** cadastro por Compras; alocação/manutenção por Eventos/Operações.
4. **Layout geral:** tabela/calendário de alocação por item.
5. **Componentes:** tabela de itens, calendário de alocação, painel de detalhe.
6. **Cards:** itens disponíveis, itens em manutenção.
7. **Indicadores:** taxa de utilização.
8. **Gráficos:** nenhum.
9. **KPIs:** total de itens ativos.
10. **Tabelas:** lista de Equipamentos/Veículos com estado e próxima alocação.
11. **Filtros:** por tipo, por estado, por período de alocação.
12. **Pesquisas:** por nome/identificação do item.
13. **Botões:** "Cadastrar" (F-057), "Alocar" (F-058), "Registrar Manutenção/Baixa" (F-059).
14. **Menus:** menu lateral (Equipamentos).
15. **Ações rápidas:** "Ver Evento" a partir de uma alocação.
16. **Alertas:** conflito de alocação, com sugestão de alternativa (RN-035, bloqueante).
17. **Notificações:** manutenção concluída — item disponível novamente.
18. **Modais:** "Alocar a Evento", "Registrar Manutenção".
19. **Fluxo de navegação:** acessível pelo menu ou pela aba Equipamentos da tela de Eventos.
20. **Ações automáticas:** bloqueio automático de conflito de sobreposição.
21. **Integração com outros módulos:** 07 (Eventos), 03 (Financeiro, Despesa de manutenção).
22. **Regras de visibilidade:** Eventos/Operações e Compras.
23. **Estados da interface:** Disponível (verde), Alocado (Brasa), Em manutenção (âmbar), Baixado (cinza).
24. **Tratamento de erro:** tentativa de alocar item em manutenção é bloqueada.
25. **Melhorias futuras:** QR code por item para check-in/check-out físico no dia do Evento.

### 3.25 Funcionários *(Módulo 19)*

1. **Objetivo:** manter o cadastro e o custo de mão de obra da equipe.
2. **Quem acessa:** Pessoas/Mão de Obra.
3. **Permissões:** criação/edição/desligamento restritos a Pessoas/Mão de Obra; dados de remuneração restritos a Financeiro/Direção.
4. **Layout geral:** lista de Funcionários + painel de detalhe (histórico de Alocações).
5. **Componentes:** tabela de Funcionários, painel de detalhe.
6. **Cards:** total de Funcionários ativos, fixos vs. freelancers.
7. **Indicadores:** custo médio de mão de obra por Evento.
8. **Gráficos:** nenhum.
9. **KPIs:** Funcionários alocados no período.
10. **Tabelas:** lista de Funcionários; histórico de Alocações no painel de detalhe.
11. **Filtros:** por tipo de vínculo, por função, por status.
12. **Pesquisas:** por nome.
13. **Botões:** "Cadastrar" (F-060), "Desligar" (F-062).
14. **Menus:** menu lateral (Funcionários).
15. **Ações rápidas:** "Ver Escala" (Módulo 20).
16. **Alertas:** Alocação sem valor definido (RN-036).
17. **Notificações:** nenhuma própria.
18. **Modais:** "Cadastrar/Editar Funcionário".
19. **Fluxo de navegação:** acessível pelo menu; drill-down para Escalas (Módulo 20).
20. **Ações automáticas:** consolidação automática de custo a partir de Alocações Realizadas (F-061).
21. **Integração com outros módulos:** 20 (Escalas), 10 (Produção), 07 (Eventos), 03 (Financeiro).
22. **Regras de visibilidade:** dados cadastrais para Pessoas/Mão de Obra; remuneração restrita a Financeiro/Direção (CG-05).
23. **Estados da interface:** Ativo, Afastado, Inativo/Desligado.
24. **Tratamento de erro:** desligamento de Funcionário com Alocação futura pendente exige confirmação explícita.
25. **Melhorias futuras:** avaliação de desempenho estruturada por Evento.

### 3.26 Escalas *(Módulo 20)*

1. **Objetivo:** planejar quem trabalha em cada Evento/Produção.
2. **Quem acessa:** Pessoas/Mão de Obra, Eventos/Operações.
3. **Permissões:** sugestão automática; confirmação/ajuste por Pessoas/Mão de Obra.
4. **Layout geral:** calendário de Escalas por Evento/Produção.
5. **Componentes:** calendário, lista de Alocações por Evento.
6. **Cards:** Escalas pendentes de confirmação, Eventos sem escala definida.
7. **Indicadores:** taxa de acerto de dimensionamento de equipe.
8. **Gráficos:** nenhum.
9. **KPIs:** Funcionários escalados no período.
10. **Tabelas:** lista de Alocações por Evento (Funcionário, função, horário, status).
11. **Filtros:** por Evento, por Funcionário, por período.
12. **Pesquisas:** por nome de Funcionário/Evento.
13. **Botões:** "Confirmar/Ajustar Escala" (F-064).
14. **Menus:** menu lateral (Escalas).
15. **Ações rápidas:** "Substituir Funcionário" em caso de indisponibilidade.
16. **Alertas:** escala não confirmada a X dias do Evento (RN-037); sobreposição de horário (bloqueio).
17. **Notificações:** escala confirmada — Funcionários notificados.
18. **Modais:** "Ajustar Escala" (adicionar/remover Funcionário, trocar função).
19. **Fluxo de navegação:** gerada automaticamente na confirmação do Evento; acessível pela aba Equipe da tela de Eventos.
20. **Ações automáticas:** sugestão automática de escala (RN-037).
21. **Integração com outros módulos:** 19 (Funcionários), 07 (Eventos), 24 (Configurações — proporção de escala).
22. **Regras de visibilidade:** Pessoas/Mão de Obra e Eventos/Operações.
23. **Estados da interface:** "parâmetro não definido" (bloqueio com link para Configurações), Planejada, Confirmada, Realizada, Cancelada.
24. **Tratamento de erro:** sobreposição de horário do mesmo Funcionário é bloqueada.
25. **Melhorias futuras:** app mobile de confirmação de presença pelo próprio Funcionário (Roadmap).

### 3.27 Bancos *(Módulo 27)*

1. **Objetivo:** centralizar o cadastro de Banco, Conta e Cartão.
2. **Quem acessa:** Financeiro.
3. **Permissões:** cadastro/edição/encerramento restritos a Financeiro.
4. **Layout geral:** lista de Bancos/Contas + painel de detalhe com saldo e histórico.
5. **Componentes:** tabela de Contas agrupadas por Banco, painel de detalhe.
6. **Cards:** saldo consolidado total, saldo por tipo de Conta (pessoal/empresarial/investimento).
7. **Indicadores:** saldo consolidado por tipo.
8. **Gráficos:** distribuição de saldo por Banco (pizza ou barras).
9. **KPIs:** número de Contas ativas.
10. **Tabelas:** lista de Contas/Cartões; movimentações no painel de detalhe.
11. **Filtros:** por Banco, por tipo de Conta, por status.
12. **Pesquisas:** por nome do Banco/Conta.
13. **Botões:** "Cadastrar Banco" (F-092), "Cadastrar Conta/Cartão" (F-093/F-094), "Encerrar" (F-095).
14. **Menus:** menu lateral (Bancos).
15. **Ações rápidas:** "Ver Histórico de Movimentações" (F-097), "Ir para Conciliação".
16. **Alertas:** herdados de RN-043/RN-044 (exibidos aqui como resumo).
17. **Notificações:** Conta/Cartão cadastrado com sucesso.
18. **Modais:** "Cadastrar Conta" (tipo: pessoal, empresarial, digital, investimento, internacional), "Cadastrar Cartão" (limite, vencimento).
19. **Fluxo de navegação:** acessível pelo menu; usado como referência em Financeiro Pessoal/Empresarial.
20. **Ações automáticas:** nenhuma própria — fornece dado às automações do Financeiro.
21. **Integração com outros módulos:** 02, 03, 22 (IA — importação).
22. **Regras de visibilidade:** restrita a Financeiro/Direção.
23. **Estados da interface:** Ativa, Encerrada.
24. **Tratamento de erro:** Conta encerrada não aceita novo Pagamento (bloqueio).
25. **Melhorias futuras:** Cartão como entidade própria com fatura detalhada (M-003A-04, ainda pendente).

### 3.28 Conciliação Bancária *(Módulo 27 — sub-tela financeira)*

1. **Objetivo:** garantir que todo Pagamento registrado corresponda a um lançamento real.
2. **Quem acessa:** Financeiro.
3. **Permissões:** conciliação e tratamento de divergência restritos a Financeiro.
4. **Layout geral:** tela de duas colunas — Pagamentos registrados (esquerda) vs. lançamentos do extrato (direita) — com sugestões de correspondência ao centro.
5. **Componentes:** duas listas paralelas, indicadores visuais de correspondência (linha conectando os dois lados quando batem).
6. **Cards:** total conciliado, total pendente, divergências abertas.
7. **Indicadores:** confiabilidade do Fluxo de Caixa (percentual conciliado).
8. **Gráficos:** nenhum.
9. **KPIs:** percentual conciliado do período.
10. **Tabelas:** Pagamentos e lançamentos do extrato, lado a lado.
11. **Filtros:** por Conta, por período, por status (conciliado/pendente/divergente).
12. **Pesquisas:** por valor/data.
13. **Botões:** "Importar Extrato" (F-068/FL-023), "Conciliar Selecionados", "Marcar Divergência".
14. **Menus:** menu lateral (Bancos → Conciliação).
15. **Ações rápidas:** aceitar sugestão de correspondência com um clique.
16. **Alertas:** Conta com pendência de conciliação há mais de um período definido (RN-044); possível duplicidade; possível lançamento pessoal (RN-005).
17. **Notificações:** extrato importado com sucesso; conciliação concluída.
18. **Modais:** "Importar Extrato" (seleção de arquivo/Conta); "Tratar Divergência".
19. **Fluxo de navegação:** acessível a partir de Bancos ou do Dashboard Financeiro Empresarial.
20. **Ações automáticas:** sugestão de categorização e conciliação via IA (RN-043); nenhuma conciliação é efetivada sem confirmação em caso de ambiguidade.
21. **Integração com outros módulos:** 03 (Financeiro Empresarial), 02 (Financeiro Pessoal), 22 (IA).
22. **Regras de visibilidade:** restrita a Financeiro/Direção.
23. **Estados da interface:** conciliado (verde), pendente (cinza), divergente (âmbar).
24. **Tratamento de erro:** divergência nunca é corrigida automaticamente — exige decisão humana registrada.
25. **Melhorias futuras:** conciliação em lote com regras salvas pelo usuário ("sempre categorizar X como Y").

### 3.29 Configurações *(Módulo 24)*

1. **Objetivo:** ser o local único onde todo parâmetro de negócio pendente é definido.
2. **Quem acessa:** Direção, Administrador do Sistema; Produção/Financeiro conforme o parâmetro.
3. **Permissões:** cada grupo de parâmetro tem dono claro (ex.: consumo por Produção, margem por Financeiro/Direção).
4. **Layout geral:** lista de categorias de parâmetro (Consumo, Perdas/Rendimento, Precificação, Escalas, Cancelamento) com formulário por categoria.
5. **Componentes:** menu de categorias à esquerda, formulário à direita, indicador de "parâmetros pendentes".
6. **Cards:** quantidade de parâmetros definidos vs. pendentes.
7. **Indicadores:** nenhum de negócio — indicador de completude de configuração.
8. **Gráficos:** nenhum.
9. **KPIs:** percentual de parâmetros configurados.
10. **Tabelas:** lista de parâmetros por categoria, com valor atual e data da última alteração.
11. **Filtros:** por categoria, por status (definido/pendente).
12. **Pesquisas:** por nome do parâmetro.
13. **Botões:** "Definir Parâmetro de Consumo" (F-075), "Definir Perdas/Rendimento" (F-076), "Definir Margem-Alvo" (F-077), "Definir Proporção de Escala" (F-078), "Definir Política de Cancelamento" (F-079).
14. **Menus:** menu lateral de categorias.
15. **Ações rápidas:** "Ir para onde este parâmetro é usado" (ex.: da margem-alvo direto para Precificação).
16. **Alertas:** parâmetro crítico ainda não definido, com destaque visual persistente até ser resolvido.
17. **Notificações:** parâmetro salvo com sucesso, com aviso do impacto ("afeta X Orçamentos abertos").
18. **Modais:** formulário de definição por parâmetro (pode ser inline em vez de modal, dado o volume de campos).
19. **Fluxo de navegação:** acessível pelo menu; também acessado via links diretos a partir de telas bloqueadas por parâmetro ausente (Produção, Precificação, Escalas, Eventos).
20. **Ações automáticas:** nenhuma — este módulo é 100% definição humana, nunca suposição do sistema.
21. **Integração com outros módulos:** 10, 14, 20, 07 (consomem os parâmetros).
22. **Regras de visibilidade:** Direção e Administrador do Sistema veem tudo; demais áreas veem apenas os parâmetros de sua responsabilidade.
23. **Estados da interface:** "Definido" (verde), "Pendente" (âmbar, com badge de contagem no menu).
24. **Tratamento de erro:** valores fora de faixas plausíveis (ex.: percentual de perda negativo) são bloqueados.
25. **Melhorias futuras:** assistente de configuração inicial guiado (M-003A-01 style, já sugerido no TCOS-003).

### 3.30 Administração *(Módulo 25)*

1. **Objetivo:** governar acesso, integridade e auditabilidade técnica do sistema.
2. **Quem acessa:** Administrador do Sistema; Direção (consulta).
3. **Permissões:** gestão de usuários/permissões restrita ao Administrador do Sistema.
4. **Layout geral:** abas internas (Usuários e Permissões, Log de Auditoria, Central de Alertas, Saúde do Sistema).
5. **Componentes:** tabela de usuários, visualizador de log, central de alertas consolidada, painel de saúde.
6. **Cards:** usuários ativos, alertas pendentes, parâmetros de Configurações não definidos.
7. **Indicadores:** tempo médio de tratamento de alerta.
8. **Gráficos:** nenhum.
9. **KPIs:** número de usuários ativos.
10. **Tabelas:** usuários e suas Áreas de Empresa vinculadas (F-080); log de auditoria filtrável (F-081); lista de alertas (F-082).
11. **Filtros:** por usuário, por área, por período, por tipo de alerta.
12. **Pesquisas:** por nome de usuário ou por entidade auditada.
13. **Botões:** "Adicionar Usuário", "Editar Permissões", "Marcar Alerta como Tratado".
14. **Menus:** abas internas.
15. **Ações rápidas:** "Ver detalhe da alteração" a partir de uma linha do log.
16. **Alertas:** central consolidada de todos os alertas do sistema (RN-047).
17. **Notificações:** usuário criado/editado com sucesso.
18. **Modais:** "Adicionar/Editar Usuário" (nome, Área(s) de Empresa vinculada(s)).
19. **Fluxo de navegação:** acessível apenas pelo menu (não é destino de drill-down de outras telas).
20. **Ações automáticas:** nenhuma — é o próprio ponto de controle manual do sistema.
21. **Integração com outros módulos:** todos (governança transversal).
22. **Regras de visibilidade:** restrita ao Administrador do Sistema; Direção com leitura.
23. **Estados da interface:** normal, "alerta crítico pendente" (badge vermelho no menu principal).
24. **Tratamento de erro:** tentativa de remover a única permissão de Administrador do Sistema é bloqueada (trava de segurança).
25. **Melhorias futuras:** perfis de acesso pré-configurados por função (ex.: "Perfil Comercial", "Perfil Produção"), reduzindo configuração manual por usuário.

---

## 4. Navegação do Sistema

- **Como o usuário entra:** tela de login → redirecionamento automático ao Dashboard CEO (papéis com acesso) ou ao Dashboard/tela mais relevante ao seu papel (ex.: Produção entra direto no Dashboard Produção).
- **Como navega:** menu lateral fixo, com os 27 módulos agrupados pelas mesmas Áreas da Empresa já definidas (Comercial/CRM, Produção, Compras/Suprimentos, Estoque/Logística, Eventos/Operações, Financeiro, Marketing, Pessoas/Mão de Obra, Administrativo/Documentos, BI/Direção Executiva); cada área é uma seção colapsável do menu.
- **Como retorna:** breadcrumb no topo de toda tela de detalhe (ex.: Eventos > Evento #123 > Orçamento); botão "voltar" sempre disponível; clique no logo retorna ao Dashboard CEO.
- **Como pesquisa:** barra de busca global no cabeçalho (Seção 5.3, melhoria de UX identificada na auditoria), pesquisando simultaneamente Cliente, Evento, Orçamento e Contrato; cada tela também tem pesquisa local por seus próprios itens.
- **Como filtra:** todo filtro (período, status, categoria) é combinável e persiste durante a sessão de navegação dentro do mesmo módulo.
- **Como cria registros:** botão de ação primário (cor Brasa) sempre no canto superior direito da lista ("Novo X"); abre modal ou tela dedicada, conforme a complexidade do formulário (modal para cadastros simples, tela dedicada para Orçamento/Contrato/Ficha Técnica).
- **Como edita:** clique na linha/card do item abre o painel/tela de detalhe em modo de edição inline; toda edição de item com histórico obrigatório (PF-04) confirma antes de salvar, mostrando o que vai mudar.
- **Como exclui:** nunca há "excluir" no sentido literal (CG-01) — o botão correspondente é sempre "Inativar", "Cancelar", "Encerrar" ou "Descontinuar", com confirmação explícita e, quando aplicável, motivo obrigatório.
- **Como imprime:** botão "Imprimir" disponível em telas de documento (Orçamento, Contrato) e em relatórios de Dashboard, gerando visualização otimizada para impressão.
- **Como exporta:** botão "Exportar" (PDF ou planilha) disponível em toda tabela/Dashboard relevante à gestão (Financeiro, Metas, Produção).
- **Como importa:** fluxo dedicado de importação (extrato bancário, Seção 3.28) com passos claros: selecionar arquivo → pré-visualizar → confirmar.
- **Como utiliza IA:** toda sugestão de IA aparece com um ícone e cor distintos (roxo-IA, ver Design System), nunca se confunde com dado confirmado; usuário sempre vê um botão "Aceitar" e "Recusar" lado a lado.
- **Como acessa histórico:** toda entidade com histórico (praticamente todas, CG-01) tem uma aba ou link "Ver histórico" no painel de detalhe, mostrando versões/alterações anteriores com data e autor.
- **Como utiliza notificações:** sino de notificações no cabeçalho, com contagem de não lidas; painel lateral desliza ao clicar, listando notificações recentes agrupadas por módulo; alertas críticos (RN-047) também aparecem como banner persistente na tela relevante até serem tratados.

---

## 5. Design System

### 5.1 Filosofia Visual

O THE CHARCOAL OS deve parecer **um único sistema**, mesmo integrando vida financeira pessoal, empresa, produção, eventos, CRM, marketing e IA em um só lugar — a consistência visual é o que comunica que tudo está conectado (PF-02, compartilhamento automático). A estética evoca o universo da marca (brasa, carvão, produção artesanal) sem infantilizar a ferramenta: é uma ferramenta de gestão séria, usada por quem administra dinheiro e operação real.

### 5.2 Organização e Hierarquia

- **Hierarquia de tela:** Dashboard (visão agregada) → Lista (coleção de itens) → Detalhe (um item específico) → Modal (ação pontual). Nenhuma tela pula mais de um nível sem passar pelos breadcrumbs.
- **Hierarquia visual dentro da tela:** título da página (H1) → seção/aba (H2) → título de card (H3) → corpo → legenda/metadado (menor contraste).

### 5.3 Espaçamentos

Grid de 8px como unidade base (múltiplos de 8 para todo espaçamento e dimensionamento de componente), garantindo alinhamento consistente entre Dashboards com muitos cards e telas de formulário mais simples.

### 5.4 Tipografia

Fonte sans-serif única em todo o sistema (peso variável: regular para corpo, semibold para títulos e valores de KPI, bold apenas para alertas críticos). Números de KPI recebem tratamento tipográfico maior e mais forte que qualquer outro texto da tela — são o que o usuário deve ver primeiro.

### 5.5 Ícones

Estilo de linha (outline), consistente em todo o sistema; ícone de IA sempre o mesmo símbolo (ex.: uma pequena "faísca"), nunca reaproveitado para outro significado, para que o usuário associe esse ícone exclusivamente a conteúdo gerado/sugerido por IA (reforça RN-041 visualmente).

### 5.6 Componentes Reutilizáveis

Card de KPI, Card de progresso (usado em Metas), Tabela com paginação e ordenação, Filtro lateral/superior combinável, Modal padrão (cabeçalho, corpo, rodapé com ações), Botão primário/secundário/terciário, Badge de status (uma cor por estado do ciclo de vida da entidade), Alerta inline (dentro de formulário), Banner de alerta persistente (topo de tela), Notificação toast (efêmera), Menu lateral colapsável, Breadcrumb, Componente "Documentos Anexados" (reutilizado em Contratos, Compras, Clientes, Fornecedores — resolve a ausência de tela própria de Documentos, Módulo 23), Componente de sugestão de IA (com botões Aceitar/Recusar).

### 5.7 Cores por Categoria

- **Brasa** (laranja-avermelhado): cor de marca, usada em ações primárias, estado "ativo/confirmado" e destaques.
- **Carvão** (grafite escuro): texto principal, elementos de alta ênfase, fundo do menu lateral.
- **Cinza-claro:** fundos neutros, estados inativos/desabilitados.
- **Verde-sucesso:** confirmações, Metas atingidas, itens "Disponível"/"Concluído".
- **Amarelo/Âmbar-atenção:** alertas não críticos, "Metas não atingidas" (tom deliberadamente não punitivo), itens "Em manutenção".
- **Vermelho-crítico:** alertas de alta prioridade, bloqueios, itens "Vencido"/"Cancelado".
- **Roxo-IA:** exclusivo para qualquer conteúdo gerado ou sugerido por Inteligência Artificial, em qualquer tela do sistema.

### 5.8 Estados dos Botões

Normal, hover (leve escurecimento/elevação), focus (contorno visível para acessibilidade), disabled (opacidade reduzida, cursor bloqueado), loading (spinner substitui o texto, botão desabilitado durante a ação).

### 5.9 Estados dos Cards

Normal, carregando (skeleton), erro/indisponível (ícone de atenção + tooltip, nunca card em branco silencioso), destaque (borda Brasa quando o card representa uma ação pendente do usuário).

### 5.10 Estados dos Indicadores

Atualizado (normal), desatualizado/sem dado (cinza com aviso, nunca zero silencioso), acima da Meta (verde), abaixo da Meta (âmbar/vermelho conforme severidade).

### 5.11 Responsividade

- **Desktop:** layout completo, menu lateral fixo expandido, grids de 2 a 4 colunas nos Dashboards.
- **Tablet:** menu lateral colapsa para ícones (expansível por toque), grids reduzem para 1–2 colunas, tabelas priorizam colunas essenciais com "ver mais" para o restante.
- **Mobile:** navegação por abas inferiores (Dashboard CEO, Eventos, Financeiro, Notificações, Mais), uma coluna única, cards empilhados verticalmente, tabelas viram listas de cartões; funcionalidades operacionais de campo (confirmação de Escala, consulta de Evento do dia) são priorizadas nesta camada, consistente com o Roadmap de aplicativo mobile já registrado no Framework (Seção 25).

---

## 6. Experiência do Usuário

O THE CHARCOAL OS precisa ser aprendido rapidamente por qualquer pessoa da equipe, do proprietário ao Funcionário temporário de um Evento. Isso se traduz em seis compromissos de experiência:

- **Simplicidade:** cada tela mostra primeiro o que mais importa (KPI, status, ação pendente) — detalhes secundários ficam a um clique de distância, nunca poluindo a primeira visão.
- **Velocidade:** ações mais frequentes (criar Evento, registrar Pagamento, confirmar Escala) estão sempre a, no máximo, dois cliques do Dashboard relevante; buscas e filtros respondem de forma instantânea à percepção do usuário.
- **Profissionalismo:** o sistema nunca usa linguagem informal ou "gamificada" para tratar dinheiro, custo ou desempenho — números são apresentados com clareza e seriedade, mesmo quando o resultado é negativo (ex.: Meta não atingida em âmbar, não em vermelho punitivo, seção 5.7).
- **Inteligência:** toda sugestão de IA é visível, identificável (cor Roxo-IA) e nunca se disfarça de decisão humana já tomada — o sistema "ajuda a pensar", nunca "decide escondido" (PF-06).
- **Segurança:** dados sensíveis (custo, margem, remuneração, dados pessoais) só aparecem para quem tem permissão (CG-05); toda ação irreversível pede confirmação explícita; nada é "excluído" de verdade — apenas inativado, com histórico completo sempre disponível.
- **Confiabilidade:** todo número no sistema é rastreável até sua origem (RN-039/040) — se um dado está desatualizado ou indisponível, o sistema diz isso claramente, nunca esconde ou inventa um valor.

---

## 7. Resumo para o Proprietário

Desenhamos como vai ser, na prática, usar o THE CHARCOAL OS no dia a dia — as 30 telas principais do sistema (11 painéis de gestão e 19 telas de trabalho), como cada uma se parece, o que cada botão faz, e como uma tela leva à outra.

Isso é importante porque, até agora, os documentos diziam o que o sistema é capaz de fazer — este documento diz **como vai ser sentir usando**: onde clicar para confirmar um evento, como a Inteligência Artificial vai aparecer na tela (sempre identificada, nunca escondida), como um alerta de margem baixa vai chamar a atenção do usuário, e como alguém que nunca usou o sistema vai conseguir aprender rápido.

O benefício direto é reduzir o risco de retrabalho na hora de construir as telas de verdade: qualquer profissional de design ou desenvolvimento vai conseguir seguir este documento sem precisar adivinhar decisões — cor, hierarquia, comportamento de cada botão e tela já estão definidos.

Este documento se conecta a todos os quatro anteriores (o que existe, o que o sistema faz, o que o usuário faz, como tudo acontece no tempo) e prepara diretamente a próxima etapa: quando decidirmos a Arquitetura, o Banco de Dados e o Desenvolvimento propriamente dito, será a partir exatamente destas 30 telas e deste Design System — nenhuma dessas decisões técnicas foi tomada ainda.

---

## 8. TCOS QUALITY GATE EXECUTIVO

**1. Resumo Executivo**
Projetadas as 30 telas obrigatórias (11 Dashboards + 19 telas de módulo), cada uma com os 25 campos exigidos (Dashboards com detalhamento adicional de layout/origem de dado/IA), mais Navegação do Sistema, Design System completo e capítulo de Experiência do Usuário. Nenhum documento anterior foi alterado.

**2. Estado atual do projeto**
Fases 000 a 004 encerradas e oficiais; Fase 005 em validação. Nenhuma fase técnica (Arquitetura, Banco de Dados, APIs, Desenvolvimento) foi iniciada.

**3. Documentos oficiais existentes**
Os 8 já registrados na Executive Memory, mais este documento em rascunho.

**4. Dependências desta fase**
30 entidades, 47 Regras de Negócio, 27 módulos, 98 funcionalidades e 30 fluxos — todos referenciados, nenhum reescrito.

**5. Pendências abertas**
Validação formal deste documento; parâmetros do Módulo 24 (afetam diretamente os estados de bloqueio das telas de Produção, Precificação e Escalas); M-003A-03/04; M-004-01/02; decisão sobre retomar a entrevista de descoberta.

**6. Dúvidas encontradas**
Nenhuma nova além das já herdadas do Business Discovery.

**7. Riscos ativos**
R-000-03/R-002-01, R-001-01/R-002-02, R-002A-01 — herdados; nenhum bloqueia o design de UX/UI, pois todas as telas dependentes já preveem estado de "parâmetro não definido".

**8. Novos riscos encontrados**
Nenhum.

**9. Inconsistências encontradas**
Nenhuma.

**10. Conflitos entre documentos**
Nenhum.

**11. Telas sem funcionalidades**
Nenhuma — toda tela documentada referencia ao menos uma funcionalidade F-XXX já oficial.

**12. Funcionalidades sem telas**
Nenhuma das 98 funcionalidades ficou sem componente de UI — as de natureza transversal (F-072–F-074, Documentos; F-080/F-081/F-083, Administração) foram resolvidas com o componente reutilizável "Documentos Anexados" e com a tela de Administração (Seção 3.30), respectivamente.

**13. Fluxos sem navegação**
Nenhum — os 30 fluxos do TCOS-004 mapeiam para sequências de tela documentadas na Seção 4.

**14. Módulos sem interface**
Nenhum dos 27 módulos — Módulo 23 (Documentos) é servido pelo componente reutilizável "Documentos Anexados" (Design System, Seção 5.6) em vez de tela própria, decisão de design explicitamente registrada, não uma lacuna.

**15. Melhorias sugeridas**
- M-005-01: barra de busca global unificada (Cliente, Evento, Orçamento, Contrato) — identificada na auditoria de abertura.
- M-005-02: assistente de configuração inicial guiado no Módulo 24 (reforça M-003A-01).
- M-005-03: perfis de acesso pré-configurados por função no Módulo 25 (Administração).

**16. Impacto nas próximas fases**
Estas 30 telas e o Design System tornam-se a referência obrigatória de experiência para Arquitetura, Banco de Dados e Desenvolvimento — nenhuma dessas fases deve introduzir uma tela, fluxo de navegação ou componente visual que contradiga o que está aqui documentado, sem registrar formalmente o motivo.

**17. Quality Score: 9,5/10**
Justificativa técnica: cobertura completa das 30 telas com os 25 campos exigidos, Design System coeso e consistente com a identidade de marca já registrada no Manifesto (Framework, Seção 21), e auditoria genuína que identificou decisões de design defensáveis (não gaps) para Documentos, CRM, Marketing e IA. Não é 10 porque a experiência de Pós-venda (FL-030) permanece a mais fracamente sustentada por falta de regra/funcionalidade dedicada — a tela de Clientes cobre o mínimo possível, mas não mais que isso, até que o negócio real seja confirmado.

**18. Atualização do PROJECT_MEMORY.md:** ver commit correspondente.

**19. Estatísticas Finais**
- Quantidade de páginas: ~55 páginas equivalentes.
- Quantidade de telas: 30 (11 Dashboards + 19 telas de módulo).
- Quantidade de dashboards: 11.
- Quantidade de módulos: 27 (26 com tela própria + 1 servido por componente reutilizável).
- Quantidade de componentes: 15 componentes reutilizáveis catalogados no Design System (Seção 5.6).
- Quantidade de fluxos: 30 (referenciados do TCOS-004, 0 novos).
- Quantidade de entidades: 30 (referenciadas, 0 novas).
- Quantidade de regras: 47 (referenciadas, 0 novas).
- Quantidade de integrações: 15 (reutilizadas da Matriz de Integração do TCOS-004).
- Quantidade de decisões: 1 (D-005-01, ver `PROJECT_MEMORY.md`).
- Quantidade de riscos: 0 novos (3 herdados).
- Quantidade de pendências: 5 (validação do documento + 4 herdadas).
- Quantidade de melhorias: 3 (M-005-01 a M-005-03).
- Percentual estimado de maturidade do projeto: **55%** (subiu de 48% — toda a experiência de uso está agora projetada e auditada; falta majoritariamente decisão técnica de arquitetura, dados e código, além da confirmação de parâmetros reais de negócio).

---

*Fim do documento — THE CHARCOAL OS UX/UI SPECIFICATION v1.0.0*
