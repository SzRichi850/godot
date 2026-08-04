# Godot Learning Notes

> Saját tanulási jegyzetek a Godot Engine és a GDScript programozási nyelv elsajátításához.

---

## A repository célja

Ez a repository a Godot Engine és a GDScript tanulásához készült, saját tanulási folyamatra épülő jegyzeteket és gyakorlati példákat tartalmaz.

A cél nem a hivatalos dokumentáció lemásolása, hanem egy olyan könnyen követhető tananyag létrehozása, amely az alapoktól indulva fokozatosan vezeti végig az olvasót a Godot működésén, a GDScript programozási alapjain és később egy gyakorlati 2D platformer projekt elkészítésén.

A magyarázatok nagyrészt saját szavakkal készültek, ezért bizonyos fogalmak egyszerűbb, hétköznapibb módon vannak megfogalmazva.

---

# Tananyag

## 01 - Godot alapok

A Godot Engine alapvető működésének megismerése.

* Node-ok
* Scene-ek
* Scene Tree
* Root Node
* Main Scene
* Inspector és Property-k
* Assetek
* Collision
* Camera2D

`01-Godot-Alapok.md`

---

## 02 - GDScript alapok

Az első lépések a Godot saját programozási nyelvében.

* Az első Script
* `_ready()`
* `print()`
* GDScript szintaxis
* Node-ok módosítása Scriptből
* Input kezelés
* Kommentek
* Alapvető programozási szokások

`02-GDScript-Alapok.md`

---

## 03 - Változók és adattípusok

Adatok tárolása és kezelése GDScriptben.

* Változók
* Scope
* Dinamikus típusok
* `bool`
* `int`
* `float`
* `String`
* `Vector2`
* `Vector3`
* Típusmegadás
* Inferred Typing
* `@export`
* Konstansok
* Casting

`03-Valtozok-es-Adattipusok.md`

---

## 04 - Feltételek és programlogika

Döntések és feltételek kezelése.

* `if`
* `elif`
* `else`
* Összehasonlító operátorok
* Egymásba ágyazott feltételek
* `and`
* `or`
* Feltételek használata játéklogikában

`04-Feltetelek-es-Programlogika.md`

---

## 05 - Függvények

A program kisebb, újrafelhasználható részekre bontása.

* Beépített függvények
* Saját függvények
* Paraméterek
* `return`
* Visszatérési érték
* `void`
* Függvények használata játéklogikában

`05-Fuggvenyek.md`

---

## 06 - Tömbök és ciklusok

Több adat tárolása és ismétlődő műveletek végrehajtása.

* Array
* Indexelés
* Elemek módosítása
* `append()`
* `remove_at()`
* `for`
* `while`
* `break`
* `continue`
* Végtelen ciklusok

`06-Tombok-es-Ciklusok.md`

---

## 07 - Dictionary, Enum és Match

Összetettebb adatok és állapotok kezelése.

* Dictionary
* Kulcs–érték párok
* Dictionary bejárása
* Beágyazott Dictionary
* Enum
* Enum exportálása
* `match`
* Állapotok kezelése

`07-Dictionary-Enum-es-Match.md`

---

## 08 - Node-ok elérése és Signals

A különböző Node-ok közötti kommunikáció alapjai.

* Node-ok elérése
* `$`
* `get_node()`
* `@onready`
* NodePath
* Exportált Node referencia
* Beépített Signals
* Saját Signals
* `emit()`
* `connect()`
* `disconnect()`
* Paraméterek továbbítása Signal segítségével
* Decoupling

`08-Nodeok-es-Signals.md`

---

## 09 - Getterek és Setterek

Változók értékének ellenőrzése és automatikus kezelése.

* Getter
* Setter
* `clamp()`
* Setter és Signal
* Adatok átalakítása
* Értékek korlátozása

`09-Getterek-es-Setterek.md`

---

## 10 - Osztályok (Classes)

Saját újrafelhasználható objektumok létrehozása.

* Objektumorientált programozás alapjai
* Classes
* `class_name`
* Tulajdonságok
* Példányok (Instances)
* Függvények osztályokban
* Saját osztályok használata
* Újrafelhasználható logika

`10-Osztalyok.md`

---

