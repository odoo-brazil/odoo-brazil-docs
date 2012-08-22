
.. _part2-crm-opport:

Otimizando seu Ciclo de Vendas através de Oportunidades
======================================================

Enquanto um prospecto representa um primeiro contato qua ainda deve ser qualificado, uma oprtunidade de vendas representa um contrato em potencial. Cada oprtunidade deve ser acompanhada por um vendedor (ou pela equipe de vendas) que deverá qualificar a oprtunidade, realizando uma cotação ou cancelando a oportunidade. 

Prospectos são, geralmente, tratados em grupos, com a automatização de certas respostas por emails.
Oportunidades, em contrapartida, são geralmente seguidas uma a uma pela equipe de vendas, pois uma oportunidade envolve um processo de negociação com o cliente em potencial.

Assim como para os prospectos, o OpenERP possui funcionalidades específicas para tratar as oportunidades de vendas eficientemente. Todas as oportunidades podem ser encontradas no menu: seleção de menu: Vendas > Vendas > Oportunidades.

Em Oportunidades, você pode gerir e acompanhar suas vendas criando documentos de vendas relacionados a clientes ou prospectos específicos.
Informaços como retorno esperado, fase da oportunidade, data esperada para o fechamento, histórico da comunicação, data da próxima ação, e muito mais podem ser gravadas.

Oportunidades pedem ser conectadas com o email: novos emails podem criar oprtunidades, cada um deles busca automaticamente o histórico da conversa com o cliente.
Você e sua equipe de vendas poderão planejar encontros e chamadas telefônicas a partir de oportunidades, convertê-los em cotações, administrar documentos relacionados, seguir todas as atividades relacionadas aos clientes e muito mais.

.. dica:: Anexos

      Por padrão, você pode manter os anexos no OpenERP para ter certeza que todos os documentos relacionados estarão diretamente acessíceis. 
      Do lado direito da tela, sob "Anexos", clique em "Adicionar" para começar a ligar os documentos a sua oportunidade. Com botão "Pesquisar", você 
      pode procurar pelo arquivo que deve ser anexado nos seus diretórios. Você pode adicionar anexos do mesmo jeito que prospectos, por exemplo.
      Se você também quer que os deocumentos sejam indexados (menos imagens), você deve instalar a "Knowledge Application".

Convertendo Prospectos em Clientes ou Oportunidades
--------------------------------------------------

Se o vendedor pensa que o prospeco é uma verdadeira oportunidade, prosseguindo o contato que ele teve com o prospecto, ele pode facilmente converter o prospecto em um parceiro/oportunidade utilizanndo o bota:guilabel: converter em oportunidade.

O botão "Converter em Oportunidade" oferece diversas possibilidades, impedindo que você duplique parceiros:

* Você pode escolher por simplesmente criar uma oportunidade e manter os dados do contato do prospecto sem criar um parceiro,

* Você pode converter em uma oportunidade, e criar um novo parceiro se ele ainda não existe, ou fundir o contato com um parceiro existente,

* Você pode primeiro criar um parceiro, e depois converter o prospecto em oportunidade. 


Para criar apenas um parceiro, clique em "Criar" próximo ao campo "Cliente". Você também ppode decidir adicionar os dados de contato do prospecto como um novo contato para um parceiro existente.

O OpenERP mostra uma janela com as opções:

*criar um novo parceiro,

*fundir o contato com um parceiro existente.

O OpenERP abre um formulário que contém as informações do prospecto. Nessa etapa você pode completar os detalhes do contato ou adicionar outras informações ao parceiro.

O parceiro criado é automaticamente anexado ao prospecto, o que permite que você mantenha uma traçabilidade completa do prospecto. Para encontrar essa informação, você deve ir na aba "Comunicação & Histórico" no prospecto.

Você também pode combinar o passo de criar um parceiro e direcionar a conversão do prospecto para a criação de uma oportunidade através da funcionalidade "Converter em oportunidade".

.. dica:: Converter em Oportunidade

      Quando você clica em "Converter em Oportunidade" e o endereço de email do contato é preenchido, o OpenERP irá conferir se o email
      corresponde a algum endereço de email de um parceiro já existente. Se sim, o OpenERP irá propor a fusão do novo contato com o parceiro
      encontrado.

Clicando em "Converter Oportunidade" e o parceiro já existe, o OpenERP abre uma janela com as opções:

*criar um novo parceiro,

*fundir o contato com um parceiro existente.

