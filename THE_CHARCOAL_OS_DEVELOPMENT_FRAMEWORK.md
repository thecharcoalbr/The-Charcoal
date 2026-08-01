# THE CHARCOAL OS DEVELOPMENT FRAMEWORK

**Documento:** Constituição Oficial do Projeto
**Projeto:** THE CHARCOAL OS
**Fase:** 000 — Governança do Projeto
**Status:** APROVADO pelo proprietário em 2026-08-01
**Versão:** 1.1.0

### Histórico de Versões deste Documento

| Versão | Data | Natureza | Descrição |
|---|---|---|---|
| 1.0.0 | 2026-08-01 | Inicial | Primeira versão da Constituição (Seções 1–20, Regras Permanentes). |
| 1.1.0 | 2026-08-01 | MINOR (adição compatível) | Complementação solicitada pelo proprietário (comando `ALTERAR`): adicionadas Seções 21–26 (Manifesto, Princípios Fundamentais, Documentos Oficiais, Glossário Oficial, Filosofia de Evolução, Auditoria de Revisão). Nenhum conteúdo da v1.0.0 foi removido ou alterado. |
| 1.1.0 | 2026-08-01 | Aprovação | Documento aprovado pelo proprietário via comando `APROVADO`, sem novas alterações de conteúdo. Passa a integrar oficialmente a documentação do THE CHARCOAL OS. |

---

## 0. Preâmbulo

Este documento é a Constituição do projeto THE CHARCOAL OS. Nenhuma linha de código, esquema de banco de dados, tela, API ou funcionalidade poderá ser criada antes da aprovação formal deste documento pelo proprietário do projeto. A partir da aprovação, este framework passa a ser de observância obrigatória em todas as fases subsequentes, e qualquer alteração a ele exige novo ciclo de aprovação explícita.

---

## 1. Missão do Framework

Estabelecer o conjunto único e obrigatório de regras de governança, engenharia e qualidade que regerá a concepção, o desenvolvimento, a evolução e a manutenção do THE CHARCOAL OS, garantindo que todas as decisões técnicas e de produto sejam tomadas de forma rastreável, consistente e alinhada ao padrão de engenharia praticado por organizações como Microsoft, Apple, Google, Oracle e SAP — independentemente de quem execute o trabalho ou em qual fase o projeto se encontre.

## 2. Visão do Projeto

THE CHARCOAL OS deverá se consolidar como um sistema de gestão empresarial (ERP/CRM) de referência para o seu segmento, construído sobre uma arquitetura modular, escalável, segura e auditável, capaz de sustentar crescimento contínuo em volume de dados, número de usuários e complexidade de negócio sem exigir reescritas estruturais. O sistema deve ser percebido pelos usuários como confiável, coerente e previsível, e pelos engenheiros que nele trabalham como bem documentado e seguro de estender.

## 3. Objetivos

1. Definir uma governança formal que preceda e discipline todo o desenvolvimento técnico.
2. Garantir rastreabilidade completa de decisões, mudanças e riscos ao longo do tempo.
3. Impedir o início de qualquer fase sem auditoria da fase anterior.
4. Assegurar consistência arquitetural entre todos os módulos do sistema (financeiro, custos, CRM, BI, etc.).
5. Proteger o projeto contra desvios de escopo não documentados.
6. Estabelecer critérios objetivos e verificáveis de conclusão para cada fase.
7. Preservar uma memória cumulativa do projeto, acessível e obrigatória para fases futuras.
8. Garantir que o proprietário do projeto mantenha controle final sobre toda decisão relevante.

## 4. Filosofia do Desenvolvimento

- **Governança antes de código.** Nenhuma fase técnica se inicia sem que suas regras e critérios de aceite estejam definidos e aprovados.
- **Arquitetura como produto de primeira classe.** Decisões estruturais recebem o mesmo rigor de revisão que funcionalidades voltadas ao usuário.
- **Simplicidade deliberada, não simplismo.** Escolhe-se a solução mais simples que atenda aos requisitos reais — nunca a mais simples de se implementar às custas de qualidade.
- **Nada é assumido, tudo é registrado.** Toda decisão relevante tem motivo documentado; ausência de registro é tratada como ausência de decisão.
- **Reversibilidade como critério de risco.** Ações de alto impacto e difícil reversão exigem validação explícita do proprietário antes de execução.
- **Consistência sobre conveniência local.** Um módulo não deve resolver seu problema de forma que quebre padrões usados pelos demais.
- **Qualidade é contínua, não uma etapa final.** Revisão, auditoria e validação ocorrem em todas as transições de fase, não apenas ao final do projeto.

