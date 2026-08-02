# THE CHARCOAL OS — AI ARCHITECTURE

**Documento:** TCOS-013 — Arquitetura Conceitual de Inteligência Artificial
**Projeto:** THE CHARCOAL OS
**Fase:** 013 — AI Architecture
**Status:** Rascunho para validação do proprietário
**Versão:** 1.0.0

---

## EXECUTIVE MEMORY

- **Estado atual do projeto:** negócio, domínio, regras, funcionalidades, fluxos, UX/UI, arquitetura de sistema, arquitetura de dados, banco de dados, contrato de integração, arquitetura de backend, arquitetura de frontend e arquitetura de segurança/privacidade completos e oficiais; iniciando a arquitetura conceitual de Inteligência Artificial, ainda sem modelo de IA, API, linguagem, banco de dados ou qualquer tecnologia definida.
- **Fase atual:** 013 — AI Architecture (TCOS-013).
- **Fases concluídas:** 000 a 012, todas aprovadas e oficiais (a mais recente, TCOS-012, congelada em 2026-08-02).
- **Critério de contagem de Documentos Oficiais (vigente desde o encerramento da Fase 012):** 16 Documentos Oficiais Congelados + 1 Documento Oficial Vivo (`PROJECT_MEMORY.md`) = **17 Documentos Oficiais no total**.
- **Documentos Oficiais Congelados (16):** Development Framework (v1.2.0), Enterprise Domain Discovery (v1.0.0), Business Discovery Questionnaire (v1.0.0), Discovery Interview Roadmap (v1.0.0), Domain Model (v1.0.0), Business Rules Specification (v1.0.0), Functional Specification (v1.2.0), User Journeys and System Flows (v1.0.0), UX/UI Specification (v1.0.0), System Architecture (v1.0.0), Data Architecture (v1.0.0), Database Specification (v1.0.0), Integration and API Contract (v1.0.0), Backend Architecture (v1.0.0), Frontend Architecture (v1.0.0), Security and Privacy Architecture (v1.0.0).
- **Documento Oficial Vivo (1):** `PROJECT_MEMORY.md`.
- **Documento em elaboração:** este documento (TCOS-013) — `THE_CHARCOAL_OS_AI_ARCHITECTURE.md`.
- **Pendências:** confirmação do domínio de negócio (R-000-03); parâmetros do Módulo 24; M-003A-03/04; M-005 a M-012 (todas as melhorias sugeridas e ainda não resolvidas); decisão sobre retomar a entrevista de descoberta; decisão de governança sobre anonimização de dado pessoal (Capítulo 31 do TCOS-012).
- **Riscos ativos:** R-000-03/R-002-01, R-001-01/R-002-02, R-002A-01 — herdados; nenhum impede o desenho da arquitetura de IA, pois toda sugestão de IA já opera sobre dado real do sistema (nunca inventado) e nunca decide sozinha (PF-06), independentemente da confirmação de parâmetros de negócio ainda pendentes.
- **Dependências para esta fase:** o Serviço de Inteligência Artificial e o padrão publicar/assinar (System Architecture, TCOS-006, Seção 3.11 e Capítulo 6); as Regras RN-041 a RN-043 (Business Rules Specification, TCOS-002A); as funcionalidades F-068 a F-071 (Functional Specification, Módulo 22); a Cadeia Completa de Atualização da IA (Integration and API Contract, TCOS-009, Capítulo 8); o Motor de Sugestões de IA (Backend Architecture, TCOS-010, Capítulo 28); a Integração Conceitual com IA na interface (Frontend Architecture, TCOS-011, Capítulo 31); a Segurança da IA (Security and Privacy Architecture, TCOS-012, Capítulo 20) — todos referenciados, nenhum reescrito.
- **Objetivo da fase que será iniciada:** projetar a arquitetura conceitual completa da Inteligência Artificial do THE CHARCOAL OS — filosofia, papéis, tipos de agente, fluxo de decisão, memória, atuação em cada domínio de negócio, explicabilidade, auditoria, limites, privacidade, segurança e integração com toda a arquitetura já aprovada — sem nenhuma decisão de tecnologia.
- **O que não pode ser alterado:** nenhum conteúdo de nenhum dos 16 Documentos Oficiais Congelados já aprovados; nenhuma nova entidade, regra de negócio ou funcionalidade é criada nesta fase — a atuação da IA em domínios além dos já cobertos por F-068 a F-071 é descrita como **padrão arquitetural extensível**, nunca como funcionalidade nova já aprovada.

### Auditoria de Abertura

Os 16 Documentos Oficiais Congelados foram revisados quanto aos pontos relevantes a esta fase (Serviço de Inteligência Artificial, Regras RN-041 a RN-043, funcionalidades F-068 a F-071, Cadeia de Atualização da IA, Motor de Sugestões, Segurança da IA). Resultado:

