# Haushaltskasse

Eine kleine Android-App für zwei Personen oder eine WG, die sich Ausgaben teilen:
Einkauf, Tanken, Essen gehen. Die App rechnet aus, wer wem wie viel schuldet, und hält
alle Handys über das eigene Heimnetz auf demselben Stand.

**Kein Konto, keine Anmeldung, keine Cloud.** Alle Daten liegen auf einem
Netzwerkspeicher im eigenen WLAN, zum Beispiel dem USB-Speicher am Router. Nichts
verlässt das Haus.

---

## Was die App kann

- **Ausgabe eintragen:** Betrag, kurze Bezeichnung, wer bezahlt hat. Drei Schnellwahl-Knöpfe
  für die Dinge, die man ständig einträgt, frei umbenennbar durch langes Drücken.
- **Halbe-halbe oder ganz:** Normalerweise wird geteilt. Ohne Haken zahlt der andere den
  vollen Betrag, praktisch, wenn man jemandem etwas mitbringt.
- **Der offene Betrag, groß und aus deiner Sicht:** Grün heißt, du bekommst Geld. Rot heißt,
  du schuldest. Antippen kopiert den Betrag für die Überweisung.
- **Zeitraum wählen:** dieser Monat, ein einzelner vergangener Monat oder alles zusammen.
  Offene Beträge aus Vormonaten werden mitgenommen.
- **Auf null setzen,** wenn ihr euch ausgeglichen habt. Alle Einträge bleiben erhalten.
- **Excel-Tabelle pro Monat**, automatisch auf den Netzwerkspeicher geschrieben. Zum
  Nachschauen am Rechner, mit Datum, Bezeichnung, wer bezahlt hat und wer wem was schuldet.
- **Änderungsprotokoll:** Jede Änderung wird mit Gerät, Datum und Uhrzeit festgehalten. Man
  sieht also immer, wer was wann eingetragen, geändert oder gelöscht hat.
- **Beide Handys bleiben synchron:** beim Start, nach jedem Eintrag und stündlich im
  Hintergrund, solange ihr im heimischen WLAN seid. Bringt der Abgleich im Hintergrund
  etwas vom anderen Handy mit, zeigt Android eine kurze Meldung, ohne Beträge und Namen.
- **Fixkosten** wie Miete, Strom oder ein gemeinsamer Kredit auf einer eigenen Seite:
  wer zahlt, wer was trägt, dauerhaft oder bis zu einem Monat.
- **Eigene Namen und Farben:** Die beiden Konten heißen ab Werk „Name 1" (rosa) und
  „Name 2" (blau) und sind frei änderbar. Die Namen gelten für beide Handys.
- **Paar oder WG:** In den Einstellungen unter *Konten und Aufteilung* stellst du auf
  WG um. Dann gibt es 2 bis 12 Personen mit eigenen Namen, und geteilt wird gleich auf
  alle oder nach eigenen Prozenten, die zusammen 100 ergeben. Beim Eintragen wählst du
  die Person aus einem Feld. *Auf null setzen* zeigt, wer wem wie viel überweist, mit
  möglichst wenigen Überweisungen. Die WG hat ihre eigene Kasse, die des Paars bleibt
  erhalten. Die Fixkosten gibt es bisher nur für das Paar.
- **Hell, dunkel oder wie das System.**

Voraussetzung: Android 8 oder neuer.

---

## Installation

Die App kommt nicht aus dem Play Store, sondern wird direkt installiert. Das ist einmal
etwas Klickerei, danach aktualisiert sie sich selbst.

1. **APK herunterladen.** Oben rechts unter *Releases* die neueste Version öffnen und die
   Datei `haushaltskasse-vX.Y.Z.apk` antippen. Sie landet im Download-Ordner.
2. **Datei öffnen.** Android fragt jetzt nach: *„Aus dieser Quelle dürfen keine unbekannten
   Apps installiert werden."*
3. **Erlauben.** Auf *Einstellungen* tippen und den Schalter **„Unbekannte Apps installieren"**
   für die App umlegen, aus der du die Datei geöffnet hast (meist *Dateien* oder *Chrome*).
   Dann zurück.
4. **Installieren** antippen. Fertig.

Wenn eine Warnung erscheint, dass die App nicht überprüft wurde: Das ist normal bei Apps,
die nicht aus dem Play Store kommen. *Trotzdem installieren*.

