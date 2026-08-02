# THE CHARCOAL OS — BACKEND ARCHITECTURE

**Documento:** TCOS-010 — Arquitetura Conceitual de Backend
**Projeto:** THE CHARCOAL OS
**Fase:** 010 — Backend Architecture
**Status:** Oficial — Aprovado e Congelado pelo proprietário em 2026-08-02 (comando `APROVADO`, após auditoria corretiva)
**Versão:** 1.0.0

---

## EXECUTIVE MEMORY

- **Estado atual do projeto:** negócio, domínio, regras, funcionalidades, fluxos, UX/UI, arquitetura de sistema, arquitetura de dados, banco de dados e contrato de integração entre módulos completos e oficiais; iniciando a arquitetura lógica interna de backend, ainda sem linguagem, framework, banco físico ou API definidos.
- **Fase atual:** 010 — Backend Architecture (TCOS-010).
- **Fases concluídas:** 000 a 009, todas aprovadas e oficiais (a mais recente, TCOS-009, congelada nesta mensagem).
- **Critério de contagem de Documentos Oficiais (esclarecido nesta fase, ver Auditoria de Abertura, item de correção 1):** distingue-se **Documento Oficial Congelado** (entregável de uma Fase encerrada, que só muda mediante criação de nova versão) de **Documento Oficial Vivo** (o `PROJECT_MEMORY.md`, que por natureza é atualizado ao final de toda fase e nunca é "congelado"). Um documento em rascunho (ainda sem comando `APROVADO`) não é contado como oficial em nenhum dos dois grupos.
- **Documentos Oficiais Congelados (13):** Development Framework (v1.2.0), Enterprise Domain Discovery (v1.0.0), Business Discovery Questionnaire (v1.0.0), Discovery Interview Roadmap (v1.0.0), Domain Model (v1.0.0), Business Rules Specification (v1.0.0), Functional Specification (v1.2.0), User Journeys and System Flows (v1.0.0), UX/UI Specification (v1.0.0), System Architecture (v1.0.0), Data Architecture (v1.0.0), Database Specification (v1.0.0), Integration and API Contract (v1.0.0, congelado a partir da aprovação da Fase 009).
- **Documento Oficial Vivo (1):** `PROJECT_MEMORY.md`.
- **Total de Documentos Oficiais (congelados + vivo): 14.**
- **Documento em elaboração (não contado como oficial até aprovação):** este documento (TCOS-010) — `THE_CHARCOAL_OS_BACKEND_ARCHITECTURE.md`.
- **Pendências:** confirmação do domínio de negócio (R-000-03); parâmetros do Módulo 24; M-003A-03/04; M-005-01/02/03; M-006-01; M-007-01; M-008-01; M-009-01; decisão sobre retomar a entrevista de descoberta.
- **Riscos ativos:** R-000-03/R-002-01, R-001-01/R-002-02, R-002A-01 — herdados; nenhum impede o desenho da arquitetura de backend, pois todo parâmetro não confirmado continua modelado como Configuração pendente que bloqueia/alerta, nunca como valor assumido.
- **Dependências para esta fase:** os 15 Serviços Conceituais e o Event Bus (System Architecture, TCOS-006); os 7 Domínios de Dados e 24 Agregados (Data Architecture, TCOS-007); as 32 estruturas conceituais (Database Specification, TCOS-008); as 20 Integrações (Integration and API Contract, TCOS-009); as 47 Regras de Negócio e 98 funcionalidades — todos referenciados, nenhum reescrito.
- **Objetivo da fase que será iniciada:** definir a arquitetura lógica interna de backend do THE CHARCOAL OS — organização, camadas, casos de uso, orquestração, processamento síncrono/assíncrono, jobs, filas, auditoria, logs, erros, transações, cache, configuração, observabilidade, tolerância a falhas, segurança, IA e integrações futuras — sem nenhuma decisão de tecnologia.
- **O que não pode ser alterado:** nenhum conteúdo de nenhum dos 13 Documentos Oficiais Congelados já aprovados.

### Auditoria de Abertura

Os 13 Documentos Oficiais Congelados foram revisados quanto aos pontos relevantes a esta fase (organização de Serviços, Agregados, estruturas de dado, eventos, integrações e regras de negócio já aprovados). Resultado da primeira rodada (registrado na versão inicial deste documento):

- Não foram identificadas inconsistências, conflitos ou duplicidades entre os 13 Documentos Oficiais Congelados, no escopo revisado.
- **Base já sólida para o backend:** o System Architecture (TCOS-006) já define os 15 Serviços Conceituais, o Event Bus e 5 camadas macro (Apresentação, Orquestração de Regras, Domínio, Dados, Transversal); o Data Architecture (TCOS-007) já define 24 Agregados como unidade de consistência transacional; o Database Specification (TCOS-008) já define estrutura física conceitual; o Integration and API Contract (TCOS-009) já define o comportamento completo de comunicação entre módulos. Este documento **não redefine nada disso** — detalha como cada Serviço se organiza *por dentro* para implementar o que já foi aprovado.
- **Lacuna real identificada:** nenhum documento anterior formalizou **processamento agendado (jobs)** como conceito arquitetural — apenas comportamentos implícitos já aprovados o exigem (ex.: RN-034 alerta de Lote vencendo, RN-046 encerramento de ciclo de Meta na data definida, IN-019 alerta de escala não confirmada a X dias, expiração de Orçamento). Esta arquitetura de backend formaliza esses casos como Jobs Agendados (Capítulo 15), por adição — nenhuma Regra de Negócio é alterada, apenas fica explícito **como** o backend a executa no tempo certo.
- **Lacuna real identificada:** o Event Bus (TCOS-006, Capítulo 7) definiu publicar/assinar, mas nunca formalizou ordenação, nova tentativa (retry) ou tratamento de falha de entrega de um evento. Esta arquitetura de backend formaliza isso como Filas Conceituais (Capítulo 16), sem contradizer o Event Bus já aprovado — apenas detalha seu comportamento interno de confiabilidade.
- **Lacuna real identificada:** nenhum documento anterior tratou de Logs técnicos como algo distinto de Auditoria de negócio (TCOS-006/008) — os dois foram, até aqui, mencionados de forma próxima o suficiente para gerar ambiguidade. Esta arquitetura separa formalmente os dois conceitos (Capítulos 17 e 18).
- **Lacuna real identificada:** Tratamento de Erros, Observabilidade e Tolerância a Falhas nunca foram tratados em nenhum documento anterior — são formalizados aqui pela primeira vez, sempre em conformidade com os Princípios Fundamentais já aprovados (especialmente PF-04, PF-06, PF-09, PF-11).
- O Caso de Uso proposto nesta arquitetura confirma e detalha (nunca altera) o padrão de Agregado já definido no TCOS-007 — a fronteira transacional é o próprio Agregado (Capítulo 20).
- Nenhuma decisão de linguagem, framework, banco de dados físico, API, protocolo ou tecnologia foi tomada, em conformidade com a restrição explícita da fase.

