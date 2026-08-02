# THE CHARCOAL OS — PROJECT CONSTITUTION

**Documento:** Constituição Permanente do Projeto (fora da sequência TCOS)
**Projeto:** THE CHARCOAL OS
**Natureza:** Documento de maior autoridade do projeto — não representa uma nova Fase, não substitui nenhum documento existente
**Baseline governada:** v1.0.0 (TCOS-000 a TCOS-016)
**Status:** Oficial — Registrada e Vigente desde 2026-08-02
**Versão:** 1.0.0

---

## Auditoria de Pré-Criação (executada antes de qualquer linha desta Constituição)

Antes de iniciar este documento, foram lidos integralmente os 20 Documentos Oficiais Congelados (TCOS-000 a TCOS-016) e o `PROJECT_MEMORY.md`, com verificação específica dos seis pontos exigidos:

1. **Nenhuma decisão arquitetural foi perdida** — confirmado pela Auditoria Executiva Global (TCOS-016), que verificou mecanicamente 258 referências cruzadas entre documentos (0 quebradas) e todas as contagens-chave do projeto (30 entidades, 47 regras, 98 funcionalidades, 27 módulos, 15 Serviços, 20 Integrações, entre outras), todas consistentes.
2. **Nenhuma regra de negócio foi omitida** — as 47 Regras de Negócio (TCOS-002A) permanecem rastreadas 47/47 na Matriz do Backend Architecture (TCOS-010, Capítulo 30), reafirmada sem alteração pelo TCOS-016.
3. **Nenhuma política de governança existente será contrariada** — esta Constituição foi desenhada para **incorporar e elevar** as regras de governança já vigentes no Development Framework (TCOS-000, Seções 1-26, e o padrão documental v1.2.0), nunca para substituí-las ou contradizê-las.
4. **Nenhuma referência cruzada será quebrada** — esta Constituição é um documento novo, fora da sequência TCOS, que apenas referencia os documentos existentes por nome; não insere nem altera nenhuma referência dentro de qualquer documento já congelado.
5. **Nenhuma diretriz já aprovada será substituída** — onde esta Constituição formaliza uma política (ex.: versionamento, auditoria, congelamento), ela **consolida** uma prática já seguida rigorosamente desde a Fase 000 (nunca alterar documento aprovado sem nova versão), nunca introduz uma regra nova que a contradiga.
6. **Nenhuma informação será duplicada desnecessariamente** — esta Constituição referencia o conteúdo técnico já existente (Princípios Fundamentais, Convenções Gerais, padrão documental) em vez de reproduzi-lo; onde repete algo (ex.: os 12 Princípios Fundamentais, Capítulo 1), é por necessidade de a Constituição ser autocontida como documento de maior autoridade, nunca para criar uma segunda fonte de verdade divergente.

**Resultado da auditoria: nenhuma inconsistência encontrada.** A criação desta Constituição prossegue, em conformidade com o Prompt Oficial recebido.

---

## 1. Objetivo da Constituição

Esta Constituição estabelece a autoridade máxima, permanente e superior de governança do THE CHARCOAL OS. Seu objetivo é garantir que o patrimônio documental construído ao longo de 17 fases (000 a 016) — a Baseline Oficial v1.0.0 (Capítulo 5) — nunca seja perdido, contradito ou alterado sem o devido processo, independentemente de quantos anos se passem, quantas pessoas ou IAs participem do projeto, ou quantas fases técnicas futuras venham a existir. Esta Constituição não substitui nenhum documento TCOS existente e não representa uma nova Fase — é a camada de governança que protege todas as fases já concluídas e disciplina todas as que ainda virão.

## 2. Escopo

Esta Constituição se aplica a:

