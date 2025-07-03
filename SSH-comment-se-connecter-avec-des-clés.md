![Debian_logo-01](./images/Cloud-et-securite.png)

## CYBERSÉCURITÉ / SSH comment se connecter avec des clés ?

👋 Sommaire des sujets abordés :

- 01 - [SSH comment se connecter avec des clés ?](#balise-01)
- 02 - [Comment fonctionne l’authentification par clé ?](#balise-02)
- 03 - [Comment créer des clés SSH ?](#balise-03)
- 04 - [Comment transférer votre clé publique vers le serveur ?](#balise-04)

<a name="balise-01"></a>
- 01 Comment se connecter à SSH avec des clés ?

S’il est utile de pouvoir se connecter à un système à distance à l’aide de mots de passe, il est bien plus judicieux de mettre en place une authentification par clé.

<a name="balise-02"></a>
- 02 Comment fonctionne l’authentification par clé ?

L’authentification par clé fonctionne en créant une paire de clés : une clé privée et une clé publique.

La clé privée se trouve sur la machine du client et est sécurisée et gardée secrète.

La clé publique peut être donnée à n’importe qui ou placée sur n’importe quel serveur auquel vous souhaitez accéder.

Lorsque vous tentez de vous connecter à l’aide d’une paire de clés, le serveur utilise la clé publique pour créer un message pour l’ordinateur client qui ne peut être lu qu’avec la clé privée.

L’ordinateur client renvoie alors la réponse appropriée au serveur et celui-ci saura que le client est légitime.

Tout ce processus se fait automatiquement après l’installation des clés.

<a name="balise-03"></a>
- 03 Comment créer des clés SSH ?

**Les clés SSH doivent être générées sur l’ordinateur duquel vous souhaitez vous connecter.** 

Il s’agit généralement de votre machine locale.

Entrez ce qui suit dans la ligne de commande :
```
ssh-keygen -t rsa
```
Appuyez sur la touche Entrée pour accepter les valeurs par défaut.

Vos clés seront créées à l’adresse ~/.ssh/id_rsa.pub et ~/.ssh/id_rsa.
```
ls -l ~/.ssh/*
```
Regardez les autorisations des fichiers :
```
-rw------- 1 root root 2590 28 juil. 18:53 /root/.ssh/id_rsa
-rw-r--r-- 1 root root  564 28 juil. 18:53 /root/.ssh/id_rsa.pub
```
```
cd ~/.ssh/
```
Comme vous pouvez le voir, le fichier id_rsa est lisible et accessible en écriture uniquement au propriétaire.

C’est pour cela qu’il doit être gardé secret.

Le fichier id_rsa.pub, cependant, peut être partagé et dispose de permissions appropriées pour cette activité.

<a name="balise-04"></a>
- 04 Comment transférer votre clé publique vers le serveur.

Si vous avez actuellement un accès par mot de passe à un serveur, vous pouvez y copier votre clé publique en émettant cette commande :
```
ssh-copy-id -p 2234 root@192.168.50.205
```
Cela permettra de démarrer une session SSH.

Après que vous ayez entré votre mot de passe, il copiera votre clé publique dans le fichier des clés autorisées du serveur 192.168.50.205, ce qui vous permettra de vous connecter sans mot de passe la prochaine fois à celui-ci.

On peut constater que sur le serveur 192.168.50.205 la clé a été déposer dans ~/.ssh/authorized_keys

Effectuons un test de connexion depuis la machine hôte root@0xCLT (192.168.50.250) vers le serveur srv-linux-05 (192.168.50.205).
```
root@0xCLT:~/.ssh# ssh -p 2234 root@192.168.50.205
```
```
root@0xCLT:~/.ssh# ssh -p 2234 root@192.168.50.205
Linux srv-linux-05 6.1.0-10-amd64 #1 SMP PREEMPT_DYNAMIC Debian 6.1.37-1 (2023-07-03) x86_64

The programs included with the Debian GNU/Linux system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Debian GNU/Linux comes with ABSOLUTELY NO WARRANTY, to the extent
permitted by applicable law.
Last login: Fri Jul 28 19:27:21 2023 from 192.168.50.250
root@srv-linux-05:~#
```
Options côté client :

Il existe un certain nombre d’indicateurs optionnels que vous pouvez sélectionner lorsque vous vous connectez via SSH.

Certains d’entre eux peuvent être nécessaires pour correspondre aux paramètres de la configuration sshd de l’hôte distant.

Par exemple, si vous avez changé le numéro de port dans votre sshd, vous devrez faire correspondre ce port côté client en tapant :
```
ssh -p port_number remote_host
```
Si vous ne souhaitez exécuter qu’une seule commande sur un système distant, vous pouvez la spécifier après l’hôte comme cela :
```
ssh remote_host command_to_run
```
Vous vous connecterez à la machine distante, vous vous authentifierez, et la commande sera exécutée.

Comme nous l’avons déjà dit, si la transmission X11 est activée sur les deux ordinateurs, vous pouvez accéder à cette fonctionnalité en tapant :
```
ssh -X remote_host
```
Si vous disposez des outils appropriés sur votre ordinateur, les programmes de l’environnement graphique que vous utilisez sur le système distant ouvriront désormais leur fenêtre sur votre système local.

Désactiver l’authentification par mot de passe :

Si vous avez créé des clés SSH, vous pouvez renforcer la sécurité de votre serveur en désactivant l’authentification uniquement par mot de passe. En dehors de la console, la seule façon de se connecter à votre serveur est d’utiliser la clé privée qui se couple avec la clé publique que vous avez installée sur le serveur.

Avertissement : Avant de procéder à cette étape, assurez-vous que vous avez installé une clé publique pour votre serveur.

Sinon, vous serez bloqué à l’extérieur !

En tant que root ou utilisateur avec des privilèges sudo, ouvrez le fichier de configuration sshd :
```
sudo nano /etc/ssh/sshd_config
```
Localisez la ligne qui indique Password Authenticationet la décommenter en supprimant le premier #. Vous pouvez alors changer sa valeur à no :
```
/etc/ssh/sshd_config
```
```
# To disable tunneled clear text passwords, change to no here!
PasswordAuthentication no
#PermitEmptyPasswords no
```
Deux autres paramètres qui ne devraient pas avoir à être modifiés (à condition que vous n’ayez pas modifié ce fichier auparavant) sont PubkeyAuthentification et ChallengeResponseAuthentification.

Elles sont définies par défaut et doivent se lire comme suit :
```
nano /etc/ssh/sshd_config
```
```
PubkeyAuthentication yes
ChallengeResponseAuthentication no
```
```
# Authentication:

LoginGraceTime 1m
#PermitRootLogin prohibit-password
#PermitRootLogin yes
#StrictModes yes
MaxAuthTries 4
MaxSessions 2

PubkeyAuthentication yes
ChallengeResponseAuthentication no
```
Après avoir effectué vos modifications, enregistrez et fermez le fichier.

Vous pouvez maintenant recharger le démon SSH :
```
sudo systemctl restart ssh.service
```
L’authentification par mot de passe devrait maintenant être désactivée, et votre serveur ne devrait être accessible que via l’authentification par clé SSH.

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