O OpenERP mostra o título da oportunidade (retirada da descrição do prospecto) e do parceiro.
Tenha certeza de haver colocado o retorno esperado e a taxa de sucesso (probabilidade) disse ses converter em vendas.

.. figure:: figure:: images/crm_lead_convert.png
   :scale: 80
   :align: center

   *Convertendo um Prospecto em uma Oprtunidade de Vendas*

.. figure:: images/crm_opport_data.jpeg
   :scale: 100
   :align: center

   *De Prospecto para Oportunidade : Detalhes*

.. _ch-team:


Adaptando o OpenERP para a sua Organização de Vendas
----------------------------------------------------

.. index::
   single: sales

Sua organização de vendas pode ser composta de vários grupos que, por exemplo, endereçam diferentes segmentos de clientes ou geografias, vendem diferentes produtos e serviços e frequentemente administram diferentes ciclos de vendas. Como um administrador você irá querer seguir a performance não apenas individualmente, mas também em por grupo.

O OpenERP permite que você faça isso definindo "Equipes de Vendas". Uma equipe de vendas é um grupo de pessoas que estão ocupando uma posição semelhante. Implementar equipes de vendas é uma ferramenta poderosa, pois permite que:

* Atribua para as equipes de vendas prospectos ou oportunidades de acordo com a natureza deles. E, de acordo com a política da empresa, as oportunidads podem ser atribuídas para um dado indivíduo. Por exemplo, oportunidades podem ser atribuídas para a "equipe de vendas da região oeste" ou para a "equipe de vendas da região leste" dependendo da localização. Cada vendedor pode pegar oportunidades não atribuídas em sua equipe de vendas de acordo com a disponibilidade.

* Você pode agrupar sua equipe de vendas de acordo com sua hierarquia. Isso permite que você tenha uma visão das suas vendas em diferentes níveis (local, regional, nacional, por exemplo).

*Algumas equipes de vendas podem gerir suas oportunidades através de diferentes ciclos de vendas. Por exemplo, uma concessonária que venda para clientes pessoa física e jurídica terá diferentes ciclos de vendas.
 
*Para cada equipe de vendas, você pode designar um usuário responsável e um endereço de email que será usado quando foram criados ou respondidos emails do OpenERP. Isto será proposto por padrão no OpenERP quando você criar um evento para esse cliente.

.. nota:: Equipes de Vendas
        Para definir suas Equipes de Vendas, vá em: menuselection: Vendas --> Configuração --> Vendas --> Equipes de Vendas.

Vamos pegar o exemplo de um banco para explicar como você pode definir suas equipes de vendas. Um banco possui diversos departamentos, como Seguros, Contabilidade, Ativos, Gestão de Crédito. Cada departamento pode ser dividido em subdepartamentos. Para Seguros, poderia ser Seguro de Empresas e Seguro de residências. A estrutura hierárquica da sua equipe de vendas poderia ser:

* Equipe de Vendas de Seguros
     * Seguro empresarial
     * Seguro residêncial

* Equipe de Vendas Contabilidade

* Equipe de Vendas Ativos

* Equipe de Vendas Gestão de Creditos

Definindo os passos chave para seu ciclo de vendas
--------------------------------------------------

Cada empresa tera estágios similares para qualificar as oportunidades, ainda que customizados.

Para ver e definir estágios para a qualificação das Oportunidades, vá em :menuselection: Vandas --> Configuração --> Oportunidades --> Estágios.

Os passos chave do seu ciclo e vendas são o que o OpenERP chama "estágios". Você pode usar os estágiso para melhorar sua capacidade de vendas, pois com eles você pode saber as razões pelas quais os negócios dão certo ou não.

Os estágios vão permitir que o vendedor descubra onde uma oportunidade específica está posicionada no ciclo de vendas. Uma das dificuldades mais frequentes na utilização de estágios é que diferentes vendedores podem achar que as oportunidades de vendas deveriam estar em diferentes estágios. Você pode prevenir isso definindo claramente o quê você espera como resultado para cada estágio. Assim, todos os vendedores irão utilizar os mesmos estágios durante o processo de qualificação, possibilitando que o gerente de vendas tenha informações objetivas e consistentes. Também recomendamos limitar o número de estágios no seu ciclo de vendas para deixá-lo fácil de acompanar.

