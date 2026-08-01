# THE CHARCOAL OS — USER JOURNEYS AND SYSTEM FLOWS

**Documento:** TCOS-004 — Jornadas do Usuário e Fluxos do Sistema
**Projeto:** THE CHARCOAL OS
**Fase:** 004 — User Journeys & System Flows
**Status:** Rascunho para validação do proprietário
**Versão:** 1.0.0

---

## EXECUTIVE MEMORY

- **Estado atual do projeto:** documentação de negócio, modelo de domínio, regras de negócio e especificação funcional completos e oficiais; iniciando a documentação operacional de como cada processo acontece do início ao fim, ainda sem nenhuma decisão técnica.
- **Fase atual:** 004 — User Journeys & System Flows (TCOS-004).
- **Fases concluídas:** 000 (Governança), 001 (Business Discovery), 001B (Questionário + Roteiro — conteúdo aprovado, entrevista não executada), 002 (Domain Model), 002A (Business Rules Specification + padrão de documentação), 003 (Functional Specification v1.2.0 — **aprovada e congelada** nesta mensagem).
- **Documentos oficiais:** `THE_CHARCOAL_OS_DEVELOPMENT_FRAMEWORK.md` (v1.2.0), `PROJECT_MEMORY.md`, `THE_CHARCOAL_OS_ENTERPRISE_DOMAIN_DISCOVERY.md` (v1.0.0), `THE_CHARCOAL_OS_BUSINESS_DISCOVERY_QUESTIONNAIRE.md` (v1.0.0), `THE_CHARCOAL_OS_DISCOVERY_INTERVIEW_ROADMAP.md` (v1.0.0), `THE_CHARCOAL_OS_DOMAIN_MODEL.md` (v1.0.0), `THE_CHARCOAL_OS_BUSINESS_RULES_SPECIFICATION.md` (v1.0.0), `THE_CHARCOAL_OS_FUNCTIONAL_SPECIFICATION.md` (v1.2.0, congelado a partir de agora).
- **Documentos em elaboração:** este documento (TCOS-004).
- **Pendências:** confirmação da hipótese de domínio de negócio (R-000-03); parâmetros de negócio do Módulo 24 (R-002A-01); M-003A-03 (cadastro explícito de Produto/Ingrediente/Fornecedor/Pacote/Indicador); M-003A-04 (Cartão como entidade própria); decisão sobre retomar a entrevista de descoberta.
- **Riscos ativos:** R-000-03/R-002-01 (crítico), R-001-01/R-002-02, R-002A-01 — todos herdados e relevantes: várias jornadas abaixo (Produção, Precificação, Escalas) dependem de parâmetros ainda não confirmados.
- **Dependências para esta fase:** as 30 entidades e Regras Globais do Domain Model; as 47 Regras de Negócio (RN-001–RN-047); os 27 módulos e 98 funcionalidades (F-001–F-098) do Functional Specification — todos referenciados por nome/número, nunca reescritos.
- **Objetivo da fase que será iniciada:** documentar, para no mínimo 30 fluxos obrigatórios, como cada processo do THE CHARCOAL OS acontece do início ao fim, em termos operacionais — sem arquitetura, banco de dados, UX ou APIs.
- **O que não pode ser alterado:** nenhum conteúdo do Framework (v1.2.0), Domain Discovery, Questionnaire, Interview Roadmap, Domain Model, Business Rules Specification ou Functional Specification (v1.2.0, agora oficial e congelada) — todos documentos aprovados e imutáveis sem nova versão própria.

### Auditoria de Abertura

Todos os documentos oficiais foram lidos integralmente. Resultado:

- **Nenhuma inconsistência ou conflito real** entre os documentos existentes.
- **Duplicidade aparente resolvida por escopo:** FL-003 (Jornada do Evento) e FL-029 (Encerramento de Evento) — FL-003 é a visão de ciclo de vida completo; FL-029 é o detalhamento (zoom) do momento de encerramento, explicitamente solicitado em separado pelo Prompt Oficial. Da mesma forma, FL-021 (Dashboards), FL-026 (Atualização de Dashboards), FL-027 (Atualização do Dashboard CEO) e FL-028 (Atualização de Indicadores) descrevem o mesmo mecanismo contínuo em quatro recortes diferentes, todos explicitamente solicitados — tratados como fluxos distintos, mas referenciando-se mutuamente para evitar repetição de conteúdo.
- **Funcionalidades órfãs:** nenhuma real. F-080, F-081, F-083 (Módulo 25 — Administração do Sistema) e F-072 a F-074 (Módulo 23 — Documentos) não possuem uma "jornada" própria entre os 30 fluxos obrigatórios — são, por natureza, transversais (gestão de acesso, log de auditoria, geração de documentos como subproduto de outras jornadas), consumidos ao longo de todas as jornadas de negócio, nunca jornadas de negócio autônomas. Isso é esperado, não um gap.
- **Entidades sem fluxo dedicado:** Documento (Módulo 23) segue a mesma lógica transversal acima. Produto, Ingrediente, Pacote e Indicador — já registrados como cobertura "Parcial" no TCOS-003 (gap M-003A-03, ainda aberto) — aparecem dentro de fluxos de outras entidades (Produção, Compras, Orçamento, Dashboards), mas não como jornada própria nomeada, consistente com o gap já conhecido.
- **Regras sem fluxo dedicado:** RN-004 (Fechamento de Período) e RN-047 (Tratamento Padrão de Alerta) não têm uma jornada própria nesta lista de 30 — são processos periódicos/administrativos, não jornadas iniciadas por um evento de negócio específico. Referenciados dentro de outras jornadas (FL-006, todas as jornadas quanto a alertas).
- **Módulos sem integração:** nenhum — todos os 27 módulos aparecem em ao menos uma jornada ou na Matriz de Integração (Seção 4).
- **Dependências circulares:** nenhuma encontrada. O grafo de dependências entre módulos (Seção 4) é acíclico e segue a mesma Cadeia de Valor já registrada no Domain Discovery (Seção 4) e no Domain Model.
- **Oportunidade de simplificação registrada:** FL-026, FL-027 e FL-028 são, do ponto de vista de negócio, um único mecanismo contínuo de recálculo — mantidos como fluxos separados por exigência explícita do Prompt Oficial desta fase, mas recomenda-se, em fase técnica futura, um único motor de recálculo (não três implementações paralelas).
- **Gap herdado reforçado:** a jornada de Pós-venda (FL-030) é sustentada apenas por RN-010 (Fidelização) e F-014 (Consultar Histórico do Cliente) — não há Regra de Negócio nem funcionalidade dedicada a contato estruturado, registro de feedback/reclamação ou geração formal de indicação. Isso é consistente com as perguntas Q79–Q81 do Business Discovery, ainda sem resposta, e fica registrado, não inventado.
- Nenhuma decisão técnica foi tomada neste documento, em conformidade com a restrição explícita da fase.

---

## 1. Papel deste Documento

O Domain Model definiu o que cada entidade é. O Business Rules Specification definiu o que o sistema faz automaticamente. O Functional Specification definiu o que o usuário consegue fazer. Este documento (TCOS-004) conecta tudo isso no tempo: como cada processo de negócio acontece, passo a passo, do evento que o inicia ao resultado final — em linguagem operacional, sem arquitetura, banco de dados, UX ou tecnologia.

## 2. Legenda e Convenções

- **FL-XXX:** identificador único de Fluxo, numerado sequencialmente pela ordem solicitada no Prompt Oficial.
- Toda referência a Regra de Negócio (RN-XXX), Funcionalidade (F-XXX), Módulo ou Entidade usa exatamente os nomes/números já oficiais — nenhum é redefinido aqui.
- Cada fluxo é apresentado em formato compacto: um bloco de contexto (campos 2–8), uma sequência numerada (campo 9), um bloco de decisões/exceções (campo 10–13) e um bloco de resultado (campos 14–19).

---

## 3. Fluxos

### FL-001 — Jornada Completa do Lead

**Objetivo:** acompanhar o Lead da captação até a conversão ou perda. | **Evento inicial:** "Lead criado" (RN-008). | **Pré-requisitos:** Campanha (opcional) já cadastrada. | **Participantes:** Comercial/CRM, Marketing. | **Módulos:** 06, 04, 21. | **Entidades:** Lead, Campanha, Cliente. | **Regras aplicadas:** RN-008, RN-009, RN-011, RN-038.

**Sequência:**
1. Lead chega (Campanha, indicação, contato espontâneo) → F-016, origem registrada (RN-008).
2. Comercial qualifica → F-017, Lead "Em qualificação".
3. Sistema monitora inatividade → RN-011 sugere perda se aplicável.
4. Comercial decide: converter (F-018, RN-009, checagem de duplicidade) ou marcar como perdido (F-019).
5. Se convertido, retorno de Campanha é atribuído (RN-038, F-012).

**Decisões possíveis:** qualificar, converter, marcar como perdido, manter em prospecção. | **Exceções:** correspondência ambígua na conversão exige confirmação humana; Lead perdido não reabre automaticamente. | **Alertas:** Lead inativo há X dias. | **Automações:** atribuição de origem; sugestão de perda.

