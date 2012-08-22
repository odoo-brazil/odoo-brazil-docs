*********************
Começando com OpenERP
*********************

Agora você vai explorar o banco de dados \ ``openerp_ch02``\   com estes módulos instalados em seu perfil para dar
lhe uma perspectiva sobre a cobertura do software OpenERP core.

.. tip:: Traduzindo Módulos novos

	Quando você tiver instalado um novo módulo e estiver usando idiomas adicionais com Inglês, você tem que recarregar
o arquivo de tradução. Novos termos introduzidos nesses módulos não são traduzidos por padrão. para fazer
este uso :menuselection:`Administration --> Translations --> Load an Official Translation`.

Dependendo do usuário que se está conectado, a página aparece de forma diferente.
Usando a sequência de instalação acima, painéis de controle determinados podem ser atribuídos como várias
páginas dos usuários. Eles mostram um resumo das informações necessárias para começar o dia de forma eficaz. o
painel do projeto pode conter:

* uma lista das tarefas a realizar,

* uma lista das tarefas a que é atribuído ao usuário atual,

* uma lista de sprints,

* uma lista de questões atribuídas ao usuário atual,

* um gráfico de horas planejados vs total,

* um gráfico de horas restante pelo Projeto,

* um gráfico de Questões em aberto por data de criação.

Cada uma das listas podem ser reordenadas simplesmente clicando no título de uma coluna – primeiro em ordem crescente, em seguida, em ordem decrescente à medida que você clica repetidamente. Para obter mais informações sobre qualquer entrada particular, clique sobre o nome na primeira coluna, ou se você quiser mostrar um painel específico, clique :guilabel:`Zoom` above it.

.. figure:: images/admin_project_dashboard.png
   :align: center
   :scale: 65

   *Painel do Projeto*

A página de usuário é automaticamente reatribuída durante a criação ou melhoria de um banco de dados. é
costuma-se atribuir um painel para à home page, mas qualquer tela OpenERP pode ser atribuído à
home page de qualquer usuário.

.. index::
   single: shortcut

.. tip:: Criando atalhos

	Cada usuário tem acesso a muitos itens de menu a partir do menu. mas, em
geral, um funcionário usa apenas uma pequena parte das funções do sistema.

	Para que você possa definir atalhos para os menus mais utilizados. Esses atalhos são pessoais para cada usuário. para
criar um novo atalho, basta clicar no "*" do cabeçalho da visão no cliente web.

	Para remover um atalho basta clicar no link e clique novamente em "*" do cabeçalho da visão.

As seções seguintes apresentam uma visão geral das principais funções do OpenERP. Algumas áreas são
abordadas com mais detalhes nos próximos capítulos deste livro, e você vai encontrar muitas outras funções
disponíveis nos módulos opcionais. As funções são apresentadas na ordem em que aparecem na principal
menu.

Conceitos básicos
=================

.. index::
   single: Partners

Parceiros e contatos
^^^^^^^^^^^^^^^^^^^^

