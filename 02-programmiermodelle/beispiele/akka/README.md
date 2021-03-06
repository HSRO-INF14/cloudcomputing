# Übung: Functional Reactive Programming mit akka

## Vorbereitung
1. Holen sie sich die Vorlage zur Übung aus dem github Repository der Vorlesung (entweder indem sie sich das gesamte Repository als ZIP-Datei herunterladen oder per Befehl `git clone https://github.com/adersberger/cloudcomputing.git`).
2. Öffnen sie in Netbeans das Vorlagen-Verzeichnis der Übung als Projekt.
3. Führen Sie das Maven Goal `clean package` aus.

## Ziel
Das Ziel der heutigen Übung ist es, einen Service für Zwitscher zu erstellen, mit dem Nachrichten der New York Times und Artikel aus Wikipedia zu einem Suchwort extrahiert werden können.

![Ziel](ziel.png)

## Aufgaben
### Aufgabe 1: Den Code in der Vorlage sichten
In der Vorlage sind die Connectoren zu finden (Paket `connectors`), mit denen Wikipedia und NY-Times aufgerufen werden kann (synchron). Ferner existieren Vorlagen zu allen notwendigen Aktoren (Paket `actors`). Dabei stehen zwei Klassen mit `main()`-Methoden zur Verfügung: `Mai`n nutzt die Connectoren direkt und sequenziell. `MainWithActors` nutzt das Aktorensystem, um die Ergebnisse zu ermitteln. Die jeweiligen Aktoren nutzen dann intern jeweils auch wieder die Connectoren. Ferner ist noch eine Konfigurationsdatei für akka hinterlegt (`application.conf`), die die Log-Ausgaben konfiguriert.

Machen sie ausgehend von den Main-Klassen einen Rundgang durch den Code und erschließen sie sich das definierte Aktorensystem dadurch. Nutzen sie bei Bedarf die akka Online-Dokumentation bei Verständnisproblemen. Lassen sie die sequentielle Variante (`Main`) einmal laufen und notieren sie sich die dabei gemessene Laufzeit (siehe Konsolenausgabe).

### Aufgabe 2: Das Aktorensystem lauffähig machen
Füllen sie die Lücken im Aktor-System. Gehen sie dazu durch den Code und füllen sie alle Code-Stellen, an denen ein `TODO` als Kommentar hinterlegt ist. Führen sie das Aktorensystem aus (`MainWithActors`) und vergleichen sie die Laufzeit mit der sequenziellen Variante.

### Aufgabe 3 (Kür): Das Aktorensystem in Dropwizard integrieren
Falls sie schnell durch die vorherigen Übungen gekommen sind, so können sie noch einen Schritt weiter gehen: Den Code, der bisher nur aus den `Main`-Klassen angestoßen wird, in den Code der Übung zu REST auf Basis von Dropwizard integrieren. Sie müssen dazu das Aktorensystem bei der Initialisierung der Dropwizard-Applikation erzeugen und dann eine REST-Schnittstelle entwerfen, die einen Request an das Aktorensystem delegiert und die Ergebnisse nach Außen reicht.
