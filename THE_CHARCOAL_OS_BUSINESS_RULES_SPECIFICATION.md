# THE CHARCOAL OS — BUSINESS RULES SPECIFICATION

**Documento:** TCOS-002A — Especificação de Regras de Negócio (complementar ao Domain Model)
**Projeto:** THE CHARCOAL OS
**Fase:** 002A — Business Rules Specification
**Status:** Rascunho para validação do proprietário
**Versão:** 1.0.0
**Documentos-base considerados (todos oficiais):** `THE_CHARCOAL_OS_DEVELOPMENT_FRAMEWORK.md` (v1.1.0), `PROJECT_MEMORY.md`, `THE_CHARCOAL_OS_ENTERPRISE_DOMAIN_DISCOVERY.md` (v1.0.0), `THE_CHARCOAL_OS_BUSINESS_DISCOVERY_QUESTIONNAIRE.md` (v1.0.0), `THE_CHARCOAL_OS_DISCOVERY_INTERVIEW_ROADMAP.md` (v1.0.0), `THE_CHARCOAL_OS_DOMAIN_MODEL.md` (v1.0.0)

**Regra permanente desta fase:** este documento **não altera, remove ou reescreve** nenhuma parte do `THE_CHARCOAL_OS_DOMAIN_MODEL.md`. Ele apenas **complementa** o Domain Model, traduzindo suas entidades, estados e Regras Globais (Seção 5 do Domain Model) em regras de comportamento concretas e acionáveis — a resposta a "o que o sistema deve fazer quando...".

---

## 0. Auditoria de Abertura e Estado Atual do Projeto

Todos os documentos oficiais listados acima foram lidos integralmente antes do início deste documento, em conformidade com a Seção 17 do Framework.

### Fases concluídas
- **Fase 000 — Governança:** APROVADA E ENCERRADA. Framework v1.1.0 é documentação oficial.
- **Fase 001 — Business Discovery:** APROVADA E ENCERRADA. Três documentos oficiais (Domain Discovery, Questionnaire, Interview Roadmap) — encerrada **antes** da execução da entrevista de descoberta (achado já registrado na Fase 002).
- **Fase 002 — Domain Model:** conteúdo **conceitualmente aprovado** pelo proprietário (comando `ALTERAR`, não `APROVADO`) — tratado, a partir de agora, como referência oficial e **imutável**, porém a fase permanece formalmente aberta até fechamento explícito, que deverá considerar também este complemento (TCOS-002A).

### Documentos oficiais
1. `THE_CHARCOAL_OS_DEVELOPMENT_FRAMEWORK.md` v1.1.0 — Aprovado.
2. `PROJECT_MEMORY.md` — memória cumulativa viva.
3. `THE_CHARCOAL_OS_ENTERPRISE_DOMAIN_DISCOVERY.md` v1.0.0 — Aprovado/Oficial.
4. `THE_CHARCOAL_OS_BUSINESS_DISCOVERY_QUESTIONNAIRE.md` v1.0.0 — Aprovado/Oficial (conteúdo; entrevista não executada).
5. `THE_CHARCOAL_OS_DISCOVERY_INTERVIEW_ROADMAP.md` v1.0.0 — Aprovado/Oficial (roteiro; entrevista não executada).
6. `THE_CHARCOAL_OS_DOMAIN_MODEL.md` v1.0.0 — Conceitualmente aprovado, tratado como referência oficial imutável.
7. `THE_CHARCOAL_OS_BUSINESS_RULES_SPECIFICATION.md` v1.0.0 — este documento (rascunho).

### Pendências abertas (herdadas)
- P-000-03 / P-002-01/02: confirmação do domínio de negócio e decisão sobre retomar a entrevista de descoberta.
- P-002-01: validação formal (comando `APROVADO`) do Domain Model, ainda pendente (tratado como `ALTERAR` com aprovação conceitual).

### Riscos ativos (herdados)
- **R-000-03 / R-002-01 (crítico):** hipótese de domínio de negócio (produção culinária em brasa/carvão via Eventos) segue sem confirmação. Este documento herda esse risco diretamente: várias regras abaixo (Consumo, Perdas, Rendimento, Precificação) dependem de parâmetros numéricos reais do negócio que ainda não foram informados — tratados explicitamente como **parâmetros configuráveis pendentes**, nunca como valores inventados.
- **R-001-01 / R-002-02:** custo de mão de obra e insumos de apoio podem não estar hoje incorporados ao custo real — refletido nas regras de Engenharia de Custos (RN-018, RN-036).
- **R-002-03:** Glossário Oficial do Framework desatualizado — não afeta este documento diretamente.

### Dependências para esta fase
- Todas as 30 entidades, estados e eventos já definidos no Domain Model (Seção 3) — reutilizados por nome, nunca redefinidos.
- As 9 categorias de Regras Globais do Domain Model (Seção 5) — este documento as **operacionaliza** em regras específicas e acionáveis; não as duplica nem as substitui.
- Os Princípios Fundamentais PF-01 a PF-12 do Framework, referenciados via as Convenções Gerais CG-01 a CG-07 já estabelecidas no Domain Model.
- A regra de nomenclatura D-000-07 (Receita = culinário; Receita Financeira = entrada financeira), aplicada de forma consistente em todas as regras abaixo.

**Nota de auditoria:** nenhuma inconsistência, conflito ou entidade repetida foi encontrada entre os documentos oficiais lidos. A única observação de consistência registrada é que "Engenharia de Custos" é tratada, desde o Domain Model, como uma função especializada dentro de Produção/Financeiro (não uma Área de Empresa própria, listada separadamente apenas na Seção 5 do Domain Discovery) — este documento mantém esse mesmo tratamento, sem propor mudança de estrutura organizacional.

---

## 1. Papel deste Documento

O Domain Model (TCOS-002) definiu **o que cada entidade é**. Este documento (TCOS-002A) define **o que o sistema faz, automaticamente, quando algo acontece** — o comportamento inteligente do THE CHARCOAL OS. Nenhuma regra aqui contradiz o Domain Model; toda regra referencia suas entidades, estados e eventos pelo nome exato já estabelecido. Nenhuma decisão de arquitetura técnica, banco de dados, UX ou API é tomada aqui.

## 2. Legenda e Convenções

- **RN-XXX:** identificador único de Regra de Negócio, numerado sequencialmente por ordem de aparição.
- Toda regra referencia as Convenções Gerais **CG-01 a CG-07** e os Princípios Fundamentais **PF-01 a PF-12**, já definidos no Framework/Domain Model, sem redefini-los.
- Onde uma regra depende de um **parâmetro numérico de negócio ainda não confirmado** (ex.: gramas de carne por pessoa, percentual de perda, margem-alvo), isso é declarado explicitamente no campo "Exceções" — o sistema deve tratar a ausência do parâmetro como uma condição a ser resolvida pelo usuário, nunca assumir um valor não confirmado.
- Os "módulos afetados" usam os nomes das Áreas da Empresa já definidos na Seção 5 do Domain Discovery: Comercial/CRM, Produção, Compras/Suprimentos, Estoque/Logística, Eventos/Operações, Financeiro, Marketing, Pessoas/Mão de Obra, Administrativo/Documentos, BI/Direção Executiva.

---

## 3. Regras de Negócio por Área

### 3.1 Dashboard CEO

#### RN-001 — Atualização em Tempo Real do Dashboard CEO
- **Objetivo:** garantir que o Dashboard CEO reflita, continuamente, o estado consolidado do negócio.
- **Evento que dispara:** qualquer Evento do Domínio já catalogado no Domain Model que afete um Indicador incluído no Dashboard CEO (ex.: Evento confirmado, Pagamento recebido, Despesa registrada, Produção concluída).
- **Condições:** o evento de origem afeta ao menos um Indicador do Dashboard CEO.
- **O que o sistema deve fazer:** recalcular automaticamente todo Indicador afetado e refletir a atualização no Dashboard CEO, sem ação manual do usuário.
- **Módulos afetados:** BI/Direção Executiva, e transitivamente todos os módulos.
- **Entidades alteradas:** Indicador (recalculado), Dashboard (atualizado) — nunca a entidade de origem.
- **Impacto financeiro:** nenhum direto; reflete impacto já ocorrido em outra entidade.
- **Impacto operacional:** visão sempre atualizada à Direção, sem esforço manual.
- **Exceções:** se um recálculo falhar por falta de dado de origem, o Dashboard deve sinalizar explicitamente que o dado pode estar desatualizado — nunca exibir silenciosamente um valor obsoleto.
- **Alertas ao usuário:** alerta de Indicador não recalculável.
- **Auditoria e histórico:** a atualização não gera histórico próprio — herda o histórico dos Indicadores subjacentes.