Para se familiarizar com a interface do usuário do OpenERP, você vai começar a trabalhar com informações sobre
parceiros. clicando :menuselection:`Sales --> Address Book --> Clientes exibem uma lista de parceiros que foram
carregados automaticamente quando você criou o banco de dados com :guilabel:`Load Demonstration Data` checado.

.. index::
   single: partner; search

Pesquisar um parceiro
^^^^^^^^^^^^^^^^^^^^^

Acima da lista de parceiros, você verá um formulário de pesquisa que lhe permite filtrar rapidamente os parceiros.

O filtro \ ``Customers`` \ é ativado por padrão mostrando parceiros que são clientes. Se você não tiver aplicado nenhum filtro, a lista mostra todos os parceiros no sistema. Por razões de espaço, essa lista mostra apenas os primeiros parceiros alguns. Se você deseja exibir outros registros, você pode procurá-los ou navegar através de toda a lista usando as setas :guilabel:`First`, :guilabel:`Previous`, :guilabel:`Next`, :guilabel:`Last`.

.. figure:: images/partner_search_tab.png
   :scale: 75
   :align: center

   *Procura de parceiros padrão*

.. note:: Limite das listas

	Po padrão, a lista no cliente GTK mostra apenas os primeiros 80 registros, para evitar sobrecarregar a
rede e do servidor.

	Mas você pode alterar esse limite, clicando no elemento de seleção (mostrando 80 por padrão) à
	direita de os critérios de pesquisa.

	Da mesma forma, a lista no cliente web mostra apenas os primeiros 20, 50, 100, 500 ou registros ilimitados.

	O número real pode ser ligado, clicando no link entre os botões ANTERIOR e PRÓXIMO
	e selecionando um dos outros limites.

Na versão web, se você clicar no nome de um sócio, a forma de visão correspondente a esse parceiro abre em modo Read-Only.
Na lista você pode alternativamente clicar no ícone do lápis para abrir o mesmo formulário no modo Editar.
Uma vez que você tem um formulário, você pode alternar entre os dois modos, clicando :guilabel:`Save` or :guilabel:`Cancel` quando em
modo de edição e :guilabel:`Edit` quando em modo Read-Only.

.. index::
   single: parceiro; visão de formulário

Formulário de parceiro
^^^^^^^^^^^^^^^^^^^^^^

O formulário de parceiro contém várias guias, todos referentes ao registro atual:

*  :guilabel:`General`,

*  :guilabel:`Sales & Purchases`,

*  :guilabel:`Accounting`,

*  :guilabel:`History`,

*  :guilabel:`Notes`.

Os campos em uma aba não são todos do mesmo tipo – alguns (tal como as :guilabel:`Name`) contêm texto livre
, alguns permitem que você selecione um valor de uma lista de opções (tais como o :guilabel:`Language`),
ooutros dão-lhe uma visão de outro objeto (such as :guilabel:`Partner Contacts` – porque um parceiro
pode ter vários contatos) ou uma lista de links para um outro objeto (tal como :guilabel:`Partner Categories`).
Há caixas de seleção (tal como campo :guilabel:`Active` na aba :guilabel:`Sales & Purchases`),
campos numéricos (como o  :guilabel:`Credit Limit` na aba :guilabel:`Accounting` ) e campos de data (tal como :guilabel:`Date`).

A aba :guilabel:`History` dá uma visão geral das atividades dos parceiros – uma visão geral de informações úteis, tais como leads e oportunidades, reuniões, telefonemas, e-mails e tarefas. Eventos são gerados automaticamente pelo OpenERP, apartir de mudanças em outros documentos que se referem a este parceiro.

É possível adicionar eventos manualmente que se relacionam diretamente com o formulário correspondente, tal como uma nota a gravação de um telefonema. Para adicionar um novo evento, clique :guilabel:`New` na seção :guilabel:`Phone Calls`. Que abre um novo pop-up :guilabel:`Phone Call` de formulário permitindo um evento telefonema a ser criado e adicionado ao parceiro atual.

Possíveis ações do parceiro
^^^^^^^^^^^^^^^^^^^^^^^^^^^

À direita do formulário de sócio é uma barra de ferramentas contendo uma lista de possíveis :guilabel:`Reports` ,
:guilabel:`Actions` e rápido:guilabel:`Links` sobre o parceiro exibido no formulário.

YVocê pode gerar documentos PDF para o objeto selecionado (ou, na visão de lista, cerca de um ou mais
objetos selecionados) usando os botões certos na seção :guilabel:`Reports`  da barra de ferramentas:

*  :guilabel:`Labels` : imprimir etiquetas de endereço para os parceiros selecionados,

*  :guilabel:`Overdue Payments` : imprimir uma carta para notificar os parceiros selecionados de pagamentos em atraso,

Certas ações podem ser iniciados pelos os seguintes botões na seção :guilabel:`Actions` da
barra de ferramentas:

*  :guilabel:`SMS Send`: permite-lhe enviar um SMS para os parceiros selecionados. Este sistema utiliza a maior parte
   Serviços de SMS da empresa ® Clickatell http://clickatell.com,

*  :guilabel:`Mass Mailing`: permite que você envie um email para uma seleção de parceiros,

*  :guilabel:`Create Opportunity`: abre uma janela para criar uma oportunidade para o parceiro.

.. index::
   single: buttons; reports, actions, links

.. tip:: Relatórios, links e ações no cliente GTK

	Quando você estiver visualizando um formulário no cliente GTK, os botões à direita do formulário são atalhos para
os mesmos relatórios, links e ações conforme descrito no texto. Quando você estiver visualizando uma lista (tais como
a lista de parceiros), os botões não estão disponíveis para você. Em vez disso, você pode alcançar Relatórios e Ações
através de dois dos botões na barra de ferramentas no topo da lista – Impressão e ação.

Parceiros são usados ​​em todo o sistema OpenERP em outros documentos. Por exemplo, o menu
:menuselection:`Sales --> Sales Orders` traz à tona todas as pedidos de vendas na visão em lista. Abra um pedido na visão em formulário e clique no nome de um parceiro, mesmo quando o formulário é somente de leitura. O formulário de parceiro será aberto.

.. tip:: Clique no botão direito do mouse e atalhos

	No cliente GTK você não tem hyperlinks para outros tipos de documentos. Em vez disso, você pode clicar botão direito do mouse em
uma visão em lista para mostrar os campos relacionados nessa linha(que é campos tendo um link para outras formas).

	No cliente web você verá atalhos hiperlink em vários dos campos em um formulário em modo de leitura
apenas , permitindo que você seja levado diretamente para o formulário correspondente. Quando o formulário web é no modo de edição,
	você pode em vez de clicar o com o botão direito do mouse
	no campo, para obter todos os campos ligados em um menu pop-up como se fosse com o GTK
	cliente.

	Você pode rapidamente tentar dar um presente, vá a qualquer uma das ordens de vendas em :menuselection:`Sales
	--> Sales Orders`. Veja onde você pode vão desde o campo
	:guilabel:`Customer` usando o cliente na web com a forma em
	ambos só no modo de leitura e de edição, ou com o cliente GTK.

.. figure:: images/familiarization_sale_partner.png
   :scale: 85
   :align: center

   *Links para um parceiro aparecem em um formulário de pedido*

Antes de passar para o próximo tópico, dê uma olhada rápida no menu :menuselection:`Sales -->
Configuration --> Address Book`, particularmente :menuselection:`Partner Categories`  e no menu  :menuselection:`Localisation`.
Eles contêm alguns dos dados de demonstração que você instalou quando você criou o banco de dados.

Produtos
--------

No OpenERP, `product` é usado para definir uma matéria-prima, um produto armazenável​​, um consumível ou um serviço. Você poderá
trabalhar com produtos inteiros ou com modelos que separam a definição dos produtos e suas variantes (*módulo extra*).

Por exemplo, se você vender camisetas em diferentes tamanhos e cores:

* the product template is the “T-shirt” which contains information common to all sizes and all
  colors,

* o modelo do produto é a "Camiseta", que contém informação comum a todos os tamanhos e todos as
   cores,

* Ele produto final é, assim, a combinação dos dois – Camisetas no tamanho S e cor vermelha.

O valor desta abordagem, para alguns setores, é que você pode apenas definir um modelo em detalhes e todos os
de suas variantes disponíveis brevemente, ao invés de cada item como um produto inteiro.

	.. note::  *Exemplo Modelos de Produto e Variantes*

			Um produto pode ser definido como um todo ou como um modelo de produto e diversas variantes. as variantes
			podem ser em uma ou várias dimensões, dependendo dos módulos instalados.

			Por exemplo, se você trabalha no sector dos têxteis, as variantes do modelo de produto para “Camiseta” será:

			* Tamanho (XS, S, M, G, GG),

			* Cor (branco, cinza, preto, vermelho),

			* Qualidade do Tecido (125g/m2, 150g/m2, 160g/m2, 180g/m2),

			* Gola (V, Redonda).

			.. index::
			   single: module; product_variant_multi

			Esta separação de tipos de variante requer o módulo opcional :mod:`product_variant_multi`.
			Usá-lo
			significa que você pode evitar uma explosão no número de produtos para gerenciar no banco de dados.Se você
			tomar o exemplo acima, é mais fácil de gerir um modelo com 15 variantes em quatro tipos diferentes
			de 160 produtos completamente diferentes. Este módulo está disponível em ``extra-addons``.

O menu :menuselection:`Sales --> Products` lhe dá acesso à definição de produtos e seus modelos e variantes.

.. index::
   single: Product; Consumable

.. tip::  Consumíveis

	No OpenERP, um consumível é um produto físico, que é tratado como um produto armazenável​​, com exceção
	que a gestão de estoque não é levada em conta pelo sistema. Você poderia comprá-lo, entregá-lo ou
	produzi-lo, mas o OpenERP sempre vai assumir que há o suficiente em estoque. Nunca acione uma
	exceção de aquisição

Abra um formulário de produto para ver as informações que o descreve. Os dados mostram vários tipos de demonstração de produtos, o que dá uma visão muito boa das opções.

Listas de preço (:menuselection:`Sales --> Configuration --> Pricelists`) determinam os preços de compra e venda e
ajustes decorrentes do uso de diferentes moedas. 
O :menuselection:`Default Purchase
Pricelist` usa os produtos do campo :guilabel:`Cost Price` para o preço de compra a ser calculado. O
:menuselection:`Public Pricelist` usa os produtos do campo :guilabel:`Sale Price`  para calcular o preço de vendas nas cotações.

Listas de preços são extremamente flexíveis e permitem que você coloque uma política de gestão completa de preços no local.
Eles são compostos de regras simples que lhe permitem construir um conjunto de regras para a maioria das situações complexas:
descontos múltiplos, preços de venda com base nos preços de compra, a redução dos preços, promoções em gamas de produtos e assim por diante.

Você pode encontrar muitos módulos opcionais para ampliar a funcionalidade do produto, como:

.. index::
   single: module; membership

* :mod:`membership` : para gerenciar as assinaturas de membros de uma empresa,

  .. index::
     single: module; product_electronic

* :mod:`product_electronic` : para o gerenciamento de produtos eletrônicos,

  .. index::
     single: module; product_extended

* :mod:`product_extended` : para o gerenciamento de custos de produção,

  .. index::
     single: module; product_expiry

* :mod:`product_expiry` : de produtos agro-alimentares, onde os itens devem ser aposentado depois de um certo
   período,

  .. index::
     single: module; product_lot_foundry

* :mod:`product_lot_foundry` : para o gerenciamento de produtos de metal forjado.

todos os módulos acima são encontrados em ``extra-addons``, exceto para o :mod:`membership` e o módulo :mod:`product_expiry`.

.. index::
   single: CRM
   single: Customer Relationship Management
   single: SRM
   single: Supplier Relationship Management
..

Aumentar suas vendas
====================

OpenERP fornece muitas ferramentas para gerenciar relacionamentos com parceiros. Estas informações estão disponíveis através do
menu :menuselection:`Sales`.

.. tip::  :guilabel:`CRM & SRM`

	``CRM`` significa Gestão Relacionamento com o Cliente,um termo padrão para sistemas que gerenciam clientes e
	relações com os clientes. ``SRM`` significa Gestão de Relacionamento com Fornecedores, e é comumente usado para
	funções que gerenciam suas comunicações com os seus fornecedores.

Através da Gestão Relacionamento com o Cliente, OpenERP permite que você mantenha o controle de:

* Leads
* Oportunidades
* Reuniões
* Chamadas telefônicas
* Reclamações
* Helpdesk e Suporte
* Captação de Recursos

OpenERP garante que cada caso seja tratado de forma eficaz pelo sistema de usuários, clientes e
fornecedores. Ele pode automaticamente reatribuir um caso, segui-lo para o novo proprietário, enviar lembretes por e-mail
e levantar a documentação OpenERP e outros processos.

ATodas as operações são arquivados, e um gateway de e-mail permite que você atualize automaticamente um caso de e-mails
enviados e recebidos. Um sistema de regras permite que você configure ações que podem melhorar automaticamente
sua qualidade de processo, garantindo que nunca abra casos de *Atenção* fuga.

Bem como aquelas funções, você tem as ferramentas para melhorar a produtividade de todos os funcionários em suas atividades diárias de
trabalho:

* um plugin para o cliente de email Outlook e Firefox que lhe permite armazenar automaticamente seus e-mails e seus anexos na
Gestão de conhecimento (anteriormente Sistema de Gestão Documental) integrado com OpenERP,

* interfaces para sincronizar seus contatos e calendários com OpenERP,

* sincronizar as suas reuniões em seu telefone móvel,

* construir uma visão de 360 ​​° em seu cliente,

* integração com aplicativos do Google.

Você pode implementar uma política de melhoria contínua para todos os seus serviços, utilizando algumas das
ferramentas estatísticas em OpenERP, para analisar os diferentes comunicações com seus parceiros. Com
estes, você pode executar uma política de melhoria real para gerenciar sua qualidade de serviço.

A gestão de relacionamento com os clientes é detalhada na segunda seção deste livro (veja
:ref:`part2-crm`).

.. index::
   single: Gestão de Vendas


.. index::
   single: Contabilidade e Finanças
   single: Gestão Financeira

Gerenciar seus Livros
=====================

Os capítulos :ref:`part-genacct` neste livro são dedicados à contabilidade geral e analítica.
Que se segue é um breve resumo das funções para apresentar-lhe este aplicativo de negócios.

A Contabilidade é totalmente integrada em todas as funções da empresa, se é geral,
contabilidade, analítica orçamentais ou auxiliar.A função de contabilidade OpenERP é de dupla entrada e
suporta múltiplas divisões da empresa e várias empresas, bem como várias moedas e
línguas.

Contabilidade que está integrada em todo todos os processos da empresa simplifica muito o trabalho
de inserção de dados contábeis, porque a maioria das entradas são geradas automaticamente, enquanto outros
documentos estão sendo processados. Você pode evitar a introdução de dados duas vezes no OpenERP, que é geralmente um
fonte de erros e atrasos.

Então a contabilidade OpenERP não é apenas para os relatórios financeiros – é também o ponto de âncora para muitos
dos processos de gestão da empresa. Por exemplo, se um de seus contadores coloca um cliente para
manter crédito, então, que irá imediatamente bloquear qualquer outra ação relacionada ao crédito daquela empresa (tal
como vendas ou entrega).

OpenERP também fornece contabilidade analítica integrada, que permite o gerenciamento por parte das empresas
atividade ou projeto e fornece níveis muito detalhados de análise. Você pode controlar suas operações
com base nas necessidades de gestão de negócios, ao invés de nas paradas de contas que geralmente atendem somente
exigências legais.

OpenERP adicionou um flexível, e facil módulo **Invoicing** permitindo-lhe manter o controle de seus documentos e pagamentos, mesmo quando você não é um contabilista. Isso permitirá que empresas menores, mantenham o controle de seus pagamentos sem a necessidade de implementar um sistema de contabilidade completo.

Manter o controle de Movimentação do dinheiro usando o OpenERP Cash Box

.. index::
     single: Recursos Humanos
     single: HR

Lead e Inspirar o seu Povo
==========================

A aplicão de negócios, Gestão de Recursos Humanos do OpenERP fornece a funcionalidade, tais como:

* Gerenciar seus funcionários, Contratos e desempenho do pessoal,

* Aquisição de talentos,

* Manter o controle de férias e licenças por doença,

* Gerenciar o processo de avaliação,

* Manter o controle de Atendimentos e o quadros de horários,

* Acompanhar Despesas. 

.. index::
   single: modules; hr_
   single: module; hr

A maioria destas funções são fornecidos a partir de módulos opcionais cujo nome começa com \ ``hr_`` \
em vez do módulo central :mod:`hr`, mas todos eles são carregados no principal principais :menuselection:`Human
Resources`.

As diferentes questões são tratadas em detalhe na quarta parte deste livro :ref:`part-ops`, dedicado a interna
organização e à gestão de uma empresa de serviços.

.. index::
   single: gestão de projeto
   single: projeto

Conduza o seu Projeto
=====================

As ferramentas de gerenciamento de projetos do OpenERP, permitem que você defina tarefas e especifique os requisitos para essas tarefas, alocação eficiente de recursos para os requisitos, projeto de planejamento, programação e comunicação automática com os parceiros.

Todos os projectos são hierarquicamente estruturados. Você pode analisar todos os projetos no menu :menuselection:`Project --> Projects`. Em seguida, selecione :guilabel:`Gantt view` para obter uma representação gráfica do projeto.

.. figure:: images/project_gantt.png
   :scale: 65
   :align: center

   *Planejamento de Projeto*

Você pode executar projetos relacionados a serviços ou suporte, Produção ou Desenvolvimento – é um universal
módulo para todas as necessidades da empresa.

Gerenciamento de projetos é descrito no :ref:`ch-projects`.

.. index::
   single: vendas

Conduzindo suas vendas
======================

O menu :menuselection:`Sales` dá-lhe mais ou menos a mesma funcionalidade que o menu :menuselection:`Purchases`  – a capacidade de criar novos pedidos e para revisar os
pedidos existentes em seus vários estados – mas há diferenças importantes nos fluxos de trabalho.

Confirmação de um pedido desencadeia a entrega de mercadorias, e tempo de faturamento é definida por um
definição em cada pedido individual.

Taxas de entrega podem ser gerenciados usando uma grade de tarifas de operadoras diferentes.

.. index::
   single: compra
   single: gestão de compras

Conduzindo suas compras
=======================

:menuselection:`Purchases` permite que você acompanhe as cotações de seus fornecedores preços e convertê-los em
Pedidos de compra como quiser. OpenERP tem vários métodos de faturas monitoramento e rastreamento
o recebimento de mercadorias encomendadas.

Você pode lidar com entregas parciais em OpenERP, assim você pode manter o controle de itens que ainda estão a ser
emitidas em seus pedidos, e você pode emitir lembretes automaticamente.

As regras de gestão de reposição do OpenERP, permite que o sistema gere projetos de pedidos de compra
automaticamente, ou você pode configurá-lo para executar um processo lean, conduzido inteiramente por produção atual
necessidades.

Você também pode gerenciar as requisições de compra para manter o controle de cotações enviadas para um grande número de fornecedores.

.. index::
   single: estoque
   single: gestão de armazéns

Organize o seu Armazém
======================

Os vários sub-menus sob :menuselection:`Warehouse` juntos, oferecem operações que você precisa para gerenciar estoque.
Você pode:

* definir seus armazéns e estruturá-los em torno de locais que você escolher,

* gerenciar níveis de estoque de rotação e de ações,

* executar os pedidos de embalagem gerados pelo sistema,

* executar as entregas com notas de entrega e calcular as taxas de entrega,

* gerenciar lotes e números de série para rastreabilidade,

* calcular os níveis de estoque teórico e automatizar avaliação de ações,

* criar regras para reposição de estoque automático.

Pedidos de embalagem e as entregas são geralmente definidas automaticamente pelo cálculo com base em requisitos
vendas. Lojas pessoal usam listas de picking  gerada pelo OpenERP, produzida automaticamente por pedido de
prioridade.

Gestão de estoques é, como entrada dupla de contabilidade. Assim, ações não aparecem e desaparecem num passe de mágica
dentro de um armazém, eles apenas são movidos de lugar para lugar. E, assim como a contabilidade, como uma
de dupla entrada sistema dá-lhe grandes vantagens quando você vem a auditoria das ações, porque cada item em falta
tem uma contrapartida em algum lugar.

A maioria dos softwares de gerenciamento de estoque é limitado a geração de listas de produtos em armazéns. por causa de
seu sistema de dupla entrada, OpenERP gerencia automaticamente estoques de clientes e fornecedores, bem como, que
tem muitas vantagens: a rastreabilidade completa do fornecedor ao cliente, gestão de estoque consignado,
e análise de movimentos de ações de contrapartida.

Além disso, assim como contas, ações locais são hierárquicos, para que você possa realizar análises em
vários níveis de detalhe.


.. index::
   single: Gestão da Produção
   single: Manufatura

Obter manufatura concluída
==========================

A gestão de produção do OpenERP possibilita as empresas possam planejar, automatizar e controlar de fabricação e montagem de produtos. OpenERP suporta multi-nível de listas de materiais e permite substituir subconjuntos de forma dinâmica, no momento da venda de ordenação. Você pode criar virtuais subconjuntos para reutilização em diversos produtos com contas fantasmas de materiais.

.. index::
   single: bill of materials
   single: BOM

.. note:: BOMs, roteamento, centros de trabalho

	Esses documentos descrevem os materiais que compõem um conjunto maior. Eles são comumente chamados
Listas de materiais ou BOMs.

	Eles estão ligados a rotas que lista as operações necessárias para realizar a fabricação ou
montagem do produto.

	Cada operação é realizada em um centro de trabalho, que pode ser uma máquina ou uma pessoa.

Pedidos de produção com base nas necessidades da sua empresa são agendadas automaticamente pelo sistema,
mas você também pode executar o agendador manualmente sempre que quiser. Os pedidos são trabalhados por meio do cálculo
os requisitos de vendas, através de listas de materiais, tendo em conta estoque atual. O
cronograma de produção também é gerado a partir dos tempos de lead diferentes definidos ao longo do sistema, usando a mesma
rota.

Os dados de demonstração contêm uma lista de produtos e matérias-primas com várias classificações
e intervalos. Você pode testar o sistema usando esses dados.

.. index::
   single: conhecimento
   single: documento
   single: FTP
   single: Gestão de Documento
   single: calendário
   single: CalDAV

Compartilhe o seu conhecimento através da Gestão de Documentos, eficiente e móvel
=================================================================================

OpenERP integra um sistema completo de gestão de documentos que não só
realiza as funções de um DMS padrão, mas também se integra com todos os
do seu sistema gerado de documentos, como faturas e citações. Além disso,
ele mantém tudo isto sincronizado. Você pode definir sua própria estrutura de diretórios e dizer ao OpenERP para armazenar automaticamente documentos como facturas na DMS.

OpenERP fornece uma interface de FTP para o Sistema de Gerenciamento de Documentos. Você não só será capaz de acessar documentos de OpenERP, mas você também pode usar um sistema de arquivos regular com o cliente FTP.
FTP é apenas uma maneira de obter acesso aos arquivos sem a necessidade de usar um cliente OpenERP, para permitir que você acesse arquivos de qualquer lugar.
Você também pode adicionar documentos a serem armazenados em OpenERP diretamente através do sistema de FTP no diretório OpenERP correspondente. Estes documentos serão automaticamente acessíveis a partir do formulário em causa no OpenERP.

O conhecimento do sistema também é bem integrado com clientes de email como o Firefox eo Outlook. Ele também permite que você sincronize seus calendários (CalDAV).

.. index::
   single: painéis de controle

Medir o seu desempenho nos negócios
===================================

Para medir o seu desempenho empresarial OpenERP, fornece dois recursos interessantes:

* Painéis de controle
* Relatórios Estatísticos

Em uma única página, os painéis de controle lhe dão uma visão geral de toda a informação que é importante para você.
Em OpenERP, cada aplicativo tem seu próprio painel que se abre por padrão quando você selecionar o aplicativo específico.
Por exemplo, `Painel de controle da administração` será aberta quando você clicar no menu :menuselection:`Administration`.

.. note:: Painéis de controle

	Diferentemente da maioria dos outros sistemas ERP e estatística base clássica dos sistemas,
	OpenERP pode fornecer painéis para todos os usuários do sistema, e não apenas para gerentes e contadores.

	Cada usuário pode ter seu próprio painel, adaptado às suas necessidades,
	permitindo-lhe gerir o seu próprio trabalho de forma 		eficaz.
	Por exemplo, um desenvolvedor usando o :guilabel:`Project Dashboard` pode ver tais informações
	como uma lista de tarefas aberto, tarefas delegadas a ele e uma análise do progresso da
	os projetos relevantes.

Dashboards são dinâmicos, permitindo que você navegue facilmente ao redor da inteira base de informações.
Usando os ícones acima de um gráfico, por exemplo, você pode filtrar os dados ou fazer zoom no gráfico. Você pode
clicar em qualquer elemento da lista para obter estatísticas detalhadas sobre o elemento selecionado.

Painéis podem ser personalizados para atender às necessidades de cada usuário e cada empresa.

.. note:: Criar ou personalizar painél de controle

	OpenERP contém um editor de painél de controle. Crie seu próprio painél para atender às suas
	necessidades específicas em apenas alguns cliques. Vá para o menu :menuselection:`Administration --> Customization --> Reporting --> Dashboard Definition` para definir o seu próprio painél de controle.

O `Análise estatística` é uma das coisas cruciais para tomada de decisão em qualquer negócio. OpenERP fornece
Relatórios estatísticos para cada aplicação. Por exemplo, você pode acessar a análise estatística de vendas informações relacionadas
a partir do menu :menuselection:`Sales --> Reporting --> Sales Analysis`. Você pode pesquisar e agrupar os dados usando esta
``Análise estatística`.