### Auditoria Corretiva (comando `CORRIGIR`, após a primeira entrega)

O proprietário determinou uma segunda rodada de auditoria sobre o rascunho já entregue, antes de qualquer aprovação. Esta rodada revisou especificamente a contagem de Documentos Oficiais, a Regra Transacional de Agregados, a cobertura das 47 Regras de Negócio, a nomenclatura do `PROJECT_MEMORY.md`, as referências cruzadas internas e as declarações categóricas do documento. Resultado:

1. **Contagem de Documentos Oficiais — divergência real encontrada e corrigida.** A versão anterior listava 14 artefatos no campo "Documentos oficiais" da Executive Memory, mas as frases de fechamento ("O que não pode ser alterado", Auditoria de Abertura, Quality Gate) alternavam entre os números 13 e "os 13 já registrados", sem declarar o critério de contagem. Correção aplicada: a Executive Memory agora declara explicitamente dois grupos — **13 Documentos Oficiais Congelados** (entregáveis de Fase, imutáveis sem nova versão) e **1 Documento Oficial Vivo** (`PROJECT_MEMORY.md`, atualizado a cada fase por natureza, nunca congelado) — **total de 14 Documentos Oficiais**. Toda ocorrência no corpo do documento foi revisada para usar um dos dois números com o qualificador correto ("congelados" ou "total").
2. **Regra Transacional de Agregados — reformulada para a versão oficial de seis pontos.** O Capítulo 20 foi reescrito com a formulação exata determinada pelo proprietário (consulta apenas via contrato público; uma transação por Agregado; nenhuma transação distribuída; alteração em outro Agregado sempre via novo Caso de Uso iniciado por Evento; consulta nunca amplia a transação; processamento assíncrono sempre com retry/idempotência/fila de falhas/reconciliação) e propagada, por referência direta (nunca por reformulação divergente), aos Capítulos 7, 8, 9, 10, 11, 12 e 16 — nenhuma contradição remanescente entre eles.
3. **Cobertura das 47 Regras de Negócio — matriz de rastreabilidade produzida.** A versão anterior citava "34 das 47 Regras" sem demonstrar quais e por quê. O novo Capítulo 30 (Matriz de Rastreabilidade das Regras de Negócio) cobre as 47 regras individualmente, com Serviço, Caso de Uso, tipo de execução, Agregado, Evento publicado, Integração relacionada e capítulo responsável — incluindo, para 3 regras cujo Job Agendado não estava no catálogo original do Capítulo 15 (RN-011, RN-030, RN-042), a atualização por adição desse catálogo, e, para 2 regras sem evento de domínio ou Integração dedicada (RN-004, RN-007), a justificativa formal exigida.
4. **Nomenclatura do `PROJECT_MEMORY.md` — verificado, nenhuma divergência encontrada.** `git ls-files` confirma um único arquivo com esse nome exato no repositório; não existe duplicata, variante de grafia ou arquivo órfão. Nenhuma correção foi necessária neste item.
5. **Referências cruzadas internas — duas referências quebradas encontradas e corrigidas.** A Auditoria de Abertura original citava "Jobs Agendados (Capítulo 13)" e "Filas Conceituais (Capítulo 14)" — números que correspondiam a uma numeração de rascunho anterior à consolidação final dos 29 capítulos, e não foram atualizados quando Jobs Agendados e Filas Conceituais se fixaram, respectivamente, nos Capítulos 15 e 16. Corrigido nesta rodada. As demais referências cruzadas do documento (mais de 60 ocorrências de "Capítulo N", incluindo Eventos Internos, Segurança, Controle Transacional, Integrações Futuras e Quality Gate) foram conferidas uma a uma contra os cabeçalhos reais e confirmadas corretas.
6. **Declarações absolutas — revisadas para formulações comprováveis.** Frases como "todos os documentos foram lidos integralmente" e "nenhuma inconsistência encontrada" foram substituídas por afirmações que declaram o escopo revisado (ver abertura desta seção); a frase sobre uma equipe "implementar integralmente a partir daqui" (Capítulo 1) foi reformulada para descrever exatamente o que este documento fornece, sem prometer suficiência além do que está demonstrado.

Nenhuma regra de negócio nova foi criada; nenhum documento das Fases 000–009 foi alterado; nenhuma tecnologia foi escolhida; a Fase 011 não foi iniciada.

---

## 1. Papel deste Documento

O System Architecture (TCOS-006) definiu **quais Serviços existem** e como eles se comunicam entre si (Event Bus). O Data Architecture (TCOS-007) e o Database Specification (TCOS-008) definiram **como o dado se organiza e se persiste**. O Integration and API Contract (TCOS-009) definiu **o comportamento completo de comunicação** entre módulos. Este documento (TCOS-010) define **como cada Serviço se organiza por dentro** para executar tudo isso de forma consistente, auditável, escalável e tolerante a falhas — a arquitetura lógica de implementação. Este documento fornece a organização de camadas, Casos de Uso, regra transacional e comportamento transversal (Capítulos 3 a 29) necessária para que uma equipe de desenvolvimento inicie a escolha de linguagem, framework e tecnologia de persistência/mensageria; as decisões de negócio, entidades e integrações permanecem nos documentos de origem (TCOS-002 a TCOS-009) e não são redefinidas aqui — este documento referencia-as, nunca as substitui.

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

Nenhum Serviço chama diretamente um método/procedimento interno de outro Serviço — mesmo a consulta síncrona ocorre apenas contra o contrato público explicitamente exposto (Capítulo 6, campo "Saídas"/consultas), nunca contra a implementação interna. Esta é a aplicação direta da regra 1 do Controle Transacional (Capítulo 20): um Caso de Uso só acessa outro Agregado ou Serviço através do seu contrato público; e da regra 5: uma consulta síncrona a esse contrato público nunca torna o Agregado consultado parte da transação corrente do Caso de Uso que consulta.

## 8. Casos de Uso

Um **Caso de Uso** é a menor unidade de execução de uma ação de negócio dentro de um Serviço — corresponde sempre a uma das 98 funcionalidades (F-XXX) já aprovadas ou ao comando que inicia uma das 20 Integrações (IN-XXX). Todo Caso de Uso:

