---
author:
- |
    Mario H. Gonzalez-Sauri, UNU-MERIT\
    [gonzalez@merit.unu.edu](gonzalez@merit.unu.edu)
title: An Introduction to R for Network Analysis
...

Introduction to R
=================

Operators
---------

Operators are symbols that perform an action with a specific result.
They help us to manipulate variables, evaluate statements, construct
functions and perform operations in general.[^1]

                Logical Operators
  ---- -------- ---------------------------------------------------------------
     1 -        Minus, can be unary or binary
     2 +        Plus, can be unary or binary
     3 !        Unary not
     4 \~       Tilde, used for model formulae, can be either unary or binary
     5 ?        Help
     6 :        Sequence, binary (in model formulae: interaction)
     7 \*       Multiplication, binary
     8 /        Division, binary
     9 `^`      Exponentiation, binary
    10 %x%      Special binary operators, x can be replaced by any valid name
    11 %%       Modulus, binary
    12 %/%      Integer divide, binary
    13 %%       Matrix product, binary
    14 %o%      Outer product, binary
    15 %x%      Kronecker product, binary
    16 %in%     Matching operator, binary (in model formulae: nesting)
    17 $<$      Less than, binary
    18 $>$      Greater than, binary
    19 ==       Equal to, binary
    20 $>$=     Greater than or equal to, binary
    21 $<$=     Less than or equal to, binary
    22 &        And, binary, vectorized
    23 &&       And, binary, not vectorized
    24 $|$      Or, binary, vectorized
    25 $|$$|$   Or, binary, not vectorized
    26 $<$-     Left assignment, binary
    27 -$>$     Right assignment, binary
    28 \$       List subset, binary

We can use the operators to perform basic algebraic operations and to
evaluate logical statements. Keep track of the basic syntax of the
language such as *semicolons* and *parentheses*.

`  `

    ## [1] 6

`  `

    ## [1] 30

` `

    ## [1] 0.25

`  `

    ## [1] 1.5

`        `

    ## [1] -0.2222222

\
` `<span>`%/%`</span>` `

    ## [1] 1

\
` `<span>`%%`</span>` `

    ## [1] 2

    ## [1] 4 5 6 7

\
\
`    `

    ## [1] TRUE

`    `

    ## [1] TRUE

`  `

    ## [1] FALSE

`  `

    ## [1] FALSE

`      `

    ## [1] TRUE

`    `

    ## [1] FALSE FALSE

`    `

    ## [1] TRUE TRUE

`        `

    ## [1] TRUE

\
`          `

    ## [1] TRUE TRUE TRUE

\
`          `

    ## [1] TRUE

`  `<span>`%in%`</span>`   `

    ## [1] TRUE TRUE

Objects
-------

**R** is an object-base programming language [^2] and what that means
for practial purposes is that everything aside the *operators* and
*syntaxis* has a specific *attributes*: class, structure, typeof,
length, dimmension and *structure*. Pay attention to the use of the
*left assignment* for storing objects and also to the use of
*parentheses* for declaring arguments of functions.

-   **Vectors**: Also called atomic vectors.

    \
    \
    \
    \
    `  `\

        ## [1] "NULL"

        ## [1] 0

        ## [1] "NULL"

    \
    `       `\

        ##   a   b 
        ## 2.3 4.0

    `   `\
    `   `\

        ## a b 
        ## 4 7

    `    `\

        ## [1] "numeric"

        ## [1] 2

        ## [1] "double"

    \
    `   `\

        ## [1] "integer"

        ## [1] 2

        ## [1] "integer"

    \
    `  `\

        ## [1] "logical"

        ## [1] "logical"

    \
    `   `\

        ## [1] "character"

        ## [1] "character"

    \
    `  `\
    `   `\

        ## [1] 2

        ## [1] "male"   "female"

        ## [1] FALSE

    ` `\
    \
    `    `\
    ` `\

        ## [1] TRUE

-   **Matrices:** Are 2-dimensional arrays of data of one single
    atomic object. Matrices are helpful for running statistical analysis
    and any kind of algorithm that requires mathematical manipulation. A
    key aspect of a matrix is that their type is inherited by one single
    atomic object. Create a matrix with a numeric vector as elements and
    run the **typeof** function. Then add an extra column but these time
    use a character vector and verify the change in the attributes of
    the object with **typeof**. Notice that you can not use mathematical
    operators if the matrix is *character* type.

    \
    \
    `       `\

        ## [1] "matrix"

        ## [1] "integer"

    \
    `       `\

        ## [1] "matrix"

        ## [1] "character"

    \

    <span>****</span>

    \
    `  `\
    `  `\
    `  `\

        ##      [,1] [,2] [,3]
        ## [1,]    3    1    1
        ## [2,]    2    3    1
        ## [3,]    2    2    3

    \
    `    `\

        ##      [,1] [,2] [,3]
        ## [1,]    2    1    0
        ## [2,]    1    2    1
        ## [3,]    0    3    2

    \
    `    `\

        ##      [,1] [,2] [,3]
        ## [1,]    1    2    3
        ## [2,]    4    5    6
        ## [3,]    7    8    9

    \
    \
    `  `

        ##    a    b 
        ##  9.2 16.0

    ` `

        ##         a         b 
        ## 0.4347826 0.2500000

    `  `

        ##    a    b 
        ##  6.3 11.0

    \

        ##      [,1] [,2] [,3]
        ## [1,]    3    2    2
        ## [2,]    1    3    2
        ## [3,]    1    1    3

    \
    `    `

        ##      [,1] [,2] [,3]
        ## [1,]    4    0   -2
        ## [2,]   -1    0   -4
        ## [3,]   -5   -3   -4

    \
    ` `<span>`%%`</span>` `

        ##      [,1] [,2] [,3]
        ## [1,]    7    8    3
        ## [2,]    7   11    5
        ## [3,]    6   15    8

    \
    ` `<span>`%%`</span>`   `

        ##      [,1] [,2] [,3]
        ## [1,] TRUE TRUE TRUE
        ## [2,] TRUE TRUE TRUE
        ## [3,] TRUE TRUE TRUE

    \
    `             `\
    `  `\
    ` `<span>`%%`</span>` `

        ##      [,1]          [,2] [,3]
        ## [1,]    1  0.000000e+00    0
        ## [2,]    0  1.000000e+00    0
        ## [3,]    0 -4.440892e-16    1

    ` `<span>`%%`</span>` `

        ##      [,1] [,2] [,3]
        ## [1,]    1    0    0
        ## [2,]    0    1    0
        ## [3,]    0    0    1

    \

        ## eigen() decomposition
        ## $values
        ## [1] 147.741703 -34.981904  -4.759798
        ## 
        ## $vectors
        ##            [,1]       [,2]       [,3]
        ## [1,] -0.6935491 -0.1529705  0.3017373
        ## [2,] -0.4916846 -0.6387581 -0.7727752
        ## [3,] -0.5265319  0.7540478  0.5583664

    `  `\
    `  `\
    ` `<span>`%%`</span>`       `

        ##       [,1]
        ## [1,] FALSE
        ## [2,] FALSE
        ## [3,] FALSE

    ` `<span>`%%`</span>`     `

        ## [1] TRUE