- Todos os 20 Documentos Oficiais Congelados (TCOS-000 a TCOS-016) e ao `PROJECT_MEMORY.md`, coletivamente a Baseline Oficial v1.0.0 (Capítulo 5).
- Toda futura Fase técnica ou de negócio do THE CHARCOAL OS, incluindo — mas não se limitando a — escolha de tecnologia, desenvolvimento, banco de dados físico, APIs reais e infraestrutura física.
- Toda IA, desenvolvedor, consultor ou qualquer participante que venha a interagir com a documentação ou a implementação do THE CHARCOAL OS.
- Toda alteração, correção, extensão ou nova versão de qualquer documento oficial, presente ou futuro.

Esta Constituição **não define** nenhuma regra de negócio, entidade, funcionalidade, arquitetura técnica ou tecnologia — essas permanecem exclusivamente nos documentos TCOS já aprovados. Esta Constituição define **como esse conteúdo é protegido e como evolui**, nunca o que esse conteúdo diz.

## 3. Autoridade da Constituição

Esta Constituição é o documento de **maior autoridade** do THE CHARCOAL OS. Em caso de qualquer conflito entre esta Constituição e um documento TCOS existente sobre uma questão de **governança, versionamento, auditoria ou processo de mudança**, prevalece esta Constituição. Em qualquer questão de **conteúdo técnico ou de negócio** (o que uma entidade é, o que uma regra faz, como uma arquitetura se organiza), prevalecem os documentos TCOS já aprovados — esta Constituição não tem autoridade para redefinir conteúdo técnico, apenas para governar como ele é tratado. Esta distinção é o que permite que a Constituição seja "de maior autoridade" sem jamais precisar contradizer ou substituir o trabalho técnico já construído.

## 4. Hierarquia Oficial dos Documentos

1. **THE CHARCOAL OS — PROJECT CONSTITUTION** (este documento) — autoridade máxima sobre governança, versionamento e processo de mudança.
2. **THE_CHARCOAL_OS_DEVELOPMENT_FRAMEWORK.md** (TCOS-000) — a constituição original do método de trabalho (Manifesto, Princípios Fundamentais PF-01 a PF-12, Convenções Gerais CG-01 a CG-07 herdadas pelo Domain Model, padrão documental) — permanece vigente e incorporada, nunca substituída, por esta Constituição.
3. **Os demais 19 Documentos Oficiais Congelados** (TCOS-001 a TCOS-016), cada um com autoridade plena sobre seu próprio domínio técnico (negócio, domínio, regras, funcionalidades, fluxos, UX/UI, arquitetura de sistema, dados, banco, integração, backend, frontend, segurança, IA, infraestrutura, DevOps, auditoria global) — nenhum documento desta camada tem autoridade sobre outro; todos são mutuamente consistentes, conforme confirmado pela Auditoria Executiva Global (TCOS-016).
4. **`PROJECT_MEMORY.md`** — o registro histórico vivo, cumulativo e nunca reescrito, de toda decisão, alteração, risco, pendência e melhoria já registrada. Tem autoridade de **registro histórico**, nunca de decisão técnica nova — nenhuma entrada no `PROJECT_MEMORY.md` pode contradizer um documento oficial; se algum dia contradisser, o documento oficial prevalece, e a entrada do `PROJECT_MEMORY.md` é uma imprecisão de registro a ser corrigida por adição (nunca por reescrita, Capítulo 29).

## 5. Definição da Baseline Oficial v1.0.0

A Baseline Oficial v1.0.0 do THE CHARCOAL OS é o conjunto fechado e íntegro de:

- **20 Documentos Oficiais Congelados:** Development Framework (v1.2.0), Enterprise Domain Discovery (v1.0.0), Business Discovery Questionnaire (v1.0.0), Discovery Interview Roadmap (v1.0.0), Domain Model (v1.0.0), Business Rules Specification (v1.0.0), Functional Specification (v1.2.0), User Journeys and System Flows (v1.0.0), UX/UI Specification (v1.0.0), System Architecture (v1.0.0), Data Architecture (v1.0.0), Database Specification (v1.0.0), Integration and API Contract (v1.0.0), Backend Architecture (v1.0.0), Frontend Architecture (v1.0.0), Security and Privacy Architecture (v1.0.0), AI Architecture (v1.0.0), Infrastructure Architecture (v1.0.0), DevOps and Operational Architecture (v1.0.0), Executive Global Audit (v1.0.0).
- **1 Documento Oficial Vivo:** `PROJECT_MEMORY.md`, no estado em que se encontra ao final da Fase 016.
- **Esta Constituição**, que passa a acompanhar a Baseline como seu documento de governança, sem ser, ela mesma, uma Fase numerada.