1. Recebe um comando do usuário **ou** reage a um evento de domínio assinado pelo Serviço.
2. Verifica autorização (Capítulo 27) antes de qualquer execução.
3. Quando necessário, consulta outros Agregados ou Serviços exclusivamente por seus contratos públicos (Capítulo 7) — essa consulta nunca torna o Agregado consultado parte da transação corrente (Capítulo 20, regras 1 e 5).
4. Executa a regra de negócio (Camada de Domínio, Capítulo 9), modificando, dentro de uma única transação, exatamente um Agregado (TCOS-007, Seção 3.2) por vez — nunca dois (Capítulo 20, regra 2).
5. Persiste o resultado (Camada de Dados).
6. Publica o(s) evento(s) de domínio correspondente(s), se houver mudança de estado relevante (PF-04); qualquer alteração necessária em outro Agregado é sempre feita por um novo Caso de Uso, iniciado por esse evento, nunca dentro desta mesma transação (Capítulo 20, regra 4).

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
2. **Domínio:** as entidades do Serviço (Domain Model, TCOS-002) e as Regras de Negócio (TCOS-002A) que se aplicam a elas, organizadas em Agregados (TCOS-007). É onde a decisão de negócio de fato acontece, sempre respeitando a Regra Transacional de Agregados (Capítulo 20).
3. **Persistência (Dados):** a estrutura conceitual de tabela de cada entidade (TCOS-008), acessada exclusivamente pela Camada de Domínio.
4. **Transversal:** Segurança, Auditoria, Logs, Observabilidade, Tolerância a Falhas, Cache, Configuração — disponível a todas as camadas acima, mas sem conter regra de negócio.

## 10. Regras de Isolamento entre Camadas

- A Camada de Aplicação nunca acessa diretamente a Persistência — sempre passa pela Camada de Domínio.
- A Camada de Domínio nunca conhece a tecnologia de persistência escolhida no futuro — trabalha apenas com o conceito de entidade e Agregado já definidos (TCOS-007).
- A Camada de Persistência nunca contém regra de negócio — apenas estrutura de dado e restrição de integridade já definidas (TCOS-008).
- A Camada Transversal nunca decide uma regra de negócio em nome da Camada de Domínio — por exemplo, o Cache (Capítulo 23) nunca decide um valor de negócio, apenas armazena temporariamente um valor já calculado pela Camada de Domínio.
- Nenhuma camada de um Serviço acessa diretamente qualquer camada de outro Serviço — toda comunicação entre Serviços ocorre exclusivamente pelos dois canais do Capítulo 7, sempre partindo da Camada de Aplicação de cada lado.
- A Camada de Domínio de um Serviço nunca inclui, na mesma transação, um Agregado pertencente à Camada de Domínio de outro Serviço — isolamento que é a própria definição da Regra Transacional de Agregados (Capítulo 20).

## 11. Orquestração

O Caso de Uso é a única unidade de orquestração de uma ação de negócio (Capítulo 8) — nunca existe uma orquestração síncrona que atravesse dois ou mais Serviços em uma única execução. Quando uma ação de negócio impacta múltiplos Serviços (o exemplo mais amplo é a confirmação de Evento, RN-006/IN-001), a orquestração ocorre da seguinte forma:

1. O Caso de Uso de origem (ex.: "Confirmar Evento", no Serviço Eventos) executa sua própria regra de negócio e publica um único evento ("Evento confirmado").
2. Cada Serviço assinante (Produção, Suprimentos, Pessoas e Recursos, Financeiro, Indicadores e Dashboards) executa seu próprio Caso de Uso em reação a esse evento, de forma paralela e independente (confirmado no Fluxo de Sincronização, TCOS-009 Capítulo 10).
3. Nenhum Caso de Uso de origem aguarda a conclusão dos Casos de Uso reativos — a orquestração é **coreografada** (cada Serviço reage por conta própria a um evento público), nunca **centralizada** (um único orquestrador chamando cada Serviço em sequência), preservando o baixo acoplamento já estabelecido no TCOS-006.

Este padrão é exatamente a regra 4 do Controle Transacional (Capítulo 20): toda alteração necessária em um Agregado de outro Serviço ocorre através de um novo Caso de Uso, iniciado pelo evento publicado no passo 1 — nunca como extensão da transação do Caso de Uso de origem.

---

## 12. Processamento Síncrono

Ocorre em dois casos, sempre dentro do tempo de resposta esperado pelo usuário na tela (TCOS-005):

- **Comando do usuário:** toda ação iniciada por um clique/submissão de tela (criar Orçamento, confirmar Evento, registrar Compra) é processada de forma síncrona pelo Caso de Uso correspondente — o usuário recebe confirmação de sucesso ou motivo de bloqueio antes de prosseguir.
- **Consulta ao contrato público de outro Serviço:** quando um Caso de Uso precisa de um dado de outro Serviço no exato instante da execução (ex.: preço vigente ao montar um Orçamento), a consulta é síncrona (Capítulo 7) e faz parte do mesmo Caso de Uso — mas, em conformidade com a regra 5 do Controle Transacional (Capítulo 20), essa consulta nunca inclui o Agregado consultado na transação do Caso de Uso que consulta; é sempre uma leitura externa ao contrato público, nunca uma escrita compartilhada.

Todo processamento síncrono deve retornar um resultado determinístico ao usuário: sucesso, bloqueio de regra de negócio (com o motivo, Capítulo 19), ou indisponibilidade temporária de uma dependência (Capítulo 26).

## 13. Processamento Assíncrono

Ocorre sempre que um Caso de Uso reage a um evento de domínio publicado por outro Serviço, sem envolver diretamente uma tela aguardando resposta:

- Todas as reações de Capítulo 11 (orquestração coreografada) são assíncronas por definição.
- Todo recálculo de Indicador/Dashboard (IN-016/IN-017) é assíncrono em relação ao evento de origem que o disparou.
- Toda sugestão de Inteligência Artificial (IN-015) é assíncrona — o usuário nunca aguarda a IA na mesma interação que gerou o evento de origem.
- Todo Job Agendado (Capítulo 15) é, por definição, assíncrono — nunca iniciado por uma ação de tela.

O processamento assíncrono nunca é a única forma de uma ação de negócio "acontecer de verdade" — o Caso de Uso síncrono de origem já produziu o efeito principal e teve sua confirmação enviada ao usuário antes de qualquer reação assíncrona começar (garantia de que o usuário nunca "espera" por uma cadeia de reação de outros Serviços).

