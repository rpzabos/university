# Autószereló munkanyilvántartó

## Egy autószerelő műhelyben működő kliens - szerver alkalmazás implementálása.

### Alapkövetelmények
> Ezek hiányában a feladat értékelhetetlennek minősül

- Git repo
    - Rendszeres commit minden csapattagtól
- Egy solution használata
- Konvenciók alkalmazása: [NI C# Style Guide](https://github.com/ni/csharp-styleguide)
    - A package is bereferálható, de a warning-okat ki kell javítani ezesetben

## Munka felvevő kliens - .NET WPF vagy Blazor frontend

> Az ügyintéző irodájában működik.

### Az érkező ügyfelek adatait tudja felvenni

- Ügyfél neve
    - Validáció
        - Nem lehet: üres, whitespace, különleges karakterek szűrése pl !?_-:;#
- Autó típusa és rendszáma
    - Validáció
        - Nem lehet: üres, whitespace, különleges karakterek szűrése pl !?_-:;#
        - Rendszám formátuma: XXX-000
- Gyártási év
    - Validáció
        - Kötelező mező, csak számjegyek
- Munka kategória
    - Karosszéria, motor, futómű, fékberendezés
    - Validáció
        - Kötelező mező
        - A felsorolt értékek közül az egyik
- Az autó hibájának rövid leírása
    - Validáció
        - Kötelező mező
- A hiba súlyossága (1-10)
    - Validáció
        - Kötelező mező
        - 1 és 10 közötti érték
- UNIT tesztek az input validációra

### Látja a felvett munkákat

- Az adatok táblázatos formában megjelenítve
- Indításkor betölti a korábbi adatokat
- Adatok frissítésére alkalmas gomb
- A sorok a különböző kategóriák szerint rendezhetőek növekvő vagy csökkenő sorrend (dátum, abc)
- Keresés lehetőség az összes attribútum alapján. Validáció is szükséges az input mezőkre.
- Munkaóra esztimáció megjelenítése (API számolja)
- Egy kiválasztott munka adatait
    - Meg tudja nézni
    - Módosítani tudja

## Autószerelő kliens - .NET WPF vagy Blazor frontend

> Az autószerelő műhelyben működik.

### Látja a felvett munkákat

- Az adatok táblázatos formában megjelenítve
- Indításkor betölti a korábbi adatokat
- Adatok frissítésére alkalmas gomb
- A sorok a különböző kategóriák szerint rendezhetőek növekvő vagy csökkenő sorrendben (dátum, abc)
- Keresés lehetőség az összes attribútum alapján
- Munkaóra esztimáció megjelenítése (API számolja)
- Ki tud választani egy munkát
    - Aminek az állapotát változtathatja
        - `Felvett munka` -> `Elvégzés alatt` -> `Befejezett`

## Szerver - .NET WEB API alkalmazás (önálló konzol alkalmazás)

### Tárolja és szolgáltatja a bevitt adatokat

- Adatbázis (Entity Framework), relációs DB engine szabadon választható (MSSQL, Postgre, stb) 
- Munkaóra esztimáció
    - Átlagos munkaóra kategóriákra lebontva
        - Karosszéria = 3 óra
        - Motor = 8 óra
        - Futómű = 6 óra
        - Fékberendezés = 4 óra
    - Az autó életkorából származó munkaóra súlyozás
        - 0-5 év: 0.5
        - 5-10 év: 1
        - 10-20 év: 1.5
        - 20- év: 2
    - Hiba súlyosságából származó munkaóra súlyozás
        - 1-2: 0.2
        - 3-4: 0.4
        - 5-7: 0.6
        - 8-9: 0.8
        - 10: 1
    - Képlet: kategória * kor * hiba súlyossága
- Validáció szükséges backend oldalon is
- UNIT tesztek a munkaóra esztimációra