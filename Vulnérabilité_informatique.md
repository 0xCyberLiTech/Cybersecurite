Vulnérabilité (informatique)

Outils

Page d’aide sur l’homonymie

Cet article concerne la vulnérabilité en informatique. Pour une utilisation plus large du terme, voir Vulnérabilité.

Dans le domaine de la sécurité informatique, une vulnérabilité ou faille est une faiblesse dans un système informatique permettant à un attaquant de porter atteinte à l'intégrité de ce système, c'est-à-dire à son fonctionnement normal, à la confidentialité ou à l'intégrité des données qu'il contient.

Ces vulnérabilités sont la conséquence de faiblesses dans la conception, la mise en œuvre ou l'utilisation d'un composant matériel ou logiciel du système, mais il s'agit souvent d'anomalies logicielles liées à des erreurs de programmation ou à de mauvaises pratiques. Ces dysfonctionnements logiciels sont en général corrigés à mesure de leurs découvertes, mais l'utilisateur reste exposé à une éventuelle exploitation tant que le correctif (temporaire ou définitif) n'est pas publié et installé. C'est pourquoi il est important de maintenir les logiciels à jour avec les correctifs fournis par les éditeurs de logiciels. La procédure d'exploitation d'une vulnérabilité logicielle est appelée exploit.
Causes

Les vulnérabilités informatiques proviennent souvent de la négligence ou de l'inexpérience d'un programmeur. Il peut y avoir d'autres causes liées au contexte comme l'évolution des technologies, notamment en cryptographie. Une vulnérabilité permet généralement à l'attaquant de duper l'application, par exemple en outrepassant les vérifications de contrôle d'accès ou en exécutant des commandes sur le système hébergeant l'application.

