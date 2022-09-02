# Könyvtári nyilvántartó

> Egy könyvtárban működő kliens - szerver alkalmazás implementálása.

## Alapkövetelmények
> Ezek hiányában a feladat értékelhetetlennek minősül

- Git repo használata
    - Rendszeres commit minden csapattagtól. A csapattagok a commit-jaik alapján lesznek értékelve.
- Egy solution használata
- Konvenciók alkalmazása: [NI C# Style Guide](https://github.com/ni/csharp-styleguide)
    - Java, Python stílusú elnvezések negatívan hatnak az értékelésre
## Könyvtáros kliens - .NET WPF vagy Blazor frontent

> A könyvtáros pultján működik, látja a könyvtárban lévő könyvek listáját

### Követelmények:
- A tagok táblázatos formában jelennek meg
    - Új tagot tud hozzáadni
    - Meg tudja nézni a tagok adatait
        - Látja a kikölcsönzött könyveket
        - Legyen kiemelve ha egy könyv nem lett visszaadva időben  
- A könyvek táblázatos formában jelennek meg
    - Adott állapot lekérdezése könyvenként
        - Bent van vagy ki van kölcsönözve
        - Kinél van kikölcsönözve
        - Mikorra kell visszavinnie
- Az érkező ügyfélhez ki tud adni vagy visszavenni könyvet
    - Csak bent lévő könyveket tud kiadni
    - A könyv állapota megváltozik kölcsönzöttre
    - Letárolódnak az kölcsönzés adatai

## Ügyfél kliens - .NET WPF vagy Blazor frontend

> A könyvtárban lévő ügyfelek szmára fenntartott gépeken működik, lekérheti a kölcsönözhető könyvek listáját

### Név megadásával tájékoztatást kap a kölcsönzéseiről
- A kölcsönözhető könyvek táblázatos formában jelennek meg
    - Adott állapot lekérdezése könyvenként
        - Bent van vagy ki van kölcsönözve
        - Kinél van kikölcsönözve
        - Mikorra kell visszavinnie
- Az általa kikölcsönzött könyvek adatai
- Határidők
- Időrendi sorrendben dátum és idő szerint rendezve (Az adatok hozzáadási sorrendje nem minősül dátum szerinti rendezésnek)

## Szerver - .NET WEB API alkalmazás (önálló konzol alkalmazás)

### Tárolja és kezeli a bevitt adatokat

- Könyvtárban lévő könyvekkel kapcsolatos műveletek (cím, esetleg darabszám, stb.)
- Kölcsönzött könyvek kezelése
- Tárolja le az adatokat adatbázisban, a DB engine szabadon választható (MSSQL, Postgre, stb) 
    - Könyvek adatai
        - Cím
        - Szerző
        - Kiadó
        - Leltári szám
        - Kiadás éve
    - Könyvtár tagok adatai
        - Név
            - Nem lehet: üres, whitespace, különleges karakterek szűrése pl !?_-:;#
            - UNIT tesztek a validáló fv-re
        - Lakcím
        - Olvasószám
        - Születési dátum
    - Kölcsönzések adatai
        - Olvasószám (Tag)
        - Leltári szám (Könyv)
        - Kölcsönzés ideje
        - Visszahozás határideje
            - Csak későbbi dátum lehet mint a kölcsönzés ideje (DateTime típus használata)
            - UNIT tesztek a validáló fv-re
- Entity FWK használata (Tegyük lehetővé a reprodukálhatóságot)
