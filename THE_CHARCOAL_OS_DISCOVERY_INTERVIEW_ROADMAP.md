# THE CHARCOAL OS — ROTEIRO DEFINITIVO DA ENTREVISTA DE DESCOBERTA

**Documento:** Fase 001B (v2.0) — Reorganização Estratégica do Questionário em Fases de Entrevista
**Projeto:** THE CHARCOAL OS
**Status:** APROVADO pelo proprietário em 2026-08-01 — Documentação Oficial do THE CHARCOAL OS. Qualquer alteração exige criação de nova versão. A execução da Fase 1 da entrevista ainda depende de autorização específica e posterior do proprietário.
**Versão:** 1.0.0
**Documento-base:** `THE_CHARCOAL_OS_BUSINESS_DISCOVERY_QUESTIONNAIRE.md` (v1.0.0, conteúdo aprovado)

---

## 0. O que este documento é (e o que não é)

Este documento **não cria perguntas novas de conteúdo livre** — ele reorganiza as 110 perguntas já aprovadas no Questionário Oficial em uma sequência estratégica de entrevista, dividida em Fases de Descoberta que dependem umas das outras. Cada pergunta mantém seu número original (**Q1–Q110**) para rastreabilidade; o racional de "por que importa" de cada uma continua valendo e pode ser consultado no documento original.

Cinco perguntas foram **adicionadas** (marcadas como `[NOVA]`, com seu próprio racional) por representarem lacunas identificadas apenas ao reorganizar a entrevista como um fluxo único e contínuo. Uma pergunta foi **movida** de categoria para melhorar a lógica de dependência (marcada como `[MOVIDA]`). Nenhuma pergunta foi excluída. Nenhuma duplicidade literal foi encontrada entre as 110 originais — uma sobreposição temática (Q91 e Q97) foi resolvida por sequenciamento, não por fusão, pois pertencem a fases com objetivos diferentes.

**Nenhuma pergunta foi feita ao proprietário neste documento.** Esta é uma entrega de organização, não de entrevista.

## 1. Critério Utilizado para Organizar as Perguntas

A sequência segue seis critérios, nesta ordem de prioridade:

1. **Do abstrato para o concreto**: identidade e propósito da empresa vêm antes de qualquer detalhe operacional.
2. **Do que se vende para como se vende**: portfólio de oferta antes do processo comercial.
3. **Da cadeia de valor**: a sequência de Fases 4 a 7 espelha exatamente a Cadeia de Valor já registrada no `THE_CHARCOAL_OS_ENTERPRISE_DOMAIN_DISCOVERY.md` (Seção 4) — Fornecedor/Compra/Estoque → Produção → Recursos (Equipamento/Pessoas) → Custo/Preço — garantindo consistência entre os documentos da Fase 001.
4. **Do operacional para o analítico**: produção, recursos e custo (fatos concretos) são levantados antes de indicadores e dashboards (leitura analítica desses fatos).
5. **Do relacionamento contínuo para a comunicação externa**: cliente/pós-venda antes de marketing, pois o motivo de um cliente indicar a empresa (pós-venda) explica o que o marketing deveria comunicar.
6. **Do presente para o futuro**: a entrevista termina em tecnologia, automação e crescimento — nunca começa por aí, pois essas respostas só fazem sentido depois de conhecer a operação real.

Uma regra adicional, mais rígida que "afinidade temática", foi aplicada: **nenhuma fase pergunta algo cuja resposta pressuponha informação ainda não coletada em fase anterior.** Isso é o que torna esta sequência "estratégica" e não apenas "por assunto".

---

## FASE 1 — Identidade e Propósito da Empresa

**Objetivo:** Compreender a história, o modelo de negócio, a operação física atual e os sonhos/objetivos que motivam a empresa — o "porquê" e o "para onde" antes de qualquer "como".

**Depende de:** nada (fase inicial).

**Perguntas:**
- Q1 a Q4 — História da Empresa
- **[NOVA-1]** Hoje a produção e a administração da empresa acontecem em um único local, ou já existe mais de um ponto (cozinha, escritório, depósito)?
  *Por que foi adicionada:* é um fato básico de identidade operacional que nenhuma das 110 perguntas originais cobria diretamente, e afeta desde já como o sistema deve tratar o conceito de "unidade".
- **[NOVA-2]** A empresa já possui identidade visual definida (logo, cores, forma de comunicação) que deveria estar refletida nos documentos gerados pelo sistema (orçamentos, contratos)?
  *Por que foi adicionada:* afeta a personalização visual dos documentos e telas do sistema; é uma informação de negócio, não uma decisão técnica.
- Q5 a Q9 — Modelo de Negócio
- Q108 a Q110 — Sonhos e Objetivos da Empresa

