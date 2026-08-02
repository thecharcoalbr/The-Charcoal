# THE CHARCOAL OS — IMPLEMENTATION MASTER PLAN

**Documento:** TCOS-017 — Plano Mestre de Implementação
**Projeto:** THE CHARCOAL OS
**Fase:** 017 — Implementation Master Plan
**Status:** Rascunho para validação do proprietário
**Versão:** 1.0.0

---

## EXECUTIVE MEMORY

- **Estado atual do projeto:** a arquitetura conceitual completa do THE CHARCOAL OS está concluída e protegida — 20 Documentos Oficiais Congelados (TCOS-000 a TCOS-016), a Constituição Permanente do Projeto, e o `PROJECT_MEMORY.md`, formando a Baseline Oficial v1.0.0. Esta fase não altera esse conteúdo — planeja **como** ele será implementado, ainda sem escolher nenhuma tecnologia.
- **Fase atual:** 017 — Implementation Master Plan (TCOS-017).
- **Fases concluídas:** 000 a 016, todas aprovadas e oficiais, mais a Constituição Permanente (documento de governança, fora da sequência de Fases).
- **Critério de contagem de Documentos Oficiais (vigente desde o registro da Constituição):** 20 Documentos Oficiais Congelados (TCOS-000 a TCOS-016) + 1 Documento Oficial Vivo (`PROJECT_MEMORY.md`) + a Constituição Permanente (documento de governança, autoridade máxima, não contado como Fase) = **21 Documentos Oficiais + 1 Constituição**.
- **Documento em elaboração:** este documento (TCOS-017) — `THE_CHARCOAL_OS_IMPLEMENTATION_MASTER_PLAN.md`.
- **Pendências:** as mesmas 8 pendências substantivas consolidadas na Fase 016, lideradas pela confirmação do domínio de negócio (R-000-03); parâmetros do Módulo 24; M-003A-03/04; decisão de negócio sobre Multiempresa/Multifilial; decisão de governança sobre anonimização de dado pessoal; lacuna de cobertura do TCOS-009 (M-010-03); priorização das Extensões Estruturais de IA (M-013-03); decisão sobre retomar a entrevista de descoberta.
- **Riscos ativos:** R-000-03/R-002-01, R-001-01/R-002-02, R-002A-01 — herdados; **R-000-03 é o risco de maior impacto para esta fase especificamente**, pois um Plano Mestre de Implementação pressupõe que o domínio de negócio será, de fato, o já modelado — este plano trata essa confirmação como pré-requisito do primeiro Sprint (Capítulo 11), nunca como um dado assumido.
- **Dependências para esta fase:** a Matriz de Dependências entre Módulos e a classificação Central/Auxiliar (System Architecture, TCOS-006, Capítulo 4); o Fluxo Global de Dados (TCOS-006, Capítulo 5); a Matriz de Integração entre Módulos (User Journeys and System Flows, TCOS-004); os 15 Serviços e Casos de Uso (Backend Architecture, TCOS-010); o Pipeline Conceitual de Entrega e os Critérios de Aprovação (DevOps and Operational Architecture, TCOS-015); a Política de Change Request e o processo de evolução (Constituição, Capítulos 14-15) — todos referenciados, nenhum reescrito.
- **Objetivo da fase que será iniciada:** definir a estratégia completa de implementação do THE CHARCOAL OS — ordem dos 27 módulos, definição de MVP, roadmap de entregas, estratégia de sprints, testes, homologação, migração, implantação, treinamento e gestão de risco — sem nenhuma decisão de tecnologia e sem escrever código.
- **O que não pode ser alterado:** nenhum conteúdo de nenhum dos 20 Documentos Oficiais Congelados, nem da Constituição Permanente.

### Auditoria de Consistência (executada antes de qualquer linha deste documento)

Foram lidos integralmente os 20 Documentos Oficiais Congelados, a Constituição Permanente e o `PROJECT_MEMORY.md`, com verificação específica de que o plano de implementação respeitará integralmente a Baseline Oficial. Resultado:

