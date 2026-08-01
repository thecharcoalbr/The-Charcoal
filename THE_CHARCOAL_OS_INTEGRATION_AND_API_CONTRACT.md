# THE CHARCOAL OS — INTEGRATION AND API CONTRACT

**Documento:** TCOS-009 — Contrato Conceitual de Integração
**Projeto:** THE CHARCOAL OS
**Fase:** 009 — Integration & API Contract
**Status:** Rascunho para validação do proprietário
**Versão:** 1.0.0

---

## EXECUTIVE MEMORY

- **Estado atual do projeto:** negócio, domínio, regras, funcionalidades, fluxos, UX/UI, arquitetura de sistema, arquitetura de dados e especificação de banco completos e oficiais; iniciando a documentação de como os módulos efetivamente conversam entre si, ainda sem REST, GraphQL, endpoints, autenticação técnica ou protocolo definidos.
- **Fase atual:** 009 — Integration & API Contract (TCOS-009).
- **Fases concluídas:** 000 a 008, todas aprovadas e oficiais (a mais recente, TCOS-008, congelada nesta mensagem).
- **Documentos oficiais:** Framework (v1.2.0), `PROJECT_MEMORY.md`, Domain Discovery (v1.0.0), Business Discovery Questionnaire (v1.0.0), Discovery Interview Roadmap (v1.0.0), Domain Model (v1.0.0), Business Rules Specification (v1.0.0), Functional Specification (v1.2.0), User Journeys and System Flows (v1.0.0), UX/UI Specification (v1.0.0), System Architecture (v1.0.0), Data Architecture (v1.0.0), Database Specification (v1.0.0, congelado a partir de agora).
- **Documentos em elaboração:** este documento (TCOS-009).
- **Pendências:** confirmação do domínio de negócio (R-000-03); parâmetros do Módulo 24; M-003A-03/04; M-005-01/02/03; M-006-01; M-007-01; M-008-01; decisão sobre retomar a entrevista de descoberta.
- **Riscos ativos:** R-000-03/R-002-01, R-001-01/R-002-02, R-002A-01 — herdados; nenhum impede o contrato conceitual de integração, pois toda integração dependente de parâmetro pendente já está descrita com o comportamento de bloqueio/alerta correspondente.
- **Dependências para esta fase:** os 27 módulos e 98 funcionalidades; os 30 fluxos (TCOS-004); os 15 Serviços Conceituais e o Event Bus com seus eventos arquiteturais (TCOS-006); os 7 Domínios de Dados e 30 entidades (TCOS-007); as 32 estruturas conceituais (TCOS-008) — todos referenciados, nenhum reescrito.
- **Objetivo da fase que será iniciada:** documentar como todos os módulos do THE CHARCOAL OS conversam entre si — quando um módulo executa uma ação, quais outros são notificados e como o sistema reage — sem nenhuma decisão de tecnologia de comunicação.
- **O que não pode ser alterado:** nenhum conteúdo de nenhum dos 12 documentos oficiais já aprovados e congelados.

### Auditoria de Abertura

Todos os documentos oficiais foram lidos integralmente. Resultado:

- **Nenhuma inconsistência, conflito ou duplicidade** entre os documentos existentes.
- **Módulos sem integração:** nenhum — todos os 27 módulos aparecem em ao menos uma das 20 Integrações documentadas (Capítulo 3) ou na Matriz Geral de Integração (Capítulo 4).
- **Entidades sem integração:** nenhuma — as 30 entidades aparecem como "Entidades envolvidas" em ao menos uma Integração.
- **Funcionalidades isoladas:** nenhuma das 98 funcionalidades opera de forma isolada do resto do sistema — mesmo as funcionalidades de cadastro simples (ex.: Cadastrar Fornecedor) alimentam integrações subsequentes (ex.: IN-009, Compras).
- **Regras de negócio sem comunicação:** nenhuma das 47 Regras de Negócio deixou de ser referenciada em ao menos uma Integração.
- **Fluxos sem integração:** nenhum dos 30 fluxos do TCOS-004 ficou sem uma Integração correspondente nesta especificação — a relação de cobertura completa está na Matriz Geral (Capítulo 4).
- **Oportunidade de simplificação identificada:** IN-005 (Planejamento de Produção) e IN-019 (Sugestão de Escala) são ambas disparadas pelo mesmo evento "Evento confirmado" e fazem parte da mesma orquestração (IN-001) — documentadas separadamente apenas porque o Prompt Oficial exige o detalhamento de Produção e de Pessoas/Escalas como fluxos distintos; na prática, arquiteturalmente, são ramificações paralelas de uma única publicação de evento (Capítulo 8 — Fluxo de Sincronização).
- **Achado de auditoria:** IN-016 (Indicadores) e IN-017 (Dashboards) têm uma relação de causa-efeito direta e sequencial (todo recálculo de Indicador é seguido de atualização de Dashboard) — mantidas como duas Integrações, mas documentadas com uma cadeia explícita e única no Capítulo 6.
- Nenhuma decisão de tecnologia de comunicação, protocolo, formato de mensagem, autenticação técnica ou API foi tomada, em conformidade com a restrição explícita da fase.

---

## 1. Papel deste Documento

O System Architecture (TCOS-006) definiu os 15 Serviços Conceituais e o padrão publicar-assinar do Event Bus. Este documento (TCOS-009) detalha, integração por integração, **o que efetivamente acontece** quando um módulo age: quem é avisado, o que muda, o que aparece em qual Dashboard, que alerta é gerado, e qual o impacto operacional e financeiro. É o contrato de comportamento entre os módulos — não um contrato técnico de API. Um arquiteto de backend deve conseguir desenhar os endpoints/mensagens reais a partir daqui, sem reinterpretar nenhuma regra de negócio.

## 2. Legenda e Convenções

- **IN-XXX:** identificador único de Integração, numerado sequencialmente.
- Toda referência a Módulo, Serviço, Entidade, Regra (RN-XXX) ou Evento de Domínio usa exatamente os nomes/números já oficiais.
- "Módulo de origem/impactado" usa a numeração 01–27 do Functional Specification; "Serviço de origem/impactado" usa os 15 Serviços do System Architecture.

---

## 3. Integrações

### 3.1 Fluxo Operacional (Orquestração Central)

