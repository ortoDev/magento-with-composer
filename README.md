# Installazione Magento

## Creare le Access keys

1. Loggarsi nel marketplace di [Magento](https://marketplace.magento.com)
2. Cliccare sull'account name in alto a destra della pagina e seleziona My Profile.
3. Cliccare su Access Keys nel tab Marketplace.
4. Cliccare Create a New Access Key. Inserire un nome specifico per le chiavi (es., il nome del sito) e cliccare OK.
5. Verrà generata una chiave pubblica e una privata associate a questo account, da utilizzare come username e password del composer.


## Creare il progetto Magento
Eseguire il seguente comando composer:

```
 composer create-project --repository=https://repo.magento.com/ magento/project-community-edition <install-directory-name>
```

Settare i permessi per file e cartelle: 
````
cd /var/www/html/<magento install directory>
find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} +
find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} +
chown -R :www-data . # Ubuntu
chmod u+x bin/magento
```
