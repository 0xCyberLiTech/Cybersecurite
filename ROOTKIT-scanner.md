![Debian_logo-01](./images/Cloud-et-securite.png)

## CYBERSÉCURITÉ / Détecter les rootkits présents dans votre système Linux.

Introduction :

Votre système ne répond pas correctement ? Vous avez l’impression qu’une personne s’est introduite dans votre ordinateur ? Alors il est possible que vous ayez un Malware ou un rootkit sur votre machine.

Partons du principe où l’on a vérifié nos logs et on s’est rendu compte qu’une intrusion a eu lieu. Que faire dans ce cas ?

Vous avez sûrement entendu parler des portes dérobées dans la série Mr ROBOT .

Définition :

C’est quoi un Malwares ? C’est un logiciel malveillant qui a pour but de nuire sur le bon fonctionnement d’un système informatique.

Maintenant que l’on sait ce qu’est un maliciel, voyons les rootkits. Ce sont plusieurs techniques réunies en utilisant des softwares afin de pérenniser un accès au noyau d’un serveur.

- Comment savoir si votre machine est infectée ?
- Vous ne savez comment analyser votre système ?

Sur la plupart des distributions GNU/Linux dédiées aux tests de sécurités d’un système d’information, il existe plusieurs outils que vous pouvez utiliser pour voir la présence d’une porte dérobée ou programme malveillant. Ceux-ci sont dans la rubrique « Criminalistique » dans Kali Linux ou Parrot OS.

Imaginez que vous soupçonnez une personne ayant un accès non autorisé sur votre réseau ou machine. Que faire dans ce cas ? Il faut rechercher l’existence d’un script nuisible. Il y a deux outils pour ce faire : RKhunter et checkrootkit

Vous n’avez pas ces derniers installés et que vous utilisez Ubuntu par exemple ? Pas de panique, il suffit de taper la commande « apt install rkhunter ».

Je vais scanner ma machine Parrot OS à la recherche de rootkit.

Pour cela je vais utiliser rkhunter et regarder les différentes options utilisables avec l’option « -h ».
```
apt install rkhunter
```
```
rkhunter -h
```
Quel était notre objectif ? De checker notre système, donc je vais utiliser tout simplement l’option « -c ou –check » depuis mon terminal. Je peux demarrer mon scan.
```
rkhunter --check
```
```
root@srv-linux-05:~# rkhunter --check
[ Rootkit Hunter version 1.4.6 ]

Checking system commands...

  Performing 'strings' command checks
    Checking 'strings' command                               [ OK ]

  Performing 'shared libraries' checks
    Checking for preloading variables                        [ None found ]
    Checking for preloaded libraries                         [ None found ]
    Checking LD_LIBRARY_PATH variable                        [ Not found ]

  Performing file properties checks
    Checking for prerequisites                               [ OK ]
    /usr/sbin/adduser                                        [ OK ]
    /usr/sbin/chroot                                         [ OK ]
    /usr/sbin/cron                                           [ OK ]
    /usr/sbin/depmod                                         [ OK ]
    /usr/sbin/fsck                                           [ OK ]
    /usr/sbin/groupadd                                       [ OK ]
    /usr/sbin/groupdel                                       [ OK ]
    /usr/sbin/groupmod                                       [ OK ]
    /usr/sbin/grpck                                          [ OK ]
```

```
Checking for rootkits...

  Performing check of known rootkit files and directories
    55808 Trojan - Variant A                                 [ Not found ]
    ADM Worm                                                 [ Not found ]
    AjaKit Rootkit                                           [ Not found ]
    Adore Rootkit                                            [ Not found ]
    aPa Kit                                                  [ Not found ]
    Apache Worm                                              [ Not found ]
    Ambient (ark) Rootkit                                    [ Not found ]
    Balaur Rootkit                                           [ Not found ]
    BeastKit Rootkit                                         [ Not found ]
    beX2 Rootkit                                             [ Not found ]
```
Et voilà, le process d’analyse de rootkit vient de commencer.

Il va vérifier tous les scripts présents sur un système GNU/Linux.

Regardons de plus près l’analyse, il y a un script signalé « warning » donc possibilité d’être une fausse alerte ou présence d’un programme malveillant :
```
  Performing system configuration file checks
    Checking for an SSH configuration file                   [ Found ]
    Checking if SSH root access is allowed                   [ Warning ]
    Checking if SSH protocol v1 is allowed                   [ Not set ]
    Checking for other suspicious configuration settings     [ None found ]
    Checking for a running system logging daemon             [ Found ]
    Checking for a system logging configuration file         [ Found ]
```
Rapport :
```
System checks summary
=====================

File properties checks...
    Files checked: 139
    Suspect files: 0

Rootkit checks...
    Rootkits checked : 495
    Possible rootkits: 0

Applications checks...
    All checks skipped

The system checks took: 12 minutes and 40 seconds

All results have been written to the log file: /var/log/rkhunter.log

One or more warnings have been found while checking the system.
Please check the log file (/var/log/rkhunter.log)
```

Que faire ? Google est votre ami, allez faire des recherches en copiant le chemin suivi de rkhunter pour vérifier si l’alerte est un faux positif.
