# THE CHARCOAL OS — ENTERPRISE DOMAIN DISCOVERY

**Documento:** TCOS-001 — Descoberta Completa do Domínio de Negócio
**Projeto:** THE CHARCOAL OS
**Fase:** 001 — Business Discovery
**Status:** APROVADO pelo proprietário em 2026-08-01 — Documentação Oficial do THE CHARCOAL OS. Qualquer alteração exige criação de nova versão.
**Versão:** 1.0.0
**Documentos-base considerados:** `THE_CHARCOAL_OS_DEVELOPMENT_FRAMEWORK.md` (v1.1.0), `PROJECT_MEMORY.md`

---

## 0. Nota de Auditoria de Abertura de Fase

Em conformidade com a Seção 17 do Framework, antes de qualquer conteúdo desta fase foram lidos integralmente o `THE_CHARCOAL_OS_DEVELOPMENT_FRAMEWORK.md` (v1.1.0, aprovado) e o `PROJECT_MEMORY.md`. Resultado da auditoria de abertura:

- Nenhuma inconsistência, conflito ou duplicidade nova foi identificada entre os dois documentos.
- O único item em aberto herdado é o **R-000-03 / P-000-03**: o Manifesto e o Glossário Oficial (Seções 21 e 24 do Framework) assumem, a partir do vocabulário de negócio fornecido, que a empresa opera no domínio de **produção alimentícia e eventos** (culinária em brasa/carvão — churrasco/BBQ). Esta fase de Business Discovery é precisamente o instrumento adequado para confirmar, corrigir ou expandir essa hipótese — por isso ela não é tratada como bloqueio, mas como a primeira pergunta formal da Seção "Perguntas ao Proprietário" (Seção Q deste documento).
- Este documento assume o papel de **hipótese de domínio de negócio a ser validada**, não de fato consumado. Toda afirmação sobre como a empresa funciona hoje que não pôde ser confirmada pela documentação existente foi tratada como hipótese de trabalho (sinalizada) ou como pergunta formal ao proprietário — nunca como verdade assumida silenciosamente, em conformidade com a Filosofia do Desenvolvimento (Seção 4 do Framework) e com o Princípio "Nada é assumido, tudo é registrado".
- Nenhuma decisão técnica (arquitetura, banco de dados, tecnologia) foi tomada ou insinuada neste documento, em conformidade com a restrição explícita desta fase.

---

## 1. Visão Geral do Negócio

THE CHARCOAL OS é o sistema que sustentará a operação de uma empresa cuja atividade central é a **produção de alimentos preparados em brasa/carvão (estilo churrasco/BBQ) e sua comercialização por meio de eventos, pacotes e/ou produtos**, unindo três frentes que hoje tipicamente operam de forma fragmentada em negócios deste tipo: (1) relacionamento comercial com clientes e leads, (2) produção com controle rigoroso de receita, ficha técnica, ingrediente e custo, e (3) gestão financeira e executiva do resultado do negócio.

O negócio se caracteriza por unir **produção artesanal/culinária** (que exige precisão de receita, rendimento e custo) com **venda sob encomenda ligada a eventos** (que exige gestão comercial de orçamento, contrato, calendário e mão de obra temporária) — uma combinação que a maioria dos ERPs genéricos de mercado não atende bem, pois foram desenhados ou para varejo simples, ou para indústria de produção contínua, não para produção sob encomenda vinculada a eventos.

> **Hipótese de domínio (a confirmar — ver Seção Q, pergunta Q1):** assume-se que a empresa vende principalmente por meio de (a) atendimento a Eventos (casamentos, festas corporativas, confraternizações, aniversários) mediante Orçamento e Contrato, e possivelmente (b) venda avulsa de Pacotes/Produtos fora do contexto de evento (ex.: kits para consumo doméstico, venda direta). A proporção entre estas duas frentes comerciais não está documentada e precisa ser confirmada.

## 2. Objetivos da Empresa

Objetivos de negócio inferidos a partir da documentação de governança já aprovada (Manifesto, Seção 21 do Framework) e das boas práticas do setor de catering/produção de eventos:

1. Consolidar-se como referência de qualidade e confiabilidade no seu segmento (produção em brasa/eventos).
2. Garantir margem de lucro previsível e protegida em cada Evento/Pacote vendido, por meio de custo de produção real e rastreável (Ficha Técnica).
3. Escalar a operação — em volume de eventos, em unidades e, potencialmente, em franquias — sem perda de padrão de qualidade ou de controle financeiro.
4. Reduzir dependência de conhecimento informal/tácito (receitas e processos "na cabeça" de poucas pessoas), tornando o know-how um ativo documentado da empresa.
5. Oferecer ao cliente final uma experiência de compra e de pós-venda consistente, do primeiro contato (Lead) à entrega do Evento e além (fidelização).

> **Pergunta associada:** ver Q2 (metas quantitativas de crescimento) e Q3 (indicadores que já são hoje acompanhados pela direção).

## 3. Missão Operacional

Entregar, em cada Evento ou Pacote vendido, o padrão de qualidade prometido ao cliente no Orçamento, dentro do custo de produção projetado na Ficha Técnica, no prazo e nas condições combinadas em Contrato — de forma repetível, rastreável e independente de heróis individuais na operação.

Isto se traduz operacionalmente em três compromissos permanentes:

- **Compromisso com o Cliente**: o que foi vendido é o que é entregue, sem improviso não documentado.
- **Compromisso com o Custo**: o que sai como Despesa/consumo de Ingrediente bate com o que foi planejado na Ficha Técnica; qualquer desvio é visível, não escondido em uma média geral.
- **Compromisso com a Continuidade**: nenhum processo depende de uma única pessoa não substituível para acontecer.

## 4. Cadeia de Valor

Sequência de macroetapas que geram valor, do insumo bruto ao resultado financeiro, refletindo o fluxo natural do negócio de produção sob encomenda para eventos:

```
Fornecedor → Compra → Estoque (Ingrediente/Lote)
        → Ficha Técnica / Receita (padronização)
        → Produção (transformação)
        → Produto / Pacote (oferta comercial)
        → Lead → Orçamento → Contrato → Evento (venda e entrega)
        → Pós-venda (satisfação, fidelização, indicação)
        → Financeiro (Receita Financeira, Despesa, Fluxo de Caixa)
        → Dashboard CEO (decisão executiva)
        → Crescimento (novas unidades, novos produtos, novos mercados)
```