**Dados gerados:** Lead, vínculo com Campanha. | **Dados atualizados:** Cliente (se convertido). | **Indicadores impactados:** taxa de conversão, custo de aquisição. | **Dashboards atualizados:** CRM, Dashboard CEO (indireto). | **Auditoria:** origem imutável; toda decisão registrada. | **Resultado final:** Lead convertido em Cliente ativo, ou perdido com histórico preservado.

### FL-002 — Jornada Completa do Cliente

**Objetivo:** acompanhar o relacionamento do Cliente do cadastro à fidelização/inatividade. | **Evento inicial:** "Cliente criado". | **Pré-requisitos:** nenhum. | **Participantes:** Comercial/CRM, Financeiro, Eventos/Operações. | **Módulos:** 05, 07, 08, 09, 03. | **Entidades:** Cliente, Evento, Orçamento, Contrato, Receita Financeira. | **Regras aplicadas:** RN-009, RN-010.

**Sequência:**
1. Cliente cadastrado (F-013), direto ou por conversão de Lead.
2. Cliente solicita Evento → jornada FL-003 se inicia, vinculada ao Cliente.
3. A cada Evento concluído, sistema verifica critério de fidelização (RN-010).
4. Histórico consolidado disponível a qualquer momento (F-014).
5. Se necessário, Cliente é inativado (F-015).

**Decisões possíveis:** manter ativo, inativar, reativar. | **Exceções:** Cliente inativo não recebe novo Orçamento sem reativação. | **Alertas:** herdados dos Eventos associados. | **Automações:** marcação automática de fidelização.

**Dados gerados:** nenhum além do cadastro inicial. | **Dados atualizados:** Cliente (histórico, fidelização, status). | **Indicadores impactados:** número de Clientes ativos, taxa de fidelização. | **Dashboards atualizados:** CRM, Dashboard CEO. | **Auditoria:** histórico nunca excluído. | **Resultado final:** relacionamento contínuo e rastreável do primeiro contato à recorrência.

### FL-003 — Jornada Completa do Evento

**Objetivo:** coordenar o ciclo de vida completo de um Evento, do registro à conclusão (ver FL-029 para o detalhamento do encerramento). | **Evento inicial:** "Evento registrado" (F-020). | **Pré-requisitos:** Cliente/Lead identificado. | **Participantes:** Comercial/CRM, Eventos/Operações, Produção, Financeiro, Pessoas/Mão de Obra. | **Módulos:** 07, 08, 09, 10, 15, 16, 18, 19, 20, 03. | **Entidades:** Evento, Cliente, Orçamento, Contrato, Produção, Estoque, Equipamento, Alocação de Funcionário, Receita Financeira, Despesa. | **Regras aplicadas:** RN-006, RN-007, RN-003, RN-017.

**Sequência:**
1. Evento registrado (F-020), "Prospectado".
2. Orçamento elaborado e vinculado → jornada FL-004.
3. Orçamento aceito → Contrato gerado e assinado → jornada FL-005; Evento passa a "Confirmado".
4. Confirmação dispara orquestração completa (RN-006, F-021): Produção planejada, Estoque reservado, Escala sugerida, Compras sugeridas, previsão financeira atualizada, Dashboards atualizados.
5. Planejamento operacional é revisado/ajustado por humanos (F-022).
6. Evento é executado; Produção é realizada (jornada FL-007).
7. Evento é concluído (F-023) → jornada FL-029.
8. Alternativamente, Evento é cancelado em qualquer ponto após a confirmação (F-024, RN-007).

**Decisões possíveis:** confirmar, ajustar planejamento, concluir, cancelar. | **Exceções:** inviabilidade operacional bloqueia a confirmação; política de cancelamento não formalizada exige decisão manual a cada caso. | **Alertas:** inviabilidade operacional; margem prevista abaixo do mínimo; impacto financeiro do cancelamento. | **Automações:** orquestração completa na confirmação.

**Dados gerados:** Produção, Alocação de Funcionário, lista de Compras sugerida, Receita Financeira prevista. | **Dados atualizados:** Estoque, Equipamento/Veículo, Indicadores. | **Indicadores impactados:** número de Eventos, margem média, taxa de cancelamento. | **Dashboards atualizados:** Dashboard CEO, Dashboard Financeiro, Dashboard de Metas (indireto). | **Auditoria:** encadeamento completo registrado no histórico do Evento. | **Resultado final:** Evento concluído com margem apurada, ou cancelado com recursos liberados.

### FL-004 — Jornada Completa do Orçamento

**Objetivo:** formalizar a proposta comercial com preço sempre lastreado em custo real. | **Evento inicial:** solicitação de proposta pelo Cliente/Lead. | **Pré-requisitos:** Produtos/Pacotes com Ficha Técnica vigente. | **Participantes:** Comercial/CRM, Direção (exceção de margem). | **Módulos:** 08, 13, 14, 07. | **Entidades:** Orçamento, Cliente/Lead, Evento, Produto, Pacote, Ficha Técnica. | **Regras aplicadas:** RN-012, RN-013, RN-021, RN-022, RN-023.

**Sequência:**
1. Orçamento criado (F-025), preço calculado a partir da Ficha Técnica vigente.
2. Orçamento enviado (F-026), validade definida.
3. Negociação gera novas versões (F-027), preservando histórico.
4. Cliente aceita (F-028) → jornada FL-005; ou recusa; ou prazo expira automaticamente (RN-013).

**Decisões possíveis:** aceitar, recusar, renegociar, aprovar exceção de margem. | **Exceções:** Produto sem Ficha Técnica vigente bloqueia inclusão; ajuste abaixo da margem mínima exige aprovação de alçada superior (F-047). | **Alertas:** margem abaixo do mínimo. | **Automações:** cálculo automático de preço; expiração automática.

**Dados gerados:** Orçamento e suas versões. | **Dados atualizados:** nenhuma outra entidade. | **Indicadores impactados:** taxa de aceite, tempo médio de fechamento, margem média proposta. | **Dashboards atualizados:** CRM, Dashboard CEO (indireto). | **Auditoria:** toda alteração de preço registrada com autor e justificativa. | **Resultado final:** Orçamento aceito (avança a Contrato), recusado ou expirado, sempre com histórico completo.

### FL-005 — Jornada Completa do Contrato

**Objetivo:** formalizar juridicamente o compromisso e disparar a previsão financeira. | **Evento inicial:** "Orçamento aceito". | **Pré-requisitos:** dados obrigatórios do Orçamento completos. | **Participantes:** Comercial/CRM, Administrativo/Documentos, Financeiro. | **Módulos:** 09, 08, 23, 03, 07. | **Entidades:** Contrato, Orçamento, Cliente, Documento, Receita Financeira, Evento. | **Regras aplicadas:** RN-014, RN-015, RN-006.

**Sequência:**
1. Minuta gerada automaticamente (F-029, RN-014).
2. Minuta é revisada pelas partes.
3. Contrato assinado (F-030) → Evento "Confirmado" (FL-003, passo 4) → Receita Financeira prevista criada.
4. Se necessário, aditivo é registrado (F-031, RN-015).
5. Contrato acompanha o Evento até conclusão ou cancelamento.

**Decisões possíveis:** assinar, solicitar aditivo, cancelar (via FL-003). | **Exceções:** dados obrigatórios ausentes impedem geração automática; redução de escopo em aditivo pós-planejamento alerta sobre recursos reservados. | **Alertas:** dados ausentes; impacto de aditivo em recursos reservados. | **Automações:** geração automática de minuta e de Receita Financeira prevista.

**Dados gerados:** Contrato, Documento, Receita Financeira prevista. | **Dados atualizados:** Evento, Orçamento. | **Indicadores impactados:** tempo médio de formalização, volume de aditivos. | **Dashboards atualizados:** Dashboard CEO, Dashboard Financeiro. | **Auditoria:** todo aditivo vinculado permanentemente ao Contrato original. | **Resultado final:** compromisso formalizado, operação do Evento autorizada.

### FL-006 — Jornada Completa do Pagamento

**Objetivo:** liquidar Despesas e Receitas Financeiras com rastreabilidade total. | **Evento inicial:** vencimento de lançamento, ou recebimento/pagamento real. | **Pré-requisitos:** Despesa/Receita Financeira em aberto; Conta cadastrada (Módulo 27). | **Participantes:** Financeiro. | **Módulos:** 03, 27, 22. | **Entidades:** Pagamento, Despesa, Receita Financeira, Conta, Banco. | **Regras aplicadas:** RN-043, RN-044, RN-045.

**Sequência:**
1. Origem identificada: lançamento manual (F-005/F-006) ou importação de extrato (FL-023).
2. Pagamento registrado/confirmado (F-007), vinculado à Despesa/Receita Financeira e à Conta.
3. Status é atualizado (parcial ou total).
4. Conciliação confirma correspondência com o extrato real (FL-024).
5. Fluxo de Caixa é recalculado (F-008).