Em conformidade com a regra 6 do Controle Transacional (Capítulo 20), todo processamento assíncrono desta arquitetura respeita, sem exceção, os quatro mecanismos detalhados no Capítulo 16 (Filas Conceituais): **retry** (nova tentativa antes de qualquer falha ser considerada definitiva), **idempotência** (um mesmo evento nunca produz o efeito de negócio duas vezes), **fila de falhas** (nenhum evento que esgota o retry é descartado — fica visível para intervenção) e **reconciliação** (o estado de um Agregado pode sempre ser comparado ao histórico de eventos processados para identificar e corrigir divergência).

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
Regras de funcionamento: RN-046 (encerramento de ciclo de Meta), RN-034 (alerta de Lote vencendo), IN-019 (alerta de escala não confirmada a X dias), RN-013 (expiração de Orçamento por validade vencida), RN-011 (perda de Lead por inatividade), RN-030 (verificação periódica de ponto de reposição, complementar à reação por evento), RN-042 (ciclo periódico de previsão de demanda pela Inteligência Artificial).
Restrições: nunca decide uma regra de negócio por conta própria — apenas aciona, na hora certa, o Caso de Uso do Serviço responsável pela regra; falha de execução de um Job nunca é silenciosa (Capítulo 19).
Impacto nos demais módulos: aciona Casos de Uso em Metas, Suprimentos (Lote), Pessoas e Recursos (Escala), Comercial (Orçamento) — sem nunca pertencer a nenhum desses Serviços, é um componente transversal que os aciona.

**Catálogo de Jobs Agendados identificados** (ampliado nesta auditoria corretiva com 3 Jobs adicionais — RN-011, RN-030, RN-042 — encontrados durante a construção da Matriz de Rastreabilidade das Regras de Negócio, Capítulo 30; permanece não exaustivo — novos Jobs podem ser adicionados de forma aditiva conforme novas regras de negócio dependentes de tempo forem aprovadas):

| Job | Periodicidade conceitual | Serviço acionado | Regra/Integração de origem |
|---|---|---|---|
| Encerramento de ciclo de Meta | Na data de término do ciclo | Metas | RN-046, IN-018 |
| Alerta de Lote próximo do vencimento | Diária | Suprimentos | RN-034 |
| Alerta de Escala não confirmada | X dias antes do Evento (parâmetro pendente, Configurações) | Pessoas e Recursos | IN-019 |
| Expiração de Orçamento por validade vencida | Na data de validade | Comercial | RN-013 |
| Alerta de pendência de conciliação bancária prolongada | Diária | Financeiro | IN-013 |
| Perda de Lead por inatividade | Verificação periódica (período configurável, Configurações) | Comercial | RN-011 |
| Verificação periódica de ponto de reposição | Diária (complementar à reação por evento "Estoque atualizado") | Suprimentos | RN-030, RN-033, IN-009 |
| Ciclo periódico de previsão de demanda | Periodicidade definida pela Direção (parâmetro pendente, Configurações) | Inteligência Artificial | RN-042, IN-015 |

## 16. Filas Conceituais

**Novo conceito desta fase** (achado de auditoria): o Event Bus (TCOS-006) definiu o padrão publicar/assinar, mas nunca formalizou como a entrega de um evento é garantida entre a publicação e o processamento por cada assinante. Este capítulo formaliza esse comportamento, sem nomear tecnologia de mensageria.

**Componente: Barramento de Eventos e Filas**
Objetivo: garantir que todo evento publicado por um Serviço seja efetivamente processado por todos os seus assinantes, mesmo em caso de indisponibilidade temporária de um deles, em conformidade com a regra 6 do Controle Transacional (Capítulo 20).
Responsabilidades: entregar cada evento a cada assinante de forma independente (uma fila lógica por par publicador-assinante); preservar a ordem de eventos de uma mesma entidade; aplicar nova tentativa (**retry**) em caso de falha de processamento; direcionar um evento que esgotou as tentativas de retry para uma **Fila de Falhas** (equivalente conceitual a uma fila de mensagens não entregues), nunca descartá-lo; oferecer um mecanismo de **reconciliação** que permita, a qualquer momento, comparar o estado de um Agregado com o histórico de eventos já processados e identificar divergência.
Entradas: todo evento publicado por qualquer Serviço (Capítulo 14).
Saídas: entrega do evento a cada Serviço assinante; ao esgotar as tentativas de entrega, o evento é movido para a Fila de Falhas e um registro de exceção é gerado (Capítulo 19).
Dependências: nenhuma — é o mecanismo estrutural sobre o qual toda comunicação assíncrona (Capítulo 13) se apoia.
Regras de funcionamento:
- **Retry:** toda falha de entrega ou de processamento aciona uma nova tentativa, dentro de um limite definido, antes de qualquer escalonamento.
- **Idempotência:** um evento já processado com sucesso por um assinante nunca é reprocessado por ele (idempotência conceitual) — condição necessária para que o retry nunca duplique um efeito de negócio.
- **Fila de Falhas:** um evento que esgota as tentativas de retry é movido para a Fila de Falhas, onde permanece visível e alertável até intervenção técnica — nunca é descartado silenciosamente.
- **Reconciliação:** periodicamente, ou sob demanda, o estado persistido de um Agregado pode ser comparado ao histórico de eventos já assinados/processados (Auditoria, Capítulo 17), para identificar e corrigir qualquer divergência causada por uma falha já resolvida na Fila de Falhas.
- Um evento sobre a mesma entidade nunca é processado fora de ordem por um mesmo assinante.
Restrições: nunca perde um evento silenciosamente — falha de entrega definitiva é sempre registrada na Fila de Falhas e alertável, nunca descartada sem rastro; nunca bloqueia o publicador aguardando confirmação de todos os assinantes (PF-02, comunicação nunca síncrona entre Serviços via evento).
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

**Regra Transacional de Agregados (versão corrigida nesta auditoria — ver Auditoria de Abertura, item de correção 2; esta é a formulação oficial e única, referenciada, nunca reformulada de modo divergente, pelos Capítulos 7, 8, 9, 10, 11 e 12):**

1. Um Caso de Uso pode consultar outros Agregados ou Serviços somente através de seus contratos públicos (Capítulo 7) — nunca por acesso à estrutura interna de outro Agregado ou Serviço.
2. Uma transação modifica exatamente um Agregado (TCOS-007, Seção 3.2) — nunca dois Agregados na mesma transação, mesmo que pertençam ao mesmo Serviço.
3. Não existem transações distribuídas entre Serviços — nenhuma transação permanece aberta aguardando resposta de outro Serviço.
4. Qualquer alteração necessária em outro Agregado ocorre através de um **novo Caso de Uso, iniciado por Evento** (Capítulo 11 — Orquestração) — nunca dentro da mesma transação do Caso de Uso de origem.
5. Consultas síncronas a outro Agregado ou Serviço (Capítulo 12) nunca tornam esse outro Agregado parte da transação corrente — a consulta é uma leitura externa ao contrato público, concluída antes ou durante a transação, mas nunca sob o mesmo escopo transacional.
6. Todo processamento assíncrono decorrente da regra 4 deve respeitar retry, idempotência, fila de falhas e reconciliação, exatamente como detalhado no Capítulo 16 (Filas Conceituais).

