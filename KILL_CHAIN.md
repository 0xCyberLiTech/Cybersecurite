<a name="balise_01"></a>
# La kill chain c'est quoi ?

Le principe de kill chain (chaîne de frappe) désigne dans le domaine de la sécurité des systèmes d'information une méthode de modélisation des procédés d'intrusion sur un réseau informatique1.

## La kill chain traditionnelle.

Des informaticiens de la société Lockheed Martin ont décrit en 2011 un nouveau cadre ou modèle de «kill chain d'intrusion» pour défendre les réseaux informatiques en 20112. Selon ce modèle, les attaques peuvent être découpées en phases et peuvent être perturbées grâce à des contrôles établis à chaque étape. Depuis, le modèle de «cyber kill chain» a été adopté par les organisations de sécurité des données pour définir les phases des cyberattaques3.

La «kill chain d'intrusion» décrit les phases d'une cyberattaque, de la reconnaissance à l'exfiltration de données4. Celle-ci peut également être utilisée comme outil de gestion, afin d'améliorer en permanence la défense du réseau. Selon Lockheed Martin, les menaces doivent passer par plusieurs phases du modèle, parmi lesquelles :

- 1) Reconnaissance : l'attaquant sélectionne la cible, la recherche et tente d'identifier les vulnérabilités du réseau cible.
- 2) Armement : l'attaquant crée un logiciel malveillant, comme un virus ou un ver, lui permettant d'accéder à distance à la cible et exploitant une ou plusieurs vulnérabilités du système.
- 3) Livraison: l'attaquant transmet l'arme à la cible (via des pièces jointes de courrier électronique, des sites Web ou des clés USB par exemple).
- 4) Exploitation : le code du logiciel malveillant se déclenche et agit sur le réseau cible pour exploiter la vulnérabilité identifiée.
- 5) Installation : le logiciel malveillant installe un point d'accès (une porte dérobée) utilisable par un attaquant externe.
- 6) Commandement et contrôle : le logiciel malveillant offre à l'attaquant un accès permanent au réseau cible.
- 7) Actions sur l'objectif : l'attaquant prend des mesures pour atteindre ses objectifs, tels que l'exfiltration de données, la destruction de données ou le chiffrement contre rançon.

## Des moyens de défense peuvent être mis en place pour contrer le déroulement présenté ci-dessus5 :

- 1) Détecter: déterminer si un attaquant fouille
- 2) Refuser: empêcher la divulgation d'informations et l'accès non-autorisé
- 3) Interrompre: arrêter ou modifier le trafic sortant (vers l'attaquant)
- 4) Dégrader: contre-attaquer face au commandement et contrôle pris par l'attaquant
- 5) Tromper: interférer avec le commandement et le contrôle pris par l'attaquant
- 6) Contenir: modifier la segmentation du réseau

## Modèles alternatifs de kill chain

Différentes organisations ont construit leurs propres kill chains pour essayer de modéliser différentes menaces. FireEye propose un modèle linéaire, similaire à celui proposé par Lockheed Martin. Dans la kill chain de FireEye, la persistance des menaces est soulignée : ce modèle souligne qu'une menace ne s'arrête pas après un cycle6.

- 1) Reconnaissance
- 2) Intrusion initiale dans le réseau
- 3) Établissement d'une porte dérobée dans le réseau
- 4) Obtention d'identifiants d'utilisateurs
- 5) Installation de programmes utilitaires divers
- 6) Élévation des privilèges / mouvement latéral / exfiltration de données
- 7) Maintien dans le système cible

MITRE tient à jour un modèle de kill chain connu sous le nom d'« ATT&CK ». Celui-ci modélise les tactiques, les techniques et les procédures utilisées par les acteurs malveillants et constitue une ressource utile pour les équipes rouges et bleues . Les pentesters peuvent imiter ce comportement lors d'exercices imitant des scénarios réels, afin d'aider leurs clients à déterminer l'efficacité de leurs mesures défensives7. Le framework ATT&CK comporte 4 matrices principales : PRE_ATT&CK, Enterprise, Mobile et ICS. L'Enterprise Matrix a des catégories pour Windows, macOS, Linux et le Cloud. Les catégories Enterprise Windows sont les suivantes :

- 1) Reconnaissance - Le recueil d'informations par l'attaquant qui pourront être utilisées
- 2) Développement de ressources - Recueil et mise en place de ressources qui pourront être utilisées dans les autres phases du cycle
- 3) Accès initial - Intrusion dans le réseau attaqué
- 4) Exécution - Exécution de code sur un système attaqué, local ou distant
- 5) Persistance - Maintien dans la durée d'une présence sur le système attaqué
- 6) Élévation des privilèges - Obtention d'un niveau de privilège plus élevé
- 7) Évasion de la défense - Échapper à la détection ou aux systèmes de sécurité
- 8) Accès authentifié - Utilisation d'informations d'identification légitimes pour accéder au système
- 9) Découverte - Acquisition post-compromission d'une connaissance interne du système
- 10) Mouvement latéral - Mouvement d'un système à un autre au sein du réseau cible
- 11) Collecte - Processus de collecte d'informations d’intérêt pour l'attaquant, telles que des fichiers, avant exfiltration
- 12) Commandement et contrôle - Communication avec les systèmes contrôlés par l'attaquant au sein du réseau cible
- 13) Exfiltration - Extraction des informations collectées, d’intérêt pour l'attaquant et sensibles pour le système cible
- 14) Impact - Perturbation des processus du système cible (les processus commerciaux et opérationnels 8 de l'organisation ciblée)

## Critiques de la kill chain

Parmi les critiques du modèle de kill chain de Lockheed Martin en tant qu'outil d'évaluation et de prévention des menaces, on note :

- le fait que les premières phases se déroulent en dehors du réseau cible, ce qui rend difficile l'identification ou la défense contre les actions dans ces phases9.
- le fait que cette méthodologie est censée renforcer les stratégies défensives traditionnelles, basées sur le périmètre (modèle de la «forteresse» plutôt que défense dite en profondeur) ainsi que la prévention des malwares10.
- le fait que la kill chain traditionnelle est inadaptée pour la modélisation de menaces internes 11.

## La kill chain unifiée

La kill chain unifiée se compose de 18 phases d'attaque uniques pouvant se produire dans des cyberattaques avancées.
Une version unifiée de la kill chain a été développée afin de surmonter les critiques émises à l'encontre de la kill chain traditionnelle, en unissant et en étendant la kill chain de Lockheed Martin et le modèle ATT&CK de MITRE . La kill chain unifiée est un arrangement ordonné de 18 phases d'attaque uniques, couvrant l'ensemble des activités se produisant à l'extérieur et au sein du réseau cible. En tant que telle, la kill chain unifiée améliore les limites de la portée de la kill chain traditionnelle et la nature agnostique des tactiques dans le modèle ATT&CK. Le modèle unifié peut être utilisé pour analyser, comparer et se défendre contre les cyberattaques complexes menées par des Advanced Persistent Threats (APT)12.

Source : https://fr.wikipedia.org/wiki/Kill_chain_(s%C3%A9curit%C3%A9_informatique)