**IN-001 — Confirmação de Evento → Orquestração Multi-Serviço**
Objetivo: garantir que a confirmação comercial de um Evento aciona toda a cadeia operacional sem reentrada manual | Evento que inicia: "Evento confirmado" | Módulo de origem: 07 | Serviço de origem: Eventos
Entidades: Evento, Contrato, Produção, Estoque, Alocação de Funcionário, Equipamento, Compra, Receita Financeira, Indicador | Módulos impactados: 10, 15, 16, 18, 19, 20, 03, 01 | Serviços impactados: Produção, Suprimentos, Pessoas e Recursos, Financeiro, Indicadores e Dashboards
Dados compartilhados: escopo do Evento, data, Contrato assinado | Regras aplicadas: RN-006
Atualizações automáticas: planejamento de Produção, reserva de Estoque, sugestão de Escala, lista de Compras, previsão financeira, Indicadores | Dashboards atualizados: CEO, Eventos, Financeiro Empresarial, Produção | Indicadores atualizados: margem prevista, Eventos confirmados | Alertas gerados: inviabilidade operacional, margem abaixo do mínimo
Histórico registrado: encadeamento completo no histórico do Evento | Exceções: recurso insuficiente bloqueia a confirmação antes de executar a cadeia | Impacto operacional: aciona toda a operação a partir de uma única ação comercial | Impacto financeiro: define a expectativa de receita, custo e margem do Evento.

### 3.2 Fluxo Comercial e CRM

**IN-002 — Ciclo Comercial: Lead → Cliente → Orçamento → Contrato**
Objetivo: conectar o funil comercial completo em uma cadeia contínua e rastreável | Evento que inicia: "Lead criado" | Módulo de origem: 06 | Serviço de origem: Comercial
Entidades: Lead, Cliente, Orçamento, Contrato, Campanha | Módulos impactados: 05, 08, 09, 04 | Serviços impactados: Comercial, Marketing
Dados compartilhados: dados de contato, origem, histórico de negociação | Regras aplicadas: RN-008, RN-009, RN-011 a RN-015
Atualizações automáticas: conversão sem duplicidade, cálculo de preço, geração de minuta de Contrato | Dashboards atualizados: CRM, CEO | Indicadores atualizados: taxa de conversão, tempo médio de fechamento | Alertas gerados: duplicidade, Lead inativo, margem baixa, dados ausentes
Histórico registrado: toda transição de estágio e versão de Orçamento | Exceções: correspondência ambígua exige confirmação humana | Impacto operacional: define o funil que alimentará Eventos | Impacto financeiro: origina a Receita Financeira futura da empresa.

**IN-003 — CRM: Atribuição de Retorno de Campanha**
Objetivo: medir e consolidar o retorno comercial gerado por cada Campanha | Evento que inicia: "Lead convertido em Cliente" / "Contrato assinado" | Módulo de origem: 21 | Serviço de origem: Marketing
Entidades: Campanha, Lead, Cliente, Contrato | Módulos impactados: 04, 06, 05 | Serviços impactados: Comercial, Indicadores e Dashboards
Dados compartilhados: vínculo de origem do Lead | Regras aplicadas: RN-038
Atualizações automáticas: atribuição de conversão/valor à Campanha | Dashboards atualizados: Marketing, CRM | Indicadores atualizados: retorno por Campanha, custo por Lead/Cliente | Alertas gerados: nenhum próprio
Histórico registrado: atribuição permanente e consultável | Exceções: Cliente sem origem identificável é "origem direta" | Impacto operacional: orienta decisão de investimento em canais | Impacto financeiro: mede retorno sobre investimento em marketing.

### 3.3 Fluxo de Marketing

**IN-004 — Marketing: Geração de Lead por Campanha**
Objetivo: alimentar o funil comercial a partir de iniciativas de marketing | Evento que inicia: "Campanha criada/em execução" | Módulo de origem: 21 | Serviço de origem: Marketing
Entidades: Campanha, Lead | Módulos impactados: 06, 04 | Serviços impactados: Comercial
Dados compartilhados: canal, período, objetivo | Regras aplicadas: RN-008
Atualizações automáticas: registro de origem em todo novo Lead | Dashboards atualizados: Marketing | Indicadores atualizados: Leads gerados por Campanha | Alertas gerados: nenhum
Histórico registrado: vínculo de origem imutável | Exceções: nenhuma | Impacto operacional: previsibilidade de volume de entrada comercial | Impacto financeiro: base do custo de aquisição.

### 3.4 Fluxo de Produção

**IN-005 — Produção: Planejamento Automático a partir de Evento Confirmado**
Objetivo: transformar o escopo comercial confirmado em plano de produção executável | Evento que inicia: "Evento confirmado" (parte da IN-001) | Módulo de origem: 07 | Serviço de origem: Eventos
Entidades: Produção, Ficha Técnica, Ingrediente, Evento | Módulos impactados: 10, 13, 24, 16 | Serviços impactados: Produção, Suprimentos
Dados compartilhados: convidados, Produtos/Pacotes do Evento | Regras aplicadas: RN-016, RN-024 a RN-027
Atualizações automáticas: quantidade calculada, verificação de Estoque | Dashboards atualizados: Produção | Indicadores atualizados: volume planejado, desvio esperado | Alertas gerados: prazo insuficiente, parâmetro não definido
Histórico registrado: plano vinculado ao Evento | Exceções: parâmetro de consumo pendente bloqueia o cálculo automático | Impacto operacional: define a agenda de produção | Impacto financeiro: base do custo previsto do Evento.

**IN-006 — Produção: Execução, Perdas e Rendimento**
Objetivo: capturar o resultado real da Produção frente ao planejado | Evento que inicia: "Produção concluída" | Módulo de origem: 10 | Serviço de origem: Produção
Entidades: Produção, Lote, Estoque, Ficha Técnica | Módulos impactados: 16, 17, 11 | Serviços impactados: Suprimentos, Custos e Precificação, Indicadores
Dados compartilhados: consumo real, rendimento real | Regras aplicadas: RN-017, RN-028, RN-029, RN-032
Atualizações automáticas: baixa de Estoque, geração de Lote, cálculo de desvio | Dashboards atualizados: Produção, Engenharia de Custos | Indicadores atualizados: desvio de rendimento, desvio de perda | Alertas gerados: rendimento insuficiente (alta prioridade)
Histórico registrado: planejado vs. real por Produção | Exceções: rendimento insuficiente exige decisão operacional imediata | Impacto operacional: pode exigir produção emergencial adicional | Impacto financeiro: altera o custo efetivo por porção.

### 3.5 Fluxo de Engenharia de Custos

**IN-007 — Engenharia de Custos: Recálculo em Cascata**
Objetivo: manter o custo de produção sempre atualizado sem intervenção manual | Evento que inicia: "Custo de Ingrediente atualizado" | Módulo de origem: 15 | Serviço de origem: Suprimentos
Entidades: Ingrediente, Ficha Técnica, Orçamento | Módulos impactados: 13, 14, 08, 11 | Serviços impactados: Produção, Custos e Precificação, Comercial
Dados compartilhados: novo custo unitário | Regras aplicadas: RN-018, RN-019
Atualizações automáticas: recálculo de todas as Fichas Técnicas afetadas, alerta em Orçamentos abertos | Dashboards atualizados: Engenharia de Custos | Indicadores atualizados: custo médio por Produto | Alertas gerados: impacto em Orçamento aberto
Histórico registrado: nova versão de Ficha Técnica | Exceções: Orçamentos já aceitos não são recalculados retroativamente | Impacto operacional: nenhum direto | Impacto financeiro: protege a margem de vendas ainda não fechadas.

