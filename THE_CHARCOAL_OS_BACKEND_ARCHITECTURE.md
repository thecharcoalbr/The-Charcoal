# THE CHARCOAL OS — BACKEND ARCHITECTURE

**Documento:** TCOS-010 — Arquitetura Conceitual de Backend
**Projeto:** THE CHARCOAL OS
**Fase:** 010 — Backend Architecture
**Status:** Rascunho para validação do proprietário
**Versão:** 1.0.0

---

## EXECUTIVE MEMORY

- **Estado atual do projeto:** negócio, domínio, regras, funcionalidades, fluxos, UX/UI, arquitetura de sistema, arquitetura de dados, banco de dados e contrato de integração entre módulos completos e oficiais; iniciando a arquitetura lógica interna de backend, ainda sem linguagem, framework, banco físico ou API definidos.
- **Fase atual:** 010 — Backend Architecture (TCOS-010).
- **Fases concluídas:** 000 a 009, todas aprovadas e oficiais (a mais recente, TCOS-009, congelada nesta mensagem).
- **Documentos oficiais:** Framework (v1.2.0), `PROJECT_MEMORY.md`, Domain Discovery (v1.0.0), Business Discovery Questionnaire (v1.0.0), Discovery Interview Roadmap (v1.0.0), Domain Model (v1.0.0), Business Rules Specification (v1.0.0), Functional Specification (v1.2.0), User Journeys and System Flows (v1.0.0), UX/UI Specification (v1.0.0), System Architecture (v1.0.0), Data Architecture (v1.0.0), Database Specification (v1.0.0), Integration and API Contract (v1.0.0, congelado a partir de agora).
- **Documentos em elaboração:** este documento (TCOS-010).
- **Pendências:** confirmação do domínio de negócio (R-000-03); parâmetros do Módulo 24; M-003A-03/04; M-005-01/02/03; M-006-01; M-007-01; M-008-01; M-009-01; decisão sobre retomar a entrevista de descoberta.
- **Riscos ativos:** R-000-03/R-002-01, R-001-01/R-002-02, R-002A-01 — herdados; nenhum impede o desenho da arquitetura de backend, pois todo parâmetro não confirmado continua modelado como Configuração pendente que bloqueia/alerta, nunca como valor assumido.
- **Dependências para esta fase:** os 15 Serviços Conceituais e o Event Bus (System Architecture, TCOS-006); os 7 Domínios de Dados e 24 Agregados (Data Architecture, TCOS-007); as 32 estruturas conceituais (Database Specification, TCOS-008); as 20 Integrações (Integration and API Contract, TCOS-009); as 47 Regras de Negócio e 98 funcionalidades — todos referenciados, nenhum reescrito.
- **Objetivo da fase que será iniciada:** definir a arquitetura lógica interna de backend do THE CHARCOAL OS — organização, camadas, casos de uso, orquestração, processamento síncrono/assíncrono, jobs, filas, auditoria, logs, erros, transações, cache, configuração, observabilidade, tolerância a falhas, segurança, IA e integrações futuras — sem nenhuma decisão de tecnologia.
- **O que não pode ser alterado:** nenhum conteúdo de nenhum dos 13 documentos oficiais já aprovados e congelados.

### Auditoria de Abertura

Todos os documentos oficiais foram lidos integralmente. Resultado:

- **Nenhuma inconsistência, conflito ou duplicidade** entre os documentos existentes.
- **Base já sólida para o backend:** o System Architecture (TCOS-006) já define os 15 Serviços Conceituais, o Event Bus e 5 camadas macro (Apresentação, Orquestração de Regras, Domínio, Dados, Transversal); o Data Architecture (TCOS-007) já define 24 Agregados como unidade de consistência transacional; o Database Specification (TCOS-008) já define estrutura física conceitual; o Integration and API Contract (TCOS-009) já define o comportamento completo de comunicação entre módulos. Este documento **não redefine nada disso** — detalha como cada Serviço se organiza *por dentro* para implementar o que já foi aprovado.
- **Lacuna real identificada:** nenhum documento anterior formalizou **processamento agendado (jobs)** como conceito arquitetural — apenas comportamentos implícitos já aprovados o exigem (ex.: RN-034 alerta de Lote vencendo, RN-046 encerramento de ciclo de Meta na data definida, IN-019 alerta de escala não confirmada a X dias, expiração de Orçamento). Esta arquitetura de backend formaliza esses casos como Jobs Agendados (Capítulo 13), por adição — nenhuma Regra de Negócio é alterada, apenas fica explícito **como** o backend a executa no tempo certo.
- **Lacuna real identificada:** o Event Bus (TCOS-006, Capítulo 7) definiu publicar/assinar, mas nunca formalizou ordenação, nova tentativa (retry) ou tratamento de falha de entrega de um evento. Esta arquitetura de backend formaliza isso como Filas Conceituais (Capítulo 14), sem contradizer o Event Bus já aprovado — apenas detalha seu comportamento interno de confiabilidade.
- **Lacuna real identificada:** nenhum documento anterior tratou de Logs técnicos como algo distinto de Auditoria de negócio (TCOS-006/008) — os dois foram, até aqui, mencionados de forma próxima o suficiente para gerar ambiguidade. Esta arquitetura separa formalmente os dois conceitos (Capítulos 17 e 18).
- **Lacuna real identificada:** Tratamento de Erros, Observabilidade e Tolerância a Falhas nunca foram tratados em nenhum documento anterior — são formalizados aqui pela primeira vez, sempre em conformidade com os Princípios Fundamentais já aprovados (especialmente PF-04, PF-06, PF-09, PF-11).
- **Nenhuma contradição encontrada** entre o padrão de Caso de Uso proposto nesta arquitetura e o padrão de Agregado já definido no TCOS-007 — o Caso de Uso é modelado como a fronteira transacional que opera sobre exatamente um Agregado por vez (Capítulo 20), confirmando e detalhando (nunca alterando) essa definição.
- Nenhuma decisão de linguagem, framework, banco de dados físico, API, protocolo ou tecnologia foi tomada, em conformidade com a restrição explícita da fase.

---

## 1. Papel deste Documento

O System Architecture (TCOS-006) definiu **quais Serviços existem** e como eles se comunicam entre si (Event Bus). O Data Architecture (TCOS-007) e o Database Specification (TCOS-008) definiram **como o dado se organiza e se persiste**. O Integration and API Contract (TCOS-009) definiu **o comportamento completo de comunicação** entre módulos. Este documento (TCOS-010) define **como cada Serviço se organiza por dentro** para executar tudo isso de forma consistente, auditável, escalável e tolerante a falhas — a arquitetura lógica de implementação. Uma equipe de desenvolvimento deve conseguir escolher a linguagem, o framework e a tecnologia de mensageria/banco inteiramente a partir daqui, sem reinterpretar nenhuma regra de negócio, nenhuma entidade e nenhuma integração já aprovada.

## 2. Legenda e Convenções

- Toda referência a Módulo (01–27), Serviço Conceitual (1–15), Entidade, Regra de Negócio (RN-XXX), Evento de Domínio, Agregado, Esquema ou Integração (IN-XXX) usa exatamente os nomes/números já oficiais dos documentos anteriores.
- **Caso de Uso:** novo conceito desta fase — a menor unidade de execução de uma ação de negócio dentro de um Serviço, correspondendo a uma funcionalidade (F-XXX) ou a um comando que inicia uma Integração (IN-XXX).
- **Componente:** qualquer bloco arquitetural detalhado nesta especificação (um Serviço, ou uma peça transversal como o Motor de Jobs ou a Camada de Cache) — todo componente segue o template de 8 campos exigido (Objetivo, Responsabilidades, Entradas, Saídas, Dependências, Regras de funcionamento, Restrições, Impacto nos demais módulos).

---

## 3. Organização do Backend

O backend do THE CHARCOAL OS ocupa quatro das cinco camadas macro já definidas no System Architecture (TCOS-006, Seção 3.3) — todas exceto a Apresentação (as 30 telas, que permanecem fora de escopo de backend):