### 3.2 Financeiro Pessoal

#### RN-002 — Retirada Pessoal (Pró-labore) como Despesa Formal
- **Objetivo:** impedir que recursos saiam da empresa para uso pessoal sem registro formal, distorcendo o resultado do negócio.
- **Evento que dispara:** usuário registra uma retirada pessoal, ou o sistema identifica (via RN-043) uma transferência para conta pessoal.
- **Condições:** a retirada é identificada como de natureza pessoal.
- **O que o sistema deve fazer:** criar automaticamente uma Despesa da categoria "Retirada Pessoal", vinculada à Conta de origem; nunca tratá-la como Despesa operacional comum.
- **Módulos afetados:** Financeiro.
- **Entidades alteradas:** Despesa (criação), Pagamento.
- **Impacto financeiro:** protege o resultado operacional real da empresa contra distorção por retiradas pessoais.
- **Impacto operacional:** nenhum além do registro.
- **Exceções:** nenhuma — toda retirada pessoal é sempre registrada, mesmo pequena.
- **Alertas ao usuário:** alerta se o total de retiradas em um período comprometer o Fluxo de Caixa (parâmetro configurável).
- **Auditoria e histórico:** toda retirada pessoal é permanentemente rastreável, distinta de Despesa operacional.

### 3.3 Financeiro Empresarial

#### RN-003 — Apuração de Resultado por Evento
- **Objetivo:** conhecer a margem real de cada Evento individualmente, não apenas o total do período.
- **Evento que dispara:** "Evento concluído" e quitação das Despesas/Receita Financeira associadas.
- **Condições:** todas as Despesas diretas do Evento (produção, mão de obra, equipamento) estão vinculadas a ele.
- **O que o sistema deve fazer:** consolidar Receita Financeira recebida menos todas as Despesas vinculadas ao Evento (custo de Ficha Técnica realizado, mão de obra, Equipamento/Veículo), resultando na margem real.
- **Módulos afetados:** Financeiro, Produção, BI/Direção Executiva.
- **Entidades alteradas:** nenhuma alteração de cadastro — Indicador derivado.
- **Impacto financeiro:** Indicador de rentabilidade mais importante por Evento.
- **Impacto operacional:** orienta decisões futuras de precificação e aceitação de Eventos semelhantes.
- **Exceções:** Eventos com Despesas ainda não quitadas exibem margem "prevista", não "real".
- **Alertas ao usuário:** alerta se a margem real ficar abaixo do mínimo aceitável.
- **Auditoria e histórico:** a apuração de cada Evento é preservada permanentemente.

#### RN-004 — Fechamento de Período
- **Objetivo:** consolidar o resultado financeiro de um período de forma auditável.
- **Evento que dispara:** solicitação de fechamento de período (ex.: mensal) pela Direção/Financeiro.
- **Condições:** todas as Despesas e Receitas Financeiras previstas para o período têm status definido.
- **O que o sistema deve fazer:** consolidar entradas e saídas do período no Fluxo de Caixa; sinalizar pendências antes de considerar o período "fechado".
- **Módulos afetados:** Financeiro, BI/Direção Executiva.
- **Entidades alteradas:** nenhuma — consolidação derivada.
- **Impacto financeiro:** base do resultado mensal/anual do negócio.
- **Impacto operacional:** orienta decisões futuras de investimento e precificação.
- **Exceções:** um período não é fechado definitivamente com pendências abertas, sem alerta explícito.
- **Alertas ao usuário:** alerta de pendências não resolvidas ao tentar fechar.
- **Auditoria e histórico:** todo fechamento é registrado permanentemente.

### 3.4 Integração entre Vida Pessoal e a Empresa

#### RN-005 — Alerta de Lançamento de Natureza Ambígua
- **Objetivo:** evitar que um lançamento ambíguo (pessoal ou empresarial) seja classificado incorretamente de forma silenciosa.
- **Evento que dispara:** qualquer novo lançamento (manual ou importado) sem categoria clara de origem.
- **Condições:** o sistema não consegue associar o lançamento a nenhuma origem conhecida.
- **O que o sistema deve fazer:** nunca classificar automaticamente um lançamento ambíguo como Despesa/Receita Financeira operacional; sempre solicitar confirmação explícita da natureza (pessoal vs. empresarial) antes de incluí-lo em qualquer apuração de resultado.
- **Módulos afetados:** Financeiro.
- **Entidades alteradas:** Despesa/Receita Financeira (criação condicionada à confirmação).
- **Impacto financeiro:** protege a integridade de todos os Indicadores financeiros.
- **Impacto operacional:** exige interação humana pontual.
- **Exceções:** nenhuma.
- **Alertas ao usuário:** alerta obrigatório sempre que houver lançamento ambíguo.
- **Auditoria e histórico:** toda classificação é registrada com autor e data.

### 3.5 Eventos

#### RN-006 — Confirmação de Evento (Orquestração Automática)
- **Objetivo:** garantir que, ao confirmar um Evento, todos os módulos dependentes reajam automaticamente e de forma consistente, sem reentrada manual.
- **Evento que dispara:** "Evento confirmado" (Contrato assinado).
- **Condições:** Evento possui Orçamento aceito com Produtos/Pacotes definidos e Contrato assinado.
- **O que o sistema deve fazer, em sequência:**
  1. Reservar Estoque necessário (RN-032), com base no consumo calculado (RN-024 a RN-027);
  2. Calcular a Produção necessária (RN-016);
  3. Calcular a mão de obra necessária e sugerir Alocação de Funcionário (RN-037);
  4. Calcular o lucro previsto do Evento (Receita Financeira prevista − custo total da Ficha Técnica − despesas diretas previstas);
  5. Gerar a lista de Compras para itens com Estoque insuficiente (RN-030);
  6. Atualizar o Dashboard CEO e os Indicadores relevantes (RN-001, RN-040);
  7. Atualizar a previsão do Fluxo de Caixa;
  8. Registrar todo o processo no histórico do Evento.
- **Módulos afetados:** Produção, Estoque/Logística, Compras/Suprimentos, Financeiro, Pessoas/Mão de Obra, BI/Direção Executiva.
- **Entidades alteradas:** Evento (estado), Estoque (reserva), Produção (planejamento), Alocação de Funcionário (sugestão), Receita Financeira (prevista), Indicador/Dashboard.
- **Impacto financeiro:** define a expectativa de receita, custo e margem do Evento antes de sua execução.
- **Impacto operacional:** aciona toda a cadeia operacional a partir de uma única confirmação comercial.
- **Exceções:** se Estoque/capacidade produtiva/mão de obra forem insuficientes para o prazo, o sistema alerta **antes** de finalizar a confirmação — nunca confirma silenciosamente um Evento inviável.
- **Alertas ao usuário:** alerta de inviabilidade operacional; alerta de margem prevista abaixo do mínimo (RN-023).
- **Auditoria e histórico:** todo o encadeamento é registrado no histórico do Evento, com data e origem de cada cálculo.

#### RN-007 — Cancelamento de Evento
- **Objetivo:** tratar o cancelamento de forma consistente, liberando recursos reservados e aplicando a política financeira definida.
- **Evento que dispara:** "Evento cancelado".
- **Condições:** o Evento estava em qualquer estado a partir de "Confirmado".
- **O que o sistema deve fazer:** liberar automaticamente Estoque reservado, Equipamento/Veículo alocado e Alocações de Funcionário planejadas; aplicar a política de reembolso/multa definida no Contrato à Receita Financeira prevista; registrar o motivo.
- **Módulos afetados:** Produção, Estoque/Logística, Eventos/Operações, Pessoas/Mão de Obra, Financeiro.
- **Entidades alteradas:** Evento (estado), Estoque (liberação), Equipamento/Veículo (liberação), Alocação de Funcionário (cancelamento), Receita Financeira (ajuste).
- **Impacto financeiro:** pode gerar Despesa de compras já feitas e não canceláveis, ou retenção de sinal conforme política contratual.
- **Impacto operacional:** libera capacidade de Produção/equipe para outros Eventos.
- **Exceções:** a política de cancelamento/reembolso não está hoje formalmente definida (achado do Business Discovery, Q9/Q34); enquanto isso, o sistema alerta e exige decisão manual da Direção a cada cancelamento, em vez de aplicar uma regra automática não confirmada.
- **Alertas ao usuário:** alerta obrigatório à Direção a cada cancelamento, com impacto financeiro estimado.
- **Auditoria e histórico:** todo cancelamento, motivo e decisão financeira são registrados permanentemente.