-   **Data Frames:** have a more heterogeneous structure, whereas
    vectors an matrices belong to a specific *typeof* object, data
    frames can have multiple types in each column.

    \
    ` `\
    `  `\
    `   `\
    `    `\
    `    `\
    `        `\
    `  `\
    `  `\
    `  `

        ## 'data.frame':    5 obs. of  4 variables:
        ##  $ A: Factor w/ 5 levels "A","B","C","D",..: 1 2 3 4 5
        ##  $ B: Factor w/ 5 levels "a","b","c","d",..: 1 2 3 4 5
        ##  $ C: int  1 2 3 4 5
        ##  $ D: num  2.4 2 3 9 7

    `  `\
    `  `

        ##  A     B           C           D       
        ##  A:1   a:1   Min.   :1   Min.   :2.00  
        ##  B:1   b:1   1st Qu.:2   1st Qu.:2.40  
        ##  C:1   c:1   Median :3   Median :3.00  
        ##  D:1   d:1   Mean   :3   Mean   :4.68  
        ##  E:1   e:1   3rd Qu.:4   3rd Qu.:7.00  
        ##              Max.   :5   Max.   :9.00

    `  `\
    `   `

        ##   A B C   D
        ## 1 A a 1 2.4
        ## 2 B b 2 2.0
        ## 3 C c 3 3.0

    `  `\
    `  `

        ##   A B C   D
        ## 1 A a 1 2.4
        ## 2 B b 2 2.0
        ## 3 C c 3 3.0
        ## 4 D d 4 9.0
        ## 5 E e 5 7.0

    \
    \
    `        `\

        ##   papers authors
        ## 1      A       1
        ## 2      A       2
        ## 3      A       3
        ## 4      B       2
        ## 5      B       3
        ## 6      C       4

    \
    `  `\

        ##       authors
        ## papers 1 2 3 4
        ##      A 1 1 1 0
        ##      B 0 1 1 0
        ##      C 0 0 0 1

    \
    `  `\

        ##        authors
        ## authors 1 2 3 4
        ##       1 1 1 1 0
        ##       2 1 2 2 0
        ##       3 1 2 2 0
        ##       4 0 0 0 1

-   **Functions**: Are very usefull when we need to perfrom the
    same operation(s) multiple times.

    \
    `  `\
    `        `\
    `  `\
    `  `\
    \
    `  `\
    \
    `  `<span>`) {`</span>\
    `  `\
    `   `<span>`%%`</span>` `\
    `  `\
    \
    \
    \

        ##   Degree
        ## A      1
        ## B      1
        ## C      2
        ## D      3
        ## E      2

-   **Lists**: Are the most flexible structure, we can store multiple
    objects of different classes. A *data frame* is actually a list with
    a particular structure. We can use **dput** function to print and
    store the structure of any object, also helps to create reproducible
    examples.[^3]

    \

        ## structure(list(A = structure(1:5, .Label = c("A", "B", "C", "D", 
        ## "E"), class = "factor"), B = structure(1:5, .Label = c("a", "b", 
        ## "c", "d", "e"), class = "factor"), C = 1:5, D = c(2.4, 2, 3, 
        ## 9, 7)), .Names = c("A", "B", "C", "D"), row.names = c(NA, -5L
        ## ), class = "data.frame")

    \
    `  `\
    `  `\
    `   `\
    `   `\
    `   `\
    `   `\
    \

        ## List of 4
        ##  $ factor    : Factor w/ 2 levels "male","female": 1 2
        ##  $ matrix    : num [1:5, 1:5] 0 0 1 1 0 0 0 0 1 0 ...
        ##   ..- attr(*, "dimnames")=List of 2
        ##   .. ..$ : chr [1:5] "A" "B" "C" "D" ...
        ##   .. ..$ : chr [1:5] "A" "B" "C" "D" ...
        ##  $ data.frame:'data.frame':  5 obs. of  4 variables:
        ##   ..$ A: Factor w/ 5 levels "A","B","C","D",..: 1 2 3 4 5
        ##   ..$ B: Factor w/ 5 levels "a","b","c","d",..: 1 2 3 4 5
        ##   ..$ C: int [1:5] 1 2 3 4 5
        ##   ..$ D: num [1:5] 2.4 2 3 9 7
        ##  $ list      :List of 1
        ##   ..$ : int [1:3] 1 2 3

    ` `\
    `  `\
    `   `\
    `    `\
    `    `\
    `        `\
    `  `\
    `  `

        ##  A     B           C           D       
        ##  A:1   a:1   Min.   :1   Min.   :2.00  
        ##  B:1   b:1   1st Qu.:2   1st Qu.:2.40  
        ##  C:1   c:1   Median :3   Median :3.00  
        ##  D:1   d:1   Mean   :3   Mean   :4.68  
        ##  E:1   e:1   3rd Qu.:4   3rd Qu.:7.00  
        ##              Max.   :5   Max.   :9.00