**Decisões possíveis:** confirmar, estornar, classificar manualmente. | **Exceções:** valor não pode exceder saldo em aberto; lançamento ambíguo exige confirmação humana. | **Alertas:** possível duplicidade; lançamento sem correspondência. | **Automações:** sugestão de categorização e conciliação via IA.

**Dados gerados:** Pagamento. | **Dados atualizados:** Despesa/Receita Financeira, Conta (saldo, indireto). | **Indicadores impactados:** saldo em Conta, inadimplência. | **Dashboards atualizados:** Dashboard Financeiro, Dashboard CEO. | **Auditoria:** todo Pagamento e estorno registrados. | **Resultado final:** caixa real sempre refletido com precisão.

### FL-007 — Jornada Completa da Produção

**Objetivo:** transformar Ingredientes em Produtos conforme planejado, com controle de consumo, perdas e rendimento. | **Evento inicial:** "Evento confirmado" ou necessidade de reposição de Estoque. | **Pré-requisitos:** Ficha Técnica vigente; Estoque disponível/reservado. | **Participantes:** Produção. | **Módulos:** 10, 11, 13, 16, 17, 24. | **Entidades:** Produção, Ficha Técnica, Ingrediente, Estoque, Lote, Produto. | **Regras aplicadas:** RN-016, RN-017, RN-024 a RN-029, RN-032.

**Sequência:**
1. Produção planejada automaticamente (F-032), quantidade calculada via parâmetros do Módulo 24.
2. Produção executada (F-033): Ingrediente baixado do Estoque, referenciando Lote.
3. Consumo e rendimento reais registrados (F-034).
4. Produto acabado gerado em novo Lote.
5. Comparação planejado vs. real (F-035) sinaliza desvios.

**Decisões possíveis:** ajustar plano, registrar produção emergencial adicional. | **Exceções:** Estoque insuficiente bloqueia início; rendimento insuficiente gera alerta de alta prioridade. | **Alertas:** prazo insuficiente; rendimento insuficiente; desvio de perda. | **Automações:** planejamento e baixa de Estoque automáticos.

**Dados gerados:** Produção, Lote de Produto. | **Dados atualizados:** Estoque, Ficha Técnica (referência). | **Indicadores impactados:** desvio médio de rendimento, custo real de produção. | **Dashboards atualizados:** Dashboard CEO (indireto). | **Auditoria:** todo plano e execução registrados. | **Resultado final:** Produto disponível para o Evento, com custo e rendimento reais conhecidos.

### FL-008 — Jornada Completa das Compras

**Objetivo:** garantir o abastecimento junto a Fornecedores. | **Evento inicial:** "Produção planejada" ou ponto de reposição atingido. | **Pré-requisitos:** Fornecedor cadastrado. | **Participantes:** Compras/Suprimentos. | **Módulos:** 15, 16, 10, 03. | **Entidades:** Compra, Fornecedor, Ingrediente, Estoque, Lote, Despesa. | **Regras aplicadas:** RN-030, RN-031, RN-027.

**Sequência:**
1. Lista de Compras gerada automaticamente (F-048), com fator de perda de limpeza aplicado.
2. Cotação e emissão de pedido (F-049).
3. Recebimento e conferência (F-050): gera Estoque, Lote e Despesa.
4. Histórico por Fornecedor (F-051) apoia negociações futuras.

**Decisões possíveis:** aprovar lista sugerida, ajustar Fornecedor, registrar divergência. | **Exceções:** item sem Fornecedor exige decisão manual; divergência gera registro para devolução/renegociação. | **Alertas:** item sem Fornecedor; prazo incompatível; divergência na conferência. | **Automações:** geração automática de lista de Compras.

**Dados gerados:** Compra, Lote. | **Dados atualizados:** Estoque, Despesa. | **Indicadores impactados:** prazo médio de entrega, taxa de divergência. | **Dashboards atualizados:** Dashboard CEO (indireto). | **Auditoria:** toda lista, decisão e conferência registradas. | **Resultado final:** insumos disponíveis em Estoque, com custo real capturado.

### FL-009 — Jornada Completa do Estoque

**Objetivo:** manter a posição real e confiável de Ingredientes/Produtos. | **Evento inicial:** qualquer entrada ou saída. | **Pré-requisitos:** item cadastrado. | **Participantes:** Estoque/Logística. | **Módulos:** 16, 15, 10, 17. | **Entidades:** Estoque, Lote, Ingrediente, Produto. | **Regras aplicadas:** RN-032, RN-033.

**Sequência:**
1. Entrada automática (Compra conferida ou Produção concluída) → Estoque atualizado, Lote criado.
2. Saída automática (Produção ou venda) → Estoque baixado, referenciando Lote.
3. Ponto de reposição monitorado continuamente (F-054); alerta ao ser atingido.
4. Inventário periódico (F-053) ajusta divergências.

**Decisões possíveis:** ajustar saldo (com justificativa), definir/revisar ponto de reposição. | **Exceções:** saldo nunca fica negativo. | **Alertas:** saldo insuficiente; estoque abaixo do ponto de reposição. | **Automações:** atualização e alerta automáticos.

**Dados gerados:** nenhum próprio. | **Dados atualizados:** Estoque, Lote. | **Indicadores impactados:** giro de Estoque, frequência de ruptura. | **Dashboards atualizados:** Dashboard CEO (indireto). | **Auditoria:** toda movimentação registrada com origem e Lote. | **Resultado final:** saldo sempre confiável e rastreável por Lote.

### FL-010 — Jornada Completa dos Lotes

**Objetivo:** garantir rastreabilidade de origem e validade de todo item físico. | **Evento inicial:** Compra conferida ou Produção concluída. | **Pré-requisitos:** nenhum. | **Participantes:** Estoque/Logística, Produção. | **Módulos:** 17, 15, 10, 16. | **Entidades:** Lote, Compra, Produção, Ingrediente, Produto, Estoque. | **Regras aplicadas:** RN-034.

**Sequência:**
1. Lote criado automaticamente na conferência de Compra ou conclusão de Produção.
2. Consumo é registrado a cada saída, priorizando os mais próximos do vencimento.
3. Validade é monitorada continuamente; alerta emitido quando próxima.
4. Lote vencido é bloqueado para nova Produção; descarte é registrado (F-056).
5. Rastreabilidade completa é consultável a qualquer momento (F-055).

**Decisões possíveis:** priorizar uso, descartar, investigar problema de qualidade. | **Exceções:** Lote sem validade aplicável não gera alerta de vencimento. | **Alertas:** validade próxima; tentativa de uso de Lote vencido. | **Automações:** priorização "primeiro que vence, primeiro que sai".

**Dados gerados:** Lote. | **Dados atualizados:** Estoque, estado do Lote. | **Indicadores impactados:** percentual de perda por vencimento. | **Dashboards atualizados:** Dashboard CEO (indireto). | **Auditoria:** todo vencimento/descarte registrado com quantidade e motivo. | **Resultado final:** rastreabilidade completa, resposta rápida a qualquer questão de segurança alimentar.

### FL-011 — Jornada Completa da Engenharia de Custos

**Objetivo:** consolidar e proteger o custo real de produção e de cada Evento. | **Evento inicial:** "Custo de Ingrediente atualizado" ou conclusão das Produções de um Evento. | **Pré-requisitos:** Ficha Técnica, Produção e Alocação de Funcionário registradas. | **Participantes:** Produção (Engenharia de Custos), Financeiro. | **Módulos:** 11, 13, 10, 19, 03. | **Entidades:** Ficha Técnica, Produção, Alocação de Funcionário, Despesa, Evento. | **Regras aplicadas:** RN-018, RN-019, RN-027, RN-036.

**Sequência:**
1. Custo de Ingrediente muda → Ficha Técnica recalculada automaticamente (F-037/F-043); Orçamentos abertos alertados.
2. Ao longo do Evento, custo de mão de obra é consolidado (F-061).
3. Ao concluir as Produções, custo total real é calculado (F-036).
4. Desvio de custo é disponibilizado para consulta (F-038).
5. Resultado alimenta a apuração de margem (FL-003/FL-029).

**Decisões possíveis:** revisar Ficha Técnica, revisar preço, investigar desvio. | **Exceções:** custo "parcial" enquanto houver pendência; Orçamentos já aceitos não são recalculados retroativamente. | **Alertas:** custo real excedendo o previsto; impacto em Orçamentos abertos. | **Automações:** recálculo automático em cascata.

**Dados gerados:** nenhum próprio. | **Dados atualizados:** Ficha Técnica, Indicador (margem, custo real). | **Indicadores impactados:** custo real médio por Evento, desvio de custo. | **Dashboards atualizados:** Dashboard CEO, Dashboard Financeiro. | **Auditoria:** todo cálculo final preservado permanentemente. | **Resultado final:** custo real sempre conhecido, protegido contra desatualização silenciosa.

### FL-012 — Jornada Completa das Receitas

**Objetivo:** padronizar e versionar o "como fazer" de cada item produzido. | **Evento inicial:** necessidade de novo item ou ajuste de um existente. | **Pré-requisitos:** Ingredientes cadastrados. | **Participantes:** Produção. | **Módulos:** 12, 13. | **Entidades:** Receita, Ingrediente, Ficha Técnica, Produto. | **Regras aplicadas:** RN-020.

