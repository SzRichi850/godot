# 26 - Audio

## Bevezetés

A játékunk már rendelkezik:

* mozgással;
* animációkkal;
* Coin rendszerrel;
* pontszám kijelzéssel;
* ellenfelekkel.

Most már csak egy dolog hiányzik igazán ahhoz, hogy élőbbnek hasson.

A hangok.

Ebben a fejezetben egyszerű hanghatásokat adunk a játékhoz.

---

# AudioStreamPlayer2D

A térben elhelyezett hangok lejátszásához használhatjuk az:

```text id="3vkr5x"
AudioStreamPlayer2D
```

Node-ot.

Ez ugyanúgy egy Node, mint bármelyik másik.

Képes különböző hangfájlokat lejátszani a játék során.

---

# Hang hozzáadása

Adjunk a kívánt Scene-hez egy AudioStreamPlayer2D Node-ot.

Az Inspectorban keressük meg a:

```text id="v3i8qg"
Stream
```

tulajdonságot.

Ide tölthetjük be a lejátszani kívánt hangfájlt.

Például:

* Coin felvétel;
* ugrás;
* halál;
* háttérzene.

---

# Hang lejátszása

A hangot scriptből egyszerűen elindíthatjuk.

```gdscript id="w1btxg"
audio_player.play()
```

Ez azonnal elindítja a kiválasztott hangot.

---

# Coin hang

A Coin felvételekor érdemes egy rövid hangot lejátszani.

A folyamat például így nézhet ki:

1. a Player hozzáér a Coinhoz;
2. lejátszódik a hang;
3. frissül a pontszám;
4. a Coin eltűnik.

Ettől a játék sokkal több visszajelzést ad a játékosnak.

---

# Háttérzene

Nem csak rövid hanghatásokat használhatunk.

Egy AudioStreamPlayer2D vagy AudioStreamPlayer Node segítségével háttérzenét is lejátszhatunk.

Ha szeretnénk, a **Autoplay** lehetőséget is bekapcsolhatjuk.

Így a zene automatikusan elindul a játék betöltésekor.

---

# Hangerő

A hangerő az Inspectorból is állítható.

Később természetesen készíthetünk külön hangerő-beállító menüt is.

Ebben a projektben azonban elegendő az alapértelmezett beállításokat használni.

---

# Tesztelés

Indítsuk el a játékot.

Próbáljuk ki:

* Coin felvétele;
* ugrás;
* halál.

Figyeljük meg, hogy minden eseményhez tartozik-e megfelelő hang.

A jól megválasztott hanghatások sokat javítanak a játékélményen.

---

# Mit tanultunk?

Ebben a fejezetben:

* megismertük az AudioStreamPlayer2D Node-ot;
* betöltöttünk hangfájlokat;
* lejátszottunk hangokat scriptből;
* háttérzenét adtunk a játékhoz;
* javítottuk a játék visszajelzéseit hanghatások segítségével.

---

## Következő fejezet

➡️ **27 - Export**
