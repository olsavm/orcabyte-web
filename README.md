# orcabyte-web

Kostra firemného webu pre **orcabyte.sk**: statické HTML/CSS/JS stránky, bez
build kroku, nasadzované na **GitHub Pages**.

## Štruktúra repozitára

```
orcabyte-web/
├── docs/              ← TOTO sa publikuje ako web (GitHub Pages: branch main, priečinok /docs)
│   ├── index.html     ← Domov
│   ├── sluzby.html
│   ├── cennik.html
│   ├── kontakt.html
│   ├── CNAME          ← vlastná doména (orcabyte.sk)
│   ├── robots.txt
│   ├── sitemap.xml
│   └── assets/
│       ├── css/style.css
│       ├── js/main.js
│       └── img/
└── project/           ← projektová dokumentácia, NIE JE súčasťou publikovaného webu
    ├── 01-planovanie/  ← zadanie, ciele, cieľová skupina
    ├── 02-obsah/       ← skutočné texty pred preklopením do HTML
    ├── 03-dizajn/      ← poznámky k vizuálu, logo, farby
    ├── 04-vyvoj/       ← technický backlog (čo ešte doplniť)
    └── 05-nasadenie/   ← DNS záznamy a postup nasadenia (ťahák)
```

Prečo `/docs`, a nie `/src` alebo `/public`? GitHub Pages pri nastavení
"Deploy from a branch" vie publikovať **len** koreňový priečinok repozitára
alebo priečinok `/docs`, nič iné. `/docs` sme teda zvolili zámerne, aby sa
dalo zvyšné (`project/`) držať mimo publikovaného webu, bez potreby GitHub
Actions alebo build kroku.

> Poznámka: `project/` nie je zo samotného webu nikdy linkované a nepublikuje
> sa, ale pokiaľ bude repozitár **verejný** (čo GitHub Pages s vlastnou
> doménou na free pláne vyžaduje), ktokoľvek si ho vie prezrieť priamo na
> GitHub.com. Nedávaj tam teda nič citlivé.

## Prvé nasadenie: kompletný postup

### 1. Priprav si projekt lokálne

Rozbaľ tento priečinok (alebo ho stiahni cez odkaz v chate) na svoj počítač,
napr. do `~/projects/orcabyte-web`.

### 2. Vytvor repozitár na GitHube

Buď cez web (github.com → New repository → názov napr. `orcabyte-web` →
**Public** → bez README/licencie, tie už máš), alebo cez `gh` CLI, ak ho máš
nainštalovaný lokálne:

```bash
cd orcabyte-web
git init
git add .
git commit -m "Initial skeleton"
gh repo create orcabyte-web --public --source=. --remote=origin --push
```

Ak nepoužívaš `gh`, po vytvorení repozitára na githube.com spusti:

```bash
git remote add origin https://github.com/TVOJ-USERNAME/orcabyte-web.git
git branch -M main
git push -u origin main
```

### 3. Zapni GitHub Pages

V repozitári na GitHube: **Settings → Pages**

- **Source:** Deploy from a branch
- **Branch:** `main`, priečinok: **/docs**
- Ulož

Web bude o chvíľu dostupný na `https://TVOJ-USERNAME.github.io/orcabyte-web/`
(dočasná adresa, kým nepripojíš vlastnú doménu).

### 4. Zaregistruj doménu orcabyte.sk

Over dostupnosť a kúp doménu u akreditovaného registrátora, napr.
[websupport.sk/domeny](https://www.websupport.sk/domeny/) alebo
[active24.sk](https://www.active24.sk).

### 5. Nastav DNS záznamy u registrátora

| Typ | Názov/Host | Hodnota |
|---|---|---|
| A | @ | `185.199.108.153` |
| A | @ | `185.199.109.153` |
| A | @ | `185.199.110.153` |
| A | @ | `185.199.111.153` |
| CNAME | www | `TVOJ-USERNAME.github.io.` |

(`@` niektorí registrátori nazývajú "koreňová doména" alebo necháte pole
prázdne, rozhranie sa líši, princíp je rovnaký.)

DNS zmeny sa prejavia od pár minút po niekoľko hodín.

### 6. Pripoj vlastnú doménu v GitHub Pages nastaveniach

**Settings → Pages → Custom domain** → zadaj `orcabyte.sk` → Save.

GitHub si sám overí DNS a aktualizuje `docs/CNAME` (ten istý súbor už máme v
repozitári, takže je to len potvrdenie). Keď DNS prejde, zaškrtni **Enforce
HTTPS** a GitHub vydá certifikát automaticky (môže to trvať až pár hodín).

### 7. Over, že to žije

Otvor `https://orcabyte.sk` v prehliadači (aj `https://www.orcabyte.sk`, mal
by sa presmerovať).

## Ako nasadiť ďalšiu verziu

Od tejto chvíle je to jednoduché: žiadny ručný upload, žiadny FTP.

```bash
# uprav súbory v docs/
git add .
git commit -m "popis zmeny"
git push
```

GitHub Pages automaticky zverejní novú verziu do minúty od pushu.

## Čo doplniť pred ostrým spustením

Hľadaj značku `[DOPLŇ]` naprieč `docs/*.html`, je to zámerne viditeľný
placeholder pre skutočný obsah (texty, kontakt, IČO). Zoznam a návod, kde čo
doplniť, je v `project/02-obsah/`, `project/03-dizajn/` a
`project/04-vyvoj/todo.md` (vrátane riešenia pre funkčný kontaktný formulár,
statický hosting sám o sebe formulár neodošle).