**Sequência:**
1. Receita criada (F-039), "Em desenvolvimento".
2. Receita testada; Ficha Técnica formalizada em paralelo (jornada FL-013).
3. Receita aprovada (F-040) — só então pode originar um Produto comercial.
4. Ajustes futuros geram nova versão (F-041), nunca sobrescrevendo a anterior.
5. Receita é descontinuada junto com o Produto associado, quando aplicável.

**Decisões possíveis:** aprovar, revisar, descontinuar. | **Exceções:** não é aprovada sem Ficha Técnica associada. | **Alertas:** aviso à equipe de Produção sobre nova versão vigente. | **Automações:** propagação de nova versão de Ficha Técnica.

**Dados gerados:** Receita e suas versões. | **Dados atualizados:** Ficha Técnica. | **Indicadores impactados:** número de Receitas ativas, frequência de revisão. | **Dashboards atualizados:** nenhum direto. | **Auditoria:** todas as versões preservadas. | **Resultado final:** "como fazer" documentado, testado e evoluindo com histórico íntegro.

### FL-013 — Jornada Completa das Fichas Técnicas

**Objetivo:** ser a fonte única de custo de produção de cada item. | **Evento inicial:** aprovação de Receita, ou atualização de custo de Ingrediente. | **Pré-requisitos:** Receita aprovada. | **Participantes:** Produção (Engenharia de Custos). | **Módulos:** 13, 12, 24, 14, 11. | **Entidades:** Ficha Técnica, Receita, Ingrediente, Produto. | **Regras aplicadas:** RN-018, RN-019, RN-021, RN-027.

**Sequência:**
1. Ficha Técnica criada a partir da Receita aprovada (F-042), com fator de perda de limpeza e rendimento definidos (Módulo 24).
2. Custo total calculado; Ficha Técnica passa a "Vigente".
3. Atualização de custo de Ingrediente recalcula automaticamente (F-043).
4. Mudança de composição gera nova versão (a anterior torna-se "Substituída").
5. Produto sem Ficha Técnica vigente é bloqueado na venda (jornada FL-004).

**Decisões possíveis:** revisar composição, revisar fatores de perda/rendimento. | **Exceções:** não podem existir duas Fichas Técnicas Vigentes simultâneas para o mesmo item. | **Alertas:** impacto de recálculo em Orçamentos abertos. | **Automações:** recálculo automático.

**Dados gerados:** Ficha Técnica e suas versões. | **Dados atualizados:** nenhuma outra entidade diretamente. | **Indicadores impactados:** custo médio por Produto. | **Dashboards atualizados:** Dashboard CEO (indireto). | **Auditoria:** toda versão preservada. | **Resultado final:** custo de produção sempre atual, fonte única para toda decisão de preço.

### FL-014 — Jornada Completa da Precificação

**Objetivo:** garantir que todo preço tenha lastro em custo real e margem definida. | **Evento inicial:** definição/atualização de preço, ou inclusão em Orçamento. | **Pré-requisitos:** Ficha Técnica vigente; margem-alvo definida (F-077). | **Participantes:** Produção/Financeiro, Direção (exceções). | **Módulos:** 14, 13, 24, 08. | **Entidades:** Produto, Pacote, Ficha Técnica. | **Regras aplicadas:** RN-022, RN-023, RN-012.

**Sequência:**
1. Margem-alvo definida centralmente (F-045/F-077).
2. Preço calculado a partir do custo vigente + margem (F-046).
3. Preço é usado na criação de Orçamentos (FL-004).
4. Ajuste que leve a margem abaixo do mínimo é sinalizado e requer aprovação da Direção (F-047).

**Decisões possíveis:** aceitar preço calculado, ajustar dentro da alçada, solicitar exceção. | **Exceções:** margem-alvo pendente de confirmação real — enquanto isso, cálculo opera em alerta. | **Alertas:** preço fora de faixa esperada; margem abaixo do mínimo. | **Automações:** cálculo automático de preço.

**Dados gerados:** nenhum próprio. | **Dados atualizados:** Produto, Pacote (preço). | **Indicadores impactados:** margem média, frequência de exceção aprovada. | **Dashboards atualizados:** Dashboard CEO (indireto). | **Auditoria:** toda mudança de preço registra custo/margem vigentes. | **Resultado final:** preço sempre defensável e rastreável até o custo real.

### FL-015 — Jornada Completa das Escalas

**Objetivo:** planejar quem trabalha em cada Evento/Produção, evitando falta ou excesso de equipe. | **Evento inicial:** "Evento confirmado". | **Pré-requisitos:** proporção de escala definida (F-078). | **Participantes:** Pessoas/Mão de Obra, Eventos/Operações. | **Módulos:** 20, 19, 07, 24. | **Entidades:** Alocação de Funcionário, Funcionário, Evento. | **Regras aplicadas:** RN-037.

**Sequência:**
1. Escala sugerida automaticamente na confirmação do Evento (F-063).
2. Escala revisada e confirmada/ajustada manualmente (F-064).
3. Funcionários são notificados.
4. No dia do Evento, participação real é registrada, alimentando a Engenharia de Custos (FL-011).

**Decisões possíveis:** confirmar, ajustar quantidade/função, substituir Funcionário. | **Exceções:** parâmetro pendente impede sugestão automática; sobreposição de horário é bloqueada. | **Alertas:** escala não confirmada a X dias do Evento. | **Automações:** sugestão automática na confirmação do Evento.

**Dados gerados:** Alocação de Funcionário. | **Dados atualizados:** nenhuma outra entidade diretamente. | **Indicadores impactados:** taxa de acerto de dimensionamento de equipe. | **Dashboards atualizados:** Dashboard CEO (indireto). | **Auditoria:** toda sugestão e ajuste registrados. | **Resultado final:** equipe correta garantida, custo de mão de obra rastreável.

### FL-016 — Jornada Completa dos Funcionários

**Objetivo:** manter o cadastro e o custo de mão de obra da equipe fixa e temporária. | **Evento inicial:** contratação ou primeiro engajamento. | **Pré-requisitos:** nenhum. | **Participantes:** Pessoas/Mão de Obra. | **Módulos:** 19, 20, 03. | **Entidades:** Funcionário, Alocação de Funcionário, Despesa. | **Regras aplicadas:** RN-036.

**Sequência:**
1. Funcionário cadastrado (F-060).
2. Funcionário é alocado a Eventos/Produções ao longo do tempo (FL-015).
3. Custo de mão de obra é consolidado a cada Alocação Realizada (F-061).
4. Funcionário é eventualmente desligado (F-062), preservando o histórico.

**Decisões possíveis:** manter ativo, afastar, desligar. | **Exceções:** Funcionário inativo não é incluído em nova Alocação. | **Alertas:** Alocação sem valor definido. | **Automações:** consolidação automática de custo.

**Dados gerados:** nenhum além do cadastro. | **Dados atualizados:** Funcionário, Despesa (custo de mão de obra). | **Indicadores impactados:** custo médio de mão de obra por Evento. | **Dashboards atualizados:** Dashboard CEO (indireto). | **Auditoria:** alteração preserva histórico. | **Resultado final:** custo de mão de obra sempre rastreável.

### FL-017 — Jornada Completa dos Equipamentos

**Objetivo:** controlar disponibilidade e alocação de bens físicos reutilizáveis (inclui Veículos). | **Evento inicial:** aquisição/contratação, ou confirmação de Evento. | **Pré-requisitos:** nenhum para cadastro. | **Participantes:** Eventos/Operações, Compras/Suprimentos. | **Módulos:** 18, 07, 03. | **Entidades:** Equipamento, Veículo, Evento, Despesa. | **Regras aplicadas:** RN-035.

**Sequência:**
1. Equipamento/Veículo cadastrado (F-057), "Disponível".
2. Na confirmação de Evento, item é alocado (F-058), com verificação de conflito.
3. Após o Evento, item retorna a "Disponível".
4. Manutenção é registrada quando necessário (F-059), gerando Despesa.
5. Item é baixado quando descartado/vendido.

**Decisões possíveis:** alocar, substituir por conflito, enviar para manutenção, baixar. | **Exceções:** item "Em manutenção" não pode ser alocado; conflito de sobreposição é sempre bloqueado. | **Alertas:** conflito de alocação, com sugestão de alternativa. | **Automações:** bloqueio automático de conflito.

**Dados gerados:** nenhum além do cadastro. | **Dados atualizados:** Equipamento/Veículo, Despesa. | **Indicadores impactados:** taxa de utilização, frequência de manutenção. | **Dashboards atualizados:** Dashboard CEO (indireto). | **Auditoria:** toda tentativa de conflito e sua resolução registradas. | **Resultado final:** nenhum Evento falha por falta de Equipamento/Veículo.

### FL-018 — Jornada Completa dos Bancos