Indexing Objects
----------------

The syntaxys for subsetting changes slightly from object to object, but
in general, we can subset in three ways: *nominal, numeric, logical*.
**Data frames** and **lists** use a special operator: **\$**.

`  `\
`  `\
`  `

    ## [1] "a" "b"

`  `

    ##   a 
    ## 2.3

`  `

    ## b 
    ## 4

`  `\
`     `

    ##   D E
    ## A 0 1
    ## C 0 1

`  `\
`   `

    ##   A   D
    ## 1 A 2.4
    ## 2 B 2.0
    ## 3 C 3.0
    ## 4 D 9.0
    ## 5 E 7.0

`  `\
`   `

    ## $factor
    ## [1] male   female
    ## Levels: male female
    ## 
    ## $matrix
    ##   A B C D E
    ## A 0 0 0 0 1
    ## B 0 0 0 0 1
    ## C 1 0 0 0 1
    ## D 1 1 1 0 0
    ## E 0 0 1 1 0

`  `\
\
`  `\
`  `

    ##   a 
    ## 2.3

`  `\
`   `

    ## B C 
    ## 0 0

`  `\
`   `

    ##   B C
    ## 1 a 1
    ## 2 b 2
    ## 3 c 3
    ## 4 d 4
    ## 5 e 5

`  `\
`  `\
`  `

    ## $matrix
    ##   A B C D E
    ## A 0 0 0 0 1
    ## B 0 0 0 0 1
    ## C 1 0 0 0 1
    ## D 1 1 1 0 0
    ## E 0 0 1 1 0

`  `\
`  `

    ## [1] "list"

`  `\
`  `

    ## [1] "matrix"

`  `\
`   `

    ## A B C D E 
    ## 0 0 0 1 0

`  `\
\
`  `\
`   `

    ##   a 
    ## 2.3

`  `\
`  `

    ##  [1] 0 0 0 0 0 0 1 1 1 0

`  `\
`     `

    ## [1] 2.4 2.0 3.0 9.0 7.0

`  `\
`  `\
`    `

    ## $data.frame
    ##   A B C   D
    ## 1 A a 1 2.4
    ## 2 B b 2 2.0
    ## 3 C c 3 3.0
    ## 4 D d 4 9.0
    ## 5 E e 5 7.0

`  `\
`    `

    ##   C D
    ## B 0 0
    ## C 0 0

`  `\
`  `\
`  `

    ## [1] A B C D E
    ## Levels: A B C D E

`  `\
`  `

    ## [1] 1 2 3 4 5

`  `

    ## A B C D E 
    ## 0 0 0 0 1

Control Flow
------------

Basic structure of *if, else and ifelse* statetements.

\
`    `\
`     `<span>`) {`</span>\
`  `\
`  `

    ## [1] "Yes it is..."

`  `\
`  `\
`  `\
`    `\
\
`    `<span>`) {`</span>\
`    `\
`     `<span>`)) {`</span>\
`  `\
`   `<span>`{`</span>\
`  `\
`  `<span>`}`</span>\
\
`  `

    ##        authors
    ## authors 1 2 3 4
    ##       1 0 1 1 0
    ##       2 1 0 2 0
    ##       3 1 2 0 0
    ##       4 0 0 0 0

`  `

    ## [1] "Graph is disconnected"

`  `\
`  `\
`  `\
\
`    `<span>`) {`</span>\
`  `\
`      `\
`  `\
`      `\
`      `\
`     `<span>`loops) {`</span>\
`      `\
`    `\
`     `\
`    `<span>`{`</span>\
`  `\
`  `\
`  `\
\
`  `

    ## [1] "The graph has: multi edges and loops."

`  `

    ## [1] "The graph is simple"

`  `\
`  `\
`  `\
`    `<span>`) {`</span>\
`  `\
`    `\
`  `\
`      `\
`     `<span>`v) {`</span>\
`  `\
`      `<span>`v) {`</span>\
`  `\
`   `<span>`{`</span>\
`  `\
`  `\
`  `\
\
`  `

    ## [1] "Edges: 9"

`  `

    ## [1] "Edges: 7"

`  `\
`  `\
`  `\
\
`  `\
`        `

    ## [1]  TRUE FALSE  TRUE

`  `\
`    `

    ## [1] "NO"

`  `

    ## [1] 1

`    `

    ## [1] "YES"

`          `

    ## [1] "YES" "NO"  "YES"

`        `

    ## [1] TRUE

`  `\
`   `\
`  `<span>`) {`</span>\
`    `\
`  `\
`      `\
`  `\
`  `

    ##   A B C D E
    ## A 0 0 0 0 1
    ## B 0 0 0 0 1
    ## C 1 0 0 0 1
    ## D 1 1 1 0 0
    ## E 0 0 1 1 0

`  `

    ## [1] "Squared"

`     `\
`  `

    ##      [,1] [,2] [,3]
    ## [1,]    2    1    0
    ## [2,]    1    2    1
    ## [3,]    0    1    2

`  `

    ## [1] "Symmetric"

Loops
-----

Review the basic structure of while and for loops. Two rules of thumb,
try to avoid them as possible; and in many situations, the while loop is
more efficient and simpler to read.

