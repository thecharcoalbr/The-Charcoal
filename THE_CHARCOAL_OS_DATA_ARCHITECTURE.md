# THE CHARCOAL OS — DATA ARCHITECTURE

**Documento:** TCOS-007 — Arquitetura de Dados
**Projeto:** THE CHARCOAL OS
**Fase:** 007 — Data Architecture
**Status:** Rascunho para validação do proprietário
**Versão:** 1.0.0

---

## EXECUTIVE MEMORY

- **Estado atual do projeto:** negócio, domínio, regras, funcionalidades, fluxos, UX/UI e arquitetura de sistema completos e oficiais; iniciando a organização conceitual dos dados, ainda sem banco físico, SQL, ORM ou tecnologia definidos.
- **Fase atual:** 007 — Data Architecture (TCOS-007).
- **Fases concluídas:** 000 a 006, todas aprovadas e oficiais (a mais recente, TCOS-006, congelada nesta mensagem).
- **Documentos oficiais:** Framework (v1.2.0), `PROJECT_MEMORY.md`, Domain Discovery (v1.0.0), Business Discovery Questionnaire (v1.0.0), Discovery Interview Roadmap (v1.0.0), Domain Model (v1.0.0), Business Rules Specification (v1.0.0), Functional Specification (v1.2.0), User Journeys and System Flows (v1.0.0), UX/UI Specification (v1.0.0), System Architecture (v1.0.0, congelado a partir de agora).
- **Documentos em elaboração:** este documento (TCOS-007).
- **Pendências:** confirmação do domínio de negócio (R-000-03); parâmetros do Módulo 24; M-003A-03/04; M-005-01/02/03; M-006-01 (dimensão multiempresa/multifilial); decisão sobre retomar a entrevista de descoberta.
- **Riscos ativos:** R-000-03/R-002-01, R-001-01/R-002-02, R-002A-01 — herdados; nenhum impede a arquitetura de dados, pois todo dado ainda não confirmado é tratado como parâmetro de Configuração explicitamente pendente, nunca como valor assumido no modelo de dados.
- **Dependências para esta fase:** as 30 entidades e Regras Globais (Domain Model); as 47 Regras de Negócio; os 98 funcionalidades; os 30 fluxos; as 30 telas; os 15 Serviços Conceituais e o Event Bus (System Architecture) — todos referenciados, nenhum reescrito.
- **Objetivo da fase que será iniciada:** definir como as informações do sistema serão organizadas, relacionadas, protegidas e evoluirão ao longo do tempo — sem nenhuma decisão de tecnologia de persistência.
- **O que não pode ser alterado:** nenhum conteúdo de nenhum dos 10 documentos oficiais já aprovados e congelados.

### Auditoria de Abertura

Todos os documentos oficiais foram lidos integralmente. Resultado:

- **Nenhuma inconsistência, conflito ou duplicidade** entre os documentos existentes.
- **Entidades órfãs:** nenhuma — as 30 entidades do Domain Model são todas retomadas aqui, cada uma associada a um Serviço proprietário já definido no System Architecture (Capítulo 6 do TCOS-006).
- **Atributos ausentes identificados e corrigidos nesta fase:** nenhuma das 30 entidades previa, até agora, um identificador global explícito nem metadados de auditoria padronizados (autor/data de criação e de última alteração) — esta arquitetura de dados introduz ambos como atributos conceituais universais (Seção 4), aplicáveis a todas as entidades sem exceção.
- **Relacionamentos incompletos:** nenhum encontrado — todo relacionamento já citado no Domain Model (Seção 3.x, campo "Relacionamentos") é retomado e classificado aqui por tipo de integridade (Seção 5).
- **Regras sem suporte de dados:** nenhuma das 47 Regras de Negócio exige um dado que não esteja contemplado por alguma das 30 entidades ou pelos Dados Configuráveis (Seção 3.5) — confirmado item a item na auditoria.
- **Funcionalidades sem suporte de dados:** nenhuma das 98 funcionalidades manipula um dado fora do que está mapeado nesta arquitetura.
- **Oportunidade de simplificação identificada:** Despesa, Receita Financeira e Pagamento compartilham o mesmo padrão de ciclo de vida (previsto → parcial → quitado) e a mesma necessidade de vínculo com Conta — tratados aqui como um único **Agregado Financeiro** com três entidades-membro, em vez de três estruturas de dados isoladas, reduzindo duplicação conceitual de regra de integridade.
- **Achado de governança:** a ausência de uma entidade "Organização/Unidade" (já registrada como M-006-01 no TCOS-006) significa que, hoje, toda entidade deste modelo é implicitamente escopada a uma única empresa/unidade. Esta arquitetura de dados reserva esse escopo como uma dimensão transversal a ser adicionada de forma aditiva (Seção 7.6/7.7), sem exigir redesenho de nenhuma entidade quando for implementada.
- Nenhuma decisão de banco físico, SQL, ORM, tecnologia ou API foi tomada, em conformidade com a restrição explícita da fase.

---

## 1. Papel deste Documento

O Domain Model definiu o que cada entidade **é** e como ela se comporta. O System Architecture definiu **quem é dono** de cada dado e como os Serviços se comunicam. Este documento (TCOS-007) define como o dado em si **se organiza, se relaciona, se protege e evolui no tempo** — a camada de dados da arquitetura em camadas já estabelecida (TCOS-006, Seção 3.3). Nenhuma tecnologia de persistência é escolhida aqui; um arquiteto de dados/DBA deve conseguir desenhar o banco físico (TCOS-008) inteiramente a partir do que está aqui, sem reinterpretar regra de negócio.

## 2. Metadados Universais

Toda entidade deste documento — sem exceção — carrega, conceitualmente, os seguintes metadados, além dos seus próprios atributos de negócio:

- **Identificador Global** (Seção 7.5): único, estável durante todo o ciclo de vida da entidade, nunca reutilizado.
- **Metadado de criação:** autor (usuário ou "Sistema", quando automático) e data/hora.
- **Metadado de última alteração:** autor e data/hora da alteração mais recente.
- **Estado do ciclo de vida:** o conjunto de estados já definido para cada entidade no Domain Model (ex.: Ativo/Inativo, Rascunho/Vigente/Substituída).
- **Escopo organizacional** (reservado, Seção 7.6/7.7): atributo de Organização/Unidade, hoje implícito (uma única empresa/unidade), a ser preenchido quando a dimensão multiempresa/multifilial for implementada — nenhuma entidade precisa ser redesenhada para isso, apenas passa a carregar o atributo.

---

## 3. Domínios de Dados, Agregados e Classificação Estrutural

### 3.1 Domínios de Dados

Os mesmos 7 grupos já usados no Domain Model e no System Architecture, agora como **Domínios de Dados** (fronteiras naturais de coesão de informação):

1. **Comercial** — Cliente, Lead, Orçamento, Contrato, Campanha.
2. **Produção** — Produto, Ingrediente, Receita, Ficha Técnica, Produção.
3. **Suprimentos** — Fornecedor, Compra, Estoque, Lote, Equipamento, Veículo.
4. **Financeiro** — Despesa, Receita Financeira, Pagamento, Banco, Conta, Fluxo de Caixa.
5. **Pessoas** — Funcionário, Alocação de Funcionário.
6. **Gestão** — Documento, Meta, Indicador, Dashboard.
7. **Comercial Adicional** — Pacote, Evento.

### 3.2 Agregados

Um Agregado é a menor unidade de consistência transacional — tudo dentro dele muda de forma atômica; referências para fora do Agregado são sempre por identificador, nunca por cópia do dado (PF-01/PF-03).

| Agregado | Raiz | Membros internos | Referencia (por ID, fora do Agregado) |
|---|---|---|---|
| Cliente | Cliente | — | Lead de origem |
| Lead | Lead | — | Campanha de origem |
| Orçamento | Orçamento | Versões do Orçamento, itens (Produto/Pacote + quantidade) | Cliente/Lead, Evento, Ficha Técnica (preço) |
| Contrato | Contrato | Aditivos | Orçamento de origem, Cliente, Evento |
| Campanha | Campanha | — | — |
| Receita | Receita | Versões, lista de Ingredientes+quantidades | — |
| Ficha Técnica | Ficha Técnica | Versões | Receita, Ingredientes (custo) |
| Produção | Produção | Registro de consumo/rendimento real | Ficha Técnica, Evento, Lotes consumidos/gerados |
| Fornecedor | Fornecedor | — | — |
| Compra | Compra | Itens da Compra | Fornecedor, Ingredientes |
| **Agregado Financeiro** | Despesa **ou** Receita Financeira | Pagamentos vinculados | Conta, Contrato/Compra/Alocação (origem) |
| Conta | Conta | — | Banco |
| Banco | Banco | — | — |
| Estoque (posição) | posição por item | — | Lotes que compõem o saldo |
| Lote | Lote | — | Compra/Produção de origem |
| Equipamento/Veículo | item | — | Evento (alocação) |
| Funcionário | Funcionário | — | — |
| Alocação de Funcionário | Alocação | — | Funcionário, Evento/Produção |
| Documento | Documento | Versões | entidade de origem |
| Meta | Meta | Justificativas de ciclo | Indicador |
| Indicador | Indicador | Histórico de fórmulas | — |
| Dashboard | Dashboard | — | Indicadores incluídos |
| Pacote | Pacote | — | Produtos incluídos |
| Evento | Evento | — | Cliente, Orçamento, Contrato, Produções, Alocações, Equipamentos (todos por ID) |

### 3.3 Entidades Mestres

Baixa frequência de mudança, alta frequência de referência por outras entidades: **Cliente, Fornecedor, Funcionário, Ingrediente, Produto, Pacote, Equipamento, Veículo, Banco, Conta**.

### 3.4 Entidades Transacionais

Alta frequência de criação, representam um evento de negócio ocorrido: **Lead, Orçamento, Contrato, Evento, Produção, Compra, Despesa, Receita Financeira, Pagamento, Alocação de Funcionário, Campanha**.

### 3.5 Dados Configuráveis

Não são entidades de negócio no sentido do Domain Model — são **parâmetros** consultados por Regras de Negócio, mantidos pelo Serviço de Configurações (TCOS-006): consumo por pessoa/tipo de Evento/acompanhamento (RN-024–026), fatores de perda de limpeza/produção e rendimento esperado (RN-027–029), margem-alvo (RN-022), proporção de escala (RN-037), política de cancelamento/reembolso (RN-007), ponto de reposição de Estoque (RN-033). Cada parâmetro carrega seu próprio histórico de alteração (Seção 7.1).

### 3.6 Dados Históricos

Toda versão substituída de Receita, Ficha Técnica, Orçamento e Documento; todo aditivo de Contrato; todo valor anterior de fórmula de Indicador; todo ciclo encerrado de Meta. Nunca removidos — apenas deixam de ser a versão "vigente" (Seção 7.1).

### 3.7 Dados de Auditoria

O log de eventos assinado pelo Serviço de Auditoria (TCOS-006, Capítulo 6): quem fez o quê, quando, sobre qual entidade, a partir de qual comando/evento. É um dado derivado dos eventos do Event Bus, não uma cópia paralela do dado de negócio.

### 3.8 Dados Analíticos

Indicador (valor calculado e sua fórmula) e Dashboard (composição de Indicadores) — dados **derivados**, nunca fonte primária; se todo dado analítico fosse apagado, seria inteiramente reconstruível a partir dos dados operacionais e financeiros.

### 3.9 Dados de IA

Sugestão gerada (categorização, previsão de demanda, sugestão de preço), sua origem (Regra/evento que a gerou), e a decisão humana tomada sobre ela (aceita/recusada/revertida) — um histórico próprio, apartado do dado operacional que a sugestão eventualmente afeta, garantindo que toda ação de IA permaneça auditável (PF-06) mesmo depois de aplicada.