A Baseline Oficial v1.0.0 representa **100% da arquitetura conceitual do THE CHARCOAL OS, com 0% de tecnologia escolhida e 0% de implementação iniciada** — exatamente o estado confirmado pela Auditoria Executiva Global (TCOS-016): maturidade 97%, Score Geral 9,6/10. Qualquer trabalho técnico futuro (escolha de tecnologia, código, banco físico, deploy) parte desta Baseline e nunca a substitui — apenas a implementa.

## 6. Política de Preservação do Patrimônio Intelectual

Todo o conteúdo da Baseline Oficial v1.0.0 é patrimônio intelectual permanente do projeto. Regras permanentes:

- Nenhum documento oficial é excluído, mesmo que se torne obsoleto no futuro — o mesmo princípio de exclusão lógica já aplicado a todo dado de negócio (CG-01, Domain Model) se aplica, por analogia direta, à própria documentação do projeto.
- Nenhum conteúdo técnico, decisão, regra ou entidade já aprovada é removida da Baseline — apenas superada por uma nova versão explícita (Capítulo 7), preservando a versão anterior integralmente acessível.
- Todo conhecimento de negócio capturado (as 47 Regras, as 30 entidades, os 89 eventos de domínio, entre outros) é tratado como ativo do proprietário, nunca como artefato descartável de uma fase concluída.

## 7. Política de Versionamento

Reafirma e eleva a regra já seguida rigorosamente em todas as 17 fases deste projeto: **nenhum documento oficial é alterado diretamente após seu congelamento**. Toda evolução de conteúdo já aprovado ocorre exclusivamente por:

- **Nova versão do próprio documento** (ex.: TCOS-003 v1.0.0 → v1.1.0 → v1.2.0), preservando o conteúdo anterior e destacando exatamente o que mudou e por quê — nunca uma edição silenciosa.
- **Documento complementar** (ex.: TCOS-002A como complemento ao TCOS-002), quando o conteúdo novo não invalida o anterior, apenas o estende.
- **Change Request formal** (Capítulo 14), quando a alteração é motivada por uma inconsistência encontrada após o congelamento (ex.: os achados M-016-01/M-016-02 sobre o TCOS-006) — nunca corrigida diretamente, apenas registrada até que um CR formal autorize uma nova versão.

Nenhuma exceção a esta política é permitida, mesmo para correções consideradas "pequenas" ou "óbvias".

## 8. Política de Auditoria

Toda nova Fase, documento ou Change Request desta Baseline em diante deve, sem exceção, seguir a mesma disciplina de auditoria genuína já praticada desde a Fase 000: ler integralmente a documentação relevante antes de agir, registrar achados reais (nunca "nenhuma inconsistência" por padrão), e nunca alterar um documento já congelado sem processo formal. A Auditoria Executiva Global (TCOS-016) é o modelo de referência permanente de como uma auditoria completa do projeto deve ser conduzida — incluindo verificação mecânica de referências e contagens, não apenas releitura.

## 9. Política de Governança

O modelo de governança já estabelecido desde a Fase 000 — o proprietário emite o Prompt Oficial de cada Fase ou Change Request, a IA executa a auditoria e produz o rascunho, e o proprietário responde com um dos cinco comandos formais (`APROVADO`, `CORRIGIR`, `ALTERAR`, `REMOVER`, `CONTINUAR`) — é elevado por esta Constituição a regra permanente e obrigatória para toda interação futura com a Baseline, técnica ou não. Nenhuma decisão de escopo, arquitetura, priorização ou governança é tomada sem esse ciclo completo.

## 10. Política de Rastreabilidade

