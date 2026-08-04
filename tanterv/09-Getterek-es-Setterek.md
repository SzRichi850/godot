# 09 - Getterek és Setterek

## Bevezetés

A legtöbb változót egyszerűen létrehozzuk, majd tetszőlegesen módosítjuk.

Bizonyos esetekben azonban szeretnénk, hogy egy változó módosításakor automatikusan történjen még valami.

Például:

- ne lehessen 100 fölé növelni az életerőt;
- ne mehessen 0 alá;
- frissüljön a felhasználói felület;
- küldjünk egy Signalt más rendszereknek.

Erre szolgálnak a Getterek és Setterek.

---

# Mi az a Setter?

A Setter minden alkalommal lefut, amikor módosítjuk egy változó értékét.

Ez lehetőséget ad arra, hogy ellenőrizzük vagy módosítsuk az új értéket, mielőtt eltárolnánk.

Példa:

```gdscript
var health := 100:
    set(value):
        health = clamp(value, 0, 100)
```

Ebben a példában a `health` értéke soha nem lehet kisebb 0-nál vagy nagyobb 100-nál.

---

# A clamp()

A `clamp()` függvény egy értéket egy megadott tartományon belül tart.

Szintaxisa:

```gdscript
clamp(érték, minimum, maximum)
```

Példa:

```gdscript
health = clamp(value, 0, 100)
```

Ha:

```gdscript
health = -50
```

akkor a tárolt érték:

```text
0
```

Ha:

```gdscript
health = 250
```

akkor a tárolt érték:

```text
100
```

Ez egy egyszerű és biztonságos módja annak, hogy korlátozzuk a változók értékét.

---

# Setter és Signal

A Setter egyik legnagyobb előnye, hogy nemcsak módosíthatjuk az értéket, hanem más rendszereket is értesíthetünk róla.

Először hozzunk létre egy Signalt.

```gdscript
signal health_changed(new_health)
```

Ezután a Setterben kibocsátjuk.

```gdscript
var health := 100:
    set(value):
        health = clamp(value, 0, 100)
        health_changed.emit(health)
```

Így minden alkalommal, amikor megváltozik a játékos élete, a Signal automatikusan értesíti a többi rendszert.

Például:

- UI;
- Health Bar;
- Hangok;
- Effektek.

---

# Getter

A Getter akkor fut le, amikor lekérjük egy változó értékét.

Gyakran arra használjuk, hogy egy értéket átalakítsunk, mielőtt visszaadnánk.

Példa:

```gdscript
var chance := 0.2

var chance_percent: int:
    get:
        return chance * 100
```

Ebben a példában a `chance` lebegőpontos számként van eltárolva.

Amikor azonban lekérjük a `chance_percent` változót, már százalékos formában kapjuk vissza.

---

# Getter és Setter együtt

A két megoldás együtt is használható.

```gdscript
var chance := 0.2

var chance_percent: int:

    get:
        return chance * 100

    set(value):
        chance = float(value) / 100.0
```

Használata:

```gdscript
chance_percent = 40
```

Ebben az esetben a háttérben a `chance` értéke 0.4 lesz.

A Getter és Setter elrejti ezt az átalakítást, így a kód olvashatóbb marad.

---

# Mikor érdemes használni?

Gettereket és Settereket akkor érdemes használni, ha:

- korlátozni szeretnénk egy változó értékét;
- automatikusan szeretnénk Signalokat küldeni;
- szeretnénk átalakítani az adatot;
- szeretnénk megakadályozni a hibás értékeket.

Nem szükséges minden változóhoz Gettert vagy Settert készíteni.

Csak ott használjuk őket, ahol valóban előnyt jelentenek.

---

# Jó gyakorlatok

✔ Használjunk `clamp()` függvényt, ha egy értéknek meghatározott tartományban kell maradnia.

✔ Ha egy változó módosítása más rendszereket is érint, érdemes Signal segítségével értesíteni őket.

✔ Gettereket inkább értékek átalakítására használjunk.

✔ Setterekben kerüljük a túl sok logikát, maradjanak egyszerűek és könnyen követhetők.

---

# Mit tanultunk?

Ebben a fejezetben megismertük:

- mi az a Setter;
- mi az a Getter;
- hogyan működik a `clamp()`;
- hogyan használhatunk Signalokat Setterekkel;
- mikor érdemes Gettereket és Settereket alkalmazni.

---

## Következő fejezet

➡️ **10 - Osztályok és objektumorientált programozás**