### 3.6 CRM

#### RN-008 — Atribuição de Origem ao Lead
- **Objetivo:** garantir que todo Lead mantenha, permanentemente, o rastro de sua origem comercial.
- **Evento que dispara:** "Lead criado".
- **Condições:** o Lead foi originado de uma Campanha, indicação ou contato espontâneo.
- **O que o sistema deve fazer:** registrar a origem na criação; propagar o vínculo mesmo após a conversão em Cliente.
- **Módulos afetados:** Comercial/CRM, Marketing.
- **Entidades alteradas:** Lead (criação com origem).
- **Impacto financeiro:** base do cálculo de retorno de Campanha.
- **Impacto operacional:** nenhum direto.
- **Exceções:** Lead sem origem identificável é registrado como "origem não identificada", nunca descartado.
- **Alertas ao usuário:** nenhum.
- **Auditoria e histórico:** origem é imutável após o registro inicial, salvo correção explícita registrada.

### 3.7 Clientes

#### RN-009 — Conversão de Lead sem Duplicidade
- **Objetivo:** impedir que a conversão de um Lead gere um Cliente duplicado.
- **Evento que dispara:** "Lead convertido em Cliente".
- **Condições:** o sistema verifica correspondência com Cliente já cadastrado (nome + contato, ou outro critério).
- **O que o sistema deve fazer:** se houver correspondência, vincular o Lead ao Cliente existente (CG-02); caso contrário, criar o novo Cliente preservando o vínculo de origem.
- **Módulos afetados:** Comercial/CRM.
- **Entidades alteradas:** Cliente (criação ou vinculação), Lead (estado).
- **Impacto financeiro:** evita distorção de Indicadores de novos clientes vs. recorrentes.
- **Impacto operacional:** evita retrabalho de cadastro duplicado.
- **Exceções:** correspondência ambígua exige confirmação humana, nunca decisão automática.
- **Alertas ao usuário:** alerta de possível duplicidade quando a correspondência não for exata.
- **Auditoria e histórico:** toda vinculação/criação é registrada com a decisão tomada.

#### RN-010 — Fidelização de Cliente
- **Objetivo:** identificar automaticamente quando um Cliente se torna recorrente.
- **Evento que dispara:** "Evento concluído" de um Cliente que já teve Evento concluído anteriormente.
- **Condições:** o Cliente atinge o critério de recorrência definido pela Direção.
- **O que o sistema deve fazer:** marcar o Cliente com o atributo de fidelização; disponibilizar o dado ao Pós-venda/Marketing.
- **Módulos afetados:** Comercial/CRM, Marketing, BI/Direção Executiva.
- **Entidades alteradas:** Cliente (atributo de fidelização).
- **Impacto financeiro:** Indicador relevante de custo de aquisição/retenção.
- **Impacto operacional:** orienta ações diferenciadas de relacionamento.
- **Exceções:** o critério exato (número de Eventos, valor mínimo) é parâmetro pendente de confirmação (Q76 do Business Discovery).
- **Alertas ao usuário:** notificação informativa ao atingir o critério.
- **Auditoria e histórico:** a data de fidelização é registrada permanentemente.

### 3.8 Leads

#### RN-011 — Perda de Lead por Inatividade
- **Objetivo:** manter o funil comercial realista.
- **Evento que dispara:** decurso de um período configurável sem interação registrada com um Lead "Em qualificação".
- **Condições:** ausência de interação no período definido.
- **O que o sistema deve fazer:** sugerir (nunca decidir sozinho) a marcação como "Perdido", alertando o Comercial responsável antes de efetivar.
- **Módulos afetados:** Comercial/CRM.
- **Entidades alteradas:** Lead (estado, mediante confirmação).
- **Impacto financeiro:** melhora a precisão do Indicador de conversão.
- **Impacto operacional:** evita acúmulo de Leads não trabalhados.
- **Exceções:** o Comercial pode recusar a sugestão, registrando o motivo.
- **Alertas ao usuário:** alerta de Lead inativo há X dias (parâmetro configurável).
- **Auditoria e histórico:** toda sugestão e decisão são registradas.

### 3.9 Orçamentos

#### RN-012 — Cálculo de Preço a partir da Ficha Técnica
- **Objetivo:** garantir que nenhum Orçamento seja emitido com preço desconectado do custo real.
- **Evento que dispara:** inclusão de um Produto/Pacote em um Orçamento.
- **Condições:** o Produto possui Ficha Técnica Vigente.
- **O que o sistema deve fazer:** calcular o preço sugerido a partir do custo vigente somado à margem da Precificação (RN-022); permitir ajuste manual apenas dentro da alçada de desconto.
- **Módulos afetados:** Comercial/CRM, Produção, Financeiro.
- **Entidades alteradas:** Orçamento (valor calculado).
- **Impacto financeiro:** protege a margem mínima desde a primeira proposta.
- **Impacto operacional:** agiliza a montagem do Orçamento (gargalo identificado em Q26 do Business Discovery).
- **Exceções:** Produto sem Ficha Técnica Vigente não pode ser incluído sem alerta explícito.
- **Alertas ao usuário:** alerta se o preço ajustado ficar abaixo da margem mínima (RN-023).
- **Auditoria e histórico:** toda alteração manual de preço é registrada com autor e justificativa.

#### RN-013 — Expiração Automática de Orçamento
- **Objetivo:** manter o funil comercial atualizado.
- **Evento que dispara:** decurso da validade do Orçamento sem resposta do Cliente.
- **Condições:** Orçamento em "Enviado" ou "Em negociação" com validade expirada.
- **O que o sistema deve fazer:** marcar automaticamente como "Expirado"; notificar o Comercial responsável.
- **Módulos afetados:** Comercial/CRM.
- **Entidades alteradas:** Orçamento (estado).
- **Impacto financeiro:** melhora a precisão do funil de vendas previsto.
- **Impacto operacional:** libera o Comercial para reengajar ou desistir.
- **Exceções:** reabertura manual gera nova versão do Orçamento.
- **Alertas ao usuário:** alerta ao Comercial no momento da expiração.
- **Auditoria e histórico:** toda expiração/reabertura é registrada.

### 3.10 Contratos

#### RN-014 — Geração Automática a partir do Orçamento Aceito
- **Objetivo:** eliminar retrabalho manual na formalização.
- **Evento que dispara:** "Orçamento aceito".
- **Condições:** o Orçamento contém todos os dados obrigatórios.
- **O que o sistema deve fazer:** gerar automaticamente uma minuta de Contrato a partir do modelo padrão, pré-preenchida, para revisão e assinatura.
- **Módulos afetados:** Comercial/CRM, Administrativo/Documentos.
- **Entidades alteradas:** Contrato (criação), Documento (geração).
- **Impacto financeiro:** dispara previsão de Receita Financeira somente após a assinatura.
- **Impacto operacional:** reduz tempo de formalização comercial.
- **Exceções:** dados obrigatórios ausentes impedem geração automática.
- **Alertas ao usuário:** alerta de dados obrigatórios ausentes.
- **Auditoria e histórico:** geração de minuta é registrada, distinta da assinatura formal.

#### RN-015 — Aditivo Contratual
- **Objetivo:** formalizar mudança de escopo/valor/data de Contrato assinado, sem perda de histórico.
- **Evento que dispara:** necessidade de alteração em Contrato "Assinado"/"Em execução".
- **Condições:** alteração solicitada e aprovada pela área responsável.
- **O que o sistema deve fazer:** gerar aditivo formal, preservando o Contrato original; atualizar a Receita Financeira prevista se houver mudança de valor.
- **Módulos afetados:** Comercial/CRM, Administrativo/Documentos, Financeiro.
- **Entidades alteradas:** Contrato (nova versão via aditivo), Receita Financeira (ajuste), Documento.
- **Impacto financeiro:** pode aumentar/reduzir a Receita Financeira prevista.
- **Impacto operacional:** pode impactar planejamento operacional já feito.
- **Exceções:** aditivo que reduz escopo após planejamento iniciado alerta sobre impacto em recursos já reservados.
- **Alertas ao usuário:** alerta de impacto em Produção/Alocação/Estoque já reservados.
- **Auditoria e histórico:** todo aditivo é permanentemente vinculado ao Contrato original.

### 3.11 Produção