- Não foram identificadas inconsistências, conflitos ou duplicidades entre os 16 Documentos Oficiais Congelados, no escopo revisado.
- **Base já sólida para a IA:** o System Architecture (TCOS-006, Seção 3.11) já define o padrão "assina evento → publica sugestão, nunca altera diretamente"; o Business Rules Specification (TCOS-002A) já define RN-041 (regra geral, auditável e reversível), RN-042 (previsão de demanda) e RN-043 (categorização de extrato bancário); o Functional Specification (TCOS-003, Módulo 22) já define 4 funcionalidades (F-068 a F-071) cobrindo Financeiro, Compras/Produção e Precificação; o Integration and API Contract (TCOS-009, Capítulo 8) já define a cadeia completa de sugestão-confirmação; o Backend Architecture (TCOS-010, Capítulo 28) já define o Motor de Sugestões de IA; o Frontend Architecture (TCOS-011, Capítulo 31) já define como a sugestão aparece na interface; o Security and Privacy Architecture (TCOS-012, Capítulo 20) já define isolamento e minimização de dado para a IA. Este documento **não redefine nada disso** — consolida, generaliza e aprofunda o comportamento da IA como uma arquitetura própria e completa.
- **Achado crítico de escopo (tratado com disciplina de governança):** o Prompt Oficial desta fase solicita documentação da atuação da IA em domínios (Engenharia de Custos, Produção, Estoque, Eventos, CRM, Marketing, Dashboards, Indicadores) além dos 4 já cobertos por funcionalidade formal (F-068 a F-071). Esta arquitetura resolve esse pedido **sem inventar funcionalidade nova**: cada capítulo de domínio (Capítulos 12-22) descreve o **padrão arquitetural** pelo qual a IA já teria acesso e já poderia atuar naquele domínio (mesmo mecanismo de assinatura de evento e sugestão já aprovado, TCOS-006/TCOS-010), distinguindo explicitamente entre o que já é funcionalidade oficial (F-068 a F-071) e o que é **extensão estrutural preparada, ainda não formalizada como funcionalidade** — a criação de uma nova F-XXX específica permanece pendente de uma futura nova versão do Functional Specification (TCOS-003), não desta fase.
- **Lacuna real identificada:** nenhum documento anterior formalizou **Memória Operacional** e **Memória Estratégica** como conceitos distintos de IA — apenas "histórico de dados suficiente" foi mencionado de forma genérica (TCOS-003, F-069/070). Esta arquitetura formaliza os dois conceitos (Capítulos 10-11) por adição.
- **Lacuna real identificada:** nenhum documento anterior categorizou **Tipos de Agentes Inteligentes** — as 4 funcionalidades de IA já aprovadas (F-068 a F-071) correspondem, na prática, a padrões distintos de atuação, nunca antes nomeados como categorias. Esta arquitetura formaliza essa categorização (Capítulo 6) a partir do que já existe, sem criar comportamento novo.
- **Achado de consistência:** a distinção Sugestão vs. Decisão (RN-041, PF-06) já é o princípio mais repetido em toda a documentação de IA (TCOS-006, TCOS-009, TCOS-010, TCOS-011, TCOS-012) — esta arquitetura a eleva a capítulo próprio (Capítulo 8), consolidando, não alterando, o que já era unânime.
- Nenhuma decisão de modelo de IA, linguagem, framework, API, banco de dados ou infraestrutura foi tomada, em conformidade com a restrição explícita da fase.

---

## 1. Papel deste Documento

O System Architecture (TCOS-006) reservou o Serviço de Inteligência Artificial como um dos 15 Serviços Conceituais. O Backend Architecture (TCOS-010), o Frontend Architecture (TCOS-011) e o Security and Privacy Architecture (TCOS-012) detalharam, cada um em sua camada, como a IA se conecta, aparece e é protegida. Este documento (TCOS-013) consolida e aprofunda **toda** a arquitetura conceitual de Inteligência Artificial do THE CHARCOAL OS: sua filosofia, seus papéis, como decide o que sugerir, como "lembra" do que já viu, e como atua — sempre como sugestão, nunca como decisão — em cada domínio de negócio do sistema. Fornece a base de comportamento (Capítulos 3 a 33) necessária para que uma equipe de desenvolvimento inicie a escolha de modelo, linguagem e infraestrutura de IA; as regras de negócio, entidades e funcionalidades permanecem nos documentos de origem (TCOS-002 a TCOS-012) e não são redefinidas aqui.

## 2. Legenda e Convenções

- Toda referência a Módulo, Serviço, Entidade, Regra (RN-XXX), Evento, Funcionalidade (F-XXX) ou Integração (IN-XXX) usa exatamente os nomes/números já oficiais.
- **Agente Inteligente:** uma das categorias funcionais de atuação da IA, formalizada no Capítulo 6.
- **Extensão Estrutural Preparada:** um domínio em que a IA já poderia atuar pelo mesmo padrão arquitetural aprovado (TCOS-006/TCOS-010), mas para o qual ainda não existe uma funcionalidade F-XXX formal — distinção usada nos Capítulos 12 a 22.

---

## 3. Filosofia da IA

A Inteligência Artificial do THE CHARCOAL OS é tratada como um **membro estratégico da empresa** — presente em todo lugar onde há decisão a apoiar, mas sem cadeira de comando: ela analisa, alerta, prevê e recomenda, nunca aprova, nunca assina, nunca decide sozinha. Essa filosofia já está integralmente prevista no Framework (PF-06: "IA como assistente inteligente, não como caixa-preta") e nas Regras de Negócio já aprovadas (RN-041): toda sugestão é auditável, explicável e reversível. Um "membro estratégico" que nunca decide sozinho não é uma limitação da IA — é o que permite que ela seja usada com confiança em áreas sensíveis (dinheiro, preço, dado de Cliente) sem risco de decisão automática indevida.

## 4. Princípios de Funcionamento

- **Sugestão, nunca decisão (PF-06/RN-041):** toda saída da IA é uma proposta, nunca um fato consumado.
- **Confirmação humana como regra, automação como exceção (RN-041):** apenas ações de baixo risco, reversíveis e pré-aprovadas explicitamente pela Direção podem ocorrer sem confirmação pontual (F-071) — nunca uma ação financeira, de Cliente ou de preço.
- **Nunca inventar dado:** toda sugestão deriva exclusivamente de dado já existente no sistema (histórico operacional real) — a IA nunca cria, estima ou assume um dado de entrada que não exista, apenas processa o que já foi registrado por um Serviço dono (PF-01/PF-03).
- **Nunca alterar registro diretamente:** a IA publica uma sugestão como evento (TCOS-006, Seção 3.11); apenas o Serviço de origem, após confirmação humana, executa o Caso de Uso que de fato altera o dado (TCOS-010, Capítulo 28).
- **Transparência total (Capítulo 23 — Explicabilidade):** toda sugestão informa sua origem e seu nível de confiança, nunca aparece como um número "vindo do nada".
- **Auditabilidade total (Capítulo 24):** toda sugestão, aceite, recusa ou reversão é permanentemente registrada (RN-041).
- **Privacidade e segurança por padrão (Capítulos 26-27):** a IA nunca acessa ou expõe mais dado do que o Perfil que a consulta já teria direito de ver.

