# Kapitel 3: CAD i Onshape

> **I det här kapitlet lär du dig**
> - hur en parametrisk CAD-modell är uppbyggd
> - hur du går från skiss till del, assembly och ritning i Onshape
> - hur du arbetar med färdiga komponenter och stora assemblies
> - hur du delar ett projekt och kontrollerar en modell med simulering

CAD, computer aided design, betyder att konstruktionen tas fram i ett datorprogram. Styrkan är inte att bilderna blir snygga. Styrkan är att du kan pröva hur delarna passar ihop, ändra ett mått och få hela konstruktionen uppdaterad, innan någon har sågat i materialet. I kursen använder du Onshape, som körs i webbläsaren. Du behöver ett konto och nätverk, och läraren berättar hur du får ditt konto. Verktygens namn nedan är på engelska, som i Onshapes engelska gränssnitt.

## Parametrisk modellering

Onshape är **parametriskt**. Det betyder att modellen styrs av mått och villkor som du kan ändra i efterhand. Ändrar du armens längd från 400 till 450 mm följer resten av delen med, och även assembly och ritning uppdateras. Förutsättningen är att du bygger upp modellen på rätt sätt, och därför är grunderna viktiga.

Allt du gör samlas i ett **dokument** i molnet. Dokumentet består av flikar som hänger ihop:

| Flik | Innehåller |
|---|---|
| Part Studio | En eller flera delar som hör ihop, med skisser och features |
| Assembly | Delar monterade ihop |
| Drawing | 2D-ritning av del eller assembly |

Skillnaden mot att arbeta med vanliga filer är att du inte behöver hålla reda på någon mapp och att dokumentet sparas automatiskt. En assembly tappar inte bort sina delar, för de ligger i samma dokument eller är länkade till ett annat. Dessutom kan du modellera flera delar i samma Part Studio, vilket är praktiskt när de ska passa mot varandra.

## Från skiss till del

Så här bygger du en del:

1. **Skapa en skiss** (Sketch) på ett plan, till exempel Top.
2. **Rita enkel geometri** och lägg till **villkor** (constraints) som håller ihop formen: parallell, vinkelrät, lika långa.
3. **Måttsätt** med Dimension tills skissen är helt bestämd. Onshape visar det med färg: svarta linjer är helt bestämda, blå saknar mått eller villkor och röda betyder att villkoren krockar. En obestämd skiss kan ändra form när du ändrar något annat.
4. **Skapa en feature**: Extrude drar ut profilen till en kropp, som en ny del (New) eller som tillägg till en befintlig del (Add). Med Remove skär den bort material. Revolve vrider profilen runt en axel.
5. **Bygg vidare** med Hole, Fillet (rundning), Chamfer (fasning) och Linear Pattern eller Circular Pattern för upprepade hål. Mirror speglar delar över ett plan.
6. **Sätt materialet** genom att högerklicka på delen i Parts-listan och välja **Assign material**. Då vet Onshape densiteten och kan räkna ut delens massa i **Mass properties**, som du hittar nere till höger.

Skisser och features hamnar i **Feature list** till vänster, i den ordning du gjorde dem. Du ändrar en rad genom att dubbelklicka på den eller högerklicka och välja **Edit**.

### Exempel: en kastarm i fyra steg

```text
1. Variable: skapa variablerna langd = 400 mm och hojd = 30 mm.
2. Sketch: en rektangel #langd x #hojd, centrerad på origo.
3. Extrude (New): dra ut profilen 12 mm. Armen får bredden 12 mm.
4. Hole: skissa en punkt 100 mm från ena änden (axeln)
          och gör ett hål Ø 8 mm där.
          Döp delen till arm. Sätt material med Assign material.
```

Genom att kalla måtten för `langd` och `hojd` kan du senare ändra dem på ett ställe, i Variable-raden i Feature list, och se hur modellen uppdateras. Variabelnamn får bara innehålla engelska bokstäver, siffror och understreck, så skriv `langd` utan å och ä. Variabeln måste också ligga före den skiss som använder den.

## Från delar till assembly

I en **assembly** placerar du delar och låser hur de förhåller sig till varandra.

