# JAG

Status: Done

## Requirements

Regulární jazyky a bezkontextové jazyky. Popis těchto jazyků pomocí automatů a gramatik,
vlastnosti regulárních a bezkontextových jazyků. 

• Deterministické a nedeterministické konečné automaty a jejich vztah.

• Regulární jazyky a jejich vlastnosti. Lemma o vkládání (Pumping lemma) a Nerodova věta.

• Regulární výrazy a jejich vztah k regulárním jazykům.

• Bezkontextové gramatiky. Chomského hierarchie jazyků. Bezkontextové jazyky a jejich vlastnosti. Lemma o vkládání pro bezkontextové jazyky (Pumping lemma pro bezkontextové
jazyky).

• Zásobníkové automaty (nedeterministické i deterministické ) a jejich vztah k bezkontextovým
jazykům.

## Deterministic and Non Deterministic Automata

### Deterministic Automata

![image.png](assets/image.png)

![image.png](assets/image%201.png)

![image.png](assets/image%202.png)

![image.png](assets/image%203.png)

### Reduction of DFA

![image.png](assets/image%204.png)

![image.png](assets/image%205.png)

![image.png](assets/image%206.png)

![image.png](assets/image%207.png)

### Non-Deterministic Automata

![image.png](assets/image%208.png)

![image.png](assets/image%209.png)

![image.png](assets/image%2010.png)

![image.png](assets/image%2011.png)

![image.png](assets/image%2012.png)

![image.png](assets/image%2013.png)

![image.png](assets/image%2014.png)

## Regular Languages

The class of languages accepted by some finite deterministic (or non-deterministic) automaton.

![image.png](assets/image%2015.png)

### Pumping Lemma

Can be used to prove a language is not regular (necessary condition)

![image.png](assets/image%2016.png)

### Nerod’s Theorem

Can be used to prove a language is or isn’t regular.

![image.png](assets/image%2017.png)

![image.png](assets/image%2018.png)

### Operations with Languages

![image.png](assets/image%2019.png)

![image.png](assets/image%2020.png)

![image.png](assets/image%2021.png)

Prove claims by proving the elementary ones with automatons and the rest with logic.

## Regular Expressions

![image.png](assets/image%2022.png)

![image.png](assets/image%2023.png)

![image.png](assets/image%2024.png)

Proof by closure of regular languages to the operations, and the fact that all of the elementary regular expressions describe regular languages.

![image.png](assets/image%2025.png)

Construct by incremental hops and loops in the DFA

![image.png](assets/image%2026.png)

![image.png](assets/image%2027.png)

### Problems that can be solved algorithmically

![image.png](assets/image%2028.png)

![image.png](assets/image%2029.png)

## Grammars

![image.png](assets/image%2030.png)

![image.png](assets/image%2031.png)

![image.png](assets/image%2032.png)

![image.png](assets/image%2033.png)

### Chomsky Hierarchy of Grammars

![image.png](assets/image%2034.png)

![image.png](assets/image%2035.png)

![image.png](assets/image%2036.png)

Construct by an algorithm that first removes everything that generates an empty word by backward induction and then add all possible empty-word rules to the grammar.

![image.png](assets/image%2037.png)

## Context-Free Grammar

![image.png](assets/image%2038.png)

![image.png](assets/image%2039.png)

### Reduced Context-Free Grammar

![image.png](assets/image%2040.png)

![image.png](assets/image%2041.png)

![image.png](assets/image%2042.png)

### Chomsky Normal Form CF Grammar

![image.png](assets/image%2043.png)

![image.png](assets/image%2044.png)

![image.png](assets/image%2045.png)

Proof: binary tree

### Pumping Lemma for Context-Free Languages

![image.png](assets/image%2046.png)

Again, used to prove a language is not context free.

### CYK Algorithm

![image.png](assets/image%2047.png)

Check if CF grammar in CHNF generates w

### Closures

![image.png](assets/image%2048.png)

Proof 1.: grammars

Proof 2.: counterexample

![image.png](assets/image%2049.png)

Proof 1: stack automaton

Proof 2: reversed grammar

Proof 3: too hard

### Problems

![image.png](assets/image%2050.png)

1. solve by finding a grammar that does not generate an empty word
2. CYK

## Stack-Based Automata

![image.png](assets/image%2051.png)

![image.png](assets/image%2052.png)

![image.png](assets/image%2053.png)

![image.png](assets/image%2054.png)

![image.png](assets/image%2055.png)

Proof 1: Add a new starting symbol, new starting state and new finish state, whenever the read word is empty and new starting symbol is on stack, go to finish.

Proof 2: In finish states empty the stack and go to a new dummy state.

![image.png](assets/image%2056.png)

Let the automaton expand the rules of the grammar on the stack such that the non terminal symbols are expanded with empty input (generate a stack with all possible rule applications), and whenever the word and the top of the stack match with the same letter, delete them from both. 

### Deterministic SFA

![image.png](assets/image%2057.png)

![image.png](assets/image%2058.png)

![image.png](assets/image%2059.png)