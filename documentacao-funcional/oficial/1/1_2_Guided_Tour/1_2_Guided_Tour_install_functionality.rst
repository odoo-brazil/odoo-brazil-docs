
.. index::
  single: module; new functionality

Instalação de novas funcionalidades
===================================

Todas as funcionalidades do OpenERP estão contidas no seus variados módulos. Muitos destes, os
módulos principais, são carregados automaticamente durante a instalação inicial do sistema e podem ser
atualizados online mais tarde. Embora a maioria não esteja instalada em seu banco de dados no início, eles estão
disponíveis em seu computador para instalação imediata. Módulos adicionais também pode ser carregados online
a partir do site oficial OpenERP http://openerp.com. Estes módulos são inativos quando são carregados
no sistema, e podem ser instalados em uma etapa separada.

Você vai começar verificando se há atualizações disponíveis online que se apliquem  à instalação inicial.
Então você vai instalar um módulo de CRM para completar o seu banco de dados existente.

.. index::
  single: module; upgrading

Atualizando a lista de módulos
------------------------------

Clique :menuselection:`Administration --> Modules --> Update Modules List` para iniciar a
atualização de ferramentas. A janela :guilabel:`Module Update` vai se abrir notificando o usuário OpenERP que vai procurar no servidor para adição de novos módulos e atualização
dos já existentes.

Clique em :guilabel:`Update` para iniciar a atualização do pelo servidor. Quando for
completa, você verá uma seção :guilabel:`Module update result` indicando quantos novos módulos foram adicionados
e quantos módulos existentes foram atualizados. Clique em :guilabel:`Open Modules` para retornar à lista atualizada.

.. note:: Módulos

	Todos os módulos disponíveis no seu computador podem ser encontrados no diretório de addons do seu servidor OpenERP.
Cada módulo é representado por um diretório com o nome do módulo ou por um
arquivo com o nome do módulo e .zip anexado a ele. O arquivo está em formato de arquivo ZIP e replica
a estrutura de diretórios de módulos descompactado.

.. tip:: Pesquisar toda a lista

	A lista de módulos mostra apenas os primeiros módulos disponíveis. No cliente web você pode pesquisar ou
seguir o primeiro / anterior / próximo / últimos links  para chegar a qualquer ponto em toda a lista, e você pode
alterar o número de entradas listadas, clicando no número da linha entre os indicadores :guilabel:`Previous` 
	e :guilabel:`Next`
	e selecione um número diferente do padrão de 20

	Se você usar o cliente GTK você pode pesquisar, como você faria com o cliente web, ou usar o campo de seleção
	(mostrando atualmente 80)
no canto superior direito da janela para alterar o número de entradas retornadas pela busca do seu padrão
limite de 80, ou seu deslocamento padrão de 0 em toda a lista (a partir de a primeira entrada).

.. index::
  single: module; installing

A configuração / Assistente para reconfigurar
--------------------------------------