**Quantidade de perguntas:** 14 (10 originais + 2 novas + 3 [reordenadas de categoria 35, mantidas]) — ver contagem consolidada na Seção 2.
**Tempo estimado:** 60–75 minutos.

---

## FASE 2 — Portfólio de Oferta (O Que a Empresa Vende)

**Objetivo:** Entender exatamente o que a empresa vende — produtos, serviços agregados e o formato de evento — antes de investigar como isso é comercializado.

**Depende de:** Fase 1 (o modelo de negócio já esclarecido direciona quais produtos/serviços merecem mais profundidade).

**Perguntas:**
- Q10 a Q13 — Produtos
- Q14 a Q16 — Serviços
- Q17 a Q20 — Eventos

**Quantidade de perguntas:** 11
**Tempo estimado:** 45–60 minutos.

---

## FASE 3 — Jornada Comercial (Do Contato ao Pagamento)

**Objetivo:** Mapear o caminho completo do cliente: processo comercial, orçamento, negociação, fechamento e pagamento — o ciclo de venda de ponta a ponta.

**Depende de:** Fase 2 (só faz sentido perguntar como se vende depois de saber o que se vende).

**Perguntas:**
- Q21 a Q24 — Processo Comercial
- Q25 a Q28 — Processo de Orçamento
- Q29 a Q31 — Processo de Negociação
- Q32 a Q34 — Processo de Fechamento
- Q35 a Q38 — Pagamentos

**Quantidade de perguntas:** 18 (a maior fase — recomenda-se dividir em duas sessões, ex.: Orçamento+Negociação+Fechamento em uma sessão, Comercial+Pagamentos em outra, se a duração for um problema prático).
**Tempo estimado:** 75–90 minutos.

---

## FASE 4 — Cadeia de Suprimentos (De Onde Vêm os Insumos)

**Objetivo:** Entender de onde vêm os insumos: compras, fornecedores e estoque — a base física de toda a produção.

**Depende de:** Fase 2 (saber o que é produzido orienta quais insumos investigar a fundo).

**Perguntas:**
- Q39 a Q42 — Compras
- Q43 a Q45 — Fornecedores
- Q46 a Q48 — Estoque

**Quantidade de perguntas:** 10
**Tempo estimado:** 40–50 minutos.

---

## FASE 5 — Produção e Padronização (Como o Produto Nasce)

**Objetivo:** Entender como os insumos se transformam em produto: produção, receitas e fichas técnicas — o coração operacional e o know-how do negócio.

**Depende de:** Fase 4 (a produção consome exatamente os insumos já mapeados).

**Perguntas:**
- Q49 a Q51 — Produção
- Q52 a Q54 — Receitas
- Q55 a Q57 — Fichas Técnicas

**Quantidade de perguntas:** 9
**Tempo estimado:** 40–50 minutos.

---

## FASE 6 — Estrutura de Recursos: Equipamentos e Pessoas

**Objetivo:** Entender com que equipamentos e com que equipe a produção e os eventos realmente acontecem — os recursos que sustentam o que foi mapeado na Fase 5.

**Depende de:** Fase 5 (equipamentos e pessoas são usados dentro do processo de produção/evento já conhecido).

**Perguntas:**
- Q67 a Q69 — Equipamentos *(categoria original 20, reordenada para antes da Engenharia de Custos — ver nota na Fase 7)*
- Q70 a Q72 — Funcionários
- **[NOVA-3]** Quem, hoje, tem acesso a informações sensíveis do negócio (preços, custos, contratos), e existe algo que deveria ficar restrito mesmo dentro da própria equipe?
  *Por que foi adicionada:* antecipa os requisitos de confidencialidade e permissão de acesso por papel de usuário, informação de negócio necessária antes de qualquer decisão técnica futura.
- Q73 a Q75 — Escalas

**Quantidade de perguntas:** 10
**Tempo estimado:** 40–50 minutos.

---

## FASE 7 — Engenharia de Custos e Precificação (Quanto Custa, Quanto se Cobra)

**Objetivo:** Consolidar tudo que já foi levantado (insumos, produção, equipamentos, pessoas) em uma única resposta: quanto custa de verdade produzir, e quanto se cobra por isso.

**Depende de:** Fases 4, 5 e 6 — o custo real só pode ser discutido com profundidade depois de conhecer insumos, produção, equipamentos e mão de obra. É por isso que esta fase vem **depois** da Fase 6, e não junto com a categoria original de Engenharia de Custos.

**Perguntas:**
- Q58 a Q60 — Engenharia de Custos
- Q61 a Q63 — Precificação
- Q64 a Q66 — Desperdícios
- **Q94 [MOVIDA de "Financeiro da Empresa"]** — Qual evento ou produto a empresa acredita, hoje, que dá mais lucro, e qual dá menos — e como chegou a essa conclusão?
  *Por que foi movida:* é a pergunta-síntese natural do raciocínio de custo e preço, não do raciocínio financeiro de caixa — funciona melhor como fechamento desta fase do que como abertura da Fase 10.

