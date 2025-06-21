# MA2

Status: Done

# Requirements

Funkce více proměnných. Mocninné řady. Dvojný a trojný integrál. B0B01MA2 (Webové
stránky předmětu)

• Derivace ve směru, parciálnı́ derivace a diferenciál funkce. Gradient a jeho geometrický
význam (směr největšı́ho spádu a kolmost na hladiny konstantnosti).

• Lokálnı́a globálnı́extrémy funkce. Aplikace diferenciálnı́ho počtu na hledánı́extrémů. Vázané
extrémy a metoda Lagrangeových multiplikátorů.

• Mocninná řada. Poloměr konvergence mocninné řady. Derivovánı́ a integrovánı́ mocninné
řady člen po členu. Geometrická řada a jejı́ součet. Rozvoj exponenciálnı́ funkce do mocninné řady.

• Polárnı́, válcové a sférické souřadnice. Jejich využitı́ na výpočet integrálů

# Mnoziny v $\mathbb{R}^n$

## Posloupnost bodu

![image.png](assets/image.png)

![image.png](assets/image%201.png)

Konvergentni = existuje limitni bod, divergentni otherwise

Konverguje prave tehdy, konverguje-li po slozkach

![image.png](assets/image%202.png)

![image.png](assets/image%203.png)

## Okoli bodu

![image.png](assets/image%204.png)

Koule o prumeru $\epsilon$ v n dimenzich

Prstencove = chybi stred

## Casti mnozin

![image.png](assets/image%205.png)

Vnitrek = otevrena mnozina, kazdy bod ma okoli ktere se cele vejde do M

Vnejsek = kazdy bod ma okoli ktere nezasahuje do M

Hranice = kazde okoli kazdeho bodu zasahuje to vnitrku a vnejsku zaroven

![image.png](assets/image%206.png)

![image.png](assets/image%207.png)

![image.png](assets/image%208.png)

# Funkce vice promennych

## Definice

![image.png](assets/image%209.png)

![image.png](assets/image%2010.png)

## Limita

![image.png](assets/image%2011.png)

Pro kazde epsilon existuje delta takove, ze pokud x patri do prstencoveho delta okoli bodu a, pak f(x) spadne do epsilon okoli bodu L

![image.png](assets/image%2012.png)

Ostatni vlastnosti plati stejne jako v MA1

## Spojitost

![image.png](assets/image%2013.png)

![image.png](assets/image%2014.png)

![image.png](assets/image%2015.png)

![image.png](assets/image%2016.png)

Ukazujeme rozepsanim spojitosti obou funkci samostatne a vyuzitim spojitosti po slozkach

# Smerove a parcialni derivace

## Smerova derivace

![image.png](assets/image%2017.png)

Myslenka: v definicnim oboru vybereme smer, podle ktereho se budeme posouvat a vysetrovat rust funkce jedne promenne → dostavame smerovou derivaci.

Bod musi byt vnitrni nebo nalezet do otevrene mnoziny, abychom meli okoli!

![image.png](assets/image%2018.png)

### Aritmetika smerove derivace

![image.png](assets/image%2019.png)

### Smerove derivaci vyssich radu

![image.png](assets/image%2020.png)

### Homogenita ve smeru

![image.png](assets/image%2021.png)

Ukazeme cachrovanim s limitou

## Parcialni derivace

![image.png](assets/image%2022.png)

Jednoduse: ve smeru kanonicke baze prostoru. Prakticky pocitame jako derivace pouze v te jedne promenne

![image.png](assets/image%2023.png)

### Parcialni derivace vyssich radu

![image.png](assets/image%2024.png)

Specialne pro derivace druheho radu plati Schwarzova veta

![image.png](assets/image%2025.png)

## Diferencial

![image.png](assets/image%2026.png)

Linearni zobrazeni dobre aproximujici puvodni funkci na okoli bodu a

Existuje = funkce je diferencovatelna

![image.png](assets/image%2027.png)

![image.png](assets/image%2028.png)

Ukazuj z limity a protlac linearitu pres diferencial

### Diferencial spojite funkce

![image.png](assets/image%2029.png)

## Gradient a geometrie

![image.png](assets/image%2030.png)

Plyne z vlastnosti dot productu.

![image.png](assets/image%2031.png)

Tayloruv polynom prvniho radu.

## Derivace a gradient slozeneho zobrazeni

![image.png](assets/image%2032.png)

## Hessova matice

![image.png](assets/image%2033.png)

Matice druhych derivaci

Je to realna symetricka matice, dle definitnosti ziskavame chovani funkce v tomto bode viz extremy.

