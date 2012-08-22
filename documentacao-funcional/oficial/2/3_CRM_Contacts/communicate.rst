
.. _part2-crm-communicate:

.. index::
   single: module; outlook, thunderbird
   single: module; fetchmail
   single: gateway

Conectar-se com seu e-mail e acessar a partir do seu dispositivo móvel
======================================================================

 *OpenERP fornece todas as informações que você precisa para buscar oportunidades de negócios da sua empresa de forma eficaz. Mas para se manter produtivo com todas as informações que você tem que manipular, é essencial que você possa continuar usando suas ferramentas de comunicação normal por interface com OpenERP, e que você não está limitado apenas à interface do OpenERP.*

Muitas vezes as pessoas as suas vendas já estão acostumados a trabalhar com clientes de e-mail padrão para gerenciar seus negócios. OpenERP permite integrar perfeitamente os seus conhecimentos com o uso do OpenERP. 

OpenERP oferece esta flexibilidade para aqueles que precisam de continuar a usar seus programas de e-mail tradicionais para manter a sua eficiência: OpenERP pode ser conectado ao Outlook e Thunderbird. Seus usuários podem participar em muitas OpenERP mantida processos sem nunca deixar seu ambiente familiar, e pode evitar a dupla entrada de dados, mas facilmente ligar as informações ao banco de dados OpenERP automaticamente .

Com o Outlook e plug-ins do Thunderbird, você pode criar e/ou abrir contatos diretamente do seu cliente de e-mail em OpenERP sem esforço.
Você também pode vincular-mails (com anexos) para OpenERP, para evitar que informações se percam.
Ambos os plug-ins permitem por exemplo, para criar ligações com base no intercâmbio que você tem com o cliente.

A funcionalidade de gateway de e-mail permite que você use CRM OpenERP sem necessariamente usar a interface OpenERP. Dia a dia levam podendo ser automaticamente armazenada em OpenERP apenas enviando e recebendo e-mails através de um endereço de e-mail específico. uma mails até mesmo responder a tal da caixa de correio própria.

E, claro, você pode vincular o calendário de reuniões OpenERP para o seu dispositivo móvel.

.. _ch-crm-fetchmail:

Ferramentas de Comunicação
--------------------------

.. index:: fetchmail

