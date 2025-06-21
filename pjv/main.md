# PJV

Status: Done

## Requirements

Programování v jazyce JAVA: vlastnosti a koncepce jazyka. Principy objektového programování. B0B36PJV (Webové stránky předmětu)

• Vývojové prostředí (JDK), JVM. Kompilace a běh programu. Správa paměti, GC. profilování a
optimalizace.

• Objekty, třídy a jejich vztahy, princip abstrakce a zapouzdření, modifikátory přístupu. Interface
a abstraktní třída. Dědičnost a kompozice, polymorfismus, dynamická vazba.

• Výčtové typy, práce s kolekcemi, vzor iterátor, generické typy.

• Vnitřní a anonymní třídy. Imutabilita, vzor singleton. Proměnné a metody třídy vs. instance.

• Mechanismus výjimek (typy a jejich ošetření, vlastní výjimky), práce se soubory (přístup k
souboru, textové vs. binární, proudy, ukládání dat) a sokety (typy soketů, typy spojení, síťová
komunikace).

• Paralelismus, vícevláknové aplikace, problém souběhu a zastavení. Tvorba vláken a jejich
ukončení, threadpool, synchronizace, volatilita.

## Java Basics

![image.png](assets/image.png)

![image.png](assets/image%201.png)

![image.png](assets/image%202.png)

Java is pass by reference!

## OOP

![image.png](assets/image%203.png)

![image.png](assets/image%204.png)

![image.png](assets/image%205.png)

### Class Attributes

![image.png](assets/image%206.png)

### Objects

![image.png](assets/image%207.png)

### Encapsulation

![image.png](assets/image%208.png)

### Instance vs Class

![image.png](assets/image%209.png)

![image.png](assets/image%2010.png)

### Access Modifiers

![image.png](assets/image%2011.png)

### Constructor

![image.png](assets/image%2012.png)

### Immutable Objects

![image.png](assets/image%2013.png)

### Polymorphism

Simply put - we have a method with the same name, but the underlying implementation for each class differs.

![image.png](assets/image%2014.png)

![image.png](assets/image%2015.png)

![image.png](assets/image%2016.png)

### Inheritance

![image.png](assets/image%2017.png)

![image.png](assets/image%2018.png)

### Composition

![image.png](assets/image%2019.png)

![image.png](assets/image%2020.png)

### Derived Classes

![image.png](assets/image%2021.png)

### Abstract Classes and Interfaces

![image.png](assets/image%2022.png)

### Single Dispatch

![image.png](assets/image%2023.png)

Calling the correct method implemented for the runtime type of an object.

### Double Dispatch

![image.png](assets/image%2024.png)

### Method Overloading Vs Overriding

![image.png](assets/image%2025.png)

## Data Types

### Primitives

Same as C

### Objects

Duals of the primitives with some convenience methods.

![image.png](assets/image%2026.png)

### Enums

![image.png](assets/image%2027.png)

![image.png](assets/image%2028.png)

## Collections

### Java Collection Framework

![image.png](assets/image%2029.png)

![image.png](assets/image%2030.png)

![image.png](assets/image%2031.png)

Some advantages of JFC

![image.png](assets/image%2032.png)

### Iterators

![image.png](assets/image%2033.png)

![image.png](assets/image%2034.png)

It is important to consider what will happen with the underlying data when using an iterator some collection:

![image.png](assets/image%2035.png)

### Collection Interface

![image.png](assets/image%2036.png)

### Set

![image.png](assets/image%2037.png)

### List

![image.png](assets/image%2038.png)

Exact implementations: ArrayList (hash-table based), LinkedList, Vector (thread safe)

### Map

![image.png](assets/image%2039.png)

## Generic Types

![image.png](assets/image%2040.png)

![image.png](assets/image%2041.png)

Type checking and automatic casting solved by the compiler

![image.png](assets/image%2042.png)

![image.png](assets/image%2043.png)

## Exceptions

![image.png](assets/image%2044.png)

![image.png](assets/image%2045.png)

![image.png](assets/image%2046.png)

Example exception classes:

![image.png](assets/image%2047.png)

### Checked and unchecked exceptions

![image.png](assets/image%2048.png)

### Finally

![image.png](assets/image%2049.png)

## File Operations

Main model of file access in Java

![image.png](assets/image%2050.png)

### Sequential and Direct (Random) access

Sequential: file is read iteratively by bytes, data can be interpreted on the fly (e.g. numbers). A cursor points to the current index in the file. Cursor can only be reset to the beginning. Suitable for different data sources, not just files.

Random: Read and write at any position in the file. Cursor can be set to an arbitrary position, the file must be available in memory (loaded) for this to work.

### Files and streams in Java

![image.png](assets/image%2051.png)

![image.png](assets/image%2052.png)

Readers/streams are for sequential access

### Serialization

![image.png](assets/image%2053.png)

### Example

![image.png](assets/image%2054.png)

## Parallel Programming

![image.png](assets/image%2055.png)

### Process

![image.png](assets/image%2056.png)

![image.png](assets/image%2057.png)

### OS

![image.png](assets/image%2058.png)

### Semaphores

![image.png](assets/image%2059.png)

![image.png](assets/image%2060.png)

A more abstract construct is a Monitor (used in Java):

![image.png](assets/image%2061.png)

### Multi-threaded applications

![image.png](assets/image%2062.png)

