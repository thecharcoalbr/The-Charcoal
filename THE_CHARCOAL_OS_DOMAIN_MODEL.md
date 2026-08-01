# THE CHARCOAL OS — DOMAIN MODEL

**Documento:** TCOS-002 — Modelo de Domínio Oficial
**Projeto:** THE CHARCOAL OS
**Fase:** 002 — Domain Model
**Status:** Rascunho para validação do proprietário
**Versão:** 1.0.0
**Documentos-base considerados (todos oficiais/aprovados):** `THE_CHARCOAL_OS_DEVELOPMENT_FRAMEWORK.md` (v1.1.0), `PROJECT_MEMORY.md`, `THE_CHARCOAL_OS_ENTERPRISE_DOMAIN_DISCOVERY.md` (v1.0.0), `THE_CHARCOAL_OS_BUSINESS_DISCOVERY_QUESTIONNAIRE.md` (v1.0.0), `THE_CHARCOAL_OS_DISCOVERY_INTERVIEW_ROADMAP.md` (v1.0.0)

---

## 0. Nota de Auditoria de Abertura

Em conformidade com a Seção 17 do Framework, todos os documentos oficiais listados acima foram lidos integralmente antes de iniciar este documento. Resultado da auditoria:

1. **Achado crítico — encerramento antecipado da Fase 001 frente ao plano registrado.** O `PROJECT_MEMORY.md` registrava, em P-001B-02, que o `THE_CHARCOAL_OS_ENTERPRISE_DOMAIN_DISCOVERY.md` seria "reavaliado e possivelmente reescrito" **depois** de coletadas as respostas às perguntas Q1–Q110 (Fase 001B), e só então resubmetido à aprovação da Fase 001. O proprietário, no entanto, aprovou e encerrou a Fase 001 **antes** de qualquer entrevista ter sido realizada — a hipótese de domínio de negócio (produção culinária em brasa/carvão via Eventos) registrada como risco **R-000-03/P-000-03** permanece formalmente **não confirmada**. Tratamento: este achado não bloqueia a Fase 002, pois decorre de uma instrução explícita, direta e inequívoca do proprietário ("A Fase 001 está oficialmente encerrada"), que é a autoridade máxima de aprovação do projeto (Seção 19 do Framework). O risco é, no entanto, formalmente **herdado por este Domain Model** e mantido em aberto (ver Seção 7 — Auditoria Final), pois toda esta modelagem de domínio reutiliza o vocabulário e as entidades da Fase 001, que podem precisar de correção caso uma futura entrevista revele um negócio diferente do hipotetizado.
2. **Achado — Glossário Oficial do Framework desatualizado frente às entidades da Fase 001.** O Glossário Oficial (Seção 24 do Framework, v1.1.0, já aprovado e congelado na Fase 000) lista 20 termos; a Fase 001 já trabalhava com 29 entidades, e este Domain Model formaliza 30 (ver item 3). O Framework está aprovado e não pode ser alterado sem nova versão formal (Seção 12 do Framework). Tratamento: nenhuma alteração foi feita no Framework; a divergência é registrada como pendência para uma futura v1.2.0 do Framework (já antecipada em M-001-02 do `PROJECT_MEMORY.md`), e este Domain Model é, a partir de agora, a referência mais completa e atual do vocabulário de entidades — sem contradizer o Glossário do Framework, apenas estendendo-o.
3. **Nenhuma entidade duplicada ou regra contraditória** foi encontrada entre os documentos da Fase 001 e os Princípios Fundamentais (PF-01 a PF-12) do Framework. Todas as Regras Globais deste documento (Seção 6) são extensões diretas desses princípios, nunca substitutos ou contradições.
4. **Entidade faltante identificada e adicionada.** Nenhuma das 29 entidades da Fase 001 formalizava o vínculo entre Funcionário e Evento/Produção (quem exatamente trabalha em quê, e quando) — algo já implícito nos capítulos de Mão de Obra e Escalas do Domain Discovery e nas perguntas de Escala do Questionário, mas nunca como entidade própria. Foi adicionada a entidade **Alocação de Funcionário**, claramente destacada como tal na Seção 2.5.
5. Nenhuma decisão técnica (banco de dados, classes, código) foi tomada neste documento, em conformidade com a restrição explícita desta fase.

---

## 1. Papel deste Documento

Este é o Modelo de Domínio Oficial do THE CHARCOAL OS: a referência de negócio para **o que cada entidade significa, como ela se comporta e quem pode fazer o quê com ela**, em linguagem de negócio. Ele não define tabelas, colunas, classes, endpoints ou qualquer tecnologia — isso é reservado a uma fase técnica futura, que deverá **derivar-se** deste documento, nunca contradizê-lo sem registrar formalmente o motivo (Seção 9 do Framework).

Este documento é, a partir de sua aprovação, **documentação oficial e imutável sem nova versão**, no mesmo regime já aplicado aos documentos da Fase 001 (Seção 12 do Framework).

## 2. Convenções Gerais Aplicáveis a Todas as Entidades

Para evitar repetição e garantir consistência (Seção 9 do Framework — Como Evitar Inconsistências), as seguintes convenções valem por padrão para **todas** as entidades listadas na Seção 3, salvo exceção explícita registrada na própria entidade:

- **CG-01 (PF-04 — Histórico obrigatório):** nenhuma entidade transacional é fisicamente excluída do sistema. A operação equivalente é sempre a **inativação, encerramento ou cancelamento**, preservando o registro histórico completo — inclusive de quem fez o quê e quando.
- **CG-02 (PF-01 — Cadastro único):** entidades de cadastro (Cliente, Fornecedor, Ingrediente, Funcionário etc.) são criadas uma única vez e reutilizadas, nunca duplicadas.
- **CG-03 (PF-02 — Compartilhamento automático):** toda informação relevante criada em uma entidade fica automaticamente disponível às demais que dela dependem, sem reentrada manual.
- **CG-04 (PF-03 — Cálculo único):** todo valor calculado (custo, preço, indicador) deriva de uma única fonte de verdade.
- **CG-05 (PF-12 — Segurança por padrão):** dados financeiros sensíveis (custo, margem, remuneração) são visíveis, por padrão, apenas a Financeiro e Direção, salvo indicação em contrário na própria entidade; dados pessoais de Cliente e Funcionário são protegidos por padrão.
- **CG-06 (PF-07 — Dashboard CEO):** a Direção (Dashboard CEO) tem, por padrão, visão consolidada de todas as entidades relevantes ao negócio, mesmo quando o detalhe operacional é restrito a uma área específica.
- **CG-07:** os "papéis" citados nos campos 13–16 de cada entidade (Comercial, Produção, Compras, Estoque/Logística, Operações/Eventos, Financeiro, Marketing, Pessoas/Mão de Obra, Administrativo/Documentos, BI/Direção) referem-se às **áreas de negócio** já definidas na Seção 5 do Domain Discovery — não são perfis técnicos de acesso, decisão que pertence a uma fase técnica futura.

## 3. Entidades do Domínio

30 entidades ao todo: as 29 já identificadas na Fase 001, mais 1 nova (destacada). Organizadas nos mesmos 7 grupos já usados no Domain Discovery, para manter consistência entre os documentos.

### 3.1 Grupo Comercial / CRM

#### Cliente

1. **Definição:** pessoa física ou jurídica que já contratou, ou está no processo ativo de contratar, produtos/serviços da empresa.
2. **Objetivo:** centralizar todo o relacionamento comercial e o histórico de compra.
3. **Responsabilidades:** manter dados de contato atualizados; ser a referência única para todo Orçamento, Contrato e Evento associado.
4. **Ciclo de vida:** nasce da conversão de um Lead ou de contato direto; permanece indefinidamente, mesmo sem compras recentes.
5. **Estados possíveis:** Ativo; Inativo.
6. **Eventos que alteram seu estado:** Cliente criado; Cliente inativado.
7. **Regras de negócio:** um Cliente é sempre cadastrado uma única vez (CG-02); múltiplos Eventos/Contratos do mesmo Cliente sempre referenciam o mesmo cadastro.
8. **Restrições:** não pode existir sem ao menos um meio de contato válido; um Cliente inativado não recebe novo Orçamento sem reativação.
9. **Dependências:** pode depender de um Lead de origem (não obrigatório).
10. **Relacionamentos:** Lead (origem), Orçamento, Contrato, Evento, Documento, Receita Financeira, Pagamento.
11. **Informações obrigatórias:** nome/razão social; ao menos um meio de contato; tipo (pessoa física/jurídica).
12. **Informações opcionais:** data de nascimento/fundação, endereço, observações internas, como conheceu a empresa.
13. **Quem pode criar:** Comercial.
14. **Quem pode alterar:** Comercial (contato); Financeiro (dados de faturamento) — sempre com histórico (CG-01).
15. **Quem pode excluir:** ninguém — apenas inativação (CG-01), por Comercial ou Direção.
16. **Quem pode visualizar:** Comercial, Financeiro, Operações/Eventos; visão consolidada à Direção (CG-06).

