# LAG

Status: Done

## Requirements

Lineární prostor, báze a dimenze, řešení soustav lineárních rovnic, lineární zobrazení. Základy maticového počtu.

• Lineárnı́ prostor a podprostor. Ilustrace na přı́kladech.

• Lineárnı́ obal. Lineárnı́ závislost a nezávislost.

• Báze, dimense a souřadnice vektoru v bázi.

• Matice. Sčı́tánı́ a násobenı́ matic.

• Lineárnı́ zobrazenı́, matice lineárnı́ho zobrazenı́, transformace souřadnic v jedné bázi na
souřadnice v jiné bázi.

• Soustavy lineárnı́ch rovnic, Frobeniova věta a geometrie množiny všech řešenı́ soustavy
lineárnı́ch rovnic.

• Determinant čtvercové matice. Výpočet determinantu (GEM a rozvoj determinantu podle
řádku nebo sloupce).

• Vlastnı́ čı́sla a vlastnı́ vektory matice. Diagonalisace matice.

• Skalárnı́ součin. Výpočet souřadnic vzhledem k ortogonálnı́ bázi. Ortogonalisačnı́ proces
(Gram-Schmidt).

## Linear Spaces and Subspaces

### Algebraic Fields

![image.png](assets/image.png)

![image.png](assets/image%201.png)

![image.png](assets/image%202.png)

Simply put, algebraic fields are structures of elements  with addition and multiplication. Addition must contain a neutral element (e.g. 0), it must be associative, commutative, and contain an inverse element (a - b = 0). Multiplication must contain a neutral element (e.g. 1), be associative and commutative. Together, they distribute on the left and the right (separately!). Finnally, the invertibility test must hold.

![image.png](assets/image%203.png)

### Linear Spaces

![image.png](assets/image%204.png)

![image.png](assets/image%205.png)

![image.png](assets/image%206.png)

Some important notes: 

1. There is only 1 null vector: 

![image.png](assets/image%207.png)

1. Zero times any vector is null vector

![image.png](assets/image%208.png)

1. For any vector x, -x is the opposite vector

![image.png](assets/image%209.png)

1. Any scalar times the null vector is still a null vector.

![image.png](assets/image%2010.png)

1. ax = 0 iff a is 0 or x is the null vector

![image.png](assets/image%2011.png)

### Linear Combination

![image.png](assets/image%2012.png)

### Span of Vectors

![image.png](assets/image%2013.png)

![image.png](assets/image%2014.png)

1. Simple, a combination of vectors from M is also a combination of vectors from N
2. Constructively, write it as a canonical combination of vectors from M
3. Take a combination of vectors from span(span(M)). Each individual vector is from span(M), which means it is a combination of vectors from M. Decompose each individual vector. Now, reorganize the sum in terms of vectors from M, and add the coefficients accordingly. This is equal to a linear combination of vectors from M, and therefore is a part of span(M).

### Linear Subspace

![image.png](assets/image%2015.png)

 Proof ideas

1. Previous point 3. The second IDK, I guess you could argue that a space containing M must contain all elements individually, and we can build that minimal space as span(M).
2. Proof from previous point 3 and the definition of a linear subspace.

![image.png](assets/image%2016.png)

Proofs

1. If the subspaces intersect anywhere other than the null vector, then the intersect is a non-empty subspace
2. Counterexample: x-axis and y-axis subspaces in R^2

## Linear Dependence and Independence

![image.png](assets/image%2017.png)

![image.png](assets/image%2018.png)

![image.png](assets/image%2019.png)

Some facts that hold:

If M is linearly independent, then any subset is also linearly independent.

If M is linearly dependent, then any superset is also linearly dependent.

M is linearly independent iff it remains independent after adding any vector that is not contained in its span.

M is linearly dependent iff we can remove some vector and its span remains unchanged.

Useful for proofs:

![image.png](assets/image%2020.png)

### Basis of Linear Space and Coordinates

![image.png](assets/image%2021.png)

![image.png](assets/image%2022.png)

![image.png](assets/image%2023.png)

Proof: Denote the finite set of generators G. If G is empty, then it is linearly independent.

Construct a system M of all LIDP subsets of G. Now pick M_0, the set with the highest number of elements. M_0 is LIDP, let us show it generates the original space L (and therefore is its basis). First, show that G is a subset of span(M_0). For each element x of G, investigate its presence in M_0.

