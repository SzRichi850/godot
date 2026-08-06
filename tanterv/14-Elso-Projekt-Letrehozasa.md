# 14 - Első projekt létrehozása

## Bevezetés

Most, hogy megismertük a Godot Engine működésének alapjait és a GDScript programozási nyelvet, elkezdhetjük elkészíteni az első saját projektünket.

Ebben a részben egy egyszerű 2D platformer játékot fogunk felépíteni.

A cél nem az, hogy minél gyorsabban elkészüljön a játék, hanem hogy közben megértsük, miért úgy építjük fel a projektet, ahogy.

A korábbi fejezetekben megismert fogalmak most már valódi példákon keresztül jelennek meg.

---

# Új projekt létrehozása

Indítsuk el a Godot Engine-t.

A Project Manager ablakban válasszuk az **New Project** lehetőséget.

Adjunk nevet a projektnek.

Például:

```text
Platformer
```

Ezután válasszuk ki azt a mappát, ahová a projekt kerül.

A Godot automatikusan létrehozza a szükséges fájlokat.

---

# Renderelési mód

A projekt létrehozásakor válasszuk a **Forward+** renderert.

A későbbiekben ugyan 2D játékot készítünk, de ez a renderer teljesen megfelelő ehhez is.

---

# Projekt felépítése

Már a projekt elején érdemes egy rendezett mappastruktúrát kialakítani.

Például:

```text
Platformer
│
├── Scenes
├── Scripts
├── Assets
├── Audio
└── Fonts
```

Ahogy a projekt növekszik, egy rendezett struktúra sokkal könnyebbé teszi a munkát.

---

# Assetek importálása

A játék grafikáit egyszerűen húzzuk be a Godot FileSystem paneljére.

A Godot automatikusan importálja őket.

Ha pixel art grafikákat használunk, érdemes kikapcsolni a textúraszűrést.

Korábban már láttuk, hogyan lehet ezt beállítani.

```
Project
→ Project Settings
→ Rendering
→ Textures
→ Default Texture Filter
→ Nearest
```

Így a képek élesek maradnak, és nem lesznek elmosódottak.

---

# A fő Scene létrehozása

Minden projektnek szüksége van egy kezdő Scene-re.

Ez lesz a játék belépési pontja.

Hozzunk létre egy új Scene-t.

Root Node-nak egy egyszerű **Node2D** megfelelő választás.

Nevezzük el:

```text
Main
```

Ez lesz az a Scene, amely később összefogja a játék többi részét.

---

# Main Scene beállítása

Miután elmentettük a Scene-t, állítsuk be kezdő Scene-ként.

```
Project
→ Project Settings
→ Run
→ Main Scene
```

Válasszuk ki az imént létrehozott **Main.tscn** fájlt.

Mostantól a projekt mindig ezzel a Scene-nel indul.

---

# Miért kezdünk ilyen egyszerűen?

Sokan rögtön játékost vagy pályát kezdenének készíteni.

Viszont érdemes először létrehozni a projekt alapjait.

Ha már az elején rendezett struktúrát alakítunk ki, később sokkal könnyebb lesz bővíteni a játékot.

Ez ugyanaz a szemlélet, amiről a Composition fejezetben is szó volt.

---

# Mit készítettünk el?

Ebben a fejezetben:

- létrehoztunk egy új Godot projektet;
- kialakítottuk az alap mappastruktúrát;
- importáltuk az asseteket;
- létrehoztuk a Main Scene-t;
- beállítottuk a projekt kezdő Scene-jét.

Most már készen állunk arra, hogy elkészítsük a játék első valódi objektumát: a játékost.

---

## Következő fejezet

➡️ **15 - Player létrehozása**