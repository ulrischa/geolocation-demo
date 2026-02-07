# geolocation-demo

## Features

* Live-Tracking als **Polyline** (Linie) + **Marker** (aktueller Punkt)
* **Start**, **Pause/Weiter**, **Stopp**
* **Follow an/aus** (Map folgt dem Marker)
* **Linie löschen**
* **Diagnostik-Panel** (Secure Context, iFrame, Leaflet geladen, Permission-Status)
* **Error-Panel** (JS-Fehler direkt sichtbar)
* **Test-Panel** (PASS/FAIL Checks für typische Breakages)

---

## Dateien

* `index.html` (einzelne Datei, enthält CSS + JS)

---

## Voraussetzungen

* Browser: **Chrome** (für das `<geolocation>`-Element idealerweise Chrome 144+)
* Für Geolocation:

  * **HTTPS** oder `http://localhost`
  * Standortberechtigung im Browser aktiviert

Wichtig: In **iFrames** kann Geolocation durch **Permissions Policy** blockiert werden. Dann funktionieren Standort-APIs ggf. nicht oder es kommt keine Abfrage.

---

## Starten

### Option A: Lokal mit einfachem HTTP-Server (empfohlen)

In das Verzeichnis wechseln und einen Server starten:

**Python**

```bash
python -m http.server 8000
```

Dann öffnen:

* `http://localhost:8000`

### Option B: HTTPS (z.B. eigener Webserver)

Datei auf einem HTTPS-Host ablegen und im Browser öffnen.

---

## Bedienung

### Start

* **Start (JS)**: startet Tracking über `navigator.geolocation.watchPosition()`
* Alternativ: Klick auf das `<geolocation>`-UI (wenn dein Chrome es rendert)

### Pause

* Stoppt das Sammeln neuer Punkte (Watcher wird angehalten)
* **Weiter** setzt das Sammeln fort

### Stopp

* Stoppt Tracking und beendet Watcher

### Follow

* **Follow an**: Karte folgt dem aktuellen Marker
* **Follow aus**: Marker bewegt sich, Karte bleibt

### Linie löschen

* Löscht Polyline + Marker + Statistik

---

## Ausgabe/Status

### Statuszeile

Zeigt z.B.:

* `Bereit`
* `Starte ueber JS-Geolocation (Permission bestaetigen)`
* `Tracking aktiv (X Punkte)`
* Fehlertexte

### Diagnostik

Zeigt u.a.:

* `secure_context: yes/no`
* `in_iframe: yes/no`
* `permissions_api.geolocation: granted/denied/prompt/error`
* `leaflet_loaded: yes/no`
* wenn vorhanden zusätzlich Werte vom `<geolocation>`-Element:

  * `geo.isValid`
  * `geo.invalidReason`
  * `geo.permissionStatus`




