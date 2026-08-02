# THE CHARCOAL OS — DEVOPS AND OPERATIONAL ARCHITECTURE

**Documento:** TCOS-015 — Arquitetura Conceitual de DevOps e Operação
**Projeto:** THE CHARCOAL OS
**Fase:** 015 — DevOps & Operational Architecture
**Status:** Rascunho para validação do proprietário
**Versão:** 1.0.0

---

## EXECUTIVE MEMORY

- **Estado atual do projeto:** negócio, domínio, regras, funcionalidades, fluxos, UX/UI, arquitetura de sistema, arquitetura de dados, banco de dados, contrato de integração, arquitetura de backend, arquitetura de frontend, arquitetura de segurança/privacidade, arquitetura de IA e arquitetura de infraestrutura completos e oficiais; iniciando a arquitetura conceitual de DevOps e Operação, ainda sem CI/CD específico, ferramenta de pipeline, containers ou qualquer tecnologia definida.
- **Fase atual:** 015 — DevOps & Operational Architecture (TCOS-015).
- **Fases concluídas:** 000 a 014, todas aprovadas e oficiais (a mais recente, TCOS-014, congelada em 2026-08-02).
- **Critério de contagem de Documentos Oficiais (vigente desde o encerramento da Fase 014):** 18 Documentos Oficiais Congelados + 1 Documento Oficial Vivo (`PROJECT_MEMORY.md`) = **19 Documentos Oficiais no total**.
- **Documentos Oficiais Congelados (18):** Development Framework (v1.2.0), Enterprise Domain Discovery (v1.0.0), Business Discovery Questionnaire (v1.0.0), Discovery Interview Roadmap (v1.0.0), Domain Model (v1.0.0), Business Rules Specification (v1.0.0), Functional Specification (v1.2.0), User Journeys and System Flows (v1.0.0), UX/UI Specification (v1.0.0), System Architecture (v1.0.0), Data Architecture (v1.0.0), Database Specification (v1.0.0), Integration and API Contract (v1.0.0), Backend Architecture (v1.0.0), Frontend Architecture (v1.0.0), Security and Privacy Architecture (v1.0.0), AI Architecture (v1.0.0), Infrastructure Architecture (v1.0.0).
- **Documento Oficial Vivo (1):** `PROJECT_MEMORY.md`.
- **Documento em elaboração:** este documento (TCOS-015) — `THE_CHARCOAL_OS_DEVOPS_AND_OPERATIONAL_ARCHITECTURE.md`.
- **Pendências:** confirmação do domínio de negócio (R-000-03); parâmetros do Módulo 24; M-003A-03/04; M-005 a M-014 (melhorias ainda não resolvidas); decisão de governança sobre anonimização de dado pessoal; decisão de negócio sobre Multiempresa/Multifilial.
- **Riscos ativos:** R-000-03/R-002-01, R-001-01/R-002-02, R-002A-01 — herdados; nenhum impede o desenho da arquitetura de DevOps e Operação, pois nenhuma decisão desta fase depende de parâmetro de negócio ainda não confirmado.
- **Dependências para esta fase:** Escalabilidade (System Architecture, TCOS-006); Versionamento de Contrato de Serviço (Backend Architecture, TCOS-010, Capítulo 21); Ambientes, Estrutura de Deploy, Filas, Scheduler, Observabilidade, Monitoramento, Logging, Health Checks, Configurações, Capacidade e Continuidade Operacional (Infrastructure Architecture, TCOS-014); Continuidade Operacional e Disponibilidade (Security and Privacy Architecture, TCOS-012) — todos referenciados, nenhum reescrito.
- **Objetivo da fase que será iniciada:** projetar a arquitetura conceitual completa de DevOps e Operação do THE CHARCOAL OS — como uma mudança percorre o caminho de código a produção, como releases e rollbacks são geridos, como a qualidade é continuamente verificada, e como o sistema é operado no dia a dia (incidentes, problemas, mudanças, capacidade, disponibilidade) — sem nenhuma decisão de tecnologia.
- **O que não pode ser alterado:** nenhum conteúdo de nenhum dos 18 Documentos Oficiais Congelados já aprovados.

### Auditoria de Abertura

Os 18 Documentos Oficiais Congelados foram revisados quanto aos pontos relevantes a esta fase (versionamento de contrato, ambientes, deploy, filas, scheduler, observabilidade, monitoramento, logging, health checks, configurações, capacidade, continuidade operacional, disponibilidade). Resultado:

- Não foram identificadas inconsistências, conflitos ou duplicidades entre os 18 Documentos Oficiais Congelados, no escopo revisado.
- **Base já sólida para DevOps e Operação:** o Backend Architecture (TCOS-010, Capítulo 21) já define versionamento de contrato de Serviço; o Infrastructure Architecture (TCOS-014) já define Ambientes (Capítulo 5), Estrutura de Deploy (Capítulo 6), Filas (Capítulo 11), Scheduler (Capítulo 12), Observabilidade (Capítulo 17), Monitoramento (Capítulo 18), Logging (Capítulo 19), Health Checks (Capítulo 20), Configurações (Capítulo 21), Capacidade (Capítulo 24) e Continuidade Operacional (Capítulo 29); o Security and Privacy Architecture (TCOS-012) já define Continuidade Operacional (Capítulo 34) e Disponibilidade (Capítulo 36). Este documento **não redefine nada disso** — acrescenta a camada de **processo** que faltava: como uma mudança é construída, testada, aprovada, liberada e operada ao longo do tempo, usando a infraestrutura e a arquitetura já definidas como base física e lógica.
- **Distinção formalizada nesta fase (achado de auditoria):** existe uma diferença clara entre **arquitetura** (o que o TCOS-014 já define — que Ambientes existem, que o Deploy é reversível, que Backup/Recuperação de Desastres existem) e **operação** (o que este documento define — quem decide promover uma mudança de Staging para Production, com que critério, e o que se faz quando um Incidente ocorre). Nenhuma arquitetura é redefinida; apenas o processo humano/organizacional que a opera é formalizado.
- **Lacuna real identificada:** nenhum documento anterior formalizou o ciclo de vida de uma mudança de código — da construção até a operação em Produção (Pipeline Conceitual de Entrega, Gestão de Releases, Testes, Critérios de Aprovação). Esta arquitetura formaliza esse ciclo pela primeira vez, por adição.
- **Lacuna real identificada:** nenhum documento anterior formalizou a disciplina operacional de responder a uma falha já em Produção — Gestão de Incidentes, Gestão de Problemas e Gestão de Mudanças (como conceitos distintos e relacionados) nunca haviam sido definidos; apenas a Tolerância a Falhas arquitetural (TCOS-010, Capítulo 26) e a Continuidade Operacional (TCOS-012/TCOS-014) já existiam. Este documento formaliza essa disciplina, sem contradizer a arquitetura já aprovada.
- **Achado de consistência:** "Observabilidade Operacional" e "Monitoramento Operacional" (Capítulos 18-19 desta fase) reaproveitam integralmente a Observabilidade e o Monitoramento já definidos no TCOS-010 (Capítulo 25) e no TCOS-014 (Capítulos 17-18) — a diferença é de **uso**, não de mecanismo: aqui, os mesmos sinais técnicos já coletados são consumidos por uma equipe de operação para decidir uma ação, nunca uma segunda infraestrutura de coleta paralela.
- Nenhuma decisão de CI/CD, ferramenta de pipeline, container, orquestração ou tecnologia foi tomada, em conformidade com a restrição explícita da fase.

---

## 1. Papel deste Documento

O Infrastructure Architecture (TCOS-014) definiu **onde e como o sistema roda fisicamente**. Este documento (TCOS-015) define **como uma mudança chega até lá, e como o sistema é operado no dia a dia depois disso** — o processo de entrega contínua (do código à produção) e a disciplina operacional (incidentes, problemas, mudanças, capacidade, disponibilidade), sempre em nível conceitual. Fornece a base de processo (Capítulos 3 a 29) necessária para que uma equipe de DevOps inicie a escolha de ferramenta de CI/CD, orquestração de pipeline e plataforma de operação; a arquitetura de sistema, dado, backend, frontend, segurança, IA e infraestrutura permanecem nos documentos de origem (TCOS-002 a TCOS-014) e não são redefinidas aqui.

## 2. Legenda e Convenções

- Toda referência a Módulo, Serviço, Entidade, Regra (RN-XXX), Ambiente ou Evento usa exatamente os nomes/números já oficiais.
- **Release:** um conjunto coeso de mudanças, versionado e implantável como unidade (Capítulo 6).
- **Incidente:** uma interrupção ou degradação não planejada de um comportamento já aprovado (Capítulo 20).
- **Problema:** a causa raiz recorrente por trás de um ou mais Incidentes (Capítulo 21).
- **Mudança:** qualquer alteração planejada em código, configuração ou infraestrutura, distinta de um Incidente (evento não planejado) — Capítulo 22.

---

## 3. Filosofia DevOps

DevOps, no THE CHARCOAL OS, não é uma equipe nem uma ferramenta — é a garantia de que toda a disciplina já exigida do sistema (histórico obrigatório, PF-04; nenhuma quebra silenciosa, PF-11; simplicidade acima de tudo, PF-09) também se aplica a **como o sistema muda ao longo do tempo**. Uma mudança de código que não pode ser testada, revertida e auditada com o mesmo rigor de uma Operação Crítica de negócio (TCOS-012, Capítulo 30) representa um risco tão real quanto qualquer regra de negócio mal desenhada. A filosofia central desta fase é: **toda mudança no sistema segue o mesmo padrão de confiança verificável, nunca assumida**, já estabelecido em toda a documentação anterior.

## 4. Princípios Operacionais