## 5. Padrões de Qualidade

Todo entregável de qualquer fase deve atender, no mínimo, a:

- **Corretude funcional**: a funcionalidade faz o que se propõe a fazer, nos casos normais e nos casos-limite documentados.
- **Escalabilidade**: a solução suporta crescimento esperado de dados, usuários e carga sem redesenho estrutural.
- **Segurança**: segue princípios de menor privilégio, validação de entradas em fronteiras do sistema, e proteção de dados sensíveis (financeiros, cadastrais, credenciais).
- **Manutenibilidade**: código e estruturas são compreensíveis por terceiros sem depender do autor original; complexidade acidental é evitada.
- **Desempenho**: operações críticas de negócio possuem expectativa de desempenho definida e verificável.
- **Experiência do usuário**: interfaces e fluxos são coerentes com os padrões já estabelecidos em módulos anteriores.
- **Documentação mínima obrigatória**: toda decisão de arquitetura relevante, todo módulo novo e toda mudança de escopo possuem registro formal (ver Seções 7 e 8).

Nenhum entregável é considerado "pronto" sem revisão contra estes sete critérios.

## 6. Critérios para Aprovação de cada Fase

Uma fase somente é submetida à aprovação do proprietário quando:

1. Todos os itens do escopo definido para a fase foram entregues.
2. A auditoria de início de fase (Seção 17) foi executada e suas pendências resolvidas.
3. A revisão de finalização de fase (Seção 18) foi executada sem inconsistências abertas.
4. O Relatório de Fase foi produzido, seguindo a estrutura padrão (ver Regra de Relatório Final).
5. Riscos identificados foram registrados, mesmo que não solucionados.
6. Não existem conflitos não resolvidos com fases anteriores.

A aprovação é um ato exclusivo do proprietário, manifestado por um dos comandos formais: `APROVADO`, `CORRIGIR`, `ALTERAR`, `REMOVER` ou `CONTINUAR`.

## 7. Como Documentar Decisões

- Toda decisão técnica ou de produto relevante é registrada em um **Registro de Decisões (Decision Log)**, cumulativo, mantido a partir da Fase 000.
- Cada entrada do Registro de Decisões contém, no mínimo: data, fase, decisão tomada, alternativas consideradas, motivo da escolha, e responsável.
- Decisões sem motivo registrado são consideradas inválidas e devem ser refeitas com a devida justificativa antes de seguir adiante.
- Decisões que revertem ou alteram decisões anteriores devem referenciar explicitamente a entrada original.

## 8. Como Registrar Alterações

- Toda alteração relevante em escopo, arquitetura, regras de negócio ou estrutura de dados é registrada em um **Changelog do Projeto**, organizado por fase e por módulo.
- Cada alteração descreve: o que mudou, por que mudou, o que foi impactado, e quem aprovou.
- Alterações não documentadas não são consideradas parte oficial do histórico do projeto, mesmo que tecnicamente implementadas.

## 9. Como Evitar Inconsistências

- Toda nova fase é obrigatoriamente precedida por auditoria contra as fases anteriores (Seção 17).
- Convenções de nomenclatura, padrões de dados e padrões de interface, uma vez definidos, são de uso obrigatório em todos os módulos subsequentes.
- Divergências entre módulos devem ser resolvidas antes do avanço de fase, nunca "corrigidas depois".
- Qualquer inconsistência identificada é registrada no Registro de Riscos (Seção 13) até sua resolução formal.

## 10. Como Validar Novas Funcionalidades

Toda nova funcionalidade proposta passa pelos seguintes filtros, nesta ordem:

1. **Alinhamento com a Visão** (Seção 2) — a funcionalidade serve ao propósito do produto?
2. **Impacto arquitetural** — quais módulos são afetados e como?
3. **Análise de vantagens e desvantagens** — apresentada de forma explícita, nunca omitida em favor da opção "mais simples".
4. **Critérios de qualidade** (Seção 5) — a proposta atende aos sete critérios mínimos?
5. **Aprovação do proprietário** — nenhuma funcionalidade nova é implementada sem validação explícita.

Funcionalidades rejeitadas são registradas na memória cumulativa (Regra de Memória), com o motivo da rejeição preservado para consulta futura.