O Fetchmail * / * mailGateway a funcionalidade permite a interface do CRM com e-mails recebidos e enviados. Assim, você pode receber e-mails em OpenERP e respondê-las diretamente do OpenERP.
Você pode instalá-lo quando você configurar o CRM, por meio da Reconfigure `assistente,` Fetch Emails `, ou instalando o: mod:` fetchmail módulo `a partir da lista de módulos.
Graças a esta característica, cada e-mail que você receberá no endereço de e-mail especificado pode criar automaticamente uma ligação, um contato ou um outro objeto no OpenERP, mantendo a leitura de anexos de e-mail. Esta é uma maneira fácil de garantir que nenhuma informação importante se perda em vendas.

Você define o endereço de e-mail genérico que pretende utilizar, tais como vendas@minhaempresa.com, e então você diz OpenERP que cada e-mails para este endereço devem ser automaticamente criado como um lead.

.. tip:: Objetos

      Você pode usar esse recurso para qualquer objeto em OpenERP, assim, por exemplo, também para acompanhar o seu helpdesk ou pedidos de emprego.

Para usar o e-mai do gateway , você deve instalar o módulo `` Fetchmail. Você pode precisar de um administrador do sistema para realizar este trabalho.

Se você seguiu os passos nos capítulos anteriores, você deve ter o `` Fetchmail módulo instalado. Se não, você pode instalar o módulo `Fetchmail` a partir do Assistente de Configuração (CRM Assistente de Configuração, de sincronização, Fetch e-mails), ou a partir da lista de módulos.

.. note:: Ação programada

       Clique no botão `` Fetch email `` para obter os e-mails diretamente. OpenERP também cria automaticamente um **Ação programada**  para buscar os e-mails a cada 5 minutos.

*Passo 1*

Você pode configurar sua conta de correio de entrada (s) a partir de :menuselection:`Sales --> Configuration --> Emails --> Email Servers`.

.. figure::  images/email_server_config.jpeg
   :scale: 80
   :align: center

   *How to Configure your Email Server for Incoming Mails?*

Vá em :menuselection:`Tools --> Configuration --> Email Template --> Email Accounts` to define the email smtp settings.

No campo ``Description``, digite o nome visível que você gostaria de usar como a conta.

No ``Server``, tipo do email do servidor, ex: smtp.googlemail.com.

Digite a porta SMTP (por exemplo, 587), configure as outras configurações de acordo com as especificações do seu servidor.

Adicione as informações do usuário, como endereço de e-mail para o qual os e-mails entrará OpenERP, support@mycompany.com ou seja, o nome de usuário ea senha. Configure as outras opções para suas necessidades.

Salve e clique no botão ``Test Outgoing Connection`` para verificar se as configurações estão corretas.

Quando tudo estiver corretamente configurado, `Aprovar` a conta. OpenERP irá criar automaticamente um agendador de e-mails. Você também pode enviar/receber e-mails manualmente, clicando no botão ``Enviar/Receber``.

*Passo 2*

Você pode configurar sua conta(s) de correio de saída em :menuselection:`Tools --> Configuration --> Email Template --> Email Accounts`.

.. figure::  images/outgoing_server_config.jpeg
   :scale: 80
   :align: center

   *Como configurar seu servidor de e-mail para mails de saída?*

Vá em Vendas > Configuração > Emails > Email Servers para definir as configurações do servidor de e-mail.

Atribua um ``Nome`` e selecione o  ``Tipo de Servidor``, ex IMAP Server.

Clique em ``Adicionar Anexos`` se você quiser incluir anexos para os e-mails recebidos / enviados.

Digite a Informação do Servidor, cheque SSL se necessário, ex imap.googlemail.com e as informações de login.

Você também pode optar por enviar uma resposta automática de recebimento do email. Você pode configurar o e-mail aqui no campo ``Email Server Action``.

Atribua o ``Modelo`` para usar quando um e-mail novo chega, ex escolha Lead (crm.leads) se você quiser a cada novo e-mail que chega a ser criado como uma lead. 

Clique em `Confirmar` para confirmar as configurações da conta.

.. note:: Configuração do Servidor

       Você também vai precisar de o administrador para configurar as definições de seu servidor para permitir um gateway de e-mail. TIsso não será explicado
       neste livro.

.. index:: Outlook (Microsoft)

.. _outl:

Gerir o seu CRM do Microsoft Outlook
------------------------------------

O Microsoft Outlook plug-in permite que você realize uma série de operações OpenERP forma rápida e direta
a partir do cliente de e-mail Outlook:

* crie um contato ou parceiro de um e-mail,

* abra um parceiro de um e-mail,

* salve um e-mail e seus anexos no OpenERP da caixa de correio,

* senvie qualquer anexo de um documento OpenERP (tais como oportunidades, clientes).

Graças ao plug-in, você pode facilmente ligar e-mails e anexos correspondentes a oportunidade no OpenERP, ou vincular uma pasta do produto ligado a um cliente, por exemplo.

.. tip:: Versões Outlook

	O Microsoft Outlook plug-in funciona com o Microsoft Outlook 2003 e 2007, mas não com o Outlook Express.

Neste capítulo, apenas as possibilidades reais do plug-in será discutido. Para mais informações sobre como instalar e configurar o Outlook plug-in, consulte o capítulo :ref:`outlook`.

Na barra de ferramentas do Outlook, de uma olhada em  :menuselection:`Tools` menu.

Uma opção `empurrar` permite-lhe o arquivamento dos e-mails para OpenERP, quer para novos tipos de documentos ou para os já existentes (como Leads). Ele também permite que você crie um novo contato.

A opção `Parceiro` permite que você abra o parceiro no OpenERP de acordo com o e-mail selecionado (ex contactar endereço de email). 

Com o `Documento`, você pode abrir o documento (ex um cliente, uma oportunidade) no OpenERP. Verifique se o seu servidor web está sendo executado para utilizar esta funcionalidade.. 

.. figure::  images/outlook_config2.png
   :scale: 100
   :align: center

   *Como acessar OpenERP a partir do Outlook?*

* Víncule um e-mail a um documento existente no OpenERP

Para arquivar um e-mail no OpenERP a partir do Outlook, selecione o e-mail e clique no botão`Empurrar`. Alternativamente, você pode abrir o menu :menuselection:`Tools --> Push`: the ``Push to OpenERP`` tela será aberta.

Na seção ``Vincular um documento existente``, cheque *Parceiro*. Em seguida, selecione o cliente que você deseja anexar o e-mail selecionado para.
O plug-in também permite que você selecione vários clientes ao mesmo tempo, simplesmente selecionando um cliente e pressionar o botão ``ctrl`` ao selecionar o próximo.

SSuponha que você decida não mais vincular o e-mail selecionado para um cliente, mas sim uma oportunidade. Então você tem que clicar no botão ``Pesquisar`` para atualizar a lista de `Documentos` para mostrar as suas oportunidades.    

A partir da lista de documentos disponíveis, você pode selecionar qualquer tipo de documento definido na seção ``Configurações do documento``. 

* Criar um novo documento

Este recurso pode ser usado para criar qualquer um dos tipos de documentos configurados na aba ``Configurações do documento``.
Supomos você gostaria de criar um novo lead a partir de um e-mail. Na seção ``Criar um novo documento`` , Selecione ``CRM Lead``, em seguida, clique no botão ``Criar``. AA novo lead será criada no do e-mail selecionado do OpenERP.

* Criar um novo contato / Parceiro

Se o parceiro ou entrar em contato de seu e-mail não existe no OpenERP ainda, o Outlook plug-in permite que você
crie um em tempo real simplesmente usando as informações contidas no e-mail.

Selecione o e-mail a partir do qual você quer criar um novo contato, em seguida clique no botão ``Empurrar``.
Na seção ``Crie um novo contato``, clique no botão ``novo contato``. Esta opção oferece duas possibilidades:
quer você apenas crie um contato (endereço), ou crie um parceiro com o contato ligado a ela.

	- Quando você quer apenas criar um novo contato, complete os dados de endereço na caixa de diálogo e clique no botão ``Salvar``.
	  O contato será então criado em OpenERP.

	- Quando você também deseja criar um novo parceiro, completa o contato data.34
	  Em seguida, clique no botão ``Crie um Parceiro``, adicione o nome do parceiro e clique no botão ``Salvar``.

	- Você também pode adicionar um novo contato para um parceiro existente. Clique no botão ``Pesquisar`` próximo ao campo Parceiro e selecione o parceiro correspondente da lista. Em seguida, preencha os dados de contato e clique no botão ``Salvar``.

.. figure::  images/outlook_creation.png
   :scale: 100
   :align: center

   *Criando um contato no Fly a partir do Outlook*

* Abra o documento criado no OpenERP

Da caixa de correio, simplesmente clicando em um e-mail, você pode acessar diretamente os dados correspondentes no OpenERP. Vá para o menu :menuselection:`Tools --> Document` que irá abrir o documento correspondente no OpenERP (ex uma lead), directamente a partir do e-mail que você selecionou.

.. tip:: Gestão do Conhecimento

	O Outlook plug-in é compatível com a Gestão de conhecimento do OpenERP (ex Documento). Se você instalar o aplicativo Conhecimento você será capaz de:

	* pesquisa através do conteúdo de documentos da sua empresa (os que o tipo .doc, .pdf, .sxw
	  and .odt) e também em e-mails arquivados,

	* ter um sistema de arquivos compartilhado que está ligado a vários documentos OpenERP para compartilhar informações e
	  acessá-lo com seu navegador favorito,

	* organizar e estruturar os seus documentos no sistema OpenERP(tais como projetos, parceiros e usuários).

* Passo 1: Instalar o plugin Outlook no OpenERP

Use o Assistente de Configuração OpenERP e instale a aplicação ``Customer Relationship Management``. Na *Configuração de aplicação do CRM* diálogo em Plug-In, selecione `MS-Outlook`.
Em seguida, o *Outlook Plug-In * assistente aparece. Ao lado do campo ``Outlook Plug-in``, clique no botão ``Salvar como`` para salvar o plug-in para o seu desktop (ou qualquer outro local no seu computador).

Você também pode baixar o manual de instalação, clicando na seta verde ao lado de ``instalação manual``.  

Outra maneira de usar o plug-in Outlook, é instalando o módulo OpenERP \
``outlook``\. Quando você instalar esse módulo, o mesmo Assistente de Configuração explicado anteriormente será exibido. Siga as mesmas instruções.. Siga as mesmas instruções.


* Passo 2: Pré-requisitos (para mais detalhes, consulte a documentação on-line)

  1. Instale Python 2.6+

  2. Python para extensões do Windows - PyWin32, este módulo para python deve ser instalado para a versão apropriada do Python.

  3. Especificar a pasta python no caminho do sistema (tipicamente com este instalador C:\Python26)

  *Como definir o caminho no Windows XP*
  Para o Windows XP: http://www.computerhope.com/issues/ch000549.htm
    
  *Como definir o caminho no Windows 7*
  Para alterar as variáveis ​​de ambiente do sistema, siga os passos abaixo. 

   - A partir do botão do Windows, selecione ``Painel de controle``, clique em ``Sistema``. 
   - Clique em ``Configurações Remotas`` para abrir a janela Propriedades do sistema.
   - Na janela Propriedades do Sistema, clique na guia Avançado. 
   - Na seção Avançado, clique no botão ``Variáveis ​​de ambiente``. 
   - Finalmente, na janela Variáveis ​​de ambiente (como mostrado abaixo) em Variáveis ​​do Sistema, destaque o caminho do diretório,
     clique em Editar e adicionar ;C:\Python26.

  4. Se você estiver usando o MS Outlook 2007, então você é obrigado a instalar "Microsoft Exchange Server MAPI Client and Collaboration
  Data Objects 1.2.1 (CDO 1.21)"
  Dê um duplo clique em Exchange CDO para instalá-lo.

  5. Se você estiver usando o MS Outlook 2003, não se esqueça de instalar o componente embutido CDO.


* Passo 3: instale a extensão OpenERP no Outlook.

	#. De dois cliques no arquivo \``OpenERP-Outlook-addin.exe``\ que você salvou no seu desktop. Confirme as configurações padrão.

	#. De dois cliques no arquivo \``Register plugin``\ na pasta OpenERP Outlook Addin folder (typically in C:\Program Files).

	#. Inicie o Outlook.