## 5. Papéis da IA

Como "membro estratégico", a IA assume três papéis conceituais, nunca um quarto papel de decisora:

- **Analista de Apoio:** processa dado operacional para produzir uma leitura que economiza tempo humano (ex.: categorizar um lançamento, F-068).
- **Vigia Contínua:** monitora continuamente o sistema em busca de padrões que mereçam atenção, gerando Alertas Inteligentes (Capítulo 22) antes que um humano precisasse notar manualmente.
- **Conselheira Estratégica:** para a Direção, sintetiza tendência e histórico de longo prazo (Memória Estratégica, Capítulo 11) em Recomendações (Capítulo 24) — nunca uma deliberação de negócio por conta própria, sempre uma síntese que informa a deliberação humana.

## 6. Tipos de Agentes Inteligentes

**Categorização formalizada nesta fase** (achado de auditoria — os padrões já existiam nas 4 funcionalidades aprovadas, nunca haviam sido nomeados como categorias). Quatro tipos de agente, cada um correspondendo a um padrão de atuação já usado ou já preparado pela arquitetura:

| Tipo de Agente | Padrão de atuação | Exemplo já aprovado |
|---|---|---|
| **Agente de Classificação** | recebe um dado novo e sugere a categoria/rótulo mais provável | F-068 (categorização de lançamento financeiro) |
| **Agente de Previsão** | projeta um valor futuro a partir de série histórica | F-069 (previsão de demanda) |
| **Agente de Recomendação** | sugere um curso de ação (não apenas um número) a partir de custo, histórico e contexto | F-070 (sugestão de preço/margem) |
| **Agente de Monitoramento** | observa continuamente um Indicador/limiar e gera alerta quando um padrão de atenção é identificado | extensão estrutural preparada (Capítulo 22 — Alertas Inteligentes) |

Nenhum agente executa uma ação de escrita — todos os quatro tipos, sem exceção, terminam sua atuação publicando uma sugestão (Capítulo 8), nunca uma alteração de dado.

## 7. Fluxo de Decisão da IA

Reafirma, sem alteração, a Cadeia Completa de Atualização da IA já definida (Integration and API Contract, TCOS-009, Capítulo 8) e o Motor de Sugestões de IA (Backend Architecture, TCOS-010, Capítulo 28):

1. Um evento de domínio relevante ocorre em um Serviço-fonte (ex.: "Extrato bancário importado", "Produção concluída", elaboração de Orçamento).
2. O Serviço de Inteligência Artificial assina esse evento e processa uma sugestão, consultando exclusivamente a Memória Operacional (Capítulo 10) e, quando relevante, a Memória Estratégica (Capítulo 11).
3. A sugestão é publicada como evento ("Sugestão gerada (IA)"), com nível de confiança explícito (Capítulo 23).
4. O usuário vê a sugestão na interface (TCOS-011, Capítulo 31) e decide: aceitar, recusar ou ajustar (Capítulo 8 desta arquitetura).
5. Apenas após a decisão humana (ou uma pré-aprovação reversível já configurada, F-071), o Serviço de origem executa o Caso de Uso correspondente.
6. O resultado entra na Cadeia de Dashboards normal (TCOS-009, Capítulo 7) e é permanentemente auditado (Capítulo 24).

## 8. Sugestões vs. Decisões

Distinção central de toda a arquitetura de IA, elevada aqui a capítulo próprio por sua importância transversal (já presente em TCOS-006, TCOS-009, TCOS-010, TCOS-011, TCOS-012, sempre com o mesmo conteúdo, nunca contraditório):

- Uma **Sugestão** é uma saída da IA que não produz nenhum efeito no sistema até ser confirmada por um humano autorizado.
- Uma **Decisão** é a confirmação (ou recusa) humana que transforma uma Sugestão em uma ação real, executada pelo Caso de Uso do Serviço de origem — nunca pela própria IA.
- A única exceção é a **automação pré-aprovada e reversível** (F-071): mesmo nesse caso, a "decisão" já foi tomada previamente por um humano (a Direção, ao configurar a política de automação) — a IA nunca decide no momento, apenas executa uma política humana já registrada, e a ação permanece reversível.
- Nenhuma Sugestão de domínio financeiro, de Cliente ou de preço pode, em nenhuma circunstância, ser configurada como automática sem confirmação pontual (F-071, exceção já registrada nesta própria funcionalidade).

## 9. Aprendizado Contínuo

A IA melhora sua sugestão ao longo do tempo exclusivamente a partir do próprio histórico de decisões humanas já registrado pela Auditoria (Capítulo 24) — taxa de aceite/recusa de cada tipo de sugestão (já um Indicador catalogado, TCOS-003 Módulo 22) é o sinal primário de aprendizado. Este documento formaliza o princípio, sem definir mecanismo técnico: **aprender é ajustar a confiança futura com base na decisão humana passada**, nunca aprender a contornar a exigência de confirmação. Nenhum "aprendizado" da IA jamais resulta em uma sugestão se tornando automática por conta própria — apenas a Direção, através de F-071, decide formalmente ampliar o nível de automação de um tipo de sugestão específico, e apenas dentro do limite já estabelecido (RN-041 — nunca para domínio financeiro/Cliente/preço).

---

## 10. Memória Operacional

**Formalizada nesta fase** (achado de auditoria — apenas mencionada genericamente como "histórico de dados suficiente", TCOS-003 F-069/070). A Memória Operacional é o conjunto de dado recente e específico que a IA consulta para gerar uma única sugestão — nunca um armazenamento próprio e paralelo ao dado de origem (PF-01): ao invés disso, é uma **consulta de curto prazo, por contrato público**, aos Serviços já donos do dado (TCOS-010, Capítulo 7). Exemplos já implícitos nas funcionalidades aprovadas: o histórico de lançamentos semelhantes usado por F-068; o histórico de Eventos/Produção usado por F-069; o histórico de Ficha Técnica e conversão de Orçamento usado por F-070. A Memória Operacional nunca persiste além do necessário para a sugestão em curso — não é uma base de conhecimento permanente da IA, apenas uma janela de consulta ao dado operacional já existente.