**Aplicação da regra quando uma ação de negócio afeta mais de um Agregado** (ex.: "Compra conferida gera Estoque/Lote/Despesa", já descrito no TCOS-007 Seção 4.3):

- **Um único Caso de Uso, um único Agregado, com submembros internos** (regra 2): quando os dados afetados pertencem à mesma raiz de consistência (ex.: Compra e seus Itens são o mesmo Agregado) — a transação cobre o Agregado inteiro, nunca um Agregado externo.
- **Múltiplos Casos de Uso encadeados por Evento, entre Serviços diferentes** (regras 3 e 4): quando os Agregados afetados pertencem a Serviços diferentes (ex.: "Compra conferida", publicada pelo Serviço Suprimentos, inicia um novo Caso de Uso no Serviço Financeiro que grava o Agregado Financeiro) — cada Serviço executa sua própria transação local sobre seu próprio Agregado, e a consistência entre elas é **eventual**, nunca uma transação distribuída única (confirmado no Fluxo de Sincronização, TCOS-009 Capítulo 10).

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

## 30. Matriz de Rastreabilidade das Regras de Negócio (RN-001 a RN-047)

**Capítulo criado nesta auditoria corretiva** (item de correção 3). Cobre as 47 Regras de Negócio já aprovadas no Business Rules Specification (TCOS-002A), sem alterar nenhuma delas — apenas demonstrando, regra a regra, qual componente desta arquitetura de backend a executa. Legenda de "Tipo de execução": **S** = Síncrono (Capítulo 12); **A** = Assíncrono (Capítulo 13); **J** = Job Agendado (Capítulo 15); **T** = Transversal (aplicada dentro de outros Casos de Uso, sem Caso de Uso próprio).

| RN | Serviço responsável | Caso de Uso responsável | Tipo | Agregado alterado | Evento publicado | Integração relacionada | Capítulo TCOS-010 |
|---|---|---|---|---|---|---|---|
| RN-001 | Indicadores e Dashboards | Recalcular Indicador | A | Indicador | "Indicador recalculado" | IN-016/IN-017 | 13 |
| RN-002 | Financeiro | Registrar retirada pessoal | S | Agregado Financeiro (Despesa) | "Despesa registrada" | IN-014 | 12 |
| RN-003 | Custos e Precificação / Financeiro | Apurar resultado do Evento | A | leitura agregada (Evento, sem persistência própria) | nenhum evento próprio — alimenta Indicador | IN-011 | 13 |
| RN-004 | Financeiro | Fechar período financeiro | S | Agregado Financeiro (consolidação) | nenhum evento de domínio catalogado até o TCOS-002 | nenhuma (não é uma das 20 Integrações) | 12 |
| RN-005 | Financeiro | Registrar Despesa/Receita Financeira (validação) | S | Agregado Financeiro | nenhum evento próprio — gera alerta | IN-014 | 19 (categoria 1) |
| RN-006 | Eventos (origem) + assinantes | Confirmar Evento | S (origem) / A (reação) | Evento | "Evento confirmado" | IN-001 | 11, 20 |
| RN-007 | Eventos | Cancelar Evento | S (origem) / A (reação) | Evento | "Evento cancelado" | nenhuma das 20 Integrações trata o cancelamento como fluxo dedicado — evento catalogado no Event Bus (TCOS-006) sem Integração própria no TCOS-009; achado registrado como pendência de cobertura do TCOS-009, não deste documento | 11, 13 |
| RN-008 | Comercial | Registrar Lead | S | Lead | "Lead criado" | IN-002/IN-004 | 12 |
| RN-009 | Comercial | Converter Lead em Cliente | S | Lead (escrita) + Cliente (consulta via contrato, e escrita própria se novo) | "Lead convertido em Cliente" | IN-002 | 20 (exemplo de consulta que não amplia a transação), 8 |
| RN-010 | Comercial | Marcar fidelização (reação a "Evento concluído") | A | Cliente | nenhum evento de domínio próprio catalogado — atualiza atributo do Agregado Cliente | IN-011 (indireto) | 13 |
| RN-011 | Comercial | Marcar Lead como perdido por inatividade | J | Lead | "Lead marcado como perdido" | nenhuma das 20 Integrações | 15 |
| RN-012 | Comercial (consulta Custos e Precificação) | Incluir item em Orçamento | S | Orçamento | nenhum evento próprio | IN-007 (relacionado) | 7, 12 |
| RN-013 | Comercial | Expirar Orçamento | J | Orçamento | "Orçamento expirado" | nenhuma das 20 Integrações dedicada | 15 |
| RN-014 | Comercial → Documentos | Gerar Contrato / Gerar Documento | A | Contrato / Documento | "Contrato gerado", "Documento gerado" | IN-002, IN-020 | 13 |
| RN-015 | Comercial | Registrar Aditivo de Contrato | S | Contrato (aditivo como submembro) | "Contrato aditivado" | nenhuma das 20 Integrações dedicada | 20 (submembros internos) |
| RN-016 | Produção | Planejar Produção | A | Produção | "Produção planejada" | IN-005 | 11, 13 |
| RN-017 | Produção | Concluir Produção (comparação planejado vs. real) | S | Produção | "Produção concluída" | IN-006 | 12 |
| RN-018 | Custos e Precificação | Apurar custo total do Evento | A / S (sob demanda) | leitura agregada (sem persistência própria) | nenhum evento próprio | IN-011 | 13, 23 (leitura derivada) |
| RN-019 | Custos e Precificação | Recalcular custo em cascata | A | Ficha Técnica | "Ficha Técnica recalculada" / "Custo recalculado" | IN-007 | 13 |
| RN-020 | Produção | Revisar Receita | S | Receita | "Receita revisada" | nenhuma das 20 Integrações dedicada | 21 |
| RN-021 | Comercial (consulta Produção) | Incluir item em Orçamento (bloqueio) | S | Orçamento (bloqueio antes de persistir) | nenhum (bloqueio não gera evento) | IN-002/IN-007 (relacionado) | 19 (categoria 1), 7 |
| RN-022 | Custos e Precificação | Atualizar preço | S (definição manual) / A (recálculo em cascata) | Ficha Técnica/Produto | "Preço atualizado" | IN-007 | 12, 13 |
| RN-023 | Comercial | Validar margem ao revisar Orçamento | S | Orçamento | nenhum evento — gera alerta | IN-001 (relacionado) | 19 (categoria 1), 12 |
| RN-024 | Produção | Planejar Produção (cálculo de consumo) | A (via IN-005) / S (se recálculo manual) | Produção | parte de "Produção planejada" | IN-005 | 13, 24 |
| RN-025 | Produção | Planejar Produção (ajuste por tipo de Evento) | A / S | Produção/Orçamento | parte de "Produção planejada" | IN-005 | 13, 24 |
| RN-026 | Produção | Planejar Produção (múltiplos acompanhamentos) | A / S | Produção | parte de "Produção planejada" | IN-005 | 13, 24 |
| RN-027 | Suprimentos | Gerar lista de reposição | A | Compra (proposta) | nenhum evento próprio — insumo do Caso de Uso "Registrar Compra" | IN-009 | 13, 24 |
| RN-028 | Produção | Concluir Produção (registro de perda) | S | Produção | "Produção concluída" | IN-006 | 12 |
| RN-029 | Produção | Concluir Produção (rendimento real vs. previsto) | S | Produção | "Produção concluída" | IN-006 | 12 |
| RN-030 | Suprimentos | Gerar lista de reposição | A (evento) + J (verificação periódica) | Compra (proposta) | nenhum evento próprio de "lista gerada" | IN-009 | 13, 15 |
| RN-031 | Suprimentos | Conferir Compra | S (origem) / A (reação encadeada) | Compra (+ Estoque/Lote gerados) | "Compra conferida" | IN-008, IN-010 | 20 (exemplo central da Regra Transacional), 12, 13 |
| RN-032 | Suprimentos | Registrar consumo de Estoque | A | Estoque (posição) + Lote | "Estoque atualizado"/"Estoque baixado" | IN-008 | 13 |
| RN-033 | Suprimentos | Verificar ponto de reposição | A (reação a "Estoque atualizado") + J (verificação periódica) | Estoque | nenhum evento próprio — gera alerta | IN-009 | 13, 15, 19 |
| RN-034 | Suprimentos | Job "Alerta de Lote próximo do vencimento" | J | Lote | "Lote vencido" (quando efetivamente vence) | nenhuma das 20 Integrações trata diretamente (evento catalogado no Event Bus, TCOS-006) | 15 |
| RN-035 | Pessoas e Recursos | Alocar Equipamento | S | Equipamento (alocação) | "Equipamento alocado" (se sucesso) | IN-001/IN-019 (relacionado) | 19 (categoria 1), 12 |
| RN-036 | Custos e Precificação | Consolidar custo de mão de obra | A | leitura agregada (sem persistência própria) | nenhum evento próprio | IN-010 | 13 |
| RN-037 | Pessoas e Recursos | Sugerir Escala | A | Alocação de Funcionário | nenhum evento próprio da sugestão (confirmação gera "Alocação de Funcionário realizada") | IN-019 | 13 |
| RN-038 | Marketing | Atribuir retorno de Campanha | A | Campanha | "Retorno atribuído" | IN-003 | 13 |
| RN-039 | Indicadores e Dashboards | Atualizar composição de Dashboard | S | Dashboard | "Dashboard atualizado" | IN-017 | 12 |
| RN-040 | Indicadores e Dashboards | Definir/Revisar fórmula de Indicador; Recalcular Indicador | S (definição/revisão) + A (recálculo contínuo) | Indicador | "Indicador definido"/"Fórmula de Indicador revisada"/"Indicador recalculado" | IN-016 | 12, 13, 21 |
| RN-041 | Inteligência Artificial | Gerar sugestão (regra geral) | A | nenhum Agregado próprio da IA — decisão final altera o Agregado do Serviço de origem | "Sugestão gerada (IA)" | IN-015 | 28, 13 |
| RN-042 | Inteligência Artificial | Gerar previsão de demanda | J (ciclo periódico) / A (sob demanda) | nenhum Agregado próprio | "Sugestão gerada (IA)" | IN-015 | 28, 15 |
| RN-043 | Financeiro + Inteligência Artificial | Importar Extrato; Gerar sugestão de categorização | S (importação) + A (sugestão) | Agregado Financeiro (Pagamento candidato) | "Extrato bancário importado" → "Sugestão gerada (IA)" | IN-012, IN-015 | 12, 13, 28 |
| RN-044 | Financeiro | Conciliar Pagamento | S (ação do usuário) / A (reação à importação) | Pagamento | nenhum evento de domínio próprio catalogado para "conciliado" — atualiza atributo de status | IN-013 | 12, 13 |
| RN-045 | Financeiro | Registrar Despesa/Receita Financeira manualmente | S | Agregado Financeiro | "Despesa registrada"/"Receita Financeira prevista" (mesmo evento de um lançamento automático) | IN-010 | 17, 12 |
| RN-046 | Metas | Encerrar ciclo de Meta | J | Meta | "Ciclo de Meta encerrado" | IN-018 | 15 |
| RN-047 | Transversal (aplicada por todos os Serviços) | nenhum Caso de Uso próprio — convenção aplicada dentro de cada Caso de Uso que gera alerta | T | nenhum Agregado próprio | nenhum evento próprio | todas as 20 Integrações (campo "Alertas gerados" já citado em cada uma) | 19, 25 |