- **Nenhum conflito encontrado** entre a ordem de implementação proposta neste plano e qualquer dependência já documentada — a ordem dos 27 módulos (Capítulo 4) deriva diretamente da Matriz de Dependências já existente (TCOS-006, Capítulo 4), nunca de um critério novo e paralelo.
- **Achado tratado com transparência:** a Matriz de Dependências do TCOS-006 registra uma relação de colaboração mútua entre os Módulos 10 (Produção) e 16 (Estoque) — cada um lista o outro como dependência obrigatória ("16 depende de 15,10"; "10 depende de 13,16,24"). Isso não é uma inconsistência do TCOS-006 (a relação é de colaboração em tempo de execução, via Event Bus, não uma dependência de construção em uma única direção) — mas exige uma decisão explícita de **ordem de implementação**, já que os dois não podem, na prática, ser construídos em sequência estrita um após o outro. Este plano resolve isso implementando-os no mesmo bloco (Camada 3, Capítulo 4), sem alterar a documentação original.
- **Nenhuma decisão de negócio não confirmada foi assumida:** onde a ordem de implementação poderia ser influenciada por um parâmetro ainda pendente (ex.: prioridade de negócio real dos módulos, que só o proprietário pode confirmar), este plano apresenta a ordem **tecnicamente** correta (por dependência) e sinaliza explicitamente onde a Priorização por Valor de Negócio (Capítulo 6) é uma recomendação, sujeita à confirmação do proprietário, nunca um fato assumido.
- Nenhuma decisão de linguagem, framework, banco de dados, API, backend, frontend ou infraestrutura física foi tomada, em conformidade com a restrição explícita da fase.

**Resultado: nenhum conflito impeditivo encontrado.** A elaboração deste documento prossegue.

---

## 1. Papel deste Documento

Os 20 Documentos Oficiais Congelados definiram **o que** o THE CHARCOAL OS é e **como** ele se organiza, conceitualmente, em cada camada (negócio, dados, backend, frontend, segurança, IA, infraestrutura, DevOps). Este documento (TCOS-017) define **em que ordem e sob que critérios** essa arquitetura será efetivamente construída — a ponte final entre a Baseline Oficial v1.0.0 e o início do desenvolvimento real. Nenhuma tecnologia é escolhida aqui; nenhuma linha de código é escrita. Fornece o roteiro (Capítulos 3 a 22) que qualquer equipe de desenvolvimento seguirá a partir do momento em que o proprietário autorizar a implementação técnica.

## 2. Legenda e Convenções

- Toda referência a Módulo (01–27), Serviço, Entidade, Regra (RN-XXX) ou Integração (IN-XXX) usa exatamente os nomes/números já oficiais.
- **Camada de Implementação:** um agrupamento de módulos com dependências resolvidas entre si, implementados no mesmo intervalo do roadmap (Capítulo 4) — não deve ser confundido com "Camada" de arquitetura (TCOS-006/010).
- **Sprint:** o ciclo de trabalho no qual uma ou mais funcionalidades de um módulo são construídas, testadas e homologadas (Capítulos 10-12), sem tecnologia definida.
- **MVP (Produto Mínimo Viável):** o menor conjunto de módulos que permite operar o ciclo de negócio completo de um Evento, do primeiro contato comercial ao resultado financeiro apurado (Capítulo 7).

---

## 3. Estratégia Geral de Implementação

A implementação do THE CHARCOAL OS segue três princípios, todos já estabelecidos na Baseline Oficial e agora aplicados à execução:

- **Extensão, nunca reconstrução** (Framework, Seção 25; Constituição, Capítulo 13): cada módulo implementado se conecta aos já existentes via Event Bus e contratos públicos já definidos (TCOS-006/010) — nunca exige retrabalho do que já está em produção.
- **Cadeia de valor antes de recursos de apoio** (TCOS-006, Capítulo 5 — Fluxo Global de Dados): a ordem de implementação segue a mesma cadeia principal já documentada (Lead → Cliente → Orçamento → Contrato → Evento → Produção → Compras → Estoque → Financeiro → Dashboard CEO), implementando primeiro o que sustenta essa cadeia, depois o que a enriquece (Marketing, IA, Metas).
- **Nenhuma implementação antecipa uma decisão de negócio pendente:** todo módulo cuja operação dependa de um parâmetro ainda não confirmado (Módulo 24, R-002A-01) é implementado com o mesmo comportamento de bloqueio/alerta já definido — nunca com um valor assumido "só para poder testar".

