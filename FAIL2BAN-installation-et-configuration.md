
## FAIL2BAN instalation et configuration.

Bannir des IP avec fail2ban.

fail2ban lit les logs de divers serveurs (ssh, apache, ftp,…) à la recherche d'erreurs d'authentification répétées et ajoute une règle iptables pour bannir l'adresse IP de la source. 

Installez le paquet fail2ban disponible dans les dépôts Universe. 
```
apt-get install fail2ban
```
Pour spécifier à fail2ban quels services il doit surveiller, éditez le fichier /etc/fail2ban/jail.conf 

Dans la partie jail vous trouverez des blocs du type : 
```
nano /etc/fail2ban/jail.conf
```
```
[ssh]

enabled = true
port    = ssh,sftp
filter  = sshd
logpath  = /var/log/auth.log
maxretry = 6
```
Il indique, par ordre, l'activation, les ports à bloquer avec les règles iptables, le nom du filtre (expression régulière) associé, le fichier de log à lire, le nombre maximal de tentatives. 
Un certain nombre de services disposent de tels blocs de configuration, vous pouvez les activer en passant si besoin false à true. 

Relancez la configuration avec 
```
sudo fail2ban-client reload
```
Vous pouvez alors vérifier si les prisons ont été correctement lancées avec : 
```
sudo fail2ban-client status 
```
```
Status 
|- Number of jail:	1 
`- Jail list:		ssh 
[12:33 0.00] 
[cybernatus 2] ~ > 
```
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
