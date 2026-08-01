# THE CHARCOAL OS — QUESTIONÁRIO OFICIAL DE DESCOBERTA DO NEGÓCIO

**Documento:** Fase 001B — Business Discovery Questionnaire
**Projeto:** THE CHARCOAL OS
**Status:** Aguardando respostas do proprietário
**Versão:** 1.0.0

---

## Como usar este documento

Este questionário é a base definitiva para todo o desenvolvimento do THE CHARCOAL OS. Ele não substitui o `THE_CHARCOAL_OS_ENTERPRISE_DOMAIN_DISCOVERY.md` — ele existe para validar, corrigir e aprofundar aquele documento com a realidade específica desta empresa, não com um modelo genérico de catering.

Não é necessário responder tudo de uma vez, nem em ordem. Respostas podem ser dadas por categoria, aos poucos, ou em texto livre — o importante é que reflitam como o negócio **realmente** funciona hoje, e não como "deveria" funcionar.

Cada pergunta traz, logo abaixo, uma explicação de **por que ela importa** para o sistema.

---

## 1. História da Empresa

**Q1.** Como e quando a empresa começou, e qual foi a motivação de quem a fundou?
*Por que importa:* entender a origem ajuda a preservar a identidade e os valores da marca dentro do sistema e no discurso comercial.

**Q2.** Quais foram os principais marcos ou mudanças de rumo desde o início até hoje (mudança de local, de porte, de tipo de cliente, de sócios)?
*Por que importa:* revela se o negócio já passou por mudanças que deixaram processos ou dados "legados" que precisam ser considerados.

**Q3.** De onde veio o nome da empresa e o que ele representa para quem a fundou?
*Por que importa:* ajuda a alinhar a identidade de marca (o Manifesto já registrado) com a história real, evitando um discurso institucional genérico.

**Q4.** Como a empresa se descreveria hoje, em poucas frases, para alguém que nunca ouviu falar dela?
*Por que importa:* essa descrição vira a base da comunicação comercial e do Manifesto dentro do sistema.

## 2. Modelo de Negócio

**Q5.** De onde vem a maior parte do faturamento hoje: eventos, venda avulsa de produtos, encomendas, ou outra fonte?
*Por que importa:* define qual módulo do sistema deve ser tratado como prioridade absoluta na implantação.

**Q6.** Além do atendimento a eventos, quais outras formas de venda já existem hoje (loja, ponto fixo, cozinha aberta ao público, encomenda avulsa)? Como cada uma funciona?
*Por que importa:* se existirem, o sistema precisa tratar vendas avulsas/de balcão, não só vendas por contrato de evento.

**Q7.** Como o dinheiro entra na empresa, do primeiro contato do cliente até o recebimento final — quais são as etapas reais desse caminho hoje?
*Por que importa:* essa é a espinha dorsal do módulo comercial e financeiro do sistema.

**Q8.** Quais tipos de cliente a empresa atende hoje (pessoa física, empresas, ambos), e qual grupo representa a maior parte da receita?
*Por que importa:* pode exigir tratamentos comerciais e fiscais diferentes dentro do sistema.

**Q9.** Como a sazonalidade (datas de mais ou menos movimento ao longo do ano) afeta o negócio?
*Por que importa:* afeta diretamente o planejamento de estoque, produção e caixa que o sistema vai apoiar.

## 3. Produtos

**Q10.** Quais são, hoje, os produtos que a empresa vende? (liste da forma mais detalhada possível, mesmo que pareça óbvio)
*Por que importa:* forma a base real do catálogo de Produtos do sistema.

**Q11.** Qual produto, se algum, representa sozinho boa parte das vendas — e por quê?
*Por que importa:* ajuda a priorizar qual Ficha Técnica detalhar primeiro na implantação.

**Q12.** Os produtos vendidos mudam de tempos em tempos (cardápio sazonal, encomenda especial) ou o catálogo é fixo?
*Por que importa:* define se o sistema precisa de um processo simples ou de um processo robusto de criação/descontinuação de produto.