## 4. Ordem de Implementação dos 27 Módulos

Deriva diretamente da Matriz de Dependências entre Módulos já definida (TCOS-006, Capítulo 4), organizada em 9 Camadas de Implementação sequenciais:

| Camada | Módulos | Razão da ordem |
|---|---|---|
| **0 — Fundação** | 24 Configurações, 25 Administração do Sistema | Sem dependência; todo módulo posterior consulta parâmetros (24) ou permissões (25) |
| **1 — Cadastros-base** | 12 Receitas, 15 Compras, 19 Funcionários, 27 Bancos, 05 Clientes | Entidades Mestres sem dependência obrigatória (TCOS-006, Capítulo 4) |
| **2 — Núcleo inicial** | 13 Fichas Técnicas, 02 Financeiro Pessoal | Dependem apenas da Camada 0-1 (12+24; 27) |
| **3 — Produção e Estoque (bloco colaborativo)** | 16 Estoque, 10 Produção, 14 Precificação | Estoque e Produção têm dependência mútua de operação (Auditoria de Consistência) — implementados no mesmo bloco; Precificação depende de Fichas Técnicas (Camada 2) |
| **4 — Comercial avançado** | 08 Orçamentos | Depende de Fichas Técnicas e Precificação (Camadas 2-3) |
| **5 — Fechamento comercial e operacional** | 09 Contratos, 07 Eventos, 11 Engenharia de Custos | Contratos depende de Orçamentos; Eventos depende de Clientes/Orçamentos/Contratos; Engenharia de Custos depende de Fichas Técnicas/Produção/Funcionários |
| **6 — Financeiro empresarial** | 03 Financeiro Empresarial | Depende de Eventos, Contratos, Compras, Funcionários, Bancos (Camadas 1-5) |
| **7 — Visão executiva mínima** | 01 Dashboard CEO (versão mínima) | Depende, para uma visão útil, de que a cadeia comercial-operacional-financeira já exista (Camadas 1-6) |
| **8 — Extensões de valor agregado** | 20 Escalas, 17 Lotes, 18 Equipamentos, 06 Leads, 04 CRM, 23 Documentos, 21 Marketing, 26 Metas, 22 Inteligência Artificial | Módulos Auxiliares (TCOS-006, Capítulo 4) que enriquecem a cadeia já operacional, sem serem pré-requisito dela |

Nenhuma Camada inicia antes que todas as suas dependências (Camadas anteriores) estejam implementadas e homologadas (Capítulo 12).

## 5. Dependências entre Módulos

Reafirma, sem redefinir, a Matriz de Dependências completa já publicada (TCOS-006, Capítulo 4) como a única fonte de verdade sobre "o que depende de quê". Este plano não cria uma segunda matriz de dependências — apenas a organiza em ordem de execução (Capítulo 4). Qualquer dúvida sobre se o Módulo X pode ser implementado antes do Módulo Y deve ser resolvida consultando a Matriz original do TCOS-006, nunca por suposição durante o desenvolvimento.

## 6. Priorização por Valor de Negócio

**Recomendação sujeita à confirmação do proprietário** (nunca um fato assumido, conforme a Auditoria de Consistência desta fase): dentro de cada Camada de Implementação (Capítulo 4), a prioridade sugerida segue o valor de negócio já evidenciado pela Cadeia de Valor (TCOS-006, Capítulo 5) — Comercial e Produção antes de Marketing e IA, pois é a cadeia comercial-operacional-financeira que gera receita e permite medir resultado real; Auxiliares que otimizam (Escalas, Lotes) ou ampliam (Marketing, IA) vêm depois de a cadeia principal já operar de ponta a ponta. O proprietário pode reordenar módulos dentro da mesma Camada (nunca entre Camadas, o que quebraria uma dependência técnica) conforme sua própria priorização de negócio.

