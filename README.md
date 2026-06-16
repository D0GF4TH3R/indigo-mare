# La Nuit Indigo Mare · Gäste-Info-Seite

Statische Info-Seite für das Sommerfest (4.–5. Juli 2026, Casa Indigo Mare, Korsika).
Eine einzige `index.html` – kein Build, keine Abhängigkeiten. Hintergrundbild und
Easter-Egg-GIF sind als Base64 direkt in die Datei eingebettet.

## In VS Code öffnen

1. Diesen Ordner in VS Code öffnen: **File → Open Folder…** und den Projektordner wählen.
2. Empfohlene Erweiterung installieren: **Live Server** (Autor: Ritwick Dey).
   - In VS Code links auf das Extensions-Symbol, nach „Live Server" suchen, **Install**.
3. `index.html` öffnen, dann unten rechts auf **Go Live** klicken (oder Rechtsklick im
   Editor → **Open with Live Server**). Die Seite öffnet sich im Browser und lädt bei
   jeder Speicherung automatisch neu.

> Tipp: Ohne Live Server kannst du `index.html` auch einfach per Doppelklick im Browser
> öffnen – nur ohne Auto-Reload.

## Inhalte bearbeiten

Alle Texte/Einträge stehen in **einem** JavaScript-Block in `index.html`, markiert mit:

```js
const DATEN = [ ... ];
```

Jeder Eintrag hat dieselbe Struktur. Beispiel:

```js
{ kategorie:"Restaurants", gruppe:"Abends", name:"Name des Lokals",
  info:"kurze Zeile · z. B. Preis / Lage",
  text:"Beschreibung in ein, zwei Sätzen.",
  tip:"<b>Tipp:</b> optionaler Hinweis.",
  maps:M("Suchbegriff für Google Maps") },
```

Felder:
- `kategorie` – einer der Tabs: `Programm`, `Transport`, `Hotels`, `Restaurants`,
  `Strände`, `Ausflüge`, `Aktivitäten`
- `gruppe` – optionale Unterüberschrift (z. B. bei Restaurants `Mittags` / `Abends` /
  `Bars & Beach Clubs`; bei Aktivitäten `Sport vor Ort` / `Auf dem Wasser` / …)
- `info` – kurze graue Zeile unter dem Titel
- `text` – Haupttext
- `tip` – optionaler Hinweis-Kasten (HTML wie `<b>…</b>` erlaubt)
- `maps` – Karten-Button. Entweder `M("Suchbegriff")` (öffnet Google-Maps-Suche)
  oder eine fertige URL als String
- `link` + `linklabel` – ein zusätzlicher Button (z. B. Website)
- `links:[ {href, label, style} ]` – mehrere Buttons (z. B. Anrufen + Mail);
  `style:"whatsapp"` macht den Button grün mit WhatsApp-Icon
- `sea:true` – färbt den Akzentstrich bei Stränden meerblau

Neuen Eintrag anlegen = einen bestehenden kopieren, anpassen, Komma am Ende nicht
vergessen.

## Tabs ändern

Die Reihenfolge/Namen der Tabs steht in der Zeile:

```js
const KATEGORIEN = ["Programm","Transport","Hotels","Restaurants","Strände","Ausflüge","Aktivitäten"];
```

## Projektstruktur

```
indigo-mare/
├─ index.html        ← die Seite (klein & gut editierbar, ~40 KB)
├─ preview.jpg       ← WhatsApp-Vorschaubild (1200×630)
├─ assets/
│  ├─ bg.jpg         ← Hintergrundbild (nächtliches Aquarell)
│  └─ dance.gif      ← Easter-Egg-GIF
├─ README.md
└─ .vscode/          ← Editor-Einstellungen (optional)
```

## Bilder austauschen

- **Hintergrund:** `assets/bg.jpg` durch ein neues Bild ersetzen (gleicher Dateiname,
  Hochformat ~1080×1935 ist ideal).
- **Easter-Egg-GIF:** `assets/dance.gif` ersetzen.
- **Vorschaubild:** `preview.jpg` ersetzen (1200×630). Das ist das Bild, das in WhatsApp
  als Link-Vorschau erscheint (`og:image` im `<head>`).

Die Pfade stehen im Code als `assets/bg.jpg`, `assets/dance.gif` bzw. `preview.jpg` –
solange die Dateinamen gleich bleiben, musst du nichts im Code ändern.

## Veröffentlichen (GitHub Pages)

Die komplette Struktur (`index.html`, `preview.jpg` **und** der `assets/`-Ordner) muss
ins Repo `indigo-mare`. Am einfachsten per Drag & Drop des gesamten Ordnerinhalts in
**Add file → Upload files**. Wichtig: Der `assets/`-Ordner muss mit hochgeladen werden,
sonst fehlen Hintergrund und GIF.

Nach ~1 Minute live unter: `https://d0gf4th3r.github.io/indigo-mare/`

> Mit **git** (falls du es nutzt): `git add . && git commit -m "update" && git push`.

Wichtig: Wenn sich die WhatsApp-Vorschau nicht aktualisiert, den Link einmal mit
`?v=2` am Ende posten – das umgeht den WhatsApp-Cache.

## Easter Egg

10× schnell hintereinander auf den Titel „La Nuit Indigo Mare" tippen → Tanz-GIF
im Vollbild (spielt 3×, schließt automatisch; Tippen schließt sofort).