#### RN-016 — Planejamento Automático a partir de Evento Confirmado
- **Objetivo:** transformar o escopo comercial confirmado em plano de produção executável.
- **Evento que dispara:** "Evento confirmado".
- **Condições:** Evento com Produtos/Pacotes com Ficha Técnica vigente e número de convidados definido.
- **O que o sistema deve fazer:** gerar a(s) Produção(ões) necessárias, com quantidade calculada (RN-024 a RN-027), vinculadas ao Evento, com data compatível com o prazo mínimo de antecedência necessário.
- **Módulos afetados:** Produção, Compras/Suprimentos, Estoque/Logística.
- **Entidades alteradas:** Produção (criação, "Planejada").
- **Impacto financeiro:** base do custo previsto do Evento.
- **Impacto operacional:** define a agenda de produção da equipe.
- **Exceções:** prazo insuficiente para produção/compra gera alerta antes de confirmar o planejamento.
- **Alertas ao usuário:** alerta de prazo insuficiente.
- **Auditoria e histórico:** todo plano gerado é registrado e vinculado ao Evento de origem.

#### RN-017 — Comparação Planejado vs. Real
- **Objetivo:** dar visibilidade a desvios de execução.
- **Evento que dispara:** "Produção concluída".
- **Condições:** existe um plano de Produção (RN-016) para comparação.
- **O que o sistema deve fazer:** comparar quantidade planejada vs. produzida e consumo planejado vs. real; registrar o desvio (RN-028/029).
- **Módulos afetados:** Produção.
- **Entidades alteradas:** Produção (registro de desvio).
- **Impacto financeiro:** alimenta a apuração de margem real do Evento (RN-003).
- **Impacto operacional:** base para revisão de parâmetros de consumo/perda.
- **Exceções:** nenhuma — todo desvio é sempre registrado.
- **Alertas ao usuário:** alerta de desvio acima de limite aceitável (parâmetro configurável).
- **Auditoria e histórico:** histórico permanente de planejado vs. real por Produção.

### 3.12 Engenharia de Custos

#### RN-018 — Cálculo de Custo Total do Evento
- **Objetivo:** consolidar o custo real total de um Evento para comparação com a Receita Financeira.
- **Evento que dispara:** conclusão de todas as Produções vinculadas a um Evento (ou sob demanda, para acompanhamento prévio).
- **Condições:** Produções, Alocações de Funcionário e Despesas diretas do Evento registradas.
- **O que o sistema deve fazer:** somar custo real de Ingrediente consumido, custo de mão de obra e demais Despesas diretas, obtendo o custo total real.
- **Módulos afetados:** Produção, Pessoas/Mão de Obra, Financeiro.
- **Entidades alteradas:** nenhuma alteração de cadastro — Indicador derivado.
- **Impacto financeiro:** base da apuração de margem real por Evento (RN-003).
- **Impacto operacional:** informa decisões futuras de precificação.
- **Exceções:** com Despesa/Produção pendente, o custo é "parcial", não "final".
- **Alertas ao usuário:** alerta se o custo real exceder significativamente o previsto no Orçamento.
- **Auditoria e histórico:** o cálculo final é preservado permanentemente, vinculado ao Evento.

#### RN-019 — Recálculo Automático por Atualização de Ingrediente
- **Objetivo:** manter toda Ficha Técnica sempre refletindo o custo real vigente.
- **Evento que dispara:** "Custo de Ingrediente atualizado".
- **Condições:** o Ingrediente é usado em ao menos uma Ficha Técnica Vigente.
- **O que o sistema deve fazer:** recalcular automaticamente o custo total de toda Ficha Técnica afetada; alertar o Comercial sobre Orçamentos ainda não aceitos que usam o custo antigo.
- **Módulos afetados:** Produção, Comercial/CRM.
- **Entidades alteradas:** Ficha Técnica (recálculo).
- **Impacto financeiro:** protege a margem de Orçamentos ainda não fechados.
- **Impacto operacional:** nenhum direto.
- **Exceções:** Orçamentos já aceitos (virados Contrato) não são recalculados retroativamente.
- **Alertas ao usuário:** alerta ao Comercial sobre Orçamentos abertos impactados.
- **Auditoria e histórico:** toda atualização e seu efeito em cascata são registrados.

### 3.13 Receitas

#### RN-020 — Versionamento de Receita
- **Objetivo:** nunca perder o histórico de evolução de uma Receita.
- **Evento que dispara:** "Receita revisada".
- **Condições:** a Receita estava "Aprovada" e sofre alteração.
- **O que o sistema deve fazer:** criar nova versão, preservando a anterior; propagar a necessidade de nova versão da Ficha Técnica associada.
- **Módulos afetados:** Produção.
- **Entidades alteradas:** Receita (nova versão), Ficha Técnica (nova versão associada).
- **Impacto financeiro:** pode alterar o custo de produção do Produto associado.
- **Impacto operacional:** equipe de Produção deve ser informada antes da próxima execução.
- **Exceções:** nenhuma.
- **Alertas ao usuário:** alerta à equipe de Produção sobre nova versão vigente.
- **Auditoria e histórico:** todas as versões anteriores permanecem consultáveis.

### 3.14 Fichas Técnicas

#### RN-021 — Bloqueio de Produto sem Ficha Técnica Vigente
- **Objetivo:** impedir venda de Produto sem lastro de custo conhecido.
- **Evento que dispara:** tentativa de incluir um Produto em Orçamento.
- **Condições:** Produto sem Ficha Técnica "Vigente".
- **O que o sistema deve fazer:** bloquear a inclusão e alertar, exigindo Ficha Técnica vigente antes.
- **Módulos afetados:** Comercial/CRM, Produção.
- **Entidades alteradas:** nenhuma (bloqueio preventivo).
- **Impacto financeiro:** evita venda sem controle de margem.
- **Impacto operacional:** força disciplina de custo definido antes da venda.
- **Exceções:** nenhuma — regra sem exceção, por proteção de margem.
- **Alertas ao usuário:** alerta bloqueante.
- **Auditoria e histórico:** toda tentativa bloqueada é registrada.

### 3.15 Precificação

#### RN-022 — Cálculo de Preço (Custo + Margem)
- **Objetivo:** garantir que todo preço tenha lastro de custo e margem definida.
- **Evento que dispara:** definição/atualização de preço de Produto/Pacote.
- **Condições:** Ficha Técnica Vigente e margem-alvo definida.
- **O que o sistema deve fazer:** calcular preço a partir do custo vigente e da margem-alvo (fórmula definida pela Direção); permitir revisão manual apenas dentro da alçada de desconto.
- **Módulos afetados:** Comercial/CRM, Produção, Financeiro.
- **Entidades alteradas:** Produto/Pacote (preço).
- **Impacto financeiro:** regra central de proteção de rentabilidade.
- **Impacto operacional:** nenhum direto.
- **Exceções:** a fórmula exata e o valor da margem-alvo são parâmetros de negócio pendentes de confirmação (Q61 do Business Discovery).
- **Alertas ao usuário:** alerta se o preço resultante ficar fora de uma faixa esperada (parâmetro configurável).
- **Auditoria e histórico:** toda mudança de preço registra o custo e a margem vigentes no momento.

#### RN-023 — Alerta de Margem Abaixo do Mínimo
- **Objetivo:** impedir Orçamentos/Contratos com margem inferior ao mínimo aceitável.
- **Evento que dispara:** ajuste manual de preço em Orçamento que resulte em margem abaixo do mínimo.
- **Condições:** margem mínima definida pela Direção (Regra Global Financeira do Domain Model).
- **O que o sistema deve fazer:** alertar no momento do ajuste; exigir aprovação de alçada superior para prosseguir.
- **Módulos afetados:** Comercial/CRM, Financeiro.
- **Entidades alteradas:** Orçamento (aprovação de exceção, se concedida).
- **Impacto financeiro:** última linha de defesa da rentabilidade mínima.
- **Impacto operacional:** pode atrasar o fechamento comercial em casos de exceção.
- **Exceções:** a Direção pode aprovar margem abaixo do mínimo, com justificativa registrada.
- **Alertas ao usuário:** alerta bloqueante até aprovação de alçada superior.
- **Auditoria e histórico:** toda exceção aprovada é registrada com justificativa e responsável.

### 3.16 Consumo por Pessoa

