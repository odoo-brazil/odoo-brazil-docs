
.. _part2-crm-cont:

Gerenciando o Catálogo de Endereços
===================================

.. index::
   single: Parceiro
   single: Cliente
   single: Prospect
   single: Endereço
   single: Contato

Qual é a diferença entre um parceiro e um contato no OpenERP? Um ``Parceiro`` representa uma entidade que você faz negócio com 
- um parceiro, um prospect, ou eventualmente um funcionário da sua empresa. Em outras Aplicações CRM, um parceiro é 
também referenciado como uma Conta.
Um ``Contato`` representa uma pessoa que trabalha para um parceiro.

Cada parceiro pode ter um número ilimitado de contatos. O OpenERP também permite que você tenha vários contatos com o mesmo tipo
de endereço para um parceiro. Você pode facilmente vincular vários Endereços de Faturamento para um Cliente, por exemplo.

.. note:: Tipo de Endereço

        Se você tem vários contatos para o mesmo parceiro, você pode dizer ao OpenERP qual dos contatos será usado em 
alguns docunentos (e.g. Uma Cotação) através do ``Tipo de Endereço``.

	Por exemplo, um parceiro (*Empresa*) pode ter um endereço de entrada que difere do endereço de faturamento da empresa.
	Se o tipos de endereços estão atribuídos corretamente, OpenERP pode automaticamente selecionar o endereço adequado durante 
a criação do documento – uma Fatura é endereçada para um contato que tenha sido atribuído o tipo de endereço da fatura,
caso contrário, para o endereço padrão.

O conceito de parceiro no OpenERP é muito mais flexível do que em muitos outros aplicativos de gerenciamento. Por que? 
Porque um parceiro pode ser o seu fornecedor e seu cliente, ao mesmo tempo.
Como consequência, quaisquer dados que você atualizar para esse parceiro serão aplicados tanto ao cliente quanto ao fornecedor! 
Graças a isso, você não precisa atualizar seu catálogo de endereços várias vezes (ou até mesmo em vários locais) para o mesmo parceiro.

O formulário de parceiro inclui informações sobre a empresa, como sua razão social, seu idioma principal, e se a empresa
é um \ ``Cliente`` \ e/ou um \ ``Fornecedor`` \. O formulário de parceiro é composto de várias guias,

* A guia :guilabel:`Geral` contém informações sobre diferentes contatos do parceiro, endereços, comunicação e as categorias que
o parceiro pertence,

* A Guia :guilabel:`Vendas e compras` contém informações como o vendedor padrão e equipe de vendas, e site,

* A guia :menuselection:`Histórico` fornece visibilidade sobre todo o ``histórico das comunicações`` (Reuniões, Campanha de Marketing, 
leads e oportunidades, telefonemas, emails) com o parceiro. Os eventos nos quais o parceiro esteve envolvido em são criados
automaticamente por documentos diferentes, como chamadas telefônicas, leads, reuniões,

* A guia :menuselection:`Notas` para comentários.

.. figure::  images/crm_partner_hist.jpeg
   :scale: 100
   :align: center

   *A Guia Histórico de um cliente*

Criando e Atualizando Parceiros
------------------------------_

Antes de explicar como criar um parceiro, uma palavra rápida sobre as diferentes formas de visualização de parceiros no OpenERP.
Modo `Lista` exibe uma lista de clientes (a visualização padrão quando você clicar no menu Clientes). Nesta Visualização,
você pode ver vários clientes ao mesmo tempo. Modo `Formulário` é exibido quando você clicar em um determinado cliente para 
iniciar uma edição ou quando você cria um novo cliente.

Para criar um novo parceiro (uma empresa, clientes, fornecedores, ...) ou para exibir uma lista de clientes já existente, acesse 
o menu :menuselection:`Vendas --> Catálogo de Endereços --> Clientes`. Este menu não só permite que você crie um novo parceiro como 
também para pesquisar parceiros.

.. figure::  images/crm_partner_default.jpeg
   :scale: 100
   :align: center

   *Um Formulário de Cliente*

.. note:: Obrigatório

        Campos azuis são sempre obrigatórios, significando que você tem que introduzir um valor. É impossível salvar as alterações,
enquanto os campos azuis não frem preenchidos.

Você deve pelo menos digitar o ``Nome`` da empresa no formulário do parceiro. Alguns campos são campos de texto, os outros campos
podem ser vinculados aos dados existentes que tenham sido inseridos em outros lugares, como ``Países``.