Quando você tiver executado Instalação Passo 1, Passo 2 e Passo 3, a primeira coisa a fazer é conectar o Outlook ao OpenERP.
Pouca configuração precisa ser feita.

.. tip:: Barra de Ferramentas

      Se você quiser que a conexão OpenERP para ser mostrada como uma barra de ferramentas separadas, vá no menu :menuselection:`View --> Toolbars`. Select ``OpenERP``.

* Vá no menu :menuselection:`Tools` and select `Configuration`. Se isso gera um erro, não se esqueça de verificar os direitos de acesso a essa pasta específica.

A janela de configuração será exibida para que você possa inserir os dados de configuração sobre o servidor OpenERP.

.. figure::  images/outlook_menu2.png
   :scale: 75
   :align: center

   *Como se conectar ao servidor*

	#. Na aba ``Definições de configuração`` , em *Parâmetros de conexão* clique no botão `Alterar`
	   e digite as configurações do servidor e a porta XML-RPC , ex ``http://127.0.0.1:8069``,

	#. Selecione o banco de dados você deseja se conectar e digite o usuário ea senha necessários para efetuar login no banco de dados,

	#. Clique no botão `Conectar´.

	#. Na aba ``Definições de configuração``, em *Parâmetros webserver* clique no botão `Alterar`
	   e digite as configurações do servidor web, ex ``http://localhost:8080``,

	#. Clique no botão `Abrir` para testar a conexão.