Conforme você progressa no seu ciclo de vendas, e muda de um estágio para outro, você tem informações mais precisas sobre uma dada oportunidade. Por exemplo, quando você marca uma oportunidade como "Qualificada", você pode decidir que o vendedor tenha que definir o "Retorno epserado" e a "Data de fechamento esperada". A probabilidade também pode mudar automaticamete conforme a mudança de estágios, basta selecionar "Mudar a probabilidade automaticamente". Depois de selecionada o OpenERP irá mudar a probabilidade da oportunidade para a probabilidade definida no estágio. Se você escolher a probabilidade de 0% (perdida) ou de 100% (ganha), Openerp irá colocar o estágio correspondente de quando a oportunidade foi marcada como perdida ou ganha.

Por exemplo, para seguir suas oportunidiades, você pode definir critérios que devam ser alcançados pela equipe de vendas antes da mudança para o estágio seguinte.

1. Território - Dividir suas oportunidades em territórios.

2. Qualificado - Determina onde o prospecto tem uma necessidade.

    Qual é o resultado esperado?
    * A necessidade de comprar o produto/serviço foi confirmada,
    * Confirma que existe um orçamento.

3. Patrocinadores qualificados - Fazer as perguntas certas e ouvir atentamente para identificar e compreender completamente as necessidades do prospecto.

    Qual é o resultado esperado?
    * Atuais pontos fracos identificados,
    * Identificar o que o prospecto quer atingir
    * Identificar o responsável pelas decisões.

4. Proposição - Discute algumas soluções para determinar as preferências do cliente, recomenda soluções específicas para responder às necessidades do cliente.

    Qual o resultado esperado?
    * Demonstração e/ou proposição dada,
    * O responsável confirma seu interesse na compra,
    * Preço preliminar confirmado

5. Negociação - Enviar a proposta final para o cliente e começar o processo de negociação.
    
    Qual o resultado esperado? 
    * Negociação concluída,
    * Termos do contrato/condições acertadas,
    * Contrato enviado para assinatura.
    
6. Ganho/Perdido - Registra o passo final da oportunidade.

    Qual o resultado esperado?
    * Contrato assinado/ não assinado,
    * Próximos passos.
    

Você pode aplicar seus próprios passos durante o processo de qualificação através do campo "Estágio" que pode ser encontrado à direita da definição de oportunidade. Para enviar uma oportunidade automaticamente para o próximo passo, você pode usar o botão em forma de uma flecha verde para a direita.

.. figure:: images/crm_opport_stages.jpeg
   :scale: 100
   :align: center

   *Exemplo de Estágios de Oportunidades*

O OpenERP também possui outras opções de confiuração; você pode definir suas "Campanhas", permitindo que você siga evente ao qual seus prospectos e oportunidades se referem. Exemplos de campanhas são, Google adwords, um evento que você esteja realizando, uma newsletter.
Com "Categorias" você identifica as necessidades dos seus prospectos (ex, necessidade de treinamento, de OpenERP online), enquanto "Canais" ajudam você a manter a visibilidade em como o prospecto ou a oportunidade entrou no sistema (email, website, através de um cliente existente).

Planejando suas próximas ações
------------------------------

Quando um prospecto foi transformado em oportunidade, esta pode ser atribuída para qualquer vendedor. Você deve designar um diretor de oportunidades na empresa para que ele seja responsável por atribuir as novas oportunidades para diferentes vendedores de acordo com o trabalho que eles fazem, sua localização ou disponibilidade.

O OpenERP, também permite que você automatise esses passos no sue ciclo de vendas. Com "Automatizar regras" você pode dizer ao sistema, por exemplo, para automaticamente atribuir oportunidades para um vendedor ou para mudar o status de uma oportunidade de acordo com critérios específicos.

.. nota:: Ações Automatizadas

       Para acessar as regras do CRM, use :menuselection: Vendas 
       To access the CRM rules, use the :menuselection:`Sales --> Configuration --> Automated Actions --> Automated Actions` menu.




Vamos dar um exemplo do que você pode fazer com as Ações Automatizadas. Suponha que você quer atribuir as oprtunidades no setor de TI diretamente para Thomas, seu vendedor do setor de TI. Thomas deverá receber automaticamente a oportunidade quando um prospecto for convertido em uma, através do botão "Converter em Oportunidade", na tela de *Prospectos*. Isso pode ser definido no campo "Objeto" no formulário "Ações Automatizadas"; basta escolher "Converter/Fusionar Oportunidade".


As capturas de tela abaixo ilustram como você deve fazer para que o OpenERP faça isso automaticamente para você. 

*Step 1*

