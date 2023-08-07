Pour gérer et exploiter vos logs Linux, nous utiliserons un serveur rsyslog.

Voyons ensemble comment le protocole fonctionne, et pourquoi installer ce type de serveur.

Découvrez syslog.

Quand vos logs vous sont remontés, ils contiennent beaucoup d’informations sur ce qui se passe sur votre système.

Le protocole syslog est utilisé pour l'envoi et la réception de logs dans un format particulier, à partir de divers systèmes. Les messages incluent les horodatages, les messages d'événements, la criticité, les adresses IP, les diagnostics, etc., mais de façon digeste.

Le protocole syslog a été conçu pour surveiller les périphériques réseaux et systèmes afin d'envoyer des messages de notification en cas de dysfonctionnement.

Il peut vous envoyer aussi des alertes pour les événements prénotifiés, et surveiller les activités suspectes via les différents journaux de monitoring.

Le protocole syslog a été initialement écrit par Eric Allman, et est défini dans la RFC 3164, un des documents officiels qui décrit les spécifications techniques de l'Internet. Les messages sont envoyés à travers le réseau IP vers les collecteurs de messages d'événements ou les serveurs syslog. Syslog utilise le protocole UDP (User Datagram Protocol), port 514, pour communiquer. Depuis 2009, Syslog a été normalisé par l'Internet Engineering Task Force dans la RFC 5424.

Il existe 3 versions différentes de syslog :

- Syslog : la version initiale dont nous venons de discuter. Les autres versions sont des versions améliorées. 

- Syslog-ng : il étend les fonctionnalités initiales en ajoutant le filtrage basé sur le contenu, le support TCP et le chiffrement TLS.

- Rsyslog : la dernière version, mais aussi la plus utilisée. 

Dans ce cours, nous nous concentrerons sur Rsyslog. Il fonctionne sur le modèle client/serveur. Par défaut, les logs sont gérés localement. Votre serveur Rsyslog sera un point unique de centralisation, auquel vos clients pourront envoyer leurs logs.

Les logs sont classés selon plusieurs thématiques :

```

```