**Objetivo:** centralizar a gestão de Banco, Conta e Cartão como base de todo o Financeiro. | **Evento inicial:** necessidade de nova relação bancária. | **Pré-requisitos:** nenhum. | **Participantes:** Financeiro. | **Módulos:** 27, 02, 03, 22. | **Entidades:** Banco, Conta, Pagamento. | **Regras aplicadas:** Regras Globais Financeiras do Domain Model, RN-043, RN-044.

**Sequência:**
1. Banco cadastrado (F-092).
2. Conta/Cartão cadastrado e classificado por tipo (F-093/F-094).
3. Conta é usada como origem/destino em Pagamentos (FL-006).
4. Saldo e status consultados continuamente (F-096); histórico apoia conciliação (F-097, FL-024).
5. Conta/Cartão é encerrado quando a relação termina (F-095).

**Decisões possíveis:** cadastrar novo tipo de Conta, encerrar, reclassificar. | **Exceções:** Conta encerrada não recebe novo Pagamento. | **Alertas:** herdados de RN-043/RN-044. | **Automações:** nenhuma própria — fornece a base para as automações do Financeiro.

**Dados gerados:** Banco, Conta. | **Dados atualizados:** nenhuma outra entidade diretamente. | **Indicadores impactados:** saldo consolidado por tipo de Conta. | **Dashboards atualizados:** Dashboard Financeiro (F-098), Dashboard CEO. | **Auditoria:** toda alteração de cadastro/status registrada. | **Resultado final:** base bancária confiável sustentando todo o Financeiro.

### FL-019 — Jornada Completa das Metas

**Objetivo:** acompanhar objetivos quantitativos de gestão do início ao encerramento do ciclo. | **Evento inicial:** definição de objetivo pela Direção. | **Pré-requisitos:** Indicador associado já existente. | **Participantes:** Direção, responsável pela Meta. | **Módulos:** 26, 01. | **Entidades:** Meta, Indicador. | **Regras aplicadas:** RN-046.

**Sequência:**
1. Meta criada (F-084): período, Indicador, responsável, valor-alvo e critério de sucesso definidos.
2. Progresso é acompanhado continuamente (F-088).
3. Ajustes são feitos quando necessário (F-085).
4. Ao fim do período, ciclo é encerrado automaticamente como "Atingida" ou "Não atingida" (F-086).
5. Justificativa é registrada (F-090); Meta pode ser duplicada para novo ciclo (F-087).
6. Histórico disponível permanentemente (F-089); Dashboard de Metas consolida tudo (F-091), consumido pelo Dashboard CEO.

**Decisões possíveis:** ajustar, encerrar antecipadamente, duplicar, justificar. | **Exceções:** Meta sem Indicador correspondente não pode ser criada; Meta encerrada não é reaberta. | **Alertas:** atraso no progresso; conclusão de ciclo. | **Automações:** encerramento automático de ciclo.

**Dados gerados:** Meta. | **Dados atualizados:** nenhuma outra entidade diretamente. | **Indicadores impactados:** taxa de metas atingidas. | **Dashboards atualizados:** Dashboard de Metas, Dashboard CEO (apenas consumo). | **Auditoria:** todo ciclo e justificativa preservados permanentemente. | **Resultado final:** gestão por objetivos formal, mensurável e historicamente rastreável.

### FL-020 — Jornada Completa do Marketing

**Objetivo:** planejar e medir Campanhas de geração de demanda. | **Evento inicial:** planejamento de uma iniciativa de marketing. | **Pré-requisitos:** nenhum. | **Participantes:** Marketing. | **Módulos:** 21, 06, 04. | **Entidades:** Campanha, Lead, Cliente, Contrato. | **Regras aplicadas:** RN-038.

**Sequência:**
1. Campanha criada (F-065), "Planejada" → "Em execução".
2. Leads gerados são atribuídos automaticamente a ela (FL-001).
3. Conversões são atribuídas de volta à Campanha de origem.
4. Retorno é consultado a qualquer momento (F-066), inclusive consolidado no CRM (F-012).
5. Campanha é encerrada ao fim do período (F-067), permanecendo como histórico.

**Decisões possíveis:** continuar, ajustar investimento, encerrar antecipadamente. | **Exceções:** Campanha encerrada não recebe novos Leads; Cliente sem origem identificável aparece como "origem direta". | **Alertas:** nenhum próprio. | **Automações:** atribuição automática de conversão/retorno.

**Dados gerados:** Campanha. | **Dados atualizados:** nenhuma outra entidade diretamente. | **Indicadores impactados:** retorno por Campanha, custo por Lead/Cliente. | **Dashboards atualizados:** Dashboard CEO (indireto). | **Auditoria:** toda atribuição é permanente e consultável. | **Resultado final:** decisão de investimento em marketing orientada por dado real.

### FL-021 — Jornada Completa dos Dashboards

**Objetivo:** garantir que toda visão de gestão seja composta exclusivamente por Indicadores auditáveis. | **Evento inicial:** necessidade de uma nova visão de gestão. | **Pré-requisitos:** Indicadores já definidos. | **Participantes:** BI/Direção Executiva; cada área dona do respectivo Dashboard. | **Módulos:** 01, 26, 27. | **Entidades:** Dashboard, Indicador. | **Regras aplicadas:** RN-039, RN-001.

**Sequência:**
1. Dashboard é configurado com os Indicadores relevantes (F-002/F-091/F-098).
2. Cada evento de negócio relevante recalcula os Indicadores associados (FL-028).
3. Dashboard reflete a atualização automaticamente (FL-026), sem ação manual.
4. Dashboards especializados (Metas, Financeiro) alimentam o Dashboard CEO por consumo, nunca por gestão direta.

**Decisões possíveis:** reconfigurar quais Indicadores aparecem em cada Dashboard. | **Exceções:** não é permitido incluir dado sem Indicador correspondente. | **Alertas:** Indicador não recalculável. | **Automações:** atualização contínua.

**Dados gerados:** nenhum — Dashboard é uma visão, não um registro. | **Dados atualizados:** composição do Dashboard (quando reconfigurado). | **Indicadores impactados:** todos os incluídos em cada Dashboard. | **Dashboards atualizados:** este é o próprio objeto da jornada. | **Auditoria:** herdada dos Indicadores subjacentes. | **Resultado final:** visão de gestão sempre atualizada, nunca dissociada do dado real.

### FL-022 — Jornada Completa da Inteligência Artificial

**Objetivo:** oferecer assistência auditável em todo o sistema, nunca decisão automática silenciosa. | **Evento inicial:** situação elegível a apoio de IA (extrato importado, planejamento de compra, definição de preço). | **Pré-requisitos:** histórico de dados suficiente. | **Participantes:** todas as áreas conforme a sugestão; Direção (configuração do nível de automação). | **Módulos:** 22, 03, 15, 14. | **Entidades:** variável (Pagamento, Compra, Produto). | **Regras aplicadas:** RN-041, RN-042, RN-043.

**Sequência:**
1. IA analisa o contexto (extrato, histórico de Produção/Compra, custo vigente).
2. Sugestão é gerada — sempre sinalizada como sugestão, nunca como fato.
3. Usuário confirma, ajusta ou recusa (salvo ação de baixo risco pré-aprovada, F-071).
4. Decisão é aplicada e registrada; se recusada, motivo é preservado.

**Decisões possíveis:** aceitar, ajustar, recusar, configurar automação futura. | **Exceções:** nenhuma sugestão financeira/de cliente/de preço é aplicada sem confirmação, salvo pré-aprovação reversível. | **Alertas:** baixa confiança da previsão quando o histórico for insuficiente. | **Automações:** ações de baixo risco pré-aprovadas.

**Dados gerados:** nenhum próprio. | **Dados atualizados:** variável, conforme a decisão sobre a sugestão. | **Indicadores impactados:** taxa de aceite de sugestões de IA. | **Dashboards atualizados:** Dashboard CEO (indireto). | **Auditoria:** toda sugestão, aceite, recusa ou reversão registrada permanentemente. | **Resultado final:** apoio inteligente que acelera decisões sem substituir o julgamento humano em pontos críticos.

### FL-023 — Importação Automática de Extratos Bancários

**Objetivo:** reduzir o trabalho manual de registrar Pagamentos. | **Evento inicial:** "Extrato bancário importado". | **Pré-requisitos:** Conta cadastrada (Módulo 27) correspondente ao extrato. | **Participantes:** Financeiro; IA (sugestão). | **Módulos:** 27, 03, 22. | **Entidades:** Pagamento, Despesa, Receita Financeira, Conta. | **Regras aplicadas:** RN-043.

**Sequência:**
1. Extrato é importado.
2. Sistema identifica lançamentos de entrada/saída.
3. IA sugere categoria com base em histórico semelhante (F-068).
4. IA sugere conciliação com Despesas/Receitas Financeiras já previstas.
5. Possíveis duplicidades são identificadas.
6. Usuário confirma cada lançamento ambíguo.
7. Após confirmação, Pagamento é efetivado; Fluxo de Caixa, Indicadores e Dashboards são atualizados.

**Decisões possíveis:** confirmar categoria/conciliação sugerida, corrigir, marcar como pessoal. | **Exceções:** nenhuma conciliação é efetivada automaticamente sob ambiguidade. | **Alertas:** possível duplicidade; lançamento sem correspondência; possível lançamento pessoal. | **Automações:** categorização e conciliação sugeridas por IA.