## 11 - Öröklődés (Inheritance)

Az osztályok közötti kapcsolat és a Godot öröklődési rendszerének megértése.

* Inheritance
* `extends`
* Godot Node hierarchy
* Beépített osztályok
* Saját osztályok öröklődése
* Megfelelő alap Node kiválasztása
* Örökölt tulajdonságok és függvények

`11-Oroklodes-Inheritance.md`

---

## 12 - Composition és Call Down, Signal Up

A Godot projektek strukturálásának alapvető szemlélete.

* Composition
* Composition vs. Inheritance
* Komponensek
* Újrafelhasználható Node-ok
* Call Down
* Signal Up
* Parent–Child kommunikáció
* Sibling kommunikáció
* Signals használata rendszerek között
* Lazább kapcsolat a különböző rendszerek között
* Átláthatóbb Scene struktúrák

`12-Composition-es-Call-Down-Signal-Up.md`

---

## 13 - Hasznos GDScript függvények

Gyakran használt beépített eszközök és segédfüggvények.

* `randf()`
* `randi()`
* `randi_range()`
* `randf_range()`
* `randomize()`
* `clamp()`
* `lerp()`
* `move_toward()`
* `abs()`
* `min()`
* `max()`
* `round()`
* `floor()`
* `ceil()`
* `str()`
* `print()`

`13-Hasznos-GDScript-Fuggvenyek.md`

---

# Gyakorlati rész

Az alapok elsajátítása után a tananyag egy egyszerű **2D platformer projekt** elkészítésével folytatódik.

Itt az eddig külön-külön megtanult fogalmakat már egy valódi projektben használjuk fel.

A cél nem csak az, hogy elkészüljön egy működő játék, hanem hogy érthető legyen, hogyan kapcsolódnak össze a korábban megtanult rendszerek.

A gyakorlati rész többek között érinteni fogja:

* Player létrehozását
* CharacterBody2D használatát
* Mozgást
* Ugrást
* Gravitációt
* Animációkat
* Collision rendszert
* Camera2D-t
* TileMap használatát
* Platformokat
* Coin rendszert
* Enemy-ket
* UI-t
* Audio rendszert
* Scene-ek közötti kommunikációt
* Signalokat
* A projekt strukturálását
* Exportálást

> A gyakorlati projekt dokumentációja a tananyag következő része.

---

# Jelenlegi repository struktúra

```text
Godot-Learning-Notes/
│
├── README.md
│
├── 01-Godot-Alapok.md
├── 02-GDScript-Alapok.md
├── 03-Valtozok-es-Adattipusok.md
├── 04-Feltetelek-es-Programlogika.md
├── 05-Fuggvenyek.md
├── 06-Tombok-es-Ciklusok.md
├── 07-Dictionary-Enum-es-Match.md
├── 08-Nodeok-es-Signals.md
├── 09-Getterek-es-Setterek.md
├── 10-Osztalyok.md
├── 11-Oroklodes-Inheritance.md
├── 12-Composition-es-Call-Down-Signal-Up.md
└── 13-Hasznos-GDScript-Fuggvenyek.md
```

---

# Ajánlott tanulási sorrend

A fejezetek egymásra épülnek, ezért érdemes őket sorrendben feldolgozni.

```text
Godot alapok
      │
      ▼
GDScript alapok
      │
      ▼
Változók és adattípusok
      │
      ▼
Feltételek és programlogika
      │
      ▼
Függvények
      │
      ▼
Tömbök és ciklusok
      │
      ▼
Dictionary, Enum és Match
      │
      ▼
Node-ok és Signals
      │
      ▼
Getterek és Setterek
      │
      ▼
Osztályok
      │
      ▼
Öröklődés
      │
      ▼
Composition
      │
      ▼
Call Down, Signal Up
      │
      ▼
Hasznos GDScript funkciók
      │
      ▼
2D Platformer projekt
```

---

## Megjegyzés

A repository és a jegyzetek folyamatosan bővülnek a tanulási folyamat során.

A cél egy olyan gyakorlatorientált Godot tananyag kialakítása, amely nem csak azt mutatja meg, **hogyan** kell valamit megcsinálni, hanem ahol szükséges, azt is elmagyarázza, **miért** úgy érdemes megoldani.
