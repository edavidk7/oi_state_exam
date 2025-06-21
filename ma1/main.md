# MA1

Status: Done

# Requirements

Funkce jedné proměnné. Určitý a neurčitý integrál, řady

- Maximum, minimum, supremum a infimum množiny reálných čı́sel, jejich existence.

• Pojem funkce, inverznı́ funkce a jejı́ existence. Monotonie a (lokálnı́) extrémy funkcı́ a jejich
vyšetřovánı́ pomocı́ derivace. Vlastnosti (monotonie, limity) základnı́ch funkcı́ (mocniny,
exponenciálnı́, sinus, kosinus, tangens a k nim inverznı́).

• Limita funkce, jejı́jednoznačnost, způsoby výpočtu (součet, rozdı́l, součin, podı́l, l’Hospitalovo
pravidlo).

• Spojitost funkce, spojitost součtu, rozdı́lu, součinu, podı́lu, složené funkce. Vlastnosti spojity-
́ch funkcı́ na intervalu: nabývánı́ mezihodnot, existence primitivnı́ funkce, nabývánı́ maxima
a minima na uzavřeném intervalu, existence určitého integrálu.

• Derivace funkce, jejı́ geometrický význam. Výpočet derivace pro součet, rozdı́l, součin a podı́l
funkcı́, složenou funkci. Souvislost derivace se spojitostı́.

• Neurčitý a určitý integrál, vztahy mezi nimi (Newtonova–Leibnizova formule, primitivnı́ funkce
jako určitý integrál s proměnnou hornı́ mezı́). Linearita, integrace per partes, substituce.
Integrace mocnin, exp, sin, cos.

• Definice čı́selné řady, jejı́ součet. Konvergence, absolutnı́ konvergence a jejich souvislost.
Nutná podmı́nka konvergence. Kritéria konvergence (podı́lové, odmocninové, integrálnı́,
Leibnizovo)

# Realna cisla

## Racionalni cisla

![image.png](assets/image.png)

Racionalni cisla: spocetna mnozina vsech zlomku

## Rozsirena mnozina realnych cisel

Zavadime nevlastni cisla +-nekonecno, takove, ze omezuji realna cisla shora resp. zdola.

![image.png](assets/image%201.png)

## Extremalni prvky mnoziny

![image.png](assets/image%202.png)

![image.png](assets/image%203.png)

Sup/inf nemusi byt prvkem mnoziny, ale museji byt z rozsirenych realnych cisel

$(\sqrt 2, \infty)$ ma infimum $\sqrt2$, ale minimum neexistuje

![image.png](assets/image%204.png)

![image.png](assets/image%205.png)

Dodatecne, kazda konecna neprazdna podmnozina $\mathbb{R}$ ma maximum i minimum, lze seradit

# Funkce

![image.png](assets/image%206.png)

Zobrazeni definovane pro podmnoziny realnych cisel

## Zakladni vlastnosti

![image.png](assets/image%207.png)

### Inverzni funkce

![image.png](assets/image%208.png)

Nesmi se na “ztracet informace” a musime mit moznost nalezt vzor libovolneho realneho cisla

### Rust funkci

![image.png](assets/image%209.png)

Definice je vzdy pro rostouci x,y libovolna z def. oboru

![image.png](assets/image%2010.png)

Dokazujeme pres 1) prave jeden vzor sporem, kdyby jich existovalo vic porusili bychom podminku (podivat nad i pod vybrane x) 2) bereme zuzeni na obor hodnot jako domenu, invertujeme podminku z definice a ukazeme, ze je rostouci/klesajici

### Dalsi vlastnosti

![image.png](assets/image%2011.png)

![image.png](assets/image%2012.png)

## Limita funkce

### Okoli bodu

![image.png](assets/image%2013.png)

Okoli: otevreny interval do jiste vzdalenosti od bodu (cisla)

Prstencove okoli: neobsahuje samotny bod

### Limita

![image.png](assets/image%2014.png)

Tradicneji $\forall \epsilon > 0 \, \exists \delta > 0: \forall x \in P(a, \delta): f(x) \in U(b, \epsilon)$.  Tedy k limitnimu bodu se muzeme priblizit libovolne blizko a vzdy najdeme prstencove okoli v definicnim oboru takove, ze se cele zobrazi do okoli limitniho bodu.