> **Umstieg von einer älteren Fassung:** Wenn schon eine Version installiert ist, die nicht
> von hier stammt, muss sie vorher deinstalliert werden. Android lässt einen Wechsel des
> Signaturschlüssels nicht zu. Danach laufen alle weiteren Updates von selbst.

---

## Einrichtung des Netzwerkspeichers

Die App speichert nichts auf einem fremden Server. Beide Handys tauschen ihre Daten über
eine Dateifreigabe im eigenen WLAN aus, über SMB, also dasselbe Verfahren, mit dem auch
Windows Ordner freigibt.

Das kann sein: der USB-Stick oder die Festplatte am Router, ein NAS im Haushalt oder ein
Rechner mit freigegebenem Ordner. Nötig ist **SMB in Version 2.1 oder neuer**, alles aus
den letzten zehn Jahren kann das.

### Schritt 1: Speicher freigeben

Auf dem Gerät, das den Speicher bereitstellt (Router-Oberfläche, NAS-Oberfläche oder
Rechner):

1. Speicher aktivieren und die Dateifreigabe im Heimnetz einschalten.
2. Den **Namen der Freigabe** notieren. Er steht in der Oberfläche und sieht aus wie
   `FREIGABENAME` oder `daten`.
3. Nur im Heimnetz freigeben, der Zugriff aus dem Internet wird nicht gebraucht und sollte
   aus bleiben.

### Schritt 2: Benutzer anlegen

1. Einen **eigenen Benutzer** für die App anlegen, nicht den Verwaltungszugang benutzen.
2. Diesem Benutzer **Lese- und Schreibrechte** auf die Freigabe geben. Nur lesen reicht
   nicht, die App muss schreiben können.
3. Ein Passwort vergeben. Beide Handys benutzen denselben Benutzer.

### Schritt 3: Angaben in der App eintragen

In der App oben den Reiter *Einstellungen* wählen oder aufs Zahnrad tippen, dann ausfüllen:

| Feld | Was dort hingehört | Beispiel |
|---|---|---|
| **Adresse** | IP-Adresse des Speichers im Heimnetz. Zuverlässiger als ein Name. | `192.0.2.10` |
| **Freigabe** | Der Name aus Schritt 1 | `FREIGABENAME` |
| **Ordner** | Unterordner für die Kasse. Wird automatisch angelegt. Leer lassen = Hauptordner. | `Haushalt` |
| **Benutzer** | Der Benutzer aus Schritt 2 | `haushalt` |
| **Passwort** | Sein Passwort | `••••••••` |
| **Heim WLAN (SSID)** | Der Name eures WLANs. **Pflichtfeld.** | `MeinWLAN` |
| **Gerätename** | Damit ihr im Protokoll seht, von welchem Handy ein Eintrag kam | `Handy links` |

> Die IP-Adresse oben ist nur ein Beispiel. Die richtige steht in der Oberfläche eures
> Routers oder NAS.

Dann **„Verbindung testen"** drücken. Es sollte *„Verbindung steht"* erscheinen.

Zum Schluss **Speichern**.

### Schritt 4: Standortfreigabe erlauben

Beim ersten Abgleich fragt die App nach der Standortfreigabe. Das wirkt seltsam, hat aber
einen Grund: Android gibt den Namen des WLANs nur mit dieser Berechtigung heraus, und die
App prüft damit, ob sie wirklich zu Hause ist.

**Ohne diese Berechtigung synchronisiert die App nicht.** Das ist Absicht: Sonst würde sie
in jedem fremden WLAN versuchen, sich anzumelden, und dabei die Zugangsdaten an einen
fremden Rechner schicken. Bitte dauerhaft erlauben, „nur während der Nutzung" reicht dem
stündlichen Hintergrundabgleich nicht.

### Schritt 5: Zweites Handy

Auf dem zweiten Handy dieselben Angaben eintragen, nur beim **Gerätenamen** einen anderen
wählen. Beim nächsten Abgleich zieht es sich den gesamten Stand vom Speicher.

### Was auf dem Speicher landet

Im eingestellten Ordner legt die App an:

- `haushalt.json`, der gemeinsame Datenstand, den beide Handys abgleichen
- `haushalt-JJJJ-MM.xlsx`, eine Excel-Tabelle pro Monat, zum Nachschauen am Rechner
- `haushalt-protokoll.txt`, das Änderungsprotokoll in lesbarer Form
- in der WG `haushalt-wg.json` und `haushalt-wg-JJJJ-MM.xlsx`, die Kasse der WG und eine
  Excel-Tabelle pro Monat mit einer Spalte je Person
