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

- Belépéskor kérjen nevet, majd ahhoz mentse a pontszámokat
    - Név nem lehet: üres, whitespace, különleges karakterek szűrése pl !?_-:;#
- Eredményjelző
    - Saját pontok
    - AI/Második játékos pontok
    - Eltelt idő

### Pontszámítás

- A játék pontozza az egyes játékosok lépéseit mindkét játékmódban
- A pontozás a következő képpen történjen:
  - Legyen a korongoknak egy egységes alapértéke
  - Ha egyszerre több korongot fordít meg a játékos, akkor a pontszám a következő módon alakuljon: `1 * korong_érték + 2 * korong_érték + ... + n * korong_érték`, ahol `n` az átfordított korongok száma
  - A lépést követően, ha két tengelyt érintett változás (pl vízszintes és diagonális), akkor duplázzuk meg a körben számított pontokat. Ha mindhárom tengelyt érintette, akkor triplázzuk meg a pontokat (horizontális, vertikális, diagonális)
  - Ha a lépést követően az ellenfélnek nem marad korongja a pályán, akkor a győztes kapjon bónusz pontot a fentebb említettek mellé aminek értéke `100 * korong_érték * n`, ahol `n` az összes pályán lévő korong száma
  - Ha egy játékos passzol, `0` pontot kap abban a körben
- A pontszámítás rendelkezzen unit tesztekkel

### Játék vége

- Tárolja le az eredményeket
    - Adatok tárolása: JSON, XML vagy adatbázis(Entity FWK)
- Mindenkori eredménylista beolvasva tárolt adatokból
    - Listázza és rendezze az egyes korábbi menetek adatai táblázatban (játékosok, játékosok pontjai, nyertes, eltelt idő). A rendezés alapja a pontszám legyen, hogy egy Highscore táblát kapjunk
    
### Egyéb követelmények

- Git repo
    - Rendszeres commit minden csapattagtól
- Egy solution használata
- Egy haladó technológia használata a felsoroltak közül (Entity FWK, Blazor, Async, MVVM)
- Konvenciók alkalmazása: [NI C# Style Guide](https://github.com/ni/csharp-styleguide)
    - Java, Python stílusú elnvezéseket ne használjatok
