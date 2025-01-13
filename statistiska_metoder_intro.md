#### statistiska metoder

# huvudsakligt innehåll
vanliga fördelningar
korrelation
kovarians
väntevärde
estimering och skattning
sannolikhetslära
hypotestning
regressionsanalys

numpy, scipy


# kunskaper
grundläggande statistik och kvantitativa statistiska mått
sannolikhetslära, beroende och oberoende händelser
vanliga fördelningar och dess egenskaper samt användingsområden
estimering och skattning
paketet numpy och vanliga funktioner

# färdigheter
beräkna informativa statistiska mått så som kovarians, korellation och väntevärde
tolka sannolikheter, diagram och statistik
utföra interpolation och extrapolation samt regressionsanalys
utföra hypotestning och beräkna konfidensintervall


# kompetenser
självständigt samla in data, utföra statistiska beräkningar och identifiera felkällor
kunna kritiskt granska statistik och resultat samt dra egna slutsatser och tolkningar

svara på statiska frågeställningar genom nyttjande av beräkningsverktyget numpy


# läromedel
introduction to probability and statistics - milton & arnold
grundläggande statistisk analys - björn lantz

an introduction to statistical learning - statlearning.com kap 1-3







sannolikhet och uppräkning

slump:
    klassiskt: osäkerhet
    hypermodernt: slump=tid, "slump är att storheter antar sina värden" = händelser. heisenbergs osäkerhet


# osäkerhet
tärning
    innan vi slår tärningen  {1,2,3,4,5,6} utfallsrum(eng. sample space): alla sätt som ett experiment eller observation kan fortgå(alla möjliga utfall)

efter vi kastat tärningen: {1},{5},,,-> osv  dvs ett värde, ett utfall


# två sätt att definiera sannolikhet
relativ frekvens - antalet gånger något visst händer / delat på totala antalet händelser 
    P[A]=F/N "Probability att A inträffar.. = F/N"
    P[A=3]=3/10   {1,3,3,3,4,5,7,8,9,10} (   ett stickprov - (eng. i statistik, sample), ML = batch, utfall = sample    )

andra sättet: 
    klassisk sannolikhet:
        P[A]=n(A)/n(S)= antalet sätt a kan inträffa / totala antalet möjliga utfall
        p[A=3]=1/6

# sannolikhet: (eng. probability)
    "det är 20% chans/risk för regn idag"
    P=0.2, dvs sannolikhet är ett reellt tal mellan 0-1(inklusive).  [0,1] som intervall
    0 = händer aldrig
    1 = händer alltid
    0.5 lika sannolikhet för vardera utfall


# händelser: (eng. event)
    en händelse är en delmängd till utfallsrummet
    "slå en 3:a" : {3}
    "femte slaget av 6 en 1:a" {a1,a2,a3,a4,a5=1,a6}


# permutation
    en ordnad mängd, dvs ordning har betydelse
    tex. {1,2,3} P-> {3,1,2}
        nPr = n!/(n-r)!  "antalet permutation av n distinkta objekt ordnade r st åt gången"  kombinatorisk explosion
        "välj r av n med hänsyn till ordning"


        factorial = !
            3! = 3*2*1
            5! = 5*4*3*3*2*1


    permutationer av liknande objekt:
        n!/n1!,n2!,n3!,,,,nk!
        n=n1+n2+n3+,,,+nk

# kombination
    en oordnad mängd, dvs utan ordning
        nCr = n!/r!(n-r)!   ett vanligare sätt att skriva är (n/r)=binomial-koeffecient
        "antalet kombinationer av n distinkta objekt, r st åt gången utan hänsyn till ordning"
        "välj r utan hänsyn till ordning"




# apolloprogrammet 
månraketerna hade 3 st datorer.
    s = samplespace
    s = {yyy,yyn,yny,ynn,nyy,nyn,nny,nnn}  (utfallsrum)
        primära systemet. har två fall
        sekundära
    Ø = tomma utfallsrummet, dvs händer aldrig

låt a b och c vara händelser:
a: primära systemet är igång
b: den första backupen är igång
c: den andra backupen är igång

    A: {yyy,yyn,yny,ynn}
    b: {yyy,yyn,nyy,nyn}
    c: {yyy,yny,nyy,nny}


    U = union-symbol (‹)
"primära systemet eller första backupen är igång"
    AUB = {yyy,yyn,yny,ynnn,nyyy,nyn} "detta kan man se som ett ett venn-diagram, där hela är unionen"
    
    A"snitt"B(båge)
"primära systemet och första backupen är igång"
    a()B = {yyy, yyn}

"primära eller första backup igång men andra backupen är inte igång"
    (AUB)()C´ = {yyn,ynn,nyn}

    P[(AUB)‹C´] = 3/8 (om samma sannolikhet för att varje dator fungerar eller inte)

ömsesidigt uteslutande händelser (mututally exclusive events)
    A‹b = Ø 
    P[AUB] = 0
    har inget snitt, inga punkter gemensamt
    
    inga gemensamma element:
    A1: {yyy,yyn,yny,ynn} 
    A2:{nyy,nyn,nny,nnn}


P[A]=n(A)/n(S)



permutation
"pentapeptid" 
    alanine - valine - glycine - cystein - tryptophan
    alanine - glycine - valine - cystein - tryptophan

20 st objekt, dvs n=20
välj 5, hur många permutationer av 20 st objekt, välj ut 5 av dem
    nPr=n!/(n-r)!

    20!/15! = 20*19*18*17*16 
    1,86…m