Quando a ligação foi bem sucedida, normalmente você deseja configurar o Outlook para atender às suas necessidades.

Para definir os tipos de documentos extras, vá na aba `Configurações do documento`. Este é o lugar onde você pode adicionar objetos de OpenERP que você deseja vincular mails para. A instalação padrão vem com um número de documentos pré-definidos, tais como parceiros, Leads e pedidos de vendas.

Aqui está um exemplo de como configurar os tipos de documentos extras. Suponha que você gostaria de vincular mails para uma reunião:

	#. No `Título`, tipo ``Reunião``,

	#. No `Documento`, tipo de objeto de OpenERP, neste exemplo ``crm.meeting``,

	#. Na `Imagem`, selecione um ícone que você gostaria de usar,

	#. Clique no botão `Adicionar` para realmente criar o tipo de documento.

.. note:: Uma palavra sobre Objetos

       Para encontrar o objeto que você precisa em OpenERP, vá no menu :menuselection:`Administration --> Customization --> Database Structure -->
       Objects`. OpenERP só vai mostrar objetos para o qual o correspondente Aplicações de Negócios / Módulos que tiverem sido instalados
       Você só pode adicionar objetos ao Outlook que estão disponíveis no banco de dados selecionado.

.. index::
   single: Thunderbird (Mozilla)

.. _thunder:

Gerenciando seu CRM no Mozilla Thunderbird
------------------------------------------

Com o Mozilla Thunderbird plug-in você pode realizar uma série de operações OpenERP diretamente do Thunderbird, tais como:

* crie um contato ou parceiro a partir de um e-mail,

