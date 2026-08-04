# 13 - Hasznos GDScript függvények

## Bevezetés

A GDScript rengeteg beépített függvényt biztosít, amelyek megkönnyítik a mindennapi fejlesztést.

Ezeket nem kell külön megírnunk, elég ismernünk a működésüket.

Ebben a fejezetben néhány gyakran használt beépített függvényt nézünk meg.

---

# Random számok

Játékfejlesztésben nagyon gyakran van szükség véletlenszerű értékekre.

Például:

- loot dobás;
- enemy spawn;
- kritikus sebzés;
- véletlenszerű irány;
- AI döntések.

---

## randf()

A `randf()` egy 0 és 1 közötti lebegőpontos számot ad vissza.

```gdscript
print(randf())
```

Példa:

```text
0.372

0.912

0.184
```

Minden futáskor más eredményt kaphatunk.

---

## randi()

Egész számot ad vissza.

```gdscript
print(randi())
```

Általában nem önmagában használjuk, hanem valamilyen tartományban.

---

## randi_range()

Ha egy adott intervallumban szeretnénk egész számot kapni.

```gdscript
var damage = randi_range(10,20)
```

Ebben az esetben a sebzés mindig 10 és 20 közé esik.

---

## randf_range()

Lebegőpontos szám tartományban.

```gdscript
var speed = randf_range(2.0,5.0)
```

Ez például jól használható:

- enemy sebesség;
- ugrás magassága;
- lövedék szórása.

---

# Randomize

A játék elején érdemes meghívni.

```gdscript
func _ready():

    randomize()
```

Enélkül minden indításkor ugyanazt a véletlenszám-sorozatot kaphatjuk.

---

# clamp()

A `clamp()` egy értéket egy megadott tartományon belül tart.

```gdscript
health = clamp(health,0,100)
```

Ez különösen hasznos:

- életerő;
- mana;
- stamina;
- hangerő.

---

# lerp()

A `lerp()` két érték között számol átmenetet.

```gdscript
var x = lerp(0.0,100.0,0.5)
```

Az eredmény:

```text
50
```

Nagyon gyakran használjuk:

- kamera mozgatás;
- UI animáció;
- sima mozgás.

---

# move_toward()

A `move_toward()` fokozatosan közelít egy értéket egy másikhoz.

```gdscript
speed = move_toward(speed, max_speed, acceleration)
```

Ez természetesebb mozgást eredményez.

---

# abs()

Az abszolút értéket adja vissza.

```gdscript
print(abs(-15))
```

Eredmény:

```text
15
```

---

# min() és max()

A kisebb illetve nagyobb értéket adják vissza.

```gdscript
print(min(10,3))
```

```text
3
```

```gdscript
print(max(10,3))
```

```text
10
```

---

# round(), floor(), ceil()

Számok kerekítésére használhatók.

```gdscript
round(5.6)
```

↓

```text
6
```

```gdscript
floor(5.9)
```

↓

```text
5
```

```gdscript
ceil(5.1)
```

↓

```text
6
```

---

# str()

Szám vagy más adattípus szöveggé alakítása.

```gdscript
var health = 50

print("Health: " + str(health))
```

---

# print()

A legegyszerűbb hibakereső eszköz.

```gdscript
print(player.position)
```

Fejlesztés közben nagyon sokat használjuk.

---

# Jó gyakorlatok

✔ Használjuk a Godot beépített függvényeit, mielőtt saját megoldást írnánk.

✔ Fejlesztés közben bátran használjuk a `print()` függvényt hibakereséshez.

✔ A `clamp()` és a `move_toward()` sok gyakori problémára egyszerű megoldást kínálnak.

✔ Véletlenszám-generálás előtt gondoskodjunk a megfelelő inicializálásról.

---

# Mit tanultunk?

Ebben a fejezetben megismertük néhány gyakran használt GDScript beépített függvény működését.

Ezek a függvények megkönnyítik a fejlesztést, csökkentik a saját kód mennyiségét, és sok gyakori feladatra biztosítanak kész megoldást.

---

## Következő fejezet

➡️ **2D Platformer projekt**