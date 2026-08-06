# 19 - Dying 1.0

## Bevezetés

Most, hogy már tudunk felszedhető tárgyakat készíteni, ideje foglalkozni azzal is, mi történjen akkor, ha a játékos leesik a pályáról.

A legtöbb platformjátékban ilyenkor a játékos meghal, majd újraindul a pálya.

Ebben a fejezetben ennek az alap változatát készítjük el.

---

# Death Zone

Hozzunk létre egy új Scene-t.

Root Node:

```text
Area2D
```

A Death Zone feladata nem az, hogy fizikailag megállítsa a játékost.

Csak azt kell érzékelnie, hogy a Player belépett a területére.

Ezért itt is az **Area2D** a megfelelő választás.

---

# CollisionShape2D

Adjunk a Death Zone-hoz egy CollisionShape2D Node-ot.

Ez fogja meghatározni azt a területet, amely halálzónának számít.

A pálya alatt általában érdemes egy hosszú téglalap alakú Collision Shape-et használni.

Így ha a játékos leesik a pályáról, biztosan bele fog esni ebbe a zónába.

---

# body_entered Signal

Az Area2D egyik legfontosabb Signalja itt is a:

```text
body_entered
```

Kapcsoljuk össze a Death Zone scriptjével.

Ez minden alkalommal lefut, amikor egy fizikai objektum belép a területre.

---

# A jelenet újratöltése

Ha a belépő objektum a Player, töltsük újra az aktuális Scene-t.

Példa:

```gdscript
func _on_body_entered(body):

    if body.name == "Player":
        get_tree().reload_current_scene()
```

A `reload_current_scene()` újra betölti az éppen futó jelenetet.

Ennek eredményeként minden visszaáll a kezdeti állapotba.

A játékos ismét a kezdőpontról indul.

---

# Miért jó ez a megoldás?

Ez a legegyszerűbb módja annak, hogy kezeljük a halált.

Nem kell külön:

* Player Respawn;
* Checkpoint rendszer;
* Élet kezelés.

Egyszerűen újraindítjuk az egész pályát.

A későbbi fejezetekben ezt tovább fogjuk fejleszteni.

---

# A Death Zone elhelyezése

Miután elkészült a Scene, helyezzük el a Main Scene-ben.

A legjobb helye általában a pálya alatt van.

```text
Main
│
├── World
├── Player
├── DeathZone
└── Camera
```

Így bárhol is essen le a játékos, ugyanabba a zónába érkezik.

---

# Az első teszt

Indítsuk el a játékot.

Ha minden megfelelően működik:

* a játékos leesik a pályáról;
* belép a Death Zone-ba;
* a jelenet automatikusan újratöltődik;
* ismét a kezdőpozícióból indulhatunk.

Ez már egy teljesen működő alap halálrendszer.

---

# Miért külön Scene?

A Death Zone ugyanúgy külön Scene lett, mint a Coin vagy a Platform.

Ennek előnye, hogy később több pályán is ugyanazt a rendszert használhatjuk.

Ha később módosítani szeretnénk a működését, elég ezt az egy Scene-t szerkeszteni.

---

# Mit tanultunk?

Ebben a fejezetben:

* létrehoztunk egy Death Zone Scene-t;
* ismét használtuk az Area2D Node-ot;
* csatlakoztattuk a `body_entered` Signalt;
* újratöltöttük az aktuális Scene-t a `reload_current_scene()` segítségével;
* elkészítettük a platformjáték első halálrendszerét.

---

## Következő fejezet

➡️ **20 - World Building 2.0**