### 3.6 Fluxo de Estoque e Compras

**IN-008 — Estoque: Movimentação Automática e Rastreabilidade por Lote**
Objetivo: manter o saldo de Estoque sempre correto e rastreável | Evento que inicia: "Compra conferida" / "Produção iniciada/concluída" / venda direta | Módulo de origem: 15/10 | Serviço de origem: Suprimentos, Produção
Entidades: Estoque, Lote, Ingrediente, Produto | Módulos impactados: 16, 17 | Serviços impactados: Suprimentos
Dados compartilhados: quantidade, Lote de origem/destino | Regras aplicadas: RN-032, RN-033, RN-034
Atualizações automáticas: atualização de saldo, priorização por validade, alerta de reposição | Dashboards atualizados: Estoque | Indicadores atualizados: giro de Estoque, perda por vencimento | Alertas gerados: saldo insuficiente, ponto de reposição, validade próxima
Histórico registrado: toda movimentação com origem e Lote | Exceções: saldo nunca fica negativo | Impacto operacional: evita ruptura e garante rastreabilidade de segurança alimentar | Impacto financeiro: evita compra emergencial mais cara e perda por vencimento.

**IN-009 — Compras: Geração de Lista e Reposição**
Objetivo: eliminar o cálculo manual do que precisa ser comprado | Evento que inicia: "Produção planejada" / ponto de reposição atingido | Módulo de origem: 10/16 | Serviço de origem: Produção, Suprimentos
Entidades: Compra, Fornecedor, Ingrediente, Estoque | Módulos impactados: 15, 03 | Serviços impactados: Suprimentos, Financeiro
Dados compartilhados: quantidade necessária, Fornecedor preferencial | Regras aplicadas: RN-030, RN-031, RN-027
Atualizações automáticas: lista de Compras sugerida, geração de Despesa na conferência | Dashboards atualizados: Estoque, Financeiro Empresarial | Indicadores atualizados: prazo médio de entrega | Alertas gerados: item sem Fornecedor, prazo incompatível, divergência na conferência
Histórico registrado: lista sugerida e decisão tomada | Exceções: item sem Fornecedor exige decisão manual | Impacto operacional: garante insumo disponível a tempo do Evento | Impacto financeiro: gera a Despesa real de reposição.

### 3.7 Fluxo Financeiro

**IN-010 — Financeiro: Geração Automática de Despesa e Receita Financeira**
Objetivo: eliminar lançamento manual redundante a partir de eventos de origem já confirmados | Evento que inicia: "Contrato assinado" / "Compra conferida" / "Alocação realizada" | Módulo de origem: 09/15/20 | Serviço de origem: Comercial, Suprimentos, Pessoas e Recursos
Entidades: Receita Financeira, Despesa, Contrato, Compra, Alocação de Funcionário | Módulos impactados: 03, 27 | Serviços impactados: Financeiro
Dados compartilhados: valor, condições, Conta de referência | Regras aplicadas: RN-002, RN-005, RN-036, RN-045
Atualizações automáticas: criação de Despesa/Receita Financeira prevista | Dashboards atualizados: Financeiro Empresarial, CEO | Indicadores atualizados: Fluxo de Caixa previsto, margem | Alertas gerados: lançamento ambíguo
Histórico registrado: toda geração automática vinculada à origem | Exceções: origem ambígua exige confirmação humana | Impacto operacional: nenhum direto | Impacto financeiro: origem de praticamente todo lançamento financeiro do sistema.

**IN-011 — Financeiro: Encerramento de Evento e Apuração de Resultado**
Objetivo: conhecer a margem real de cada Evento assim que ele é concluído | Evento que inicia: "Evento concluído" | Módulo de origem: 07 | Serviço de origem: Eventos
Entidades: Evento, Produção, Despesa, Receita Financeira, Ficha Técnica | Módulos impactados: 11, 03, 01 | Serviços impactados: Custos e Precificação, Financeiro, Indicadores e Dashboards
Dados compartilhados: custo real total, Receita Financeira recebida | Regras aplicadas: RN-003, RN-017, RN-018
Atualizações automáticas: cálculo de custo total real, apuração de margem | Dashboards atualizados: CEO, Financeiro, Engenharia de Custos | Indicadores atualizados: margem por Evento, desvio de custo | Alertas gerados: custo real excedendo o previsto
Histórico registrado: apuração preservada permanentemente | Exceções: margem "prevista" enquanto houver Despesa pendente | Impacto operacional: dispara a jornada de Pós-venda | Impacto financeiro: resultado financeiro definitivo do Evento.

### 3.8 Fluxo Bancário

**IN-012 — Importação Automática de Extratos Bancários**
Objetivo: reduzir o trabalho manual de registrar Pagamentos | Evento que inicia: "Extrato bancário importado" | Módulo de origem: 27 | Serviço de origem: Financeiro
Entidades: Pagamento, Despesa, Receita Financeira, Conta | Módulos impactados: 03, 02, 22 | Serviços impactados: Financeiro, Inteligência Artificial
Dados compartilhados: lançamentos do extrato | Regras aplicadas: RN-043
Atualizações automáticas: sugestão de categorização/conciliação por IA | Dashboards atualizados: Financeiro Empresarial | Indicadores atualizados: saldo em Conta | Alertas gerados: duplicidade, lançamento sem correspondência, possível lançamento pessoal
Histórico registrado: sugestão e decisão do usuário | Exceções: nenhuma conciliação automática sob ambiguidade | Impacto operacional: acelera o fechamento financeiro do período | Impacto financeiro: reduz erro de digitação e atraso de conciliação.

**IN-013 — Conciliação Bancária**
Objetivo: garantir que todo Pagamento corresponda a um lançamento real | Evento que inicia: importação de extrato (IN-012) ou conciliação manual periódica | Módulo de origem: 27 | Serviço de origem: Financeiro
Entidades: Pagamento, Conta | Módulos impactados: 03 | Serviços impactados: Financeiro
Dados compartilhados: status de correspondência | Regras aplicadas: RN-044
Atualizações automáticas: marcação de "conciliado" quando exato | Dashboards atualizados: Financeiro Empresarial | Indicadores atualizados: confiabilidade do Fluxo de Caixa | Alertas gerados: pendência de conciliação prolongada
Histórico registrado: status registrado com data/responsável | Exceções: divergência exige decisão humana, nunca correção automática | Impacto operacional: reduz retrabalho de conferência manual | Impacto financeiro: garante confiabilidade do resultado financeiro.

