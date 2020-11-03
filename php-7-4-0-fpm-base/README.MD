##Imagens PHP FPM 7.4.0

##Data de Criação
0.1.0 - 03/11/2020 - Diego Tavares

##Motivo Criação

Micro serviços utilizando o Doctrine 2.1.2 ( última versão  em 03/11/2020 ) 
precisam utilizar no máximo a versão php 7.4.0,  devido a uma dependência do Doctrine.

<pre>
doctrine/odm - 2.1.2
     |
     |
     -> ocramius/proxy-manager - 2.7.1  requer php 7.4.0 
</pre>

Até o presente momento, não existe uma atualização do ODM (2.2) utilizando 
essa lib mais recente.

##Change Log

####0.1.1 - XX/XX/XXXX

Bug Fix Library 123 example

<hr/>

####0.1.0  - 26/10/2020
[PHP Modules]
* apcu
* Core
* ctype
* curl
* date
* dom
* fileinfo
* filter
* ftp
* gd
* hash
* iconv
* json
* libxml
* mbstring
* mongodb
* mysqlnd
* newrelic
* openssl
* pcntl
* pcre
* PDO
* pdo_mysql
* pdo_sqlite
* Phar
* posix
* rdkafka
* readline
* Reflection
* session
* SimpleXML
* soap
* sodium
* SPL
* sqlite3
* standard
* tokenizer
* xdebug
* xml
* xmlreader
* xmlwriter
* Zend OPcache
* zlib


[Composer]
* Version 2.0.2 2020-10-25 23:03:59 ( Latest )