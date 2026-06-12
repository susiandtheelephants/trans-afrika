# CLAUDE.md

Arbeitsanweisung für dieses Repository. Diese Datei sagt dir, **wie an diesem Projekt
gearbeitet wird**. Das **visuelle Design** ist NICHT hier beschrieben, sondern in
`susi-design-system.md` — diese Datei ist die alleinige Quelle der Wahrheit für Farben,
Typografie, Komponenten und Animationen. Lies sie vor jeder gestalterischen Arbeit.

---

## 1 · Was dieses Projekt ist

Die Website von **Susi & The Elephants** — eine geführte Trans-Afrika-Expedition
(Europa bis Kapstadt, Westroute) sowie perspektivisch weitere Angebote (Reiseführer,
Reiseberatung, Vorträge, Blog). Inhaber: Johan Schröder (Marke "Johnny" auf Instagram,
"Johnny" auf der Website), gemeinsam mit Marie.

Aktueller Stand: Die Website besteht aus einer Seite (Expedition). Sie wird schrittweise
zu einer Mehr-Bereiche-Website ausgebaut. Siehe Abschnitt 5 für die geplante Struktur.

---

## 2 · Technik-Stack & Struktur

- **Reines HTML / CSS / JS** — kein Framework, kein Build-Schritt, keine WordPress-Basis.
  Diese Schlankheit ist ein bewusster Vorteil (schnell, wartbar). Nicht zu einem
  Framework oder CMS wechseln.
- **Hosting:** Vercel, automatisches Deploy bei jedem Push auf GitHub.
- **DNS:** Cloudflare. `.de` leitet auf `.com` weiter. `www` ist Production,
  non-www leitet per 307 auf www.
- **Kontaktformular:** Formspree.
- **Schriften:** lokal eingebunden (variable TTFs im Ordner `/fonts/`), keine
  Google-Fonts-Verlinkung. `font-display: optional` in allen `@font-face`-Blöcken.
- **Kein Tracking, keine Cookies, kein Analytics.** Bewusste Datenschutz-Entscheidung,
  positiv im Datenschutz formuliert. NICHT ohne ausdrückliche Anweisung Tracking,
  Google Analytics, Tag Manager o.Ä. einbauen.

### Dateien

| Datei | Zweck |
|---|---|
| `index.html` | Startseite / aktuell die Expeditions-Seite |
| `styles.css` | Alle Tokens, Typografie, Layout, Komponenten (Umsetzung des Design-Systems) |
| `image-slot.js` | `<image-slot>` Custom Element für füllbare Bildplätze |
| `susi-design-system.md` | **Design-Referenz — bei allem Visuellen befolgen** |
| `impressum.html`, `datenschutz.html` | Rechtsseiten (noindex, bewusst für Bots blockiert) |
| `sitemap.xml`, `robots.txt` | SEO-Basis |

---

## 3 · Design — kurz, der Rest steht im Design-System

Für **alles Visuelle** gilt ausschließlich `susi-design-system.md`. Niemals Farben,
Schriften, Abstände oder Komponenten neu erfinden — immer die dort definierten Tokens
und Klassen verwenden. Die wichtigsten Leitplanken zur Erinnerung:

- Sand-Palette, kein pures Weiß (`--bg`), kein pures Schwarz (`--ink`).
- Display-Text immer italic Serif, Gewicht 400 — Größe schafft Wirkung, nicht Fettung.
- Buttons ausschließlich pill-förmig (radius 999px).
- `.reveal` / `.reveal-stagger` für einfahrende Inhalte.
- `.section.dark` für Kontrastbänder — keine neuen Dunkel-Behandlungen erfinden.

Wenn eine neue Seite gebaut wird: bestehende Komponenten und Klassen aus `styles.css`
**wiederverwenden**, nicht duplizieren. Jede neue Seite muss sich nahtlos in den
bestehenden Stil einfügen, als wäre sie schon immer Teil der Site gewesen.

---

## 4 · Text- & Inhaltsregeln (wichtig, projektspezifisch)

- **Keine Gedankenstriche (em-dash).** Stattdessen Komma oder Doppelpunkt. Gilt
  ausnahmslos in allen Texten.