## 11. Memória Estratégica

**Formalizada nesta fase.** Distinta da Memória Operacional (Capítulo 10) pela escala de tempo e pelo propósito: a Memória Estratégica é a síntese de padrões de **longo prazo** (sazonalidade, tendência de margem, taxa de conversão ao longo de trimestres/anos) que alimenta o papel de Conselheira Estratégica (Capítulo 5) e as Recomendações à Direção (Capítulo 24). Assim como a Memória Operacional, nunca é uma cópia paralela do dado de origem (PF-01/PF-03) — é sempre derivada, sob demanda ou em ciclo periódico (mesmo padrão de Job Agendado já definido para a previsão de demanda, TCOS-010 Capítulo 15), a partir dos Indicadores e dados históricos já preservados pelo Serviço de Indicadores e Dashboards (TCOS-010, item 10) e pelo histórico de versões/estados terminais já garantido pelo Domain Model (CG-01). A Memória Estratégica nunca é usada para uma decisão operacional pontual (isso é papel da Memória Operacional) — apenas para uma leitura de tendência apresentada como Recomendação, sempre sujeita à mesma exigência de confirmação humana (Capítulo 8).

---

## 12. Análise Financeira

Atuação já aprovada: F-068 (sugestão de categorização de lançamento, RN-043) — Agente de Classificação (Capítulo 6), disparado por "Extrato bancário importado" (IN-012). Extensão estrutural preparada (não uma nova funcionalidade): alerta de padrão incomum de fluxo de caixa, usando o mesmo Agente de Monitoramento (Capítulo 22) sobre o Indicador de Fluxo de Caixa já existente (TCOS-007, Seção 4.4). Confirmação exigida: sempre — nenhuma sugestão financeira é aplicada automaticamente (RN-041, exceção vedada em F-071). Risco mitigado: categorização incorreta de lançamento nunca altera o registro sem revisão humana (Capítulo 20 do TCOS-012 — Segurança Financeira).

## 13. Engenharia de Custos

Atuação já aprovada: F-070 (sugestão de preço/margem a partir do custo vigente, RN-022). Extensão estrutural preparada: alerta antecipado de recálculo de custo com impacto relevante em margem, aproveitando o mesmo evento "Custo recalculado" já assinado pelo Serviço Comercial (TCOS-006, Seção 3.12) — a IA apenas sintetiza a magnitude do impacto para o usuário, nunca recalcula custo por conta própria (PF-03, exclusivo do Serviço de Custos e Precificação). Confirmação exigida: sempre, para qualquer ajuste de preço. Risco mitigado: exposição de margem/custo a Perfil sem permissão é vedada pela própria Segurança da Engenharia de Custos (TCOS-012, Capítulo 15) — a IA nunca contorna essa restrição ao gerar uma sugestão.

## 14. Produção

Atuação já aprovada: F-069 usa histórico de Produção como insumo de previsão de demanda. Extensão estrutural preparada: alerta de padrão de perda de produção acima do esperado (Agente de Monitoramento, Capítulo 22) sobre o já existente registro de perda (RN-028) e rendimento real vs. previsto (RN-029) — apoia decisão humana de revisão de Ficha Técnica, nunca altera a Ficha Técnica diretamente (PF-01, exclusivo do Serviço de Produção). Confirmação exigida: qualquer ajuste de Receita/Ficha Técnica permanece uma ação humana via Caso de Uso próprio (TCOS-010, item 3). Risco mitigado: nenhuma alteração de composição/rendimento ocorre sem revisão humana, preservando a fonte única de custo (PF-03).

## 15. Estoque

Atuação já aprovada: F-069 (previsão de demanda) já alimenta indiretamente o planejamento de reposição de Estoque. Extensão estrutural preparada: sugestão antecipada de reposição, complementar ao Job Agendado de verificação periódica de ponto de reposição já formalizado (TCOS-010, Capítulo 15, RN-033) — a IA sugere quando antecipar uma Compra além do ponto de reposição fixo, nunca decide a Compra por conta própria (Serviço de Suprimentos permanece o único dono do Estoque, TCOS-006 Seção 3.16). Confirmação exigida: toda Compra permanece uma decisão humana do Serviço de Compras. Risco mitigado: reforça (nunca contorna) a regra de que nenhum Serviço além de Suprimentos altera Estoque diretamente (Capítulo 17 do TCOS-012).

## 16. Compras

Atuação já aprovada: F-069 (Previsão de Demanda de Ingredientes/Produtos, RN-042), a funcionalidade de IA mais diretamente ligada a este domínio, já formalizada e auditável. Extensão estrutural preparada: recomendação de melhor momento de compra a partir de sazonalidade de custo (Memória Estratégica, Capítulo 11), nunca uma negociação ou decisão de Fornecedor por conta própria. Confirmação exigida: toda decisão de Compra permanece do Serviço de Compras/Suprimentos. Risco mitigado: previsão com histórico insuficiente já gera alerta de baixa confiança (RN-042) em vez de uma sugestão apresentada com falsa certeza.

## 17. Eventos

Atuação já aprovada: nenhuma funcionalidade de IA dedicada a Eventos existe hoje (F-068 a F-071 não cobrem este domínio diretamente). Extensão estrutural preparada: alerta de risco de inviabilidade operacional (complementar à checagem síncrona já obrigatória de RN-006) a partir de padrão histórico de Eventos semelhantes — a IA nunca substitui o bloqueio já obrigatório de RN-006, apenas antecipa um alerta antes da tentativa de confirmação. Confirmação exigida: a confirmação de Evento permanece exclusivamente um Caso de Uso humano do Serviço de Eventos (TCOS-010, item 2). Risco mitigado: nenhuma reserva de recurso (Produção/Estoque/Equipamento/Alocação) ocorre a partir de uma sugestão de IA — apenas a partir da confirmação humana real do Evento (Capítulo 16 do TCOS-012).

