# Autószereló munkanyilvántartó

> Egy autószerelő műhelyben működő kliens - szerver alkalmazás implementálása.

## Munka felvevő kliens - .NET WPF vagy Blazor frontend

> Az ügyintéző irodájában működik.

### Az érkező ügyfelek adatait tudja felvenni

- Ügyfél neve
    - Validáció
        - Nem lehet: üres, whitespace, különleges karakterek szűrése pl !?_-:;#
    - UNIT teszt a validáló fv-re
- Autó típusa és rendszáma
    - Validáció
        - Nem lehet: üres, whitespace, különleges karakterek szűrése pl !?_-:;#
        - Rendszám formátuma: XXX-000
    - UNIT teszt a validáló fv-re
- Az autó hibájának rövid leírásá (kötelező mező = nem lehet üres)

### Látja a felvett munkákat

- Időrendi sorrendben rendezve dátum és idó szerint
- Egy kiválasztott munka adatait
    - Meg tudja nézni
    - Módosítani tudja

## Autószerelő kliens - .NET WPF vagy Blazor frontend

> Az autószerelő műhelyben működik.

### Látja a felvett munkákat

- Időrendi sorrendben rendezve dátum és idő szerint
- Ki tud választani egy munkát
    - Aminek az állapotát változtathatja
        - `Felvett munka` -> `Elvégzés alatt` -> `Befejezett`

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