**Q13.** Quais produtos só são vendidos sob certas condições (quantidade mínima, tipo de cliente, região), e quais são essas condições?
*Por que importa:* pode gerar regras de disponibilidade específicas dentro do catálogo.

## 4. Serviços

**Q14.** Além dos produtos em si, quais serviços a empresa entrega junto (montagem no local, atendimento no evento, aluguel de equipamento, garçom, etc.)?
*Por que importa:* serviços muitas vezes não têm "ficha técnica" própria e acabam mal precificados — o sistema precisa cobri-los.

**Q15.** Quais desses serviços são terceirizados hoje, de quem, e como funciona essa parceria?
*Por que importa:* muda como o custo e a margem desse serviço são calculados dentro do sistema.

**Q16.** Como o preço ou a disponibilidade de um serviço muda dependendo da distância ou do local do evento?
*Por que importa:* pode exigir uma regra de custo variável por deslocamento no motor de precificação.

## 5. Eventos

**Q17.** Como é, na prática, o dia de um evento típico, do início da montagem até o fim da desmontagem?
*Por que importa:* é a base para desenhar o módulo operacional de planejamento e execução de eventos.

**Q18.** Quais tipos de evento a empresa atende hoje (casamento, corporativo, aniversário, confraternização, outro), e qual o tamanho médio (número de convidados) de cada tipo?
*Por que importa:* afeta diretamente o dimensionamento de produção, equipe e equipamento.

**Q19.** Quais foram os principais problemas que já aconteceram durante um evento (atraso, falta de produto, problema de equipe), e como cada um foi resolvido?
*Por que importa:* casos reais de falha são a melhor fonte para desenhar alertas e controles preventivos no sistema.

**Q20.** Quanto tempo de antecedência, em média, um cliente fecha um evento antes da data de realização?
*Por que importa:* define a janela de tempo que o sistema tem para planejar compras e produção.

## 6. Processo Comercial

**Q21.** Como um cliente em potencial normalmente chega até a empresa hoje (indicação, redes sociais, evento anterior, outro)?
*Por que importa:* define de onde vêm os Leads e como atribuir mérito a cada canal de marketing.

**Q22.** Quem, na equipe, atende esse primeiro contato, e como essa pessoa decide o que oferecer ao cliente?
*Por que importa:* revela se já existe um processo comercial estruturado ou se ele depende do conhecimento pessoal de quem atende.

**Q23.** Qual roteiro ou lista de perguntas, se houver, a empresa já usa para entender a necessidade do cliente antes de montar uma proposta?
*Por que importa:* pode virar o formulário de captação de escopo de evento dentro do sistema.

**Q24.** O que normalmente faz um cliente desistir ou escolher outro fornecedor no meio da negociação?
*Por que importa:* ajuda a identificar pontos de atrito no funil comercial que o sistema pode ajudar a reduzir.

## 7. Processo de Orçamento

**Q25.** Como é montado um orçamento hoje, passo a passo — o que é preciso saber do cliente e do evento antes de calcular um valor?
*Por que importa:* é a base para desenhar o fluxo de criação de Orçamento no sistema.

**Q26.** Quanto tempo leva, em média, para um orçamento ficar pronto depois que o cliente pede?
*Por que importa:* identifica se há um gargalo de agilidade que a automação pode resolver.

**Q27.** O orçamento já sai com o valor final, ou passa por revisão de outra pessoa antes de ser enviado ao cliente?
*Por que importa:* revela se existe (ou deveria existir) um fluxo de aprovação interna antes do envio.

**Q28.** Um mesmo cliente já recebeu mais de uma versão de orçamento para o mesmo evento? O que costuma mudar de uma versão para outra?
*Por que importa:* mostra a necessidade real de versionamento de orçamento e o motivo mais comum de revisão.

## 8. Processo de Negociação

**Q29.** Quais itens do orçamento costumam ser negociados pelo cliente (preço total, forma de pagamento, itens do cardápio, quantidade)?
*Por que importa:* indica quais campos do orçamento precisam ser facilmente ajustáveis sem refazer tudo do zero.

**Q30.** Até que ponto a pessoa que negocia tem liberdade para dar desconto, e a partir de que ponto precisa da autorização de outra pessoa?
*Por que importa:* define a regra de alçada de desconto que o sistema deve controlar.