**Dados gerados:** Pagamento. | **Dados atualizados:** Despesa/Receita Financeira, Conta. | **Indicadores impactados:** saldo em Conta, tempo de conciliação. | **Dashboards atualizados:** Dashboard Financeiro, Dashboard CEO. | **Auditoria:** toda sugestão e decisão registradas com rastreabilidade completa. | **Resultado final:** extrato bancário refletido no sistema com mínimo esforço manual e máxima confiabilidade.

### FL-024 — Conciliação Bancária

**Objetivo:** garantir que todo Pagamento registrado corresponda a um lançamento real na Conta. | **Evento inicial:** importação de extrato (FL-023) ou conciliação manual periódica. | **Pré-requisitos:** Pagamentos registrados e extrato do mesmo período disponível. | **Participantes:** Financeiro. | **Módulos:** 03, 27. | **Entidades:** Pagamento, Conta. | **Regras aplicadas:** RN-044.

**Sequência:**
1. Sistema compara Pagamentos registrados com lançamentos do extrato (F-097).
2. Lançamentos que batem exatamente são marcados "conciliados".
3. Divergências (valor, data, ausência de correspondência) são destacadas.
4. Usuário trata cada divergência manualmente, registrando a decisão.

**Decisões possíveis:** conciliar, investigar divergência, corrigir lançamento. | **Exceções:** divergência nunca é corrigida automaticamente. | **Alertas:** Conta com pendência de conciliação há mais de um período definido. | **Automações:** comparação automática; decisão sempre humana em caso de divergência.

**Dados gerados:** nenhum — apenas status de conciliação. | **Dados atualizados:** Pagamento (status). | **Indicadores impactados:** confiabilidade do Fluxo de Caixa. | **Dashboards atualizados:** Dashboard Financeiro. | **Auditoria:** todo status de conciliação registrado com data e responsável. | **Resultado final:** Fluxo de Caixa confiável e auditável.

### FL-025 — Lançamentos Financeiros Manuais

**Objetivo:** permitir o registro de Despesas/Receitas Financeiras/Pagamentos sem origem automática. | **Evento inicial:** usuário inicia um lançamento manual. | **Pré-requisitos:** Conta cadastrada. | **Participantes:** Financeiro. | **Módulos:** 03, 27. | **Entidades:** Despesa, Receita Financeira, Pagamento, Conta. | **Regras aplicadas:** RN-045, RN-005.

**Sequência:**
1. Usuário informa origem/categoria, valor, data e Conta.
2. Se a origem não é automaticamente associável, categoria e justificativa são exigidas.
3. Lançamento é tratado com as mesmas regras de qualquer outro.
4. Se o lançamento se repetir de forma padronizada, sistema sugere criação de uma origem formal.

**Decisões possíveis:** categorizar, justificar, aceitar sugestão de automação futura. | **Exceções:** lançamento ambíguo exige confirmação de natureza pessoal vs. empresarial. | **Alertas:** lançamento manual repetido, sugerindo automação. | **Automações:** nenhuma na criação — é o próprio complemento humano à automação.

**Dados gerados:** Despesa/Receita Financeira/Pagamento manual. | **Dados atualizados:** Fluxo de Caixa (indireto). | **Indicadores impactados:** os mesmos de qualquer lançamento financeiro. | **Dashboards atualizados:** Dashboard Financeiro, Dashboard CEO. | **Auditoria:** lançamento manual registra o autor, distintamente dos automáticos. | **Resultado final:** nenhuma exceção financeira fica fora do sistema por falta de automação.

### FL-026 — Atualização Automática dos Dashboards

**Objetivo:** garantir que toda visão de gestão reflita o estado real continuamente. | **Evento inicial:** qualquer Evento do Domínio que afete um Indicador incluído em algum Dashboard. | **Pré-requisitos:** Indicadores associados a pelo menos um Dashboard. | **Participantes:** nenhum humano — fluxo 100% automático. | **Módulos:** 01, 26, 27, e transitivamente todos. | **Entidades:** Indicador, Dashboard. | **Regras aplicadas:** RN-001, RN-039, RN-040.

**Sequência:**
1. Um Evento de negócio ocorre (ex.: Pagamento recebido, Produção concluída).
2. Todo Indicador cuja fórmula depende desse dado é recalculado (FL-028).
3. Todo Dashboard que inclui esse Indicador é atualizado.
4. Não há intervenção manual em nenhuma etapa.

**Decisões possíveis:** nenhuma — automático; composição prévia de cada Dashboard é decidida fora desta jornada. | **Exceções:** falha de recálculo é sinalizada explicitamente, nunca escondida. | **Alertas:** Indicador não recalculável. | **Automações:** 100% deste fluxo.

**Dados gerados:** nenhum. | **Dados atualizados:** Indicador (valor), Dashboard (view). | **Indicadores impactados:** todos os afetados pelo Evento de origem. | **Dashboards atualizados:** todos que incluem os Indicadores afetados. | **Auditoria:** herdada dos Indicadores subjacentes. | **Resultado final:** nenhum Dashboard fica desatualizado sem que isso seja explicitamente sinalizado.

### FL-027 — Atualização Automática do Dashboard CEO

**Objetivo:** garantir que a visão executiva máxima da Direção esteja sempre correta. | **Evento inicial:** qualquer Evento de Domínio que afete um Indicador incluído no Dashboard CEO (subconjunto de FL-026). | **Pré-requisitos:** Indicador incluído especificamente no Dashboard CEO. | **Participantes:** nenhum humano. | **Módulos:** 01, e transitivamente todos. | **Entidades:** Indicador, Dashboard (instância CEO). | **Regras aplicadas:** RN-001, PF-07.

**Sequência:**
1. Segue exatamente o fluxo geral FL-026, restrito aos Indicadores marcados como prioritários pela Direção.
2. Por ser a instância principal (PF-07), qualquer Indicador relevante de qualquer módulo deve, direta ou indiretamente, estar refletido aqui.

**Decisões possíveis:** nenhuma — automático. | **Exceções:** idênticas à FL-026. | **Alertas:** idênticos à FL-026, com prioridade máxima de visibilidade. | **Automações:** 100%.

**Dados gerados:** nenhum. | **Dados atualizados:** Dashboard CEO. | **Indicadores impactados:** todos os priorizados pela Direção. | **Dashboards atualizados:** Dashboard CEO. | **Auditoria:** herdada dos Indicadores subjacentes. | **Resultado final:** a Direção nunca decide com base em dado desatualizado.

### FL-028 — Atualização Automática dos Indicadores

**Objetivo:** ser a camada de cálculo que sustenta todos os Dashboards (FL-021, FL-026, FL-027). | **Evento inicial:** qualquer alteração em uma entidade que participe da fórmula de um Indicador. | **Pré-requisitos:** fórmula do Indicador definida. | **Participantes:** nenhum humano na execução; Direção/BI na definição da fórmula (fora desta jornada). | **Módulos:** todos (fonte de dado), 01 (consumo). | **Entidades:** Indicador. | **Regras aplicadas:** RN-040.

**Sequência:**
1. Entidade de origem é criada/alterada (ex.: nova Despesa, novo Pagamento, Produção concluída).
2. Todo Indicador cuja fórmula referencia essa entidade é recalculado.
3. Valor anterior é preservado no histórico.
4. Dashboards que consomem o Indicador são notificados (FL-026).

**Decisões possíveis:** nenhuma nesta jornada — apenas na definição/revisão da fórmula (fora do escopo aqui). | **Exceções:** revisão de fórmula preserva o histórico calculado com a fórmula anterior. | **Alertas:** nenhum próprio. | **Automações:** 100%.

**Dados gerados:** nenhum. | **Dados atualizados:** Indicador (valor). | **Indicadores impactados:** o próprio objeto desta jornada. | **Dashboards atualizados:** todos que o incluem (FL-026). | **Auditoria:** toda fórmula, passada e presente, preservada e rastreável. | **Resultado final:** todo número exibido em qualquer Dashboard é sempre calculável e auditável até sua origem.

### FL-029 — Encerramento de Evento

**Objetivo:** formalizar a conclusão de um Evento, com apuração de resultado e histórico completo. | **Evento inicial:** fim da execução operacional do Evento (zoom do passo 7 da FL-003). | **Pré-requisitos:** Evento em execução. | **Participantes:** Eventos/Operações, Financeiro, Produção. | **Módulos:** 07, 03, 10, 11. | **Entidades:** Evento, Produção, Despesa, Receita Financeira, Ficha Técnica. | **Regras aplicadas:** RN-003, RN-017, RN-018.

**Sequência:**
1. Execução do Evento é confirmada como concluída (F-023).
2. Comparação planejado vs. real é acionada para toda Produção vinculada (F-035).
3. Custo total real do Evento é calculado (F-036).
4. Margem real é apurada (F-009), assim que Despesas/Receita Financeira do Evento estiverem quitadas.
5. Evento passa a "Concluído"; jornada de Pós-venda (FL-030) é disparada.

