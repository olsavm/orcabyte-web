# 05 — Nasadenie (ťahák)

Plné kroky sú v koreňovom `README.md`. Tu je len rýchla referencia na DNS záznamy.

## DNS záznamy pre orcabyte.sk (nastavuješ u svojho registrátora, napr. WebSupport/Active24)

| Typ | Názov/Host | Hodnota | Poznámka |
|---|---|---|---|
| A | @ (alebo orcabyte.sk) | 185.199.108.153 | GitHub Pages |
| A | @ (alebo orcabyte.sk) | 185.199.109.153 | GitHub Pages |
| A | @ (alebo orcabyte.sk) | 185.199.110.153 | GitHub Pages |
| A | @ (alebo orcabyte.sk) | 185.199.111.153 | GitHub Pages |
| CNAME | www | TVOJ-GITHUB-USERNAME.github.io. | nahraď skutočným GitHub používateľským menom |

Po pridaní záznamov treba počkať na DNS propagáciu (zvyčajne minúty až pár hodín).

## Na GitHub strane

1. Settings → Pages → Build and deployment → Source: **Deploy from a branch**
2. Branch: **main**, priečinok: **/docs**
3. Settings → Pages → Custom domain: `orcabyte.sk` → Save (GitHub si overí DNS a sám vytvorí/aktualizuje `CNAME` súbor)
4. Počkaj, kým sa objaví možnosť **Enforce HTTPS** a zaškrtni ju (certifikát vydáva GitHub automaticky, trvá to pár minút až hodín po overení domény)
