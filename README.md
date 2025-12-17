
# Enkel Virtuell Maskin – Referanse & Brukermanual

Dette dokumentet beskriver et lite, pedagogisk assembler-lignende språk for en enkel virtuell maskin (VM). Språket er designet for å lære grunnleggende konsepter som minnehåndtering, aritmetikk, kontrollflyt og inn/ut-operasjoner.

---

## Innholdsfortegnelse

- Oversikt
- Arkitektur
- Instruksjonssett
  - Datahåndtering
  - Aritmetikk
  - Kontrollflyt
  - Inn / Ut
- Programmeringsregler
- Eksempler
  - Hello World
  - Nedtelling
  - Matematikksjekk
- Tips og begrensninger

---

## Oversikt

Programmer kjøres sekvensielt, én instruksjon per linje. Hver instruksjon kan ta **én parameter**, vanligvis en minneadresse eller en konstant verdi.

Språket bruker et **akkumulator-register (AKK)** som mellomlager for alle beregninger.

---

## Arkitektur

- **AKK (Akkumulator)**
  - Ett register
  - Verdier: `0–255`
  - Overflow/underflow “wrapper rundt” (modulo 256)

- **Minne**
  - 256 adresser (`0–255`)
  - Hver adresse lagrer én verdi (`0–255`)

- **Programflyt**
  - Linjenummer starter på `0`
  - Hver instruksjon opptar én linje

---

## Instruksjonssett

### Datahåndtering

| Instruksjon | Beskrivelse |
|-------------|------------|
| `SETT n`    | Sett AKK til verdien `n` |
| `HENT n`    | Hent verdi fra minneadresse `n` til AKK |
| `LAGRE n`   | Lagre verdien i AKK til minneadresse `n` |
| `NULLSTILL` | Sett AKK til `0` |

---

### Aritmetikk

Alle operasjoner bruker verdien i AKK og verdien i minneadresse `n`.

| Instruksjon | Beskrivelse |
|-------------|------------|
| `PLUSS n`   | AKK = AKK + minne[n] |
| `MINUS n`   | AKK = AKK − minne[n] |
| `GANG n`    | AKK = AKK × minne[n] |
| `DELE n`    | AKK = AKK ÷ minne[n] |

---

### Kontrollflyt

| Instruksjon | Beskrivelse |
|-------------|------------|
| `HOPP n`    | Hopp ubetinget til linje `n` |
| `ER_LIK n`  | Hopp til linje `n` hvis AKK == 0 |
| `ER_ULIK n` | Hopp til linje `n` hvis AKK != 0 |
| `ER_POS n`  | Hopp til linje `n` hvis AKK > 0 |
| `STOPP`     | Avslutt programmet |

---

### Inn / Ut

| Instruksjon | Beskrivelse |
|-------------|------------|
| `LES n`     | Les ett tegn og lagre det i minneadresse `n` |
| `SKRIV n`   | Skriv tegn fra minneadresse `n` |
| `VIS`       | Skriv den numeriske verdien i AKK |

---

## Programmeringsregler

- Kommentarer starter med `;` eller `#`
- Én instruksjon per linje
- Tomme linjer ignoreres
- Alle hopp refererer til **linjenummer**, ikke etiketter

---

## Eksempler

### Hello World (Hei)

```asm
; Skriv "Hei"
SETT 72      ; 'H'
LAGRE 0
SETT 101     ; 'e'
LAGRE 1
SETT 105     ; 'i'
LAGRE 2
SKRIV 0
SKRIV 1
SKRIV 2
STOPP
````

---

### Nedtelling

```asm
; Tell ned fra 5 til 1
SETT 5
LAGRE 0
SETT 1
LAGRE 1

HENT 0      ; Start løkke
VIS
MINUS 1
LAGRE 0
ER_POS 5    ; Hopp tilbake til løkkestart
STOPP
```

---

### Matematikksjekk

Sjekker om `5 × 3 = 15`.

```asm
SETT 5
LAGRE 0
SETT 3
LAGRE 1
SETT 15     ; Fasit
LAGRE 2

HENT 0      ; 5
GANG 1      ; 5 * 3
MINUS 2     ; Resultat - fasit

ER_LIK 12   ; Riktig
HOPP 15     ; Feil

SETT 1      ; Suksess
VIS
STOPP

NULLSTILL   ; Feil
VIS
STOPP
```

---

## Tips og Begrensninger

* Alle verdier er **8-bit** (0–255)
* Negative tall representeres via wrap-around
* Ingen etiketter – bruk linjenummer nøye
* Deling på 0 er **ikke definert**
* Perfekt for undervisning, emulatorer og eksperimenter

---