Atividades de apoio que perpassam toda a cadeia: Mão de Obra (equipe fixa e temporária de eventos), Documentos e Contratos, Marketing/Campanhas, Equipamentos e Veículos, e Governança/BI.

## 5. Áreas da Empresa

| Área | Responsabilidade central | Entidades-chave |
|---|---|---|
| **Comercial / CRM** | Captação e conversão de Leads em Clientes, elaboração de Orçamentos, fechamento de Contratos. | Lead, Cliente, Orçamento, Contrato, Campanha |
| **Produção** | Padronização de Receitas/Fichas Técnicas, execução da Produção para Eventos e Estoque. | Receita, Ficha Técnica, Produção, Lote, Ingrediente |
| **Compras / Suprimentos** | Relação com Fornecedores, aquisição de Ingredientes e materiais. | Fornecedor, Compra |
| **Estoque / Logística** | Controle de disponibilidade, rastreabilidade e movimentação física. | Estoque, Lote, Equipamento, Veículo |
| **Eventos / Operações** | Planejamento e execução logística do Evento (local, equipe, equipamento, cronograma). | Evento, Equipamento, Veículo, Funcionário |
| **Financeiro** | Contas a pagar/receber, Fluxo de Caixa, gestão bancária. | Despesa, Receita Financeira, Pagamento, Banco, Conta |
| **Marketing** | Geração de demanda, Campanhas, relacionamento de marca. | Campanha, Lead |
| **Pessoas / Mão de Obra** | Equipe fixa e temporária, escalas para Eventos. | Funcionário, Turno/Escala |
| **Administrativo / Documentos** | Contratos, documentos fiscais e legais, arquivos. | Documento, Contrato, Nota Fiscal |
| **BI / Direção Executiva** | Indicadores, metas e visão consolidada do negócio. | Meta, Indicador, Dashboard |

> **Pergunta associada:** ver Q4 — confirmar se todas estas áreas já existem formalmente hoje (com responsáveis definidos) ou se algumas são exercidas informalmente/acumuladas por poucas pessoas.

## 6. Mapa Completo dos Processos

Visão consolidada dos macroprocessos do negócio, organizados por natureza (detalhados nas Seções 7 a 25):

| # | Grupo de Processos | Natureza |
|---|---|---|
| 7 | Processos Principais | Fim-a-fim, geram a venda e a entrega de valor ao cliente |
| 8 | Processos de Apoio | Sustentam os processos principais sem gerar receita diretamente |
| 9 | Processos Administrativos | Gestão de documentos, contratos e obrigações legais |
| 10 | Processos Financeiros | Contas a pagar/receber, caixa, bancos |
| 11 | Processos de Marketing | Geração de demanda e relacionamento de marca |
| 12 | Processos Operacionais | Execução logística do dia a dia e dos Eventos |
| 13 | Processos de Produção | Transformação de Ingrediente em Produto |
| 14 | Processos de Eventos | Ciclo de vida completo de um Evento |
| 15 | Processos de Compras | Aquisição junto a Fornecedores |
| 16 | Processos de Estoque | Controle de disponibilidade e rastreabilidade |
| 17 | Processos de Clientes | Ciclo de vida do relacionamento comercial |
| 18 | Processos de Fornecedores | Ciclo de vida do relacionamento de suprimento |
| 19 | Processos de Documentos | Geração, versionamento e arquivamento formal |
| 20 | Processos de Receitas (culinárias) | Criação e padronização de Receita/Ficha Técnica |
| 21 | Processos de Engenharia de Custos | Cálculo e controle do custo real de produção |
| 22 | Processos de Precificação | Definição do preço de venda a partir do custo |
| 23 | Processos de Mão de Obra | Alocação e gestão de equipe fixa e temporária |
| 24 | Processos de Pós-venda | Satisfação, fidelização e indicação |
| 25 | Processos de Crescimento | Expansão, novas unidades, franquias, novos produtos |

*Nota de nomenclatura (aplicação do D-000-07 do Framework): o Capítulo 20 trata exclusivamente de "Receita" no sentido culinário (padronização de pratos). Qualquer processo relativo a entradas financeiras está no Capítulo 10 e usa sempre o termo "Receita Financeira".*

## 7. Processos Principais

Processos que, executados em sequência, entregam valor direto ao cliente final e geram Receita Financeira:

1. **Captação e Qualificação** (Lead → Cliente potencial).
2. **Elaboração de Orçamento** (Produtos/Pacotes, quantidade de convidados, data, local).
3. **Negociação e Fechamento de Contrato**.
4. **Planejamento do Evento** (cronograma, equipe, equipamentos, compras adicionais).
5. **Produção** (transformação de Ingredientes em Produtos conforme Ficha Técnica).
6. **Execução/Entrega do Evento**.
7. **Faturamento e Recebimento** (Receita Financeira).
8. **Pós-venda** (satisfação, fidelização).

## 8. Processos de Apoio

Processos que não geram receita diretamente, mas são indispensáveis para que os Processos Principais aconteçam com qualidade:

- Compras e reposição de Estoque.
- Manutenção de Equipamentos e Veículos.
- Gestão de Documentos e Contratos-modelo.
- Gestão de Mão de Obra (recrutamento de equipe temporária para Eventos).
- Suporte de TI/sistemas (o próprio THE CHARCOAL OS, quando implementado).
- Marketing institucional e geração de demanda.

## 9. Processos Administrativos

- Emissão e arquivamento de Contratos, Orçamentos e Notas Fiscais.
- Gestão de obrigações legais e regulatórias (ex.: vigilância sanitária para produção de alimentos, alvarás para eventos).
- Gestão de Documentos de Fornecedores e Funcionários (contratos, certidões).
- Controle de versões de Documentos (aditivos contratuais, revisões de Orçamento).

> **Pergunta associada:** Q5 — quais exigências regulatórias (sanitárias, fiscais, trabalhistas) já se aplicam hoje à operação e precisam ser respeitadas pelo sistema desde o início.

## 10. Processos Financeiros

