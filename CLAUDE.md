# CLAUDE.md

Kontext für den KI-Assistenten (Claude Code o. ä.) bei der Arbeit an diesem Projekt.
Für die ausführliche Bedienungsanleitung siehe @README.md.

## Was das ist

Eine statische Gäste-Info-Seite für ein privates Sommerfest
("La Nuit Indigo Mare", 4.–5. Juli 2026, Casa Indigo Mare, Korsika).
Sie wird als Link in einer WhatsApp-Gruppe geteilt; die Gäste tippen drauf und sehen
Programm, Restaurants, Strände, Ausflüge, Hotels, Transport und Aktivitäten.
Zielgruppe: gemischt, jung bis alt – alles muss ohne Login, ohne App, auf jedem Handy
funktionieren.

## Technische Eckpunkte (nicht ändern ohne Grund)

- **Eine einzige `index.html`**, kein Build-Schritt, kein Framework, keine npm-Pakete.
  Reines HTML + CSS + Vanilla-JS. Das ist Absicht – es muss auf GitHub Pages ohne
  Pipeline laufen und für eine Nicht-Entwicklerin wartbar bleiben.
- Bilder liegen als echte Dateien in `assets/` (`bg.jpg`, `dance.gif`); das
  Vorschaubild ist `preview.jpg` im Root. (Online-Variante hatte sie als Base64
  eingebettet – hier bewusst ausgelagert, damit die HTML editierbar bleibt.)
- **Kein localStorage / sessionStorage** und keine externen Skripte außer den Google
  Fonts im `<head>`. Keine Tracking-Skripte, kein Backend.
- Schriften: `Cormorant Garamond` (Überschriften) + `EB Garamond` (Text).
- Dark-Mode-Design, nächtliches Aquarell als fixer Hintergrund.

## Wo der Inhalt lebt

Der gesamte redaktionelle Inhalt steckt in **einem** Array `const DATEN = [...]` in
`index.html`. Tabs/Reihenfolge in `const KATEGORIEN = [...]`. Die Render-Funktion
gruppiert Restaurants und Aktivitäten nach dem optionalen Feld `gruppe`.
Struktur der Einträge und Felder: siehe README.

## Verhaltensregeln für Änderungen

- **Inhalt vs. Code trennen:** Für neue Spots/Texte nur das `DATEN`-Array bearbeiten,
  nicht die Render-Logik anfassen.
- **Keine echten privaten Daten erfinden.** Telefonnummern, Adressen, Links nur dann
  eintragen, wenn sie vom Nutzer kommen oder belegt sind – im Zweifel nachfragen,
  nicht raten. (Es sind reale Kontaktdaten von realen Personen im Spiel.)
- **Datenschutz:** Das Repo ist öffentlich. Keine sensiblen Daten ergänzen, die nicht
  ohnehin für die Gästegruppe gedacht sind.
- **Die Suche durchsucht ALLE Kategorien**, sobald etwas getippt wird (nicht nur den
  aktiven Tab) – diese Logik nicht versehentlich zurückbauen.
- **Easter Egg:** 10× schnelles Tippen auf den Titel `.hero h1` zeigt `assets/dance.gif`
  im Overlay. Wenn der Titeltext geändert wird, bleibt der `.hero h1`-Selektor erhalten –
  nicht das Element umbauen.
- Vor dem Festschreiben einer Änderung kurz prüfen, dass die Seite im Browser lädt
  (Live Server) und Suche + Tabs funktionieren.

## Veröffentlichen

GitHub Pages, Repo `indigo-mare`, live unter
`https://d0gf4th3r.github.io/indigo-mare/`. Beim Hochladen **immer den `assets/`-Ordner
mitnehmen**. Details und der WhatsApp-`?v=2`-Cache-Trick stehen in der README.

## Sprache

Projektsprache ist **Deutsch** (Inhalte, Commit-Messages, Antworten an den Nutzer).