- **Toda mudança é rastreável (PF-04):** nenhuma alteração em código, configuração ou infraestrutura chega à Produção sem uma origem identificável e um autor.
- **Reversibilidade sempre disponível (TCOS-014, Capítulo 6):** toda mudança implantada tem um caminho de retorno já conhecido antes de ser implantada, nunca descoberto depois de um problema.
- **Qualidade verificada, nunca presumida (Capítulo 14):** nenhuma mudança avança de Ambiente sem evidência de que continua funcionando como esperado.
- **Operação nunca surpreendida (Capítulo 18-19):** a equipe de operação enxerga o comportamento do sistema antes que o usuário de negócio precise reportar um problema.
- **Resposta a Incidente é disciplinada, não heroica (Capítulo 20):** existe um processo já conhecido antes de qualquer Incidente ocorrer, nunca improvisado no momento da crise.
- **Aprendizado contínuo (Capítulo 21/29):** todo Problema recorrente e toda melhoria de processo alimentam a Evolução Contínua, nunca são esquecidos após resolvidos pontualmente.

## 5. Pipeline Conceitual de Entrega

**Formalizado nesta fase.** O caminho que uma mudança percorre, do código à Produção, é composto por estágios conceituais sequenciais, cada um um portão de confiança que a mudança precisa atravessar — sem nomear ferramenta:

1. **Construção** (Capítulo 13 — Build): o código é transformado em um Artefato (Capítulo 12) verificável.
2. **Verificação Automatizada** (Capítulo 15): testes automatizados confirmam que o comportamento já aprovado continua correto.
3. **Verificação Manual** (Capítulo 16), quando aplicável: revisão humana complementar, nunca substituta da verificação automatizada.
4. **Aprovação** (Capítulo 17): um Critério de Aprovação já definido decide se o Artefato pode avançar.
5. **Implantação** (Capítulo 8): o Artefato aprovado é implantado no próximo Ambiente (TCOS-014, Capítulo 5), na sequência Development → Test → Staging → Production.
6. **Operação** (Capítulos 18-26): o comportamento em Produção é observado continuamente.

Nenhum estágio é pulado — uma mudança urgente segue o mesmo Pipeline, apenas com prioridade de execução mais alta, nunca com portões de confiança removidos (reforça o princípio de não presumir qualidade, Capítulo 4).

## 6. Estratégia de Versionamento

Distinta do Versionamento de Contrato de Serviço já definido (Backend Architecture, TCOS-010, Capítulo 21, que trata de compatibilidade entre Serviços): esta é a versão do **artefato de software entregável** como um todo. Toda mudança recebe um identificador de versão único e sequencial, nunca reutilizado — o mesmo princípio de Identificador Global já usado para entidades de negócio (TCOS-007, Seção 7.5) se aplica, por analogia, a cada versão de software. Uma versão implantada em um Ambiente é sempre rastreável a exatamente quais mudanças ela contém, nunca uma implantação "do que estiver na branch principal no momento", sem registro explícito do conteúdo.

## 7. Gestão de Releases

Um Release é a decisão de tornar uma ou mais versões (Capítulo 6) disponíveis em Produção — uma decisão **operacional**, distinta da Implantação técnica em si (Capítulo 8). Um Release:

- É sempre uma decisão explícita, nunca automática apenas por uma mudança ter passado no Pipeline (Capítulo 5) — a aprovação final de Release segue os Critérios de Aprovação (Capítulo 17).
- Tem um escopo documentado — o que mudou, por quê, e qual o impacto esperado — no mesmo espírito de transparência já exigido de qualquer sugestão de IA (TCOS-013, Capítulo 25 — Explicabilidade).
- Pode agrupar múltiplas mudanças pequenas ou representar uma única mudança relevante — a granularidade é uma decisão de gestão, não uma regra fixa desta arquitetura.

## 8. Deploy Conceitual

Reafirma, sem alteração, a Estrutura de Deploy já definida no Infrastructure Architecture (TCOS-014, Capítulo 6): implantação independente por Serviço, sempre reversível, nunca quebrando silenciosamente um Serviço consumidor (PF-11). Esta arquitetura acrescenta o processo operacional que aciona essa capacidade arquitetural: o Deploy de um Release aprovado (Capítulo 7) segue a sequência de Ambientes já definida (TCOS-014, Capítulo 5), nunca implanta diretamente em Production sem antes passar por Staging, salvo um Rollback de emergência (Capítulo 9) executando o caminho inverso já conhecido.

## 9. Rollback

Um Rollback é o processo operacional que aciona a reversibilidade já garantida arquiteturalmente (TCOS-014, Capítulo 6): retornar um Serviço à versão anterior (Capítulo 6) quando a versão recém-implantada apresenta comportamento inesperado. Princípios:

