========================
Manual de Instalação do OpenERP 6.1
========================

Este manual tem como premissa a instalação completa da localização brasileira numa máquina com Ubuntu "zerado" e atualizado. Foi testado na versão 12.04 LTS. Pode ser tanto máquina real quanto virtual.

Todos os comandos são emitidos numa janela terminal.

Para atualizar digite

sudo apt-get update

Depois execute o Gerenciador de Atualizações do Ubuntu


Instalação do PostgreSQL
-------------------------------

Para instalar o PostgreSQL:

sudo apt-get install postgresql 

Verifique qual versão do PostgreSQL foi instalada para substituir "X.Y" abaixo pela versão - exemplo 8.4, 9.1, etc. Isso pode ser feito observando a mensagem "Starting PostgreSQL X.X database server" logo cima da finalização da instalação ou com o comando 

psql -V (só os 2 primeiros números X.X)

Criação do Banco de Dados
----------------------------------

Crie uma nova conta de usuário de USUÁRIO LINUX, chamada "postgres", e verifique a versão do PostgreSQL que está instalada. Note que quando o comando é realizado, o controle passa do usuário administrador para o usuário "postgres".

sudo -u postgres -i

O comando a seguir faz parte dos comandos do PostgreSQL, e irá criar uma "role" (papel de usuário) chamada "openuser", e um usuário chamado "postgres".

createuser --createdb --username postgres --no-createrole --pwprompt openuser

Será pedido para digitar duas vezes a senha do novo usuário.

Na pergunta "A nova role poderá criar um super-usuário? (s/n)" responda com "s".

Agora é preciso sair do login do usuário Linux "postgres" e retornar para o usuário administrador:

exit 

Se você quiser pode instalar a interface gráfica do PostgreSQL com o comando

sudo apt-get install pgadmin3


Configurando o PostgreSQL para Acesso Remoto (etapa opcional)
-------------------------------------------------------------------------------

A configuração que faremos a seguir permitirá que qualquer máquina da sua rede ou de fora acessem o banco de dados. Esta configuração é muito útil para a instalação e testes do OpenERP, mas antes de colocar o sistema em produção é bom retornar aqui e controlar quais máquinas poderão ter acesso ao sistema.

Vamos agora editar o famoso arquivo "pg_hba.conf". Não esqueça que X.Y deve ser trocado pela sua versão de PostgreSQL

Antes de mais nada, faça um backup do arquivo

sudo cp /etc/postgresql/X.Y/main/pg_hba.conf /etc/postgresql/X.Y/main/pg_hba_bk.conf 

Depois abra o editor

sudo pico /etc/postgresql/X.Y/main/pg_hba.conf 

Com o comando acima você irá entrar no editor de textos "pico". Se o "pico" não funcionar em seu sistema, tente o "nano". Use as setas do teclado para se movimentar pelo texto. Serão três alterações neste arquivo:

I) Vamos configurar o acesso administrativo ao banco de dados. Procure (quase no fim do arquivo) as seguintes linhas:

# Database administrative login by UNIX sockets local all postgres ident

Nas versões mais novas ao invés de "ident" você vai encontrar "peer"

Troque "postgres" por "all", e "ident" ou "peer" por "trust", para que fique assim:

local all all trust

II) Vamos configurar o acesso local ao banco de dados. Procure as linhas a seguir:

# "local" is for Unix domain socket connections only local all all ident 

Troque o "ident" por "trust", para que fique assim:

local all all trust 

III) Vamos configurar o acesso remoto (através de IP v4). Procure as linhas:

# IPv4 local connections: host all all 127.0.0.1/32 md5 

Troque "127.0.0.1/32" por "0.0.0.0/0", e "md5" por "trust", para que fique assim:

host all all 0.0.0.0/0 trust 

Tecle "Ctrl O" seguido de ENTER para salvar as modificações no arquivo. Saia do pico teclando "Ctrl X".

Agora vamos configurar o arquivo "postgresql.conf":

Faça um backup do arquivo

sudo cp /etc/postgresql/X.Y/main/postgresql.conf /etc/postgresql/X.Y/main/postgresql_bk.conf 

sudo pico /etc/postgresql/X.Y/main/postgresql.conf 

Procure a linha:

#listen_addresses = 'localhost' 

Retire o "#", e troque 'localhost' por '*', para que fique assim:

