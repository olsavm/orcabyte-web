# Zadanie pre Claude Code: aktualizácia webu orcabyte.sk

Tento súbor je zadanie pre teba, Claude Code, ktoré spúšťa Michal priamo v repozitári `orcabyte-web`. Priprav zmeny v priečinku `docs/` (to je to, čo sa publikuje cez GitHub Pages) presne podľa krokov nižšie. Keď skončíš, over si výsledok podľa kontrolného zoznamu na konci tohto súboru.

## Kontext (prečo sa toto mení)

Orcabyte mení úvodné zacielenie biznisu: namiesto toho, aby bol hlavnou ponukou vývoj appiek na mieru, bude hlavnou ponukou AI automatizácia firemných procesov pre malé firmy a živnostníkov na Slovensku (naprieč odvetviami, bez špecializácie na konkrétny typ podniku), doplnená o AI poradenstvo a bezplatnú úvodnú konzultáciu pre každého záujemcu. Appky na mieru ostávajú v ponuke ako ďalší krok pre klientov, ktorí z automatizácie vyrastú, ale už nie sú hlavným posolstvom webu. Michal je od teraz platcom DPH (základná sadzba na Slovensku je od 1.1.2026 23 %), takže ceny na webe musia byť jasne označené ako "bez DPH".

## Prísne pravidlo pre celý web (najvyššia priorita)

Na celom webe je absolútne zakázaný znak pitkovej čiarky "em dash" (to je tento znak: `—`). Toto neplatí len pre nový obsah, ktorý pridávaš, over aj existujúci obsah vo všetkých súboroch v `docs/` (nadpisy `<title>`, `<meta name="description">`, texty v `<body>`) a ak tam znak `—` nájdeš, nahraď ho. Nikdy ho len nezmaž tak, aby sa slová zlepili, nahraď ho prirodzeným spôsobom podľa kontextu, napríklad čiarkou, bodkou a novou vetou, spojkou "a", alebo zátvorkou. Bežná krátka pomlčka "-" (napríklad v spojeniach ako "appky na mieru") problém nie je, zakázaný je iba dlhý `—`.

Vieme, že sa `—` momentálne nachádza napríklad v `docs/index.html` (title, hero text), `docs/sluzby.html` (viacero kariet), `docs/kontakt.html` (hero text) aj v `README.md`. Prejdi všetky súbory v `docs/` a vyčisti ich. `README.md` a súbory v `project/` nie sú súčasťou publikovaného webu, ale ak tam `—` nájdeš, voliteľne ho môžeš vyčistiť tiež kvôli konzistencii.

## Úloha 1: Zrušiť stránku "O nás"

1. Zmaž súbor `docs/o-nas.html`.
2. Vo všetkých zostávajúcich súboroch v `docs/` (momentálne `index.html`, `sluzby.html`, `kontakt.html`, plus nová `cennik.html` z úlohy 2) odstráň z navigácie položku `<li><a href="o-nas.html">O nás</a></li>`.
3. Over `docs/sitemap.xml` a ak obsahuje záznam pre `o-nas.html`, odstráň ho.
4. Voliteľne (odporúčam, ale nie je to nutné): v `project/01-planovanie/brief.md` uprav "Rozsah (v1)" tak, aby už neobsahoval "O nás", a v `project/02-obsah/obsah-stranok.md` a `project/04-vyvoj/todo.md` odstráň zmienky o stránke O nás, keďže sa zrušila.

## Úloha 2: Pridať podstránku "Cenník"

Vytvor nový súbor `docs/cennik.html`. Použi rovnakú štruktúru (doctype, head, header s logom a navigáciou, footer, skripty) ako majú ostatné stránky, napríklad `docs/sluzby.html`, aby bol vzhľad konzistentný. V `<head>` nastav:

```html
<title>Cenník | Orcabyte</title>
<meta name="description" content="Orientačný cenník AI automatizácie a konzultácií pre malé firmy a živnostníkov na Slovensku. Ceny bez DPH, úvodná konzultácia zadarmo." />
```

Obsah stránky (sekcia `<main>`):

Hero sekcia:
- Nadpis: `Cenník`
- Text pod nadpisom: "Orientačné ceny za naše služby. Presný rozsah a finálnu sumu vždy potvrdíme po bezplatnej úvodnej konzultácii, podľa reálnej náročnosti vášho projektu."

Sekcia s cenami, použi rovnaký vzor ako `.card-grid` a `.card` z `sluzby.html` (jedna karta na jednu položku cenníka), v tomto poradí:

1. **Úvodná konzultácia**: cena "Zadarmo", popis "30 až 45 minút, zmapujeme váš proces a orientačne odhadneme rozsah a úsporu. Bez záväzkov."
2. **Spracovanie faktúr**: cena "od 490 € jednorazovo", popis "Automatické spracovanie a zápis faktúr do účtovníctva alebo iného systému. Voliteľný mesačný paušál od 29 €/mesiac za prevádzku a drobné úpravy."
3. **Automatizácia komunikácie**: cena "od 690 € jednorazovo", popis "Triedenie a automatické odpovede na e-maily alebo správy od zákazníkov. Voliteľný mesačný paušál od 39 €/mesiac."
4. **Reporting**: cena "od 490 € jednorazovo", popis "Automatické pravidelné reporty a prehľady z vašich dát. Voliteľný mesačný paušál od 29 €/mesiac."
5. **Plánovanie**: cena "od 390 € jednorazovo", popis "Automatizácia rezervácií, kalendára alebo pripomienok. Voliteľný mesačný paušál od 19 €/mesiac."
6. **Riešenie na mieru**: cena "podľa rozsahu, orientačne od 500 €", popis "Keď váš proces nezapadá do žiadnej z kategórií vyššie, navrhneme riešenie presne naň. Cenu potvrdíme po konzultácii."
7. **AI poradenstvo**: cena "45 až 60 € za hodinu", popis "Konzultácie k tomu, ako využiť AI vo vašej firme. K dispozícii aj ako pol-dňový workshop od 250 €."

Pod kartami pridaj poznámku (napríklad ako `<p class="lead">` alebo podobne, štylisticky konzistentne so zvyškom webu):

"Uvedené ceny sú bez DPH. Ako platca DPH k nim pripočítame DPH vo výške 23 %. Presnú cenu vám vždy potvrdíme písomne pred začiatkom prác."

Na záver stránky pridaj CTA s odkazom na kontakt, napríklad: "Nie ste si istí, čo presne potrebujete? [Dohodnite si bezplatnú konzultáciu](kontakt.html)."

Do navigácie (`<nav class="main-nav">`) vo všetkých súboroch v `docs/` nastav rovnaké poradie položiek, s príslušnou aktívnou položkou (`class="active"`) podľa toho, na ktorej stránke sa nachádzaš:

```html
<nav class="main-nav">
  <ul>
    <li><a href="index.html">Domov</a></li>
    <li><a href="sluzby.html">Služby</a></li>
    <li><a href="cennik.html">Cenník</a></li>
    <li><a href="kontakt.html">Kontakt</a></li>
  </ul>
</nav>
```

Pridaj do `docs/sitemap.xml` nový záznam pre `cennik.html` v rovnakom formáte, aký používajú existujúce záznamy pre ostatné stránky.

Ak chceš cenu v kartách vizuálne zvýrazniť, môžeš do `docs/assets/css/style.css` pridať jednoduchú triedu, napríklad:

```css
.card .price {
  font-weight: 700;
  color: var(--color-primary);
  font-size: 1.1rem;
  margin: 4px 0 12px;
}
```

a v `cennik.html` cenu obaliť do `<p class="price">...</p>`.

## Úloha 3: Prepísať podstránku "Služby" (`docs/sluzby.html`)

Nahraď obsah tak, aby presne opisoval reálnu ponuku. Zachovaj existujúcu štruktúru stránky (hero, card-grid, sekcia s postupom), len priprav nový text:

V `<head>` uprav:

```html
<title>Služby | Orcabyte</title>
<meta name="description" content="AI automatizácia firemných procesov pre malé firmy a živnostníkov na Slovensku: faktúry, komunikácia, reporting, plánovanie, riešenia na mieru a AI poradenstvo." />
```

Hero sekcia:
- Nadpis: "Čo pre vás vieme spraviť"
- Text: "Automatizujeme konkrétne procesy vo vašej firme pomocou AI, nech už podnikáte v akomkoľvek odvetví. Každý proces je iný, preto vždy začíname bezplatnou konzultáciou, v ktorej spoločne nájdeme, kde vám AI ušetrí najviac času."

Sekcia "Bezplatná úvodná konzultácia" (nová, pridaj ju ako prvú kartu alebo samostatný blok pred kategóriami automatizácie):
"Každému záujemcovi ponúkame 30 až 45 minútový rozhovor zadarmo a bez záväzkov. Zmapujeme váš súčasný proces, povieme vám, či a ako sa dá automatizovať, a pripravíme orientačnú ponuku."

Sekcia "Automatizácia podľa typu procesu" (card-grid so 4 kartami, nahraď pôvodné 3 karty):
1. **Spracovanie faktúr**: "Automatické spracovanie, kontrola a zápis faktúr do účtovníctva alebo iného systému, bez ručného prepisovania."
2. **Automatizácia komunikácie**: "Triedenie e-mailov a správ od zákazníkov, automatické návrhy odpovedí alebo úplná automatizácia bežnej komunikácie."
3. **Reporting**: "Pravidelné prehľady a reporty poskladané automaticky z vašich dát, presne vo formáte, ktorý potrebujete."
4. **Plánovanie**: "Automatizácia rezervácií, kalendára, pripomienok a jednoduchého plánovania."

Sekcia "Riešenie na mieru":
"Váš proces nezapadá do žiadnej z kategórií vyššie? Žiadny problém, navrhneme automatizáciu presne naň. Rozsah a cenu dohodneme po úvodnej konzultácii."