Quelques vulnérabilités surviennent lorsque l'entrée d'un utilisateur n'est pas contrôlée, permettant l'exécution de commandes ou de requêtes SQL (connues sous le nom d'injection SQL). D'autres proviennent d'erreurs d'un programmeur lors de la vérification des buffers de données (qui peuvent alors être dépassés), causant ainsi une corruption de la pile mémoire (et ainsi permettre l'exécution de code fourni par l'attaquant).
Publication d'une vulnérabilité
Méthode de publication

La méthode de publication des vulnérabilités est un sujet qui fait débat au sein de la communauté de la sécurité des systèmes d'information. Certains affirment qu'il est nécessaire de publier immédiatement toutes les informations à propos d'une vulnérabilité dès qu'elle a été découverte (full disclosure). D'autres prétendent qu'il est préférable de limiter en premier lieu la publication uniquement aux programmeurs ou utilisateurs qui en ont un besoin important (divulgation responsable, voire coordonnée), puis après un certain délai, de publier en détail, s'il y a besoin.

Ces délais laissent le temps aux développeurs de corriger la vulnérabilité et aux utilisateurs d'appliquer les patchs de sécurité nécessaires, mais ils peuvent aussi accroître les risques pour ceux qui n'ont pas ces informations. Les éditeurs de logiciels appellent cette méthode de publication la divulgation responsable et encouragent les chercheurs en sécurité à l'utiliser. En théorie, ces délais permettent aux éditeurs de publier les correctifs nécessaires pour protéger leurs logiciels et leurs utilisateurs, mais en pratique, cela ne les contraint pas à corriger les vulnérabilités. Il a ainsi pu arriver que certaines vulnérabilités soient restées non corrigées pendant des mois voire des années, tant qu'aucun exploit n'a été publié. Devant cette situation, certains ont décidé de laisser un délai - considéré raisonnable - aux éditeurs pour corriger les vulnérabilités avant de les divulguer. Ainsi la société TippingPoint laisse un délai de 6 mois avant de divulguer les détails d'une vulnérabilité1.
Date et source de publication

La date de publication est la première date à laquelle une vulnérabilité est décrite sur un média. L'information révélée suit les conditions suivantes :

    l'information est disponible librement et publiquement ;
    l'information sur la vulnérabilité est publiée par une source indépendante et de confiance ;
    la vulnérabilité a fait l'objet d'analyse par des experts, notamment sur l'estimation du risque de la révélation.

D'un point de vue sécurité, seule une publication libre d'accès et complète peut assurer que toutes les parties intéressées obtiennent l'information appropriée. La sécurité par l'obscurité est un concept qui n'a jamais fonctionné.

La source de la publication doit être indépendante d'un éditeur, d'un vendeur, ou d'un gouvernement. Elle doit être impartiale pour permettre une diffusion de l'information juste et critique. Un média est considéré comme « de confiance » lorsqu'il est une source de la sécurité des systèmes d'information largement acceptée dans l'industrie (par exemple : CERT, CESTI).

L'analyse et l'estimation du risque assurent la qualité de l'information révélée. Une unique discussion sur une faille potentielle dans une liste de diffusion ou une vague information d'un vendeur ne permettent donc pas de qualifier une vulnérabilité. L'analyse doit inclure assez de détails pour permettre à un utilisateur concerné d'évaluer lui-même son risque individuel, ou de prendre une mesure immédiate pour se protéger.
Référence

Lorsqu'une vulnérabilité a été publiée, le MITRE lui attribue un identifiant CVE. Cet identifiant permet de faire des recherches croisées entre plusieurs sources d'information.
Identification et correction des vulnérabilités

Il existe de nombreux outils qui peuvent faciliter la découverte de vulnérabilités sur un système information, certains permettant leur suppression. Mais, bien que ces outils puissent fournir à un auditeur une bonne vision d'ensemble des vulnérabilités potentiellement présentes, ils ne peuvent pas remplacer le jugement humain. Se reposer uniquement sur des scanners automatiques de vulnérabilité rapportera de nombreux faux positifs et une vue limitée des problèmes présents dans le système.

Des vulnérabilités ont été trouvées dans tous les principaux systèmes d'exploitation, en premier lieu sur Windows, mais aussi sur Mac OS, différentes versions d'Unix et Linux, OpenVMS, et d'autres. La seule manière de réduire la probabilité qu'une vulnérabilité puisse être exploitée est de rester constamment vigilant en développant la maintenance système (par exemple en appliquant les patchs de sécurité), de déployer une architecture sécurisée (par exemple en plaçant judicieusement des pare-feu), de contrôler les accès, et de mettre en place des audits de sécurité (à la fois pendant le développement et pendant le cycle de vie).

Les téléphones mobiles et smartphones sont des équipements informatiques. Les logiciels espions utilisent les failles de sécurité des systèmes d'exploitation iOS ou Android des téléphones mobiles et évoluent en permanence. Les vulnérabilités zero-day étant très difficiles à trouver, elles font l'objet d'un véritable marché dans lequel des hackers vendent leurs trouvailles au plus offrant.
Exploitation malveillante

Les failles de sécurité deviennent particulièrement intéressantes lorsqu'un programme contenant une de ces vulnérabilités est lancé avec des privilèges spéciaux, qu'il permet une authentification sur un système, ou bien encore lorsqu'il fournit un accès à des données sensibles.

Les Crackers et non « hackers », grâce à leur connaissance et à des outils appropriés, peuvent prendre le contrôle de machines vulnérables. Les failles de sécurité découvertes sont généralement colmatées au plus vite à l'aide d'un patch, afin d'empêcher des prises de contrôles intempestives ; cependant dans bien des cas, des machines restent vulnérables à des failles anciennes, les différents correctifs n'ayant pas été appliqués.

Certains logiciels malveillants utilisent des vulnérabilités pour infecter un système, se propager sur un réseau, etc.

L'exploitation d'une faille peut provoquer un déni de service du système (programme informatique, noyau du système d'exploitation, etc.), un accès à un système ou à des informations sensibles, voire une élévation des privilèges d'un utilisateur.

On parle de faille distante lorsque la vulnérabilité se situe dans un logiciel constituant un service réseau (par exemple un serveur Web) et qu'elle peut être exploitée par un attaquant distant, qui ne dispose pas d'un compte local. Les vulnérabilités locales peuvent être utilisées par un utilisateur malintentionné, qui possède un compte, pour effectuer une élévation des privilèges, ou bien par un attaquant distant pour augmenter ses privilèges, après l'exploitation d'une vulnérabilité distante.

On parle de faille locale lorsque la vulnérabilité n'est exploitable que par un utilisateur disposant d'un compte local. Les vulnérabilités distantes peuvent être utilisées par des attaquants pour obtenir un accès sur un système.
Exemples de vulnérabilités

Les vulnérabilités ci-dessous font partie des plus connues :

    dépassement de tampon ;
    injection SQL ;
    cross site scripting.

Source : https://fr.wikipedia.org/wiki/Vuln%C3%A9rabilit%C3%A9_(informatique)