- Um Rollback nunca é a primeira tentativa de correção para um problema de negócio (RN-XXX) — apenas para um problema técnico introduzido pela própria mudança (categoria "Erro técnico", TCOS-010 Capítulo 19).
- Um Rollback é sempre possível de decidir e iniciar dentro do mesmo tempo de resposta esperado para qualquer Incidente (Capítulo 20) — nunca um processo mais lento que a implantação original.
- Um Rollback nunca reverte dado de negócio já processado pela versão nova (isso violaria o Histórico Imutável, TCOS-012 Capítulo 24) — reverte apenas o comportamento do software, nunca apaga um evento de domínio já ocorrido.

---

## 10. Gestão de Configurações

Reafirma, sem alteração, a distinção já definida no Infrastructure Architecture (TCOS-014, Capítulo 21) entre Configuração de negócio (Módulo 24) e Configuração de infraestrutura. Esta arquitetura acrescenta a disciplina operacional: toda Configuração de infraestrutura é versionada com o mesmo rigor de uma mudança de código (Capítulo 6) — nunca alterada diretamente em um Ambiente sem passar pelo mesmo Pipeline Conceitual de Entrega (Capítulo 5), mesmo quando a mudança é "apenas configuração". Isso evita que uma configuração de Produção divirja, sem rastro, da configuração validada em Staging.

## 11. Gestão de Ambientes

Reafirma, sem alteração, os 4 Ambientes já definidos no Infrastructure Architecture (TCOS-014, Capítulo 5). Esta arquitetura formaliza o processo operacional de **promoção** entre eles: uma mudança avança de Development para Test, de Test para Staging, e de Staging para Production, sempre na mesma ordem, nunca pulando um Ambiente — cada promoção exige a aprovação do estágio correspondente do Pipeline (Capítulo 5) e, para Production, o Critério de Aprovação mais rigoroso (Capítulo 17). A Gestão de Ambientes também garante que nenhum Ambiente de menor criticidade (Development, Test) jamais receba dado real de Cliente ou Financeiro — reforço operacional da privacidade por padrão já exigida (TCOS-012, Capítulo 6).

## 12. Gestão de Artefatos

**Formalizado nesta fase.** Um Artefato é o resultado verificável da Construção (Capítulo 13) — a unidade que efetivamente é implantada (Capítulo 8) em um Ambiente. Todo Artefato é: **imutável** após criado (a mesma versão nunca é reconstruída com conteúdo diferente sob o mesmo identificador, Capítulo 6); **rastreável** à mudança de código que o originou; e **armazenado** de forma centralizada, permitindo que qualquer versão anterior seja localizada e reimplantada em um Rollback (Capítulo 9), a qualquer momento.

## 13. Estratégia de Build

**Formalizado nesta fase.** A Construção (primeiro estágio do Pipeline, Capítulo 5) transforma código-fonte em Artefato (Capítulo 12) de forma **reprodutível** — a mesma entrada de código sempre produz o mesmo Artefato, nunca um resultado que varie conforme o momento ou o ambiente de construção. Nenhuma Build inclui Segredo (TCOS-014, Capítulo 22) embutido no Artefato — Segredos são sempre injetados no momento da execução em um Ambiente, nunca gravados dentro do próprio Artefato.

## 14. Qualidade Contínua

Consolida o princípio central desta arquitetura (Capítulo 4): a qualidade de uma mudança é verificada em cada estágio do Pipeline (Capítulo 5), nunca apenas no final. Qualidade Contínua significa que um problema é identificado o mais cedo possível — um erro encontrado na Construção (Capítulo 13) é sempre mais barato de corrigir do que o mesmo erro encontrado em Produção (Capítulo 20). Esta arquitetura não define métricas específicas de qualidade (decisão técnica futura) — apenas o princípio de que qualidade é um portão em cada estágio, nunca uma verificação isolada ao final.

## 15. Testes Automatizados (Conceitual)

Verificam, sem intervenção humana, que o comportamento já aprovado nas 47 Regras de Negócio (TCOS-002A), nas 98 funcionalidades (TCOS-003) e nas 20 Integrações (TCOS-009) continua correto após uma mudança. Três categorias conceituais, sem nomear ferramenta:

- **Verificação de unidade:** confirma que um Caso de Uso isolado (TCOS-010, Capítulo 8) se comporta como esperado.
- **Verificação de integração:** confirma que uma cadeia entre Serviços (uma das 20 Integrações, TCOS-009) continua funcionando de ponta a ponta.
- **Verificação de regressão:** confirma que uma mudança nova não quebrou um comportamento antigo já aprovado — a defesa direta contra a quebra silenciosa vedada por PF-11.

Nenhum Teste Automatizado substitui a Regra de Negócio que verifica — ele apenas confirma que a implementação da regra continua correta; a regra em si permanece definida exclusivamente no Business Rules Specification (TCOS-002A).

## 16. Testes Manuais

Complementares, nunca substitutos, aos Testes Automatizados (Capítulo 15) — reservados para o que uma verificação automatizada não cobre bem: a experiência de uso real (os seis compromissos de UX já definidos, TCOS-005 Capítulo 6/TCOS-011 Capítulo 34) e cenários exploratórios não previstos antecipadamente. Um Teste Manual é sempre documentado (o que foi testado, por quem, com que resultado) com o mesmo rigor de rastreabilidade já exigido de qualquer ação relevante (PF-04) — nunca uma validação informal sem registro.

