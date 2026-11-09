# Kapitel 2: Moment, energi och kastbana

> **I det här kapitlet lär du dig**
> - hur kraft och avstånd tillsammans ger ett moment
> - hur en hävstång byter kraft mot rörelse
> - hur du räknar ut energin som lagras i en motvikt eller en fjäder
> - hur du uppskattar en kastlängd och bedömer om svaret är rimligt

Den som knuffar på en dörr nära gångjärnet märker att det tar emot. Knuffar du i handtaget går det lätt, trots att du trycker lika hårt. Det beror på moment. I en katapult bestämmer momentet hur armen rör sig, energin avgör hur mycket som kan överföras till kulan, och kastbanan visar var kulan landar. Med några enkla samband kan du förutsäga resultatet innan du har byggt något.

## Kraft och moment

**Kraft** mäts i newton (N). Tyngdkraften på en massa m är

```text
F = m · g        g = 9,82 m/s²  (tyngdaccelerationen i Sverige)
```

En kraft som verkar på ett avstånd från en vridpunkt ger ett **moment**:

```text
M = F · a        M i Nm, F i N, a i meter
```

Avståndet a, **momentarmen**, mäts vinkelrätt från vridpunkten till kraftens riktning.

### Exempel: moment på en arm

En kraft på 25 N drar i en arm 0,30 m från axeln.

```text
M = F · a = 25 · 0,30 = 7,5 Nm
```

## Hävstång

En **hävstång** är en stång som kan vrida sig runt en punkt. Momenten på varje sida om vridpunkten måste balansera varandra när armen står still:

```text
F1 · a1 = F2 · a2
```

### Exempel: hävarm på en katapult

Armen har korta sidan 0,10 m och långa sidan 0,40 m. En kraft på 60 N verkar på korta sidan.

```text
M = 60 · 0,10 = 6,0 Nm
F2 = M / a2 = 6,0 / 0,40 = 15 N
```

Du får ut en mindre kraft på långa sidan, men den änden rör sig fyra gånger så långt och därmed fyra gånger så fort. Det är hela poängen med en kastarm: du byter kraft mot fart. Förhållandet 0,40 / 0,10 = 4 kallas **hävarmsförhållande**.

Armen, axeln och ramen ska sedan klara de krafter som uppstår. Det räknar du på i kapitlen om böjning och skjuvning.

## Lagrad energi

**Energi** mäts i joule (J). Katapulten lagrar energi innan du släpper. Två vanliga sätt:

```text
Motvikt:         E = m · g · h          h = sträckan vikten sjunker
Fjäder/gummi:    E = 0,5 · k · x²       k = fjäderkonstant (N/m), x = töjning (m)
```

### Exempel: lagrad energi

En motvikt på 3,0 kg sjunker 0,15 m.

```text
E = 3,0 · 9,82 · 0,15 = 4,4 J
```

Ett fjädersystem med k = 800 N/m som dras ut 0,10 m:

```text
E = 0,5 · 800 · 0,10² = 4,0 J
```

Allt detta når aldrig fram till kulan. En stor del går åt till att sätta själva armen i rörelse, till friktion i axeln och till vibrationer. Andelen som faktiskt når kulan kallas **verkningsgrad**. Hur stor den är får du fram genom att mäta. I exemplen nedan antar vi 25 %, och det antagandet måste du kontrollera mot din egen katapult.

## Kastbana

När kulan lämnar armen har den en fart v. Rörelseenergin är

```text
Ek = 0,5 · m · v²     →     v = √(2 · Ek / m)
```

Om kulan släpps från markhöjd och luftmotståndet försummas blir kastlängden

```text
R = v² · sin(2θ) / g
```

Formeln ger störst längd vid vinkeln θ = 45°, eftersom sin(90°) = 1.

### Exempel: från energi till kastlängd

Motvikten ovan lagrar 4,42 J. Med verkningsgraden 25 % får en kula på 30 g energin 1,10 J.

```text
v = √(2 · 1,10 / 0,030) = 8,6 m/s
R = 8,6² · sin(90°) / 9,82 = 7,5 m     (från markhöjd, 45°)
```

Släpps kulan från 0,40 m höjd landar den något längre bort. Med en mer fullständig formel, som tar hänsyn till släpphöjden, får du:

| Vinkel | Kastlängd (m) |
|---|---|
| 30° | 7,1 |
| 40° | 7,8 |
| 45° | 7,9 |
| 50° | 7,7 |
| 60° | 6,7 |

Vid 0,40 m släpphöjd ligger den bästa vinkeln strax under 45° (runt 43–44°). Skillnaden är dock liten, och i praktiken styrs resultatet mer av hur jämnt armen släpper än av en enstaka grad.

## Rimlighetsbedömning

Fråga dig alltid om svaret verkar rimligt. Modellen ovan bortser från luftmotstånd och antar en verkningsgrad, och därför ska den bara ses som en uppskattning. Om kalkylen säger 7 m och katapulten kastar 1 m, då måste något stämma dåligt: kanske stor friktion, en för tung arm eller en ojämn släpp. Skillnaden mellan modell och mätning är ofta det mest lärorika i hela projektet. Mätmetoder tar vi upp i kapitel 10.

## Begrepp

- **Moment:** kraft multiplicerad med vinkelrätt avstånd till en vridpunkt.
- **Momentarm:** det vinkelräta avståndet från vridpunkten till kraftens verkningslinje.
- **Hävstång:** en stång som kan vrida sig runt en punkt och byter kraft mot rörelse.
- **Hävarmsförhållande:** kvoten mellan långa och korta armens längd.
- **Lägesenergi:** energi hos en höjd massa, E = m · g · h.
- **Rörelseenergi:** energi hos en massa i rörelse, Ek = 0,5 · m · v².
- **Verkningsgrad:** den andel av tillförd energi som blir nyttig energi.

## Koppling till projektet

I [Katapult](../projekt/katapult/README.md) räknar du på hävarmsförhållande, lagrad energi och kastbana innan du bestämmer huvudmåtten. När ni testat katapulten jämför ni resultaten med era beräkningar.

## Läs mer

- [Hävstång (Wikipedia, engelska)](https://en.wikipedia.org/wiki/Lever)
- [Moment (Wikipedia, engelska)](https://en.wikipedia.org/wiki/Torque)
- [Kastparabel och kastbana (Wikipedia, engelska)](https://en.wikipedia.org/wiki/Projectile_motion)

[← Föregående](01-konstruktionsprocessen.md) | [Innehåll](../README.md) | [Nästa →](03-cad-i-onshape.md)
