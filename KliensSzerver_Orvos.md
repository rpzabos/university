# Orvos - asszisztens

## Egy orvosi rendelőben működő kliens - szerver alkalmazás implementálása.

## Alapkövetelmények
> Ezek hiányában a feladat értékelhetetlennek minősül

- Git repo használata
    - Rendszeres commit minden csapattagtól. A csapattagok a commit-jaik alapján lesznek értékelve.
- Egy solution használata
- Konvenciók alkalmazása: [NI C# Style Guide](https://github.com/ni/csharp-styleguide)
    - Java, Python stílusú elnvezések negatívan hatnak az értékelésre

## Asszisztens kliens - .NET WPF vagy Blazor frontend

> Az asszisztens kezelőfelülete, az érkező betegek adatait tudja rögzíteni

Szükséges adatok és egyéb feltételek:
- Név
    - Validáció
        - Nem lehet: üres, whitespace, különleges karakterek szűrése pl !?_-:;#
    - UNIT tesztek a validáló fv-re (Adott bemenetre megfelelő kimenetek ellnőrzése)
- Lakcím
- Tajszám `Formátum: 000 000 000`
    - Validáció
        - Formátumra és hogy csak számokat tartalmaz
    - UNIT tesztek a validáló fv-re
- Panasz rövid leírása (kötelező mezó = nem lehet üres)

## Orvos kliens - .NET WPF vagy Blazor frontend

> A orvos irodájában működik, Látja a felvett betegek listáját

Szükséges adatok és egyéb feltételek:
- Időrendi sorrendben rendezve dátum és idő szerint 
    - Note: A az adatok felvételének a sorrendje nem számít dátum szerinti rendezettségnek
- Ki tud választani egy beteget
    - Látja az adatait, tudja módosítani
    - Diagnózis felvétele
    - Tudja törölni az adott sort
## Szerver - .NET WEB API alkalmazás (önálló konzol alkalmazás)

### Kezeli és szolgáltatja az adatokat

- Adatok tárolása: Adatbázis, a DB engine szabadon választható(MSSQL, Postgre, stb) 
- Entity FWK használata (Tegyük lehetővé a reprodukálhatóságot)
- Indításkor betölti a korábbi adatokat