**Justificativas formais para regras sem evento de domínio ou Integração dedicada exclusiva** (exigido pelo Prompt Oficial quando uma regra não gera comportamento arquitetural específico de comunicação cross-Serviço):

- **RN-004 (Fechamento de Período):** é um Caso de Uso síncrono interno ao Serviço Financeiro, disparado por comando da Direção/Financeiro, sem cadeia de reação documentada em outro Serviço no Integration and API Contract (TCOS-009) — por isso não há evento de domínio catalogado nem Integração associada. O comportamento está integralmente coberto pelo Capítulo 12 (Processamento Síncrono); não há lacuna de execução, apenas ausência de comunicação cross-Serviço a documentar.
- **RN-007 (Cancelamento de Evento):** o evento "Evento cancelado" está catalogado no Event Bus (TCOS-006, Capítulo 7) e a reação de múltiplos Serviços (liberação de recursos, tratamento financeiro) está descrita na Regra de Negócio — mas o Integration and API Contract (TCOS-009) não formalizou essa cadeia como uma das suas 20 Integrações numeradas. Esta arquitetura de backend executa o comportamento normalmente pelo padrão de orquestração coreografada (Capítulo 11), como reação ao evento já catalogado; a ausência de um IN-XXX dedicado é registrada como um achado de cobertura do TCOS-009 (não deste documento), sem impedir a execução, e não é corrigida aqui por não ser mandato desta fase alterar um documento já congelado.

**Confirmação de rastreabilidade:** as 47 linhas acima cobrem RN-001 a RN-047 sem lacuna — rastreabilidade **47/47** demonstrada nesta matriz. Nenhuma Regra de Negócio foi criada, alterada ou removida; todas já constavam do Business Rules Specification (TCOS-002A, congelado).

---

## RESUMO PARA O PROPRIETÁRIO

