# Kapitel 5: Material och materialval

> **I det här kapitlet lär du dig**
> - vilka egenskaper som skiljer olika material åt
> - hur stål, aluminium, trä och plast används i konstruktioner
> - hur du jämför material med en enkel beräkning
> - hur materialvalet hänger ihop med tillverkning, kostnad, kvalitet och hållbarhet

Varför är cykelramar ofta av aluminium eller stål, men sällan av trä? Varför byggs broar av stål och betong och inte av aluminium, trots att aluminium är lättare? Materialets egenskaper avgör vad en konstruktion klarar, hur den tillverkas, vad den kostar och vad som händer med den efteråt.

## Egenskaper som spelar roll

| Egenskap | Vad den betyder | Exempel |
|---|---|---|
| Hållfasthet | Hur stor spänning materialet tål | Stål tål mer än trä per area |
| Styvhet (E-modul) | Hur lite materialet ger efter under last | Stål är ungefär tre gånger styvare än aluminium |
| Seghet | Hur mycket energi materialet tål innan det går av | Stål är segt, glas är sprött |
| Densitet | Hur tungt materialet är per volym | Stål ca 7850 kg/m³, aluminium ca 2700 kg/m³ |
| Korrosionsbeständighet | Hur materialet tål väta och kemikalier | Rostfritt stål, anodiserad aluminium |
| Bearbetbarhet | Hur lätt materialet går att forma, svetsa, skära | Trä och PLA är enkla att bearbeta |

Lägg märke till skillnaden mellan **hållfasthet** och **styvhet**. Ett material kan tåla höga spänningar men ändå böja sig mycket under last. Aluminium går ofta bra att använda ur hållfasthetssynpunkt, men en lika grov balk av aluminium böjer sig tre gånger så mycket som en av stål.

## Vanliga konstruktionsmaterial

**Stål** är billigt, starkt och lätt att svetsa, men det rostar om det inte skyddas. Beteckningen S235 anger att sträckgränsen är minst 235 N/mm² för tunna dimensioner, och talet 355 i S355 på samma sätt. **Rostfritt stål** innehåller krom som bildar ett skyddande ytskikt. Det är dyrare och används till exempel i livsmedelsindustrin.

**Aluminium** är lätt och tål väder bra. Det går att strängpressa till profiler med invecklad form. Därför finns färdiga T-spårsprofiler som du kan bygga med som en byggsats. **Trä** är förnybart och lätt att bearbeta, men egenskaperna varierar med fuktighet och fiberriktning. **Plast** är ett brett område. PLA används ofta vid 3D-utskrift, medan ABS och PETG tål värme och stötar bättre. Plaster kryper, alltså deformeras långsamt under konstant last, så en plastdetalj som håller i dag kan ha böjt sig efter ett år.

### Ungefärliga materialdata

Värdena nedan är hämtade från öppna källor. De är förenklade, varierar med dimension, leverans och källa, och ska bara användas för att jämföra material och för exemplen i den här boken. Vid proven i kursen använder du tabellsamlingen som delas ut i klassrummet.

| Material | Sträckgräns Re eller Rp0,2 (N/mm²) | Brottgräns Rm (N/mm²) | E-modul (GPa) | Densitet (kg/m³) |
|---|---|---|---|---|
| Konstruktionsstål S235 | 235 | 360–510 | ca 200–210 | ca 7850 |
| Konstruktionsstål S355 | 355 | 470–630 | ca 200–210 | ca 7850 |
| Aluminium 6063-T6 | 160 | 190 | ca 69 | ca 2690 |
| Aluminium 6063-T5 | 97 | 140 | ca 69 | ca 2690 |
| Trä C24 (gran, karakteristiska värden) | böj 24, drag 14,5 | – | ca 11 | ca 420 |
| PLA, 3D-utskrift | ca 50 | – | ca 2,3–3,3 | ca 1240 |