## 11. Como Tratar Mudanças de Escopo

- Toda mudança de escopo é tratada como um evento formal, nunca como um ajuste silencioso.
- Deve ser registrada com: escopo original, escopo proposto, motivo da mudança, impacto em prazo/arquitetura/módulos já entregues.
- Mudanças de escopo que afetam fases já aprovadas exigem nova auditoria dessas fases antes de seguir adiante.
- Nenhuma mudança de escopo é assumida como aprovada por omissão; exige manifestação expressa do proprietário.

## 12. Como Controlar Versões

- O projeto adota versionamento semântico (`MAJOR.MINOR.PATCH`) para este framework, para módulos e, futuramente, para releases do sistema.
- `MAJOR`: mudança que quebra compatibilidade ou redefine regras de governança/arquitetura.
- `MINOR`: adição de funcionalidade ou regra compatível com o que já existe.
- `PATCH`: correção, esclarecimento ou ajuste que não altera comportamento ou regra estabelecida.
- Todo controle de versão de código-fonte segue histórico em sistema de controle de versões (Git), com commits descritivos e rastreáveis às decisões do Registro de Decisões.
- Este documento (o Framework) é ele próprio versionado; toda alteração nele incrementa a versão e é registrada no Changelog do Projeto.

## 13. Como Registrar Riscos

- Mantém-se um **Registro de Riscos**, cumulativo, com: descrição do risco, fase de origem, probabilidade, impacto, mitigação proposta, status (aberto/mitigado/aceito/encerrado).
- Nenhum risco identificado é descartado sem registro, mesmo que julgado de baixa relevância.
- Riscos em aberto ao final de uma fase são obrigatoriamente citados no Relatório da Fase e reavaliados na auditoria da fase seguinte.

## 14. Como Registrar Melhorias

- Mantém-se um **Backlog de Melhorias**, cumulativo, separado do escopo formal de cada fase.
- Toda melhoria sugerida — por qualquer membro do "comitê" (papéis especializados desta IA) — é registrada com: descrição, justificativa, módulo afetado, e benefício esperado.
- Melhorias não aprovadas permanecem no backlog para reavaliação futura; não são descartadas apenas por não caberem na fase atual.

## 15. Como Manter Consistência entre Módulos

- Um **Glossário Único de Domínio** é mantido desde a primeira fase técnica, com termos de negócio e seus significados exatos (ex.: definições de custo, cliente, pedido, contas a pagar/receber).
- Padrões de dados, nomenclatura, tratamento de erros e camadas arquiteturais definidos para um módulo são vinculantes para os demais, salvo decisão explícita em contrário, registrada e justificada.
- Toda nova fase revisa o Glossário e os padrões vigentes antes de propor qualquer estrutura nova.

## 16. Regras para Integração entre Módulos

- Nenhum módulo acessa dados de outro módulo diretamente sem um contrato de integração formalmente definido (interface, evento ou serviço definido em fase própria).
- Toda integração nova é registrada no **Mapa de Integrações do Projeto**, cumulativo, indicando origem, destino, natureza dos dados trocados e dependências geradas.
- Mudanças em um módulo que quebrem contratos de integração existentes são tratadas como mudança de escopo (Seção 11) e exigem auditoria dos módulos dependentes antes de aprovação.

## 17. Processo Obrigatório de Auditoria Antes de Iniciar Qualquer Nova Fase

Antes do início de qualquer fase, é obrigatório:

1. Ler integralmente o histórico de todas as fases anteriores (Registro de Decisões, Changelog, Registro de Riscos, Backlog de Melhorias, Mapa de Integrações).
2. Auditar o estado atual do projeto em busca de inconsistências, conflitos, duplicidades e oportunidades de melhoria.
3. Corrigir os problemas encontrados que estejam dentro do escopo já aprovado.
4. Caso seja encontrado qualquer conflito que exija decisão de escopo ou arquitetura não coberta por decisão prévia, o trabalho é interrompido imediatamente e a orientação do proprietário é solicitada antes de prosseguir.

Nenhuma fase nova tem sua primeira entrega produzida antes da conclusão deste processo.

## 18. Processo Obrigatório de Revisão Antes de Finalizar Qualquer Fase

Antes de declarar uma fase finalizada, é obrigatório:

1. Revisar todos os entregáveis da fase contra os Padrões de Qualidade (Seção 5).
2. Verificar aderência aos padrões e convenções estabelecidos em fases anteriores (Seção 9 e 15).
3. Consolidar o Registro de Riscos e o Backlog de Melhorias com os itens surgidos durante a fase.
4. Produzir o Relatório da Fase, na estrutura padrão obrigatória.
5. Confirmar que não há pendência técnica crítica sem registro explícito.

## 19. Processo Obrigatório de Validação pelo Proprietário

- Nenhuma fase é considerada aprovada sem manifestação expressa do proprietário através de um dos comandos formais: `APROVADO`, `CORRIGIR`, `ALTERAR`, `REMOVER` ou `CONTINUAR`.
- Silêncio não constitui aprovação.
- Caso o proprietário solicite `CORRIGIR` ou `ALTERAR`, a fase permanece aberta até nova submissão e novo ciclo de validação.
- Caso o proprietário solicite `REMOVER`, o item é retirado do escopo e registrado como rejeitado na memória cumulativa, com motivo.

## 20. Critérios para que uma Fase seja Considerada Concluída

Uma fase é considerada oficialmente concluída somente quando, cumulativamente:

1. Todos os critérios da Seção 6 foram atendidos.
2. O processo de revisão da Seção 18 foi executado sem pendência crítica em aberto.
3. O Relatório da Fase foi entregue na estrutura obrigatória.
4. O proprietário respondeu com o comando `APROVADO`.
5. O histórico cumulativo (Regra de Memória) foi atualizado com o resultado da fase.

Até que estas cinco condições sejam satisfeitas simultaneamente, a fase permanece em aberto e nenhuma fase subsequente pode ser iniciada.

---

## 21. Manifesto do THE CHARCOAL OS

### O que é o THE CHARCOAL OS

THE CHARCOAL OS é o sistema de gestão empresarial (ERP/CRM) proprietário que unifica, em um único ecossistema, todo o ciclo operacional do negócio: relacionamento com clientes e leads, orçamentos e contratos, produção (receitas, fichas técnicas, ingredientes, lotes), estoque, compras e fornecedores, gestão financeira (despesas, receitas financeiras, fluxo de caixa) e inteligência de negócio (dashboards executivos). Não é um ERP genérico adaptado ao negócio — é um sistema operacional de negócio desenhado desde a origem em torno do vocabulário, dos processos e das prioridades reais da operação que ele serve.

### Missão

Eliminar a fragmentação de sistemas e planilhas, garantir que cada dado exista uma única vez e seja compartilhado automaticamente entre todas as áreas da empresa, e colocar nas mãos do proprietário uma visão executiva completa, confiável e em tempo real do negócio — do custo de um único ingrediente ao resultado financeiro consolidado da empresa.

### Visão de Longo Prazo

Ser, em até dez anos, o sistema operacional central da empresa e de suas eventuais unidades e franquias: a única fonte de verdade para dados de clientes, produção, estoque e finanças, capaz de sustentar múltiplas unidades, um aplicativo mobile, integrações bancárias e uma camada de inteligência artificial nativa — sem exigir reconstrução da base já existente.

### Problemas que Resolve

- Dados cadastrados repetidamente em sistemas ou planilhas diferentes, gerando divergência e retrabalho.
- Cálculo de custo de produção feito manualmente ou em múltiplos lugares, com risco de divergir do custo real.
- Ausência de uma visão executiva única e atualizada do negócio (financeiro, produção e vendas vistos separadamente).
- Falta de histórico e rastreabilidade de decisões, alterações de preço, insumos e produção.
- Processos manuais repetitivos que consomem tempo sem agregar valor à operação.
- Crescimento do negócio (novas unidades, franquias, volume) barrado por sistemas que não foram desenhados para escalar.

### Diferencial em Relação aos ERPs Existentes

- **Cadastro único de verdade**: um dado (cliente, ingrediente, fornecedor) é cadastrado uma única vez e reutilizado por todos os módulos — não replicado nem sincronizado por integrações frágeis.
- **Integração nativa entre módulos**: Vendas, Produção, Estoque, Compras e Financeiro nascem conectados pelo mesmo modelo de dados, em vez de serem sistemas isolados unidos por integrações externas.
- **Governança e auditabilidade desde a Fase 000**: diferente da maioria dos ERPs de mercado, o THE CHARCOAL OS nasce com constituição, memória cumulativa e processo de auditoria formal antes de qualquer linha de código.
- **IA como assistente nativo**, não como módulo à parte — atuando sobre o mesmo dado único de todo o sistema (ver Seção 22, Princípio PF-06).
- **Dashboard CEO como visão central do produto** (Princípio PF-07), não um relatório adicional entre outros.
- **Verticalização real**: vocabulário e processos (Ficha Técnica, Produção, Lote, Evento, Pacote) refletem a operação real do negócio, não um genérico "ERP para qualquer empresa".

