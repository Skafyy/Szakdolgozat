# Piackutatás és hasonló alkalmazások

## 1. Bevezetés

A szakdolgozatom célja egy olyan asztali alkalmazás készítése Java nyelven (Swing keretrendszerrel), amellyel könnyen be lehet olvasni, szerkeszteni és vizualizálni adatbázis-sémákat. A fejlesztés és a rendszertervezés előtt érdemes megvizsgálni, hogy milyen hasonló programok léteznek már a piacon, milyen technikai kompromisszumokkal működnek, és ezek alapján milyen konkrét funkcionális elvárásokat kell megfogalmazni a saját szoftverrel szemben.

## 2. Hasonló alkalmazások

Íme néhány elterjedt eszköz, amelyek hasonló célt szolgálnak:

1. **DbSchema**
   - **Leírás:** Java alapú, vizuális adatbázis-tervező asztali program. Architektúráját tekintve közel áll a tervezett alkalmazáshoz, azonban komplex, vállalati szintű, fizetős szoftver.
   - **Link:** [https://www.dbschema.com/](https://www.dbschema.com/)

2. **MySQL Workbench**
   - **Leírás:** A MySQL hivatalos vizuális tervező- és adminisztrációs eszköze. Fő erőssége az ER-diagramok rajzolása és a séma-kezelés, azonban erősen kötődik a MySQL ökoszisztémához.
   - **Link:** [https://www.mysql.com/products/workbench/](https://www.mysql.com/products/workbench/)

3. **DBeaver**
   - **Leírás:** Népszerű, nyílt forráskódú univerzális adatbázis-kezelő, amely tartalmaz egy beépített diagramnézetet a sémák megjelenítésére.
   - **Link:** [https://dbeaver.io/](https://dbeaver.io/)

4. **dbdiagram.io**
   - **Leírás:** Webes alapú, gyors séma-tervező eszköz, amely saját szöveges leírónyelvből (DBML) generál diagramokat.
   - **Link:** [https://dbdiagram.io/](https://dbdiagram.io/)

5. **phpMyAdmin**
   - **Leírás:** Klasszikus, webes adatbázis-kezelő felület (PHP-alapú), amely tartalmaz egy alapvető vizuális tervező modult (*Designer*) is.
   - **Link:** [https://www.phpmyadmin.net/](https://www.phpmyadmin.net/)

## 3. Összehasonlító táblázat

| Funkció / Tulajdonság | Saját alkalmazás (Java Swing) | DbSchema | MySQL Workbench | DBeaver | dbdiagram.io | phpMyAdmin |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: |
| **Környezet** | Asztali | Asztali | Asztali | Asztali | Webes | Webes |
| **Interaktív vizualizáció** | Igen | Igen | Igen | Igen | Igen | Alap szintű |
| **Séma beolvasás** | Egyedi parser | Igen | Igen | Élő adatbázis | DSL nyelv | Élő adatbázis |
| **Vektoros export (SVG)** | **Igen** | Igen | Igen | Korlátozott | Fizetős | Nem |
| **Offline működés** | **Igen** | Igen | Igen | Igen | Nem | Szerverfüggő |
| **Biztonsági validáció** | **Igen** | Alap | Alap | Alap | Nem releváns | Alap |

## 4. A szerkesztők működésének technikai finomságai

A piacon elérhető eszközök mélyebb vizsgálata rávilágít azokra a tervezési és megvalósítási döntésekre, amelyek közvetlenül meghatározzák a saját alkalmazás specifikációját:

* **SQL dialektusok és séma-források kezelése:**
  * *Vizsgált működés:* A DBeaver és a phpMyAdmin élő adatbázis-kapcsolatból (JDBC vagy szerveroldali metaadatokból) olvassa ki a sémát, míg a dbdiagram.io egyedi leírónyelvet (DBML) használ. A különböző adatbázis-kezelők (pl. [SQLite](https://www.sqlite.org/), [PostgreSQL](https://www.postgresql.org/), [MySQL](https://www.mysql.com/)) eltérően kezelik a típusokat: az SQLite dinamikus tipizálást (*Type Affinity*) alkalmaz, míg a MySQL Workbench szigorú relációs típusmegkötésekre épít.
  * *Következtetés a specifikációra:* Az alkalmazásnak élő adatbázis-szerver nélkül, közvetlenül statikus `.sql` (DDL) fájlokból kell dolgoznia. A saját lexikális és szintaktikai elemzőnek támogatnia kell a `CREATE TABLE` utasítások feldolgozását, az oszlopdefiníciókat, a tábla- és oszlopszintű `PRIMARY KEY`, `FOREIGN KEY`, `NOT NULL`, valamint `UNIQUE` megkötéseket, emellett tolerálnia kell az SQLite rugalmas típusmegadásait is.

* **Számosság és kulcsok vizuális megjelenítése:**
  * *Vizsgált működés:* A MySQL Workbench és a DbSchema a *Crow's Foot* (varjúláb) jelölésrendszert alkalmazza az $1:1$, $1:N$ és $N:M$ kapcsolatok jelölésére. Nagyobb sémáknál a statikus csatlakozási pontok és a sűrűn futó vonalak rontják az áttekinthetőséget.
  * *Következtetés a specifikációra:* A táblákat reprezentáló grafikus komponenseknek vizuálisan el kell különíteniük az elsődleges kulcsokat (`PK`), az idegen kulcsokat (`FK`) és a normál attribútumokat. A relációs éleknek irányított vonalként kell megjelenniük a hivatkozó (`FK`) és a hivatkozott (`PK`) tábla között, dinamikusan a két doboz legközelebbi oldalához igazodva.

* **Kezdeti elrendezés és interaktív szerkeszthetőség:**
  * *Vizsgált működés:* A DBeaver automatikus elrendezése (*Auto-layout*) sok tábla esetén gyakran egymásra helyezi vagy átláthatatlanul rendezi el a csomópontokat, a kézi finomhangolás pedig korlátozott.
  * *Következtetés a specifikációra:* Fájlbetöltéskor egy determinisztikus, ütközésmentes kezdeti elrendezésre (pl. rácsos elhelyezésre) van szükség, amelyet a felhasználó szabad egérműveletes pozicionálással (*drag-and-drop*), valamint nagyítással (zoom) és eltolással (pan) tetszőlegesen átrendezhet.

## 5. Alternatív eszközök és szöveges ábragenerátorok

Az adatbázis-sémák vizualizálására és dokumentálására nemcsak dedikált adatbázis-tervezők, hanem más kategóriájú eszközök is léteznek:

* **Általános diagramszerkesztők ([draw.io / diagrams.net](https://www.drawio.com/), [Dia](http://dia-installer.de/)):**
  * *Vizsgált működés:* Teljes grafikai szabadságot adnak, de nem értelmezik az SQL szintaxist. Minden táblát, mezőt és kapcsolatot kézzel kell felvenni, így a séma változásakor a diagram könnyen elavul.
  * *Specifikációs hozadék:* Az alkalmazásnak automatikusan kell generálnia a diagramot az SQL fájlból, ugyanakkor meg kell őriznie a kézi vizuális testreszabhatóságot (táblák szabad mozgatása, átméretezéshez igazodó kapcsolatok).

* **UML szerkesztők ([StarUML](https://staruml.io/), [Visual Paradigm](https://www.visual-paradigm.com/)):**
  * *Vizsgált működés:* Kiválóak objektumorientált osztálydiagramok készítésére, azonban a relációs adatbázisok fizikai sajátosságai (idegen kulcs referenciák, SQL adattípusok) csak korlátozottan vagy körülményes profillal modellezhetők bennük.
  * *Specifikációs hozadék:* A felületnek kifejezetten relációs séma-elemekre (táblanév, attribútumnév, adattípus, `PK`/`FK` jelölés) kell specializálódnia, felesleges UML-jelölések nélkül.

* **Szöveges ábragenerátorok ([PlantUML](https://plantuml.com/), [Mermaid](https://mermaid.js.org/), [TikZ](https://tikz.dev/)):**
  * *Vizsgált működés:* Verziókezelő rendszerekben (Git) kiválóan kezelhetők, a TikZ pedig nyomdai minőségű LaTeX kimenetet ad. Hátrányuk, hogy nem biztosítanak közvetlen, egérrel történő interaktív szerkesztést, és a komplex elrendezések kézi kódolása időigényes.
  * *Specifikációs hozadék:* A dokumentációkba és szakdolgozatokba történő veszteségmentes beilleszthetőség érdekében az alkalmazásnak támogatnia kell a skálázható vektoros (**SVG**) és a raszteres (**PNG**) exportálást.

## 6. Összegzés

A piaci és technológiai elemzés alapján a fejlesztendő Java Swing alapú asztali alkalmazás a nehézsúlyú adatbázis-adminisztrációs rendszerek (DBeaver, MySQL Workbench) és a tisztán kézi vagy szöveges rajzolók (draw.io, TikZ) közötti rést tölti be. A vizsgálatból levezetett főbb követelmények:

1. **Önálló, offline működés:** Külső adatbázis-szerver és internetkapcsolat nélküli futtatás.
2. **Biztonságos és robusztus SQL DDL elemzés:** Kizárólag szerkezeti definíciók (`CREATE TABLE`) feldolgozása, a nem kívánt vagy kártékony utasítások (pl. `DROP`, `DELETE`, `EXEC`) szűrésével.
3. **Interaktív grafikus vászon:** Ütközésmentes kezdeti elrendezés, szabad egérműveletes pozicionálás (*drag-and-drop*), zoomolás és a kapcsolati vonalak dinamikus újraszámítása.
4. **Publikációs minőségű export:** A vizuális modell mentése **PNG** és **SVG** formátumban, dokumentációs felhasználásra.