.. figure:: images/crm_autom_act1.jpeg
   :scale: 100
   :align: center

   *Conditions Tab of Automated Actions*

*Step 2*

.. figure:: images/crm_autom_act2.jpeg
   :scale: 100
   :align: center

   *Actions Tab of Automated Actions*

Quando você responde a uma oportunidade da aba "Comunicação & História", você pode diretamente mudar o status da oportunidade. Você também pode adicionar um CC global, mesmo com múltiplos emails separados por ';'. Isso garante que quando um email sobre essa oportunidade é enviado, todas as pessoas que estão no CC global serão notificadas.


Planejar suas próximas ações também se refere ao preenchimento de campos ou à realização de ações manualmente, sem a interferência de regras automatizadas. É importante que você preencha todos os campos oportunidade com precisão. Para garantir um bom acompanhamento e priorizar suas oportunidades, certifique-se de registrar a "Data da próxima ação" e a "Próxima Ação" em Oportunidade. Na tela *Oportunidades*, você pode agrupar seus resultados de pesquisa por esses campos, para que você saiba exatamente como planejar o seu trabalho.

Você pode usar os filtros para agrupar por "Prioridade" e então clicar na coluna  ``Data da próxima ação" para classificar pela data da próxima ação e para facilmente acompanhar suas oportunidades e saber exatamente o que você tem que fazer.


Planejando suas reuniões e chamadas telefônicas 
-----------------------------------------------

Planejar suas reuniões e chamadas não só permite estruturar seu trabalho, mas também melhorar suas habilidades de vendas, aprendendo com o histórico de suas chamadas e reuniões. Para ambas, você pode inserir um relatório completo sobre o quê foi discutido!

Como explicado no capítulo :ref:`crm-flow`, você pode agendar uma reunião diretamente de uma oportunidade. Quando você cria uma reunião de uma oportunidade, os campos relacionados serão preenchidos a partir da oportunidade.

Para facilitar a leitura, Thomas irá agendar uma nova reunião a partir de uma oportunidade aqui e definir Luc, o gerente de vendas, como a pessoa responsável pela reunião. Ele quer enviar um lembrete a Luc 1 dia antes da reunião começar.

.. nota:: Programar uma reunião a partir de uma oportunidade

   Para planejar a reunião, Thomas clica no botão 'Agendar Reunião' em "Oportunidade" e depois clica no botão "Semana" na visão de Calendário. Ele usa a função de arrastar e soltar para agendar a reunião para Luc. Ele planeja a próxima reunião para quarta-feira 14:00-3:00. Ele coloca Luc como a pessoa responsável e define um lembrete para ser enviado um dia antes do início da reunião. Ele também altera a "Data da próxima Ação" na oportunidade para a data da reunião.

Você também pode agendar uma reunião diretamente de um formulário *cliente*. Vá no Cliente para quem você deseja agendar uma reunião e abra a exibição de formulário. Na lista de ações no lado direito da tela, clique em agendar uma reunião. Se você ficar na vista "Mês" do calendário, você só terá que clicar no dia em que você deseja que a reunião seja planejada, vamos dizer que quinta-feira em duas semanas. Um formulário reunião será exibido, com o nome do cliente e a data preenchida.

Outra forma de introduzir um pedido de reunião, é usar diretamente o calendário de reuniões a partir do menu: menuselection: `Vendas -> Reuniões -> Reuniões`. Você pode usar mensais, semanais ou diárias para planejar uma reunião, selecionando os botões correspondentes. Você também pode clicar em um dia na janela Navegador para agendar uma reunião.

Na janela **Reunião**, insira os dados de reunião, tais como resumo da reunião, tipo, duração. Nas exibições semanais e diárias, você também pode pressionar o botão esquerdo do mouse no calendário e deslizar o mouse para criar um evento de várias horas. O OpenERP em seguida abrirá uma tela de entrada para uma nova reunião.
Você pode adicionar lembretes (ou `` Alarmes ``) para as suas reuniões e enviar convites, seja para pessoas de sua própria empresa, contatos parceiros ou pessoas externas (apenas especificar o endereço de e-mail diretamente no convite). Você pode enviar convites antes ou após a confirmação de uma reunião. Quer a partir da reunião em si ou a partir d visão "Convites para eventos" no menu: menuselection: `Vendas -> Configuração -> Calendário - Convites> Evento`, você pode acompanhar e alterar o status do participante. Se você não puder comparecer a uma reunião, você pode delegá-la a um de seus colegas.

