# 10 - Osztályok (Classes)

## Bevezetés

A GDScript egy objektumorientált programozási nyelv.

Ez elsőre bonyolultan hangzik, de valójában egy nagyon egyszerű ötletre épül.

Ahelyett, hogy minden adatot és logikát egyetlen scriptben tárolnánk, külön objektumokat készítünk.

Ezeket az objektumokat osztályoknak (Class) nevezzük.

Egy osztály olyan, mint egy tervrajz.

Megmondja, hogy egy adott objektumnak milyen tulajdonságai és milyen viselkedése legyen.

---

# Mi az az osztály?

Képzeljünk el egy RPG játékot.

Tele van karakterekkel.

Van:

- kereskedő;
- őr;
- boszorkány;
- boss;
- játékos.

Mindegyik karakternek lehet:

- neve;
- életereje;
- foglalkozása;
- párbeszéde.

És mindegyik tudhat például:

- beszélni;
- meghalni;
- sebződni.

Ha minden karakterhez külön scriptet írnánk, rengeteg ismétlődő kódunk lenne.

Ehelyett készítünk egy Character osztályt.

---

# Saját osztály létrehozása

Új script készítése után a script elején megadhatjuk a nevét.

```gdscript
class_name Character

extends Node
```

A `class_name` kulcsszóval a Godot globálisan elérhetővé teszi az osztályunkat.

Így később bárhol használhatjuk a projektben.

---

# Tulajdonságok

Adjunk a Character osztálynak néhány tulajdonságot.

```gdscript
class_name Character

extends Node

@export var profession: String

@export var health: int
```

Most már minden Character rendelkezik:

- foglalkozással;
- életerővel.

Az `@export` miatt ezeket az Inspectorból is módosíthatjuk.

---

# Példányok (Instances)

Az osztály önmagában még nem karakter.

Csak egy tervrajz.

Amikor létrehozunk belőle egy példányt (Instance), akkor lesz belőle egy konkrét karakter.

Például készíthetünk három Character Node-ot.

Mindegyik ugyanazzal a scripttel működik.

Viszont teljesen más értékeket kaphatnak.

| Profession | Health |
|------------|-------:|
| Merchant | 40 |
| Guard | 120 |
| Boss | 500 |

Ugyanaz az osztály.

Három különböző karakter.

---

# Függvények az osztályban

Az osztályok nem csak adatokat tárolhatnak.

Saját logikájuk is lehet.

Példa:

```gdscript
class_name Character

extends Node

@export var profession: String

@export var health: int

func die():

    health = 0

    print(profession + " died")
```

Most már minden Character tud "meghalni".

---

# Az osztály használata

Az egyik legegyszerűbb megoldás egy exportált változó használata.

```gdscript
@export var character_to_kill: Character
```

Ezután az Inspectorban egyszerűen kiválaszthatjuk, melyik Character példányra szeretnénk hivatkozni.

Majd meghívhatjuk a függvényét.

```gdscript
func _ready():

    character_to_kill.die()
```

Ebben az esetben a kiválasztott karakter életereje 0 lesz, és kiírja a konzolra:

```text
Guard died
```

(vagy annak a Characternek a nevét, amelyiket hozzárendeltük.)

---

# Miért használunk osztályokat?

Az osztályok egyik legnagyobb előnye az újrafelhasználhatóság.

Nem kell minden enemyhez, NPC-hez vagy karakterhez külön scriptet írni.

Elég egyszer megírni az alap működést.

Ezután minden példány ugyanazt a logikát használja, de saját értékekkel dolgozik.

Ez sokkal könnyebben karbantartható megoldás.

---

# Jó gyakorlatok

✔ Egy osztály egy jól meghatározott feladatot lásson el.

✔ Adjunk beszédes nevet az osztályoknak.

Például:

- Character
- Weapon
- Inventory
- Quest

✔ Az osztályok legyenek minél általánosabbak.

A konkrét különbségeket inkább a példányok értékei adják.

---

# Mit tanultunk?

Ebben a fejezetben megismertük:

- mi az az osztály;
- mire való a `class_name`;
- hogyan készítünk saját osztályt;
- mi az a példány (Instance);
- hogyan adunk tulajdonságokat egy osztályhoz;
- hogyan írunk saját függvényt egy osztályba;
- hogyan használhatjuk ugyanazt az osztályt több különböző objektumhoz.

---

## Következő fejezet

➡️ **11 - Öröklődés (Inheritance)**