Crie um cliente contendo os seguintes dados:

* :guilabel:`Nome` : \ ``Smith and Offspring``\ ,

* :guilabel:`Cliente` checkbox : \ ``checked``\ ,

* :guilabel:`Fornecedor` checkbox : \ ``unchecked``\ ,

* :guilabel:`Nome de Contato` : \ ``Stephen Smith``\ ,

* :guilabel:`Tipo` : \ ``Default``\, na Guia de Endereços,

* :guilabel:`Salvar` o formulário.

.. tip:: Email

      Se você usar um gateway de e-mail, o Outlook ou o Thunderbird Plugin, não se esquecer de informar um endereço de e-mail para 
cada contato, para que o gateway possa anexar automaticamente e-mails recebidos para o parceiro correto.

Para atualizar um parceiro, abra o formulário correspondente, selecione `Editar` e alterar os campos necessários. 
Como explicado anteriormente, quando uma empresa é simultaneamente um cliente e um fornecedor, 
você só precisa editar o formulário parceiro e uma vez que tenha realizado as modificações serão feitas tanto
para os clientes quanto para os fornecedores.

.. note:: Caixas de Selelão

       Por que é tão importante definir corretamente as caixas de seleção de Cliente e do Fornecedor no parceiro?
Estes checkboxes visam permitir ao OpenERP selecionar rapidamente os parceiros que devem ser exibidos em algumas caixas suspensas. 
Um exemplo: quando você seleciona um parceiro numa cotação de venda, o OpenERP só irá permitir que você selecione na lista de clientes. 
E é exatamente para isso que a caixa de seleção Cliente é utilizada.

.. index:: Contatos; Endereços

Gerenciando Contatos & Endereços
--------------------------------

Você pode ter alguns contatos por parceiro. Contatos representam funcionários da empresa que você está em contato, juntamente com
seus detalhes de endereço. Para cada endereço você pode indicar o tipo (\ ``Padrão``\, \ ``Fatura``\, \ ``Entrega``\, \ ``Contato``\ 
or \ ``Outros``\).

Contatos podem ser inseridos na Guia :guilabel:`Geral` do formulário do **Cliente**, ou na lista de endereços
no menu :menuselection:`Vendas --> Livro de Endereços --> Enderços`.

.. tip:: Mesmo Contato, Diferentes Parceiros

        Você tem contatos que trabalham para diversas empresas, e precisa de estar vinculado a vários parceiros?
Confira o capítulo :ref:`ch-contact`.

Personalizando Campos do Parceiro
---------------------------------

OpenERP também permite que você personalize o ``Parceiro`` à suas necessidades. Clique na opção `Gerenciar Exibições` se
você quiser adicionar campos, excluir campos ou alterar a ordem dos campos.

Vamos adicionar o campo ``Aniversário`` no contato, no formulário de `Endereços`. Para fazer isso, vá para o :menuselection:`Vendas -->
Catalogo de Endereços --> Endereços` e abra qualquer enderço no modo Formulário. Na barra de menu da direita, clique em `Gerenciar Views`, e `Editar` porque a visão correspondentes já está pré-selecionada.

Vá para a última linha da exibição e clique no sinal de mais(+) azul para adicionar um campo para ao grupo `Comunicação`. 
Veja na figura abaixo e depois clique no botão `Atualizar`.

.. figure::  images/manage_views_addfield_small.jpeg
   :scale: 75
   :align: center

   *Adicionar o campo de aniversário para um contato*

Na tela de `Propriedades` exibida, você pode alterar a legenda para ``Aniversário``  no campo ``Texto``. 
Para indicar que um novo campo pode ser usado no modo de exibição pesquisa, certifique-se de selecionar ``Sempre Pesquisável``.
Clique no botão `Atualizar` para confirmar as alterações. Clique ``Pré-visualização`` para ver o resultado.
O campo ``Aniversário`` agora vai aparecer em `Endereço` no `Modo de Formulário`, pronto para ser utilizado.

Executando Ações nos Clientes
-----------------------------

.. index::
   single: Enviar SMS
   single: Oportunidade
   single: Lembrete

No lado direito da lista de `Cliente` ou do modo de formulário, você vai encontrar uma lista de todos os relatórios, ações e links
disponíveis para os parceiros selecionados. Você pode executar ações e imprimir relatórios tanto da lista como do formulário.
A Lista lhe permite fazer ações para vários parceiros ao mesmo tempo.

