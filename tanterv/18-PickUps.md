# 18 - Pick Ups

## Bevezetés

Eddig elkészítettük a játékost, felépítettük az első pályát, és mozgó platformokat is létrehoztunk.

Most készítünk egy olyan objektumot, amelyet a játékos fel tud venni.

Ebben a példában ez egy Coin lesz, de ugyanilyen elven működhetnek később:

* kulcsok;
* életerő növelők;
* power-upok;
* küldetéstárgyak.

---

# Új Coin Scene

A Coin-t külön Scene-ként hozzuk létre.

Ez ugyanazt az előnyt biztosítja, mint a Platform Scene.

Ha később több pályán is szeretnénk használni, egyszer kell elkészítenünk.

Root Node:

```text
Area2D
```

Az Area2D olyan Node, amely érzékeli, ha egy másik objektum belép a területére.

Ezért kiváló választás felszedhető tárgyakhoz.

---

# A Coin felépítése

Adjuk hozzá a szükséges Node-okat.

```text
Coin
│
├── AnimatedSprite2D
└── CollisionShape2D
```

Az AnimatedSprite2D jeleníti meg a Coin animációját.

A CollisionShape2D határozza meg azt a területet, ahol a játékos fel tudja venni.

---

# Animáció

A Coin akkor mutat igazán jól, ha folyamatosan animálódik.

Hozzuk létre a Sprite Frames erőforrást, majd adjuk hozzá a Coin animáció képkockáit.

Kapcsoljuk be a folyamatos lejátszást.

Így a Coin már akkor is "élőnek" hat, amikor még nem vettük fel.

---

# Collision beállítása

A CollisionShape2D mérete legyen akkora, hogy a játékos könnyen fel tudja venni a Coin-t.

Ha túl kicsi, nehéz lesz pontosan eltalálni.

Ha túl nagy, a játékos már messziről felveheti.

Érdemes olyan méretet választani, amely természetes játékélményt ad.

---

# body_entered Signal

Az Area2D egyik legfontosabb Signalja a:

```text
body_entered
```

Ez akkor fut le, amikor egy másik fizikai objektum belép az Area2D területére.

Csatlakoztassuk ezt a Signalt a Coin scriptjéhez.

---

# A Coin eltüntetése

Miután a játékos hozzáért a Coinhoz, nincs rá többé szükség.

A legegyszerűbb megoldás:

```gdscript
queue_free()
```

A `queue_free()` eltávolítja a Node-ot a Scene Tree-ből.

A Coin így eltűnik a pályáról.

---

# Mi történik ilyenkor?

Amikor a játékos hozzáér a Coinhoz:

1. lefut a `body_entered` Signal;
2. ellenőrizhetjük, hogy valóban a Player lépett-e bele;
3. végrehajtjuk a kívánt műveletet;
4. eltávolítjuk a Coin-t.

Például:

```gdscript
func _on_body_entered(body):

    if body.name == "Player":
        queue_free()
```

Ez már önmagában működő Coin rendszert ad.

---

# Több Coin használata

Mivel a Coin külön Scene, egyszerűen több példányt is elhelyezhetünk belőle.

```text
Main
│
├── Coin
├── Coin
├── Coin
├── Coin
└── Coin
```

Mindegyik ugyanazzal a működéssel rendelkezik.

Ez ismét jól mutatja a Scene rendszer egyik legnagyobb előnyét: az újrafelhasználhatóságot.

---

# Miért Area2D?

Felmerülhet a kérdés, miért nem CharacterBody2D vagy StaticBody2D.

Azért, mert a Coinnak nincs saját fizikája.

Nem mozog.

Nem ütközik úgy, mint a Player.

Csak érzékelni szeretnénk, amikor valaki belép a területére.

Pontosan erre való az Area2D.

---

# Az első Pick Up rendszer

Most már képesek vagyunk felszedhető tárgyakat készíteni.

A Coin csak egy példa.

Ugyanezt a rendszert később felhasználhatjuk más objektumokhoz is.

Például:

* kulcs;
* életerő;
* extra élet;
* új képesség.

A különbség csak az lesz, hogy mi történik a `body_entered` Signal lefutásakor.

---

# Mit tanultunk?

Ebben a fejezetben:

* létrehoztunk egy Coin Scene-t;
* megismertük az Area2D szerepét;
* hozzáadtunk animációt;
* beállítottuk a CollisionShape2D-t;
* használtuk a `body_entered` Signalt;
* eltávolítottuk a Coin-t a `queue_free()` segítségével;
* elkészítettük az első Pick Up rendszerünket.

---

## Következő fejezet

➡️ **19 - Dying 1.0**