* abra um parceiro a partir de um e-mail,

* salve um e-mail e seus anexos no OpenERP,

* envie qualquer anexo de um documento OpenERP (tais como oportunidades, clientes).

Graças ao plug-in, você pode facilmente ligar e-mails e anexos correspondentes a oportunidade no OpenERP, ou vincular de uma pasta de produtos ligados a um cliente, por exemplo.

Neste capítulo, apenas as possibilidades reais do plug-in serão discutidos. Para mais informações sobre como instalar e configurar o Thunderbird plug-in, por favor consulte o capítulo :ref:`thunderbird`.

Na barra de ferramentas Thunderbird, Na barra de ferramentas Thunderbird, veja em o :menuselection:`OpenERP` menu.

A opção `Empurrar` permite-lhe arquivar e-mails para OpenERP, tanto para novos tipos de documentos ou para os já existentes. Ele também permite que você crie um novo contato.

O `Parceiro` permite que você abra o parceiro no OpenERP de acordo com o e-mail selecionado (ex endereço de email do contato). 

Com o `Documento`, você pode abrir o documento concedido no OpenERP(ex um cliente, uma oportunidade). Verifique se o seu servidor web está sendo executado para utilizar esta funcionalidade. Você tem que abrir o e-mail para usar este recurso. 

* Víncule um e-mail a um documento existente no OpenERP

.. figure::  images/thunderbird_selection.png
   :scale: 100
   :align: center

   *Como acessar OpenERP no Thunderbird?*

Para arquivar um e-mail no OpenERP a partir do Thunderbird, selecione o e-mail e clique no botão `Empurrar`. Alternativamente, você pode abrir o menu :menuselection:`OpenERP --> Push`: the ``Push to OpenERP`` tela será aberta.

Na seção ``Vincule um documento existente``, cheque o *Parceiro*. Em seguida, selecione o cliente que você deseja anexar o e-mail selecionados para.
O plug-in também permite que você selecione vários clientes ao mesmo tempo, simplesmente selecionando um cliente e pressionar o botão ``ctrl``  ao selecionar o próximo.

Suponha que você decida não mais vincular o e-mail selecionado para um cliente, mas sim uma oportunidade. Então você tem que clicar no botão ``Pesquisar`` para atualizar a lista `Documentos` para mostrar as suas oportunidades.    

Da lista de documentos disponíveis, você pode selecionar qualquer tipo de documento que você definiu na seção ``Configurações do documento``. 

* Criar um novo documento

Este recurso pode ser usado para criar qualquer um dos tipos de documentos configurados na guia ``Configurações do documento``.
Suponha que você gostaria de criar uma nova pista a partir de um e-mail. Na seção ``Criar um novo documento``, selecione ``CRM Lead``, em seguida, clique no botão ``Criar``. Um novo lead será criada no OpenERP apartir do e-mail selecionado.

* Criar um novo contato / Parceiro

Se o parceiro ou contato a partir de seu e-mail não existe no OpenERP ainda, o plug-in do Thunderbird permite que você
criar um em tempo real simplesmente usando as informações contidas no e-mail.

Selecione o e-mail a partir do qual você quer criar um novo contato, clique no botão ``Empurrar``.
Na seção ``Criar um novo contato``, clique no botão ``Novo contato``. Esta opção oferece duas possibilidades:
seja você acabou de criar um contato (endereço), ou criou um parceiro com o contato ligado a ela.

	- Quando você quer apenas criar um novo contato, complete os dados de endereço na caixa de diálogo e clique no botão ``Salvar`` .
	  O contato será então criada em OpenERP

	- Quando você também deseja criar um novo parceiro, complete os dados de contato.
	  Em seguida, clique no botão ``Criar Parceiro``, adicione o nome do parceiro e clique no botão ``Salve``.

	- Você também pode adicionar um novo contato para um parceiro existente. Clique no botão ``Pesquisar`` ao lado do campo Parceiro
e selecione o sócio correspondente da lista. Em seguida, preencha os dados de contato e clique no botão ``Salvar``.

.. figure::  images/thunderbird_creation.png
   :scale: 75
   :align: center

   *Criando um contacto em tempo real no Thunderbird*

* Abra o documento criado no OpenERP

Da caixa de correio, simplesmente clicando em um e-mail, você pode acessar diretamente os dados correspondentes no OpenERP. Vá para o menu :menuselection:`Tools --> Document` que irá abrir o documento correspondente no OpenERP(ex um lead), directamente a partir do e-mail que você selecionou.