## 22. Princípios Fundamentais

Estes princípios são de observância obrigatória em toda decisão de arquitetura, modelagem de dados e funcionalidade, em todas as fases futuras. Em caso de conflito aparente entre um princípio e uma conveniência de implementação, o princípio prevalece — ou o conflito é escalado ao proprietário (Seção 17/19), nunca contornado silenciosamente.

- **PF-01 — Cadastro único.** Um dado (cliente, fornecedor, ingrediente, produto etc.) é cadastrado uma única vez no sistema e referenciado, nunca duplicado, por todos os módulos que o utilizam.
- **PF-02 — Compartilhamento automático entre módulos.** Uma informação cadastrada ou gerada em um módulo fica automaticamente disponível para todos os demais módulos que dela dependem, sem reentrada manual.
- **PF-03 — Cálculo único.** Nenhuma regra de cálculo (custo, preço, imposto, saldo, indicador) existe implementada em mais de um lugar; todo cálculo deriva de uma única fonte de verdade e é reutilizado onde for necessário.
- **PF-04 — Histórico obrigatório.** Toda informação relevante (preço, contrato, cadastro, produção, decisão) mantém histórico de alterações, com data, autor e valor anterior — nada é sobrescrito silenciosamente.
- **PF-05 — Automação a serviço da redução de trabalho manual.** Toda automação introduzida deve eliminar ou reduzir mensuravelmente um passo manual existente; automação que apenas desloca trabalho manual não é aceita.
- **PF-06 — IA como assistente inteligente, não como caixa-preta.** A inteligência artificial atua sobre os dados únicos do sistema para apoiar decisões e automatizar tarefas, mas toda sugestão ou ação de IA é auditável, explicável e reversível pelo usuário.
- **PF-07 — Dashboard CEO como visão principal.** O Dashboard CEO é a tela padrão de entrada e a referência executiva do sistema; qualquer indicador relevante de qualquer módulo deve ser refletido nele, direta ou indiretamente.
- **PF-08 — Preparado para crescer por muitos anos.** Toda decisão de modelagem e arquitetura é avaliada quanto à sua capacidade de sustentar o crescimento do negócio ao longo de, no mínimo, uma década (ver Seção 25), sem exigir reescrita estrutural.
- **PF-09 — Simplicidade, escalabilidade e manutenção acima de tudo.** Entre alternativas tecnicamente válidas, prevalece a que for mais simples de entender, mais fácil de manter e mais capaz de escalar — nesta ordem de desempate quando houver conflito entre elas.
- **PF-10 — Toda regra de negócio tem dono e está documentada.** Nenhuma regra de negócio relevante (cálculo, fluxo de aprovação, política comercial) existe apenas implicitamente no código; toda regra é registrada e associada a um responsável pela sua definição.
- **PF-11 — Nenhuma automação ou integração quebra silenciosamente outro módulo.** Mudanças que afetam contratos de integração (Seção 16) entre módulos são tratadas como mudança de escopo, nunca como ajuste local sem aviso.
- **PF-12 — Segurança e privacidade não são negociáveis.** Dados financeiros, cadastrais e de clientes são protegidos por padrão (privacidade por padrão / *privacy by default*), independentemente de pressão de prazo ou simplicidade de implementação.

## 23. Documentos Oficiais do Projeto

Os documentos abaixo são de manutenção obrigatória durante todo o ciclo de vida do projeto. Vários deles formalizam, com nomenclatura de mercado, mecanismos já exigidos nas Seções 7 a 16 desta Constituição — não são artefatos adicionais e sim os nomes oficiais dos artefatos ali definidos, unificados aqui para referência única.