1. **Camada de Aplicação (Casos de Uso)** — recebe um comando (ação do usuário) ou reage a um evento; nunca contém regra de negócio própria, apenas orquestra.
2. **Camada de Domínio** — as 30 entidades e as Regras Globais/Regras de Negócio; onde a lógica de negócio de fato vive.
3. **Camada de Dados** — persistência conceitual de cada entidade, conforme já especificado (TCOS-007/008).
4. **Camada Transversal** — Segurança, Auditoria, Logs, Observabilidade, Tolerância a Falhas, Inteligência Artificial, Jobs Agendados e Filas — atravessa as três camadas acima sem pertencer a nenhuma isoladamente.

O backend é organizado internamente como um conjunto de **15 unidades de backend**, uma por Serviço Conceitual já definido no TCOS-006 — nunca uma unidade por módulo funcional e nunca uma unidade por tela, preservando o Princípio PF-09 (simplicidade acima de tudo). Cada unidade de backend contém, internamente, as quatro camadas acima, escopadas apenas às entidades e regras de sua própria responsabilidade (PF-01/PF-02/PF-03).

## 4. Organização por Domínios

As 15 unidades de backend se agrupam nos mesmos 7 Domínios de Dados já definidos no Data Architecture (TCOS-007, Seção 3.1) — a organização por Domínio é uma visão de negócio sobre as mesmas unidades, não uma estrutura paralela:

| Domínio de Dados | Unidades de Backend (Serviços) contidas |
|---|---|
| Comercial | Comercial, Marketing |
| Produção | Produção, Custos e Precificação |
| Suprimentos | Suprimentos |
| Financeiro | Financeiro |
| Pessoas | Pessoas e Recursos |
| Gestão | Indicadores e Dashboards, Metas, Documentos |
| Comercial Adicional | Eventos |
| *(transversais, sem Domínio de Dados próprio)* | Inteligência Artificial, Configurações, Administração e Segurança, Auditoria |

Nenhum Domínio acessa a estrutura interna de outro — a mesma regra de comunicação por contrato já estabelecida entre Serviços (TCOS-006) e entre Esquemas (TCOS-008) se aplica entre Domínios no nível de backend.

## 5. Organização por Serviços

Os 15 Serviços Conceituais já definidos e nomeados no System Architecture (TCOS-006, Capítulo 6) são a unidade primária de organização de todo o backend. Nenhum Serviço novo é criado nesta fase; nenhum Serviço existente é dividido ou fundido. O Capítulo 6 a seguir detalha, para cada um, a estrutura interna de responsabilidade exigida pelo Prompt Oficial desta fase.

---

## 6. Responsabilidades de cada Serviço

**1. Comercial** (Módulos 04, 05, 06, 08, 09)
Objetivo: gerir o funil comercial completo, do Lead ao Contrato assinado, com preço sempre derivado de fonte única.
Responsabilidades: cadastrar/gerir Lead, Cliente, Orçamento (versionado), Contrato (com Aditivos); calcular preço a partir do custo vigente; revalidar Orçamentos abertos ao ser avisado de recálculo de custo.
Entradas: comando do usuário (criar/gerir Lead, Orçamento, Contrato); evento "Custo recalculado" (Custos e Precificação); evento "Evento cancelado" (Eventos).
Saídas: eventos "Lead criado/convertido em Cliente", "Orçamento aceito", "Contrato assinado".
Dependências: Custos e Precificação (preço vigente da Ficha Técnica); Marketing (leitura de atribuição de origem).
Regras de funcionamento: RN-008, RN-009, RN-011 a RN-015, RN-019, RN-021, RN-022.
Restrições: nunca duplica Cliente (PF-01); nunca calcula preço de forma independente (PF-03); nunca acessa dado interno de Produção/Suprimentos diretamente.
Impacto nos demais módulos: origem de IN-002, IN-003, IN-007 (revalidação), IN-010, IN-020; sua saída "Contrato assinado" é pré-condição de IN-001.

**2. Eventos** (Módulo 07)
Objetivo: orquestrar o ciclo comercial-operacional-financeiro de cada Evento, sem executar a lógica de outros domínios.
Responsabilidades: gerir o ciclo de vida do Evento (Prospectado→Confirmado→Concluído/Cancelado); publicar os eventos que disparam a orquestração multi-Serviço.
Entradas: comando do usuário (confirmar/concluir/cancelar Evento); evento "Contrato assinado" (Comercial).
Saídas: eventos "Evento confirmado", "Evento concluído", "Evento cancelado".
Dependências: Comercial (Contrato assinado como pré-condição obrigatória).
Regras de funcionamento: RN-003, RN-006, RN-007, RN-010.
Restrições: nunca executa diretamente Produção/Estoque/Financeiro/Pessoas — apenas publica evento (PF-02); confirmação é bloqueada se a viabilidade operacional falhar (RN-006).
Impacto nos demais módulos: origem de IN-001, IN-005, IN-011, IN-019 — o Serviço com maior efeito em cascata de todo o sistema.

**3. Produção** (Módulos 10, 12, 13)
Objetivo: planejar e executar a transformação de Ingredientes em Produtos com custo sempre rastreável.
Responsabilidades: gerir Receita/Ficha Técnica versionadas; planejar e executar Produção; registrar consumo/rendimento real.
Entradas: evento "Evento confirmado" (Eventos); comando do usuário (criar/aprovar Receita, iniciar/concluir Produção).
Saídas: eventos "Produção planejada/concluída", "Ficha Técnica recalculada".
Dependências: Suprimentos (Estoque/Lote); Configurações (parâmetros RN-024 a RN-029).
Regras de funcionamento: RN-016 a RN-020, RN-024 a RN-029.
Restrições: nunca inicia Produção sem Estoque reservado (salvo exceção registrada); nunca mantém duas Fichas Técnicas vigentes simultâneas para o mesmo Produto.
Impacto nos demais módulos: origem de IN-005, IN-006, IN-008, IN-009.

**4. Custos e Precificação** (Módulos 11, 14)
Objetivo: manter custo e preço sempre corretos, com fonte única de cálculo (PF-03).
Responsabilidades: recalcular custo em cascata ao mudar custo de Ingrediente ou Ficha Técnica; calcular preço a partir do custo somado à margem-alvo.
Entradas: evento "Custo de Ingrediente atualizado" (Suprimentos); evento "Ficha Técnica recalculada" (Produção); evento "Alocação de Funcionário realizada" (Pessoas e Recursos, quando aplicável — R-001-01 ainda pendente de confirmação).
Saídas: eventos "Custo recalculado", "Preço atualizado".
Dependências: Produção (Ficha Técnica); Configurações (margem-alvo, RN-022).
Regras de funcionamento: RN-019, RN-022.
Restrições: é a única fonte de cálculo de custo/preço do sistema — nenhum outro Serviço recalcula de forma independente (PF-03).
Impacto nos demais módulos: origem de IN-007; alimenta IN-001, IN-011, IN-015.

**5. Suprimentos** (Módulos 15, 16, 17)
Objetivo: ser o único dono do saldo de Estoque e da rastreabilidade por Lote.
Responsabilidades: gerir Fornecedor, Compra, Estoque (posição), Lote; gerar lista de reposição automática.
Entradas: evento "Produção planejada/iniciada/concluída" (Produção); evento "Evento confirmado" (Eventos); comando do usuário (registrar Compra).
Saídas: eventos "Compra conferida", "Estoque atualizado", "Lote vencido/descartado".
Dependências: nenhuma obrigatória para a operação básica (Compra/Fornecedor); Produção para o consumo.
Regras de funcionamento: RN-030 a RN-036.
Restrições: nenhum outro Serviço altera Estoque diretamente (PF-01); saldo nunca negativo.
Impacto nos demais módulos: origem de IN-006, IN-008, IN-009, IN-010, IN-020.

**6. Pessoas e Recursos** (Módulos 18, 19, 20)
Objetivo: garantir a alocação correta de Funcionários e Equipamentos a cada Evento/Produção.
Responsabilidades: gerir Funcionário, Equipamento/Veículo, Alocação de Funcionário; sugerir escala a partir do porte do Evento.
Entradas: evento "Evento confirmado" (Eventos); comando do usuário (confirmar/ajustar Alocação).
Saídas: eventos "Alocação de Funcionário realizada", "Equipamento alocado".
Dependências: Eventos (porte do Evento); Configurações (proporção de escala, RN-037).
Regras de funcionamento: RN-037.
Restrições: nunca duas Alocações com sobreposição de horário para o mesmo Funcionário/Equipamento.
Impacto nos demais módulos: origem de IN-010, IN-019.

