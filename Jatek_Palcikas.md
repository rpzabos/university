# Pálcikás játék

> .NET-es grafikus (WPF keretrendszerben írt) játék elkészítése.

## Játék leírása

[Magyar](https://hu.wikipedia.org/wiki/P%C3%A1lcik%C3%A1sj%C3%A1t%C3%A9k)

A Wikipedia nem említi, de ha egy játékos az aktuális lépésben pontot szerez (tehát bezárt egy négyzetet),
akkor a következő lépés is az övé lesz.

### Alapkövetelmények

> Ezek hiányában a feladat értékelhetetlennek minősül

- Git repo
  - Rendszeres commit minden csapattagtól
- Egy solution használata
- Konvenciók alkalmazása: [NI C# Style Guide](https://github.com/ni/csharp-styleguide)
  - A package is bereferálható, de a warning-okat ki kell javítani ezesetben

## Követelmények

### Egymás ellen lehessen játszani ugyanazon a gépen, ugyanabban az alkalmazásban

- Két játékos nevet kér be

### AI ellen lehessen játszani

- Egy játékos nevet kér be
- Kezdő játékos véletlenszerűen választva
- AI elemezési sorrend (súlyozás)
    1. 2 pontos találat (olyan oldalszakasz keresése, ami 2 db négyzet bezárását eredményezi egyidőben)
    2. 1 pontos találat
    3. Négyzet második oldalát húzza be
    4. Véletlenszerűen húz be egyet
- 3 AI nehézségi szint:
  - Nehéz: a fenti elemzési sorrendet követi az aktuális játék állapotra, az 1. legjobb lépést választja
  - Normál: a fenti elemzési sorrendet követi az aktuális játék állapotra, a 2. legjobb lépést választja
  - Könnyű: ugyanaz, mint a Normál, de 40%-os eséllyel véletlenszerűen húz be egyet
- UNIT tesztek írása az AI logikához (több eset az elemzési sorrendre, és a nehézségi szintekre is)

### Játékmenet

- Belépéskor kérjen nevet, majd ahhoz mentse az eredményeket
    - Név nem lehet: üres, whitespace, különleges karakterek szűrése pl !?_-:;#
- Kérje be a tábla méretét
  - Minimum 3x3, maximum 6x6. Az aszimmetrikusságot biztosítani kell (tehát lehet pl. 5x4-es is)
- Eredményjelző
    - Saját pontok
    - AI pontjai
    - Eltelt idő

### Játék vége

- Tárolja le az eredményeket
    - Adatok tárolása: JSON, XML vagy adatbázis (Entity Framework)
- Mindenkori eredménylista beolvasva tárolt adatokból
    - Listázza az egyes korábbi menetek adatai táblázatban (játékosok, játékosok pontjai, nyertes, eltelt idő)