# LittleTourist – Interaktivní úkoly pro žáky

Webová aplikace určená pro výuku informatiky na 1. stupni ZŠ (5. třída). Žáci v ní plní interaktivní úkoly přímo ve svém webovém prohlížeči.

Živá verze: https://kocikdav.github.io/LittleTourist/

---

## O projektu

Žák se vydá na **cestu za kamarádem** a cestou vyřeší **7 úkolů z informatiky**. Příběh i úkoly jsou v češtině a procvičují látku ICT hravou a praktickou formou. Všechno běží na straně klienta (žádná instalace, žádné přihlašování, žádné ukládání dat) — každý splněný úkol na konci otevře ten další.

Úvodní stránka (`index.html`) nabízí start cesty a drobné „tajné“ tlačítko 🔑 vpravo dole, kterým se dá skočit rovnou na konkrétní úkol (např. když se žák k rozpracované cestě vrací později).

## Přehled úkolů

| # | Úkol | Procvičuje |
|---|------|------------|
| 1 | **Tajné město** | Caesarova šifra (kódování/dekódování) |
| 2 | **Výběr letenky** | výběr podle podmínek (rozpočet, přestup, datum…) |
| 3 | **Odbavení zavazadla** | rozvětvený rozhodovací strom se smyčkou |
| 4 | **Stihni nástup k bráně** | orientace na tabuli, práce s časem a přestupem |
| 5 | **Výběr hotelu** | splnění požadavků, čtení z mapy |
| 6 | **Trasa metrem** | hledání nejkratší cesty (graf, přestupy) |
| 7 | **Plán dne podle počasí** | přiřazování podle podmínek (drag & drop) |

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
    06-trasa-metra/
    07-plan-vyletu/        – každý úkol = samostatná stránka s vlastní URL
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