## 18. CRM

Atuação já aprovada: nenhuma funcionalidade de IA dedicada existe hoje neste domínio específico. Extensão estrutural preparada: recomendação de priorização de Lead com maior probabilidade de conversão, a partir de padrão histórico de conversão (Memória Operacional, Capítulo 10) — nunca uma decisão automática de descarte de Lead (RN-011 permanece uma regra de negócio determinística, não uma decisão de IA). Confirmação exigida: toda ação sobre um Lead/Cliente permanece do Serviço Comercial. Risco mitigado: dado pessoal de Cliente usado na recomendação segue a mesma minimização já exigida (Capítulo 6 do TCOS-012) — a IA nunca expõe mais dado pessoal do que o Perfil Comercial já teria acesso.

## 19. Marketing

Atuação já aprovada: nenhuma funcionalidade de IA dedicada existe hoje neste domínio. Extensão estrutural preparada: recomendação de alocação de investimento entre Campanhas a partir do retorno histórico já calculado por RN-038 — a IA apenas ordena e sintetiza um dado já público ao Perfil Marketing, nunca decide o orçamento de Campanha. Confirmação exigida: toda decisão de investimento permanece humana. Risco mitigado: a recomendação nunca cria uma nova Campanha ou altera uma existente — apenas lê o retorno já atribuído (TCOS-009, IN-003).

## 20. Dashboards

Atuação já aprovada: o "widget de insight do dia" já citado no UX/UI Specification (TCOS-005, Seção 3.1, Dashboard CEO) — uma síntese textual gerada por IA sobre os KPIs já exibidos, sempre rotulada como sugestão (RN-041), nunca como fato definitivo. Extensão estrutural preparada: o mesmo padrão de insight textual aplicado aos demais 10 Dashboards especializados (TCOS-005), não apenas ao Dashboard CEO. Confirmação exigida: nenhuma — um insight textual em Dashboard é informativo, não uma ação; mas nunca é a única fonte de um número exibido (RN-039/040 seguem sendo a fonte de verdade). Risco mitigado: o insight nunca substitui ou contradiz o Indicador já calculado pelo Serviço de Indicadores e Dashboards — apenas comenta sobre ele.

## 21. Indicadores

Atuação já aprovada: nenhuma funcionalidade de IA altera o cálculo de um Indicador — isso seria uma violação direta de PF-03 (cálculo único). Extensão estrutural preparada: alerta de anomalia estatística em um Indicador (variação muito acima do padrão histórico, Memória Estratégica) — a IA identifica a anomalia, nunca recalcula ou substitui o Indicador (RN-040 permanece a única fonte de cálculo, TCOS-010 item 10). Confirmação exigida: nenhuma para o alerta em si (é informativo); qualquer ação corretiva decorrente permanece humana. Risco mitigado: a IA nunca é uma segunda fonte de cálculo de Indicador — apenas uma camada de leitura sobre o Indicador já oficial.

---

## 22. Alertas Inteligentes

Formaliza o padrão de saída do Agente de Monitoramento (Capítulo 6), usado transversalmente pelos Capítulos 12-21: um Alerta Inteligente é uma sugestão de **atenção**, não de ação — aponta que algo se desvia do padrão esperado, sem propor obrigatoriamente uma solução (essa é a função da Recomendação, Capítulo 24). Todo Alerta Inteligente segue o mesmo padrão visual e de auditoria já definido para qualquer sugestão de IA (Roxo-IA, TCOS-011 Capítulo 31) e nunca se confunde com um alerta determinístico de regra de negócio (ex.: RN-023, margem abaixo do mínimo) — os dois podem coexistir na mesma tela, mas a origem de cada um é sempre identificável (Capítulo 25 — Explicabilidade).

## 23. Previsões

Reafirma, sem alteração, RN-042 e F-069 como a funcionalidade de Previsão já oficial (demanda de Ingredientes/Produtos). Formaliza o padrão geral do Agente de Previsão (Capítulo 6): toda Previsão declara, junto ao valor projetado, o **nível de confiança** e o **tamanho do histórico usado** — histórico insuficiente gera alerta de baixa confiança em vez de uma previsão apresentada com falsa certeza (já garantido por RN-042, generalizado aqui a qualquer futura extensão de Previsão em outro domínio, ex.: Capítulo 16 — Compras). Nenhuma Previsão é, por si só, uma alocação de recurso — é sempre uma entrada para uma decisão humana subsequente.

## 24. Recomendações

Formaliza o padrão de saída do Agente de Recomendação (Capítulo 6), já usado por F-070 (preço/margem): uma Recomendação combina um ou mais dados (custo, histórico, tendência da Memória Estratégica, Capítulo 11) em uma proposta de curso de ação, sempre acompanhada da justificativa que a originou (Capítulo 25). Toda Recomendação, sem exceção, exige confirmação humana explícita (Capítulo 8) — nunca é aplicada automaticamente, mesmo quando reversível, salvo a exceção já vedada para domínio financeiro/Cliente/preço em qualquer circunstância (F-071).

---

## 25. Explicabilidade

Toda sugestão, alerta, previsão ou recomendação da IA (Capítulos 20-24) é acompanhada, sem exceção, de três informações mínimas: **origem** (qual evento/dado a disparou), **nível de confiança** (alto/médio/baixo, nunca omitido), e **justificativa em linguagem de negócio** (nunca um número técnico sem explicação — ex.: "sugerido porque o custo do Ingrediente X subiu 12% nas últimas 3 Compras", nunca apenas "confiança: 0.82"). Esta exigência já está implícita em RN-041 ("toda sugestão é auditável e explicável") e é elevada aqui a requisito formal de toda saída de IA, sem exceção de domínio.

