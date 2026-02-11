# M300 – Services & Cloud Computing

---

## Repository erstellen

1. Auf **www.github.com** anmelden  
2. Auf **Start a project** klicken  
3. Repository Name definieren (z.B. `M300-Services`)  
4. Optional Beschreibung eingeben  
5. **Public** auswählen  
6. Haken bei **Initialize with README** setzen  
7. **Create repository** klicken 


## SSH-Key erstellen (lokal)

```bash
$ ssh-keygen -t rsa -b 4096 -C "beispiel@beispiel.com"
Generating public/private rsa key pair.
Enter a file in which to save the key (~/.ssh/id_rsa): [Press enter]
Enter passphrase (empty for no passphrase): [Passwort]
Enter same passphrase again: [Passwort wiederholen]
```


## SSH-Key dem SSH-Agent hinzufügen

Public Key in die Zwischenablage kopieren:

```bash
$ cat ~/.ssh/id_rsa.pub
```

Den angezeigten Schlüssel komplett kopieren.

---

## SSH-Key bei GitHub hinzufügen

1. Auf **www.github.com** anmelden  
2. Oben rechts auf das Benutzerkonto klicken  
3. **Settings** öffnen  
4. Links auf **SSH and GPG keys** gehen  
5. Auf **New SSH key** klicken  
6. Unter **Title** eine Bezeichnung eingeben (z.B. `M300`)  
7. Den kopierten Key mit **CTRL + V** einfügen  
8. Auf **Add SSH key** klicken  

Der Schlüssel sollte nun in der Liste erscheinen.

![SSH-KEY](images/ssh-key.png)

## Client konfigurieren

Terminal (Bash) öffnen und Git mit den Informationen des GitHub-Accounts konfigurieren:

```bash
git config --global user.name "<username>"
git config --global user.email "<e-mail>"
```

Konfiguration abgeschlossen.

## Repository klonen (Test)

Zu Testzwecken soll ein Repository geklont werden.

Terminal (Bash) öffnen und folgende Befehle ausführen:

```bash
git clone https://gitlab.com/ch-tbz-it/Stud/m300/
cd M300
git pull
git status
```

Beispielausgabe:

```text
Already up to date.

Your branch is up to date with 'origin/master'.
```

Die Statusmeldung zeigt, dass das lokale Repository mit dem Original übereinstimmt.


## Repository herunterladen & aktualisieren (clone/pull)

Terminal (Bash) öffnen.

### Ordner für das Repository erstellen

```bash
cd Wohin/auch/immer
mkdir MeinLokalesRepository
cd MeinLokalesRepository
```

### Repository mit SSH klonen

```bash
git clone git@github.com:<IhrName>/my_M300.git
```

Beispielausgabe:

```text
Cloning into 'my_M300'...
```

### Repository aktualisieren und Status prüfen

```bash
git pull
```

Beispielausgabe:

```text
Already up to date.
```


![Apache](images/apache.png)


# Cloud Computing

## Fragen

### Was versteht man unter Cloud Computing?
Darunter versteht man die Ausführung von Programmen, die nicht auf dem lokalen Rechner installiert sind, sondern auf einem entfernten Rechner laufen und über das Internet aufgerufen werden.

### Was versteht man unter Infrastructure as a Service (IaaS)?
IaaS stellt die unterste Schicht im Cloud Computing dar.  
Der Benutzer greift auf bestehende Infrastruktur wie virtuelle Maschinen, Speicher und Netzwerke zu und verwaltet das Betriebssystem selbst.

### Was ist der Unterschied zur manuellen Installation der VM?
- Automatisierung
- Wiederholbarkeit
- Dokumentation

---

## Vagrant

### Was wird mit Vagrant erzeugt?
Virtuelle Maschinen.

### Welche der Aussagen treffen zu?

a) Vagrant ist ein Hypervisor  
b) Vagrant erzeugt virtuelle Maschinen und unterstützt mehrere Hypervisor und Cloud-Umgebungen (z.B. AWS)  
c) Vagrant erzeugt Container  

**Antwort:**  
**b)**

### In welchen Bereich des Cloud-Computings ist Vagrant einzuordnen?
**IaaS**

### Welche Alternativen zu Vagrant bestehen?
https://alternativeto.net/software/vagrant/

### Wo speichert Vagrant seine Konfiguration?
Im **Vagrantfile**.

### Was bedeutet die Fehlermeldung  
"A Vagrant environment or target machine is required to run this command."?
Man befindet sich im falschen Verzeichnis, in dem kein **Vagrantfile** vorhanden ist.