listen_addresses = '*' 

Tecle "Ctrl O" seguido de ENTER para salvar as modificações no arquivo. Saia do pico teclando "Ctrl X".


Testando o acesso ao PostgreSQL
----------------------------------------

Reinicie o PostgreSQL:

sudo /etc/init.d/postgresql restart 

Se em seu computador servidor (ou em outro computador da mesma rede) você tiver o programa pgAdmin III, você pode testar agora se o acesso externo ao PostgreSQL está corretamente configurado.

Abra o pgAdmin III. Menu "Arquivo" > Adicionar ao servidor... Nome: (digite aqui o nome da máquina onde está instalado o PostgreSQL) Máquina: (digite aqui o IP da máquina onde está instalado o PostgreSQL) Porta: 5432 Nome de usuário: openuser Senha: (digite aqui a senha do usuário openuser) [ OK ] 
Estando tudo certo, o novo servidor de banco de dados vai aparecer na lista.

Se você não tem o pgAdmin III, pode tentar:

sudo su postgres

psql (você verá o prompt do psql)

\q (este é o comando para sair do psql). 

exit


Instalação dos outros pacotes necessários
---------------------------------------------------

Execute os comandos abaixo para instalar as bibliotecas complementares

sudo apt-get install build-essential python python-dev python-psycopg2 python-reportlab python-egenix-mxdatetime python-tz python-pychart python-mako python-pydot python-lxml python-vobject python-yaml python-dateutil python-pychart python-webdav python-cherrypy3 python-formencode python-pybabel python-simplejson python-pyparsing python-openid python-pip libpq-dev libfreetype6-dev libxml2-dev libxslt1-dev libjpeg62-dev liblcms1-dev libpng12-dev

sudo pip install werkzeug

sudo pip install --upgrade werkzeug


Instalação do Bazaar
--------------------------

O Bazaar é um sistema de controle de versões, fundamental para que um ambiente de desenvolvimento de software seja administrável. O Bazaar é a ferramenta básica tanto para baixar o código-fonte e atualizar o OpenERP quanto para enviar as suas contribuições para o projeto.

sudo apt-get install bzr 

Para usar o Bazaar (para instalar e atualizar pacotes, por exemplo) é necessário abrir uma conta no site launchpad.net e criar uma chave pública SSH para baixar o código. Mais informações aqui


Instalação Básica do OpenERP com a localização brasileira

Para baixar todos os fontes do OpenERP e da localização brasileira, basta você instalar a ferramenta openerp-br:

cd /opt

sudo mkdir openerp-br

sudo chmod 777 -R openerp-br

bzr branch lp:~openerp-brazil-team/openerp/openerp-br --use-existing-dir

Após baixar o openerp-br acesse a pasta:

cd openerp-br

Execute o bzr_set.py:

 ./bzr_set.py

Após executar o bzr_set.py, serão baixadas todas as branches do OpenERP. Também serão criados os links dos módulos da localização brasileira e dos módulos da branch addons-extra que fazem parte da dependência da localização brasileira. Serão criadas as seguintes pastas:

addons - Pasta com os módulos core do OpenERP
addons-extra - Pasta com os módulos extra do OpenERP
br - Pasta com os módulos da localização Brasileira
client - Cliente GTK do OpenERP
server - Servidor OpenERP
web - Cliente Web do OpenERP

Cliente Web
Basta incluir a pasta openerp-br/web/addons no parametro addons-path do arquivo de configuração do servidor OpenERP. Você também pode fazer isso no momento que você executar o servidor OpenERP pela primeira com o argumento --addons-path, como mostrado abaixo.


Executando o Servidor OpenERP pela Primeira Vez
--------------------------------------------------------------

Na primeira vez em que o servidor é executado, podemos gravar parâmetros de configuração. Não esqueça de trocar SENHA pela senha do usuário postgres do PostgreSQL

cd /opt/openerp-br/server

./openerp-server --db_user=openuser --db_password=SENHA --db_host=127.0.0.1 --db_port=5432 --addons-path=/opt/openerp-br/addons,/opt/openerp-br/addons-extra,/opt/openerp-br/web/addons -c openerp-server.conf --save 

Em outras vezes, o servidor poderá ser iniciado apenas com:

cd /opt/openerp-br/server

./openerp-server -c openerp-server.conf 


Acesso via Navegador
---------------------------

