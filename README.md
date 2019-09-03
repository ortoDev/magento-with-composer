# Installazione Magento e estensioni con Composer

 - [Installazione Magento](https://github.com/ortoDev/magento-with-composer#installazione-magento-con-composer)
 - [Installazione estensioni](https://github.com/ortoDev/magento-with-composer#installazione-estensioni-con-composer)
 - [Installazione pacchetto lingua italiana](https://github.com/ortoDev/magento-with-composer/blob/master/README.md#installazione-pacchetto-lingia-italiana)

## Installazione Magento con Composer
- [Creare le Access Keys](https://github.com/ortoDev/magento-with-composer#creare-le-access-keys)
- [Creare il progetto Magento](https://github.com/ortoDev/magento-with-composer#creare-il-progetto-magento)
- [Installare con Web Setup Wizard](https://github.com/ortoDev/magento-with-composer#installare-magento-con-web-setup-wizard)

#### Creare le Access keys

1. Loggarsi nel marketplace di [Magento](https://marketplace.magento.com)
2. Cliccare sull'account name in alto a destra della pagina e seleziona My Profile.
3. Cliccare su Access Keys nel tab Marketplace.
4. Cliccare Create a New Access Key. Inserire un nome specifico per le chiavi (es., il nome del sito) e cliccare OK.
5. Verrà generata una chiave pubblica e una privata associate a questo account, da utilizzare come username e password del composer.


#### Creare il progetto Magento
1. Scaricare magento dal repository con composer:

```
 composer create-project --repository=https://repo.magento.com/ magento/project-community-edition <install-directory-name>
```
Come **username** inserire la chiave pubblica creata nel marketplace e come **password** la chiave privata.

2. Settare i permessi per file e cartelle: 
```
cd /var/www/html/<magento install directory>
find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} +
find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} +
chown -R :www-data . # Ubuntu
chmod u+x bin/magento
```

#### Installare Magento con Web Setup Wizard

Navigare all' url del sito /setup
```
http://<Magento-host-or-IP>/<path-to-magento-root>/setup
```
Seguire gli step di installazione

## Installazione estensioni con composer

1. Acquistare l'estensione
2. Aggiornare il file composer.json:
```
cd <your Magento install dir>
composer require <component-name>:<version> --no-update
composer update
```
3. Installare il modulo: 
```
php bin/magento setup:upgrade
php bin/magento setup:di:compile
```
4. Pulire la cache e verificare l' installazione del modulo

## Installazione pacchetto lingua italiana

- [Scaricare il pacchetto via composer](https://github.com/ortoDev/magento-with-composer/blob/master/README.md#scaricare-il-pacchetto-via-composer)
- [Deploy dei file statici](https://github.com/ortoDev/magento-with-composer/blob/master/README.md#deploy-dei-file-statici)
- [Reindex e pulizia cache](https://github.com/ortoDev/magento-with-composer/blob/master/README.md#reindex-e-pulizia-cache)

#### Scaricare il pacchetto via composer
```
composer require mageplaza/magento-2-italian-language-pack:dev-master
```

#### Deploy dei file statici
```
php bin/magento setup:static-content:deploy
php bin/magento setup:static-content:deploy it_IT
```

#### Reindex e pulizia cache
```
php bin/magento indexer:reindex
php bin/magento cache:clean
php bin/magento cache:flush
```
