# Praxisarbeit – HFSNT.F.6.11-BE-S2411-DBWE.IA1A.PA

## Anleitung zum Starten der Applikation auf der lokalen Umgebung

### Starten mit Docker

Um das Repository zu klonen, verwenden Sie den entsprechenden Befehl und navigieren anschließend im Terminal bzw. der Kommandozeile zum geklonten Verzeichnis. Starten Sie die Docker-Services mit folgendem Befehl:
```shell
docker compose up -d
```
Hinweis: Die Applikation wird im Hintergrund gestartet, sodass sie nicht direkt in der Konsole ausgeführt wird. Möchten Sie die Applikation jedoch in der Konsole starten, lassen Sie den -d-Schalter weg und führen Sie den folgenden Befehl aus: `docker compose up`.

Um die Applikation wieder zu beenden, verwenden Sie den folgenden Befehl:
```shell
docker compose down
```
Wenn die Applikation ohne den -d-Schalter ausgeführt wurde, können Sie sie durch Drücken von CTRL + C auf Windows/Linux oder CMD + C auf macOS beenden.

### Starten auf Windows

Falls die Applikation ohne Docker-Unterstützung gestartet werden soll, führen Sie die folgenden Schritte in der Kommandozeile aus. Stellen Sie sicher, dass Sie sich im Ordner des geklonten Repositorys befinden. Es wird vorausgesetzt, dass Sie [Python Version 3](https://www.python.org/downloads/) sowie [virtualenv](https://pypi.org/project/virtualenv/) auf Ihrem System installiert haben.

1. Erstellen Sie ein virtuelles Python-Environment:
   ```shell
   virtualenv venv
   ```

2. Aktivieren Sie das virtuelle Environment:
   - Für die Kommandozeile:
     ```shell
     .\venv\Scripts\activate.bat
     ```
   - Für PowerShell:
     ```shell
     .\venv\Scripts\activate.ps1
     ```

3. Installieren Sie die notwendigen Abhängigkeiten:
   ```shell
   pip3 install -r requirements.txt
   ```

4. Initialisieren Sie die Datenbank:
   ```shell
   flask db init
   ```

5. Erstellen Sie die Migrationen:
   ```shell
   flask db migrate -m "Initialize database"
   ```

6. Wenden Sie die Migrationen an:
   ```shell
   flask db upgrade
   ```

7. Setzen Sie die Umgebungsvariable für die Flask-Applikation:
   ```shell
   set FLASK_APP=zeitverwaltung.py
   ```

8. Starten Sie die Flask-Applikation:
   ```shell
   flask run
   ```

Nach der Ausführung dieser Befehle sollte die Applikation lokal verfügbar sein und über den Webbrowser zugänglich gemacht werden.

### Starten auf macOS oder Linux

Um die Applikation zu starten, führen Sie die folgenden Schritte im Terminal aus. Stellen Sie sicher, dass Sie sich im Ordner des geklonten Repositorys befinden. Es wird vorausgesetzt, dass [Python Version 3](https://www.python.org/downloads/) und [virtualenv](https://pypi.org/project/virtualenv/) bereits auf Ihrem System installiert sind.

1. Erstellen Sie ein virtuelles Python-Environment:
   ```shell
   virtualenv venv
   ```

2. Aktivieren Sie das virtuelle Environment:
   ```shell
   source ./venv/bin/activate
   ```

3. Installieren Sie die benötigten Abhängigkeiten:
   ```shell
   pip3 install -r requirements.txt
   ```

4. Initialisieren Sie die Datenbank:
   ```shell
   flask db init
   ```

5. Erstellen Sie die Migrationen:
   ```shell
   flask db migrate -m "Initialize database"
   ```

6. Wenden Sie die Migrationen an:
   ```shell
   flask db upgrade
   ```

7. Setzen Sie die Umgebungsvariable für die Flask-Applikation:
   ```shell
   export FLASK_APP=zeitverwaltung.py
   ```

8. Starten Sie die Flask-Applikation:
   ```shell
   flask run
   ```

Nach der Ausführung dieser Befehle sollte die Applikation lokal laufen und im Webbrowser zugänglich sein.

## Allgemeine Informationen

Dieses Repository enthält eine Webapplikation, die mit dem Python-basierten Flask-Framework entwickelt wurde und eine Anbindung an die relationale Datenbank MariaDB integriert. Die Applikation wurde vollständig von mir entwickelt, wobei einige Komponenten, insbesondere die Struktur der Verzeichnisse sowie der Registrierungs- und Login-Mechanismus, aus dem [Microblog](https://github.com/miguelgrinberg/microblog) von Miguel Grinberg übernommen wurden. Diese Vorlagen dienten als Ausgangspunkt und wurden entsprechend den spezifischen Anforderungen der Applikation weiter modifiziert und optimiert.

### Was ist Time Management?

Time Management ist eine benutzerfreundliche Webapplikation, die es den Nutzern ermöglicht, ihre geleisteten Arbeitsstunden präzise zu erfassen und zu verwalten. Nach der erfolgreichen Registrierung und dem Login haben die Nutzer *ausschließlich* Zugriff auf ihre eigenen Daten, was eine hohe Datensicherheit und Privatsphäre gewährleistet.  

Die Applikation ermöglicht es den Nutzern, für jeden Arbeitstag *einen Zeiteintrag* zu erstellen, in dem die geleisteten Stunden dokumentiert werden. Zusätzlich besteht die Möglichkeit, für jeden Eintrag einen optionalen Kommentar hinzuzufügen, um etwaige spezifische Details zu vermerken. Die erfassten Stunden können jederzeit eingesehen, bearbeitet oder – falls erforderlich – gelöscht werden.  

In der Profilübersicht werden nicht nur die persönlichen Daten des Nutzers angezeigt, sondern auch die insgesamt geleisteten Arbeitsstunden. Weiterhin haben die Nutzer die Möglichkeit, ihren aktuellen Stand in Bezug auf Über- oder Minusstunden (Flextime) zu überprüfen, um ihre Arbeitszeit flexibel und effizient zu verwalten.

### Quellen

Bestimmte Teile der Applikation wurden entweder inspiriert oder direkt aus dem [MicroBlog](https://github.com/miguelgrinberg/microblog) von Miguel Grinberg übernommen. Diese Komponenten, insbesondere die Struktur der Verzeichnisse sowie der Registrierungs- und Login-Mechanismus, dienten als Grundlage und wurden an die spezifischen Anforderungen der eigenen Webapplikation angepasst.

## Technologien & Bibliotheken

Für die Entwicklung der Webanwendung wurden die folgenden Technologien und Bibliotheken verwendet:

- **Programmiersprache**: [Python](https://www.python.org/) – Die Hauptsprache für die Backend-Entwicklung.
- **Web-Framework**: [Flask](https://flask.palletsprojects.com/en/2.2.x/) – Ein leichtgewichtiges Web-Framework, das für die schnelle Entwicklung von Webanwendungen optimiert ist.
- **Datenbanksystem**: [MariaDB](https://mariadb.org/) – Eine relationale Open-Source-Datenbank, die für die Verwaltung der Benutzer- und Arbeitsstundendaten verantwortlich ist.
- **Containerisierung**: [Docker und docker-compose](https://www.docker.com/) – Ermöglicht die Erstellung, Bereitstellung und Verwaltung von Containern zur Isolierung und Skalierung der Anwendung.
- **Rendering der Webseiten**: [Jinja2](https://jinja.palletsprojects.com/en/3.1.x/) – Ein Templating-Engine, die für die dynamische Generierung von HTML-Seiten verwendet wird.
- **Styling-Bibliothek**: [Bootstrap](https://getbootstrap.com/) – Ein Framework für die Entwicklung responsiver und ansprechender Benutzeroberflächen.
- **Benutzte Icons**: [FontAwesome](https://fontawesome.com/) – Eine Icon-Bibliothek, die in der Anwendung für die visuelle Darstellung von Funktionen und Aktionen genutzt wird.

### Erreichbarkeit im Internet

Die Webapplikation ist für eine geraume Zeit öffentlich im Internet erreichbar unter der URL [http://136.244.87.119:5000/](http://136.244.87.119:5000/).

### Repository vom Source Code

Der komplette Code befindet sich öffentlich zugänglich auf GitHub unter folgendem Repository: [https://github.com/FuatHacilar/DBWE](https://github.com/FuatHacilar/DBWE)

## WebAPI

Die WebAPI stellt eine Schnittstelle zur Verfügung, über die HTTP-Anfragen an den Webserver gesendet werden können, um verschiedene Datenoperationen durchzuführen. Die Webapplikation bietet derzeit API-Endpunkte für die folgenden Szenarien:

- Erstellen und Bearbeiten von Nutzerdaten
- Erstellen und Löschen von Authentifizierungstokens
- Abrufen aller erfassten Arbeitsstunden
- Erstellen, Bearbeiten, Abrufen und Löschen von erfassten Arbeitsstunden

Diese APIs sind unter den folgenden Pfaden erreichbar:
- `/api/users` – für Operationen im Zusammenhang mit Nutzerdaten
- `/api/working-hours` – für das Verwalten von Arbeitsstunden
- `/api/tokens` – für die Verwaltung von Authentifizierungstokens

### Token API

#### Neuen Token erstellen

Base-Auth: `<USERNAME>:<PASSWORD>`
> Die Authentifizierungsdaten werden in der URL mitgegeben. Beispielsweise: `https://<USERNAME>:<PASSWORD>http://136.244.87.119:5000/api/tokens`

Pfad: `/api/tokens`

Methode: `POST`

Dieses Beispiel als `curl` Kommando:
```shell
curl http://TestUser:TestPasswort@136.244.87.119:5000/api/tokens -X POST
```

#### Token wiederrufen bzw. löschen

Pfad: `/api/tokens`

Methode: `DELETE`

Authorization im Header: `Authorization: Bearer <TOKEN>`
> Ersetzen Sie `<TOKEN>` durch Ihren eigenen Token.

Dieses Beispiel als `curl` Kommando:
```shell
curl http://136.244.87.119:5000/api/tokens -X DELETE -H "Authorization: Bearer 1ZTtkbEocxOMPd4VdN1n7dBwZXtmoCRT"
```


### Users API

#### Erstellen eines neuen Nutzers

Pfad: `/api/users`

Methode: `POST`

Content-Type im Header: `Content-Type: application/json`

Body als JSON:
```json
{
  "username": "TestUser",
  "email": "test@test.com",
  "password": "TestPassword",
  "company": "TEST",
  "job": "TEST",
  "target_time": 24
}
```
> Ersetzen Sie die Beispielwerte im JSON mit Ihren eigenen.

Dieses Beispiel als `curl` Kommando:
```shell
curl http://136.244.87.119:5000/api/users -X POST -H "Content-Type: application/json" -d "{\"username\": \"TestUser\", \"email\": \"test@test.com\", \"password\": \"TestPassword\", \"company\": \"TEST\", \"job\": \"TEST\", \"target_time\": 24}"
```

#### Auslesen des Nutzer-Profils

Pfad: `/api/users`

Methode: `GET`

Authorization im Header: `Authorization: Bearer <TOKEN>`
> Ersetzen Sie `<TOKEN>` durch Ihren eigenen Token.

Dieses Beispiel als `curl` Kommando:
```shell
curl http://136.244.87.119:5000/api/users -H "Authorization: Bearer 1ZTtkbEocxOMPd4VdN1n7dBwZXtmoCRT"
```

#### Bearbeiten des Nutzer-Profils

Pfad: `/api/users`

Methode: `PUT`

Content-Type im Header: `Content-Type: application/json`

Authorization im Header: `Authorization: Bearer <TOKEN>`
> Ersetzen Sie `<TOKEN>` durch Ihren eigenen Token.

Body als JSON:
```json
{
  "username": "TestUser",
  "email": "test@test.com",
  "password": "TestPassword",
  "company": "TEST",
  "job": "TEST",
  "target_time": 24
}
```
> Ersetzen Sie die Beispielwerte im JSON mit Ihren eigenen. Es müssen nicht alle Werte mitgegeben werden, nur jene, 
> welche geändert werden sollen.

Dieses Beispiel als `curl` Kommando:
```shell
curl http://136.244.87.119:5000/api/users -X PUT -H "Authorization: Bearer 1ZTtkbEocxOMPd4VdN1n7dBwZXtmoCRT" -H "Content-Type: application/json" -d "{\"company\":\"TEST\", \"job\":\"TEST\"}"
```

### Arbeitsstunden API

#### Erfassen neuer Arbeitsstunden

Pfad: `/api/working-hours`

Methode: `POST`

Content-Type im Header: `Content-Type: application/json`

Authorization im Header: `Authorization: Bearer <TOKEN>`
> Ersetzen Sie `<TOKEN>` durch Ihren eigenen Token.

Body als JSON:
```json
{
  "date": "2024-09-02",
  "working_hours": 8.4,
  "comment": "Time Management Flask Applikation"
}
```
> Ersetzen Sie die Beispielwerte im JSON mit Ihren eigenen.
> Beachten Sie, dass das Datum im Format YYYY-MM-DD mitgegeben werden muss.

Dieses Beispiel als `curl` Kommando:
```shell
curl http://136.244.87.119:5000/api/working-hours -X POST -H "Authorization: Bearer 1ZTtkbEocxOMPd4VdN1n7dBwZXtmoCRT" -H "Content-Type: application/json" -d "{\"date\":\"2024-09-02\",\"working_hours\":\"8.4\",\"comment\":\"Time Management Flask Applikation\"}"
```

#### Auslesen aller bereits erfassen Arbeitsstunden

Pfad: `/api/working-hours`

Methode: `GET`

Authorization im Header: `Authorization: Bearer <TOKEN>`
> Ersetzen Sie `<TOKEN>` durch Ihren eigenen Token.

Dieses Beispiel als `curl` Kommando:
```shell
curl http://136.244.87.119:5000/api/working-hours -H "Authorization: Bearer 1ZTtkbEocxOMPd4VdN1n7dBwZXtmoCRT"
```

#### Auslesen einer bestimmten erfassten Arbeitsstunden mit dem ID

Pfad: `/api/working-hours/<ID>`
> Hier `<ID>` durch die ID der erfassten Arbeitsstunden ersetzen. Diese ID kann man herausfinden, indem man alle Einträge der 
> Arbeitsstunden lädt und die ID ausliest.

Methode: `GET`

Authorization im Header: `Authorization: Bearer <TOKEN>`
> Ersetzen Sie `<TOKEN>` durch Ihren eigenen Token.

Dieses Beispiel als `curl` Kommando:
```shell
curl http://136.244.87.119:5000/api/working-hours/1 -H "Authorization: Bearer 1ZTtkbEocxOMPd4VdN1n7dBwZXtmoCRT"
```

#### Bearbeiten einer bestimmten erfassten Arbeitsstunden

Pfad: `/api/working-hours/<ID>`
> Hier `<ID>` durch die ID der erfassten Arbeitsstunden ersetzen. Diese ID kann man herausfinden, indem man alle Einträge der
> Arbeitsstunden lädt und die ID ausliest.

Methode: `PUT`

Content-Type im Header: `Content-Type: application/json`

Authorization im Header: `Authorization: Bearer <TOKEN>`
> Ersetzen Sie `<TOKEN>` durch Ihren eigenen Token.

Body als JSON:
```json
{
  "working_hours": 9,
  "comment": "Time Management Dokumentation"
}
```
> Ersetzen Sie die Beispielwerte im JSON mit Ihren eigenen. Es kann nur der Kommentar bzw. die geleistete Arbeitsstunden bearbeitet werden.

Dieses Beispiel als `curl` Kommando:
```shell
curl http://136.244.87.119:5000/api/working-hours/1 -X PUT -H "Authorization: Bearer 1ZTtkbEocxOMPd4VdN1n7dBwZXtmoCRT" -H "Content-Type: application/json" -d "{\"working_hours\":9,\"comment\":\"Time Management Dokumentation\"}"
```

#### Löschen einer bestimmten erfassten Arbeitsstunden

Pfad: `/api/working-hours/<ID>`
> Hier `<ID>` durch die ID der erfassten Arbeitsstunden ersetzen. Diese ID kann man herausfinden, indem man alle Einträge der
> Arbeitsstunden lädt und die ID ausliest.

Methode: `DELETE`

Authorization im Header: `Authorization: Bearer <TOKEN>`
> Ersetzen Sie `<TOKEN>` durch Ihren eigenen Token.

Dieses Beispiel als `curl` Kommando:
```shell
curl http://136.244.87.119:5000/api/working-hours/1 -X DELETE -H "Authorization: Bearer 1ZTtkbEocxOMPd4VdN1n7dBwZXtmoCRT"
```
