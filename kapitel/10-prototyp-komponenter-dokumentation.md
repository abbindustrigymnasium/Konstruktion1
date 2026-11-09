# Kapitel 10: Prototyp, komponenter, provning och dokumentation

> **I det här kapitlet lär du dig**
> - hur du väljer komponenter och håller en budget
> - hur du bygger en prototyp med enkla verktyg
> - hur du planerar test, mäter och drar slutsatser
> - hur du konstruerar för montering, med ett robotchassi som exempel
> - hur du dokumenterar och redovisar ett konstruktionsarbete

En ritning är inte en maskin. När din konstruktion ska bli något som fungerar varje gång kommer du att märka att skruvar glappar, att kablar är i vägen och att sensorn inte ser det du trodde. Det är här prototyper, mätningar och dokumentation blir viktiga. I det här kapitlet samlar vi det som krävs för att gå från modell till fungerande produkt.

## Val av komponenter

En **komponent** är en färdig del som du köper eller hämtar, till exempel en motor, en sensor, en skruv eller en profil. För varje komponent ställer du samma frågor:

| Fråga | Exempel |
|---|---|
| Vad ska den göra? | Mäta avstånd till en vägg |
| Vilka gränser har den? | Mätområde, spänning, tillåten belastning |
| Hur får den plats och fästs? | Hålavstånd, mått, kontakter |
| Vad kostar den och går den att få tag på? | Budget, leveranstid |
| Vad händer om den går sönder? | Går den att byta, och blir något farligt? |

Komponenternas mått och gränser står i **datablad** som du hittar hos tillverkaren. Lita inte blint på vad en butikssida skriver. Mät också den riktiga komponenten med skjutmått, särskilt om något ska få plats i en utskuren eller utskriven del.

### Exempel: materiallista inom budget

En **materiallista**, ofta kallad BOM efter engelska bill of materials, visar vad som behövs och vad det kostar. Priserna nedan är påhittade för exemplet.

| Artikel | Antal | Pris (kr) |
|---|---|---|
| Motor med växel | 1 | 89 |
| Servo | 1 | 45 |
| Plattor och lim | – | 60 |
| Skruv och mutter | – | 35 |
| **Summa** |  | **229** |

Summan 229 kr ryms inom en budget på 250 kr. Spara kvitton, så kan du visa vad som faktiskt användes.

## Prototyper

En **prototyp** är en tidig version som du bygger för att lära dig något. Den behöver inte vara snygg. Målet är att billigt ta reda på om idén fungerar. Bygg delar var för sig och testa dem innan du bygger ihop allt. Mekanik kan provas med kartong, snabbt 3D-utskrivna bitar eller lego innan du gör något i slutligt material.

## Konstruera för montering: robotchassit

Ett **chassi** är grunden som bär motor, styrning, elektronik och sensorer. När du konstruerar ett chassi handlar det mindre om hållfasthet och mer om att alla delar ska få plats, sitta stabilt och gå att komma åt.

Fundera på följande:

- **Placering.** Var hamnar tyngdpunkten? Var ska motor, servo och styrenhet sitta för att kablarna inte ska bli för långa eller trassliga?
- **Fästen.** Hålbilder för komponenterna går att mäta upp. Lämna lite spel och gör hellre avlånga hål om ett mått är osäkert.
- **Sensorer.** En ultraljudssensor behöver fri sikt framåt och får inte sitta där den ser chassit eller hjulen.
- **Penna eller verktyg.** Ett verktyg som ska hålla kontakt med golvet behöver en viss fjädring så att det inte lyfter bilen.
- **Service.** Går batteri och kablar att byta utan att plocka isär allt?

### Exempel: rimlighet för ett sensorfäste

En sensor på 50 g ska sitta på en utskriven konsol av PLA, 15 mm bred och 3 mm tjock, 40 mm ut. Hur stor blir spänningen av tyngden?

```text
F = 0,050 · 9,82 = 0,49 N
Mb = 0,49 · 40 = 19,6 Nmm
Wb = 15 · 3² / 6 = 22,5 mm³
σb = 19,6 / 22,5 = 0,87 N/mm²
```

Jämfört med PLA:s ungefärliga hållfasthet på 50 N/mm² är säkerheten mycket stor. Spänningen från tyngden är alltså inget problem. Det svåra är stötar när bilen kör in i något och att fästet inte vibrerar så att sensorn mäter fel. Beräkningen visar var du inte behöver lägga din tid.

## Provning: mätning, simulering och test

Du lär dig något först när du jämför med verkligheten. **Provning** kan ske på tre sätt:

- **Simulering** kör modellen i datorn, till exempel Stress Analysis i Inventor eller ett styrprogram i en simulator som turtlesim. Det är billigt och går snabbt, men visar bara det modellen innehåller.
- **Mätning** ger siffror på verkligheten.
- **Funktionstest** visar om produkten gör det den ska, gång på gång.

Ändra **en sak i taget** och mät igen. Om du ändrar tre saker vet du inte vilken av dem som gjorde skillnad.

### Exempel: kast, medelvärde och jämförelse

