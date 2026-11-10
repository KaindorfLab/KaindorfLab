# KaindorfLab
 
Schulserver auf Proxmox für alle IT-Klassen der HTBLA Kaindorf. Jeder Schüler bekommt einen eigenen, isolierten Container, in dem er root ist und frei arbeiten kann: programmieren, Docker nutzen, Services hosten und Cybersecurity üben. Fehler betreffen nur den eigenen Container, nie andere Schüler.
 
## Warum KaindorfLab?
 
- Schüler brauchen Rechte zum Experimentieren (Software installieren, Services starten, Netzwerk testen)
- Auf einem gemeinsamen Server wäre das ein Sicherheits- und Rechteproblem
- Mit einem eigenen Container pro Schüler gibt es dieses Problem nicht: jeder hat root, aber nur in seiner eigenen Umgebung
- Durch Automatisierung bleibt der Aufwand für die Admins gering
## Rollen
 
| Rolle | Aufgaben |
|---|---|
| **Schüler** | Arbeitet im eigenen Container (root), startet Services, setzt den Container bei Fehlern zurück |
| **Admin** | Verwaltet Server, Vorlagen und Klassen, sieht im Dashboard alle Container und Services |
 
## Funktionen
 
### Bereitstellung
- Eine Vorlage (Template) mit OS, Docker, OpenSSH-Server und Basis-Tools
- Container werden pro Klasse automatisch aus der Vorlage erstellt
- Am Schuljahresende können Container archiviert oder gelöscht werden
### Arbeiten im eigenen Container
- Root-Rechte im eigenen Container
- Zugriff per SSH oder Proxmox-Konsole im Browser
- Zugriff von zu Hause per VPN
- Docker ist vorinstalliert
- Zurücksetzen auf den Ausgangszustand per Snapshot, eigene Snapshots möglich
### Isolation und Schutz vor Missbrauch
- Schüler sehen und bedienen nur den eigenen Container
- Kein Zugriff auf die Proxmox-Verwaltung
- Limits für CPU, RAM, Speicher und Netzwerk pro Container
- Ausgehender Traffic wird begrenzt und / oder protokolliert
- (optional) Nutzungsordnung mit klaren Regeln, die jeder Schüler bestätigt
### Admin-Dashboard
- Übersicht aller Klassen und Container mit Status (läuft / gestoppt)
- Anzeige der laufenden Services pro Container (Name, Port, Status)
- Anzeige der Auslastung (CPU, RAM, Speicher)
- Geschützter Login
Jeder Container meldet seine Services über einen kleinen Agenten automatisch an eine zentrale API, die das Dashboard mit Daten versorgt.
 
### Betrieb
- Warnungen bei Speicherplatzmangel oder Serverausfall
