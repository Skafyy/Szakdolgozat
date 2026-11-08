# Adatbázis-séma Elemző és Vizualizáló Asztali Alkalmazás

Szakdolgozat projekt a Miskolci Egyetem Gépészmérnöki és Informatikai Kar Programtervező informatikus BSc képzésén.

## A dolgozat címe és témája
* **Cím:** Relációs séma és diagram szerkesztő alkalmazás fejlesztése
* **Konzulens:** Dr. Tompa Tamás
* **Szakmai konzulens / Architektúra tanácsadó:** Piller Imre, Dr. Tompa Tamás

## Feladatleírás
A szakdolgozat célja egy olyan asztali grafikus felhasználói felülettel (GUI) rendelkező alkalmazás fejlesztése Java nyelven (Swing keretrendszer használatával), amely képes különböző SQL adatbázis-sémák beolvasására, elemzésére, valamint az adatbázis-szerkezetek (táblák, kapcsolatok, idegen kulcsok) interaktív, testreszabható grafikus vizualizációjára. 

A szoftver kiemelt figyelmet fordít a biztonságra (SQL injection megelőzése a séma lekérdezése során) és a rugalmas exportálási lehetőségekre (PNG és SVG vektoros formátumok), hogy a generált diagramok közvetlenül beilleszthetők legyenek dokumentációkba vagy prezentációkba.

## Projekt Struktúra
- `docs/` - Rendszertervek, felületi leírások (`felulet.md`) és piackutatás (`piackutatas.md`)
- `szakdolgozat/` - A szakdolgozat szöveges dokumentuma
- `editor/` - A Java Swing alapú szerkesztő és parser forráskódjai
- `README.md` - Projekt áttekintés

## Technológiai Stack
* **Nyelv:** Java
* **UI keretrendszer:** Java Swing
* **Adatbázis & SQL:** SQL sémák, relációs adatbázis-kezelők támogatása
* **Verziókövetés:** Git, GitHub
* **Dokumentáció:** Markdown, LaTeX Beamer / sablonok

## Főbb Funkciók és Tervezett Modulok
1. **Séma-elemzés (Parser):** SQL adatbázis-sémák vagy élő kapcsolatok struktúrájának feldolgozása, entitások és kapcsolatok kinyerése.
2. **Grafikus vizualizáció:** Az adatbázis-objektumok (táblák, mezők, relációk) interaktív megjelenítése grafikus felületen, zoom és elmozgatás támogatással.
3. **Exportálási lehetőségek:** A megrajzolt sémák mentése kiváló minőségű raszteres (PNG) vagy skálázható vektoros (SVG) formátumban.
4. **Biztonsági validáció:** Beépített input validációk és szűrések a biztonságos adatkezelés és az SQL injekciók megelőzése érdekében.

## Projekt Struktúra
- `Docs/` - Dokumentumok, szakdolgozat sablonok, irodalomkutatás és összehasonlító táblázatok
- `src/` - Forráskódok
- `README.md` - Projekt áttekintés és dokumentáció