## 17. Critérios de Aprovação

**Formalizado nesta fase.** Antes de qualquer promoção de Ambiente (Capítulo 11), um Critério de Aprovação explícito decide se a mudança pode avançar — nunca uma decisão informal ou implícita. Os Critérios crescem em rigor a cada Ambiente:

- **Development → Test:** Testes Automatizados de unidade (Capítulo 15) aprovados.
- **Test → Staging:** Testes Automatizados de integração e regressão aprovados; nenhuma Regra de Negócio quebrada.
- **Staging → Production:** Testes Manuais (Capítulo 16) concluídos; aprovação humana explícita — a mesma disciplina de confirmação já exigida para qualquer Operação Crítica de negócio (TCOS-012, Capítulo 29-30), aplicada aqui à mudança de software.

Nenhuma mudança chega a Production sem satisfazer, em sequência, todos os Critérios dos Ambientes anteriores — nunca um atalho, mesmo sob urgência (a urgência altera a prioridade de execução, Capítulo 5, nunca remove um portão de qualidade).

---

## 18. Observabilidade Operacional

Reafirma, sem alteração, a Camada de Observabilidade já definida no Backend Architecture (TCOS-010, Capítulo 25) e consolidada no Infrastructure Architecture (TCOS-014, Capítulo 17) — os mesmos sinais técnicos já coletados (tempo de resposta, taxa de erro, saúde de Serviço). A diferença desta fase é de **uso, nunca de mecanismo** (achado de auditoria): aqui, esses sinais são consumidos por uma equipe de operação para decidir uma ação (Capítulo 20 — Gestão de Incidentes), nunca uma segunda infraestrutura de coleta paralela. Observabilidade Operacional responde à pergunta "o que está acontecendo agora, e o que isso exige de nós".

## 19. Monitoramento Operacional

Complementar à Observabilidade Operacional (Capítulo 18): reafirma, sem alteração, o Monitoramento já definido no Infrastructure Architecture (TCOS-014, Capítulo 18) — vigilância contínua com limiares que disparam alerta técnico. Sob a ótica operacional, esta arquitetura formaliza que todo alerta técnico tem um **responsável designado** (Capítulo 27) e um **tempo de resposta esperado**, nunca um alerta que existe apenas tecnicamente sem ninguém encarregado de agir sobre ele.

## 20. Gestão de Incidentes

**Formalizado nesta fase** (achado de auditoria — apenas a Tolerância a Falhas arquitetural, TCOS-010 Capítulo 26, já existia; a disciplina operacional de resposta nunca havia sido formalizada). Um Incidente é uma interrupção ou degradação não planejada de um comportamento já aprovado. Processo conceitual, sem nomear ferramenta:

1. **Detecção:** via Monitoramento Operacional (Capítulo 19) ou relato direto de usuário.
2. **Classificação:** severidade determinada pelo impacto — um Incidente em Serviço Central (TCOS-006, Capítulo 4) é sempre mais severo que o mesmo tipo de Incidente em Serviço Auxiliar, mesma priorização já usada na Continuidade Operacional (TCOS-012, Capítulo 34).
3. **Resposta:** contenção imediata (pode incluir um Rollback, Capítulo 9) para restaurar o comportamento esperado, antes de investigar a causa raiz completa.
4. **Comunicação:** o impacto e o estado da resposta são comunicados ao responsável de negócio afetado, na mesma transparência já exigida de qualquer sugestão de IA (TCOS-013, Capítulo 25).
5. **Encerramento e registro:** todo Incidente é documentado — o que ocorreu, como foi contido, e por quanto tempo — alimentando a Gestão de Problemas (Capítulo 21) quando recorrente.

## 21. Gestão de Problemas

**Formalizado nesta fase.** Um Problema é a causa raiz recorrente por trás de um ou mais Incidentes (Capítulo 20) — a Gestão de Problemas existe para que a mesma causa nunca gere o mesmo Incidente indefinidamente. Diferente da resposta a Incidente (contenção imediata), a Gestão de Problemas busca a correção definitiva, através de uma Mudança formal (Capítulo 22). Todo Problema identificado é registrado com o mesmo rigor de rastreabilidade de qualquer entidade de negócio (PF-04), e sua resolução alimenta a Evolução Contínua (Capítulo 29) — nenhum Problema recorrente é aceito como "normal" sem uma tentativa formal de correção.

## 22. Gestão de Mudanças

**Formalizado nesta fase.** Uma Mudança é qualquer alteração planejada em código, configuração (Capítulo 10) ou infraestrutura — distinta de um Incidente (evento não planejado, Capítulo 20). Toda Mudança, independentemente de origem (nova funcionalidade, correção de Problema, ajuste de Configuração), percorre o mesmo Pipeline Conceitual de Entrega (Capítulo 5) e os mesmos Critérios de Aprovação (Capítulo 17) — nunca um caminho paralelo "só para mudanças pequenas". Uma Mudança de emergência (originada de um Incidente ativo) pode ter prioridade de execução elevada, mas nunca dispensa o registro e a rastreabilidade já exigidos de qualquer Mudança comum.