Sekcia "AI poradenstvo":
"Potrebujete skôr poradiť, ako firmu nasmerovať pri využívaní AI, než konkrétnu automatizáciu? Ponúkame konzultácie aj workshopy na mieru, zamerané na to, kde vo vašej prevádzke má AI zmysel a kde nie."

Sekcia "Appky a AI agenti na mieru" (zachovaj, ale skráť a daj ju až za automatizáciu, nie pred ňu):
"Pre klientov, ktorí potrebujú viac než automatizáciu jedného procesu, vyvíjame aj vlastné aplikácie, webové, mobilné alebo pre tablet, postavené presne okolo vášho use-case."

Sekcia "Ako postupujeme", uprav zoznam krokov na:
"1. Bezplatná konzultácia, spoznáme váš proces a ciele. 2. Návrh a cenová ponuka, navrhneme riešenie a rozsah. 3. Implementácia, postavíme a nasadíme riešenie. 4. Podpora, doladíme a rozširujeme podľa potreby."

Sekciu "Cenník" na konci stránky nahraď kratším textom s odkazom na novú podstránku, napríklad: "Orientačné ceny nájdete na stránke [Cenník](cennik.html)." (bez toho, aby si tam duplikoval celý cenník).

## Úloha 4: Prepísať podstránku "Domov" (`docs/index.html`)

Zachovaj existujúcu štruktúru (hero, sekcia s kartami), uprav text tak, aby odrážal novú pozíciu firmy:

V `<head>` uprav:

```html
<title>Orcabyte | AI automatizácia pre malé firmy na Slovensku</title>
<meta name="description" content="Orcabyte automatizuje firemné procesy pomocou AI pre malé firmy a živnostníkov na Slovensku: faktúry, komunikácia, reporting a plánovanie. Úvodná konzultácia zadarmo." />
```

Hero sekcia:
- Nadpis: "AI automatizácia, ktorá vám reálne ušetrí čas"
- Text: "Automatizujeme rutinné procesy vo vašej firme pomocou AI, od spracovania faktúr cez komunikáciu so zákazníkmi až po reporting a plánovanie. Pracujeme s malými firmami a živnostníkmi po celom Slovensku, bez ohľadu na odvetvie, a úvodná konzultácia je vždy zadarmo."
- Tlačidlá (zachovaj dve, len priprav nové texty): "Bezplatná konzultácia" vedie na `kontakt.html`, "Naše služby" vedie na `sluzby.html`.

Pridaj novú sekciu "Čo automatizujeme" s card-grid, 4 karty (rovnaké kategórie ako na `sluzby.html`, krátke verzie popisu):
1. **Faktúry**: "Spracovanie a zápis faktúr bez ručnej práce."
2. **Komunikácia**: "Triedenie a automatické odpovede na správy od zákazníkov."
3. **Reporting**: "Pravidelné reporty poskladané automaticky z vašich dát."
4. **Plánovanie**: "Rezervácie, kalendár a pripomienky bez ručného zadávania."

Sekciu "Prečo my" uprav na 3 kratšie dôvody:
1. **Automatizácia šitá na mieru vášho procesu**: "Nepoužívame univerzálne šablóny, riešenie navrhujeme presne podľa toho, ako reálne pracujete."
2. **Rýchle nasadenie vďaka AI**: "Bežnú automatizáciu dokážeme vďaka modernému AI vývoju nasadiť v priebehu dní, nie mesiacov."
3. **Lokálna podpora po slovensky**: "Sme firma na Slovensku, hovoríme po slovensky a sme k dispozícii na telefonáte aj osobne."

Na koniec stránky pridaj krátky CTA blok: "Nenašli ste svoj proces medzi príkladmi? Napíšte nám, poradíme, čo sa dá automatizovať. [Dohodnite si bezplatnú konzultáciu](kontakt.html)."

## Kontrolný zoznam na záver

- [ ] `docs/o-nas.html` neexistuje
- [ ] Navigácia vo všetkých stránkach v `docs/` (`index.html`, `sluzby.html`, `cennik.html`, `kontakt.html`) má presne poradie Domov, Služby, Cenník, Kontakt, bez odkazu na "O nás"
- [ ] `docs/cennik.html` existuje, obsahuje cenník vyššie a poznámku o DPH
- [ ] `docs/sitemap.xml` neobsahuje `o-nas.html`, obsahuje `cennik.html`
- [ ] `docs/sluzby.html` opisuje reálnu ponuku (konzultácia zadarmo, 4 kategórie automatizácie, riešenie na mieru, AI poradenstvo, appky na mieru)
- [ ] `docs/index.html` má novú hero sekciu a sekciu "Čo automatizujeme"
- [ ] V žiadnom súbore v `docs/` sa nenachádza znak `—` (over si to napríklad príkazom `grep -rn "—" docs/`)
- [ ] Web sa dá lokálne otvoriť (stačí otvoriť `docs/index.html` v prehliadači) a všetky odkazy v navigácii fungujú
- [ ] Zmeny commitni a pushni (`git add . && git commit -m "Aktualizácia webu: cenník, nové služby, zrušenie O nás" && git push`), GitHub Pages ich zverejní automaticky