![image.png](assets/image%2015.png)

Smer ⇒ rozloz prstencove okoli na sjednoceni leveho a praveho (vsechna x)

Smer ≤= je muzeme sjednotit

![image.png](assets/image%2016.png)

Kdyby mela dve limity, nalezneme pro ne dve disjunktni okoli (na ose y). Pro kazde z nich najdeme prstencove okoli na ose x. Ty maji urcite neprazdny prunik (roven tomu mensimu okoli). Zobrazme libovolny bod z tohoto pruniku funkci do kazdeho z okoli. Protoze ty jsou disjunktni, obrazy museji byt navzajem ruzne, co je spor s definici zobrazeni.

![image.png](assets/image%2017.png)

Konecna limita: jeji okoli s konecnym epsilon je konecny realny interval, coz je omezena mnozina

### Aritmetika limit

![image.png](assets/image%2018.png)

![image.png](assets/image%2019.png)

Toto nam umoznuje dokazovat limity

![image.png](assets/image%2020.png)

Dva policajti: umlatit nejak na okoli or whatever

Dalsi aritmetika:

![image.png](assets/image%2021.png)

![image.png](assets/image%2022.png)

![image.png](assets/image%2023.png)

![image.png](assets/image%2024.png)

Vysvetleni tretiho bodu: pokud g(b)=c, pak je to free. Pokud ale g(b)≠c (abs hodnota s + 5 v 0), potrebujeme zarucit, ze kazde prstencove okoli x bude zobrazeno funkci f do jinych hodnot nez je b. Pokud by aspon jeden bod sel do b, tim, ze limita g neni v b rovna c, nedokazali bychom nalezt okoli vzoru pro kazde epsilon.

## Posloupnosti

![image.png](assets/image%2025.png)

Zakladni vlastnosti, limity apod. stejne jako u funkci.

![image.png](assets/image%2026.png)

![image.png](assets/image%2027.png)

## Spojitost funkce

![image.png](assets/image%2028.png)

Stejna definice jako limita az na to, ze do okoli limity musi spadnout i obraz bodu a.

![image.png](assets/image%2029.png)

### Aritmetika spojitych funkci

![image.png](assets/image%2030.png)

### Vlastnosti spojitych funkci

![image.png](assets/image%2031.png)

Funkce na uzavrenem intervalu je omezena: 

1. Bolzano-weierstrass: existuje konvergujici posloupnost, ze spojitosti je limita vzdy konecna, tedy funkce je omezena
2. Ukazeme ze supremum a infimum obrazu je prvkem teto mnoziny, zase bolzano-weierstrass, udelame posloupnost sup-1/n a posleme n do nekonecna, pricemz vybereme konvergentni podposloupnost, dostaneme sup ≤ funkce ≤ sup, tedy plati rovnost (stejne pro infimum/minimum).

![image.png](assets/image%2032.png)

![image.png](assets/image%2033.png)

# Derivace

![image.png](assets/image%2034.png)

![image.png](assets/image%2035.png)

Funkce je diferencovatelna, pokud je tato limita realna

Funkce je diferencovatelna na otevrenem intervalu (kraje!), pokud je diferencovatelna v kazdem bode

## Derivace znamych funkci

![image.png](assets/image%2036.png)

![image.png](assets/image%2037.png)

## Vlastnosti derivace

![image.png](assets/image%2038.png)

Myslenka dukazu:

Vezmeme alternativni definici limity $\lim_{x \to c} \frac{f(x)-f(c)}{x-c} = f^\prime(c)$ existuje a je konecna

Pro $x \neq c$ zvazme tuto rovnost $f(x) - f(c) = \frac{f(x)-f(c)}{x-c} (x-c)$

Vysetrime limity, rozdelime na soucin limit, prava je 0, tedy limita leve strany kdyz $x \to c$ je rovna 0 ⇒ plati rovnost limity a funkcni hodnoty

## Aritmetika derivaci

![image.png](assets/image%2039.png)

![image.png](assets/image%2040.png)

## Derivace slozene funkce (chain rule)

![image.png](assets/image%2041.png)

## Derivace inverzni funkce

![image.png](assets/image%2042.png)