| Documento | Formaliza | Finalidade |
|---|---|---|
| **Project Memory** | Regra de Memória / `PROJECT_MEMORY.md` | Histórico cumulativo, por fase, de decisões, alterações, melhorias, riscos, pendências, funcionalidades aprovadas/rejeitadas, módulos e integrações. Leitura obrigatória antes de qualquer nova fase (Seção 17). |
| **Architecture Decision Records (ADR)** | Seção 7 — Registro de Decisões (Decision Log) | Nome padrão de mercado para o registro individual de cada decisão técnica ou de produto relevante: contexto, alternativas consideradas, decisão tomada e motivo. Cada decisão relevante gera um ADR. |
| **Project Changelog** | Seção 8 — Registro de Alterações | Lista cronológica de toda alteração relevante em escopo, arquitetura, regra de negócio ou estrutura de dados, com o que mudou, por que, impacto e aprovação. |
| **Risk Register** | Seção 13 — Registro de Riscos | Lista viva de riscos identificados, com probabilidade, impacto, mitigação e status; nenhum risco é descartado sem registro. |
| **Improvement Backlog** | Seção 14 — Backlog de Melhorias | Lista viva de melhorias sugeridas e ainda não implementadas, preservadas para reavaliação em fases futuras. |
| **Glossary** | Seção 15 — Glossário Único de Domínio | Dicionário oficial de termos de negócio do sistema, com significado único e padronizado (ver versão inicial na Seção 24). |
| **Integration Map** | Seção 16 — Mapa de Integrações | Registro de todo contrato de integração entre módulos (ou com sistemas externos), com origem, destino, dados trocados e dependências geradas. |
| **Version History** | Seção 12 — Controle de Versões | Histórico de versões semânticas deste Framework, dos módulos e das releases do sistema, com a natureza (MAJOR/MINOR/PATCH) de cada mudança. |

## 24. Glossário Oficial

Versão inicial do Glossário Único de Domínio (Seção 15/23), a ser mantida e expandida em toda fase técnica futura. Cada termo é definido de forma padronizada: Definição, Módulo(s) relacionado(s) e Observações.

| Termo | Definição | Módulo(s) | Observações |
|---|---|---|---|
| **Cliente** | Pessoa física ou jurídica que contrata produtos ou serviços da empresa. | CRM, Vendas, Financeiro | Cadastro único (PF-01); mesmo registro é reutilizado por todos os módulos que se relacionam com o cliente. |
| **Lead** | Cliente em potencial, ainda não convertido, em estágio de prospecção ou negociação. | CRM | Ao ser convertido, transforma-se em Cliente sem gerar novo cadastro (PF-01) — apenas muda de estado. |
| **Evento** | Ocorrência com data, local e escopo definidos para a qual a empresa fornece produtos ou produção. | Vendas, Eventos, Produção | Pode originar um ou mais Orçamentos, um Contrato e uma ou mais ordens de Produção. |
| **Produto** | Item ou serviço final oferecido comercialmente ao cliente. | Vendas, Catálogo | Pode ser composto por uma ou mais Receitas/Fichas Técnicas. |
| **Ingrediente** | Insumo básico utilizado na composição de uma Receita ou Ficha Técnica. | Produção, Estoque, Compras | Possui unidade de medida, custo unitário e controle próprio de Estoque e Lote. |
| **Receita** | Conjunto padronizado de Ingredientes, quantidades e modo de preparo utilizado para produzir um item. | Produção | Termo restrito ao contexto culinário/produtivo. **Nunca** utilizar isoladamente para valores financeiros — ver "Receita Financeira". |
| **Ficha Técnica** | Documento formal que detalha uma Receita com quantidades exatas, custo unitário de cada Ingrediente, rendimento e custo total por unidade produzida. | Produção, Custos | Fonte única do cálculo de custo de produção (PF-03) — nenhum outro lugar do sistema recalcula esse custo de forma independente. |
| **Produção** | Processo de transformar Ingredientes em Produtos a partir de uma Ficha Técnica, para atender a um Evento ou repor Estoque. | Produção | Gera baixa de Estoque de Ingredientes e entrada de Estoque de Produtos/Lotes. |
| **Fornecedor** | Pessoa física ou jurídica que fornece Ingredientes, produtos ou serviços à empresa. | Compras | Cadastro único (PF-01), compartilhado entre Compras, Estoque e Financeiro (contas a pagar). |
| **Compra** | Aquisição de Ingredientes, produtos ou serviços junto a um Fornecedor. | Compras, Financeiro | Gera entrada de Estoque e lançamento de Despesa/contas a pagar. |
| **Estoque** | Quantidade disponível de Ingredientes, Produtos ou materiais, controlada por localização e por Lote. | Estoque | Atualizado automaticamente por Compra, Produção e Venda (PF-02); nunca ajustado manualmente sem registro de histórico (PF-04). |
| **Lote** | Conjunto de unidades de um Ingrediente ou Produto, produzido ou recebido em uma mesma ocasião, com rastreabilidade própria (data, validade, origem). | Estoque, Produção | Garante a rastreabilidade exigida pelo histórico obrigatório (PF-04). |
| **Pacote** | Agrupamento comercial de um ou mais Produtos, vendido como unidade única ao Cliente. | Vendas | Não confundir com "Lote" (rastreabilidade de produção) nem com embalagem física. |
| **Orçamento** | Proposta comercial formal enviada a um Cliente ou Lead, com Produtos/Pacotes, valores e condições. | Vendas | Pode estar vinculado a um Evento; quando aceito, origina um Contrato. |
| **Contrato** | Documento formal que vincula empresa e Cliente às condições comerciais acordadas a partir de um Orçamento aprovado. | Vendas, Financeiro | Dispara a previsão de Receita Financeira e o cronograma correspondente no Fluxo de Caixa. |
| **Documento** | Registro formal (arquivo, contrato, nota fiscal, ficha técnica etc.) anexado ou gerado pelo sistema. | Transversal | Termo genérico; toda entidade que gera Documento mantém histórico de versões (PF-04). |
| **Despesa** | Saída de recursos financeiros da empresa, decorrente de Compra, custo operacional ou obrigação. | Financeiro | Não confundir com "custo de produção" (calculado via Ficha Técnica); Despesa é o lançamento financeiro/de caixa. |
| **Receita Financeira** | Entrada de recursos financeiros na empresa, decorrente de Contrato, venda ou outra fonte. | Financeiro | Termo deliberadamente qualificado com "Financeira" para eliminar ambiguidade com "Receita" (culinária). Nunca usar "Receita" isoladamente em contexto financeiro. |
| **Fluxo de Caixa** | Consolidação temporal das entradas (Receita Financeira) e saídas (Despesa) de recursos financeiros da empresa. | Financeiro, BI | Alimentado automaticamente por Contrato, Compra e Despesa (PF-02); nenhum lançamento manual duplica um lançamento já existente (PF-03). |
| **Dashboard** | Painel visual consolidado de indicadores do negócio. | BI | O **Dashboard CEO** (PF-07) é a instância principal e prioritária deste conceito, agregando dados de todos os módulos em tempo real. |

