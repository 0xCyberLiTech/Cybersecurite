![Debian_logo-01](./images/Cloud-et-securite.png)

## CYBERSÉCURITÉ / PROXY REVERSE installation.

Prérequis pour installer un Reverse Proxy Apache2 :

Depuis une machine Debian 12 qui ne va servir qu’a ça (recommandation mais pas obligé), nous allons saisir les instructions suivantes :

Mise à jour du système :
```
apt update && apt full-upgrade -y
```
Installation du paquet Apache2 :
```
apt-get install apache2
```
Afin de bénéficier du mode reverse sur Apache2, il faut activer les module : proxy et proxy_http.
Pour activer ces 2 modules saisissez la commande :
```
a2enmod proxy proxy_http
```
Pour que l’activation de ces modules soient pris en compte redémarrer le service d’apache2 :
```
systemctl restart apache2.service
```
Créer un fichier de configuration Apache :
```
nano /etc/apache2/conf-available/votre-conf.conf
```
```
<VirtualHost *:80>
    ServerName votre-domaine.fr
    ServerAdmin postmaster@domaine.fr
 
    ProxyPass / http://127.0.0.1/
    ProxyPassReverse / http://127.0.0.1/
    ProxyRequests Off
</VirtualHost>
```
- ServerName correspond à votre domaine.
- ProxyPass et ProxyPassReverse correspondent au serveur de destination.
- ProxyRequests est en off pour des raison de sécurité.

Activer la configuration :
```
a2ensite votre-conf.conf
```
Puis redémarrer apache2 :
```
systemctl restart apache2.service
````
Recommandations :

Je vous recommande de sécuriser ce serveur à l’aide d’un firewall sur vos deux machines, comme UFW qui est facile à prendre en mains ou Iptables. Sur votre machine qui sert de serveur Web, vous pouvez autoriser uniquement le serveur reverse proxy à se connecter à l’aide du port 80 ou 443 (ports part défaut) et n’oubliez pas de garder le port SSH (port 22 par défaut) ouvert si vous l’utilisez. Vous pouvez également utiliser l’outil CrowdSec afin de limiter les tentatives de cyberattaques si votre site web est exposé sur internet.

Je vous recommande aussi d’utiliser faill2ban pour limiter les attaques de force brute sur vos serveurs web Apache2.
