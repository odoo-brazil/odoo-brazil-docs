
.. raw:: latex

    \afterpage{\clearpage}

.. _part2-crm-leads:

Gerindo seus Prospectos
===================

Para definir prospectos, imagine um recipiente cheio de contatos de clientes potenciais, manifestando interesse pelos produtos da sua empresa. 

Um prospecto, representa um cliente potencial com quem você ainda não entrou em relação. Usualmente, um prospecto contém informações valiosas para realizar futuras oportunidades de venda. Porém, o erro o mais comum é que essa informação chave se perde frequentemente, porque nao está cadastrada em parte alguma. E mesmo quando está registrada, é complicado seguir as atividades desses prospectos, porque essa informação não é disponível quando se precisa dela.

Gravar as informações dos prospectos num lugar central como OpenERP, acabará com esses problemas.

Então, quando criar um prospecto no OpenERP, manualmente ou automaticamente? Os eventos seguintes poderiam ser um ponto de partida:

* Um e-mail mandado para um dos seus endereços genéricos de email, tal como sales@mycompany.com

* Um cartão de negócio de um cliente em perspetiva encontrado brevemente numa exibição: contatar ele mais uma vez para qualificar o prospecto e para saber se existe uma possibilidade de oportunidade de venda; cadastrada manualmente, 

* Um banco de dados de clientes potenciais num dado setor e região importada desde um arquivo CSV. Os clientes potenciais tem que ser contatados mais uma vez individualmente ou com um mass mailing para determinar quais contatos precisam ser seguidos,

* Um contato interesante que encontrou durante um evento de negócio. Tem que qualificar ele antes de atribuir um vendedor ao contato,

* Um formulário preenchido sobre seu site de Internet diretamente integrado no OpenERP usando nosso web serviço. Antes de converter o formulário em uma proposta ou oportunidade, é necessário ler e gerir o pedido da pessoa. 

Funcionários do departamento de marketing ou pre-venda trabalharão usualmente sobre prospectos. Uma vez que esses prospectos serão convertidos em clientes e/ou oportunidades de venda, o departamento de venda presta individual atenção para cada opportunidade. Naturalmente, antes de converter um prospecto em uma oportunidade, algum trabalho de qualificaçao tem que ser feito.

O OpenERP te permite configurar facilmente o jeito de qualificar prospectos. Pode criar seus proṕrios estágios com :menuselection:`Vendas --> Configuração --> Dicas & Oportunidade --> Estágios`. Usa o numero da sequência para determinar o ordem dos estágios, ex : 10 para primeira ligação, 20 para renovação do contato, etc. Naturalmente, você pode também colocar o estágio num outro lugar para automaticamente mudar o ordem de todos os estágios. O vendedor pode mudar o estado do prospecto em função da reposta do prospecto e entrar o resultado desse contato na visão de formulário do prospecto (e.g. no campo ``Notas``).

Desde o :menuselection:`Vendas --> Vendas --> Prospectos` menu, pode qualificar cada prospecto individual com o ``Estágio`` campo que pode encontrar em cima, na direita da definição do prospecto. Para mudar seu prospecto automaticamente para a próxima desde a lista dos prospectos, basta usar o botão que parece com uma flecha direita verde.

Prospectos podem ser atribuidos a um *time de vendas* para serem seguidos facilmente (olha  :ref:`ch-team`). Cada usuário pode ser adicionado a um time de vendas por padrão que pode ser especificado no `usuário preferências`. Quando definir uma estrutura em árvore pra seu time de vendas, pode também atribuir um prospecto para um outro time de vendas para ações posteriores.

.. nota:: Prospectos ou Opportunidades

       Empresas podem decidir não usar os prospectos, mas, em vez disso, de guardar todas informações diretamente numa oportunidade. Para algumas empresas, 
       prospectos são apenas uma passagem adicional no processo de vendas. Pode-se chamar isso de extendido (começar desde prospecto) contra simplificado (começar 
       desde oportunidade).
       OpenERP permite perfeitamente ecolher a aproximação adaptada. Se sua empresa gerir seus pedidos desde oportunidades diretamente, pode ir ao capítulo
       :ref:`part2-crm-opport`, mesmo se a maioria das características explicadas em baixo, também se aplicam às oportunidades.

Nas próximas seções, explicaremos alguns exemplos mais em detalhes de como `prospectos` no OpenERP podem ser usados.

