# EIGENKERN – Homepage-Entwurf „Grundriss & Typenschild"

## Idee
EIGENKERN verkauft keine Cloud-Magie, sondern eine KI, die nachweisbar im eigenen Haus steht. Deshalb erklärt das Design den Ort der Daten wie eine technische Zeichnung. Statt einer Chat-Karte zeigt der Hero den **Grundriss einer Kanzlei** mit Gerät, Archiv und gestrichelter **Datengrenze**. Darunter sitzt ein **Typenschild** mit Standort, Verarbeitung, Internet und 0,00 € pro Frage. Die Sektionen sind wie in einer Norm nummeriert (§ 01–07), was Steuerberatern und Juristen vertraut ist. Linien gliedern die Seite, Schatten gibt es keine. Die Farben sind ruhiges Petrol und Tinte. Nur eine Signalfarbe kommt hinzu: **Markergelb**. Es kennzeichnet ausschließlich, was der Wächter schwärzt bzw. ersetzt.

## Dateien
| Datei | Inhalt |
|---|---|
| `previews/00-poster.png/.jpg` | Übersichtsposter 1920 × 1400 |
| `previews/01-startseite-desktop-1440.png/.jpg` | Startseite Desktop, 1440 px, ganze Seite |
| `previews/02-startseite-mobil-390-hero-bis-s02.png/.jpg` | Mobil (390 px, @2x): Hero + § 01 Lösungen + § 02 Begleitung |
| `previews/02b-startseite-mobil-390-komplett.png/.jpg` | Mobil, ganze Seite (Bonus) |
| `previews/03-style-tile.png/.jpg` | Style Tile: Schriften, Palette mit WCAG-Werten, Buttons, Karten, Icons |
| `previews/04-waechter-flow.png/.jpg` | Wächter-Visualisierung: Original → Schattenkopie → Cloud-KI → Antwort mit echten Namen |
| `startseite.html`, `styletile.html`, `waechter-flow.html`, `ek.css` | Klickbarer HTML/CSS-Prototyp (Quelle der PNGs) |

## Seitenaufbau
Hero (Grundriss + Typenschild) · Branchenleiste + Kennzahlen · § 01 Lösungen · § 02 Rundum begleitet · § 03 Drei Wege (Lokal / Eigener Server / Hybrid, je mit Schema) · § 04 Der Wächter · § 05 Klare Kosten (als Kostenaufstellung) · § 06 Der Unterschied (Vergleichstabelle) · § 07 FAQ · Abschluss-CTA · Footer.
Die Texte stammen von eigenkern.de. Die FAQ-Antworten sind Platzhalter, weil /hilfe nicht öffentlich erreichbar war.

## Technik
- **Schriften (alle SIL OFL, selbst hostbar als WOFF2):** Source Serif 4 (Headlines), IBM Plex Sans (Text), IBM Plex Mono (Labels/Zahlen). Im Prototyp werden sie nur für die Vorschau von Google Fonts geladen. Im Theme liegen sie lokal unter `/theme_eigenkern/static/fonts`.
- **Kontrast (WCAG AA):** Tinte 16:1, Text 8,5:1, Petrol 8,6:1, Labels 5,5:1, Markergelb auf Tinte 13,7:1.
- **Raster:** Container 1240 px, 12 Spalten, 32 px Gutter, entspricht Bootstrap-5-`container`/`row`/`col-*`. Mobil 20 px Rand.
- **Keine Bilder nötig:** Alle Grafiken sind Inline-SVG oder CSS. Das lädt schnell, ist scharf und lässt sich in Odoo als Snippet bearbeiten.

## Odoo-Basis (2–3 Sätze)
**DE:** Ich würde nicht auf einem Marketplace-Theme aufbauen, sondern ein schlankes eigenes Modul `theme_eigenkern` auf Basis des Odoo-Standardthemes (Bootstrap 5, Odoo 17/18) anlegen. Palette und Schriften kommen über die Theme-SCSS-Variablen (`o-color-palettes`, `o-theme-font-configs`) mit lokalem `@font-face` hinein. Grundriss-Hero, Paragraphen-Kopf, Drei-Wege-Karten, Wächter-Flow und Kostenaufstellung werden eigene Snippets mit `data-snippet`-Optionen, sodass das Team Texte, Reihenfolge und Farbvarianten im Odoo-Editor ändern kann. Fertige Themes bringen viel CSS mit, das gegen genau diesen reduzierten Stil arbeiten würde und Updates erschwert.

**EN:** I would not build on a marketplace theme. Instead I'd ship a lean custom `theme_eigenkern` module on top of Odoo's default Bootstrap 5 theme (Odoo 17/18), with the palette and self-hosted fonts injected through the theme SCSS variables (`o-color-palettes`, `o-theme-font-configs`, local `@font-face`). The floor-plan hero, § section header, three-ways cards, Wächter flow and cost sheet become custom snippets with editor options, so the EIGENKERN team can edit text, order and colour variants directly in the Odoo website builder. Off-the-shelf themes ship heavy CSS that would fight this restrained style and complicate upgrades.
