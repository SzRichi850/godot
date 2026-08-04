# 06 - Tömbök és ciklusok

## Bevezetés

Eddig egy változóban mindig egyetlen értéket tároltunk.

De mi történik akkor, ha egyszerre több adatot szeretnénk eltárolni?

Például:

- a játékos inventoryja;
- az összes felvett tárgy;
- az enemy-k nevei;
- a pályán található coinok.

Erre szolgálnak a tömbök (Array).

---

# Tömbök (Array)

A tömb egy olyan adatszerkezet, amely egyszerre több elemet képes tárolni.

Példa:

```gdscript
var items = ["Potion", 3, 6]
```

A GDScript lehetővé teszi, hogy különböző adattípusokat is egy tömbben tároljunk.

Viszont nagyobb projektekben érdemes azonos típusú elemeket használni.

Erre típust is megadhatunk.

```gdscript
var items: Array[String] = ["Sword", "Potion", "Shield"]
```

Így biztosak lehetünk benne, hogy a tömb csak szöveget tartalmaz.

---

# Indexelés

A tömb elemei sorszámot kapnak.

Fontos, hogy a számozás **0-tól indul**.

Példa:

```gdscript
var items = ["Potion", "Sword", "Shield"]
```

```gdscript
print(items[0])
```

Ekkor a konzolra ez kerül:

```text
Potion
```

A második elem indexe 1.

A harmadiké 2.

---

# Elem módosítása

A tömb egy adott elemét egyszerűen módosíthatjuk.

```gdscript
items[1] = "Smelly Sock"
```

Most már a második elem nem Sword lesz, hanem Smelly Sock.

---

# Elem törlése

Egy elemet a `remove_at()` függvénnyel törölhetünk.

```gdscript
items.remove_at(1)
```

Ez törli a második elemet.

---

# Új elem hozzáadása

Új elemet az `append()` függvénnyel adhatunk hozzá.

```gdscript
items.append("Overpowered Sword")
```

A tömb végére bekerül az új elem.

---

# Miért használunk tömböket?

Játékfejlesztés során rengeteg helyen találkozhatunk velük.

Például:

- inventory;
- quest lista;
- achievementek;
- ellenfelek;
- fegyverek;
- mentések.

Szinte minden játék használ tömböket valamilyen formában.

---

# Ciklusok

Ha egy tömb több száz elemet tartalmaz, nem szeretnénk egyesével feldolgozni őket.

Erre valók a ciklusok.

A ciklus lehetővé teszi, hogy ugyanazt a műveletet több elemen is végrehajtsuk.

---

# For ciklus

A leggyakrabban használt ciklus.

Példa:

```gdscript
for item in items:
    print(item)
```

Ez végigmegy a tömb összes elemén.

Minden iterációban az aktuális elem kerül az `item` változóba.

---

# Feltétel cikluson belül

A ciklusban ugyanúgy használhatunk `if` utasítást.

Példa:

```gdscript
for item in items:
    if item.length() > 6:
        print(item)
```

Ebben az esetben csak azok az elemek jelennek meg, amelyek hosszabbak 6 karakternél.

---

# Lépésszámlálós for ciklus

Nem csak tömbökön lehet végigmenni.

```gdscript
for n in 8:
    print(n)
```

Ebben az esetben a ciklus nyolcszor fut le.

Az `n` minden iterációban egy új értéket kap.

---

# While ciklus

A `while` ciklus addig fut, amíg a megadott feltétel igaz.

Példa:

```gdscript
var glass := 0.0

while glass < 0.5:
    glass += randf_range(0.01, 0.2)
    print(glass)

print("The glass is now half full!")
```

Ebben a példában egy poharat "töltünk fel" véletlenszerű mennyiségekkel.

A ciklus addig fut, amíg a pohár legalább félig meg nem telik.

---

# Végtelen ciklus

A `while` ciklusoknál nagyon kell figyelni arra, hogy a feltétel egyszer hamissá váljon.

Ha ez nem történik meg, a ciklus örökké futni fog.

Ezt nevezzük végtelen ciklusnak.

A végtelen ciklusok könnyen lefagyaszthatják vagy összeomlaszthatják a programot.

---

# Break

A `break` megszakítja a ciklust.

Miután lefut, a program a ciklus utáni első sorral folytatódik.

---

# Continue

A `continue` nem állítja meg a ciklust.

Csak az aktuális iterációt hagyja ki, majd a következő elemmel folytatja.

---

# Jó gyakorlatok

✔ Tömbökben lehetőleg azonos típusú adatokat tároljunk.

✔ Beszédes neveket használjunk.

✔ A `for` ciklust használjuk, ha ismert az elemek listája.

✔ A `while` ciklust csak akkor használjuk, ha valóban egy feltételig szeretnénk ismételni.

✔ Mindig figyeljünk arra, hogy a `while` ciklus egyszer biztosan véget érjen.

---

# Mit tanultunk?

Ebben a fejezetben megismertük:

- mi az a tömb;
- hogyan érjük el az elemeit;
- hogyan módosítjuk őket;
- hogyan törlünk és adunk hozzá új elemeket;
- hogyan működik a `for` ciklus;
- hogyan működik a `while` ciklus;
- mire való a `break` és a `continue`.

---

## Következő fejezet

➡️ **07 - Dictionary és Enum**