kombination
motorer tillverkas i serier om 20 var
    3st väljs ut slumpmässigt och testas
    (20/3) = n!/r!(n-r!) = 20!/3!(15!)= 20*19*18*17*16/3*2 = 20*19*18*8/3
    nCr = (n/1)
    0! = 1


varför heter dem binomial koeffiecenter
    (a+b)^n
    https://mathsathome.com/wp-content/uploads/2021/10/the-binomial-theorem-formula-1024x577.png
    pascals triangel



nästa gång

# räkneregler för sannolikheter
s => "Sample Space" = utfallsrum
| = "har inträffat"
p[S]=1
P[A] > 0 för alla A
p[ø] = 0

P[A1unionA2] = P[A1] + P[A2] - P[A1unionA2]


om
    A1 = primära motorn fungerar
    A2 = sekundära motorn fungerar
    p[A1]






låt a1,a2,... vara ömsesidigt uteslutande händelser (dem kan inte ske samtidigt)
p[a1Ua2U...] = p[a1]+p[a2]+...


#### oberoende händelser
a1 och a2 är oberoende om och endast om
p[a1()a2]= p[a1]p[a2]
#### beroende händelser
p[a2|a1]= p[a1()a2]/p[a1] "sannolikhet för snittet delat på händelsen som hänt"

p[a2|a1]= p[a2] (p[a1]=/=0)
p[a1|a2]= p[a1] (p[a2]=/=0)

#### multiplikationsregeln
p[a1snitta2]= p[a2|a1]p[a1]

#### bayes theorem
låt A1,A2,A3,...,An vara en samlig ömsesidigt uteslutande händelser vars union är S.
låt B vara en händelse, p[B]=/=0, b är nollskild
då gäller för varje händelse Aj, j=1,2,3,...,n
p[aj|b] = p[B|Aj] p[Aj] / nsummai=1 p[B|Ai]p[Ai]


#### example
a chemist analyses water near a factory
past experience shows that 38% of samples contain toxic levels of lead or mercury
in addition 32% contain toxic levels of lead
and 16% contain toxic levels of mercury
Q: what is the probability that a random sample contains toxic levels of lead only?

A1: sample contains toxic levels of lead
A2: sample contains toxic levels of mercury
given: 

$ p[A1] = .32 $
$ p[A2] = .16 $
$ p[A1\cup A2] = .38 $

$ p[a1\cup a2]= p[a1]+p[a2]-p[a1()a2] $
$ .38 = .32+.16 - p[a1()a2] $
$ p[a1\cap a2] = 0.1 $
$ p[a1\cap a2'] $









#### gender identification

a1 = protein present
a2 = child is male

$ p[a1]=.43 $
$ p[a2]=.51 $
$ p[a1\cap a2]=.17 $

$ p[a2|a1] $ <- vi söker
$ .17/.43 = .395 $ 
$ p[a2|a1] = p[a1\cap a2]/p[a1] $ 




#### exempel med kort

a1: spader dras
a2: honorcard (10,J,Q,K,A)


$ p[a1] = 13/52 $
$p[a2] = 20/52 $
$ p[a1\cap a2] = 5/52 $

är a1 och a2 oberoende?
    
$ p[A1]p[A2] = (13/52)(20/52) = 5/52 $
    

#### exempel backupsystem apolloraketen
a1: main operable
a2: first backup operable
a3: second backup operable

$ p[a1] = p[a2] = p[a3] = .9 $
vi söker (oberoende)

$$ p[a1\cap a2\cap a3] = p[a1]p[a2]p[a3] = (.9)^3 = .729 $$

#### exempel fortkörning (bayes theorem)
E: fortkörning (någon förare körde för fort)
A: rattfylla (någon förare var full)

$P[E] = .4$
$P[A] = .3$


$ P[E|A] = .6 $
$ P[E|A'] = .1 $

$ P[E'] = 1-.4=.6 $
$ P[A'] = 1-.3=.7 $

$P[A|E] = \frac{p[E\cap A]}{P[E]} $
$ P[A|E]P[E] = p[E \cap A] $

$ E = [E\cap A]\cup [E\cap A] $

$ P[E] =P[E\cap A] + P[E\cap A'] $

$ P[E\cap A'] = P[E|A']P[A'] $

$$ P[A|E] = $$
$$ \frac{p[E\cap A]}{p[E]} = $$
$$ \frac{P[E|A]P[A]}{P[E|A]P[A]+P[E|A']P[A] } = $$
$$ \frac{.6* .3}{(.6)(.3)+(.1)*(.7)} $$


#### exempel blodtyper i USA
Typ A: 41% 
Typ B: 9%
Typ AB: 4%
Typ O: 46%

Typ O men klassad som A: 4%
typ A och korrekt: 88%
typ B klassad om A: 4%
typ AB klassad som A: 10%

antag en individ klassad som typ A.
vad är sannolikheten att individen verkligen har typ A?

**A1: Blodtypen är A**
**A2: Blodtypen är B**
**A3: Blodtypen är AB**
**A4: Blodtypen är O**
**B: Klassad som typ A**


P[A1] = .41
p[A2] = .09
p[A3] = .04
p[A4] = .46


P[B|A1] = .88
P[B|A2] = .04
P[B|A3] = .10
P[B|A4] = .04

vi söker P[A1|B]


$ P[A1|B] = $
$ \frac{p[B|A1] * P[A1]}{P[B|A1]P[A1]+P[B|A2]P[A2]p[B|A3]P[A3]+P[B|A4]P[A4]} $
=
$$ \frac{(.88)(.44)}{(.88)(.44)+(.04)(.09)+(.10)(.04)+(.04)(.46)} = .93 $$