`  `\
`     `\
`    `\
`  `\
`     `<span>`) {`</span>\
`    `\
`        `\
`  `\
`  `

    ## [1] "Fibonacci Seq: 2"
    ## [1] "Fibonacci Seq: 3"
    ## [1] "Fibonacci Seq: 5"

`  `\
`  `\
`  `

    ##   A B C D E
    ## A 0 0 0 0 1
    ## B 0 0 0 0 1
    ## C 1 0 0 0 1
    ## D 1 1 1 0 0
    ## E 0 0 1 1 0

`    `\
`    `\
`     `<span>`(A)) {`</span>\
`    `\
`  `

    ## [1] "E"
    ## [1] "E"
    ## [1] "A" "E"
    ## [1] "A" "B" "C"
    ## [1] "C" "D"

apply family of functions
-------------------------

:

The **apply** function takes an array as first argument and perform a
function over all the elements of the array.

\
`        `\
\
`  `\
`     `\
`  `<span>`(ma)){col.cum`</span>`   `\
`  `\

    ## [1] TRUE TRUE TRUE TRUE TRUE

\
\
`  `\
`     `\
`  `<span>`(ma)){row.cum`</span>`   `\
`  `\

    ## [1] TRUE TRUE TRUE TRUE TRUE

`  `\
<span>`%%`</span>

    ## [1] TRUE TRUE TRUE TRUE TRUE

` `\
`            `\
`  `\
<span>`) {`</span>\
`  `\
<span>`)`</span>

    ##   [,1] [,2] [,3] [,4] [,5]
    ## I    2    0    0    0    1
    ## J    1    1    1    0    0
    ## B    1    1    0    2    0
    ## C    1    1    0    0    0
    ## E    0    2    0    0    0
    ## D    0    0    1    0    0
    ## G    0    0    1    1    2
    ## A    0    0    2    1    0
    ## H    0    0    0    1    1
    ## F    0    0    0    0    1

The **lapply** function takes a list as the first argument and applies a
function to all the elements of the list. The function has two main
advantages, first improves the readability of the code by avoiding the
overuse of loops. Secondly, **lapply** is more flexible in comparison to
the **apply** function, because can take a list of multiple non list
objects to perform functions over each element of the list.

\
`  `\
`   `

    ## [[1]]
    ## [1] 55
    ## 
    ## [[2]]
    ## [1] 275

`  `\
`  `

    ## [[1]]
    ##   Degree
    ## A      1
    ## B      1
    ## C      2
    ## D      3
    ## E      2
    ## 
    ## [[2]]
    ##      Degree
    ## [1,]      3
    ## [2,]      4
    ## [3,]      3
    ## 
    ## [[3]]
    ##      Degree
    ## [1,]    187
    ## [2,]    139
    ## [3,]    128
    ## 
    ## [[4]]
    ##           Degree
    ## [1,]  0.04585366
    ## [2,] -0.07556911
    ## [3,]  0.06121951

`  `\
`  `\
`  `\
`  `\
`  `\
`   `<span>`) {`</span>\
`  `\
`  `\
`  `<span>`)`</span>

    ## $rating
    ## [1] 148.1713
    ## 
    ## $complaints
    ## [1] 177.2828
    ## 
    ## $privileges
    ## [1] 149.7057
    ## 
    ## $learning
    ## [1] 137.7575
    ## 
    ## $raises
    ## [1] 108.1023
    ## 
    ## $critical
    ## [1] 97.9092
    ## 
    ## $advance
    ## [1] 105.8575

`  `\
`  `\
`     `<span>`) {`</span>\
`  `\
`    `\
`    `\
`    `\
`    `\
`    `\
`  `\
`  `<span>`)`</span>\
`  `

    ## [1] "matrix"

`  `\
`  `

    ##      rating        complaints     privileges       learning    
    ##  Min.   :40.00   Min.   :37.0   Min.   :30.00   Min.   :34.00  
    ##  1st Qu.:58.75   1st Qu.:58.5   1st Qu.:45.00   1st Qu.:47.00  
    ##  Median :65.50   Median :65.0   Median :51.50   Median :56.50  
    ##  Mean   :64.63   Mean   :66.6   Mean   :53.13   Mean   :56.37  
    ##  3rd Qu.:71.75   3rd Qu.:77.0   3rd Qu.:62.50   3rd Qu.:66.75  
    ##  Max.   :85.00   Max.   :90.0   Max.   :83.00   Max.   :75.00  
    ##      raises         critical        advance     
    ##  Min.   :43.00   Min.   :49.00   Min.   :25.00  
    ##  1st Qu.:58.25   1st Qu.:69.25   1st Qu.:35.00  
    ##  Median :63.50   Median :77.50   Median :41.00  
    ##  Mean   :64.63   Mean   :74.77   Mean   :42.93  
    ##  3rd Qu.:71.00   3rd Qu.:80.00   3rd Qu.:47.75  
    ##  Max.   :88.00   Max.   :92.00   Max.   :72.00

Graphics
--------

**R** has a robust environment for graphics, in fact statistical
analysis and graphics are at the core of the language.[^4]. Start by
running **demo$graphics$** in the console to get an overview of the
capabilities of the **graphics** library. Take a look at this
**cheatsheet**[^5] to get an overview of the main plotting functions.

<span>`  `</span>

-   **Color Management**

    A key point about the **graphics** library is how to manage the
    colour spaces. A color can be defined in three different ways: by
    *name*, by *hexadecimal* values and by *RGB* values. Browse this
    website to get an exhaustive list of colours and conversions between
    the three systems. [^6]

    \
    `  `\
    \
    `  `\
    \
    `  `\
    \
    \
    `  `\
    `    `\
    `      `\
    `    `\
    `      `\
    `    `\
    `      `\
    `    `\
    `      `\
    `    `\
    `      `\
    `    `\
    `      `\
    `      `\
    `    `\
    `    `\
    `       `\
    `       `\
    `    `\
    \
    \
    `  `<span>`){`</span>\
    `  `\
    `      `\
    `  `\
    `      `\
    \
    \
    \

    ![image](figure/unnamed-chunk-15-1){width="\maxwidth"}

