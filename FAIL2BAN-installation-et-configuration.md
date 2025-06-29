<p align="center">
  <img src="./images/Cloud-et-securite.png" alt="Cloud et Sécurité" width="300">
</p>

<h1 align="center">🛡️ CYBERSÉCURITÉ – FAIL2BAN</h1>

<p align="center">
   Fail2ban est un outil open source de protection contre les attaques par force brute.
</p>

---

## CYBERSÉCURITÉ / FAIL2BAN installation et configuration.

C'est quoi Fail2ban ?

Fail2ban lit des fichiers de log présents sur votre serveur pour détecter les adresses IP essayant d'accéder à vos services en générant de nombreux échecs lors de l'authentification.

Fail2ban bannit ces adresses IP suspectes en mettant à jour les règles du pare-feu pour rejeter ces adresses.

Ces règles peuvent être définies par l'utilisateur.

Fail2ban peut lire plusieurs fichiers de log comme ceux de sshd ou du serveur nginx.

Installation de Fail2ban :

On commence par installer le paquet.
```
sudo apt-get install fail2ban
```
Le fichier /etc/fail2ban/jail.conf contient l'ensemble des plugins que vous pouvez activer pour protéger les services de votre serveur.

Mais vous ne devez pas modifier ce fichier directement. Car lors des mises à jour de votre Debian, il peut être remplacé à tout moment avec une version plus récente.
```
nano /etc/fail2ban/jail.conf
```
Fail2ban permet de surveiller et de protéger de nombreux services sur votre serveur : SSH, nginx, postfix, FTP...
La configuration de chaque service est contenu dans une section spécifique [sshd] pour le service SSH qui est le seul actif par défaut.

Pour activer la surveillance d'un service, il faut placer la variable enabled à true dans la section du service.
Si vous avez modifier le port par défaut de SSH (pour ne pas utiliser 22), pensez de l'indiquer ici dans la variable port.

Pour activer et configurer les plugins de votre choix, vous devez spécifier vos paramètres personnes dans le fichier /etc/fail2ban/jail.local.

En fait, Fail2ban charge les configurations dans cet ordre : 

/etc/fail2ban/jail.conf
puis /etc/fail2ban/jail.d/defaults-debian.conf
et enfin /etc/fail2ban/jail.local
On crée donc notre fichier de config perso:

```
sudo nano /etc/fail2ban/jail.local
```

Et on commence donc par coller le bout de configuration ci-dessous pour activer le plugin sshd et spécifier le numéro de port SSH si vous l'avez modifié (Attention 44422 est mon numéro de port à moi!)

[sshd]
port = 2267
enabled = true

Ce plugin surveille les tentatives de connexions SSH sur votre serveur.

Par défaut, si Fail2ban détecte 5 tentatives de connexion erronées durant les 600 dernières secondes (soit 10 minutes), l'IP ayant essayé de se connecter sera bloquée 600s (10 min).