.. tip:: Ações

       Para exibir a lista de ações possíveis, basta selecionar um ou mais clientes ou clique na seta no topo da barra lateral direita.

Você pode criar uma nova oportunidade para um cliente, ou iniciar um envio de e-mails em massa.
O envio de e-mail em massa geralmente é iniciado a partir de uma lista, porque você poderá selecionar vários parceiros.

.. note:: Campanhas

        Para correspondência em massa, talvez você prefira usar o aplicativo de Marketing Direto, que oferece grandes funcionalidades 
(consulte o capítulo :ref:`part3-crm-market`).

Outra ação permite enviar rapidamente uma mensagem de SMS.

.. tip::  Envia uma mensagem SMS

        Para enviar uma mensagem SMS a partir do padrão Open ERP você terá que fazer um pedido de SMS de grandes quantidades da
operadora Clickatell ™ http://clickatell.com.

        Para enviar uma mensagem SMS a um parceiro ou uma seleção de vários parceiros, primeiro selecione os parceiros no
Modo de lista, então clique no ícone da ação :guilabel:`Enviar SMS`.

.. index:: Filtro

Encontrando Parceiros Utilizando Filtros
----------------------------------------

Abra o Modo de Lista de `Clientes` para descobrir as opções de busca que lhe permite facilmente filtrar seus parceiros.
Você pode agrupar por ``Vendedor`` para ver quais os clientes que já foram atribuídos a um vendedor ou não. 
Clique no botão à direita (o ícone da pessoa) para ver os clientes que são seus.

.. tip:: Limites

        Se você deseja exibir mais do que os 20 parceiros exibidos por padrão, clique na opção ``1 a 20 de - XX`` na parte
inferior da tela para poder alterar o limite.

Os filtros também permitem definir rapidamente as listas de clientes para os quais você quer fazer ações específicas.
Através da opção ``Novo Filtro``, você também pode adicionar seus próprios filtros para qualquer área relacionada ao formulário
de ``Cliente``.

.. note:: Filtros

        Você pode facilmente criar seus próprios filtros frequentemente utilizados por pré-filtragem dos dados da forma que desejar
e em seguida, usar a opção Salvar filtro.

.. _partner-categ:

Categorizando Parceiros
-----------------------

.. index::
   pair: Parceiro; Categoria

OpenERP usa categorias para organizar todos os seus parceiros de acordo com o seu relacionamento com a sua empresa 
(cliente, prospect, fornecedor, e assim por diante). Cada parceiro podem ser associado às diversas categorias. 
Para abrir a lista de categorias disponíveis no parceiro, use o menu :menuselection:`Vendas --> Configuração --> 
Catálogo de Endereços --> Categorias de Parceiros`.

.. figure::  images/crm_partner_category_big.png
   :scale: 100
   :align: center

   *Lista de Categorias do Parceiro*

Clique em uma das categorias na estrutura de categoria de parceiros para obter uma lista dos parceiros nessa categoria. 
Se você clicar em uma categoria que tem subcategorias, você receberá uma lista de todos os parceiros na categoria principal
e em todas as suas subcategorias.

.. note:: Categorias

        Para criar uma nova categoria, vá para :menuselection:`Vendas --> Configuração --> Catálogo de Endereços --> Categorias de
Parceiros` e clique no botão `Novo`.

Porque as categorias podem ser organizadas de acordo com uma estrutura de árvore, você pode aplicar uma
ação em qualquer nível da estrutura: uma promoção de marketing, por exemplo, pode ser aplicada a todos os clientes,
ou seletivamente apenas para os clientes numa categoria e suas subcategorias.

Você pode criar suas próprias categorias e atribuir-lhes o seu parceiro a partir do formulário do `cliente`.
Outra maneira de atribuir o parceiro que correspondente a uma categoria é abrir a categoria em `Categorias de Parceiros`

No capítulo :ref:`profiling`, você verá como atribuir parceiros a categorias automaticamente usando às regras de segmentação.

.. _ch-contact:

Uma Alternativa Para Gerenciar Contatos
---------------------------------------

