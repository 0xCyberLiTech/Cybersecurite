# Tarpit

Principe d'utilisation des tarpits.

Les tarpits servent à ralentir les connexions des personnes qui se branchent dessus.

Le but étant de garder la connexion active le plus longtemps possible du côté de l'attaquant.

Dans un monde où les tarpits seraient généralisés, un attaquant devrait alors ruser et ne pourrait plus s'attaquer à une IP au hasard pour faire propager des vers par exemple (la problèmatique de générer une IP à attaquer aléatoirement devrait disparaître avec l'IP v6, en effet, l'espace d'adresse sera moins saturé donc il y aura beaucoup moins de chance que l'adresse soit une adresse utilisée).

Quand Tom Liston présente pour la première fois la notion de tarpits, il explique qu'il cherchait une parade au vers CodeRed.

Il constata qu'en général quand on se voit attribuer un bloc d'adresses publiques, il est rare de tout utiliser.

Donc il pensa que tout trafic vers ses IP publiques non attribuées ne pouvait être qu'un trafic illicite. Il commença alors à écrire un petit service qui écoutait sur le port 80 de ces machines (le port où CodeRed attaquait) et qui répondait au SYN par un SYN/ACK avec une valeur de MSS très petite, ce qui avait pour effet de ralentir le vers (il ne pouvait plus envoyer que des paquets de petite taille, de plus, le service n'écoutait plus la session ensuite).

Finalement, le principe de tarpit pouvait être généralisé à n'importe quel port TCP.

Il est conseillé de l'utiliser que sur des ports où l'on est sûr d'avoir aucun trafic "légal".

Par exemple, le port 113, où identd est lié, est utilisé par certains serveurs IRC pour connaître le login de l'utilisateur.

Si on "tarpitte" ce port, le serveur n'aura jamais sa réponse et l'utilisateur n'obtiendra jamais sa connexion.

Au final, il faudra donc peser le pour et le contre de cette technique.

Sur une IP qui n'est pas attribuée, on pourra "tarpiter" tous les ports sans problème, mais sur une IP attribuée, il faudra bien faire attention à ne pas être trop agressif dans les règles au risque de réduire connectivité du réseau.

Vous pouvez tarpit la requête HTTP d’un client, ce qui bloque la demande pendant un certain temps avant de renvoyer une réponse d’erreur.

Ceci est souvent utilisé pour dissuader une armée de bots malveillants, car il bloque les bots afin qu’ils ne puissent pas immédiatement réessayer leurs demandes.

Dans l’exemple ci-dessous, nous utilisons pour tarpit le client s’il dépasse une limite de débit.

Permet de définir la durée d’attente de HAProxy Enterprise avant de renvoyer une réponse d’erreur :http-request tarpittimeout tarpit.

Introduction :

Lorsque vous consultez les journaux d’authentification, vous pouvez voir plusieurs tentatives de connexion infructueuses à partir de différentes adresses IP.

Ces tentatives de connexion infructueuses proviennent souvent d’un nœud sur un botnet qui analyse l’ensemble du Web à la recherche de serveurs vulnérables avec des informations d’identification par défaut.

Alors que la plupart des gens auront un mot de passe sécurisé ou des clés SSH empêchant les attaquants de se connecter à leur serveur, certains serveurs seront vulnérables à cette analyse.

Bien que vous ne puissiez peut-être pas arrêter ces attaques, vous pouvez les ralentir avec des tarpits.

Dans ce tutoriel, vous allez installer et configurer Endlessh, une tarpit qui envoie lentement une bannière infiniment longue à tout utilisateur tentant de se connecter.

Vous allez également configurer le service SSH pour qu’il s’exécute sur un port différent, ce qui rendra vos journaux d’authentification plus lisibles.

Après avoir terminé ce tutoriel, vous pourrez vous connecter à votre serveur sur un port non standard, tandis que tous les robots analysant votre serveur trouveront leur temps perdu en frappant à une porte qui ne s’ouvrira jamais.

Conditions préalables :

Pour suivre ce didacticiel, vous aurez besoin des éléments suivants :

- Un serveur Debian avec un utilisateur sudo non-root, un pare-feu et au moins 1 Go de RAM.

- Git installé sur votre serveur, que vous pouvez compléter avec le didacticiel d’installation Git.

Étape 1 – Déplacement de SSH vers un port non standard.

Dans cette étape, vous allez déplacer SSH vers un port non standard afin de libérer un port pour Endlessh. Étant donné que les botnets ne disposent pas de ressources infinies, ils analysent généralement uniquement le port SSH par défaut ().