-   **Histograms**

    \
    \
    `     `\
    `  `

        ## null device 
        ##           1

    `    `\
    `   `<span>`) {`</span>\
    `  `\
    `   `\
    `    `\
    `    `\
    `  `<span>`))`</span>

-   **Box-plots**

    \
    `     `\
    `    `\
    `   `<span>`) {`</span>\
    `  `\
    `   `\
    `    `\
    `  `<span>`))`</span>

    ![image](figure/unnamed-chunk-17-1){width="\maxwidth"}

-   **Scatterplots**

    `  `\
    `       `

    ![image](figure/unnamed-chunk-18-1){width="\maxwidth"}

    `  `\
    `  `\
    `  `\
    `         `

    ![image](figure/unnamed-chunk-18-2){width="\maxwidth"}

-   **ggplot2**

    \
    `   `\
    `        `\
    \
    \
    `   `\
    `       `\
    `      `\
    `       `\
    `       `\
    `    `\
    \
    \
    `       `

    ![image](figure/unnamed-chunk-19-1){width="\maxwidth"}

Multiple Regression model
-------------------------

`  `\
`        `\
\
`  `\
`        `\
\
`  `\
`    `\
`       `\
`     `\
\
\
`  `

<span>l c c c </span> & Model 1 & Model 2 & Model 3\
(Intercept) & $56.76^{***}$ & $10.79$ & $13.58$\
& $(9.74)$ & $(11.59)$ & $(7.54)$\
advance & $0.18$ & $-0.22$ & $-0.19$\
& $(0.22)$ & $(0.18)$ & $(0.14)$\
complaints & & $0.61^{***}$ & $0.62^{***}$\
& & $(0.16)$ & $(0.12)$\
privileges & & $-0.07$ &\
& & $(0.14)$ &\
learning & & $0.32$ & $0.31$\
& & $(0.17)$ & $(0.15)$\
raises & & $0.08$ &\
& & $(0.22)$ &\
critical & & $0.04$ &\
& & $(0.15)$ &\
R$^2$ & 0.02 & 0.73 & 0.73\
Adj. R$^2$ & -0.01 & 0.66 & 0.69\
Num. obs. & 30 & 30 & 30\
RMSE & 12.24 & 7.07 & 6.73\

`  `\
`    `\
`     `\
`       `\
`       `\
`  `\
`  `

![image](figure/unnamed-chunk-20-1){width="\maxwidth"}

Utilities
---------

The most basic utilities, include reading files, installing packages,
and basic regular expressions.

\
\
\
\
\
\
\
\
\
\
`  `\
`   `\
`      `<span>`) {`</span>\
`  `\
`   `<span>`{`</span>\
`  `\
`  `\
\
`  `\
`     `\
\
`  `\
`      `

    ##   X rating complaints
    ## 1 1     43         51
    ## 2 2     63         64

`  `\
`    `\
`  `\
`      `

    ## [[1]]
    ## [1] "\"\""           "\"rating\""     "\"complaints\"" "\"privileges\""
    ## [5] "\"learning\""   "\"raises\""     "\"critical\""   "\"advance\""

`  `\
`      `

    ## [[1]]
    ## [1] "\"\""           "\"rating\""     "\"complaints\"" "\"privileges\""
    ## [5] "\"learning\""   "\"raises\""     "\"critical\""   "\"advance\""   
    ## 
    ## [[2]]
    ## [1] "\"1\"" "43"    "51"    "30"    "39"    "61"    "92"    "45"

`  `\
\
`  `\
`  `\
`     `<span>`) {`</span>\
`         `\
`  `\
\
\
`  `\
`  `\
`    `\
`      `\
`  `\
`    `\
`  `

    ## [1] "     Y   </td><td style=\"text-align: left;\"> rating    </td><td style=\"text-align: left;\"> numeric  </td><td style=\"text-align: left;\"> Overall rating </td>"                  
    ## [2] "    X[1] </td><td style=\"text-align: left;\"> complaints</td><td style=\"text-align: left;\"> numeric </td><td style=\"text-align: left;\"> Handling of employee complaints </td>"  
    ## [3] "    X[2] </td><td style=\"text-align: left;\"> privileges</td><td style=\"text-align: left;\"> numeric </td><td style=\"text-align: left;\"> Does not allow special privileges </td>"

`   `

    ## [1] "Overall rating "                   
    ## [2] "Handling of employee complaints "  
    ## [3] "Does not allow special privileges "
    ## [4] "Opportunity to learn "             
    ## [5] "Raises based on performance "      
    ## [6] "Too critical "                     
    ## [7] "Advancement"

Application: Monte Carlo Simulation
-----------------------------------

Use a loop to generate a Montecarlo simulation on an OLS model, to
estimate the bias due to an ommited variable.
$$y=\beta_0+\beta_1x_1+\beta_2x_2+\beta_3x_1*x_2+\epsilon$$ Estimate the
model: $$y=\beta_0+\beta_1x+\epsilon$$

\
`  `\
\
\
`  `\
`  `\
`  `\
`  `\
\
\
`       `<span>`= T) {`</span>\
`  `\
`   `\
`  `\
`      `\
`      `\
`      `\
`  `\
`  `\
`                    `\
`  `\
`   `<span>`(ommit) {`</span>\
`      `\
`  `\
`   `<span>`{`</span>\
`          `\
`  `\
`  `\
\
\
`   `\
`      `\
\
\
\
` `

![image](figure/unnamed-chunk-22-1){width="\maxwidth"}

\

    ## [1] 0.07347242

