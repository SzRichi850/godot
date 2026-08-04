# 11 - Öröklődés (Inheritance)

## Bevezetés

Az előző fejezetben megismertük az osztályokat.

Most megnézzük, hogyan épülnek egymásra ezek az osztályok.

Ezt nevezzük öröklődésnek (Inheritance).

A Godot teljes Node rendszere erre az elvre épül.

Ha ezt megértjük, sokkal könnyebben fogjuk átlátni, miért működik úgy a Godot, ahogy.

---

# Mi az öröklődés?

Az öröklődés lehetővé teszi, hogy egy osztály egy másik osztály tulajdonságait és függvényeit is megkapja.

Valójában ezt már eddig is használtuk.

Minden scriptünk elején szerepelt például:

```gdscript
extends Node
```

vagy

```gdscript
extends CharacterBody2D
```

Ez azt jelenti, hogy a scriptünk az adott osztályból származik.

---

# Mit jelent ez a gyakorlatban?

Ha egy script ezt használja:

```gdscript
extends CharacterBody2D
```

akkor automatikusan hozzáférünk minden olyan változóhoz és függvényhez, amelyet a CharacterBody2D biztosít.

Például:

- `velocity`
- `move_and_slide()`
- `is_on_floor()`
- `get_gravity()`

Ezeket nem nekünk kellett megírni.

A CharacterBody2D osztályból örököltük őket.

---

# A Node-ok is öröklődnek

Amikor új Node-ot hozunk létre a Godotban, láthatjuk, hogy bizonyos Node-ok más Node-ok alatt jelennek meg.

Ez nem véletlen.

A Godot ezzel mutatja meg az öröklődési kapcsolatot.

Például:

```text
Node
│
├── Node2D
│     │
│     ├── Sprite2D
│     ├── Camera2D
│     ├── Area2D
│     └── CharacterBody2D
```

A CharacterBody2D tehát egy Node2D-ből származik, a Node2D pedig a Node-ból.

Ezért minden CharacterBody2D egyben Node2D is.

---

# Saját osztályok öröklődése

Nem csak a beépített Node-ok örökölhetnek.

A saját osztályaink is.

Például korábban készítettünk egy Character osztályt.

```gdscript
class_name Character

extends Node
```

Ezután a Character is megjelenik a Node listában.

Mostantól ugyanúgy használható, mint bármelyik beépített Node.

Ez azt is jelenti, hogy később akár más saját osztályokat is készíthetünk belőle.

---

# Miért jó az öröklődés?

Az öröklődés egyik legnagyobb előnye, hogy nem kell ugyanazt a kódot újra és újra megírni.

Ha egy osztály már tartalmaz egy működő megoldást, azt a leszármazott osztály automatikusan megkapja.

Ez csökkenti az ismétlődő kód mennyiségét, és könnyebben karbantarthatóvá teszi a projektet.

---

# Melyik Node-ból induljunk?

A Godotban nagyon fontos, hogy mindig a megfelelő Node típust válasszuk.

Például:

Ha egy karaktert szeretnénk mozgatni:

```gdscript
extends CharacterBody2D
```

Ha csak egy képet szeretnénk megjeleníteni:

```gdscript
extends Sprite2D
```

Ha csak egy egyszerű logikai objektumra van szükségünk:

```gdscript
extends Node
```

Mindig abból az osztályból érdemes kiindulni, amelyik már tartalmazza azokat a funkciókat, amelyekre szükségünk lesz.

---

# Öröklődés a gyakorlatban

A CharacterBody2D jó példa erre.

Ha ezt választjuk alapnak, automatikusan megkapjuk:

- mozgás kezelését;
- ütközések kezelését;
- gravitáció támogatását;
- a beépített fizikai függvényeket.

Ha ugyanezt egy sima Node-ból szeretnénk megvalósítani, szinte mindent nekünk kellene megírni.

Ezért fontos, hogy mindig jól válasszuk meg az alap osztályt.

---

# Jó gyakorlatok

✔ Mindig a feladathoz legjobban illő Node típust válasszuk.

✔ Ne használjunk túl általános Node-ot, ha létezik megfelelőbb.

✔ Használjuk ki a Godot beépített osztályait, ne találjuk fel újra a kereket.

✔ Érdemes megnézni egy Node öröklődési láncát, mert sok hasznos függvény érhető el rajta keresztül.

---

# Mit tanultunk?

Ebben a fejezetben megismertük:

- mi az öröklődés;
- mit jelent az `extends`;
- hogyan épül fel a Godot Node rendszere;
- hogyan öröklődnek a saját osztályaink;
- miért fontos a megfelelő alap Node kiválasztása.

---

## Következő fejezet

➡️ **12 - Composition és Call Down, Signal Up**