#### RN-024 — Cálculo de Consumo por Convidado
- **Objetivo:** calcular a quantidade necessária de cada Ingrediente/Produto com base no número de convidados.
- **Evento que dispara:** "Evento confirmado" ou alteração no número de convidados de um Evento já confirmado.
- **Condições:** Produtos/Pacotes com Ficha Técnica vigente; parâmetro de consumo médio por pessoa definido para cada item.
- **O que o sistema deve fazer:** multiplicar o parâmetro de consumo médio por pessoa (configurável por Produto — RN-025) pelo número de convidados, obtendo a quantidade total necessária; alimenta o planejamento de Produção (RN-016) e a lista de Compras (RN-030).
- **Módulos afetados:** Produção, Compras/Suprimentos, Estoque/Logística.
- **Entidades alteradas:** Produção (quantidade planejada).
- **Impacto financeiro:** base do custo total previsto do Evento.
- **Impacto operacional:** define volume de Produção e Compra necessários.
- **Exceções:** se o parâmetro de consumo por pessoa não estiver definido, o sistema não calcula automaticamente — alerta e exige definição manual (valor exato pendente de confirmação do proprietário, risco herdado R-000-03/R-001-01).
- **Alertas ao usuário:** alerta se o parâmetro não estiver definido; alerta se a quantidade calculada exceder o Estoque disponível.
- **Auditoria e histórico:** toda alteração no parâmetro gera nova versão com histórico.

### 3.17 Consumo Conforme Tipo de Evento

#### RN-025 — Ajuste de Consumo por Tipo de Evento
- **Objetivo:** permitir que o consumo por pessoa varie conforme o tipo de Evento (ex.: corporativo vs. casamento).
- **Evento que dispara:** definição/alteração do tipo de Evento no Orçamento.
- **Condições:** existência (ou não) de parâmetro de consumo específico por combinação Produto + tipo de Evento.
- **O que o sistema deve fazer:** ao calcular o consumo (RN-024), verificar se há parâmetro específico para o tipo de Evento; se houver, usá-lo no lugar do padrão geral.
- **Módulos afetados:** Produção, Comercial/CRM.
- **Entidades alteradas:** nenhuma alteração de cadastro — parâmetro consultado.
- **Impacto financeiro:** pode aumentar/reduzir o custo previsto conforme o perfil de consumo do tipo.
- **Impacto operacional:** refina a precisão do planejamento de Produção/Compras.
- **Exceções:** ausência de parâmetro específico não bloqueia o cálculo — usa-se o padrão geral, com alerta informativo.
- **Alertas ao usuário:** alerta informativo de uso do padrão geral.
- **Auditoria e histórico:** toda definição de parâmetro específico é registrada com histórico.

### 3.18 Consumo Conforme Acompanhamentos

#### RN-026 — Cálculo de Consumo com Múltiplos Acompanhamentos
- **Objetivo:** calcular corretamente o consumo total quando um Evento inclui múltiplos acompanhamentos.
- **Evento que dispara:** definição do Orçamento com mais de um acompanhamento selecionado.
- **Condições:** cada acompanhamento é um Produto com Ficha Técnica e parâmetro de consumo próprios.
- **O que o sistema deve fazer:** somar o consumo calculado (RN-024/025) de cada acompanhamento individualmente — nunca dividir o consumo do prato principal entre os acompanhamentos de forma genérica.
- **Módulos afetados:** Produção, Compras/Suprimentos.
- **Entidades alteradas:** nenhuma alteração de cadastro.
- **Impacto financeiro:** o custo total é a soma dos custos individuais, nunca uma média genérica (PF-03).
- **Impacto operacional:** define a lista de Produção e Compras detalhada por item.
- **Exceções:** acompanhamento sem parâmetro de consumo definido segue a mesma exceção da RN-024.
- **Alertas ao usuário:** alerta se o número de acompanhamentos exceder um limite operacional razoável (parâmetro configurável).
- **Auditoria e histórico:** a composição de acompanhamentos de cada Orçamento/Evento é registrada permanentemente.

### 3.19 Perdas de Limpeza

#### RN-027 — Fator de Perda de Limpeza na Compra
- **Objetivo:** garantir que a quantidade comprada considere a perda inerente à limpeza/preparo (aparas, ossos, partes não aproveitáveis).
- **Evento que dispara:** cálculo de necessidade de Compra a partir de uma Produção planejada.
- **Condições:** existe um fator de perda de limpeza definido na Ficha Técnica.
- **O que o sistema deve fazer:** aplicar o fator sobre a quantidade líquida necessária, resultando na quantidade bruta a comprar (bruta = líquida ÷ (1 − % perda)), alimentando a lista de Compras (RN-030).
- **Módulos afetados:** Produção, Compras/Suprimentos.
- **Entidades alteradas:** nenhuma — cálculo derivado da Ficha Técnica.
- **Impacto financeiro:** aumenta o custo real de compra frente ao custo "líquido" ingênuo; deve estar refletido na Ficha Técnica (PF-03).
- **Impacto operacional:** evita ruptura de Estoque por subestimar a quantidade real.
- **Exceções:** fator não definido para um Ingrediente é assumido como zero, com alerta de que essa suposição pode ser imprecisa.
- **Alertas ao usuário:** alerta quando o fator não está definido; alerta quando a perda real (RN-028/029) diverge significativamente do fator previsto.
- **Auditoria e histórico:** toda alteração no fator gera nova versão da Ficha Técnica.

### 3.20 Perdas de Produção

#### RN-028 — Registro de Perda de Produção
- **Objetivo:** registrar a perda ocorrida durante a execução da Produção (queima, redução de peso na cocção, descarte por erro), distinta da perda de limpeza.
- **Evento que dispara:** "Produção concluída".
- **Condições:** a Produção registra quantidade consumida e quantidade obtida.
- **O que o sistema deve fazer:** calcular a perda como a diferença entre o previsto (já considerando a perda de limpeza) e o efetivamente obtido; registrar vinculada à Produção específica, nunca diluída em média do período.
- **Módulos afetados:** Produção.
- **Entidades alteradas:** Produção (registro de perda real).
- **Impacto financeiro:** perdas acima do esperado corroem a margem já calculada no Orçamento — visível na apuração de resultado (RN-003).
- **Impacto operacional:** indica necessidade de treinamento, ajuste de processo ou revisão do fator esperado.
- **Exceções:** perda zero ou negativa (rendimento acima do esperado) também é registrada, sem tratamento como erro.
- **Alertas ao usuário:** alerta quando a perda de um Evento excede um limite aceitável (parâmetro configurável).
- **Auditoria e histórico:** toda perda é registrada permanentemente, vinculada à Produção e ao Evento.

### 3.21 Rendimento

#### RN-029 — Verificação de Rendimento Real vs. Previsto
- **Objetivo:** verificar se a quantidade de porções obtida corresponde ao rendimento previsto na Ficha Técnica.
- **Evento que dispara:** "Produção concluída".
- **Condições:** a Ficha Técnica define um rendimento esperado.
- **O que o sistema deve fazer:** comparar rendimento real (Produto produzido ÷ Ingrediente consumido) com o previsto; se insuficiente para atender ao número de convidados, alertar imediatamente para decisão operacional (produção emergencial ou ajuste de porção).
- **Módulos afetados:** Produção, Eventos/Operações.
- **Entidades alteradas:** Produção (registro de rendimento real).
- **Impacto financeiro:** rendimento abaixo do esperado aumenta o custo efetivo por porção.
- **Impacto operacional:** pode exigir produção emergencial antes do Evento.
- **Exceções:** rendimento acima do esperado é registrado como oportunidade de ajuste futuro do parâmetro.
- **Alertas ao usuário:** alerta imediato (alta prioridade) quando o rendimento for insuficiente para o número de convidados do Evento vinculado.
- **Auditoria e histórico:** todo rendimento real é registrado permanentemente, formando a base histórica de revisão do parâmetro.

### 3.22 Compras

#### RN-030 — Geração Automática de Lista de Compras
- **Objetivo:** eliminar o cálculo manual do que precisa ser comprado.
- **Evento que dispara:** "Produção planejada" (RN-016) ou verificação periódica de ponto de reposição.
- **Condições:** a quantidade necessária (RN-024 a RN-027) excede o saldo em Estoque.
- **O que o sistema deve fazer:** gerar sugestão de lista de Compras com itens e quantidades faltantes, agrupada por Fornecedor preferencial quando definido.
- **Módulos afetados:** Compras/Suprimentos, Estoque/Logística, Produção.
- **Entidades alteradas:** nenhuma alteração direta — gera sugestão a confirmar.
- **Impacto financeiro:** base do planejamento de Despesa futura.
- **Impacto operacional:** elimina o gargalo manual identificado no Business Discovery.
- **Exceções:** itens sem Fornecedor definido são destacados para decisão manual.
- **Alertas ao usuário:** alerta de item sem Fornecedor; alerta de prazo de compra incompatível com a data do Evento.
- **Auditoria e histórico:** toda lista sugerida e a decisão sobre ela são registradas.

