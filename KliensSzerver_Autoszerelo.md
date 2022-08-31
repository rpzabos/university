# Autószereló munkanyilvántartó

## Egy autószerelő műhelyben működő kliens - szerver alkalmazás implementálása.

## Alapkövetelmények
> Ezek hiányában a feladat értékelhetetlennek minősül

- Git repo használata
    - Rendszeres commit minden csapattagtól. A csapattagok a commit-jaik alapján lesznek értékelve.
- Egy solution használata
- Konvenciók alkalmazása: [NI C# Style Guide](https://github.com/ni/csharp-styleguide)
    - Java, Python stílusú elnvezések negatívan hatnak az értékelésre

## Munka felvevő kliens - .NET WPF vagy Blazor frontend

> Az ügyintéző irodájában működik, az érkező ügyfelek adatait tudja kezelni

### Felhasználói felület, ahol az ügyintéző kezeli a felvett munkákat
- Az adatok táblázatos formában jelenjenek meg
- Indításkor betölti a korábbi adatokat is
- Adattábla frissítésére alkalmas gomb
- A sorok a különböző kategóriák szerint rendezhetőek növekvő vagy csökkenő sorrend (dátum, abc)
- Keresés lehetőség az összes attribútum alapján
- Munkaóra esztimáció megjelenítése (API számolja)
- Egy kiválasztott munka adatait
    - Meg tudja nézni
    - Módosítani tudja

### Szükséges adatok és azok validálása:
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
    - Adott bemeneti értékekhez megfelelő értéket adnak vissza a metódusok
## Autószerelő kliens - .NET WPF vagy Blazor frontend

> Az autószerelő műhelyben működik, látja a felvett munkákat

### Felhasználói felület, ahol az ügyintéző látja a felvett munkákat
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

- Adatbázis, DB engine szabadon választható (MSSQL, Postgre, stb) 
- Entity FWK használata (Tegyük lehetővé a reprodukálhatóságot)
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