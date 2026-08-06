# 23 - Player 2.0

## Bevezetés

A Player Scene már hosszú utat tett meg.

Korábban elkészítettük:

* a mozgást;
* az ugrást;
* a kamerát;
* a Collision rendszert.

Most tovább fejlesztjük a karakterünket, hogy természetesebbnek és látványosabbnak hasson játék közben.

A cél nem új rendszer készítése, hanem a meglévő Player finomítása.

---

# Animációk használata

Eddig a karakter már megjelent a képernyőn.

Most azt szeretnénk, hogy a különböző állapotokhoz külön animációk tartozzanak.

Például:

* Idle
* Run
* Jump

Így a karakter mindig azt az animációt játssza le, amelyik megfelel az aktuális állapotának.

---

# Idle animáció

Ha a játékos nem mozog, az Idle animációt szeretnénk lejátszani.

Például:

```gdscript
if velocity.x == 0:
    animated_sprite.play("Idle")
```

Ez biztosítja, hogy a karakter ne maradjon futó animációban álló helyzetben.

---

# Futás animáció

Ha a Player vízszintesen mozog, váltsunk át a Run animációra.

```gdscript
if velocity.x != 0:
    animated_sprite.play("Run")
```

A mozgás így sokkal természetesebbnek fog hatni.

---

# Ugrás animáció

A földtől való elemelkedéskor érdemes külön animációt használni.

Ennek ellenőrzésére használhatjuk a korábban megismert:

```gdscript
is_on_floor()
```

függvényt.

Ha a Player nincs a talajon, lejátszhatjuk a Jump animációt.

---

# A Sprite tükrözése

Korábban ezt már az Enemy-nél is használtuk.

A Player esetében is szeretnénk, hogy mindig a mozgás irányába nézzen.

Például:

```gdscript
if velocity.x > 0:
    animated_sprite.flip_h = false

elif velocity.x < 0:
    animated_sprite.flip_h = true
```

Így ugyanazt a grafikát használhatjuk mindkét irányban.

---

# Az animációk sorrendje

Fontos, hogy a feltételek ne írják felül egymást.

Ha például a Player ugrik, ne induljon el ugyanabban a képkockában a Run animáció.

Érdemes először azokat az állapotokat vizsgálni, amelyek elsőbbséget élveznek.

Egy egyszerű sorrend lehet:

1. Jump
2. Run
3. Idle

Így mindig a megfelelő animáció fog látszani.

---

# A Player finomítása

Most már egy sokkal élőbb karakterünk van.

A mozgás ugyanaz maradt, de az animációknak köszönhetően sokkal természetesebbnek érződik.

Ez jól mutatja, hogy néhány kisebb fejlesztés is sokat javíthat a játékélményen.

---

# Tesztelés

Indítsuk el a játékot.

Próbáljuk ki a különböző helyzeteket:

* álljunk egy helyben;
* fussunk balra és jobbra;
* ugorjunk;
* essünk le egy platformról.

Figyeljük meg, hogy minden állapotban a megfelelő animáció jelenik-e meg.

---

# Mit tanultunk?

Ebben a fejezetben:

* külön animációkat rendeltünk a Player állapotaihoz;
* használtuk az `AnimatedSprite2D.play()` függvényt;
* tükröztük a Sprite-ot a mozgás irányának megfelelően;
* felhasználtuk az `is_on_floor()` függvényt az ugrás felismerésére;
* természetesebbé tettük a karakter működését.

---

## Következő fejezet

➡️ **24 - Szöveg**
