# Orvos - asszisztens

> Egy orvosi rendelőben működő kliens - szerver alkalmazás implementálása.

## Asszisztens kliens - .NET WPF vagy Blazor frontend

> A asszisztens pultján működik.

### Az érkező betegeket tudja rögzíteni

- Név
    - Validáció
        - Nem lehet: üres, whitespace, különleges karakterek szűrése pl !?_-:;#
    - UNIT teszt a validáló fv-re
- Lakcím
- Tajszám `Formátum: 000 000 000`
    - Validáció
        - Formátumra és hogy csak számokat tartalmaz
    - UNIT teszt a validáló fv-re
- Panasz rövid leírása (kötelező mezó = nem lehet üres)

## Orvos kliens - .NET WPF vagy Blazor frontend

> A orvos irodájában működik.

### Látja a felvett betegek listáját

- Időrendi sorrendben rendezve dátum és idő szerint
- Ki tud választani egy beteget
    - Látja az adatait
    - Tudja módosítani
        - Diagnózis felvétele
    - Tudja törölni

## Szerver - .NET WEB API alkalmazás (önálló konzol alkalmazás)

### Tárolja és szolgáltatja a bevitt adatokat

- Adatok tárolása: JSON, XML vagy adatbázis(Entity FWK)
- Indításkor betölti a korábbi adatokat

## Egyéb követelmények

- Git repo
    - Rendszeres commit minden csapattagtól
- Egy solution használata
- Egy haladó technológia használata a felsoroltak közül (Entity FWK, Blazor, Async, MVVM)
- Konvenciók alkalmazása: [NI C# Style Guide](https://github.com/ni/csharp-styleguide)
    - Java, Python stílusú elnvezéseket ne használjatok
