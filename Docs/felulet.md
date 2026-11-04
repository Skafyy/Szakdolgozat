# Felhasználói felület és működés

Ez a dokumentum bemutatja az adatbázis-séma elemző és vizualizáló alkalmazás grafikus felépítését és működési logikáját.

## 1. A felület felépítése
Az alkalmazás egy asztali ablak (Java Swing alapokon), amely a következő főbb részekből áll:

* **Felső menüsáv:** Itt érhetők el az alapvető funkciók (Fájl megnyitása, Exportálás, Kilépés).
* **Bal oldali panel (Séma lista):** Egy fastruktúra, amely kilistázza a beolvasott adatbázis tábláit és azok mezőit.
* **Középső rajzvászon (Diagram nézet):** Ez a fő munkaterület. Itt jelenik meg maga az adatbázis-diagram. A táblákat dobozokként, a közöttük lévő kapcsolatokat (idegen kulcsok) pedig összekötő vonalakként mutatja.
* **Eszköztár:** Gombok a diagram nagyításához (zoom), kicsinyítéséhez és az alapállapot visszaállításához.

## 2. A program működése
A szoftver használata az alábbi egyszerű lépésekből áll:

1. **Beolvasás:** A felhasználó tallózással kiválaszt egy SQL séma fájlt.
2. **Ellenőrzés:** A program a háttérben leellenőrzi a bemenetet (biztonsági szűrés, pl. SQL injection ellen).
3. **Feldolgozás:** A beépített elemző (parser) kinyeri a táblákat, mezőket és a kapcsolatokat.
4. **Interaktív megjelenítés:** A program kirajzolja a diagramot a középső vászonra. A felhasználó az egérrel szabadon mozgathatja (drag-and-drop) a táblákat, hogy a legátláthatóbb elrendezést kapja.
5. **Exportálás:** A végleges elrendezést a felhasználó kimentheti képként (PNG) vagy nagyítható, vektoros formátumban (SVG) prezentációkhoz és dokumentációkhoz.

## 3. Látványvilág és stílus
A cél egy letisztult, modern és könnyen átlátható felület. A táblákat reprezentáló dobozok fejléce (a tábla neve) kiemelt színt kap, a primer és idegen kulcsok pedig egyértelmű jelöléssel (pl. ikonokkal vagy félkövér betűtípussal) lesznek megkülönböztetve.