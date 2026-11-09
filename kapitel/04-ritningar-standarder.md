# Kapitel 4: Ritningar, standarder och normer

> **I det här kapitlet lär du dig**
> - hur en konstruktionsritning är uppbyggd
> - hur vyer, skala, linjer och måttsättning används
> - vad toleranser och passningar är och hur du räknar på dem
> - vilka system för teknisk standardisering som finns i Sverige och internationellt

En ritning är konstruktörens sätt att prata med den som ska tillverka. Tillverkaren ska kunna göra delen utan att fråga dig något, även om ni aldrig träffas och även om ni talar olika språk. Det fungerar bara om alla följer samma regler. Sådana regler kallas standarder, och utan dem skulle en M8-skruv köpt i Sverige inte passa en mutter köpt i Tyskland.

## Delarna i en ritning

En ritning innehåller:

- **Vyer** som visar delen från olika håll.
- **Mått** som anger alla storlekar.
- **Toleranser** som anger hur mycket måtten får avvika.
- **Ritningshuvud** med namn, ritningsnummer, skala, material och vem som ritat.

I Onshape högerklickar du på delen i Parts-listan och väljer **Create drawing of**. Du väljer en mall och kan låta Onshape föreslå vyer. Fler vyer tar du fram med **Projected view**, och med **Section view** får du en snittbild som visar hur delen ser ut inuti.

### Projektionsmetod

Vyerna ska placeras på ett bestämt sätt i förhållande till varandra. I Europa används oftast **projektionsmetod 1** (first-angle): vyn sedd från vänster placeras till höger om framvyn. I USA används oftast metod 3, där vyerna ligger på motsatt sida. Metoden anges med en liten symbol i ritningshuvudet. I Onshape styrs metoden av ritningsmallen: en ISO-mall ger metod 1 och millimeter, och en ANSI-mall ger metod 3. Välj en ISO-mall, och kontrollera att symbolen i ritningshuvudet stämmer.

### Linjer, format och skala

Linjetjocklek och linjetyp har olika betydelse. Grova heldragna linjer visar synliga kanter, och streckade linjer visar dolda kanter. Streckprickade linjer markerar symmetri och centrumlinjer. Ritningar görs på standardformat som A3 och A4.

**Skala** anger hur stor bilden är jämfört med verkligheten:

```text
1:1   naturlig storlek
1:5   förminskning, 800 mm i verkligheten blir 160 mm på papperet
2:1   förstoring, 12 mm blir 24 mm på papperet
```

Måtten skrivs alltid med den verkliga storleken, oavsett skala.

### Måttsättning

Grundregler som hjälper den som ska tillverka:

1. Alla mått som behövs ska finnas, men varje mått bara en gång.
2. Mått anges i millimeter och enheten skrivs inte ut.
3. Placera måtten utanför figuren när det går.
4. Utgå från samma kant eller yta, en så kallad **referens**, så att felen inte läggs ihop.
5. Tänk på hur delen tillverkas. Hålens centrumavstånd är ofta viktigare än avståndet från kanten.

## Toleranser

Inget tillverkas exakt. Om du skriver 45 mm kan det bli 44,8 eller 45,2. En **tolerans** anger hur stor avvikelse som är godtagbar.

```text
45 ± 0,3      → minsta tillåtna mått 44,7 mm, största 45,3 mm
```

Allmänna toleranser kan anges med standarden ISO 2768, till exempel klass m (medel). Då gäller för längdmått bland annat ±0,2 mm för mått mellan 6 och 30 mm och ±0,3 mm mellan 30 och 120 mm. Hänvisningen skrivs i ritningshuvudet och täcker alla mått som inte har en egen tolerans.

### Exempel: passning av en axel i ett hål

En **passning** beskriver hur två delar ska sitta ihop. ISO:s toleranssystem använder beteckningar som Ø8 H7/g6, där H7 gäller hålet och g6 gäller axeln.

```text
Hål  Ø8 H7:  8,000 till 8,015 mm
Axel Ø8 g6:  7,986 till 7,995 mm

Minsta spel: 8,000 - 7,995 = 0,005 mm
Största spel: 8,015 - 7,986 = 0,029 mm
```

Spelet är alltid positivt, så axeln kan rotera i hålet utan att fastna. Det kallas **spelpassning**. Om hålet i stället är mindre än axeln får du en **presspassning**, som håller delarna fast.

### Exempel: snittbredd vid laserskärning

