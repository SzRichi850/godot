# 12 - Composition és Call Down, Signal Up

## Bevezetés

Az előző fejezetben megismertük az öröklődést (Inheritance).

Ez egy nagyon hasznos eszköz, azonban nem minden problémára ez a legjobb megoldás.

A Godot ugyan erősen épít az öröklődésre, de a nagyobb projektekben gyakran egy másik megközelítést részesítenek előnyben.

Ezt nevezzük **Compositionnek**.

A Composition lényege, hogy ahelyett, hogy egyetlen nagy osztályba próbálnánk mindent belezsúfolni, inkább több kisebb, önálló részből építjük fel az objektumainkat.

---

# Inheritance vagy Composition?

Képzeljünk el egy játékot, amelyben van Player és Enemy.

Mindkettő rendelkezik:

- életerővel;
- támadással;
- hitboxszal.

Viszont a Player rendelkezik:

- játékos inputtal;

míg az Enemy rendelkezik:

- mesterséges intelligenciával (AI).

```text
Player
│
├── Attack
├── Health
├── Hitbox
└── Player Input

Enemy
│
├── Attack
├── Health
├── Hitbox
└── AI
```

Első ránézésre könnyű lenne azt mondani, hogy készítsünk egy közös osztályt, amelyből mindkettő öröklődik.

Ez működik.

Viszont idővel ez az osztály egyre nagyobb és bonyolultabb lesz.

---

# A Composition gondolkodásmódja

A Composition másképp közelíti meg a problémát.

Nem egyetlen nagy osztályt készítünk.

Hanem több kisebb részt.

Például:

```text
Player
│
├── Health Component
├── Attack Component
├── Hitbox Component
└── Input Component
```

Az Enemy pedig:

```text
Enemy
│
├── Health Component
├── Attack Component
├── Hitbox Component
└── AI Component
```

Látható, hogy a két objektum ugyanazokat az elemeket használja, de nem ugyanabból az osztályból örököl.

Egyszerűen ugyanazokat a komponenseket kapják.

---

# Miért illik ez jól a Godothoz?

A Godot eleve Node-okból épül fel.

Minden Node egy önálló egység.

Ez nagyon jól illeszkedik a Composition szemlélethez.

Például:

```text
Enemy
│
├── AnimatedSprite2D
├── CollisionShape2D
├── Health
├── RayCastLeft
├── RayCastRight
└── AnimationPlayer
```

Nem egyetlen script próbál mindent kezelni.

Minden Node egy kisebb feladatért felel.

Így a projekt könnyebben bővíthető és átlátható marad.

---

# Call Down, Signal Up

Ez az egyik legfontosabb ökölszabály Godot projektekben.

A neve elsőre furcsán hangzik, de nagyon egyszerű.

**Call Down. Signal Up.**

---

# Mit jelent a "Call Down"?

Egy felsőbb Node nyugodtan meghívhatja a saját gyermek Node-jainak függvényeit.

Például:

```text
Player
│
├── Weapon
├── Health
└── Camera
```

A Player nyugodtan meghívhatja a Weapon egyik függvényét.

```gdscript
weapon.attack()
```

Mivel a Weapon a Player gyermeke, ez természetes kapcsolat.

---

# Mit jelent a "Signal Up"?

Fordított irányban viszont már nem érdemes közvetlenül hivatkozni.

Ha egy gyermek Node szeretne szólni a szülőnek, akkor inkább Signal segítségével jelezze.

Például:

```text
Coin
│
└── body_entered
```

A Coin nem akarja tudni, hogy ki gyűjtötte fel.

Egyszerűen kibocsát egy Signalt.

```gdscript
coin_collected.emit()
```

Majd a Level vagy a GameManager eldönti, mit szeretne csinálni.

Például:

- pontot ad;
- hangot játszik le;
- eltünteti a Coin-t;
- frissíti a UI-t.

A Coinnak ezekről semmit sem kell tudnia.

---

# Miért fontos ez?

Ha minden Node közvetlenül hivatkozna minden másik Node-ra, a projekt nagyon gyorsan átláthatatlanná válna.

Például:

```text
Player
│
├── UI
├── Enemy
├── Coin
├── Audio
├── Inventory
├── SaveSystem
├── Achievements
└── ...
```

A Player mindenkivel kommunikál.

Ez hosszú távon nehezen karbantartható.

Signalok használatával minden rendszer csak arra figyel, ami számára fontos.

Ez lazább kapcsolatot eredményez a különböző részek között.

---

# Testvér Node-ok kommunikációja

Felmerülhet a kérdés:

Mi történik akkor, ha két Node ugyanazon a szinten helyezkedik el?

Például:

```text
Level
│
├── Player
└── UI
```

A Player és a UI testvér (Sibling) kapcsolatban vannak.

Ilyenkor általában nem a Player hívja meg közvetlenül a UI függvényeit.

A Player inkább kibocsát egy Signalt.

A felsőbb Node (például a Level vagy a GameManager) kapcsolódik ehhez a Signalhoz, majd ő értesíti a UI-t.

Így egyik Node sem függ közvetlenül a másiktól.

---

# Mikor nem kell mindenáron ragaszkodni hozzá?

A "Call Down, Signal Up" nem egy kötelező szabály.

Inkább egy ajánlott tervezési minta.

Egy kisebb projektben teljesen elfogadható lehet egy egyszerűbb megoldás.

Viszont ahogy nő a projekt mérete, egyre többet segít ez a szemlélet abban, hogy a kód rendezett és könnyen bővíthető maradjon.

---

# Jó gyakorlatok

✔ Egy Node lehetőleg egyetlen feladatot lásson el.

✔ Inkább több kisebb Node, mint egy hatalmas script.

✔ A gyermek Node-ok ne ismerjék feleslegesen a teljes projekt felépítését.

✔ Ha egy esemény több rendszert is érinthet, használjunk Signalt.

✔ Ne féljünk új Scene-eket készíteni. A Godot egyik legnagyobb erőssége az újrafelhasználható Scene rendszer.

---

# Mit tanultunk?

Ebben a fejezetben megismertük:

- mi a Composition;
- miben különbözik az öröklődéstől;
- miért illik jól a Godot Node rendszeréhez;
- mit jelent a "Call Down, Signal Up";
- hogyan kommunikálnak a Node-ok egymással;
- miért segít ez a szemlélet nagyobb projektekben.

---

## Következő fejezet

➡️ **13 - Hasznos GD-script függvények**