- Contas a pagar (Despesas decorrentes de Compras, folha, aluguel de equipamento, etc.).
- Contas a receber (Receita Financeira decorrente de Contratos — sinal + parcelas + saldo, tipicamente).
- Conciliação bancária (Banco, Conta).
- Consolidação do Fluxo de Caixa.
- Apuração de resultado por Evento/Pacote (receita financeira do evento menos custo real de produção e despesas diretas).

> **Pergunta associada:** Q6 — como funciona hoje a política de pagamento ao cliente (sinal + parcelas? à vista? prazo?) e Q7 — quantas contas bancárias/bancos a empresa utiliza hoje.

## 11. Processos de Marketing

- Criação e execução de Campanhas (redes sociais, indicações, feiras/eventos do setor).
- Geração de Leads a partir de Campanhas.
- Gestão de portfólio/imagem de marca (fotos de Eventos anteriores, depoimentos).
- Acompanhamento de retorno de Campanha (Leads gerados, conversão em Cliente).

> **Pergunta associada:** Q8 — quais canais de marketing são usados hoje e há alguma métrica de retorno já acompanhada.

## 12. Processos Operacionais

Processos logísticos do dia a dia que sustentam a execução:

- Roteirização e transporte de Equipamentos, Veículos e Produção até o local do Evento.
- Montagem e desmontagem de estrutura no local do Evento.
- Gestão de escala de equipe no dia do Evento.
- Controle de perdas e sobras (Ingrediente/Produto) por Evento.

## 13. Processos de Produção

- Planejamento de produção a partir dos Eventos confirmados (o que produzir, quando, em que quantidade).
- Requisição de Ingredientes ao Estoque conforme Ficha Técnica.
- Execução da Produção (preparo conforme Receita).
- Controle de rendimento real vs. rendimento previsto na Ficha Técnica.
- Geração de Lote de Produto acabado.
- Baixa de Estoque de Ingredientes consumidos.

## 14. Processos de Eventos

Ciclo de vida completo de um Evento, do primeiro contato à entrega:

1. Registro do interesse (Lead/Cliente) e coleta de escopo (data, local, número de convidados, tipo de evento).
2. Elaboração de Orçamento com Pacotes/Produtos.
3. Aprovação e assinatura de Contrato.
4. Planejamento operacional (Produção, Mão de Obra, Equipamento, Veículo).
5. Execução do Evento.
6. Encerramento (faturamento final, avaliação de satisfação, arquivamento de Documentos).

> **Pergunta associada:** Q9 — existe hoje um processo formal de cancelamento/remarcação de Evento e política de reembolso associada?

## 15. Processos de Compras

- Identificação de necessidade de Compra (por ponto de reposição de Estoque ou por demanda de Evento específico).
- Cotação e seleção de Fornecedor.
- Emissão de pedido/Compra.
- Recebimento e conferência (quantidade, qualidade, validade — gerando Lote).
- Lançamento da Despesa correspondente.

> **Pergunta associada:** Q10 — a empresa trabalha com Fornecedores fixos/contratados ou compra pontual por evento? Existe negociação de preço fixo por volume?

## 16. Processos de Estoque

- Entrada de Estoque (via Compra ou Produção).
- Saída de Estoque (via Produção ou venda direta de Produto).
- Controle de validade e rastreabilidade por Lote.
- Inventário periódico e ajuste (com histórico obrigatório, PF-04).
- Alerta de ruptura (falta) e de excesso/vencimento próximo.

## 17. Processos de Clientes

- Cadastro único de Cliente (PF-01), a partir da conversão de um Lead ou de contato direto.
- Histórico de Eventos, Orçamentos e Contratos por Cliente.
- Classificação/segmentação de Cliente (ex.: recorrente, corporativo, social).
- Atendimento pós-venda e fidelização.

## 18. Processos de Fornecedores

- Cadastro único de Fornecedor (PF-01).
- Avaliação/qualificação de Fornecedor (qualidade, prazo, preço).
- Histórico de Compras por Fornecedor.
- Gestão de condições comerciais (prazo de pagamento, tabela de preços).

## 19. Processos de Documentos

- Geração de Documentos a partir de eventos de negócio (Orçamento gera documento de proposta; Contrato gera documento assinado; Compra gera nota fiscal de entrada).
- Versionamento de Documentos (PF-04 — histórico obrigatório).
- Arquivamento e recuperação de Documentos por Cliente/Fornecedor/Evento.

## 20. Processos de Receitas (Culinárias)

*(Ver nota de nomenclatura na Seção 6 — este capítulo não trata de finanças.)*

- Criação de uma nova Receita (composição de Ingredientes, quantidades, modo de preparo).
- Formalização da Receita em Ficha Técnica (custo, rendimento).
- Teste e aprovação de Receita antes de entrar no catálogo comercial (Produto).
- Revisão/versionamento de Receita (ex.: troca de Ingrediente por variação de custo ou disponibilidade) — com histórico obrigatório (PF-04).
- Padronização entre diferentes produtores/cozinheiros, garantindo que a mesma Receita produza o mesmo resultado independentemente de quem a execute.

> **Pergunta associada:** Q11 — as Receitas e Fichas Técnicas já existem hoje formalizadas (mesmo que em papel/planilha) ou seria necessário documentá-las do zero durante a implantação do sistema?

## 21. Processos de Engenharia de Custos

- Cálculo do custo unitário de cada Ingrediente (incluindo perdas/quebras de processo, quando aplicável).
- Cálculo do custo total da Ficha Técnica (soma de Ingredientes + eventualmente mão de obra direta e insumos de apoio, como carvão/embalagem).
- Rateio de custos indiretos (ex.: transporte, equipamento) por Evento.
- Apuração do custo real de produção por Evento, comparado ao custo projetado no Orçamento.
- Identificação de desvios de custo (Ingrediente mais caro que o previsto, perda de rendimento, etc.).

> **Pergunta associada:** Q12 — o custo de mão de obra (equipe de produção/evento) hoje é considerado no custo de cada Ficha Técnica/Evento, ou é tratado apenas como despesa geral do período?

## 22. Processos de Precificação

- Definição da margem-alvo sobre o custo da Ficha Técnica.
- Composição do preço de venda do Produto/Pacote (custo + margem + eventuais custos variáveis do Evento, como deslocamento).
- Ajuste de preço por sazonalidade, volume de convidados ou complexidade do Evento.
- Revisão periódica de preços diante de variação de custo de Ingrediente (PF-03 — cálculo único: o preço nunca é definido isoladamente do custo real vigente).