Du mäter fem kast: 3,42, 3,61, 3,38, 3,55 och 3,47 m. Beräkningen sa 3,90 m.

```text
Medelvärde: 3,49 m
Spridning (största − minsta): 3,61 − 3,38 = 0,23 m
Avvikelse från beräknat värde: (3,49 − 3,90) / 3,90 = −11 %
```

Fem kast är bättre än ett, och skillnaden mellan modell och mätning är normal så länge du kan förklara den. Det kan bero på luftmotstånd och friktion, och det kan också bero på att modellens antagande om verkningsgrad var lite för högt.

### Exempel: repeterbarhet

En maskin sorterar 47 av 50 bitar rätt. Andelen blir 47 / 50 = 94 %. En robotmopp berör 56 av 64 rutor, alltså 87,5 % täckning. Ett mått i procent gör det lätt att jämföra två versioner av lösningen.

Provning kan också gälla säkerhet. Kör bilen med hjulen i luften första gången, och fundera på vad som händer om något går fel. Ett exempel: om bilen tappar kontakten ska den stanna. Den hinner då rulla en bit. Vid 0,36 m/s och en stopptid på 0,5 s blir det 0,36 · 0,5 = 0,18 m.

## Dokumentation och redovisning

**Dokumentation** är det som gör att någon annan kan förstå, granska och bygga vidare på ditt arbete. En bra projektdokumentation innehåller:

| Del | Innehåll |
|---|---|
| Uppgift och krav | Vad ska lösningen klara? |
| Idéer och val | Skisser, beslutsmatris, varför ni valde som ni gjorde |
| Beräkningar | Formler, värden, antaganden och rimlighetsbedömning |
| Konstruktion | CAD-bilder, ritningar, materiallista |
| Test och resultat | Vad ni mätte, tabeller, bilder |
| Utvärdering | Vad fungerade, vad skulle ni göra annorlunda? |

Spara material medan ni arbetar: bilder av varje steg, misslyckade försök och korta anteckningar. Ett misslyckat försök med en förklaring är bra dokumentation.

Vid **redovisningen** berättar du varför konstruktionen ser ut som den gör. Börja med problemet, visa lösningen och dina resultat, och berätta vad du lärde dig. Visa helst att konstruktionen fungerar.

## Begrepp

- **Komponent:** färdig del som används i en konstruktion.
- **Datablad:** tillverkarens dokument med en komponents mått, gränser och egenskaper.
- **Materiallista (BOM):** förteckning över artiklar, antal och kostnad.
- **Prototyp:** tidig version som byggs för att lära sig eller testa.
- **Simulering:** provning av en modell i datorn.
- **Repeterbarhet:** att en produkt ger samma resultat gång efter gång.
- **Chassi:** bärande grundstruktur i en maskin eller bil.

## Testa dig själv

1. Vilka frågor bör du ställa innan du väljer en komponent?
2. Varför ska du mäta själva komponenten även om det finns ett datablad?
3. Vad är poängen med att bygga en prototyp som inte är snygg?
4. Varför ska du ändra en sak i taget vid test?
5. Vad gör simulering bra och vad gör den dåligt?
6. Varför är det värdefullt att dokumentera misslyckade försök?
7. Vad är viktigt att tänka på när en sensor ska fästas på ett chassi?

## Övningar

**Grund 1.** En grupp mäter kastlängderna 2,10, 2,25, 2,05 och 2,20 m. Beräkna medelvärde och spridning.

<details><summary>Svar</summary>

Medelvärde 2,15 m. Spridning 0,20 m.

</details>

**Grund 2.** En robot berör 52 av 64 rutor. Beräkna täckningen.

<details><summary>Svar</summary>

81,25 %

</details>

**Vidare 3.** Teorin gav 2,4 m och medelvärdet från övning 1 är 2,15 m. Beräkna den procentuella avvikelsen.

<details><summary>Svar</summary>

(2,15 − 2,4) / 2,4 = −10 %

</details>

**Vidare 4.** Bilen kör med farten 0,50 m/s och stopptiden är 0,50 s. Hur långt rullar den?

<details><summary>Svar</summary>

25 cm

</details>

**Utmaning 5.** Planera ett test för en konstruktion du bygger. Ange vad som ska mätas, hur många gånger, vilken variabel du ändrar och vilka resultat som skulle få dig att ändra konstruktionen.

## Koppling till projektet

Kapitlet används i [Bygg 2.0](../projekt/bygg-2-0/README.md), där budget, prototyp och redovisning står i fokus, och i [Robotmopp](../projekt/robotmopp/README.md), där chassits konstruktion, kalibrering och mätning av täckning är centrala. I [Sort My Brick](../projekt/sort-my-brick/README.md) tränar du experiment, test och dokumentation. Det gäller också [Katapult](../projekt/katapult/README.md) när ni testar kast och jämför med beräkningarna.

## Läs mer

- [Prototyp (Wikipedia, engelska)](https://en.wikipedia.org/wiki/Prototype)
- [Materiallista (Wikipedia, engelska)](https://en.wikipedia.org/wiki/Bill_of_materials)

[← Föregående](09-vridning-effekt.md) | [Innehåll](../README.md)