## 25. Filosofia de Evolução (Horizonte de 10 Anos)

A arquitetura do THE CHARCOAL OS deve ser concebida, desde a primeira fase técnica, para absorver os seguintes vetores de crescimento sem exigir reescrita estrutural:

- **Crescimento da empresa e novos usuários**: modelo de permissões e papéis (roles) desenhado para escalar em número de usuários simultâneos sem redesenho do modelo de autenticação/autorização.
- **Novas unidades e franquias**: o modelo de dados deve prever, desde o início, um conceito de unidade/organização como dimensão transversal aos dados (mesmo que a primeira versão opere com uma única unidade), evitando migração destrutiva quando a segunda unidade surgir.
- **Aplicativo mobile**: o mobile é um cliente adicional consumindo os mesmos serviços e o mesmo modelo de dados do sistema principal — nunca um sistema paralelo com sua própria cópia de dados.
- **Integração bancária**: tratada como uma integração externa formal (Seção 16/Integration Map), isolada por contrato de integração, de forma que a troca de provedor bancário não impacte o núcleo do Financeiro.
- **Inteligência artificial**: atua como camada transversal de apoio (PF-06), consumindo o dado único de todos os módulos — não como um módulo isolado com sua própria base de dados paralela.
- **Automações**: cada nova automação deve reduzir trabalho manual mensurável (PF-05), ser auditável e reversível, e respeitar os contratos de integração já existentes (PF-11).
- **Novos módulos**: toda nova área do sistema (ex.: um futuro módulo de RH ou logística) deve nascer aderente ao Glossário (Seção 24), aos Princípios Fundamentais (Seção 22) e aos padrões de dados já estabelecidos (Seção 15), sendo auditada quanto a isso antes de ser aceita (Seção 17).

O critério de sucesso da arquitetura, ao longo desses dez anos, é que cada um destes vetores possa ser adicionado como uma **extensão** do sistema existente, e não como um **motivo de reconstrução** dele.

## 26. Auditoria de Revisão desta Complementação

