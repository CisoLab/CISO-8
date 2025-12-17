REFERANSE
DATAHÅNDTERING
SETT n - Sett AKK til verdi n
HENT n - Hent verdi fra adresse n til AKK
LAGRE n - Lagre AKK til adresse n
ARITMETIKK
PLUSS n - Legg minne[n] til AKK
MINUS n - Trekk minne[n] fra AKK
GANG n - Gang AKK med minne[n]
DELE n - Del AKK på minne[n]
NULLSTILL - Sett AKK til 0
KONTROLLFLYT
HOPP n - Hopp til linje n
ER_LIK n - Hopp til linje n hvis AKK == 0
ER_ULIK n - Hopp til linje n hvis AKK != 0
ER_POS n - Hopp til linje n hvis AKK > 0
STOPP - Avslutt program
INN/UT
LES n - Les tegn til adresse n
SKRIV n - Skriv tegn fra adresse n
VIS - Skriv numerisk verdi i AKK
EKSEMPLER
Hello World:
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
Nedtelling:
; Tell ned fra 5
SETT 5
LAGRE 0
SETT 1
LAGRE 1
HENT 0      ; Start løkke
VIS
MINUS 1
LAGRE 0
ER_POS 5    ; Hopp tilbake
STOPP
Matematikksjekk:
; Sjekk om 5 * 3 = 15
SETT 5
LAGRE 0
SETT 3
LAGRE 1
SETT 15     ; Fasit
LAGRE 2
HENT 0      ; Hent 5
GANG 1      ; 5 * 3 = 15
MINUS 2     ; 15 - 15 = 0?
ER_LIK 12   ; Hvis 0: Riktig!
HOPP 15     ; Ellers: Feil
SETT 1      ; Last 1 (Suksess)
VIS
STOPP
NULLSTILL   ; Last 0 (Feil)
VIS
STOPP
TIPS
AKK register: 0-255 (wrapper rundt)
Minneadresser: 0-255
Linjenummer starter på 0
Kommentarer starter med ; eller #