- **Insert:** hämtar delar från dokumentets Part Studios, eller från andra dokument, till din assembly. Du kan också hämta en hel assembly och använda den som underassembly.
- **Fix:** den första delen låses i rummet genom att du högerklickar på den och väljer Fix. Övriga delar monteras mot den.
- **Mate connector:** en liten koordinatpunkt på en del. Onshape föreslår sådana punkter automatiskt på till exempel hålets mitt, och två delar placeras genom att deras connectorer riktas mot varandra.
- **Mate:** bestämmer hur två delar får röra sig mot varandra. Ofta räcker det med en mate mellan två delar.
- **Interference detection:** letar efter delar som tar i varandra. Du hittar det under analysverktygen nere till höger. Använd det innan du tillverkar.
- **Bill of Materials:** en lista över delarna som du kan använda när du skriver materiallistan.

| Mate | Rörelse | Exempel |
|---|---|---|
| Fastened | Ingen rörelse | En skruv i ett hål, två delar som är fast monterade |
| Revolute | Rotation runt en axel | Katapultarmen runt axeln |
| Slider | Rörelse längs en axel | Ett ben som kan höjas och sänkas |

Det finns fler, till exempel Planar, Cylindrical och Ball. Med en Revolute kan du dra i armen i assemblyn och kontrollera att den går att vrida och inte krockar med ramen.

## Färdiga komponenter

En konstruktör modellerar inte varje skruv själv. Komponenter hämtas från bibliotek.

**Standard content** är Onshapes bibliotek över standardkomponenter som skruvar, muttrar och brickor, bland annat enligt ISO och DIN. Du hittar det i dialogen Insert, under fliken Standard content, och det används i en assembly.

