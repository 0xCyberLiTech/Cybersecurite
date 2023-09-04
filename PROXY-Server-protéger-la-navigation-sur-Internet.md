![Debian_logo-01](./images/Cloud-et-securite.png)
[PROXY REVERSE - Installation.](https://github.com/0xCyberLiTech/Cybersecurite/blob/main/POXY-REVERSE-Installtion.md)

## CYBERSÉCURITÉ / PROXY Server protéger la navigation sur Internet.

# Comment installer un serveur proxy HTTPS.

La confidentialité est un sujet d’actualité permanent sur Internet.

De nombreux internautes ne savent pas comment protéger leurs informations.

Toutefois, les professionnels du Web avertis peuvent implémenter un serveur proxy HTTPS à cette fin.

Un serveur proxy HTTPS vous permet de préserver votre confidentialité tout en permettant la navigation sur Internet sans restriction.

Qu’est-ce qu’un serveur proxy ? 

- Nous parlerons ensuite de ce dont vous aurez besoin pour en créer un, avant de vous montrer comment configurer votre propre serveur proxy.

# C’est parti !

Qu’est-ce qu’un serveur proxy (et pourquoi vous en avez besoin) :

En termes simples, un serveur proxy agit comme un « intermédiaire » entre votre navigateur et le site Web que vous visitez.

Cela peut sembler complexe, mais vous n’avez pas besoin d’en savoir trop sur son fonctionnement pour effectuer les tâches quotidiennes. 

Vous devez savoir que, comme pour tout autre site Web, les données transmises par un serveur proxy peuvent également être chiffrés par HTTPS.

Il existe des avantages certains à utiliser HTTPS via un proxy, à commencer par la confidentialité et la navigation anonyme qu’il offre.

Cependant, un serveur proxy HTTPS peut vous aider avec beaucoup plus de choses, y compris les fonctions de sécurité et de blocage des publicités, les tests de géolocalisation et même la mise en cache.

Plutôt que de le voir simplement comme un moyen de masquer votre identité en ligne, vous pouvez voir votre serveur proxy HTTPS comme un outil de développement précieux.

Les éléments essentiels dont vous aurez besoin pour configurer un serveur proxy HTTPS :

- Le premier élément dont vous aurez besoin est un hébergeur approprié présentant les caractéristiques suivantes :

- (Heureusement, les plans d’hébergement Pro, VPS et serveur dédié de GoDaddy répondent à ces exigences.)

Ensuite, vous aurez besoin d’un moyen de chiffrer les données qui transitent par votre proxy.

Tout comme avec un site Web standard, vous devrez utiliser un certificat SSL approprié. Il existe de nombreuses options et fournisseurs disponibles, et vous pouvez trouver une pléthore de certificats différents à des prix compétitifs.

Enfin, vous aurez besoin d’un script proxy approprié.

Ils sont généralement codés avec PHP et une recherche rapide sur Google vous permettra de découvrir une multitude de choix.

Cependant, méfiez-vous : des scripts gratuits sont parfois publiés par des développeurs ayant d’autres motivations.

Vous devez donc examiner attentivement vos options.

Néanmoins, Glype et Squid sont des scripts de proxy gratuits appropriés et ce dernier est également une excellente solution de mise en cache de proxy.

Cinq étapes pour configurer un serveur proxy HTTPS :

Une fois rassemblé tout ce dont vous avez besoin pour créer votre serveur proxy HTTPS (et vous êtes assuré que votre serveur est correctement préparé), la dernière étape consiste à effectuer la configuration proprement dite. Heureusement, ce processus doit être simple pour la plupart des professionnels du Web.

1. Configurer un sous-domaine avec SSL
Configurez un sous-domaine et assurez-vous que votre certificat SSL est opérationnel pour cette URL particulière.

2. Télécharger votre script de proxy
Téléchargez le script de proxy de votre choix et décompressez le fichier compressé si nécessaire.

3. Importer les fichiers dans le dossier du sous-domaine
Téléchargez les fichiers via FTP (File Transfer Protocol) dans le dossier du sous-domaine. Si vous n’avez pas de gestionnaire FTP préféré, nous vous recommandons FileZilla.

4. Ajuster les paramètres d’administration du sous-domaine
Accédez à l’écran d’administration du sous-domaine proxy (généralement en ajoutant votre URL avec admin.php) et ajustez les paramètres en fonction de vos besoins et du script de proxy choisi.

5. Vérifier les signaux de sécurité
Enfin, vérifiez que vous pouvez voir les indicateurs d’un site Web sécurisé : le cadenas vert et la désignation https:// dans la barre du navigateur.

Et c’est tout ! Si tout va bien, vous devriez avoir un serveur proxy HTTPS fonctionnel et sécurisé en 15 minutes environ !

Conclusion :

Bien que la confidentialité en ligne ne cesse d’être un problème pressant, il n’existe pas de moyen simple et rapide de protéger votre navigation en ligne sans restreindre vos options. Cependant, pour les professionnels du Web expérimentés, la connexion à HTTPS via un proxy est probablement votre meilleur choix.
