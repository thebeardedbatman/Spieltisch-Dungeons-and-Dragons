# 🎲 Spieltisch für Dungeons & Dragons

Ein eigener, deutschsprachiger Online-Spieltisch für unsere D&D-Runde. Er läuft komplett im Browser: Spieler brauchen **kein Konto**, nichts installieren und keinen eigenen Server, nur einen Link und das Passwort.

**Unser Zuhause:** https://baertiges-pen-and-paper-online.de mit Startseite, Mitgliederbereich, Terminen und dem Spieltisch unter `/tisch/`.

**Ausweich-Tisch hier bei GitHub:** https://thebeardedbatman.github.io/Spieltisch-Dungeons-and-Dragons/

---

## Was der Spieltisch kann

| Bereich | Funktionen |
|---|---|
| **Karte** | Eigene Kartenbilder hochladen, Raster mit einstellbarer Spaltenzahl und Versatz, vier Linienstile (gut sichtbar, sehr kräftig, dunkel, fein), Raster jederzeit ein- und ausblendbar, Zoom |
| **Nebel des Krieges** | Aufdecken und Verdecken mit Pinsel (1 Feld, 3×3, 5×5), Spieleransicht zur Kontrolle. Figuren im Nebel sind für Spieler unsichtbar |
| **Figuren** | Helden, Gegner und Nebenfiguren mit Bildern, Größen von klein bis gigantisch (4×4), TP-Verwaltung, „Am Zug“-Markierung, versteckte Figuren für Hinterhalte, eigene Bilder per Klick („Eigenes Bild“). Fertige Knöpfe für die Gegner jedes Abenteuers, Mehrfach-Gegner werden automatisch nummeriert |
| **Reittiere** | Dragooner reitet seine Wolfshündin Luna: Der Spieler darf beide Figuren ziehen |
| **Szenen** | Beliebig viele vorbereitete Szenen, jede einem Abenteuer zugeordnet. Der Spielleiter bestimmt, welche Szene die Spieler sehen |
| **Würfel** | W4 bis W100, Vorteil und Nachteil, gemeinsames Würfelprotokoll für alle |
| **Musik** | YouTube-Titel und -Playlists oder eigene MP3-Dateien, synchron für alle Spieler, ohne Discord-Bot. MP3s lassen sich vorab an die Spieler senden |
| **Regeln** | Kurzregeln zum Nachschlagen, auch für die Spieler |
| **Themes** | Passende Optik je Abenteuer: Standard, „Die letzte Rasur“, „Der Bart des Drachen“, „Kurs auf Nimmerfels“. Wird ein Abenteuer gewählt, schaltet das Thema automatisch um, von Hand bleibt es jederzeit änderbar. Effekte lassen sich abschalten |
| **Zurück zur Startseite** | Läuft der Tisch auf unserer Seite, führt „← Zum Portal“ zurück. Das öffnet einen neuen Tab, die Verbindung am Tisch bleibt bestehen |

---

## So wird gespielt

### Als Spielleiter
1. Den Tisch **ohne Zusatz** öffnen, auf unserer Seite über **„Zum Tisch“** im Menü. Wer ihn so öffnet, ist automatisch Spielleiter.
2. Im Reiter **„Szenen“** oben das Abenteuer wählen und ein Passwort festlegen.
3. Oben rechts auf **„Spieler-Link kopieren“** klicken. Der Link endet auf `?tisch=…` und bleibt immer gleich.
4. Den Link in der Verwaltung der Seite eintragen, dann sehen ihn alle Mitglieder auf der Startseite. Allen anderen Link und Passwort **getrennt** schicken.
5. **Den Tisch-Tab während des Spiels offen lassen.** Die Spieler verbinden sich direkt mit dem Browser des Spielleiters.

> Den Spielleiter-Zugang immer nur auf **einem** Gerät gleichzeitig öffnen.

### Als Spieler
1. Auf der Startseite anmelden und **„Spieltisch öffnen“** klicken, oder den Link vom Spielleiter öffnen. Dann das Passwort eingeben.
2. Oben rechts bei **„Ich spiele“** den eigenen Helden wählen.
3. Fertig. Die eigene Figur lässt sich ziehen, gewürfelt wird im Reiter „Würfel“.

Funktioniert auf dem PC, dem Tablet und dem Handy.

---

## Technik in Kürze

