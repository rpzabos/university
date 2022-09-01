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
- A könyvek táblázatos formában jelennek meg
- Adott állapot lekérdezése könyvenként
    - Bent van vagy ki van kölcsönözve
    - Kinél van kikölcsönözve
    - Mikorra kell visszavinnie
    - Az érkező ügyfélhez ki tud adni könyvet
        - Csak bent lévő könyveket tud kiadni
        - A könyv állapota megváltozik kölcsönzöttre
        - Letárolódnak az kölcsönzés adatai
            - Név
                - Validáció
                    - Nem lehet: üres, whitespace, különleges karakterek szűrése pl !?_-:;#
                - UNIT teszt a validáló fv-re
            - Visszahozás határideje
                - Validáció
                    - Későbbi mint a kölcsönzés ideje, valós dátum (pl: DateTime típus használata)
                - UNIT tesztek a validáló fv-re
- Indításkor betölti az aktuális adatokat

## Ügyfél kliens - .NET WPF vagy Blazor frontend

> A könyvtárban lévő ügyfelek szmára fenntartott gépeken működik, lekérheti a kölcsönözhető könyvek listáját

### Név megadásával tájékoztatást kap a kölcsönzéseiről

- Kikölcsönzött könyvek adatai
- Határidők
- Időrendi sorrendben dátum és idő szerint (Az adatok hozzáadási sorrendje nem minősül dátum szerinti rendezésnek)

## Szerver - .NET WEB API alkalmazás (önálló konzol alkalmazás)

### Tárolja és kezeli a bevitt adatokat

- Könyvtárban lévő könyvekkel kapcsolatos műveletek (cím, esetleg darabszám, stb.)
- Kölcsönzött könyvek kezelése (A fenti adatokat használva)
- Tárolja le az eredményeket adatbázisban, a DB engine szabadon választható (MSSQL, Postgre, stb) 
- Entity FWK használata (Tegyük lehetővé a reprodukálhatóságot)