#### Lead

1. **Definição:** contato ainda não convertido em Cliente, em prospecção/qualificação comercial.
2. **Objetivo:** dar visibilidade e rastreabilidade ao funil comercial antes do fechamento.
3. **Responsabilidades:** registrar origem do contato e estágio de interesse até a decisão.
4. **Ciclo de vida:** nasce de Campanha, indicação ou contato espontâneo; evolui por estágios; termina em conversão ou perda.
5. **Estados possíveis:** Novo; Em qualificação; Convertido; Perdido.
6. **Eventos que alteram seu estado:** Lead criado; Lead qualificado; Lead convertido em Cliente; Lead marcado como perdido.
7. **Regras de negócio:** a conversão não gera novo cadastro duplicado de Cliente (CG-02) — apenas muda de classificação.
8. **Restrições:** um Lead perdido não é reaberto automaticamente; exige nova decisão comercial explícita.
9. **Dependências:** pode depender de uma Campanha de origem (não obrigatório).
10. **Relacionamentos:** Campanha (origem), Cliente (destino da conversão), Orçamento.
11. **Informações obrigatórias:** nome, ao menos um meio de contato, origem do contato.
12. **Informações opcionais:** interesse inicial declarado, observações de qualificação.
13. **Quem pode criar:** Comercial, Marketing.
14. **Quem pode alterar:** Comercial (estágio de qualificação).
15. **Quem pode excluir:** ninguém — permanece como histórico mesmo perdido (CG-01).
16. **Quem pode visualizar:** Comercial, Marketing; taxa de conversão consolidada visível à Direção.

#### Orçamento

1. **Definição:** proposta comercial formal com Produtos/Pacotes, valores e condições, para um Cliente/Lead.
2. **Objetivo:** formalizar a oferta antes de qualquer compromisso contratual.
3. **Responsabilidades:** refletir com precisão o escopo do Evento e o preço vigente.
4. **Ciclo de vida:** nasce de solicitação de Cliente/Lead; pode ser revisado até ser aceito, recusado ou expirar.
5. **Estados possíveis:** Rascunho; Enviado; Em negociação; Aceito; Recusado; Expirado.
6. **Eventos que alteram seu estado:** Orçamento criado; enviado; revisado; aceito; recusado; expirado.
7. **Regras de negócio:** o valor sempre deriva do custo vigente na Ficha Técnica somado à margem da Precificação (CG-04) — nunca digitado livremente.
8. **Restrições:** não pode ser aceito sem preço final definido; alterações pós-envio geram nova versão (CG-01).
9. **Dependências:** Cliente/Lead, Evento (quando aplicável), Produtos/Pacotes com preço vigente.
10. **Relacionamentos:** Cliente/Lead, Evento, Produto, Pacote, Contrato (quando aceito).
11. **Informações obrigatórias:** Cliente/Lead vinculado, itens e quantidades, valor total, validade da proposta.
12. **Informações opcionais:** observações de escopo, condições especiais, desconto com justificativa.
13. **Quem pode criar:** Comercial.
14. **Quem pode alterar:** Comercial, dentro da alçada de desconto (Seção 6 — Regras Globais Financeiras).
15. **Quem pode excluir:** ninguém — permanece como histórico mesmo recusado/expirado (CG-01).
16. **Quem pode visualizar:** Comercial, o próprio Cliente, Financeiro; consolidado à Direção.

#### Contrato

1. **Definição:** documento formal que vincula empresa e Cliente às condições comerciais de um Orçamento aprovado.
2. **Objetivo:** formalizar juridicamente o compromisso de entrega e pagamento.
3. **Responsabilidades:** ser a referência única de "o que foi vendido" para Produção, Financeiro e Operações.
4. **Ciclo de vida:** nasce da aceitação de um Orçamento; pode receber aditivos; encerra-se com conclusão do Evento e quitação.
5. **Estados possíveis:** Rascunho; Assinado; Em execução; Concluído; Cancelado.
6. **Eventos que alteram seu estado:** Contrato gerado; assinado; aditivado; concluído; cancelado.
7. **Regras de negócio:** só é "Assinado" quando a formalização definida na Regra Global de Fechamento é cumprida; dispara automaticamente a previsão de Receita Financeira (CG-03).
8. **Restrições:** nenhuma alteração de valor/escopo sem aditivo formal (CG-01); cancelamento segue a Regra Global de Eventos.
9. **Dependências:** Orçamento aceito, Cliente.
10. **Relacionamentos:** Orçamento (origem), Cliente, Evento, Documento, Receita Financeira, Fluxo de Caixa.
11. **Informações obrigatórias:** Orçamento de origem, Cliente, valor total, condições de pagamento, data(s) do Evento.
12. **Informações opcionais:** cláusulas específicas, política de cancelamento customizada.
13. **Quem pode criar:** Comercial (geração a partir do Orçamento aceito).
14. **Quem pode alterar:** Comercial/Administrativo, apenas via aditivo formal.
15. **Quem pode excluir:** ninguém — apenas cancelamento formal (CG-01).
16. **Quem pode visualizar:** Comercial, Administrativo, Financeiro, Direção; Cliente visualiza o seu.

#### Campanha

1. **Definição:** iniciativa de marketing com objetivo, período e canal definidos.
2. **Objetivo:** gerar Leads e fortalecer a marca.
3. **Responsabilidades:** registrar investimento e permitir medir retorno em Leads gerados/convertidos.
4. **Ciclo de vida:** nasce do planejamento de Marketing; executa-se em período definido; encerra-se, permanecendo como histórico.
5. **Estados possíveis:** Planejada; Em execução; Encerrada.
6. **Eventos que alteram seu estado:** Campanha criada; iniciada; encerrada.
7. **Regras de negócio:** todo Lead gerado mantém o vínculo de origem mesmo após conversão (CG-01), para cálculo de retorno.
8. **Restrições:** uma Campanha Encerrada não recebe novos Leads atribuídos.
9. **Dependências:** nenhuma.
10. **Relacionamentos:** Lead (gerado por ela), Indicador/Dashboard (retorno).
11. **Informações obrigatórias:** nome, canal, período, objetivo.
12. **Informações opcionais:** orçamento investido, público-alvo, peça/material vinculado.
13. **Quem pode criar:** Marketing.
14. **Quem pode alterar:** Marketing.
15. **Quem pode excluir:** ninguém — permanece como histórico de desempenho (CG-01).
16. **Quem pode visualizar:** Marketing, Comercial; consolidado à Direção.

### 3.2 Grupo Produção / Custos

#### Produto

1. **Definição:** item ou serviço final comercializável, oferecido no Orçamento.
2. **Objetivo:** ser a unidade de venda por trás da qual existe uma Ficha Técnica com custo controlado.
3. **Responsabilidades:** refletir corretamente composição e preço vigente.
4. **Ciclo de vida:** nasce da aprovação comercial de uma Receita/Ficha Técnica testada; evolui em preço/composição; é descontinuado.
5. **Estados possíveis:** Em teste; Ativo; Descontinuado.
6. **Eventos que alteram seu estado:** Produto criado; aprovado para venda; descontinuado.
7. **Regras de negócio:** um Produto Ativo sempre tem Ficha Técnica vigente (CG-04); não é vendido sem essa referência.
8. **Restrições:** Produto Descontinuado não entra em novo Orçamento, mas permanece no histórico de vendas.
9. **Dependências:** ao menos uma Receita/Ficha Técnica aprovada.
10. **Relacionamentos:** Receita, Ficha Técnica, Pacote, Orçamento/Contrato.
11. **Informações obrigatórias:** nome comercial, Ficha Técnica vigente, preço de venda.
12. **Informações opcionais:** descrição, imagem, categoria/linha.
13. **Quem pode criar:** Produção, com aprovação Comercial para venda.
14. **Quem pode alterar:** Produção (composição), Comercial (preço, dentro da Precificação).
15. **Quem pode excluir:** ninguém — apenas descontinuação (CG-01).
16. **Quem pode visualizar:** Comercial, Produção, Financeiro; catálogo ativo visível a toda a operação.