Acompanhar o seu processo de Fluxos
===================================

Muitos documentos têm um fluxo de trabalho próprio, e também participar de processos multifuncionais.
Leve um documento que se poderia esperar para ter um fluxo de trabalho, como uma pedido de venda, e
em seguida, clique no botão :guilabel:`?`acima de seu formulário para ver o processo completo.

.. figure:: images/guided_tour_process.png
   :scale: 55
   :align: center

   *Processo para um pedido de venda*

Você pode ver onde um determinado documento está em seu processo, se você tiver selecionado
um documento único, pela barra sólida sobre um dos nodos do processo. Você também apontam
aos documentos e menus para cada um dos estágios.

Há uma clara distinção entre um processo cross-funcional (que atualmente só é
mostrado no cliente web) eo fluxo de documentos detalhados (que é mostrada em ambos os
cliente web a partir de um nó de processo, eo cliente GTK a partir do menu
:menuselection:`Plugins > Execute a Plugin...` e clicando no :guilabel:`Print Workflow` ou na opção :guilabel:`Print Workflow (Complex)`.

.. figure:: images/purchase_workflow.png
   :scale: 65
   :align: center

   *Workflow para um Pedido de Compra*

Ao lado do sistema de gestão de documentos, o processo de tornar os recursos de visualização do OpenERP é
muito melhor para a documentação do que sistemas similares.

Precisa de mais?
================

Você foi guiado através de uma visão geral, rápida breve muitas das principais áreas funcionais de OpenERP.
Alguns destes – uma grande proporção dos módulos principais – são tratados com mais detalhes
nos capítulos seguintes.

Você pode usar o menu :menuselection:`Administration --> Modules --> Modules`
para encontrar os restantes módulos que foram carregados em sua instalação, mas
ainda não instalado em seu banco de dados. Alguns módulos têm apenas menores efeitos colaterais para OpenERP (tal como
:mod:`google_maps`), alguns têm efeitos bastante extenso (como os vários gráficos de contas), e
alguns fazem adições fundamentais.

Mas agora há mais de cem módulos disponíveis. Você pode instalá-los de acordo com suas necessidades.

Uma breve descrição está disponível para cada módulo, mas a forma mais completa de sua compreensão
funcionalidade é a instalação de um e experimentá-lo. Então, parando apenas para preparar outro banco de dados de teste para tentar
-lo em diante, basta baixar e instalar os módulos que aparecem ser interessante.

Dicas e Truques
===============

Visão geral de teclas de atalho
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

* Atalhos para OpenERP

.. table::

   ===============  ===============================
   Tecla de Atalho  O que ele faz?
   ===============  ===============================
   Ctrl+H           Ajuda ao Contexto
   Ctrl+O           Conectar
   Ctrl+Q           Sair
   ===============  ===============================

* Atalhos no Formulário dentro do OpenERP

.. table::

   ===============  ===============================
   Tecla de Atalho  O que ele faz?
   ===============  ===============================
   Ctrl+D           Excluir
   Ctrl+F           Procurar
   Ctrl+G           Ir para o recurso ID
   Ctrl+L           Mudar para a Lista/Formulário
   Ctrl+N           Novo
   Ctrl+P           Visualização em PDF
   Ctrl+Page Down   Próxima aba
   Ctrl+Page Up     Aba Anterior
   Ctrl+R           Atualizar/Desfazer
   Ctrl+S           Salvar
   Ctrl+T           Menu
   Ctrl+W           Fechar aba
   Page Down        Próxima
   Page Up          Anterior
   Shift+Ctrl+D     Duplicar
   Shift+Ctrl+H     Nova aba Principal
   Shift+Ctrl+Y     Repetir a última ação
   ===============  ===============================

* Atalhos para OpenERP ao editar um recurso em uma janela popup

.. table::

   ===============  ===============================
   Tecla de Atalho  O que ele faz?
   ===============  ===============================
   Ctrl+Enter       Salvar e Fechar janela
   Ctrl+Esc         Fechar a janela sem salvar
   ===============  ===============================

* Atalhos em um campo de relação

.. table::

   ===============  ==================================
   Tecla de Atalho  O que ele faz?
   ===============  ==================================
   F1               Adicionar novo campo/linha na hora
   F2               Procurar informações
   F3               Zoom no campo atual
   ===============  ==================================

* Atalhos nas entradas de texto

.. table::

   ===============  ===============================
   Tecla de Atalho  O que ele faz?
   ===============  ===============================
   Ctrl+C           Copiar o texto selecionado
   Ctrl+V           Colar o texto selecionado
   Ctrl+X           Recorta o texto selecionado
   Enter            Auto-completar o campo de texto
   Shift+Tab        Elemento editável anterior
   Tab              Próximo Elemento editável
   ===============  ===============================

Filtros
^^^^^^^

A `Visão de pesquisa avançada` é um novo recurso do OpenERP v6 que fornece um mecanismo muito amigável de filtragem
para o usuário final possa facilmente olhar para cima registros desejados da lista.

O exemplo perfeito de uma visão de pesquisa avançada é a `Relatório Estatístico` do OpenERP.
Esse relatório mostra o resumo estatístico com resultados filtrados para o usuário final.

Normalmente uma pesquisa avançada é composta por três elementos, os botões no topo do filtro, os filtros de Extensão e Grupo por opção.
Estes filtros são dinâmicos, assim de acordo com os filtros que você aplica, colunas extra pode ser adicionada à vista.

Você também pode facilmente combinar filtros; uma seta será exibido e você terá uma estrutura de acordo com o pedido em que você clicou no botão Filtro.

Vamos mostrar um exemplo.
Este relatório estatístico para as tarefas do projeto é `Análise da tarefa` que pode ser exibido usando o
menu :menuselection:`Project --> Reporting --> Tasks Analysis` quando você tiver instalado o módulo `Gestão de Projetos`.

.. figure:: images/filter_task_analysis.png
   :scale: 75
   :align: center

   *Análise da tarefa*

Você pode ver o `Visão de Pesquisa Avançada` na área verde clara sombreado

Você pode filtrar as informações de uma tarefa de acordo com o grupo por características

Clique, por exemplo, o botão no Grupo de `etapa` , e clique em `Task` para analisar as suas tarefas por etapa e, em seguida, por tarefa.

Esta `Visão de Pesquisa Avançada` também pode ser conectada a qualquer 'Visão em lista' de um objeto e, consequentemente, aumentar a facilidade na
 facilidade quando o usuário olha para o registro no visão em  de lista.

.. figure:: images/filter_task_list_view.png
   :scale: 75
   :align: center

   *Pesquisa as tarefas que estão `Em progresso` com o Grupo de Projeto e Estado*



.. Copyright © Open Object Press. Todos os direitos reservados.

.. Você pode levar cópia eletrônica desta publicação e distribuí-lo se você não
.. mudar o conteúdo. Você também pode imprimir uma cópia para ser lido somente por você.

.. Temos contratos com editoras diferentes em países diferentes para vender e
.. distribuir versões em papel ou eletrônicas baseadas deste livro (traduzido ou não)
.. em livrarias. Isso ajuda a distribuir e promover os produtos OpenERP. Também
.. nos ajuda a criar incentivos para pagar os colaboradores e autores com
.. os direitos do autor com essas vendas.

.. Devido a isso, concede a traduzir, modificar ou vender este livro é estritamente
.. proibido, a menos que Tiny SPRL(representando Open Object Press) lhe der uma
.. autorização por escrito para isso.

.. Muitas das designações usadas pelos fabricantes e fornecedores para distinguir seus
.. produtos são as marcas registradas. Onde essas designações aparecem neste livro,
.. e Open Object Press tinha conhecimento de uma reivindicação da marca registrada, as designações foram
.. nas letras maiúsculas iniciais.

.. Embora toda precaução foi tomada na preparação deste livro, a editora
.. e os autores não assumem nenhuma responsabilidade por erros ou omissões, ou por danos
.. resultantes do uso das informações aqui contidas.

.. Publicado por Open Object Press, Grand Rosière, Bélgica