**Tillverkares bibliotek** erbjuder CAD-modeller av deras produkter. [SolidComponents](https://www.solidcomponents.com/) är ett sådant bibliotek, med bland annat aluminiumprofiler och fästen under kategorin Beams and Profiles. Ladda hem modellen, helst i STEP-format om det finns, och klicka sedan på plusset längst ned till vänster i dokumentet och välj **Import**. Varje fil blir en egen flik. Importerade delar saknar Feature list, så du kan mäta dem och montera dem men inte ändra hur de är uppbyggda.

**Frame** är en feature i Part Studio som bygger ramar av profiler längs linjer i en skiss. Onshape har färdiga profiler, till exempel ISO-rör och T-spårsprofiler. Verktyget är ett sätt att skapa stora ramar, men i smådjursställningen kommer du långt med nedladdade profiler.

### Arbeta med stora assemblies

När en assembly växer gäller några enkla regler. Håll ihop projektet i ett och samma dokument. Dela upp stora konstruktioner i **underassemblies**, till exempel ett ben som en egen enhet. Då räcker det att bygga benet en gång och placera det fyra gånger. Ge dokument, flikar och delar namn som går att förstå, till exempel `ben-justerbart` i stället för `Assembly 4`.

## Dela och lämna in

Eftersom modellen ligger i molnet behöver du inte packa ihop och skicka några filer. Med **Share** bjuder du in andra till dokumentet och väljer om de får ändra (**Can edit**) eller bara titta (**Can view**). I samma dialog kan du kopiera en länk som ger läsbehörighet. Tänk på att alla som har länken kommer åt modellen.

Flera kan arbeta i samma dokument samtidigt, och ändringarna syns direkt för alla. Det passar bra i grupprojekt som katapulten. En Drawing-flik kan däremot bara redigeras av en person åt gången.

Med **Versions and history** ser du allt som hänt i dokumentet och kan gå tillbaka till en tidigare punkt. Med **Create version** sparar du ett namngivet läge som inte kan ändras. Skapa en version innan du lämnar in, så att läraren ser exakt det du är nöjd med, och dela sedan dokumentet med läraren eller lämna in på det sätt läraren anger.

## Från CAD till tillverkning

CAD-modellen ska till slut bli en verklig del. Laserskärning och 3D-utskrift brukar utgå från en fil från CAD-programmet, och för laserskärning används ofta DXF-formatet. I Onshape högerklickar du på en plan yta i Part Studio och väljer **Export as DXF/DWG**. Välj millimeter som enhet. Till 3D-skrivare högerklickar du på delen och väljer **Export** med formatet STL eller 3MF, och du kan exportera till STEP på samma sätt. Uppgiften [Laserskär mobil och pennhållare](../Lasersk%C3%A4r%20mobil%20och%20pennh%C3%A5llare.docx) visar arbetsgången för laserskärning. Beskrivningen är skriven för ett annat CAD-program, men kraven gäller och du gör CAD-arbetet i Onshape. Tänk på att snittet tar bort material, och att en passning därför måste ta hänsyn till snittbredden. Det räknar vi på i [kapitel 4](04-ritningar-standarder.md).

## Simulering

Hållfasthetsberäkning i datorn görs oftast med den så kallade finita elementmetoden, FEM. Programmet delar upp modellen i små element och räknar ut spänningar och deformationer. I Onshape heter funktionen **Simulation**, och den används i en assembly. Du behöver fixera minst en del och lägga på minst en last, och materialet måste ha värden för densitet, Poissons tal, elasticitetsmodul och sträckgräns. Resultatet kan bland annat visa spänningar och en säkerhetsfaktor, alltså sträckgränsen delad med spänningen.

Simulation finns inte i alla Onshape-planer. Läraren berättar om du har tillgång till den. Har du inte det gör du dimensioneringen för hand, som i kapitel 6–9.

Det går att dimensionera med hjälp av simulering, men resultatet blir aldrig bättre än dina antaganden. Analysen är linjär och statisk, så den säger inget om utmattning, alltså skador av upprepad belastning. Om datorn säger att du har säkerhetsfaktorn 12 men handräkningen säger 2 är något fel. Använd alltid en handberäkning som kontroll. Teorin kommer i kapitel 6–9.

## Begrepp

- **Parametrisk modellering:** modellen styrs av mått och villkor som går att ändra.
- **Dokument:** samling av flikar i molnet där du har delar, assemblies och ritningar.
- **Part Studio:** flik där du modellerar en eller flera delar.
- **Skiss:** tvådimensionell profil som en tredimensionell del byggs upp från.
- **Feature:** byggsteg i en del, till exempel Extrude eller Hole.
- **Assembly:** en sammanställning av flera delar.
- **Mate:** bestämmer hur två delar får röra sig mot varandra.
- **Mate connector:** koordinatpunkt på en del som två delar riktas mot varandra med.
- **Standard content:** Onshapes bibliotek över standardkomponenter.
- **Version:** ett sparat, namngivet läge av dokumentet som inte går att ändra.

## Testa dig själv

1. Vad innebär det att en CAD-modell är parametrisk?
2. Varför ska en skiss vara helt bestämd innan du gör en Extrude?
3. Vad händer med din ritning när du ändrar ett mått i delen?
4. Vilken mate passar för en axel som ska kunna rotera i ett hål, och vilken passar för två delar som ska sitta fast?
5. När lönar det sig att skapa en underassembly?
6. Hur gör du för att läraren ska se exakt det läge du vill lämna in?
7. Varför räcker inte en simulering som enda kontroll?

## Koppling till projektet

I [Katapult](../projekt/katapult/README.md) modellerar du ram, arm och axel och sätter ihop dem. I [Smådjursställning](../projekt/smadjursstallning/README.md) arbetar du med färdiga profiler och en stor assembly och delar dokumentet med läraren. Kunskaperna behövs också i [Robotmopp](../projekt/robotmopp/README.md) när du konstruerar chassit.

## Läs mer

- [CAD Basics](https://learn.onshape.com/learning-paths/introduction-to-cad) och [Onshape Fundamentals](https://learn.onshape.com/learning-paths/onshape-fundamentals), kurser i Onshapes Learning Center. Du loggar in med ditt Onshape-konto.
- [Mates i Onshapes hjälp](https://cad.onshape.com/help/Content/Assembly/mates.htm)
- [Simulation i Onshapes hjälp](https://cad.onshape.com/help/Content/Assembly/simulation.htm)
- [Importera filer i Onshapes hjälp](https://cad.onshape.com/help/Content/Document/importing_files.htm)
- [SolidComponents](https://www.solidcomponents.com/)

[← Föregående](02-moment-energi-kastbana.md) | [Innehåll](../README.md) | [Nästa →](04-ritningar-standarder.md)