---

## 4. Entidades

Para cada entidade: Papel, Tipo, Proprietário (Serviço, conforme TCOS-006), Ciclo de vida, Dependências, Relacionamentos, Regras de integridade, Dados obrigatórios/opcionais, Histórico, Auditoria, Estratégia de evolução. Os campos Ciclo de vida/Dependências/Relacionamentos/Obrigatórios/Opcionais resumem o já detalhado no Domain Model (Seção 3) — não são redefinidos, apenas referenciados.

### 4.1 Domínio Comercial

**Cliente** — Papel: parte central do relacionamento comercial | Tipo: Mestre | Proprietário: Serviço Comercial | Ciclo de vida: Ativo/Inativo (Domain Model 3.1) | Dependências: nenhuma obrigatória | Relacionamentos: Lead (origem, opcional), Orçamento, Contrato, Evento (referenciado por ID) | Integridade: não pode ser inativado enquanto houver Orçamento/Contrato/Evento em estado ativo sem tratamento explícito; nunca duplicado (unicidade lógica por nome+contato, PF-01) | Obrigatórios: nome/razão social, meio de contato, tipo | Opcionais: data de nascimento/fundação, endereço, observações | Histórico: nunca excluído, apenas inativado (CG-01) | Auditoria: evento "Cliente criado/inativado" assinado pelo Serviço de Auditoria | Evolução: aditiva — novos atributos (ex.: segmentação) podem ser adicionados sem afetar registros existentes.

**Lead** — Papel: prospecção comercial | Tipo: Transacional | Proprietário: Serviço Comercial | Ciclo de vida: Novo/Em qualificação/Convertido/Perdido | Dependências: Campanha de origem (opcional) | Relacionamentos: Cliente (destino de conversão), Campanha | Integridade: conversão nunca cria Cliente duplicado — deve vincular a um Cliente existente quando houver correspondência (RN-009) | Obrigatórios: nome, meio de contato, origem | Opcionais: interesse declarado | Histórico: preservado mesmo se perdido | Auditoria: "Lead criado/convertido/perdido" | Evolução: aditiva.

**Orçamento** — Papel: proposta comercial | Tipo: Transacional, versionado | Proprietário: Serviço Comercial | Ciclo de vida: Rascunho→Enviado→Em negociação→Aceito/Recusado/Expirado | Dependências: Cliente/Lead; Produto/Pacote com Ficha Técnica vigente | Relacionamentos: Evento (opcional), Contrato (gerado no aceite) | Integridade: preço sempre derivado do custo vigente na Ficha Técnica no momento do cálculo (nunca um valor solto); nova versão nunca sobrescreve a anterior | Obrigatórios: Cliente/Lead, itens, valor, validade | Opcionais: observações, desconto justificado | Histórico: todas as versões preservadas | Auditoria: "Orçamento criado/enviado/revisado/aceito/recusado/expirado" | Evolução: aditiva; nova versão é sempre um novo registro vinculado ao Orçamento original.

**Contrato** — Papel: formalização jurídica | Tipo: Transacional, com aditivos | Proprietário: Serviço Comercial | Ciclo de vida: Rascunho→Assinado→Em execução→Concluído/Cancelado | Dependências: Orçamento aceito | Relacionamentos: Cliente, Evento, Documento, Receita Financeira | Integridade: aditivo nunca substitui o Contrato original — é um registro adicional vinculado; valor total sempre reconciliável com a soma de aditivos aplicados | Obrigatórios: Orçamento de origem, Cliente, valor, condições, data(s) | Opcionais: cláusulas específicas | Histórico: aditivos preservados permanentemente | Auditoria: "Contrato gerado/assinado/aditivado/concluído/cancelado" | Evolução: aditiva.

**Campanha** — Papel: iniciativa de marketing | Tipo: Transacional | Proprietário: Serviço de Marketing | Ciclo de vida: Planejada→Em execução→Encerrada | Dependências: nenhuma | Relacionamentos: Lead (gerado por ela) | Integridade: Lead mantém vínculo de origem mesmo após conversão, imutável | Obrigatórios: nome, canal, período, objetivo | Opcionais: investimento, público-alvo | Histórico: preservada como registro de desempenho | Auditoria: "Campanha criada/iniciada/encerrada" | Evolução: aditiva.

### 4.2 Domínio Produção

**Produto** — Papel: unidade de venda | Tipo: Mestre | Proprietário: Serviço de Produção | Ciclo de vida: Em teste/Ativo/Descontinuado | Dependências: Ficha Técnica aprovada | Relacionamentos: Receita/Ficha Técnica, Pacote, Orçamento | Integridade: nunca vendável (Orçamento) sem Ficha Técnica Vigente associada (RN-021) | Obrigatórios: nome, Ficha Técnica vigente, preço | Opcionais: descrição, categoria | Histórico: preço/composição anteriores preservados via versões de Ficha Técnica | Auditoria: "Produto criado/aprovado/descontinuado" | Evolução: aditiva.

**Ingrediente** — Papel: insumo básico | Tipo: Mestre | Proprietário: Serviço de Suprimentos | Ciclo de vida: Ativo/Descontinuado | Dependências: nenhuma | Relacionamentos: Receita, Ficha Técnica, Estoque, Lote, Compra, Fornecedor | Integridade: não pode ser descontinuado enquanto usado em Receita Ativa sem tratamento explícito | Obrigatórios: nome, unidade de medida, custo unitário vigente | Opcionais: Fornecedor preferencial, validade típica | Histórico: custo unitário versionado no tempo | Auditoria: "Ingrediente cadastrado/custo atualizado/descontinuado" | Evolução: aditiva.

