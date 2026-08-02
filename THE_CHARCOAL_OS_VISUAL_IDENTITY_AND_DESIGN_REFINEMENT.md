# THE CHARCOAL OS — VISUAL IDENTITY & DESIGN REFINEMENT

**Documento:** TCOS-019A
**Fase:** 019A — Visual Identity & Design Refinement (Fase 1 — Identidade Visual Oficial)
**Natureza:** Documento exclusivamente conceitual de identidade e linguagem visual. NÃO constitui implementação, NÃO constitui código, NÃO constitui CSS, NÃO define tecnologia, framework ou biblioteca. NÃO altera arquitetura, regra de negócio, funcionalidade, fluxo, UX oficial, nomenclatura, módulo, Dashboard, componente existente ou qualquer documento oficial congelado.
**Baseline referenciada:** v1.0.0 (TCOS-000 a TCOS-018), sob a autoridade da Constituição Permanente do Projeto.
**Documentos-fonte desta fase:** Constituição Permanente; `THE_CHARCOAL_OS_UX_UI_SPECIFICATION.md` (TCOS-005); `THE_CHARCOAL_OS_FRONTEND_ARCHITECTURE.md` (TCOS-011); `THE_CHARCOAL_OS_VISUAL_BLUEPRINT.md` (TCOS-018).
**Status:** Em construção — Fase 1 (Identidade Visual Oficial) concluída — aguardando decisão do proprietário.

---

## EXECUTIVE MEMORY

Esta fase eleva a qualidade visual do THE CHARCOAL OS, definindo pela primeira vez os valores concretos (paleta, tipografia, espaçamento, elevação) para os tokens conceituais que o TCOS-018 deixou deliberadamente `[Pendente de confirmação visual]` — sem alterar nenhuma categoria semântica, nome, comportamento ou regra já oficial. Onde o TCOS-005 já nomeou uma categoria (ex.: "Brasa", "Roxo-IA"), esta fase apenas **instancia** essa categoria com um valor concreto; nunca renomeia, remove ou reatribui seu papel semântico.

**Auditoria Visual pré-fase (executada antes de qualquer definição):**
- Constituição Permanente: relida integralmente — nenhuma cláusula de governança impede a definição de identidade visual nesta fase; a Política de Change Request (Capítulo 15) permanece a única via de alteração de documento já congelado, não invocada aqui, pois nenhum documento congelado é alterado.
- UX/UI Specification (TCOS-005), Capítulo 5 (Design System): relido integralmente — confirma que nenhum valor hexadecimal, pixel além do grid de 8px, ou fonte tipográfica foi definido até este momento; as 7 categorias de cor (Brasa, Carvão, Cinza-claro, Verde-sucesso, Âmbar-atenção, Vermelho-crítico, Roxo-IA), os 5 estados de botão, os 4 estados de card e os 4 estados de indicador permanecem exatamente como já nomeados — esta fase não os redefine, apenas os instancia.
- Frontend Architecture (TCOS-011), Capítulo 11: relido — confirma o Design System como "congelado e não redefinido" na arquitetura de frontend, com uma única formalização adicional (Roxo-IA como atributo de estado obrigatório de conteúdo de IA) — mantida integralmente nesta fase.
- Visual Blueprint (TCOS-018): relido — nenhuma divergência entre o Blueprint e o mockup de alta fidelidade já aprovado (Dashboard CEO) foi encontrada; as 2 correções aplicadas ao mockup antes de sua apresentação (tabela restrita a Data/Cliente/Status; barra lateral com as 10 Áreas completas) já garantem essa aderência.
- **Nenhuma inconsistência documental, nenhuma divergência entre Blueprint e Mockup, nenhuma funcionalidade criada, nenhuma tela diferente do Blueprint foi encontrada.** A construção da Fase 1 está autorizada a prosseguir.

---

## 1. Papel deste Documento