---

## 23. Gestão de Capacidade

Reafirma, sem alteração, a Capacidade já definida no Infrastructure Architecture (TCOS-014, Capítulo 24): volume histórico, taxa de crescimento e resultado do Monitoramento como os três sinais de dimensionamento. Esta arquitetura acrescenta a disciplina operacional: a Capacidade é revisada em ciclo definido (nunca apenas reativamente, após um problema de desempenho já ter afetado o usuário), e toda decisão de ampliar Capacidade é registrada como uma Mudança (Capítulo 22), sujeita aos mesmos Critérios de Aprovação (Capítulo 17).

## 24. Gestão de Disponibilidade

Reafirma, sem alteração, a Disponibilidade já definida no Security and Privacy Architecture (TCOS-012, Capítulo 36) e a Alta Disponibilidade do Infrastructure Architecture (TCOS-014, Capítulo 8): nenhum ponto único de falha em Serviço Central. Esta arquitetura acrescenta o acompanhamento operacional contínuo: a Disponibilidade real de cada Serviço é medida (Capítulo 26 — Métricas Operacionais) e comparada a um nível esperado definido pela Direção — qualquer degradação sustentada é tratada como um Problema (Capítulo 21), nunca apenas uma série de Incidentes isolados sem conexão reconhecida.

## 25. Continuidade Operacional

Reafirma, sem alteração, a Continuidade Operacional já definida no Security and Privacy Architecture (TCOS-012, Capítulo 34) e no Infrastructure Architecture (TCOS-014, Capítulo 29): Serviços Centrais e a Camada de Segurança/Autorização recebem prioridade de recurso sobre Serviços Auxiliares em qualquer cenário de degradação. Esta arquitetura acrescenta a prática operacional que sustenta esse princípio: um roteiro de resposta já conhecido antes de qualquer cenário de indisponibilidade ampla, incluindo a Recuperação de Desastres já definida (TCOS-014, Capítulo 16) — nunca um plano descoberto no momento da crise. A validação periódica desse roteiro (sem interromper a operação real) é parte da mesma disciplina de "capacidade de recuperação verificável, não apenas presumida" já exigida no TCOS-014.

## 26. Métricas Operacionais

**Formalizado nesta fase.** Consolida os indicadores técnicos que a operação acompanha continuamente, todos já derivados de mecanismos já aprovados, nunca uma nova fonte de dado paralela: tempo de resposta e taxa de erro por Serviço (Observabilidade, TCOS-010 Capítulo 25); profundidade de Fila e taxa de execução de Job (TCOS-014, Capítulos 11-12); frequência e severidade de Incidentes (Capítulo 20); tempo médio de detecção e de resolução de Incidente; frequência de Mudança e taxa de Mudança revertida (Rollback, Capítulo 9) — este último um indicador direto da Qualidade Contínua (Capítulo 14). Nenhuma Métrica Operacional é um Indicador de negócio (TCOS-010, item 10) — são categorias distintas, a primeira técnica, a segunda de negócio, nunca confundidas na mesma composição de Dashboard.

## 27. Papéis e Responsabilidades

Distintos dos Perfis de negócio já definidos (TCOS-012, Capítulo 9 — Perfis de Usuário): esta arquitetura formaliza papéis operacionais, sempre exercidos por pessoas técnicas, nunca por um Perfil de Área da Empresa:

- **Responsável por Mudança:** garante que uma Mudança (Capítulo 22) percorra corretamente o Pipeline (Capítulo 5) e seus Critérios de Aprovação (Capítulo 17).
- **Responsável por Incidente:** conduz a resposta a um Incidente ativo (Capítulo 20) até seu encerramento.
- **Responsável por Capacidade/Disponibilidade:** acompanha as Métricas Operacionais (Capítulo 26) e decide quando uma ampliação de Capacidade (Capítulo 23) é necessária.

Um mesmo indivíduo pode acumular mais de um papel operacional — a formalização aqui é de responsabilidade, nunca de estrutura organizacional obrigatória.

## 28. Governança Operacional

Consolida a autoridade final sobre decisões operacionais de maior impacto — no mesmo espírito da Governança já exigida em toda a documentação de negócio (Framework, Seções 1-26): nenhuma Mudança de alto risco (Capítulo 22), nenhuma ampliação relevante de Capacidade (Capítulo 23) e nenhuma alteração de Critério de Aprovação (Capítulo 17) ocorre sem uma decisão explícita e registrada, nunca uma decisão informal de um único indivíduo sem registro. A Governança Operacional nunca aprova, por si só, uma Mudança que afete uma Regra de Negócio (TCOS-002A) — essa aprovação permanece com o proprietário/Direção, através do mesmo processo de comando formal (`APROVADO`/`CORRIGIR`/`ALTERAR`/`REMOVER`/`CONTINUAR`) já usado em todo este projeto.