Ces constantes sont définies de manières globales pour tous les plugins (section [DEFAULT] du fichier /etc/fail2ban/jail.conf

```
# "bantime" is the number of seconds that a host is banned.
bantime  = 10m

# A host is banned if it has generated "maxretry" during the last "findtime"
# seconds.
findtime  = 10m

# "maxretry" is the number of failures before a host get banned.
maxretry = 5
Mais depuis votre fichier jail.local, vous pouvez les sur-définir au niveau de la configuration d'un plugin.

[sshd]
enabled = true
# 1 jour de bannissement
bantime  = 1d
```
Ou de manière globale pour tous les plugins. Noté que j'ai spécifié 1 jour en secondes ici (86400 = 24 * 60 * 60) pour vous montrer une autre manière de configurer la durée.

Vous trouverez les différents formats utilisables sur cette page.
```
[DEFAULT]
# 1 jour de bannissement pour tous les plugins
bantime = 86400
```
Reste à redémarrer le servie fail2ban pour prendre en compte les modifications de la configuration.
```
sudo systemctl restart fail2ban.service
```
Ne pas vous faire bannir de votre serveur !

Je vous recommande d'exclure votre adresse IP personnelle du scope de Fail2ban. Cela vous évitera de vous faire bannir de votre propre serveur !

Pour cela, ouvrez à nouveau le fichier de configuration /etc/fail2ban/jail.local
```
sudo nano /etc/fail2ban/jail.local
```
Et ajouter la variable ignoreip  dans la section [DEFAULT] du fichier.
Remplacez 123.456.789.101 par votre adresse IP (ou vos adresses).
```
[DEFAULT]
ignoreip = 127.0.0.1/8 123.456.789.123
```
Ca fonctionne ?

Après quelques heures ou jours de fonctionnement de Fail2ban, allez jeter un coup d'oeil dans son fichier de log
```
sudo nano /var/log/fail2ban.log
```
Vous serez très surpris de voir le nombre de connexions SSH bloquées par fail2ban...

Il y a plein de robots sur Internet qui scannent les serveurs à la recherche de vulnérabilités.

Configuration de plugins additionnels :

Pour activer et configurer les plugins de votre choix, ça se passe donc dans /etc/fail2ban/jail.local
```
sudo nano /etc/fail2ban/jail.local
```
Voici un exemple de config qui protège postfix et dovecot
```
[DEFAULT]
# 1 jour de bannissement pour tous les plugins
bantime = 86400

[sshd]
enabled = true
# 3 mots de passe erronés consécutifs et c'est le bannissement direct pour SSH
maxretry = 3

[postfix]
port = smtp,submission
enabled = true

[dovecot]
port = imaps
enabled = true
```
N'oubliez pas de redémarrer le service Fail2ban pour activer vos modifications
```
sudo systemctl restart fail2ban.service
```
Je joins un exemple concernant le fichier jail.local :
```
[DEFAULT]
# 1 jour de bannissement pour tous les plugins
bantime = 86400



# Protection SSH contre la force brute :
# Créez une prison personnalisée pour vous protéger contre les attaques brute de force SSH en analysant le fichier journal SSH à la recherche de plusieurs tentatives de connexion infructueuses dans un délai spécifié.

[sshd-custom]
port = 2234
enabled = true
filter = sshd
logpath = /var/log/auth.log
bantime = 3600
findtime = 600
maxretry = 3
action = iptables-multiport[name=sshd, port="ssh", protocol=tcp]



# Authentification HTTP Nginx :
# Configurez une prison pour vous protéger contre les attaques par brute de force ciblant l'authentification HTTP Nginx en surveillant les fichiers journaux Nginx pour les tentatives d'authentification infructueuses répétées.

#[nginx-http-auth-custom]
#enabled = true
#filter = nginx-http-auth
#logpath = /var/log/nginx/error.log
#bantime = 1800
#findtime = 300
#maxretry = 5
#action = iptables-multiport[name=nginx, port="http,https", protocol=tcp]



# Authentification SMTP Postfix :
# Configurez une prison personnalisée pour protéger votre serveur de messagerie Postfix contre les attaques par brute de force SMTP en surveillant les fichiers journaux de Postfix pour les échecs d'authentification répétés.

#[postfix-smtp-auth-custom]
#enabled = true
#filter = postfix-auth
#logpath = /var/log/mail.log
#bantime = 3600
#findtime = 600
#maxretry = 5
#action = iptables-multiport[name=postfix, port="smtp", protocol=tcp]



# Authentification Dovecot IMAP/POP3 :
# Implémentez une prison personnalisée pour sécuriser votre serveur de messagerie Dovecot contre les attaques par brute de force d'authentification IMAP et POP3 en surveillant les fichiers journaux Dovecot pour les échecs d'authentification répétés.


#[dovecot-imap-pop3-auth-custom]
#enabled = true
#filter = dovecot-auth
#logpath = /var/log/dovecot.log
#bantime = 3600
#findtime = 600
#maxretry = 5
#action = iptables-multiport[name=dovecot, port="imap,imaps,pop3,pop3s", protocol=tcp]



# Protection de connexion WordPress :
# Créez une prison personnalisée pour protéger votre site Web WordPress contre les attaques de connexion par brute de force en analysant le journal d'accès à la recherche de plusieurs tentatives de connexion infructueuses.

#[wordpress-login-custom]
#enabled = true
#filter = wordpress-auth
#logpath = /var/log/nginx/access.log
#bantime = 1800
#findtime = 300
#maxretry = 5
#action = iptables-multiport[name=wordpress, port="http,https", protocol=tcp]



# Protection de l'authentification MySQL :
# Sécurisez votre serveur MySQL contre les attaques par brute de force ciblant l'authentification MySQL en surveillant le journal des erreurs MySQL.

#[mysql-auth-custom]
#enabled = true
#filter = mysql-auth
#logpath = /var/log/mysql/error.log
#bantime = 3600
#findtime = 600
#maxretry = 5
#action = iptables-multiport[name=mysql, port="3306", protocol=tcp]



# Protection de connexion FTP :
# Configurez une prison personnalisée pour protéger votre serveur FTP des attaques de connexion par brute de force en surveillant le journal du serveur FTP.

#[vsftpd-custom]
#enabled = true
#filter = vsftpd
#logpath = /var/log/vsftpd.log
#bantime = 3600
#findtime = 600
#maxretry = 3
#action = iptables-multiport[name=vsftpd, port="ftp", protocol=tcp]



# Protection de l'authentification Apache :
# Configurez une prison personnalisée pour protéger votre serveur Apache contre les attaques par brute de force ciblant l'authentification HTTP en analysant les fichiers journaux Apache.

[apache-auth-custom]
enabled = true
filter = apache-auth
logpath = /var/log/apache2/error.log
bantime = 1800
findtime = 300
maxretry = 5
action = iptables-multiport[name=apache, port="http,https", protocol=tcp]



# Protection de connexion à la messagerie Web Roundcube :
# Implémentez une prison personnalisée pour protéger votre messagerie Web Roundcube contre les attaques par brute de force de connexion en surveillant les fichiers journaux Roundcube.

#[roundcube-auth-custom]
#enabled = true
#filter = roundcube-auth
#logpath = /var/log/roundcube/errors.log
#bantime = 1800
#findtime = 300
#maxretry = 5
#action = iptables-multiport[name=roundcube, port="http,https", protocol=tcp]



# Protection du partage de fichiers Samba :
# Créez une prison personnalisée pour protéger votre serveur de partage de fichiers Samba contre les attaques par brute de force en surveillant les fichiers journaux Samba.

#[samba-custom]
#enabled = true
#filter = samba
#logpath = /var/log/samba/log.*
#bantime = 3600
#findtime = 600
#maxretry = 5
#action = iptables-multiport[name=samba, port="139,445", protocol=tcp]



# Protection de connexion Joomla :
# Configurez une prison personnalisée pour protéger votre site Web Joomla contre les attaques par brute de force de connexion en analysant le journal d'accès pour les tentatives de connexion infructueuses.

#[joomla-login-custom]
#enabled = true
#filter = joomla-auth
#logpath = /var/log/nginx/access.log
#bantime = 1800
#findtime = 300
#maxretry = 5
#action = iptables-multiport[name=joomla, port="http,https", protocol=tcp]



# Protection de connexion Drupal :
# Créez une prison personnalisée pour sécuriser votre site Web Drupal contre les attaques brutede force de connexion en surveillant le journal d'accès pour plusieurs tentatives de connexion infructueuses.

#[drupal-login-custom]
#enabled = true
#filter = drupal-auth
#logpath = /var/log/nginx/access.log
#bantime = 1800
#findtime = 300
#maxretry = 5
#action = iptables-multiport[name=drupal, port="http,https", protocol=tcp]



# Protection de connexion Moodle :
# Implémentez une prison personnalisée pour protéger votre plate-forme d'apprentissage en ligne Moodle contre les attaques par brute de force de connexion en analysant le journal d'accès pour les tentatives de connexion infructueuses répétées.

#[moodle-login-custom]
#enabled = true
#filter = moodle-auth
#logpath = /var/log/nginx/access.log
#bantime = 1800
#findtime = 300
#maxretry = 5
#action = iptables-multiport[name=moodle, port="http,https", protocol=tcp]



# Protection de connexion Nextcloud :
# Configurez une prison personnalisée pour protéger votre instance Nextcloud contre les attaques par brute de force de connexion en surveillant le fichier journal Nextcloud pour plusieurs tentatives de connexion infructueuses.

#[nextcloud-login-custom]
#enabled = true
#filter = nextcloud-auth
#logpath = /var/nextcloud/data/nextcloud.log
#bantime = 3600
#findtime = 600
#maxretry = 5
#action = iptables-multiport[name=nextcloud, port="http,https", protocol=tcp]



# Protection de connexion ProFTPD :
# Configurez une prison personnalisée pour sécuriser votre serveur ProFTPD contre les attaques de connexion par brute de force en analysant le fichier journal ProFTPD pour les tentatives de connexion infructueuses répétées.

#[proftpd-custom]
#enabled = true
#filter = proftpd
#logpath = /var/log/proftpd/proftpd.log
#bantime = 3600
#findtime = 600
#maxretry = 3
#action = iptables-multiport[name=proftpd, port="ftp", protocol=tcp]



# Protection d'authentification OpenVPN :
# Créez une prison personnalisée pour protéger votre serveur OpenVPN contre les attaques par brute de d'authentification en surveillant les fichiers journaux OpenVPN.

#[openvpn-auth-custom]
#enabled = true
#filter = openvpn
#logpath = /var/log/openvpn.log
#bantime = 3600
#findtime = 600
#maxretry = 3
#action = iptables-multiport[name=openvpn, port="1194", protocol=udp]



# Protection d'authentification SMTP Exim :
# Configurez une prison personnalisée pour protéger votre serveur de messagerie Exim contre les attaques par brute de force d'authentification SMTP en analysant les fichiers journaux Exim.

#[exim-smtp-auth-custom]
#enabled = true
#filter = exim-auth
#logpath = /var/log/exim/main.log
#bantime = 3600
#findtime = 600
#maxretry = 5
#action = iptables-multiport[name=exim, port="smtp", protocol=tcp]



# Protection de connexion au panneau Plesk :
# Implémentez une prison personnalisée pour sécuriser votre panneau Plesk contre les attaques par brute de force de connexion en surveillant les fichiers journaux de Plesk pour plusieurs tentatives de connexion infructueuses.

#[plesk-panel-login-custom]
#enabled = true
#filter = plesk-panel-auth
#logpath = /var/log/plesk/panel.log
#bantime = 1800
#findtime = 300
#maxretry = 5
#action = iptables-multiport[name=plesk, port="http,https", protocol=tcp]



# Protection de connexion cPanel :
# Configurez une prison personnalisée pour protéger votre serveur cPanel contre les attaques par brute de force de connexion en analysant les fichiers journaux cPanel pour les tentatives de connexion infructueuses répétées.

#[cpanel-login-custom]
#enabled = true
#filter = cpanel-auth
#logpath = /var/log/cpanel/login_log
#bantime = 1800
#findtime = 300
#maxretry = 5
#action = iptables-multiport[name=cpanel, port="2082,2083,2086,2087", protocol=tcp]



# Protection de connexion Webmin :
# Créez une prison personnalisée pour sécuriser votre serveur Webmin contre les attaques par brute de force de connexion en surveillant les fichiers journaux Webmin pour plusieurs tentatives de connexion infructueuses.

#[webmin-login-custom]
#enabled = true
#filter = webmin-auth
#logpath = /var/log/webmin/miniserv.log
#bantime = 1800
#findtime = 300
#maxretry = 5
#action = iptables-multiport[name=webmin, port="10000", protocol=tcp]

```

---

<p align="center">
  🔒 Un guide proposé par <a href="https://github.com/0xCyberLiTech">0xCyberLiTech</a> • Pour une cybersécurité accessible à tous.
</p>