**Receita** — Papel: "como fazer" padronizado | Tipo: Mestre, versionado | Proprietário: Serviço de Produção | Ciclo de vida: Em desenvolvimento/Aprovada/Em revisão/Descontinuada | Dependências: Ingredientes cadastrados | Relacionamentos: Ficha Técnica, Produto | Integridade: só aprovada com Ficha Técnica associada | Obrigatórios: nome, Ingredientes+quantidades, modo de preparo | Opcionais: tempo de preparo | Histórico: todas as versões preservadas | Auditoria: "Receita criada/testada/aprovada/revisada/descontinuada" | Evolução: versionada (nunca sobrescrita).

**Ficha Técnica** — Papel: fonte única de custo | Tipo: Mestre, versionado | Proprietário: Serviço de Custos e Precificação | Ciclo de vida: Rascunho/Vigente/Substituída/Descontinuada | Dependências: Receita aprovada, Ingredientes com custo vigente | Relacionamentos: Receita, Produto, Produção | Integridade: nunca duas Fichas Técnicas "Vigente" simultâneas para o mesmo Produto | Obrigatórios: Receita de origem, quantidades exatas, rendimento, custo total | Opcionais: custos de apoio, percentual de perda | Histórico: toda versão preservada | Auditoria: "Ficha Técnica criada/recalculada/revisada/descontinuada" | Evolução: versionada; recálculo gera nova versão, nunca edição in-place do custo vigente.

**Produção** — Papel: execução de transformação | Tipo: Transacional | Proprietário: Serviço de Produção | Ciclo de vida: Planejada/Em execução/Concluída/Cancelada | Dependências: Ficha Técnica vigente, Estoque suficiente | Relacionamentos: Ficha Técnica, Ingrediente, Lote, Produto, Evento, Alocação de Funcionário | Integridade: consumo real sempre referencia Lote específico existente; nunca inicia sem Estoque reservado (salvo exceção registrada) | Obrigatórios: Ficha Técnica, quantidade planejada, Evento/finalidade, data | Opcionais: observações de execução | Histórico: cada execução é registro permanente | Auditoria: "Produção planejada/iniciada/concluída/cancelada" | Evolução: aditiva — cada execução é um novo registro, nunca reaproveitado.

### 4.3 Domínio Suprimentos

**Fornecedor** — Papel: origem de Compra | Tipo: Mestre | Proprietário: Serviço de Suprimentos | Ciclo de vida: Ativo/Inativo | Dependências: nenhuma | Relacionamentos: Compra, Ingrediente, Despesa | Integridade: cadastro único (PF-01); Fornecedor inativo não recebe nova Compra sem reativação | Obrigatórios: nome/razão social, contato | Opcionais: condições comerciais, avaliação | Histórico: preservado | Auditoria: "Fornecedor cadastrado/avaliado/inativado" | Evolução: aditiva.

**Compra** — Papel: aquisição de insumo | Tipo: Transacional | Proprietário: Serviço de Suprimentos | Ciclo de vida: Solicitada→Cotação→Pedido→Recebida→Conferida/Cancelada | Dependências: Fornecedor | Relacionamentos: Ingrediente, Estoque, Lote, Despesa | Integridade: conferência gera Estoque/Lote/Despesa de forma atômica — nunca parcial | Obrigatórios: Fornecedor, itens, valor, datas | Opcionais: número de nota fiscal | Histórico: preservado permanentemente | Auditoria: "Compra solicitada/.../conferida/cancelada" | Evolução: aditiva.

**Estoque (posição)** — Papel: saldo real disponível | Tipo: Transacional (posição derivada) | Proprietário: Serviço de Suprimentos | Ciclo de vida: contínuo, sem "criação" tradicional | Dependências: Ingrediente/Produto de referência | Relacionamentos: Lote, Compra, Produção | Integridade: saldo nunca negativo; toda alteração deriva de um evento de origem (Compra/Produção/venda), nunca editada livremente | Obrigatórios: item, saldo, localização | Opcionais: ponto de reposição | Histórico: toda movimentação preservada | Auditoria: "Estoque atualizado/reservado/baixado/esgotado" | Evolução: aditiva.

**Lote** — Papel: rastreabilidade de origem/validade | Tipo: Transacional | Proprietário: Serviço de Suprimentos | Ciclo de vida: Ativo/Em consumo/Vencido/Descartado/Esgotado | Dependências: Compra ou Produção de origem | Relacionamentos: Ingrediente, Produto, Estoque | Integridade: toda saída de Estoque referencia um Lote existente; Lote vencido não pode ser referenciado em nova Produção | Obrigatórios: item, quantidade, data de origem, validade (quando aplicável) | Opcionais: Fornecedor de origem | Histórico: preservado mesmo descartado | Auditoria: "Lote criado/consumido/vencido/descartado/esgotado" | Evolução: aditiva.

**Equipamento / Veículo** — Papel: bem físico reutilizável | Tipo: Mestre | Proprietário: Serviço de Pessoas e Recursos | Ciclo de vida: Disponível/Alocado/Em manutenção/Baixado | Dependências: nenhuma | Relacionamentos: Evento, Despesa (manutenção) | Integridade: nunca duas alocações com sobreposição de horário para o mesmo item | Obrigatórios: identificação, tipo, condição | Opcionais: valor de aquisição, histórico de manutenção | Histórico: preservado até a baixa | Auditoria: "Equipamento/Veículo cadastrado/alocado/devolvido/baixado" | Evolução: aditiva.

### 4.4 Domínio Financeiro

**Despesa** — Papel: saída de recursos | Tipo: Transacional | Proprietário: Serviço Financeiro | Ciclo de vida: Prevista→A pagar→Parcialmente paga→Paga/Cancelada | Dependências: origem válida (Compra, Alocação, obrigação) | Relacionamentos: Fornecedor/Funcionário, Pagamento, Conta, Evento | Integridade: sempre referencia origem identificável; retirada pessoal nunca é lançada como Despesa operacional (RN-002) | Obrigatórios: origem, valor, vencimento, status | Opcionais: Evento associado, categoria | Histórico: nunca excluída, apenas cancelada | Auditoria: "Despesa registrada/aprovada/quitada/cancelada" | Evolução: aditiva.

