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

