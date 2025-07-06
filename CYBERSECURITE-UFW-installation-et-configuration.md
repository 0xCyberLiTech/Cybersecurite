<div align="center">

<a href="https://github.com/0xCyberLiTech">
  <img src="https://readme-typing-svg.herokuapp.com?font=Fira+Code&size=32&pause=1000&color=33FF33&center=true&vCenter=true&width=1050&lines=Cybersécurité+et+Pare-feu+UFW;Installation+et+Configuration+pas+à+pas;Filtrage+des+ports+et+sécurisation+des+connexions" alt="Titre dynamique UFW" />
</a>

<p>
  <em style="color:#888">Un dépôt <strong>pédagogique</strong> sur les firewalls Linux.</em><br>
  <strong>📘 Apprentissage – 🔐 Sécurité – 🧠 Compréhension</strong>
</p>

</div>

---

### 👨‍💻 **À propos de moi.**

> Ce dépôt constitue mon laboratoire numérique où je consigne rigoureusement mes apprentissages et expérimentations.
> Passionné par l'écosystème Linux et la cybersécurité, je documente mon parcours et mes projets sur mon GitHub.
> Vous y trouverez des guides pratiques sur la supervision (Zabbix, Nagios), la conteneurisation (Docker) et la sécurisation de serveurs Debian.
> Mon objectif : partager mes connaissances de manière claire et pédagogique.
> N'hésitez pas à y jeter un œil : https://github.com/0xcyberlitech

<p align="center">
  <a href="https://skillicons.dev">
    <img src="https://skillicons.dev/icons?i=linux,debian,bash,docker,nginx,grafana,prometheus,git,vim" />
  </a>
</p>

---

### 🧭 Sommaire :

