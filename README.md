# A projekt leírása

A projekt egy egyetemi tárgy feladatát valósítja meg, melyet 5 fős csapatban oldottunk meg.

A feladat leírása adott volt, annak megfelelő, egyszerűsített grafikus interface-szel rendelkező játékprogramot kellett megvalósítanunk. A tervezés közepén módosításokat is kaptunk a fejlesztéshez, amiket abszolválnunk kellett (ld. a leírás végén).

A GUI működésének leírása a *grafikus_spec.docx* fájlban olvasható.

# Futtatási útmutató

## Fordítás
A projektet jdk 20 alatt szükséges futtatni. Lefordítani a következőképpen lehetséges, először
is a letöltött zip fájlból a fájlokat egy mappába kell kicsomagolni, majd indítani egy
parancssort és annak a mappának a “src” mappájába kell navigálni, ahova kicsomagoltuk a fájlokat.
Ezek után a következő paranccsal fordítható:

```javac @compile.txt```

## Futtatás
A programot parancssor segítségével tudjuk futtatni. Először is a parancssor segítségével abba
a mappába navigálunk, ahol lefordítottuk a programot. A fordítást követően, a következő paranccsal lehet futtatni a programot:

```java game.Main```

# A játék leírása

A Műegyetem Központi épületének alagsora alatt egy elátkozott labirintus rejtőzik. A mérnökhallgatók dolga fellelni a Logarléc nevű mágikus képességű ereklyét. A labirintus szobáit ajtók választják el egymástól, ezeken átlépve lehet az egyik szobából a másikba átjutni. Egy-egy szobából legalább egy, de esetenként sok másik szobába is nyílhat ajtó. Vannak ráadásul ajtók, amelyek csak egy irányban használhatók.

A szobákban különféle tárgyak lehetnek (ilyen a Logarléc is), amiket a hallgatók magukhoz vehetnek, de egy hallgatónál egy időben legfeljebb öt tárgy lehet. A tárgyakat a hallgatók le is tudják tenni.

A labirintusban oktatók próbálják megakadályozni a hallgatókat abban, hogy sikerrel járjanak. Ha egy oktató egy szobába kerül egy vagy több hallgatóval, akkor elveszi a lelkét és a hallgató kibukik az egyetemről. A tárgyak között azonban vannak olyanok, amik adott ideig védettséget nyújtanak az oktatók ellen (pl. a TVSZ denevérbőrre nyomtatott példányai három alkalommal mentik meg a hallgató életét, utána elveszítik a varázserejüket, a szent söröspoharak pedig csak adott ideig hatnak). Van olyan tárgy is, a nedves táblatörlő rongy, amely adott ideig működik (amíg ki nem szárad), és a vele egy szobában lévő oktatókat megbénítja. A dobozolt káposztás camembert felbontáskor mérges gázt bocsát ki (lásd lejjebb a gázos szobákat). A tárgyakat az oktatók is fel tudják venni!

A szobákban elvétve tranzisztorok is találhatók. A hallgatónál levő tranzisztorokat páronként össze lehet kapcsolni, majd a pár egyik tagját menet közben egy másik szobában le lehet tenni. Az így összekapcsolt tranzisztorok varázserővel bírnak: ha a hallgató a nála maradó tranzisztort bekapcsolja és leteszi, akkor a másik tranzisztor szobájába kerül, a bekapcsolt tranzisztor pedig kikapcsol. A tranzisztorok korlátlan ideig használhatók.

Minden szobának van egy (a szobára jellemző) befogadóképessége. Ennél több hallgató és oktató a szobában nem tartózkodhat. Ezen kívül a szobáknak több fajtája is ismert. Vannak szobák, amikben mérgező gáz van. Az ide belépő hallgatók és oktatók egy rövid időre eszméletüket vesztik és a náluk lévő tárgyakat elejtik. Ha valakinél van FFP2-es maszk, akkor ezekben a szobákban adott időre védettséget kap, de a maszk egyre rövidebb ideig képes a védelem nyújtására. Vannak olyan elátkozott szobák, amiknek az ajtajai időnként eltűnnek, majd később újra előtűnnek.

A szobák egy korábbi (félresikerült) gráfelméleti tételbizonyítás eredményeként meghazudtolják a fizika törvényeit: képesek egyesülni és osztódni. Két szomszédos szoba egyesülésével létrejövő szoba a korábbi két szoba tulajdonságaival és szomszédaival rendelelkezik, de a befogadóképessége a nagyobb szoba befogadóképességével lesz azonos. Az osztódó szoba két olyan szobára válik szét, amelyek egymás szomszédai lesznek, és megosztoznak a korábbi szoba képességein és szomszédain (a korábbi szomszédok vagy csak az egyik, vagy csak a másik “új” szobának lesznek szomszédai).

A játékot egyszerre több játékos játssza, akik a hallgatókat irányítják, és akkor nyernek, ha megadott időn belül megtalálták és magukhoz vették a Logarlécet.

### Utólagos módosítások:

- A söröskorsó képessége (véd az oktatótól) kibővül: a még aktív söröskorsót használva a hallgatók elejtik az egyik náluk levő tárgyat.
- Új tárgy: légfrissítő. Egyszerhasználatos tárgy. Gázos szobában lerakva semlegesíti a gázhatást.
- Új ember: takarító. A szobák befogadóképessége rá is érvényes. Ha belép egy szobába, minden mozogni képes (nem bénult / ájult) embert kitessékel onnan. Ha gázos szobába lép, kiszellőztet, megszüntetve a szoba gázosságát. A szobák a takarítást követően adott számú látogató után ragacsossá válnak: a bennük lévő és bennük letett tárgyakat nem lehet felvenni. 
- Egyes tárgyaknak (tvsz, maszk, logarléc) létezik "hamis" változata, amelyiknek nincs az eredeti tárgyra jellemző jó tulajdonsága. Például a hamis logarléc felvételével nem lehet nyerni.

## Grafikus felületen megjelenő elemek rövidítése
- **ru**: Ruler
- **ca**: Camember
- **ma**: Mask
- **sp**: Sponge
- **tv**: TVSZ
- **mu**: Mug
- **tr**: Transistor
- **fr**: Freshener
- **D**: Door
