# 04 — Vývoj (technický backlog)

## Kostra (hotovo v tomto skeletone)

- [x] 4 statické stránky (Domov, O nás, Služby, Kontakt)
- [x] Responzívna navigácia (mobilné menu)
- [x] Spoločný CSS, žiadne externé závislosti
- [x] `robots.txt`, `sitemap.xml`
- [x] `CNAME` pre vlastnú doménu

## Ďalšie kroky

- [x] Nahradiť všetky `[DOPLŇ]` texty skutočným obsahom (pozri `project/02-obsah/`)
      (O nás stránka zámerne ponechaná ako [DOPLŇ] — obsah bude doplnený neskôr)
- [x] Pridať logo a favicon (pozri `project/03-dizajn/`)
- [ ] Vyriešiť odosielanie kontaktného formulára — keďže GitHub Pages je čisto statický
      hosting bez backendu, formulár momentálne nič neodošle. Možnosti:
  - [Formspree](https://formspree.io) — zadarmo pre malý objem, stačí zmeniť `action=` vo `<form>`
  - [Getform](https://getform.io) — podobné ako Formspree
  - jednoduchý `mailto:` odkaz (už je v `kontakt.html` ako záloha)
- [ ] Pridať Google Search Console / overenie vlastníctva domény (po nasadení)
- [ ] (voliteľné) Pridať analytics bez cookies (napr. Plausible/Fathom) ak chcete merať návštevnosť

## Možný budúci upgrade

Ak web časom narastie (blog, viac jazykov, zložitejšia štruktúra), zváž prechod
na statický generátor (napr. Astro) s buildom cez GitHub Actions. Princíp nasadenia
(git push → live web) ostáva rovnaký, len pribudne build krok pred publikovaním.
