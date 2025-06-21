# LGR

Status: Done

## Requirements

Syntaxe a sémantika výrokové a predikátové logiky. Základní pojmy teorie grafů. B0B01LGR
(Webové stránky předmětu)

• Syntax výrokové logiky. Sémantika výrokové logiky. Důkazový systém přirozená dedukce.
Významová (sémantická) ekvivalence formulı́ výrokové logiky. Normálnı́ formy formulı́. Du-
̊sledek ve výrokové logice. Úplné systémy logických spojek. Schopnost formalisace a řešenı́
logických úloh s využitı́m výrokové logiky.

• Syntax predikátové logiky. Sémantika predikátové logiky. Významová (sémantická) ekvivalence formulı́ predikátové logiky. Normálnı́ formy formulı́. Důsledek v predikátové logice.
Schopnost formalisace a řešenı́ logických úloh s využitı́m predikátové logiky.

• Základnı́ pojmy a definice teorie grafů; schopnost formálnı́ práce s těmito pojmy. Stromy a
jejich vlastnosti. Minimálnı́ kostry a algoritmy na jejich hledánı́. Komponenty silné souvislosti
a algoritmus na jejich hledánı́. Schopnost modelovánı́ praktických problémů s využitı́m
grafů.

## Vyrokova Logika

![image.png](assets/image.png)

Kazda formule vyrokove logiky je jednoznacne citelna

![image.png](assets/image%201.png)

### Syntakticky Strom

![image.png](assets/image%202.png)

![image.png](assets/image%203.png)

![image.png](assets/image%204.png)

Formule jsou logicky ekvivalentni, pokud $\phi \vdash \psi$ a zaroven $\psi \vdash \phi$

### Prirozena dedukce ve vyrokove logice

![image.png](assets/image%205.png)

![image.png](assets/image%206.png)

![image.png](assets/image%207.png)

![image.png](assets/image%208.png)

![image.png](assets/image%209.png)

![image.png](assets/image%2010.png)

Priklad:

![image.png](assets/image%2011.png)

V PD existuje scope platnych predpokladu, a lze iterativne opakovat jiz platna tvrzeni z vnejsich scopu

![image.png](assets/image%2012.png)

Neprimy Dukaz LEM

![image.png](assets/image%2013.png)

Negace je syntactic sugar pro $\phi \vdash \bot$

Syntakticky a semanticky vyznam se lisi, $a \neq \neg \neg a$

## Semantika vyrokove logiky

tl;dr, hledame pravdivostni ohodnoceni dane formule z existence ohodnoceni atomickych formuli

![image.png](assets/image%2014.png)

![image.png](assets/image%2015.png)

![image.png](assets/image%2016.png)

![image.png](assets/image%2017.png)

Pravdivostni ohodnoceni formule je zobrazeni rozsirujici ohodnoceni atomickych formuli. Necht $u_\text{at}: \text{At} \to \{0,1\}$ je ohodnoceni atomickych formuli. Hodnoceni vsech formuli definujeme rekurzivne:

- $u(a) = u_\text{at}(a)$
- $u(\top) = 1$
- $u(\bot) = 0$
- $u(\phi \cdot \psi) = [\bullet](u(\phi), u(\phi)]$ kde $\bullet$ je libovolna binarni spojka
- $u(\neg \phi) = [\neg]u(\phi)$

### Formule dle splnitelnosti

![image.png](assets/image%2018.png)

![image.png](assets/image%2019.png)

Mnozina formuli je splnitelna, pokud existuje ohodnoceni takove, ze vsechny formule mnoziny jsou pravdive zaroven.

Vztah semanticke ekvivalence je reflexivni, symetricky a tranzitivni.

### Tautologicke vztahy spojek

![image.png](assets/image%2020.png)

![image.png](assets/image%2021.png)

Semanticky dusledek mnoziny formuli $S$

Rekneme, ze $\phi$ je semantickym dusledkem $S$, pokud $\forall u: S \text{ je pravdiva} \implies u(\phi)=1$

Pro $S$ ktera neni splnitelna je dusledkem libovolna formule (predpoklad nelze splnit).

### Logicky a semanticky dusledek

Veta o korektnosti a uplnosti prirozene dedukce ve vyrokove logice

- Plati $S \vdash \phi \iff S \vDash \phi$
- Levo-pravo: korektnost
- Pravo-levo: uplnost

Vhodne pro dukazy, ukazeme semanticky dusledek dukazem logickeho pomoci PD. Na druhou stranu ukazeme, ze formule neni dusledek tak, ze najdeme protiprikladove ohodnoceni atomickych formuli

### Normalni Formy

Booleovske funkce lze popsat tabulkami, lze kazdou takovou funkci reprezentovat formuli VL?

- DNF - jazyk
    - L:= $a| \neg a$ - literál
    - K:= $L| K\land L$ - konjunkce literálů
    - D:=$K|D\lor K$ - formule
- CNF - jazyk
    - L:= $a| \neg a$ - literál
    - K:= $L| K\lor L$ - disjunkce literálů
    - D:=$K|D\land K$ - formule

Dokazuji, ze $\lor, \land, \neg$ je uplny system logicky spojek, lze s nimi reprezentovat jakoukoliv booleovskou funkci (napr. NAND)

## Predikatova Logika

### Jazyk

![image.png](assets/image%2022.png)

Predikatovy symbol: ruznym hodnotam promennych (pocet dany aritou) prirazuje logicke ohodnoceni (0,1), napr. x je sude

