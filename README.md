# LittleTourist – Interaktivní úkoly pro žáky

Webová aplikace určená pro výuku informatiky na 1. stupni ZŠ (5. třída). Žáci v ní plní interaktivní úkoly přímo ve svém webovém prohlížeči.

Živá verze: https://kocikdav.github.io/LittleTourist/

---

## O projektu

Žák se vydá na **cestu za kamarádem** a cestou vyřeší **9 úkolů z informatiky**. Příběh i úkoly jsou v češtině a procvičují látku ICT hravou a praktickou formou. Všechno běží na straně klienta (žádná instalace, žádné přihlašování, žádné ukládání dat) — každý splněný úkol na konci otevře ten další.

Úvodní stránka (`index.html`) nabízí start cesty a drobné „tajné“ tlačítko 🔑 vpravo dole, kterým se dá skočit rovnou na konkrétní úkol (např. když se žák k rozpracované cestě vrací později).

## Přehled úkolů

Každý úkol běží ve sdíleném „desktopovém" rozhraní (pošta, aplikace k úkolu, nápověda) a má **randomizovaný scénář** — nejde ho projít náhodným klikáním ani se naučit nazpaměť (princip „anti-random"). U každého úkolu je i **postupná nápověda**. Níže je popis jednotlivých úkolů a prvků, které obsahují a procvičují.

### 1. Tajné město 🔐
Kamarád Marco pošle e-mailem zašifrované jméno města. Žák šifru rozluští a napíše, kam letí.
**Prvky:** Caesarova šifra (dešifrování, posun o 2 zpět) · e-mailová schránka (styl Outlooku) · nápověda s abecední tabulkou · kontrola odpovědi.

### 2. Výběr letenky 🎫
Podle podmínek z e-mailu žák vybere v aplikaci aerolinek jedinou správnou letenku.
**Prvky:** výběr podle **více podmínek najednou** (rozpočet, max. 1 přestup, doba přestupu, odbavené zavazadlo, datum) · čtení z nabídkové tabulky · vítězná varianta je s přestupem · randomizované pořadí nabídek.

### 3. Odbavení zavazadla 🧳
Žák se odbaví na letišti podle rozhodovacího stromu od letiště.
**Prvky:** **rozvětvený rozhodovací strom (vývojový diagram) se smyčkou** (ANO/NE) · navigace na správný terminál · kontrola váhy kufru · **přebalení zakázaných věcí drag & drop** (tekutiny > 100 ml a ostré předměty) · čtení dat z panelu · randomizovaný scénář.

### 4. Stihni nástup k bráně 🛫
Na neoznačené tabuli odletů žák najde svůj let, zjistí bránu a dojde k ní včas.
**Prvky:** orientace v **tabuli odletů** · **práce s časem** (přijít včas, ne brzy/pozdě) · let s **přestupem** (dvě letenky) · rozhodování podle stavu brány · při chybě návrat k tabuli.

### 5. Výběr hotelu 🏨
Žák vybere hotel, který splňuje všechny požadavky z e-mailu, nad mapou města.
**Prvky:** splnění **více podmínek** (cena, hodnocení, snídaně, blízkost metra, volný termín) · **eliminace podle důvodu** (každý nevhodný hotel porušuje jiný požadavek) · čtení z mapy · randomizace.

### 6. Šifra pro Marca 🤫
Marco se ptá, kde se sejdete. Žák **zašifruje** název stanice u hotelu a pošle mu ho.
**Prvky:** Caesarova šifra (**šifrování, posun o 2 dopředu** — opačný směr než úkol 1) · abecední tabulka jako pomůcka · zvládnutí víceslovných názvů (mezery, pomlčka) · kontrola.

### 7. Trasa metrem 🚇
Žák hledá nejkratší cestu metrem z letiště k hotelu klikáním stanic a přestupů.
**Prvky:** **graf a hledání nejkratší cesty** (metro jako graf, počítání stanic) · **přestupy mezi linkami** · čtení mapy metra odpovídající reálnému městu (více linek, přestupní stanice) · uzná se jen **nejkratší** trasa.

### 8. Plán dne podle počasí 🗺️
Podle předpovědi žák sestaví plán dne — aktivitu na ráno, odpoledne a večer.
**Prvky:** **přiřazování podle podmínek** (denní doba × počasí) · **drag & drop** karet · randomizované počasí (hodinová předpověď, mění se po třetinách dne) · venkovní aktivity jen za hezkého počasí · aktivity se hodí k danému městu.

### 9. Sbal se na výlet 🎒
Žák se podle svého plánu a počasí sbalí na výlet — projde rozhodovací strom a zabalí batoh.
**Prvky:** **rozhodovací strom** s **kombinovanou podmínkou** (plán × počasí) · **předání dat z úkolu 8** (plán a počasí přes URL parametry; bez nich si úkol vygeneruje vlastní) · **drag & drop balení se smyčkou** · rozlišení potřebného a zbytečného (nástrahy, které patří domů).

## Struktura

```
index.html                 – úvodní rozcestník (náhodně vybere město A/B/C/D + skok na úkol)
mesta/
  a/                       – město A (stejná cesta, jiný cíl)
    01-sifra-mesto/
    02-vyber-letenky/
    03-odbaveni-kufru/
    04-vyber-gate/
    05-vyber-hotelu/
    06-sifra-stanice/
    07-trasa-metra/
    08-plan-vyletu/
    09-sbal-batoh/         – každý úkol = samostatná stránka s vlastní URL
  b/                       – město B (kopie A s jiným městem; stejná struktura)
  c/                       – město C (kopie A s jiným městem; stejná struktura)
  d/                       – město D (kopie A s jiným městem; stejná struktura)
.nojekyll                  – vypne zpracování Jekyllem na GitHub Pages
```

Cesta existuje ve **více městech** (`mesta/a`, `mesta/b`, …). Úvodní stránka vybere město **náhodně**; v menu se města označují jen jako **A, B, …**, aby neprozradila cíl cesty (ten je odpovědí na 1. úkol). Každý úkol je **samostatná stránka s vlastní URL**, takže jde otevřít i přímo a snadno se ladí.

## Technické řešení

- Čistě **statický web** — HTML, CSS a vanilla JavaScript, **bez build kroku** a bez frameworků.
- Sdílené „desktopové“ rozhraní: levý panel s aplikacemi (Pošta, Nápověda a aplikace k danému úkolu), plocha a horní lišta s postupem.
- Běží na **GitHub Pages** (větev `main`, kořen repozitáře). Všechny cesty jsou relativní, aby web fungoval i v podadresáři `/LittleTourist/`.
- Bez serveru a bez ukládání dat — žáci jen procházejí stránky a plní úkoly.

## Lokální spuštění

Stačí otevřít `index.html` v prohlížeči. Případně můžeš použít jednoduchý lokální server, např.:

```
npx serve .
```

a otevřít zobrazenou adresu.