Dukaz

![image.png](assets/image%2043.png)

## Derivace vyssich radu

![image.png](assets/image%2044.png)

## l`Hospitalovo pravidlo

![image.png](assets/image%2045.png)

Nulove limity, ale existuje limita derivaci, pak jsou si rovny.

![image.png](assets/image%2046.png)

## Tayloruv Polynom

![image.png](assets/image%2047.png)

## Derivace a  extremy funkce

![image.png](assets/image%2048.png)

![image.png](assets/image%2049.png)

![image.png](assets/image%2050.png)

V bode extremu stacionarni bod

![image.png](assets/image%2051.png)

Podminka druheho radu

![image.png](assets/image%2052.png)

Pro prakticke vysetreni extremu

![image.png](assets/image%2053.png)

# Neurcity integral

![image.png](assets/image%2054.png)

![image.png](assets/image%2055.png)

![image.png](assets/image%2056.png)

## Integraly znamych funkci

![image.png](assets/image%2057.png)

![image.png](assets/image%2058.png)

## Vlastnosti primitivnich funkci

![image.png](assets/image%2059.png)

## Per parts

![image.png](assets/image%2060.png)

Odvozeni z derivace soucinu

## Substituce

![image.png](assets/image%2061.png)

![image.png](assets/image%2062.png)

# Urcity integral

## Integralni soucty

![image.png](assets/image%2063.png)

Horni a dolni odhad urciteho integralu

## Riemannuv integral

![image.png](assets/image%2064.png)

supremum dolnich se zjemnujicim se delenim → inf na stale mensim intervalu se bude blizit jednomu cislu, stejne jako pro infimum suprem → konverguje k rovnosti

Nezavisi na hodnotach funkce v konecne mnoha bodech

## Stejnomerna spojitost

![image.png](assets/image%2065.png)

Vsechny body z intervalu blizsi nez delta budou zobrazeny nejvyse epsilon daleko → funkce se “nemeni moc rychle”. Lze rozbit pro 1/x

## Vlastnosti urciteho integralu

![image.png](assets/image%2066.png)

## Aritmetika urciteho integralu

![image.png](assets/image%2067.png)

![image.png](assets/image%2068.png)

## Zakladni veta kalkulu

![image.png](assets/image%2069.png)

## Newton-Leibniz

Klicovy vztah mezi primitivni funkci a urcitym integralem

![image.png](assets/image%2070.png)

## Nevlastni integral

![image.png](assets/image%2071.png)

![image.png](assets/image%2072.png)

Hodi se pro rady

## Aplikace

![image.png](assets/image%2073.png)

Rovnomerne rozdeleni z PST

![image.png](assets/image%2074.png)

Obsah utvaru vymezeneho grafy funkci

# Ciselne rady

## Definice

![image.png](assets/image%2075.png)

![image.png](assets/image%2076.png)

## Konvergence

![image.png](assets/image%2077.png)

![image.png](assets/image%2078.png)

Absolutni konvergence je silnejsi kriterium nez konvergence. Uvedeme $\frac{(-1)^n}{n}$, tato rada konverguje, ale nekonverguje absolutne (harmonicka rada).

## Srovnavaci kriterium

![image.png](assets/image%2079.png)

Jak aplikovat? Ze sve rady algebraicky vyvodim nerovnost vuci zname konvergentni rade

Pokud nelze, evaluujeme limitu podilu

$L = \lim_{n \to \infty}\frac{|a_k|}{|b_n|}$, pokud je rovna 0, rada konverguje pokud rada b konverguje. Pokud ne, kriterium nerozhodlo

## Podilove kriterium

![image.png](assets/image%2080.png)

A v limitnim tvaru

![image.png](assets/image%2081.png)

evaluujeme limitu primo

## Odmocninove kriterium

![image.png](assets/image%2082.png)

A v limitnim tvaru

![image.png](assets/image%2083.png)

Tady pozor na odmocninu, reseni pres exp-log trik

## Integralni kriterium

![image.png](assets/image%2084.png)

Vicemene podle kucharky, nacpu tam radu v abs. hodnote a spocitam nevlastni integral

## Leibnizovo kriterium

![image.png](assets/image%2085.png)

Dava konvergenci, ne absolutni!