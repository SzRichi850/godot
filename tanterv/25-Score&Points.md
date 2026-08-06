# 25 - Score & Points

## Bevezetés

Korábban már elkészítettük a Coin rendszert.

Amikor a játékos hozzáér egy Coinhoz, az eltűnik a pályáról.

Most ezt a rendszert továbbfejlesztjük úgy, hogy a Coin felvétele pontot is adjon a játékosnak.

A megszerzett pontokat egy Label segítségével jelenítjük meg a képernyőn.

---

# Score változó

Először szükségünk lesz egy változóra, amely eltárolja az aktuális pontszámot.

Például:

```gdscript
var score := 0
```

Ez a változó fogja nyilvántartani, hogy a játékos hány pontot szerzett eddig.

---

# Label elérése

Az előző fejezetben már elkészítettük a Label Node-ot.

Most scriptből is el kell érnünk.

Például:

```gdscript
@onready var score_label: Label = $CanvasLayer/ScoreLabel
```

Az `@onready` biztosítja, hogy a Label már létezzen, amikor használni szeretnénk.

---

# A Label frissítése

Készítsünk egy külön függvényt, amely frissíti a megjelenített pontszámot.

```gdscript
func update_score():

    score_label.text = "Score: " + str(score)
```

Így mindig ugyanaz a függvény felel a Label frissítéséért.

Ha később változtatni szeretnénk a megjelenésen, elég ezt az egy helyet módosítani.

---

# Pont hozzáadása

Amikor a játékos felvesz egy Coin-t, növeljük a pontszámot.

```gdscript
score += 1

update_score()
```

Ezután már a Label is automatikusan frissül.

---

# A Coin módosítása

A Coin korábban csak eltűnt.

Most már pontot is kell adnia.

A `body_entered` Signal továbbra is ugyanúgy működik.

A különbség az, hogy a Coin már nem csak saját magát távolítja el, hanem jelzi azt is, hogy pontot kell hozzáadni.

Ezután továbbra is:

```gdscript
queue_free()
```

eltávolítja magát a Scene Tree-ből.

---

# Miért külön függvény?

Felmerülhet a kérdés:

Miért nem írjuk közvetlenül mindenhol ezt?

```gdscript
score_label.text = ...
```

Azért, mert így minden pontszám-frissítés ugyanazon a helyen történik.

Ha később szeretnénk például:

* animációt;
* hangot;
* villanást;
* formázást;

elég az `update_score()` függvényt módosítani.

Ez tisztább és könnyebben karbantartható megoldás.

---

# Az első működő HUD

Most már a játékos minden Coin felvételekor:

1. pontot kap;
2. frissül a Label;
3. eltűnik a Coin.

Ez az első valóban működő HUD (Heads-Up Display) elemünk.

A HUD olyan felhasználói felület, amely játék közben folyamatosan információt jelenít meg.

---

# Tesztelés

Indítsuk el a játékot.

Próbáljunk felvenni néhány Coin-t.

Ha minden megfelelően működik:

* a Coin eltűnik;
* a pontszám eggyel növekszik;
* a Label azonnal frissül.

Most már a játékos visszajelzést kap arról, hogy valóban gyűjtötte a Coinokat.

---

# Mit tanultunk?

Ebben a fejezetben:

* létrehoztunk egy pontszám változót;
* elértük a Label Node-ot scriptből;
* frissítettük a szöveget;
* összekapcsoltuk a Coin rendszert a pontszám kijelzésével;
* elkészítettük az első működő HUD elemet.

---

## Következő fejezet

➡️ **26 - Audio**
