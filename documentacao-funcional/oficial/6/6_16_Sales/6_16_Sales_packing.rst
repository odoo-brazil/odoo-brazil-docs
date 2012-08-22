
Embalagem
=========

Produtos podem ser gerenciados em várias formas embalados. Por exemplo, se você vender
baterias você pode definir os seguintes pacotes para um produto dado bateria:

* Peça: uma bateria,

* Pacote Blister: um pacote de 4 pilhas,

* Pacote de 100 bolhas: 400 batteries,

* Paleta: 40 pacotes para um total de 16 mil baterias.

O gerenciamento OpenERP  de pacotes permite-lhe vender o mesmo produto em várias formas diferentes. o
vendedor poderia vender separadamente, uma bateria ou uma paleta de baterias. No fim, você pode
selecione o tipo de embalagem padrão em função das quantidades encomendadas.

Por exemplo, se o cliente quer comprar 30 mil baterias, o vendedor pode selecionar o pacote ``paleta``. O OpenERP proporá ao vender 32 mil baterias, o que corresponde a duas paletas. Ou o vendedor pode escolher 75 pacotes.

Os pacotes disponíveis são definidos no formulário do produto, na aba :guilabel:`Packaging`. O primeiro item da
lista é a que será usada por padrão.

Uma vez que um pacote foi definido no fim, OpenERP irá lançar um alerta, se o ordenado
quantidades não correspondem aos pacotes propostos. A quantidade deve ser um múltiplo do campo
:guilabel:`Quantity by Package` definido na formulário de embalagem.

.. figure:: images/sale_warning_packaging.png
   :scale: 75
   :align: center

   *Alerta sobre as quantidades vendidas em comparação com a embalagem*

Não confunda a gestão de embalagens com a gestão de várias unidades de medida. o
Unidade de medida é usada para gerenciar o estoque de maneira diferente de acordo com as várias unidades.
Com os pacotes, o estoque é sempre gerenciado por itens individuais, mas as informações sobre o pacote para utilização é fornecida
ao vendedor juntamente com esse item.

Mesmo se os efeitos são os mesmos, os documentos impressos serão diferentes. Os dois seguintes
operações têm o mesmo efeito sobre os níveis de movimento de estoque, mas será impresso de maneira diferente
sobre o pedido de vendas e no pedido em que as quantidades de embalagem como estão em causa:

* 32 mil baterias, emitido em duas paletas,

* 2 paletas de baterias, sem informações sobre embalagem.

Se o cliente quer pedir uma paleta e 10 pacotes, o vendedor pode colocar duas linhas de pedido
no pedido de venda usando o mesmo produto com diferentes unidades de medida.

Às vezes é mais útil para definir produtos diferentes para definir vários pacotes possíveis para
o mesmo produto. Uma caixa de cerveja em um supermercado é um bom exemplo. Um caso detém 24 garrafas, além de
o caso esvaziar-se. O cliente pode comprar garrafas à peça ou um caso de 24 garrafas de uma só vez.

Você pode definir dois pacotes para a ``Garrafa de cerveja`` : ``PCE`` e ``caixa`` . Mas esta
representação não permite que você gerencie o estoque e preço de caso vazio. Então você pode em vez disso
preferir um Lista de materiais, definindo e usando três diferentes produtos:

* o caso vazio para a cerveja,

* a garrafa de cerveja,

* A caixa de 24 garrafas de cerveja.

Você também define a lista de materiais abaixo do qual determina a make-up do caso de 24 cervejas

* Caixa de 24 garrafas de cerveja: 1 unidade,

* Garrafa de cerveja: 24 unidades,

* Caixa vazia de cerveja: 1 unidade.

Cada um destes três produtos tem um preço diferente. Os produtos ``Garrafa de cerveja`` e ``Caixa vazia de cerveja`` ter um nível de estoque que precisa ser gerenciado. A ``Caixa de 24 garrafas de cerveja`` não tem estoque, pois, se você vender o produto, OpenERP move automaticamente o estoque em duas linhas, uma para a caixa vazia e outra para as 24 garrafas individuais de cerveja. Para mais informações sobre listas de materiais,
veja o capítulo :ref:`ch-mnf`.

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
