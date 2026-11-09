# Kapitel 9: Vridning och överföring av effekt

> **I det här kapitlet lär du dig**
> - vad vridning är och hur spänningen fördelas i en axel
> - hur du räknar ut vridspänning med vridmotståndet
> - hur effekt, varvtal och vridmoment hänger ihop
> - hur du dimensionerar en axel som ska överföra effekt

Varje motor, från en borrmaskin till en bil, överför sin effekt genom en axel som vrids. Den axeln är ofta den detalj som håller minst, och den kan gå av utan att det syns några tecken på det innan. Här lär du dig räkna på vridning och koppla ihop effekten från en motor med spänningen i axeln.

## Vad händer när en axel vrids?

När ett vridmoment verkar på en axel förskjuts tvärsnitten i förhållande till varandra, som om du vred om en handduk. Det uppstår **skjuvspänningar** i axeln. Precis som vid böjning är spänningen noll i mitten och ökar ju längre ut du kommer. Därför är materialet i mitten ganska oviktigt för vridstyvheten, och ett rör kan vara nästan lika starkt som en massiv axel med mycket mindre vikt.

## Spänningslagen för vridning

```text
τv = Mv / Wv

τv   vridspänning (skjuvspänning) i N/mm²
Mv   vridmoment i Nmm
Wv   vridmotstånd i mm³
```

| Tvärsnitt | Vridmotstånd Wv |
|---|---|
| Massiv axel, diameter d | π · d³ / 16 |
| Rör, ytter D, inner d | π · (D⁴ − d⁴) / (16 · D) |

Jämför med böjmotståndet: för samma cirkulära tvärsnitt är Wv dubbelt så stort som Wb.

### Exempel: vridspänning i en massiv axel

En axel med diametern 25 mm belastas med vridmomentet 150 Nm.

```text
Mv = 150 Nm = 150 000 Nmm
Wv = π · 25³ / 16 = 3068 mm³
τv = 150 000 / 3068 = 48,9 N/mm²
```

### Exempel: rör jämfört med massiv axel

Vad händer om du borrar ett hål med diametern 15 mm genom samma axel?

```text
Wv = π · (25⁴ − 15⁴) / (16 · 25) = 2670 mm³
τv = 150 000 / 2670 = 56,2 N/mm²
```

Du har tagit bort 36 % av materialet men vridmotståndet har bara minskat med 13 %. Att göra en axel ihålig är ofta effektivt. Priset är att arbetet kostar mer, och att röret ska få plats.

## Dimensionering vid vridning

För metalliska material utgår vi från sträckgränsen och använder faktorn 0,6, på samma sätt som vid skjuvning:

```text
τtill = 0,6 · Re / nS
```

Är kravet på styvhet viktigare än hållfastheten, till exempel i en lång axel i en maskin, räcker det inte att räkna på spänning. Då måste även förvridningen vara liten.

## Överföring av effekt

Ofta vet du effekt och varvtal men inte vridmoment. **Effekt** är arbete per tidsenhet och mäts i watt. För en roterande axel gäller:

```text
P = Mv · ω         ω = 2 · π · n / 60

P   effekt i W
Mv  vridmoment i Nm
ω   vinkelhastighet i rad/s
n   varvtal i varv per minut (rpm)
```

Om effekten anges i kW och varvtalet i rpm finns en användbar genväg:

```text
Mv (Nm) ≈ 9550 · P (kW) / n (rpm)
```

### Exempel: från motordata till axeldiameter

En motor på 4,0 kW går med 1440 rpm. Axeln ska vara av ett stål med Re = 355 N/mm² och nS = 2,0.

```text
ω = 2 · π · 1440 / 60 = 150,8 rad/s
Mv = P / ω = 4000 / 150,8 = 26,5 Nm = 26 500 Nmm

τtill = 0,6 · 355 / 2,0 = 106,5 N/mm²
Wv krävs = 26 500 / 106,5 = 249 mm³
d = (16 · 249 / π)^(1/3) = 10,8 mm     → välj 12 mm
```

Kontroll: med d = 12 mm blir τv = 26 500 / 339 = 78,2 N/mm², och det ligger under τtill.

### Exempel: växel

En motor på 1,5 kW går med 1400 rpm. Via en växel med utväxlingen 4:1 minskar varvtalet till 350 rpm.

```text
Mv före växeln:  1500 / (2 · π · 1400 / 60) = 10,2 Nm
Mv efter växeln: 1500 / (2 · π · 350 / 60)  = 40,9 Nm  (om inga förluster finns)
Med verkningsgraden 90 %:    0,9 · 40,9 = 36,8 Nm
```

Effekten är densamma eller lite lägre, men momentet ökar när varvtalet minskar. Det är just därför axeln efter växeln oftast är grövre. En växel byter varvtal mot moment.

### Exempel: robotbilens drivaxel