#### Ingrediente

1. **Definição:** insumo básico consumido na composição de Receita/Ficha Técnica.
2. **Objetivo:** compor Receitas com custo e disponibilidade controlados.
3. **Responsabilidades:** manter custo unitário vigente e unidade de medida padronizada.
4. **Ciclo de vida:** nasce no cadastro único (CG-02) na primeira necessidade; tem custo revisado; é descontinuado se sair de uso.
5. **Estados possíveis:** Ativo; Descontinuado.
6. **Eventos que alteram seu estado:** Ingrediente cadastrado; custo atualizado; descontinuado.
7. **Regras de negócio:** atualização de custo dispara recálculo automático de toda Ficha Técnica que o utilize (CG-03/CG-04).
8. **Restrições:** não pode ser descontinuado se usado em Receita Ativa, sem tratar a dependência antes.
9. **Dependências:** nenhuma; é pré-requisito de Receita/Ficha Técnica.
10. **Relacionamentos:** Receita, Ficha Técnica, Estoque, Lote, Compra, Fornecedor.
11. **Informações obrigatórias:** nome, unidade de medida, custo unitário vigente.
12. **Informações opcionais:** Fornecedor preferencial, validade típica, condições de armazenamento.
13. **Quem pode criar:** Compras, Produção.
14. **Quem pode alterar:** Compras (custo); Produção (unidade de medida, uso em Receita).
15. **Quem pode excluir:** ninguém — apenas descontinuação (CG-01).
16. **Quem pode visualizar:** Produção, Compras, Estoque, Financeiro.

#### Receita *(culinária — ver nota de nomenclatura, D-000-07)*

1. **Definição:** conjunto padronizado de Ingredientes, quantidades e modo de preparo.
2. **Objetivo:** garantir repetibilidade de resultado, independente de quem produz.
3. **Responsabilidades:** ser a fonte de verdade do "como fazer", sustentando a Ficha Técnica.
4. **Ciclo de vida:** nasce de criação/teste pela Produção; recebe revisões; é descontinuada com o Produto associado.
5. **Estados possíveis:** Em desenvolvimento; Aprovada; Em revisão; Descontinuada.
6. **Eventos que alteram seu estado:** Receita criada; testada; aprovada; revisada; descontinuada.
7. **Regras de negócio:** só entra em uso comercial (vira Produto) quando Aprovada; toda revisão gera nova versão (CG-01).
8. **Restrições:** não pode ser aprovada sem Ficha Técnica associada.
9. **Dependências:** um ou mais Ingredientes cadastrados.
10. **Relacionamentos:** Ingrediente, Ficha Técnica, Produto, Produção.
11. **Informações obrigatórias:** nome, lista de Ingredientes e quantidades, modo de preparo.
12. **Informações opcionais:** tempo de preparo, variação sazonal, foto do resultado.
13. **Quem pode criar:** Produção.
14. **Quem pode alterar:** Produção, sempre gerando nova versão (CG-01).
15. **Quem pode excluir:** ninguém — apenas descontinuação (CG-01).
16. **Quem pode visualizar:** Produção; Financeiro/Direção visualizam o custo resultante (Ficha Técnica), não necessariamente o modo de preparo.

#### Ficha Técnica

1. **Definição:** detalhamento formal de uma Receita com quantidades exatas, custo unitário por Ingrediente, rendimento e custo total.
2. **Objetivo:** ser a fonte única de cálculo de custo de produção (CG-04).
3. **Responsabilidades:** refletir sempre o custo real vigente dos Ingredientes.
4. **Ciclo de vida:** nasce da formalização de uma Receita aprovada; recalcula-se automaticamente; é substituída por nova versão; descontinua-se com a Receita/Produto.
5. **Estados possíveis:** Rascunho; Vigente; Substituída; Descontinuada.
6. **Eventos que alteram seu estado:** Ficha Técnica criada; recalculada; revisada; descontinuada.
7. **Regras de negócio:** é a **única** fonte de custo de produção do sistema (CG-04); toda Precificação deriva obrigatoriamente do custo Vigente aqui.
8. **Restrições:** não podem existir duas Fichas Técnicas Vigentes simultâneas para a mesma Receita/Produto.
9. **Dependências:** Receita aprovada; Ingredientes com custo vigente.
10. **Relacionamentos:** Receita, Ingrediente, Produto, Produção.
11. **Informações obrigatórias:** Receita de origem, quantidade exata de cada Ingrediente, rendimento, custo total.
12. **Informações opcionais:** custos de apoio (embalagem, gás/carvão), percentual de perda estimado.
13. **Quem pode criar:** Produção, com validação de Engenharia de Custos.
14. **Quem pode alterar:** Produção/Engenharia de Custos — sempre gerando nova versão (CG-01).
15. **Quem pode excluir:** ninguém — apenas descontinuação (CG-01).
16. **Quem pode visualizar:** Produção, Financeiro, Direção; Comercial visualiza o preço resultante, não necessariamente o detalhamento de custo (CG-05), salvo decisão em contrário do proprietário.

#### Produção *(execução)*

1. **Definição:** registro de uma execução concreta de transformação de Ingredientes em Produtos, a partir de uma Ficha Técnica.
2. **Objetivo:** gerar o Produto acabado para Evento/Estoque, permitindo comparar planejado vs. real.
3. **Responsabilidades:** consumir Ingrediente/Estoque corretamente e gerar Lote com rastreabilidade.
4. **Ciclo de vida:** planejada a partir de Evento confirmado ou necessidade de Estoque; executada; concluída gerando Lote; permanece como histórico.
5. **Estados possíveis:** Planejada; Em execução; Concluída; Cancelada.
6. **Eventos que alteram seu estado:** Produção planejada; iniciada; Produto produzido (gera Lote); concluída; cancelada.
7. **Regras de negócio:** toda Produção concluída registra rendimento e consumo reais, comparados obrigatoriamente ao previsto na Ficha Técnica (Seção 6 — Regras de Produção).
8. **Restrições:** não inicia sem Estoque de Ingrediente suficiente reservado, salvo exceção formalmente registrada.
9. **Dependências:** Ficha Técnica vigente; Estoque de Ingrediente suficiente.
10. **Relacionamentos:** Ficha Técnica, Ingrediente, Lote, Produto, Evento, Estoque, Alocação de Funcionário.
11. **Informações obrigatórias:** Ficha Técnica utilizada, quantidade planejada, Evento/finalidade, data de execução.
12. **Informações opcionais:** observações de execução, motivo de desvio de rendimento.
13. **Quem pode criar:** Produção.
14. **Quem pode alterar:** Produção, durante a execução.
15. **Quem pode excluir:** ninguém — apenas cancelamento (CG-01).
16. **Quem pode visualizar:** Produção, Engenharia de Custos, Direção.

### 3.3 Grupo Estoque / Compras / Logística

#### Fornecedor

1. **Definição:** pessoa física ou jurídica que fornece Ingredientes, produtos ou serviços.
2. **Objetivo:** ser a origem formal de toda Compra e insumo do controle de custo.
3. **Responsabilidades:** manter condições comerciais (prazo, preço) atualizadas e confiáveis.
4. **Ciclo de vida:** nasce no cadastro único (CG-02) na primeira Compra/negociação; acumula histórico; é inativado se sair de uso.
5. **Estados possíveis:** Ativo; Inativo.
6. **Eventos que alteram seu estado:** Fornecedor cadastrado; avaliado; inativado.
7. **Regras de negócio:** cadastrado uma única vez (CG-02), mesmo fornecendo múltiplas categorias.
8. **Restrições:** um Fornecedor Inativo não recebe nova Compra sem reativação.
9. **Dependências:** nenhuma.
10. **Relacionamentos:** Compra, Ingrediente, Despesa.
11. **Informações obrigatórias:** nome/razão social, ao menos um meio de contato.
12. **Informações opcionais:** condições comerciais negociadas, avaliação de qualidade, prazo médio de entrega.
13. **Quem pode criar:** Compras.
14. **Quem pode alterar:** Compras.
15. **Quem pode excluir:** ninguém — apenas inativação (CG-01).
16. **Quem pode visualizar:** Compras, Estoque, Financeiro.

