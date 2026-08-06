# 22 - Dying 2.0

## Bevezetés

Korábban már elkészítettük a legegyszerűbb halálrendszert.

Ha a játékos leesett a pályáról, a jelenet újratöltődött.

Most ezt a rendszert kibővítjük úgy, hogy az Enemy is veszélyt jelentsen a játékosra.

---

# Ütközés az Enemyvel

Az Enemy rendelkezik CollisionShape2D-vel, így fizikailag is kapcsolatba tud lépni a Playerrel.

A következő lépés annak eldöntése, hogy mi történjen, amikor a két objektum találkozik.

Ebben a példában azt szeretnénk, hogy a játékos meghaljon.

---

# Area2D használata

A legegyszerűbb megoldás, ha az Enemy rendelkezik egy külön érzékelő területtel.

Például:

```text
Enemy
│
├── AnimatedSprite2D
├── CollisionShape2D
├── RayCastLeft
├── RayCastRight
└── Area2D
      └── CollisionShape2D
```

Az Area2D feladata nem az ütközés kezelése.

Csak azt figyeli, hogy a Player belépett-e a területére.

---

# body_entered Signal

Az Area2D `body_entered` Signalját ugyanúgy használhatjuk, mint korábban a Coin vagy a Death Zone esetében.

Példa:

```gdscript
func _on_body_entered(body):

    if body.name == "Player":
        get_tree().reload_current_scene()
```

Ha a Player belép az Enemy érzékelési területére, a jelenet újratöltődik.

---

# Miért ugyanaz a megoldás?

Észrevehetjük, hogy most is ugyanazt a függvényt használjuk:

```gdscript
get_tree().reload_current_scene()
```

Ez nem véletlen.

A játék szempontjából teljesen mindegy, hogy a játékos:

* leesett a pályáról;
* vagy hozzáért egy Enemyhez.

Mindkét esetben ugyanazt szeretnénk elérni: a pálya induljon újra.

---

# A rendszer előnye

Mivel korábban már elkészítettük a halál logikáját, most nagyon kevés új kódra volt szükség.

Csak egy új eseményt kellett hozzákapcsolnunk ugyanahhoz a működéshez.

Ez jól mutatja, hogy egy jól felépített projektben a korábbi megoldások könnyen újra felhasználhatók.

---

# Tesztelés

Indítsuk el a játékot.

Ha minden megfelelően működik:

* az Enemy továbbra is járőrözik;
* a Player hozzá tud érni;
* az érintés hatására a jelenet újratöltődik;
* a játékos ismét a kezdőpozícióból indul.

Most már nem csak a pálya, hanem az ellenfelek is veszélyt jelentenek.

---

# Lehetséges továbbfejlesztések

Ez még egy egyszerű halálrendszer.

Később természetesen tovább bővíthetjük.

Például:

* életerő rendszer;
* checkpointok;
* halál animáció;
* hanghatások;
* részecskeeffektek.

Most azonban az a célunk, hogy egy stabil alapot építsünk fel.

---

# Mit tanultunk?

Ebben a fejezetben:

* kibővítettük a halálrendszert;
* Area2D segítségével érzékeltük a Player és az Enemy találkozását;
* újra felhasználtuk a korábban elkészített jelenet-újratöltő megoldást;
* összekapcsoltuk az Enemy rendszert a játék többi részével.

---

## Következő fejezet

➡️ **23 - Player 2.0**
