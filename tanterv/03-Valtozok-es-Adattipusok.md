# 03 - Változók és adattípusok

## Bevezetés

A programozás egyik legalapvetőbb építőeleme a **változó**.

A változók arra szolgálnak, hogy adatokat tároljunk bennük.

Ha egy játékot készítünk, rengeteg olyan információ van, amit folyamatosan nyilván kell tartanunk.

Például:

- Mennyi életereje van a játékosnak?
- Mennyi pontot szerzett?
- Él-e még?
- Mi a neve?
- Milyen fegyver van nála?

Ezeket mind változókban tároljuk.

---

# Változó létrehozása

A GDScriptben a `var` kulcsszóval hozhatunk létre változót.

```gdscript
var health = 100
```

Értéket később bármikor módosíthatunk.

```gdscript
health = 50
```

Vagy akár számolhatunk is vele.

```gdscript
health += 20
health -= 10
health *= 2
health /= 2
```

A változók azért hasznosak, mert ugyanazt az adatot a program több pontján is fel tudjuk használni.

---

# Mire használunk változókat?

Játékfejlesztés során szinte mindenhez.

Például:

```gdscript
var player_name = "Knight"

var health = 100

var score = 0

var is_alive = true
```

Látszik, hogy minden változó más-más információt tárol.

---

# Scope

A Scope azt határozza meg, hogy honnan érhető el egy változó.

Ez kezdőként az egyik leggyakoribb hiba.

Ha egy változót egy `if` blokkon belül hozunk létre, akkor azt csak ott tudjuk használni.

```gdscript
if health > 0:
    var damage = 15
```

Ebben az esetben a `damage` változó csak az `if` blokkon belül létezik.

Ha több helyen is szükségünk van rá, akkor érdemes a Script elején létrehozni.

```gdscript
var damage = 15
```

Így a Script bármely részéből elérhető.

---

# Dinamikus típusok

Alapértelmezetten a GDScript dinamikusan kezeli a változókat.

Ez azt jelenti, hogy a legtöbbször nem kell megmondanunk, milyen típusú adatot tárolunk.

```gdscript
var health = 100
```

A Godot automatikusan felismeri, hogy ez egy egész szám.

---

# Alap adattípusok

A leggyakrabban használt adattípusok:

## Bool

Igaz vagy hamis.

```gdscript
var is_alive = true
```

---

## Int

Egész szám.

```gdscript
var coins = 15
```

---

## Float

Tizedes szám.

```gdscript
var speed = 2.5
```

---

## String

Szöveg.

```gdscript
var player_name = "Knight"
```

---

# Vector2 és Vector3

Játékfejlesztésben gyakran nem egyetlen számot szeretnénk tárolni, hanem egy pozíciót.

Erre szolgálnak a vektorok.

## Vector2

Két értéket tárol.

```gdscript
var position = Vector2(200,150)
```

Az első érték az X tengely.

A második az Y.

Külön is módosíthatjuk.

```gdscript
position.x += 50
```

---

## Vector3

Ugyanez három dimenzióban.

```gdscript
var position = Vector3(3,-10,5)
```

Ezt főleg 3D projektekben használjuk.

---

# Típus megadása

Ha szeretnénk, a változó típusát mi magunk is megadhatjuk.

```gdscript
var damage: int = 15
```

Így a Godot figyelni fog arra, hogy csak megfelelő típusú adat kerülhessen bele.

---

# Inferred Typing

Van egy rövidebb forma is.

```gdscript
var damage := 15
```

Ebben az esetben a Godot maga állapítja meg a típust.

A háttérben ugyanúgy statikus típus készül.

---

# Export változók

Ha egy változót szeretnénk az Inspectorból is szerkeszteni, használjuk az `@export` kulcsszót.

```gdscript
@export var speed := 250
```

Ezután a jobb oldali Inspectorban is módosíthatjuk az értékét.

Ez nagyon hasznos például:

- sebesség
- sebzés
- ugrás ereje
- életerő

beállítására.

Így nem kell minden apró módosítás miatt megnyitni a Scriptet.

---

# Konstansok

Ha egy érték soha nem fog változni, érdemes konstansként létrehozni.

```gdscript
const GRAVITY = -9.81
```

A konstansokat a program futása közben nem lehet módosítani.

Ez segít elkerülni a véletlen hibákat.

---

# Casting

Előfordulhat, hogy egy adattípust át kell alakítanunk egy másik típusra.

Ezt castingnak nevezzük.

Példa:

```gdscript
var number = 42

var text = "Meaning of life: " + str(number)
```

A `str()` számból szöveget készít.

Másik példa:

```gdscript
var pi = 3.14

print(int(pi))
```

Ebben az esetben lebegőpontos számból egész szám készül.

---

# Jó gyakorlatok

✔ Beszédes változóneveket használjunk.

✔ A közösen használt változókat a Script elején hozzuk létre.

✔ Ha lehet, adjunk típust a változóknak.

✔ Amit az Inspectorból szeretnénk állítani, használjuk `@export` változóként.

✔ Az állandó értékeket `const`-ként hozzuk létre.

---

# Mit tanultunk?

Ebben a fejezetben megismertük:

- mi az a változó;
- hogyan hozunk létre változókat;
- mire szolgál a Scope;
- milyen adattípusokat használ a GDScript;
- mi az a Vector2 és Vector3;
- hogyan működik a típusmegadás;
- mire való az `@export`;
- mikor érdemes konstansokat használni;
- hogyan alakíthatunk át adattípusokat casting segítségével.

---

## Következő fejezet

➡️ **04 - Feltételek és programlogika**