- **Sprache:** durchgehend Deutsch, "du"-Ansprache (informell, nahbar).
- **Marke:** Auf der Website "Johnny", auf Instagram "Johnny". Firmenname
  "Susi & The Elephants".
- **Ton:** ehrlich, geerdet, Expeditions-Charakter. Kein Marketing-Sprech, keine
  Superlative. Es ist "kein einfacher Urlaub, sondern eine echte Expedition".
- **Eckdaten konsistent halten:**
  - **Eigene Reise von Marie & Johnny:** 23.000 km, 21 Länder, 140 Tage (Dezember 2025 bis April 2026). Für Über-uns- und Erfahrungs-Texte (Beratungs-Hero, About-Sektion, persönliche Erzählung).
  - **Angebotene Expedition:** 22.000 km, 21 Länder, ~125 Tage, ab 14.990€ p.P. (Einzelfahrerzuschlag 7.990€), 5 bis 8 Fahrzeuge, Start Anfang 2027. Für alle Angebots-Texte (Expedition, Home-Karten).
  - **Nicht vermischen.** Niemals 140 Tage für die Expedition oder 125 Tage für die eigene Reise verwenden.

---

## 5 · Geplante Seitenstruktur (Ausbau)

Reihenfolge bewusst so gewählt: zuerst bauen, was unabhängig von der noch offenen
Partnerfrage (Tour-Vermarktung) dir gehört. Die Expeditions-Seite zuletzt umbauen.

```
Home              Verzweigung: mit uns fahren / selbst fahren / eintauchen
├── Expedition    bestehende Seite — vorerst NICHT umbauen (Partnerfrage offen)
├── Reiseführer   digitales Buch, Kauf
├── Beratung      Video-Pakete 30/60/90 Min + "WhatsApp-Backoffice"
├── Journal       SEO-Motor, Artikel aus dem 120-Seiten-Reiseführer destilliert
└── Über uns      Marie, Johnny & Susi, Geschichte, Kontakt
```

Empfohlene Baureihenfolge: Home-Gerüst + Navigation → Journal → Reiseführer →
Beratung → Expedition (zuletzt).

**Wichtig:** Beratung ("ich helfe dir, selbst zu fahren") und Expedition
("fahr mit uns") sind zwei verschiedene Versprechen. Klar trennen, damit der Besucher
nicht verwirrt wird, welches Angebot was ist. Trennung am besten über die Home-Verzweigung.

---

## 6 · Arbeitsweise

- **Eine Seite nach der anderen** bauen, nicht alles auf einmal. Nach jeder Seite
  prüfen, ob Stil und Inhalt stimmen, bevor die nächste beginnt.
- **Deploy:** Änderung committen und pushen → Vercel deployt automatisch. Vor dem Push
  prüfen, dass die Seite lokal/visuell stimmt.
- **SEO-Basis erhalten:** Jede neue, öffentliche Seite braucht einen sinnvollen
  `<title>` (kurz, unter ~60 Zeichen), eine `meta description`, und sollte in die
  `sitemap.xml` aufgenommen werden. Canonical-Tag auf die www-Variante.
- **Konsistenz vor Kreativität:** Im Zweifel die bestehende Lösung wiederverwenden,
  nicht eine neue erfinden.
- **Navigation und Footer:** Beim Anlegen neuer Seiten IMMER 1:1 von `beratung.html`
  kopieren, nie neu schreiben. Einzige erlaubte Anpassungen: aktiver Nav-Link und Pfade.
  Nav-Klasse bleibt `brt-nav`, Footer-Markup bleibt identisch.

---

## 7 · Was du NICHT tun sollst

- Kein Framework / CMS / Build-System einführen.
- Kein Tracking, keine Cookies, kein externes Analytics ohne ausdrückliche Anweisung.
- Keine Google-Fonts-Verlinkung (Schriften bleiben lokal).
- Keine Gedankenstriche in Texten.
- Die Expeditions-Seite (`index.html`) nicht ohne Anweisung umbauen — die Tour-Frage
  (Eigenvermarktung vs. Partner) ist noch offen.
- Das Design-System nicht in dieser Datei duplizieren — bei Designänderungen
  `susi-design-system.md` und `styles.css` pflegen, nicht hier.
