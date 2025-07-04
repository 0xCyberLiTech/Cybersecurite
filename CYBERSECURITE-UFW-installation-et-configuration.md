<p align="center">
  <img src="https://avatars.githubusercontent.com/u/167217017?s=400&u=d983b9423c4eb8cdb9bfe8b14f505be5c894d6bc&v=4" width="150" />
</p>

<h1 align="center">🌐 CYBERSÉCURITÉ 🌐</h1>
<h2 align="center">FIREWALL - UFW</h2>

<p align="center">
  Un dépôt pédagogique autour des fondamentaux de la cybersécurité.<br>
  📘 Apprentissage – 🔐 Sécurité – 🧠 Compréhension
</p>

---
<h3 align="left">💡 CYBERSÉCURITÉ / UFW installation et configuration.</h3>
<h3 align="left">👋 Sommaire :</h3>

- 01 - [Installation de UFW.](#balise-01)
- 02 - [Mise en place des politiques par défaut.](#balise-02)
- 03 - [Autoriser les connexions SSH.](#balise-03)
- 04 - [Activation d’UFW.](#balise-04)
- 05 - [Autoriser d’autres connexions.](#balise-05)
- 06 - [Refuser les connexions.](#balise-06)
- 07 - [Suppression de règles.](#balise-07)
- 08 - [Vérification de l’état et des règles d’UFW.](#balise-08)
- 09 - [Exemple Zabbix installé en dur et Grafana déployé sous la forme d'un container (Docker) sur la même machine Zabbix server.](#balise-09)
- 10 - [Désactivation ou réinitialisation d’UFW (facultatif).](#balise-10)

Introduction :

UFW, ou Uncomplicated Firewall, est une interface de gestion de pare-feu simplifiée qui masque la complexité des technologies de filtrage de paquets de niveau inférieur telles que iptables et nftables.

Si vous souhaitez commencer à sécuriser votre réseau, et vous n’êtes pas sûr de l’outil à utiliser, UFW peut être le bon choix pour vous.

<a name="balise-01"></a>
## 01 - Installation de UFW.
```
sudo apt install ufw
```
<a name="balise-02"></a>
## 02 — Mise en place des politiques par défaut.

Si vous commencez tout juste à utiliser votre pare-feu, les premières règles à définir sont vos politiques par défaut.

Ces règles contrôlent la manière de traiter le trafic qui ne correspond pas explicitement à d’autres règles.

Par défaut, UFW est configuré pour refuser toutes les connexions entrantes et autoriser toutes les connexions sortantes.

Cela signifie que toute personne essayant d’atteindre votre serveur ne pourra pas se connecter, tandis que toute application à l’intérieur du serveur pourra atteindre le monde extérieur.

Remettons vos règles UFW à leur valeur par défaut afin que nous puissions être sûrs que vous pourrez suivre ce tutoriel.

Pour définir les valeurs par défaut utilisées par UFW, utilisez ces commandes :

Nous définissons que toutes les connexions entrantes sont bloquées.
```
sudo ufw default deny incoming
```
Nous définissons que toutes les connexions sortantes sont autorisées.
```
sudo ufw default allow outgoing
```
## Activer/désactiver la journalisation.

Activer la journalisation :
```
sudo ufw logging on
```
Désactiver la journalisation :
```
sudo ufw logging off
```
<a name="balise-03"></a>
## 03 — Autoriser les connexions SSH.

Si nous activions notre pare-feu UFW maintenant, il refuserait toutes les connexions entrantes.

Cela signifie que nous devrons créer des règles qui autorisent explicitement les connexions entrantes légitimes – connexions SSH ou HTTP, par exemple – si nous voulons que notre serveur réponde à ce type de demandes.

Si vous utilisez un serveur cloud, vous voudrez probablement autoriser les connexions SSH entrantes afin de pouvoir vous connecter à votre serveur et le gérer.

Pour configurer votre serveur afin d’autoriser les connexions SSH entrantes, vous pouvez utiliser cette commande :
```
sudo ufw allow ssh
```
Cela créera des règles de pare-feu qui autoriseront toutes les connexions sur le port 22, qui est le port que le démon SSH écoute par défaut.

UFW sait quel port allow ssh désigne parce qu’il est listé comme un service dans le fichier /etc/services.

Cependant, nous pouvons réellement écrire la règle équivalente en spécifiant le port au lieu du nom du service.

Par exemple, cette commande fonctionne de la même manière que celle ci-dessus :
```
sudo ufw allow 22
```
Si vous avez configuré votre démon SSH pour utiliser un port différent, vous devrez spécifier le port approprié. Par exemple, si votre serveur SSH écoute sur le port 2222, vous pouvez utiliser cette commande pour autoriser les connexions sur ce port :
```
sudo ufw allow 2222
```
Maintenant que votre pare-feu est configuré pour autoriser les connexions SSH entrantes, nous pouvons l’activer.

<a name="balise-04"></a>
## 04 — Activation d’UFW.

Pour activer UFW, utilisez cette commande :
```
sudo ufw enable
```
Vous recevrez un avertissement qui indique que la commande peut perturber les connexions SSH existantes.

Nous avons déjà mis en place une règle de pare-feu qui autorise les connexions SSH, donc nous pouvons continuer.

Répondez à l’invite avec y et appuyez sur ENTER.

Le pare-feu est maintenant actif. 

Exécutez la commande sudo ufw status verbose pour connaître les règles fixées.

Le reste de ce tutoriel explique plus en détail comment utiliser UFW, par exemple en autorisant ou en refusant différents types de connexions.

<a name="balise-05"></a>
## 05 — Autoriser d’autres connexions.

À ce stade, vous devez autoriser toutes les autres connexions auxquelles votre serveur a besoin de répondre.

Les connexions que vous devez autoriser dépendent de vos besoins spécifiques.

Heureusement, vous savez déjà comment écrire des règles qui autorisent les connexions basées sur un nom de service ou un port ; nous l’avons déjà fait pour SSH sur le port 22.

Vous pouvez également le faire pour :

- HTTP sur le port 80, qui est ce qu’utilisent les serveurs web non cryptés, en utilisant sudo ufw allow http ou sudo ufw allow 80
- HTTPS sur le port 443, qui est ce qu’utilisent les serveurs web cryptés, en utilisant sudo ufw allow https ou sudo ufw allow 443

Il existe plusieurs autres moyens d’autoriser d’autres connexions, outre la spécification d’un port ou d’un service connu.

Plages de ports spécifiques :

Vous pouvez spécifier des plages de ports avec UFW.

Certaines applications utilisent plusieurs ports, au lieu d’un seul.

Par exemple, pour autoriser les connexions X11 qui utilisent les ports 6000-6007, utilisez ces commandes :
```
sudo ufw allow 6000:6007/tcp
```
```
sudo ufw allow 6000:6007/udp
```
Lorsque vous spécifiez des plages de ports avec UFW, vous devez spécifier le protocole (tcp ou udp) auquel les règles doivent s’appliquer. Nous n’avons pas mentionné cela auparavant car le fait de ne pas spécifier le protocole autorise automatiquement les deux protocoles, ce qui est correct dans la plupart des cas.

Adresses IP spécifiques :

Lorsque vous travaillez avec UFW, vous pouvez également spécifier des adresses IP.

Par exemple, si vous souhaitez autoriser les connexions à partir d’une adresse IP spécifique, comme une adresse IP professionnelle ou personnelle de 203.0.113.4, vous devez spécifier from, puis l’adresse IP :
```
sudo ufw allow from 203.0.113.4
```
Vous pouvez également spécifier un port spécifique auquel l’adresse IP est autorisée à vous connecter en ajoutant to any port suivi du numéro de port.

Par exemple, Si vous souhaitez autoriser 203.0.113.4 à se connecter au port 22 (SSH), utilisez cette commande :
```
sudo ufw allow from 203.0.113.4 to any port 22
```
Sous réseaux :

Si vous souhaitez autoriser un sous-réseau d’adresses IP, vous pouvez le faire en utilisant la notation CIDR pour spécifier un masque de réseau.

Par exemple, si vous souhaitez autoriser toutes les adresses IP allant de 203.0.113.1 à 203.0.113.254 vous pourriez utiliser cette commande :
```
sudo ufw allow from 203.0.113.0/24
```
De même, vous pouvez également spécifier le port de destination auquel le sous-réseau 203.0.113.0/24 est autorisé à se connecter.

Une fois encore, nous utiliserons le port 22 (SSH) comme exemple :
```
sudo ufw allow from 203.0.113.0/24 to any port 22
```
Connexion à une interface réseau spécifique :

Si vous souhaitez créer une règle de pare-feu qui s’applique uniquement à une interface réseau spécifique, vous pouvez le faire en spécifiant « allow in on » suivi du nom de l’interface.

Vous pouvez consulter vos interfaces réseau avant de continuer.

Pour ce faire, utilisez cette commande :
```
ip -c addr
```
```
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host noprefixroute
       valid_lft forever preferred_lft forever

2: enp86s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether 58:47:fa:72:14:92 brd ff:ff:ff:ff:ff:ff
    inet 192.168.50.250/24 brd 192.168.50.255 scope global enp86s0
       valid_lft forever preferred_lft forever
    inet6 fe80::5a47:cnf5:f572:1412/64 scope link
       valid_lft forever preferred_lft forever
```
Le résultat mis en évidence indique les noms d’interface réseau.

Elles sont généralement nommées par quelque chose comme : eth0 ou enp3s2.

Donc, si votre serveur a une interface réseau publique appelée eth0, vous pouvez l’autoriser à recevoir du trafic HTTP (port 80) avec cette commande :
```
sudo ufw allow in on eth0 to any port 80
```
Cela permettrait à votre serveur de recevoir des requêtes HTTP de l’Internet public.

Ou, si vous voulez que votre serveur de base de données MySQL (port 3306) écoute les connexions sur l’interface de réseau privé eth1, par exemple, vous pourriez utiliser cette commande :
```
sudo ufw allow in on eth1 to any port 3306
```
Cela permettrait à d’autres serveurs de votre réseau privé de se connecter à votre base de données MySQL.

<a name="balise-06"></a>
## 06 — Refuser les connexions.

Si vous n’avez pas modifié la politique par défaut des connexions entrantes, UFW est configuré pour refuser toutes les connexions entrantes.

En général, cela simplifie le processus de création d’une politique de pare-feu sécurisée en vous obligeant à créer des règles qui autorisent explicitement le passage de ports et d’adresses IP spécifiques.

Cependant, il peut arriver que vous souhaitiez refuser des connexions spécifiques en fonction de l’adresse IP source ou du sous-réseau, peut-être parce que vous savez que votre serveur est attaqué à partir de là. De plus, si vous souhaitez modifier votre politique d’entrée par défaut a allow (ce qui n’est pas recommandé), vous devrez créer des règles deny pour tous les services ou adresses IP pour lesquels vous ne souhaitez pas autoriser les connexions.

Pour écrire des règles deny, vous pouvez utiliser les commandes décrites ci-dessus, en remplaçant allow par deny.

Par exemple, pour refuser des connexions HTTP, vous pourriez utiliser cette commande :
```
sudo ufw deny http
```
Ou si vous souhaitez refuser toutes les connexions à partir de 203.0.113.4 vous pouvez utiliser cette commande :
```
sudo ufw deny from 203.0.113.4
```
Examinons maintenant comment supprimer des règles.

<a name="balise-07"></a>
## 07 — Suppression de règles.

Savoir comment supprimer des règles de pare-feu est tout aussi important que de savoir comment les créer.

Il existe deux façons différentes de spécifier les règles à supprimer : par le numéro de la règle ou par la règle elle-même (de la même façon que les règles ont été spécifiées lors de leur création).

Nous commencerons par la méthode delete by rule number, car elle est plus facile.

Par numéro de règle :

Si vous utilisez le numéro de règle pour supprimer des règles de pare-feu, la première chose que vous voudrez faire est d’obtenir une liste de vos règles de pare-feu.

La commande UFW status permet d’afficher des numéros à côté de chaque règle, comme illustré ici :
```
sudo ufw status numbered
```
```
Numbered Output:
Status: active

     To                         Action      From
     --                         ------      ----
[ 1] 22                         ALLOW IN    15.15.15.0/24
[ 2] 80                         ALLOW IN    Anywhere
```
Si nous décidons que nous voulons supprimer la règle 2, celle qui autorise les connexions sur le port 80 (HTTP), nous pouvons la spécifier dans une commande de suppression UFW comme celle-ci :
```
sudo ufw delete 2
```
Cela affichera une demande de confirmation puis supprimera la règle 2, qui autorise les connexions HTTP.

Notez que si vous avez activé IPv6, vous voudrez également supprimer la règle IPv6 correspondante.

Par règle réelle :

L’alternative aux numéros de règle est de spécifier la règle réelle à supprimer.

Par exemple, si vous voulez supprimer la règle allow http, vous pouvez l’écrire comme ceci :
```
sudo ufw delete allow http
```
Vous pouvez également spécifier la règle par allow 80, au lieu de par nom de service :
```
sudo ufw delete allow 80
```
Cette méthode supprimera les règles IPv4 et IPv6, si elles existent.
<a name="balise-08"></a>
## 08 — Vérification de l’état et des règles d’UFW.

À tout moment, vous pouvez vérifier le statut d’UFW avec cette commande :
```
sudo ufw status verbose
```
Si UFW est désactivé, ce qui est le cas par défaut, vous verrez quelque chose comme ceci :
```
Output
Status: inactive
```
Si UFW est actif, ce qui devrait être le cas si vous avez suivi l’étape 3, la sortie indiquera qu’il est actif et énumérera toutes les règles qui sont définies. Par exemple, si le pare-feu est configuré pour autoriser les connexions SSH (port 22) de n’importe où, la sortie pourrait ressembler à ceci :
```
Output
Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing), disabled (routed)
New profiles: skip

To                         Action      From
--                         ------      ----
22/tcp                     ALLOW IN    Anywhere
```
<a name="balise-09"></a>
## 09 - Exemple Zabbix installée en dur et Grafana déployé sous la forme d'un container (Docker) sur la même machine Zabbix server.

Ouvrir le port SSH approprié en entrée, afin d'avoir la main sur votre serveur Zabbix à distance.

Dans cet exemple, je n'autorise que la machine distante 192.168.50.118 à pouvoir accéder en SSH sur le serveur Zabbix au travers du port 2277 en TCP en entrée.
```
ufw limit in on enp86s0 from 192.168.50.118 to 192.168.50.250 port 2277 proto tcp comment '2277 SSH'
```
La variable 'limit' correspond à n'autoriser que 6 tentatives de connexion en 30 secondes sur notre règle. 

Cela permet de renfocer un peu plus la sécurité.

Ouvrir le port 80 sur le serveur Zabbix ainsi que le port 443 en entrée.
```
ufw allow in on enp86s0 from 192.168.50.118 to 192.168.50.250 port 80 proto tcp comment '80 Apache2'
```
```
ufw allow in on enp86s0 from 192.168.50.118 to 192.168.50.250 port 443 proto tcp comment '443 Apache2'
```
- Il faut autoriser le LANSUBNET 192.168.0.0/16 à communiquer vers le serveur Zabbix (192.168.50.250) à travers le port 10050 en TCP, pour le mode passif.
- Il faut autoriser le LANSUBNET 192.168.0.0/16 à communiquer vers le serveur Zabbix (192.168.50.250) à travers le port 10051 en TCP, pour le mode actif.

Ces ports doivent être ouverts en entrée sur le serveur Zabbix, afin de recueillir les communications en provenance des agent Zabbix des hôtes distants, que ce soit en mode passif ou en mode actif.
```
ufw allow in on enp86s0 from 192.168.0.0/16 to 192.168.50.250 port 10050 proto tcp comment '1050 agent Zabbix - For Passive checks'
```
```
ufw allow in on enp86s0 from 192.168.0.0/16 to 192.168.50.250 port 10051 proto tcp comment '1051 agent Zabbix - For Active checks'
```
Lister les règles en service :
```
ufw status numbered
```
```
     To                                    Action      From
     --                                    ------      ----
[ 1] 192.168.50.250 2277/tcp    on enp86s0 ALLOW IN    192.168.50.118             # 2277 SSH
[ 2] 192.168.50.250 80/tcp      on enp86s0 ALLOW IN    192.168.50.118             # 80 Apache2
[ 3] 192.168.50.250 443/tcp     on enp86s0 ALLOW IN    192.168.50.118             # 443 Apache2
[ 4] 192.168.50.250 10050/tcp   on enp86s0 ALLOW IN    192.168.0.0/16             # 1050 agent Zabbix - For Passive checks
[ 5] 192.168.50.250 10051/tcp   on enp86s0 ALLOW IN    192.168.0.0/16             # 1051 agent Zabbix - For Active checks
```
Poursuivons :

Dans cet exemple, nous avons installé Docker sur notre serveur Zabbix et également déployé Grafana sous la forme d'un container sur celui-ci.
Zabbix est installé en du sur notre serveur Zabbix.

De nouvelles règles seront mises en service afin d'assurer la communication entre docker, Grafana et votre réseau local.
```
ufw allow from 172.17.0.0/16 to 192.168.50.0/24 proto tcp comment 'LANSUBNET 172.17.0.0 Docker'
```
```
ufw allow from 172.18.0.0/16 to 192.168.50.0/24 proto tcp comment 'LANSUBNET 172.18.0.0 Docker'
```
Permettre l'accès depuis la machine hôte au portail Portainer.
```
ufw allow in on enp86s0 from 192.168.50.118 to 192.168.50.250 port 9443 proto tcp comment '9443 portail Portainer - Docker'
```
Lister à nouveau les règles mis en service :
```
ufw status numbered
```
```
     To                                             Action      From
     --                                             ------      ----
[ 1] 192.168.50.250             2277/tcp on enp86s0 LIMIT IN    192.168.50.118             # 2277 SSH
[ 2] 192.168.50.250               80/tcp on enp86s0 ALLOW IN    192.168.50.118             # 80 Apache2
[ 3] 192.168.50.250              443/tcp on enp86s0 ALLOW IN    192.168.50.118             # 443 Apache2
[ 4] 192.168.50.250            10050/tcp on enp86s0 ALLOW IN    192.168.0.0/16             # 1050 agent Zabbix - For Passive checks
[ 5] 192.168.50.250             9443/tcp on enp86s0 ALLOW IN    192.168.50.118             # 9443 portail Portainer - Docker
[ 6] 192.168.50.0/24/tcp                            ALLOW IN    172.17.0.0/16/tcp          # LANSUBNET 172.17.0.0 Docker
[ 7] 192.168.50.0/24/tcp                            ALLOW IN    172.18.0.0/16/tcp          # LANSUBNET 172.18.0.0 Docker
[ 8] 192.168.50.250            10051/tcp on enp86s0 ALLOW IN    192.168.0.0/16             # 1051 agent Zabbix - For Active checks
```
<a name="balise-10"></a>
## 10 - Désactivation ou réinitialisation d’UFW (facultatif).

Si vous décidez que vous ne voulez pas utiliser UFW, vous pouvez le désactiver avec cette commande :
```
sudo ufw disable
```
Toutes les règles que vous avez créées avec UFW ne seront plus actives.

Vous pourrez toujours exécuter la commande sudo ufw enable si vous devez l’activer plus tard.

Si vous avez déjà configuré des règles UFW mais que vous décidez de tout recommencer, vous pouvez utiliser la commande reset :
```
sudo ufw reset
```
Cela désactivera l’UFW et supprimera toutes les règles qui ont été définies précédemment.

Gardez à l’esprit que les règles par défaut ne retrouveront pas leurs paramètres d’origine, si vous les avez modifiées à un moment quelconque.

Cela devrait vous permettre de repartir à zéro avec UFW.

---

## 🌐 À propos de moi

- 💡 Passionné par Debian GNU/Linux depuis plusieurs années
- 🎓 Autodidacte, avec un fort esprit de transmission
- 🔐 Intéressé par la cybersécurité, les solutions open source et la performance système
- 🧪 Toujours partant pour tester une nouvelle stack technique

---

<p align="center">
  🔒 Un guide proposé par <a href="https://github.com/0xCyberLiTech">0xCyberLiTech</a> • Pour des tutoriels accessible à tous.
</p>

