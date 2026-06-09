# Erdens Beauty by Cigdem — Website

Elegante One-Page-Website für das Kosmetikstudio **Erdens Beauty by Cigdem** (Raum Willich, NRW).
Reines HTML/CSS/JS, **kein Build-Schritt**, keine Abhängigkeiten zum Installieren.

---

## Schnellstart in Cursor

1. Diesen Ordner in Cursor öffnen (`File → Open Folder`).
2. Empfohlen: Extension **"Live Server"** installieren → Rechtsklick auf `index.html` → *"Open with Live Server"*.
   (Alternativ `index.html` einfach im Browser öffnen — Doppelklick reicht.)
3. Änderungen an `index.html` speichern, Browser aktualisiert live.

Es gibt bewusst keinen Framework-Overhead: eine Datei, alles inline (CSS im `<style>`, JS im `<script>`). Das hält die Seite schnell und leicht wartbar.

---

## Aufbau der Seite

- **Hero** mit Hintergrund-Video + Creme-Überblendung
- **Behandlungen** (Karten-Grid, „Dauerhafte Haarentfernung" als Spezialgebiet hervorgehoben, „Body Shape" als *bald verfügbar*)
- **Über mich** (dunkle Sektion — Teil des Farbsystems, s. u.)
- **CTA-Banner** (Anfrage / Instagram)
- **Kontakt** (Infos + Formular, das auf WhatsApp weiterleitet)
- **Footer** mit **Impressum** und **Datenschutz** (öffnen sich als Overlay-Seiten)

### Farbsystem · 60 / 30 / 10
Oben im CSS dokumentiert. Bitte beim Weiterbauen einhalten:
- **60 % Creme/Ivory** (`--cream`, `--ivory`) — Basis/Hintergrund
- **30 % Anthrazit** (`--charcoal`) — Texte, „Über mich"-Block, CTA-Box, Footer
- **10 % Gold** (`--gold`) — Buttons, Linien, Icons, Eyebrows, Hover (sparsam!)

---

## OFFENE TO-DOS (vor dem Live-Gang)

### 1. Hero-Video lokal hosten  ⚠️ wichtig
Aktuell lädt das Video von einem temporären Online-Link, der **ablaufen kann**.
- MP4 aus dem Chat herunterladen → als **`hero.mp4`** in diesen Ordner legen.
- In `index.html` im `<video>`-Block die lange `https://...cloudfront...`-URL ersetzen durch:
  ```html
  <source src="hero.mp4" type="video/mp4">
  ```

### 2. Schriften selbst hosten (DSGVO)  ⚠️ wichtig
Aktuell kommen die Fonts (Cormorant Garamond, Jost, Italiana) von **Google Fonts (CDN)** — in DE ein Abmahn-Thema, weil die Besucher-IP an Google geht.
- Fonts herunterladen (z. B. über google-webfonts-helper) → lokal einbinden → den `<link ...fonts.googleapis...>` im `<head>` entfernen.

### 3. Inhalte / Platzhalter füllen
Im Code mit `[...]` markiert:
- **Öffnungszeiten** (Kontakt-Sektion)
- **Foto** von Cigdem/Studio (Sektion „Über mich", aktuell Platzhalter-Fläche)
- **„Über mich"-Text** (persönliche Story/Philosophie)

### 4. Impressum prüfen  ⚠️ rechtlich
- **Straßenname bestätigen:** als *Martin-Zieffert-Str. 8* gelesen — in 47877 Willich nicht gefunden; bitte exakte Schreibweise verifizieren.
- **Rechtsform** (eingetragen: Einzelunternehmen) bestätigen.
- **Umsatzsteuer**: aktuell „Kleinunternehmerin §19 UStG" — bestätigen oder USt-IdNr. ergänzen.
- Ggf. **IHK / Aufsichtsbehörde** ergänzen.

### 5. Rechtliches gegenlesen lassen  ⚠️ rechtlich
- Impressum + Datenschutz sind saubere **Vorlagen**, keine Rechtsberatung — vor Veröffentlichung prüfen lassen.
- **HWG/UWG beachten:** Vorsicht bei Vorher-Nachher-Bildern und Versprechen wie „dauerhaft"/Heilwirkung.

---

## Noch nicht umgesetzt (Entscheidungen offen)
Diese Punkte aus dem Briefing-Prozess sind noch nicht final entschieden:
- Inhaltspflege: fest gecodet vs. CMS/Baukasten
- Buchung: WhatsApp vs. echtes Buchungstool (Kalender / Anzahlung)
- Eigene Domain + professionelle E-Mail (statt iCloud-Adresse)
- Cookie-/Consent-Banner (nur nötig bei Tracking/nicht-essenziellen Cookies)
- Mobile 9:16-Version des Hero-Videos
- Galerie / echte Behandlungs-Clips (lizenzfrei, selbst gehostet)

---

## Technische Notizen
- Keine `localStorage`/`sessionStorage`-Nutzung.
- Formular nutzt kein `<form>`-Submit, sondern öffnet WhatsApp (`wa.me/491749675443`) mit vorausgefülltem Text.
- Impressum/Datenschutz sind reine Overlays per JS (`openLegal()` / `closeLegal()`) — bei Bedarf später in echte Unterseiten auslagern.
- Scroll-Reveals via `IntersectionObserver`.