#### Compra

1. **Definição:** transação de aquisição de Ingredientes/produtos/serviços junto a um Fornecedor.
2. **Objetivo:** repor Estoque e formar a base de custo real de Ingrediente.
3. **Responsabilidades:** gerar entrada de Estoque/Lote conferida e a Despesa correspondente.
4. **Ciclo de vida:** nasce de necessidade identificada; passa por cotação, pedido, recebimento, conferência; encerra-se com recebimento e quitação.
5. **Estados possíveis:** Solicitada; Em cotação; Pedido enviado; Recebida; Conferida; Cancelada.
6. **Eventos que alteram seu estado:** Compra solicitada; cotada; pedido enviado; recebida; conferida (gera Lote/Estoque); cancelada.
7. **Regras de negócio:** toda Compra Conferida gera automaticamente entrada de Estoque, Lote e Despesa (CG-03) — nunca isoladamente.
8. **Restrições:** não é "Conferida" sem validação de quantidade e (quando aplicável) validade.
9. **Dependências:** Fornecedor; ao menos um Ingrediente/item.
10. **Relacionamentos:** Fornecedor, Ingrediente, Estoque, Lote, Despesa.
11. **Informações obrigatórias:** Fornecedor, itens e quantidades, valor total, data prevista/realizada.
12. **Informações opcionais:** número de nota fiscal/Documento associado, observações de conferência.
13. **Quem pode criar:** Compras.
14. **Quem pode alterar:** Compras (até conferência); Estoque (registro de recebimento).
15. **Quem pode excluir:** ninguém — apenas cancelamento antes do recebimento (CG-01).
16. **Quem pode visualizar:** Compras, Estoque, Financeiro; consolidado à Direção.

#### Estoque *(posição)*

1. **Definição:** quantidade disponível de um Ingrediente/Produto, controlada por Lote.
2. **Objetivo:** garantir disponibilidade para Produção/venda, evitando ruptura ou excesso.
3. **Responsabilidades:** refletir com exatidão o saldo real disponível.
4. **Ciclo de vida:** não é "criada" no sentido tradicional — é uma posição contínua, existente desde a primeira entrada do item; nunca "conclui", apenas chega a zero.
5. **Estados possíveis:** Disponível; Reservado; Esgotado.
6. **Eventos que alteram seu estado:** Estoque atualizado (entrada); reservado; baixado (saída); esgotado.
7. **Regras de negócio:** toda entrada/saída é automática, decorrente de Compra, Produção ou venda (CG-03); ajuste manual só via inventário formal, com histórico (CG-01).
8. **Restrições:** o saldo nunca fica negativo; operação que exigiria saldo negativo é bloqueada ou tratada como exceção formalmente registrada.
9. **Dependências:** existência do Ingrediente/Produto de referência.
10. **Relacionamentos:** Ingrediente, Produto, Lote, Compra, Produção.
11. **Informações obrigatórias:** item de referência, saldo atual, localização (se houver mais de um local).
12. **Informações opcionais:** ponto de reposição mínimo, saldo reservado para Eventos futuros.
13. **Quem pode criar:** não se aplica — nasce automaticamente da primeira Compra/Produção do item.
14. **Quem pode alterar:** automático (Compra, Produção, venda); ajuste manual apenas por Estoque/Logística via inventário formal.
15. **Quem pode excluir:** não se aplica — a posição existe enquanto o item existir (CG-01).
16. **Quem pode visualizar:** Produção, Compras, Estoque/Logística; consolidado à Direção.

#### Lote

1. **Definição:** conjunto de unidades de um Ingrediente/Produto produzido ou recebido em uma mesma ocasião, com rastreabilidade própria.
2. **Objetivo:** garantir rastreabilidade de origem/validade e suporte a controle de qualidade.
3. **Responsabilidades:** manter vínculo entre origem (Compra/Produção) e todo consumo posterior.
4. **Ciclo de vida:** nasce a cada Compra recebida ou Produção; saldo diminui conforme consumido; termina consumido, vencido ou descartado.
5. **Estados possíveis:** Ativo; Em consumo; Vencido; Descartado; Esgotado.
6. **Eventos que alteram seu estado:** Lote criado; consumido parcialmente; vencido; descartado; esgotado.
7. **Regras de negócio:** toda saída de Estoque referencia obrigatoriamente um Lote específico (CG-01 — rastreabilidade); descarte é sempre registrado.
8. **Restrições:** um Lote vencido não pode ser usado em nova Produção.
9. **Dependências:** uma Compra ou Produção de origem.
10. **Relacionamentos:** Ingrediente, Produto, Compra, Produção, Estoque.
11. **Informações obrigatórias:** item de referência, quantidade, data de origem, data de validade (quando aplicável).
12. **Informações opcionais:** Fornecedor de origem, observações de qualidade.
13. **Quem pode criar:** automático (via Compra conferida ou Produção concluída).
14. **Quem pode alterar:** Estoque/Produção (consumo, descarte, vencimento).
15. **Quem pode excluir:** ninguém — mesmo descartado, o registro permanece (CG-01).
16. **Quem pode visualizar:** Produção, Estoque/Logística, Compras.

#### Equipamento

1. **Definição:** bem físico reutilizável usado na Produção/Evento (churrasqueiras, fornos, utensílios, estruturas).
2. **Objetivo:** viabilizar fisicamente a execução da Produção e do Evento.
3. **Responsabilidades:** estar disponível e em condições de uso quando alocado.
4. **Ciclo de vida:** nasce no cadastro na aquisição; passa por uso, alocação, manutenção; é baixado quando descartado/vendido.
5. **Estados possíveis:** Disponível; Alocado; Em manutenção; Baixado.
6. **Eventos que alteram seu estado:** Equipamento cadastrado; alocado a Evento; devolvido; enviado para manutenção; baixado.
7. **Regras de negócio:** não pode ser alocado a dois Eventos com sobreposição de data/horário (Seção 6 — Regras de Eventos).
8. **Restrições:** "Em manutenção" não pode ser alocado a um Evento.
9. **Dependências:** nenhuma.
10. **Relacionamentos:** Evento, Produção, Despesa (manutenção).
11. **Informações obrigatórias:** nome/identificação, tipo, condição atual.
12. **Informações opcionais:** data de aquisição, histórico de manutenção, valor de aquisição.
13. **Quem pode criar:** Operações/Eventos, Compras.
14. **Quem pode alterar:** Operações/Eventos (alocação); Manutenção (condição).
15. **Quem pode excluir:** ninguém — apenas baixa (CG-01).
16. **Quem pode visualizar:** Operações/Eventos, Produção; consolidado à Direção.

#### Veículo

1. **Definição:** bem usado para transporte de Produção, Equipamento e equipe até o local do Evento.
2. **Objetivo:** viabilizar a logística de entrega.
3. **Responsabilidades:** estar disponível e apto para uso quando alocado.
4. **Ciclo de vida:** análogo ao Equipamento.
5. **Estados possíveis:** Disponível; Alocado; Em manutenção; Baixado.
6. **Eventos que alteram seu estado:** Veículo cadastrado; alocado a Evento; devolvido; enviado para manutenção; baixado.
7. **Regras de negócio:** não pode ser alocado a dois Eventos com sobreposição de data/horário/rota (Seção 6 — Regras de Eventos).
8. **Restrições:** "Em manutenção" não pode ser alocado a um Evento.
9. **Dependências:** nenhuma.
10. **Relacionamentos:** Evento, Despesa (manutenção/combustível).
11. **Informações obrigatórias:** identificação (placa/nome), tipo, condição atual.
12. **Informações opcionais:** próprio ou terceirizado, histórico de manutenção, quilometragem.
13. **Quem pode criar:** Operações/Eventos.
14. **Quem pode alterar:** Operações/Eventos (alocação); Manutenção (condição).
15. **Quem pode excluir:** ninguém — apenas baixa (CG-01).
16. **Quem pode visualizar:** Operações/Eventos; consolidado à Direção.