O TCOS-019A é o documento que responde à pergunta: **qual é, concretamente, a aparência do THE CHARCOAL OS?** O TCOS-005 (UX/UI Specification) já havia nomeado as categorias semânticas de cor, os estados de componente e o grid-base; o TCOS-018 (Visual Blueprint) já havia mostrado exatamente onde cada uma dessas categorias aparece, tela por tela. Faltava o elo final: os valores concretos — a identidade visual completa e coesa que faz o sistema parecer **um único produto**, com personalidade própria, e não uma composição genérica de componentes.

## 2. Legenda e Convenções

- Toda categoria semântica de cor, estado ou componente usa exatamente o nome já oficial (TCOS-005, Seção 5.6–5.10) — este documento nunca renomeia, apenas instancia com valor concreto.
- **Token de identidade:** um valor concreto (cor, medida, curva de animação) atribuído a um conceito já nomeado — nunca um conceito novo.
- Todo valor definido aqui é **conceitual e visual**, nunca técnico: cores são descritas por papel e valor de referência (não por variável de CSS/SCSS); tipografia é descrita por característica (não por nome de arquivo de fonte ou licença); animação é descrita por sensação e curva (não por biblioteca ou implementação).

## 3. Personalidade Visual e Sensação Transmitida

O THE CHARCOAL OS deve parecer o oposto de dois extremos comuns em software de gestão: nunca a frieza burocrática de uma planilha, e nunca a leveza descompromissada de um aplicativo de consumo. A personalidade é a de um **instrumento de precisão operado por quem entende do ofício** — o mesmo cuidado de quem controla o ponto exato da brasa se reflete na forma como o sistema apresenta um número, um alerta ou uma decisão pendente.

As 10 sensações exigidas pelo proprietário se traduzem em decisões visuais concretas, não apenas em adjetivos:

| Sensação exigida | Tradução visual |
|---|---|
| Confiança | Cor usada com intenção, nunca decorativa; todo número crítico (KPI, alerta) recebe o mesmo tratamento tipográfico em qualquer tela — nunca varia sem motivo. |
| Robustez | Componentes com peso visual estável (bordas e sombras discretas, nunca frágeis ou "flutuantes" demais); nenhuma tela parece incompleta mesmo em Estado Vazio. |
| Organização | Grid rígido de 8px (já oficial, TCOS-005 §5.3) aplicado sem exceção; alinhamento vertical e horizontal previsível em toda tela. |
| Inteligência | Números sempre tabulares e alinhados; toda sugestão de IA visualmente distinta (Roxo-IA) e nunca misturada ao dado "de fato". |
| Simplicidade | Um único acento de cor por tela para ação primária; nunca mais de uma cor "gritando" ao mesmo tempo. |
| Alta tecnologia | Uso deliberado de profundidade sutil (elevação, Capítulo 9) para sinalizar camadas de informação, não decoração. |
| Sofisticação | Paleta neutra refinada (nunca cinza puro, nunca branco puro no canvas) — ver Capítulo 5. |
| Estabilidade | Nenhum componente muda de posição ou tamanho ao mudar de estado (loading/vazio/erro) — apenas seu conteúdo interno muda. |
| Velocidade | Microinterações curtas (Capítulo 22) — o sistema nunca faz o usuário esperar visualmente por uma confirmação que já aconteceu. |
| Precisão | Alinhamento numérico exato (tabular-nums), hierarquia sem ambiguidade entre o que é dado real e o que é meta/previsão. |

## 4. Linguagem de Design e Princípios de Interface

Cinco princípios, cada um derivado diretamente de um Princípio Fundamental já oficial (Framework, TCOS-000) ou de uma regra já estabelecida no TCOS-005/011:

1. **Um acento, uma vez por tela.** A cor Brasa é reservada para exatamente uma ação primária e para o item de navegação ativo — nunca usada como decoração repetida (evita a "poluição de cor" comum em dashboards genéricos).
2. **Hierarquia por peso, não por quantidade de cor.** Diferenciação de importância vem de peso tipográfico e tamanho (já oficial, TCOS-005 §5.4), não de aplicar cores diferentes a textos igualmente importantes.
3. **A cor sempre significa algo.** Nenhuma cor é usada apenas por estética — toda cor fora da paleta neutra corresponde a uma categoria semântica já oficial (status, criticidade, IA).
4. **Densidade com respiro.** O sistema mostra muito dado (Dashboards com 6 KPIs, tabelas extensas) sem parecer congestionado — resolvido por espaçamento consistente (Capítulo 7), nunca por reduzir a quantidade de informação real.
5. **Nada se move sem motivo.** Toda animação (Capítulo 21) comunica uma mudança de estado real — nunca decorativa (reforça PF-06, "IA nunca decide sozinha", e PF-04, "histórico obrigatório": o usuário sempre percebe visualmente que algo mudou e por quê).

## 5. Paleta Oficial

Instancia, pela primeira vez, valores concretos para as 7 categorias já nomeadas no TCOS-005 (§5.7) — nenhum nome, papel ou categoria é alterado.

| Categoria (já oficial) | Papel (já oficial) | Valor de referência definido nesta fase |
|---|---|---|
| Brasa | Ação primária, estado ativo/confirmado, destaque | `#E2542B` — laranja-avermelhado quente, a única cor "alta energia" do sistema |
| Carvão | Texto principal, alta ênfase, fundo do menu lateral | `#1B1917` — quase-preto de matiz quente (nunca neutro-frio) |
| Cinza-claro | Fundos neutros, estados inativos/desabilitados | Escala de 4 tons quentes, de `#F8F7F5` (fundo de tela) a `#DEDAD3` (bordas fortes) — nunca cinza-azulado |
| Verde-sucesso | Confirmações, Metas atingidas, "Disponível"/"Concluído" | `#1E9E6C` |
| Âmbar-atenção | Alertas não críticos, "Metas não atingidas", "Em manutenção" | `#C77C1F` |
| Vermelho-crítico | Alertas de alta prioridade, bloqueios, "Vencido"/"Cancelado" | `#D6472F` |
| Roxo-IA | Exclusivo para conteúdo gerado/sugerido por IA | `#7C5CFF` — deliberadamente a **única cor fria** de toda a paleta |

**Justificativa de identidade:** a decisão de fundamentar a paleta inteira em tons quentes (laranja-carvão, nunca azul) é a principal fonte de reconhecimento visual imediato do sistema — a esmagadora maioria dos produtos de gestão corporativa (incluindo várias das referências de qualidade citadas) usa azul ou roxo como cor dominante. Manter o Roxo-IA como a única exceção fria da paleta não é acidental: transforma a própria "quebra da regra de cor" em sinal — qualquer conteúdo em tom frio é, por definição, gerado por IA, nunca dado humano direto. Nenhum valor de cor aqui definido altera o papel semântico já oficial de nenhuma categoria — apenas atribui, pela primeira vez, um valor de referência a cada uma.

## 6. Tipografia e Pesos Tipográficos

Sem nomear uma família tipográfica comercial específica (decisão de licenciamento/tooling, fora do escopo conceitual desta fase) — define-se o **arquétipo tipográfico** que qualquer fonte escolhida futuramente deve seguir, reafirmando sem alteração a regra já oficial (TCOS-005 §5.4: fonte sans-serif única, peso variável).

- **Arquétipo:** grotesca contemporânea, de baixo contraste entre traços finos e grossos, terminais discretamente quadrados (não geométrica-circular, não humanista-caligráfica) — transmite precisão sem frieza excessiva.
- **Escala de peso:** Regular (400) para corpo de texto; Semibold (600) para títulos de card, cabeçalhos de seção e valores de KPI; Bold (700) reservado exclusivamente para alertas críticos (já oficial, TCOS-005 §5.4) — nunca usado por ênfase estética.
- **Números:** sempre com alinhamento tabular (todo dígito ocupa a mesma largura) — obrigatório em toda tabela, KPI e gráfico, para que colunas de números sempre alinhem verticalmente, reforçando a sensação de precisão (Capítulo 3).
- **Escala de tamanho:** proporção modesta entre níveis (na ordem de 1,25×), nunca saltos grandes — reforça "organização" e "estabilidade" (Capítulo 3) em vez de hierarquia agressiva.

