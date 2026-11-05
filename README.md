# 🎲 Spieltisch für Dungeons & Dragons

Ein eigener, deutschsprachiger Online-Spieltisch für unsere D&D-Runde. Er läuft komplett im Browser: Spieler brauchen **kein Konto**, nichts installieren und keinen Server, nur einen Link und das Passwort.

**Spieltisch öffnen:** https://thebeardedbatman.github.io/Spieltisch-Dungeons-and-Dragons/

---

## Was der Spieltisch kann

| Bereich | Funktionen |
|---|---|
| **Karte** | Eigene Kartenbilder hochladen, Raster mit einstellbarer Spaltenzahl und Versatz, vier Linienstile (gut sichtbar, sehr kräftig, dunkel, fein), Raster ein- und ausblendbar, Zoom |
| **Nebel des Krieges** | Aufdecken und Verdecken mit Pinsel (1 Feld, 3×3, 5×5), Spieleransicht zur Kontrolle. Figuren im Nebel sind für Spieler unsichtbar |
| **Figuren** | Helden, Gegner und Nebenfiguren mit Bildern, Größen von klein bis gigantisch (4×4), TP-Verwaltung, „Am Zug“-Markierung, versteckte Figuren für Hinterhalte, eigene Bilder per Klick |
| **Szenen** | Beliebig viele vorbereitete Szenen, sortiert nach Abenteuer. Der Spielleiter bestimmt, welche Szene die Spieler sehen |
| **Würfel** | W4 bis W100, Vorteil und Nachteil, gemeinsames Würfelprotokoll für alle |
| **Musik** | YouTube-Titel und -Playlists oder eigene MP3-Dateien, synchron für alle Spieler, ohne Discord-Bot |
| **Regeln** | Kurzregeln zum Nachschlagen, auch für die Spieler |
| **Themes** | Passende Optik je Abenteuer: Standard, „Die letzte Rasur“, „Der Bart des Drachen“, „Kurs auf Nimmerfels“. Effekte lassen sich abschalten |

---

## So wird gespielt

### Als Spielleiter
1. Die Adresse oben **ohne Zusatz** öffnen. Wer sie so öffnet, ist automatisch Spielleiter.
2. Im Reiter **„Szenen“** ein Passwort festlegen.
3. Oben rechts auf **„Spieler-Link kopieren“** klicken. Der Link endet auf `?tisch=…` und bleibt immer gleich.
4. Link und Passwort **getrennt** an die Spieler schicken.
5. **Das Fenster während des Spiels offen lassen.** Die Spieler verbinden sich direkt mit dem Browser des Spielleiters.

> Den Spielleiter-Zugang immer nur auf **einem** Gerät gleichzeitig öffnen.

### Als Spieler
1. Den Link vom Spielleiter öffnen und das Passwort eingeben.
2. Oben rechts bei **„Ich spiele“** den eigenen Helden wählen.
3. Fertig. Die eigene Figur lässt sich ziehen, gewürfelt wird im Reiter „Würfel“.

Funktioniert auf dem PC, dem Tablet und dem Handy.

---

## Technik in Kürze

- **Eine einzige Datei:** `index.html` enthält die ganze Anwendung. Dazu kommt `peerjs.min.js` für die Verbindung.
- **Peer-to-Peer:** Der Browser des Spielleiters ist der „Tisch“. Die Spieler verbinden sich über [PeerJS](https://peerjs.com/) (WebRTC) direkt mit ihm. Es gibt keinen eigenen Server und keine Datenbank.
- **Spielleiter entscheidet:** Nur der Spielleiter-Browser speichert den Spielstand. Spieler können nur ihre eigene Figur bewegen. Versteckte Figuren, Trefferpunkte und Bilder bekommen sie gar nicht erst geschickt bzw. erst nach dem Passwort.
- **Speicher:** Szenen, Karten, Bilder und Musik liegen im Browser des Spielleiters (IndexedDB), nicht auf GitHub.

---

## Daten und Sicherung

Was im Spieltisch eingerichtet wird, liegt **nur im Browser** des Spielleiters, nicht in diesem Repository.

- **Sichern:** Reiter „Szenen“ → **„Sichern“** lädt eine Datei mit Szenen, Karten, Bildern, Tisch-Code, Passwort, Theme und Musikliste herunter (MP3-Dateien sind nicht enthalten).
- **Laden:** Dieselbe Datei über **„Laden“** einspielen, zum Beispiel auf einem anderen Rechner oder nach dem Löschen der Browserdaten. Danach stimmt auch der Spieler-Link wieder.
- **Figurenbilder:** Die Bilder der Helden und Figuren kommen aus einer separaten Datei `Heldenbilder.json`. Sie wird **nicht** hier hochgeladen, sondern einmalig im Spieltisch über „Laden“ eingespielt. So bleiben die Bilder hinter dem Passwort.

> Eine neue `index.html` hochzuladen ändert **nichts** an Szenen, Bildern, Tisch-Code oder Spieler-Link.

---

## Aktualisieren

1. Hier im Repository: **„Add file“ → „Upload files“** → neue `index.html` hineinziehen → **„Commit changes“**.
2. Unter **„Actions“** warten, bis der grüne Haken erscheint (ca. 1 Minute).
3. Im Spieltisch **Strg + F5** drücken.

**Tipp für Firefox:** Klappt das Hochladen nicht (Fehler 400), den „Verbesserten Schutz vor Aktivitätenverfolgung“ für github.com ausschalten.

---

## Dateien

| Datei | Inhalt |
|---|---|
| `index.html` | Der komplette Spieltisch |
| `peerjs.min.js` | PeerJS 1.5.4 für die Verbindung zwischen den Browsern |
| `peerjs-LICENSE.txt` | Lizenz von PeerJS (MIT) |
| `README.md` | Diese Beschreibung |

---

## Danksagung

- [PeerJS](https://peerjs.com/) für die einfache WebRTC-Verbindung (MIT-Lizenz)
- Musikvorschläge von [Tabletop Audio](https://tabletopaudio.com/)
- Dungeons & Dragons ist eine Marke von Wizards of the Coast. Dies ist ein privates Fanprojekt ohne Verbindung zu Wizards of the Coast.

Erstellt von **Sebastian Preuß** ([thebeardedbatman](https://github.com/thebeardedbatman)) für die Runde der *Bearded Bad Boys*. 🧔‍♂️⚔️