**Quantidade de perguntas:** 10
**Tempo estimado:** 45–60 minutos.

---

## FASE 8 — Relacionamento com o Cliente

**Objetivo:** Entender quem são os clientes e o que acontece depois que o evento termina.

**Depende de:** Fase 3 (a jornada comercial já mapeada contextualiza o relacionamento contínuo com quem já comprou).

**Perguntas:**
- Q76 a Q78 — Clientes
- Q79 a Q81 — Pós-venda

**Quantidade de perguntas:** 6
**Tempo estimado:** 25–35 minutos.

---

## FASE 9 — Marketing e Presença Digital

**Objetivo:** Entender como a empresa se comunica e gera novos clientes.

**Depende de:** Fase 8 (o motivo de um cliente indicar a empresa, já levantado no pós-venda, explica o que o marketing deveria comunicar e para quem).

**Perguntas:**
- Q82 a Q84 — Marketing
- Q85 a Q87 — Redes Sociais

**Quantidade de perguntas:** 6
**Tempo estimado:** 25–35 minutos.

---

## FASE 10 — Financeiro da Empresa

**Objetivo:** Entender a saúde financeira da empresa, a separação entre pessoa física e jurídica, e os investimentos já feitos.

**Depende de:** Fase 7 (o financeiro consolida, em termos de caixa, o resultado que já foi entendido em termos de custo/preço por evento).

**Perguntas:**
- Q88 a Q90 — Financeiro Pessoal
- Q91 a Q93 — Financeiro da Empresa *(Q94 foi movida para a Fase 7 — ver nota acima)*
- **[NOVA-4]** Qual é hoje o enquadramento legal/tributário da empresa (MEI, Simples Nacional, Lucro Presumido, outro), e isso já impacta como as notas fiscais são emitidas?
  *Por que foi adicionada:* é um fato de negócio indispensável para o futuro módulo financeiro tratar corretamente emissão fiscal e tributos, e nenhuma das 110 perguntas originais perguntava isso diretamente.
- Q95 a Q96 — Investimentos

**Quantidade de perguntas:** 9
**Tempo estimado:** 40–50 minutos.

---

## FASE 11 — Gestão à Vista: Indicadores e Dashboards

**Objetivo:** Entender o que a empresa já mede hoje e o que gostaria de ver reunido em um painel de gestão.

**Depende de:** Fase 10 (indicadores e dashboards são a síntese visual de tudo que já foi levantado, especialmente do resultado financeiro).

**Perguntas:**
- Q97 a Q98 — Indicadores
- Q99 a Q100 — Dashboards

**Quantidade de perguntas:** 4
**Tempo estimado:** 20–25 minutos.

---

## FASE 12 — Tecnologia, Automação e Futuro

**Objetivo:** Entender o apetite por Inteligência Artificial e automação, o plano de crescimento e o nível de prontidão da equipe para usar o sistema — encerrando a entrevista com a visão de futuro do negócio.

**Depende de:** todas as fases anteriores — só é possível discutir com sentido onde a tecnologia pode ajudar depois de conhecer toda a operação.

**Perguntas:**
- Q101 a Q102 — Inteligência Artificial
- Q103 a Q104 — Automações
- **[NOVA-5]** Quem, na equipe, efetivamente usaria o sistema no dia a dia, além de quem toma as decisões hoje, e qual é o nível de conforto dessas pessoas com tecnologia (celular, aplicativos, planilhas)?
  *Por que foi adicionada:* define o nível de simplicidade de interface necessário para adoção real do sistema pela equipe — informação de negócio sobre pessoas, não uma decisão técnica.
- Q105 a Q107 — Crescimento Futuro

**Quantidade de perguntas:** 8
**Tempo estimado:** 35–45 minutos.

---

## 2. Resumo Consolidado