Um dos novos recursos do OpenERP é o assistente :guilabel:`Configuration` . Uma vez executado, o atalho do :guilabel:`Reconfigure
 irá aparecer. Este assistente fornece uma maneira fácil de instalar os módulos, graças ao seu user-friendly e easy-to-use interface.
O usuário pode carregar este assistente em sua própria conveniência usando o atalho :guilabel:`Reconfigure`, encontrado logo abaixo do 
banco de dados e nome do usuário na web do cliente ou no menu de atalho no cliente GTK. Aparece a mesma caixa de diálogo de configuração
 do momento da instalação de um novo banco de dados. Por que nós chamamos o o assistente  :guilabel:`Reconfigure`? Na verdade, 
porque permite que o utilizador reveja os aplicativos instalados e instale recursos adicionais relacionados ou simplesmente  
instale novas aplicações em tempo real.

Quando você passar por várias etapas no assistente, você vai encontrar algumas opções que são marcadas como verificadas (em cinza).
Estes são aplicativos já instalados. Na configuração de banco de dados \ ``openerp_ch02`` \, você pode ver que a opção \ ``Gestão 
de Relacionamento com o Cliente`` \ já está marcada porque esse aplicativo comercial foi instalado neste banco de dados.

Instalar aplicações extra simplesmente marcando as opções correspondentes e clicando :guilabel:`Install` ou clique em :guilabel:`Skip`
para parar a configuração. Você acabará por também entrar em toda a :guilabel:`CRM Application Configuration`
passo que você pode usar para adicionar funcionalidades ao seu aplicativo de CRM. Por agora, selecione a \ ``Claims`` \ opção e 
clique em :guilabel:`Configure`. Este, por sua vez instala o módulo :mod:`crm_claim`.

.. figure:: images/reconfigure_wizard.png
   :scale: 75
   :align: center

   *Assistente de reconfigurar mostrando a aplicação Gestão de Relacionamento com o Cliente como instalado*

Você pode continuar adicionando funcionalidades desta maneira, pule as etapas de configuração ou simplesmente saia do assistente.
Quando você sente a necessidade de carregar o sistema com recursos adicionais, você pode chamar o assistente :guilabel:`Reconfigure`
novamente a qualquer momento.

.. note:: Você também pode alterar o Assistente de Configuração através do :menuselection:`Administration --> Configuration --> 
Configuration Wizards --> Configuration Wizards`.

Instalando um aplicativo / Módulo da lista Módulos
--------------------------------------------------------

.. index::
   single: module; google maps

Agora você vai instalar um módulo chamado :mod:`google_map`, o que permitirá que você adicione um recurso para a forma parceiro para abrir
o local diretamente no Google Maps. Esta é parte da instalação do núcleo, assim você não precisa carregar nada para fazer este trabalho.

Abra a lista de módulos a partir de :menuselection:`Administration --> Modules --> Modules`. Pesquisa do módulo digitando
o nome :mod:`google_map` no campo :guilabel:`Name` na tela de pesquisa, em seguida, clicando-o na lista que aparece para abri-lo.
A descrição do módulo dá informações úteis, como seu número de versão, seu status e uma revisão de sua
funcionalidade. Clique em :guilabel:`Schedule for Installation` e o estado do módulo muda para :guilabel:`To be installed`.

.. tip:: A partir de agora você pode programar e instalar os módulos de visão de lista também. Observe os botões do lado
direito e o botão de ação para instalar.

.. figure:: images/install_google_map_module.png
   :scale: 75
   :align: center

   *Instalação do módulo Google Maps*


.. tip::  Guia Técnico

	Se você selecionar um módulo em qualquer uma das listas do módulo, clicando em uma linha de módulo e, em seguida,no canto superior
direito da janela
	:guilabel:`Technical Guide`, o OpenERP produz um relatório técnico
nesse módulo. É útil somente se o módulo está instalado.

	Este relatório inclui uma lista de todos os objetos e todos os campos, juntamente com suas descrições.
O relatório se adapta ao seu sistema e reflete as modificações que você fez e todos os outros
módulos que você instalou.

Então, use o menu :menuselection:`Administration --> Modules --> Apply Scheduled Upgrades`, ou a partir da seção :guilabel:`Actions` 
clique em :guilabel:`Apply Scheduled Upgrades`, então :guilabel:`Start update` no :guilabel:`Module Upgrade`
o formulário que aparece. Feche a janela quando a operação for concluída. Volte para o menu :guilabel:`Sales`; você irá
ver que o novo menu :menuselection:`Products` tornou-se disponível.

.. tip:: Atualizando o menu no cliente GTK

	Depois de uma atualização no cliente GTK você terá que abrir um novo menu para atualizar o conteúdo –
	caso contrário você não verá o novo item de menu. Para fazer isso, use o menu da janela :menuselection:`Form -->
	Reload / Undo` ou use o atalho :kbd:`Ctrl+R`.

Instalar um módulo com as suas dependências
-------------------------------------------

.. index::
   single: module; stock

Agora instale o módulo de Gestão de Armazém usando o mesmo processo como antes.
Iniciar a partir de :menuselection:`Administration --> Modules --> Modules`.

	#.  Obter a lista de módulos, e procure o módulo :mod:`stock` nesta lista
	
	#.  Agendar o módulo para instalação clicando em :guilabel:`Schedule for Installation`.
	
	#.  Faça o mesmo para :mod:`account`. 
	
	#.  Clique na barra de ferramentas de ação para a direita. :guilabel:`Apply Scheduled Upgrades`.

	#.  Clique em :guilabel:`Start update`para instalar os dois módulos.
	
	#.  Após alguns segundos, quando a instalação estiver completa, você pode fechar esta caixa de diálogo.
	
	#.  Você vai ver detalhes de todos os recursos instalados pelos módulos em uma nova aba
	    :guilabel:`Features` no formulário do módulo. 

Quando você retornar ao menu :menuselection:`Warehouse`, você encontrará os novos itens de menu abaixo dele como
:menuselection:`Warehouse --> Warehouse Management --> Incoming Shipments`, :menuselection:`Warehouse --> Products Moves`, 
que são uma parte do sistema de gestão de armazém. Você também verá todas as funções de contabilidade que estão agora 
disponíveis no menu :menuselection:`Accounting`.

Não há nenhuma relação particular entre os módulos instalados e os menus acrescentados. A maioria dos
módulos principais adiciona menus completos, mas alguns também acrescenta submenus aos menus que já estão no sistema. Outros
módulos adicionam menus e submenus de acordo com a necessidade. Os módulos podem também adicionar campos extras,
formulários ou dados de demonstração adicionais ou simplesmente algumas configurações específicas para um determinado requisito.

.. index::
  single: module; dependencies
..

.. note::  Dependências entre os módulos

	O formulário de módulos mostra duas abas antes de ser instalado
	O primeira guia dá informações básicas sobre o módulo, e a
segunda dá uma lista de módulos que este módulo depende. Então, quando você instalar um módulo, o OpenERP
seleciona automaticamente todas as dependências necessárias para instalar este módulo.

	Que é também a forma como você desenvolve os módulos perfil: ele simplesmente define uma lista de módulos que você quer
em seu perfil como um conjunto de dependências.

Embora você possa instalar um módulo e todas as suas dependências de uma só vez, você não pode removê-los em uma
só vez –você teria que desinstalar módulo a módulo. Desinstalar é mais complexo do que
instalar, porque você tem que lidar com os dados do sistema existente.

.. note::  Módulos de desinstalação

	Embora ele funcione muito bem, a desinstalação de módulos não é perfeita no OpenERP. Não é garantido
poder retornar o sistema exatamente ao estado em que estava antes da instalação.

	Por isso, é recomendável que você faça um backup do banco de dados antes de instalar seus novos módulos, para
que você possa testar os novos módulos e decidir se eles são adequados ou não. Se eles não forem, então
você pode voltar para o seu backup. Se forem, então você pode ainda reinstalar os módulos do
seu backup para que não tenha que apagar todos os dados de teste.

	Se você quiser desinstalar, você usará o menu :menuselection:`Administration --> Modules
	--> Modules` e, em seguida, desinstalá-los na ordem inversa das suas
dependências: ``stock``, ``account``.

Instalando Funcionalidades adicionais
------------------------------------

Para descobrir toda a gama de possibilidades OpenERP, você pode instalar vários módulos adicionais.
Instalá-los com seus dados de demonstração fornece uma maneira conveniente de explorar todo o núcleo
do sistema. Quando você constrói sobre o banco de dados \ ``openerp_ch02``\, você vai incluir automaticamente
dados de demonstração, porque você marcou a caixa de seleção  :guilabel:`Load Demonstration Data` quando você originalmente
criou o banco de dados.

.. index::
   single: module; importing
..

Clique em :menuselection:`Administration --> Modules --> Modules` para lhe dar uma
visão geral de todos os módulos disponíveis para instalação.

Para testar vários módulos, você não terá que instalá-los todos um por um. Você pode usar as dependências
entre os módulos para carregar vários de uma vez.

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