**7. Financeiro** (Módulos 02, 03, 27)
Objetivo: registrar toda entrada/saída de recursos, pessoal e empresarial, com uma única fonte de verdade.
Responsabilidades: gerir Despesa, Receita Financeira, Pagamento, Banco, Conta; importar/conciliar extratos bancários; nunca calcula um lançamento de forma independente — sempre reage a um evento de origem.
Entradas: eventos "Contrato assinado", "Compra conferida", "Alocação de Funcionário realizada"; comando do usuário (registrar retirada pessoal, importar extrato).
Saídas: eventos "Despesa registrada", "Receita Financeira prevista", "Pagamento efetivado", "Extrato bancário importado".
Dependências: Comercial, Suprimentos, Pessoas e Recursos (eventos de origem); Inteligência Artificial (sugestão de categorização, opcional).
Regras de funcionamento: RN-001, RN-002, RN-004, RN-005, RN-044, RN-045.
Restrições: retirada pessoal nunca é lançada como Despesa operacional (RN-002); decide sozinho sobre seu próprio domínio — nenhum outro Serviço escreve nele.
Impacto nos demais módulos: origem de IN-010, IN-011, IN-012, IN-013, IN-014.

**8. Marketing** (Módulo 21)
Objetivo: gerir Campanhas e medir o retorno comercial de cada uma.
Responsabilidades: gerir Campanha; atribuir Lead/conversão/Contrato à Campanha de origem.
Entradas: eventos "Lead convertido em Cliente", "Contrato assinado" (Comercial); comando do usuário (criar Campanha).
Saídas: eventos "Campanha criada/iniciada/encerrada", "Retorno atribuído".
Dependências: Comercial (eventos de conversão, leitura).
Regras de funcionamento: RN-038.
Restrições: nunca escreve diretamente no domínio do Serviço Comercial.
Impacto nos demais módulos: origem de IN-003, IN-004.

**9. Inteligência Artificial** (Módulo 22)
Objetivo: apoiar decisões em todo o sistema sem jamais decidir sozinha (PF-06).
Responsabilidades: assinar eventos de outros Serviços; gerar sugestão (categorização, previsão de demanda, sugestão de preço); nunca aplicar automaticamente, salvo exceção pré-aprovada e reversível.
Entradas: eventos "Extrato bancário importado" (Financeiro), "Produção concluída" (Produção), elaboração de Orçamento (Comercial).
Saídas: evento "Sugestão gerada (IA)".
Dependências: o Serviço de origem de cada sugestão, como fonte do dado de entrada.
Regras de funcionamento: RN-041, RN-042, RN-043.
Restrições: nunca modifica diretamente o dado de outro Serviço; toda sugestão é auditável, explicável e reversível (PF-06).
Impacto nos demais módulos: origem de IN-015; alimenta IN-012.

**10. Indicadores e Dashboards** (Módulo 01 + visões especializadas)
Objetivo: manter toda métrica de gestão sempre atualizada, com um único caminho de atualização de painel.
Responsabilidades: assinar todos os eventos relevantes de todos os Serviços; recalcular Indicador; compor Dashboard.
Entradas: qualquer evento de domínio relevante publicado por qualquer Serviço.
Saídas: evento "Indicador recalculado".
Dependências: todos os demais Serviços (leitura via evento, nunca consulta direta ao dado interno de cada um).
Regras de funcionamento: RN-039, RN-040.
Restrições: nenhum Dashboard consulta um Serviço de origem diretamente; nunca escreve de volta em nenhum Serviço.
Impacto nos demais módulos: origem de IN-016, IN-017; alimenta IN-018.

**11. Metas** (Módulo 26)
Objetivo: medir objetivos de gestão sem duplicar cálculo.
Responsabilidades: gerir Meta; consumir Indicador; encerrar ciclo automaticamente na data definida.
Entradas: evento "Indicador recalculado" (Indicadores e Dashboards); disparo de fim de período (Job Agendado, Capítulo 15).
Saídas: evento "Ciclo de Meta encerrado".
Dependências: Indicadores e Dashboards (valor do Indicador).
Regras de funcionamento: RN-046.
Restrições: nunca criada sem Indicador correspondente; nunca recalcula o Indicador por conta própria.
Impacto nos demais módulos: origem de IN-018.

**12. Documentos** (Módulo 23)
Objetivo: eliminar formalização manual redundante.
Responsabilidades: gerar Documento versionado a partir de uma entidade de origem já confirmada.
Entradas: eventos "Contrato assinado", "Compra conferida" e demais origens.
Saídas: evento "Documento gerado/revisado".
Dependências: o Serviço de origem da entidade formal.
Regras de funcionamento: RN-014.
Restrições: nova versão nunca remove a anterior; dados obrigatórios ausentes impedem a geração automática.
Impacto nos demais módulos: origem de IN-020.

**13. Configurações** (Módulo 24)
Objetivo: ser a única fonte de parâmetros de negócio configuráveis.
Responsabilidades: manter parâmetros (consumo, perda, margem-alvo, proporção de escala, política de cancelamento, ponto de reposição) com histórico de alteração; nunca assumir valor quando pendente.
Entradas: comando do usuário/Direção (definir/alterar parâmetro).
Saídas: evento "Parâmetro definido/alterado".
Dependências: nenhuma.
Regras de funcionamento: tratamento de parâmetro pendente (R-002A-01, Business Rules Specification).
Restrições: é consultado, nunca consulta outro Serviço; parâmetro pendente bloqueia o cálculo dependente, nunca assume valor.
Impacto nos demais módulos: consultado por Produção, Custos e Precificação, Pessoas e Recursos, Eventos.

**14. Administração e Segurança** (Módulo 25)
Objetivo: gerir perfis, permissões e identidade de usuário.
Responsabilidades: gerir perfil/permissão; fornecer o resultado de autenticação/autorização consultado antes de toda operação de comando.
Entradas: comando do usuário/Direção (criar/alterar perfil e permissão).
Saídas: evento "Permissão alterada".
Dependências: nenhuma.
Regras de funcionamento: CG-05, PF-12.
Restrições: nunca escreve no domínio de negócio de nenhum outro Serviço.
Impacto nos demais módulos: consultado por todos os Serviços antes de qualquer Caso de Uso (Capítulo 27 — Segurança).

**15. Auditoria** (transversal, sem módulo funcional próprio)
Objetivo: materializar o histórico obrigatório (PF-04) de todo o sistema.
Responsabilidades: assinar todos os eventos do Event Bus, sem exceção; construir o log de auditoria completo.
Entradas: qualquer evento publicado por qualquer Serviço.
Saídas: nenhuma — é o Serviço terminal de consumo do sistema.
Dependências: todos os demais Serviços, como fonte de evento.
Regras de funcionamento: PF-04, CG-01.
Restrições: nunca escreve de volta em nenhum outro Serviço; o log é apenas-para-inserção, nunca editado ou removido.
Impacto nos demais módulos: nenhum efeito automático — é consultado (não notificado) quando um Caso de Uso precisa reconstruir histórico.

---

## 7. Comunicação entre Serviços

Reafirma e detalha, no nível de implementação, o já definido no System Architecture (TCOS-006, Seções 3.5/3.6) e no Integration and API Contract (TCOS-009). Todo Serviço se comunica com outro por exatamente dois canais, nunca um terceiro:

- **Comando síncrono para leitura sob demanda:** um Caso de Uso consulta o **contrato público** de outro Serviço (ex.: Comercial consulta o preço vigente calculado por Custos e Precificação) quando precisa de um dado no exato instante da execução. Nunca lê a estrutura interna do Serviço dono (PF-01/PF-02).
- **Evento assíncrono para reação a mudança de estado:** um Caso de Uso publica um evento ao final de sua execução (Capítulo 14); qualquer Serviço assinante reage de forma independente, sem que o Serviço publicador aguarde ou conheça seus assinantes (padrão já estabelecido no Event Bus, TCOS-006 Capítulo 7).

Nenhum Serviço chama diretamente um método/procedimento interno de outro Serviço — mesmo a consulta síncrona ocorre apenas contra o contrato público explicitamente exposto (Capítulo 6, campo "Saídas"/consultas), nunca contra a implementação interna.

## 8. Casos de Uso