## 7. Definição do MVP

O MVP do THE CHARCOAL OS é definido como o conjunto de módulos que permite operar **um Evento real, do primeiro Orçamento ao resultado financeiro apurado**, com visão executiva mínima — as Camadas 0 a 7 (Capítulo 4), totalizando **18 módulos**:

24, 25, 12, 15, 19, 27, 05, 13, 02, 16, 10, 14, 08, 09, 07, 11, 03, 01 (versão mínima).

O MVP inclui deliberadamente a Engenharia de Custos (Módulo 11) — apurar se um Evento foi lucrativo é o núcleo do valor de negócio já expresso em toda a documentação (margem, PF-07). O MVP **não inclui**: sugestão automática de Escala (20 — alocação pode ser manual no MVP), rastreabilidade completa por Lote (17 — Estoque opera por saldo agregado no MVP), CRM/Leads/Marketing (04/06/21 — aquisição comercial pode ser tratada fora do sistema no MVP), Documentos automáticos (23 — geração manual no MVP), Metas (26) e Inteligência Artificial (22) — todos no Roadmap Pós-MVP (Capítulo 9).

## 8. Roadmap de Entregas

| Etapa | Camadas | Módulos | Entrega de valor |
|---|---|---|---|
| Entrega 1 — Fundação | 0-1 | 24, 25, 12, 15, 19, 27, 05 | Sistema operável, cadastros básicos prontos |
| Entrega 2 — Custo e Caixa Pessoal | 2 | 13, 02 | Custo de produção calculável; controle financeiro pessoal ativo |
| Entrega 3 — Núcleo Operacional | 3 | 16, 10, 14 | Produção e Estoque operando; preço calculável |
| Entrega 4 — Núcleo Comercial | 4-5 | 08, 09, 07, 11 | Ciclo comercial completo; margem por Evento apurável |
| Entrega 5 — Financeiro Empresarial e Visão | 6-7 | 03, 01 (mínimo) | **MVP completo** — ciclo de negócio de ponta a ponta |
| Entrega 6 (Pós-MVP) — Eficiência Operacional | 8 (parte 1) | 20, 17, 18 | Escala automática, rastreabilidade de Lote, gestão de Equipamento |
| Entrega 7 (Pós-MVP) — Crescimento Comercial | 8 (parte 2) | 06, 04, 21 | Funil de Leads, CRM consolidado, Marketing |
| Entrega 8 (Pós-MVP) — Inteligência e Governança | 8 (parte 3) | 23, 26, 22 | Documentos automáticos, Metas, Inteligência Artificial |

## 9. Roadmap Pós-MVP

Reafirma a Camada 8 (Capítulo 4) como o Pós-MVP, sem alteração de escopo em relação aos 27 módulos já oficiais — nenhum módulo novo é criado. A ordem interna do Pós-MVP (Entregas 6-8, Capítulo 8) prioriza primeiro eficiência operacional (reduz custo/erro na operação já existente), depois crescimento comercial (amplia a entrada de negócio), e por último inteligência e governança (otimiza decisão sobre uma base de dados operacional já madura — a IA, em particular, produz sugestões mais confiáveis quanto mais histórico operacional já existir, Capítulo 9 do TCOS-013).

## 10. Estratégia de Sprints

Cada módulo (ou conjunto pequeno de módulos da mesma Camada) é implementado em um ou mais Sprints, seguindo integralmente o Pipeline Conceitual de Entrega já definido (DevOps and Operational Architecture, TCOS-015, Capítulo 5): Construção → Verificação Automatizada → Verificação Manual → Aprovação → Implantação → Operação. Um Sprint nunca implementa um módulo fora da sua Camada de Implementação (Capítulo 4) antes de suas dependências estarem prontas. O tamanho de um Sprint é definido pela equipe técnica no momento da implementação (decisão fora do escopo conceitual desta fase) — este plano define apenas a ordem e os critérios, nunca a duração.