| Fase | Nome | Perguntas originais | Novas | Movidas | Total | Tempo estimado |
|---|---|---|---|---|---|---|
| 1 | Identidade e Propósito da Empresa | 12 (Q1-4, Q5-9, Q108-110) | 2 | – | 14 | 60–75 min |
| 2 | Portfólio de Oferta | 11 (Q10-20) | – | – | 11 | 45–60 min |
| 3 | Jornada Comercial | 18 (Q21-38) | – | – | 18 | 75–90 min |
| 4 | Cadeia de Suprimentos | 10 (Q39-48) | – | – | 10 | 40–50 min |
| 5 | Produção e Padronização | 9 (Q49-57) | – | – | 9 | 40–50 min |
| 6 | Estrutura de Recursos: Equipamentos e Pessoas | 9 (Q67-75) | 1 | – | 10 | 40–50 min |
| 7 | Engenharia de Custos e Precificação | 9 (Q58-66) | – | 1 (Q94) | 10 | 45–60 min |
| 8 | Relacionamento com o Cliente | 6 (Q76-81) | – | – | 6 | 25–35 min |
| 9 | Marketing e Presença Digital | 6 (Q82-87) | – | – | 6 | 25–35 min |
| 10 | Financeiro da Empresa | 8 (Q88-93, Q95-96) | 1 | – | 9 | 40–50 min |
| 11 | Gestão à Vista: Indicadores e Dashboards | 4 (Q97-100) | – | – | 4 | 20–25 min |
| 12 | Tecnologia, Automação e Futuro | 7 (Q101-107) | 1 | – | 8 | 35–45 min |
| **Total** | | **109 + 1 movida = 110** (nenhuma das 110 originais foi perdida) | **5** | **1** | **115** | **~490–625 min** |

*Nota de reconciliação: a coluna "Perguntas originais" soma 109 porque Q94 aparece contabilizada na coluna "Movidas" (associada à Fase 7, sua nova localização), não na coluna "originais" da Fase 10. 109 + 1 = 110, o total exato do Questionário Oficial — nenhuma pergunta foi perdida na reorganização.*

- **Quantidade de fases da entrevista:** 12
- **Quantidade total de perguntas no roteiro:** 115 (110 originais + 5 novas, nenhuma excluída)
- **Tempo total estimado:** aproximadamente 8 a 10,5 horas de entrevista qualitativa, a ser dividida em múltiplas sessões — recomenda-se **uma Fase por sessão** (ou duas fases pequenas juntas, como 8+9 ou 11+12), nunca mais que isso, para preservar a qualidade das respostas.
- **Ordem recomendada:** 1 → 2 → 3 → 4 → 5 → 6 → 7 → 8 → 9 → 10 → 11 → 12, estritamente nesta sequência, pois cada fase depende de respostas coletadas nas fases anteriores (ver dependências declaradas em cada fase).

## 3. Protocolo de Execução de Cada Fase (a ser seguido quando as entrevistas começarem)

Ao final de **cada** Fase, antes de avançar para a próxima, o seguinte protocolo é obrigatório:

1. **Resumir** tudo o que foi aprendido na fase.
2. **Listar inconsistências** encontradas (respostas que conflitam entre si ou com documentação já aprovada).
3. **Listar dúvidas** que permaneceram em aberto mesmo após as perguntas da fase.
4. **Listar oportunidades** percebidas (de melhoria, automação ou IA) reveladas pelas respostas.
5. **Atualizar o `PROJECT_MEMORY.md`** com o resultado da fase.
6. **Aguardar autorização explícita do proprietário** antes de iniciar a fase seguinte.

Nenhuma fase da entrevista pode começar antes da autorização de encerramento da fase anterior — mesmo que o roteiro já esteja todo definido aqui.

---

## 4. Auditoria desta Reorganização

- **Consistência verificada:** a sequência das Fases 4 a 7 foi conferida contra a Cadeia de Valor já registrada na Seção 4 do `THE_CHARCOAL_OS_ENTERPRISE_DOMAIN_DISCOVERY.md` — são a mesma sequência, o que reforça a coerência entre os dois documentos da Fase 001.
- **Duplicidade:** nenhuma pergunta original duplicada foi encontrada; a sobreposição temática entre Q91 e Q97 foi resolvida por sequenciamento (fases diferentes, objetivos diferentes), não por fusão.
- **Perguntas movidas:** apenas Q94, de "Financeiro da Empresa" (Fase 10) para "Engenharia de Custos e Precificação" (Fase 7), pelo motivo já registrado na Fase 7.
- **Perguntas adicionadas:** exatamente 5, todas marcadas `[NOVA]`, cada uma com racional próprio e integradas à fase mais coerente com seu conteúdo — nenhuma alteração foi feita no Questionário Oficial original (`THE_CHARCOAL_OS_BUSINESS_DISCOVERY_QUESTIONNAIRE.md`), que permanece intacto como registro histórico da versão aprovada.
- **Reconciliação numérica conferida:** a soma das 12 fases bate exatamente com 110 perguntas originais (109 na coluna "originais" + 1 na coluna "movidas", referente a Q94) mais as 5 novas, totalizando 115 — conferido item a item na Seção 2.
- **Conformidade com a restrição desta fase:** confirmado que nenhuma pergunta foi de fato feita ao proprietário e nenhuma entrevista foi iniciada — este documento é exclusivamente organizacional.

---

*Fim do documento — THE CHARCOAL OS DISCOVERY INTERVIEW ROADMAP v1.0.0*