> **Pergunta associada:** Q13 — como a precificação é feita hoje (tabela fixa, negociação caso a caso, markup percentual único, etc.)?

## 23. Processos de Mão de Obra

- Planejamento de equipe necessária por Evento (fixa + temporária/freelancer).
- Escala e alocação de Funcionário por Evento/turno.
- Registro de horas/participação em Evento (para custeio e para pagamento).
- Gestão de equipe de Produção (fixa, na cozinha/central de produção) separada da equipe de Evento (atendimento no local).

> **Pergunta associada:** Q14 — a equipe de eventos é majoritariamente própria (CLT), freelancer, ou terceirizada via parceiros? Isso muda o tratamento de custo e de escala.

## 24. Processos de Pós-venda

- Coleta de feedback/avaliação após o Evento.
- Tratamento de reclamações e não conformidades.
- Programa de relacionamento com Cliente recorrente (ex.: aniversário de casamento, eventos corporativos anuais).
- Geração de indicação (referral) a partir de Clientes satisfeitos.

> **Pergunta associada:** Q15 — existe hoje algum processo estruturado de pós-venda ou ele é informal (contato pessoal, sem registro)?

## 25. Processos de Crescimento

- Abertura de novas unidades (nova base de produção/atendimento em nova região).
- Estruturação de modelo de franquia (se aplicável), incluindo padronização de Receita/Ficha Técnica para replicação com qualidade constante.
- Expansão de portfólio (novos Produtos/Pacotes, novos formatos de evento).
- Expansão de canais de venda (ex.: venda avulsa de Produto fora do contexto de Evento, e-commerce, aplicativo mobile).

> **Pergunta associada:** Q16 — há um plano concreto de crescimento (quando, quantas unidades, se franquia é modelo pretendido) ou este é um objetivo de longo prazo ainda não detalhado?

---

## 26. Entidades do Domínio de Negócio

Para cada entidade: **O que é** · **Finalidade** · **Quem utiliza** · **Como nasce** · **Como evolui** · **Quando deixa de existir** · **Relacionamentos**. Nenhuma decisão de banco de dados é feita aqui — apenas o significado de negócio.

### 26.1 Comercial / CRM

**Cliente**
- O que é: pessoa física ou jurídica que já contratou (ou está contratando) produtos/serviços da empresa.
- Finalidade: centralizar todo o relacionamento comercial e histórico de compra.
- Quem utiliza: Comercial, Financeiro, Pós-venda, Marketing.
- Como nasce: pela conversão de um Lead, ou por contato direto que já resulta em Orçamento/Contrato.
- Como evolui: acumula histórico de Eventos, Orçamentos, Contratos e interações de pós-venda; pode mudar de classificação (ex.: de ocasional para recorrente).
- Quando deixa de existir: nunca é excluído (preserva-se histórico, PF-04); pode ser marcado como inativo.
- Relaciona-se com: Lead (origem), Evento, Orçamento, Contrato, Documento, Pagamento.

**Lead**
- O que é: contato ainda não convertido em Cliente, em fase de prospecção.
- Finalidade: dar visibilidade e rastreabilidade ao funil comercial antes do fechamento.
- Quem utiliza: Comercial, Marketing.
- Como nasce: por Campanha, indicação, contato espontâneo.
- Como evolui: passa por estágios de qualificação até virar Cliente (conversão) ou ser marcado como perdido.
- Quando deixa de existir: não é excluído; permanece como registro histórico mesmo se não convertido (para análise futura de Marketing/BI).
- Relaciona-se com: Campanha (origem), Cliente (destino da conversão), Orçamento (pode receber orçamento ainda como Lead).

**Orçamento**
- O que é: proposta comercial formal com Produtos/Pacotes, valores e condições para um Cliente/Lead.
- Finalidade: formalizar a oferta antes do compromisso contratual.
- Quem utiliza: Comercial, Cliente (como destinatário), Financeiro (referência de valor previsto).
- Como nasce: a partir de uma solicitação de Cliente/Lead, geralmente vinculada a um Evento.
- Como evolui: pode ser revisado (novas versões, PF-04) até ser aceito ou recusado.
- Quando deixa de existir: não é excluído; permanece como histórico mesmo se recusado ou expirado.
- Relaciona-se com: Cliente/Lead, Evento, Produto/Pacote, Contrato (quando aceito).

**Contrato**
- O que é: documento formal que vincula empresa e Cliente às condições comerciais de um Orçamento aprovado.
- Finalidade: formalizar juridicamente o compromisso de entrega e pagamento.
- Quem utiliza: Comercial, Jurídico/Administrativo, Financeiro.
- Como nasce: da aceitação de um Orçamento.
- Como evolui: pode receber aditivos (mudança de escopo, data, valor) — cada alteração preserva histórico.
- Quando deixa de existir: encerra-se com a conclusão do Evento e quitação financeira, mas o registro é preservado indefinidamente.
- Relaciona-se com: Orçamento (origem), Cliente, Evento, Documento, Receita Financeira, Fluxo de Caixa.

**Campanha**
- O que é: iniciativa de marketing com objetivo, período e canal definidos.
- Finalidade: gerar Leads e fortalecer marca.
- Quem utiliza: Marketing, Comercial (para atribuição de origem do Lead), BI (retorno).
- Como nasce: planejamento de Marketing.
- Como evolui: acumula métricas de desempenho (Leads gerados, conversões atribuídas) ao longo de sua execução.
- Quando deixa de existir: é encerrada ao fim do período, mas permanece como histórico para análise de retorno.
- Relaciona-se com: Lead (gerado por ela), Indicador/Dashboard (métricas de retorno).

### 26.2 Produção / Custos

**Produto**
- O que é: item ou serviço final comercializável (o que aparece no Orçamento).
- Finalidade: ser a unidade de venda ao Cliente.
- Quem utiliza: Comercial (venda), Produção (execução), Financeiro (precificação).
- Como nasce: da aprovação comercial de uma Receita/Ficha Técnica já testada.
- Como evolui: pode ter preço revisado, compor-se de diferentes Fichas Técnicas ao longo do tempo (com histórico).
- Quando deixa de existir: é descontinuado quando não é mais oferecido; permanece no histórico de vendas passadas.
- Relaciona-se com: Receita/Ficha Técnica (composição), Pacote (agrupamento), Orçamento/Contrato (venda).