If it is present in M_0, it is in its span. If not, then adding it to M_0 makes it LDP (M_0 was the maximal LIDP subset). Now write out the linear combination of x and vectors from M_0. This must be equal to zero for some nonzero coefficient of x. Reorder the equation, and prove that x is a linear combination of elements of M_0 → is in its span. 

Therefore, every x from G is an element of span(M_0). Now, do the following: L = span(G) is subset of span(span(M_0)) = span(M_0). Span(M_0) is a subset of L trivially, therefore, we have proven equality L = span(M_0), and M_0 is the basis of L.

![image.png](assets/image%2024.png)

![image.png](assets/image%2025.png)

It makes sense, by unifying the two subspaces and not gaining any additional dimensions, they must share a common basis and therefore be equal.

![image.png](assets/image%2026.png)

![image.png](assets/image%2027.png)

![image.png](assets/image%2028.png)

Proof: write out x as an element of span(B), therefore the linear combination. Assume that 2 distinct (non-equal) coordinate coefficients exist. Because x = x, write out the vectors using 2 different coordinate coefficients. Subtract them and reorder to get the differences of coefficients in front of the basis vectors. Because basis is LIDP, the difference must be 0, therefore the coefficients are always equal.

![image.png](assets/image%2029.png)

## Matrices and Linear Maps

![image.png](assets/image%2030.png)

### Linear Maps are Defined Up to a Basis

![image.png](assets/image%2031.png)

![image.png](assets/image%2032.png)

The matrix is identified with a linear map, defined for the canonical basis of the s-dim space.

![image.png](assets/image%2033.png)

### Space of all matrices is a linear space

![image.png](assets/image%2034.png)

### Matrix Multiplication is a Composition of Linear Maps

![image.png](assets/image%2035.png)

### Basic Properties Of Linear Maps

![image.png](assets/image%2036.png)

![image.png](assets/image%2037.png)

![image.png](assets/image%2038.png)

![image.png](assets/image%2039.png)

![image.png](assets/image%2040.png)

### Change of Basis

Matrices of Linear Maps are usually defined up to a fixed basis, and if we want to express them with respect to a different basis, we need to remap the matrix of the map to the new basis.

![image.png](assets/image%2041.png)

![image.png](assets/image%2042.png)

![image.png](assets/image%2043.png)

![image.png](assets/image%2044.png)

Don’t forget the correct multiplication order from mapping composition!

## Systems of Linear Equations

![image.png](assets/image%2045.png)

![image.png](assets/image%2046.png)

![image.png](assets/image%2047.png)

![image.png](assets/image%2048.png)

![image.png](assets/image%2049.png)

![image.png](assets/image%2050.png)

![image.png](assets/image%2051.png)

## Determinant of a Square Matrix

### Permutations

![image.png](assets/image%2052.png)

![image.png](assets/image%2053.png)

![image.png](assets/image%2054.png)

### Determinant

![image.png](assets/image%2055.png)

![image.png](assets/image%2056.png)

![image.png](assets/image%2057.png)

![image.png](assets/image%2058.png)

![image.png](assets/image%2059.png)

![image.png](assets/image%2060.png)

![image.png](assets/image%2061.png)

### Row/Column Expansion

![image.png](assets/image%2062.png)

![image.png](assets/image%2063.png)

## Eigenvectors, Eigenvalues

![image.png](assets/image%2064.png)

![image.png](assets/image%2065.png)

![image.png](assets/image%2066.png)

![image.png](assets/image%2067.png)

![image.png](assets/image%2068.png)

![image.png](assets/image%2069.png)

![image.png](assets/image%2070.png)

## Scalar (Inner) Product

![image.png](assets/image%2071.png)

![image.png](assets/image%2072.png)

![image.png](assets/image%2073.png)

### The inner product implies a vector norm

![image.png](assets/image%2074.png)

![image.png](assets/image%2075.png)

![image.png](assets/image%2076.png)

![image.png](assets/image%2077.png)

![image.png](assets/image%2078.png)

![image.png](assets/image%2079.png)

## Orthogonality and Orthogonal Basis

![image.png](assets/image%2080.png)

![image.png](assets/image%2081.png)

![image.png](assets/image%2082.png)

![image.png](assets/image%2083.png)

### Gram-Schmidt

![image.png](assets/image%2084.png)