Toda informação da Baseline Oficial v1.0.0 permanece rastreável, permanentemente, à Fase, ao documento e ao comando do proprietário que a originou ou aprovou — o mesmo princípio de rastreabilidade total já exigido de todo dado de negócio (RN-039/040, PF-04) se aplica à própria governança do projeto. Nenhuma decisão de governança futura (uma nova versão, um Change Request, uma nova Fase) é aceita sem registro completo de origem, motivo e aprovação no `PROJECT_MEMORY.md`.

## 11. Política de Segurança Documental

Aplica, à própria documentação do projeto, os mesmos princípios já definidos para a segurança do sistema (Security and Privacy Architecture, TCOS-012): **negação padrão** — na dúvida sobre se uma alteração é permitida, ela não é permitida até confirmação explícita do proprietário; **menor privilégio** — nenhuma IA ou participante tem, por padrão, autoridade para alterar um documento oficial, apenas para propor uma alteração via Change Request; **auditabilidade total** — toda tentativa de alteração, aprovada ou não, é registrada.

## 12. Política de Backup

A Baseline Oficial v1.0.0 deve estar sempre recuperável a partir do histórico do repositório de controle de versão (`git`) já usado em todo o projeto — cada commit de cada Fase, desde a Fase 000, é, ele mesmo, um ponto de recuperação. Nenhuma política de backup técnico (servidor, nuvem) é definida aqui — isso pertence à Infrastructure Architecture (TCOS-014, Capítulo 15) quando implementada — mas a garantia de que a Baseline documental nunca é perdida já existe hoje, no histórico de commits já acumulado.

## 13. Política de Evolução do Projeto

Reafirma o critério de sucesso "extensão, nunca reconstrução" já estabelecido no Framework (Seção 25) e repetido em toda arquitetura subsequente. Esta Constituição eleva esse critério a regra permanente de todo o projeto, não apenas da arquitetura técnica: toda evolução futura — uma nova Fase, uma nova tecnologia, uma nova regra de negócio — deve se conectar à Baseline Oficial v1.0.0 por adição, nunca exigir a reconstrução do que já foi aprovado.

## 14. Política Oficial de Change Request (CR)

Toda alteração a um documento já congelado da Baseline Oficial v1.0.0 — incluindo a correção dos achados M-016-01/M-016-02 já identificados — deve seguir o processo formal de Change Request:

1. **Abertura do CR:** qualquer participante (incluindo a própria IA, ao identificar uma inconsistência em auditoria) pode propor um CR, descrevendo o documento afetado, o problema encontrado e a mudança proposta.
2. **Auditoria de Impacto:** antes de qualquer aprovação, é obrigatório avaliar o impacto do CR sobre todos os demais documentos oficiais — quais referências cruzadas, contagens ou decisões dependem do trecho a ser alterado.
3. **Decisão do proprietário:** o CR só avança mediante um dos cinco comandos formais (`APROVADO`, `CORRIGIR`, `ALTERAR`, `REMOVER`) — nunca por iniciativa autônoma de qualquer IA ou participante.
4. **Execução como nova versão:** um CR aprovado nunca edita o documento original — sempre gera uma nova versão explícita (Capítulo 7) ou um documento complementar.
5. **Registro permanente:** todo CR, aprovado ou recusado, é registrado no `PROJECT_MEMORY.md` (Capítulo 29), preservando o histórico de por que a mudança foi ou não feita.

## 15. Fluxo Obrigatório para Qualquer Alteração Futura

```
Identificação do problema/necessidade
        │
        ▼
Abertura de Change Request (Capítulo 14)
        │
        ▼
Auditoria de Impacto (Capítulo 8) — nunca pulada
        │
        ▼
Apresentação ao proprietário (relatório técnico + recomendação)
        │
        ▼
Decisão formal do proprietário (APROVADO / CORRIGIR / ALTERAR / REMOVER)
        │
        ▼
Execução exclusivamente por nova versão ou documento complementar (nunca edição direta)
        │
        ▼
Registro permanente no PROJECT_MEMORY.md
```