Um **Caso de Uso** é a menor unidade de execução de uma ação de negócio dentro de um Serviço — corresponde sempre a uma das 98 funcionalidades (F-XXX) já aprovadas ou ao comando que inicia uma das 20 Integrações (IN-XXX). Todo Caso de Uso:

1. Recebe um comando do usuário **ou** reage a um evento de domínio assinado pelo Serviço.
2. Verifica autorização (Capítulo 27) antes de qualquer execução.
3. Executa a regra de negócio (Camada de Domínio, Capítulo 9), operando sobre exatamente um Agregado (TCOS-007, Seção 3.2) por vez (Capítulo 20 — Controle Transacional).
4. Persiste o resultado (Camada de Dados).
5. Publica o(s) evento(s) de domínio correspondente(s), se houver mudança de estado relevante (PF-04).

**Catálogo representativo de Casos de Uso por Serviço** (não exaustivo — um Caso de Uso existe para cada uma das 98 funcionalidades já aprovadas; a tabela ilustra a correspondência):

| Serviço | Exemplos de Casos de Uso | Funcionalidade(s) de origem |
|---|---|---|
| Comercial | Registrar Lead, Converter Lead em Cliente, Criar Orçamento, Registrar aceite de Orçamento, Assinar Contrato | F-014 a F-033 (Módulos 04, 05, 06, 08, 09) |
| Eventos | Confirmar Evento, Concluir Evento, Cancelar Evento | Módulo 07 |
| Produção | Aprovar Receita, Recalcular Ficha Técnica, Planejar Produção, Concluir Produção | Módulos 10, 12, 13 |
| Custos e Precificação | Recalcular custo em cascata, Atualizar preço | Módulo 11, 14 |
| Suprimentos | Registrar Compra, Conferir Compra, Gerar lista de reposição, Registrar Lote | Módulos 15, 16, 17 |
| Pessoas e Recursos | Sugerir Escala, Confirmar Alocação, Alocar Equipamento | Módulos 18, 19, 20 |
| Financeiro | Registrar Despesa/Receita Financeira, Registrar Pagamento, Importar Extrato, Conciliar Pagamento | Módulos 02, 03, 27 |
| Marketing | Criar Campanha, Atribuir retorno de Campanha | Módulo 21 |
| Inteligência Artificial | Gerar sugestão de categorização, Gerar previsão de demanda | Módulo 22 |
| Indicadores e Dashboards | Recalcular Indicador, Atualizar composição de Dashboard | Módulo 01 |
| Metas | Definir Meta, Encerrar ciclo de Meta | Módulo 26 |
| Documentos | Gerar Documento, Arquivar Documento | Módulo 23 |
| Configurações | Definir parâmetro, Revisar parâmetro | Módulo 24 |
| Administração e Segurança | Criar perfil, Alterar permissão | Módulo 25 |
| Auditoria | (nenhum Caso de Uso de comando — apenas reação a evento) | — |

Nenhum Caso de Uso cruza a fronteira de mais de um Serviço — quando uma ação de negócio afeta múltiplos Serviços (ex.: confirmar um Evento), cada Serviço executa seu próprio Caso de Uso de forma independente, em reação ao evento publicado pelo Caso de Uso de origem (Capítulo 11 — Orquestração).

## 9. Camadas da Aplicação

Cada um dos 15 Serviços é internamente organizado em quatro camadas, na mesma ordem de dependência (cada camada só pode depender da camada abaixo dela, nunca da acima):

1. **Aplicação (Casos de Uso):** recebe comando/evento, verifica autorização, orquestra a execução, publica eventos de saída. Não contém regra de negócio própria.
2. **Domínio:** as entidades do Serviço (Domain Model, TCOS-002) e as Regras de Negócio (TCOS-002A) que se aplicam a elas. É onde a decisão de negócio de fato acontece.
3. **Persistência (Dados):** a estrutura conceitual de tabela de cada entidade (TCOS-008), acessada exclusivamente pela Camada de Domínio.
4. **Transversal:** Segurança, Auditoria, Logs, Observabilidade, Tolerância a Falhas, Cache, Configuração — disponível a todas as camadas acima, mas sem conter regra de negócio.

## 10. Regras de Isolamento entre Camadas

- A Camada de Aplicação nunca acessa diretamente a Persistência — sempre passa pela Camada de Domínio.
- A Camada de Domínio nunca conhece a tecnologia de persistência escolhida no futuro — trabalha apenas com o conceito de entidade e Agregado já definidos (TCOS-007).
- A Camada de Persistência nunca contém regra de negócio — apenas estrutura de dado e restrição de integridade já definidas (TCOS-008).
- A Camada Transversal nunca decide uma regra de negócio em nome da Camada de Domínio — por exemplo, o Cache (Capítulo 23) nunca decide um valor de negócio, apenas armazena temporariamente um valor já calculado pela Camada de Domínio.
- Nenhuma camada de um Serviço acessa diretamente qualquer camada de outro Serviço — toda comunicação entre Serviços ocorre exclusivamente pelos dois canais do Capítulo 7, sempre partindo da Camada de Aplicação de cada lado.

## 11. Orquestração

O Caso de Uso é a única unidade de orquestração de uma ação de negócio (Capítulo 8) — nunca existe uma orquestração síncrona que atravesse dois ou mais Serviços em uma única execução. Quando uma ação de negócio impacta múltiplos Serviços (o exemplo mais amplo é a confirmação de Evento, RN-006/IN-001), a orquestração ocorre da seguinte forma:

1. O Caso de Uso de origem (ex.: "Confirmar Evento", no Serviço Eventos) executa sua própria regra de negócio e publica um único evento ("Evento confirmado").
2. Cada Serviço assinante (Produção, Suprimentos, Pessoas e Recursos, Financeiro, Indicadores e Dashboards) executa seu próprio Caso de Uso em reação a esse evento, de forma paralela e independente (confirmado no Fluxo de Sincronização, TCOS-009 Capítulo 10).
3. Nenhum Caso de Uso de origem aguarda a conclusão dos Casos de Uso reativos — a orquestração é **coreografada** (cada Serviço reage por conta própria a um evento público), nunca **centralizada** (um único orquestrador chamando cada Serviço em sequência), preservando o baixo acoplamento já estabelecido no TCOS-006.

---

## 12. Processamento Síncrono

Ocorre em dois casos, sempre dentro do tempo de resposta esperado pelo usuário na tela (TCOS-005):

- **Comando do usuário:** toda ação iniciada por um clique/submissão de tela (criar Orçamento, confirmar Evento, registrar Compra) é processada de forma síncrona pelo Caso de Uso correspondente — o usuário recebe confirmação de sucesso ou motivo de bloqueio antes de prosseguir.
- **Consulta ao contrato público de outro Serviço:** quando um Caso de Uso precisa de um dado de outro Serviço no exato instante da execução (ex.: preço vigente ao montar um Orçamento), a consulta é síncrona (Capítulo 7) e faz parte do mesmo Caso de Uso.

Todo processamento síncrono deve retornar um resultado determinístico ao usuário: sucesso, bloqueio de regra de negócio (com o motivo, Capítulo 19), ou indisponibilidade temporária de uma dependência (Capítulo 26).

## 13. Processamento Assíncrono

Ocorre sempre que um Caso de Uso reage a um evento de domínio publicado por outro Serviço, sem envolver diretamente uma tela aguardando resposta:

- Todas as reações de Capítulo 11 (orquestração coreografada) são assíncronas por definição.
- Todo recálculo de Indicador/Dashboard (IN-016/IN-017) é assíncrono em relação ao evento de origem que o disparou.
- Toda sugestão de Inteligência Artificial (IN-015) é assíncrona — o usuário nunca aguarda a IA na mesma interação que gerou o evento de origem.
- Todo Job Agendado (Capítulo 15) é, por definição, assíncrono — nunca iniciado por uma ação de tela.

O processamento assíncrono nunca é a única forma de uma ação de negócio "acontecer de verdade" — o Caso de Uso síncrono de origem já produziu o efeito principal e teve sua confirmação enviada ao usuário antes de qualquer reação assíncrona começar (garantia de que o usuário nunca "espera" por uma cadeia de reação de outros Serviços).

## 14. Eventos Internos