Em atendimento ao comando `ALTERAR` do proprietário, foi realizada auditoria completa do documento após a inclusão das Seções 21 a 25, com o seguinte resultado:

- **Duplicidade identificada e resolvida**: as Seções 22–24 introduziam nomenclatura potencialmente redundante com artefatos já definidos nas Seções 7–16 (ex.: "ADR" vs. "Registro de Decisões"). Resolução: a Seção 23 declara explicitamente que os oito Documentos Oficiais **formalizam**, com nome de mercado, os artefatos já exigidos nas Seções 7 a 16 — não são artefatos novos e adicionais. Nenhuma duplicidade real permanece.
- **Ambiguidade de domínio identificada e resolvida**: o termo "Receita" (culinário) e "Receita Financeira" (financeiro) são termos naturalmente ambíguos em português. Resolução: o Glossário (Seção 24) fixa que "Receita", isoladamente, refere-se sempre ao contexto de Produção, e todo valor financeiro de entrada deve obrigatoriamente ser referido como "Receita Financeira" — nunca abreviado. Esta regra deverá ser propagada a toda nomenclatura técnica (banco de dados, telas, APIs) a partir da primeira fase técnica.
- **Consistência verificada entre Manifesto e Visão (Seção 2)**: o Manifesto (Seção 21) especializa e detalha a Visão genérica já registrada na Seção 2, aplicando-a ao domínio de produção e eventos evidenciado pelo vocabulário de negócio; não há conflito, apenas aprofundamento. Nenhuma alteração foi necessária na Seção 2.
- **Consistência verificada entre Princípios Fundamentais (Seção 22) e Padrões de Qualidade (Seção 5)**: são complementares e operam em níveis diferentes — a Seção 22 rege decisões de produto e modelagem de dados (nível de negócio), enquanto a Seção 5 rege critérios de aceite técnico de cada entrega (nível de execução). Nenhuma sobreposição conflitante identificada.
- **Antecipação registrada**: a Seção 15 já previa a criação do Glossário "desde a primeira fase técnica"; a Seção 24 antecipa essa criação ainda na Fase 000 (governança), o que é tratado como avanço, não como violação — toda fase técnica futura deve **manter e expandir** este Glossário, nunca recriá-lo do zero.
- **Risco novo identificado**: a especialização do Manifesto para um domínio de produção/eventos (Seção 21, Seção 24) tacitamente assume um segmento de negócio específico. Caso o proprietário pretenda um escopo diferente ou mais amplo, esta suposição deve ser corrigida antes da Fase 001. Este risco foi registrado no Risk Register (`PROJECT_MEMORY.md`) como **R-000-03**.
- **Melhoria identificada**: nenhuma nova melhoria adicional além das já registradas em M-000-01 e M-000-02 foi identificada nesta revisão.

Nenhuma inconsistência, conflito ou duplicidade permaneceu em aberto após esta auditoria. O conteúdo da versão 1.0.0 foi preservado integralmente; apenas conteúdo novo foi adicionado, conforme instrução do proprietário.

---

## Regra Permanente (Auditoria Contínua)

Antes de iniciar qualquer fase futura, é obrigatório: ler todas as fases anteriores, auditar integralmente o projeto, procurar inconsistências, conflitos, duplicidades e oportunidades de melhoria, e corrigir o que for encontrado dentro do escopo já aprovado. Havendo qualquer conflito que exija decisão do proprietário, o trabalho é interrompido imediatamente até obter orientação. Nenhuma decisão relevante é tomada sem registro do motivo.

## Regra de Memória (Memória Cumulativa)

Ao final de cada fase, mantém-se e atualiza-se um histórico único e cumulativo do projeto, contendo: decisões tomadas, alterações, melhorias, riscos, pendências, funcionalidades aprovadas, funcionalidades rejeitadas, módulos existentes e integrações. Este histórico é insumo obrigatório de leitura para toda fase subsequente.

## Regra de Qualidade (Postura do Comitê)

Em todas as fases, o trabalho é conduzido com a postura de um Arquiteto de Software Sênior: decisões são questionadas quando existem alternativas melhores, vantagens e desvantagens são apresentadas de forma explícita, e nenhuma escolha é feita apenas por ser mais simples de implementar. Toda proposta considera, no mínimo: escalabilidade, manutenção, segurança, desempenho, experiência do usuário e crescimento futuro.

---

*Fim do documento — THE CHARCOAL OS DEVELOPMENT FRAMEWORK v1.1.0*