Nenhuma etapa deste fluxo pode ser omitida, mesmo sob urgência — a mesma disciplina de "nenhum atalho, mesmo sob urgência" já estabelecida para o Pipeline de Entrega (DevOps and Operational Architecture, TCOS-015, Capítulo 17) se aplica, por analogia direta, a qualquer alteração de documentação de governança.

## 16. Responsabilidades da IA

Toda IA que atuar sobre o THE CHARCOAL OS, nesta ou em qualquer sessão futura, deve:

- Executar fielmente o Prompt Oficial recebido do proprietário, sem adicionar escopo não solicitado.
- Ler integralmente a documentação relevante e executar auditoria genuína antes de qualquer produção de conteúdo.
- **Nunca** alterar um documento oficial já congelado por iniciativa própria, mesmo ao encontrar um erro — apenas registrar o achado e recomendar um Change Request.
- **Nunca** tomar uma decisão arquitetural, de negócio ou de priorização em nome do proprietário — apenas apresentar opções e aguardar decisão.
- **Nunca** iniciar uma nova Fase sem autorização explícita e formal do proprietário.
- Registrar toda decisão, alteração, risco, pendência e melhoria no `PROJECT_MEMORY.md`, sem exceção.
- Encerrar toda interação relevante aguardando um dos comandos formais do proprietário, nunca presumindo aprovação tácita.

## 17. Responsabilidades do Proprietário

- Emitir o Prompt Oficial de cada nova Fase ou Change Request, definindo objetivo, escopo obrigatório e restrições.
- Revisar o rascunho e as auditorias apresentadas antes de decidir.
- Emitir uma decisão formal e explícita (`APROVADO`, `CORRIGIR`, `ALTERAR`, `REMOVER` ou `CONTINUAR`) para toda entrega relevante — nenhuma Fase ou Change Request avança sem essa decisão.
- Ser a única autoridade capaz de confirmar dados de negócio ainda pendentes (ex.: R-000-03) — nenhuma IA pode presumir ou inventar esses dados em seu lugar.
- Autorizar explicitamente o início de qualquer implementação técnica, banco físico, API real, backend, frontend, IA em produção ou infraestrutura física.

## 18. Critérios Obrigatórios Antes de Qualquer Commit

1. O conteúdo do commit corresponde exatamente ao que foi apresentado e, quando aplicável, aprovado pelo proprietário.
2. Nenhum documento oficial já congelado foi alterado, salvo as linhas de status explicitamente autorizadas em um encerramento de Fase.
3. Toda referência cruzada nova ou modificada foi verificada contra o cabeçalho real do documento referenciado.
4. O `PROJECT_MEMORY.md` foi atualizado de forma aditiva, sem remoção de histórico.
5. A mensagem de commit descreve fielmente o que mudou e por quê.

## 19. Critérios Obrigatórios Antes de Qualquer Nova Fase

1. Prompt Oficial recebido do proprietário, com objetivo e escopo explícitos.
2. Todos os Documentos Oficiais Congelados relevantes lidos integralmente.
3. Auditoria de abertura executada e registrada, com achados genuínos (nunca "nenhuma inconsistência" por padrão sem verificação real).
4. Nenhuma decisão de negócio ou tecnologia não confirmada é assumida — tratada como pendência explícita.
5. O documento resultante segue o padrão documental completo (Executive Memory, Resumo para o Proprietário, Quality Gate Executivo).

## 20. Critérios Obrigatórios Antes de Qualquer Implementação

1. Autorização explícita e formal do proprietário para iniciar tecnologia/desenvolvimento — nunca implícita a partir da conclusão da arquitetura conceitual.
2. A Baseline Oficial v1.0.0 (Capítulo 5) permanece a referência obrigatória — nenhuma escolha técnica pode introduzir um comportamento incompatível com o que já foi conceitualmente aprovado, sem Change Request formal.
3. Os riscos e pendências ainda ativos (consolidados no TCOS-016 e neste documento, Capítulo 30) são conhecidos e aceitos explicitamente pelo proprietário antes do início — em especial a confirmação do domínio de negócio (R-000-03).
4. Toda decisão de tecnologia (linguagem, framework, banco físico, cloud, CI/CD) é registrada como uma nova Fase ou Change Request, nunca uma decisão silenciosa tomada durante a implementação.