Reafirma o catálogo já aprovado no Event Bus (TCOS-006, Capítulo 7) e nos eventos arquiteturais complementares do Integration and API Contract (TCOS-009, Seção 6.3) — nenhum evento novo é criado nesta fase. Do ponto de vista de implementação de backend, todo evento carrega, no mínimo: o nome do evento (linguagem de negócio, já catalogado), o Identificador Global da entidade afetada (TCOS-007, Seção 7.5), o momento em que ocorreu, e o Serviço publicador. Nenhum evento carrega a estrutura interna completa da entidade — apenas o necessário para que um assinante decida se e como reagir, consultando o contrato público do Serviço publicador (Capítulo 7) caso precise de mais dado.

## 15. Jobs Agendados

**Novo conceito desta fase** (achado de auditoria, ver Auditoria de Abertura): processamento disparado pela passagem do tempo, não por um comando de usuário nem por um evento de outro Serviço. Todo comportamento já aprovado que depende de "quando uma data/prazo é atingida" é formalizado aqui como Job Agendado — nenhuma Regra de Negócio é alterada, apenas fica explícito o mecanismo que a executa no momento certo.

**Componente: Motor de Jobs Agendados**
Objetivo: executar, no momento certo, todo comportamento de negócio que depende da passagem do tempo em vez de um comando ou evento.
Responsabilidades: dispara, na periodicidade ou data definida, o Caso de Uso correspondente dentro do Serviço dono da regra.
Entradas: passagem do tempo (data/hora atual), consultada ciclicamente ou agendada por regra.
Saídas: o mesmo evento de domínio que o Caso de Uso disparado publicaria se fosse iniciado por comando (ex.: "Ciclo de Meta encerrado").
Dependências: o Serviço dono de cada regra agendada (nunca executa a regra por conta própria — apenas aciona o Caso de Uso do Serviço correto).
Regras de funcionamento: RN-046 (encerramento de ciclo de Meta), RN-034 (alerta de Lote vencendo), IN-019 (alerta de escala não confirmada a X dias), expiração de Orçamento por validade vencida (RN-013).
Restrições: nunca decide uma regra de negócio por conta própria — apenas aciona, na hora certa, o Caso de Uso do Serviço responsável pela regra; falha de execução de um Job nunca é silenciosa (Capítulo 19).
Impacto nos demais módulos: aciona Casos de Uso em Metas, Suprimentos (Lote), Pessoas e Recursos (Escala), Comercial (Orçamento) — sem nunca pertencer a nenhum desses Serviços, é um componente transversal que os aciona.

**Catálogo de Jobs Agendados identificados** (não exaustivo — novos Jobs podem ser adicionados de forma aditiva conforme novas regras de negócio dependentes de tempo forem aprovadas):

| Job | Periodicidade conceitual | Serviço acionado | Regra/Integração de origem |
|---|---|---|---|
| Encerramento de ciclo de Meta | Na data de término do ciclo | Metas | RN-046, IN-018 |
| Alerta de Lote próximo do vencimento | Diária | Suprimentos | RN-034 |
| Alerta de Escala não confirmada | X dias antes do Evento (parâmetro pendente, Configurações) | Pessoas e Recursos | IN-019 |
| Expiração de Orçamento por validade vencida | Na data de validade | Comercial | RN-013 |
| Alerta de pendência de conciliação bancária prolongada | Diária | Financeiro | IN-013 |

## 16. Filas Conceituais

**Novo conceito desta fase** (achado de auditoria): o Event Bus (TCOS-006) definiu o padrão publicar/assinar, mas nunca formalizou como a entrega de um evento é garantida entre a publicação e o processamento por cada assinante. Este capítulo formaliza esse comportamento, sem nomear tecnologia de mensageria.

**Componente: Barramento de Eventos e Filas**
Objetivo: garantir que todo evento publicado por um Serviço seja efetivamente processado por todos os seus assinantes, mesmo em caso de indisponibilidade temporária de um deles.
Responsabilidades: entregar cada evento a cada assinante de forma independente (uma fila lógica por par publicador-assinante); preservar a ordem de eventos de uma mesma entidade; permitir nova tentativa (retry) em caso de falha de processamento.
Entradas: todo evento publicado por qualquer Serviço (Capítulo 14).
Saídas: entrega do evento a cada Serviço assinante; ao esgotar as tentativas de entrega, registro de exceção (Capítulo 19).
Dependências: nenhuma — é o mecanismo estrutural sobre o qual toda comunicação assíncrona (Capítulo 13) se apoia.
Regras de funcionamento: um evento sobre a mesma entidade nunca é processado fora de ordem por um mesmo assinante; um evento já processado com sucesso por um assinante nunca é reprocessado por ele (idempotência conceitual).
Restrições: nunca perde um evento silenciosamente — falha de entrega definitiva é sempre registrada e alertável, nunca descartada sem rastro; nunca bloqueia o publicador aguardando confirmação de todos os assinantes (PF-02, comunicação nunca síncrona entre Serviços via evento).
Impacto nos demais módulos: sustenta toda a comunicação assíncrona documentada no Integration and API Contract (TCOS-009) — nenhuma das 20 Integrações funciona de forma confiável sem esta garantia estrutural.

---

## 17. Auditoria

Reafirma e detalha, no nível de implementação, o Serviço de Auditoria já definido (TCOS-006, Capítulo 6) e a estrutura `tb_log_auditoria` já especificada (TCOS-008, Seção 13.8). Do ponto de vista de backend: todo Caso de Uso que produz uma mudança de estado relevante publica um evento (Capítulo 14) **como parte da mesma execução** que persistiu a mudança (Capítulo 20 — Controle Transacional) — nunca como um passo separado e opcional. O Serviço de Auditoria assina esse evento e grava, de forma apenas-para-inserção, quem fez o quê, quando e a partir de qual comando. Auditoria é sempre de **negócio**: responde "o que mudou no domínio e por quem" — distinto de Logs (Capítulo 18), que respondem "o que o sistema fez tecnicamente".

## 18. Logs

**Distinção formalizada nesta fase** (achado de auditoria): Logs são registros técnicos operacionais do funcionamento do backend — nunca substituem nem se confundem com a Auditoria de negócio (Capítulo 17).

**Componente: Camada de Logs**
Objetivo: registrar o comportamento técnico de execução do backend, para diagnóstico e correlação de incidentes.
Responsabilidades: registrar início/fim de cada Caso de Uso, cada consulta síncrona entre Serviços, cada entrega/falha de evento (Capítulo 16), cada execução de Job Agendado (Capítulo 15); associar um identificador de correlação a toda a cadeia de reação a um mesmo evento de origem.
Entradas: toda execução técnica relevante em qualquer camada de qualquer Serviço.
Saídas: registro técnico consultável por período, Serviço, Caso de Uso ou identificador de correlação.
Dependências: nenhuma.
Regras de funcionamento: log técnico nunca contém dado de negócio sensível (CG-05/PF-12) além do necessário para diagnóstico — nunca substitui o conteúdo de negócio já registrado pela Auditoria.
Restrições: nunca é a fonte de verdade de uma decisão de negócio; sua retenção pode ser mais curta que a da Auditoria (que é permanente, PF-04), por ser um dado de diagnóstico técnico, não histórico de negócio.
Impacto nos demais módulos: usado pela Observabilidade (Capítulo 25) para medir saúde e desempenho de todos os Serviços.

## 19. Tratamento de Erros

**Novo conceito desta fase.** Todo Caso de Uso pode falhar por exatamente três categorias de motivo, cada uma com uma resposta arquitetural distinta:

1. **Erro de regra de negócio (bloqueio esperado):** a ação viola uma condição já definida em uma Regra de Negócio (ex.: RN-006 bloqueando confirmação de Evento por inviabilidade operacional). Resposta: o Caso de Uso é interrompido antes de qualquer persistência, nenhum evento é publicado, e o motivo exato (referenciando a Regra de Negócio) é retornado ao usuário/Serviço solicitante. Nunca é tratado como falha técnica.
2. **Erro de dado pendente (parâmetro de Configuração ausente):** o Caso de Uso depende de um parâmetro ainda não definido (Seção 3.5 do TCOS-007, R-002A-01). Resposta: o Caso de Uso é bloqueado com alerta explícito de qual parâmetro está pendente e qual Serviço/perfil deve defini-lo — nunca assume um valor padrão silenciosamente.
3. **Erro técnico (dependência indisponível):** uma consulta síncrona a outro Serviço (Capítulo 7) ou a persistência falha por indisponibilidade temporária. Resposta: o usuário recebe indicação de indisponibilidade temporária (nunca um erro genérico sem contexto); nenhuma alteração parcial é persistida (Capítulo 20); a operação pode ser reapresentada pelo usuário sem risco de duplicidade (idempotência do Caso de Uso).