En liten likströmsmotor antas ge 0,08 Nm vid 150 rpm och driver ett hjul med radien 32,5 mm. Värdena är antaganden för exemplet, så mät din egen bil eller läs databladet.

```text
ω = 2 · π · 150 / 60 = 15,7 rad/s
P = 0,08 · 15,7 = 1,3 W
F = Mv / r = 0,08 / 0,0325 = 2,5 N
v = ω · r = 15,7 · 0,0325 = 0,51 m/s
```

Detta ger en känsla för vad bilen klarar. Med dessa antaganden räcker det för att rulla den lätta bilen och dra en penna som släpar lätt, men en bil som trycker pennan hårt mot golvet tappar mycket fart.

## Begrepp

- **Vridmoment Mv:** moment som vrider en axel kring dess längdriktning.
- **Vridmotstånd Wv:** tvärsnittets förmåga att stå emot vridning.
- **Vridspänning τv:** den skjuvspänning som uppstår vid vridning.
- **Effekt P:** arbete per tidsenhet, mäts i watt.
- **Vinkelhastighet ω:** rotationshastighet i radianer per sekund.
- **Utväxling:** förhållandet mellan varvtal in och varvtal ut i en växel.

## Testa dig själv

1. Var i en axel är spänningen störst vid vridning?
2. Varför är ett rör ett effektivt sätt att överföra vridmoment?
3. Vad är sambandet mellan Wv och Wb för ett cirkulärt tvärsnitt?
4. Vad händer med vridmomentet om effekten är konstant men varvtalet halveras?
5. Vad ändrar en växel, och vad ändrar den inte?
6. Varför är det rimligt att räkna med 0,6 · Re för vridning?

## Övningar

**Grund 1.** Beräkna vridspänningen i en axel med diametern 30 mm vid vridmomentet 200 Nm.

<details><summary>Svar</summary>

Wv = 5301 mm³. τv = 37,7 N/mm².

</details>

**Grund 2.** En motor på 2,2 kW går med 960 rpm. Beräkna vridmomentet.

<details><summary>Svar</summary>

21,9 Nm

</details>

**Grund 3.** Vilken effekt överför en axel som går med 3000 rpm vid vridmomentet 50 Nm?

<details><summary>Svar</summary>

15,7 kW

</details>

**Vidare 4.** En axel med diametern 20 mm har Re = 420 N/mm². Hur stort vridmoment tål den med nS = 2,0?

<details><summary>Svar</summary>

τtill = 126 N/mm². Wv = 1571 mm³. Mv = 198 Nm.

</details>

**Vidare 5.** Dimensionera en axel för 7,5 kW vid 730 rpm. Re = 355 N/mm², nS = 2,5.

<details><summary>Svar</summary>

Mv = 98,1 Nm. τtill = 85,2 N/mm². Wv = 1152 mm³. d = 18,0 mm, välj till exempel 20 mm.

</details>

**Utmaning 6.** En massiv axel med diametern 30 mm ska bytas mot ett rör med ytterdiameter 40 mm och samma vridmotstånd. Vilken innerdiameter ska röret ha? Hur stor andel av materialet behövs jämfört med den massiva axeln?

<details><summary>Svar</summary>

Wv = 5301 mm³. d⁴ = 40⁴ − Wv · 16 · 40 / π, vilket ger d = 34,9 mm. Röret behöver ungefär 43 % av materialet.

</details>

Räkna också övningsuppgifterna om vridning och överföring av effekt i [kompendiet](../H%C3%A5llfasthetsl%C3%A4ra/02.%20H%C3%A5llfasthetsl%C3%A4ra%20kompendium.docx).

## Koppling till projektet

Kapitlet avslutar teorin i [Hållfasthetslära](../projekt/hallfasthetslara/README.md). Filmerna [Lektion 7: vridning](../H%C3%A5llfasthetsl%C3%A4ra/11.0%20H%C3%A5llf%20lektion%207%20Vridning.mp4), [Vridning samt uppgift](../H%C3%A5llfasthetsl%C3%A4ra/11.1%20Vridning%20samt%20uppg%2082.mp4) och [Överföring av effekt](../H%C3%A5llfasthetsl%C3%A4ra/12.%20%C3%96verf%C3%B6ring%20av%20effekt%20samt%20uppg%2068.mp4) går igenom beräkningarna. Lösningar finns i [Lösningar 67-87](../H%C3%A5llfasthetsl%C3%A4ra/L%C3%B6sningar%2067-87.pdf). Motorer och drivning kommer du i kontakt med igen i [Robotmopp](../projekt/robotmopp/README.md).

## Läs mer

- [Vridning (Wikipedia, engelska)](https://en.wikipedia.org/wiki/Torsion_(mechanics))
- [Moment (Wikipedia, engelska)](https://en.wikipedia.org/wiki/Torque)

[← Föregående](08-bojning.md) | [Innehåll](../README.md) | [Nästa →](10-prototyp-komponenter-dokumentation.md)
