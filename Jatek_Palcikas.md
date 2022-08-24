# Pálcikás játék

> .NET-es grafikus (WPF keretrendszerben írt) játék elkészítése.

## Játék leírása

[Magyar](https://hu.wikipedia.org/wiki/P%C3%A1lcik%C3%A1sj%C3%A1t%C3%A9k)

## Követelmények

### Egymás ellen lehessen játszani ugyanazon a gépen, ugyanabban az alkalmazásban

- Két játékos nevet kér be

### AI ellen lehessen játszani

- Egy játékos nevet kér be
- Kezdő játékos véletlenszerűen választva
- AI elemezési sorrend
    1. 2 pontos találat TODO részletek
    2. 1 pontos találat
    3. Négyzet második oldalát húzza be
    4. Véletlenszerűen húz be egyet

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

### Testreszabhatóság

- Tábla orientációja két fajta lehessen [KÉP](https://hu.wikipedia.org/wiki/F%C3%A1jl:P%C3%A1lcik%C3%A1sj%C3%A1t%C3%A9k_5.PNG)

### Egyéb követelmények

- Git repo
    - Rendszeres commit minden csapattagtól
- Egy solution használata
- Egy haladó technológia használata a felsoroltak közül (Entity FWK, Blazor, Async, MVVM)
- Konvenciók alkalmazása: [NI C# Style Guide](https://github.com/ni/csharp-styleguide)
    - Java, Python stílusú elnvezéseket ne használjatok
