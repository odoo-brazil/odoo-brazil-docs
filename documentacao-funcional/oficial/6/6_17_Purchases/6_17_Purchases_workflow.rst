
Todos os elementos de um fluxo de trabalho completo
===================================================

O pedido do fornecedor ou de compra é o documento que permite que você gerencie as negociações de preços, 
controle de faturas de fornecedores, lidar com entradas de mercadorias e sincronizar todos esses documentos.

Vamos começar a olhar para o fluxo de trabalho na seguinte ordem:

#. Pedido de preços para o fornecedor,

#. Confirmação da compra,

#. Recepção e controle de produtos,

#. Controle de faturamento.

Criação de seu banco de dados
-----------------------------

Para configurar um sistema para estes exemplos, crie um novo banco de dados com dados de demonstração e
selecione a interface :guilabel:`Extended` quando você logar como o usuário *admin*. Você pode inserir seus próprios
detalhes da empresa quando solicitado, ou simplesmente usar o padrão se quiser.

.. index::
   single: module; purchase

Em seguida, usando o Assistente de Configuração, selecione :guilabel:`Purchase Management` na seção :guilabel:`Install Applications`
para instalar o módulo :mod:`que também instala vários outros módulos como dependências. Continue
o restante deste capítulo logado como o usuário *admin*.

Pedido de preço do Fornecedor
-----------------------------

Para inserir dados para um novo pedido de preço do fornecedor (i.e. solicitação de cotação), use o menu :menuselection:`Purchases --> 
Purchase Management -->
Request for Quotation`. Quando você clicar em :guilabel:`New`, OpenERP abre uma solicitação em branco para um formulário de
cotação que você usa para solicitar os preços de um fornecedor. isso é mostrado na figura :ref:`fig-pfrm`. Se o preço pedido veio de
uma aquisição automática criado pelo OpenERP, você vai encontrar uma referência ao documento que gerou o pedido no 
campo :guilabel:`Origin`.

.. _fig-pfrm:

.. figure:: images/purchase_form.png
   :scale: 75
   :align: center

   *Data Entry for a Purchase Order*

.. index::
   single: module; warning

.. note:: Gerenciando alertas

        Se você instalar o módulo :mod:`warning`, você será capaz de definir alertas que aparecem quando o comprador entra um pedido 
de preço ou ordem. Você pode definir alertas sobre o produto e o fornecedor.

A referência interna, a data e o armazém dos produtos que deverão ser entregues, são concluídas automaticamente pelo OpenERP, 
mas você pode alterar esses valores, se necessário. Em seguida, quando você selecionar um fornecedor, o OpenERP completa automaticamente 
o endereço de contato para o fornecedor. A tabela de preços também é preenchida automaticamente a partir da lista de preços 
no formulário do fornecedor. Isso deve trazer todas as condições que você tem negociado com o fornecedor por um determinado período.

.. tip:: Seleção de fornecedor

        A procura de um fornecedor está limitada a todos os parceiros no sistema que tem a caixa de seleção marcada 
:guilabel:`Supplier`. Se você não encontrar o seu fornecedor, pode valer a pena verificar a lista completa de todos 
os parceiros para se certificar de que o fornecedor ainda não existe sem a caixa de seleção do fornecedor a ser verificada.

Uma vez que o corpo principal do pedido de compra tenha sido concluído, você pode digitar as linhas de produtos.

.. figure:: images/purchase_line_form.png
   :scale: 75
   :align: center

   *Linha do Pedido de Compra*

Quando você tiver selecionado o produto, o OpenERP completa automaticamente os outros campos do formulário:

* :guilabel:`Product UoM`, tomado a partir do campo :guilabel:`Purchase Unit of Measure` no formulário de produto,

* A :guilabel:`Description` do produto em linguagem do fornecedor,

* :guilabel:`Scheduled Date`, calculado a partir da data do pedido e o tempo de entrega para o fornecedor (para o determinado produto),

* :guilabel:`Unit Price`, tirado da lista de preços do fornecedor,

* :guilabel:`Taxes`, tomado a partir da informação sobre a forma de produtos e formulário sócio,
  dependendo das regras, visto em :ref:`Financial Analysis <ch-financial>`.

.. tip:: Escrevendo o produto e Código

        Quando você digitar nomes de fornecedores no formulário de produto, você pode definir um nome e um código de produto 
para cada fornecedor individual. Se você fizer isso, o OpenERP irá então usar esses detalhes ao invés de seus próprios nomes de 
produtos internos para o fornecedor selecionado.

Se você trabalha com gestão por caso, você também pode configurar a conta analítica que deve ser usada para o
relatório de todos os custos de aquisição. Os custos serão então notificados com o recibo do fornecedor
fatura.

.. index::
   single: module; purchase_analytic_analysis

.. tip:: Gestão por Processo

   Contas analíticas podem ser muito úteis para todas as empresas que gerenciam os custos por caso, por site, por
    projeto ou por pasta.
   Para trabalhar com vários eixos de análise, você deve instalar o módulo :mod:`purchase_analytic_plans`,
   selecionando :guilabel:`Purchase Analytic Plans` no assistente :guilabel:`Reconfigure` e clicando
   :guilabel:`Configure`.

.. index::
   single: module; account_analytic_default
   single: module; purchase_analytic_plans

Para se certificar de que a conta analítica é selecionada automaticamente de acordo com o parceiro, a data, o
produto ou o usuário, você pode instalar o módulo :mod:`account_analytic_default` (que é instalado
automaticamente como uma dependência do :mod:`purchase_analytic_plans`).

Na aba :guilabel:`Notes` da linha de produtos, você pode digitar uma nota que será anexada quando a ordem de
cotação de confirmação ou o preço é impresso. Esta nota pode ser pré-definidos sob a forma de produtos para
aparecem automaticamente em cada pedido para esse produto. Por exemplo, você pode entrar “Não se esqueça de enviar
pela entrega expressa, conforme especificado no nosso contrato de referência 1234.”

Uma vez que o documento tenha sido concluído, você pode imprimi-lo como uma estimativa de preço para enviar para
o fornecedor. Você pode definir uma nota para a atenção do fornecedor na terceira aba do formulário.

.. figure:: images/purchase_quotation.png
   :scale: 75
   :align: center

   *Impressão da Cotação do Fornecedor*

Em seguida, deixe o documento no estado ``Pedido de Cotação``. Quando você receber uma resposta do fornecedor, use o menu
:menuselection:`Purchases --> Purchase Management --> Requests for Quotation`. Selecione o
pedido e conclua os seus detalhes.

Quando você quiser aprovar o pedido, use o botão :guilabel:`Convert to Purchase Order`. o preço
pedido, em seguida, passa para o estado ``Approved``. 
Nenhuma alteração a mais será possível.

.. figure:: images/purchase_process.png
   :scale: 75
   :align: center

   *Processo de Pedido de Compra*

Recebimento de mercadorias
--------------------------

Uma vez que o pedido foi aprovado, o OpenERP automaticamente prepara um pedido na entrada de mercadorias em
estado de rascunho para você. Para obter uma lista dos produtos que você está esperando de seus fornecedores, use o
menu :menuselection:`Warehouse --> Warehouse Management --> Incoming Shipments`.

.. tip:: Serviços de compra

    Se você comprar os serviços do seu fornecedor, o OpenERP não gera uma nota de entrada de mercadorias.
     Não há recebimento de serviço equivalente a uma entrada de mercadorias.

Selecione o documento que corresponde ao item que você está recebendo. Normalmente, o recebimento da mercadoria
é encontrado fazendo uma pesquisa sobre a referência ao pedido ou o nome do fornecedor. Você pode então confirmar
o recebimento dos produtos.

Conforme descrito na :ref:`ch-stocks`, se você receber apenas uma parte do pedido o OpenERP
gerencia o restante desse pedido.
Uma nota é então criada automaticamente para as mercadorias não recebidas.
Você pode cancelá-lo se você acha que você nunca vai receber os produtos restantes.

Depois de receber a mercadoria, o OpenERP irá mostrar-lhe que as ordens estão abertas e o estado do
recebimento e faturamento, se você voltar à lista de pedidos.

.. figure:: images/purchase_list.png
   :scale: 75
   :align: center

   *Lista de Pedidos em Aberto, Recebimento e status da fatura*

Controle de Faturamento
-----------------------

Para controlar o faturamento do fornecedor, o OpenERP oferece três sistemas como padrão, que podem diferir pedido
por pedido:

* :guilabel:`From Order` : faturamento com base em quantidades encomendadas,

* :guilabel:`From Picking` : faturamento com base em quantidades recebidas,

* :guilabel:`Manual` : faturamento manual.

O modo de controle de faturamento é definido na guia segundo o pedido no campo
:guilabel:`Invoicing Control`.

.. figure:: images/purchase_form_tab2.png
   :scale: 75
   :align: center

   *Pedido de Compra, Controle da fatura*

.. tip:: Valor padrão

  Uma empresa geralmente usa um método único de controle de faturamento para todas as suas faturas.
   Então, você é aconselhado a definir um valor padrão no campo :guilabel:`Invoicing Control` após a
instalação.

Controle baseado em pedidos
---------------------------

Se você selecionou o seu controle de faturamento com base em pedidos, o OpenERP irá gerar automaticamente uma
fatura do fornecedor no estado de rascunho quando o pedido for confirmado. Você pode obter uma lista de faturas em
espera utilizando o menu :menuselection:`Accounting --> Suppliers --> Supplier Invoices` e permitindo o filtro ``Draft``.

Quando você receber uma fatura no papel a partir do seu fornecedor, tudo que você precisa fazer é validar a fatura pre-
gerada pelo sistema. Não se esqueça de verificar o preço e as quantidades. Quando a fatura é
confirmada, os lançamentos contábeis representam o custo de aquisição e são automaticamente colocados no sistema.

O pedido do fornecedor é automaticamente definido como ``Paid`` quando você pagar a fatura do fornecedor.

Este método de controle de faturas é frequentemente utilizado em empresas de serviços, porque valores faturados
correspondem aos montantes solicitados. Em logística, ao contrário, na maioria das vezes você trabalha com faturamento
controlado por entrada de mercadorias.

Controle baseado em entrada de mercadorias
------------------------------------------

Para controlar o seu fornecedor de faturas com base na entrada de mercadorias, defina o campo :guilabel:`Invoicing
Control` na segunda aba do pedido de :guilabel:`From Picking`.

Neste caso, nenhuma fatura, no estado de rascunho ou qualquer outro, é gerada pelo pedido. Sobre a entrada de mercadorias
nota, o campo :guilabel:`Invoice Control` is set to :guilabel:`To Be Invoiced`.

A pessoa poderá então receber ordens diferentes. Se ela quer gerar a fatura para um projeto de
entrada de mercadorias, ela pode clicar na ação :guilabel:`Create Invoice`. O OpenERP pede-lhe para fazer a
revisão desta fatura. Ela então abre isso ou as faturas geradas (no caso de criação de
faturas de vários recibos de uma só vez) que lhe permite modificá-la antes de a confirmar.

Essa abordagem é útil quando você receber a fatura, ao mesmo tempo que o item do fornecedor.
Normalmente, as faturas são enviadas por correio alguns dias depois. Neste caso, a pessoa armazenada deixa o item
inalterado, sem gerar uma fatura. Então, uma vez por dia ou uma vez por semana o contador vai
criar o projeto com base em faturas de todos os recibos para o dia. Para fazer isso, ele usa o menu
:menuselection:`Purchases --> Invoice Control --> Purchase Lines Not Invoiced`. 
Ele clica a ação :guilabel:`Create invoices` para gerar todas as faturas do projeto
da lista de receitas que ainda não foram faturadas.

.. index::
   single: accountant

Nesse ponto, o contabilista pode decidir se ele quer gerar uma fatura por item ou grupo de todos os itens
para o mesmo parceiro na mesma fatura.

As Faturas são então tratadas assim como aquelas controladas a partir de ``On Order``. Uma vez que a fatura chega ao
serviço de contabilidade, ele apenas compara com as faturas à espera de controle.
faturas você.

.. index::
   single: module; delivery

.. tip:: Taxas de entrega

   Para gerenciar custos de entrega, instalar o módulo de assistente:mod:`delivery` using the :guilabel:`Reconfigure`
   e selecionando :guilabel:`Delivery Costs` na seção :guilabel:`Sales Application Configuration`.
   Isso irá adicionar automaticamente taxas de entrega para a criação da fatura projeto como uma função
    dos produtos entregues ou encomendadas.

.. index:: 
   single: tender
   single: purchase; tender

Propostas
---------

.. index::
   single: module; purchase_tender

Para gerenciar propostas, você deve usar o módulo :mod:`purchase_requisition`, instalados através da opção
:guilabel:`Purchase Requisition` no assistente :guilabel:`Reconfigure`.
Isto permite-lhe criar diversos preços de pedidos de fornecedores para uma exigência de fornecimento única.
Assim que o módulo está instalado, o OpenERP acrescenta
um novo menu :menuselection:`Purchase Requisitions` em :menuselection:`Purchases --> Purchase Management`. 
Você pode então definir os novos concursos.

.. figure:: images/purchase_tender.png
   :scale: 75
   :align: center

   *Definição de uma proposta*

Para inserir dados para uma nova concorrência, use o menu :menuselection:`Purchases --> Purchase Management -->
Purchase Requisitions` e selecione :guilabel:`New`. O OpenERP então abre um formulário nova concoccência em branco. O número de referência
é definido por padrão e você pode inserir informações sobre a sua concorrência nos outros campos.

Se você deseja inserir uma resposta do fornecedor à sua solicitação de concurso, adicione um novo
projeto de ordem de compra para a lista na guia :guilabel:`Quotation` do seu documento de concurso. 
Se você quiser rever o preço do fornecedor em resposta às negociações, edite qualquer
pedido de compra apropriado que você deixou no estado de rascunho e ligado à proposta.

Quando um dos pedidos sobre a proposta for confirmado, todas as outras ordens são automaticamente
canceladas pelo OpenERP se você selecionou o tipo de requisição de compra (exclusivo) que lhe permite aceitar apenas um pedido 
para uma proposta específica. Se você selecionar múltiplas requisições, você pode aprovar vários pedidos de compra sem cancelar
outros pedidos desta concorrência.

Revisões de preços
------------------

O OpenERP suporta diversos métodos de cálculo e atualiza automaticamente os custos do produto:

* Preço Padrão: manualmente fixo, e

* Preço Padrão: reavaliado de forma automática e periodicamente,,

* Preço Médio: atualizados em cada recibo para o armazém..

Este custo é utilizado para avaliar o seu estoque e representa os custos do seu produto. Está Incluído no custo
tudo o que for diretamente relacionado com o custo recebido. Você poderia incluir elementos como:

* preço do fornecedor,

* taxas de entrega,

* custos de fabricação,

* taxas de armazenagem.

Preço Padrão
^^^^^^^^^^^^

O modo de gestão de preços para o produto é mostrado no guia :guilabel:`Information` na formulário de produto.
Em cada produto, você pode selecionar se você quer trabalhar em ``Standard Price`` ou ponderada ``Average Price``.

.. tip:: Interface simplificada

   Se você trabalha no modo de interface ``Simplified`` você não vai ver o campo que lhe permite
    gerenciar o modo de cálculo do preço de um produto. Nesse caso, o valor padrão é ``Standard Price``.

A configuração ``Standard Price``significa que o custo do produto é fixo manualmente para cada produto no campo
:guilabel:`Cost Price`. Isso geralmente é reavaliado uma vez ao ano com base na média dos custos de aquisição
ou dos custos de fabricação.
Você geralmente usa os custos padrão para gerenciar os produtos cujo preço dificilmente se altera ao longo
do ano. Por exemplo, o custo-padrão pode ser usado para gerenciar livros, ou o custo do pão.

Os custos que podem ser fixos para todo o ano trazem algumas vantagens:

* você pode basear o preço de venda sobre o custo do produto e, então, trabalhar com margens, em vez de
   um preço fixo por produto,

* contabilidade é simplificada, pois há uma relação direta entre o valor das ações e os
   número de itens recebidos.

.. index::
   single: module; product_extended

Para se ter uma reavaliação periódica automatizada do preço padrão que você pode usar a ação :guilabel:`Update`
no formalário de produto, permitindo que você atualize os preços de todos os produtos selecionados.
O OpenERP então recalcula o preço dos produtos em função do custo das matérias-primas e as
operações de manufatura dadas no roteamento.

Preço Médio
^^^^^^^^^^^^^

Trabalhar com preços normais não é indicado para a gestão do preço de custo dos produtos
quando os preços mudam muito com a flutuação do mercado. Este é o caso de muitas commodities e
energia.

Neste caso, você iria desejar que o OpenERP defina automaticamente o preço em resposta a cada movimento de entrada de mercadorias
para o armazém. Os fornecimentos (saída do estoque) não têm nenhum impacto sobre o preço do produto.

.. tip:: Cálculo do preço

   Em cada entrada de mercadorias, o preço do produto é recalculado utilizando a fórmula contábil abaixo:
   NP = (OP * QS + PP * QR) / (QS + QR), onde a seguinte notação é usada:

   * NP: Novo Preço,

   * OP: Preço Antigo,

   * QS: Quantidade efetivamente no estoque,

   * PP: Preço pago para a quantidade recebida,

   * QR: Quantidade recebida.

Se os produtos são gerenciados como uma média ponderada, OpenERP irá abrir uma
janela que permite que você especifique o preço do produto recebido em cada entrada de mercadorias.
O preço de compra é, por padrão,
definido a partir do pedido de compra, mas você pode alterar o preço para adicionar o custo de
entrega aos diversos produtos recebidos, por exemplo.

.. figure:: images/purchase_pmp.png
   :scale: 75
   :align: center

   *Bens de recepção de produtos gerenciados na Média Ponderada*

Uma vez que o recebimento foi confirmado, o preço é recalculado automaticamente e entram no
formulário de produtos.

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
