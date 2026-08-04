# 07 - Dictionary, Enum és Match

## Bevezetés

Az előző fejezetben megismertük a tömböket (Array), amelyek több adat tárolására szolgálnak.

Viszont vannak olyan helyzetek, amikor nem egy sorszám alapján szeretnénk elérni egy adatot, hanem egy név vagy kulcs alapján.

Erre szolgál a **Dictionary**.

A fejezet második részében megismerkedünk az **Enumokkal**, amelyek segítségével könnyebben kezelhetjük a különböző állapotokat, végül pedig a **Match** utasítással, amely a Godot `switch` megfelelője.

---

# Dictionary

A Dictionary kulcs–érték (Key–Value) párokat tárol.

A való életben is használunk hasonlót.

Például egy szótárban a kulcs egy szó, az érték pedig annak jelentése.

A GDScriptben ugyanígy működik.

## Dictionary létrehozása

```gdscript
var my_dict = {}
```

Ez egy üres Dictionary.

---

## Kulcs–érték párok

```gdscript
var players = {
    "Crook": 1,
    "Villain": 35,
    "Boss": 100
}
```

Ebben a példában:

- a kulcsok a játékosok nevei;
- az értékek a szintjeik.

---

## Érték lekérése

Egy adott értéket a kulcs segítségével érhetünk el.

```gdscript
print(players["Villain"])
```

Ebben az esetben a konzolra a következő kerül:

```text
35
```

---

## Érték módosítása

Egy meglévő elem módosítása egyszerű.

```gdscript
players["Villain"] = 50
```

Most már a Villain értéke 50.

---

## Új elem hozzáadása

Új kulcs–érték pár hozzáadása ugyanilyen egyszerű.

```gdscript
players["Dwayne"] = 999
```

Ha a kulcs még nem létezett, a Dictionary automatikusan létrehozza.

---

## Dictionary bejárása

A Dictionary elemein is végigmehetünk egy `for` ciklussal.

```gdscript
for username in players:
    print(username + ": " + str(players[username]))
```

Itt a ciklus a kulcsokon megy végig.

Az aktuális kulcshoz tartozó értéket a `players[username]` segítségével érjük el.

---

## Beágyazott Dictionary

Egy Dictionary tartalmazhat újabb Dictionaryket is.

```gdscript
var players = {
    "Crook": {
        "Level": 1,
        "Health": 80
    },

    "Villain": {
        "Level": 35,
        "Health": 150
    },

    "Boss": {
        "Level": 999,
        "Health": 500
    }
}
```

Lekérés:

```gdscript
print(players["Boss"]["Health"])
```

Ez nagyon hasznos lehet például:

- inventory rendszereknél;
- karakter statisztikáknál;
- mentési adatoknál.

---

# Enum

Az Enum segítségével különböző állapotokat vagy kategóriákat tudunk kezelni.

Például egy játékban lehetnek:

- Ally
- Neutral
- Enemy

Ezeket sokkal biztonságosabb Enumként tárolni, mint számként vagy szövegként.

---

## Enum létrehozása

```gdscript
enum Alignment {
    ALLY,
    NEUTRAL,
    ENEMY
}
```

Használata:

```gdscript
var unit_alignment = Alignment.ALLY
```

---

## Miért jó az Enum?

Sokan stringeket használnának.

```gdscript
var alignment = "Enemy"
```

Ez működik, de ha elgépeljük:

```gdscript
"Enmey"
```

a program nem fogja felismerni.

Az Enum ezt megakadályozza.

A Godot hibát jelez, ha nem létező állapotot próbálunk használni.

---

## Inspectorban használható Enum

Az Enum exportálható is.

```gdscript
@export var unit_alignment: Alignment
```

Így az Inspectorban kiválaszthatjuk a megfelelő állapotot.

Ez különösen hasznos például NPC-knél vagy enemy-knél.

---

## Egyedi értékek

Ha szeretnénk, az Enum elemei saját értéket is kaphatnak.

```gdscript
enum Alignment {
    ALLY = 1,
    NEUTRAL = 0,
    ENEMY = -1
}
```

Erre ritkán van szükség, de jó tudni, hogy létezik.

---

# Match

A Match a Godot `switch` utasításának megfelelője.

Lehetővé teszi, hogy egy változó értékétől függően különböző kódrészletek fussanak le.

Példa:

```gdscript
match unit_alignment:

    Alignment.ALLY:
        print("Hello, friend!")

    Alignment.NEUTRAL:
        print("I come in peace.")

    Alignment.ENEMY:
        print("TASTE MY WRATH!")

    _:
        print("Unknown alignment")
```

A `_` jelenti az alapértelmezett ágat.

Ez akkor fut le, ha egyik feltétel sem teljesül.

---

# Mikor használjuk?

A `match` különösen akkor hasznos, ha ugyanazt a változót több különböző értékre szeretnénk vizsgálni.

Például:

- karakter állapota;
- inventory item típusa;
- NPC viselkedése;
- játék nehézségi szintje.

Ilyenkor sok egymásba ágyazott `if` helyett sokkal átláthatóbb megoldást ad.

---

# Jó gyakorlatok

✔ Dictionaryt használjunk, ha kulcs alapján szeretnénk adatokat tárolni.

✔ Enumot használjunk különböző állapotok kezelésére.

✔ A Match-et akkor érdemes választani, ha ugyanazt a változót több különböző értékre vizsgáljuk.

✔ Az Enumok nevei legyenek egyértelműek és következetesek.

---

# Mit tanultunk?

Ebben a fejezetben megismertük:

- mi az a Dictionary;
- hogyan tárol kulcs–érték párokat;
- hogyan érjük el és módosítjuk az elemeit;
- hogyan működnek a beágyazott Dictionaryk;
- mire használjuk az Enumokat;
- hogyan működik a Match utasítás;
- mikor érdemes ezeket alkalmazni játékfejlesztés során.

---

## Következő fejezet

➡️ **08 - Node-ok elérése és Signals**