## 7. Espaçamento e Grid

Reafirma, sem alteração, o grid de 8px já oficial (TCOS-005 §5.3) como a única unidade de espaçamento do sistema. Esta fase define a **aplicação consistente** dessa unidade:

- Espaçamento interno de componente (padding): múltiplos de 8, nunca valores intermediários.
- Espaçamento entre componentes irmãos (gap): múltiplos de 16 em telas densas (Dashboards, Listas), múltiplos de 24 em telas de leitura (Detalhe).
- Margem externa de seção: múltiplos de 32.
- Nenhum elemento visual jamais rompe o grid — inclusive elementos decorativos (ícones, avatares, badges) são dimensionados em múltiplos de 8 sempre que possível.

## 8. Raios de Borda

Conceito novo desta fase — não definido em nenhum documento anterior. Uma única escala de 3 valores, aplicada por categoria de componente, nunca por preferência pontual:

- **Raio pequeno** (elementos de ação: botões, badges, chips, campos de entrada) — cantos discretamente arredondados, transmitindo precisão sem rigidez.
- **Raio médio** (contêineres: cards, painéis, modais) — arredondamento mais perceptível, para diferenciar visualmente "container de conteúdo" de "elemento de ação".
- **Raio circular** (exclusivo para avatares, indicadores de estado pontuais e o ícone de IA) — a única forma totalmente circular do sistema, reforçando que representa uma "pessoa" ou uma "IA", nunca um dado ou uma ação.

## 9. Sombras e Profundidade

Conceito novo desta fase. A profundidade comunica **camada de informação**, nunca decoração:

- **Nível 0 (plano):** o próprio canvas da tela e a barra lateral — sem sombra, são a "base" de tudo.
- **Nível 1 (conteúdo):** cards, painéis, linhas de tabela em hover — sombra muito sutil, quase imperceptível, apenas suficiente para separar do fundo.
- **Nível 2 (sobreposição temporária):** Drawers, menus suspensos, tooltips — sombra mais perceptível, sinalizando que o elemento está temporariamente "acima" do fluxo normal da tela.
- **Nível 3 (interrupção):** Modais e confirmações de Operação Crítica (TCOS-018, item 25.19) — a sombra mais forte do sistema, reservada exclusivamente para o momento em que o sistema exige atenção total do usuário antes de prosseguir.

Esta escala de 4 níveis nunca se sobrepõe: um elemento de Nível 2 nunca aparece simultaneamente com um de Nível 3 sem que o de Nível 2 seja visualmente "esmaecido" ao fundo (reforça PF-06 e o padrão de confirmação explícita já oficial).

## 10. Hierarquia Visual

Reafirma e refina a hierarquia já oficial (TCOS-005 §5.2; TCOS-019A Capítulo 4, princípio 2): título de página → título de seção/card → corpo → legenda/metadado, cada nível distinguido por peso e tamanho tipográfico (Capítulo 6), nunca por cor. Números de KPI permanecem, como já oficial, o elemento de maior destaque tipográfico de qualquer tela — nesta fase, esse destaque é formalizado como o único caso em que um valor numérico pode usar tamanho de texto maior que um título de seção.

## 11. Padrões de Contraste

Conceito novo desta fase, respondendo à melhoria M-011-02 já registrada (Frontend Architecture, TCOS-011): todo par texto/fundo do sistema deve atingir, no mínimo, contraste equivalente ao padrão AA de acessibilidade — aplicável a texto sobre card, texto sobre barra lateral (Carvão) e texto sobre qualquer badge/pill de status. Esta fase registra o **requisito de contraste como princípio de identidade** (não apenas como regra técnica de acessibilidade) — um sistema "sofisticado e preciso" nunca sacrifica legibilidade por estética. A validação técnica exata do contraste permanece, como já registrado, pendente da escolha de tecnologia (M-011-02).