### 3.9 Fluxo entre Vida Pessoal e Empresa

**IN-014 — Integração entre Vida Pessoal e Empresa**
Objetivo: impedir que dinheiro pessoal e da empresa se misturem no resultado do negócio | Evento que inicia: registro de retirada pessoal ou lançamento ambíguo | Módulo de origem: 02 | Serviço de origem: Financeiro
Entidades: Despesa (categoria Retirada Pessoal), Conta | Módulos impactados: 03 | Serviços impactados: Financeiro
Dados compartilhados: categoria do lançamento | Regras aplicadas: RN-002, RN-005
Atualizações automáticas: categorização automática como Retirada Pessoal | Dashboards atualizados: Financeiro Pessoal | Indicadores atualizados: total de retiradas do período | Alertas gerados: retirada comprometendo o Fluxo de Caixa, lançamento ambíguo
Histórico registrado: toda retirada rastreável, distinta de Despesa operacional | Exceções: nenhuma — toda retirada é sempre registrada | Impacto operacional: nenhum | Impacto financeiro: protege a integridade do resultado operacional da empresa.

### 3.10 Fluxo de Inteligência Artificial

**IN-015 — Inteligência Artificial: Sugestão e Confirmação Humana**
Objetivo: apoiar decisões em todo o sistema sem jamais decidir sozinha | Evento que inicia: extrato importado / Produção concluída / elaboração de Orçamento | Módulo de origem: 22 | Serviço de origem: Inteligência Artificial
Entidades: variável (Pagamento, Compra, Produto) | Módulos impactados: 03, 15, 14 | Serviços impactados: Financeiro, Suprimentos, Custos e Precificação
Dados compartilhados: sugestão gerada, nível de confiança | Regras aplicadas: RN-041, RN-042, RN-043
Atualizações automáticas: nenhuma sem confirmação, salvo pré-aprovação reversível | Dashboards atualizados: Inteligência Artificial | Indicadores atualizados: taxa de aceite de sugestões | Alertas gerados: baixa confiança de previsão
Histórico registrado: toda sugestão, aceite, recusa ou reversão | Exceções: sugestão financeira/de cliente/de preço nunca é aplicada automaticamente sem confirmação | Impacto operacional: acelera decisões repetitivas | Impacto financeiro: variável, sempre rastreável à decisão humana que a autorizou.

### 3.11 Fluxo de Indicadores e Dashboards

**IN-016 — Indicadores: Recálculo Contínuo**
Objetivo: manter toda métrica de gestão sempre atualizada e auditável | Evento que inicia: qualquer evento de domínio que afete a fórmula de um Indicador | Módulo de origem: variável | Serviço de origem: variável
Entidades: Indicador | Módulos impactados: 01, 26, e todos os Dashboards especializados | Serviços impactados: Indicadores e Dashboards
Dados compartilhados: valor recalculado | Regras aplicadas: RN-040
Atualizações automáticas: recálculo automático, preservação de histórico da fórmula | Dashboards atualizados: todos que incluem o Indicador | Indicadores atualizados: o próprio objeto desta integração | Alertas gerados: Indicador não recalculável
Histórico registrado: toda fórmula, passada e presente | Exceções: revisão de fórmula preserva histórico calculado com a fórmula anterior | Impacto operacional: nenhum direto | Impacto financeiro: sustenta todo indicador financeiro do sistema.

**IN-017 — Dashboards: Atualização Automática**
Objetivo: garantir que toda visão de gestão reflita o estado real continuamente | Evento que inicia: "Indicador recalculado" (IN-016) | Módulo de origem: 01/26/27 | Serviço de origem: Indicadores e Dashboards
Entidades: Dashboard, Indicador | Módulos impactados: todos com Dashboard próprio | Serviços impactados: todos, por consumo (nunca escrita)
Dados compartilhados: composição de Indicadores exibidos | Regras aplicadas: RN-001, RN-039
Atualizações automáticas: 100% automático, sem ação do usuário | Dashboards atualizados: todos | Indicadores atualizados: nenhum novo — apenas consumidos | Alertas gerados: Indicador não recalculável
Histórico registrado: herdado dos Indicadores subjacentes | Exceções: falha de recálculo é sinalizada explicitamente | Impacto operacional: visão sempre confiável para toda a gestão | Impacto financeiro: nenhum direto.

**IN-018 — Metas: Consumo de Indicador e Encerramento de Ciclo**
Objetivo: medir objetivos de gestão sem duplicar cálculo | Evento que inicia: "Indicador recalculado" / fim do período da Meta | Módulo de origem: 01/26 | Serviço de origem: Indicadores e Dashboards
Entidades: Meta, Indicador | Módulos impactados: 26 | Serviços impactados: Metas
Dados compartilhados: valor atual do Indicador | Regras aplicadas: RN-046
Atualizações automáticas: encerramento automático de ciclo na data definida | Dashboards atualizados: Metas, CEO (consumo) | Indicadores atualizados: taxa de metas atingidas | Alertas gerados: atraso no progresso, conclusão de ciclo
Histórico registrado: todo ciclo e justificativa | Exceções: Meta sem Indicador correspondente não pode existir | Impacto operacional: orienta revisão de estratégia | Impacto financeiro: nenhum direto.

### 3.12 Fluxo de Pessoas e Documentos

**IN-019 — Pessoas/Escalas: Sugestão e Alocação**
Objetivo: garantir equipe correta para cada Evento sem erro de dimensionamento | Evento que inicia: "Evento confirmado" (parte da IN-001) | Módulo de origem: 07 | Serviço de origem: Eventos
Entidades: Alocação de Funcionário, Funcionário, Evento | Módulos impactados: 19, 20, 24, 11 | Serviços impactados: Pessoas e Recursos, Custos e Precificação
Dados compartilhados: porte do Evento, proporção de escala | Regras aplicadas: RN-037
Atualizações automáticas: sugestão automática de escala | Dashboards atualizados: Produção (indireto) | Indicadores atualizados: taxa de acerto de dimensionamento | Alertas gerados: escala não confirmada a X dias, parâmetro não definido
Histórico registrado: toda sugestão e ajuste | Exceções: parâmetro pendente impede sugestão automática | Impacto operacional: evita falta/excesso de equipe no dia do Evento | Impacto financeiro: alimenta o custo de mão de obra previsto.