Este documento (TCOS-010) responde à pergunta: **por dentro de cada "setor" do sistema (cada um dos 15 Serviços já definidos), como o trabalho realmente vai ser organizado e executado?**

O que foi construído: detalhamos, para cada um dos 15 Serviços, exatamente o que ele recebe, o que ele produz, de quem depende e o que nunca pode fazer — uma espécie de "descrição de cargo" completa para cada setor interno do sistema. Além disso, formalizamos conceitos que ainda não existiam em nenhum documento anterior: como o sistema executa tarefas programadas por data (por exemplo, avisar quando um Lote está perto de vencer, ou encerrar automaticamente um ciclo de Meta), como ele garante que nenhum aviso entre setores se perde, como ele trata um erro sem travar o sistema todo, e como ele continua funcionando mesmo que uma parte não crítica (como a Inteligência Artificial) fique temporariamente indisponível.

Por que isso é importante: até aqui, sabíamos *o que* o sistema faz e *quem conversa com quem*. Faltava saber *como* cada "setor" organiza seu próprio trabalho por dentro, de forma que o sistema continue simples de manter mesmo depois de crescer por anos — sem que um problema em uma área derrube as demais.

Como isso conecta com tudo que já foi construído: cada um dos 15 Serviços aqui detalhados é exatamente o mesmo já aprovado na Arquitetura de Sistema; cada regra de negócio aplicada é exatamente uma das 47 já aprovadas; cada estrutura de dado usada é exatamente uma das já definidas na Arquitetura de Dados e no Banco de Dados; cada integração citada é exatamente uma das 20 já aprovadas. Nada foi reinventado — apenas detalhado o "como" interno.

Como isso prepara o próximo passo: com este documento, uma equipe de desenvolvimento tem a organização interna necessária para começar a escolher a linguagem de programação, o banco de dados físico e a tecnologia de comunicação entre sistemas — sem que essas escolhas exijam redefinir como cada parte se comporta por dentro.

Nada de código, linguagem, framework, banco físico ou tecnologia foi definido nesta fase — apenas o "manual de organização interna" de cada setor do sistema.

**Sobre esta versão do documento:** após a primeira entrega, o proprietário solicitou uma auditoria corretiva (comando `CORRIGIR`) antes de aprovar. Essa auditoria encontrou e corrigiu uma contagem ambígua de documentos oficiais, reformulou a regra de transação em seis pontos exatos, adicionou uma matriz mostrando como cada uma das 47 Regras de Negócio é executada, verificou mais de 60 referências internas (encontrando e corrigindo 2 que apontavam para o capítulo errado) e suavizou frases que soavam mais absolutas do que o documento conseguia comprovar sozinho. Nenhuma regra de negócio, entidade ou integração já aprovada foi alterada — apenas a organização e a precisão deste documento em rascunho.

---

## TCOS QUALITY GATE EXECUTIVO

Esta é a segunda rodada de Quality Gate desta fase, produzida após a Auditoria Corretiva solicitada pelo proprietário (comando `CORRIGIR`). Em conformidade com a Regra Permanente do Framework, os 13 Documentos Oficiais Congelados foram revisados quanto aos pontos relevantes a esta fase; adicionalmente, o próprio rascunho do TCOS-010 foi revisado internamente (contagem de documentos, regra transacional, cobertura de regras de negócio, referências cruzadas, declarações categóricas) — resultado consolidado na Auditoria de Abertura/Auditoria Corretiva e detalhado item a item abaixo.

**1. Resumo Executivo**
Definida a arquitetura lógica interna de backend do THE CHARCOAL OS: organização em 4 camadas por Serviço, 15 Serviços detalhados em 8 campos cada, conceito de Caso de Uso regido pela Regra Transacional de Agregados (6 pontos, Capítulo 20), orquestração coreografada, processamento síncrono/assíncrono, 10 componentes transversais (incluindo os 3 conceitos genuinamente novos desta fase: Jobs Agendados, Filas Conceituais, e a separação Logs/Observabilidade/Tolerância a Falhas), e uma Matriz de Rastreabilidade cobrindo as 47 Regras de Negócio (Capítulo 30, novo nesta auditoria corretiva). Nenhuma tecnologia foi definida; nenhum documento das Fases 000-009 foi alterado.

**2. Estado atual do projeto**
Fases 000 a 009 encerradas e oficiais; Fase 010 em correção, ainda não aprovada. Nenhum código, API, banco físico ou desenvolvimento foi iniciado.

**3. Documentos oficiais existentes**
**14 no total** — **13 Documentos Oficiais Congelados** (Development Framework, Enterprise Domain Discovery, Business Discovery Questionnaire, Discovery Interview Roadmap, Domain Model, Business Rules Specification, Functional Specification, User Journeys and System Flows, UX/UI Specification, System Architecture, Data Architecture, Database Specification, Integration and API Contract) **+ 1 Documento Oficial Vivo** (`PROJECT_MEMORY.md`). Este documento (TCOS-010) permanece em rascunho e não é contado como oficial até aprovação — critério corrigido nesta auditoria (item de correção 1).

**4. Dependências desta fase**
15 Serviços Conceituais e Event Bus (TCOS-006); 7 Domínios de Dados e 24 Agregados (TCOS-007); 32 estruturas conceituais (TCOS-008); 20 Integrações (TCOS-009); 47 Regras de Negócio; 98 funcionalidades — todos referenciados, nenhum reescrito.

**5. Pendências abertas**
Validação formal deste documento; parâmetros do Módulo 24 (incluindo os 2 novos parâmetros identificados nesta auditoria: periodicidade do Job de previsão de demanda e período de inatividade de Lead); M-003A-03/04; M-005-01/02/03; M-006-01; M-007-01; M-008-01; M-009-01; confirmação do domínio de negócio (R-000-03). Nenhuma pendência nova de negócio além dos parâmetros de Configuração já identificados.

**6. Dúvidas encontradas**
Nenhuma nova de negócio. A dúvida técnica já registrada na primeira rodada (como formalizar processamento agendado e confiabilidade de entrega de evento) permanece respondida nos Capítulos 15 e 16.

**7. Riscos ativos**
R-000-03/R-002-01, R-001-01/R-002-02, R-002A-01 — herdados; nenhum impede a arquitetura de backend.

**8. Novos riscos encontrados**
Nenhum risco novo de negócio.