.. tip:: Gestão de Conhecimento

	O plug-in do Thunderbird é compatível com a gestão de conhecimento do OpenERP (ex. Documento). Se você instalar o
Aplicação do conhecimento, você será capaz de:

	* pesquisa através do conteúdo de documentos da sua empresa e também em e-mails arquivados (aqueles que têm o tipo .doc, .pdf, .sxw
	  and .odt),

	* ter um sistema de arquivos compartilhado que está ligado a vários documentos OpenERP para compartilhar informações e
acessá-lo com seu navegador favorito,

* Passo 1: Instale o plugin Thunderbird no OpenERP

Use o Assistente de Configuração OpenERP e instalar o aplicativo ``Gestão de Relacionamento com o Cliente``. No diálogo *Configuração de Aplicação CRM* sob Plug-In, selecione `Thunderbird '
Em seguida, aparece o assistente *Thunderbird Plug-In* . Ao lado do campo ``Thunderbird Plug-in`` , clique no botão ``Salvar como`` para salvar o plug-in em seu desktop (ou qualquer outro local no seu computador).

Você também pode baixar o manual de instalação, clicando na seta ao lado de laranja ``Manual de instalação``.  

Outra maneira de usar o plugin Thunderbird, é instalando o módulo OpenERP \
``thunderbird``\. Quando você instalar esse módulo, o Assistente de Configuração mesmo explicado anteriormente será exibido. Siga as mesmas instruções.

* Passo 2: Instalar a extensão OpenERP no Thunderbird.

Para fazer isso, use o arquivo \``openerp_plugin.xpi``\ que você salvou no seu desktop.

Em seguida, proceda da seguinte forma:

	#. A partir doThunderbird, abra o menu :menuselection:`Tools --> Add-ons`.

	#. Clique em Extensões, clique no botão `Instalar` .

	#. Vá para o seu desktop e selecione o arquivo \ ``openerp_plugin.xpi``\. Clique em Abrir.

	#. Clique `Instalar agora` em seguida, reinicie o Thunderbird.

Uma vez que a extensão foi instalado, um novo item do menu"OpenERP" é adicionado ao seu menu do Thunderbird.

.. tip::  Versões Thunderbird  

	O plugin OpenERP para Thunderbird funciona a partir do Thunderbird versão 2.0.

	Portanto, verifique a sua versão Thunderbird antes de instalar e baixar a última versão que você precisa
no seguinte endereço : http://www.mozilla.org/products/thunderbird/

Quando você tiver executado Instalação Passo 1 e Passo 2, a primeira coisa a fazer é se conectar Thunderbird no OpenERP.
Um pouco de configuração precisa ser feito.

.. note:: Antes de iniciar a configuração, verifique se o servidor GTK e servidor web está executando (deve ser permitido XML-RPC).

Vá na barra de menu ``OpenERP`` e selecione ` Configuração`.

A janela de configuração será exibida para que você possa inserir os dados de configuração sobre o servidor OpenERP

.. figure::  images/thunderbird_config.png
   :scale: 75
   :align: center

   *Como se conectar ao servidor*

	#. Na guia ``Definição de configuração``, clique em *Parâmetros de conexão* clique no botão `Alterar` 
	   e digite as configurações do servidor e porta XML-RPC, ex. ``http://127.0.0.1:8069``,

	#. Selecione o banco de dados você deseja se conectar e digite o usuário e a senha necessários para efetuar login no banco de dados,

	#. Clique no botão `Conectar`,

	#. Na aba ``Definição de configuração``, em *Parâmetros do servidor web* clique no botão `Alterar`
	   e digite as configurações do servidor web, ex. ``http://localhost:8080``,

	#. Clique no botão `Abrir` para testar a conexão.

Quanto a  sua conexão, foi bem sucedida, normalmente você deseja configurar o Thunderbird para atender às suas necessidades

o definir os tipos de documento extra, vá para a aba `Configurações do documento`. Este é o lugar onde você pode adicionar objetos de OpenERP que você deseja vincular mails. A instalação padrão vem com um número de documentos pré-definidos, tais como parceiros, Leads e Pedidos de Vendas

Aqui está um exemplo de como configurar os tipos de documentos extra. Suponha que você gostaria de vincular mails a uma ordem de compra.

	#. No `Título`, tipo ``ordem de compra``,

	#. No `Documento`, o tipo do objeto a partir OpenERP, neste exemplo ``purchase.order``,

	#. Na `Imagem`, selecione um ícone que você gostaria de usar,

	#. Clique no botão `Adicionar` para realmente criar o tipo de documento.