Konstantni symbol: ekvivalent “vlastniho podstatneho jmena”

Dvousortovy jazyk: termy - objekty, formule - vlastnosti

Funkcni symbol: mapuji promenne na jine promenne, napr. x+6 (Arita 1)

![image.png](assets/image%2023.png)

### Termy

![image.png](assets/image%2024.png)

Termy specifikujeme BNF jako $t := x|c|f(t_1,t_2, \dots, t_m)$

### Atomicka formule

![image.png](assets/image%2025.png)

### Formule

![image.png](assets/image%2026.png)

### Promenne

![image.png](assets/image%2027.png)

Substituci lze nahradit volne vyskyty promennych

### Sentence

![image.png](assets/image%2028.png)

### Substituce

Pro promennou $x$, term $t$ a formuli $\phi$ definujeme substituci $\phi[\frac{t}{x}]$ jako formuli ktera vznikne nahrazenim volnym vyskytu promenne x termem t.

Rekneme, ze term je volny pro x, pokud se zadna volna promenna v termu t nestane po substituci vazana (name clash s kvantifikatorem).

### Prirozena dedukce v predikatove logice

Ekvivalence a uplnost plati stejne, jako ve vyrokove logice

### PD v Predikatove Logice

Spojky jako ve VL, kvantifikatory nasledovne:

![image.png](assets/image%2029.png)

Pri eliminaci obecneho kvantifikatoru musime mit volnost!

Musime deklarovat promenne, a pouzivat pouze deklarovane promenne

Rovnost:

![image.png](assets/image%2030.png)

## Semantika Predikatove Logiky

![image.png](assets/image%2031.png)

Predikatovym symbolum priradime ty mnoziny promennych, kde jsou pravdive

Konstantnim priradime prvky universa

Funkcnim priradime N-tice z universa

Priklad:

![image.png](assets/image%2032.png)

![image.png](assets/image%2033.png)

Jak interpretujeme termy? Pomoci kontextu promennych

Kontext promennych $\rho$  je parcialni zobrazeni promennych na prvky univerza, ne nutne pro vsechny promenne. Definujeme update kontextu $\rho[x:= d]$ tak, ze vsechny prvky jine nez $x$ si ponechaji prirazeni a pouze x je zmeneno.

Interpretaci termu definujeme induktivne.

![image.png](assets/image%2034.png)

![image.png](assets/image%2035.png)

![image.png](assets/image%2036.png)

![image.png](assets/image%2037.png)

![image.png](assets/image%2038.png)

Toto se dokazuje pomoci prirozene dedukce v predikatove logice

![image.png](assets/image%2039.png)

### Semanticky dusledek

- Sémantický důsledek
    - sentence $\varphi$ je sémantický důsledek množiny S, pokud je každý model množiny $S_i$ i modelem sentence $\varphi$

Korektnost a uplnost dle Godelovy vety.

### Normalni Formy

![image.png](assets/image%2040.png)

![image.png](assets/image%2041.png)

## Teorie Grafu

### Neorientovane Grafy

![image.png](assets/image%2042.png)

![image.png](assets/image%2043.png)

![image.png](assets/image%2044.png)

![image.png](assets/image%2045.png)

![image.png](assets/image%2046.png)

![image.png](assets/image%2047.png)

![image.png](assets/image%2048.png)

![image.png](assets/image%2049.png)

![image.png](assets/image%2050.png)

![image.png](assets/image%2051.png)

![image.png](assets/image%2052.png)

![image.png](assets/image%2053.png)

![image.png](assets/image%2054.png)

### Stromy

![image.png](assets/image%2055.png)

![image.png](assets/image%2056.png)

![image.png](assets/image%2057.png)

![image.png](assets/image%2058.png)

![image.png](assets/image%2059.png)

### Kostry

![image.png](assets/image%2060.png)

![image.png](assets/image%2061.png)

Myslenka obecneho algoritmu pro nalezeni: Rozdel graf na jednovrcholove komponenty souvislosti, postupne pridavej hrany, ktere propoji dve komponenty, a jsou pro jednu z nich nejlevnejsi.

![image.png](assets/image%2062.png)

![image.png](assets/image%2063.png)

### Grafove Algoritmy

![image.png](assets/image%2064.png)

![image.png](assets/image%2065.png)

![image.png](assets/image%2066.png)

### Eulerovske Grafy

![image.png](assets/image%2067.png)

![image.png](assets/image%2068.png)

![image.png](assets/image%2069.png)

![image.png](assets/image%2070.png)

![image.png](assets/image%2071.png)

### Barveni Grafu

![image.png](assets/image%2072.png)

![image.png](assets/image%2073.png)

![image.png](assets/image%2074.png)

![image.png](assets/image%2075.png)

![image.png](assets/image%2076.png)

![image.png](assets/image%2077.png)

![image.png](assets/image%2078.png)

### Nezavislost

![image.png](assets/image%2079.png)

![image.png](assets/image%2080.png)

### Orientovane Grafy

![image.png](assets/image%2081.png)

![image.png](assets/image%2082.png)

![image.png](assets/image%2083.png)

![image.png](assets/image%2084.png)

![image.png](assets/image%2085.png)

![image.png](assets/image%2086.png)

### Korenovy strom

![image.png](assets/image%2087.png)

### Acyklicke grafy

![image.png](assets/image%2088.png)

![image.png](assets/image%2089.png)

![image.png](assets/image%2090.png)

![image.png](assets/image%2091.png)

![image.png](assets/image%2092.png)