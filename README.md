# 30er – Punktetafel

Eine Web-App zur Punkteverwaltung für das Würfelspiel «30er». Ihr würfelt am Tisch, gebt die Ergebnisse ein – die App übernimmt alle Berechnungen: Punktestände, Zugreihenfolge, Abzugsrichtung, Überspringen ausgeschiedener Spieler und die Sieger-Erkennung.

Alles läuft komplett im Browser, es wird kein Server und keine Datenbank benötigt. Die App ist eine **PWA (Progressive Web App)** und lässt sich auf Android und iOS wie eine echte App auf dem Homescreen installieren – inklusive eigenem Logo, Vollbildmodus und Offline-Nutzung.

## Funktionen

- 2–8 Spieler mit Namen und Sitzreihenfolge
- Vorlagen: Namen und alle Einstellungen lassen sich als benannte Vorlagen speichern (z.B. «Stammtisch») und beim nächsten Mal per Knopfdruck laden – die App startet immer leer, geladen wird nur auf Wunsch
- Abzugsrichtung wählbar (nachfolgender / vorheriger Spieler)
- Spielvarianten **Slow-Death** und **Instant-Death**
- Wählbare Würfelanzahl 1–8 (Standard 6): Die Zielzahl ist immer 5 × Würfelanzahl (alle Würfel zeigen eine 5), Punktefelder und Berechnungen passen sich automatisch an; bei einer Differenz über 6 (7–8 Würfel) erscheint eine Zwischenseite mit Wahl der Abzugsart: Zielzahl 1–6 oder „6 zählt als 7/8"
- Eingabe der Startpunktzahlen und freie Wahl des Startspielers
- Automatische Auswertung jedes Wurfs: genau 30 / über 30 (+Differenz) / unter 30 (−Differenz)
- Abzugs-Assistent: Zielzahl wird angezeigt, Anzahl der Treffer eingeben, Abzug wird berechnet und beim richtigen Nachbarn abgezogen (im Minus befindliche bzw. ausgeschiedene Spieler werden übersprungen)
- Punkteeingabe wahlweise per Antippen (vorgegebene Punktefelder, Normalbereich 28–32 prominent, seltene Werte unter 21 eingeklappt) oder klassisch per Tastatur – im Setup wählbar, Standard: Antippen
- Rückgängig-Funktion für Fehleingaben
- Humorvolle Animationen: freches Aufziehen bei schwachen Würfen (20 oder weniger), Effekt-Einblendungen bei grossen Abzügen (mehr als 10 Punkte) und Spott bei erfolglosen Abzugsversuchen (0 Treffer) – im Setup ein-/ausschaltbar, Standard: an
- Session-Siege: Solange Revanchen gespielt werden, trägt jeder Sieger eine Krone mit Sieganzahl neben dem Namen (👑2); bei «Neues Spiel» werden die Kronen zurückgesetzt
- Spielprotokoll und Sieger-Bildschirm mit Revanche-Option – die Abzugsrichtung kann für die nächste Runde neu gewählt werden, Spieler und Variante bleiben gleich
- Menü mit «Spielen» und «Scores»: Hall of Fame (höchste End-Punktzahlen der Sieger), Hall of Shame (tiefste je erreichte Punktestände), höchste Abzüge und schlechteste Würfe, filterbar nach Würfelanzahl – bleiben lokal auf dem Gerät gespeichert und über Spielabende hinweg erhalten
- Installierbar auf Android und iOS (PWA), offline nutzbar

## Dateistruktur

```
index.html            Die komplette App
manifest.webmanifest  App-Infos für die Installation (Name, Farben, Icons)
sw.js                 Service Worker (Offline-Modus)
icons/                Logo und alle Icon-Grössen
```

Wichtig: Alle Dateien und der Ordner `icons/` müssen zusammen hochgeladen werden.

## Über GitHub Pages veröffentlichen

1. Neues Repository auf [github.com](https://github.com) erstellen (z.B. `30er-spiel`), öffentlich.
2. Alle Dateien inkl. `icons/`-Ordner ins Repository hochladen («Add file» → «Upload files» – der Ordner kann per Drag & Drop mitgezogen werden).
3. Im Repository auf **Settings → Pages** gehen.
4. Unter **Build and deployment** als Source «Deploy from a branch» wählen, Branch `main` und Ordner `/ (root)`, dann **Save**.
5. Nach ein bis zwei Minuten ist die App erreichbar unter:
   `https://DEIN-BENUTZERNAME.github.io/30er-spiel/`

## Auf dem Handy installieren

**Android (Chrome):**
1. Die App-URL in Chrome öffnen.
2. Es erscheint entweder direkt ein Hinweis «App installieren» – antippen. Oder: Menü (⋮) → **«Zum Startbildschirm hinzufügen»** / **«App installieren»**.
3. Bestätigen – das 30er-Logo liegt nun auf dem Homescreen, die App startet im Vollbild und funktioniert auch offline.

**iOS / iPadOS (Safari):**
1. Die App-URL in Safari öffnen (wichtig: Safari, nicht Chrome).
2. Teilen-Symbol (Viereck mit Pfeil nach oben) antippen.
3. **«Zum Home-Bildschirm»** wählen und bestätigen.
4. Das 30er-Logo liegt nun auf dem Homescreen, die App startet im Vollbild und funktioniert auch offline.

## Optional: Veröffentlichung in den App Stores

Falls die App später im Google Play Store oder Apple App Store erscheinen soll, ist das mit derselben Codebasis möglich:

- **Google Play:** Über ein «Trusted Web Activity»-Paket (z.B. mit dem Werkzeug [Bubblewrap](https://github.com/GoogleChromeLabs/bubblewrap)) lässt sich die gehostete PWA als Android-App verpacken. Benötigt ein Google-Play-Entwicklerkonto (einmalig ca. 25 USD).
- **Apple App Store:** Mit [Capacitor](https://capacitorjs.com) lässt sich die App in eine native iOS-App verpacken. Benötigt einen Mac mit Xcode und ein Apple-Developer-Konto (ca. 99 USD pro Jahr).

Für den Spieltisch reicht die PWA-Installation in aller Regel völlig aus – sie ist kostenlos, sofort verfügbar und Updates erscheinen automatisch, sobald neue Dateien auf GitHub liegen.

## Hinweise

- Der Spielstand lebt im Browser-Tab bzw. in der geöffneten App. Wird die App komplett geschlossen und neu geöffnet, beginnt ein neues Spiel.
- Nach dem ersten Öffnen ist die App dank Service Worker offline nutzbar.
