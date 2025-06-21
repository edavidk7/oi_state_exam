# PRP

Status: Done

Imperativní programování. Programovací jazyk C. Abstraktní datové typy a spojové struktury. 

• Řídící struktury, výrazy, funkce, nedefinované chování, kódovací (programovací) styly a čitelnost a srozumitelnost programů.

• Dekompozice programu do funkcí, předávání argumentů funkcím, návratová hodnota, rekurze a volání funkcí.

• Datové typy, vnitřní reprezentace číselných typů, struktury a uniony v C.

• Pole, ukazatel, textový řetězec, dynamická alokace a paměťové třídy.

• Zpracování vstupů a ošetření chybových stavů, práce se soubory.

• Zápis, překlad a spouštění programu v C. Vstup, výstup programu a jeho interakce s operačním systémem.

• Abstraktní datové typy (ADT) - definice, příklady specifikací základní ADT.

• Jednosměrný a obousměrný spojový seznam - implementace zásobníku a fronty.

• Nelineární spojové struktury - binární vyhledávací strom, prioritní fronta a halda.

• Datové struktury reprezentovatelné polem - kruhový buffer, prioritní fronta a halda.

• Využití prioritní fronty v hledání nejkratší cesty v grafu.

## Basics

C is a low-level, system programming language. Close to the hardware. Needs careful memory management.

## Programming Style

![image.png](assets/image.png)

![image.png](assets/image%201.png)

![image.png](assets/image%202.png)

## Program Structure

![image.png](assets/image%203.png)

![image.png](assets/image%204.png)

![image.png](assets/image%205.png)

### Expressions

![image.png](assets/image%206.png)

In expressions, we need some operators

![image.png](assets/image%207.png)

![image.png](assets/image%208.png)

![image.png](assets/image%209.png)

![image.png](assets/image%2010.png)

![image.png](assets/image%2011.png)

![image.png](assets/image%2012.png)

Variables

![image.png](assets/image%2013.png)

![image.png](assets/image%2014.png)

### Control Flow

![image.png](assets/image%2015.png)

![image.png](assets/image%2016.png)

![image.png](assets/image%2017.png)

![image.png](assets/image%2018.png)

Blocks can be nested, functions are named blocks. Curly braces.

![image.png](assets/image%2019.png)

### Functions

We break the program atomically into functions

![image.png](assets/image%2020.png)

![image.png](assets/image%2021.png)

![image.png](assets/image%2022.png)

**EXTREMELY IMPORTANT** in C, functions have pass-by-value arguments!

Everything is stored temporarily on the system stack, we have to pass pointer (whose value is an address) to pass arrays etc. to functions.

![image.png](assets/image%2023.png)

![image.png](assets/image%2024.png)

We can have function pointers:

![image.png](assets/image%2025.png)

## Data Types

### Numeric

![image.png](assets/image%2026.png)

![image.png](assets/image%2027.png)

![image.png](assets/image%2028.png)

![image.png](assets/image%2029.png)

### Enums

![image.png](assets/image%2030.png)

### Symbolic Macros

![image.png](assets/image%2031.png)

### String Literals

![image.png](assets/image%2032.png)

### Constants

![image.png](assets/image%2033.png)

![image.png](assets/image%2034.png)

### Custom

![image.png](assets/image%2035.png)

### Structs

![image.png](assets/image%2036.png)

![image.png](assets/image%2037.png)

![image.png](assets/image%2038.png)

This is super important for some structures with large data inside, we want to avoid copying them!

Structs are usually aligned, we can force packing:

![image.png](assets/image%2039.png)

### Unions

![image.png](assets/image%2040.png)

![image.png](assets/image%2041.png)

![image.png](assets/image%2042.png)

### Type Casting

![image.png](assets/image%2043.png)

## Arrays and memory

### Arrays

![image.png](assets/image%2044.png)

These arrays are fixed-size, cannot be resized, saved on stack!

![image.png](assets/image%2045.png)

![image.png](assets/image%2046.png)

Basically, a contiguous chunk of memory of sizeof(type)*count bytes

C99 allows VLA - run-time variable-size static memory allocation.

![image.png](assets/image%2047.png)

They are scope-local and the stack frame is trashed after function exits → don’t return the pointer.

![image.png](assets/image%2048.png)

### Pointers

![image.png](assets/image%2049.png)

![image.png](assets/image%2050.png)

![image.png](assets/image%2051.png)

![image.png](assets/image%2052.png)

![image.png](assets/image%2053.png)

![image.png](assets/image%2054.png)

![image.png](assets/image%2055.png)

### Dynamically-allocated memory

Always manage carefully, don’t forget to free!

![image.png](assets/image%2056.png)

### C and memory organization

![image.png](assets/image%2057.png)

![image.png](assets/image%2058.png)

![image.png](assets/image%2059.png)

Super important, storage class specifiers!

![image.png](assets/image%2060.png)

## C standard library

Why do we need it?

![image.png](assets/image%2061.png)

### Examples of common headers

![image.png](assets/image%2062.png)

![image.png](assets/image%2063.png)

### Files

![image.png](assets/image%2064.png)

![image.png](assets/image%2065.png)

![image.png](assets/image%2066.png)

![image.png](assets/image%2067.png)

![image.png](assets/image%2068.png)

### Error Handling

![image.png](assets/image%2069.png)

## Linked Structures

### List

![image.png](assets/image%2070.png)

![image.png](assets/image%2071.png)

Improvement - cyclic tail link

![image.png](assets/image%2072.png)

Bidirectional

![image.png](assets/image%2073.png)

Cyclic-bidirectional

![image.png](assets/image%2074.png)

## Abstract Data Types

![image.png](assets/image%2075.png)

Super important to know the definition - independent of exact implementation

![image.png](assets/image%2076.png)

### Stack

![image.png](assets/image%2077.png)

![image.png](assets/image%2078.png)

![image.png](assets/image%2079.png)

### Queue

![image.png](assets/image%2080.png)

![image.png](assets/image%2081.png)

### Priority Queue

![image.png](assets/image%2082.png)

![image.png](assets/image%2083.png)

Not good

![image.png](assets/image%2084.png)

Use a heap

![image.png](assets/image%2085.png)

![image.png](assets/image%2086.png)

![image.png](assets/image%2087.png)

![image.png](assets/image%2088.png)

![image.png](assets/image%2089.png)

### Heap for Dijkstra Shortest Path

![image.png](assets/image%2090.png)

![image.png](assets/image%2091.png)