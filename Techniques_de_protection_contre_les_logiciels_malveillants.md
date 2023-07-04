
<a name="Techniques_de_protection_contre_les_logiciels_malveillants.md"></a>
# Techniques de protection contre les logiciels malveillants :

| Cat  | Etapes |
|------|--------|
| - A. | [ Diminution de la surface d'attaque.](#balise_010) |
| - B. | [ Sensibilisation des utilisateurs.](#balise_011) |
| - C. | [ Détection.](#balise_012) |
| - D. | [ Gestion des correctifs.](#balise_013) |
| - E. | [ Contrôle des accès.](#balise_014) |
| - F. | [ Sauvegarde et chiffrement des données.](#balise_015) |

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

<a name="balise_014"></a>
## - E. Contrôle des accès.

Les commandes d'administration doivent être réservées aux applications approuvées et aux utilisateurs qui en ont réellement besoin. En cas d'attaque, le logiciel malveillant aura plus de difficultés à infecter les fonctions principales de votre système. Vérifiez fréquemment les commandes d'administration.

<a name="balise_015"></a>
## - F. Sauvegarde et chiffrement des données.

Un système de protection efficace des données peut radicalement changer la donne en cas d'attaque de logiciel malveillant. Dans le pire des cas, vous pourrez basculer vers une sauvegarde saine effectuée avant l'infection. Cela suppose d'isoler les sauvegardes pour éviter qu'elles ne soient endommagées ou écrasées. Vous pouvez aussi chiffrer les données afin de les rendre inexploitables en cas de vol. Pour cela, vous devrez peut-être combiner plusieurs stratégies selon la taille et la complexité de votre entreprise. Dans les structures de grande taille, le déploiement d'une solution de stockage logiciel dans un environnement de cloud hybride offre un large choix d'options pour la sauvegarde et le chiffrement des données.

Aucun système informatique n'est infaillible, et les développeurs de logiciels malveillants s'obstinent à détecter ces vulnérabilités et à les exploiter. C'est pourquoi la protection contre les logiciels malveillants évolue sans cesse.

Source : https://www.redhat.com/fr/topics/security/what-is-malware#:~:text=Un%20logiciel%20malveillant%20(ou%20malware,avec%20lesquels%20celui%2Dci%20communique.