**Decisões possíveis:** nenhuma decisão de negócio nova — fluxo majoritariamente automático a partir da confirmação humana de conclusão. | **Exceções:** margem é "prevista" enquanto houver Despesa em aberto. | **Alertas:** custo real excedendo significativamente o previsto. | **Automações:** apuração de resultado e comparação planejado x real, acionadas automaticamente.

**Dados gerados:** nenhum próprio — consolida dados já existentes. | **Dados atualizados:** Evento (estado), Indicador (margem por Evento). | **Indicadores impactados:** margem por Evento, desvio de custo/rendimento. | **Dashboards atualizados:** Dashboard CEO, Dashboard Financeiro. | **Auditoria:** conclusão e apuração registradas permanentemente. | **Resultado final:** Evento com resultado final conhecido e histórico íntegro.

### FL-030 — Pós-venda

**Objetivo:** manter o relacionamento com o Cliente após a conclusão do Evento, gerando fidelização e indicação. | **Evento inicial:** "Evento concluído" (FL-029). | **Pré-requisitos:** Evento concluído vinculado a um Cliente. | **Participantes:** Comercial/CRM, Marketing. | **Módulos:** 05, 07, 21, 04. | **Entidades:** Cliente, Evento, Campanha (indiretamente). | **Regras aplicadas:** RN-010.

**Sequência:**
1. Sistema verifica o critério de fidelização do Cliente (RN-010) a cada Evento concluído.
2. Cliente é marcado como fidelizado quando o critério é atingido.
3. Histórico do relacionamento fica disponível (F-014) para contato de pós-venda.
4. Indicações geradas por Clientes satisfeitos alimentam novos Leads (FL-001), atribuídos como "indicação" na origem.
5. Retorno desse relacionamento contínuo é consolidado no CRM (F-011/F-012).

**Decisões possíveis:** contatar o Cliente, oferecer condição de fidelidade, registrar feedback. | **Exceções:** critério de fidelização é parâmetro pendente de confirmação real (Q76 do Business Discovery). | **Alertas:** nenhum próprio nesta fase — feedback estruturado é tema pendente (Q79–Q81 do Business Discovery), sem funcionalidade dedicada além do que já existe em Clientes. | **Automações:** marcação automática de fidelização.

**Dados gerados:** nenhum próprio. | **Dados atualizados:** Cliente (atributo de fidelização). | **Indicadores impactados:** taxa de fidelização, taxa de indicação. | **Dashboards atualizados:** CRM, Dashboard CEO (indireto). | **Auditoria:** data de fidelização registrada permanentemente. | **Resultado final:** ciclo comercial se realimenta — Cliente satisfeito gera nova demanda para a empresa.

---

## 4. Matriz de Integração entre Módulos

### 4.1 Quem Chama Quem (Direção da Dependência)

| Módulo de origem | Chama/aciona | Natureza |
|---|---|---|
| 06 — Leads | 05 — Clientes (na conversão) | Síncrona, sob decisão humana |
| 08 — Orçamentos | 13 — Fichas Técnicas, 14 — Precificação | Síncrona, automática (cálculo de preço) |
| 08 — Orçamentos | 09 — Contratos (no aceite) | Automática |
| 09 — Contratos | 07 — Eventos (confirmação), 03 — Financeiro (Receita Financeira prevista), 23 — Documentos | Automática |
| 07 — Eventos | 10 — Produção, 16 — Estoque, 20 — Escalas, 18 — Equipamentos, 15 — Compras, 03 — Financeiro, 01 — Dashboard CEO | Automática (orquestração RN-006) |
| 10 — Produção | 13 — Fichas Técnicas, 16 — Estoque, 17 — Lotes, 24 — Configurações | Automática |
| 15 — Compras | 16 — Estoque, 17 — Lotes, 03 — Financeiro | Automática (na conferência) |
| 13 — Fichas Técnicas | 12 — Receitas, 24 — Configurações, 11 — Engenharia de Custos | Automática |
| 11 — Engenharia de Custos | 03 — Financeiro, 01 — Dashboard CEO | Automática |
| 27 — Bancos | 02 — Financeiro Pessoal, 03 — Financeiro Empresarial, 22 — Inteligência Artificial | Fornecimento de dado (não aciona, é consultado) |
| 22 — Inteligência Artificial | 03 — Financeiro, 15 — Compras, 14 — Precificação | Sugestão, sempre com confirmação humana |
| 26 — Metas | 01 — Dashboard CEO | Consumo (Metas nunca é acionado pelo Dashboard CEO — via única) |
| 21 — Marketing | 06 — Leads, 04 — CRM | Atribuição automática |
| 24 — Configurações | 10 — Produção, 14 — Precificação, 20 — Escalas, 07 — Eventos | Fornecimento de parâmetro (não aciona, é consultado) |
| 25 — Administração do Sistema | todos | Transversal (governança de acesso e alertas) |

### 4.2 Dependências entre Módulos

Mesma Cadeia de Valor já registrada no Domain Discovery/Domain Model — confirmado grafo acíclico, sem dependência circular:

```
Configurações, Bancos ──► (fornecem parâmetro/dado, não dependem de ninguém)
Leads ──► Clientes ──► Orçamentos ──► Contratos ──► Eventos
Receitas ──► Fichas Técnicas ──► Engenharia de Custos ──► Precificação ──► Orçamentos
Eventos ──► Produção ──► Compras ──► Estoque ──► Lotes
Eventos ──► Equipamentos, Escalas ──► Funcionários
Eventos, Contratos, Compras, Funcionários ──► Financeiro Empresarial/Pessoal ──► Dashboard CEO
Marketing ◄──► Leads, Clientes (atribuição bidirecional de dado, não de controle)
Metas ──► Dashboard CEO (consumo, nunca o inverso)
Inteligência Artificial ──► Financeiro, Compras, Precificação (apoio, nunca controle)
Documentos ◄── Contratos, Compras, Clientes, Fornecedores, Eventos
Administração do Sistema ──► todos (governança, transversal)
```

### 4.3 Processos Automáticos vs. Dependentes do Usuário

| Processo | Tipo |
|---|---|
| Orquestração de confirmação de Evento (RN-006) | Automático |
| Cálculo de preço, custo, consumo, perdas, rendimento | Automático |
| Baixa/atualização de Estoque | Automático |
| Recálculo de Indicadores e Dashboards | Automático |
| Atribuição de origem/retorno de Campanha | Automático |
| Sugestão de IA (categorização, previsão, preço) | Automático (sugestão), dependente do usuário (confirmação) |
| Criação/qualificação/conversão de Lead | Dependente do usuário |
| Criação, envio e negociação de Orçamento | Dependente do usuário |
| Assinatura de Contrato | Dependente do usuário |
| Execução física da Produção, do Evento, das Compras | Dependente do usuário |
| Definição de parâmetros (Módulo 24) e cadastro de Banco/Conta (Módulo 27) | Dependente do usuário |
| Criação, acompanhamento e encerramento de Meta | Dependente do usuário (encerramento de ciclo é automático na data, RN-046) |
| Aprovação de exceção de margem, cancelamento de Evento | Dependente do usuário (Direção) |

### 4.4 Sequenciamento: Série vs. Paralelo

**Devem executar em série (dependência estrita):** Lead → Cliente → Orçamento → Contrato → Evento Confirmado → Produção/Compras → Encerramento → Pós-venda; Receita → Ficha Técnica → Engenharia de Custos → Precificação → Orçamento.

**Podem executar em paralelo (sem dependência entre si), a partir da confirmação do Evento:** Planejamento de Produção, Reserva de Estoque, Sugestão de Escala, Geração de lista de Compras, Alocação de Equipamento — todos disparados pela mesma RN-006, mas sem depender uns dos outros para começar.

**Podem executar em paralelo, de forma contínua e independente do restante:** Importação/Conciliação Bancária, Gestão de Metas, Gestão de Campanhas de Marketing, Cadastro de Bancos/Contas — nenhum deles bloqueia ou é bloqueado pelo ciclo comercial/operacional do Evento.

---

## 5. Mapa Operacional do THE CHARCOAL OS

Em linguagem simples: assim é o caminho que a informação percorre dentro do THE CHARCOAL OS, do primeiro contato de um cliente até o número final aparecer no Dashboard CEO.

Tudo começa com um **Lead** — alguém interessado, vindo de uma indicação, de uma campanha de marketing ou de contato direto. Quando esse Lead vira um **Cliente**, o sistema já sabe quem ele é para sempre, sem duplicar cadastro. O Cliente pede um **Evento**, e o time comercial monta um **Orçamento** — cujo preço nunca é inventado, porque vem direto do custo real já calculado na Ficha Técnica de cada prato.

Quando o Cliente aceita, o Orçamento vira **Contrato**, e é exatamente nesse momento que o sistema "liga todos os motores de uma vez": ele reserva o que precisa do estoque, calcula quanto vai ser produzido, sugere quem vai trabalhar naquele evento, gera a lista do que falta comprar, calcula o lucro esperado e já atualiza o painel da Direção — tudo isso automaticamente, a partir de uma única confirmação comercial.