.. dicas:: Alarmes ou Lembretes de Reuniões

     Adicione seus próprios alarmes através de: menuselection: `Vendas -> Configuração -> Calendário -> Alarmes`. Você pode querer ser avisado com uma semana de antecedência da reunião, então tudo que você tem a fazer é criar seu próprio alarme. A imagem abaixo mostra como fazer isso.
     
.. figure:: images/alarm.jpeg
   :scale: 100
   :align: center

   *Defining your Own Alarms*
     
.. figure:: images/crm_meeting_form.png
   :scale: 100
   :align: center

   *Criando uma nova Reunião*

Você pode notar diferentes cores e estilos no calendário. Isso é porque o OpenERP distingue entre eventos recorrentes, eventos que ocorrem em diversos dias e eventos que só acontecem uma vez.
Eventos que ocorrem em diversos dias têm um fundo colorido, enquanto que os eventos únicos têm uma única fonte colorida. Cada evento tem uma cor que representa o usuário que criou a reunião. Você pode filtrar os diferentes usuários selecionando-os na lista à direita da tela.

.. figure:: images/crm_calendar_month.png
   :scale: 90
   :align: center

   *Monthly Meeting Calendar*

.. figure:: images/crm_calendar_week.png
   :scale: 90
   :align: center

   *Weekly Meeting Calendar*

.. index:: calendários

Você pode alterar a visão de Calendário para reuniões e retornar à visão de formulário, de lista, ou gantt usando os botões na parte superior direita. Ferramentas usuais OpenERP de busca e filtros permitem filtrar os eventos exibidos no calendário, ou, por exemplo, exibir o calendário para apenas alguns funcionários de cada vez.

.. tip:: Parceiros relacionados

      Quando você passa o cursor do mouse sobre uma reunião na visão Calendário, o parceiro relacionado e a equipe de vendas será exibida.

É claro que você pode acessar este calendário OpenERP do seu smartphone. Para mais informações sobre esse recurso, consulte o capítulo: ref: `ch-sync1`.

O OpenERP também permite que você gerencie a entrada (inbound `) e a saída (outbound` `) das chamadas. Mesmo a partir da visão de lista **Chamadas**, você pode editar diretamente uma chamada (mudar o status, convertê-la em uma oportunidade ou agendar uma reunião). Para cada chamada, você pode criar notas sobre o resultado. Enquanto no telefone com seu prospecto ou cliente, você pode diretamente agendar uma reunião, marcar uma nova chamada ou converter a sua chamada para uma oportunidade. Não há necessidade de você se deslocar para vários menus para fazer o que você precisa: planeje uma ação como resultado da sua chamada.

O Gerenciamento de chamadas pode ser usado para outras necessidades de planejamento, tais como:

* Entrar chamadas de clientes para que você mantenha um registro da comunicação conectada a um parceiro ou uma
   oportunidade de vendas,

* Chamar uma grande lista de prospectos,

* Agendar chamadas recorrentes ou próximas ações.

.. nota:: Agendando uma Chamada diretamente

       Ir para: menuselection: `Vendas - Chamadas> Telefone -> 'Inbound' para registar as chamadas recebidas ou  'Outbound' para registrar chamadas de saída.

O telefonema será visível na aba Histórico do formulário **Parceiro** e dará uma visibilidade completa dos eventos para um cliente ou fornecedor.

É claro que o OpenERP também permite que você programe uma chamada de telefone diretamente de um formulário  **Oportunidade** através do botão "Agenda / registro de chamadas".

.. nota:: Chamadas no Calendário de Reuniões

       Para ter um calendário com as suas reuniões e suas chamadas, você pode escolher entrar telefonemas como uma reunião, como um tipo de reunião específica, "Chamadas telefônicas".

Agendando datas de enceramento
------------------------------

Para acompanhar o pipeline de vendas, você deve digitar a data de encerramento prevista para cada oportunidade. Ao fazer isso, a partir da tela **Oportunidades** você pode facilmente filtrar a sua pipeline por `` Encerramento esperado `` (botão no agrupar por). Esta é uma maneira clara para prever as receitas esperadas. Você também pode usar esse filtro para verificar se a data de encerramento prevista foi definida.

Adicionando uma data limite esperada, a equipe de vendas pode gerenciar o processo de vendas mais eficiente e eficazmente.

.. figure::  images/crm_opport_closing.jpeg
   :align: center
   :scale: 100

   *Closing Dates*

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

