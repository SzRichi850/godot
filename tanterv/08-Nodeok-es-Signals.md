# 08 - Node-ok elérése és Signals

## Bevezetés

A játékaink egyre összetettebbek lesznek.

Egy idő után már nem elég, hogy egy Node csak önmagával foglalkozik.

Szükségünk lesz arra, hogy különböző Node-ok kommunikáljanak egymással.

Ehhez először meg kell tanulnunk, hogyan érjük el őket scriptből, majd azt is, hogyan kommunikálnak egymással a Signal rendszeren keresztül.

---

# Node elérése

Ha egy másik Node tulajdonságát vagy függvényét szeretnénk használni, először hivatkoznunk kell rá.

A legegyszerűbb módszer, hogy a Scene Tree-ből egyszerűen behúzzuk a Node-ot a scriptbe.

Ha simán behúzzuk, a Godot egy elérési utat (NodePath) készít.

Példa:

```gdscript
$Player/Weapon
```

Ez egy rövidített forma.

Valójában ugyanaz, mint:

```gdscript
get_node("Player/Weapon")
```

A `$` jel csak egy kényelmes rövidítés.

---

# @onready

Ha a Node-ot **Ctrl** nyomva tartása mellett húzzuk be a scriptbe, a Godot automatikusan létrehoz egy változót.

```gdscript
@onready var weapon: Sprite2D = $Player/Weapon
```

Az `@onready` kulcsszó biztosítja, hogy a változó csak akkor jöjjön létre, amikor a Scene összes Node-ja már betöltődött.

Ha túl korán próbálnánk elérni egy Node-ot, a Godot hibát dobna.

Ezért használjuk az `@onready` kulcsszót.

---

# NodePath

A Node-ok eléréséhez útvonalakat használunk.

Például:

```gdscript
$Player/Weapon
```

Ez azt jelenti, hogy:

- Player Node
- azon belül Weapon Node

Az útvonal mindig az aktuális Node-hoz viszonyított.

---

# NodePath hátránya

A NodePath egyszerű és gyors megoldás.

Viszont ha átnevezünk egy Node-ot vagy megváltoztatjuk a Scene felépítését, az útvonal érvénytelenné válhat.

Ezért nagyobb projektekben érdemes rugalmasabb megoldásokat használni.

---

# Exportált Node referencia

Egy Node exportálható is.

```gdscript
@export var my_node: Node
```

Ezután az Inspectorban egyszerűen hozzáhúzhatjuk a kívánt Node-ot.

Ha tudjuk, hogy csak egy adott Node típust szeretnénk elfogadni, azt is megadhatjuk.

```gdscript
@export var my_node: Sprite2D
```

Így csak Sprite2D Node rendelhető hozzá.

Ez biztonságosabb és átláthatóbb megoldás.

---

# Signals

A Signalok lényegében üzenetek, amelyeket a Node-ok egymásnak küldenek.

Arra szolgálnak, hogy jelezzék:

**"Történt valami."**

A legtöbb Node rendelkezik előre elkészített Signalokkal.

Például egy Button rendelkezik egy `pressed` Signallal.

Amikor rákattintunk a gombra, a Signal automatikusan kibocsátásra (emit) kerül.

---

# Signal csatlakoztatása

A legegyszerűbb módszer:

- kiválasztjuk a Node-ot;
- jobb oldalon a **Node / Signals** fület;
- dupla kattintás a kívánt Signalra;
- Connect.

A Godot automatikusan létrehozza a megfelelő függvényt.

Példa:

```gdscript
func _on_button_pressed() -> void:
    print("MONEY")
```

Ebben az esetben minden gombnyomáskor lefut ez a függvény.

---

# Egy Signal több helyre is kapcsolódhat

Ez a Signal rendszer egyik legnagyobb előnye.

Egyetlen Signalhoz több különböző függvény is csatlakozhat.

Amikor a Signal kibocsátásra kerül, az összes kapcsolódó függvény lefut.

Így a Node-oknak nem kell tudniuk egymás létezéséről.

Ez lazább kapcsolatot (decoupling) eredményez a rendszerben.

---

# Saját Signal

Nem csak a beépített Signalokat használhatjuk.

Sajátot is készíthetünk.

```gdscript
signal leveled_up
```

Ez létrehoz egy új Signalt.

Ezután ugyanúgy csatlakozhatunk hozzá, mint bármelyik beépített Signalhoz.

---

# Signal kibocsátása

Ha egy esemény bekövetkezik, a Signal kibocsátható.

Példa:

```gdscript
if xp >= 20:
    xp = 0
    leveled_up.emit()
```

Ebben a példában a játékos szintet lép.

A Signal értesíti az összes rá csatlakozott rendszert.

Például:

- UI
- Achievement rendszer
- Skill rendszer
- Hangok

Mindegyik reagálhat ugyanarra az eseményre.

---

# Csatlakozás kódból

Nem csak az Editorból csatlakozhatunk Signalhoz.

Kódból is megtehetjük.

```gdscript
func _ready() -> void:
    leveled_up.connect(_on_leveled_up)
```

Ha már nincs rá szükség, leválaszthatjuk.

```gdscript
leveled_up.disconnect(_on_leveled_up)
```

---

# Paraméter átadása

A Signal adatot is továbbíthat.

Példa:

```gdscript
signal leveled_up(msg)
```

Kibocsátás:

```gdscript
leveled_up.emit("GZ!")
```

Fogadás:

```gdscript
func _on_leveled_up(msg):
    print(msg)
```

Ez nagyon hasznos, mert nem csak azt jelezhetjük, hogy történt valami, hanem azt is, hogy **mi** történt.

---

# Miért jó a Signal rendszer?

Képzeljük el, hogy a játékos szintet lép.

Ha minden rendszert közvetlenül a Playerből hívnánk meg, a kód gyorsan átláthatatlanná válna.

Signal használatával a Player csak kibocsát egy eseményt.

Az összes többi rendszer pedig eldönti, hogy szeretne-e reagálni rá.

Ez sokkal tisztább és könnyebben bővíthető megoldás.

---

# Jó gyakorlatok

✔ Signalokat használjunk események jelzésére.

✔ Ne hívjunk meg feleslegesen más Node-okat közvetlenül.

✔ Ha több rendszernek is reagálnia kell ugyanarra az eseményre, Signal használata szinte mindig jobb megoldás.

✔ Használjunk beszédes Signal neveket.

Például:

- `player_died`
- `leveled_up`
- `coin_collected`

---

# Mit tanultunk?

Ebben a fejezetben megismertük:

- hogyan érjük el a Node-okat;
- mire való az `@onready`;
- hogyan működik a NodePath;
- mikor használjunk exportált Node referenciát;
- hogyan működnek a Signalok;
- hogyan készítünk saját Signalt;
- hogyan csatlakozunk hozzá;
- hogyan továbbíthatunk adatokat egy Signal segítségével.

---

## Következő fejezet

➡️ **09 - Getterek és Setterek**