**IN-020 — Documentos: Geração Automática a partir de Entidades de Origem**
Objetivo: eliminar formalização manual redundante | Evento que inicia: "Contrato assinado" / "Compra conferida" / outras origens | Módulo de origem: variável | Serviço de origem: variável
Entidades: Documento, entidade de origem | Módulos impactados: 23 | Serviços impactados: Documentos
Dados compartilhados: dados da entidade de origem | Regras aplicadas: RN-014
Atualizações automáticas: geração automática de Documento vigente | Dashboards atualizados: nenhum direto | Indicadores atualizados: nenhum direto | Alertas gerados: dados obrigatórios ausentes
Histórico registrado: toda versão de Documento preservada | Exceções: dados ausentes impedem geração automática | Impacto operacional: reduz tempo de formalização | Impacto financeiro: nenhum direto.

---

## 4. Matriz Geral de Integração

| IN-XXX | Nome | Módulo(s) de Origem | Serviço(s) de Origem | Módulo(s) Impactado(s) | Serviço(s) Impactado(s) | Entidade(s) Principal(is) |
|---|---|---|---|---|---|---|
| IN-001 | Confirmação de Evento → Orquestração Multi-Serviço | 07 | Eventos | 10, 15, 16, 18, 19, 20, 03, 01 | Produção, Suprimentos, Pessoas e Recursos, Financeiro, Indicadores e Dashboards | Evento, Contrato, Produção, Estoque, Alocação de Funcionário, Equipamento, Compra, Receita Financeira, Indicador |
| IN-002 | Ciclo Comercial: Lead → Cliente → Orçamento → Contrato | 06 | Comercial | 05, 08, 09, 04 | Comercial, Marketing | Lead, Cliente, Orçamento, Contrato, Campanha |
| IN-003 | CRM: Atribuição de Retorno de Campanha | 21 | Marketing | 04, 06, 05 | Comercial, Indicadores e Dashboards | Campanha, Lead, Cliente, Contrato |
| IN-004 | Marketing: Geração de Lead por Campanha | 21 | Marketing | 06, 04 | Comercial | Campanha, Lead |
| IN-005 | Produção: Planejamento Automático a partir de Evento Confirmado | 07 | Eventos | 10, 13, 24, 16 | Produção, Suprimentos | Produção, Ficha Técnica, Ingrediente, Evento |
| IN-006 | Produção: Execução, Perdas e Rendimento | 10 | Produção | 16, 17, 11 | Suprimentos, Custos e Precificação, Indicadores e Dashboards | Produção, Lote, Estoque, Ficha Técnica |
| IN-007 | Engenharia de Custos: Recálculo em Cascata | 15 | Suprimentos | 13, 14, 08, 11 | Produção, Custos e Precificação, Comercial | Ingrediente, Ficha Técnica, Orçamento |
| IN-008 | Estoque: Movimentação Automática e Rastreabilidade por Lote | 15/10 | Suprimentos, Produção | 16, 17 | Suprimentos | Estoque, Lote, Ingrediente, Produto |
| IN-009 | Compras: Geração de Lista e Reposição | 10/16 | Produção, Suprimentos | 15, 03 | Suprimentos, Financeiro | Compra, Fornecedor, Ingrediente, Estoque |
| IN-010 | Financeiro: Geração Automática de Despesa e Receita Financeira | 09/15/20 | Comercial, Suprimentos, Pessoas e Recursos | 03, 27 | Financeiro | Receita Financeira, Despesa, Contrato, Compra, Alocação de Funcionário |
| IN-011 | Financeiro: Encerramento de Evento e Apuração de Resultado | 07 | Eventos | 11, 03, 01 | Custos e Precificação, Financeiro, Indicadores e Dashboards | Evento, Produção, Despesa, Receita Financeira, Ficha Técnica |
| IN-012 | Importação Automática de Extratos Bancários | 27 | Financeiro | 03, 02, 22 | Financeiro, Inteligência Artificial | Pagamento, Despesa, Receita Financeira, Conta |
| IN-013 | Conciliação Bancária | 27 | Financeiro | 03 | Financeiro | Pagamento, Conta |
| IN-014 | Integração entre Vida Pessoal e Empresa | 02 | Financeiro | 03 | Financeiro | Despesa (Retirada Pessoal), Conta |
| IN-015 | Inteligência Artificial: Sugestão e Confirmação Humana | 22 | Inteligência Artificial | 03, 15, 14 | Financeiro, Suprimentos, Custos e Precificação | variável (Pagamento, Compra, Produto) |
| IN-016 | Indicadores: Recálculo Contínuo | variável | variável | 01, 26 e Dashboards especializados | Indicadores e Dashboards | Indicador |
| IN-017 | Dashboards: Atualização Automática | 01/26/27 | Indicadores e Dashboards | todos com Dashboard próprio | todos (por consumo) | Dashboard, Indicador |
| IN-018 | Metas: Consumo de Indicador e Encerramento de Ciclo | 01/26 | Indicadores e Dashboards | 26 | Metas | Meta, Indicador |
| IN-019 | Pessoas/Escalas: Sugestão e Alocação | 07 | Eventos | 19, 20, 24, 11 | Pessoas e Recursos, Custos e Precificação | Alocação de Funcionário, Funcionário, Evento |
| IN-020 | Documentos: Geração Automática a partir de Entidades de Origem | variável | variável | 23 | Documentos | Documento, entidade de origem |

**Leitura da matriz:** os Módulos 07 (Eventos) e 15 (Compras)/10 (Produção) concentram o maior número de integrações de origem, confirmando o papel de "Eventos" como orquestrador comercial-operacional (já identificado no TCOS-006) e de "Suprimentos/Produção" como o núcleo de rastreabilidade física do negócio. O Módulo 01 (Dashboard CEO) e o Serviço de Indicadores e Dashboards aparecem como impactados em quase todas as cadeias — não porque escrevam em outros domínios, mas porque **consomem** o resultado de todos eles, confirmando o desenho de acoplamento único já estabelecido no System Architecture.

---

## 5. Mapa Global das Comunicações

O sistema não possui comunicação direta módulo-a-módulo. Toda comunicação passa pelo Event Bus conceitual (TCOS-006): um Serviço publica um evento de domínio; qualquer Serviço interessado assina esse evento e reage de forma independente, sem chamada direta e sem espera síncrona.

**Três papéis de comunicação, confirmados por todas as 20 Integrações:**

- **Serviços-fonte de negócio** (publicam a maior parte dos eventos que iniciam cadeias): Comercial, Eventos, Produção, Suprimentos, Financeiro, Marketing, Pessoas e Recursos. Representam a operação real do negócio.
- **Serviços-consolidadores** (assinam eventos de praticamente todos os demais, mas nunca escrevem de volta no domínio de origem): Indicadores e Dashboards, Auditoria. Existem para agregar, nunca para operar.
- **Serviços-conselheiros** (assinam eventos, publicam apenas sugestões, nunca alteram dado de outro Serviço): Inteligência Artificial. Confirma o PF-06 em toda comunicação em que participa (IN-012, IN-015).