**Q31.** Qual é o limite mínimo de margem que a empresa nunca aceita romper, mesmo sob pressão do cliente?
*Por que importa:* essa é a regra de negócio que protege a lucratividade e deve ficar visível durante a negociação.

## 9. Processo de Fechamento

**Q32.** O que formaliza, hoje, o fechamento de um evento — assinatura de contrato, pagamento de sinal, troca de mensagem, ou outra coisa?
*Por que importa:* define o que o sistema deve considerar como "evento confirmado" de fato.

**Q33.** Qual documento padrão (contrato, termo), mesmo informal, já é utilizado hoje?
*Por que importa:* esse documento pode servir de modelo para a geração automática de Contrato no sistema.

**Q34.** O que acontece se o cliente quiser cancelar depois de fechado? Existe alguma regra hoje (mesmo informal) sobre reembolso?
*Por que importa:* essa regra precisa existir formalmente para o sistema tratar cancelamentos sem depender de decisão caso a caso.

## 10. Pagamentos

**Q35.** Como o cliente paga hoje, na prática — existe sinal, parcelas, pagamento só no dia do evento, ou depende do caso?
*Por que importa:* é a base do módulo de contas a receber e do fluxo de caixa previsto.

**Q36.** Quais formas de pagamento a empresa aceita hoje (Pix, cartão, dinheiro, transferência, boleto)?
*Por que importa:* define quais formas de registro/integração o sistema precisa suportar.

**Q37.** Como a empresa trata hoje um cliente que atrasa ou não paga?
*Por que importa:* ajuda a desenhar o processo de cobrança e o indicador de inadimplência.

**Q38.** Como fornecedores e equipe são pagos hoje (à vista na entrega, prazo, dia fixo do mês)?
*Por que importa:* é a base do módulo de contas a pagar.

## 11. Compras

**Q39.** Como a empresa decide o que precisa comprar para um evento específico — é feito à mão, olhando a ficha de cada produto, ou de outra forma?
*Por que importa:* mostra o processo real que a automação de lista de compras precisará reproduzir.

**Q40.** Quais ingredientes exigem prazo mínimo de antecedência para compra (por disponibilidade, validade ou frescor), e qual é esse prazo?
*Por que importa:* define restrições de tempo que o planejamento de compras do sistema precisa respeitar.

**Q41.** Quem tem autonomia para decidir e efetivamente fazer uma compra hoje?
*Por que importa:* define quem serão os usuários responsáveis pelo módulo de Compras no sistema.

**Q42.** Quais casos de falta de ingrediente importante em cima da hora de um evento já aconteceram, e o que causou cada um?
*Por que importa:* casos reais de ruptura ajudam a desenhar alertas de estoque mínimo.

## 12. Fornecedores

**Q43.** Quais são os principais fornecedores da empresa hoje, e o que cada um fornece?
*Por que importa:* forma a base do cadastro inicial de Fornecedores do sistema.

**Q44.** Quais fornecedores têm condições especiais negociadas (preço fixo, prazo maior, exclusividade), e quais são essas condições?
*Por que importa:* essas condições precisam ser respeitadas pelo sistema ao sugerir compras.

**Q45.** Como a qualidade de um fornecedor é avaliada hoje, mesmo que informalmente (nunca atrasa, produto sempre bom, etc.)?
*Por que importa:* pode virar um critério formal de avaliação de fornecedor dentro do sistema.

## 13. Estoque

**Q46.** Como a empresa sabe, hoje, o que tem disponível em estoque (contagem física, planilha, "no olho")?
*Por que importa:* define o ponto de partida real para implantar um controle de estoque confiável.

**Q47.** Quais locais físicos separados de armazenamento existem hoje (câmara fria, despensa, depósito), e como os produtos circulam entre eles?
*Por que importa:* pode ser necessário controlar estoque por localização, não apenas por item.

**Q48.** Quais casos de ingrediente vencido ou estragado descoberto tarde demais já aconteceram, e o que causou isso?
*Por que importa:* mostra a necessidade real de controle de validade por lote.