## 12. Linguagem de Ícones

Reafirma o estilo já oficial (TCOS-005 §5.5: linha/outline, ícone de IA fixo). Esta fase acrescenta: traço de espessura única e consistente em todos os ícones do sistema (nunca ícones preenchidos misturados a ícones de linha); cantos com o mesmo raio pequeno já definido para botões (Capítulo 8), para que o ícone "combine" visualmente com os controles ao seu redor; o ícone de IA (já oficial, "uma pequena faísca") é o único ícone do sistema autorizado a usar a cor Roxo-IA — todos os demais ícones usam Carvão ou Cinza conforme o contexto, nunca cor semântica decorativa.

## 13. Linguagem dos Gráficos

Novo nesta fase, aplicável aos tipos de gráfico já usados no TCOS-018 (linha, barras, funil, calendário/timeline, feed cronológico, histograma): toda linha de gráfico usa a cor Brasa como traço principal, com preenchimento em gradiente sutil da mesma cor (opacidade decrescente) — nunca uma segunda cor de traço, exceto quando o gráfico compara duas séries semanticamente diferentes (ex.: planejado × real), caso em que a série "real" usa Brasa sólida e a série "planejado" usa Cinza-claro. Grades de fundo (linhas de referência) são sempre discretas, nunca competindo visualmente com o dado. Nenhum gráfico usa mais de 2 cores simultâneas, exceto o funil (Capítulo 20, Dashboard CRM) e o calendário, que usam a paleta semântica completa por serem, por natureza, uma composição de vários estados.

## 14. Linguagem dos Cards

Todo Card (KPI, progresso, contêiner de gráfico/tabela) segue a mesma anatomia visual: fundo neutro claro, borda de 1px na cor de borda mais sutil da escala (Capítulo 5), Nível 1 de sombra (Capítulo 9), raio médio (Capítulo 8). O rótulo do Card é sempre o elemento de menor ênfase visual dentro dele; o valor/conteúdo principal é sempre o de maior ênfase — nunca o inverso, reafirmando a hierarquia de KPI já oficial (TCOS-005 §5.4).

## 15. Linguagem das Tabelas

Cabeçalho de tabela sempre em texto pequeno, peso Semibold, cor secundária (nunca Carvão puro) e caixa alta discreta — para se diferenciar claramente do conteúdo das linhas. Linhas separadas por uma borda mais sutil que a borda de card (Capítulo 5), nunca por zebra-striping (alternância de cor de fundo), para manter a densidade visual "organizada" (Capítulo 3) sem ruído. Toda coluna numérica é alinhada à direita com números tabulares (Capítulo 6); toda coluna de texto é alinhada à esquerda.

## 16. Linguagem dos Botões

Reafirma os 3 tipos já oficiais (primário/secundário/terciário, TCOS-005 §5.6) com identidade concreta: o botão primário é a única aplicação de fundo sólido Brasa em toda a interface fora de badges de estado; o botão secundário usa apenas borda e texto Carvão, fundo neutro; o botão terciário é texto puro, sem borda nem fundo, reservado a ações de baixíssima prioridade (ex.: "Baixar PDF"). Os 5 estados já oficiais (normal, hover, focus, disabled, loading, TCOS-005 §5.8) recebem tratamento visual consistente em todos os tipos — hover sempre um leve escurecimento da própria cor do botão, nunca uma cor diferente.

## 17. Linguagem dos Filtros

O componente "Filtro combinável" (já oficial) usa sempre a mesma forma visual do campo de entrada (raio pequeno, Capítulo 8) com um ícone de seta discreto indicando que é expansível. Filtros ativos (com valor selecionado, diferente do padrão) recebem uma marcação visual sutil (borda em Brasa, nunca preenchimento) para que o usuário perceba, à distância, que a tela está sendo exibida com um recorte — nunca uma cor forte que compita com o dado principal da tela.

