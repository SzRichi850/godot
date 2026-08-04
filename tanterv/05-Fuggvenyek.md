# 05 - Függvények

## Bevezetés

A függvények a programozás egyik legfontosabb építőelemei.

Lehetővé teszik, hogy a kódunkat kisebb, újrafelhasználható részekre bontsuk.

Ha ugyanazt a műveletet több helyen is el kell végezni, nem kell újra és újra leírnunk a kódot, egyszerűen létrehozunk egy függvényt, majd meghívjuk, amikor szükség van rá.

---

# Beépített függvények

A Godot számos beépített függvényt biztosít számunkra.

Ilyenek például:

- `_ready()`
- `_process()`
- `_input()`

A nevük előtt található alsóvonás (`_`) azt jelzi, hogy ezeket a függvényeket a Godot Engine hívja meg automatikusan.

Nekünk csak meg kell adnunk, hogy mi történjen bennük.

Példa:

```gdscript
func _ready() -> void:
    print("Hello World!")
```

Ebben az esetben a `print()` akkor fut le, amikor a Node belép a Scene Tree-be.

---

# Saját függvények

Természetesen nem csak a Godot beépített függvényeit használhatjuk.

Saját függvényeket is létrehozhatunk.

Például egy játékban teljesen természetes lehet, hogy külön függvény kezeli:

- az ugrást;
- a támadást;
- a sebződést;
- a halált;
- az újraéledést.

Példa:

```gdscript
func jump():
    print("Jump!")
```

A függvény addig nem fut le, amíg meg nem hívjuk.

```gdscript
jump()
```

---

# Paraméterek

A függvények adatokat is fogadhatnak.

Ezeket paramétereknek nevezzük.

Példa:

```gdscript
func add(num1: int, num2: int) -> int:
    var result = num1 + num2
    return result
```

Ebben a példában két egész számot adunk át a függvénynek.

A függvény összeadja őket, majd visszaadja az eredményt.

---

# Return érték

A `return` kulcsszóval adhatjuk vissza a függvény eredményét.

```gdscript
func add(num1: int, num2: int) -> int:
    return num1 + num2
```

Felhasználása:

```gdscript
var result = add(3, 5)

print(result)
```

Ebben az esetben a konzolra a következő kerül:

```text
8
```

Nem minden függvény ad vissza értéket.

Ha csak végrehajt valamilyen műveletet, akkor a visszatérési típusa általában `void`.

---

# Paraméterek és visszatérési értékek

Érdemes úgy gondolni a függvényekre, mint egy gépre.

Beleteszünk valamit.

A függvény elvégzi a feladatát.

Majd visszaad egy eredményt.

Például:

```text
2 + 3
   │
   ▼
 add()
   │
   ▼
5
```

Ez ugyanaz az elv, mint egy kávéfőzőnél.

Beletesszük a szükséges hozzávalókat, a gép elvégzi a feladatát, majd elkészül a kávé.

A programozásban ezeket nevezzük paramétereknek és visszatérési értéknek.

---

# Miért használunk függvényeket?

A függvények segítségével:

- kevesebb ismétlődő kódot írunk;
- könnyebb átlátni a programot;
- egyszerűbb javítani a hibákat;
- ugyanazt a logikát több helyen is felhasználhatjuk.

Ez különösen fontos nagyobb projektekben.

---

# Jó gyakorlatok

✔ Egy függvény lehetőleg egyetlen feladatot végezzen.

✔ Adjunk beszédes nevet a függvénynek.

Például:

```gdscript
take_damage()
```

jobb, mint

```gdscript
asd()
```

✔ Ha egy függvény visszaad valamit, használjuk fel a visszatérési értéket.

✔ Ne írjunk túl hosszú függvényeket.

Ha egy függvény több különböző feladatot is ellát, érdemes kisebb függvényekre bontani.

---

# Mit tanultunk?

Ebben a fejezetben megismertük:

- mi az a függvény;
- hogyan készítünk saját függvényt;
- hogyan működnek a paraméterek;
- mire való a `return`;
- mikor használunk `void` visszatérési típust;
- miért teszik átláthatóbbá a programot a függvények.

---

## Következő fejezet

➡️ **06 - Tömbök és ciklusok**