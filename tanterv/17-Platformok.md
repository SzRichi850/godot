# 17 - Platformok

## Bevezetés

Most, hogy elkészült az első pályánk, érdemes egy kicsit érdekesebbé tenni.

A platformjátékok egyik leggyakoribb eleme a mozgó platform.

Ebben a fejezetben elkészítünk egy olyan platformot, amely két pont között folyamatosan mozog, és amelyre a játékos fel tud állni.

---

# Új Platform Scene

A mozgó platformot külön Scene-ként hozzuk létre.

Ez azért hasznos, mert később ugyanazt a platformot akár több pályán is felhasználhatjuk.

Hozzunk létre egy új Scene-t.

Root Node:

```text
AnimatableBody2D
```

Ez a Node olyan objektumokhoz készült, amelyeket mi mozgatunk, de továbbra is részt vesznek a fizikai világban.

---

# Sprite és Collision

A Platform Scene-hez adjunk hozzá:

```text
Platform
│
├── Sprite2D
└── CollisionShape2D
```

A Sprite2D jeleníti meg a platform grafikáját.

A CollisionShape2D biztosítja, hogy a játékos meg tudjon állni rajta.

---

# AnimationPlayer

Ahhoz, hogy a platform mozogni tudjon, adjunk hozzá egy új Node-ot:

```text
AnimationPlayer
```

Az AnimationPlayer nem csak karakteranimációkhoz használható.

Tulajdonságokat is tud animálni, például egy Node pozícióját.

Ezért kiváló választás mozgó platformok készítésére.

---

# Az első animáció

Nyissuk meg az Animation panelt, majd hozzunk létre egy új animációt.

Például:

```text
Move
```

Az animáció hossza legyen néhány másodperc.

Ezután rögzítsük a Platform pozícióját az első kulcskockában.

Majd vigyük a platformot egy új helyre, és készítsünk egy második kulcskockát.

Így a platform két pont között fog mozogni.

---

# Loop

Ha azt szeretnénk, hogy a platform folyamatosan mozogjon, kapcsoljuk be a **Loop** lehetőséget.

Így amikor az animáció eléri a végét, automatikusan újraindul.

A platform megszakítás nélkül ismételni fogja ugyanazt a mozgást.

---

# Autoplay

Nem szeretnénk minden indításkor külön elindítani az animációt.

Az AnimationPlayerben állítsuk be az elkészített animációt **Autoplay** animációnak.

Így a platform már a játék indulásakor mozogni kezd.

---

# Platform elhelyezése

Mentsük el a Platform Scene-t.

Ezután húzzuk be a Main Scene-be.

Most már ugyanúgy használható, mint bármely más Scene.

Akár több példányt is elhelyezhetünk belőle a pályán.

Mindegyik ugyanazt a működést használja.

---

# Miért külön Scene?

Ez egy jó példa arra, miért érdemes Scene-ekben gondolkodni.

Ha később szeretnénk módosítani a platform működését vagy kinézetét, elég a Platform Scene-t szerkeszteni.

Minden elhelyezett példány automatikusan megkapja a módosításokat.

Ez sokkal kényelmesebb, mintha minden platformot külön kellene szerkesztenünk.

---

# Az első teszt

Indítsuk el a játékot.

Ha minden megfelelően sikerült:

* a platform automatikusan mozog;
* a játékos rá tud állni;
* a platform végigjárja a beállított útvonalat.

Most már egy klasszikus platformjáték egyik alapvető eleme is elkészült.

---

# Mit tanultunk?

Ebben a fejezetben:

* létrehoztunk egy külön Platform Scene-t;
* megismertük az AnimatableBody2D szerepét;
* használtuk az AnimationPlayert;
* kulcskockákkal animáltuk a platform mozgását;
* beállítottuk a Loop és az Autoplay működését;
* újrafelhasználható Scene-t készítettünk.

---

## Következő fejezet

➡️ **18 - Pick Ups**