## 14. Produção

**Q49.** Como é organizado o dia de produção para um evento — quem decide o que produzir primeiro, e com base em quê?
*Por que importa:* é a base para desenhar o planejamento de produção do sistema.

**Q50.** Quantas pessoas participam da produção em um evento típico, e como as tarefas são divididas entre elas?
*Por que importa:* ajuda a dimensionar o módulo de mão de obra de produção.

**Q51.** O que costuma dar errado durante a produção (falta de tempo, falta de ingrediente, erro de quantidade)?
*Por que importa:* aponta os pontos onde o sistema pode gerar mais valor prevenindo erros.

## 15. Receitas

**Q52.** As receitas usadas hoje estão escritas em algum lugar (caderno, arquivo, planilha), ou estão só na cabeça de quem cozinha?
*Por que importa:* define se será preciso um trabalho de documentação de receitas do zero antes de usar o sistema.

**Q53.** Quando uma receita muda (troca de ingrediente, ajuste de tempero), quem decide, e como essa mudança é comunicada para quem produz?
*Por que importa:* mostra a necessidade real de versionamento e comunicação de mudança de receita.

**Q54.** Diferentes pessoas que preparam a mesma receita produzem exatamente o mesmo resultado, ou existe variação de pessoa para pessoa?
*Por que importa:* mede o quanto a padronização por Ficha Técnica é urgente para a operação.

## 16. Fichas Técnicas

**Q55.** Qual documento, se houver, detalha hoje a quantidade exata de cada ingrediente, o rendimento e o custo de cada receita?
*Por que importa:* se não existir, essa é uma das primeiras entregas necessárias antes do sistema entrar em uso real.

**Q56.** Como o rendimento de uma receita é medido hoje (quantas porções realmente saem de uma produção)?
*Por que importa:* é essencial para o cálculo de custo por porção/produto.

**Q57.** Alguma vez o custo real de produzir algo surpreendeu a empresa (ficou mais caro do que o esperado)? O que causou essa diferença?
*Por que importa:* identifica onde o controle de custo real vs. planejado precisa ser mais rígido.

## 17. Engenharia de Custos

**Q58.** Hoje, o custo de um evento leva em conta só os ingredientes, ou também mão de obra, transporte, gás/carvão, embalagem e outros gastos?
*Por que importa:* define se a fórmula de custo atual está subestimando o custo real — ponto crítico para a margem.

**Q59.** Como as perdas de produção (o que sobra, estraga ou é descartado) são hoje contabilizadas no custo?
*Por que importa:* perdas não contabilizadas corroem a margem sem que ninguém perceba.

**Q60.** Existe algum rateio de custos fixos (aluguel, salário administrativo, conta de luz) sobre cada evento, ou esses custos são vistos só no total do mês?
*Por que importa:* sem esse rateio, um evento pode "parecer" lucrativo isoladamente sem ser, de fato.

## 18. Precificação

**Q61.** Como o preço final cobrado do cliente é definido hoje — existe uma margem-alvo, uma tabela, ou é caso a caso?
*Por que importa:* é a regra de negócio central do motor de precificação do sistema.

**Q62.** O preço muda dependendo da época do ano, do tamanho do evento ou da localização?
*Por que importa:* define quantas variáveis o motor de precificação do sistema precisa considerar.

**Q63.** Com que frequência os preços são revisados, e o que normalmente motiva essa revisão?
*Por que importa:* ajuda a decidir se o sistema deve alertar automaticamente quando o preço está desatualizado frente ao custo.

## 19. Desperdícios

**Q64.** Quais são, hoje, os principais tipos de desperdício na operação (comida que sobra, ingrediente que estraga, retrabalho)?
*Por que importa:* cada tipo de desperdício aponta para um controle diferente que o sistema pode ajudar a implantar.

**Q65.** Qual seria uma estimativa, mesmo informal, de quanto esse desperdício representa em dinheiro por mês?
*Por que importa:* ajuda a priorizar, entre todas as funcionalidades do sistema, qual ataca o maior prejuízo primeiro.

