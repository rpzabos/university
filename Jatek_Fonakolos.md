# Fonákolós játék

> .NET-es grafikus (WPF keretrendszerben írt) játék elkészítése.

## Játék leírása

[Magyar](https://hu.wikipedia.org/wiki/Fon%C3%A1kol%C3%B3s) \
[Angol](https://en.wikipedia.org/wiki/Reversi)

## Követelmények

### Egymás ellen lehessen játszani ugyanazon a gépen, ugyanabban az alkalmazásban

- Két játékos nevet kér be

### AI ellen lehessen játszani

- Egy játékos nevet kér be
- Kezdő játékos véletlenszerűen választva
- AI elemzés
    - Először oda rakjon korongot, ahol a legtöbbet változtatja át
        - UNIT tesztet írni hozzá pár bemenetre
    - Véletlenszerűen helyezzen le egy korongot

### Játékmenet

- Belépéskor kérjen nevet, majd ahhoz mentse az eredményeket
    - Név nem lehet: üres, whitespace, különleges karakterek szűrése pl !?_-:;#
- Eredményjelző
    - Saját pontok
    - AI pontjai
    - Eltelt idő

### Játék vége

- Tárolja le az eredményeket
    - Adatok tárolása: JSON, XML vagy adatbázis(Entity FWK)
- Mindenkori eredménylista beolvasva tárolt adatokból
    - Listázza az egyes korábbi menetek adatai táblázatban (játékosok, játékosok pontjai, nyertes, eltelt idő)

### Egyéb követelmények

- Git repo
    - Rendszeres commit minden csapattagtól
- Egy solution használata
- Egy haladó technológia használata a felsoroltak közül (Entity FWK, Blazor, Async, MVVM)
- Konvenciók alkalmazása: [NI C# Style Guide](https://github.com/ni/csharp-styleguide)
    - Java, Python stílusú elnvezéseket ne használjatok
