# 20 - World Building 2.0

## Bevezetés

Az első pályánk már működik.

A játékos tud mozogni, ugrani, platformokon közlekedni, coinokat gyűjteni, és leesés esetén újraindul a pálya.

Most itt az ideje, hogy a világ ne csak működjön, hanem jól is nézzen ki.

Ebben a fejezetben tovább építjük a pályát különböző Tile-ok és Layerök segítségével.

---

# A pálya bővítése

Az első pálya eddig főleg a működésről szólt.

Most elkezdhetjük részletesebbé tenni.

Például:

* hosszabb platformok;
* kisebb szigetek;
* magasabb ugrások;
* több útvonal.

Így a pálya érdekesebb lesz, miközben ugyanazokat a Tile-okat használjuk.

---

# Háttérelemek

A TileMap nem csak járható platformok készítésére alkalmas.

Külön Layeren létrehozhatunk háttérelemeket is.

Például:

```text id="8x3t5g"
Background

↓

Hegyek
Fák
Felhők
```

Ezekhez általában nem tartozik Collision.

Csak a világ hangulatát javítják.

---

# Dekoráció

A pálya sokkal élettelibb lesz, ha kisebb díszítőelemeket is elhelyezünk.

Például:

* bokrok;
* virágok;
* kövek;
* táblák.

Ezek többnyire nem befolyásolják a játékmenetet, viszont sokkal természetesebbnek hat tőlük a világ.

---

# Layerök szerepe

Korábban már létrehoztunk külön Layereket.

Most látszik igazán, miért volt erre szükség.

Például:

```text id="l9kd3w"
Background

↓

Ground

↓

Decoration
```

Így minden elem a saját rétegén marad.

Ha később módosítani szeretnénk valamit, nem kell az egész pályát újraépíteni.

---

# Ismétlődő elemek

Nem szükséges minden részt teljesen egyedivé tenni.

A TileMap egyik előnye, hogy ugyanazokat a Tile-okat tetszőleges számban felhasználhatjuk.

Ez gyorsabb pályaépítést tesz lehetővé, és egységes megjelenést biztosít.

---

# Coinok és platformok elhelyezése

Most már nem csak a talajt rajzoljuk meg.

Helyezzük el az eddig elkészített Scene-eket is.

Például:

* Coin;
* Moving Platform;
* Death Zone.

Így a pálya már valódi játékszintként kezd működni.

A korábban elkészített Scene-eket egyszerűen behúzhatjuk a Main Scene-be, és ott tetszőleges helyre mozgathatjuk őket.

---

# Többször felhasználható Scene-ek

Most már több olyan Scene is van a projektünkben, amelyeket újra és újra használhatunk.

Például:

```text id="7nwy9d"
Coin

Platform

DeathZone

Player
```

Ez jól mutatja a Godot Scene rendszerének egyik legnagyobb előnyét.

Nem kell minden objektumot újra elkészíteni.

Egyszer elkészítjük, majd annyi példányt helyezünk el belőle, amennyire szükségünk van.

---

# A pálya tesztelése

Indítsuk el a játékot.

Érdemes végigmenni a teljes pályán, és figyelni arra, hogy:

* minden platform elérhető-e;
* nem lehet-e elakadni;
* minden Coin felvehető-e;
* megfelelő helyen vannak-e a Death Zone-ok.

A pályaépítés során a folyamatos tesztelés legalább olyan fontos, mint maga az építés.

---

# Mit tanultunk?

Ebben a fejezetben:

* tovább építettük a pályát;
* háttérelemeket és dekorációkat helyeztünk el;
* kihasználtuk a Layerek előnyeit;
* elhelyeztük a korábban elkészített Scene-eket;
* megismertük az újrafelhasználható Scene-ek gyakorlati előnyeit.

---

## Következő fejezet

➡️ **21 - Enemy**