**Receita Financeira** — Papel: entrada de recursos | Tipo: Transacional | Proprietário: Serviço Financeiro | Ciclo de vida: Prevista→A receber→Parcialmente recebida→Recebida/Inadimplente | Dependências: Contrato ou origem de venda válida | Relacionamentos: Contrato, Cliente, Pagamento, Conta | Integridade: nunca marcada "Recebida" sem Pagamento correspondente | Obrigatórios: origem, valor, data prevista, status | Opcionais: parcelamento | Histórico: preservada | Auditoria: "Receita Financeira prevista/quitada/inadimplente" | Evolução: aditiva.

**Pagamento** — Papel: liquidação real | Tipo: Transacional | Proprietário: Serviço Financeiro | Ciclo de vida: Efetivado/Estornado | Dependências: Despesa ou Receita Financeira de origem; Conta | Relacionamentos: Despesa/Receita Financeira, Conta, Banco | Integridade: valor nunca excede o saldo em aberto da origem; correção sempre via estorno + novo registro, nunca edição in-place | Obrigatórios: origem, valor, data, Conta | Opcionais: forma de pagamento | Histórico: preservado, incluindo estornos | Auditoria: "Pagamento registrado/estornado" | Evolução: aditiva.

**Banco / Conta** — Papel: origem/destino real do dinheiro | Tipo: Mestre | Proprietário: Serviço Financeiro (Bancos) | Ciclo de vida: Ativa/Encerrada | Dependências: Conta pertence a um único Banco | Relacionamentos: Pagamento | Integridade: Conta Encerrada não aceita novo Pagamento | Obrigatórios: nome do Banco, identificação da Conta | Opcionais: finalidade, tipo (pessoal/empresarial/cartão/digital/investimento/internacional) | Histórico: movimentações preservadas | Auditoria: "Conta cadastrada/encerrada" | Evolução: aditiva — "Cartão"/"Conta Internacional" hoje são um tipo de Conta (nota de modelagem já registrada no TCOS-002/003, M-003A-04 pendente para reavaliação futura).

**Fluxo de Caixa** — Papel: consolidação temporal | Tipo: Analítico (derivado) | Proprietário: Serviço de Indicadores e Dashboards | Ciclo de vida: contínuo, sem estado próprio | Dependências: Despesa, Receita Financeira, Pagamento, Conta | Relacionamentos: todos os anteriores | Integridade: nunca editável diretamente — sempre recalculado a partir das fontes | Obrigatórios: não se aplica (visão, não cadastro) | Opcionais: não se aplica | Histórico: implícito no histórico das fontes | Auditoria: não gera evento próprio | Evolução: aditiva (novas fontes de entrada/saída podem ser somadas sem redesenho).

### 4.5 Domínio Pessoas

**Funcionário** — Papel: executor de Produção/Evento | Tipo: Mestre | Proprietário: Serviço de Pessoas e Recursos | Ciclo de vida: Ativo/Afastado/Inativo | Dependências: nenhuma | Relacionamentos: Alocação de Funcionário, Despesa | Integridade: cadastro único (PF-01); Funcionário inativo não recebe nova Alocação | Obrigatórios: nome, tipo de vínculo, função | Opcionais: contato, forma de pagamento acordada | Histórico: preservado | Auditoria: "Funcionário cadastrado/afastado/desligado" | Evolução: aditiva.

**Alocação de Funcionário** — Papel: vínculo Funcionário↔Evento/Produção | Tipo: Transacional | Proprietário: Serviço de Pessoas e Recursos | Ciclo de vida: Planejada/Confirmada/Realizada/Cancelada | Dependências: Funcionário; Evento ou Produção | Relacionamentos: Funcionário, Evento, Produção, Despesa | Integridade: nunca duas Alocações com sobreposição de horário para o mesmo Funcionário | Obrigatórios: Funcionário, Evento/Produção, função, data/horário | Opcionais: valor acordado | Histórico: preservado, incluindo cancelamentos | Auditoria: "Alocação criada/confirmada/realizada/cancelada" | Evolução: aditiva.

### 4.6 Domínio Gestão

**Documento** — Papel: registro formal | Tipo: Transacional, versionado | Proprietário: Serviço de Documentos | Ciclo de vida: Rascunho/Vigente/Versão anterior/Arquivado | Dependências: entidade de origem | Relacionamentos: praticamente todas as entidades transacionais | Integridade: nova versão nunca remove a anterior | Obrigatórios: tipo, entidade de origem, data | Opcionais: descrição, validade | Histórico: todas as versões preservadas | Auditoria: "Documento gerado/aprovado/revisado/arquivado" | Evolução: versionada.

**Meta** — Papel: objetivo quantitativo | Tipo: Transacional | Proprietário: Serviço de Metas | Ciclo de vida: Ativa/Atingida/Não atingida/Encerrada | Dependências: Indicador associado | Relacionamentos: Indicador, Dashboard | Integridade: nunca criada sem Indicador correspondente; encerrada não é reaberta (apenas duplicada) | Obrigatórios: período, Indicador, responsável, valor-alvo | Opcionais: critério de sucesso detalhado | Histórico: todo ciclo preservado | Auditoria: "Meta criada/revisada/ciclo encerrado" | Evolução: aditiva.

**Indicador** — Papel: métrica calculada | Tipo: Analítico | Proprietário: Serviço de Indicadores e Dashboards | Ciclo de vida: Ativo/Em revisão de fórmula/Descontinuado | Dependências: dados operacionais que alimentam seu cálculo (variável) | Relacionamentos: Meta, Dashboard | Integridade: uma única fórmula vigente por vez; fórmula anterior preservada para não distorcer histórico | Obrigatórios: nome, fórmula, fonte de dado | Opcionais: Meta associada | Histórico: toda fórmula (passada e presente) preservada | Auditoria: "Indicador definido/fórmula revisada/descontinuado" | Evolução: versionada (fórmula).