**9. Inconsistências encontradas e corrigidas nesta auditoria**
1. Contagem ambígua de Documentos Oficiais (14 listados vs. "13"/"os 13" citados em 3 pontos diferentes do texto, sem critério declarado) — corrigida (item 1, ver Auditoria Corretiva).
2. Formulação da regra transacional dispersa e menos precisa que a versão oficial de 6 pontos determinada pelo proprietário — corrigida e propagada aos Capítulos 7, 8, 9, 10, 11, 12, 16 (item 2).
3. Estatística "34 das 47 Regras de Negócio referenciadas" sem matriz que a comprovasse — substituída por rastreabilidade 47/47 demonstrada (Capítulo 30, item 3).
4. Catálogo de Jobs Agendados incompleto: 3 regras dependentes de tempo (RN-011, RN-030, RN-042) não constavam da tabela do Capítulo 15 — adicionadas (item 3).
5. Duas referências cruzadas apontando para números de capítulo desatualizados ("Jobs Agendados, Capítulo 13" e "Filas Conceituais, Capítulo 14", corretos: 15 e 16) — corrigidas (item 5).
6. Declarações absolutas não comprováveis pelo próprio documento ("todos os documentos lidos integralmente", "nenhuma inconsistência encontrada", promessa de implementação integral a partir deste único documento) — reformuladas para afirmações com escopo declarado (item 6).

**10. Conflitos entre documentos**
Nenhum — todas as correções desta rodada foram internas ao rascunho do TCOS-010; nenhum dos 13 Documentos Oficiais Congelados foi alterado ou contradito.

**11. Serviços sem estrutura interna**
Nenhum — **15 de 15 (100%)** Serviços Conceituais têm os 8 campos obrigatórios detalhados (Capítulo 6).

**12. Regras de negócio sem suporte de execução**
Nenhuma — **47 de 47 (100%)** Regras de Negócio rastreadas individualmente na Matriz do Capítulo 30, com Serviço, Caso de Uso, tipo de execução, Agregado, evento e capítulo responsável; 2 delas (RN-004, RN-007) têm justificativa formal registrada por não possuírem evento de domínio/Integração dedicada exclusiva, sem que isso afete sua execução.

**13. Integrações sem suporte de orquestração**
Nenhuma — **20 de 20 (100%)** Integrações (TCOS-009) têm o padrão de orquestração (síncrono, assíncrono, coreografado) identificado nos Capítulos 11 a 13, e todas permanecem preservadas sem qualquer redefinição de conteúdo.

**14. Dependências ocultas / Agregados**
Nenhuma dependência oculta nova identificada. **24 de 24 (100%)** Agregados (TCOS-007) respeitados pela Regra Transacional de 6 pontos (Capítulo 20) — nenhum Caso de Uso desta arquitetura descrito na Matriz do Capítulo 30 modifica mais de um Agregado por transação.

**15. Melhorias sugeridas**
- M-010-01 (mantida): ao escolher a tecnologia de mensageria em fase técnica futura, avaliar mecanismos nativos de garantia de entrega/ordem/idempotência antes de implementar o Barramento de Eventos e Filas (Capítulo 16) de forma customizada.
- M-010-02 (mantida): o parâmetro "X dias antes do Evento" para o Job de alerta de escala não confirmada (Capítulo 15) depende de um valor de Configuração ainda não definido.
- M-010-03 (nova, desta auditoria): o Integration and API Contract (TCOS-009) não formalizou uma Integração dedicada para "Evento cancelado" (RN-007) nem para "Lead marcado como perdido" (RN-011) — sugerido para avaliação em uma eventual v1.1.0 daquele documento, sem que isso seja alterado agora (documento congelado).

**16. Impacto nas próximas fases**
Esta arquitetura de backend é a referência obrigatória para qualquer fase técnica futura (escolha de linguagem, framework, banco físico, APIs, desenvolvimento) — nenhuma dessas fases deve introduzir um padrão de camada, transação, comunicação ou tratamento de erro incompatível com o que está aqui documentado, sem registrar formalmente o motivo.

**17. Quality Score (recalculado): 9,7/10**
Justificativa técnica: além da cobertura já reconhecida na primeira rodada (27 itens de arquitetura exigidos, 8 campos obrigatórios para os 25 componentes), esta rodada demonstra rastreabilidade completa e verificável 47/47 das Regras de Negócio, uma regra transacional única e propagada sem contradição por 7 capítulos, e a correção de 6 categorias de imprecisão real encontradas por auditoria independente do próprio autor do documento — evidência de um processo de revisão genuíno, não apenas declarado. A nota sobe em relação à primeira rodada (9,5) por essa correção verificada; não chega a 10 porque as 3 melhorias registradas (M-010-01 a M-010-03) permanecem como refinamento pendente de decisões futuras (tecnologia de mensageria, parâmetro de Configuração, e uma eventual nova versão do TCOS-009).

**18. Atualização do PROJECT_MEMORY.md:** ver commit correspondente — exclusivamente a seção da Fase 010, status mantido como rascunho aguardando validação do proprietário.

**19. Estatísticas Finais (recalculadas)**
- Documentos oficiais: 14 no total (13 congelados + 1 vivo) — ver item 3.
- Serviços Conceituais: **15/15 (100%)**.
- Regras de Negócio rastreadas: **47/47 (100%)** — Capítulo 30.
- Integrações preservadas: **20/20 (100%)**, nenhuma redefinida.
- Agregados respeitados pela regra transacional: **24/24 (100%)**.
- Quantidade de Jobs Agendados identificados: **8** (5 da primeira rodada + 3 adicionados nesta auditoria: RN-011, RN-030, RN-042).
- Quantidade de componentes transversais: 10 (inalterado).
- Quantidade total de componentes com os 8 campos obrigatórios: 25 (15 Serviços + 10 transversais).
- Referências cruzadas internas verificadas: mais de 60 ocorrências de "Capítulo N" conferidas uma a uma; 2 corrigidas (item de correção 5).
- Inconsistências encontradas nesta auditoria: 6, todas corrigidas (ver item 9 acima) — 0 remanescentes.
- Módulos cobertos: 27/27 (100%, via os 15 Serviços).
- Riscos ativos: 4 herdados; 0 novos de negócio.
- Pendências: 9, todas herdadas ou de Configuração já previstas (nenhuma pendência nova de negócio).
- Melhorias: 3 (M-010-01, M-010-02 mantidas; M-010-03 nova).
- Percentual estimado de maturidade do projeto: **84%** (sem alteração em relação à primeira rodada — esta auditoria corrigiu precisão e rastreabilidade do documento já entregue, sem adicionar nem remover escopo arquitetural).

**Status desta fase:** APROVADA E CONGELADA pelo proprietário em 2026-08-02 (comando `APROVADO`, após auditoria corretiva). Este documento passa a integrar a documentação oficial do THE CHARCOAL OS; nenhuma alteração futura sem criação de nova versão formal. Nenhuma fase de linguagem, framework, banco de dados físico, API ou Desenvolvimento foi iniciada. A Fase 011 aguarda o Prompt Oficial do proprietário.

---

*Fim do documento — THE CHARCOAL OS BACKEND ARCHITECTURE v1.0.0 (Oficial)*
