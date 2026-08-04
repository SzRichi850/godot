# 01 - Godot alapok

## Bevezetés

Mielőtt játékot tudnánk készíteni Godotban, meg kell értenünk, hogyan épül fel maga az engine.

A Godot egyik legnagyobb előnye, hogy szinte minden ugyanarra az alapelvre épül: **Node-okból** építjük fel a játékot, ezeket pedig **Scene-ekbe** szervezzük.

Ha ezt a két fogalmat megértjük, a Godot működésének nagy része már érthetővé válik.

---

# Node

Ahhoz, hogy bármit készíteni tudjak Godotban, **Node-okat használunk**.

Ha enemyt akarunk készíteni → Node.

Ha menüt szeretnénk → Node.

Ha játékos karaktert készítünk → Node.

Ha kamerát vagy hangot akarunk → szintén Node.

A Node-ok a játék alapvető építőkockái.

Minden Node egy adott feladatra készült. Vannak olyanok, amelyek grafikát jelenítenek meg, mások fizikát kezelnek, animációkat játszanak le vagy éppen hangokat kezelnek.

Néhány gyakori Node:

- Sprite2D
- AnimatedSprite2D
- CharacterBody2D
- StaticBody2D
- Area2D
- Camera2D
- AudioStreamPlayer2D
- TileMap

A Node-ok tovább bővíthetők saját script segítségével, így nemcsak a beépített működésüket használhatjuk, hanem saját logikát is adhatunk hozzájuk.

---

# Scene

Ha mindent egyetlen helyre tennénk, a projekt nagyon gyorsan átláthatatlanná válna.

Ezért használjuk a **Scene** rendszert.

A Scene lehetővé teszi, hogy a Node-okat egy logikai egységbe szervezzük.

Egy Scene lehet például:

- Player
- Enemy
- Coin
- Platform
- Menü
- Fegyver
- Egy teljes pálya

A Scene-ek egymásba is helyezhetők.

Ezt **Scene Nestingnek** nevezzük.

Példa:

```text
Level1
│
├── Player
├── Platform
├── Coin
└── Enemy
```

A Scene-ek újra felhasználhatók.

Ha ugyanazt a Coin Scene-t több pályán is használjuk, akkor elegendő egyszer módosítani, és a változás mindenhol megjelenik.

Ez az egyik legerősebb tulajdonsága a Godotnak.

---

# Scene Tree

Minden Node és minden Scene egy fa szerkezetben helyezkedik el.

Ezt nevezzük **Scene Tree-nek**.

```text
Root
│
├── Player
│   ├── AnimatedSprite2D
│   ├── CollisionShape2D
│   └── Camera2D
│
├── World
│
└── UI
```

A hierarchia tetején mindig található egy **Root** Node.

Ez tartalmazza a teljes jelenetet és minden további Node ebből ágazik le.

A Node-ok között szülő–gyerek kapcsolat alakul ki (Parent → Child).

Ez a kapcsolat később a scriptelés során is fontos lesz.

---

# Main Scene

A Godotnak tudnia kell, hogy melyik Scene induljon el a játék elindításakor.

Ezt nevezzük **Main Scene-nek**.

Ez általában a teljes játék belépési pontja.

Ha nincs Main Scene beállítva, a projekt nem tud elindulni.

---

# Inspector és Property-k

Miután kiválasztottunk egy Node-ot, a jobb oldali Inspector panelen módosíthatjuk annak tulajdonságait.

Itt állíthatjuk például:

- pozíció
- méret
- forgatás
- textúra
- animáció
- fizikai beállítások
- collision rétegek
- kamera beállítások

Sok olyan tulajdonság, amit itt kézzel módosítunk, később scriptből is elérhető.

---

# Assetek

A játék grafikája általában külső assetekből áll.

Ezek lehetnek:

- karakterek
- hátterek
- animációk
- csempék (Tileset)
- ikonok

Ha pixel artot használunk, alapértelmezetten a Godot elmoshatja a képet.

Ennek javításához:

```
Project
→ Project Settings
→ Textures
→ Default Texture Filter
→ Nearest
```

Ez kikapcsolja a szűrést, így a pixel art éles marad.

---

# Collision

A fizikai Node-oknak szükségük van Collision Shape-re.

Például:

- CharacterBody2D
- StaticBody2D
- Area2D

Ha egy fizikai Node nem rendelkezik Collision Shape-pel, a Godot figyelmeztetést jelenít meg.

A Collision Shape-eknek nem kell minden esetben pontosan követniük a grafikát.

Sőt, sok esetben jobb, ha egy kicsit kisebbek, mert így természetesebbnek érződik az ütközés.

---

# Kamera

Miután elkészült a játékos, szükségünk lesz egy kamerára.

Erre szolgál a **Camera2D** Node.

A kamera határozza meg, hogy a játékos mit lát a játékból.

Hasznos beállítások:

- Zoom
- Position
- Limit
- Smoothing

Az **F** billentyű segítségével könnyen megtekinthető a kamera nézete az editorban.

---

# Összefoglalás

Ebben a fejezetben megismertük a Godot működésének legalapvetőbb építőelemeit.

Megtanultuk:

- mi az a Node;
- hogyan működik a Scene rendszer;
- mi az a Scene Tree;
- mire szolgál a Root Node;
- hogyan használjuk az Inspectort;
- hogyan kezeljük az asseteket;
- miért van szükség Collision Shape-ekre;
- hogyan működik a Camera2D.

Ezekre az alapokra épül a teljes Godot fejlesztési folyamat.

---

## Következő fejezet

➡️ **02 - GDScript alapok**