### 3.4 Grupo Financeiro

#### Despesa

1. **Definição:** saída de recursos financeiros da empresa.
2. **Objetivo:** registrar e controlar todo compromisso financeiro do negócio.
3. **Responsabilidades:** refletir com exatidão origem, valor e status de quitação.
4. **Ciclo de vida:** nasce de Compra, folha de Mão de Obra, custo operacional ou obrigação; passa por status até quitação; nunca é excluída.
5. **Estados possíveis:** Prevista; A pagar; Parcialmente paga; Paga; Cancelada.
6. **Eventos que alteram seu estado:** Despesa registrada; aprovada; pagamento parcial registrado; quitada; cancelada.
7. **Regras de negócio:** sempre referencia sua origem; despesas pessoais do proprietário seguem a Regra Global de Integração Pessoa Física/Empresa (Seção 6) — nunca misturadas silenciosamente ao resultado do negócio.
8. **Restrições:** uma Despesa Cancelada não é reaberta — uma nova é criada, se necessário, preservando o histórico da anterior.
9. **Dependências:** uma origem válida (Compra, Fornecedor, Funcionário/Alocação, obrigação).
10. **Relacionamentos:** Fornecedor, Compra, Pagamento, Conta, Fluxo de Caixa, Evento (quando alocável).
11. **Informações obrigatórias:** origem, valor, data de vencimento, status.
12. **Informações opcionais:** Evento associado (para margem por Evento), categoria, observações.
13. **Quem pode criar:** Financeiro, Compras (a partir de uma Compra).
14. **Quem pode alterar:** Financeiro.
15. **Quem pode excluir:** ninguém — apenas cancelamento (CG-01).
16. **Quem pode visualizar:** Financeiro, Direção; Compras visualiza as originadas de suas próprias Compras.

#### Receita Financeira

1. **Definição:** entrada de recursos financeiros na empresa. *(Nunca referida apenas como "Receita" — ver D-000-07.)*
2. **Objetivo:** registrar e controlar o faturamento do negócio.
3. **Responsabilidades:** refletir com exatidão origem, valor e status de recebimento.
4. **Ciclo de vida:** nasce de um Contrato (venda) ou outra fonte; passa por status até quitação; nunca é excluída.
5. **Estados possíveis:** Prevista; A receber; Parcialmente recebida; Recebida; Inadimplente/Cancelada.
6. **Eventos que alteram seu estado:** Receita Financeira prevista; pagamento parcial recebido; quitada; marcada como inadimplente.
7. **Regras de negócio:** deriva obrigatoriamente de um Contrato/venda formal — nunca de lançamento solto sem origem.
8. **Restrições:** não é marcada "Recebida" sem Pagamento correspondente registrado.
9. **Dependências:** um Contrato ou outra origem de venda válida.
10. **Relacionamentos:** Contrato, Cliente, Pagamento, Conta, Fluxo de Caixa.
11. **Informações obrigatórias:** origem (Contrato), valor, data prevista, status.
12. **Informações opcionais:** parcelamento (sinal + parcelas + saldo), observações.
13. **Quem pode criar:** Financeiro (geração automática a partir do Contrato assinado).
14. **Quem pode alterar:** Financeiro.
15. **Quem pode excluir:** ninguém — apenas cancelamento/inadimplência (CG-01).
16. **Quem pode visualizar:** Financeiro, Direção; Comercial visualiza o status dos seus próprios Contratos.

#### Pagamento

1. **Definição:** movimento financeiro concreto de liquidação (total ou parcial) de uma Despesa ou Receita Financeira.
2. **Objetivo:** registrar o momento e a forma real de entrada/saída de caixa.
3. **Responsabilidades:** vincular-se sempre a uma Despesa ou Receita Financeira específica.
4. **Ciclo de vida:** nasce no momento da liquidação; pode ser único ou parcelado; nunca é excluído, apenas estornado.
5. **Estados possíveis:** Efetivado; Estornado.
6. **Eventos que alteram seu estado:** Pagamento registrado; estornado.
7. **Regras de negócio:** atualiza automaticamente o status da Despesa/Receita Financeira e o Fluxo de Caixa (CG-03).
8. **Restrições:** não pode exceder o saldo em aberto da Despesa/Receita Financeira de referência.
9. **Dependências:** Despesa ou Receita Financeira de origem; Conta/Banco por onde transita.
10. **Relacionamentos:** Despesa, Receita Financeira, Conta, Banco.
11. **Informações obrigatórias:** origem, valor, data, Conta utilizada.
12. **Informações opcionais:** forma de pagamento (Pix, cartão, dinheiro, transferência, boleto), observações.
13. **Quem pode criar:** Financeiro.
14. **Quem pode alterar:** não se aplica — correções via estorno e novo registro (CG-01).
15. **Quem pode excluir:** ninguém — apenas estorno (CG-01).
16. **Quem pode visualizar:** Financeiro, Direção.

#### Banco e Conta

1. **Definição:** instituição financeira (Banco) e a conta bancária (Conta) por onde transitam os Pagamentos.
2. **Objetivo:** ser a origem/destino real do dinheiro, base da conciliação bancária.
3. **Responsabilidades:** refletir saldo e histórico real de movimentações.
4. **Ciclo de vida:** nasce no cadastro da abertura da relação bancária; acumula histórico; encerra-se quando a relação termina.
5. **Estados possíveis:** Ativa; Encerrada.
6. **Eventos que alteram seu estado:** Conta cadastrada; encerrada.
7. **Regras de negócio:** toda movimentação financeira referencia uma Conta específica — nunca um valor sem origem/destino.
8. **Restrições:** Conta Encerrada não recebe novos Pagamentos.
9. **Dependências:** um Banco pode ter várias Contas; uma Conta pertence a um único Banco.
10. **Relacionamentos:** Pagamento, Fluxo de Caixa.
11. **Informações obrigatórias:** nome do Banco, identificação da Conta.
12. **Informações opcionais:** finalidade da Conta (operacional, reserva, etc.).
13. **Quem pode criar:** Financeiro.
14. **Quem pode alterar:** Financeiro.
15. **Quem pode excluir:** ninguém — apenas encerramento (CG-01).
16. **Quem pode visualizar:** Financeiro, Direção.

#### Fluxo de Caixa

1. **Definição:** consolidação temporal das entradas (Receita Financeira) e saídas (Despesa) de recursos financeiros.
2. **Objetivo:** dar visibilidade de curto, médio e longo prazo sobre a saúde financeira.
3. **Responsabilidades:** refletir em tempo real o resultado de toda Despesa/Receita Financeira registrada.
4. **Ciclo de vida:** *não é uma entidade transacional discreta* — é uma visão viva e permanente, recalculada continuamente; nunca "nasce" nem "termina" enquanto a empresa operar.
5. **Estados possíveis:** não se aplica estado próprio — está sempre ativo.
6. **Eventos que alteram seu estado:** recalculado a cada Despesa registrada, Pagamento registrado, Receita Financeira prevista, entre outros lançamentos financeiros.
7. **Regras de negócio:** nenhum lançamento manual duplica um valor já existente (CG-04); é sempre **derivado**, nunca fonte primária de dado.
8. **Restrições:** não pode ser editado diretamente — só se altera pela alteração das entidades que o alimentam.
9. **Dependências:** Despesa, Receita Financeira, Pagamento, Conta.
10. **Relacionamentos:** Despesa, Receita Financeira, Pagamento, Conta, Dashboard.
11. **Informações obrigatórias:** não se aplica (visão consolidada, não cadastro).
12. **Informações opcionais:** não se aplica.
13. **Quem pode criar:** não se aplica — existe desde o primeiro lançamento financeiro.
14. **Quem pode alterar:** não se aplica diretamente — apenas indiretamente, pela alteração de suas fontes.
15. **Quem pode excluir:** não se aplica.
16. **Quem pode visualizar:** Financeiro, Direção (Dashboard CEO, CG-06).

### 3.5 Grupo Pessoas

#### Funcionário

