# 16 - World Building 1.0

## Bevezetés

Az előző fejezetben elkészítettük a játékos karaktert, és egy ideiglenes talajt használtunk arra, hogy kipróbáljuk a mozgást.

Most ezt lecseréljük egy valódi pályára.

Ebben a fejezetben megismerkedünk a **TileMap** rendszerrel, amely lehetővé teszi, hogy gyorsan és egyszerűen építsünk fel egy 2D világot.

---

# Mi az a TileMap?

A TileMap egy olyan Node, amely kisebb csempékből (Tile) építi fel a pályát.

Nem kell minden platformot külön Spriteként elhelyezni.

Ehelyett egy előre elkészített Tilesetből választhatunk elemeket, és ezekből "kirajzolhatjuk" a pályát.

Ez gyorsabb, átláthatóbb, és később sokkal egyszerűbb módosítani is.

---

# TileMap létrehozása

A Main Scene-ben hozzunk létre egy új **TileMapLayer** Node-ot.

Ez lesz az első rétegünk.

Nevezzük el például:

```text
Ground
```

A TileMapLayer fogja tárolni a pálya csempéit.

---

# Tileset létrehozása

A TileMap önmagában még üres.

Először létre kell hoznunk egy Tilesetet.

Az Inspectorban keressük meg a **Tile Set** tulajdonságot, majd hozzunk létre egy új TileSet erőforrást.

Ezután adjuk hozzá a pályához használni kívánt tile sprite sheetet.

---

# Atlas Source

Miután betöltöttük a sprite sheetet, a Godotnak meg kell mondanunk, hogyan darabolja fel.

Ehhez használjuk az **Atlas Source** lehetőséget.

Az Atlas Source alapján a Godot automatikusan felosztja a képet kisebb csempékre.

Ha szükséges, a csempék méretét kézzel is beállíthatjuk.

---

# Collision hozzáadása

A grafika önmagában még nem elég.

Ha azt szeretnénk, hogy a játékos meg tudjon állni a platformokon, Collisiont is kell adnunk a Tile-okhoz.

A TileSet szerkesztőben válasszuk ki a megfelelő csempét, majd adjunk hozzá Collision Polygon-t.

Ezt minden olyan Tile esetében érdemes megtenni, amelyen a játékos járhat.

---

# Az első pálya

Most már elkezdhetjük kirajzolni a pályát.

Válasszuk ki a kívánt Tile-t, majd egyszerűen fessük fel vele a talajt.

Érdemes először csak egy egyszerű, egyenes platformot készíteni.

Ha minden megfelelően működik, később bonyolultabb pályákat is építhetünk.

---

# Több Layer használata

A TileMap egyik előnye, hogy több különböző réteget is létrehozhatunk.

Például:

```text
Ground
Background
Decoration
```

Így a különböző elemeket egymástól függetlenül kezelhetjük.

Ha később módosítani szeretnénk a hátteret vagy a díszítőelemeket, nem kell a teljes pályát újraépíteni.

---

# Miért használunk Layereket?

Képzeljük el, hogy minden egyetlen Layeren lenne.

Ebben az esetben:

* a talaj;
* a háttér;
* a díszítőelemek;

mind ugyanazon a rétegen lennének.

Ez gyorsan átláthatatlanná válna.

A külön Layerek segítségével sokkal rendezettebben tudunk dolgozni.

---

# Az első teszt

Indítsuk el a játékot.

Ha minden megfelelően sikerült:

* a Player már nem esik át a talajon;
* a kamera követi a karaktert;
* szabadon mozoghatunk az elkészített platformon.

Most már valódi pályán fut a karakterünk.

---

# Mit tanultunk?

Ebben a fejezetben:

* megismertük a TileMap rendszer működését;
* létrehoztunk egy Tilesetet;
* beállítottuk az Atlas Source-ot;
* Collisiont adtunk a Tile-okhoz;
* elkészítettük az első pályát;
* megismertük a Layerek szerepét.

---

## Következő fejezet

➡️ **17 - Platformok**
