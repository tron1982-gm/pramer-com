# pramer.com – Arbeitsanleitung für Claude

Diese Website gehört **Mag. Gerlinde Pramer** (Führungskräfte-Begleitung, Online Sessions, 1:1 Begleitung, Coaching, Keynotes, Anahata Business Circle). Sie pflegt die Seite selbst – mit Claude. Sie ist keine Entwicklerin: Erkläre alles in einfachen Worten, ohne Fachbegriffe, auf Deutsch.

## So arbeitest du in diesem Repo

- **Nie direkt auf `main` arbeiten.** Jede Änderung in einem eigenen Branch, danach einen Pull Request mit einer kurzen deutschen Beschreibung öffnen („Was wurde geändert, auf welcher Seite").
- **Kleine, gezielte Änderungen.** Nur das ändern, worum gebeten wurde. Keine ungefragten Umbauten, Aufräumarbeiten oder Design-Experimente.
- Wenn ein Wunsch unklar ist (welche Seite, welcher Text, welches Bild): **zuerst nachfragen**, dann ändern.
- Am Ende jeder Aufgabe in 2–4 Sätzen sagen: was geändert wurde, und dass Mag. Gerlinde Pramer jetzt auf GitHub den Pull Request mit „Merge pull request" übernehmen kann. Danach ist die Änderung nach ca. 1–2 Minuten in der **Vorschau** sichtbar (GitHub Pages dieses Repos, Adresse: `https://<github-name>.github.io/pramer-com/`).
- **Niemals selbst live schalten.** Live geht die Seite ausschließlich, wenn Mag. Gerlinde Pramer unter „Actions" den Ablauf **„Website live schalten"** startet. Das ist ihre Entscheidung.
- Keine Zugangsdaten, Passwörter oder Tokens in Dateien schreiben. Dieses Repo ist öffentlich.

## Technik

- Reine statische Website: HTML + CSS + etwas JavaScript direkt in den Seiten. Kein Build-Tool, kein Framework, kein npm. So soll es bleiben.
- Jede Seite ist ein Ordner mit `index.html` (`ueber-mich/`, `angebote/`, `online-sessions/`, `termine/`, `kontakt/`, `coaching/`, `keynote/`, `1-1-begleitung/`, `anahata-business-circle/`), dazu `index.html`, `impressum.html`, `datenschutz.html` im Hauptordner. Bilder liegen in `img/`.
- **Interne Links immer relativ**, nie mit führendem `/` (also `../kontakt/`, nicht `/kontakt/`) – sonst funktioniert die Vorschau auf GitHub Pages nicht.
- **Neue Seite oder neuer Ordner?** Dann zusätzlich: in `.github/workflows/live-schalten.yml` in die Liste `ORDNER` eintragen (sonst geht sie nicht live), in `sitemap.xml` ergänzen, und Navigation, mobiles Menü und Footer auf **allen** Seiten anpassen.
- `img-originale-archiv/`, `logo-testseite*.html` und `newsletter-baukasten*` nicht anfassen.

## Sprache & Ton

- Österreichisches Deutsch, mit „ß".
- Die Website spricht Besucher:innen in der **Sie-Form** an.
- Ton: warm, einladend, authentisch, **bescheiden**. Keine marktschreierischen Superlative („exklusiv", „einzigartig", „die Nr. 1").
- Gerlinde wird auf der Website immer **„Mag. Gerlinde Pramer"** genannt – nie ohne akademischen Titel.
- Dauer der Online Sessions immer so schreiben: „30 – 45 Min." (Halbgeviertstrich mit Leerzeichen).

## Design (verbindlich – nichts Neues erfinden)

Farben (CSS-Variablen, bereits in jeder Seite definiert – diese verwenden, keine neuen Farbwerte):
- Navy `--ink: #1A3A6B` (Überschriften, Footer), Gold `--gold: #B89968` (Akzente, Buttons), Creme `--cream: #FAF7F2`, `--cream-deep: #F2EDE3`, Weiß `--surface: #FFFFFF`, Akzentblau `--blue-deep: #2B5A8C`, Fließtext `--ink-soft: #3A4F6E`.
- **Keine Lila-/Violett-Töne** (veraltet).

Schriften: Überschriften **Outfit**, Fließtext **Inter** (über Google Fonts eingebunden).

Regeln für Seitenaufbau:
- Sektionen wechseln streng **weiß / beige** ab. Wird eine Sektion eingefügt, die Farbfolge der ganzen Seite prüfen.
- Die letzte Sektion vor dem (navy) Footer ist **nie navy**.
- Zwei benachbarte Sektionen nie mit demselben Layout (z. B. nicht zweimal hintereinander ein Karten-Raster).
- Pro Sektion nur **ein** visuelles Hauptelement (Foto oder Logo, nicht beides).
- Bild-Text-Spalten oben bündig (`align-items: start`).
- Zitat-Quellenangabe ohne Gedankenstrich: `Mag. Gerlinde Pramer`.
- Logo-Farbwechsel (Hover/Scroll) nur über zwei übereinanderliegende Bilder mit `opacity`, nie mit CSS-Filtern oder `display`.
- `impressum.html` und `datenschutz.html` haben ein älteres CSS-Grundgerüst: Bei Änderungen an Buttons, Logo, Navigation oder Footer diese beiden Seiten immer separat mitprüfen.

## Bilder

- Vorhandene Bilder aus `img/` verwenden. Neue Bilder: JPG, längste Seite max. 2000 px, sprechender Dateiname in Kleinbuchstaben mit Bindestrichen (z. B. `gerlinde-vortrag-graz.jpg`).
- Immer einen aussagekräftigen deutschen `alt`-Text setzen.
- `width`/`height` am `<img>`: nie doppelt setzen; wenn eines schon vorhanden ist, das andere proportional ergänzen.
- KI-bearbeitete Bilder: Der allgemeine Hinweis steht bereits im Impressum – kein zusätzlicher Hinweis am Bild nötig.

## Mobil prüfen

Jede Änderung muss auch auf dem Handy gut aussehen (ca. 375 px Breite): Bildausschnitte, Buttons, Zeilenumbrüche in Überschriften, das mobile Menü (Drawer).

## Termine (häufigste Änderung)

Termine stehen an **mehreren Stellen**, die immer gemeinsam angepasst werden müssen:
1. `termine/index.html` (Tabelle) – jede Zeile hat am Button `.btn-anmelden` die Attribute `data-datum="Wochentag, T.M.JJJJ"`, `data-uhrzeit="HH:MM"`, `data-dauer="… Min."` oder `"… Std."` und optional `data-adresse`. Diese müssen stimmen, sonst blendet die Seite vergangene Termine nicht automatisch aus. Neue Zeilen **vor** der Zeile `tr-keine-termine` einfügen.
2. Die Seite `anahata-business-circle/index.html` (falls dort Termine genannt sind).
3. **Außerhalb dieses Repos:** die Landingpage **abc.pramer.com** (eigenes Repo `anahata-business-circle`) und die Bestätigungsmails in ActiveCampaign. Darauf am Ende der Aufgabe ausdrücklich hinweisen.

## Nicht ohne ausdrücklichen Auftrag ändern

- Rechtliche Texte in `impressum.html` und `datenschutz.html`.
- Newsletter-Formulare (ActiveCampaign, Formular 19, versteckte Felder `field[3]`/`field[4]`) – nur Texte rundherum dürfen geändert werden.
- Strukturierte Daten (`<script type="application/ld+json">`), `robots.txt`, `llms.txt`. Wenn sich Angebote, Termine oder Kontaktdaten ändern, die JSON-LD-Angaben aber passend mitziehen.
