# Zadanie pre Claude Code: zjednodušiť cenník na orcabyte.sk

Toto je doplnkové zadanie k predchádzajúcemu súboru `zadanie-pre-claude-code.md`. Týka sa iba jedného súboru: `docs/cennik.html`. Dôvod: pôvodná verzia mala pri každej kategórii automatizácie vlastnú, inú sumu za "voliteľný mesačný paušál" (29 €, 39 €, 29 €, 19 €), čo pôsobí nejasne, nie je jasné, čo presne ten paušál obsahuje, a líši sa to bezdôvodne medzi kategóriami. Cieľ je mať jednu jasne vysvetlenú voliteľnú mesačnú podporu namiesto štyroch rôznych čísel.

Nahraď celý obsah `<main>...</main>` v súbore `docs/cennik.html` týmto:

```html
<main>
  <section class="hero">
    <div class="container">
      <h1>Cenník</h1>
      <p>
        Orientačné ceny za naše služby. Presný rozsah a finálnu sumu vždy
        potvrdíme po bezplatnej úvodnej konzultácii, podľa reálnej náročnosti
        vášho projektu.
      </p>
    </div>
  </section>

  <section>
    <div class="container">
      <div class="card-grid">
        <div class="card">
          <h3>Úvodná konzultácia</h3>
          <p class="price">Zadarmo</p>
          <p>
            30 až 45 minút, zmapujeme váš proces a orientačne odhadneme rozsah a
            úsporu. Bez záväzkov.
          </p>
        </div>
        <div class="card">
          <h3>Spracovanie faktúr</h3>
          <p class="price">od 490 € jednorazovo</p>
          <p>
            Automatické spracovanie a zápis faktúr do účtovníctva alebo iného
            systému.
          </p>
        </div>
        <div class="card">
          <h3>Automatizácia komunikácie</h3>
          <p class="price">od 690 € jednorazovo</p>
          <p>
            Triedenie a automatické odpovede na e-maily alebo správy od
            zákazníkov.
          </p>
        </div>
        <div class="card">
          <h3>Reporting</h3>
          <p class="price">od 490 € jednorazovo</p>
          <p>Automatické pravidelné reporty a prehľady z vašich dát.</p>
        </div>
        <div class="card">
          <h3>Plánovanie</h3>
          <p class="price">od 390 € jednorazovo</p>
          <p>Automatizácia rezervácií, kalendára alebo pripomienok.</p>
        </div>
        <div class="card">
          <h3>Riešenie na mieru</h3>
          <p class="price">podľa rozsahu, orientačne od 500 €</p>
          <p>
            Keď váš proces nezapadá do žiadnej z kategórií vyššie, navrhneme
            riešenie presne naň. Cenu potvrdíme po konzultácii.
          </p>
        </div>
        <div class="card">
          <h3>AI poradenstvo</h3>
          <p class="price">45 až 60 € za hodinu</p>
          <p>
            Konzultácie k tomu, ako využiť AI vo vašej firme. K dispozícii aj
            ako pol-dňový workshop od 250 €.
          </p>
        </div>
      </div>
      <p class="lead">
        Uvedené ceny sú bez DPH. Ako platca DPH k nim pripočítame DPH vo výške
        23 %. Presnú cenu vám vždy potvrdíme písomne pred začiatkom prác.
      </p>
    </div>
  </section>

  <section>
    <div class="container">
      <h2>Priebežná podpora (voliteľné)</h2>
      <p class="lead">
        Po spustení ktorejkoľvek automatizácie si môžete objednať mesačnú
        podporu, jednotne
        <strong>29 € za mesiac na jednu automatizáciu</strong>, bez ohľadu na
        to, o ktorú kategóriu ide. Podpora zahŕňa:
      </p>
      <ul>
        <li>pravidelnú kontrolu, že automatizácia funguje správne,</li>
        <li>opravu v prípade výpadku alebo zmeny na strane iného softvéru,</li>
        <li>jednu drobnú úpravu mesačne v rozsahu do 30 minút práce.</li>
      </ul>
      <p>
        Podporu nie je nutné objednať hneď, dá sa pridať kedykoľvek po spustení
        aj kedykoľvek zrušiť. Ak u vás bežia viaceré automatizácie naraz, cenu
        podpory prispôsobíme spoločne pre všetky.
      </p>
    </div>
  </section>

  <section>
    <div class="container">
      <h2>Nie ste si istí, čo presne potrebujete?</h2>
      <p class="lead">
        <a href="kontakt.html">Dohodnite si bezplatnú konzultáciu</a>.
      </p>
    </div>
  </section>
</main>
```

Pripomienky, ktoré stále platia z predchádzajúceho zadania:

- Znak "—" (em dash) je na celom webe zakázaný, over, že sa v tomto novom obsahu nenachádza (nemal by, ale skontroluj).
- Hlavička (`<head>`), navigácia a pätička v `docs/cennik.html` sa nemenia, uprav iba obsah vnútri `<main>`.
- Po úprave over v prehliadači, že stránka vyzerá správne a ceny pôsobia prehľadne a zrozumiteľne.
- Commitni a pushni zmenu (`git add docs/cennik.html && git commit -m "Zjednodušenie cenníka: jedna jasná mesačná podpora namiesto rôznych paušálov" && git push`).