## 26. Auditoria da IA

Reafirma, sem alteração, RN-041 e o Motor de Sugestões de IA (TCOS-010, Capítulo 28): toda sugestão gerada, toda decisão humana (aceite/recusa/ajuste) e toda reversão são registradas permanentemente pelo Serviço de Auditoria (TCOS-010, Capítulo 17), com o mesmo rigor de qualquer outra ação de negócio — nunca um histórico "à parte" ou de menor importância. A Auditoria da IA responde sempre a três perguntas, para qualquer sugestão passada: o que foi sugerido, quem decidiu, e o que aconteceu depois — sustentando o Indicador "taxa de aceite de sugestões de IA" já catalogado (TCOS-003, Módulo 22) e permitindo, no Dashboard de Inteligência Artificial (TCOS-005, Seção 3.11), a reconstrução completa do histórico de qualquer Agente Inteligente (Capítulo 6).

## 27. Limites da IA

Consolida, em uma lista única, tudo que a IA **nunca** pode fazer, reunindo restrições já espalhadas por múltiplos documentos:

1. Nunca decide sozinha — toda saída é sugestão, alerta, previsão ou recomendação, nunca uma ação (Capítulo 8).
2. Nunca inventa dado — toda saída deriva exclusivamente de dado já existente e real no sistema (Capítulo 4).
3. Nunca altera um registro diretamente — apenas o Caso de Uso do Serviço de origem, após confirmação humana, o faz (TCOS-010, Capítulo 28).
4. Nunca aplica automaticamente uma sugestão financeira, de Cliente ou de preço, sob nenhuma configuração de automação (F-071, RN-041).
5. Nunca acumula dado de múltiplos Serviços além do estritamente necessário à sugestão em curso (Capítulo 20 do TCOS-012).
6. Nunca decide sobre segurança, permissão, autenticação ou perfil de usuário (Capítulo 4 do TCOS-012).
7. Nunca oculta sua origem, nível de confiança ou justificativa (Capítulo 25).
8. Nunca opera fora do padrão publicar/assinar já definido — não existe um caminho alternativo de atuação da IA fora do Event Bus (Capítulo 32).

## 28. Privacidade

Reafirma, sem alteração, a Arquitetura de Privacidade já definida (TCOS-012, Capítulo 6) aplicada especificamente à IA: toda sugestão que envolve dado pessoal (Cliente, Funcionário) é exibida apenas ao Perfil que já teria acesso a esse dado por sua própria Permissão (TCOS-012, Capítulo 20) — a IA nunca é um caminho para um Perfil ver um dado pessoal que não veria de outra forma. A Memória Operacional e Estratégica (Capítulos 10-11) nunca retêm dado pessoal além do estritamente necessário à sugestão em curso, e nunca de forma agregada entre Clientes/Funcionários distintos sem finalidade de negócio já aprovada (ex.: taxa de conversão agregada é permitida; perfil individual cruzado entre Clientes não é, sem base em uma funcionalidade já aprovada).

## 29. Segurança

Reafirma, sem alteração, a Segurança da IA já definida (TCOS-012, Capítulo 20): isolamento de dado por finalidade, exibição de sugestão restrita ao Perfil já autorizado ao dado de origem, e nenhuma ampliação de acesso através de uma sugestão. Esta arquitetura acrescenta que o princípio de negação padrão (fail-closed, TCOS-012 Capítulo 4) se aplica também à IA: se a checagem de permissão do Perfil que consulta uma sugestão não puder ser confirmada, a sugestão é ocultada, nunca exibida "por segurança" na dúvida inversa — a IA segue exatamente a mesma regra de qualquer outro componente do sistema, sem exceção especial por ser "apenas uma sugestão".

---

## 30. Integração com os 27 Módulos

A IA não possui módulo funcional próprio de origem de dado (é, como a Auditoria, transversal, TCOS-006 Capítulo 6) — sua integração ocorre por assinatura de evento, nunca por pertencer à estrutura de um módulo específico. Os Capítulos 12-21 já detalham a atuação (aprovada ou preparada) em 10 dos 27 módulos; os demais módulos permanecem cobertos pelo mesmo padrão estrutural (Capítulo 6), sem exigir uma seção dedicada nesta versão — qualquer novo módulo futuro herda automaticamente a possibilidade de conexão com a IA pelo mesmo mecanismo, sem exigir uma nova arquitetura.

## 31. Integração com os 15 Serviços

Reafirma a tabela já definida no Backend Architecture (TCOS-010, Capítulo 6, item 9): o Serviço de Inteligência Artificial assina eventos de Financeiro, Suprimentos, Custos e Precificação, Produção e Comercial (conforme já catalogado), e publica sugestões consumidas de volta pelo Serviço de origem de cada uma. Nenhum dos 15 Serviços é acessado pela IA fora do seu contrato público (TCOS-010, Capítulo 7) — a mesma regra de isolamento entre módulos (Capítulo 12 do TCOS-012) se aplica integralmente à IA, sem exceção por ser um Serviço "especial".

## 32. Integração com o Event Bus

Reafirma, sem alteração, o padrão publicar-assinar já definido (TCOS-006, Capítulo 7) como o único canal de comunicação da IA com o restante do sistema — nunca uma chamada direta, síncrona, a outro Serviço para "pedir uma decisão". A IA consome eventos de domínio (Capítulo 14 do TCOS-010) para acionar sua Memória Operacional (Capítulo 10) e publica "Sugestão gerada (IA)" (já catalogado no Event Bus, TCOS-006 Capítulo 7) como sua única forma de saída. As garantias de confiabilidade do Barramento de Eventos e Filas (retry, idempotência, fila de falhas, reconciliação — TCOS-010, Capítulo 16) aplicam-se integralmente às sugestões de IA: uma sugestão nunca é gerada em duplicidade para o mesmo evento de origem, e uma falha de geração de sugestão nunca é reportada como sugestão "sem problema" — é registrada como falha técnica (TCOS-010, Capítulo 19, categoria 3) e nunca impede a operação do Serviço de origem (TCOS-010, Capítulo 26 — Tolerância a Falhas).