.. dica:: Prospectos Menu não é mostrado

        Em visao ``Simplificada``, ``Prospectos`` não serão mostrados. Para ver não só oportunidades, mas também prospectos, tem que mudar para a 
        ``visao extendida``. Pode mudar visao `simplificada` para `Extendida` facilmente, mudando suas `preferências de usuários` pelo botão `Editar Preferências`.

Gravando seu Cartão de Negócio Eficientemente
---------------------------------------

Clientes potenciais são usualmente digitados como um prospecto no sistema. Quer dizer que não cria um parceiro ou uma oportunidade de venda até que tenha qualificado se o prospecto é interessante ou não.


.. dica:: Qualificação

      Quando um prospecto qualificado precisa de ações posteriores, pode virar o prospecto num parceiro e, eventualmente, uma oportunidade de venda.

Para fazer um novo prospecto, vá em :menuselection:`Vendas --> Vendas --> Prospectos` menu e clique no botão `Novo`. No formulário **prospecto** que se abre, digite os dados do contato desse novo cliente potencial e adicione notas.

.. figure:: images/crm_lead_new.png
   :scale: 80
   :align: center

   *Criando um novo prospecto*

Pode também colocar o status do prospecto em função do trabalho que foi feito:

* ``Rascunho`` : os dados do prospecto foram digitados, ainda nenhum trabalho foi feito e o vendedor ainda não foi associado com o pedida,

* ``Aberto``: o prospecto está sendo tratado,

* ``Fechado``: o prospecto foi convertido num parceiro e/ou uma oportunidade de venda,

* ``Pendente``: o prospecto está esperando uma resposta do cliente potencial,

* ``Escalada``: o prospecto é escalado para o superior time de vendas na estrutura de árvore para ações posteriores, 

* ``Cancelado``: o prospecto foi cancelado porque o vendedor decidiu que não valia a pena seguir.

Um status de prospecto pode ser mudado facilmente, mesmo desde a visao de lista (a visao por padrão quando inicia o programa **prospecto**). Simplesmente clique na flecha verde para mudar o status do prospecto.
Sobre o :guilabel:`Extra` aba no **Prospectos** formulário, encontra estatística sobre dias abertos e fechados e mais informações sobre a campanha, o canal, etc.

.. figure:: images/crm_lead_extra.jpeg
   :scale: 80
   :align: center

   *Extra ada*

Sobre :guilabel:`Comunicação & Histórico` aba, no **Prospectos** formulário, pode ver um histórico completo de todas as ações em relação a esse prospecto. Pode também adicionar notas internas e alterar o status do prospecto enquanto adiciona uma nota assim.
Manda um email diretamente desde o prospecto clicando simplesmente no botão :guilabel:`Enviar novo Email` (Para configurar suas opções de email, por favor consulte o capítulo :ref:`ch-crm-fetchmail-install`).
Pode adicionar anexos nas notas internas e emails que você mandou para o prospecto. Pode personalizar sua mensagem e ter o status mudado depois que um email foi mandado; poderia automaticamente ter o prospecto colocado em **pendente**, porque precisa uma resposta desde o cliente antes de fazer ações posteriores.

.. figure:: images/crm_lead_comm.jpeg
   :scale: 80
   :align: center

   *Aba Comunicação & Histórico*

Importação de um banco de dados de prospectos
--------------------------

Pode-se também importar uma grande lista de prospectos. Isso pode ser útil se tiver comprado um banco de dados de prospectos potenciais que você quer carregar no OpenERP para os gerir todos ao mesmo tempo.

Começa com uma lista de prospectos de formato CSV por exemplo. Se seu banco de dados de prospectos tiver um outro formato, pode-se convertê-lo facilmente no formato CSV usando Miscrosoft Excel ou OpenOffic Calc. 

.. dica:: Importação 

      A melhor coisa a fazer para garantir que sua importação  passará sem problemas, é primeiro exportar todos os campos Prospectos necessários usando a função `Export`,e então editar o arquivo csv para importação.

Abra o formulário **Prospectos**  usando o menu :menuselection:`Vendas --> Vendas --> Prospectos`. Em `Outras Opções`, clique no link :guilabel:`Import`. (Pode também importar desde a visao de lista, só abra a janela ação à direita (clicando sobre a flecha) e em `Outras Opções` clique no link :guilabel:`Import`.) 