De acordo com seu tipo de negócio, a maneira padrão de ligar vários contatos a um parceiro pode não ser flexível o suficiente para você.
Você poderia perfeitamente ter o mesmo funcionário trabalhando para várias empresas. Ou talvez você trabalhe com representantes 
assegurando o acompanhamento de diversos dos seus clientes. Então você gostaria de ter o mesmo contato ligado a diferentes parceiros. 
Claro, o OpenERP fornece uma alternativa o módulo: mod: `base_contact`, que lhe dá ainda mais flexibilidade no gerenciamento de
seus contatos.

Compartilhe facilmente o mesmo contato (empregado, por exemplo), que pode perfeitamente ter empregos diferentes, com vários parceiros. 
Você só precisa digitar (ou *criar*) o contato uma vez e fazer um link a os parceiros envolvidos, enquanto especifica a posição que o
contato detém para cada empresa em particular. Quaisquer alterações nas informações de contato só precisarão ser feitas uma vez para que
sejam aplicados para todos os parceiros que o contato está relacionado!

Podemos ilustrar o conceito de múltiplos relacionamentos entre os contatos e os parceiros (empresas) através de um exemplo. A figura :ref:`fig-crmconw` mostra duas empresas tendo diversos endereços (locais de trabalho) e diversos contatos anexado a estes endereços.

Neste exemplo você encontrará alguns exemplos:

* O banco ABC tem dois escritórios, representadado pelos endereços de ABC Bélgica e ABC Luxemburgo,

* Os endereços da Dexey França e Dexey Bélgica pertencem à empresa Dexey

* No escritório da ABC Luxemburgo, você tem os contatos do diretor (D. Smith) e o contador (A. Silva),

* Sr. Doe ocupa o cargo de contador para ABC Luxemburgo e França Dexey,

* Sr. D. Smith é diretor do Dexey França e Dexey Bélgica e também temos seu endereço privado que não está ligado a um parceiro.

Uma opção de menu extra será adicionado, permitindo-lhe apresentar a lista de contatos, através de :menuselection:`Vendas --> 
Catalogo de Endreços --> Contatos`.

A imagem abaixo ilustra como os contatos são tratados na configuração avançada de contatos.

.. _fig-crmconw:

.. figure:: images/crm_contact_with_latest.png
   :scale: 100

   *Gerenciamento Avançado de Contato*

Esta é uma forma clara de ilustrar o nível de complexidade que podem ser realizadas no OpenERP.

Se você corrigir ou alterar um nome de contato no formulário de contato, as alterações serão aplicadas a todos os lugares 
ocupados em empresas diferentes.

A tela abaixo representa um formulário de parceiro. Você pode adicionar diversos endereços, como fatura e entrega, 
e uma lista de contatos por endereço. Cada contato tem seus próprios dados, como nome, número de telefone, função e e-mail.

.. figure:: images/crm_base_contacts.png
   :scale: 80
   :align: center

   *Formulário de Parceiro com Gerenciamento Avançado de Contatos*

Vá para :menuselection:`Vendas --> Catalogo de Endereços --> Contato` para abrir o formulário de contato.
Você insere os dados no formulário de contato, contendo informações como telefone celular, diferentes funções ocupados, e blog pessoal. 
Você também pode adicionar uma foto ao seu contato. Se você clicar na linha de `Cargos e Endereços`, você irá obter mais detalhes 
sobre o trabalho (tais como data de início, data de término e fax).

.. figure:: images/crm_partner_poste.png
   :scale: 100
   :align: center

   *Detalhes de um cargo ocupado por um contato de um parceiro*

.. Copyright © Open Object Press. All rights reserved.

.. You may take electronic copy of this publication and distribute it if you don't
.. change the content. You can also print a copy to be read by yourself only.

.. We have contracts with different publishers in different countries to sell and
.. distribute paper or electronic based versions of this book (translated or not)
.. in bookstores. This helps to distribute and promote the OpenERP product. It
.. also helps us to create incentives to pay contributors and authors using author
.. rights of these sales.

.. Due to this, grants to translate, modify or sell this book are strictly
.. forbidden, unless Tiny SPRL (representing Open Object Press) gives you a
.. written authorisation for this.

.. Many of the designations used by manufacturers and suppliers to distinguish their
.. products are claimed as trademarks. Where those designations appear in this book,
.. and Open Object Press was aware of a trademark claim, the designations have been
.. printed in initial capitals.

.. While every precaution has been taken in the preparation of this book, the publisher
.. and the authors assume no responsibility for errors or omissions, or for damages
.. resulting from the use of the information contained herein.

.. Published by Open Object Press, Grand Rosière, Belgium

-