1. **Definição:** pessoa que trabalha para a empresa, de forma fixa ou temporária/freelancer para Eventos.
2. **Objetivo:** executar Produção, atendimento de Evento, funções administrativas, etc.
3. **Responsabilidades:** cumprir a função para a qual foi alocado com a qualidade esperada.
4. **Ciclo de vida:** nasce no cadastro na contratação (fixa) ou primeiro engajamento (freelancer); acumula histórico de Alocações; é inativado no desligamento.
5. **Estados possíveis:** Ativo; Afastado; Inativo/Desligado.
6. **Eventos que alteram seu estado:** Funcionário cadastrado; afastado; desligado.
7. **Regras de negócio:** cadastrado uma única vez (CG-02), mesmo atuando em Produção e Eventos.
8. **Restrições:** um Funcionário Inativo não é incluído em nova Alocação.
9. **Dependências:** nenhuma.
10. **Relacionamentos:** Alocação de Funcionário, Produção, Evento, Despesa (custo de mão de obra).
11. **Informações obrigatórias:** nome, tipo de vínculo (fixo/freelancer), função.
12. **Informações opcionais:** dados de contato, forma de pagamento acordada, avaliações de desempenho.
13. **Quem pode criar:** Pessoas/Mão de Obra.
14. **Quem pode alterar:** Pessoas/Mão de Obra.
15. **Quem pode excluir:** ninguém — apenas desligamento (CG-01).
16. **Quem pode visualizar:** Pessoas/Mão de Obra, Produção, Operações/Eventos; dados de remuneração restritos a Financeiro/Direção (CG-05).

#### Alocação de Funcionário — *entidade adicionada nesta fase (ver Auditoria de Abertura, item 4)*

1. **Definição:** vínculo entre um Funcionário e uma Produção ou Evento específico, com papel/função e período definidos.
2. **Objetivo:** formalizar quem efetivamente trabalhará em quê, permitindo planejar e custear a mão de obra corretamente.
3. **Responsabilidades:** registrar a escala planejada e a participação real, para custo e gestão de pessoas.
4. **Ciclo de vida:** nasce do planejamento de escala; é confirmada; é realizada ou cancelada por falta; permanece como histórico.
5. **Estados possíveis:** Planejada; Confirmada; Realizada; Cancelada.
6. **Eventos que alteram seu estado:** Alocação criada; confirmada; realizada; cancelada.
7. **Regras de negócio:** o custo de mão de obra usado na Engenharia de Custos deriva das Alocações Realizadas, nunca de estimativa solta (CG-04).
8. **Restrições:** um mesmo Funcionário não pode ter duas Alocações com sobreposição de horário.
9. **Dependências:** um Funcionário; uma Produção ou Evento.
10. **Relacionamentos:** Funcionário, Evento, Produção, Despesa (custo de mão de obra).
11. **Informações obrigatórias:** Funcionário, Evento/Produção, função, data/horário.
12. **Informações opcionais:** valor acordado (se diferente do padrão), observações.
13. **Quem pode criar:** Pessoas/Mão de Obra, Operações/Eventos.
14. **Quem pode alterar:** Pessoas/Mão de Obra, Operações/Eventos.
15. **Quem pode excluir:** ninguém — apenas cancelamento (CG-01).
16. **Quem pode visualizar:** Pessoas/Mão de Obra, Produção, Operações/Eventos, Financeiro.

### 3.6 Grupo Documentos e Gestão

#### Documento

1. **Definição:** registro formal (arquivo, contrato assinado, nota fiscal, ficha técnica impressa etc.) anexado ou gerado pelo sistema.
2. **Objetivo:** formalizar e arquivar informações e obrigações do negócio.
3. **Responsabilidades:** preservar com integridade o conteúdo vinculado a outra entidade.
4. **Ciclo de vida:** nasce automaticamente (gerado por outra entidade) ou é anexado manualmente; pode ter novas versões; é arquivado, nunca removido.
5. **Estados possíveis:** Rascunho; Vigente; Versão anterior; Arquivado.
6. **Eventos que alteram seu estado:** Documento gerado; assinado/aprovado; revisado; arquivado.
7. **Regras de negócio:** toda nova versão preserva a anterior visível no histórico (CG-01) — nunca substituição silenciosa.
8. **Restrições:** um Documento Vigente vinculado a um Contrato Assinado não é removido, apenas substituído por aditivo formal.
9. **Dependências:** a entidade de origem (Contrato, Compra, Cliente, Fornecedor, Evento).
10. **Relacionamentos:** praticamente todas as entidades transacionais.
11. **Informações obrigatórias:** tipo de documento, entidade de origem, data.
12. **Informações opcionais:** descrição, prazo de validade.
13. **Quem pode criar:** a área responsável pela entidade de origem.
14. **Quem pode alterar:** a mesma área de origem, sempre gerando nova versão.
15. **Quem pode excluir:** ninguém — apenas arquivamento (CG-01).
16. **Quem pode visualizar:** a área responsável pela origem; Administrativo/Documentos tem visão consolidada.

#### Meta

1. **Definição:** objetivo quantitativo definido pela Direção para um período.
2. **Objetivo:** orientar e medir o desempenho do negócio.
3. **Responsabilidades:** ser comparável, ao longo do período, com o Indicador correspondente.
4. **Ciclo de vida:** nasce da definição da Direção para um ciclo; é acompanhada continuamente; encerra-se ao fim do período.
5. **Estados possíveis:** Ativa; Atingida; Não atingida; Encerrada.
6. **Eventos que alteram seu estado:** Meta definida; revisada; ciclo encerrado.
7. **Regras de negócio:** toda Meta está associada a um Indicador mensurável.
8. **Restrições:** uma Meta Encerrada não é reaberta — uma nova é criada para o próximo ciclo.
9. **Dependências:** um Indicador que a meça.
10. **Relacionamentos:** Indicador, Dashboard.
11. **Informações obrigatórias:** descrição, valor-alvo, período, Indicador associado.
12. **Informações opcionais:** responsável pela meta, observações.
13. **Quem pode criar:** Direção.
14. **Quem pode alterar:** Direção.
15. **Quem pode excluir:** ninguém — apenas encerramento (CG-01).
16. **Quem pode visualizar:** Direção; demais áreas visualizam as Metas pertinentes a si.

#### Indicador

1. **Definição:** métrica calculada a partir dos dados do sistema (ex.: margem média por Evento, ticket médio).
2. **Objetivo:** traduzir dados operacionais em informação de gestão.
3. **Responsabilidades:** ter fórmula clara, única e auditável.
4. **Ciclo de vida:** nasce da definição conceitual (fórmula); seu valor muda continuamente; é descontinuado se deixar de fazer sentido.
5. **Estados possíveis:** Ativo; Em revisão de fórmula; Descontinuado.
6. **Eventos que alteram seu estado:** Indicador definido; fórmula revisada; descontinuado.
7. **Regras de negócio:** fórmula única e documentada (CG-04) — nunca recalculada de formas diferentes em lugares diferentes.
8. **Restrições:** revisão de fórmula gera histórico de qual fórmula valia em cada período.
9. **Dependências:** os dados operacionais que alimentam seu cálculo.
10. **Relacionamentos:** Meta, Dashboard, e transitivamente todas as entidades operacionais relevantes.
11. **Informações obrigatórias:** nome, fórmula/definição, fonte de dado.
12. **Informações opcionais:** Meta associada, frequência de atualização.
13. **Quem pode criar:** Direção, BI.
14. **Quem pode alterar:** Direção, BI — com histórico da fórmula anterior (CG-01).
15. **Quem pode excluir:** ninguém — apenas descontinuação (CG-01).
16. **Quem pode visualizar:** Direção; demais áreas visualizam os pertinentes ao seu trabalho.

#### Dashboard

1. **Definição:** painel visual consolidado de Indicadores.
2. **Objetivo:** dar visão executiva e operacional do negócio.
3. **Responsabilidades:** agregar de forma clara os Indicadores relevantes ao seu público.
4. **Ciclo de vida:** nasce da definição do conjunto de Indicadores relevantes; incorpora novos ao longo do tempo; é descontinuado se substituído.
5. **Estados possíveis:** Ativo; Em revisão; Descontinuado.
6. **Eventos que alteram seu estado:** Dashboard criado; atualizado com novo Indicador; descontinuado.
7. **Regras de negócio:** o **Dashboard CEO** é sempre a instância principal (CG-06); todo Indicador relevante de qualquer área deve estar refletido nele, direta ou indiretamente.
8. **Restrições:** nenhum dado exibido pode ter cálculo diferente do Indicador de origem (CG-04).
9. **Dependências:** um ou mais Indicadores já definidos.
10. **Relacionamentos:** Indicador, Meta, e transitivamente todos os módulos.
11. **Informações obrigatórias:** nome, público-alvo, Indicadores incluídos.
12. **Informações opcionais:** organização visual (fora do escopo deste documento).
13. **Quem pode criar:** Direção, BI.
14. **Quem pode alterar:** Direção, BI.
15. **Quem pode excluir:** ninguém — apenas descontinuação, sem perda dos dados subjacentes (CG-01).
16. **Quem pode visualizar:** conforme o público-alvo definido; o Dashboard CEO é visível à Direção.

