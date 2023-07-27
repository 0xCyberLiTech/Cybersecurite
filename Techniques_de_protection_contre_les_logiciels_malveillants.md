

# Techniques de protection contre les logiciels malveillants :

- 01 - [ Diminution de la surface d'attaque.](#balise_010) |
- 02 - [ Sensibilisation des utilisateurs.](#balise_011) |
- 03 - [ Détection.](#balise_012) |
- 04 - [ Gestion des correctifs.](#balise_013) |
- 05 - [ Contrôle des accès.](#balise_014) |
- 06 - [ Sauvegarde et chiffrement des données.](#balise_015) |

<a name="balise_010"></a>
## - A. Diminution de la surface d'attaque.

Limitez le nombre de systèmes, d'applications et de ports exposés à Internet.

QU'EST-CE QUE LA SURFACE D'ATTAQUE ?

Les cyberattaques se multiplient, en particulier au sein des petites et moyennes entreprises, puisque selon un rapport, 70 % des petites entreprises ont essuyé une attaque.

De nombreuses petites et moyennes entreprises ne sont pas préparées à faire face à la prolifération des menaces de sécurité. En fait, 45 % de ces entreprises déclarent ne pas disposer de mesures de sécurité suffisantes pour empêcher ces cyberattaques. Cet article se penche sur une des vulnérabilités potentielles : la surface d’attaque des applications logicielles.

Les petites et moyennes entreprises peuvent mapper leurs faiblesses potentielles et implémenter un programme de gestion de la surface d’attaque pour réduire leur vulnérabilité et améliorer leur cybersécurité. Au final, l’application d’un plan de gestion de la surface d’attaque protège les données sensibles des clients ainsi que d’autres ressources précieuses contre les cyberattaques.

Surface d’attaque d’une application logicielle.

La surface d’attaque désigne l’ensemble des expositions potentielles à des risques de sécurité au sein de l’environnement logiciel d’une entreprise. En d’autres termes, il s’agit de l’ensemble des vulnérabilités potentielles (connues et inconnues) et des contrôles au niveau des tous les composants matériels, logiciels et réseau.

On distingue trois types de surfaces d’attaque de base :

1 - Surface d’attaque numérique : la surface d’attaque numérique englobe l’intégralité de l’environnement réseau et logiciel d’une entreprise. Elle inclut les applications, le code, les ports ainsi que les autres points d’entrée et de sortie.

2 - Surface d’attaque physique : la surface d’attaque physique d’une entreprise couvre tous les endpoints d’une entreprise : ordinateurs de bureau, ordinateurs portables, terminaux mobiles et ports USB.

3 - Surface d’attaque d’ingénierie sociale : les attaques d’ingénierie sociale exploitent les vulnérabilités liées au comportement des utilisateurs. Les types d’attaques les plus courants dont sont victimes les entreprises incluent le harponnage (« spear phishing »), le pretexting et d’autres techniques de manipulation visant à amener les utilisateurs à donner accès à leurs données sensibles.
Parmi toutes les vulnérabilités potentielles auxquelles les entreprises devraient être sensibilisées, nous examinons ici la surface d’attaque des applications logicielles, c’est-à-dire toutes les fonctions possibles d’un code au sein d’un environnement logiciel auxquelles un utilisateur non authentifié ou un logiciel malveillant peut accéder.

- Identification de la surface d’attaque d’une application.

Pour identifier la surface d’attaque d’une application logicielle, il convient de mapper toutes les fonctions à examiner et à tester à la recherche de vulnérabilités. Cela veut dire que tous les points d’entrée et de sortie du code source de l’application doivent être examinés. Plus la surface d’attaque d’une application logicielle est grande, plus il sera facile pour le cyberattaquant ou le logiciel malveillant d’accéder au code et de l’exécuter sur une machine cible.

- Gestion de la surface d’attaque.

La gestion de la surface d’attaque des applications logicielles vise à identifier les faiblesses d’un système et à réduire le nombre de vulnérabilités exploitables. L’analyse de la surface d’attaque a pour but d’exposer aux développeurs et aux experts en sécurité l’ensemble des zones de risque d’une application. La sensibilisation constitue la première étape sur la voie de l’identification de solutions pour atténuer les risques.

En fin de compte, les entreprises peuvent utiliser l’analyse de la surface d’attaque pour implémenter ce que l’on appelle communément la sécurité Zero Trust au moyen de concepts clés tels que la segmentation du réseau et d’autres stratégies similaires.

<a name="balise_011"></a>
## - B. Sensibilisation des utilisateurs.

Les utilisateurs doivent apprendre à se méfier des pièces jointes et des liens inclus dans les e-mails, même s'ils semblent fiables. Ils doivent également apprendre comment des menaces internes peuvent causer des attaques de logiciels malveillants.

Sensibiliser les utilisateurs (aussi bien internes qu’externes à l’organisme) travaillant avec des données personnelles aux risques liés aux libertés et à la vie privée des personnes, les informer des mesures prises pour traiter ces risques et des conséquences potentielles en cas de manquement. Concrètement, il peut s’agir d’organiser une séance de sensibilisation, d’envoyer régulièrement les mises à jour des procédures pertinentes pour les personnes selon leurs fonctions, de faire des rappels par messagerie électronique, etc.

Documenter les procédures d’exploitation, les tenir à jour et les rendre disponibles à tous les utilisateurs concernés. Concrètement, toute action sur un traitement de données personnelles, qu’il s’agisse d’une opération d’administration ou de la simple utilisation d’une application, doit être expliquée dans un langage clair et adapté à chaque catégorie d’utilisateurs, dans des documents auxquels ces derniers peuvent se référer.

Rédiger une charte informatique et lui donner une force contraignante (ex. : annexion au règlement intérieur). Cette charte devrait au moins comporter les éléments suivants :
```
- Le rappel des règles de protection des données et les sanctions encourues en cas de non respect de celles-ci.
```
Le champ d’application de la charte, qui inclut notamment :
```
- les modalités d’intervention des équipes chargées de la gestion des ressources informatiques de l’organisme.
- les moyens d’authentification utilisés par l’organisme et la politique de mots de passe que l’utilisateur doit respecter.
```
les règles de sécurité auxquelles les utilisateurs doivent se conformer, ce qui doit inclure notamment de signaler au service informatique interne toute violation ou tentative de violation suspectée de son compte informatique, toute perte ou vol de matériel et, de manière générale, tout dysfonctionnement.
```
- Ne jamais confier son identifiant/mot de passe à un tiers.
- Ne pas installer, copier, modifier, détruire des logiciels et leur paramétrage sans autorisation.
- Verrouiller son ordinateur dès que l’on quitte son poste de travail.
- Ne pas accéder, tenter d’accéder, ou supprimer des informations si cela ne relève pas des tâches incombant à l’utilisateur.
- Respecter les procédures préalablement définies par l’organisme afin d’encadrer les opérations de copie de données sur des supports amovibles, notamment en obtenant l’accord préalable du supérieur hiérarchique et en respectant les règles de sécurité.
```
Les modalités d’utilisation des moyens informatiques et de télécommunications mis à disposition comme :
```
- le poste de travail.
- les équipements nomades (notamment dans le cadre du télétravail).
- les espaces de stockage individuel.
- les réseaux locaux.
- les conditions d’utilisation des dispositifs personnels.
- l’accès à Internet.
- la messagerie électronique.
- la téléphonie.
```
- Les conditions d’administration du système d’information, et l’existence, le cas échéant, de :
```
 - systèmes automatiques de filtrage.
 - systèmes automatiques de traçabilité.
 - systèmes de gestion du poste de travail.
 - Les responsabilités et sanctions encourues en cas de non respect de la charte.
```
https://www.cnil.fr/fr/securite-informatique-sensibiliser-les-utilisateurs

<a name="balise_012"></a>
## - C. Détection.

Plus tôt vous détectez l'intrusion d'un logiciel malveillant, plus vite vous pouvez réparer le système infecté. N'oubliez pas que certains logiciels malveillants sont indécelables.Pensez à mettre à jour régulièrement les signatures de détection des antivirus ou des anti-logiciels malveillants, ainsi qu'à appliquer plusieurs mesures de détection adaptées.

<a name="balise_013"></a>
## - D. Gestion des correctifs.

Les programmes de maintenance logicielle essaient de corriger les failles de sécurité le plus tôt possible. En utilisant les dernières versions des logiciels, vous réduisez les risques d'infection par un logiciel malveillant. La gestion des correctifs consiste à s'assurer que les correctifs de sécurité sont appliqués dans les meilleurs délais à l'ensemble des systèmes de l'entreprise. Aussi, vérifiez régulièrement si des mises à jour sont disponibles et appliquez-les afin de vous prémunir contre les exploits connus.

QU'EST-CE QUE LA GESTION DES CORRECTIFS ?

La gestion des correctifs consiste à identifier et à déployer des mises à jour logicielles, également appelées « correctifs » ou « patchs », sur différents endpoints, notamment des ordinateurs, des terminaux mobiles et des serveurs.

Les correctifs sont généralement distribués par les développeurs de logiciels pour corriger des vulnérabilités de sécurité ou des problèmes techniques connus. Ils permettent également d’ajouter de nouvelles fonctionnalités et fonctions à l’application. Ces solutions à court terme sont destinées à être utilisées jusqu’à la publication de la version suivante du logiciel.

Le processus de gestion des correctifs peut être pris en charge par l’équipe informatique, un outil automatisé ou une combinaison des deux. Pour être efficace, le processus de gestion des correctifs doit comprendre les étapes suivantes :

- Examen des correctifs de sécurité distribués.

Priorisation des correctifs à appliquer en fonction de la gravité de la vulnérabilité.

Test de la compatibilité des correctifs et installation sur tous les endpoints concernés.

Une stratégie précise et efficace de gestion des correctifs est indispensable pour assurer la sécurité du réseau, car ces correctifs sont conçus pour remédier à des vulnérabilités connues. Le risque associé à l’utilisation d’un logiciel obsolète sera encore plus grand si les cyberadversaires sont en mesure d’identifier et d’exploiter plus facilement les failles des systèmes.

Pourquoi faut-il assurer la gestion des correctifs ?

La gestion des correctifs est un élément incontournable de la stratégie de gestion des vulnérabilités d’une entreprise en vue d’assurer sa cybersécurité. Les applications logicielles et les systèmes d’exploitation non corrigés sont l’une des principales causes de compromission de la sécurité à l’heure actuelle. Un processus de gestion des correctifs rapide et précis, associé à des outils et processus de surveillance, de détection et de correction, permet de réduire le risque de tels incidents.

Ces dernières années, la migration vers le cloud ainsi que la montée en puissance du télétravail et de l’utilisation de terminaux personnels au travail ont rendu l’élaboration de règles plus strictes en matière de gestion des correctifs plus indispensable que jamais. Un processus moderne de gestion des correctifs doit protéger tous les endpoints qui se connectent au réseau, quel que soit leur propriétaire ou leur emplacement.

En plus de renforcer la cybersécurité, les correctifs aident les entreprises à améliorer leurs performances globales en minimisant les temps d’arrêt dus aux logiciels obsolètes ou non pris en charge. Dans certains cas, les correctifs offrent de nouveaux avantages et ajoutent des fonctionnalités qui renforcent l’efficacité opérationnelle.

Il est par ailleurs important de noter que, dans bien des cas, la gestion des correctifs est rendue obligatoire par les instances sectorielles ou gouvernementales ou autres organes de réglementation. Le non-respect de cette obligation peut donner lieu à des amendes, des sanctions et autres pénalités.

Problèmes courants liés à la gestion des correctifs.

Il peut sembler naturel d’appliquer des correctifs pour assurer la sécurité et la protection des activités et des ressources d’une entreprise. Pourtant, le nombre de cyberattaques dues à des systèmes non corrigés ne cesse d’augmenter, ce qui signifie que de nombreuses entreprises ne disposent pas encore d’un processus efficace de gestion des correctifs permettant de déployer rapidement et efficacement les mises à jour.

L’incapacité d’une entreprise à déployer des correctifs peut avoir plusieurs causes, notamment :

L’absence de collaboration entre l’équipe de cybersécurité et l’équipe informatique.

Les correctifs sont généralement distribués par les éditeurs de logiciels pour corriger des vulnérabilités de sécurité connues. Ils figurent donc en haut de la liste des priorités de l’équipe de sécurité informatique. En revanche, les tests et le déploiement de ces correctifs sont généralement dévolus à l’équipe informatique, qui a souvent bien d’autres priorités, de sorte que la correction des vulnérabilités est souvent reléguée au second plan. De nombreuses équipes informatiques privilégient les opérations système à la sécurité et concentrent leurs efforts sur l’amélioration à court terme de la productivité des systèmes plutôt que sur l’identification des éventuels points faibles. Compte tenu des risques croissants que font courir les systèmes mal corrigés, la collaboration entre le service informatique et l’équipe de sécurité des informations doit être renforcée afin d’élaborer une stratégie de gestion des vulnérabilités et des correctifs efficace et rapide.

Des priorités mal définies.

L’équipe de sécurité fournit souvent une longue liste de systèmes à corriger à l’équipe informatique, de sorte que celle-ci peut vite se retrouver submergée. Il est presque impossible pour les entreprises de corriger tous les systèmes. Une collaboration entre les deux équipes est par conséquent nécessaire pour déterminer où concentrer les ressources souvent limitées. Il convient de déterminer les logiciels et systèmes à protéger en priorité, d’évaluer régulièrement les vulnérabilités et de rechercher les mises à jour de correctifs correspondantes. Dans la mesure où les ressources varient d’une entreprise à l’autre, la stratégie d’application de correctifs doit être fonction du type de vulnérabilité, du niveau de risque et des répercussions potentielles sur les activités.

Des règles informelles en matière d’application des correctifs.

De nombreuses entreprises ne disposent pas de règles formelles d’application des correctifs ou de mécanismes d’application permettant de s’assurer que les mises à jour nécessaires ont été effectuées. Comme indiqué plus haut, les équipes informatiques ne disposent pas toujours du temps ou des ressources nécessaires pour appliquer les correctifs de manière régulière. En outre, l’absence de règles formelles n’encourage pas les équipes à accorder l’attention requise à cette tâche, en particulier lorsqu’elles sont également chargées du fonctionnement et de l’intégrité du réseau. Les entreprises doivent implémenter des règles claires et contraignantes en matière d’application des correctifs afin que l’équipe informatique inscrive cette tâche au nombre de ses priorités et assume ses responsabilités en la matière.

En quoi consiste le processus de gestion des correctifs ?

Compte tenu du rôle que joue l’application des correctifs dans la stratégie de cybersécurité globale de l’entreprise, il convient de mettre en place un processus précis et cohérent de correction des systèmes d’exploitation et des applications logicielles.

Dans le même temps, il n’est pas réaliste de confier à une équipe informatique déjà surchargée des tâches aussi fastidieuses que la surveillance manuelle des vulnérabilités, les tests et le déploiement des correctifs. Pour compliquer encore les choses, la migration vers le cloud ainsi que la généralisation du télétravail et de l’utilisation de terminaux personnels au bureau obligent la plupart des entreprises à se doter de solutions automatisées de gestion des vulnérabilités et d’application des correctifs pour accélérer le processus.

L’utilisation de telles solutions peut contribuer à améliorer l’efficacité du processus, à réduire les coûts et à limiter les perturbations des activités. Heureusement, de nombreux éditeurs proposent de nouvelles solutions basées sur les risques qui permettent de relever efficacement les défis de l’application des correctifs.

Bonnes pratiques en matière de gestion des correctifs.

Comment donc améliorer le processus de gestion des vulnérabilités et des correctifs ? Plusieurs solutions très efficaces permettent de relever les défis de la surveillance continue des vulnérabilités et du déploiement des mises à jour de correctifs. Vous trouverez ci-après quelques bonnes pratiques permettant de maintenir une ligne de défense robuste face aux cyberadversaires.

Mesures à prendre.

Mettez en place un cadre d’évaluation des risques. Nombreuses sont les entreprises qui n’ont pas conscience de la menace réelle et persistante que représentent les cybercriminels. Elles n’admettent pas toujours que les vulnérabilités présentes dans certains systèmes ou applications sont autant de possibilités d’exploitation. C’est la raison pour laquelle un cadre d’évaluation des risques (RAF, Risk Assessment Framework) est utile. Il permet en effet aux équipes informatiques d’identifier les vulnérabilités et les correctifs associés, ainsi que de déterminer les systèmes à corriger en priorité. Les équipes informatiques et de sécurité des informations doivent collaborer à l’élaboration d’un modèle d’évaluation des risques qui définit les règles d’application des correctifs et les accords de niveau de service afin de limiter les risques critiques ou majeurs.

Les deux équipes pourront alors établir une liste des priorités qui identifie les systèmes à corriger en priorité et les risques opérationnels éventuels associés à de telles décisions.

Documentez et réévaluez les règles en matière de responsabilité. Lors de l’élaboration d’un modèle de cadre d’évaluation des risques, les responsables informatiques et de sécurité doivent convenir ensemble des critères d’évaluation des vulnérabilités et de la méthode de priorisation des correctifs à appliquer. L’équipe dirigeante doit ensuite examiner et approuver ces plans, ainsi que les éventuelles exceptions, confirmant ainsi que l’entreprise accepte les risques associés. Cette hiérarchie de la gestion des vulnérabilités permet d’établir la responsabilité des équipes et de garantir l’application des correctifs aux systèmes en temps opportun. Un réexamen de ce modèle et des règles connexes aidera les équipes à se tenir informées des nouvelles vulnérabilités et solutions d’application de correctifs.

Constituez une équipe dédiée de gestion des vulnérabilités. Les entreprises qui disposent de suffisamment de ressources doivent envisager de mettre en place une équipe alliant informatique et sécurité dédiée à la gestion des vulnérabilités et des correctifs. Cette équipe serait chargée de l’identification des vulnérabilités et du déploiement rapide des correctifs, au moyen du cadre d’évaluation des risques décrit plus haut. L’un des principaux avantages de cette approche est qu’elle permet aux responsables de la sécurité de produire des mesures pour évaluer l’efficacité du programme et identifier les domaines nécessitant des améliorations ou des investissements supplémentaires.

Utilisez des solutions de gestion des vulnérabilités pour prioriser l’application des correctifs. Toutes les solutions de gestion des vulnérabilités ne se valent pas. Lors de l’élaboration de règles d’application des correctifs, il est important de tenir compte de la solution de gestion des vulnérabilités utilisée par l’entreprise pour prendre des décisions mieux informées quant à la meilleure façon de corriger les vulnérabilités. De telles solutions doivent offrir une protection optimale contre les vulnérabilités (grâce notamment à une analyse réseau continue) et inclure des fonctionnalités de priorisation des correctifs à appliquer. Ces fonctionnalités peuvent contribuer à réduire de manière significative le délai de correction, en particulier pour les vulnérabilités critiques et prioritaires.

Quels sont les outils de gestion des correctifs les plus performants ?
Ces dernières années, de nombreuses solutions de gestion des vulnérabilités ont été renforcées et intègrent désormais un processus de gestion des correctifs. Comme il existe également des outils dédiés de gestion des correctifs, il convient de mettre en balance les avantages de l’utilisation d’outils distincts de gestion des correctifs par rapport à une solution de gestion des vulnérabilités plus générale. Dans tous les cas, la solution choisie doit permettre à l’entreprise de mettre en place un processus récurrent et régulier de surveillance des vulnérabilités et d’application des correctifs.

L’utilisation d’un outil de gestion des vulnérabilités et des correctifs se traduit souvent par des économies de coûts pour l’entreprise, que ce soit directement, en raison du gain de temps et d’énergie pour l’équipe informatique, ou indirectement, du fait de la réduction du risque de compromission et des temps d’arrêt induite par la correction des systèmes et applications.

Diverses solutions de gestion des vulnérabilités et des correctifs disponibles sur le marché contribuent à l’automatisation du processus d’identification et de correction des vulnérabilités. Pour trouver la solution la mieux adaptée à vos activités, il est essentiel de déterminer les besoins de votre entreprise en collaboration avec votre partenaire de cybersécurité et d’évaluer la capacité de chaque solution à les satisfaire. Les questions suivantes vous aideront à mettre en lumière les fonctionnalités effectivement offertes par les différentes solutions de gestion des vulnérabilités et des correctifs :





Compatibilité :

 - La solution de gestion des vulnérabilités et des correctifs est-elle compatible avec différents systèmes d’exploitation, tels que 
   Windows et Linux, ainsi qu’avec des plateformes tierces comme Amazon Web Services ?
 - La solution prend-elle en charge à la fois les ressources cloud et les réseaux traditionnels sur site ?
 - La solution s’intègre-t-elle avec les outils de sécurité actuellement utilisés par l’entreprise ?

Surveillance et évaluation :

 - La solution de gestion des vulnérabilités et des correctifs analyse-t-elle le réseau en continu pour identifier les vulnérabilités dans 
   l’ensemble des applications logicielles et des systèmes d’exploitation ?
 - La solution contextualise-t-elle les exigences en matière d’application de correctifs en formulant des recommandations pour prioriser 
   les efforts ou déterminer le degré d’urgence des principales mises à jour ?

Test et déploiement :
 - La solution est-elle en mesure de télécharger automatiquement les correctifs depuis les sites des différents éditeurs ?
 - L’outil de gestion des vulnérabilités et des correctifs est-il doté d’une puissante fonctionnalité de test ?
 - La solution peut-elle déployer des correctifs en urgence ? Peut-elle être configurée pour déployer automatiquement les correctifs sur
   l’ensemble des terminaux et des endpoints ?

Production de rapports.

 - Le logiciel de gestion des vulnérabilités et des correctifs informe-t-il régulièrement l’équipe informatique de l’état des 
   vulnérabilités, de l’état de chaque mise à jour de correctif, y compris des correctifs manquants, ainsi que des échecs ou erreurs de 
   déploiement ?
 - La solution peut-elle produire facilement un rapport de synthèse de toutes les vulnérabilités ouvertes et corrigées, ainsi que des 
   opérations d’application de correctifs, en cas d’audit interne ou à la demande d’un organisme de réglementation ?
 - La solution s’intègre-t-elle avec les règles d’application des correctifs de l’entreprise et signale-t-elle les violations potentielles ?

Quel avenir pour la gestion des correctifs ?

La migration vers le cloud expose les entreprises à de nouvelles vulnérabilités de sécurité, dont beaucoup sont exploitées activement 
par des cybercriminels du monde entier. Il est particulièrement important d’atténuer ces menaces au vu du nombre croissant de 
collaborateurs en télétravail et connectant leurs terminaux personnels aux réseaux de l’entreprise dans le contexte de la pandémie de 
COVID-19.

Les entreprises peuvent éprouver des difficultés à appliquer les correctifs de manière efficace et rapide en raison des conflits entre services, de l’absence de règles de gestion des correctifs et de la responsabilisation limitée. Heureusement, de nombreux éditeurs de solutions de cybersécurité développent de nouvelles solutions basées sur les risques qui permettent de relever efficacement les défis de l’identification des vulnérabilités et de l’application des correctifs. Si les outils et solutions de gestion des vulnérabilités et des correctifs sont voués à jouer un rôle déterminant dans la stratégie d’application des correctifs de l’entreprise, leur efficacité dépendra également de la mise en place de règles et de procédures sous-jacentes pour garantir que les priorités en matière d’application des correctifs sont respectées et identifier les responsables de cette activité.

Selon toute vraisemblance, l’avenir de la gestion des correctifs sera :

Selon toute vraisemblance, l’avenir de la gestion des correctifs sera :

 - Intégré : il est probable que les solutions isolées uniquement dédiées à la recherche des vulnérabilités ou à la mise à jour des 
   correctifs seront regroupées dans des solutions complètes
 - Automatisé : la gestion des correctifs s’appuiera sur l’automatisation pour accélérer les tâches routinières et récurrentes tout au long 
   du processus d’application des correctifs.
 - Responsable : pour être efficace, une stratégie d’application des correctifs doit s’appuyer sur des règles claires et identifier les 
   collaborateurs de l’entreprise responsables de la supervision des activités et des décisions connexes.
 - Collaboratif : une gestion fructueuse des correctifs requiert la collaboration de la direction et des équipes informatiques et de 
   sécurité des informations afin d’élaborer un plan d’action raisonnable et efficace.

Source : https://www.crowdstrike.fr/cybersecurity-101/patch-management/

<a name="balise_014"></a>
## - E. Contrôle des accès.

Les commandes d'administration doivent être réservées aux applications approuvées et aux utilisateurs qui en ont réellement besoin. En cas d'attaque, le logiciel malveillant aura plus de difficultés à infecter les fonctions principales de votre système. Vérifiez fréquemment les commandes d'administration.

<a name="balise_015"></a>
## - F. Sauvegarde et chiffrement des données.

Un système de protection efficace des données peut radicalement changer la donne en cas d'attaque de logiciel malveillant. Dans le pire des cas, vous pourrez basculer vers une sauvegarde saine effectuée avant l'infection. Cela suppose d'isoler les sauvegardes pour éviter qu'elles ne soient endommagées ou écrasées. Vous pouvez aussi chiffrer les données afin de les rendre inexploitables en cas de vol. Pour cela, vous devrez peut-être combiner plusieurs stratégies selon la taille et la complexité de votre entreprise. Dans les structures de grande taille, le déploiement d'une solution de stockage logiciel dans un environnement de cloud hybride offre un large choix d'options pour la sauvegarde et le chiffrement des données.

Aucun système informatique n'est infaillible, et les développeurs de logiciels malveillants s'obstinent à détecter ces vulnérabilités et à les exploiter. C'est pourquoi la protection contre les logiciels malveillants évolue sans cesse.

Source : https://www.redhat.com/fr/topics/security/what-is-malware#:~:text=Un%20logiciel%20malveillant%20(ou%20malware,avec%20lesquels%20celui%2Dci%20communique.
