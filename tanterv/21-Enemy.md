# 21 - Enemy

## Bevezetés

A pályánk már kezd életre kelni.

Van játékosunk, platformjaink, Coin rendszerünk és halálzónánk.

Most elkészítjük az első ellenfelet.

Ebben a fejezetben egy egyszerű Enemy-t készítünk, amely folyamatosan járőrözik két irány között.

A működése egyszerű, mégis nagyon jól bemutatja, hogyan lehet több Node együttműködéséből összerakni egy viselkedést.

---

# Új Enemy Scene

Hozzunk létre egy új Scene-t.

Root Node:

```text
CharacterBody2D
```

Mivel az Enemy is mozog, és ütközik a világgal, ugyanúgy a CharacterBody2D lesz a megfelelő választás.

---

# Az Enemy felépítése

Adjuk hozzá a szükséges Node-okat.

```text
Enemy
│
├── AnimatedSprite2D
├── CollisionShape2D
├── RayCastLeft
└── RayCastRight
```

Az AnimatedSprite2D jeleníti meg az ellenfelet.

A CollisionShape2D kezeli az ütközéseket.

A két RayCast2D segítségével az Enemy érzékelni tudja a környezetét.

---

# Mi az a RayCast2D?

A RayCast2D egy láthatatlan "sugarat" bocsát ki.

Ha ez a sugár nekiütközik egy objektumnak, azt a scriptből is érzékelhetjük.

Ebben a példában arra használjuk, hogy az Enemy felismerje:

* a falakat;
* a platform végét.

Így nem fog folyamatosan ugyanabba az irányba sétálni.

---

# A mozgás alapja

Az Enemy folyamatosan egy irányba halad.

Ehhez egy sebességváltozót használunk.

```gdscript
@export var speed := 60.0

var direction := -1
```

A `direction` határozza meg, hogy éppen balra vagy jobbra mozogjon.

---

# Irányváltás

Amikor valamelyik RayCast akadályt érzékel, az Enemy megfordul.

Például:

```gdscript
direction *= -1
```

Ha a `direction` értéke:

```text
-1
```

akkor a szorzás után:

```text
1
```

Ha pedig:

```text
1
```

akkor ismét:

```text
-1
```

Így egyetlen sorral meg tudjuk fordítani a mozgás irányát.

---

# Sprite tükrözése

Ha az Enemy megfordul, a grafikáját is érdemes megfordítani.

Erre használhatjuk az AnimatedSprite2D egyik tulajdonságát.

```gdscript
animated_sprite.flip_h = direction > 0
```

Így az Enemy mindig abba az irányba néz, amerre éppen mozog.

---

# Gravitáció

Az Enemy ugyanúgy része a fizikai világnak, mint a Player.

Ezért rá is alkalmaznunk kell a gravitációt.

A korábban használt mozgási logika itt is alkalmazható.

Így az Enemy stabilan a platformon marad, és nem lebeg a levegőben.

---

# Az Enemy elhelyezése

Mentsük el az Enemy Scene-t.

Ezután húzzuk be a Main Scene-be.

Akár több példányt is elhelyezhetünk belőle.

Mindegyik ugyanazzal a működéssel rendelkezik.

---

# Az első teszt

Indítsuk el a játékot.

Ha minden megfelelően működik:

* az Enemy elindul;
* folyamatosan járőrözik;
* falhoz érve megfordul;
* a platform szélén sem esik le;
* a grafikája mindig a mozgás irányába néz.

Most már valódi ellenfél mozog a pályán.

---

# Miért külön Scene?

Az Enemy ugyanúgy önálló Scene lett, mint:

* Player;
* Coin;
* Platform;
* Death Zone.

Ennek köszönhetően később könnyen készíthetünk többféle ellenfelet is.

Akár ugyanebből az alapból kiindulva.

Ez ismét jól mutatja, mennyire fontos a Scene-ek újrafelhasználhatósága a Godotban.

---

# Mit tanultunk?

Ebben a fejezetben:

* létrehoztunk egy Enemy Scene-t;
* használtuk a CharacterBody2D-t;
* megismertük a RayCast2D szerepét;
* elkészítettük az egyszerű járőröző mozgást;
* irányt váltottunk akadály esetén;
* tükröztük a Sprite-ot a mozgás irányának megfelelően;
* elhelyeztük az első Enemy-t a pályán.

---

## Következő fejezet

➡️ **22 - Dying 2.0**