## 33. Integração com Todos os Documentos Oficiais Já Aprovados

Consolida a rastreabilidade desta arquitetura em relação aos 16 Documentos Oficiais Congelados: o Framework (PF-06) origina o princípio; o Domain Model e o Business Rules Specification (RN-041 a RN-043) definem a regra de negócio; o Functional Specification (F-068 a F-071) define a funcionalidade já aprovada; o User Journeys and System Flows referencia os fluxos onde a IA participa como etapa opcional; o UX/UI Specification define a aparência (Roxo-IA) e o Dashboard de Inteligência Artificial; o System Architecture define o Serviço e o padrão publicar/assinar; o Data Architecture e o Database Specification classificam o dado de IA como categoria própria (sugestão, origem, decisão humana); o Integration and API Contract define a cadeia completa de sugestão-confirmação; o Backend Architecture define o Motor de Sugestões; o Frontend Architecture define a integração na interface; o Security and Privacy Architecture define isolamento, minimização e segurança. Nenhum desses 16 documentos é alterado por esta arquitetura — todos são apenas referenciados, e todos permanecem mutuamente consistentes, conforme confirmado pela Auditoria de Abertura desta fase.

---

## RESUMO PARA O PROPRIETÁRIO

**O que foi construído:** a arquitetura conceitual completa da Inteligência Artificial do THE CHARCOAL OS — como ela pensa (filosofia e princípios), que "papéis" ela desempenha na empresa, os 4 tipos de tarefa que ela sabe fazer (classificar, prever, recomendar, monitorar), como ela decide o que sugerir e por que nunca decide sozinha, como ela "lembra" do que já viu (de forma recente, para uma sugestão pontual, e de forma histórica, para uma visão estratégica), e como ela atuaria — hoje ou no futuro — em cada área do negócio: Financeiro, Custos, Produção, Estoque, Compras, Eventos, CRM, Marketing, Dashboards e Indicadores.

**Por que isso é importante:** a IA já está prevista em 4 pontos específicos do sistema (categorizar lançamento, prever demanda, sugerir preço, configurar automação) — mas faltava uma visão de conjunto de como ela se comporta em tudo o mais, sem que isso significasse inventar novas funcionalidades sem sua aprovação. Este documento resolve exatamente essa tensão: mostra o "padrão" que a IA já segue e como ele se estenderia, de forma segura e sempre com confirmação humana, a qualquer outra área — sem criar, sozinho, uma única funcionalidade nova.

**Quais benefícios traz:** dá a você, proprietário, uma visão completa de até onde a IA pode ir e onde ela para — ela nunca decide sobre dinheiro, preço, ou dado de Cliente sem sua confirmação (ou de quem você autorizar); toda sugestão vem com explicação e é permanentemente auditada; e a arquitetura já reserva espaço para crescer (novas áreas, novos tipos de sugestão) sem precisar ser reconstruída.

**Como se conecta com os documentos anteriores:** nenhuma regra, entidade, funcionalidade ou tela foi alterada — o documento reúne o que já estava certo (a regra de nunca decidir sozinha, já no Framework desde o início) e formaliza o que ainda faltava (memória, tipos de agente, papéis, limites explícitos).

**Como prepara as próximas fases:** com backend, frontend, segurança e agora IA todos definidos em nível conceitual, o projeto está pronto para a etapa de decisão tecnológica real — inclusive a escolha de qual modelo ou provedor de IA usar — sem que essa escolha exija redefinir como a IA se comporta dentro do sistema.

---

## TCOS QUALITY GATE EXECUTIVO

Em conformidade com o Framework v1.2.0, os 16 Documentos Oficiais Congelados foram revisados quanto aos pontos relevantes a esta fase — resultado consolidado na Auditoria de Abertura e reafirmado aqui.

**1. Resumo Executivo da Fase**
Definida a arquitetura conceitual completa de Inteligência Artificial do THE CHARCOAL OS: 31 tópicos obrigatórios cobertos (Capítulos 3-33), 4 Tipos de Agentes Inteligentes, 2 categorias de Memória (Operacional, Estratégica), atuação detalhada em 10 domínios de negócio (4 já com funcionalidade formal, 6 como extensão estrutural preparada, sem criar funcionalidade nova), catálogo de 8 Limites da IA, e integração consolidada com os 27 módulos, 15 Serviços, Event Bus e os 16 Documentos Oficiais Congelados. Nenhuma tecnologia foi definida; nenhum documento anterior foi alterado.

**2. Estado Atual do Projeto**
Fases 000 a 012 encerradas e oficiais; Fase 013 em validação. Nenhum código, modelo de IA, API, banco de dados ou infraestrutura foi iniciado.

**3. Documentos Oficiais Existentes**
17 no total — 16 Documentos Oficiais Congelados + 1 Documento Oficial Vivo (`PROJECT_MEMORY.md`), mais este documento em rascunho (não contado como oficial até aprovação).

**4. Dependências**
Serviço de Inteligência Artificial e padrão publicar/assinar (TCOS-006); RN-041 a RN-043 (TCOS-002A); F-068 a F-071 (TCOS-003); Cadeia de Atualização da IA (TCOS-009); Motor de Sugestões (TCOS-010); Integração na interface (TCOS-011); Segurança da IA (TCOS-012) — todos referenciados, nenhum reescrito.

**5. Pendências Abertas**
Validação formal deste documento; parâmetros do Módulo 24; M-003A-03/04; M-005 a M-012 (melhorias ainda não resolvidas); confirmação do domínio de negócio (R-000-03); decisão de governança sobre anonimização de dado pessoal (herdada do TCOS-012). Nenhuma pendência nova de negócio — apenas a validação deste documento.

