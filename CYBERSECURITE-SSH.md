<div align="center">

<a href="https://github.com/0xCyberLiTech">
  <img src="https://readme-typing-svg.herokuapp.com?font=Fira+Code&size=32&pause=1000&color=33FF33&center=true&vCenter=true&width=650&lines=DURCISSEMENT+DU+SERVICE+SSH;Authentifier+•+Chiffrer+•+Isoler;Clés+SSH+•+Fail2Ban+•+sshd_config" alt="Typing SVG" />
</a>

<p align="center">
  <em>Un dépôt pédagogique SSH.</em><br>
  <b>📊 Monitoring – 📈 Performance – ⚙️ Fiabilité</b>
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

### 🧭 **Sommaire :**

| Chapitre | Description | Accès Rapide |
|:---:|:---|:---:|
| **01** | 🌐 Introduction au protocole SSH et son importance. | [<img src="https://img.shields.io/badge/EXPLORER-brightgreen?style=for-the-badge&logo=github&logoColor=white">](#balise_01) |
| **02** | 🔑 Mettre en place l'authentification par clé SSH. | [<img src="https://img.shields.io/badge/EXPLORER-brightgreen?style=for-the-badge&logo=github&logoColor=white">](#balise_02) |
| **03** | ⚙️ Durcissement du serveur OpenSSH via `sshd_config`. | [<img src="https://img.shields.io/badge/EXPLORER-brightgreen?style=for-the-badge&logo=github&logoColor=white">](#balise_03) |
| **04** | 🛡️ Se protéger des attaques Brute Force avec Fail2Ban. | [<img src="https://img.shields.io/badge/EXPLORER-brightgreen?style=for-the-badge&logo=github&logoColor=white">](#balise_04) |
| **05** | 🚇 Comprendre et utiliser les Tunnels SSH. | [<img src="https://img.shields.io/badge/EXPLORER-brightgreen?style=for-the-badge&logo=github&logoColor=white">](#balise_05) |
| **06** | ✨ Bonnes pratiques : Agent SSH et mots de passe de clé. | [<img src="https://img.shields.io/badge/EXPLORER-brightgreen?style=for-the-badge&logo=github&logoColor=white">](#balise_06) |
| **07** | 📚 Annexes et commandes utiles. | [<img src="https://img.shields.io/badge/EXPLORER-brightgreen?style=for-the-badge&logo=github&logoColor=white">](#balise_07) |

<a name="balise_01"></a>
---

### 🌐 1. Introduction au protocole SSH et son importance.

#### Qu'est-ce que SSH ?
SSH, ou **Secure Shell**, est un protocole réseau qui permet de se connecter et d'administrer une machine à distance de manière **totalement sécurisée**. Imaginez que vous donniez des ordres à un ordinateur situé à des milliers de kilomètres, comme si vous étiez assis devant.

#### Pourquoi est-ce si important ?
Avant SSH, des protocoles comme Telnet étaient utilisés, mais ils transmettaient tout en clair sur le réseau, y compris vos mots de passe ! 😱 SSH a révolutionné l'administration à distance en apportant deux garanties fondamentales :

1.  🛡️ **Chiffrement (Confidentialité)** : Toutes les données échangées (commandes, mots de passe, fichiers) sont cryptées. Personne ne peut les intercepter et les comprendre.
2.  🆔 **Authentification (Identité)** : SSH vérifie que vous vous connectez bien au bon serveur (évitant les arnaques de type "man-in-the-middle") et que vous êtes bien la personne que vous prétendez être.

Sur Debian, le service SSH est fourni par le paquet **OpenSSH**, la référence en la matière.

<a name="balise_02"></a>
---

### 🔑 2. Mettre en place l'authentification par clé SSH.

L'authentification par mot de passe est simple, mais fragile (mots de passe faibles, volés, etc.). L'authentification par clé est **infiniment plus robuste**.

**Le principe** : Vous générez une paire de clés :
* 🤫 **Clé privée** : Elle reste secrète, sur votre ordinateur personnel. C'est votre "moi" numérique.
* 🚪 **Clé publique** : Vous la copiez sur les serveurs auxquels vous voulez accéder. C'est le "cadenas" que seule votre clé privée peut ouvrir.

#### Étapes sur votre machine cliente (votre PC).

1.  **Générez votre paire de clés**.
    Ouvrez un terminal et tapez la commande suivante. `ed25519` est un algorithme moderne, rapide et très sécurisé.
    ```bash
    ssh-keygen -t ed25519 -C "votre_email@exemple.com"
    ```
    * Laissez le chemin par défaut (`~/.ssh/id_ed25519`).
    * 💡 **IMPORTANT** : Saisissez une **phrase de passe (passphrase)** robuste. C'est une sécurité supplémentaire pour protéger votre clé privée si elle était volée.

2.  **Copiez votre clé publique sur le serveur Debian**.
    Cette commande magique s'occupe de tout : elle se connecte au serveur, crée les bons dossiers et fichiers, et y ajoute votre clé publique avec les bonnes permissions.
    ```bash
    ssh-copy-id utilisateur@adresse_du_serveur
    ```
    On vous demandera le mot de passe de `utilisateur` une dernière fois.

3.  **Testez la connexion**.
    ```bash
    ssh utilisateur@adresse_du_serveur
    ```
    Le serveur devrait maintenant vous demander la **phrase de passe de votre clé**, et non plus le mot de passe de votre compte. Si c'est le cas, bravo ! 🎉

<a name="balise_03"></a>
---

### ⚙️ 3. Durcissement du serveur OpenSSH via `sshd_config`.

Maintenant que l'authentification par clé fonctionne, nous allons renforcer la sécurité de notre serveur SSH en désactivant les options les moins sûres.

Toutes les actions suivantes se font **sur le serveur Debian**.

1.  **Faites une sauvegarde du fichier de configuration** (au cas où).
    ```bash
    sudo cp /etc/ssh/sshd_config /etc/ssh/sshd_config.bak
    ```

2.  **Modifiez le fichier de configuration** avec un éditeur de texte comme `nano`.
    ```bash
    sudo nano /etc/ssh/sshd_config
    ```

3.  **Appliquez les modifications suivantes**. Cherchez ces lignes, décommentez-les si besoin (enlevez le `#` au début) et changez leur valeur.

    * 🚫 **Interdire la connexion de l'utilisateur `root`** : C'est la règle de sécurité N°1. On se connecte toujours avec un utilisateur standard, puis on utilise `sudo` si besoin.
        ```ini
        PermitRootLogin no
        ```
    * 🚫 **Désactiver l'authentification par mot de passe** : Maintenant que les clés sont en place, les mots de passe sont inutiles et constituent une porte d'entrée pour les attaquants.
        ```ini
        PasswordAuthentication no
        ```
    * 🚫 **Désactiver les authentifications "vides" et "interactives"**.
        ```ini
        PermitEmptyPasswords no
        ChallengeResponseAuthentication no
        ```

4.  **Vérifiez la syntaxe et redémarrez le service**.
    Cette première commande vérifie qu'il n'y a pas d'erreur dans votre fichier. Si elle ne renvoie rien, tout est bon.
    ```bash
    sudo sshd -t
    ```
    Appliquez ensuite les changements.
    ```bash
    sudo systemctl restart sshd
    ```

Votre serveur SSH est maintenant beaucoup plus robuste. 💪

<a name="balise_04"></a>
---

### 🛡️ 4. Se protéger des attaques Brute Force avec Fail2Ban

Même avec l'authentification par mot de passe désactivée, des robots vont continuer à essayer de se connecter en boucle, remplissant vos fichiers de logs. **Fail2Ban** est un service qui surveille ces logs et bannit automatiquement les adresses IP des attaquants.

1.  **Installez Fail2Ban** sur le serveur.
    ```bash
    sudo apt update
    sudo apt install fail2ban
    ```

2.  **Créez un fichier de configuration local**. La bonne pratique est de ne jamais modifier `jail.conf`, mais de créer un fichier `jail.local` qui le surcharge.
    ```bash
    sudo cp /etc/fail2ban/jail.conf /etc/fail2ban/jail.local
    ```

3.  **Activez la protection pour SSH**. Modifiez le fichier `jail.local`.
    ```bash
    sudo nano /etc/fail2ban/jail.local
    ```
    Cherchez la section `[sshd]`. Elle est souvent déjà présente. Assurez-vous qu'elle contient `enabled = true`.
    ```ini
    [sshd]
    enabled = true
    # Vous pouvez ajuster ces valeurs :
    # maxretry = 5      # Nombre d'essais avant bannissement
    # bantime = 10m     # Durée du bannissement (10 minutes)
    ```

4.  **Redémarrez Fail2Ban** et vérifiez son statut.
    ```bash
    sudo systemctl restart fail2ban
    sudo fail2ban-client status sshd
    ```
    Fail2Ban surveille désormais votre serveur. Vous pouvez dormir sur vos deux oreilles. 😴

<a name="balise_05"></a>
---

### 🚇 5. Comprendre et utiliser les Tunnels SSH.

Un tunnel SSH est une fonctionnalité puissante qui permet de faire passer le trafic d'une autre application à travers votre connexion SSH chiffrée. C'est un véritable couteau suisse !

#### Tunnel Local (`-L`) : 🏠➡️💻 Accéder à un service distant comme s'il était local

* **Cas d'usage** : Une base de données tourne sur votre serveur, mais pour des raisons de sécurité, elle n'est pas accessible depuis Internet. Vous voulez y accéder depuis votre PC avec votre outil graphique préféré.
* **Commande (sur votre PC)** :
    ```bash
    ssh -L 8080:127.0.0.1:5432 utilisateur@adresse_du_serveur
    ```
* **Explication** : Cette commande dit "Tout ce qui arrive sur le port `8080` de **ma machine locale** doit être redirigé, via le tunnel SSH, vers le port `5432` de la machine distante (`127.0.0.1` du point de vue du serveur)". Vous pouvez maintenant connecter votre outil de base de données à `localhost:8080`.

#### Tunnel Distant (`-R`) : 💻➡️🌍 Exposer un service local au monde extérieur

* **Cas d'usage** : Vous développez un site web sur votre PC (`localhost:3000`) et vous voulez le montrer à un client sans avoir à le déployer.
* **Commande (sur votre PC)** :
    ```bash
    ssh -R 9090:127.0.0.1:3000 utilisateur@adresse_du_serveur
    ```
* **Explication** : "Tout ce qui arrive sur le port `9090` du **serveur distant** doit être redirigé vers le port `3000` de **ma machine locale**". Le client peut maintenant voir votre site en visitant `http://adresse_du_serveur:9090`.

<a name="balise_06"></a>
---

### ✨ 6. Bonnes pratiques : Agent SSH et mots de passe de clé.

Se souvenir de la phrase de passe de sa clé, c'est bien. La taper à chaque connexion, c'est fastidieux. L'**Agent SSH** est un petit programme qui garde votre clé déverrouillée en mémoire de manière sécurisée pendant la durée de votre session.

1.  **Démarrer l'agent** (souvent fait automatiquement par les systèmes de bureau modernes).
    ```bash
    eval $(ssh-agent -s)
    ```

2.  **Ajouter votre clé à l'agent**.
    ```bash
    ssh-add ~/.ssh/id_ed25519
    ```
    On vous demandera votre phrase de passe **une seule fois**.

Désormais, toutes vos connexions `ssh`, `scp`, `sftp` utiliseront la clé stockée par l'agent, sans vous redemander la phrase de passe.

<a name="balise_07"></a>
---

### 📚 7. Annexes et commandes utiles.

* ➡️ `ssh utilisateur@serveur` : Se connecter au serveur.
* ➡️ `ssh -p 2222 utilisateur@serveur` : Se connecter sur un port non standard.
* 📤 `scp /chemin/local/fichier utilisateur@serveur:/chemin/distant/` : Copier un fichier **vers** le serveur.
* 📥 `scp utilisateur@serveur:/chemin/distant/fichier /chemin/local/` : Copier un fichier **depuis** le serveur.
* 🔄 `sftp utilisateur@serveur` : Ouvrir une session de transfert de fichiers interactive (très pratique, commandes `get`, `put`, `ls`, `cd`).
* 🔑 `ssh-keygen -t rsa -b 4096` : Alternative pour générer une clé de type RSA (plus ancienne mais toujours très utilisée).

---

<p align="center">
  <b>🔒 Un guide proposé par <a href="https://github.com/0xCyberLiTech">0xCyberLiTech</a> • Pour des tutoriels accessibles à tous. 🔒</b>
</p>
