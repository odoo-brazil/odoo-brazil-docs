
.. _configuration-files-link:

Configuration
=============

Two configuration files are available:

    * one for the client: ~/.openerprc
    * one for the server: ~/.openerp_serverrc

Those files follow the convention used by python's ConfigParser module.

Lines beginning with "#" or ";" are comments.

The client configuration file is automatically generated upon the first start. The one of the server can automatically be created using the command: ::

  openerp-server.py -s

If they are not found, the server and the client will start with the default configuration.

Server Configuration File
-------------------------

The server configuration file .openerp_serverrc is used to save server startup options. Here is the list of the available options:

:interface:
    Address to which the server will be bound 

:port:
    Port the server will listen on 

:database:
    Name of the database to use 

:user:
    Username used when connecting to the database 

:translate_in:
    File used to translate OpenERP to your language 

:translate_out:
    File used to export the language OpenERP use 

:language:
    Use this language as the language of the server. This must be specified as an ISO country code, as specified by the W3C. 

:verbose:
    Enable debug output 

:init:
    init a module (use "all" for all modules) 

:update:
    update a module (use "all" for all modules) 

:upgrade:
    Upgrade/install/uninstall modules 

:db_name:
    specify the database name 

:db_user:
    specify the database user name 

:db_password:
    specify the database password 

:pg_path:
    specify the pg executable path 

:db_host:
    specify the database host 

:db_port:
    specify the database port 

:translate_modules:
    Specify modules to export. Use in combination with --i18n-export 


You can create your own configuration file by specifying -s or --save on the server command line. If you would like to write an alternative configuration file, use -c <config file> or --config=<config file>
Here is a basic configuration for a server::

        [options]
        verbose = False
        xmlrpc = True
        database = terp
        update = {}
        port = 8069
        init = {}
        interface = 127.0.0.1
        reportgz = False

Full Example for Server V5.0 ::

        [printer]
        path = none
        softpath_html = none
        preview = True
        softpath = none

        [logging]
        output = stdout
        logger = 
        verbose = True
        level = error

        [help]
        index = http://www.openerp.com/documentation/user-manual/
        context = http://www.openerp.com/scripts/context_index.php

        [form]
        autosave = False
        toolbar = True

        [support]
        recipient = support@openerp.com
        support_id = 

        [tip]
        position = 0
        autostart = False

        [client]
        lang = en_US
        default_path = /home/user
        filetype = {}
        theme = none
        toolbar = icons
        form_tab_orientation = 0
        form_tab = top

        [survey]
        position = 3

        [path]
        pixmaps = /usr/share/pixmaps/openerp-client/
        share = /usr/share/openerp-client/

        [login]
        db = eo2
        login = admin
        protocol = http://
        port = 8069
        server = localhost


GTK-Client Configuration
------------------------

.. topic:: login section

        :login:
            login name to use to connect to OpenERP server 

        :server:
            address used by the server 

        :port:
            port used by the server 

.. topic:: path section

        :share:
            path used to find OpenERP shared files 

        :pixmaps:
            path used to find OpenERP pixmaps files 

.. topic:: tip section

        :autostart:
            Should the client display tips at startup 

        :position:
            Tip number the client will display 

.. topic:: form section

        :autosave:
            The client will automatically save the change you made to a record 

.. topic:: printer section

        :preview:
            Preview report before printing 

        :softpath:
            Path to the pdf previewer 

        :softpath_html:
            Path to the html previewer 

        :path:
            Command used to print 

.. topic:: logging section

        :logger:
            log channels to display. List values are: @common@, @common.message@, @view@, @view.form@, @common.options@, @rpc.request@, @rpc.result@, @rpc.exception@ 

        :level:
            logging level to show 

        :output:
            file used by the logger 

        :verbose:
            set the log level to INFO 

.. topic:: client section

        :default_path:
            Default path used by the client when saving/loading data. 

**Default values**::

        [login]
        login = admin
        port = 8069
        server = 192.168.1.4
         
        [printer]
        path = none
        preview = True
        softpath = none
         
        [logging]
        output = stdout
        logger =
        verbose = True
        level = ERROR
         
        [form]
        autosave = False
         
        [client]
        default_path = /home/user

Web Client Configuration 
------------------------ 

Full Example for web Client Configuration ::
	    
		[global]
		# Some server parameters that you may want to tweak
		server.socket_host = "0.0.0.0"
		server.socket_port = 8080

		# Sets the number of threads the server uses
		server.thread_pool = 10

		server.environment = "development"

		# Simple code profiling
		server.profile_on = False
		server.profile_dir = "profile"

		# if this is part of a larger site, you can set the path to the TurboGears instance here
		server.webpath = ""

		#[logging]
		#log.access_file = "/var/log/openerp-web/access.log"
		#log.error_file = "/var/log/openerp-web/error.log"

		# OpenERP Server
		[openerp]
		host = 'localhost'
		port = '8070'
		protocol = 'socket'

		# Web client settings
		[openerp-web]
		# filter dblists based on url pattern?
		# NONE: No Filter
		# EXACT: Exact Hostname
		# UNDERSCORE: Hostname_
		# BOTH: Exact Hostname or Hostname_

		dblist.filter = 'NONE'

		# whether to show Databases button on Login screen or not
		dbbutton.visible = True

		# will be applied on company logo
		company.url = ''

		# options to limit data rows in M2M/O2M lists, will be overriden 
		# with limit="5", min_rows="5" attributes in the tree view definitions
		child.listgrid.limit = 5
		child.listgrid.min_rows = 5

Get a clone of each repository::

  bzr clone lp:~openerp/openobject-server/trunk server
  bzr clone lp:~openerp/openobject-client/trunk client
  bzr clone lp:~openerp/openobject-client-web/trunk client-web
  bzr clone lp:~openerp/openobject-addons/trunk addons

If you want to get a clone of the extra-addons repository, you can execute this command::

  bzr clone lp:~openerp-commiter/openobject-addons/trunk-extra-addons extra-addons

run the setup scripts in the respective directories::

  python2.5 setup.py build
  sudo python2.5 setup.py install

Currently the initialisation procedure of the server parameter --init=all to
populate the database seems to be broken in trunk.

It is recommended to create a new database via the gtk-client. Until then the web-client will not work.

Start OpenERP server like this: ::

  ./openerp-server.py --addons-path=~/home/workspace/stable/addons

The ``bin/addons`` will be considered as default addons directory which can be
overriden by the ``~/home/workspace/stable/addons``. That is if an addon exists in
``bin/addons`` as well as ``~/home/workspace/stable/addons`` (custom path) the later one will
be given preference over the ``bin/addons`` (default path).

