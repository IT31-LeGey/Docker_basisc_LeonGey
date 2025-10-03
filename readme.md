# Hier alle im Video erwähnten Befehle:

## Docker installieren:

```
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh ./get-docker.sh
```

Falls kein curl installiert: `apt install curl`

Wenn man nicht mit dem Nutzer Root arbeitet, sollte man den aktuellen Benutzer berechtigen:

```
sudo usermod -aG docker $USER
```

## Mit Docker arbeiten

* Laufende Container auflisten: `docker ps`
* Alle Container auflisten (auch gestoppte): `docker ps -a`
* Einen Container anhalten: `docker stop <Containername>` (den Namen findet man mit `docker ps` heraus)
* Einen gestoppten Container endgültig löschen: `docker rm <Containername>`

## Einen simplen Webserver starten

Der Container aus dem Image nginx fährt mit folgendem Befehl hoch:

```
docker run -p 80:80 nginx
```
Die eigene IP-Adresse erhält man mit `ip a`

## Arbeiten mit Docker-Compose

Legt euch am besten einen eigenen Ordner für das Docker-Projekt an, um Ordnung zu halten. Die Datei docker-compose.yml enthält die Definition der Container.

Bearbeitet wird die Datei mit:

```
nano docker-compose.yml
```

Die Inhalte findet ihr unten in diesem GitHub-Gist. Den Texteditor Nano beendet man mit: `Strg+X`, dann `Y`

Die Compose-Zusammenstellung hochfahren:

```
docker compose up -d
```

Will man die Container updaten, lädt man die neuen Images mit 

```
docker compose pull
```

## Eine oder mehrere Docker-Compose-Dateien?

Das ist definitiv Geschmachssache und hängt von der Umgebung ab. Wenn man mehr als ein Projekt (zum Beispiel einen Blog und ein Pihole) auf einem Server betreibt, sollte man für jedes einen Ordner anlegen und darin eine Docker-Compose-Datei ablegen. Die nützlichen Helfer wie Portainer und Watchtower kommen zusammen in eine weitere Datei. Dann kann man mit `docker compose down`gezielt Teile der Umgebung herunterfahren.


# Docker_basisc_LeonGey

##Pi-hole
Pi-hole ist ein Werbeblocker für Ihr gesamtes Netzwerk. Anstatt auf jedem Gerät eine eigene Software zu installieren, filtert Pi-hole den Datenverkehr zentral für alle verbundenen Geräte. Es funktioniert, indem es Anfragen an bekannte Werbe- und Tracking-Domains blockiert, bevor sie überhaupt auf Ihrem Gerät ankommen.

##Watchtower
Watchtower hält Ihre Docker-Anwendungen automatisch auf dem neuesten Stand. Das Tool behält die von Ihnen genutzten Docker-Images im Auge und sobald eine neue Version veröffentlicht wird, startet es Ihre Container selbstständig mit dem aktuellen Image neu.

##Nginx
Nginx ist ein leistungsstarkes und flexibles Werkzeug für Webanwendungen. Hauptsächlich wird es als schneller Webserver genutzt, der Webseiten ausliefert. Es kann aber auch als intelligenter Vermittler (Reverse Proxy) den Datenverkehr zu Ihren Anwendungen steuern, die Last auf mehrere Server verteilen (Load Balancer) oder Inhalte zwischenspeichern, um alles zu beschleunigen.

##Portainer
Portainer vereinfacht die Verwaltung von Container-Systemen wie Docker und Kubernetes durch eine benutzerfreundliche, grafische Oberfläche. Anstatt Befehle in eine Kommandozeile tippen zu müssen, können Sie Ihre Container, Anwendungen und Netzwerke bequem über ein übersichtliches Dashboard im Webbrowser steuern und im Blick behalten.