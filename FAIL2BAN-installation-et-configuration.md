![Debian_logo-01](./images/Cloud-et-securite.png)

## CYBERSÉCURITÉ / FAIL2BAN installation et configuration.

Bannir des IP avec fail2ban.

fail2ban lit les logs de divers serveurs (ssh, apache, ftp,…) à la recherche d'erreurs d'authentification répétées et ajoute une règle iptables pour bannir l'adresse IP de la source. 

Installez le paquet fail2ban disponible dans les dépôts Universe. 
```
apt-get install fail2ban
```
Configurer les services :

Les services se configurent dans le fichier /etc/fail2ban/jail.conf

La section [DEFAULT] indique les prises de décisions par fail2ban si dans chaque service rien n'est défini
Copier vers le presse-papierCode :
```
ignoreip = 127.0.0.1/8            # adresses IP ignorées par les actions de fail2ban
bantime  = 600                    # temps de bannissement en secondes
maxretry = 3                      # nombre d'essais au bout du quel fail2ban bannit notre intrus
banaction = iptables              # Méthode de BAN (iptables = Que le port concerné / iptables-multiport = Tous les ports / ...)
protocol = tcp                    # protocole par défaut des jails définies ci-dessous
enabled = false                   # Statut par défaut des jails définies ci-dessous (par défaut tout désactivé)
```
Pour ignorer plusieurs IP, on les sépare par un espace. Des adresses ou réseaux peuvent être spécifiés :
```
ignoreip = 127.0.0.1 192.168.21.0/24 212.1.2.3
```
SSH

Nous allons configurer fail2ban pour bannir les intrus passant par ssh.

Voici un exemple de service actif, intrus banni au bout de 3 essais pour une durée de 15 minutes, juste sur le port SSH (paramètres par défaut).
Copier vers le presse-papier :
```
[sshd]
enabled  = true
port     = ssh
logpath = %(sshd_log)s
backend = %(sshd_backend)s
```
Si on change le port de SSH par exemple 1234

Copier vers le presse-papier.
```
[sshd]
enabled  = true
port     = 1234
logpath = %(sshd_log)s
backend = %(sshd_backend)s
```
On peut aussi « écraser » les valeurs par défaut (maxretry, bantime) en rappelant les options dans le service concerné

Copier vers le presse-papierCode :
```
[sshd]
enabled  = true
port     = ssh
logpath = %(sshd_log)s
backend = %(sshd_backend)s
maxretry = 2
bantime  = 3600
```
La récidive

Si le client récidive, on peut activer le filtre recidive qui poursuit le temps de ban :

Copier vers le presse-papierCode BASH :
```
[recidive]
enabled = true
logpath  = /var/log/fail2ban.log
banaction = %(banaction_allports)s
bantime  = 1w
findtime = 1d
```
Relancez la configuration avec 
```
sudo fail2ban-client reload
```
Vous pouvez alors vérifier si les prisons ont été correctement lancées avec : 
```
sudo fail2ban-client status 
```
Test de la configuration

Sur le serveur on lance un tail -f /var/log/fail2ban.log.

On tente de se connecter en SSH (dans mon exemple) plus de 2 fois et on vérifie qu'on est bien banni:

Les prisons peuvent être contrôlées séparément avec les mots clés start,stop,status Par exemple :
```
sudo fail2ban-client stop ssh
```
```
Jail stopped
```
Configuration avancée :

A chaque service est associé un fichier de configuration dans le dossier /etc/fail2ban/filter.d 

Une expression régulière définit les lignes du log qui signalent une erreur d'authentification. 

Il est possible de spécifier via une regex des exceptions, ie des lignes à ignorer.

Cela peut être utile par exemple pour ne pas bannir les IP provenant de votre réseau local. 

Exemple avec la règle anti-w00tw00t :

Voici un exemple, pour bannir les désormais célèbres requêtes DFind w00tw00t.

Dans le fichier /etc/fail2ban/jail.conf on ajoute : 
```
nano  /etc/fail2ban/jail.conf
```
```
[apache-w00tw00t]
enabled = true
filter = apache-w00tw00t
action = iptables[name=Apache-w00tw00t,port=80,protocol=tcp]
logpath = /var/log/apache2/access*.log
maxretry = 1
```
On notera que contrairement aux autres règles, celle-ci s'attaque au fichier de log des accès (/var/log/apache2/access*.log). 

Voici le fichier de règles /etc/fail2ban/filter.d/apache-w00tw00t.conf 
```
nano /etc/fail2ban/filter.d/apache-w00tw00t.conf
```
```
[Definition]
failregex = ^<HOST> -.*"GET \/w00tw00t\.at\.ISC\.SANS\.DFind\:\).*".*
ignoreregex =
```
On teste maintenant si la règle s'applique bien en faisant : 
```
fail2ban-regex /var/log/apache2/access.log /etc/fail2ban/filter.d/apache-w00tw00t.conf
```
Si vous subissez ce genre d'attaque, on peut voir en sortie de ce programme les adresses des spammeurs.

Les règles iptables sont automatiquement crées en conséquence. 
