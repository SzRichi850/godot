# 04 - Feltételek és programlogika

## Bevezetés

A programozásban nagyon gyakran kell döntéseket hoznunk.

Például:

- Meghalt a játékos?
- Felvette a coin-t?
- Megnyomta az ugrás gombot?
- Van még élete?
- Elérte a pálya végét?

Ezeket a döntéseket feltételekkel tudjuk kezelni.

A GDScriptben erre az `if` utasítást használjuk.

---

# If utasítás

Az `if` egy feltételt vizsgál meg.

Ha a feltétel igaz, akkor a benne lévő kód lefut.

Példa:

```gdscript
if health <= 0:
    print("You DIED!")
```

Ebben a példában a program megnézi, hogy a `health` kisebb vagy egyenlő-e nullával.

Ha igen, kiírja:

```text
You DIED!
```

Ha nem, akkor egyszerűen tovább fut a program.

---

# Összehasonlító operátorok

A feltételek kiértékeléséhez különböző operátorokat használhatunk.

| Operátor | Jelentése |
|----------|-----------|
| `==` | egyenlő |
| `!=` | nem egyenlő |
| `>` | nagyobb |
| `<` | kisebb |
| `>=` | nagyobb vagy egyenlő |
| `<=` | kisebb vagy egyenlő |

Példák:

```gdscript
health == 100
```

```gdscript
coins > 10
```

```gdscript
lives != 0
```

---

# Egymásba ágyazott feltételek

Egy feltételen belül újabb feltételeket is használhatunk.

```gdscript
if health <= 0:
    health = 0
    print("You DIED!")
```

A blokkokat mindig a megfelelő behúzással különítjük el.

---

# Else

Nem csak azt adhatjuk meg, mi történjen akkor, ha a feltétel igaz.

Azt is megadhatjuk, mi történjen, ha nem.

```gdscript
if health <= 0:
    print("You DIED!")
else:
    print("Still alive!")
```

Ha a játékos nem halt meg, akkor az `else` ág fog lefutni.

---

# Elif

Ha több különböző állapotot szeretnénk vizsgálni, használhatjuk az `elif` kulcsszót.

Példa:

```gdscript
if health <= 0:
    health = 0
    print("You DIED!")
elif health < 50:
    print("YOU ARE INJURED!")
else:
    print("YOU ARE HEALTHY.")
```

Ebben a példában három különböző állapot létezik.

- A játékos meghalt.
- A játékos sérült.
- A játékos egészséges.

A program fentről lefelé halad.

Amint talál egy igaz feltételt, a többit már nem vizsgálja.

---

# Több feltétel egyszerre

Előfordulhat, hogy egyszerre több feltételnek is teljesülnie kell.

Erre használjuk az `and` kulcsszót.

```gdscript
if health > 0 and has_key:
    print("The door opens.")
```

Ebben az esetben csak akkor nyílik ki az ajtó, ha:

- a játékos életben van;
- és nála van a kulcs.

Mindkét feltételnek igaznak kell lennie.

---

# Az `or` kulcsszó

Ha elég, hogy a feltételek közül csak az egyik teljesüljön, akkor az `or` kulcsszót használjuk.

```gdscript
if has_red_key or has_master_key:
    print("The door opens.")
```

Ebben az esetben elég, ha a két kulcs közül valamelyik megvan.

---

# Feltételek játékfejlesztésben

A játékok szinte folyamatosan feltételeket vizsgálnak.

Például:

- ugorhat-e a játékos;
- hozzáért-e egy enemyhez;
- felvette-e a coin-t;
- elérte-e a célterületet;
- lejárt-e az idő.

A legtöbb játékmechanika valamilyen feltételre épül.

Ezért fontos megérteni az `if` működését.

---

# Jó gyakorlatok

✔ A feltételek legyenek egyszerűek és könnyen olvashatók.

✔ Ha túl sok egymásba ágyazott `if` jelenik meg, érdemes átgondolni a kód felépítését.

✔ Beszédes változóneveket használjunk.

Például:

```gdscript
is_alive
```

jobb, mint

```gdscript
a
```

---

# Mit tanultunk?

Ebben a fejezetben megismertük:

- az `if` utasítást;
- az `else` és `elif` használatát;
- az összehasonlító operátorokat;
- az `and` és `or` kulcsszavakat;
- hogyan épülnek fel a döntések a programokban.

---

## Következő fejezet

➡️ **05 - Függvények**