**Q66.** O que já foi tentado para reduzir esse desperdício, e funcionou ou não?
*Por que importa:* evita que o sistema proponha uma solução que a empresa já testou e descartou por um bom motivo.

## 20. Equipamentos

**Q67.** Quais são os principais equipamentos usados na produção e nos eventos (churrasqueiras, fornos, utensílios, estruturas, geradores)?
*Por que importa:* forma a base do cadastro de Equipamentos e de sua alocação por evento.

**Q68.** Quais equipamentos já causaram atraso ou problema em algum evento (por quebra, manutenção ou disponibilidade), e o que aconteceu?
*Por que importa:* mostra a necessidade real de um controle de manutenção preventiva e de disponibilidade.

**Q69.** Os equipamentos usados hoje são próprios, alugados, ou uma mistura dos dois?
*Por que importa:* muda como o custo de equipamento entra na precificação de cada evento.

## 21. Funcionários

**Q70.** Quantas pessoas trabalham hoje na empresa, e quais são as funções de cada uma (mesmo que uma pessoa acumule várias)?
*Por que importa:* é a base para desenhar o módulo de pessoas e definir quem usará cada parte do sistema.

**Q71.** Quais funções são fixas (contratadas) e quais são chamadas apenas para eventos específicos (freelancers, diaristas)?
*Por que importa:* muda completamente como o custo de mão de obra é calculado e alocado por evento.

**Q72.** Como o pagamento da equipe de evento é definido hoje (valor fixo por evento, por hora, por função)?
*Por que importa:* define a fórmula de custo de mão de obra que entra na Ficha Técnica/Engenharia de Custos.

## 22. Escalas

**Q73.** Como é decidido, hoje, quantas pessoas e quem exatamente vai trabalhar em cada evento?
*Por que importa:* é o processo que o módulo de escala do sistema vai precisar apoiar ou automatizar.

**Q74.** Quais casos de falta ou sobra de gente em um evento já aconteceram, e o que causou isso?
*Por que importa:* casos reais de erro de dimensionamento orientam a regra de sugestão automática de escala.

**Q75.** Com quanto tempo de antecedência a escala de um evento costuma ficar definida e comunicada à equipe?
*Por que importa:* define o prazo que o sistema precisa respeitar para notificações e confirmações de escala.

## 23. Clientes

**Q76.** Que tipo de cliente costuma voltar a comprar com frequência, e o que faz esse cliente voltar?
*Por que importa:* ajuda a desenhar o programa de fidelização e a segmentação de cliente no sistema.

**Q77.** De que forma fica registrado, hoje, o que cada cliente já comprou ou preferiu em eventos anteriores?
*Por que importa:* mostra a maturidade atual do relacionamento com o cliente e o que precisa ser recuperado/organizado.

**Q78.** Que tipo de cliente, hoje, dá mais trabalho ou prejuízo do que vale a pena atender, e por quê?
*Por que importa:* pode virar um critério de qualificação de Lead/Cliente dentro do sistema.

## 24. Pós-venda

**Q79.** Que tipo de contato, se houver, a empresa faz com o cliente depois que o evento acaba?
*Por que importa:* mostra se existe hoje um processo de pós-venda a formalizar ou se ele será criado do zero.

**Q80.** Como a empresa fica sabendo quando um cliente ficou insatisfeito?
*Por que importa:* define o canal e o processo que o sistema precisa capturar para tratar reclamações.

**Q81.** De que forma clientes satisfeitos costumam indicar a empresa para outras pessoas, e isso é acompanhado de alguma forma?
*Por que importa:* é a base para medir e incentivar indicação (referral) dentro do sistema.

## 25. Marketing

**Q82.** O que a empresa já fez, até hoje, para conseguir novos clientes (além de indicação espontânea)?
*Por que importa:* mapeia os canais reais de aquisição que o sistema precisa rastrear.

**Q83.** Existe alguém responsável por marketing hoje, ou isso é feito de forma esporádica por quem sobra tempo?
*Por que importa:* define o nível de maturidade e de automação que faz sentido propor nessa área.