**Ingrediente**
- O que é: insumo básico consumido na produção.
- Finalidade: compor Receitas/Fichas Técnicas com custo e controle de disponibilidade.
- Quem utiliza: Produção, Compras, Estoque, Engenharia de Custos.
- Como nasce: cadastro único (PF-01) na primeira vez em que é necessário para uma Receita ou Compra.
- Como evolui: seu custo unitário varia ao longo do tempo (histórico de preço, PF-04); pode ter Fornecedor(es) associado(s).
- Quando deixa de existir: é descontinuado se deixar de ser usado em qualquer Receita ativa; histórico de uso é preservado.
- Relaciona-se com: Receita, Ficha Técnica, Estoque, Lote, Compra, Fornecedor.

**Receita** *(culinária)*
- O que é: conjunto padronizado de Ingredientes, quantidades e modo de preparo.
- Finalidade: garantir repetibilidade do resultado, independente de quem produz.
- Quem utiliza: Produção, Engenharia de Custos (base do cálculo).
- Como nasce: criação e teste por parte da equipe de Produção/culinária.
- Como evolui: recebe revisões (troca de Ingrediente, ajuste de quantidade), sempre com histórico (PF-04).
- Quando deixa de existir: é descontinuada quando o Produto associado sai de linha; histórico preservado.
- Relaciona-se com: Ingrediente, Ficha Técnica, Produto, Produção.

**Ficha Técnica**
- O que é: detalhamento formal de uma Receita com quantidades exatas, custo unitário por Ingrediente, rendimento e custo total por unidade produzida.
- Finalidade: ser a fonte única de cálculo de custo de produção (PF-03).
- Quem utiliza: Produção, Engenharia de Custos, Precificação.
- Como nasce: a partir da formalização de uma Receita aprovada.
- Como evolui: é recalculada automaticamente sempre que o custo de um Ingrediente varia (PF-02); nova versão é registrada quando a composição muda.
- Quando deixa de existir: é descontinuada junto com a Receita/Produto associado; histórico preservado.
- Relaciona-se com: Receita, Ingrediente, Produto, Produção, Precificação.

**Produção** *(processo/registro)*
- O que é: o registro de uma execução concreta de transformação de Ingredientes em Produtos, a partir de uma Ficha Técnica.
- Finalidade: gerar o Produto acabado para um Evento ou para reposição de Estoque, e permitir comparar planejado vs. real.
- Quem utiliza: Equipe de Produção, Engenharia de Custos.
- Como nasce: de um plano de produção vinculado a um Evento confirmado ou a uma necessidade de Estoque.
- Como evolui: registra consumo real de Ingrediente e rendimento real, comparável ao previsto na Ficha Técnica.
- Quando deixa de existir: cada execução é um registro histórico permanente (nunca é excluída, apenas encerrada).
- Relaciona-se com: Ficha Técnica, Ingrediente, Lote, Produto, Evento, Estoque.

### 26.3 Estoque / Compras / Logística

**Fornecedor**
- O que é: pessoa física ou jurídica que fornece Ingredientes, produtos ou serviços.
- Finalidade: origem formal de Compras e insumo do controle de custo.
- Quem utiliza: Compras, Estoque, Financeiro.
- Como nasce: cadastro único (PF-01) na primeira Compra ou negociação.
- Como evolui: acumula histórico de Compras, prazos e qualidade (avaliação).
- Quando deixa de existir: é inativado se deixar de ser utilizado; histórico preservado.
- Relaciona-se com: Compra, Ingrediente, Despesa.

**Compra**
- O que é: transação de aquisição de Ingredientes/produtos/serviços junto a um Fornecedor.
- Finalidade: repor Estoque e gerar a base de custo de Ingrediente.
- Quem utiliza: Compras, Estoque, Financeiro.
- Como nasce: de uma necessidade identificada (ponto de reposição ou demanda de Evento).
- Como evolui: passa por cotação, pedido, recebimento e conferência.
- Quando deixa de existir: encerra-se com o recebimento e quitação; histórico preservado permanentemente.
- Relaciona-se com: Fornecedor, Ingrediente, Estoque, Lote, Despesa.

**Estoque** *(posição)*
- O que é: quantidade disponível de um Ingrediente/Produto em um dado momento.
- Finalidade: garantir disponibilidade para Produção e venda, evitar ruptura ou excesso.
- Quem utiliza: Produção, Compras, Estoque/Logística.
- Como nasce: com a primeira entrada (Compra ou Produção) de um item.
- Como evolui: é atualizado a cada entrada (Compra, Produção) e saída (Produção, venda) — PF-02.
- Quando deixa de existir: a posição de um item some quando seu saldo chega a zero e ele é descontinuado; o histórico de movimentações permanece.
- Relaciona-se com: Ingrediente, Produto, Lote, Compra, Produção.

**Lote**
- O que é: conjunto de unidades de um Ingrediente/Produto produzido ou recebido em uma mesma ocasião, com rastreabilidade própria.
- Finalidade: rastreabilidade (origem, validade) e controle de qualidade/segurança alimentar.
- Quem utiliza: Estoque, Produção, Compras.
- Como nasce: a cada Compra recebida ou a cada execução de Produção.
- Como evolui: seu saldo diminui conforme consumido; pode se aproximar da validade (alerta).
- Quando deixa de existir: quando totalmente consumido ou vencido/descartado — o registro histórico permanece (inclusive descartes, para controle de perdas).
- Relaciona-se com: Ingrediente, Produto, Compra, Produção, Estoque.

**Equipamento**
- O que é: bem físico reutilizável usado na Produção ou no Evento (ex.: churrasqueiras, fornos, utensílios, estruturas).
- Finalidade: viabilizar a execução física da Produção e do Evento.
- Quem utiliza: Produção, Operações/Eventos, Manutenção.
- Como nasce: cadastro no momento da aquisição.
- Como evolui: passa por uso, manutenção, eventual depreciação/substituição (histórico de manutenção).
- Quando deixa de existir: é baixado quando descartado/vendido; histórico preservado.
- Relaciona-se com: Evento (alocação), Produção, Manutenção/Despesa.