- **Kleine Dateien:** `index.html` enthält die ganze Anwendung. Dazu kommen `peerjs.min.js` für die Verbindung und der Ordner `fonts/` mit den Schriften.
- **Peer-to-Peer:** Der Browser des Spielleiters ist der „Tisch“. Die Spieler verbinden sich über [PeerJS](https://peerjs.com/) (WebRTC) direkt mit ihm. Es gibt keine eigene Datenbank für den Tisch.
- **Spielleiter entscheidet:** Nur der Spielleiter-Browser speichert den Spielstand und prüft jeden Zug. Spieler können nur ihre eigene Figur bewegen. Versteckte Figuren, Trefferpunkte und Bilder bekommen sie gar nicht erst geschickt bzw. erst nach dem Passwort.
- **Schriften lokal:** Alle Schriften liegen im Ordner `fonts/`. Es werden keine Daten an Google Fonts übertragen.
- **Speicher:** Szenen, Karten, Bilder und Musik liegen im Browser des Spielleiters (IndexedDB), nicht auf GitHub und nicht auf der Webseite.

### Optionale Einstellungen: `tisch-config.js`

Liegt neben der `index.html` eine Datei `tisch-config.js`, liest der Tisch sie beim Start. Fehlt sie, gelten die Standardwerte. Hier bei GitHub gibt es sie absichtlich nicht.

```js
// Knopf „← Zum Portal“ oben rechts (öffnet in einem neuen Tab)
window.TISCH_HOME = { url: "/", label: "Zum Portal" };

// Eigener PeerJS-Server statt des kostenlosen PeerJS-Cloud-Servers
window.TISCH_PEER = { host: "meine-domain.de", port: 443, secure: true, path: "/" };
```

---

## Daten und Sicherung

Was im Spieltisch eingerichtet wird, liegt **nur im Browser** des Spielleiters, nicht in diesem Repository. Jede Adresse ist dabei ein eigener Speicher: Der Tisch auf unserer Seite und der Tisch hier bei GitHub wissen nichts voneinander.

- **Sichern:** Reiter „Szenen“ → **„Sichern“** lädt eine Datei mit Szenen, Karten, Bildern, Tisch-Code, Passwort, Theme und Musikliste herunter (MP3-Dateien sind nicht enthalten).
- **Laden:** Dieselbe Datei über **„Laden“** einspielen, zum Beispiel auf einem anderen Rechner, nach dem Löschen der Browserdaten oder beim Umzug zwischen GitHub und der Webseite.
- **Figurenbilder:** Die Bilder der Helden und Figuren kommen aus einer separaten Datei `Heldenbilder.json`. Sie wird **nicht** hier hochgeladen, sondern einmalig im Spieltisch über „Laden“ eingespielt. So bleiben die Bilder hinter dem Passwort.

> Eine neue `index.html` hochzuladen ändert **nichts** an Szenen, Bildern, Tisch-Code oder Spieler-Link.

---

## Aktualisieren

**Auf unserer Seite:** Die neue Version steckt im Update-Paket im Ordner `public_html/tisch/`. Mit FileZilla hochladen, danach im Spieltisch **Strg + F5**.

**Hier bei GitHub** (damit der Ausweich-Tisch aktuell bleibt):
1. **„Add file“ → „Upload files“** → neue `index.html` (und bei Bedarf den Ordner `fonts`) hineinziehen → **„Commit changes“**.
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
| `fonts/` | Schriften (IM Fell English SC, Alegreya, Alegreya Sans, Cinzel, Cinzel Decorative) mit ihren Lizenzen (SIL Open Font License) |
| `README.md` | Diese Beschreibung |

---

## Danksagung

- [PeerJS](https://peerjs.com/) für die einfache WebRTC-Verbindung (MIT-Lizenz)
- Schriften über [Fontsource](https://fontsource.org/), jeweils unter der SIL Open Font License
- Musikvorschläge von [Tabletop Audio](https://tabletopaudio.com/)
- Dungeons & Dragons ist eine Marke von Wizards of the Coast. Dies ist ein privates Fanprojekt ohne Verbindung zu Wizards of the Coast.

Erstellt von **Sebastian Preuß** ([thebeardedbatman](https://github.com/thebeardedbatman)) für die Runde der *Bearded Bad Boys*. 🧔‍♂️⚔️