### 3.7 Grupo Comercial Adicional

#### Pacote

1. **Definição:** agrupamento comercial de um ou mais Produtos, vendido como unidade única ao Cliente.
2. **Objetivo:** simplificar a oferta comercial (ex.: "Pacote Casamento 100 convidados").
3. **Responsabilidades:** refletir corretamente a composição de Produtos e o preço resultante.
4. **Ciclo de vida:** nasce de definição comercial a partir de Produtos existentes; sua composição é revisada; é descontinuado.
5. **Estados possíveis:** Em montagem; Ativo; Descontinuado.
6. **Eventos que alteram seu estado:** Pacote criado; publicado; revisado; descontinuado.
7. **Regras de negócio:** o preço deriva da soma dos custos dos Produtos/Fichas Técnicas mais a margem da Precificação (CG-04) — nunca um valor arbitrário.
8. **Restrições:** não pode incluir um Produto Descontinuado.
9. **Dependências:** um ou mais Produtos ativos.
10. **Relacionamentos:** Produto, Orçamento, Contrato, Evento.
11. **Informações obrigatórias:** nome, Produtos incluídos e quantidades, preço.
12. **Informações opcionais:** descrição comercial, público-alvo sugerido.
13. **Quem pode criar:** Comercial.
14. **Quem pode alterar:** Comercial, sempre com histórico de composição (CG-01).
15. **Quem pode excluir:** ninguém — apenas descontinuação (CG-01).
16. **Quem pode visualizar:** Comercial; catálogo ativo visível a toda a operação.

#### Evento

1. **Definição:** ocorrência com data, local e escopo definidos para a qual a empresa fornece produção/produtos.
2. **Objetivo:** ser o objeto central de venda e de planejamento operacional.
3. **Responsabilidades:** coordenar, em torno de si, Produção, Alocação de Funcionário, Equipamento, Veículo e o resultado financeiro (Contrato/Receita Financeira/Despesa).
4. **Ciclo de vida:** nasce da confirmação de interesse de um Cliente/Lead; passa por planejamento, execução e encerramento; permanece como histórico permanente.
5. **Estados possíveis:** Prospectado; Orçado; Confirmado; Em planejamento; Em execução; Concluído; Cancelado.
6. **Eventos que alteram seu estado:** Evento registrado; Orçamento vinculado; confirmado (Contrato assinado); planejamento concluído; iniciado; concluído; cancelado.
7. **Regras de negócio:** só entra em planejamento operacional depois de Confirmado (Contrato assinado) — nunca antes (Seção 6 — Regras de Eventos).
8. **Restrições:** cancelamento de Evento Confirmado segue a política definida no Contrato/Regra Global — nunca decisão informal sem registro.
9. **Dependências:** um Cliente/Lead; um Orçamento/Contrato para ser confirmado.
10. **Relacionamentos:** Cliente, Orçamento, Contrato, Produção, Equipamento, Veículo, Alocação de Funcionário, Receita Financeira, Despesa.
11. **Informações obrigatórias:** Cliente, data, local, escopo (Produtos/Pacotes), número de convidados.
12. **Informações opcionais:** observações especiais, restrições do local, contato no dia.
13. **Quem pode criar:** Comercial.
14. **Quem pode alterar:** Comercial (escopo comercial), Operações/Eventos (planejamento operacional).
15. **Quem pode excluir:** ninguém — apenas cancelamento (CG-01).
16. **Quem pode visualizar:** Comercial, Produção, Operações/Eventos, Financeiro; consolidado à Direção.

---

## 4. Relacionamentos do Domínio

Em linguagem de negócio, sem qualquer termo técnico:

O **Evento** é o ponto de encontro de quase todas as áreas da empresa. Tudo começa com um **Cliente** — que antes foi um **Lead**, possivelmente originado de uma **Campanha** de marketing — manifestando interesse em um Evento. A partir daí, o time Comercial monta um **Orçamento** com **Produtos** e **Pacotes**, e o preço desse Orçamento nunca é inventado: ele vem diretamente do custo já calculado na **Ficha Técnica** de cada Produto, que por sua vez é a formalização de uma **Receita** feita de **Ingredientes**.

Quando o Cliente aceita o Orçamento, ele se transforma em um **Contrato** — e é esse Contrato que dá à empresa a autorização para mobilizar recursos reais: a **Produção** passa a planejar o consumo de Ingredientes (que saem do **Estoque**, sempre rastreados por **Lote**, e que chegaram até ali através de uma **Compra** feita a um **Fornecedor**); **Equipamentos**, **Veículos** e pessoas (por meio de suas **Alocações de Funcionário**) são reservados especificamente para aquele Evento.

Do lado financeiro, o Contrato dá origem à expectativa de uma **Receita Financeira**, recebida por meio de **Pagamentos** lançados em uma **Conta** de um **Banco**. Do outro lado, cada Compra, cada Alocação de Funcionário e cada uso de Equipamento/Veículo geram **Despesas**. A diferença entre o que entra e o que sai, para um Evento específico, é exatamente a margem que a Engenharia de Custos e a Precificação protegeram desde o Orçamento — e essa diferença aparece consolidada no **Fluxo de Caixa** e, de forma resumida, nos **Indicadores** exibidos em um **Dashboard**, com o Dashboard CEO reunindo o que a Direção mais precisa enxergar.

Depois que o Evento termina, o relacionamento com o Cliente não se encerra: os **Documentos** gerados (Contrato, notas fiscais) são arquivados, mas o histórico do Cliente permanece disponível — é ele que sustenta o pós-venda e alimenta novas Campanhas de Marketing, que geram novos Leads, recomeçando o ciclo comercial.

Paralelamente, a Direção define **Metas** para o negócio, medidas por **Indicadores** — muitos dos quais só existem porque cada uma das entidades acima (Evento, Produção, Compra, Despesa, Receita Financeira) registra fielmente o que de fato aconteceu.

## 5. Regras Globais do Domínio

### Regras Financeiras
- Toda Receita Financeira tem origem em um Contrato ou fonte de venda formalmente registrada — nunca um lançamento solto.
- Toda Despesa tem origem identificável (Compra, Alocação de Funcionário, obrigação).
- Nenhum preço de venda é definido sem lastro no custo vigente da Ficha Técnica (CG-04); o preço de um Produto/Pacote deriva sempre do custo somado à margem definida.
- Todo Pagamento vincula-se a uma Despesa ou Receita Financeira específica e a uma Conta.
- A margem mínima aceitável, definida pela Direção, nunca é rompida sem aprovação registrada dentro da alçada de desconto.
- Toda apuração de resultado pode ser feita por Evento individual, não apenas pelo total do período.

### Regras de Eventos
- Nenhum recurso (Produção, Equipamento, Veículo, Alocação de Funcionário) é reservado para um Evento antes de ele estar Confirmado.
- Um Evento Cancelado segue a política de cancelamento/reembolso definida em Contrato; a ausência dessa política hoje é um risco em aberto (herdado da Fase 001 — ver Seção 7).
- Nenhum Equipamento, Veículo ou Funcionário é alocado a dois Eventos com sobreposição de horário.

### Regras de Estoque
- O saldo de Estoque nunca fica negativo.
- Toda saída de Estoque referencia um Lote específico.
- Ajustes manuais de saldo só ocorrem por inventário formal, com justificativa e histórico.

### Regras de Produção
- Toda Produção deriva de uma Ficha Técnica vigente.
- O consumo real de Ingrediente e o rendimento real são sempre comparados ao previsto; o desvio é visível, nunca escondido em uma média do período.
- Uma Produção não inicia sem Estoque suficiente reservado, salvo exceção formalmente registrada.