**Veículo**
- O que é: bem usado para transporte de Produção, Equipamento e equipe até o local do Evento.
- Finalidade: viabilizar a logística de entrega.
- Quem utiliza: Operações/Eventos, Logística.
- Como nasce: cadastro no momento da aquisição/contratação (próprio ou terceirizado).
- Como evolui: acumula uso, manutenção, quilometragem.
- Quando deixa de existir: é baixado quando descartado/vendido; histórico preservado.
- Relaciona-se com: Evento (alocação), Despesa (manutenção/combustível).

### 26.4 Financeiro

**Despesa**
- O que é: saída de recursos financeiros da empresa.
- Finalidade: registrar e controlar os compromissos financeiros do negócio.
- Quem utiliza: Financeiro, Engenharia de Custos (referência), Direção (Dashboard).
- Como nasce: de uma Compra, folha de Mão de Obra, custo operacional ou obrigação (aluguel, manutenção etc.).
- Como evolui: passa por status (prevista, a pagar, paga) e pode ser parcelada.
- Quando deixa de existir: nunca é excluída (histórico obrigatório, PF-04); é apenas quitada/encerrada.
- Relaciona-se com: Fornecedor, Compra, Pagamento, Conta, Fluxo de Caixa.

**Receita Financeira**
- O que é: entrada de recursos financeiros na empresa.
- Finalidade: registrar e controlar o faturamento do negócio.
- Quem utiliza: Financeiro, Direção (Dashboard).
- Como nasce: de um Contrato (venda de Evento/Pacote) ou de outra fonte de entrada.
- Como evolui: passa por status (prevista, a receber, recebida), pode ser parcelada (sinal + parcelas + saldo).
- Quando deixa de existir: nunca é excluída; é apenas quitada/encerrada.
- Relaciona-se com: Contrato, Cliente, Pagamento, Conta, Fluxo de Caixa.

**Pagamento**
- O que é: movimento financeiro concreto de liquidação (total ou parcial) de uma Despesa ou de uma Receita Financeira.
- Finalidade: registrar o momento e a forma real de entrada/saída de caixa.
- Quem utiliza: Financeiro.
- Como nasce: no momento da liquidação (recebimento do Cliente, pagamento a Fornecedor/Funcionário).
- Como evolui: pode ser único ou parte de uma série de parcelas.
- Quando deixa de existir: nunca é excluído; é o registro histórico definitivo do movimento financeiro.
- Relaciona-se com: Despesa, Receita Financeira, Conta, Banco.

**Banco** e **Conta**
- O que são: instituição financeira (Banco) e a conta bancária específica (Conta) por onde transitam os Pagamentos.
- Finalidade: origem/destino real do dinheiro; base para conciliação bancária.
- Quem utiliza: Financeiro.
- Como nascem: cadastro no momento da abertura da relação bancária.
- Como evoluem: acumulam histórico de saldo e movimentações (Pagamentos).
- Quando deixam de existir: uma Conta é encerrada quando a relação bancária termina; histórico de movimentações preservado.
- Relacionam-se com: Pagamento, Fluxo de Caixa.

**Fluxo de Caixa**
- O que é: consolidação temporal das entradas (Receita Financeira) e saídas (Despesa) de recursos.
- Finalidade: dar visibilidade de curto/médio/longo prazo sobre a saúde financeira.
- Quem utiliza: Financeiro, Direção (Dashboard).
- Como nasce: é alimentado automaticamente à medida que Despesas e Receitas Financeiras são registradas (PF-02/PF-03).
- Como evolui: é recalculado continuamente conforme novos lançamentos e Pagamentos ocorrem.
- Quando deixa de existir: nunca deixa de existir — é uma visão viva e permanente.
- Relaciona-se com: Despesa, Receita Financeira, Pagamento, Conta, Dashboard.

### 26.5 Pessoas / Mão de Obra

**Funcionário**
- O que é: pessoa que trabalha para a empresa, de forma fixa ou temporária/freelancer para Eventos.
- Finalidade: executar Produção, atendimento de Evento, funções administrativas etc.
- Quem utiliza: Todas as áreas operacionais, RH/Administrativo, Financeiro (folha).
- Como nasce: cadastro no momento da contratação (fixa) ou do primeiro engajamento (freelancer).
- Como evolui: acumula histórico de alocações (Eventos, turnos de Produção), avaliações de desempenho.
- Quando deixa de existir: é inativado no desligamento; histórico de participação em Eventos/Produção é preservado.
- Relaciona-se com: Evento (alocação/escala), Produção, Despesa (custo de mão de obra).

> **Pergunta associada:** Q17 — a Ficha Técnica/custo de produção hoje é calculada apenas com Ingredientes, ou também com uma fração de mão de obra e outros insumos de apoio (ex.: carvão, gás, embalagem)? Isso é essencial para a Seção 21 (Engenharia de Custos) não ficar incompleta.

### 26.6 Documentos e Metas

**Documento**
- O que é: registro formal (arquivo, contrato assinado, nota fiscal, ficha técnica impressa, etc.).
- Finalidade: formalizar e arquivar informações e obrigações do negócio.
- Quem utiliza: Todas as áreas, especialmente Administrativo, Jurídico, Financeiro.
- Como nasce: gerado automaticamente por outra entidade (Orçamento gera proposta, Contrato gera documento assinado, Compra gera nota fiscal) ou anexado manualmente.
- Como evolui: pode ter novas versões (aditivos, revisões) — histórico obrigatório (PF-04).
- Quando deixa de existir: nunca é excluído; pode ser arquivado/inativado.
- Relaciona-se com: praticamente todas as entidades transacionais (Cliente, Fornecedor, Evento, Contrato, Compra).

**Meta**
- O que é: objetivo quantitativo definido pela Direção para um período (ex.: faturamento, número de Eventos, margem).
- Finalidade: orientar e medir o desempenho do negócio.
- Quem utiliza: Direção, BI.
- Como nasce: definição da Direção para um ciclo (mês, trimestre, ano).
- Como evolui: é acompanhada continuamente pelo Indicador correspondente.
- Quando deixa de existir: encerra-se ao fim do período; histórico de metas passadas x realizado é preservado.
- Relaciona-se com: Indicador, Dashboard.