Abra um navegador web e acesse o endereço a seguir:

http://localhost:8069 

Ou se estiver em outra máquina da rede:

http://ip_do_servidor:8069 


Primeiro acesso ao OpenERP
-----------------------------------

Você tem duas opções: criar uma base de dados zerada ou carregar uma "pronta para uso". Para começar do zero:
Clique em Manage Databases
Preencha Master Password - mesma do parâmetro admin_passwd do openerp-server.conf. O padrão é admin.
Escolha um nome
Marque a opção Load Demonstration data
Escolha lingua português(br)
Defina a senha do administrador
Para carregar uma "pronta para uso":
baixe o arquivo http://sourceforge.net/projects/openerpbrasilvm/files/bancos_de_dados/openerp_br_ceps.gz/download e salve no diretório /tmp. Mais informações aqui.
su openuser
cd /tmp
createdb -U openuser novo_banco
gunzip -c openerp_br_ceps.gz | psql -U openuser novo_banco
cd /opt/openerp-br
bzr update
Depois você pode renomear a base para o nome que quiser

Para utilização há uma boa documentação sobre impostos aqui mas foi elaborada para a versão 6.0. Pode ter incompatiblidades com a 6.1

No primeiro acesso você deverá atualizar a lista de módulos antes de instalar qualquer novo módulo.


Iniciando o Servidor Automaticamente no Boot
---------------------------------------------------------

Depois que você tiver feito sistema funcionar, será interessante configurar o Linux para dar partida automaticamente no OpenERP toda vez que o computador for ligado.

1) Fazer cópias do script de inicialização e de configuração do OpenERP server e criar usuário openuser

cp /opt/openerp-br/server/openerp-server.conf /opt/openerp-br/server/openerp-server_bk.conf

sudo adduser openuser

cp /opt/openerp-br/server/debian/openerp.init /opt/openerp-br

sudo chmod 666 /opt/openerp-br/openerp.init 

sudo su openuser (vai solicitar a senha do openuser)


2) Editar o arquivo /opt/openerp-br/openerp.init e fazer as alterações necessárias:

pico /opt/openerp-br/openerp.init
corrigir o caminho para o arquivo de configuração openerp-server.conf, criando o parâmetro CONFIG => CONFIG=/opt/openerp-br/server/openerp-server.conf
corrigir o caminho do servidor no parâmetro DAEMON => DAEMON=/opt/openerp-br/server/openerp-server
corrigir o nome de usuário no parâmetro USER para openuser => USER=openuser
modificar se necessário o parâmetro LOGFILE para direcionar a saída do OpenERP server para o arquivo /var/log/openerp-server.log

Tecle "Ctrl O" seguido de ENTER para salvar as modificações no arquivo. Saia do pico teclando "Ctrl X".

3) Alterar as permissões do arquivo para torna-lo executável.

sudo chmod +x /opt/openerp-br/openerp.init

4) Criar um link simbólico do arquivo na pasta /etc/init.d para o script de inicialização e fazer com que o script rode automaticamente na inicialização do sistema.

cd /etc/init.d

sudo ln -s /opt/openerp-br/openerp.init openerp-server

sudo update-rc.d openerp-server defaults 

5) Editar o arquivo openerp-server.conf. Modificar o parâmetro logfile de False para /var/log/openerp-server.log.

pico /opt/openerp-br/server/openerp-server.conf

logfile = /var/log/openerp-server.log

Tecle "Ctrl O" seguido de ENTER para salvar as modificações no arquivo. Saia do pico teclando "Ctrl X".

Depois desta alteração não será mais possível ver mensagens do OpenERP na tela, só pelo arquivo /var/log/openerp-server.log

6) Criar os arquivo /var/log/openerp-server.log e /var/run/openerp-server.pid e alterar o permissão para escrita.

sudo touch /var/log/openerp-server.log

sudo touch /var/run/openerp-server.pid

sudo chown openuser /var/log/openerp-server.log

sudo chown openuser /var/run/openerp-server.pid

chmod 666 /var/run/openerp-server.pid


7) Para testar se está OK:

cd /opt/openerp-br

./openerp.init start

Verifique o arquivo de log.

less /var/log/openerp-server.log (tecle End para ir ao final do arquivo e conferir as mensagens. Deve aparecer que o OpenERP está Running)

Para parar o OpenERP

./openerp.init stop