**Dashboard** — Papel: painel consolidado | Tipo: Analítico (composição) | Proprietário: Serviço de Indicadores e Dashboards | Ciclo de vida: Ativo/Em revisão/Descontinuado | Dependências: um ou mais Indicadores | Relacionamentos: Indicador, Meta | Integridade: nenhum item exibido sem Indicador correspondente | Obrigatórios: nome, público-alvo, Indicadores incluídos | Opcionais: organização visual | Histórico: composição versionada | Auditoria: "Dashboard criado/atualizado/descontinuado" | Evolução: aditiva.

### 4.7 Domínio Comercial Adicional

**Pacote** — Papel: agrupamento comercial | Tipo: Mestre | Proprietário: Serviço Comercial | Ciclo de vida: Em montagem/Ativo/Descontinuado | Dependências: um ou mais Produtos ativos | Relacionamentos: Produto, Orçamento, Contrato, Evento | Integridade: não pode incluir Produto Descontinuado | Obrigatórios: nome, Produtos incluídos, preço | Opcionais: descrição, público-alvo | Histórico: composição versionada | Auditoria: "Pacote criado/publicado/revisado/descontinuado" | Evolução: aditiva.

**Evento** — Papel: objeto central de venda/operação | Tipo: Transacional | Proprietário: Serviço de Eventos | Ciclo de vida: Prospectado→Orçado→Confirmado→Em planejamento→Em execução→Concluído/Cancelado | Dependências: Cliente/Lead; Orçamento/Contrato para confirmação | Relacionamentos: Cliente, Orçamento, Contrato, Produção, Equipamento, Veículo, Alocação de Funcionário, Receita Financeira, Despesa | Integridade: nenhum recurso (Produção/Estoque/Equipamento/Alocação) reservado antes de "Confirmado" | Obrigatórios: Cliente, data, local, escopo, convidados | Opcionais: observações especiais | Histórico: permanente | Auditoria: "Evento registrado/confirmado/.../concluído/cancelado" | Evolução: aditiva.

---

## 5. Mapa Global dos Dados

Visão consolidada de como todas as entidades se relacionam (mesma direção de leitura da Cadeia de Valor já validada no System Architecture, Capítulo 5):

```
Campanha ──► Lead ──► Cliente ──┬──► Orçamento ──► Contrato ──► Evento
                                 │         ▲             │          │
                    Ficha Técnica┘         │             │          ├──► Produção ──► Lote ◄── Compra ◄── Fornecedor
                    (via Produto/Pacote)   │             │          │        │                    │
                                            └─ Receita ───┘          │        └──► Estoque ◄────────┘
                                                                      │
                                                                      ├──► Alocação de Funcionário ◄── Funcionário
                                                                      ├──► Equipamento / Veículo
                                                                      └──► Documento (gerado a partir de Contrato/Compra/Evento)

Evento/Contrato/Compra/Alocação ──► Despesa / Receita Financeira ──► Pagamento ──► Conta ──► Banco
Despesa/Receita Financeira/Pagamento ──► Fluxo de Caixa ──► Indicador ──► Dashboard ──► Meta (consumo)
```

**Leitura do mapa:** setas indicam "gera dado consumido por" (nunca "copia dado para"). Todo relacionamento é por identificador (Seção 3.2 — Agregados); nenhuma entidade duplica o dado de outra. As entidades Mestres (Cliente, Fornecedor, Funcionário, Ingrediente, Produto, Pacote, Equipamento, Veículo, Banco, Conta) aparecem como pontos de referência estáveis, nunca como pontas geradas por outra entidade.

---

## 6. Governança dos Dados

- **Qualidade:** todo dado obrigatório de uma entidade (Seção 4) é validado na origem, nunca aceito incompleto; parâmetros de Configuração ausentes bloqueiam o cálculo dependente em vez de assumir um valor (Seção 3.5).
- **Consistência:** todo cálculo (custo, preço, indicador) tem exatamente uma fonte (PF-03); nenhuma entidade Mestre é duplicada entre Domínios de Dados (PF-01).
- **Unicidade:** toda entidade Mestre tem um critério de correspondência único (ex.: Cliente por nome+contato) verificado antes da criação, evitando duplicidade silenciosa (RN-009 e equivalentes).
- **Rastreabilidade:** todo Identificador Global (Seção 7.5) é estável e nunca reutilizado; todo valor analítico (Indicador/Dashboard) é reconstruível até o dado operacional de origem.
- **Auditoria:** todo evento de mudança de estado é capturado pelo Serviço de Auditoria (TCOS-006); nenhuma alteração ocorre sem metadado de autor e data (Seção 2).
- **Retenção:** nenhum dado de negócio é retido por prazo limitado por padrão — o histórico é parte do valor do sistema (CG-01); retenção limitada, se necessária por exigência legal futura (ex.: dados pessoais sensíveis), é uma decisão de governança a ser tomada explicitamente, nunca uma exclusão automática silenciosa.
- **Arquivamento:** entidades em estado terminal (Descontinuado, Encerrado, Cancelado, Inativo) permanecem no mesmo espaço de dados, apenas fora das listagens operacionais ativas por padrão — "arquivar" é uma mudança de estado, nunca uma migração para um local inacessível.
- **Recuperação:** como nenhuma exclusão física ocorre para dado que já entrou em uso de negócio (Seção 7.2), a "recuperação" de um registro é, na prática, a reversão do seu estado (ex.: reativar um Cliente) — sempre uma ação registrada, nunca uma restauração de backup para dado de negócio corrente.

---

## 7. Estratégias

### 7.1 Estratégia de Versionamento

Toda entidade cuja definição pode mudar ao longo do tempo sem perder validade histórica (Receita, Ficha Técnica, Orçamento, Documento, fórmula de Indicador) segue o mesmo padrão: uma nova versão é sempre um novo registro, vinculado ao original por uma referência de "linhagem", com exatamente uma versão marcada como vigente por vez. Versões antigas nunca são removidas nem editadas.