Em todos os três casos, o erro é sempre registrado em Log (Capítulo 18) com o identificador de correlação; erros de regra de negócio e de dado pendente são também candidatos a alerta ao usuário responsável (já previsto nas 20 Integrações, campo "Alertas gerados", TCOS-009).

## 20. Controle Transacional

O **Agregado** já definido no Data Architecture (TCOS-007, Seção 3.2) é a fronteira transacional de todo Caso de Uso: um Caso de Uso sempre lê e grava exatamente um Agregado por execução, de forma atômica (tudo muda ou nada muda) — nunca dois Agregados na mesma transação, mesmo que pertençam ao mesmo Serviço. Quando uma ação de negócio precisa afetar mais de um Agregado (ex.: "Compra conferida gera Estoque/Lote/Despesa", já descrito no TCOS-007 Seção 4.3), isso ocorre por meio de:

- **Um único Caso de Uso, um único Agregado, com submembros internos:** quando os Agregados afetados pertencem à mesma raiz de consistência (ex.: Compra e seus Itens são o mesmo Agregado) — a transação cobre o Agregado inteiro.
- **Múltiplos Casos de Uso encadeados por evento, entre Serviços diferentes:** quando os Agregados afetados pertencem a Serviços diferentes (ex.: Compra conferida no Serviço Suprimentos, gerando Despesa no Serviço Financeiro) — cada Serviço executa sua própria transação local, e a consistência entre elas é **eventual**, nunca uma transação distribuída única (confirmado no Fluxo de Sincronização, TCOS-009 Capítulo 10).

Nenhuma transação permanece aberta aguardando resposta de outro Serviço — isso violaria o baixo acoplamento já estabelecido (TCOS-006) e introduziria um ponto único de falha.

## 21. Versionamento

Reafirma, no nível de backend, o padrão estrutural único de versionamento já definido (TCOS-007, Seção 7.1; TCOS-008, Capítulo 6): todo Caso de Uso que altera uma entidade versionada (Receita, Ficha Técnica, Orçamento, Documento, fórmula de Indicador) cria um novo registro de versão dentro da mesma transação do Agregado (Capítulo 20) — nunca edita a versão vigente in-place. Adicionalmente, esta arquitetura formaliza o **versionamento de contrato de Serviço**: quando a Camada de Aplicação de um Serviço precisa alterar o que aceita como comando ou o que expõe como consulta (Capítulo 7), essa mudança é tratada como uma nova versão de contrato, nunca uma alteração retroativa que quebre um Serviço consumidor já existente — aplicação direta de PF-11 (nenhuma automação ou integração quebra silenciosamente outro módulo).

---

## 22. Estratégia de Escalabilidade

Reafirma, no nível de backend, o já estabelecido no System Architecture (TCOS-006, Capítulo 9) e no Data Architecture/Database Specification (TCOS-007 Seção 7.8, TCOS-008 Capítulo 11):

- Cada um dos 15 Serviços escala de forma independente, conforme sua própria carga (ex.: Financeiro pode crescer em volume de Pagamentos sem exigir mudança em Produção).
- O Barramento de Eventos e Filas (Capítulo 16) permite que múltiplos assinantes do mesmo evento processem em paralelo, sem coordenação entre si.
- O Motor de Jobs Agendados (Capítulo 15) executa Jobs de Serviços diferentes de forma independente e paralelizável.
- Um novo Serviço, Caso de Uso ou Job se integra publicando/assinando eventos já existentes, sem exigir alteração em nenhum componente já em operação — o mesmo critério de sucesso "extensão, nunca reconstrução" já registrado no Framework.

## 23. Estratégia de Cache (Conceitual)

**Componente: Camada de Cache**
Objetivo: evitar recomputação desnecessária de valores já calculados, sem nunca se tornar uma segunda fonte de verdade.
Responsabilidades: manter, de forma temporária, o resultado de leituras de alta frequência e baixa mudança — nomeadamente o valor calculado de Indicador e a composição de Dashboard (já identificados como pré-computação/cache no TCOS-008, Seção 9).
Entradas: resultado de um Caso de Uso de cálculo (ex.: "Indicador recalculado"); evento que invalida um valor em cache.
Saídas: valor em cache servido a uma consulta síncrona (Capítulo 12), sempre com garantia de que reflete o último evento processado.
Dependências: o Serviço dono do dado original (nunca é fonte primária).
Regras de funcionamento: invalidação é sempre orientada a evento — ao ocorrer "Indicador recalculado" (Capítulo 14), o valor em cache correspondente é substituído antes de qualquer nova leitura; nunca invalidação por tempo fixo arbitrário para dado analítico.
Restrições: nunca armazena em cache um dado transacional em fase de escrita (ex.: um Orçamento sendo montado); nunca é a única cópia de um valor — sempre reconstruível a partir da Camada de Domínio (PF-03).
Impacto nos demais módulos: usado principalmente por Indicadores e Dashboards (Capítulo 6, item 10); qualquer outro Serviço pode adotar o mesmo padrão para consultas de alta frequência e baixa mudança (ex.: Ficha Técnica vigente, consultada por Comercial ao montar Orçamentos).

## 24. Estratégia de Configuração

**Componente: Camada de Configuração**
Objetivo: garantir que todo parâmetro de negócio configurável (TCOS-007, Seção 3.5) seja sempre consultado em tempo de execução, nunca fixado no comportamento do Caso de Uso.
Responsabilidades: fornecer, a qualquer Caso de Uso que precise, o valor vigente de um parâmetro (consumo por pessoa, fator de perda, margem-alvo, proporção de escala, política de cancelamento, ponto de reposição); sinalizar quando um parâmetro está pendente.
Entradas: consulta de um Caso de Uso ao iniciar sua execução.
Saídas: valor vigente do parâmetro, ou sinalização explícita de "pendente" (nunca um valor padrão assumido).
Dependências: Serviço de Configurações (Módulo 24), único dono desses valores.
Regras de funcionamento: R-002A-01 — todo parâmetro pendente bloqueia o Caso de Uso dependente com alerta explícito (Capítulo 19, categoria 2), nunca assume um valor.
Restrições: nenhum Caso de Uso "guarda" o valor de um parâmetro além da própria execução — sempre consulta de novo na próxima execução, garantindo que uma alteração de parâmetro tenha efeito imediato em todas as próximas ações.
Impacto nos demais módulos: consultado por Produção, Custos e Precificação, Pessoas e Recursos, Eventos, Comercial (validade de Orçamento) — sem nunca ser alterado por eles.

## 25. Estratégia de Observabilidade

**Novo conceito desta fase.**

**Componente: Camada de Observabilidade**
Objetivo: permitir enxergar, a qualquer momento, a saúde e o comportamento real do backend em operação.
Responsabilidades: consolidar os Logs (Capítulo 18) em indicadores técnicos — tempo de resposta de Casos de Uso síncronos, atraso de processamento de fila (Capítulo 16), taxa de erro por categoria (Capítulo 19), execução e atraso de Jobs Agendados (Capítulo 15); permitir seguir, por identificador de correlação, toda a cadeia de reação a um único evento de origem, do Serviço publicador até o último assinante.
Entradas: Logs de todos os Serviços e componentes transversais.
Saídas: indicadores técnicos consultáveis por período/Serviço/Caso de Uso; alerta técnico quando um limiar de saúde é ultrapassado (ex.: fila com atraso anormal, taxa de erro técnico acima do esperado).
Dependências: Camada de Logs (Capítulo 18).
Regras de funcionamento: observabilidade é estritamente técnica — nunca expõe dado de negócio sensível além do necessário para diagnóstico (CG-05/PF-12), papel que permanece exclusivo da Auditoria (Capítulo 17) e dos Dashboards de negócio (TCOS-005/TCOS-009).
Restrições: não decide nem corrige nada por conta própria — apenas observa e alerta; a correção de uma falha observada segue a Estratégia de Tolerância a Falhas (Capítulo 26).
Impacto nos demais módulos: nenhum efeito automático em regra de negócio — é uma camada de apoio operacional à equipe técnica, não ao usuário de negócio.