## 11. Critérios para Início de cada Sprint

1. Todos os módulos das Camadas anteriores (Capítulo 4) já implantados e homologados (Capítulo 12).
2. Todas as Regras de Negócio (TCOS-002A) e Casos de Uso (TCOS-010) do módulo do Sprint já revisados pela equipe de implementação.
3. Todo parâmetro de Configuração (Módulo 24) necessário ao módulo do Sprint já confirmado pelo proprietário — nunca iniciado com um valor assumido (R-002A-01).
4. Para o primeiro Sprint do projeto: confirmação explícita do domínio de negócio (R-000-03) pelo proprietário — pré-requisito específico desta fase, dado o impacto de R-000-03 sobre toda a arquitetura já construída.

## 12. Critérios para Encerramento de cada Sprint

Reafirma os Critérios de Aprovação já definidos (TCOS-015, Capítulo 17), aplicados ao encerramento de cada Sprint: Testes Automatizados (Capítulo 13) aprovados; nenhuma Regra de Negócio (TCOS-002A) quebrada; Testes Manuais (Capítulo 14) concluídos quando aplicável; e a Validação pelo Proprietário (Capítulo 15) explicitamente registrada antes de o módulo avançar para o próximo Ambiente (TCOS-014, Capítulo 5).

## 13. Estratégia de Testes

Reafirma, sem redefinir, os Testes Automatizados e Manuais já formalizados (TCOS-015, Capítulos 15-16): verificação de unidade por Caso de Uso, verificação de integração por Integração (TCOS-009), verificação de regressão a cada novo módulo implementado. Todo teste de um módulo novo inclui, obrigatoriamente, a verificação de que nenhuma Integração já implementada em uma Camada anterior foi quebrada (PF-11) — nunca um teste isolado que ignore o efeito cascata já documentado (TCOS-009).

## 14. Estratégia de Homologação

A homologação de um módulo ocorre no Ambiente de Staging (TCOS-014, Capítulo 5), com dado estruturalmente idêntico ao de Produção, nunca dado real de Cliente/Financeiro. Homologa-se contra os critérios já definidos nas 98 funcionalidades (TCOS-003) e nas telas correspondentes (TCOS-005/011) — um módulo só é considerado homologado quando seu comportamento reproduz exatamente o que já foi especificado, nunca uma aproximação aceita "por enquanto".

## 15. Estratégia de Validação pelo Proprietário

Reafirma o mesmo ciclo de comando formal já usado em toda a Baseline Oficial (Constituição, Capítulo 9): ao final de cada Entrega (Capítulo 8), o proprietário valida o módulo implementado em Staging e responde com um dos cinco comandos formais (`APROVADO`, `CORRIGIR`, `ALTERAR`, `REMOVER`, `CONTINUAR`) antes da promoção a Production (TCOS-014, Capítulo 5 — Ambientes). Nenhum módulo é promovido a Production sem essa validação explícita — mesma disciplina de Critério de Aprovação mais rigoroso já definida para esse Ambiente (TCOS-015, Capítulo 17).

## 16. Estratégia de Migração de Dados

**Novo tópico, formalizado nesta fase.** O THE CHARCOAL OS parte de uma operação que hoje, presumivelmente, já existe fora do sistema (planilhas, papel, outro software) — mas nenhuma suposição sobre o formato desse dado é feita aqui (decisão de negócio ainda pendente, relacionada a R-000-03). Princípios gerais, sem tecnologia:

- Toda migração de dado histórico (Cliente, Fornecedor, Ingrediente, Funcionário já existentes) ocorre módulo a módulo, na mesma ordem de implementação (Capítulo 4) — nunca uma migração única e monolítica de todo o histórico de uma vez.
- Todo dado migrado recebe os mesmos Metadados Universais já exigidos (TCOS-007, Capítulo 2) — Identificador Global, autor "Migração", data — nunca um dado sem origem rastreável (PF-04).
- Nenhuma migração assume que o dado de origem já está no formato esperado pelas 47 Regras de Negócio — toda migração passa pela mesma validação de dado obrigatório já exigida na criação normal de uma entidade (TCOS-007, Capítulo 4).