## Tayloruv polynom

![image.png](assets/image%2034.png)

# Extremy funkci vice promennych

![image.png](assets/image%2035.png)

## Extremy na mnozine

![image.png](assets/image%2036.png)

![image.png](assets/image%2037.png)

bod lokalniho extremu ⇒ stacionarni bod funkce (gradient 0)

![image.png](assets/image%2038.png)

Jak urcit definitnost? Pokud jsou hlavni minory matice kladne, je PD, pokud se stridaji znamenka a prvni je zaporne, je ND. Jinak je indefinitni. Take zname jako sylvestrovo kriterium

## Lagrangeovy multiplikatory

![image.png](assets/image%2039.png)

![image.png](assets/image%2040.png)

Pokud gradienty nejsou nezavisle, nedokazeme vyresit. Znamena to, ze bod neni pro vazebni podminky regularni. Pokud tyto body umime najit, musime je vysetrit manualne (vyhodnotit v nich funkci).

# Posloupnosti funkci a rady

## Posloupnosti funkci

### Kovergence

![image.png](assets/image%2041.png)

![image.png](assets/image%2042.png)

Pro kazde x z M konverguje posloupnost funkci k nejake funkci v nekonecnu. Nejsou svazane konvergence jednotlivych hodnot.

Bodova konvergence zachovava:

- soucty, rozdil, nasobeni, mocneni
- lichost, periodicita, neklesajici, nerostouci, konstantni

Ale nezachovava:

- prostotu, diferencovatelnou spojitost
- integraly

Prikad:

![image.png](assets/image%2043.png)

![image.png](assets/image%2044.png)

### Uniformni konvergence

![image.png](assets/image%2045.png)

Alternativne $\forall \epsilon > 0 \exists N: \forall k>N: \forall x \in M: \left| f_k(x)-f(x)\right| < \epsilon$, tedy pro libovolnou presnost epsilon naleznu k, od ktereho vsechny cleny posloupnosti maji odchylku nejvice epsilon, tedy naleznu bod, od ktereho vsechny funkce konverguji stejne rychle. 

![image.png](assets/image%2046.png)

Priklad 

![image.png](assets/image%2047.png)

Pro epsilon napr. 0.5 najdeme x, kde to bude vzdy horsi ($x \to 1)$.

### Uniformni konvergence a spojitost

![image.png](assets/image%2048.png)

### Zamena integralu

![image.png](assets/image%2049.png)

## Rady funkci

![image.png](assets/image%2050.png)

Rada = nekonecny soucet funkci 

![image.png](assets/image%2051.png)

![image.png](assets/image%2052.png)

### Derivace a integral

![image.png](assets/image%2053.png)

Integral: funkce jsou stejnomerne konvergentni → soucet zachovava → pravidlo o vnoreni integralu do castecnych souctu, kazdy castecny soucet je konecny soucet prvku posloupnosti funkci

### Kriterium konvergence

![image.png](assets/image%2054.png)

~~Postup~~

1. ~~Vypocteme limitu bodove konvergence (zkusim jestli vubec ma sanci)~~
2. ~~pomoci nejakeho kriteria evaluujeme interval absolutni konvergence~~
3. ~~Odhadnu ze shora posloupnosti hodnot podle Weiserstrassova kriteria~~

## Mocninne rady

![image.png](assets/image%2055.png)

Konverguje ve stredu $x_o$ se souctem $a_0$

### Polomer konvergence

![image.png](assets/image%2056.png)

Polomer konvergence: nejvetsi abs. rozdil stredu a x, pro ktery rada stale konverguje, tj. jeji soucet je konecny

### Kriteria

![image.png](assets/image%2057.png)

Postup

1. Nemusim resit bodovou konvergenci (pro mocninnou R vzdy existuje) (faktorial - podil, exponent s k - odmocnina)
2. Evaluuju kriterium (abs)
3. Urcim interval x kde kriterium < 1

### Uniformni konvergence

![image.png](assets/image%2058.png)

### Derivace

![image.png](assets/image%2059.png)

Lze vnorit derivaci do uniformne konvergentni rady → dle predchozi vety mame uniformni konvergenci uvnitr delta-intervalu → muzeme na nem derivovat

### Integrace

![image.png](assets/image%2060.png)

![image.png](assets/image%2061.png)

Stejne vnoreni integralu to uniformne konvergentni rady

### Rozvoj funkce

![image.png](assets/image%2062.png)

Proste nekonecny taylor

Chceme rozvinout funkci v bode, a najit interval, ve kterem skutecne konverguje k puvodni funkci.