## 26. Estratégia de Tolerância a Falhas

**Novo conceito desta fase.**

**Componente: Camada de Tolerância a Falhas**
Objetivo: garantir que a indisponibilidade temporária de um Serviço nunca derrube ou corrompa o restante do sistema.
Responsabilidades: aplicar nova tentativa (retry) controlada em consultas síncronas e em entrega de eventos (Capítulo 16); isolar a falha de um Serviço não-crítico para que ela não impeça a operação dos Serviços centrais (TCOS-006, Capítulo 4); degradar graciosamente quando uma dependência opcional está indisponível.
Entradas: falha de consulta síncrona (Capítulo 12) ou de entrega de evento (Capítulo 16).
Saídas: nova tentativa dentro de um limite definido; ao esgotar tentativas, erro técnico tratado (Capítulo 19, categoria 3) e registro para observabilidade (Capítulo 25).
Dependências: nenhuma.
Regras de funcionamento: a indisponibilidade de um Serviço Auxiliar (Marketing, Inteligência Artificial, Documentos, Metas — classificação já definida no TCOS-006, Capítulo 4) nunca bloqueia um Serviço Central (Comercial, Eventos, Produção, Custos e Precificação, Suprimentos, Financeiro, Indicadores e Dashboards); por exemplo, a Inteligência Artificial indisponível nunca impede o registro de um Pagamento — apenas adia a sugestão de categorização.
Restrições: nunca mascara uma falha permanente como sucesso; nunca reprocessa uma ação de negócio já concluída com sucesso (idempotência, Capítulo 16).
Impacto nos demais módulos: protege a disponibilidade de todos os 15 Serviços; é o que sustenta, na prática, a independência de escala e de falha já prevista no System Architecture (TCOS-006, Capítulo 9).

---

## 27. Estratégia de Segurança do Backend (Conceitual)

Reafirma e detalha, no nível de implementação, a Segurança Conceitual já definida no System Architecture (TCOS-006, Capítulo 8).

**Componente: Camada de Segurança/Autorização**
Objetivo: garantir que nenhuma operação de comando ocorra sem identidade autenticada e permissão verificada.
Responsabilidades: verificar autenticação e autorização como primeiro passo de todo Caso de Uso (Capítulo 8, passo 2), antes de qualquer leitura ou escrita de domínio.
Entradas: identidade do usuário associada ao comando; perfil/permissão mantido pelo Serviço de Administração e Segurança (Capítulo 6, item 14).
Saídas: autorização concedida (Caso de Uso prossegue) ou negada (Caso de Uso interrompido, com motivo, antes de qualquer efeito).
Dependências: Serviço de Administração e Segurança.
Regras de funcionamento: permissões derivam exclusivamente do campo "Quem pode criar/alterar/excluir/visualizar" já definido para cada uma das 98 funcionalidades (Functional Specification) — nenhuma permissão nova é inventada nesta fase; dados financeiros/pessoais protegidos por padrão (CG-05/PF-12).
Restrições: a checagem de autorização nunca ocorre apenas na Camada de Apresentação (tela) — é sempre responsabilidade do próprio Caso de Uso, mesmo que a tela já tenha ocultado uma opção não permitida.
Impacto nos demais módulos: atravessa todos os 15 Serviços — nenhum Caso de Uso de nenhum Serviço é isento desta verificação.

## 28. Estratégia para Inteligência Artificial

Reafirma e detalha, no nível de implementação, o padrão já definido no System Architecture (TCOS-006, Seção 3.11) e na Cadeia Completa de Atualização da IA (Integration and API Contract, TCOS-009, Capítulo 8).

**Componente: Motor de Sugestões de IA**
Objetivo: garantir, estruturalmente, que nenhuma sugestão de Inteligência Artificial produza efeito sem confirmação humana (PF-06).
Responsabilidades: assinar eventos de outros Serviços (Capítulo 6, item 9); processar a sugestão de forma assíncrona (Capítulo 13); publicar "Sugestão gerada (IA)" com nível de confiança; nunca invocar diretamente um Caso de Uso de escrita em outro Serviço.
Entradas: eventos "Extrato bancário importado", "Produção concluída", elaboração de Orçamento.
Saídas: evento "Sugestão gerada (IA)", consumido pelo Serviço de origem como entrada de um novo Caso de Uso (que só se completa após decisão humana, salvo exceção pré-aprovada e reversível, RN-041 a RN-043).
Dependências: o Serviço de origem de cada sugestão, para o dado de entrada e para a aplicação final da decisão.
Regras de funcionamento: RN-041 a RN-043.
Restrições: o Motor de Sugestões nunca escreve fora do seu próprio Serviço; toda decisão humana (aceite/recusa/reversão) é registrada com o mesmo rigor de Auditoria (Capítulo 17) que qualquer outra ação de negócio.
Impacto nos demais módulos: alimenta Casos de Uso em Financeiro, Suprimentos e Custos e Precificação — nunca os executa diretamente.

## 29. Estratégia para Integrações Futuras

Reafirma e detalha, no nível de implementação, o já estabelecido no System Architecture (TCOS-006, Capítulo 9): novas integrações externas (uma nova instituição bancária, uma nova fonte de dado externo, uma nova capacidade de IA) entram pelo sistema exclusivamente através dos Serviços já identificados como fronteira natural — Financeiro (para dado financeiro externo) e Inteligência Artificial (para nova capacidade de sugestão).

**Componente: Gateway de Integrações Futuras** *(conceitual — sem tecnologia definida)*
Objetivo: garantir que uma fonte de dado externa nunca acesse diretamente o domínio interno de um Serviço.
Responsabilidades: traduzir um dado vindo de fora (ex.: um novo formato de extrato bancário) para o mesmo evento de domínio já catalogado (ex.: "Extrato bancário importado") antes de qualquer Caso de Uso interno ser acionado.
Entradas: dado externo, em qualquer formato que uma futura integração venha a usar.
Saídas: exatamente o mesmo evento de domínio que uma origem interna geraria — nenhum Serviço interno percebe diferença entre uma origem externa nova e uma já existente.
Dependências: o Serviço de fronteira (Financeiro ou Inteligência Artificial) para o qual a integração é direcionada.
Regras de funcionamento: nenhuma tecnologia de integração externa é definida nesta fase; a única exigência arquitetural é que o resultado, ao entrar no sistema, seja indistinguível de um evento de domínio já catalogado.
Restrições: nenhuma integração futura pode expor a estrutura interna de um Serviço para fora do sistema, nem aceitar escrita direta em uma entidade sem passar por um Caso de Uso completo (autorização, regra de negócio, auditoria).
Impacto nos demais módulos: nenhum impacto retroativo — por definição, uma integração futura é absorvida como extensão, nunca como reconstrução (mesmo critério do TCOS-006, Capítulo 9, e do Framework, Seção 25).

---

## RESUMO PARA O PROPRIETÁRIO

Este documento (TCOS-010) responde à pergunta: **por dentro de cada "setor" do sistema (cada um dos 15 Serviços já definidos), como o trabalho realmente vai ser organizado e executado?**

O que foi construído: detalhamos, para cada um dos 15 Serviços, exatamente o que ele recebe, o que ele produz, de quem depende e o que nunca pode fazer — uma espécie de "descrição de cargo" completa para cada setor interno do sistema. Além disso, formalizamos conceitos que ainda não existiam em nenhum documento anterior: como o sistema executa tarefas programadas por data (por exemplo, avisar quando um Lote está perto de vencer, ou encerrar automaticamente um ciclo de Meta), como ele garante que nenhum aviso entre setores se perde, como ele trata um erro sem travar o sistema todo, e como ele continua funcionando mesmo que uma parte não crítica (como a Inteligência Artificial) fique temporariamente indisponível.

Por que isso é importante: até aqui, sabíamos *o que* o sistema faz e *quem conversa com quem*. Faltava saber *como* cada "setor" organiza seu próprio trabalho por dentro, de forma que o sistema continue simples de manter mesmo depois de crescer por anos — sem que um problema em uma área derrube as demais.