En déplaçant votre SSH vers un port non standard, vous pouvez piéger le bot dans la tarpit Endlessh.22

Pour commencer, effectuez une sauvegarde de votre fichier de configuration SSH à partir de votre serveur avec la commande suivante :
```
sudo cp /etc/ssh/sshd_config /etc/ssh/sshd_config.bak
```
Ce fichier peut être utilisé pour restaurer les paramètres d’origine si quelque chose ne fonctionne pas ou si vous décidez de déplacer SSH vers le port par défaut.

Ouvrez le fichier de configuration /etc/ssh/sshd_config
```
sudo nano /etc/ssh/sshd_config
```
Localisez la ligne . 

Supprimez les marques de commentaire de cette ligne en supprimant le , puis remplacez le port par un port inutilisé sur votre serveur :#Port 22#

/etc/ssh/sshd_config
```
Port 2277
```
Vous pouvez sélectionner le port que vous souhaitez utiliser pour vos connexions SSH récurrentes.

Enregistrez et fermez le fichier.2277

Si votre serveur utilise un pare-feu, tel que , vous devrez autoriser le trafic vers le nouveau port : ufw
```
sudo ufw allow 2277/tcp
```
Ensuite, redémarrez le service SSH :
```
sudo systemctl restart sshd
```
Dans une session de terminal distincte, essayez de vous connecter à votre serveur à l’aide du nouveau port :
```
ssh sammy@your_server_ip -p 2277
```
Avertissement : 

Ne fermez pas votre session SSH active à moins d’avoir confirmé que vous pouvez utiliser SSH sur le nouveau port.

Si vous ne pouvez pas vous connecter via le nouveau port, vous risquez de perdre l’accès à votre serveur en fermant la session.

Si vous ne pouvez pas vous connecter à votre serveur dans une session de terminal distincte, vous pouvez restaurer vos paramètres SSH d’origine en exécutant les commandes suivantes :
```
sudo cp /etc/ssh/sshd_config.bak /etc/ssh/sshd_config
```
```
sudo systemctl restart sshd
```
Si vous rencontrez d’autres problèmes, vérifiez que le redémarrage a réussi et vérifiez les paramètres de votre pare-feu pour vous assurer que le port accepte le trafic TCP.sshd2277

Une fois que vous avez vérifié que vous pouvez établir une nouvelle connexion au port, vous pouvez fermer votre terminal d’origine en toute sécurité.

Lors de la connexion à votre serveur à l’avenir, vous devrez toujours spécifier le nouveau port, comme suit:2277
```
ssh sammy@your_server_ip -p 2277
```
Maintenant que vous avez réussi à déplacer SSH vers un port non standard, il est temps de configurer Endlessh.

Étape 2 – Installation d’Endlessh :

Endlessh n’a pas de package officiel, vous allez donc cloner le référentiel pour le construire manuellement.

Vous utiliserez Git pour cloner le référentiel, le package (pour compiler le projet) et le package.build-essentiallibc6-dev

Installez les paquets requis à l’aide du gestionnaire de paquets apt :
```
sudo apt install build-essential libc6-dev
```
Confirmez l’installation avec lorsque vous y êtes invité.

Clonez ensuite le référentiel Endlessh de GitHub vers votre répertoire personnel :
```
git clone https://github.com/do-community/endlessh
```
Accédez au répertoire du projet et utilisez la commande pour compiler Endlessh:make
```
cd endlessh
```
```
make
```
Vous pouvez maintenant démarrer Endlessh avec la commande suivante:
```
sudo ./endlessh -v -p 22
```
Pour tester qu’Endlessh fonctionne, vous pouvez essayer d’établir une connexion SSH au port avec l’indicateur détaillé, qui affichera la bannière sans fin transmise. Dans une nouvelle fenêtre de terminal, établissez une connexion SSH au port à l’aide de l’une des commandes suivantes :22-v22
```
ssh sammy@your_server_ip -v
```
```
ssh sammy@your_server_ip -p 22 -v
```
Lorsque votre nouvelle session SSH tente de se connecter au port, vous verrez une chaîne de caractères aléatoires apparaître dans le terminal de connexion toutes les 10 secondes jusqu’à la fermeture de la session, comme la sortie ci-dessous:22
```
Output
debug1: kex_exchange_identification: banner line 0: NvnHF>]&W4p+tg*"+
debug1: kex_exchange_identification: banner line 1: n<
debug1: kex_exchange_identification: banner line 2: @/O5c0/;>1b{qd(M,vK
debug1: kex_exchange_identification: banner line 3: i+ OZ
debug1: kex_exchange_identification: banner line 4: yn
debug1: kex_exchange_identification: banner line 5: T[V\\[HUg
```
Une fois que vous avez confirmé qu’il fonctionne en essayant de vous connecter avec une nouvelle session, vous pouvez fermer le nouveau terminal et arrêter l’utilisation d’Endlessh dans votre session de terminal d’origine. Ctrl+C