A partir daí, a operação acontece de verdade: compras são feitas junto aos fornecedores, os ingredientes entram no estoque com rastreabilidade completa (sabendo exatamente de onde vieram e até quando duram), a produção acontece consumindo esses ingredientes, e a equipe escalada trabalha no dia do evento.

Quando o evento termina, o sistema fecha as contas sozinho: compara o que foi gasto de verdade com o que estava previsto, calcula a margem real daquele evento específico, e atualiza — em tempo real — os números que aparecem no Dashboard CEO. Nada disso fica pendurado: toda despesa, todo pagamento recebido, todo extrato bancário importado, tudo passa pelo mesmo controle financeiro rigoroso, com a Inteligência Artificial ajudando a categorizar e conciliar, mas sempre pedindo confirmação humana quando há qualquer dúvida.

E o ciclo não para por aí: depois do evento, o sistema observa se aquele cliente está fidelizando, alimenta o time de marketing com esse dado, e tudo isso vira, ao mesmo tempo, uma **Meta** que a Direção está acompanhando — sempre visível, sempre atualizada, nunca desconectada do que realmente aconteceu na operação.

Esse é o THE CHARCOAL OS: um caminho único e contínuo, do primeiro "oi" do cliente até o número final no painel da Direção — sem retrabalho, sem dado duplicado, e sem nenhuma decisão importante tomada de forma automática e silenciosa demais para ser conferida por uma pessoa.

---

## 6. Resumo para o Proprietário

Construímos o "roteiro" completo de como o THE CHARCOAL OS vai funcionar no dia a dia: 30 processos documentados do início ao fim, mostrando exatamente o que acontece, em que ordem, e o que é automático versus o que precisa de uma pessoa decidir.

Isso é importante porque os documentos anteriores diziam **o que existe** (entidades), **como o sistema deve se comportar** (regras) e **o que cada pessoa consegue clicar** (funcionalidades) — mas nenhum deles amarrava tudo isso **no tempo**. Este documento é essa amarração: ele mostra, por exemplo, que confirmar um evento dispara automaticamente sete ou oito coisas ao mesmo tempo (reservar estoque, calcular produção, sugerir escala, gerar lista de compras, atualizar o painel), e mostra também onde exatamente uma pessoa da sua equipe precisa decidir algo, em vez do sistema decidir sozinho.

O benefício direto para o THE CHARCOAL OS é reduzir drasticamente o risco de "esquecer alguma etapa" quando o sistema for construído de verdade: quem for programar a tela de confirmação de evento vai ter, aqui, a lista exata de tudo que precisa acontecer — nem mais, nem menos.

Este documento se conecta diretamente aos quatro anteriores (o que existe, o que o sistema faz, o que o usuário faz, e agora como tudo acontece no tempo) e é, a partir de agora, a referência que orienta a próxima etapa: quando decidirmos como construir isso por dentro (arquitetura, banco de dados, telas, tecnologia), será a partir exatamente destes 30 fluxos — nenhuma dessas decisões técnicas foi tomada ainda.

---

## 7. TCOS QUALITY GATE EXECUTIVO

**1. Resumo Executivo**
Documentados 30 fluxos operacionais completos (FL-001 a FL-030), cada um com os 19 campos obrigatórios, mais Matriz de Integração entre Módulos e Mapa Operacional em linguagem simples. Nenhum documento anterior foi alterado.

**2. Estado atual do projeto**
Fases 000 a 003 (v1.2.0) encerradas e oficiais; Fase 004 em validação. Nenhuma fase técnica (Arquitetura, Banco de Dados, UX/UI, APIs, Desenvolvimento) foi iniciada.

**3. Documentos oficiais existentes**
Os 8 já registrados na Executive Memory (Framework v1.2.0, Domain Discovery, Questionnaire, Interview Roadmap, Domain Model, Business Rules Specification, Functional Specification v1.2.0, PROJECT_MEMORY.md), mais este documento em rascunho.

**4. Dependências desta fase**
30 entidades e Regras Globais do Domain Model; 47 Regras de Negócio; 27 módulos e 98 funcionalidades do Functional Specification — todos referenciados, nenhum reescrito.

**5. Pendências abertas**
Validação formal deste documento; confirmação de parâmetros de negócio do Módulo 24 (afeta diretamente as jornadas FL-007, FL-013, FL-014, FL-015); M-003A-03 e M-003A-04 (herdadas); decisão sobre retomar a entrevista de descoberta.

**6. Dúvidas encontradas**
Nenhuma nova além das já herdadas do Business Discovery (Q9/Q34 — política de cancelamento; Q61 — margem-alvo; Q73/Q75 — proporção e prazo de escala; Q76 — critério de fidelização; Q79–Q81 — pós-venda estruturado).

**7. Riscos ativos**
R-000-03/R-002-01, R-001-01/R-002-02, R-002A-01 — todos herdados e agora rastreáveis a jornadas específicas (ver item 6 desta seção).

**8. Novos riscos encontrados**
Nenhum risco novo — apenas o gap de granularidade já conhecido do Pós-venda (FL-030), reforçado por esta auditoria, sem constituir risco novo.

**9. Inconsistências encontradas**
Nenhuma. Duplicidades aparentes entre FL-003/FL-029 e entre FL-021/FL-026/FL-027/FL-028 foram resolvidas por escopo (visão geral vs. detalhamento; mesmo mecanismo em recortes diferentes, todos explicitamente solicitados).

**10. Conflitos entre documentos**
Nenhum.

**11. Funcionalidades sem fluxo**
F-072 a F-074 (Documentos) e F-080, F-081, F-083 (Administração do Sistema) — natureza transversal/administrativa, consumidas por todas as jornadas, sem jornada de negócio própria. Não é gap, é característica esperada desses módulos.

**12. Regras sem fluxo**
RN-004 (Fechamento de Período) e RN-047 (Tratamento Padrão de Alerta) — processos periódicos/administrativos, referenciados dentro de outras jornadas, sem jornada própria nesta lista de 30.

**13. Entidades sem fluxo**
Documento — mesma natureza transversal acima. Produto, Ingrediente, Pacote e Indicador aparecem dentro de fluxos de outras entidades, sem jornada nomeada própria — consistente com o gap M-003A-03 já registrado (não um gap novo).

**14. Módulos sem integração**
Nenhum — todos os 27 módulos aparecem em ao menos uma jornada ou na Matriz de Integração (Seção 4).

**15. Melhorias sugeridas**
- M-004-01: unificar, em fase técnica futura, os mecanismos descritos em FL-026/FL-027/FL-028 em um único motor de recálculo de Indicadores/Dashboards.
- M-004-02: quando a entrevista de descoberta for retomada, aprofundar especificamente a jornada de Pós-venda (FL-030), hoje a mais fracamente sustentada por Regras/Funcionalidades dedicadas.

**16. Impacto nas próximas fases**
Estes 30 fluxos passam a ser a referência obrigatória de comportamento no tempo para Arquitetura, Banco de Dados, UX/UI e Desenvolvimento — nenhuma dessas fases deve implementar uma sequência que contradiga o que está aqui documentado, sem registrar formalmente o motivo.

**17. Quality Score: 9,5/10**
Justificativa técnica: cobertura completa dos 30 fluxos obrigatórios com os 19 campos exigidos cada; auditoria genuína que identificou e categorizou corretamente sobreposições aparentes (resolvidas por escopo, não por omissão) e gaps herdados (não inventou cobertura onde não existe, como no caso do Pós-venda). Não é 10 porque a jornada de Pós-venda permanece estruturalmente mais fraca que as demais, refletindo uma lacuna real ainda não resolvida no negócio (não neste documento).

**18. Atualização do PROJECT_MEMORY.md:** ver commit correspondente.

**19. Estatísticas Finais**
- Quantidade de páginas: ~42 páginas equivalentes.
- Quantidade de fluxos: 30 (FL-001–FL-030).
- Quantidade de módulos: 27 (referenciados, 0 novos).
- Quantidade de entidades: 30 (referenciadas, 0 novas).
- Quantidade de regras: 47 (referenciadas, 0 novas).
- Quantidade de processos: 30 (um por fluxo).
- Quantidade de eventos: reutiliza os 89 eventos de domínio já catalogados no Domain Model (0 novos).
- Quantidade de integrações: 15 relações módulo-a-módulo mapeadas na Matriz de Integração (Seção 4.1).
- Quantidade de decisões: 1 (D-004-01, ver `PROJECT_MEMORY.md`).
- Quantidade de riscos: 0 novos (3 herdados).
- Quantidade de pendências: 4 (validação do documento + 3 herdadas).
- Quantidade de melhorias: 2 (M-004-01, M-004-02).
- Percentual estimado de maturidade do projeto: **48%** (subiu de 42% — o comportamento no tempo de todo o sistema está agora documentado e auditado; o que falta é majoritariamente decisão técnica — arquitetura, dados, UX, código — e confirmação de parâmetros reais de negócio).

---

*Fim do documento — THE CHARCOAL OS USER JOURNEYS AND SYSTEM FLOWS v1.0.0*