**Q84.** Quanto a empresa gasta hoje em marketing, e quantos clientes novos isso costuma trazer, no que for possível estimar?
*Por que importa:* mostra se existe (ou não) qualquer medição de retorno sobre investimento em marketing.

## 26. Redes Sociais

**Q85.** Quais redes sociais a empresa usa hoje, e qual delas traz mais retorno percebido?
*Por que importa:* ajuda a priorizar futuras integrações de marketing do sistema.

**Q86.** Quem produz o conteúdo postado hoje, e com que frequência?
*Por que importa:* revela se há um processo de conteúdo estruturado ou informal, o que muda o tipo de apoio que o sistema deveria oferecer.

**Q87.** Fotos e vídeos de eventos já realizados são aproveitados de alguma forma para atrair novos clientes?
*Por que importa:* aponta uma oportunidade de conectar o histórico de Eventos ao portfólio de marketing.

## 27. Financeiro Pessoal

**Q88.** Como funciona, hoje, a separação entre o dinheiro da empresa e o dinheiro pessoal de quem administra o negócio?
*Por que importa:* essa separação é pré-requisito para qualquer indicador financeiro da empresa ser confiável.

**Q89.** Quais despesas pessoais, se houver, hoje são pagas com dinheiro da empresa (ou o contrário)?
*Por que importa:* se isso acontece, precisa de uma regra clara para não distorcer o resultado do negócio no sistema.

**Q90.** Como é definido, hoje, o valor retirado regularmente da empresa para sustento pessoal (pró-labore)?
*Por que importa:* esse valor precisa ser tratado como uma Despesa formal para o resultado da empresa não ficar distorcido.

## 28. Financeiro da Empresa

**Q91.** Como a empresa sabe, hoje, se um mês foi bom ou ruim financeiramente?
*Por que importa:* revela quais indicadores financeiros já fazem sentido para quem administra, mesmo sem sistema.

**Q92.** Quantas contas bancárias e quantos bancos a empresa usa hoje, e para que serve cada uma?
*Por que importa:* é a base do cadastro de Banco/Conta e da conciliação bancária no sistema.

**Q93.** Como é feito hoje o controle (mesmo informal) do que precisa ser pago e do que precisa ser recebido nos próximos dias/semanas?
*Por que importa:* mostra o ponto de partida real para o Fluxo de Caixa do sistema.

**Q94.** Qual evento ou produto a empresa acredita, hoje, que dá mais lucro, e qual dá menos — e como chegou a essa conclusão?
*Por que importa:* é exatamente a pergunta que o sistema (Ficha Técnica + Engenharia de Custos + Financeiro) precisa conseguir responder automaticamente no futuro.

## 29. Investimentos

**Q95.** Quais foram os investimentos mais importantes que a empresa já fez para crescer (equipamento, veículo, reforma, pessoal), e o que foi decisivo em cada decisão?
*Por que importa:* revela o critério de decisão de investimento hoje, que pode ser apoiado por indicadores do sistema no futuro.

**Q96.** Quais investimentos a empresa gostaria de fazer, mas ainda não conseguiu ou não teve certeza se valeria a pena?
*Por que importa:* pode virar um caso de uso concreto para simulações e indicadores do Dashboard CEO.

## 30. Indicadores

**Q97.** Quais números a empresa acompanha hoje, mesmo que de cabeça ou em uma planilha simples (faturamento, quantidade de eventos, outro)?
*Por que importa:* é o ponto de partida real dos Indicadores que o Dashboard CEO vai exibir.

**Q98.** Que pergunta sobre o negócio a empresa gostaria de conseguir responder hoje e não consegue?
*Por que importa:* essa é, provavelmente, a funcionalidade de maior valor percebido a ser priorizada no sistema.

## 31. Dashboards

**Q99.** Se a empresa pudesse ver, todos os dias, uma única tela com os números mais importantes do negócio, o que precisaria estar nela?
*Por que importa:* é a definição direta do conteúdo do Dashboard CEO.

**Q100.** Quem, além do proprietário, precisaria ver informações do negócio no dia a dia, e o que cada um precisaria ver especificamente?
*Por que importa:* define se serão necessários dashboards diferentes por função/área, além do Dashboard CEO.

