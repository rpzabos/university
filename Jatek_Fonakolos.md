# Fonákolós játék

> .NET-es grafikus (WPF keretrendszerben írt) játék elkészítése.

## Játék leírása

[Magyar](https://hu.wikipedia.org/wiki/Fon%C3%A1kol%C3%B3s) \
[Angol](https://en.wikipedia.org/wiki/Reversi)

## Alapkövetelmények

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
- AI elemzés
  - Először oda rakjon korongot, ahol a legtöbbet változtatja át
  - Ha több egyforma lehetőség van, akkor véletlenszerűen válasszon egyet
  - UNIT teszteket írni az AI-hoz néhány bemenetre (legalább 3 különböző lépés)

### Játékmenet

- Belépéskor kérjen nevet, majd ahhoz mentse a pontszámokat
  - Név nem lehet: üres, whitespace, különleges karakterek szűrése pl !?_-:;#
- Eredményjelző
  - Saját pontok
  - AI/Második játékos pontok
  - Eltelt idő
  - Az aktuális játékos legyen kiemelve (akinek lépnie kell)

### Pontszámítás

- A játék pontozza az egyes játékosok lépéseit mindkét játékmódban
- A pontozás a következő képpen történjen:
  - Legyen a korongoknak egy egységes alapértéke
  - Ha egyszerre több korongot fordít meg a játékos, akkor a pontszám a következő módon alakuljon: `1 * korong_érték + 2 * korong_érték + ... + n * korong_érték`, ahol `n` az átfordított korongok száma
  - A lépést követően, ha két tengelyt érintett változás (pl vízszintes és diagonális), akkor duplázzuk meg a körben számított pontokat. Ha mindhárom tengelyt érintette, akkor triplázzuk meg a pontokat (horizontális, vertikális, diagonális)
  - Ha a lépést követően az ellenfélnek nem marad korongja a pályán, akkor a győztes kapjon bónusz pontot a fentebb említettek mellé aminek értéke `100 * korong_érték * n`, ahol `n` az összes pályán lévő korong száma
  - Ha egy játékos passzol, `0` pontot kap abban a körben
- A pontszámítás rendelkezzen UNIT tesztekkel

### Játék vége

- Tárolja le az eredményeket
  - Adatok tárolása: JSON, XML vagy adatbázis(Entity Framework)
- Mindenkori eredménylista beolvasva tárolt adatokból
  - Listázza és rendezze az egyes korábbi menetek adatai táblázatban (játékosok, játékosok pontjai, nyertes, eltelt idő). A rendezés alapja a pontszám legyen, hogy egy Highscore táblát kapjunk