## 17. Estratégia de Implantação

Reafirma, sem redefinir, a Estrutura de Deploy e a Gestão de Ambientes já definidas (TCOS-014, Capítulo 6; TCOS-015, Capítulo 11): cada módulo é implantado de forma independente, sempre reversível (Rollback, TCOS-015 Capítulo 9), seguindo a sequência de Ambientes Development → Test → Staging → Production. A implantação de um módulo em Production nunca ocorre sem que os módulos das Camadas anteriores (Capítulo 4) já estejam estáveis em Production — evitando que uma nova implantação seja testada, na prática, sobre uma base ainda instável.

## 18. Estratégia de Treinamento do Usuário

**Novo tópico, formalizado nesta fase.** Cada Entrega (Capítulo 8) inclui treinamento dos Perfis diretamente afetados (TCOS-012, Capítulo 9) antes da promoção a Production — nunca um sistema novo entregue sem capacitação de quem vai operá-lo. O treinamento segue os mesmos seis compromissos de Experiência do Usuário já definidos (TCOS-005, Capítulo 6): prioriza Simplicidade e Velocidade, demonstrando primeiro as ações mais frequentes de cada Perfil (ex.: para Comercial, criar Orçamento; para Produção, planejar e concluir Produção). O treinamento é sempre acompanhado do material de apoio já implícito no Design System (TCOS-005/011) — a interface deve ser autoexplicativa o suficiente para que o treinamento formal seja curto, nunca um substituto de uma interface mal desenhada.

## 19. Estratégia de Evolução Contínua

Reafirma, sem alteração, a Evolução Contínua já definida (TCOS-015, Capítulo 29): todo Problema identificado em Produção, toda Métrica Operacional fora do esperado, e todo feedback do proprietário durante a Validação (Capítulo 15) alimentam um ciclo permanente de ajuste — nunca um "projeto fechado" após o MVP. A evolução pós-MVP segue exclusivamente o processo de Change Request já definido na Constituição (Capítulo 14) quando envolver alterar um documento já congelado, e o Pipeline normal (Capítulo 10) quando for uma nova funcionalidade dentro do escopo já aprovado.

## 20. Gestão de Riscos da Implementação

| Risco | Descrição | Mitigação |
|---|---|---|
| Domínio de negócio não confirmado (R-000-03) | Implementar sobre uma hipótese de negócio nunca formalmente validada | Confirmação obrigatória antes do primeiro Sprint (Capítulo 11, item 4) |
| Parâmetro de Configuração ausente no início de um Sprint | Módulo bloqueado ou implementado com valor assumido incorretamente | Critério de início de Sprint (Capítulo 11, item 3) — nunca assumir valor |
| Módulo colaborativo (Produção/Estoque) implementado fora de ordem | Retrabalho por dependência mútua não resolvida | Implementação em bloco único (Camada 3, Capítulo 4) |
| Migração de dado histórico malformado | Entidade criada sem os dados obrigatórios já exigidos | Validação de dado obrigatório aplicada também à migração (Capítulo 16) |
| Quebra de Integração já implementada por um módulo novo | Regressão silenciosa em Produção (violação de PF-11) | Teste de regressão obrigatório a cada novo módulo (Capítulo 13) |
| Adoção insuficiente por falta de treinamento | Sistema implantado, mas subutilizado ou operado incorretamente | Treinamento obrigatório antes de cada promoção a Production (Capítulo 18) |

## 21. Critérios de Aceite

Um módulo é aceito pelo proprietário quando, cumulativamente: (1) todas as suas funcionalidades (TCOS-003) e telas (TCOS-005/011) correspondentes estão implementadas e homologadas (Capítulo 14); (2) todas as Regras de Negócio (TCOS-002A) aplicáveis foram verificadas por teste automatizado (Capítulo 13); (3) nenhuma Integração (TCOS-009) já existente foi quebrada; (4) o treinamento do(s) Perfil(is) afetado(s) foi realizado (Capítulo 18); e (5) o proprietário emitiu o comando formal `APROVADO` para aquela Entrega (Capítulo 15). Nenhum módulo é considerado aceito sem os cinco critérios simultaneamente satisfeitos.