## 21. Regras Permanentes de Preservação

- Nenhum documento oficial é fisicamente excluído do repositório.
- Nenhuma versão anterior de um documento é removida quando uma nova versão é criada — ambas coexistem, com a vigente claramente identificada.
- Nenhum commit que remova conteúdo de um documento oficial é aceito, exceto como parte de um Change Request formalmente aprovado.

## 22. Regras Permanentes de Compatibilidade

- Toda nova versão de um documento oficial deve permanecer compatível com todos os demais documentos que o referenciam — uma mudança que quebraria uma referência cruzada exige, também, a atualização coordenada de quem a referencia, nunca uma correção isolada que gere uma nova inconsistência.
- Nenhuma nova Fase pode introduzir uma entidade, regra, Serviço, módulo ou conceito que contradiga um já existente sem um Change Request explícito sobre o documento original.

## 23. Regras Permanentes de Documentação

Reafirma, como regra permanente e nunca opcional, o padrão documental já estabelecido no Framework v1.2.0 (Seções 27-30) para todo documento oficial presente ou futuro: Executive Memory de abertura, Auditoria de Abertura com achados genuínos, Resumo para o Proprietário em linguagem simples, e Quality Gate Executivo de encerramento com métricas fechadas. Nenhum documento oficial futuro é aceito sem essas quatro seções.

## 24. Regras Permanentes de Aprovação

- Nenhum documento se torna oficial sem o comando explícito `APROVADO` do proprietário.
- Nenhuma Fase avança para a seguinte sem o encerramento formal da anterior.
- Os cinco comandos formais (`APROVADO`, `CORRIGIR`, `ALTERAR`, `REMOVER`, `CONTINUAR`) permanecem o único vocabulário válido de decisão do proprietário sobre esta documentação — nenhuma IA interpreta silêncio ou ambiguidade como aprovação.

## 25. Regras Permanentes de Congelamento de Versões

- Ao ser aprovado, um documento recebe o status "Oficial — Aprovado e Congelado", com data e comando de aprovação registrados.
- Apenas as linhas de status (cabeçalho, Quality Gate, linha final) podem ser alteradas no momento do congelamento — nunca o conteúdo técnico, conforme já praticado em todas as 16 fases anteriores.
- Uma auditoria confirmando que somente as linhas de status mudaram é obrigatória antes de todo commit de congelamento — conforme já praticado desde a Fase 010.

## 26. Processo Oficial para Criação de Novas Versões

1. Identificação da necessidade de nova versão (nova regra de negócio, correção de achado registrado, extensão de escopo).
2. Change Request formal (Capítulo 14) referenciando o documento e a versão atual.
3. Elaboração da nova versão como conteúdo adicional ou revisado, sempre preservando o texto e a numeração já aprovados sempre que possível (aditivo antes de substitutivo).
4. Auditoria de impacto sobre os documentos dependentes.
5. Aprovação formal do proprietário e atualização do número de versão (ex.: v1.0.0 → v1.1.0).
6. Registro completo no `PROJECT_MEMORY.md`.

## 27. Processo Oficial para Correção de Documentos através de Change Request

Idêntico ao fluxo do Capítulo 15, com ênfase em correções pontuais (ex.: os achados M-016-01/M-016-02 já registrados): o CR de correção deve citar exatamente a Fase de origem do achado, o trecho exato a corrigir, e a justificativa — nunca uma reescrita ampla de um documento sob pretexto de uma correção pontual.

## 28. Processo Oficial para Evolução do Framework

O próprio Development Framework (TCOS-000) pode evoluir (como já ocorreu, de v1.0.0 a v1.2.0) — mas apenas pelo mesmo processo de Change Request e nova versão já definido nesta Constituição, nunca por edição direta. Qualquer evolução do Framework deve ser avaliada quanto ao seu impacto sobre esta própria Constituição (Capítulo 3 — Autoridade); em caso de conflito insanável entre uma futura versão do Framework e esta Constituição, esta Constituição prevalece até que uma nova versão dela própria seja formalmente aprovada pelo proprietário.