## 29. Evolução Contínua

Reafirma, sem alteração, o critério de sucesso "extensão, nunca reconstrução" já estabelecido no Framework (Seção 25) e em cada arquitetura subsequente. Sob a ótica de DevOps e Operação, a Evolução Contínua significa que todo Problema resolvido (Capítulo 21), toda Métrica Operacional fora do esperado (Capítulo 26) e toda melhoria de processo identificada alimentam um ciclo permanente de ajuste do próprio Pipeline (Capítulo 5) e dos próprios Critérios de Aprovação (Capítulo 17) — a disciplina de DevOps se aperfeiçoa com o mesmo rigor de auditoria genuína já aplicado a cada uma das 15 fases deste projeto, nunca presumindo que o processo já está perfeito.

---

## RESUMO PARA O PROPRIETÁRIO

**O que foi construído:** a arquitetura conceitual completa de DevOps e Operação do THE CHARCOAL OS — o caminho que qualquer mudança percorre desde o código até chegar aos seus usuários (construção, testes, aprovação, implantação), como um "Release" é decidido e um "Rollback" é feito quando algo dá errado, e como o sistema é operado no dia a dia depois de estar no ar: como um Incidente é respondido, como uma causa recorrente (Problema) é corrigida de vez, e como toda Mudança é controlada.

**Por que isso é importante:** até aqui, sabíamos onde o sistema roda (Infraestrutura) — faltava saber como ele muda com segurança ao longo do tempo, e como a equipe técnica reage quando algo não vai como esperado. Sem essa disciplina, cada mudança seria um risco individual e cada problema seria resolvido de um jeito diferente.

**Quais benefícios traz:** toda mudança segue os mesmos portões de qualidade, nunca um atalho por pressa; todo problema tem um processo já conhecido antes de acontecer; e o sistema aprende com seus próprios problemas (Evolução Contínua) em vez de repeti-los.

**Como se conecta com os documentos anteriores:** nenhuma arquitetura já aprovada foi redefinida — este documento usa a Infraestrutura (TCOS-014) como base física e acrescenta a camada de processo humano que faltava: como uma mudança percorre essa infraestrutura, e como a equipe a opera.

**Como prepara as próximas fases:** com backend, frontend, segurança, IA, infraestrutura e agora DevOps/Operação todos definidos em nível conceitual, o projeto tem hoje a base conceitual mais completa possível antes da decisão de tecnologia real — cloud provider, ferramenta de CI/CD, banco de dados — sem que essa escolha exija redefinir como o sistema funciona ou é operado.

---

## TCOS QUALITY GATE EXECUTIVO

Em conformidade com o Framework v1.2.0, os 18 Documentos Oficiais Congelados foram revisados quanto aos pontos relevantes a esta fase — resultado consolidado na Auditoria de Abertura e reafirmado aqui.

**1. Resumo Executivo da Fase**
Definida a arquitetura conceitual completa de DevOps e Operação do THE CHARCOAL OS: 27 tópicos obrigatórios cobertos (Capítulos 3-29), Pipeline Conceitual de Entrega de 6 estágios, distinção formal entre Incidente/Problema/Mudança, e consolidação operacional de Capacidade/Disponibilidade/Continuidade já definidas nas fases de infraestrutura e segurança. Nenhuma tecnologia foi definida; nenhum dos 18 Documentos Oficiais Congelados foi alterado.

**2. Estado Atual do Projeto**
Fases 000 a 014 encerradas e oficiais; Fase 015 em validação. Nenhum CI/CD, pipeline real, container ou infraestrutura física foi escolhido ou criado.

**3. Documentos Oficiais Existentes**
19 no total — 18 Documentos Oficiais Congelados + 1 Documento Oficial Vivo (`PROJECT_MEMORY.md`), mais este documento em rascunho (não contado como oficial até aprovação).

**4. Dependências**
Escalabilidade (TCOS-006); Versionamento de Contrato de Serviço (TCOS-010, Capítulo 21); Ambientes, Deploy, Filas, Scheduler, Observabilidade, Monitoramento, Logging, Health Checks, Configurações, Capacidade e Continuidade Operacional (TCOS-014); Continuidade Operacional e Disponibilidade (TCOS-012) — todos referenciados, nenhum reescrito.

**5. Pendências Abertas**
Validação formal deste documento; parâmetros do Módulo 24; M-003A-03/04; M-005 a M-014 (melhorias ainda não resolvidas); confirmação do domínio de negócio (R-000-03); decisão de governança sobre anonimização de dado pessoal; decisão de negócio sobre Multiempresa/Multifilial.

**6. Dúvidas Encontradas**
Nenhuma nova de negócio. Uma dúvida técnica foi levantada e resolvida dentro desta própria fase: como diferenciar Observabilidade/Monitoramento Operacional (Capítulos 18-19) dos mesmos conceitos já definidos no TCOS-010/TCOS-014 sem duplicar mecanismo — respondida pela distinção de uso, não de mecanismo (ver Auditoria de Abertura).

