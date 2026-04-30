# Kateřina Machů — Osobní profil

Osobní profilová stránka Bc. Kateřiny Machů — náčelnice ČOS, cvičitelka, zdravotní sestra.
Slouží jako podklad pro média, redakční briefy a fact-checking.

## Struktura projektu

```
katerina-machu-profil/
├── index.html          # Celá stránka — HTML + CSS + JS v jednom souboru (1166 řádků)
└── katerinamachu.jpg   # Portrétní fotka (object-position: 65% 15%)
```

Čistý statický web. Žádný Node.js, žádný bundler, žádný package.json.
Edituje se přímo `index.html` — CSS je v `<style>`, JS v `<script>` na konci `<body>`.

## Fonty

Google Fonts, načteny přes `<link>`:
- **Cormorant Garamond** (300, 400, 600 + italic) — nadpisy, jméno, quote, logo, čísla
- **Montserrat** (300, 400, 500, 600) — tělo textu, labely, nav, buttony

## CSS design tokeny (`:root`)

```css
--white: #ffffff
--off-white: #faf9f7    /* světlé pozadí sekcí */
--black: #0d0d0d
--dark: #1a1a1a
--mid: #555555           /* tělo textu */
--light: #999999         /* muted labely */
--border: #e8e4df        /* linie, ohraničení */
--accent: #8B6F47        /* zlatohnědá — zvýraznění, labely, šipky */
--accent-light: #f0ebe4
```

## Sekce stránky (v pořadí)

| ID | Název | Popis |
|---|---|---|
| `#top` | Hero | Foto vlevo, jméno + CTA vpravo. Grid 1fr 1fr. |
| — | Stats strip | 4 čísla: 23+ let v Sokole, 1 620 cvičenek, 6 let sestra, 3 slety |
| `#biografie` | Biografie | 2 bio karty: zdravotnická + sokolská kariéra |
| `#sokol` | Sokolská timeline | Vertikální timeline 2002–2025 |
| — | Quote | „Sokol nejsem já, ale my." |
| `#leporelo` | Skladba Leporelo | Tmavá sekce (bg: var(--black)), 4 části skladby, statistiky |
| `#media` | Mediální obraz | Témata, citát z ČT Sport (2025) |
| `#vize` | Vize 2025–2028 | 6 karet: priority jako náčelnice |
| `#firmy` | Firemní cvičení | Benefity (3 sloupce) + CTA + „Proč právě ona" |
| `#zdroje` | Zdroje | 8 ověřených odkazů pro fact-checking |
| — | Footer | Černý, logo KM, email |

## Klíčové CSS třídy

- `.section` — standardní sekce (padding: 7rem 3rem, max-width: 1200px)
- `.section-label` — malý zlatý nápis s čárkou vlevo (accent)
- `.section-title` — Cormorant Garamond, clamp(2rem–3.5rem)
- `.bio-card` — ohraničená karta s border 1px
- `.timeline` / `.timeline-item` — vertikální timeline s levou linkou
- `.leporelo-section` — tmavá sekce (bg: black)
- `.firmy-section` — sekce pro firmy (bg: white)
- `.proc-pillar` — 2-sloupcový grid: název vlevo (18ch), popis vpravo
- `[data-reveal]` — IntersectionObserver scroll reveal (třída `.revealed`)
- `.btn-primary` — černý plný button
- `.btn-secondary` — průhledný s border

## JavaScript (inline na konci body)

1. **Navbar scroll** — přidá `.scrolled` (box-shadow) po 60px scrollu
2. **Scroll-to-top** (`#scroll-top`) — zobrazí se po 60px
3. **IntersectionObserver reveal** — `[data-reveal]` → `.revealed` s 80ms stagger
4. **Fallback** — elementy viditelné při loadu se odhalí po 100ms timeoutu

## Responzivní breakpointy

- `max-width: 900px` — hero grid → 1 sloupec; firmy benefity/cta → 1 sloupec
- `max-width: 768px` — nav-links skryt; bio-grid → 1 sloupec; zdroje → 1 sloupec
- `max-width: 600px` — stats-strip → 2 sloupce; vize-grid → 1 sloupec

## Kontakt a email

- E-mail v footer a CTA firmy: `kmachu@sokol.eu` ← **zkontrolovat, zda aktuální**
- Správný e-mail pro firemní záležitosti: `katerina.machu@email.cz`

## Poznámky

- Fotka `katerinamachu.jpg`: `object-position: 65% 15%` — obličej v pravém horním kvadrantu
- Stránka nemá vlastní doménu — je to lokální/exportovaný profil
- **Odlišná od** `/firmy` stránky na `C:\personal-website` (Next.js) — ta je čistě sales landing page pro nábor firemních klientů; tato je informační profil osobnosti
