# 15 - Player movement és fizika alapok

## Bevezetés

Az előző fejezetben létrehoztuk a projekt alapjait.

Most elkészítjük az első valódi Scene-ünket, amely a játékos karakter lesz.

Ebben a fejezetben még nem a mozgás logikájára koncentrálunk, hanem arra, hogy létrehozzunk egy megfelelően felépített Player Scene-t, amely később könnyen bővíthető lesz.

---

# A Player Scene létrehozása

Hozzunk létre egy új Scene-t.

Root Node-nak válasszuk a **CharacterBody2D** Node-ot.

Ez a Node kifejezetten olyan objektumokhoz készült, amelyek mozognak és a fizikai világgal is kapcsolatba lépnek.

Nevezzük el:

```text
Player
```

---

# A CharacterBody2D tulajdonságai

Miután létrehoztuk a CharacterBody2D Node-ot, a jobb oldali **Inspector** panelen módosíthatjuk a tulajdonságait.

Minden Node rendelkezik saját Property-kkel, amelyeket itt érhetünk el.

Ezek segítségével testre szabhatjuk a működésüket anélkül, hogy egyetlen sor kódot írnánk. :contentReference[oaicite:1]{index=1}

---

# AnimatedSprite2D hozzáadása

A CharacterBody2D önmagában nem jelenik meg a képernyőn.

Ahhoz, hogy lássuk a karakterünket, szükségünk lesz egy **AnimatedSprite2D** Node-ra.

Adjuk hozzá a Player gyermekeként.

Ez fogja megjeleníteni a karakter animációit.

A Sprite Frames tulajdonságnál válasszuk ki a karakterhez tartozó sprite sheetet vagy animációs képkockákat. :contentReference[oaicite:2]{index=2}

---

# Miért használunk kész asseteket?

Természetesen minden képkockát elkészíthetnénk saját magunk is.

A legtöbb esetben azonban sokkal egyszerűbb előre elkészített asseteket használni.

Így nem kell minden animációs képkockát külön megrajzolni, és később is könnyebb módosítani vagy cserélni őket. :contentReference[oaicite:3]{index=3}

---

# Pixel Art beállítása

Ha Pixel Art grafikákkal dolgozunk, a karakter valószínűleg elmosódottnak fog tűnni.

Ennek oka, hogy a Godot alapértelmezetten szűri a textúrákat.

Ezt kikapcsolhatjuk a következő beállítással:

```text
Project
→ Project Settings
→ Rendering
→ Textures
→ Default Texture Filter
→ Nearest
```

Így a pixelek élesek maradnak, és a grafika jobban illeszkedik a Pixel Art stílushoz. :contentReference[oaicite:4]{index=4}

---

# CollisionShape2D

A CharacterBody2D csak akkor tud együttműködni a Godot fizikai rendszerével, ha rendelkezik CollisionShape2D Node-dal.

Ha ezt nem adjuk hozzá, a Godot figyelmeztetést fog megjeleníteni.

A CollisionShape2D határozza meg, hogy a karakter fizikailag mekkora területet foglal el a világban. :contentReference[oaicite:5]{index=5}

---

# A Collider mérete

A Collision Shape nem feltétlenül kell, hogy pontosan kövesse a karakter grafikáját.

Sőt, sok esetben érdemes egy kicsit kisebbre készíteni.

Ha túl nagy, játék közben zavaró lehet, mert a játékos úgy érezheti, hogy olyan dolgoknak is nekimegy, amelyekhez valójában még nem ért hozzá. :contentReference[oaicite:6]{index=6}

---

# Camera2D

Most már van egy látható karakterünk.

A következő lépés egy kamera hozzáadása.

Adjunk a Player Node gyermekeként egy **Camera2D** Node-ot.

Ez fogja meghatározni, hogy a játékos a világból mit lát.

Az **F** billentyű megnyomásával megjeleníthetjük a kamera nézetét a szerkesztőben. :contentReference[oaicite:7]{index=7}

---

# Kamera nagyítása

Alapértelmezetten a kamera túl közel lehet a karakterhez.

A Zoom Property segítségével módosíthatjuk a nagyítást.

Például:

```text
Zoom = (4, 4)
```

Így sokkal nagyobb részt láthatunk a pályából. :contentReference[oaicite:8]{index=8}

---

# Az első Script

Most már van egy karakterünk, de még nem tud mozogni.

Adjunk hozzá egy új Scriptet a CharacterBody2D Node-hoz.

A Godot felajánl egy beépített CharacterBody2D movement scriptet.

Egyelőre ezt fogjuk használni.

Később természetesen saját mozgásrendszert is készíthetünk, de kezdésnek ez tökéletes alapot ad. :contentReference[oaicite:9]{index=9}

---

# Az első probléma

Ha most elindítjuk a játékot, a karakter azonnal leesik a képernyőről.

Ennek egyszerű oka van.

A Player már rendelkezik CollisionShape2D-vel, de jelenleg nincs semmi a világban, amin fizikailag meg tudna állni. :contentReference[oaicite:10]{index=10}

---

# Ideiglenes talaj

Amíg nem készítjük el a pályát, szükségünk lesz egy egyszerű talajra.

Ehhez hozzunk létre egy **StaticBody2D** Node-ot, majd adjunk hozzá egy megfelelő CollisionShape2D-t.

A jegyzetben erre a célra a **WorldBoundaryShape2D** szerepel, amely gyors megoldást ad a világ határának kialakítására.

Ha elforgatjuk, függőleges irányban is használható. :contentReference[oaicite:11]{index=11}

---

# Miért StaticBody2D?

A StaticBody2D olyan objektumokhoz készült, amelyek nem mozognak.

Például:

- talaj;
- falak;
- sziklák;
- épületek.

A Player fizikája ezekkel fog kölcsönhatásba lépni. :contentReference[oaicite:12]{index=12}

---

# Az első mozgás

A Godot által generált alap movement script már tartalmaz mozgást és ugrást.

Alapértelmezetten:

- a nyílbillentyűkkel mozoghatunk;
- a Space billentyűvel ugorhatunk.

Ezt a rendszert később a saját igényeink szerint fogjuk módosítani. :contentReference[oaicite:13]{index=13}

---

# Előkészítés a következő fejezethez

Az ideiglenes talaj csak arra szolgált, hogy kipróbáljuk a karakter mozgását.

A következő fejezetben valódi világot fogunk építeni TileMap segítségével.

Ezért az ideiglenes talajt később eltávolítjuk. :contentReference[oaicite:14]{index=14}

---

# Mit tanultunk?

Ebben a fejezetben:

- létrehoztuk a Player Scene-t;
- megismertük a CharacterBody2D szerepét;
- hozzáadtunk egy AnimatedSprite2D-t;
- beállítottuk a Pixel Art megjelenítését;
- létrehoztuk a CollisionShape2D-t;
- hozzáadtunk egy Camera2D-t;
- létrehoztuk az első Scriptet;
- elkészítettünk egy ideiglenes talajt a mozgás kipróbálásához.

---

## Következő fejezet

➡️ **16 - World Building 1.0**