Now, use the use a **loop**, to change the sample size of the Monte
Carlo simulation to test the consistency of the estimator.

\
`  `\
`  `\
`  `<span>`(samples)){`</span>\
`     `\
\
\
\
\
` `

    ## [[1]]
    ## [1] 0.05084155
    ## 
    ## [[2]]
    ## [1] 0.08611329
    ## 
    ## [[3]]
    ## [1] 0.09659755

\

    ## [[1]]
    ## [1] 0.5719636
    ## 
    ## [[2]]
    ## [1] 0.3261407
    ## 
    ## [[3]]
    ## [1] 0.02966656

\
\
`   `\
` `\
`  `\
`  `\
\
\
`   `<span>`) {`</span>\
`   `\
`  `\
\
<span>`)`</span>\
\
`  `\
`   `\
\
\
\
`    `\
`     `\
`  `\
`     `

![image](figure/unnamed-chunk-23-1){width="\maxwidth"}

Plotting graphs using Igraph
============================

Generate Graphs
---------------

To generate networks we can use the **R:Base** functions, as well as
functions provided by the **igraph** package. Firstly, generate an
adjacency matrix and an edgelist using the **R:Base** to get the
intuition of the two main objects used to generate networks.

\
`  `\
`      `\
`        `\
`  `\
`    `\
\
\
`     `\

    ## igraph layout specification, see ?layout_:
    ## layout_as_bipartite(<graph>, input = "igraph_tu_mgs_v00.Rnw", encoding = "UTF-8")

\
\
`  `

Now, use **graph\_from\_literal** function to generate networks using
*formulas*. Then generate a *plot grid* by passing a two element
*numeric vector* to **mfrow** argument from the **par** function. This
is similar as specifying the number of rows and columns in a matrix.

\
\
\
`   `\
`  `\
\
\
`      `\
\
\
`  `\
\
\
`  `\
\
\
`      `

![image](figure/unnamed-chunk-25-1){width="\maxwidth"}

**igraph** can also generate networks based on specific topologies or
models. We can visualize these graphs in a $\textbf{3x3}$ grid.

\
\
\
\
`   `\
\
\
`  `\
\
\
\
`   `\
`                 `\
\
`  `<span>`) {`</span>\
\
\
`  `\
`  `\
`  `\
`  `\
\
\
\
\
` `<span>`) {`</span>\
\
\
`  `\
`  `\
`  `\
`  `\
\
<span>`))`</span>\
\
\
`   `

![image](figure/unnamed-chunk-26-1){width="\maxwidth"}

\
`    `\
\
\
`  `\
` `<span>`) {`</span>\
\
\
`  `\
`  `\
`  `\
`  `\
\
<span>`))`</span>

![image](figure/unnamed-chunk-26-2){width="\maxwidth"}

Layouts of igraph
-----------------

The **igraph** has different algorithms called **layouts**, that help us
visualize and highlight certain network topologies.

\
`  `\
`    `\
\
\
\
\
`     `\
`   `\
`   `\
`  `\
\
\
`   `\
` `<span>`){`</span>\
\
`  `\
`  `\
` `\
<span>`))`</span>

![image](figure/unnamed-chunk-27-1){width="\maxwidth"}

![image](figure/unnamed-chunk-27-2){width="\maxwidth"}

![image](figure/unnamed-chunk-27-3){width="\maxwidth"}

![image](figure/unnamed-chunk-27-4){width="\maxwidth"}

Setting shape of vertices
-------------------------

Generate a random variable **Age** from random draws of a normal
distribution, with mean **30** and standard deviation of **5** and
create subsets accordingly to each 3-Quantiles. Use different shapes to
separate the vertices into three groups accordingly to each 3-Quantiles
of the probability distribution.

\
` `\
\
\
\
\
\
\
\
\
\
\
\
`    `\
`      `\
`      `\
`      `\
\
\
\
\
`  `\
`  `\
\
` `\
` `\

![image](figure/unnamed-chunk-28-1){width="\maxwidth"}

Setting colours of vertices and adding legends to plots
-------------------------------------------------------

Generate a vector of attributes by sampling with replacement a set
$\textbf{Gender} = \{ female, male \}$, and set a new attribute to the
graph called **gender**. Also, add legends, using **legend** function,
and pass the desired arguments.

\
`     `\
\
\
`  `\
`    `\
`        `\
`    `\
`   `\
`   `\
\
\
`  `\
`    `\
`    `\
`  `\
`   `\
`  `\
`    `\
`    `\
`     `\
`    `\
`    `\
`    `\
`    `\

![image](figure/unnamed-chunk-29-1){width="\maxwidth"}

Setting colours to groups of vertices
-------------------------------------

We can remark groups of vertices in the graph. Find the vertex with the
highest *degree centrality* and mark the adjacent vertices in a group.

` `\
`      `\
`  `\
`  `\
`    `\
`        `\
`    `\
`   `\
`   `\
`   `\
`    `\
`  `

![image](figure/unnamed-chunk-30-1){width="\maxwidth"}

Set colours and thickness to edges
----------------------------------

Change the thickness of the edges, accordingly to the output their
measurement of **edge.betweenes**. Also, change the colour of the edges
that belong to a 3-clique or connected triangle.

`   `\
`    `\
`               `\
`               `\
`      `\
\
`  `\
`          `\
`     `\
`     `\
`  `\
`   `\
`     `\
`     `<span>`%in%`</span>`   `

![image](figure/unnamed-chunk-31-1){width="\maxwidth"}

Subgraphs
---------

Find the vertices adjacent to the vertex $A$ and then plot a subgraph of
the neighbourhood.

`   `\
`  `\
`             `\
`             `\
`    `\
\
`  `\
`    `\
`       `\
\
`  `\
`      `\
\
`  `\
`     `\
`  `\
`  `

![image](figure/unnamed-chunk-32-1){width="\maxwidth"}