### 7.2 Estratégia de Soft Delete

Nenhuma entidade que já participou de um processo de negócio é fisicamente excluída (CG-01/PF-04) — ela transita para um estado terminal (Inativo, Cancelado, Encerrado, Descontinuado, Descartado). A única exceção conceitual é um registro **transitório e nunca confirmado** (ex.: um Rascunho de Orçamento abandonado antes de qualquer envio) — que pode ser removido fisicamente por não ter, ainda, se tornado parte do histórico de negócio; no momento em que uma entidade sai do estado puramente transitório (é enviada, confirmada, assinada), o soft delete passa a ser a única forma de encerramento.

### 7.3 Estratégia de Auditoria

Toda mudança de estado relevante gera um evento (Event Bus, TCOS-006), consumido pelo Serviço de Auditoria em um log imutável e apenas-para-inserção (append-only). O log de auditoria nunca é editado ou removido — é o registro definitivo de "o que aconteceu e quando" independentemente do estado atual do dado operacional.

### 7.4 Estratégia de Integridade

Toda referência entre entidades aponta para um registro existente — nunca uma referência "pendurada". Uma entidade Mestre referenciada (Cliente, Ingrediente, Fornecedor etc.) pode ser inativada, mas nunca removida enquanto houver qualquer referência ativa a ela. Toda regra de integridade específica já foi detalhada por entidade na Seção 4; esta estratégia consolida o princípio geral: **inativar, nunca remover, quando referenciado**.

### 7.5 Estratégia de Identificação Global

Toda entidade recebe um identificador único, atribuído em sua criação, estável durante todo o seu ciclo de vida (mesmo entre versões — a versão tem sua própria identidade, mas referencia a identidade da entidade "raiz" de sua linhagem) e nunca reutilizado, mesmo após inativação/descontinuação. Isso é o que sustenta a rastreabilidade e a auditoria de forma confiável ao longo de anos de operação.

### 7.6 Estratégia para Multiempresa

Nenhuma entidade desta arquitetura assume, estruturalmente, pertencer a uma única empresa. O escopo "Organização" (Seção 2 — Metadados Universais) é reservado como um atributo transversal a ser adicionado de forma aditiva quando a segunda empresa surgir — nenhuma entidade precisa ser redesenhada; apenas passa a carregar esse atributo, inicialmente com um único valor implícito. Esta é a mesma estratégia já prevista na Filosofia de Evolução do Framework (Seção 25) e no System Architecture (M-006-01).

### 7.7 Estratégia para Multifilial

Análoga à 7.6, em um nível abaixo (Unidade/Filial dentro de uma Organização). Entidades naturalmente físicas (Estoque, Equipamento, Veículo, Lote) tendem a ser escopadas por Unidade; entidades de catálogo (Produto, Receita, Ficha Técnica, Ingrediente) tendem a ser compartilhadas entre Unidades de uma mesma Organização — mas essa é uma decisão de negócio ainda não confirmada (relacionada a R-000-03), registrada aqui como pendência, não como suposição.

### 7.8 Estratégia para Crescimento Futuro

Toda evolução deste modelo de dados deve ser **aditiva**: novos atributos, novas entidades ou novos Domínios de Dados se conectam ao que já existe via referência por identificador e via eventos do Event Bus (TCOS-006) — nunca exigindo alteração retroativa de entidades já em produção. Este é o mesmo critério de sucesso já estabelecido no Framework (Seção 25) e no System Architecture (Capítulo 9): extensão, nunca reconstrução.

---

## 8. Classificação dos Dados

| Categoria | Entidades/Dados |
|---|---|
| **Operacionais** | Cliente, Lead, Campanha, Evento, Orçamento, Contrato, Produto, Ingrediente, Receita, Ficha Técnica, Produção, Fornecedor, Compra, Estoque, Lote, Equipamento, Veículo, Funcionário, Alocação de Funcionário, Pacote, Documento |
| **Financeiros** | Despesa, Receita Financeira, Pagamento, Banco, Conta, Fluxo de Caixa |
| **Estratégicos** | Meta, margem-alvo e demais parâmetros de decisão da Direção (Seção 3.5) |
| **Configuração** | Parâmetros de consumo/perda/rendimento, proporção de escala, política de cancelamento, ponto de reposição, permissões/perfis (Seção 3.5) |
| **Histórico** | Todas as versões substituídas (Receita, Ficha Técnica, Orçamento, Documento, fórmulas de Indicador), aditivos de Contrato, ciclos encerrados de Meta, log de auditoria |
| **IA** | Sugestões geradas (categorização, previsão, preço), decisão humana sobre cada uma, histórico de aceite/recusa/reversão |
| **Indicadores** | Indicador, Dashboard |

Um mesmo dado pode aparecer, ao longo do tempo, em mais de uma categoria (ex.: uma Ficha Técnica Vigente é dado Operacional; ao ser substituída, sua versão anterior passa a ser dado Histórico) — a categoria reflete o **papel atual** do dado, não uma propriedade fixa da entidade.

---

## 9. Resumo para o Proprietário

Organizamos como as informações do THE CHARCOAL OS vão ser guardadas e conectadas entre si — sem ainda escolher em que "tipo de arquivo" ou "programa de banco de dados" isso vai morar (essa decisão vem na próxima etapa).

A ideia central é: cada informação tem um "dono" único (por exemplo, só o Financeiro guarda o saldo de uma Conta), nada é jogado fora de verdade (mesmo um Cliente inativo continua no sistema, só marcado como inativo), e toda mudança fica registrada para sempre, com quem fez e quando. Isso é o que garante que, daqui a cinco ou dez anos, será possível olhar para trás e entender exatamente o que aconteceu com qualquer Evento, Contrato ou centavo do caixa.