Selecione seu arquivo que contém as informações dos prospectos, e clique em :guilabel:`Import File`. O OpenERP mapea automaticamente os cabeçalhos das colunas do seu arquivo CSV para os campos correspondentes no OpenERP. se necessário, pode  clicar em ``CSV Options`` para alterar as configurações para que elas coincidam com as configurações locais. 

.. figure:: images/crm_lead_import1.jpeg
   :scale: 80
   :align: center

   *Importação dos prospectos no sistema*

Verifique o capítulo on-line sobre o sistema de administração para mais informações sobre importação e exportação em http://doc.openerp.com/v6.0/book/.

.. dica:: várias Importações

    Importando e exportando dados no OpenErp é uma função genérica disponível a todos os recursos.
    Assim, você pode importar e exportar listas, como parceiros, oportunidades, entradas de contabilidade,
    produtos e listas de preços.

É claro que há outros métodos de geração de prospectos de forma automática ou semi-automática:

* Através de um formulário de contato em seu site;

* Usando o plugin Outlook ou Thunderbird para inserir novas pistas diretamente da caixa de correio do vendedor quando ele vê e-mails promissores,

* Usando o gateway de e-mail para cada e-mail recebido de um determinado endereço (como
   sales@mycompany.com), que pode criar um prospecto automaticamente a partir do conteúdo do e-mail.

Estes diferentes métodos são descritos neste livro  (ver capítulo :ref:`contform`).

Organizar prospectos
----------------

Para ajudar os usuários a organizar e gerir prospectos de forma eficiente, o OpenERP fornece vários recursos no CRM para ser usado em função das necessidades de cada um:

Usa a visao :menuselection:`Vendas --> Vendas --> Prospectos` para organizar os prospectos:

* Mostra uma lista de todas os Prospectos (qualificado, aberto, não aberto, ...) em função do time de vendas com qual você está ligado,

* Cria um novo porspecto através do botao "Novo",

* Mostra Prospectos não atribuidos, clique no botão ao lado do campo `Representante`,

* Mostra uma lista de todas os seus prospectos você ainda precisa gerir (seus prospectos abertos e rascunhos),

* Mostra uma lista de todos os prospectos que estão esperando uma resposta do cliente (normalmente em estado `Pendente`). Isso permite que você verifique periodicamente o seu trabalho a fazer,

* Mostra uma lista de todos os prospectos atribuídos a diferentes vendedores,

* Use Filtros Extendidos para mostrar todos os prospectos criados hoje ou durante a última semana, em um período de tempo específico,

* Encontre rapidamente prospectos ainda não atribuídos a uma campanha, clicando no grupo por botão e depois campanha.

O gerente de vendas pode usar a visao **Prospectos** para facilmente conservar pistas sobre o que cada vendedor está trabalhando.

.. figure:: images/crm_leads_list.png
   :scale: 80
   :align: center

   *Lista de todos os prospectos a gerir*

Prospectos também podem ser priorizados. Os vendedores podem atribuir uma prioridade para seus prospectos, e depois começar a trabalhar em seus prospectos a partir do topo da lista, que é ordenada por prioridade.	

Analisar prospecções
---------------

OpenERP também oferece relatórios estatísticos para conservar a memoria da geração de prospectos. O: `Vendas --> Relatórios --> Analisar Prospecções` relatório permite verificar vários elementos em relação com os prospectos. Você pode olhar para atrasos de processamento, número de respostas dadas e e-mails enviados (se você usar o recurso de gateway de e-mail). Classifica suas análises de prospectos por diferentes grupos para obter análise exata.

Estas são algumas possibilidades de análise do Analisar prospecções relatório.

1. Prospectos, por Estado e por mês

Para analisar os prospectos por estado, agrupe os prospectos por nível de qualificação (``Estágio ``) e status (`` Estado ``), este também pode ser feito por meses individuais (primeiro grupo por `` Mês ``).

2. Prospectos por Origem

Analise prospectos em função dos seus estados (aberto, perdido, ganho) e seu estágio (por exemplo, frio / quente ou novo / qualificação / ...) e descubra quantos prospectos pertencem a cada estado / estágio.

3. Quão eficaz são suas campanhas?

Agrupe por Campanha para encontrar facilmente o número de prospectos por campanha e do número total de prospectos. Você também pode selecionar uma campanha específica no seu filtro.

4. Prospectos por Prioridade.

Agrupa por Prioridade para ver que Prospectos são quentes, mornos ou frios.


.. figure:: images/crm_lead_analys.jpeg
   :scale: 80
   :align: center

   *Leads Analysis*

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