Källor: [EN 10025-2 hos Arvedi](https://www.arvedi.it/en/acciaieria/products/hot-rolled-steels/non-alloyed-structural-steels-as-per-en-10025-2/) (S235 och S355, för tjocklek under 16 mm), [Wikipedia om 6063](https://en.wikipedia.org/wiki/6063_aluminium_alloy), [Träguiden om C24](https://www.traguiden.se/produkter/konstruktionsvirke/konstruktionsvirke-obehandlat/konstruktionsvirke-hallfasthetsklass-c24/konstruktionsvirke-c24-gran-obehandlad-45x95/), [Prusa PLA-datablad](https://cdn.shopify.com/s/files/1/1745/6181/files/PRUSA_PLA_TechSheet_ENG.pdf) och [Wikipedia om E-modul](https://en.wikipedia.org/wiki/Young%27s_modulus). För PLA beror värdena starkt på utskriftens riktning och tillverkare.

Trä: talet i C24 anger den karakteristiska böjhållfastheten. Det är ett värde som minst 95 av 100 virkesbitar i ett parti ska nå upp till, och i byggkonstruktioner används därefter särskilda säkerhetsregler, Eurokoderna.

## Att jämföra material

Ett material bedöms sällan bara efter hållfasthet. Det väsentliga är ofta vikten för en given bärförmåga.

### Exempel: stål eller aluminium i ett dragstag

Ett stag ska ta dragkraften 5000 N med säkerhetsfaktorn 2. Hur tungt blir staget per meter i S235 respektive 6063-T6? Vi använder formlerna som förklaras i kapitel 6 och 7.

```text
S235:     σtill = 235 / 2 = 117,5 N/mm²
          A = 5000 / 117,5 = 42,6 mm²
          massa per meter = 42,6 · 10⁻⁶ · 7850 = 0,33 kg/m

6063-T6:  σtill = 160 / 2 = 80 N/mm²
          A = 5000 / 80 = 62,5 mm²
          massa per meter = 62,5 · 10⁻⁶ · 2690 = 0,17 kg/m
```

Stålstaget har den mindre arean. Aluminiumstaget väger ändå bara ungefär hälften så mycket per meter. Väger vikten tungt, till exempel i ett fordon, kan aluminium vara rätt trots högre kilopris. I en stationär konstruktion är stål ofta bättre.

Fråga dig alltid också om styvheten räcker. Staget ovan i aluminium förlänger sig mer för varje meter än stålstaget, och kapitel 6 visar hur du räknar ut hur mycket.

## Materialval i praktiken

Ett strukturerat materialval följer samma tanke som valet av koncept i kapitel 1:

1. **Vad måste materialet klara?** Last, miljö, temperatur och form.
2. **Hur ska delen tillverkas?** Bockning, svarvning, laserskärning eller 3D-utskrift?
3. **Vad finns tillgängligt och vad kostar det?**
4. **Hur blir miljöpåverkan?** Det går att väga in hela livscykeln, från råvara till återvinning.
5. **Jämför** i en matris och motivera valet skriftligt.

## Tillverkning, kvalitet och lönsamhet

Hur en konstruktion formas beror på hur den ska tillverkas. En konstruktion som bara ska göras i några exemplar kan laserskäras eller 3D-skrivas ut. Ska den tillverkas i hundratusentals exemplar kan det löna sig att gjuta eller pressa delarna, även om verktygen kostar mycket.

Kvalitet betyder att produkten håller det som lovats. Kvalitet handlar också om att varje exemplar blir likadant. Toleranser, kontroll och val av tillverkningsmetod påverkar kvaliteten, men också priset, och snäva toleranser kostar mer. En lönsam konstruktion har precis så hög kvalitet som användaren behöver, och inte mer.

**Hållbarhet** kommer in på flera nivåer. Att välja återvinningsbart material räcker inte om produkten går sönder i förtid eller inte går att reparera. Färre material i samma produkt, skruvade i stället för limmade förband och utbytbara delar gör den lättare att reparera och återvinna. Som konstruktör ställs du ibland inför svåra val mellan kostnad, prestanda och miljöpåverkan, och det är bra att kunna motivera vilket val du gjort och varför.

## Begrepp

- **Hållfasthet:** ett materials förmåga att tåla spänning innan det deformeras eller går sönder.
- **Styvhet:** ett materials förmåga att stå emot deformation. Mäts med elasticitetsmodulen E.
- **Seghet:** hur mycket energi ett material kan ta upp innan brott.
- **Densitet:** massa per volym.
- **Krypning:** långsam deformation under konstant last.
- **Livscykel:** en produkts väg från råvara och tillverkning till användning och avfall.

## Testa dig själv

1. Vad är skillnaden mellan hållfasthet och styvhet?
2. Varför är aluminium ofta populärt i fordon?
3. Varför används T-spårsprofiler av aluminium och inte av stål i maskinbyggsatser?
4. Vad är krypning och i vilket material är det särskilt viktigt att tänka på det?
5. Ge två sätt som materialval påverkar en produkts miljöpåverkan.
6. Hur kan valet av tillverkningsmetod hänga ihop med hur många produkter som ska göras?

## Koppling till projektet

I [Katapult](../projekt/katapult/README.md) väljer du material, motiverar valet och skriver en materiallista. I [Smådjursställning](../projekt/smadjursstallning/README.md) arbetar du med aluminiumprofiler, och i [Hållfasthetslära](../projekt/hallfasthetslara/README.md) använder du materialvärden för att dimensionera.

## Läs mer

- [Livscykelanalys (Wikipedia, engelska)](https://en.wikipedia.org/wiki/Life-cycle_assessment)
- [Stål (Wikipedia, engelska)](https://en.wikipedia.org/wiki/Steel)
- [Konstruktionsvirke, Träguiden](https://www.traguiden.se/om-tra/materialet-tra/trabaserade-produkter/virkestyper-och-kvalitet/konstruktionsvirke/)

[← Föregående](04-ritningar-standarder.md) | [Innehåll](../README.md) | [Nästa →](06-drag-tryck-hookes-lag.md)