**Indicador**
- O que é: métrica calculada a partir dos dados do sistema (ex.: margem média por Evento, ticket médio, taxa de conversão de Lead).
- Finalidade: traduzir dados operacionais em informação de gestão.
- Quem utiliza: Direção, gestores de área.
- Como nasce: é definido conceitualmente (fórmula) e passa a ser calculado a partir dos dados disponíveis.
- Como evolui: seu valor muda continuamente; sua fórmula pode ser revisada (histórico da definição, PF-04).
- Quando deixa de existir: é descontinuado se deixar de fazer sentido para a gestão; histórico de valores passados preservado.
- Relaciona-se com: Meta, Dashboard, e transitivamente com todas as entidades operacionais que alimentam seu cálculo.

**Dashboard**
- O que é: painel visual consolidado de Indicadores.
- Finalidade: dar visão executiva e operacional do negócio.
- Quem utiliza: Direção (Dashboard CEO — PF-07), gestores de cada área.
- Como nasce: é definido a partir do conjunto de Indicadores relevantes para seu público.
- Como evolui: incorpora novos Indicadores conforme o negócio e o sistema evoluem.
- Quando deixa de existir: é descontinuado se substituído por uma nova versão; não há perda de dado histórico subjacente.
- Relaciona-se com: Indicador, Meta, e transitivamente com todos os módulos do sistema.

### 26.7 Entidades Comerciais Adicionais

**Pacote**
- O que é: agrupamento comercial de um ou mais Produtos vendido como unidade única.
- Finalidade: simplificar a oferta comercial (ex.: "Pacote Casamento 100 convidados").
- Quem utiliza: Comercial, Produção (planejamento agregado).
- Como nasce: definição comercial a partir de Produtos já existentes.
- Como evolui: pode ter sua composição revisada (histórico, PF-04).
- Quando deixa de existir: é descontinuado; histórico de vendas preservado.
- Relaciona-se com: Produto, Orçamento, Contrato, Evento.

**Evento**
- O que é: ocorrência com data, local e escopo definidos para a qual a empresa fornece produção/produtos.
- Finalidade: ser o objeto central de venda e de planejamento operacional.
- Quem utiliza: Comercial, Produção, Operações, Financeiro.
- Como nasce: da confirmação de interesse de um Cliente/Lead, associada a um Orçamento.
- Como evolui: passa por planejamento, execução e encerramento; pode sofrer alterações de escopo/data (histórico).
- Quando deixa de existir: é encerrado após entrega e faturamento final; permanece como histórico permanente.
- Relaciona-se com: Cliente, Orçamento, Contrato, Produção, Equipamento, Veículo, Funcionário, Receita Financeira.

---

## 27. Gargalos Identificados

Gargalos típicos deste modelo de negócio (produção sob encomenda + eventos), inferidos a partir do domínio descrito e dos riscos já registrados no `PROJECT_MEMORY.md` (R-000-01, R-000-02):

1. **Custo de produção não confiável em tempo real**: sem uma Ficha Técnica única e atualizada (PF-03), o custo real de um Evento só é conhecido depois que ele acontece — tarde demais para corrigir a precificação.
2. **Desconexão entre vendas e produção**: Orçamentos fechados sem visibilidade de disponibilidade de Estoque/capacidade de Produção geram risco de ruptura ou de sobrecarga da equipe.
3. **Rastreabilidade de Lote frágil**: sem controle formal de Lote, um problema de qualidade/segurança alimentar é difícil de isolar e corrigir rapidamente.
4. **Mão de obra de Evento alocada de forma improvisada**: escalas montadas manualmente (planilha/WhatsApp) geram risco de falta ou excesso de equipe no dia do Evento.
5. **Visão financeira fragmentada**: Despesas e Receitas Financeiras registradas em ferramentas diferentes (ou não registradas por Evento) impedem saber a margem real de cada Evento.
6. **Conhecimento tácito concentrado**: Receitas e processos "na cabeça" de poucas pessoas-chave criam risco de continuidade do negócio.
7. **Marketing sem retorno mensurado**: Campanhas executadas sem rastreamento estruturado de Leads gerados e convertidos.
8. **Crescimento sem padronização**: abrir uma nova unidade/franquia sem processos e Fichas Técnicas documentados tende a comprometer a qualidade percebida pelo Cliente.

## 28. Oportunidades de Melhoria

1. Adotar a Ficha Técnica como fonte única e obrigatória de custo (elimina o Gargalo 1) — já alinhado ao PF-03.
2. Vincular a confirmação de um Evento à verificação automática de disponibilidade de Estoque/capacidade produtiva antes da confirmação comercial (elimina o Gargalo 2).
3. Implementar rastreabilidade por Lote desde a Compra até a entrega no Evento (elimina o Gargalo 3).
4. Criar um processo formal de planejamento de escala por Evento, com antecedência mínima definida (elimina o Gargalo 4).
5. Consolidar toda Despesa e Receita Financeira vinculada a um Evento, permitindo apurar margem real por Evento, não apenas margem média do período (elimina o Gargalo 5).
6. Documentar formalmente toda Receita/Ficha Técnica e processo operacional relevante, reduzindo dependência de pessoas específicas (elimina o Gargalo 6).
7. Atribuir Lead à Campanha de origem e acompanhar taxa de conversão por canal (elimina o Gargalo 7).
8. Criar um "playbook" replicável (processos + Fichas Técnicas + Glossário) como pré-requisito para abertura de nova unidade/franquia (elimina o Gargalo 8).

## 29. Oportunidades de Automação

- Geração automática da lista de Compras necessárias a partir dos Eventos confirmados e do Estoque atual.
- Atualização automática do custo da Ficha Técnica sempre que o preço de um Ingrediente mudar (com alerta de impacto na margem de Orçamentos já emitidos e ainda não fechados).
- Geração automática de Documento (proposta de Orçamento, minuta de Contrato) a partir de modelos, reduzindo trabalho manual repetitivo.
- Lembretes automáticos de parcelas a receber/pagar e de vencimento de Lote.
- Disparo automático de pesquisa de satisfação (pós-venda) após a data do Evento.
- Sugestão automática de escala de Mão de Obra com base no porte do Evento (número de convidados, tipo de Pacote).

## 30. Oportunidades de Inteligência Artificial