## 29. Regras para Proteção do PROJECT_MEMORY.md

- O `PROJECT_MEMORY.md` é **append-only** por natureza — toda atualização adiciona uma nova seção ("## FASE NNN" ou, para Change Requests futuros, "## CR-NNN"), nunca remove ou reescreve uma seção já existente.
- Nenhuma correção de uma entrada antiga do `PROJECT_MEMORY.md` é feita por edição do texto original — é feita por uma nova nota explícita referenciando a entrada original (mesmo padrão já usado na Fase 010, ao registrar o encerramento retroativo da Fase 008).
- O `PROJECT_MEMORY.md` nunca é a fonte de uma decisão técnica nova — é sempre o registro de uma decisão já tomada em um documento oficial ou em um Change Request aprovado.

---

## 30. RESUMO PARA O PROPRIETÁRIO

**O que foi criado:** a Constituição do THE CHARCOAL OS — um documento novo, fora da sequência de Fases, que passa a ser a maior autoridade do projeto. Ele não muda nada do que já foi decidido nas 17 fases anteriores; ele protege tudo o que já foi decidido, para sempre.

**Por que isso importa agora:** o projeto acabou de concluir toda a sua arquitetura conceitual (97% de maturidade, 20 documentos oficiais). A partir daqui, o maior risco deixa de ser "esquecer de definir algo" e passa a ser "perder ou contradizer, sem querer, o que já foi definido com tanto cuidado" — especialmente quando a implementação técnica começar e novas pessoas ou IAs passarem a interagir com o projeto. A Constituição existe exatamente para esse momento.

**O que ela estabelece, em termos simples:** nenhum documento já aprovado pode ser editado diretamente — só substituído por uma nova versão, com aprovação sua; toda mudança futura segue um processo formal de "Solicitação de Mudança" (Change Request), com análise de impacto antes de qualquer decisão; nenhuma IA pode decidir arquitetura, alterar documento ou iniciar fase por conta própria; e o `PROJECT_MEMORY.md` nunca perde histórico — só cresce.

**Como ela se conecta ao que já existe:** ela não substitui o Framework (TCOS-000) nem nenhum outro documento — ela os incorpora e os eleva a regra permanente, preenchendo apenas o que faltava: uma autoridade máxima que sobrevive a qualquer fase individual.

**Como ela prepara o que vem a seguir:** a partir de agora, qualquer decisão de tecnologia, qualquer início de desenvolvimento, e qualquer correção aos 2 pequenos achados já identificados no TCOS-006 (Fase 016), passam a seguir exatamente o processo formal aqui definido — nada será feito por atalho, mesmo quando parecer pequeno ou óbvio.

---

## 31. QUALITY GATE EXECUTIVO

**1. Resumo Executivo**
Criada a Constituição Permanente do THE CHARCOAL OS, documento de maior autoridade do projeto, fora da sequência de Fases TCOS. Define Objetivo, Escopo, Autoridade, Hierarquia Oficial dos Documentos, a Baseline Oficial v1.0.0, e 24 políticas/processos permanentes de preservação, versionamento, auditoria, governança, rastreabilidade, segurança documental, backup, evolução, Change Request e proteção do `PROJECT_MEMORY.md`. Nenhum documento oficial existente foi alterado.

**2. Estado Atual do Projeto**
Fases 000 a 016 encerradas e oficiais; Baseline Oficial v1.0.0 definida e preservada. Nenhuma nova Fase foi criada; nenhuma implementação foi iniciada.

**3. Documentos Oficiais Existentes**
21 no total — 20 Documentos Oficiais Congelados + 1 Documento Oficial Vivo (`PROJECT_MEMORY.md`) — mais esta Constituição, que não é contada como um 21º "documento de Fase" (não representa uma Fase), mas passa a existir como o documento de governança permanente acima de todos eles.

