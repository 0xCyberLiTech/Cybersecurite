<p align="center">
  <img src="./images/Cloud-et-securite.png" alt="Cyber Kill Chain" width="300">
</p>

<h1 align="center">🛡️ GEOHASH -Geohash est un système de géocodage des coordonnées géographiques</h1>

<p align="center">
  Une méthode d’analyse des cyberattaques pour mieux les comprendre et les contrer.
</p>

---

## CYBERSÉCURITÉ / GEOHASH SSH mise en place depuis Docker.

## Visualisez l’emplacement de l’attaquant SSH par force brute en temps réel

ID tableau de bord Grafana : 12323
```
docker run -e INFLUX_HOST=myinfluxdb.com -e INFLUX_DB=geoloc -p 7070:7070 acouvreur/ssh-log-to-influx
```
Conditions préalables :

- Docker
- Rsyslog
- Une instance InfluxDB (ou utilisez docker-compose.standalone.yml)
- Une instance Grafana (ou utilisez docker-compose.standalone.yml)

## Commencer :
Créer le sous dossier ~/containers/Geohash_ssh/.
```
mkdir -p ~/Containers/Geohash_ssh/
```
Créer le fichier ~/containers/Geohash_ssh/docker-compose.standalone.yml.
```
touch ~/Containers/Geohash_ssh/docker-compose.standalone.yml
```
Editer le fichier ~/containers/Geohash_ssh/docker-compose.standalone.yml
```
nano ~/Containers/Geohash_ssh/docker-compose.standalone.yml
```
Copier le code ci-dessous dans le fichier 'docker-compose.standalone.yml'qui est vide.
```
version: "3.8"

services:
  ssh-log-to-influx:
    image: acouvreur/ssh-log-to-influx:latest
    restart: always
    environment:
      - INFLUX_HOST=influxdb
      - INFLUX_DB=telegraf
    ports:
      - 7070:7070/tcp

  #----------------------------------------------#
  # InfluxDB : time series database
  #----------------------------------------------#
  influxdb:
    image: influxdb:1.8
    volumes:
      - influxdb_data:/var/lib/influxdb

  #----------------------------------------------#
  # Grafana : analytics and monitoring
  #----------------------------------------------#
  grafana-1:
    image: "grafana/grafana:latest"
    environment:
      - GF_INSTALL_PLUGINS=grafana-worldmap-panel,grafana-piechart-panel
    ports:
      - 3000:3000
    volumes:
      - grafana_data:/var/lib/grafana
      - ./grafana/provisioning:/etc/grafana/provisioning
      - ./grafana/config.ini:/etc/grafana/config.ini
      - ./grafana/dashboards:/var/lib/grafana/dashboards

volumes:
  influxdb_data:
  grafana_data:
```
Avec un InfluxDB et Grafana groupés
```
docker compose -f docker-compose.standalone.yml up
```
Avec un InfluxDB externe :

- INFLUX_PROTOCOL par défaut facultatif : protocole http à utiliser, http ou https.
- INFLUX_HOST Hôte d’afflux (FQDN) auquel se connecter.
- INFLUX_PORT Valeur par défaut facultative : port d’afflux 8086 auquel se connecter.
- INFLUX_USER Valeur par défaut facultative : nom d’utilisateur racine pour la connexion à la base de données.
- INFLUX_PWD facultatif par défaut : mot de passe root pour la connexion à la base de données.
- INFLUX_DB Base de données sur laquelle opérer.
- Remarque : Vous pouvez utiliser le nom de domaine complet du réseau Docker si vous placez le service dans le même réseau Docker que votre instance InfluxDB. INFLUX_HOST sera un afflux si le nom de votre service est l’afflux.

```
docker compose up -d
```
Tester le serveur TCP :
```
docker compose -f docker-compose.standalone.yml up
```

- 1) docker-compose -f docker-compose.standalone.yml up
- 2) netcat localhost 7070 ou avec Git bash pour Windowsncat localhost 7070
- 3) type: Failed password for username from 206.253.167.10 port 11111 ssh2
- 4) Les données doivent être analysées et ajoutées

## Configuration de Rsyslog :

Ajoutez ceci sous pour transférer les échecs d’authentification ssh au serveur local :/etc/rsyslog.conf

Activer 'PasswordAuthentication' :

```
template(name="OnlyMsg" type="string" string="%msg:::drop-last-lf%\n")
if $programname == 'sshd' then {
   if $msg startswith ' Failed' then {
      action(type="omfwd" target="127.0.0.1" port="7070" protocol="tcp" template="OnlyMsg")
   }
}
```
## Configuration du débogage :

- If you want to skip certificate validation, set to 0, but don't do this without understanding the implications.NODE_TLS_REJECT_UNAUTHORIZED
- DEBUG_LEVEL: level of logging in log4js, default is "info".