Network Analysis
================

Local Clustering
----------------

Local clustering of a vertex $v$ is the ratio of the number of
3-cliques, or triangles, that fall in to $v$ and the number of connected
triplets from which two edges are incident to $v$. For instance, for
vertex $A$, the number of triangles, is defined as the cardinality of
the set of vertices $\Delta_{A}=\{(A,C,B), (A,C,D), (A,D,E), (A,E,D)\}$.
Similarly the number of connected triplets is the set
$T=\{(A,C,B), (A,C,D), (A,D,E), (A,E,D), (C,A,E), (D,A,B) \}$. The local
clustering coefficient $C_{A}=\frac{|\Delta_{A}|}{|T|}=\frac{2}{3}$. The
local clustering is not defined for topologies, such as *stars*,*trees*,
*lattices*.

`   `\
`    `\
`             `\
`             `\
`      `\
\
`    `\
`      `

![image](figure/unnamed-chunk-33-1){width="\maxwidth"}

`    `\
`        `

    ## [1] 0.6666667

`     `

    ## [1] NaN   0   0   0 NaN

`        `

    ## [1]   0 NaN NaN NaN NaN

`        `

    ## [1]   0   0 NaN NaN NaN

Degree and Strength
-------------------

Add two new edges to the graph, from **A** to **B**, and from **A** to
**A**, and plot the graph. Compare the measurements of *degree* and
*strength* for the vertex $A$, notice that the vertices adjacent to
**A** are $\{B,C,D,E)\}$ but both measurements have a value of $7$.
Simplify the graph, remove multiples edges and loops, and compute the
*degree* centrality. Finally, use the **count\_multiple** function to
compute weights for each edge in the graph and calculate *strength*
centrality one more time.

`      `\
`               `\
`               `\
`        `\
\
`    `\
`          `\
\
`    `\
`    `

![image](figure/unnamed-chunk-34-1){width="\maxwidth"}

`    `\
`          `

    ## A 
    ## 7

`          `

    ## A 
    ## 7

`    `\
`        `\
`      `\
`      `

    ## A 
    ## 4

`    `\
`      `\
`      `\
`          `

    ## A 
    ## 7

Structural Holes
----------------

Is a measure that quantify the level of redundancy of information from
author’s connections.

`      `\
`               `\
`               `\
`        `\
`      `\
`    `

    ## 5 x 5 sparse Matrix of class "dgCMatrix"
    ##   A B D E F
    ## A . 1 . 1 1
    ## B 1 . 1 . .
    ## D . 1 . . .
    ## E 1 . . . .
    ## F 1 . . . .

Eigenvector Centrality
----------------------

The intuition of *eigenvector centrality* is to capture the importance
of the neighbourhood of each vertex. Vertices who are connected to
adjacent vertices with higher degree centrality will perform better in
this measurement. The interest lies in finding a vector that represents
a ranking of relative importance for each vertex. This is similar to
finding a solution for the eigenvalue problem. $$Aw = \lambda w$$
Suppose that we can assign equal weights $w_1$, to each vertex, and then
perform $Aw_1=w_2$, similar to computing a weighted degree. Then use
$w_2$ to perform $n$ interations till difference between
$Aw_{n} - \lambda w_{n+1}$ gets closer to zero. Run a algorithm of
*eigenvector centrality* [^7] and compare the results with the
**eigen\_centrality** function.

\
`      `\
`               `\
`               `\
`        `\
\
\
`   `<span>`) {`</span>\
`    `\
`    `\
`  `\
`  `<span>`# w <- max(A%%rep(1, n))`</span>\
`    `\
`  `\
`    `\
`  `\
`    `\
`  `\
`    `\
`  `\
`    `\
`        `<span>`pre) {`</span>\
`    `\
`      `\
`    `\
`       `<span>`%%`</span>` `\
`    `\
`      `\
`    `\
`        `\
`    `\
`        `\
`  `\
`       `\
\
\
\

    ##        A        B        C        D        E 
    ## 1.000000 0.809017 0.809017 0.809017 0.809017

` `

    ## [1] 1.000000 0.809017 0.809017 0.809017 0.809017

Weighted Measurements of centrality
-----------------------------------

The **tnet** package has implementations of weighted versions of
*degree*, *betweeness* and *closeness*. Lets generate a graph of $n$
vertices and, compare the difference between the weighted and unweighted
centrality measurements.

`      `\
`    `\
`          `\
\
`    `\
`          `\
`      `\
`        `\
`         `\
`      `\
`      `\
\
`    `\
`          `\
`        `\
`         `\
`    `\
`      `\
`      `\
`      `\
\
`    `\
`      `\
`      `\
\
`    `\
`      `\
`      `\
`     `\
`    `\
`      `\
`     `\
`     `\
`     `\
`     `\
`      `\
`     `\
`      `\
`    `\
\
`    `

         vertex   degree   w.degree   strength   betweenness   w.betweenness   closeness   w.closeness
  ---- -------- -------- ---------- ---------- ------------- --------------- ----------- -------------
     1        1   144.00      72.00    1252.00          2.77            5.00        0.05          0.00
     2        2    84.00      42.00     436.00          1.64            0.00        0.04          0.00
     3        3   192.00      96.00    1652.00          3.10           34.00        0.05          0.00
     4        4   158.00      79.00    2030.00          1.53           17.00        0.04          0.00
     5        5   112.00      56.00     668.00          2.20            1.00        0.05          0.00
     6        6   124.00      62.00     812.00          1.90            6.00        0.04          0.00
     7        7   150.00      75.00    1414.00          1.24            7.00        0.04          0.00
     8        8   218.00     109.00    2990.00          2.46           14.00        0.05          0.00
     9        9   166.00      83.00    1466.00          2.10           24.00        0.05          0.00
    10       10   214.00     107.00    3258.00          1.85           41.00        0.04          0.00
    11       11   174.00      87.00    2070.00          1.24           24.00        0.04          0.00
    12       12   140.00      70.00    1116.00          2.71            0.00        0.05          0.00
    13       13   128.00      64.00     936.00          1.92            5.00        0.04          0.00
    14       14   108.00      54.00     792.00          0.88            0.00        0.04          0.00
    15       15   202.00     101.00    2594.00          1.26           11.00        0.04          0.00
    16       16   252.00     126.00    2568.00          3.38           11.00        0.05          0.00
    17       17   104.00      52.00     524.00          1.31            1.00        0.04          0.00
    18       18   102.00      51.00     446.00          1.85            0.00        0.04          0.00
    19       19   130.00      65.00     890.00          2.23            2.00        0.05          0.00
    20       20   138.00      69.00    1054.00          1.43            6.00        0.04          0.00

