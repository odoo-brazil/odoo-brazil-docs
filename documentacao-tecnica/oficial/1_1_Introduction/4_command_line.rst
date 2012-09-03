Command line options
====================

General Options
----------------

  --version             show program version number and exit
  -h, --help            show this help message and exit
  -c CONFIG, --config=CONFIG
                        specify alternate config file
  -s, --save            save configuration to ~/.terp_serverrc
  -v, --verbose         enable debugging
  --pidfile=PIDFILE     file where the server pid will be stored
  --logfile=LOGFILE     file where the server log will be stored
  -n INTERFACE, --interface=INTERFACE
                        specify the TCP IP address
  -p PORT, --port=PORT  specify the TCP port
  --net_interface=NETINTERFACE
                        specify the TCP IP address for netrpc
  --net_port=NETPORT    specify the TCP port for netrpc
  --no-netrpc           disable netrpc
  --no-xmlrpc           disable xmlrpc
  -i INIT, --init=INIT  init a module (use "all" for all modules)
  --without-demo=WITHOUT_DEMO
                        load demo data for a module (use "all" for all
                        modules)
  -u UPDATE, --update=UPDATE
                        update a module (use "all" for all modules)
  --stop-after-init     stop the server after it initializes
  --debug               enable debug mode
  -S, --secure          launch server over https instead of http
  --smtp=SMTP_SERVER    specify the SMTP server for sending mail
 
Database related options:
-------------------------
 
  -d DB_NAME, --database=DB_NAME
                        specify the database name
  -r DB_USER, --db_user=DB_USER
                        specify the database user name
  -w DB_PASSWORD, --db_password=DB_PASSWORD
                        specify the database password
  --pg_path=PG_PATH   specify the pg executable path
  --db_host=DB_HOST   specify the database host
  --db_port=DB_PORT   specify the database port
 
Internationalization options:
-----------------------------

    Use these options to translate OpenERP to another language.See i18n
    section of the user manual. Option '-l' is mandatory.
 
  -l LANGUAGE, --language=LANGUAGE
                       specify the language of the translation file. Use it
                       with --i18n-export and --i18n-import
  --i18n-export=TRANSLATE_OUT
                       export all sentences to be translated to a CSV file
                       and exit
  --i18n-import=TRANSLATE_IN
                       import a CSV file with translations and exit
  --modules=TRANSLATE_MODULES
                       specify modules to export. Use in combination with
                       --i18n-export

Options from previous versions:
-------------------------------
Some options were removed in version 6. For example, ``price_accuracy`` is now
configured through the :ref:`decimal_accuracy` screen.