| 🔢 **Chapitre** | 📝 **Description** | 🚀 **Accès Rapide** |
|----------------|--------------------|---------------------|
| 01. Installation                | Mise en place initiale de UFW.                                        | [<img src="https://img.shields.io/badge/EXPLORER-brightgreen?style=for-the-badge&logo=github&logoColor=white">](#balise-01) |
| 02. Politiques par défaut      | Définir les règles par défaut (deny, allow).                          | [<img src="https://img.shields.io/badge/EXPLORER-brightgreen?style=for-the-badge&logo=github&logoColor=white">](#balise-02) |
| 03. Connexions SSH             | Autoriser les connexions SSH entrantes.                               | [<img src="https://img.shields.io/badge/EXPLORER-brightgreen?style=for-the-badge&logo=github&logoColor=white">](#balise-03) |
| 04. Activation                 | Activer UFW et appliquer les règles.                                  | [<img src="https://img.shields.io/badge/EXPLORER-brightgreen?style=for-the-badge&logo=github&logoColor=white">](#balise-04) |
| 05. Autres connexions          | Autoriser des services supplémentaires (HTTP, etc.).                  | [<img src="https://img.shields.io/badge/EXPLORER-brightgreen?style=for-the-badge&logo=github&logoColor=white">](#balise-05) |
| 06. Refus de connexions        | Bloquer certains ports ou services.                                   | [<img src="https://img.shields.io/badge/EXPLORER-brightgreen?style=for-the-badge&logo=github&logoColor=white">](#balise-06) |
| 07. Suppression de règles      | Supprimer des règles existantes.                                      | [<img src="https://img.shields.io/badge/EXPLORER-brightgreen?style=for-the-badge&logo=github&logoColor=white">](#balise-07) |
| 08. État & règles d’UFW        | Vérifier l’état du pare-feu et les règles appliquées.                 | [<img src="https://img.shields.io/badge/EXPLORER-brightgreen?style=for-the-badge&logo=github&logoColor=white">](#balise-08) |
| 09. Zabbix & Grafana           | Supervision : Zabbix (natif), Grafana (conteneur Docker).             | [<img src="https://img.shields.io/badge/EXPLORER-brightgreen?style=for-the-badge&logo=github&logoColor=white">](#balise-09) |
| 10. Réinitialisation d’UFW     | Réinitialiser ou désactiver UFW (facultatif).                         | [<img src="https://img.shields.io/badge/EXPLORER-brightgreen?style=for-the-badge&logo=github&logoColor=white">](#balise-10) |

---

## 🔰 Introduction à UFW (Uncomplicated Firewall)
UFW, pour Uncomplicated Firewall, est un outil simplifié de gestion de pare-feu conçu pour rendre l’utilisation de iptables (le système de filtrage réseau de Linux) plus accessible et intuitive, notamment pour les administrateurs débutants ou les utilisateurs non experts en ligne de commande.

## 🎯 Objectifs pédagogiques

### 1 - Comprendre à quoi sert un pare-feu.

Le Pare-feu : Votre Gardien Numérique Incontournable.
Un pare-feu, ou "firewall" en anglais, est un dispositif de sécurité essentiel qui agit comme une barrière protectrice entre votre ordinateur ou votre réseau informatique et le monde extérieur, notamment Internet. Son rôle principal est de surveiller et de contrôler le trafic de données entrant et sortant, en n'autorisant que les communications légitimes et en bloquant celles qui sont potentiellement dangereuses.

Imaginez votre réseau informatique comme une maison. Le pare-feu en serait le portier vigilant, vérifiant l'identité de chaque visiteur et ne laissant entrer que les personnes autorisées, tout en refoulant les intrus.

À quoi sert concrètement un pare-feu ?
La fonction première d'un pare-feu est de sécuriser votre environnement numérique en accomplissant plusieurs tâches cruciales :

Protéger contre les accès non autorisés : Il empêche les pirates informatiques, les logiciels malveillants (virus, vers, chevaux de Troie) et autres menaces de s'infiltrer dans votre système pour y voler des informations personnelles, endommager vos fichiers ou prendre le contrôle de votre appareil.

Filtrer le trafic : Le pare-feu analyse les "paquets" de données qui transitent entre votre réseau et l'extérieur. Il se base sur un ensemble de règles de sécurité prédéfinies pour décider d'autoriser ou de bloquer chaque paquet. Ces règles peuvent être basées sur l'adresse IP de l'expéditeur ou du destinataire, le type de service utilisé (web, email, etc.) ou d'autres critères techniques.

Contrôler les applications : Certains pare-feux peuvent également contrôler quelles applications sur votre ordinateur sont autorisées à se connecter à Internet. Cela permet d'éviter que des logiciels malveillants installés à votre insu ne communiquent avec des serveurs distants pour envoyer vos données.

Créer des journaux d'activité : Les pare-feux enregistrent généralement les tentatives de connexion, qu'elles soient autorisées ou bloquées. Ces journaux peuvent être utiles pour détecter des schémas d'attaque et pour renforcer la sécurité du réseau.

Différents types de pare-feu pour différents besoins
Il existe principalement deux grandes familles de pare-feu :

Les pare-feu logiciels : Ce sont des programmes installés directement sur votre ordinateur. Les systèmes d'exploitation modernes comme Windows et macOS intègrent un pare-feu logiciel de base. C'est la solution la plus courante pour les particuliers.

Les pare-feu matériels : Il s'agit d'équipements physiques, souvent intégrés dans les routeurs (votre box Internet, par exemple), qui protègent l'ensemble d'un réseau domestique ou d'entreprise. Ils offrent une première ligne de défense pour tous les appareils connectés au réseau.

Pour une sécurité optimale, il est souvent recommandé de combiner ces deux types de pare-feu.

En résumé, le pare-feu est un pilier fondamental de la sécurité informatique. Il constitue une défense indispensable pour naviguer sur Internet en toute sérénité, en protégeant vos données et votre vie privée contre un large éventail de menaces numériques. Il est donc primordial de s'assurer que votre pare-feu est activé et correctement configuré.

### 2 - Apprendre à sécuriser un système Linux avec des règles simples.

Sécuriser un système Linux peut sembler complexe, mais quelques règles simples suffisent à renforcer considérablement sa protection contre les menaces les plus courantes. En adoptant de bonnes pratiques dès le départ, vous pouvez ériger une première ligne de défense solide pour votre serveur ou votre ordinateur personnel.

Mettez à jour votre système régulièrement.

La règle la plus fondamentale est de maintenir votre système et vos logiciels à jour. Les mises à jour contiennent des correctifs pour les failles de sécurité découvertes. La plupart des distributions Linux permettent d'automatiser ce processus.

Sur les systèmes basés sur Debian/Ubuntu, vous pouvez utiliser la commande suivante pour mettre à jour votre système :

---Bash
sudo apt update && sudo apt upgrade -y
---

Utilisez des mots de passe robustes et l'authentification par clé SSH
Un mot de passe fort est une barrière essentielle. Assurez-vous d'utiliser une combinaison complexe de lettres majuscules et minuscules, de chiffres et de symboles.

Pour une sécurité accrue, privilégiez l'authentification par clé SSH à la place des mots de passe pour vous connecter à distance. Cela implique de générer une paire de clés (une publique et une privée). La clé publique est placée sur le serveur, tandis que la clé privée reste sur votre ordinateur. La connexion n'est autorisée que si les deux clés correspondent.

Configurez un pare-feu.

Un pare-feu (firewall) contrôle le trafic réseau entrant et sortant. L'outil ufw (Uncomplicated Firewall) est un moyen simple de configurer un pare-feu sur Linux.

Voici quelques commandes de base pour démarrer avec ufw :

Installer ufw (s'il n'est pas déjà présent) :

---Bash
sudo apt install ufw
---

Définir les règles par défaut (refuser tout ce qui entre, autoriser tout ce qui sort) :

---Bash
sudo ufw default deny incoming
---
---Bash
sudo ufw default allow outgoing
---
Autoriser des services spécifiques (par exemple, le SSH, le web) :

---Bash
sudo ufw allow ssh  # ou le numéro de port, ex: sudo ufw allow 22
---
---Bash
sudo ufw allow http # port 80
---
---Bash
sudo ufw allow https # port 443
---
Activer le pare-feu :

---Bash
sudo ufw enable
---

Sécurisez l'accès SSH.

Outre l'utilisation de clés SSH, vous pouvez renforcer la sécurité de votre service SSH en :

Désactivant la connexion de l'utilisateur root : Il est préférable de se connecter avec un utilisateur standard, puis d'utiliser sudo pour les tâches administratives. Pour ce faire, modifiez le fichier /etc/ssh/sshd_config et changez la ligne PermitRootLogin comme suit :

---
PermitRootLogin no
---
Changeant le port SSH par défaut : Le port 22 est la cible de nombreuses attaques automatisées. Changer ce port pour une valeur non standard (par exemple, 2222) dans le fichier /etc/ssh/sshd_config peut réduire le "bruit" des tentatives de connexion malveillantes. N'oubliez pas d'autoriser le nouveau port dans votre pare-feu.

Après toute modification du fichier sshd_config, vous devez redémarrer le service SSH pour que les changements prennent effet :

---Bash
sudo systemctl restart sshd
---
Supprimez les logiciels inutiles.

Chaque logiciel installé sur votre système représente une surface d'attaque potentielle. Désinstallez tous les services et applications dont vous n'avez pas besoin. Cela réduit les risques de failles de sécurité et allège votre système.

Contrôlez les utilisateurs et les permissions.

Appliquez le principe de moindre privilège. Ne donnez aux utilisateurs que les permissions dont ils ont absolument besoin pour effectuer leurs tâches. Utilisez la commande sudo pour accorder des privilèges administratifs de manière contrôlée plutôt que de donner un accès root complet.

En suivant ces règles simples, vous améliorerez significativement la posture de sécurité de votre système Linux, le rendant plus résistant face aux menaces courantes.

### 3 - Maîtriser les commandes de base de UFW pour filtrer le trafic réseau.

Maîtriser UFW : Un Guide Essentiel pour Sécuriser votre Réseau.

UFW (Uncomplicated Firewall) est un outil de gestion de pare-feu en ligne de commande pour Linux, conçu pour être simple et intuitif. Il offre une interface conviviale pour la configuration des règles de filtrage de paquets d'iptables. Ce guide vous présente les commandes de base pour sécuriser efficacement votre serveur.

Vérification et Activation du Pare-feu.

Avant toute configuration, il est important de vérifier l'état actuel de UFW.

Vérifier le statut :

---Bash
sudo ufw status
---

Si le pare-feu est inactif, la sortie indiquera Status: inactive. S'il est actif, vous verrez une liste des règles en place. Pour une vue plus détaillée, ajoutez 

l'argument verbose.

Activer UFW :

---Bash
sudo ufw enable
---

⚠️ Attention : L'activation d'UFW sans règle d'autorisation préalable pour SSH (port 22) peut vous bloquer l'accès à votre serveur si vous êtes connecté à distance.

Désactiver UFW :

---Bash
sudo ufw disable
---

Gestion des Politiques par Défaut.

La première étape d'une configuration sécurisée est de définir les politiques par défaut pour le trafic entrant et sortant.

Refuser tout le trafic entrant par défaut : C'est la configuration la plus courante et la plus sûre.

---Bash
sudo ufw default deny incoming
---

Autoriser tout le trafic sortant par défaut : Permet aux applications de votre serveur de contacter l'extérieur.

---Bash
sudo ufw default allow outgoing
---

Ajouter des Règles d'Autorisation (Allow)

Une fois les politiques par défaut établies, vous pouvez ouvrir des ports spécifiques pour les services nécessaires.

Par nom de service : UFW reconnaît de nombreux services courants.

---Bash
sudo ufw allow ssh  # Port 22
---
---Bash
sudo ufw allow http # Port 80
---
---Bash
sudo ufw allow https # Port 443
---
Par numéro de port : Vous pouvez spécifier le numéro de port et éventuellement le protocole (tcp ou udp).

---Bash
sudo ufw allow 22/tcp
---
---Bash
sudo ufw allow 53/udp
---
Si vous ne spécifiez pas de protocole, la règle s'appliquera aux deux (TCP et UDP).

Pour une plage de ports :

---Bash
sudo ufw allow 6000:6007/tcp
---
Pour une adresse IP spécifique : Autorisez une adresse IP à se connecter à un port donné.

---Bash
sudo ufw allow from 192.168.1.100 to any port 22
---

### 4 - Être capable de surveiller, modifier et tester la configuration du pare-feu.

Gérez votre pare-feu Linux sans effort avec UFW (Uncomplicated Firewall). Cet outil simplifie la protection de votre serveur en vous permettant de surveiller, modifier et tester facilement sa configuration.

Surveiller l'état du pare-feu
Pour commencer, il est essentiel de vérifier l'état actuel de votre pare-feu. La commande de base pour cela est :

---Bash
sudo ufw status
---
Si le pare-feu est actif, vous verrez une liste des règles en place. S'il est inactif, la sortie l'indiquera. Pour obtenir un aperçu plus détaillé, y compris l'état de la journalisation et les politiques par défaut, utilisez la commande verbose :

---Bash
sudo ufw status verbose
---
Pour une vue numérotée des règles, ce qui est pratique pour la modification, tapez :

---Bash
sudo ufw status numbered
---
Modifier la configuration du pare-feu.

La modification des règles du pare-feu est une tâche courante pour les administrateurs système. Voici comment gérer les règles de base.

Activer et désactiver le pare-feu
Pour activer le pare-feu et faire en sorte que ses règles soient appliquées au démarrage du système, utilisez :

---Bash
sudo ufw enable
---
Pour le désactiver, la commande est :

---Bash
sudo ufw disable
---
Gérer les règles.

Autoriser une connexion est simple. Par exemple, pour autoriser le trafic entrant sur le port 22 (SSH), vous pouvez utiliser :

---Bash
sudo ufw allow 22
---
Vous pouvez également spécifier le protocole :

---Bash
sudo ufw allow 22/tcp
---
Pour refuser une connexion, la syntaxe est similaire :

---Bash
sudo ufw deny 80/tcp
---
Pour supprimer une règle existante, vous pouvez utiliser son numéro (obtenu avec sudo ufw status numbered) :

---Bash
sudo ufw delete 1
---
Politiques par défaut.

Il est recommandé de définir des politiques par défaut pour le trafic entrant et sortant. Une configuration sécurisée courante consiste à refuser tout le trafic entrant et à autoriser tout le trafic sortant :

---Bash
sudo ufw default deny incoming
---
---Bash
sudo ufw default allow outgoing
---
Tester la configuration du pare-feu.

Après avoir configuré vos règles, il est crucial de les tester pour vous assurer qu'elles fonctionnent comme prévu.

Un moyen simple de tester une règle est d'essayer d'établir une connexion au port que vous avez configuré. Par exemple, si vous avez bloqué le port 80, vous pouvez essayer d'accéder à un service web hébergé sur votre serveur depuis une autre machine. La tentative de connexion devrait échouer.

Vous pouvez également utiliser des outils comme nmap depuis une machine externe pour scanner les ports de votre serveur. Si vous avez bloqué un port, nmap devrait l'indiquer comme "filtered".

Par exemple, pour scanner les ports TCP de votre serveur (en remplaçant votre_adresse_ip par l'adresse IP de votre serveur) :

---Bash
nmap -p- votre_adresse_ip
---
Enfin, la consultation des journaux du pare-feu peut vous donner des informations précieuses sur le trafic bloqué et autorisé. Pour activer la journalisation :

---Bash
sudo ufw logging on
---
Vous pouvez ensuite consulter les journaux dans le fichier /var/log/ufw.log.

---

## 📘 Extrait du Guide — Commandes essentielles

### 🔹 01 — Installation de UFW <a name="balise-01"></a>
```bash
sudo apt install ufw
```

### 🔹 02 — Politiques par défaut <a name="balise-02"></a>
```bash
sudo ufw default deny incoming
sudo ufw default allow outgoing
```

### 🔹 03 — Autoriser SSH <a name="balise-03"></a>
```bash
sudo ufw allow ssh
# ou
sudo ufw allow 22
```

### 🔹 04 — Activer UFW <a name="balise-04"></a>
```bash
sudo ufw enable
```

### 🔹 05 — Autoriser des ports précis <a name="balise-05"></a>
```bash
sudo ufw allow http
sudo ufw allow 443
sudo ufw allow 6000:6007/tcp
```

### 🔹 06 — Refuser une IP <a name="balise-06"></a>
```bash
sudo ufw deny from 203.0.113.4
```

### 🔹 07 — Supprimer une règle <a name="balise-07"></a>
```bash
sudo ufw delete 2
# ou
sudo ufw delete allow http
```

### 🔹 08 — Vérifier les règles <a name="balise-08"></a>
```bash
sudo ufw status verbose
```

### 🔹 09 — Exemple avec Zabbix + Docker <a name="balise-09"></a>
```bash
ufw limit in on enp86s0 from 192.168.50.118 to 192.168.50.250 port 2277 proto tcp comment 'SSH sécurisé'
ufw allow in on enp86s0 from 192.168.50.118 to 192.168.50.250 port 80 proto tcp comment 'HTTP'
```

### 🔹 10 — Réinitialisation d’UFW <a name="balise-10"></a>
```bash
sudo ufw disable
sudo ufw reset
```

---

<div align="center">
  <strong>🔒 Un guide par <a href="https://github.com/0xCyberLiTech">0xCyberLiTech</a> • Pour une cybersécurité accessible à tous.</strong>
</div>