## 22. Checklist Obrigatório Antes de Iniciar Qualquer Desenvolvimento

1. Confirmação explícita do domínio de negócio pelo proprietário (R-000-03).
2. Autorização formal do proprietário para iniciar a implementação técnica (Constituição, Capítulo 20).
3. Escolha de tecnologia (linguagem, framework, banco de dados, infraestrutura, CI/CD) registrada como uma nova Fase ou Change Request formal — nunca decidida durante o próprio desenvolvimento.
4. Ambientes (TCOS-014, Capítulo 5) provisionados e Health Checks (TCOS-014, Capítulo 20) operacionais antes do primeiro Sprint.
5. Equipe de implementação com acesso de leitura à Baseline Oficial v1.0.0 completa — nenhum desenvolvimento inicia com conhecimento parcial da arquitetura já aprovada.
6. Este Plano Mestre de Implementação (TCOS-017) formalmente aprovado pelo proprietário.

---

## RESUMO PARA O PROPRIETÁRIO

**O que foi construído:** o roteiro completo de como o THE CHARCOAL OS será implementado — em que ordem os 27 módulos serão construídos, o que compõe a primeira versão utilizável (MVP), o que vem depois, e como cada etapa será testada, validada por você e colocada no ar com segurança.

**Por que isso é importante:** depois de toda a arquitetura pronta, a pergunta que faltava responder era "por onde começar, e como saber que cada parte está pronta antes de seguir para a próxima". Este documento responde exatamente isso, sem ainda escolher nenhuma tecnologia.

**Quais benefícios traz:** você sabe, desde já, que o MVP (18 módulos) entrega o ciclo completo de negócio — do primeiro Orçamento ao resultado financeiro de um Evento — antes de qualquer módulo "bônus" (Marketing, Inteligência Artificial, Metas) ser construído. Isso significa valor de negócio real o mais cedo possível, com o restante chegando de forma incremental e nunca exigindo retrabalho do que já estiver pronto.

**Como se conecta com os documentos anteriores:** a ordem dos módulos vem diretamente da Matriz de Dependências já aprovada (TCOS-006); os critérios de teste e aprovação vêm do TCOS-015; a validação por você segue o mesmo ciclo de comandos formais usado em todo o projeto. Nada foi inventado — tudo foi organizado em um plano executável.

**Como prepara o próximo passo:** com este plano aprovado, o próximo passo natural é a decisão de tecnologia — e, a partir dela, o primeiro Sprint real, começando pela Camada 0 (Configurações e Administração), assim que o domínio de negócio for formalmente confirmado.

---

## TCOS QUALITY GATE EXECUTIVO

**Resumo Executivo**
Definido o Plano Mestre de Implementação do THE CHARCOAL OS: 27 módulos organizados em 9 Camadas de Implementação por dependência técnica (TCOS-006), MVP definido em 18 módulos (Camadas 0-7), Pós-MVP em 9 módulos (Camada 8) distribuídos em 3 entregas adicionais, estratégia completa de Sprint/Testes/Homologação/Validação/Migração/Implantação/Treinamento/Evolução, e gestão de risco da implementação. Nenhuma tecnologia foi definida; nenhum código foi escrito; nenhum documento da Baseline Oficial foi alterado.

**Estado Atual do Projeto**
Baseline Oficial v1.0.0 completa e protegida pela Constituição Permanente (TCOS-000 a TCOS-016 + Constituição). Fase 017 em validação. Nenhuma tecnologia escolhida; nenhum desenvolvimento iniciado.

**Dependências**
Matriz de Dependências entre Módulos e Fluxo Global de Dados (TCOS-006); Matriz de Integração (TCOS-004); Serviços e Casos de Uso (TCOS-010); Pipeline e Critérios de Aprovação (TCOS-015); Ambientes (TCOS-014); Política de Change Request (Constituição) — todos referenciados, nenhum reescrito.