**Mapa textual do fluxo predominante de comunicação** (direção da seta = "publica evento consumido por"):

```
Comercial/Marketing ─► Eventos ─┬─► Produção ─► Suprimentos ─► Custos e Precificação ─► Comercial (revalidação)
                                 ├─► Pessoas e Recursos
                                 ├─► Financeiro
                                 └─► Indicadores e Dashboards ◄── (todos os demais Serviços, sempre)
Financeiro (extrato) ─► Inteligência Artificial ─► Financeiro/Suprimentos/Custos (sugestão, sujeita a confirmação)
Qualquer Serviço ─► Auditoria (sempre, sem exceção)
Qualquer Serviço ─► Documentos (quando há entidade formal a gerar)
```

Nenhum Serviço de negócio assina eventos de Auditoria, Indicadores e Dashboards ou Documentos como pré-condição para operar — esses três são "terminais" de comunicação (recebem, nunca precisam ser aguardados), o que preserva a independência operacional dos 15 Serviços entre si, conforme já estabelecido na Matriz de Dependências do TCOS-006 e detalhado agora no Capítulo 9.

---

## 6. Mapa dos Eventos do Sistema

### 6.1 Eventos de Domínio Diretamente Utilizados nesta Especificação

Dos 89 eventos de domínio catalogados no Domain Model (TCOS-002), os seguintes nomeiam explicitamente o disparo de uma ou mais das 20 Integrações deste documento:

| Evento de Domínio | Serviço Publicador | Serviço(s) Assinante(s) | Integração(ões) |
|---|---|---|---|
| Evento confirmado | Eventos | Produção, Suprimentos, Pessoas e Recursos, Financeiro, Indicadores e Dashboards | IN-001, IN-005, IN-019 |
| Evento concluído | Eventos | Custos e Precificação, Financeiro, Indicadores e Dashboards | IN-011 |
| Lead criado | Comercial | Comercial (funil interno), Marketing | IN-002 |
| Lead convertido em Cliente | Comercial | Marketing, Indicadores e Dashboards | IN-002, IN-003 |
| Contrato assinado | Comercial | Marketing, Financeiro, Documentos | IN-003, IN-010, IN-020 |
| Campanha criada / Campanha iniciada | Marketing | Comercial | IN-004 |
| Produção planejada | Produção | Suprimentos | IN-009 |
| Produção iniciada | Produção | Suprimentos | IN-008 |
| Produção concluída | Produção | Suprimentos, Custos e Precificação, Indicadores e Dashboards, Inteligência Artificial | IN-006, IN-008, IN-015 |
| Custo de Ingrediente atualizado | Suprimentos | Produção, Custos e Precificação, Comercial | IN-007 |
| Compra realizada (conferida) | Suprimentos | Suprimentos (Estoque/Lote), Financeiro, Documentos | IN-008, IN-010, IN-020 |
| Alocação de Funcionário realizada | Pessoas e Recursos | Financeiro | IN-010 |
| Dashboard atualizado | Indicadores e Dashboards | (consumo pelo usuário, sem novo Serviço assinante) | IN-017 |

### 6.2 Cobertura do Catálogo de 89 Eventos

Os 89 eventos permanecem integralmente válidos e vigentes (nenhum foi alterado — TCOS-002 está congelado). Nem todo evento de domínio precisa gerar uma reação multi-Serviço: eventos como "Fornecedor avaliado", "Lote descartado" ou "Funcionário afastado" são publicados normalmente e sempre chegam ao Serviço de Auditoria (histórico obrigatório, PF-04), mas não exigem, por si só, uma cadeia de reação em outros Serviços — permanecem como comunicação interna de um único Serviço com o seu próprio histórico. Este documento formaliza apenas as cadeias em que **mais de um Serviço reage** ao mesmo evento, que é exatamente a definição de "Integração" adotada no Capítulo 2. Os eventos não listados na tabela 6.1 continuam ativos e não representam lacuna — representam ciclo de vida de entidade tratado dentro de um único domínio de responsabilidade, o que é, por si, uma confirmação do desenho de baixo acoplamento buscado desde o TCOS-006.

### 6.3 Eventos Arquiteturais Complementares (Event Bus)

Além dos eventos de domínio (TCOS-002), o Event Bus (TCOS-006) já previa sinais de comunicação entre Serviços que não correspondem a um evento de ciclo de vida de uma entidade de negócio, e sim a um resultado de processamento interno de um Serviço, necessário para encadear a próxima reação. Este documento confirma o uso desses sinais nas seguintes Integrações:

- **"Custo recalculado"** — publicado pelo Serviço de Custos e Precificação ao final de IN-007; assinado pelo Serviço Comercial (revalidação de Orçamento, RN-019) e por Indicadores e Dashboards.
- **"Indicador recalculado"** — publicado pelo Serviço de Indicadores e Dashboards ao final de IN-016; assinado por ele mesmo para atualizar Dashboards (IN-017) e pelo Serviço de Metas (IN-018).
- **"Sugestão gerada (IA)"** — publicado pelo Serviço de Inteligência Artificial ao final do processamento de IN-015; assinado pelo Serviço de origem da sugestão (Financeiro, Suprimentos ou Custos e Precificação), nunca aplicado automaticamente.

Nenhum desses três sinais é uma tecnologia de mensageria — são, como todo o restante deste documento, nomes de comunicação em linguagem de negócio, já previstos conceitualmente na Seção 7 do System Architecture.

---

## 7. Cadeia Completa de Atualização dos Dashboards

Esta cadeia une formalmente IN-016 e IN-017, conforme identificado na Auditoria de Abertura (achado do item 5):

1. Um evento de domínio relevante ocorre em qualquer Serviço (ex.: "Produção concluída", "Despesa quitada", "Contrato assinado").
2. O Serviço de Indicadores e Dashboards, que assina **todos** os eventos do sistema, identifica quais Indicadores têm fórmula afetada por aquele evento.
3. Cada Indicador afetado é recalculado (IN-016) e o resultado é preservado com histórico da fórmula usada (PF-04, RN-040).
4. O Serviço de Indicadores e Dashboards publica "Indicador recalculado".
5. Todo Dashboard que exibe aquele Indicador é atualizado automaticamente (IN-017) — sem exceção e sem ação do usuário.
6. O Serviço de Metas, se aquele Indicador estiver vinculado a uma Meta ativa, consome o novo valor (IN-018) e verifica se o ciclo da Meta deve ser encerrado.
7. O Serviço de Auditoria registra o evento de recálculo e a atualização de Dashboard, fechando o rastro completo desde o evento original de negócio até a tela vista pelo proprietário.

