# metterenplaceapache2
Dans ce projet, je vais illustrer l'installation d'apache sur notre serveur **VPS**, 
## INSTALLATION D’APACHE 2
nous en profitons pour installer aussi le langage PHP et le module Apache associé :
<code>
    <pre>
        sudo apt-get install apache2
        sudo apt-get install php
        sudo apt-get install libapache2-mod-php
    </pre>
</code>

Après avoir installé apache2 et PHP, nous le dossier **www** dans le dossier **var** qui va servir le container de nos site web
<code>
    <pre>
        cd /var
        mkdir www
    </pre>
</code>
Attribuez à cet utilisateur les droits sur le dossier **/var/www**<br>
<code>
    <pre>
    sudo chown -R www-data:www-data /var/www
    </pre>
</code>
Pour vérifier le statut de votre serveur, lancez la commande suivante :
<code>
    <pre>
        sudo service apache2 status
    </pre>
</code>
Résultat:<br>
![resultat](images/1.png)
qui montre que apache2 est installé et est lancé également, après cela je peux vérifier notre **adress ip** dans le navigateur
<code>
    <pre>
     http://152.228.217.119/
     </pre>
</code>
Aperçu: <br>
![apercu](images/2.png)
Nous voyons ici que notre serveur Apache2 est bien démarré et, par défaut, il se relancera automatiquement à chaque démarrage de notre VPS.

Pour avoir la doc, il faut l'installer à travers cette commande
<code>
    <pre>
        sudo apt-get install apache2-doc
    </pre>
</code>
## Quelques commandes utiles
* Pour vérifier la version de votre serveur Web, tapez :<br>
<code>
    <pre>
       sudo apache2ctl -v
    </pre>
</code> 

![vfdfd](images/3.png)

* Pour obtenir un statut détaillé du serveur  :<br>
  <code>
    <pre>
        sudo apachectl status
    </pre>
 </code>

 * Pour arrêter, lancer ou relancer votre serveur:<br>
    <code>
    <pre>
         sudo service apache2 stop
        sudo service apache2 start
        sudo systemctl reload apache2
    </pre>
 </code>
   
* Pour vérifier les modules chargés d’Apache2 :<br>
 <code>
    <pre>
        sudo apache2ctl -M
    </pre>
 </code>

 ![ch](images/4.png)
 * Enfin si vous ne souhaitez pas redémarrer Apache2 au démarrage de votre VPS :<br>
  <code>
    <pre>
        sudo systemctl disable apache2
    </pre>
 </code>
 * A l’inverse pour réactiver le service :<br>
  <code>
    <pre>
        sudo systemctl enable apache2
    </pre>
 </code>

 ## LA CONFIGURATION
Les fichiers de configuration de votre serveur se situent dans le répertoire  **/etc/apache2**:

<code>
    <pre>
        /etc/apache2/
            |-- mods-enabled
            |-- conf-enabled
            |-- sites-enabled
    </pre>
 </code>

* Trois dossiers sont disponibles:
  1. **mods-enabled** : pour les fichiers de configuration des **modules** d’Apache 
  2. conf-enabled : pour fichiers de configuration des **services** disponibles
  3. sites-enabled : pour les fichiers de configuration des **sites** disponibles
   
>**Note** : ces répertoires sont en fait des liens symboliques vers les répertoires physiques  **mods-available**, **conf-available** et **sites-available**.

Il y aura au minimum autant de fichiers de configuration dans **sites-enabled** que de sites proposés.

Au départ il y a un seul site avec les fichiers suivants :<br>

<code>
    <pre>
        /etc/apache2/ 
            |-- sites-enabled
                |-- 000-default.conf
                |-- default-ssl.conf
    </pre>
 </code>

1. **000-default.conf** : configuration utilisée par le mode HTTP (port 80)
2. **default-ssl.conf** : configuration utilisée par le mode HTTPS (port 443)

Le contenu de la configuration HTTP est la suivante :

<code>
    <pre>
       &lt;VirtualHost *:80&gt;
            ServerAdmin webmaster@localhost
            DocumentRoot /var/www/html
            ErrorLog ${APACHE_LOG_DIR}/error.log
            CustomLog ${APACHE_LOG_DIR}/access.log combined
        &lt;/VirtualHost&gt;
    </pre>
 </code>