**6. Dúvidas Encontradas**
Nenhuma nova de negócio. Uma dúvida de governança foi levantada e resolvida dentro desta própria fase: como documentar a atuação da IA em domínios sem funcionalidade formal, sem inventar escopo de negócio — respondida pelo conceito de "Extensão Estrutural Preparada" (Capítulo 2, aplicado nos Capítulos 12-21).

**7. Riscos Ativos**
R-000-03/R-002-01, R-001-01/R-002-02, R-002A-01 — herdados; nenhum impede a arquitetura de IA.

**8. Novos Riscos Encontrados**
Nenhum risco novo de negócio ou de arquitetura.

**9. Inconsistências Encontradas**
Nenhuma entre os 16 Documentos Oficiais Congelados, no escopo revisado.

**10. Conflitos entre Documentos**
Nenhum.

**11. Regras Duplicadas**
Nenhuma — RN-041 a RN-043 são citadas do Business Rules Specification (TCOS-002A) já oficial, nunca reescritas.

**12. Entidades Duplicadas**
Nenhuma — nenhuma entidade nova foi criada; a IA opera exclusivamente sobre entidades já existentes, sempre por contrato público do Serviço dono.

**13. Oportunidades de Simplificação**
Identificada e concretizada: os 4 padrões de atuação de IA já existentes (F-068 a F-071), antes descritos de forma independente, foram reunidos em 4 Tipos de Agentes Inteligentes (Capítulo 6) — permitindo que qualquer extensão futura seja classificada em um padrão já conhecido, em vez de exigir um desenho novo a cada nova ideia de uso de IA.

**14. Melhorias Sugeridas**
- M-013-01 (nova): ao escolher o modelo/provedor de IA em fase técnica futura, avaliar a viabilidade de cada Extensão Estrutural Preparada (Capítulos 12-21) como candidata a uma futura nova versão do Functional Specification (TCOS-003), antes de implementá-la.
- M-013-02 (nova): formalizar, em uma futura fase técnica, o mecanismo concreto de cálculo de "nível de confiança" (Capítulo 25) — hoje descrito apenas como conceito (alto/médio/baixo), sem metodologia definida.
- M-013-03 (nova): avaliar, junto à Direção, quais das 6 Extensões Estruturais Preparadas sem funcionalidade formal hoje (Produção, Estoque, Eventos, CRM, Marketing, Indicadores — distintas dos 4 domínios que já têm funcionalidade aprovada: Financeiro, Engenharia de Custos, Compras, Dashboards) têm maior prioridade de negócio para se tornarem funcionalidade formal primeiro.

**15. Impacto desta Fase nas Próximas**
Esta arquitetura de IA é a referência obrigatória, junto ao TCOS-010, TCOS-011 e TCOS-012, para qualquer fase técnica futura — nenhuma escolha de modelo, provedor ou infraestrutura de IA deve introduzir um comportamento de sugestão, memória, auditoria ou limite incompatível com o que está aqui documentado, sem registrar formalmente o motivo. Qualquer Extensão Estrutural Preparada que a Direção queira tornar funcionalidade formal exige uma nova versão do Functional Specification (TCOS-003), nunca uma implementação direta a partir apenas deste documento.

**16. Quality Score: 9,5/10**
Justificativa técnica: cobertura completa dos 31 tópicos exigidos, com identificação e resolução — não apenas menção — de lacunas conceituais reais (Memória Operacional/Estratégica, Tipos de Agentes, catálogo de Limites), tratando com disciplina de governança o pedido de atuação em domínios sem funcionalidade formal (nunca inventando escopo de negócio novo). Não é 10 porque 3 melhorias novas (M-013-01 a M-013-03) permanecem como refinamento pendente de decisões futuras (priorização de negócio, metodologia de confiança, escolha de modelo).

**17. Recomendação:** **APROVAR** — o documento cumpre integralmente o escopo solicitado, em nível conceitual, sem nenhuma decisão de tecnologia, sem inventar dado ou funcionalidade, e sem alterar nenhum documento anterior.

**18. Atualização do PROJECT_MEMORY.md:** ver commit correspondente — exclusivamente a seção da Fase 013.

**Estatísticas Finais**
- Quantidade total de páginas equivalentes: aproximadamente 22.
- Quantidade de entidades: 30 (referenciadas, 0 novas).
- Quantidade de regras: 47 no total do sistema; 3 citadas diretamente nesta arquitetura (RN-041 a RN-043, 0 novas, 0 alteradas).
- Quantidade de funcionalidades de IA já oficiais: 4 (F-068 a F-071, 0 novas).
- Quantidade de processos/fluxos conceituais: 1 (Fluxo de Decisão da IA, Capítulo 7).
- Quantidade de eventos: 1 evento de IA já catalogado ("Sugestão gerada (IA)", TCOS-006), reafirmado, 0 novos.
- Quantidade de decisões registradas: 4 (D-013-01 a D-013-04, ver `PROJECT_MEMORY.md`).
- Quantidade de riscos ativos: 4 herdados; 0 novos.
- Quantidade de pendências: 7 (validação do documento + 6 herdadas).
- Quantidade de melhorias sugeridas: 3 novas (M-013-01 a M-013-03).
- Percentual estimado de maturidade do projeto: **93%** (subiu de 91% — a arquitetura conceitual de IA, complementar às de backend, frontend e segurança, está completa e auditada; restam como não iniciadas: confirmação final do domínio de negócio via entrevista, escolha de tecnologia/modelo, e toda a fase de Desenvolvimento propriamente dita).

**Status desta fase:** rascunho aguardando validação do proprietário. Nenhuma fase de Desenvolvimento, Código, modelo de IA, API, banco de dados ou infraestrutura será iniciada sem autorização explícita, conforme restrição do Prompt Oficial da Fase 013.

---

*Fim do documento — THE CHARCOAL OS AI ARCHITECTURE v1.0.0*
