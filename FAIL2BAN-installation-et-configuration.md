![Debian_logo-01](./images/Cloud-et-securite.png)

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