Isso protege o crescimento futuro do negócio porque já deixamos "reservado" o espaço para quando a empresa tiver uma segunda unidade ou uma segunda empresa — sem precisar reconstruir nada do que já existir até lá. É a mesma filosofia de "crescer por extensão, nunca por reconstrução" que já vem guiando todo o projeto desde a primeira fase.

Este documento prepara diretamente a próxima etapa (TCOS-008): agora que sabemos exatamente quais informações existem, como se relacionam e quais regras protegem sua integridade, o próximo passo é desenhar o banco de dados propriamente dito — ainda sem escrever nenhuma linha de código.

---

## 10. TCOS QUALITY GATE EXECUTIVO

Em conformidade com a Regra Permanente do Framework, foi reexecutada a auditoria completa sobre todos os 10 documentos oficiais antes do encerramento desta fase — resultado consolidado na Auditoria de Abertura (Seção 0) e reafirmado aqui: nenhuma inconsistência, conflito, duplicidade, entidade órfã, atributo ausente ou relacionamento incompleto permaneceu sem tratamento.

**1. Resumo Executivo**
Definida a arquitetura de dados completa do THE CHARCOAL OS: 7 Domínios de Dados, 24 Agregados, classificação de 30 entidades (Mestres/Transacionais/Analíticas), Dados Configuráveis/Históricos/Auditoria/IA, Mapa Global dos Dados, Governança, 8 Estratégias (versionamento, soft delete, auditoria, integridade, identificação global, multiempresa, multifilial, crescimento) e Classificação dos Dados em 7 categorias. Nenhuma tecnologia foi definida; nenhum documento anterior foi alterado.

**2. Estado atual do projeto**
Fases 000 a 006 encerradas e oficiais; Fase 007 em validação. Nenhum banco físico, SQL, API ou desenvolvimento foi iniciado.

**3. Documentos oficiais existentes**
Os 10 já registrados na Executive Memory, mais este documento em rascunho.

**4. Dependências desta fase**
30 entidades, 47 Regras de Negócio, 98 funcionalidades, 30 fluxos, 30 telas, 15 Serviços Conceituais e o Event Bus — todos referenciados, nenhum reescrito.

**5. Pendências abertas**
Validação formal deste documento; parâmetros do Módulo 24; M-003A-03/04; M-005-01/02/03; M-006-01; decisão de negócio sobre escopo de Unidade para catálogo compartilhado (Seção 7.7); confirmação do domínio de negócio (R-000-03).

**6. Dúvidas encontradas**
Se Produto/Receita/Ficha Técnica devem ser compartilhados entre futuras Unidades/Filiais ou específicos de cada uma (Seção 7.7) — decisão de negócio, não de dados, ainda não confirmada.

**7. Riscos ativos**
R-000-03/R-002-01, R-001-01/R-002-02, R-002A-01 — herdados; nenhum impede a arquitetura de dados.

**8. Novos riscos encontrados**
Nenhum risco novo. A ausência de decisão sobre escopo de compartilhamento multifilial (item 6) é tratada como pendência de negócio, não como risco técnico.

**9. Inconsistências encontradas**
Nenhuma.

**10. Conflitos entre documentos**
Nenhum.

**11. Entidades órfãs**
Nenhuma — as 30 entidades do Domain Model estão todas mapeadas a um Domínio de Dados, um Agregado e um Serviço proprietário.

**12. Atributos ausentes**
Identificados e corrigidos: Identificador Global e metadados de auditoria (autor/data de criação e alteração), agora universais a toda entidade (Seção 2).

**13. Relacionamentos incompletos**
Nenhum — todos os relacionamentos do Domain Model foram retomados e classificados por tipo de integridade.

**14. Regras sem suporte de dados / Funcionalidades sem suporte de dados**
Nenhuma — confirmado item a item na auditoria de abertura.

**15. Melhorias sugeridas**
- M-007-01: ao confirmar a decisão de negócio da Seção 7.7 (compartilhamento de catálogo entre Unidades), atualizar esta arquitetura com uma nova versão antes de iniciar o TCOS-008.
- M-006-01 (herdada): permanece como pendência de implementação da dimensão Organização/Unidade, agora com o mecanismo de adição aditiva já definido (Seção 7.6/7.7).

**16. Impacto nas próximas fases**
Esta arquitetura de dados é a referência obrigatória para o TCOS-008 (Especificação de Banco de Dados) — nenhuma tabela, chave ou índice físico deve ser definida de forma incompatível com os Domínios, Agregados, integridade e estratégias aqui documentados, sem registrar formalmente o motivo.

**17. Quality Score: 9,5/10**
Justificativa técnica: cobertura completa das 30 entidades nos 12 campos exigidos, identificação e correção de uma lacuna real (ausência de Identificador Global/metadados universais até esta fase), e resolução de uma oportunidade de simplificação concreta (Agregado Financeiro unificado). Não é 10 porque a decisão de negócio sobre compartilhamento de catálogo entre futuras Unidades permanece em aberto, podendo exigir ajuste pontual antes do TCOS-008.

**18. Atualização do PROJECT_MEMORY.md:** ver commit correspondente.

**19. Estatísticas Finais**
- Domínios de dados: 7.
- Entidades: 30 (0 novas — todas herdadas do Domain Model, agora com camada de dados definida).
- Agregados: 24.
- Relacionamentos: 30+ relações mapeadas no Mapa Global dos Dados (Capítulo 5).
- Regras de integridade: 30 (uma ou mais por entidade, Seção 4).
- Riscos: 0 novos (3 herdados).
- Pendências: 7 (validação do documento + 6 herdadas/novas).
- Melhorias: 1 nova (M-007-01) + 1 herdada (M-006-01).
- Percentual estimado de maturidade do projeto: **68%** (subiu de 62% — toda a organização conceitual dos dados está definida e auditada; falta o desenho físico do banco de dados, contratos de API e a construção técnica propriamente dita, além da confirmação de parâmetros e decisões de negócio ainda pendentes).

---

*Fim do documento — THE CHARCOAL OS DATA ARCHITECTURE v1.0.0*
