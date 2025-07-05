# Fiche Réflexe en Cybersécurité : Guide Opérationnel

En matière de cybersécurité, la préparation est la clé de la résilience. Une "fiche réflexe" est un document opérationnel crucial qui guide toute personne au sein d'une organisation sur les premières actions à mener en cas d'incident de sécurité informatique.

Conçue pour être concise et immédiatement applicable, elle permet de réagir de manière ordonnée et efficace dans une situation de stress, minimisant ainsi les impacts d'une attaque.

---

## Objectifs d'une Fiche Réflexe

Une fiche réflexe vise à :
- **Qualifier l'incident :** Confirmer rapidement la nature de l'attaque (rançongiciel, hameçonnage, fuite de données, etc.).
- **Contenir la menace (Endiguement) :** Isoler les systèmes affectés pour stopper la propagation.
- **Alerter les bonnes personnes :** Identifier et contacter rapidement les responsables internes et les partenaires externes.
- **Préserver les preuves :** Sauvegarder les éléments nécessaires à l'analyse post-incident et à une éventuelle procédure judiciaire.
- **Lancer la remédiation :** Initier les premières étapes de la reconstruction et du retour à la normale.

---

## Modèle de Fiche Réflexe Générique

Voici un modèle adaptable, inspiré des recommandations de l'Agence Nationale de la Sécurité des Systèmes d'Information (ANSSI) et de Cybermalveillance.gouv.fr. Il est à personnaliser en fonction de la structure et du système d'information de chaque organisation.

---

### **FICHE RÉFLEXE CYBERSÉCURITÉ : PREMIERS GESTES EN CAS D'INCIDENT**

**ATTENTION : En cas de suspicion d'incident, gardez votre calme et suivez cette procédure. Ne prenez pas d'initiatives non coordonnées.**

### 1. Identification et Qualification de l'Incident

* **Quel est le problème observé ?** (Ex: Fichiers chiffrés, message de demande de rançon, site web défiguré, lenteurs extrêmes, alertes antivirus, etc.)
* **Quand le problème a-t-il été découvert et par qui ?**
* **Quels sont les systèmes, applications ou données impactés ?** (Serveurs, postes de travail, applications métier, etc.)
* **L'activité de l'entreprise est-elle perturbée ? Si oui, comment ?**

### 2. Actions Immédiates : L'Endiguement

| Type d'incident suspecté          | Actions immédiates à réaliser                                                                                                                                                                                                                                                                 |
| :-------------------------------- | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Rançongiciel (Ransomware)** | 1. **Isoler immédiatement la ou les machines compromises :**<br>   - **Débrancher le câble réseau (Ethernet).**<br>   - **Désactiver le Wi-Fi.**<br>2. **NE PAS ÉTEINDRE** la machine. Laissez-la en l'état pour l'analyse forensique.<br>3. **NE PAS PAYER LA RANÇON.** |
| **Hameçonnage (Phishing)** | 1. **Ne pas cliquer sur les liens, ni ouvrir les pièces jointes.**<br>2. **Ne pas répondre à l'expéditeur.**<br>3. **Signaler le message** comme "hameçonnage" dans votre client de messagerie.<br>4. Si des identifiants ont été saisis : **changer immédiatement le mot de passe** du compte concerné et de tous les autres comptes utilisant le même mot de passe.<br>5. **Alerter** l'équipe IT. |
| **Intrusion / Compromission de compte** | 1. **Changer immédiatement les mots de passe** des comptes suspectés et des comptes administrateurs.<br>2. **Déconnecter toutes les sessions actives** du compte compromis.<br>3. **Vérifier les règles de transfert d'emails** et autres modifications suspectes.<br>4. **Isoler les systèmes** sur lesquels le compte a été utilisé. |
| **Attaque par Déni de Service (DDoS)** | 1. **Contacter immédiatement votre hébergeur ou fournisseur d'accès Internet.** Ils disposent des outils pour mitiger l'attaque à la source.<br>2. **Analyser les logs** pour identifier l'origine et le type d'attaque (si possible). |

### 3. Alerter : Qui Contacter ?

* **Responsable de la Sécurité des Systèmes d'Information (RSSI) / Équipe Informatique :**
    * **Nom :** `[Nom du contact interne]`
    * **Téléphone :** `[Numéro de téléphone]`
    * **Email :** `[Email du contact]`

* **Direction / Cellule de crise :**
    * Informer la direction de l'incident et de ses impacts potentiels.

* **Contacts Externes (selon la gravité et la nature de l'incident) :**
    * **CERT-FR :** Le centre gouvernemental de veille, d'alerte et de réponse aux attaques informatiques (pour les OIV et administrations).
    * **Cybermalveillance.gouv.fr :** Pour obtenir de l'aide et être mis en relation avec des prestataires spécialisés.
    * **Prestataire de maintenance ou d'infogérance.**
    * **Forces de l'ordre (Police ou Gendarmerie) :** Pour un dépôt de plainte, indispensable pour les assurances. Contactez le `0 800 811 414` (Info Escroqueries) ou la brigade numérique de la Gendarmerie.
    * **Commission Nationale de l'Informatique et des Libertés (CNIL) :** En cas de violation de données personnelles, une notification est obligatoire dans les 72 heures.

### 4. Préserver les Preuves

* **Ne pas éteindre les machines compromises** (sauf instruction contraire des experts), car cela efface des preuves cruciales en mémoire vive (RAM).
* **Ne supprimer aucun fichier ou log.**
* **Noter chronologiquement toutes les actions entreprises :** Qui a fait quoi, quand et pourquoi.
* **Réaliser des copies des disques durs** des machines affectées (si vous avez les compétences et les outils).

### 5. Communication

* **Interne :** Informer les collaborateurs des mesures à prendre (ex: "Ne plus utiliser telle application", "Se déconnecter du réseau").
* **Externe :** Préparer les éléments de langage pour les clients, fournisseurs ou le public si l'incident a un impact externe. La communication doit être contrôlée et validée par la direction.

---

## Comment Utiliser cette Fiche ?

-   **Diffusion :** Cette fiche doit être accessible à tous les employés, en version numérique et papier (en cas de panne du système d'information).
-   **Sensibilisation :** L'existence et le contenu de cette fiche doivent faire l'objet de sessions de sensibilisation régulières.
-   **Mise à jour :** Les informations, notamment les contacts, doivent être vérifiées et mises à jour au moins une fois par an.