#### RN-031 — Recebimento e Conferência de Compra
- **Objetivo:** garantir que só entre em Estoque o que foi realmente conferido.
- **Evento que dispara:** "Compra recebida".
- **Condições:** Compra em "Pedido enviado" ou "Recebida".
- **O que o sistema deve fazer:** exigir conferência de quantidade e (quando aplicável) validade antes de mudar para "Conferida" e gerar Estoque/Lote.
- **Módulos afetados:** Compras/Suprimentos, Estoque/Logística.
- **Entidades alteradas:** Compra (estado), Estoque, Lote, Despesa.
- **Impacto financeiro:** gera a Despesa formal apenas após conferência.
- **Impacto operacional:** garante que o saldo de Estoque reflita a realidade física.
- **Exceções:** divergência entre pedido e recebido é registrada e pode gerar devolução/renegociação.
- **Alertas ao usuário:** alerta de divergência entre pedido e recebido.
- **Auditoria e histórico:** toda conferência é registrada com responsável e data.

### 3.23 Estoque

#### RN-032 — Baixa Automática de Estoque
- **Objetivo:** manter o saldo sempre atualizado sem lançamento manual.
- **Evento que dispara:** "Produção iniciada"/"concluída" (consumo) ou venda direta de Produto.
- **Condições:** saldo suficiente ou reserva já feita (RN-006).
- **O que o sistema deve fazer:** baixar automaticamente o saldo, sempre referenciando o(s) Lote(s) consumido(s).
- **Módulos afetados:** Estoque/Logística, Produção.
- **Entidades alteradas:** Estoque (saldo), Lote (consumo).
- **Impacto financeiro:** nenhum direto — reflete consumo já custeado na Ficha Técnica.
- **Impacto operacional:** garante visibilidade real de disponibilidade.
- **Exceções:** saldo insuficiente bloqueia a baixa e alerta, exigindo decisão (compra emergencial, substituição).
- **Alertas ao usuário:** alerta de saldo insuficiente.
- **Auditoria e histórico:** toda baixa é registrada com origem e Lote consumido.

#### RN-033 — Alerta de Ponto de Reposição
- **Objetivo:** evitar ruptura de Estoque de itens críticos.
- **Evento que dispara:** saldo atinge ou fica abaixo do ponto de reposição mínimo.
- **Condições:** item com ponto de reposição configurado.
- **O que o sistema deve fazer:** gerar alerta para Compras/Estoque; alimentar a lista de Compras (RN-030) mesmo sem Evento específico que o exija.
- **Módulos afetados:** Estoque/Logística, Compras/Suprimentos.
- **Entidades alteradas:** nenhuma — apenas alerta/sugestão.
- **Impacto financeiro:** evita compras emergenciais mais caras.
- **Impacto operacional:** evita ruptura que comprometeria um Evento.
- **Exceções:** itens sem ponto de reposição definido não geram este alerta.
- **Alertas ao usuário:** alerta de estoque baixo.
- **Auditoria e histórico:** histórico de disparo e tratamento de cada alerta.

### 3.24 Lotes

#### RN-034 — Rastreabilidade e Alerta de Validade
- **Objetivo:** garantir segurança alimentar e evitar uso de itens vencidos.
- **Evento que dispara:** aproximação da validade de um Lote (prazo configurável) ou tentativa de uso de Lote vencido.
- **Condições:** o Lote possui data de validade definida.
- **O que o sistema deve fazer:** alertar sobre Lotes próximos do vencimento, priorizando seu uso ("primeiro que vence, primeiro que sai"); bloquear uso de Lote já vencido em nova Produção.
- **Módulos afetados:** Estoque/Logística, Produção.
- **Entidades alteradas:** Lote (estado "Vencido"/"Descartado").
- **Impacto financeiro:** evita perda de material e desperdício.
- **Impacto operacional:** orienta a ordem de uso do Estoque no dia a dia.
- **Exceções:** Lote sem validade aplicável não gera este alerta.
- **Alertas ao usuário:** alerta de validade próxima; bloqueio com alerta ao usar Lote vencido.
- **Auditoria e histórico:** todo vencimento/descarte é registrado permanentemente, com quantidade e motivo.

### 3.25 Equipamentos

#### RN-035 — Verificação de Disponibilidade de Equipamento
- **Objetivo:** evitar conflito de alocação do mesmo Equipamento em Eventos simultâneos.
- **Evento que dispara:** tentativa de Alocação de um Equipamento a um Evento.
- **Condições:** Equipamento já "Alocado" a outro Evento com sobreposição, ou "Em manutenção".
- **O que o sistema deve fazer:** bloquear a alocação conflitante e sugerir alternativa.
- **Módulos afetados:** Eventos/Operações, Produção.
- **Entidades alteradas:** nenhuma — bloqueio preventivo.
- **Impacto financeiro:** pode indicar necessidade de investimento adicional em Equipamento.
- **Impacto operacional:** evita falha de execução por falta de Equipamento no dia do Evento.
- **Exceções:** nenhuma — bloqueio rígido, dada a gravidade de um conflito não resolvido.
- **Alertas ao usuário:** alerta bloqueante com sugestão de alternativa.
- **Auditoria e histórico:** toda tentativa de conflito e sua resolução são registradas.

### 3.26 Funcionários

#### RN-036 — Cálculo de Custo de Mão de Obra
- **Objetivo:** garantir que o custo de mão de obra de cada Evento/Produção seja conhecido e correto.
- **Evento que dispara:** "Alocação de Funcionário realizada".
- **Condições:** a Alocação possui valor acordado (fixo ou por regra de função).
- **O que o sistema deve fazer:** consolidar o custo de todas as Alocações Realizadas vinculadas a um Evento/Produção, alimentando a Engenharia de Custos (RN-018).
- **Módulos afetados:** Pessoas/Mão de Obra, Financeiro.
- **Entidades alteradas:** Despesa (custo de mão de obra), vinculada ao Evento.
- **Impacto financeiro:** parte essencial do custo real do Evento — hoje potencialmente subestimado (risco herdado R-001-01/R-002-02).
- **Impacto operacional:** nenhum direto.
- **Exceções:** Alocação sem valor definido gera alerta e impede fechar o custo do Evento como "final".
- **Alertas ao usuário:** alerta de Alocação sem valor definido.
- **Auditoria e histórico:** todo custo é rastreável por Funcionário, Alocação e Evento.

### 3.27 Escalas

#### RN-037 — Sugestão de Escala Conforme Porte do Evento
- **Objetivo:** reduzir trabalho manual e risco de erro de dimensionamento de equipe.
- **Evento que dispara:** "Evento confirmado" (parte da RN-006).
- **Condições:** existe parâmetro de proporção de Funcionário por convidados ou tipo de Evento.
- **O que o sistema deve fazer:** sugerir quantidade e função de Funcionários necessários, com base no parâmetro; permitir ajuste manual.
- **Módulos afetados:** Pessoas/Mão de Obra, Eventos/Operações.
- **Entidades alteradas:** Alocação de Funcionário (sugestão, "Planejada").
- **Impacto financeiro:** alimenta o custo de mão de obra previsto (RN-018).
- **Impacto operacional:** reduz risco de falta/sobra de equipe no dia do Evento.
- **Exceções:** parâmetro de proporção pendente de confirmação (Q73 do Business Discovery); na ausência, o sistema alerta e não sugere automaticamente.
- **Alertas ao usuário:** alerta de escala não confirmada a X dias do Evento (parâmetro ligado a Q75).
- **Auditoria e histórico:** toda sugestão e ajuste manual são registrados.

### 3.28 Marketing

#### RN-038 — Atribuição de Retorno de Campanha
- **Objetivo:** medir o retorno real de cada Campanha.
- **Evento que dispara:** "Lead convertido em Cliente" e/ou "Contrato assinado" para um Cliente com Campanha de origem.
- **Condições:** o Lead de origem está vinculado a uma Campanha.
- **O que o sistema deve fazer:** atribuir a conversão e o valor do Contrato à Campanha de origem, alimentando o Indicador de retorno.
- **Módulos afetados:** Marketing, BI/Direção Executiva.
- **Entidades alteradas:** nenhuma alteração de cadastro — Indicador derivado.
- **Impacto financeiro:** base do cálculo de retorno sobre investimento em Marketing.
- **Impacto operacional:** orienta decisões futuras de investimento em canais.
- **Exceções:** Cliente sem Lead/Campanha de origem não é atribuído a nenhuma Campanha (origem direta, não erro).
- **Alertas ao usuário:** nenhum obrigatório.
- **Auditoria e histórico:** toda atribuição é permanente e consultável historicamente.