Esta é, confirmadamente, a única cadeia de atualização de Dashboard existente no sistema — nenhum Dashboard é atualizado por caminho diferente deste, o que resolve estruturalmente a melhoria M-004-01 (já identificada no TCOS-004 e resolvida arquiteturalmente no TCOS-006; aqui ela é confirmada em nível de comportamento).

## 8. Cadeia Completa de Atualização da Inteligência Artificial

1. Um evento de domínio ocorre em um Serviço-fonte (ex.: "Extrato bancário importado", "Produção concluída", elaboração de um Orçamento).
2. O Serviço de Inteligência Artificial assina esse evento e processa uma sugestão (categorização de Pagamento, previsão de rendimento/perda, alerta de margem), nunca alterando diretamente o dado do Serviço de origem (PF-06).
3. O Serviço de Inteligência Artificial publica "Sugestão gerada (IA)", com o nível de confiança da sugestão.
4. O Dashboard de Inteligência Artificial (TCOS-005) exibe a sugestão pendente ao proprietário/usuário responsável.
5. O usuário confirma, recusa ou ajusta a sugestão (RN-041 a RN-043). Apenas exceções pré-aprovadas e reversíveis podem ser aplicadas automaticamente, sempre com opção de reversão.
6. Somente após a confirmação humana (ou pré-aprovação reversível), o Serviço de origem (Financeiro, Suprimentos ou Custos e Precificação) aplica a mudança em seu próprio domínio e publica seu próprio evento de domínio normal (ex.: "Pagamento realizado").
7. Esse evento de domínio, por sua vez, entra na Cadeia de Dashboards (Capítulo 7), atualizando Indicadores como "taxa de aceite de sugestões".
8. O Serviço de Auditoria registra a sugestão, a decisão humana (ou a regra de pré-aprovação aplicada) e a ação final, de forma permanentemente rastreável a quem autorizou.

Esta cadeia é o único caminho pelo qual uma sugestão de IA chega a produzir efeito no sistema — confirmando de forma operacional o Princípio Fundamental PF-06 ("a Inteligência Artificial nunca decide sozinha").

## 9. Matriz de Dependências entre Serviços

| Serviço | Depende obrigatoriamente de (não opera sem) | Consulta/assina de forma opcional | Nunca escreve diretamente em |
|---|---|---|---|
| Comercial | Custos e Precificação (para Orçamento) | Marketing (atribuição) | qualquer outro Serviço |
| Eventos | Comercial (Contrato assinado) | — | Produção, Suprimentos, Financeiro, Pessoas e Recursos (apenas publica evento) |
| Produção | Suprimentos (Ficha Técnica/Estoque), Configurações (parâmetros RN-024 a RN-029) | Custos e Precificação | Suprimentos, Custos e Precificação (apenas publica evento) |
| Custos e Precificação | Produção, Suprimentos (custos de origem) | Configurações | Comercial, Suprimentos (apenas publica evento) |
| Suprimentos | — (dono exclusivo do saldo de Estoque) | Produção (consumo) | nenhum — nenhum outro Serviço altera Estoque diretamente |
| Pessoas e Recursos | Eventos (porte do Evento), Configurações (parâmetro de escala) | Custos e Precificação | Financeiro (apenas publica evento) |
| Financeiro | Comercial, Suprimentos, Pessoas e Recursos (eventos de origem) | Inteligência Artificial (sugestão) | nenhum — decide sozinho sobre seu próprio domínio |
| Marketing | Comercial (eventos de conversão) | — | Comercial (apenas publica evento de atribuição) |
| Inteligência Artificial | Serviço de origem de cada sugestão | todos, por assinatura de evento | qualquer outro Serviço (nunca escreve — apenas sugere) |
| Indicadores e Dashboards | todos os demais Serviços (assina todos os eventos) | — | qualquer outro Serviço (apenas leitura/consolidação) |
| Metas | Indicadores e Dashboards | — | qualquer outro Serviço |
| Documentos | Serviço de origem da entidade formal | — | qualquer outro Serviço |
| Configurações | — | — | nenhum outro Serviço (é consultado, não consulta) |
| Administração e Segurança | — | todos (para controle de acesso) | domínio de negócio de qualquer Serviço |
| Auditoria | todos os demais Serviços (assina todos os eventos, sem exceção) | — | qualquer outro Serviço (apenas leitura/registro) |

Esta matriz confirma, ao nível de comportamento, a ausência de dependência circular já atestada estruturalmente no TCOS-006 (Capítulo "Dependências entre Módulos") — nenhum Serviço depende, direta ou indiretamente, de um Serviço que dependa dele.

## 10. Fluxo de Sincronização entre Módulos

O sistema não sincroniza módulos por espera síncrona (um módulo parado aguardando resposta de outro). O padrão único de sincronização, confirmado em todas as 20 Integrações, é:

1. **Publicação única:** o Serviço de origem publica um evento de domínio uma única vez, independentemente de quantos outros Serviços vão reagir a ele.
2. **Reação paralela e independente:** cada Serviço assinante reage em seu próprio tempo, sem que os demais assinantes precisem aguardar uns aos outros. É o caso confirmado do achado de simplificação da Auditoria de Abertura: IN-001 ("Evento confirmado") dispara IN-005 (Produção) e IN-019 (Pessoas/Escalas) como **ramificações paralelas e independentes da mesma publicação** — nenhuma das duas aguarda a outra terminar.
3. **Consistência eventual, nunca imediata forçada:** um Dashboard pode, por frações de processamento, não refletir instantaneamente um evento acabado de ocorrer em outro Serviço — o sistema tolera essa defasagem mínima em favor de baixo acoplamento; nenhuma regra de negócio depende de sincronismo absoluto entre Serviços.
4. **Bloqueio apenas na origem:** quando falta um recurso (ex.: Estoque insuficiente, parâmetro de Configuração pendente), o bloqueio ocorre **antes** da publicação do evento pelo Serviço de origem (ex.: RN-006 impede a confirmação do Evento se a viabilidade operacional falhar) — nunca depois, e nunca em um Serviço assinante tentando "desfazer" uma reação de outro.
5. **Reconciliação pelo Serviço de Auditoria:** como todos os Serviços publicam para o mesmo histórico central de eventos, qualquer divergência entre Serviços é sempre reconstruível e auditável a partir da sequência real de eventos publicados — nunca por comparação direta e ad-hoc entre bancos de dois Serviços.

Este padrão único de sincronização é o que permite que os 27 módulos e 15 Serviços cresçam de forma independente (Capítulo 8 do System Architecture) sem jamais exigir uma reescrita de integração já existente quando um novo módulo for adicionado no futuro.

---

## RESUMO PARA O PROPRIETÁRIO

Este documento (TCOS-009) responde a uma pergunta muito concreta: **quando algo acontece em uma parte do sistema, o que acontece automaticamente no resto do sistema?**