![image.png](assets/image%2063.png)

![image.png](assets/image%2064.png)

Rozvoj exponencialy:

1. Ukazeme existenci: kazda derivace je rovna $e^x \leq e^{x_0+r}$ na vysetrovanem intervalu, tedy je omezena, tim padem rozvoj existuje a konverguje pro vsechna x
2. Vyplati se funkci rozvinout v $x=0$, tim prijdeme o cleny navic a exponencialu
3. Muzeme substituovat za x $-x^2$ a vyresit tim gausse

# Integralni pocet

## Myslenka

Tvorime horni a dolni integralni soucty na obdelniku/n-dimenzionalni krabici → definicnim oboru integrovane funkce.

Horni a dolni integralni soucin nam udava objemy kvadru vytycenych minimem a maximem funkce na danem subobdelniku. Postup zjemnovanim deleni dostaneme rovnost infima a suprema stejne jako v MA1/

## Fubiniho veta

![image.png](assets/image%2065.png)

Dvojny integral na obdelniku lze pocitat jako 2 1D integraly. Muzeme reparametrizovat integraly vzajemne

![image.png](assets/image%2066.png)

![image.png](assets/image%2067.png)

## Veta o substituci

![image.png](assets/image%2068.png)

Tedy pri substituci prenasobujeme substituovanou funkci determinantem jakobianu v abs hodnote, ten popisuje absolutni bodovou zmenu objemu zobrazeni phi, pro velmi male objemy je to linearni → jakobian good enough.

### Polarni souradnice

![image.png](assets/image%2069.png)

Idealni kdyz mame nejaky kvadraticky utvar ve 2d - kruh, valec (vysku resime samostatne)

![image.png](assets/image%2070.png)

Mezikruzi

### Valcove souradnice

![image.png](assets/image%2071.png)

Polarni + plus vyska, nezmeni nam jakobian

### Sfericke souradnice

![image.png](assets/image%2072.png)

Sfericka telesa

## Krivkovy integral

### Oblouk

![image.png](assets/image%2073.png)

![image.png](assets/image%2074.png)

![image.png](assets/image%2075.png)

### Krivka

![image.png](assets/image%2076.png)

![image.png](assets/image%2077.png)

![image.png](assets/image%2078.png)

![image.png](assets/image%2079.png)

Pouze dve orientace, kladna a zaporna.

Pokud ji obchazime proti smeru hodinovych rucicek (ve smeru kladne rotace v $\mathbb{R}^n$), je kladne orientovana, jinak zaporne.

### Krivkovy integral 1. druhu

![image.png](assets/image%2080.png)

Nezavisi na parametrizaci. Pro delku integruju 1 (jenom velikost derivace).

![image.png](assets/image%2081.png)

### Krivkovy integral 2. druhu

![image.png](assets/image%2082.png)

Zalezi na smeru, kterym prochazime krivku (menime znamenko).

### Oblast

![image.png](assets/image%2083.png)

Take zvana souvislou mnozinou

### Greenova veta

![image.png](assets/image%2084.png)

Napr. integral vektoroveho pole na kruhu staci udelat integraci na kruznici okolo.

### Potencial

![image.png](assets/image%2085.png)

Pouze primitivni funkce spojiteho diferencovatelneho pole → potencial je skalarni funkce. Lze najit resenim soustavy PDE.

![image.png](assets/image%2086.png)

![image.png](assets/image%2087.png)

![image.png](assets/image%2088.png)

Na souvisle mnozine je potencialni pole konzervativni, a pro konvervativni pole nezavisi integral na krivce.

## Plosny integral

### Plocha

![image.png](assets/image%2089.png)

![image.png](assets/image%2090.png)

### Plosny integral 1. druhu

![image.png](assets/image%2091.png)

![image.png](assets/image%2092.png)

### Orientovana plocha

![image.png](assets/image%2093.png)

Pomoci normalovych vektoru co koukaji ven nebo dovnitr

Standardni plocha je definovana stejne jako neorientovana, pouze pribyvaji castecne orientace podploch

### Plosny integral 2.druhu

![image.png](assets/image%2094.png)

![image.png](assets/image%2095.png)

Normala = smer lokalne kolmy na gradienty zobrazeni

### Gaussova veta

![image.png](assets/image%2096.png)

Integral vektoroveho pole na plose je roven integralu jeho divergence v objemu ohranicenem plochou.

### Stokesova veta

![image.png](assets/image%2097.png)

### Pomucky

![image.png](assets/image%2098.png)