**7. Riscos Ativos**
R-000-03/R-002-01, R-001-01/R-002-02, R-002A-01 — herdados; nenhum impede a arquitetura de DevOps e Operação.

**8. Novos Riscos Encontrados**
Nenhum risco novo de negócio ou de arquitetura.

**9. Inconsistências Encontradas**
Nenhuma entre os 18 Documentos Oficiais Congelados, no escopo revisado.

**10. Conflitos entre Documentos**
Nenhum.

**11. Regras Duplicadas**
Nenhuma — esta arquitetura não cria nem redefine nenhuma Regra de Negócio.

**12. Entidades Duplicadas**
Nenhuma — nenhuma entidade nova foi criada.

**13. Oportunidades de Simplificação**
Identificada e concretizada: Observabilidade e Monitoramento, antes definidos em 2 documentos diferentes (TCOS-010, TCOS-014) para propósitos técnicos, agora têm um único ponto de consumo operacional formalizado (Capítulos 18-19), evitando que uma futura equipe crie um terceiro mecanismo de coleta paralelo por desconhecer os dois já existentes.

**14. Melhorias Sugeridas**
- M-015-01 (nova): ao escolher a ferramenta de CI/CD em fase técnica futura, avaliar mecanismos nativos de Pipeline, Gestão de Artefatos e Rollback antes de implementá-los de forma customizada.
- M-015-02 (nova): definir, junto à Direção, os níveis esperados de Disponibilidade (Capítulo 24) e os tempos-alvo de resposta a Incidente (Capítulo 20) — hoje descritos apenas como conceito, sem número definido.
- M-015-03 (nova): estabelecer, em fase técnica futura, a cadência concreta de revisão de Capacidade (Capítulo 23) e de Evolução Contínua (Capítulo 29).

**15. Impacto desta Fase nas Próximas**
Esta arquitetura de DevOps e Operação é a referência obrigatória, junto ao TCOS-014, para a escolha de tecnologia real de entrega e operação — nenhuma escolha de CI/CD, orquestração ou ferramenta de operação deve introduzir um comportamento de pipeline, release, incidente ou mudança incompatível com o que está aqui documentado, sem registrar formalmente o motivo.

**16. Quality Score: 9,5/10**
Justificativa técnica: cobertura completa dos 27 tópicos exigidos, com identificação e resolução — não apenas menção — de lacunas conceituais reais (Pipeline, Releases, Rollback, Incidente/Problema/Mudança como conceitos distintos), todas em conformidade com os 18 Documentos Oficiais Congelados, sem nenhuma contradição encontrada. Não é 10 porque 3 melhorias novas (M-015-01 a M-015-03) permanecem como refinamento pendente de decisões futuras (ferramenta de CI/CD, metas numéricas de disponibilidade/resposta, cadência de revisão).

**17. Recomendação:** **APROVAR** — o documento cumpre integralmente o escopo solicitado, em nível conceitual, sem nenhuma decisão de tecnologia, e sem alterar nenhum documento anterior.

**18. Atualização do PROJECT_MEMORY.md:** ver commit correspondente — exclusivamente a seção da Fase 015.

**Estatísticas Finais**
- Quantidade total de páginas equivalentes: aproximadamente 19.
- Quantidade de entidades: 30 (referenciadas, 0 novas).
- Quantidade de regras: 47 no total do sistema; 0 citadas diretamente nesta arquitetura (fase de processo operacional, sem regra de negócio própria).
- Quantidade de processos/fluxos conceituais: 2 novos (Pipeline Conceitual de Entrega, Capítulo 5; Gestão de Incidentes, Capítulo 20).
- Quantidade de eventos: 0 novos.
- Quantidade de decisões registradas: 4 (D-015-01 a D-015-04, ver `PROJECT_MEMORY.md`).
- Quantidade de riscos ativos: 4 herdados; 0 novos.
- Quantidade de pendências: 8 (validação do documento + 7 herdadas).
- Quantidade de melhorias sugeridas: 3 novas (M-015-01 a M-015-03).
- Percentual estimado de maturidade do projeto: **97%** (subiu de 95% — a sexta arquitetura conceitual essencial [Backend, Frontend, Segurança, IA, Infraestrutura, DevOps/Operação] está completa e auditada; restam como não iniciadas: confirmação final do domínio de negócio via entrevista, escolha de tecnologia, e toda a fase de Desenvolvimento propriamente dita).

**Status desta fase:** rascunho aguardando validação do proprietário. Nenhuma escolha de CI/CD, ferramenta de pipeline, container, orquestração ou infraestrutura física será feita sem autorização explícita, conforme restrição do Prompt Oficial da Fase 015.

---

*Fim do documento — THE CHARCOAL OS DEVOPS AND OPERATIONAL ARCHITECTURE v1.0.0*