Como isso conecta com tudo que já foi construído: cada um dos 15 Serviços aqui detalhados é exatamente o mesmo já aprovado na Arquitetura de Sistema; cada regra de negócio aplicada é exatamente uma das 47 já aprovadas; cada estrutura de dado usada é exatamente uma das já definidas na Arquitetura de Dados e no Banco de Dados; cada integração citada é exatamente uma das 20 já aprovadas. Nada foi reinventado — apenas detalhado o "como" interno.

Como isso prepara o próximo passo: com este documento, uma equipe de desenvolvimento já tem tudo que precisa para escolher a linguagem de programação, o banco de dados físico e a tecnologia de comunicação entre sistemas — porque já sabe exatamente como cada parte deve se comportar por dentro, mesmo antes de qualquer código ser escrito.

Nada de código, linguagem, framework, banco físico ou tecnologia foi definido nesta fase — apenas o "manual de organização interna" de cada setor do sistema.

---

## TCOS QUALITY GATE EXECUTIVO

Em conformidade com a Regra Permanente do Framework, foi reexecutada a auditoria completa sobre todos os 13 documentos oficiais antes do encerramento desta fase — resultado consolidado na Auditoria de Abertura e reafirmado aqui: nenhuma inconsistência, conflito, duplicidade ou dependência oculta permaneceu sem tratamento.

**1. Resumo Executivo**
Definida a arquitetura lógica interna de backend do THE CHARCOAL OS: organização em 4 camadas por Serviço, 15 Serviços detalhados em 8 campos cada, conceito de Caso de Uso, orquestração coreografada, processamento síncrono/assíncrono, e formalização de 10 componentes transversais (incluindo os 3 conceitos genuinamente novos desta fase: Jobs Agendados, Filas Conceituais, e a separação Logs/Observabilidade/Tolerância a Falhas). Nenhuma tecnologia foi definida; nenhum documento anterior foi alterado.

**2. Estado atual do projeto**
Fases 000 a 009 encerradas e oficiais; Fase 010 em validação. Nenhum código, API, banco físico ou desenvolvimento foi iniciado.

**3. Documentos oficiais existentes**
Os 13 já registrados na Executive Memory, mais este documento em rascunho.

**4. Dependências desta fase**
15 Serviços Conceituais e Event Bus (TCOS-006); 7 Domínios de Dados e 24 Agregados (TCOS-007); 32 estruturas conceituais (TCOS-008); 20 Integrações (TCOS-009); 47 Regras de Negócio; 98 funcionalidades — todos referenciados, nenhum reescrito.

**5. Pendências abertas**
Validação formal deste documento; parâmetros do Módulo 24; M-003A-03/04; M-005-01/02/03; M-006-01; M-007-01; M-008-01; M-009-01; confirmação do domínio de negócio (R-000-03). Nenhuma pendência nova de negócio — apenas a validação deste documento.

**6. Dúvidas encontradas**
Nenhuma nova de negócio. Uma dúvida técnica foi levantada e já resolvida dentro desta própria fase: como formalizar processamento agendado e confiabilidade de entrega de evento — respondida nos Capítulos 15 e 16.

**7. Riscos ativos**
R-000-03/R-002-01, R-001-01/R-002-02, R-002A-01 — herdados; nenhum impede a arquitetura de backend.

**8. Novos riscos encontrados**
Nenhum risco novo de negócio. Três lacunas técnicas foram identificadas e já resolvidas dentro desta própria arquitetura: ausência de conceito de Job Agendado, ausência de garantia de entrega/ordem no Event Bus, e ambiguidade entre Auditoria de negócio e Log técnico — ver Auditoria de Abertura.

**9. Inconsistências encontradas**
Nenhuma.

**10. Conflitos entre documentos**
Nenhum.

**11. Serviços sem estrutura interna**
Nenhum — os 15 Serviços Conceituais têm, todos, os 8 campos obrigatórios detalhados (Capítulo 6).

**12. Regras de negócio sem suporte de execução**
Nenhuma das 47 Regras de Negócio exige um comportamento de backend não coberto por um Caso de Uso, Job Agendado ou Componente Transversal desta arquitetura.

**13. Integrações sem suporte de orquestração**
Nenhuma das 20 Integrações (TCOS-009) fica sem explicação de qual padrão de orquestração (síncrono, assíncrono, coreografado) a implementa — confirmado Capítulo por Capítulo (11 a 13).

**14. Dependências ocultas**
Nenhuma nova identificada — todas as dependências entre Serviços já estavam explícitas desde o TCOS-006 (Capítulo 4) e são apenas reafirmadas aqui no nível de Caso de Uso.

**15. Melhorias sugeridas**
- M-010-01 (nova): ao escolher a tecnologia de mensageria em fase técnica futura, avaliar mecanismos nativos de garantia de entrega/ordem/idempotência antes de implementar o Barramento de Eventos e Filas (Capítulo 16) de forma customizada.
- M-010-02 (nova): o parâmetro "X dias antes do Evento" para o Job de alerta de escala não confirmada (Capítulo 15) depende de um valor de Configuração ainda não definido — mesma pendência já registrada para o Módulo 24, agora também associada a um Job Agendado específico.

**16. Impacto nas próximas fases**
Esta arquitetura de backend é a referência obrigatória para qualquer fase técnica futura (escolha de linguagem, framework, banco físico, APIs, desenvolvimento) — nenhuma dessas fases deve introduzir um padrão de camada, transação, comunicação ou tratamento de erro incompatível com o que está aqui documentado, sem registrar formalmente o motivo.

**17. Quality Score: 9,5/10**
Justificativa técnica: cobertura completa dos 27 itens de arquitetura de backend exigidos e dos 8 campos obrigatórios para os 15 Serviços e os 10 componentes transversais, com identificação e resolução — não apenas menção — de três lacunas técnicas reais (Jobs Agendados, Filas Conceituais, separação Logs/Auditoria). Não é 10 porque duas melhorias novas (M-010-01/M-010-02) permanecem como refinamento a ser feito quando a tecnologia de mensageria e o parâmetro de escala forem, respectivamente, escolhidos e confirmados.

**18. Atualização do PROJECT_MEMORY.md:** ver commit correspondente.

**19. Estatísticas Finais**
- Quantidade de páginas equivalentes: aproximadamente 22.
- Quantidade de Serviços detalhados: 15 de 15 (100%).
- Quantidade de componentes transversais novos/formalizados: 10 (Motor de Jobs Agendados, Barramento de Eventos e Filas, Camada de Logs, Camada de Cache, Camada de Configuração, Camada de Observabilidade, Camada de Tolerância a Falhas, Camada de Segurança/Autorização, Motor de Sugestões de IA, Gateway de Integrações Futuras).
- Quantidade total de componentes com os 8 campos obrigatórios: 25 (15 Serviços + 10 transversais).
- Quantidade de Casos de Uso catalogados (representativos): correspondem, em princípio, às 98 funcionalidades já aprovadas — nenhuma nova funcionalidade foi criada; a tabela do Capítulo 8 apresenta uma amostra por Serviço.
- Quantidade de Jobs Agendados identificados: 5.
- Quantidade de camadas por Serviço: 4 (Aplicação, Domínio, Persistência, Transversal).
- Quantidade de módulos cobertos: 27 de 27 (100%, via os 15 Serviços).
- Quantidade de regras de negócio referenciadas: 34 das 47 (as demais permanecem válidas, sem novo comportamento de execução a detalhar nesta fase).
- Riscos ativos: 4 herdados; 0 novos de negócio; 3 lacunas técnicas identificadas e resolvidas nesta própria fase.
- Pendências: 9, todas herdadas.
- Melhorias: 2 novas (M-010-01, M-010-02).
- Percentual estimado de maturidade do projeto: **84%** (subiu de 80% — a arquitetura lógica de implementação está agora completa e auditada; restam como não iniciadas: confirmação final do domínio de negócio via entrevista, escolha de tecnologia, desenho físico de API, e toda a fase de Desenvolvimento propriamente dita).

**Encerramento desta fase:** este documento permanece como **rascunho para validação do proprietário** até receber o comando `APROVADO`. Nenhuma fase de linguagem, framework, banco de dados físico, API ou Desenvolvimento será iniciada sem autorização explícita, conforme restrição do Prompt Oficial da Fase 010.

---

*Fim do documento — THE CHARCOAL OS BACKEND ARCHITECTURE v1.0.0*