**Riscos**
R-000-03/R-002-01, R-001-01/R-002-02, R-002A-01 — herdados. R-000-03 é tratado nesta fase como pré-requisito explícito do primeiro Sprint (Capítulo 11), o tratamento mais direto já dado a esse risco em qualquer fase do projeto. Nenhum risco novo de arquitetura.

**Pendências**
As mesmas 8 pendências substantivas herdadas da Fase 016, sem nenhuma nova. A confirmação do domínio de negócio (R-000-03) passa a ser, formalmente, um item do Checklist Obrigatório (Capítulo 22) antes de qualquer desenvolvimento.

**Cronograma Macro**
9 Camadas de Implementação (Capítulo 4) → 8 Entregas (Capítulo 8) → MVP ao final da Entrega 5 → 3 Entregas Pós-MVP (6-8) completando os 27 módulos. Duração de cada Sprint/Entrega não é definida nesta fase (depende da tecnologia e da equipe, ainda não escolhidas).

**Ordem Oficial de Implementação**
Camada 0: 24, 25 → Camada 1: 12, 15, 19, 27, 05 → Camada 2: 13, 02 → Camada 3: 16, 10, 14 → Camada 4: 08 → Camada 5: 09, 07, 11 → Camada 6: 03 → Camada 7: 01 (mínimo) → Camada 8 (Pós-MVP): 20, 17, 18, 06, 04, 23, 21, 26, 22.

**Módulos do MVP (18)**
24 Configurações, 25 Administração do Sistema, 12 Receitas, 15 Compras, 19 Funcionários, 27 Bancos, 05 Clientes, 13 Fichas Técnicas, 02 Financeiro Pessoal, 16 Estoque, 10 Produção, 14 Precificação, 08 Orçamentos, 09 Contratos, 07 Eventos, 11 Engenharia de Custos, 03 Financeiro Empresarial, 01 Dashboard CEO (versão mínima).

**Módulos das Fases Seguintes (9, Pós-MVP)**
20 Escalas, 17 Lotes, 18 Equipamentos, 06 Leads, 04 CRM, 23 Documentos, 21 Marketing, 26 Metas, 22 Inteligência Artificial.

**Quality Score: 9,5/10**
Justificativa técnica: cobertura completa dos 20 tópicos exigidos, ordem de implementação derivada rigorosamente da Matriz de Dependências já oficial (nenhum critério novo e arbitrário), tratamento explícito e transparente da dependência mútua Produção/Estoque, e definição de MVP com justificativa de valor de negócio clara. Não é 10 porque a Priorização por Valor de Negócio (Capítulo 6) e a definição exata de MVP (Capítulo 7), embora tecnicamente sólidas, permanecem sujeitas à confirmação final do proprietário — este plano recomenda, mas não impõe, a priorização de negócio.

**Atualização do PROJECT_MEMORY.md:** ver commit correspondente.

**Estatísticas Finais**
- Módulos organizados: 27/27 (100%).
- Camadas de Implementação: 9.
- Entregas do Roadmap: 8 (5 até o MVP + 3 Pós-MVP).
- Módulos do MVP: 18 (67% dos módulos).
- Módulos Pós-MVP: 9 (33% dos módulos).
- Riscos ativos: 4 herdados; 0 novos.
- Pendências: 8, todas herdadas.
- Melhorias: 0 novas nesta fase.
- Percentual estimado de maturidade do projeto: **97%** (inalterado — este plano organiza a execução da Baseline já completa, sem ampliar seu escopo conceitual).

**Status desta fase:** rascunho aguardando validação do proprietário. Nenhuma tecnologia foi escolhida; nenhum código foi escrito; nenhum desenvolvimento foi iniciado, conforme restrição explícita do Prompt Oficial da Fase 017.

---

*Fim do documento — THE CHARCOAL OS IMPLEMENTATION MASTER PLAN v1.0.0*