Dans cette étape, vous avez téléchargé et créé Endlessh à partir de la source.

Ensuite, vous allez le configurer et le déployer en tant que service pour le rendre persistant lors de la déconnexion et du redémarrage de votre serveur.

Étape 3 – Configuration d’Endlessh :

Dans cette étape, vous allez configurer Endlessh en tant que service qui persistera après la fin de votre session et via le redémarrage du système.

Déplacez le fichier binaire compilé dans le répertoire :/usr/local/bin
```
sudo mv ./endlessh /usr/local/bin/
```
Entrez votre mot de passe si vous y êtes invité.

Copiez le fichier de service du projet dans le répertoire :/etc/systemd/system
```
sudo cp util/endlessh.service /etc/systemd/system/
```
Vous allez modifier légèrement le fichier de service pour exécuter Endlessh sur les ports sous . Ouvrez le fichier de service dans nano ou votre éditeur de texte préféré :1024
```
sudo nano /etc/systemd/system/endlessh.service
```
Trouvez la section sur l’exécution d’Endlessh sur les ports sous .1024

Mettez à jour le fichier en supprimant au début de la ligne avec et en ajoutant au début de la ligne , comme suit :
```
# AmbientCapabilities=CAP_NET_BIND_SERVICE # PrivateUsers=true
```
```
## If you want Endlessh to bind on ports < 1024
## 1) run: 
##     setcap 'cap_net_bind_service=+ep' /usr/local/bin/endlessh
## 2) uncomment following line
AmbientCapabilities=CAP_NET_BIND_SERVICE
## 3) comment following line
#PrivateUsers=true
```
Enregistrez et quittez le fichier.

Ensuite, vous autoriserez Endlessh à s’exécuter sur des ports inférieurs à , également appelés ports privilégiés de domaine Internet.

Définissez cette fonctionnalité pour le binaire Endlessh avec la commande :1024setcap
```
sudo setcap 'cap_net_bind_service=+ep' /usr/local/bin/endlessh
```
Vous devrez définir un fichier de configuration pour Endlessh afin de lui indiquer quel port utiliser. Créez et ouvrez un fichier de configuration nommé :/etc/endlessh/config
```
sudo mkdir /etc/endlessh
```
```
sudo nano /etc/endlessh/config
```
Dans le fichier de configuration, définissez le port à utiliser comme :22
```
/etc/endlessh/config
Port 22
```
Enregistrez et fermez le fichier.

Vous pouvez maintenant démarrer le service Endlessh de manière persistante :
```
sudo systemctl --now enable endlessh
```
L’inclusion fera persister le service après le redémarrage de votre serveur.--now enable

Pour vérifier que le service a démarré correctement, vous pouvez utiliser la commande :systemctl status
```
sudo systemctl status endlessh
```
Si le démarrage réussit, vous verrez une sortie comme celle-ci :

S’il est en cours d’exécution, vous pouvez tenter de vous connecter sur le port dans une nouvelle session de terminal :22
```
ssh sammy@your_server_ip
```
Étant donné que votre tarpit est en cours d’exécution, la nouvelle session de terminal ne pourra pas se connecter et s’exécutera à perpétuité jusqu’à ce qu’elle soit arrêtée manuellement avec le terminal de connexion. Ctrl+C

Si vous souhaitez arrêter l’exécution du service, vous pouvez utiliser la commande suivante :
```
sudo systemctl --now disable endlessh
```
Après avoir arrêté le service, vous pouvez utiliser les instructions de restauration SSH de l’avertissement de l’étape 1 pour restaurer la configuration de votre serveur d’origine. Vous pouvez réactiver le service sans repasser par le processus d’installation, mais assurez-vous que SSH ne s’exécute pas sur le port lorsque vous le faites.sudo systemctl --now enable endlessh22

Conclusion :

Vous avez installé et configuré Endlessh avec succès, aidé à effacer vos journaux d’authentification et préparé à perdre du temps avec des robots SSH aléatoires.

Après avoir configuré votre tarpit Endlessh, passez en revue les autres mesures de sécurité recommandées pour protéger vos serveurs.

