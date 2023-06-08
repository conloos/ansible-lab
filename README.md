## Ansible Lab

Dieses Repository wird genutzt um ein kleines Demo-LAB für das Ansible Flottenmanagement zu erstellen.
  
### Installation von Docker and Docker-Compose

Für dieses Lab wird Docker und Docker Compose benötigt. Als Zielplattform nutzen Sie bitte Linux - empfohlen wird debian oder ubuntu. Sollten Sie Windows nutzen, wird eine belibige Desktopvirtualisierung empfohlen.

### Installation von Docker and Docker-Compose

Bitte installieren Sie die neuste Version von Docker:

* https://docs.docker.com/engine/install/ubuntu/

Bitte installieren Sie ebenfalls die neueste Version von Docker Compose, epfohlen wird pip zu nutzen.

* https://pypi.org/project/docker-compose/

### Weitere Voraussetzungen

Die weiteren Programme sind notwendig:

* git
* IDE (empfohlen VSCode)


### Download und Kurs-Vorbereitung

Bitte clonen Sie das nachfolgende Repository:

```
$ git clone https://github.com/conloos/ansible-lab.git
```

### Start des LABs

Bitte wechseln Sie in das LAB und starten Sie wie nachfolgend beschrieben die Docker Container.

```
$ docker-compose up
```

Anschließend können Sie sich mit VSCode und dem remote-explorer (ssh) verbinden.

### Credentials

**Ubuntu-controller**
* User: ubuntu
* Passwort: pass 

### Fehler
Sollten Fehler auftreten, bitte die Container entfernen und noch einmal instanziieren.
```
$ docker-compose down --remove-orphans
$ docker system prune -a
```
