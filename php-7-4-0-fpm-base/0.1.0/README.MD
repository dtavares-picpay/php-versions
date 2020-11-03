##Imagens PHP FPM 7.4.0

##Data de Criação
PR - https://github.com/PicPay/picpay-docker/pull/63 - 26/10/2020

##Micro Serviços utilizando

* ms-registration-manager (https://github.com/PicPay/picpay-dev-ms-registration-manager)

##Observações
* Instalação Mongo DB lib:<br />
https://docs.mongodb.com/drivers/php -- sempre verifique a versão do php, extensão e da lib.<br /><br />
Dentro da aplicação busque por mongodb/mongodb no composer.lock após rodar o composer install e configure conforme a versão em seu Dockerfile.<br /><br />
Exemplo de erro quando configurado de forma errada:<br />
    * MongoDb Server (Atlas) 3.6 com a extensão (Php - Mongo.so) 1.8 possui erro de comunicação TLS (OCSP verification)