Materialet som försvinner i snittet påverkar passningen. Om laserskäraren tar bort 0,15 mm blir ett spår 0,15 mm bredare än den ritade linjen visar, medan en tapp blir 0,15 mm smalare.

```text
Spår som ska bli 3,00 mm:   rita 3,00 - 0,15 = 2,85 mm
Tapp som ska bli 3,00 mm:   rita 3,00 + 0,15 = 3,15 mm
```

Hur mycket snittet tar bort beror på maskin och material. Gör alltid ett provsnitt.

## Standarder och normer

En **standard** är ett dokument med gemensamma regler som tagits fram i samförstånd. En **norm** används ofta som ett bredare ord för regler och riktlinjer. Standarder är i grunden frivilliga, men de blir i praktiken nödvändiga när kunder, lagar eller upphandlingar kräver dem.

| Nivå | Organisation | Exempel |
|---|---|---|
| Internationell | ISO (allmänt), IEC (el) | ISO 2768 toleranser |
| Europeisk | CEN, CENELEC | EN 10025 om konstruktionsstål, Eurokoderna |
| Nationell | SIS (Sverige) | SS-EN ISO-standarder, där svensk utgåva finns |

Ett dokument märkt SS-EN ISO är en internationell standard som antagits som europeisk och svensk. Du kan läsa beteckningen baklänges och se vägen den tagit.

**Lagar skiljer sig från standarder.** Inom EU finns gemensamma regler för maskiners säkerhet, och produkter som omfattas ska vara CE-märkta. Regelverket förändras över tid, så kontrollera alltid vad som gäller. Arbetsmiljöverket är den svenska myndighet som arbetar med dessa frågor.

### Standarder du möter i kursen

| Område | Exempel | Vad det betyder |
|---|---|---|
| Ritningar | Linjer, vyer, ritningsformat | Gemensamt språk på ritningar |
| Toleranser | ISO 2768, ISO 286 | Hur mycket mått får avvika |
| Fästelement | M6-, M8-gängor | Skruvar och muttrar passar ihop |
| Material | EN 10025 (stål) | Vad beteckningen S235 garanterar |

Standardblad är ofta skyddade och säljs av standardiseringsorganisationerna. Det du behöver i kursen får du genom din lärare, kompendiet och tabellsamlingen.

## Begrepp

- **Vy:** bild av delen sedd från ett bestämt håll.
- **Projektionsmetod:** regel för hur vyer placeras i förhållande till varandra.
- **Skala:** förhållandet mellan måtten på ritningen och i verkligheten.
- **Tolerans:** tillåten avvikelse från ett mått.
- **Passning:** hur två delar sitter ihop, till exempel spel eller press.
- **Standard:** gemensamma regler som tagits fram i samförstånd.
- **SIS, CEN, ISO:** svensk, europeisk och internationell organisation för standardisering.

## Testa dig själv

1. Varför behövs standarder? Ge ett vardagsexempel.
2. Vad är skillnaden på projektionsmetod 1 och 3?
3. Varför skriver du inte ut enheten "mm" vid varje mått?
4. Varför utgår man ofta från samma referens när man måttsätter?
5. Vad är skillnaden mellan en standard och en lag?
6. Vad betyder det att en standard är märkt SS-EN ISO?

## Koppling till projektet

I [Katapult](../projekt/katapult/README.md) tar du fram en ritning som används i verkstaden, och i [Smådjursställning](../projekt/smadjursstallning/README.md) utgår du från ritningar och standardiserade profiler. Passningar för axlar och fästen använder du när du konstruerar chassit i [Robotmopp](../projekt/robotmopp/README.md).

## Läs mer

- [Multiview-projektion (Wikipedia, engelska)](https://en.wikipedia.org/wiki/Multiview_orthographic_projection)
- [Ritningar (Wikipedia, engelska)](https://en.wikipedia.org/wiki/Engineering_drawing)
- [SIS, Svenska institutet för standarder](https://www.sis.se/)
- [CEN och CENELEC, europeisk standardisering](https://www.cencenelec.eu/european-standardization/)
- [ISO (Wikipedia, engelska)](https://en.wikipedia.org/wiki/International_Organization_for_Standardization)
- [Arbetsmiljöverket](https://www.av.se)

[← Föregående](03-cad-i-onshape.md) | [Innehåll](../README.md) | [Nästa →](05-material-och-materialval.md)