.. note:: Uma palavra sobre os Objetos

       Para encontrar o objeto que você precisa em OpenERP, vá ao menu :menuselection:`Administration --> Customization --> Database Structure -->
      Objetos`. O OpenERP só vai mostrar objetos para o qual o correspondente as Aplicações de Negócios / Módulos foram instalados.
       Você só pode adicionar objetos ao Thunderbird que estão disponíveis no banco de dados selecionado.

.. figure::  images/thunderbird_document.png
   :scale: 75
   :align: center

   *Como adicionar tipos de documentos extras do OpenERP para o Thunderbird?*
   * organizar e estruturar os seus documentos no sistema de OpenERP. (como projetos, parceiros e usuários).
.. _ch-sync1:

Sincronizar o seu CRM com dispositivos móveis
---------------------------------------------

sincronizar seus calendários OpenERP com o seu dispositivo móvel e sei que encontro para ir para onde quer que esteja!

Faça o seu OpenERP ainda mais eficiente e deixe suas vendas sincronizar as suas reuniões com seus dispositivos móveis.
Em qualquer lugar seu pessoal de vendas são, eles podem facilmente verificar seu planejamento e confirme novas reuniões com os clientes no local.

Você pode sincronizar seus calendários com o iPhone e telefones Android, e também com ferramentas como o Evolution e Sunbird / Lightning

.. note:: Instalação e Configuração

       Por favor note que essa configuração requer algum conhecimento técnico e, provavelmente, a assistência da equipe de TI.

.. index::
   single: mobile; caldav; Android; iPhone; Sunbird; Evolution; Lightning

.. _mobile:

Servidor OpenERPe Configuração SSL
++++++++++++++++++++++++++++++++++
Alguns módulos precisam ser instalados no servidor OpenERP (ou pode já estar instalado). estes são:

    - :mod:`caldav`: Necessário, ter a configuração de referência e o necessário os 
             código subjacentes. Também fará com que documentos e document_webdav
             seja ser instalado.
    - :modo:`crm_caldav`: Opcional, vai exportar os Encontros CRM como um calendário.
    - :modo:`project_caldav`: Opcional, vai exportar tarefas do projeto como um calendário.
    - :modo:`http_well_known`: Opcional, experimental. Vai facilitar bootstrapping,
             mas apenas quando um registro DNS SRV também é usado.

Quando você instalar o módulo(s) acima, quando estiver pronto para ir, uma configuração de referência das pastas é fornecida.
O administrador do OpenERP pode adicionar mais calendários e (re) estrutura, se necessário.

É altamente aconselhável que você também configurar SSL para trabalhar no servidor OpenERP. HTTPS é uma característica de todo o servidor no OpenERP, o que significa um
certificado será definido no OpenERP server.conf, que será o mesmo para XML-RPC, HTTP, WebDAV e CalDAV.
O iPhone também suporta conexões seguras com SSL, apesar de não esperar um certificado auto-assinado (ou que não é verificado por
um dos "grandes" certificado de autoridades).

Calendários no iPhone
+++++++++++++++++++++

Para configurar os calendários, proceda da seguinte forma:

1. Clique em ``configurações`` e vá na página ``Mail, Contatos, Calendários``.

2. vá em ``Adicionar conta...``