### 3.29 Dashboards

#### RN-039 — Composição de Dashboard por Indicador
- **Objetivo:** garantir que qualquer Dashboard seja composto exclusivamente por Indicadores já definidos e auditáveis.
- **Evento que dispara:** criação/atualização de um Dashboard.
- **Condições:** cada item incluído corresponde a um Indicador já cadastrado.
- **O que o sistema deve fazer:** impedir a inclusão de um valor "solto" (sem Indicador correspondente).
- **Módulos afetados:** BI/Direção Executiva, e a área dona de cada Dashboard específico.
- **Entidades alteradas:** Dashboard (composição).
- **Impacto financeiro:** nenhum direto; garante confiabilidade de qualquer leitura de gestão.
- **Impacto operacional:** padroniza a governança de todos os painéis, não apenas o executivo.
- **Exceções:** nenhuma.
- **Alertas ao usuário:** alerta ao tentar incluir dado sem Indicador correspondente.
- **Auditoria e histórico:** toda composição é registrada com histórico de alterações.

### 3.30 Indicadores

#### RN-040 — Cálculo Único e Auditável de Indicador
- **Objetivo:** garantir que cada Indicador tenha exatamente uma fórmula.
- **Evento que dispara:** definição ou revisão de fórmula de um Indicador.
- **Condições:** —
- **O que o sistema deve fazer:** impedir a existência de duas fórmulas diferentes simultâneas para o mesmo Indicador; ao revisar, preservar a fórmula anterior associada aos valores já calculados com ela.
- **Módulos afetados:** BI/Direção Executiva.
- **Entidades alteradas:** Indicador (nova versão de fórmula).
- **Impacto financeiro:** nenhum direto; protege a confiabilidade de todo Indicador financeiro.
- **Impacto operacional:** nenhum direto.
- **Exceções:** nenhuma.
- **Alertas ao usuário:** alerta ao revisar fórmula, informando que comparações com o período anterior podem não ser diretas.
- **Auditoria e histórico:** toda fórmula, passada e presente, é preservada e rastreável.

### 3.31 Inteligência Artificial

#### RN-041 — Sugestão Auditável e Reversível (Regra Geral de IA)
- **Objetivo:** garantir que toda atuação de IA respeite o Princípio Fundamental PF-06.
- **Evento que dispara:** qualquer ação de IA sobre qualquer entidade do Domain Model.
- **Condições:** —
- **O que o sistema deve fazer:** nunca aplicar automaticamente uma decisão de IA que altere dado financeiro, de cliente ou de preço sem confirmação humana explícita, salvo ações de baixo risco e reversíveis pré-aprovadas pela Direção; registrar toda sugestão e a decisão humana sobre ela.
- **Módulos afetados:** todos os módulos onde IA atuar.
- **Entidades alteradas:** variável conforme a sugestão aceita.
- **Impacto financeiro:** variável; sempre rastreável à decisão humana que a autorizou.
- **Impacto operacional:** preserva a confiança da equipe na IA como assistente, não substituto de decisão.
- **Exceções:** ações de baixo risco pré-aprovadas podem ser automáticas, desde que reversíveis e registradas.
- **Alertas ao usuário:** toda sugestão relevante é sinalizada como tal, nunca como fato indiscutível.
- **Auditoria e histórico:** toda sugestão, aceite, recusa ou reversão é registrada permanentemente.

#### RN-042 — Previsão de Demanda
- **Objetivo:** apoiar o planejamento de Compras/Produção com base em histórico e sazonalidade.
- **Evento que dispara:** ciclo periódico de planejamento ou sob demanda.
- **Condições:** histórico suficiente de Eventos/Produção para uma previsão minimamente confiável.
- **O que o sistema deve fazer:** sugerir previsão de demanda de Ingredientes/Produtos para o período seguinte, apoiando (não substituindo) a decisão de Compras.
- **Módulos afetados:** Compras/Suprimentos, Produção, BI/Direção Executiva.
- **Entidades alteradas:** nenhuma alteração direta — gera sugestão.
- **Impacto financeiro:** pode reduzir compras emergenciais e desperdício por excesso.
- **Impacto operacional:** apoia decisão, nunca decide sozinho (RN-041).
- **Exceções:** histórico insuficiente impede previsão confiável — o sistema declara essa limitação explicitamente.
- **Alertas ao usuário:** alerta de baixa confiança quando o histórico for insuficiente.
- **Auditoria e histórico:** toda previsão gerada e seu uso na decisão de Compra são registrados.

### 3.32 Importação Automática de Extratos Bancários

#### RN-043 — Importação e Sugestão de Classificação de Extrato Bancário
- **Objetivo:** reduzir o trabalho manual de registrar Pagamentos e permitir conciliação assistida.
- **Evento que dispara:** "Extrato bancário importado".
- **Condições:** existe uma Conta cadastrada correspondente ao extrato.
- **O que o sistema deve fazer:**
  1. Identificar lançamentos de entrada (candidatos a Receita Financeira/Pagamento) e de saída (candidatos a Despesa/Pagamento);
  2. Sugerir categoria com base em histórico de lançamentos semelhantes (PF-06);
  3. Sugerir conciliação com Despesas/Receitas Financeiras já previstas e não quitadas;
  4. Identificar possíveis duplicidades;
  5. Solicitar confirmação explícita sempre que houver ambiguidade;
  6. Somente após confirmação, efetivar o Pagamento e atualizar Fluxo de Caixa, Indicadores e Dashboard.
- **Módulos afetados:** Financeiro, BI/Direção Executiva.
- **Entidades alteradas:** Pagamento (criação), Despesa/Receita Financeira (atualização de status), Conta.
- **Impacto financeiro:** acelera a atualização do Fluxo de Caixa real; reduz erro de digitação.
- **Impacto operacional:** reduz tempo do Financeiro em lançamento manual.
- **Exceções:** nenhuma conciliação é efetivada automaticamente sem confirmação humana quando houver ambiguidade (PF-06); lançamentos não identificáveis ficam pendentes de classificação manual.
- **Alertas ao usuário:** alerta de possível duplicidade; alerta de lançamento sem correspondência sugerida; alerta de possível lançamento pessoal misturado à Conta empresarial (RN-005).
- **Auditoria e histórico:** toda sugestão de IA e toda decisão do usuário sobre ela são registradas, com rastreabilidade completa.

### 3.33 Conciliação Bancária

#### RN-044 — Conciliação entre Pagamento Registrado e Extrato Real
- **Objetivo:** garantir que todo Pagamento registrado corresponda a um lançamento real na Conta.
- **Evento que dispara:** importação de extrato (RN-043) ou conciliação manual periódica.
- **Condições:** existem Pagamentos registrados e lançamentos do extrato no mesmo período.
- **O que o sistema deve fazer:** comparar Pagamentos com lançamentos do extrato; marcar como "conciliado" os que baterem exatamente; destacar divergências (valor, data, ausência de correspondência) para tratamento manual.
- **Módulos afetados:** Financeiro.
- **Entidades alteradas:** Pagamento (status de conciliação), Conta.
- **Impacto financeiro:** garante confiabilidade do Fluxo de Caixa e dos Indicadores financeiros.
- **Impacto operacional:** reduz retrabalho de conferência manual completa.
- **Exceções:** divergências não são corrigidas automaticamente — exigem decisão humana registrada.
- **Alertas ao usuário:** alerta de Conta com pendência de conciliação há mais de um período definido (parâmetro configurável).
- **Auditoria e histórico:** todo status de conciliação é registrado com data e responsável.

### 3.34 Lançamentos Manuais