**4. Dependências**
A totalidade da Baseline Oficial v1.0.0 (Capítulo 5) — todos os 20 Documentos Oficiais Congelados e o `PROJECT_MEMORY.md`, todos referenciados, nenhum reescrito.

**5. Pendências Abertas**
As mesmas 8 pendências substantivas já consolidadas na Auditoria Executiva Global (TCOS-016): confirmação do domínio de negócio (R-000-03); parâmetros do Módulo 24; M-003A-03/04; decisão de negócio sobre Multiempresa/Multifilial; decisão de governança sobre anonimização de dado pessoal; lacuna de cobertura do TCOS-009 (M-010-03); priorização das Extensões Estruturais de IA (M-013-03); decisão sobre retomar a entrevista de descoberta. Nenhuma nova pendência de negócio foi criada por esta Constituição.

**6. Dúvidas Encontradas**
Nenhuma. A auditoria de pré-criação (ver seção dedicada, acima) não encontrou nenhuma inconsistência que exigisse interromper a criação deste documento.

**7. Riscos Ativos**
Os mesmos 5 códigos já consolidados no TCOS-016 (R-000-03, R-002-01, R-001-01, R-002-02, R-002A-01). Nenhum risco novo.

**8. Novos Riscos Encontrados**
Nenhum.

**9. Inconsistências Encontradas**
Nenhuma nova. Os 2 achados já registrados no TCOS-016 (M-016-01, M-016-02, sobre o TCOS-006) permanecem exatamente como estavam — não corrigidos por esta Constituição, pois corrigi-los exigiria o próprio processo de Change Request que este documento formaliza (Capítulo 14), ainda não executado.

**10. Conflitos entre Documentos**
Nenhum.

**11. Impacto nas Próximas Fases**
Esta Constituição passa a reger todo Change Request, toda nova versão de documento e toda futura Fase técnica do THE CHARCOAL OS — incluindo a eventual correção formal dos achados M-016-01/M-016-02 via CR, e a eventual autorização de tecnologia e desenvolvimento.

**12. Quality Score: 9,7/10**
Justificativa técnica: cobertura completa dos 29 capítulos exigidos, auditoria de pré-criação genuína e documentada (não apenas declarada), e coerência total com a hierarquia e o histórico já estabelecidos nas 17 fases anteriores — sem introduzir nenhuma contradição. Não é 10 porque a Constituição formaliza o processo de Change Request (Capítulo 14) sem ainda ter sido testada em um CR real — sua eficácia prática será confirmada apenas quando o primeiro Change Request (ex.: a correção do TCOS-006) for de fato executado sob este processo.

**13. Atualização do PROJECT_MEMORY.md:** ver commit correspondente.

**14. Estatísticas Finais**
- Capítulos desta Constituição: 29 (Capítulos 1-29) + Resumo (30) + Quality Gate (31).
- Documentos Oficiais Congelados protegidos: 20.
- Documentos Oficiais Vivos protegidos: 1.
- Políticas/processos permanentes formalizados: 24 (Capítulos 6-29).
- Riscos ativos: 5 (0 novos).
- Pendências substantivas: 8 (0 novas).
- Melhorias acumuladas no projeto: 45 (0 novas nesta Constituição).
- Percentual de maturidade do projeto: **97%** (inalterado — esta Constituição protege a Baseline, não amplia o escopo técnico).
- Score Geral do Projeto (herdado do TCOS-016): 9,6/10.

**Status deste documento:** Oficial — Registrado e Vigente desde 2026-08-02. Nenhuma implementação, nenhuma nova Fase e nenhuma tecnologia foram iniciadas. Toda alteração futura, a qualquer documento da Baseline Oficial v1.0.0 ou a esta própria Constituição, segue exclusivamente o processo de Change Request aqui definido (Capítulo 14).

---

*Fim do documento — THE CHARCOAL OS PROJECT CONSTITUTION v1.0.0 (Oficial — Documento de Maior Autoridade do Projeto)*