- daneben zwei technische Dateien für den Abgleich und die Fehlersuche

Die Excel-Dateien sind zum Lesen gedacht. Wer sie verändert, verliert die Änderungen beim
nächsten Abgleich.

### Wenn es nicht klappt

| Meldung | Was zu tun ist |
|---|---|
| *Anmeldung* oder *Logon failure* | Benutzer oder Passwort stimmen nicht, oder dem Benutzer fehlen die Rechte auf die Freigabe |
| *Verbindung* oder Zeitüberschreitung | IP-Adresse prüfen, WLAN prüfen. Ist der Speicher überhaupt eingeschaltet? |
| Etwas mit *sign* oder *signing* | Die Freigabe kann keine signierte Übertragung. In den Einstellungen „SMB-Signierung erzwingen" abschalten, nur im Notfall, das schützt sonst vor Manipulation im WLAN |
| *kein WLAN* oder *nicht das Heimnetz* | Ihr seid unterwegs. Der Abgleich läuft nur zu Hause |
| *Standortfreigabe fehlt* | Siehe Schritt 4 |
| *Prüfsumme passt nicht* | Entweder hat jemand die Datei auf dem Speicher verändert, oder das Passwort wurde geändert. Im zweiten Fall `haushalt.json` auf dem Speicher löschen, die App schreibt sie neu |

---

## Updates

Die App hält sich selbst aktuell.

- Beim Start schaut sie hier nach, ob eine neuere Version bereitliegt, höchstens alle sechs
  Stunden, damit sie nicht ständig ins Netz greift.
- Gibt es eine, erscheint ein Hinweis mit der Versionsnummer und dem, was sich geändert hat.
- Nach *Herunterladen* lädt sie die Datei und öffnet die Installation. Beim ersten Mal fragt
  Android wieder nach der Erlaubnis für unbekannte Apps; die App führt direkt zur richtigen
  Einstellung.
- Deine Daten bleiben dabei erhalten.

**Stable und Preview:** Jede neue Version erscheint hier zuerst als *Pre-release*
(Preview) zum Testen. Jeder darf eine Preview herunterladen und installieren, es
kann aber sein, dass darin noch etwas nicht funktioniert. Wer auf Nummer sicher
gehen will, nimmt die mit *Latest* markierte Version. Die App bietet von allein nur
freigegebene Versionen (Stable) an. Eine Preview erscheint nur, wenn du in den
Einstellungen unter *Version* selbst auf *Nach Updates suchen* tippst, und ist dort
deutlich als Preview gekennzeichnet.

**Selbst nachsehen:** Einstellungen → *Version* → *Nach Updates suchen* fragt sofort nach,
ohne auf die sechs Stunden zu warten. Gibt es nichts Neues, erscheint kurz
*„App ist aktuell"*. Dort steht auch, welche Version installiert ist, ob sie Stable
oder Preview ist und welche vorher lief.

**Zurück zur vorherigen Version:** Android installiert keine ältere Version über eine
neuere. Eine frühere Version kommt deshalb als neues Update mit höherer Nummer zurück
(„Stellt Version … wieder her"), dabei bleiben alle Daten. Für den Notfall zeigt
*Zur vorherigen Version zurück* den Weg auf dem Handy: erst abgleichen, dann die App
entfernen und die alte Version von hier installieren; der Abgleich holt die Daten
vom Netzwerkspeicher zurück.

Entwürfe überspringt die App.

---

## Datenschutz

- Keine Konten, keine Werbung, keine Statistik, keine Übertragung an Dritte.
- Alle Finanzdaten liegen ausschließlich auf euren Handys und eurem Netzwerkspeicher.
- Zugangsdaten werden verschlüsselt im Schlüsselspeicher des Handys abgelegt. Lässt sich der
  nicht öffnen, speichert die App das Passwort lieber gar nicht als im Klartext.
- Die App sichert nichts in der Cloud. Beim Gerätewechsel ist euer Netzwerkspeicher die
  Sicherung.
- Das technische Protokoll für die Fehlersuche enthält bewusst keine Beträge, Bezeichnungen,
  Namen oder Zugangsdaten.
- Nach außen spricht die App nur mit GitHub, und nur um nach einer neuen Version zu sehen.