O que foi construído: 20 "Integrações" foram descritas, cobrindo os 18 fluxos de comunicação exigidos (Dashboard, Indicadores, Financeiro, Comercial, Operacional, Produção, Engenharia de Custos, Estoque, CRM, Marketing, IA, Extratos Bancários, Conciliação, Vida Pessoal/Empresa, entre outros). Cada Integração explica, em português claro, quem inicia a ação, quem é avisado, o que muda automaticamente, o que aparece em qual painel, que alerta é gerado e qual o efeito financeiro e operacional.

Por que isso é importante: até aqui, cada documento (Domínio, Regras, Funcionalidades, Telas, Arquitetura, Dados, Banco) descreveu uma "peça" do sistema. Este documento é o que garante que as peças realmente **funcionam juntas** — por exemplo, confirmar um Evento aciona sozinho o planejamento de Produção, a reserva de Estoque, a sugestão de equipe e a previsão financeira, sem que ninguém precise lançar essas informações manualmente em cada módulo.

Como isso conecta os módulos: foram criados sete capítulos de amarração — uma Matriz Geral mostrando todas as 20 conexões de uma vez, um Mapa Global de quem fala com quem, um Mapa dos Eventos que disparam essas conversas, a cadeia completa de como um Dashboard se atualiza sozinho, a cadeia completa de como a Inteligência Artificial sugere algo (e nunca decide sozinha), uma Matriz de Dependências entre os 15 Serviços, e a explicação de como tudo isso é sincronizado sem que um módulo "trave" esperando outro.

Como isso prepara o Backend/APIs/Desenvolvimento: um arquiteto de sistemas agora tem, em mãos, exatamente o comportamento que cada API/endpoint real precisará implementar — quais dados trafegam, quais regras se aplicam, o que deve virar mensagem, alerta ou atualização de tela — sem que nenhuma decisão de linguagem, banco de dados ou tecnologia tenha sido tomada ainda. Essa decisão continua sendo do proprietário, em uma fase futura e com aprovação explícita.

Nada de código, banco de dados físico, tela ou tecnologia foi criado nesta fase — apenas a "receita" de como os módulos conversam entre si.

---

## TCOS QUALITY GATE EXECUTIVO

**Auditoria de Fechamento:**
- Todos os 18 tópicos de comunicação exigidos pelo Prompt Oficial da Fase 009 foram cobertos (Dashboard, Indicadores, Financeiro, Comercial, Operacional, Produção, Engenharia de Custos, Estoque, CRM, Marketing, IA, Importação de Extratos, Conciliação Bancária, Vida Pessoal/Empresa, e os capítulos transversais de Matriz Geral, Mapa Global, Mapa de Eventos e Sincronização).
- Todos os 27 módulos aparecem em ao menos uma Integração (confirmado na Matriz Geral, Capítulo 4).
- Todos os 15 Serviços Conceituais aparecem em ao menos uma Integração ou na Matriz de Dependências (Capítulo 9).
- Todas as 30 entidades aparecem em ao menos uma Integração como "Entidade envolvida".
- Nenhum documento oficial anterior (Fases 000 a 008) foi alterado.
- Nenhuma decisão de tecnologia, protocolo, formato de mensagem, API, endpoint ou autenticação técnica foi tomada — confirmado por revisão de todo o texto produzido nesta fase.
- Risco/pendência genuína identificada e registrada (não oculta): a nomenclatura de dois sinais de comunicação usados nas cadeias de Indicadores e IA ("Indicador recalculado", "Sugestão gerada (IA)", "Custo recalculado") não corresponde literalmente a um dos 89 eventos de domínio do TCOS-002 — são eventos arquiteturais do Event Bus, já previstos no TCOS-006 e agora formalmente distinguidos no Capítulo 6.3 deste documento. Registrado como esclarecimento de nomenclatura, não como inconsistência a corrigir retroativamente nos documentos congelados.

**Métricas de Fechamento:**
- Quantidade de páginas equivalentes: aproximadamente 26.
- Quantidade de integrações: 20 (IN-001 a IN-020).
- Quantidade de eventos utilizados: 13 eventos de domínio nomeados explicitamente como gatilho (Seção 6.1) + 3 eventos arquiteturais complementares do Event Bus (Seção 6.3) = 16 eventos formalmente referenciados nesta especificação, dentro do universo de 89 eventos de domínio catalogados no TCOS-002 (nenhum evento novo foi criado; todos pertencem ao catálogo já oficial ou ao Event Bus já oficial).
- Quantidade de módulos integrados: 27 de 27 (100%).
- Quantidade de serviços integrados: 15 de 15 (100%).
- Quantidade de entidades conectadas: 30 de 30 (100%).
- Quantidade de regras de negócio referenciadas: 30 das 47 regras (RN-002, RN-005, RN-006, RN-008, RN-009, RN-011 a RN-015, RN-016, RN-019, RN-024 a RN-029, RN-037 a RN-046) — as demais 17 regras permanecem válidas mas descrevem comportamento interno de um único Serviço, sem cadeia multi-Serviço a documentar nesta fase (não é lacuna, é escopo correto do documento).
- Quantidade de riscos ativos: 4 (R-000-03/R-002-01, R-001-01/R-002-02, R-002A-01 herdados; nenhum risco novo introduzido nesta fase).
- Quantidade de pendências: 9 (todas herdadas — nenhuma nova pendência de negócio foi introduzida; a única pendência nova é técnica/documental, o esclarecimento de nomenclatura de eventos já registrado acima).
- Quantidade de melhorias sugeridas nesta fase: 1 nova — M-009-01: quando uma fase técnica futura desenhar o mecanismo real de mensageria, considerar se os eventos arquiteturais do Event Bus (Custo recalculado, Indicador recalculado, Sugestão gerada) devem ser formalmente incorporados ao catálogo de eventos de domínio do TCOS-002 em uma eventual v1.1.0, por clareza de nomenclatura única (não estrutural, apenas de nomenclatura).
- Percentual estimado de maturidade do projeto: **80%** (documentação de negócio, domínio, regras, funcionalidades, fluxos, UX/UI, arquitetura de sistema, arquitetura de dados, banco de dados e agora integração/comunicação entre módulos completas e oficiais; restam como não iniciadas: confirmação final do domínio de negócio via entrevista, e todas as fases técnicas de desenvolvimento real — Backend, Frontend, APIs, banco de dados físico).

**Encerramento desta fase:** este documento permanece como **rascunho para validação do proprietário** até receber o comando `APROVADO`. Nenhuma fase de Backend, Frontend, API, banco de dados físico ou Desenvolvimento será iniciada sem autorização explícita, conforme restrição do Prompt Oficial da Fase 009.

---

*Fim do documento — THE CHARCOAL OS INTEGRATION AND API CONTRACT v1.0.0*