#### RN-045 — Lançamento Manual com a Mesma Qualidade de Auditoria
- **Objetivo:** permitir o registro de Despesas/Receitas Financeiras/Pagamentos sem origem automática, preservando a mesma qualidade de auditoria.
- **Evento que dispara:** usuário inicia um lançamento manual.
- **Condições:** usuário informa origem/categoria, valor, data e Conta.
- **O que o sistema deve fazer:** tratar o lançamento manual exatamente como qualquer outro (mesmas Regras Globais Financeiras do Domain Model); exigir categoria e justificativa quando não há origem automática associável.
- **Módulos afetados:** Financeiro.
- **Entidades alteradas:** Despesa ou Receita Financeira (criação manual), Pagamento.
- **Impacto financeiro:** mesmo peso de qualquer outro lançamento no Fluxo de Caixa.
- **Impacto operacional:** cobre casos de exceção que a automação não previu.
- **Exceções:** lançamentos manuais recorrentes de mesmo tipo geram sugestão de criação de uma origem formal, reduzindo lançamento manual repetido (PF-05).
- **Alertas ao usuário:** alerta quando um lançamento manual se repete de forma padronizada, sugerindo automação.
- **Auditoria e histórico:** todo lançamento manual registra o autor, distintamente de lançamentos gerados automaticamente.

### 3.35 Metas

#### RN-046 — Acompanhamento e Encerramento de Ciclo de Meta
- **Objetivo:** garantir que toda Meta seja acompanhada e formalmente encerrada ao fim do período.
- **Evento que dispara:** fim do período definido para uma Meta.
- **Condições:** a Meta está "Ativa".
- **O que o sistema deve fazer:** comparar o valor final do Indicador associado com o valor-alvo; marcar automaticamente como "Atingida" ou "Não atingida"; notificar a Direção.
- **Módulos afetados:** BI/Direção Executiva.
- **Entidades alteradas:** Meta (estado).
- **Impacto financeiro:** nenhum direto; orienta decisões de gestão futuras.
- **Impacto operacional:** insumo para revisão de estratégia no ciclo seguinte.
- **Exceções:** nenhuma.
- **Alertas ao usuário:** notificação à Direção do resultado do ciclo.
- **Auditoria e histórico:** todo ciclo de Meta é preservado permanentemente.

### 3.36 Alertas

#### RN-047 — Tratamento Padrão de Todo Alerta do Sistema
- **Objetivo:** garantir que todo alerta gerado por qualquer regra deste documento siga um padrão único, nunca se perdendo ou sendo ignorado silenciosamente.
- **Evento que dispara:** qualquer condição de alerta definida em qualquer regra deste documento.
- **Condições:** —
- **O que o sistema deve fazer:** registrar todo alerta com origem (regra geradora), destinatário (área responsável) e status (pendente, visto, tratado); nunca remover um alerta sem tratamento ou dispensa explícita justificada.
- **Módulos afetados:** todos.
- **Entidades alteradas:** nenhuma entidade de negócio própria — Alerta é um mecanismo transversal de comunicação do sistema com o usuário, não uma das 30 entidades do Domain Model.
- **Impacto financeiro:** indireto — depende do que cada alerta protege.
- **Impacto operacional:** garante que nenhuma condição crítica identificada por este documento passe despercebida.
- **Exceções:** nenhuma.
- **Alertas ao usuário:** (é a própria regra — meta-regra).
- **Auditoria e histórico:** todo alerta, seu tratamento e responsável são registrados permanentemente.

---

## 4. Quality Gate

**1. Resumo Executivo**
Foi produzida a Especificação de Regras de Negócio do THE CHARCOAL OS (TCOS-002A), com 47 regras de negócio (RN-001 a RN-047) cobrindo as 36 áreas exigidas, cada uma documentada nos 12 campos obrigatórios. O documento complementa, sem alterar, o Domain Model (TCOS-002) já aprovado conceitualmente, traduzindo suas entidades e Regras Globais em comportamento concreto e acionável.

**2. O que foi criado nesta fase**
`THE_CHARCOAL_OS_BUSINESS_RULES_SPECIFICATION.md` (v1.0.0): 47 regras de negócio, organizadas nas 36 áreas solicitadas, incluindo a orquestração completa de confirmação de Evento (RN-006) e de importação de extrato bancário (RN-043), nos moldes dos exemplos fornecidos.

**3. Estado atual do projeto**
Fases 000 e 001 encerradas e aprovadas; Fase 002 (Domain Model) conceitualmente aprovada e tratada como referência oficial imutável, formalmente ainda aberta; esta Fase 002A complementa a Fase 002 sem reabri-la ou contradizê-la.

**4. Documentos oficiais existentes**
Os 6 listados na Seção 0, mais este documento (em rascunho).

**5. Pendências abertas**
- Validação formal deste documento pelo proprietário.
- Fechamento formal da Fase 002 (Domain Model + este complemento).
- Confirmação de múltiplos parâmetros numéricos de negócio (consumo por pessoa, fatores de perda, margem-alvo, proporção de escala) — todos tratados como parâmetros configuráveis pendentes, nunca inventados.
- Decisão sobre retomar a entrevista de descoberta (Fase 001B), que responderia diretamente a essas pendências.

**6. Dúvidas encontradas**
- Qual é, de fato, o parâmetro de consumo por pessoa/tipo de evento/acompanhamento (RN-024 a RN-026)?
- Quais são os fatores reais de perda de limpeza e de produção por Ingrediente/Receita (RN-027, RN-028)?
- Existe hoje uma política formal de cancelamento/reembolso de Evento (RN-007)?
- Qual é a fórmula e o valor da margem-alvo de Precificação (RN-022)?
- Qual é o critério exato de "Cliente fidelizado" (RN-010)?
- Qual é a proporção de mão de obra por porte de Evento (RN-037)?
(Todas já registradas como perguntas abertas no Business Discovery Questionnaire; nenhuma foi respondida por suposição neste documento.)

**7. Riscos identificados**
- R-000-03/R-002-01 (crítico, herdado): hipótese de domínio de negócio ainda não confirmada — este documento é o que mais depende dela, pois modela comportamento sobre um vocabulário ainda não validado.
- R-001-01/R-002-02 (herdado): custo de mão de obra pode não estar hoje incorporado ao custo real — refletido explicitamente como condicionalidade nas regras RN-018 e RN-036.
- R-002A-01 (novo): várias regras de cálculo (RN-024 a RN-029, RN-022, RN-037) dependem de parâmetros numéricos ainda não fornecidos pelo proprietário; enquanto pendentes, o sistema especificado aqui deve alertar e exigir definição manual, nunca assumir valores. Risco de retrabalho caso os parâmetros reais divirjam substancialmente da estrutura de cálculo aqui prevista.

**8. Inconsistências encontradas**
Nenhuma inconsistência ou conflito foi encontrado entre este documento e o Domain Model ou o Framework. Todas as Regras Globais do Domain Model (Seção 5) foram operacionalizadas aqui sem duplicação de conteúdo — este documento cita-as, nunca as reescreve.

**9. Melhorias sugeridas**
- M-002A-01: quando os parâmetros pendentes (Dúvidas, item 6) forem confirmados, criar uma tabela de parâmetros de negócio como anexo vivo deste documento, sem necessidade de reescrever as regras em si.
- M-002A-02: considerar, em fase técnica futura, um mecanismo de "regras configuráveis" (não codificadas rigidamente) para os parâmetros numéricos aqui identificados, dado quão frequentemente podem mudar (custo, margem, proporção de equipe).

**10. Impacto desta fase nas próximas**
Este documento passa a ser a referência comportamental obrigatória para qualquer fase técnica futura (Arquitetura, Banco de Dados, APIs, UX): nenhuma dessas fases deve implementar um comportamento que contradiga uma regra aqui especificada sem registrar formalmente o motivo (Seção 9 do Framework).

**11. Nota da fase: 9/10**
Justificativa: cobertura completa das 36 áreas exigidas com 47 regras estruturadas nos 12 campos obrigatórios, e tratamento disciplinado dos parâmetros de negócio ainda não confirmados (nunca inventados). A nota não é 10 porque uma parcela relevante de regras de cálculo (consumo, perdas, precificação, escala) permanece com parâmetros pendentes de confirmação real do proprietário — o que é esperado nesta etapa do projeto, mas limita a precisão final até serem respondidos.

**12. Próxima fase recomendada**
Aguardar validação do proprietário sobre este documento. Recomenda-se, antes de qualquer fase técnica (Arquitetura, Banco de Dados, UX, APIs — todas explicitamente fora de escopo até nova ordem), decidir sobre a retomada da entrevista de descoberta (Fase 001B) para resolver as Dúvidas da Seção 6, já que várias regras aqui especificadas dependem diretamente dessas respostas.

**13.** `PROJECT_MEMORY.md` atualizado — ver commit correspondente.

---

*Fim do documento — THE CHARCOAL OS BUSINESS RULES SPECIFICATION v1.0.0*