### Bei welcher LPI-Zertifizierung nützt mir das Vagrant-Wissen?
[DevOps Tools Engineer](https://www.lpi.org/our-certifications/devops-overview)






  ## Cloud Computing

Cloud Computing bedeutet, dass Programme und Daten nicht auf dem eigenen Computer laufen, sondern auf Servern im Internet. Der Zugriff erfolgt über einen Browser oder eine App. Der Anbieter stellt Infrastruktur, Plattformen oder fertige Software bereit.

### Cloud-Modelle

- **IaaS (Infrastructure as a Service)**  
  Der Anbieter stellt virtuelle Server, Speicher und Netzwerk bereit.  
  Der Benutzer verwaltet Betriebssystem und Anwendungen selbst.

- **PaaS (Platform as a Service)**  
  Eine fertige Plattform wird bereitgestellt.  
  Der Entwickler lädt nur noch seine Anwendung hoch, alles andere übernimmt die Cloud.

- **SaaS (Software as a Service)**  
  Fertige Anwendungen über das Internet.  
  Keine Installation oder Wartung notwendig.

- **CaaS (Container as a Service)**  
  Anwendungen laufen in Containern auf der Cloud-Infrastruktur.  
  Beispiele: Docker, Kubernetes.

### Cloud-Arten
- **Public Cloud:** Dienste über das Internet
- **Private Cloud:** innerhalb eines Unternehmens
- **Lokale Virtualisierung:** auf einem einzelnen Rechner

### Vorteile der Cloud
- Schnelle Bereitstellung von Ressourcen
- Automatisierung
- Skalierbarkeit
- Weniger Hardware-Abhängigkeit

---

## Infrastructure as Code (IaC)

Infrastructure as Code bedeutet, dass IT-Infrastruktur über Code definiert und automatisch bereitgestellt wird.  
Statt manueller Einrichtung werden Konfigurationen in Dateien gespeichert und automatisiert ausgeführt.

### Vorteile von IaC
- Wiederholbare Systeme
- Automatisierung
- Schnellere Änderungen
- Einfachere Wiederherstellung

### Typische IaC-Toolarten
- Infrastructure Definition Tools
- Server Configuration Tools
- Package Management Tools
- Scripting Tools
- Versionsverwaltung




## Vagrant

Vagrant ist eine Open-Source-Anwendung zur Erstellung und Verwaltung von virtuellen Maschinen.  
Es verbindet Virtualisierungssoftware wie VirtualBox, VMware oder Hyper-V mit Konfigurations- und Automatisierungstools.

---

### Wichtige Befehle

```bash
vagrant init        # Vagrant-Umgebung erstellen
vagrant up          # VM starten und konfigurieren
vagrant ssh         # Verbindung zur VM herstellen
vagrant status      # Status anzeigen
vagrant port        # Weitergeleitete Ports anzeigen
vagrant halt        # VM stoppen
vagrant destroy     # VM löschen
```

---

### Boxen
Boxen sind vorkonfigurierte virtuelle Maschinen (Vorlagen).

Beispiele:

```bash
vagrant box add ubuntu/xenial64
vagrant box list
vagrant box remove <box-name>
```

---

### VM erstellen

```bash
mkdir myserver
cd myserver
vagrant init ubuntu/xenial64
vagrant up
```

Status anzeigen:

```bash
vagrant status
```

VM aktualisieren:

```bash
vagrant provision
```

VM löschen:

```bash
vagrant destroy -f
```

---

### Vagrantfile (Beispiel)

Die Konfiguration erfolgt im **Vagrantfile**:

```ruby
Vagrant.configure("2") do |config|
  config.vm.box = "bento/ubuntu-16.04"
  config.vm.hostname = "srv-web"
  config.vm.network :forwarded_port, guest: 80, host: 4567
end
```

---

### Provisioning (Beispiel)

Automatische Installation von Software:

```ruby
config.vm.provision :shell, inline: <<-SHELL
  sudo apt-get update
  sudo apt-get -y install apache2
SHELL
```

---

### Provider (Beispiel)

Festlegen der Virtualisierungsplattform:

```ruby
config.vm.provider "virtualbox" do |vb|
  vb.memory = "512"
end
```

---

### Synced Folders

Synchronisierte Ordner verbinden Host und VM:

```ruby
config.vm.synced_folder ".", "/var/www/html"
```

Damit kann z.B. das Webverzeichnis der VM direkt vom Host bearbeitet werden.


## Reflexion

Cloud Computing bedeutet, dass Programme und Daten auf entfernten Servern statt auf dem eigenen Computer laufen. Dadurch können Anwendungen von überall über das Internet genutzt werden.

Dynamische Infrastruktur-Plattformen stellen virtualisierte Ressourcen wie Rechenleistung, Speicher und Netzwerke bereit. Diese werden automatisch verwaltet und meist als virtuelle Maschinen zur Verfügung gestellt.

Damit **Infrastructure as Code (IaC)** eingesetzt werden kann, müssen folgende Voraussetzungen erfüllt sein:

- Infrastruktur ist über Schnittstellen programmierbar
- Ressourcen können schnell erstellt und gelöscht werden
- Nutzer können Systeme selbst verwalten
- Wechsel zwischen Anbietern ist möglich
- Sicherheitsstandards und Zertifizierungen sind gewährleistet


## LB2 – Hands-on

Zuerst habe ich **Git Bash** geöffnet, in mein Arbeitsverzeichnis gewechselt und mit folgenden Befehlen eine neue VM erstellt:

```bash
mkdir myvm
cd myvm
vagrant init
vagrant up
```

![MyVM-Erstellung](images/myvm_erstellung.png)

  Die VM hat sich während der Einrichtung aufgehängt und ich konnte nicht weiterarbeiten.  
Mit folgendem Befehl konnte das Problem behoben werden:

```bash
vagrant reload --provision
```
![Problem gelöst](images/vagrant-reload.png)

Danach war eine Verbindung per SSH wieder möglich:

```bash
vagrant ssh
```
![ssh](<images/vagrant ssh.png>)



 Anschliessend musste ich die Serverdienste installieren.  
Zuerst habe ich **Apache** installiert. Wichtig ist die Option `-y`, damit die Installation automatisch bestätigt wird:

```bash
sudo apt-get update
sudo apt-get -y install apache2
```

![Apache2](images/apache2.png)

  Anschliessend habe ich den **Webalizer** installiert:

```bash
sudo apt-get -y install webalizer
```

![webalizer](images/webalizer.png)
  
  Danach habe ich den Befehlsverlauf angezeigt:

```bash
history
```

![verlauf](images/image.png)


  ## Feintuning

Damit der **Webalizer** Daten auswerten kann, musste zuerst etwas Traffic erzeugt werden.  
Dazu habe ich folgende Befehle ausgeführt:

```bash
curl http://localhost
curl http://localhost
curl http://localhost
```

![Traffic](<images/Traffic webalizer.png>)

  Als Nächstes musste ich die **Access-Logs von Apache rotieren**, da der Webalizer nur Archivdaten auswerten kann:

```bash
sudo logrotate -f /etc/logrotate.d/apache2
```

![Logs](images/logs-rotate-webanalizer.png)

  Danach habe ich das **Output-Verzeichnis korrigiert** und anschliessend eine Webalizer-Ausgabe erzeugt:

```bash
sudo webalizer
```
![Ausgabe](images/webalizer-ausgabe.png)

  Zum Schluss habe ich die Auswertung in der **Web-Ansicht** geöffnet:

![Web](images/webalizer2.png)



## 25 – Sicherheit (Fragen)

### Was ist der Unterschied zwischen einem Webserver und einem Reverse Proxy?
Ein Webserver liefert HTML-Seiten direkt an den Benutzer.  
Ein Reverse Proxy steht davor und leitet die Anfragen an den eigentlichen Webserver weiter.

### Was versteht man unter einer White List?
Eine White List enthält vertrauenswürdige Elemente, während eine Black List unerwünschte Elemente sperrt.

### Was wäre die Alternative zum Absichern einzelner Server mit einer Firewall?
Eine **zentrale Firewall**.

### Was ist der Unterschied zwischen der Datei `id_rsa` und `id_rsa.pub`?
- `id_rsa` → Private Key  
- `id_rsa.pub` → Public Key  

### Wo darf ein SSH-Tunnel nicht angewendet werden?
Innerhalb der Firma (gemäss Sicherheitsrichtlinien).

### Wozu dient die Datei `authorized_keys`?
Sie enthält die öffentlichen Schlüssel der Benutzer, die sich ohne Passwort am System anmelden dürfen.

### Wozu dient die Datei `known_hosts`?
Sie speichert die öffentlichen Schlüssel von Servern, mit denen man sich per SSH verbunden hat.  
So kann das System prüfen, ob der Server derselbe ist wie beim letzten Verbindungsaufbau und vor Man-in-the-Middle-Angriffen warnen.

## 25 – Sicherheit (Umsetzung)

### Firewall & Reverse Proxy
Steht eine VM direkt im Internet, sind alle Dienste offen zugänglich und damit unsicher.  
Eine **Firewall** blockiert unerwünschte Verbindungen, während ein **Reverse Proxy** Anfragen weiterleitet, ohne die echte Serveradresse preiszugeben.

---

### UFW Firewall
UFW (Uncomplicated Firewall) ist ein einfaches Kommandozeilen-Tool zur Konfiguration der Linux-Firewall.  
Es dient als benutzerfreundliche Oberfläche für das komplexere System **iptables**.

### Installation und Aktivierung

```bash
sudo apt-get install ufw
sudo ufw enable
```
    
  ![UFW Installieren](<images/ufw install.png>)
  ![UFW aktivieren](<images/ufw enable.png>)



### SSH-Port freigeben

Damit ich mich später nicht selbst aussperre, musste der **SSH-Port** in der Firewall freigegeben werden:

```bash
sudo ufw allow ssh
```
  ![SSH erlauben](<images/ssh erlauben.png>)


### Firewall-Regeln konfigurieren

Anschliessend habe ich die **Firewall-Regeln überprüft und konfiguriert**:

```bash
sudo ufw status
```  
  ![Status Ports](<images/fw ports status.png>)



### Reverse Proxy

Hier habe ich **Apache als Reverse Proxy** installiert.

Zuerst mussten die benötigten Pakete installiert werden.  
Wichtig: Die entsprechenden Ports müssen vorher in der Firewall freigegeben werden, sonst kommt es zu einem Installationsfehler (ist mir passiert).

```bash
sudo apt-get install apache2
```
![Fehler](images/fehler.png)
