3. Clique em ``Outros`.

4. A partir do grupo ``Calendários``, selecione ``Adicionar Conta CalDAV``.

5. Digite o nome do host.
   (ex. se a URL é http://openerp.com:8069/webdav/db_1/calendars/ , openerp.com é o host)

.. tip:: Sincronize este calendário

      Vá em :menuselection:`Sales --> Meetings --> Synchronize this Calendar` e selecione ``Iphone``. Em seguida, o servidor CalDAV será mostrado.

6. No ``Nome de Usuário`` e ``senha``, type your OpenERP login and password.

7. Como uma descrição, você pode deixar o nome do servidor ou
    algo parecido "calendários OpenERP".

8. Se você não estiver usando um servidor SSL, você obterá um erro, não se preocupe e empurre "continuar"

9. Clique em "Configurações avançadas" para especificar as portas corretas e caminhos.
    
10. Especifique as informações sobre o servidor OpenERP: 8071 como SSL, 8069 com SSL.

11. Especifique ``Conta URL`` para o caminho certo do webdav OpenERP
Novo! Segure a tecla Shift pressionada, clique e arraste as palavras acima para reorganizar. Dispensar:
    a URL dada pelo assistente (ex. http://my.server.ip:8069/webdav/dbname/calendars/ )

12. Clique em ``Feito``. O telefone irá se conectar ao servidor OpenERP
     e verificar se a conta pode ser usado.

13. Vá para o menu principal do iPhone e abra o aplicativo Calendário.
     Seus calendários OpenERP será visível dentro da seleção do botão
    "Calendários".
    Note que ao criar uma nova entrada na agenda, você terá que especificar
     calendário que deve ser salvo.

Se você precisar de SSL * * (e seu certificado não é algo verificado),
primeiro você precisa para deixar o iPhone confiar no certificado. Siga estes passos:

1. Abra o Safari e digite o local HTTPS do servidor OpenERP:
   https://my.server.ip:8071/
   (supondo que você tenha o servidor em "my.server.ip" ea porta HTTPS é o padrão 8071)

2. Safari irá tentar se conectar e emitir um aviso sobre o certificado usado. Inspecionar o certificado
    e clique em "Aceitar" para que o iPhone agora confia-lo.

Calendários em Android
++++++++++++++++++++

Pré-requisitos
*************
Não há como built-in para sincronizar calendários com CalDAV.
Então, você precisa instalar um software de terceiros: Calendário (CalDav) Sincronização BETA
Software de Hypermatix (por enquanto, é o único).

Como configurar?
*****************

1. Abrir o aplicativo. ``Calendar Sync``
   Você tem uma interface com 2 abas
   
2. Na aba `Connection`, em CalDAV Calendar URL, digite uma URL como http://my.server.ip:8069/webdav/dbname/calendars/users/demo/c/Meetings.

.. tip:: Sincronizar esse calendário

      Vá em :menuselection:`Sales --> Meetings --> Synchronize this Calendar` e selecione ``Android``. Em seguida, no link servidor CalDAV será mostrado. Certifique-se de usar a porta XML-RPC correta, ela pode diferir 8069.

3. Digite seu nome de usuário e senha do OpenERP.

4. Se o seu servidor não usa SSL, você receberá um aviso. resposta ``Sim``.

5. Depois, você pode sincronizar manualmente ou personalizar as configurações (aba `Sync`) para sincronizar a cada X minutos.

Calendários em Evolução
+++++++++++++++++++++++

1. Vá na Visão em calendário.

2. :menuselection:`File --> New --> Calendar`.

3. Insira os dados no formulário:
 
    - tipo : CalDav
    - Nome : O que você quiser (ex. reunião)
    - URL : http://HOST:PORT/webdav/DB_NAME/calendars/users/USER/c/Meetings (e.g.
      http://localhost:8069/webdav/db_1/calendars/users/demo/c/Meetings) 
     a um dado no topo da janela
    - Desmarque "usuário SSL"
    - Usuário : seu nome de usuário (ex. Demo)
    - Atualize : toda vez que quiser fazer uma atualização para sincronizar os dados com o servidor

.. tip:: Sincronize esse calendário

      Vá em :menuselection:`Sales --> Meetings --> Synchronize this Calendar` e selecione ``Evolution``. então o servidor CalDAV será mostrado.

4. Clique em OK e digite sua senha do OpenERP.

5. Um novo calendário com o nome digitado deve aparecer no lado esquerdo.

Calendários no Sunbird / Lightning
++++++++++++++++++++++++++++++

Pré-requisitos
**************
If Se você estiver usando o Thunderbird, instale primeiro o módulo do Lightning
http://www.mozilla.org/projects/calendar/lightning/

Configuração
*************

1. Vá na Visão em calendário.

2. :menuselection:`File --> New Calendar`.

3. Escolha ``On the Network``.

4. Como um formato, selecione CalDav
e em tipo de local da URL (e.g. http://host.com:8069/webdav/db/calendars/users/demo/c/Meetings).

.. tip:: Synchronize this Calendar

      Vá em :menuselection:`Sales --> Meetings --> Synchronize this Calendar` e selecione ``Sunbird/Lightning``. Em seguida, o servidor CalDAV será mostrado.
  
5. Escolha um nome e uma cor para o Calendário, e aconselhamos que você desmarque "alarme".

6. Digite seu login e senha OpenERP (para dar a senha apenas uma vez, marque a caixa ``Use Gerenciador de Senhas para lembrar esta senha``).

7. Em seguida, clique em Concluir; as suas reuniões devem aparecer agora na sua visão de Calendário.

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