![image.png](assets/image%2063.png)

![image.png](assets/image%2064.png)

### Java Threads

![image.png](assets/image%2065.png)

![image.png](assets/image%2066.png)

![image.png](assets/image%2067.png)

Exposes some useful methods

![image.png](assets/image%2068.png)

![image.png](assets/image%2069.png)

### Thread Synchronization

As mentioned, monitors

![image.png](assets/image%2070.png)

or Synchronized

![image.png](assets/image%2071.png)

This is useful is multiple threads call a method on the same instance of an object

![image.png](assets/image%2072.png)

![image.png](assets/image%2073.png)

### Thread Pool

![image.png](assets/image%2074.png)

![image.png](assets/image%2075.png)

### Other typical applications

![image.png](assets/image%2076.png)

![image.png](assets/image%2077.png)

Boss/Worker

![image.png](assets/image%2078.png)

Peer

![image.png](assets/image%2079.png)

Pipeline

![image.png](assets/image%2080.png)

### Multithreaded functions

![image.png](assets/image%2081.png)

### Race conditions and deadlocks

![image.png](assets/image%2082.png)

![image.png](assets/image%2083.png)

## Sockets and networking

![image.png](assets/image%2084.png)

![image.png](assets/image%2085.png)

![image.png](assets/image%2086.png)

![image.png](assets/image%2087.png)

![image.png](assets/image%2088.png)

![image.png](assets/image%2089.png)

![image.png](assets/image%2090.png)

### Java Sockets

![image.png](assets/image%2091.png)

![image.png](assets/image%2092.png)

![image.png](assets/image%2093.png)

## Performance and profiling

![image.png](assets/image%2094.png)

![image.png](assets/image%2095.png)

## Garbage Collection

![image.png](assets/image%2096.png)

GC runs on the heap!

![image.png](assets/image%2097.png)

![image.png](assets/image%2098.png)

![image.png](assets/image%2099.png)

Or with reduced fragmentation

![image.png](assets/image%20100.png)

### Generational Garbage Collector

![image.png](assets/image%20101.png)

### the core concept: generations

java's heap is divided into different "generations" based on object age:

1. **young generation (eden space, s0, s1):** where new objects are born.
2. **old generation (tenured space):** where long-lived objects "graduate" to.
3. **metaspace (or permgen before java 8):** not really part of the gc generations for object allocation, but important for class metadata. this isn't handled by the generational gc in the same way.

### step-by-step gc process (simplified for common collectors like G1/ParallelGC concepts)

### phase 1: young generation gc (minor gc)

this is the most frequent gc event.

1. **object allocation in eden:**
    - when you create a `new object()`, it's initially allocated in the `eden` space of the young generation.
    - eden is filled up pretty quickly.
2. **eden space full - minor gc trigger:**
    - when `eden` is full, a minor gc is triggered. this is a "stop-the-world" (stw) event, meaning application threads pause briefly.
3. **root scanning:**
    - the gc identifies "gc roots." these are objects that are definitely alive and reachable, like:
        - local variables on method stacks.
        - active threads.
        - static fields.
        - jni references.
4. **reachability analysis & marking (young gen only):**
    - starting from the gc roots, the gc traverses the object graph in the young generation to find all objects that are reachable (i.e., still being used by the application).
    - unreachable objects are considered garbage.
5. **copying live objects to survivor spaces:**
    - all the *live* (reachable) objects in `eden` are copied to *one* of the two `survivor spaces` (let's say `s0`).
    - objects that were already in the *other* survivor space (`s1`) from a previous minor gc that are *still alive* are also copied to `s0`.
6. **age incrementation & promotion:**
    - each time an object survives a minor gc (i.e., it gets copied to a survivor space), its "age" counter increments.
    - if an object's age reaches a certain threshold (the "tenuring threshold," which is configurable), it's considered long-lived enough and is *promoted* (copied) to the **old generation**.
7. **clearing young generation:**
    - after copying, `eden` and the `survivor space` that was *just vacated* (`s1` in our example) are completely cleared. all the garbage objects that weren't copied are simply gone.
8. **survivor space swap:**
    - the `s0` and `s1` roles swap. the `s0` (which now contains live objects) becomes the "from" space for the next minor gc, and `s1` becomes the "to" space.

### phase 2: old generation gc (major gc or full gc)

this is less frequent but more expensive.

1. **old generation full - major gc trigger:**
    - when the old generation fills up, a major gc (or full gc, depending on the collector and context) is triggered. this is often a longer stw event than a minor gc.
2. **root scanning (entire heap):**
    - gc roots are identified across the *entire* heap (young and old generations).
3. **reachability analysis & marking (entire heap):**
    - the gc traverses the entire object graph, starting from roots, to identify all reachable objects in both the young and old generations.
4. **sweep/compact (old gen):**
    - unreachable objects in the old generation are identified and their memory reclaimed.
    - some collectors (like parallel old) then *compact* the old generation, moving live objects together to reduce fragmentation. other collectors (like g1) do this in phases or regions.
5. **concurrent phases (for concurrent collectors like cms/g1):**
    - more modern collectors (like cms, g1) have concurrent phases where they can do a lot of the marking and even some sweeping *while the application threads are still running*. this significantly reduces the stw pause times for major collections. however, there are still short stw pauses at the beginning and end of these phases.

![image.png](assets/image%20102.png)

![image.png](assets/image%20103.png)