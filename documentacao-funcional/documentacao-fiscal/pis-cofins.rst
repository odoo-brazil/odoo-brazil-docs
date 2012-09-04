PIS e COFINS: A forma de cobrança desses dois impostos é bem semelhante. São poucos os casos em que a empresa é isenta de um deles. A história do PIS/COFINS é bem curiosa: o Governo instituiu esses dois impostos com o objetivo de cobrir as despesas com o Plano de Integração Social e as despesas com a previdência e saúde. Aplicou o imposto sobre todo e qualquer tipo de faturamento, estabelecendo as alíquotas de 0,65% e 3%. Para as empresas que não tem faturamento, como certas associações, tributou em 1% a folha de pagamento. 

A grita geral foi causada principalmente pelo forte impacto que a cumulatividade desses impostos

proporcionava, gerando um grande aumento nos custos do produto quando é grande a cadeia de distribuição. Num dos seus últimos atos, o Governo FHC resolveu permitir o crédito do imposto, à semelhança do ICMS e do IPI. Para compensar, no entanto, aumentou as alíquotas, passando-as para 1,65% e 7,6%, respectivamente. Aí a grita veio das empresas de serviço, que tem pouca despesa com notas de compra que permitiriam o crédito, pois o grosso das despesas se concentra na Folha de Pagamento. E foi assim que possibilitou a opção de as empresas que estão no Lucro Presumido poderem escolher entre a opção cumulativa com alíquotas menores (0,65% e 3%)

ou a opção não-cumulativa (1,65% e 7,6%). Mais uma vez foi gerada a dúvida do que pode ou não pode ser creditado. E alem disso, prejudicando inclusive a arrecadação do Governo, as empresas de Lucro Real e outras que se enquadrarem na opção não-cumulativa se creditam do PIS e COFINS das Notas de Compra sempre multiplicando o valor da nota pelas alíquotas de 1,65% e 7,6%, mesmo tendo elas pago com as alíquotas menores, inclusive se forem do SIMPLES. 
INSS: A CPP (Contribuição Previdenciária Patronal) que é a parte da empresa que deve ser paga, incide sobre a folha de pagamento, abrangendo praticamente todas as verbas. São 20% sobre o total, sem teto, e mais de 1% a 7% de outras contribuições a terceiros (SESI, SENAI, SEBRAE, Salário Educação, Incra, etc). Recentemente, depois de muita luta por parte das entidades de classe, o Governo alterou a forma de cobrança deste imposto, utilizando como base para a cobrança do INSS o Faturamento. Fez isso em apenas quatro segmentos, para ver se

a experiência dará certo. Os segmentos selecionados foram calçados, têxtil e moveis, com a alíquota de 1,5% e software com a alíquota de 2,5%. 

PROCESSO FISCAL: O Processo Fiscal tem como objetivo gerar automaticamente, quando da

digitação das Notas Fiscais de Compras e de Faturamento, o CFOP e o CST. Esses campos são definidos a partir de uma série de Propriedades definidas nas tabelas de Clientes, Produtos, Empresa, NCM, Cabeçalho das Notas e Itens das Notas, sejam de Entrada sejam de Saída. Para cada Propriedade são definidas Opções. As Propriedades e as Opções são definidas em Cadastros/Configurações Fiscais/Propriedades Fiscais. Cabe ao usuário definir as Propriedades e Opções de sua empresa, devendo concentrar-se apenas em situações que realmente ocorram no

seu dia-a-dia. A partir do CST os programas definem as alíquotas, se a compra dá direito à crédito e outros detalhes do cálculo do imposto. 

Em Cadastros/Configurações Fiscais/Regras Fiscais são definidos os CFOPs e CFT do ICMS, IPI, PIS e Cofins. 
Para cada Opção de cada Propriedade define-se os CFOPs que podem nela ocorrer. Nos respectivos Cadastros e

nas Notas há uma aba onde se definem as Opções das Propriedades daquela entidade. No momento em que se digita uma Nota, é verificar as definições do Cliente, Produto, Empresa, NCM, Cabeçalho e Item da Nota que está sendo digitada e cruza os CFOPs indicados. No momento em que em uma Opção determinado CFOP não constar da lista, ele é eliminado. E assim vai o Processo, até testar todas as Propriedades. 

No final o ideal é que sobre apenas um CFOP, o qual será apresentado no respectivo campo. Caso não sobre nenhum, cabe ao Usuário digitá-lo. Caso sobre mais que um é apresentado um Combo-box para que o Usuário indique qual o correto. Na prática, cabe ao Usuário ir aprimorando o Processo, através da criação de novas Propriedades e Opções que se encaixem em sua realidade, para que sempre sobre apenas um CFOP, automatizando o trabalho de quem digita as Notas. É natural que aqueles casos especiais que ocorrem com extrema raridade vão sempre aparecer em branco para que o Operador o digite. Cobrir todas as alternativas é praticamente impossível, devido a grande variedade de CFOPs existentes. O Processo é repetido para os diversos

CST e a partir daí define as alíquotas de cada tributo, lembrando que na seleção do CST usa-se o

próprio CFOP como sendo uma Propriedade. 