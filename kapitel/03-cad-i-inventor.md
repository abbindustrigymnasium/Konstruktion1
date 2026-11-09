# Kapitel 3: CAD i Inventor

> **I det här kapitlet lär du dig**
> - hur en parametrisk CAD-modell är uppbyggd
> - hur du går från skiss till del, assembly och ritning i Inventor
> - hur du arbetar med färdiga komponenter och stora assemblies
> - hur du packar ihop en assembly och kontrollerar en modell med simulering

CAD, computer aided design, betyder att konstruktionen tas fram i ett datorprogram. Styrkan är inte att bilderna blir snygga. Styrkan är att du kan pröva hur delarna passar ihop, ändra ett mått och få hela konstruktionen uppdaterad, innan någon har sågat i materialet. I kursen använder du Autodesk Inventor. Knapparnas namn nedan är från den engelska versionen.

## Parametrisk modellering

Inventor är **parametriskt**. Det betyder att modellen styrs av mått och villkor som du kan ändra i efterhand. Ändrar du armens längd från 400 till 450 mm följer resten av delen med, och även assembly och ritning uppdateras. Förutsättningen är att du bygger upp modellen på rätt sätt, och därför är grunderna viktiga.

Inventor delar upp arbetet i filer som är kopplade till varandra:

| Fil | Filtyp | Innehåller |
|---|---|---|
| Del (part) | `.ipt` | En enskild detalj |
| Sammanställning (assembly) | `.iam` | Flera delar monterade ihop |
| Ritning (drawing) | `.idw` eller `.dwg` | 2D-ritning av del eller assembly |
| Presentation | `.ipn` | Sprängskiss och animation av hopsättning |

Eftersom filerna är länkade hittar en assembly inte sina delar om du flyttar dem. Det är därför du lämnar in projekt med Pack and Go, som beskrivs längre fram.

## Från skiss till del

Så här bygger du en del:

1. **Skapa en skiss** (Start 2D Sketch) på ett plan, till exempel XY.
2. **Rita enkel geometri** och lägg till **villkor** (constraints) som håller ihop formen: parallell, vinkelrät, lika långa.
3. **Måttsätt** med Dimension tills skissen är helt bestämd. Inventor visar i statusraden hur många mått som saknas. En obestämd skiss kan ändra form när du ändrar något annat.
4. **Skapa en feature**: Extrude drar ut profilen till en kropp. Revolve vrider den runt en axel.
5. **Bygg vidare** med Hole, Fillet (rundning), Chamfer (fasning) och Rectangular eller Circular Pattern för upprepade hål.
6. **Sätt materialet** och delnummer i iProperties. Då vet Inventor densiteten och delens massa, och uppgifterna kommer med på ritningen.

### Exempel: en kastarm i tre steg

```text
1. Skiss: en rektangel 400 x 30 mm, centrerad på X-axeln.
          Måtten sätts som parametrar: langd = 400 mm, hojd = 30 mm.
2. Extrude: dra ut profilen 12 mm. Armen får bredden 12 mm.
3. Hole: ett hål Ø 8 mm på 100 mm från ena änden (axeln).
          Spara som arm.ipt. Sätt material och delnamn i iProperties.
```

Genom att kalla måtten för `langd` och `hojd` kan du senare ändra dem på ett ställe (Manage → Parameters) och se hur modellen uppdateras.

## Från delar till assembly

I en **assembly** placerar du delar och låser hur de förhåller sig till varandra.

- **Ground (fixera):** den första delen låses i rummet. Övriga delar monteras mot den.
- **Constrain och Joint:** bestämmer till exempel att ett hål och en axel ska ligga i linje eller att två ytor ska ligga mot varandra. Joint Rotational låter en axel rotera, vilket gör att du kan kontrollera att armen går att vrida och inte krockar med ramen.
- **Interference Analysis:** letar efter delar som tar i varandra. Använd det innan du tillverkar.
- **Bill of Materials:** en lista över delarna som du kan använda när du skriver materiallistan.

## Färdiga komponenter

En konstruktör modellerar inte varje skruv själv. Komponenter hämtas från bibliotek.

**Content Center** är Inventors bibliotek över standardkomponenter som skruvar, muttrar och brickor. Du placerar dem direkt i din assembly med **Place from Content Center**.