Redundancy of Centrality in Compleate graphs
--------------------------------------------

There are some cases in which the measurements of centrality will not
provide relevant information. For instance, if the structure of a
undirected network approaches a compleate graph, each pair of different
vertices is connected by a unique edge
$\forall \{i \neq j\}:E(v_i,v_j)=1$, then the centrality measures will
not yield relevant information.

`        `\
`  `\
`     `\

\[1\] 4 4 4 4 4

\[1\] 0.25 0.25 0.25 0.25 0.25

\[1\] 0.765625 0.765625 0.765625 0.765625 0.765625

`   `

\[1\] 1 1 1 1 1

\[1\] 1 1 1 1 1

\[1\] 0 0 0 0 0

\
`  `\
`  `\
` `\
`    `\
`  `\
`  `\
`  `<span>`(conn)){`</span>\
`      `\
`  `\
` `\
`  `\
`     `\
`     `\
` `\
`       `\
\
\
`  `\
\
`   `\
\
`  `\
`  `<span>`(out.data)){`</span>\
`  `\
`  `\
`  `\
`     `\
\
`  `\
\
\
\

![image](figure/unnamed-chunk-38-1){width="\maxwidth"}

Basic Network analysis with Data
--------------------------------

Browse the **Stanford Large Network Dataset Collection** [^8] and the
**NetworkRepository** [^9] to get some sample empirical data.

\
` `

<span>****</span>

\
`    `\
`                    `\
` `\
`           `\
`     `\
`   `\
\
` `\
` `\
` `\
\
`   `\
`      `\
`           `\
`             `\
`     `\
`          `\
`      `\
`       `\
`       `\
\
` `

        id      closeness   degree   strength   betweenness   struc\_hole   transitivity   eigen\_centrality
  ----- ----- ----------- -------- ---------- ------------- ------------- -------------- -------------------
      2 2            0.00     2.00       2.00          0.00          0.86           1.00                0.01
      3 3            0.00     2.00       2.00          0.00          0.86           1.00                0.01
      4 4            0.00    34.00      34.00      10834.47          0.10           0.13                0.41
      5 5            0.00    27.00      27.00      17858.00          0.11           0.18                0.36
     16 16           0.00    21.00      21.00       1131.35          0.17           0.28                0.35
     44 44           0.00     4.00       4.00      12460.58          0.29           0.50                0.09
    113 113          0.00    15.00      15.00       4601.69          0.19           0.26                0.02
    131 131          0.00    12.00      12.00       3238.34          0.21           0.33                0.02
    250 250          0.00     6.00       6.00         13.20          0.34           0.87                0.15
    259 259          0.00     3.00       3.00          0.00          0.45           1.00                0.02

Community Detection
-------------------

The community detection functions perform different algorithms to
cluster vectors into groups. All functions of **igraph** return a vector
of **membership** which are vertices groups belonging to a community.
Pay attention to the changes in the community structure when the
algorithms change. To get a brief introduction to all the function check
this link [^10]. In order to avoid overlapping between vertices, a neat
solution is to use the **qgraph** package.[^11].

`    `\
` `\
` `\
\
\
`  `\
`  `\
`  `\
\
`  `<span>`){`</span>\
`  `\
`    `\
`      `\
` `\
\
\

![image](figure/unnamed-chunk-40-1){width="\maxwidth"}

![image](figure/unnamed-chunk-40-2){width="\maxwidth"}

![image](figure/unnamed-chunk-40-3){width="\maxwidth"}

![image](figure/unnamed-chunk-40-4){width="\maxwidth"}

![image](figure/unnamed-chunk-40-5){width="\maxwidth"}

![image](figure/unnamed-chunk-40-6){width="\maxwidth"}

![image](figure/unnamed-chunk-40-7){width="\maxwidth"}

![image](figure/unnamed-chunk-40-8){width="\maxwidth"}

[^1]: <https://cran.r-project.org/doc/manuals/r-devel/R-lang.html#Operators>

[^2]: <https://cran.r-project.org/doc/manuals/r-devel/R-lang.html#Objects>

[^3]: <https://stackoverflow.com/questions/5963269/how-to-make-a-great-r-reproducible-example>

[^4]: <https://cran.r-project.org/doc/manuals/r-release/R-lang.html#Introduction>

[^5]: <http://publish.illinois.edu/johnrgallagher/files/2015/10/BaseGraphicsCheatsheet.pdf>

[^6]: <http://cloford.com/resources/colours/500col.htm>

[^7]: <https://www.sci.unich.it/~francesc/teaching/network/eigenvector.html>

[^8]: <https://snap.stanford.edu/data/>

[^9]: <http://networkrepository.com/>

[^10]: <https://stackoverflow.com/questions/9471906/what-are-the-differences-between-community-detection-algorithms-in-igraph/>

[^11]: <https://stackoverflow.com/questions/39290909/igraph-resolving-tight-overlapping-nodes>
