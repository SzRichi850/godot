# 02 - GDScript alapok

## Bevezetés

A GDScript a Godot saját programozási nyelve.

Magas szintű, objektumorientált, imperatív nyelv, amelyet kifejezetten a Godot Engine-höz készítettek.

A szintaxisa nagyon hasonlít a Pythonhoz, ezért könnyen olvasható és kezdők számára is gyorsan megtanulható.

Ebben a fejezetben nem az a cél, hogy minden apró részletet megtanuljunk, hanem hogy megértsük a nyelv működését és elkezdjünk benne gondolkodni.

---

# Az első script

Ahhoz, hogy egyáltalán kódot tudjunk futtatni, szükségünk van egy Node-ra.

Például létrehozunk egy sima Node-ot, majd adunk hozzá egy Scriptet.

A Godot automatikusan létrehoz néhány beépített függvényt.

Az egyik ilyen a `_ready()`.

```gdscript
func _ready():
    print("Hello World!")
```

A `_ready()` akkor fut le, amikor a Node belép a Scene Tree-be.

Ha azt akarjuk, hogy valami rögtön a játék indulásakor történjen meg, ezt a függvényt használjuk.

A `print()` egyszerűen kiír valamit a Debug Console-ra.

Ez a legegyszerűbb módja annak, hogy ellenőrizzük, lefutott-e a kódunk.

---

# GDScript szintaxis

A GDScript egyik legnagyobb előnye, hogy nagyon könnyen olvasható.

Néhány fontos szabály:

- nincs pontosvessző;
- nincsenek kapcsos zárójelek;
- a behúzás (indentálás) határozza meg a blokkokat;
- a nyelv case sensitive.

Példa:

```gdscript
if health <= 0:
    print("You DIED!")
```

Ha rossz a behúzás, a program nem fog megfelelően működni.

Ezért a GDScriptben különösen fontos a rendezett kód.

---

# Node-ok módosítása scriptből

Ha egy Node tulajdonságát szeretnénk módosítani, először szükségünk van egy hivatkozásra.

A legegyszerűbb módszer, hogy a Scene Tree-ből egyszerűen behúzzuk a Node-ot a scriptbe.

Példa:

```gdscript
$Label.modulate = Color.GREEN
```

Ebben az esetben a Label színét zöldre állítjuk.

Ha az Inspectorban rámutatunk egy Property-re, a Godot megmutatja annak scriptből használható nevét is.

Ez nagyon hasznos, amikor még nem tudjuk pontosan, melyik property-t kell módosítani.

---

# Input kezelés

A legtöbb játék valamilyen játékos inputra reagál.

Ehhez a Godot Action Systemet használja.

Először létrehozunk egy új Actiont.

```
Project
→ Project Settings
→ Input Map
```

Ezután billentyűket rendelhetünk hozzá.

Például:

- jump
- move_left
- move_right
- attack

Ha ez elkészült, a Scriptből már könnyen ellenőrizhetjük.

```gdscript
func _input(event):

    if event.is_action_pressed("jump"):
        print("Jump!")
```

Az `_input()` minden alkalommal lefut, amikor a játék valamilyen bemenetet érzékel.

Az `event` tartalmazza azt az eseményt, ami kiváltotta a függvény lefutását.

Lehet:

- billentyű
- egér
- kontroller
- stb.

---

# Kommentek

A kommentek arra valók, hogy később is emlékezzünk, mit miért csináltunk.

```gdscript
# Ez egy komment
```

A kommenteket nyugodtan használjuk.

Pár hét múlva sokkal könnyebb lesz visszaolvasni a saját kódunkat.

A Godotban a **Ctrl + K** billentyűkombinációval egyszerre több sort is ki- vagy be lehet kommentelni.

---

# Jó szokások

Már az elején érdemes néhány szabályt betartani.

- Beszédes változónevek.
- Rendezett behúzás.
- Kommenteljük a bonyolultabb részeket.
- Inkább több kisebb függvény, mint egy óriási.

Ezek nem kötelező szabályok, de hosszú távon sokkal olvashatóbb lesz tőlük a projekt.

---

# Mit tanultunk?

Ebben a fejezetben megismerkedtünk a GDScript alapjaival.

Megtanultuk:

- mi a GDScript;
- hogyan készül egy első Script;
- mire való a `_ready()`;
- hogyan működik a `print()`;
- hogyan kezeljük a játékos inputot;
- hogyan módosítunk Node-okat Scriptből;
- mire valók a kommentek;
- milyen alapvető szokásokat érdemes már az elején kialakítani.

---

## Következő fejezet

➡️ **03 - Változók és adattípusok**