**Tillverkares bibliotek** erbjuder CAD-modeller av deras produkter. [SolidComponents](https://www.solidcomponents.com/) är ett sådant bibliotek, med bland annat aluminiumprofiler och fästen under kategorin Beams and Profiles. Du laddar hem filerna och placerar dem i din assembly.

**Frame Generator** bygger ramar av profiler längs linjer i en skelettmodell. Verktyget fungerar i en assembly och är ett sätt att skapa stora ramar, men i smådjursställningen kommer du långt med nedladdade profiler.

### Arbeta med stora assemblies

När en assembly växer gäller några enkla regler. Spara alla filer i en och samma projektmapp. Dela upp stora konstruktioner i **underassemblies**, till exempel ett ben som en egen enhet. Då räcker det att bygga benet en gång och placera det fyra gånger. Ge filerna namn som går att förstå, till exempel `ben-justerbart.iam` i stället för `Assembly4.iam`.

## Pack and Go

När du lämnar in en assembly behöver mottagaren alla filer den hänvisar till. **Pack and Go** samlar ihop dem, även om filerna ligger på olika ställen. Guiden [Pack and go](../Sm%C3%A5djursst%C3%A4llning/Pack%20and%20go.docx) visar stegen: File → Save As → Pack and Go, välj en ny mapp, tryck Search Now, och Start. Komprimera sedan mappen till en zip-fil.

## Från CAD till tillverkning

CAD-modellen ska till slut bli en verklig del. Laserskärning och 3D-utskrift brukar utgå från en fil från CAD-programmet, och för laserskärning används ofta DXF-formatet, som du till exempel kan exportera från en yta med **Export Face As**. Uppgiften [Laserskär mobil och pennhållare](../Lasersk%C3%A4r%20mobil%20och%20pennh%C3%A5llare.docx) visar hur det går till. Tänk på att snittet tar bort material, och att en passning därför måste ta hänsyn till snittbredden. Det räknar vi på i [kapitel 4](04-ritningar-standarder.md).

## Simulering i Inventor

Inventor har en miljö för hållfasthetsberäkning, **Stress Analysis**. Du väljer material, lägger på laster och fästen, och programmet räknar ut spänningar, deformationer och säkerhetsfaktor med den så kallade finita elementmetoden. Materialet måste ha värden för elasticitetsmodul, densitet och sträckgräns. Det går att dimensionera med hjälp av detta, men resultatet blir aldrig bättre än dina antaganden. Enligt Autodesks dokumentation täcker analysen inte utmattning, alltså skador av upprepad belastning. Om datorn säger att du har säkerhetsfaktorn 12 men handräkningen säger 2 är något fel. Använd alltid en handberäkning som kontroll. Teorin kommer i kapitel 6–9.

## Begrepp

- **Parametrisk modellering:** modellen styrs av mått och villkor som går att ändra.
- **Skiss:** tvådimensionell profil som en tredimensionell del byggs upp från.
- **Feature:** byggsteg i en del, till exempel Extrude eller Hole.
- **Assembly:** en sammanställning av flera delar.
- **Constraint:** villkor som låser hur geometri eller delar förhåller sig till varandra.
- **Content Center:** Inventors bibliotek över standardkomponenter.
- **Pack and Go:** funktion som samlar en assembly och alla dess filer på ett ställe.

## Testa dig själv

1. Vad innebär det att en CAD-modell är parametrisk?
2. Varför ska en skiss vara helt bestämd innan du gör en Extrude?
3. Vad händer med din ritning när du ändrar ett mått i delen?
4. Varför går det inte att bara skicka `.iam`-filen till en kompis?
5. När lönar det sig att skapa en underassembly?
6. Varför räcker inte en simulering i Stress Analysis som enda kontroll?

## Övningar

**Grund.** Modellera en platta 100 × 60 × 5 mm med fyra hål Ø 6 mm placerade 10 mm från kanterna. Använd Rectangular Pattern och en parameter för plattans bredd.

**Grund.** Ändra parametern för plattans bredd och kontrollera att hålen flyttas rätt. Om de inte gör det: vilka villkor saknas?

**Vidare.** Modellera en axel och två lagerbockar som delar, sätt ihop dem med Joint Rotational och kör Interference Analysis.

**Utmaning.** Gör en enkel Stress Analysis på din platta: fäst den i två hål och lägg en kraft i mitten. Jämför resultatet med en handberäkning enligt kapitel 8, fritt upplagd balk. Hur stor är skillnaden, och vad beror den på?

## Koppling till projektet

I [Katapult](../projekt/katapult/README.md) modellerar du ram, arm och axel och sätter ihop dem. I [Smådjursställning](../projekt/smadjursstallning/README.md) arbetar du med färdiga profiler och en stor assembly och lämnar in med Pack and Go. Kunskaperna behövs också i [Robotmopp](../projekt/robotmopp/README.md) när du konstruerar chassit.

## Läs mer

- [Inventors hjälpsidor](https://help.autodesk.com/view/INVNTOR/2025/ENU/)
- [Stress Analysis i Inventors hjälp](https://help.autodesk.com/cloudhelp/2015/ENU/Inventor-Help/files/GUID-0C611437-B3EA-4EF4-809A-2DA68A27B32C.htm)
- [SolidComponents](https://www.solidcomponents.com/)

[← Föregående](02-moment-energi-kastbana.md) | [Innehåll](../README.md) | [Nästa →](04-ritningar-standarder.md)