### Regras de Engenharia de Custos
- A Ficha Técnica é a única fonte de custo de produção; nenhum outro cálculo de custo é feito de forma independente.
- O custo de mão de obra e de insumos de apoio (carvão, gás, embalagem), quando confirmado que se aplica ao negócio, deve estar incorporado ao custo — nunca tratado apenas como despesa geral do período sem rastreio por Evento/Produto (pendente confirmação — risco R-001-01 herdado).
- Toda atualização de custo de Ingrediente recalcula automaticamente todas as Fichas Técnicas afetadas.

### Regras de Integração entre Vida Pessoal e The Charcoal
- Toda retirada de recursos da empresa para uso pessoal (pró-labore) é tratada como uma Despesa formal, nunca como saída de caixa não registrada.
- Nenhuma despesa pessoal é lançada como Despesa da empresa sem essa distinção estar explícita; se isso ocorrer hoje na prática, deve ser corrigido antes de qualquer lançamento equivalente no sistema (achado do Business Discovery, categoria Financeiro Pessoal, pendente resposta às perguntas Q88–Q90).
- O resultado financeiro da empresa (Fluxo de Caixa, Indicadores, Dashboard) nunca é distorcido por movimentações de natureza pessoal não identificadas como tal.

### Regras de Auditoria
- Toda decisão de negócio relevante refletida no sistema (mudança de preço, de Receita, de política de desconto) é rastreável a uma decisão registrada, em conformidade com o Registro de Decisões/ADR do Framework (Seções 7 e 23).
- Qualquer inconsistência encontrada entre o comportamento esperado (este Domain Model) e a realidade observada é registrada, nunca corrigida silenciosamente sem registro (Regra Permanente do Framework).

### Regras de Histórico
- Nenhuma entidade transacional é fisicamente excluída do sistema (CG-01) — todas seguem a Convenção Geral de inativação/encerramento com preservação de histórico.
- Toda alteração de valor relevante (preço, custo, escopo) preserva a versão anterior, com data e autor.

### Regras de Segurança
- Dados financeiros (custo, margem, remuneração) são visíveis, por padrão, apenas a Financeiro e Direção (CG-05), salvo decisão explícita em contrário do proprietário.
- Dados pessoais de Funcionário e Cliente são protegidos por padrão.
- Toda ação de Inteligência Artificial sobre qualquer entidade deste modelo é auditável e reversível — nunca uma decisão automática silenciosa sobre preço, custo ou dado de cliente.

## 6. Eventos do Domínio

Lista consolidada dos acontecimentos de negócio relevantes, organizados por área (linguagem de negócio, sem qualquer tecnologia):

**Comercial / CRM:** Lead criado · Lead qualificado · Lead convertido em Cliente · Lead marcado como perdido · Cliente criado · Cliente inativado · Cliente fidelizado (identificado quando um Cliente realiza mais de um Evento — critério a confirmar com o proprietário) · Campanha criada · Campanha iniciada · Campanha encerrada · Orçamento criado · Orçamento enviado · Orçamento revisado · Orçamento aceito · Orçamento recusado · Orçamento expirado · Contrato gerado · Contrato assinado · Contrato aditivado · Contrato concluído · Contrato cancelado.

**Eventos (objeto comercial "Evento"):** Evento registrado · Orçamento vinculado ao Evento · Evento confirmado · Planejamento do Evento concluído · Evento iniciado · Evento concluído/finalizado · Evento cancelado.

**Produção / Custos:** Produto criado · Produto aprovado para venda · Produto descontinuado · Ingrediente cadastrado · Custo de Ingrediente atualizado · Ingrediente descontinuado · Receita criada · Receita testada · Receita aprovada · Receita revisada · Receita descontinuada · Ficha Técnica criada · Ficha Técnica recalculada · Ficha Técnica revisada · Ficha Técnica descontinuada · Produção planejada · Produção iniciada · Produto produzido · Produção concluída · Produção cancelada.

**Estoque / Compras / Logística:** Fornecedor cadastrado · Fornecedor avaliado · Fornecedor inativado · Compra solicitada · Compra cotada · Pedido de compra enviado · Compra recebida · Compra realizada (conferida) · Compra cancelada · Estoque atualizado · Estoque reservado · Estoque baixado · Estoque esgotado · Lote criado · Lote consumido parcialmente · Lote vencido · Lote descartado · Lote esgotado · Equipamento cadastrado · Equipamento alocado a Evento · Equipamento devolvido · Equipamento enviado para manutenção · Equipamento baixado · Veículo cadastrado · Veículo alocado a Evento · Veículo devolvido · Veículo enviado para manutenção · Veículo baixado.

**Financeiro:** Despesa registrada · Despesa aprovada · Pagamento parcial de Despesa registrado · Despesa quitada · Despesa cancelada · Receita Financeira prevista · Pagamento parcial de Receita Financeira recebido · Receita Financeira quitada · Receita Financeira marcada como inadimplente · Pagamento recebido · Pagamento realizado (a Fornecedor/Funcionário) · Pagamento estornado · Conta bancária cadastrada · Conta bancária encerrada.

**Pessoas:** Funcionário cadastrado · Funcionário afastado · Funcionário desligado · Alocação de Funcionário criada · Alocação de Funcionário confirmada · Alocação de Funcionário realizada · Alocação de Funcionário cancelada.

**Documentos e Gestão:** Documento gerado · Documento assinado/aprovado · Documento revisado · Documento arquivado · Meta definida · Meta revisada · Ciclo de Meta encerrado · Indicador definido · Fórmula de Indicador revisada · Indicador descontinuado · Dashboard criado · Dashboard atualizado · Dashboard descontinuado.

**Comercial Adicional:** Pacote criado · Pacote publicado · Pacote revisado · Pacote descontinuado.

**Total: 89 eventos de domínio catalogados**, cobrindo o ciclo de vida completo de todas as 30 entidades.

---

## 7. Auditoria Final do Documento

- **Consistência entre entidades e Framework:** todas as Regras Globais (Seção 5) foram conferidas contra os Princípios Fundamentais PF-01 a PF-12 do Framework — nenhuma contradição encontrada; todas são extensões diretas e devidamente referenciadas via CG-01 a CG-07.
- **Entidades repetidas:** nenhuma encontrada entre as 30 listadas.
- **Regras contraditórias:** nenhuma encontrada entre as nove categorias de Regras Globais.
- **Entidade adicionada:** Alocação de Funcionário, destacada e justificada (item 4 da Nota de Auditoria de Abertura).
- **Risco crítico herdado, não resolvido:** R-000-03/P-000-03 — a hipótese de domínio de negócio (produção culinária em brasa/carvão via Eventos) segue sem confirmação do proprietário, mesmo com a Fase 001 já encerrada e este Domain Model já construído sobre ela. Isso é registrado explicitamente como risco ativo herdado por este documento (não apenas pela Fase 001), pois qualquer correção futura ao domínio do negócio (caso a entrevista da Fase 001B algum dia se realize) pode exigir nova versão deste Domain Model.
- **Risco herdado — custo de mão de obra na Ficha Técnica:** R-001-01 permanece sem confirmação; a Regra Global de Engenharia de Custos (Seção 5) já registra essa condicionalidade explicitamente, evitando que o Domain Model assuma uma resposta não confirmada como fato.
- **Oportunidade de melhoria registrada:** a natureza de "visão agregada, não transacional" do Fluxo de Caixa (Seção 3.4) deve ser um ponto de atenção explícito quando uma fase técnica futura decidir como representá-lo — recomenda-se tratá-lo como uma consolidação derivada, não como um registro criado/editado da forma tradicional.
- **Pendência formal para o Framework:** a divergência entre o Glossário Oficial do Framework (20 termos, Seção 24, já congelado) e as 30 entidades deste Domain Model é registrada como pendência para uma futura v1.2.0 do Framework — nenhuma alteração foi feita no documento já aprovado.
- **Conformidade com a restrição da fase:** confirmado que nenhuma tabela, classe, endpoint ou tecnologia foi definida neste documento; toda referência a "quem pode criar/alterar/excluir/visualizar" foi expressa em termos de áreas de negócio (CG-07), não de perfis técnicos de acesso.

Nenhuma inconsistência permaneceu sem tratamento nesta auditoria.

---

*Fim do documento — THE CHARCOAL OS DOMAIN MODEL v1.0.0*