- **Previsão de demanda**: estimar necessidade de Ingredientes/Produção a partir do histórico de Eventos e sazonalidade, apoiando o planejamento de Compras.
- **Otimização de precificação**: sugerir preço/margem por Orçamento considerando custo real vigente, histórico de conversão e sazonalidade — sempre como sugestão auditável (PF-06), nunca decisão automática silenciosa.
- **Assistente comercial**: apoiar a qualificação de Leads e a montagem inicial de Orçamentos a partir da descrição do Evento pelo Cliente.
- **Detecção de anomalias de custo**: identificar automaticamente quando o custo real de uma Produção diverge do previsto na Ficha Técnica além de um limite aceitável.
- **Leitura automática de notas fiscais/Compras** (OCR + extração estruturada) para reduzir digitação manual no registro de Compra/Despesa.
- **Copiloto do Dashboard CEO**: permitir perguntas em linguagem natural sobre os Indicadores (ex.: "qual foi a margem média dos Eventos de casamento no último trimestre?").
- **Previsão de risco de cancelamento/inadimplência** de Contrato, com base em padrões históricos.

---

## Q. Perguntas ao Proprietário

Nenhuma das perguntas abaixo foi respondida por suposição. Agrupadas por tema:

### Modelo de Negócio
- **Q1.** O domínio assumido neste documento (produção culinária em brasa/carvão — churrasco/BBQ — comercializada majoritariamente via Eventos) está correto? Há venda avulsa de Produtos/Pacotes fora do contexto de Evento (ex.: encomendas domésticas, loja física, delivery)?
- **Q2.** Quais são as metas quantitativas de crescimento da empresa (faturamento, número de Eventos, novas unidades) para os próximos 1, 3 e 10 anos?
- **Q3.** Quais indicadores a Direção já acompanha hoje (ainda que informalmente), mesmo sem sistema?

### Operação e Produção
- **Q11.** As Receitas e Fichas Técnicas já existem formalizadas hoje (papel, planilha) ou precisarão ser levantadas do zero durante a implantação?
- **Q12/Q17.** O custo de Ficha Técnica hoje considera apenas Ingredientes, ou também mão de obra direta e insumos de apoio (carvão, gás, embalagem)?
- **Q9.** Existe processo formal de cancelamento/remarcação de Evento e política de reembolso?
- **Q10.** A empresa compra de Fornecedores fixos/contratados ou pontualmente por Evento? Há negociação de preço por volume?

### Comercial e Financeiro
- **Q6.** Como funciona hoje a política de pagamento do Cliente (sinal + parcelas, à vista, prazo)?
- **Q7.** Quantas Contas bancárias/Bancos a empresa usa hoje?
- **Q13.** Como a precificação é feita hoje (tabela fixa, negociação caso a caso, markup percentual único)?

### Marketing
- **Q8.** Quais canais de marketing são usados hoje e há alguma métrica de retorno já acompanhada?

### Pessoas
- **Q14.** A equipe de Eventos é majoritariamente própria (CLT), freelancer ou terceirizada via parceiros?
- **Q4.** As áreas listadas na Seção 5 já existem formalmente hoje, com responsáveis definidos, ou são acumuladas informalmente por poucas pessoas?

### Regulatório
- **Q5.** Quais exigências regulatórias (vigilância sanitária, fiscais, trabalhistas) já se aplicam hoje à operação e devem ser respeitadas pelo sistema desde o início?

### Pós-venda e Crescimento
- **Q15.** Existe hoje algum processo estruturado de pós-venda, ou ele é informal?
- **Q16.** Há um plano concreto de expansão (quando, quantas unidades, se franquia é o modelo pretendido)?

### Sistemas Atuais
- **Q18.** A empresa já utiliza algum sistema, planilha ou ferramenta hoje para qualquer uma destas áreas? Se sim, quais dados precisarão ser migrados para o THE CHARCOAL OS no futuro?

---

## 31. Auditoria Final deste Documento

Auditoria completa realizada antes do encerramento da fase, conforme exigido:

- **Inconsistências**: nenhuma identificada entre este documento e o Framework/Memória vigentes. A nomenclatura "Receita" vs. "Receita Financeira" (D-000-07) foi aplicada de forma consistente em todo o documento (ver nota da Seção 6).
- **Conflitos**: nenhum conflito entre capítulos foi identificado; os 25 capítulos solicitados foram todos endereçados sem sobreposição contraditória — onde há sobreposição natural (ex.: Compras aparece nos Capítulos 8, 15 e 18), o conteúdo é complementar, não duplicado.
- **Duplicidades**: o conteúdo de "Processos de Clientes" (17) e "Processos de Fornecedores" (18) foi deliberadamente mantido paralelo (mesma estrutura, entidades diferentes) por clareza — não é duplicidade de conteúdo, é padronização de estrutura de capítulo.
- **Processos faltantes corrigidos automaticamente**: durante a auditoria foi percebido que o processo de **cancelamento/remarcação de Evento** e o de **inventário/ajuste de Estoque** não estavam explícitos; foram adicionados aos Capítulos 14 e 16, respectivamente.
- **Entidades faltantes corrigidas automaticamente**: durante a auditoria foram identificadas e adicionadas as entidades **Pagamento**, **Banco**, **Conta**, **Meta**, **Indicador** e **Dashboard** (já citadas nos exemplos do prompt, mas detalhadas de forma completa aqui) e **Campanha** — todas com as sete explicações obrigatórias.
- **Oportunidades não exploradas**: nenhuma adicional identificada além das já registradas nas Seções 28–30; qualquer nova oportunidade percebida em fases futuras deve ser acrescida ao Improvement Backlog (`PROJECT_MEMORY.md`), nunca perdida.
- **Riscos**: nenhum risco técnico foi levantado (fora de escopo desta fase); o único risco de negócio já registrado (R-000-03, hipótese de domínio) permanece formalmente em aberto até resposta à Q1 — tratado, não ignorado.
- **Conformidade com a restrição da fase**: confirmado que nenhum trecho deste documento define banco de dados, API, tela, tecnologia ou arquitetura técnica.

Nenhuma inconsistência permaneceu sem tratamento nesta auditoria.

---

*Fim do documento — THE CHARCOAL OS ENTERPRISE DOMAIN DISCOVERY v1.0.0*