## 32. Inteligência Artificial

**Q101.** Quais tarefas repetitivas ou demoradas, hoje, a empresa gostaria que fossem feitas automaticamente por um assistente inteligente?
*Por que importa:* aponta o primeiro caso de uso real de IA a priorizar, em vez de aplicar IA de forma genérica.

**Q102.** Quais ferramentas de inteligência artificial a empresa já usou no dia a dia (mesmo um chat de IA para escrever textos), e como foi essa experiência?
*Por que importa:* mede o nível de familiaridade e confiança da equipe com IA, o que afeta como ela deve ser introduzida no sistema.

## 33. Automações

**Q103.** Qual tarefa manual, hoje, consome mais tempo da equipe sem realmente precisar de julgamento humano?
*Por que importa:* é o melhor candidato a ser automatizado primeiro no sistema.

**Q104.** Quais automações simples (lembrete automático, mensagem padrão, planilha com fórmula), mesmo improvisadas, já são usadas hoje?
*Por que importa:* mostra que tipo de automação a equipe já valoriza e usaria se estivesse dentro do sistema.

## 34. Crescimento Futuro

**Q105.** Como a empresa imagina sua operação daqui a 5 anos — mesma unidade maior, novas unidades, franquia, outro formato?
*Por que importa:* essa visão orienta diretamente a Filosofia de Evolução já definida no Framework (Seção 25).

**Q106.** Qual é o principal obstáculo que hoje impede a empresa de crescer mais rápido?
*Por que importa:* pode revelar que a maior barreira de crescimento é operacional/de sistema, e não comercial.

**Q107.** Se a empresa abrisse uma segunda unidade amanhã, o que hoje é feito "de cabeça" que precisaria, obrigatoriamente, estar escrito e padronizado antes disso?
*Por que importa:* é a pergunta mais direta para identificar o que falta documentar antes de replicar o negócio.

## 35. Sonhos e Objetivos da Empresa

**Q108.** Qual é o maior objetivo pessoal de quem comanda a empresa em relação a esse negócio?
*Por que importa:* alinha o propósito do sistema (Missão do Manifesto) com o propósito real de quem o está construindo.

**Q109.** Se o THE CHARCOAL OS funcionasse perfeitamente desde o primeiro dia, o que mudaria na rotina de quem comanda a empresa?
*Por que importa:* é a melhor forma de descobrir o verdadeiro critério de sucesso do projeto, na visão do proprietário.

**Q110.** O que mais o proprietário considera importante sobre este negócio que ainda não foi perguntado em nenhum documento até agora?
*Por que importa:* garante um espaço aberto para qualquer informação crítica que o questionário não tenha antecipado.

---

## Resumo do Questionário

- **Quantidade total de perguntas:** 110
- **Quantidade de categorias:** 35
- **Estimativa de cobertura do negócio:** aproximadamente **85%**. As respostas completas devem cobrir a maior parte do que é necessário para desenhar um ERP verdadeiramente personalizado; o restante depende de detalhes que só aparecem depois que as respostas iniciais são dadas (efeito cascata natural de descoberta).
- **Áreas que ainda poderão precisar de aprofundamento após as respostas:**
  - Levantamento **linha a linha** das Receitas e Fichas Técnicas reais (este questionário identifica se elas existem e como são geridas, mas não substitui documentá-las por completo).
  - Exigências regulatórias específicas (vigilância sanitária, alvarás de evento, obrigações trabalhistas) aplicáveis à operação real.
  - Estrutura societária e organograma detalhado, caso mais de uma pessoa tenha papel de decisão na empresa.
  - Condições contratuais detalhadas com fornecedores-chave (para eventual módulo de contratos de compra).
  - Modelo jurídico/operacional de franquia, caso a resposta à Q105 confirme esse caminho de crescimento.
  - Inventário técnico de ferramentas/planilhas atualmente em uso, para planejamento de migração de dados (fase técnica futura).

---

*Fim do documento — THE CHARCOAL OS BUSINESS DISCOVERY QUESTIONNAIRE v1.0.0*
