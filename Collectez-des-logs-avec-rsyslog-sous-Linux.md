![Apache_logo](./images/Cloud-et-securite.png)

## CYBERSÉCURITÉ / Collectez des logs avec rsyslog sous Linux.

Pour gérer et exploiter vos logs Linux, nous utiliserons un serveur rsyslog.

Voyons ensemble comment le protocole fonctionne, et pourquoi installer ce type de serveur.

Découvrez syslog.

Quand vos logs vous sont remontés, ils contiennent beaucoup d’informations sur ce qui se passe sur votre système.

Le protocole syslog est utilisé pour l'envoi et la réception de logs dans un format particulier, à partir de divers systèmes. Les messages incluent les horodatages, les messages d'événements, la criticité, les adresses IP, les diagnostics, etc., mais de façon digeste.

![RSyslog-00.png](./images/RSyslog-00.png)

Le protocole syslog a été conçu pour surveiller les périphériques réseaux et systèmes afin d'envoyer des messages de notification en cas de dysfonctionnement.

Il peut vous envoyer aussi des alertes pour les événements prénotifiés, et surveiller les activités suspectes via les différents journaux de monitoring.

Le protocole syslog a été initialement écrit par Eric Allman, et est défini dans la RFC 3164, un des documents officiels qui décrit les spécifications techniques de l'Internet. Les messages sont envoyés à travers le réseau IP vers les collecteurs de messages d'événements ou les serveurs syslog. Syslog utilise le protocole UDP (User Datagram Protocol), port 514, pour communiquer. Depuis 2009, Syslog a été normalisé par l'Internet Engineering Task Force dans la RFC 5424.

Il existe 3 versions différentes de syslog :

- Syslog : la version initiale dont nous venons de discuter. Les autres versions sont des versions améliorées. 

- Syslog-ng : il étend les fonctionnalités initiales en ajoutant le filtrage basé sur le contenu, le support TCP et le chiffrement TLS.

- Rsyslog : la dernière version, mais aussi la plus utilisée. 

Dans ce cours, nous nous concentrerons sur Rsyslog. Il fonctionne sur le modèle client/serveur. Par défaut, les logs sont gérés localement. Votre serveur Rsyslog sera un point unique de centralisation, auquel vos clients pourront envoyer leurs logs.

Les logs sont classés selon plusieurs thématiques :

| Thématique  |  Définition |
|---    |--   |
|  auth  | utilisé pour des évènements concernant la sécurité ou l'authentification à travers des applications d'accès (type SSH) |
|  authpriv | utilisé pour les messages relatifs au contrôle d'accès |
|  daemon  | utilisé par les différents processus systèmes et d'application |
|  kern  | utilisé pour les messages concernant le kernel |
|  mail | utilisé pour les évènements des services mail |
|  user  | par défaut quand aucun n'est spécifié |
|  local7 | utilisé pour les messages du boot |
|  * | désigne tous les éléments  |
|  none | ne désigne aucun élément |

Les logs sont également classés par log level :
|  Log level  | Signification |
|-----|-----|
| Emerg | urgence, système inutilisable |
| Alert | intervention immédiate nécessaire |
| Crit | erreur système critique |
| Err | erreur de fonctionnement |
| Warning | avertissement |
| Notice | évènement normaux devant être signalés |
| Info | pour information |
| Debug | message de déboguage |

Installez et configurez un serveur rsyslog.

Dans notre cas de figure, la société NeedSec utilise également des machines sous Linux.

Pour créer notre infrastructure, nous allons configurer notre serveur rsyslog sur une machine Ubuntu.

La remontée de logs se fera depuis n’importe quel système Linux.

Votre infrastructure ressemblera à la suivante :

![RSyslog-01.png](./images/RSyslog-01.png)

Tout d’abord, installons rsyslog :
```
sudo apt install rsyslog
```
Pour configurer notre serveur, il suffit d’éditer le fichier /etc/rsyslog.conf et de décommenter les lignes suivantes pour activer la collecte de logs sur le port UDP 514, qui est le port par défaut :
```
# provides UDP syslog reception
module(load="imudp")
input(type="imudp" port="514")
```
Ensuite, redémarrez le service rsyslog avec la commande suivante :
```
systemctl restart rsyslog.service
```
Votre serveur est à présent configuré et prêt à recevoir des logs d’une machine distante !

Configurez une machine pour l’envoi de logs :

Mais pour recevoir des logs, il faut qu’ils soient envoyés.

Nous allons maintenant configurer notre client Linux pour envoyer ses logs à notre serveur de centralisation.

Pour ce faire, éditez le fichier par défaut  ( /etc/rsyslog.d/50-default.conf ).

Pour notre exemple, nous allons ajouter la ligne suivante :
```
auth,authpriv.*                 @192.168.1.38:514
```
Ici, nous voulons enregistrer les logs d’authentification (auth, authpriv) et les transmettre à la machine 192.168.1.38, qui est notre serveur.

Le “@” précise l’adresse IP de destination.

Notez qu’il faut un @ pour UDP et deux @ pour TCP.

Enfin, redémarrez le service.

Interprétez et analysez les logs remontés.

Pour vérifier la remontée de logs, nous allons simuler la tentative de plusieurs connexions sur notre machine cliente sur le port 22 (SSH), en nous connectant avec un mot de passe erroné.

Il suffit ensuite d’afficher les logs d’authentification sur notre serveur.

On voit ici les tentatives de connexion :

```
$tail -f /var/log/auth.log
Nov  1 16:45:50 OCserv sudo: pam_unix(sudo:session): 
session closed for user root
Nov  1 16:47:16 OCserv sshd[10862]: Received disconnect from 
192.168.1.3 port 51728:11: disconnected by user
Nov  1 16:47:16 OCserv sshd[10862]: Disconnected from user 
toto 192.168.1.3 port 51728
Nov  1 16:47:16 OCserv systemd-logind[1029]: Removed session 
1.
Nov  1 16:47:16 OCserv sshd[9294]: pam_unix(sshd:session): 
session closed for user toto
Nov  1 16:47:18 OCserv sshd[22374]: pam_unix(sshd:auth): 
authentication failure; logname= uid=0 euid=0 tty=ssh 
ruser= rhost=192.168.1.3  user=toto
```
Notons les première et dernière tentatives de connexion, où vous pouvez voir des tentatives de connexion avec l'utilisateur root depuis l'adresse IP 192.168.1.3, puis une connexion réussie avec l'utilisateur Toto.

Saviez-vous qu’il existe un client rsyslog pour Windows ? Il peut être intéressant à utiliser pour centraliser vos logs sur rsyslog. Pour en savoir plus sur l'utilisation, vous pouvez visiter la documentation qui lui est dédiée sur le site de rsyslog.












Source : https://openclassrooms.com/fr/courses/1750566-optimisez-la-securite-informatique-grace-au-monitoring/7144797-collectez-des-logs-avec-rsyslog-sous-linux