## 18. Linguagem dos Badges

O Badge de status (já oficial, uma cor por estado do ciclo de vida) usa sempre a mesma forma: pílula de raio circular, fundo em tom claro da cor semântica (nunca a cor sólida), texto na variante escura da mesma cor — nunca texto branco sobre cor sólida, para manter a leveza visual mesmo em telas com muitos badges simultâneos (ex.: tabela de Eventos com um badge por linha).

## 19. Linguagem dos Alertas

Reafirma os 3 componentes já oficiais (Alerta inline, Banner de alerta persistente, Notificação toast) com identidade visual distinta por nível de urgência: Alerta inline usa apenas texto colorido, sem fundo, por estar sempre próximo ao campo que o originou; Banner persistente usa fundo em tom claro da cor de criticidade com ícone de destaque, ocupando a largura total do contexto em que aparece; Toast usa fundo Carvão (não a cor semântica) com um pequeno indicador colorido lateral — para que notificações efêmeras nunca sejam confundidas visualmente com alertas persistentes que exigem ação.

## 20. Estados da Interface

Reafirma, com identidade visual concreta, os estados já formalizados (Frontend Architecture, TCOS-011, Capítulos 18–20): o Estado de Carregamento (Skeleton) usa sempre a mesma silhueta cinza-claro com uma animação sutil de "respiração" (Capítulo 21); o Estado Vazio usa uma ilustração de linha simples (nunca fotografia ou ilustração colorida, para permanecer consistente com a linguagem de ícones, Capítulo 12) mais texto explicativo; o Estado de Erro usa sempre o ícone de atenção já definido, nunca uma tela vermelha inteira — a cor crítica é reservada ao ícone e ao texto do motivo, nunca ao fundo completo da tela.

## 21. Animações Conceituais

Conceito novo desta fase — nenhuma tecnologia ou biblioteca definida, apenas sensação e curva:

- **Transições de tela:** dissolução suave e rápida (nunca deslizamento lateral longo), reforçando "velocidade" (Capítulo 3) sem desorientar o usuário.
- **Atualização automática de dado** (Dashboards, Frontend Architecture Capítulo 16): o valor numérico se atualiza com uma transição curta de contagem (nunca troca instantânea e brusca), sinalizando visualmente que algo mudou sem exigir que o usuário releia a tela inteira.
- **Skeleton de carregamento:** pulsação suave e lenta — nunca um piscar rápido, que transmitiria instabilidade, o oposto da identidade pretendida.
- **Abertura de Modal/Drawer:** entrada com leve elevação (sobe e ganha nitidez), reforçando a metáfora de profundidade já definida (Capítulo 9).

Toda animação é breve por princípio (Capítulo 4, item 5: "nada se move sem motivo") — a duração nunca compete com a velocidade percebida do sistema.

## 22. Microinterações Conceituais

- **Botão ao ser pressionado:** leve compressão visual, confirmando o toque/clique antes mesmo da resposta do backend chegar — nunca deixa o usuário em dúvida se a ação foi registrada.
- **Checkbox/seleção em tabela:** marcação com uma pequena confirmação visual instantânea (nunca uma troca abrupta sem transição).
- **Arraste em Kanban (Leads, Compras):** o card arrastado ganha elevação (Capítulo 9, Nível 2) durante o arraste, e "assenta" com uma pequena resposta visual ao soltar — comunicando fisicamente que a mudança de estágio foi aceita.
- **Aceitar/Recusar sugestão de IA:** a resposta do usuário (Componente de sugestão de IA) é seguida de uma transição de saída suave do card de sugestão — nunca um desaparecimento abrupto, para que o usuário perceba com clareza que sua decisão foi registrada (reforça PF-06 e a Auditoria Visual de Ações, TCOS-011 Capítulo 23).

---

**Fim da Fase 1 — Identidade Visual Oficial.**