# R

## The R Environment

R is an integrated suite of software for data manipulation, calculation, and graphical display. Among other features, R provides:

- An effective data handling and storage facility.
- A suite of operators for calculations on arrays, in particular matrices.
- A large, coherent, and integrated collection of intermediate tools for data analysis.
- Graphical facilities for data analysis and display, either directly at the computer or on hard copy.
- A well-developed, simple, and effective programming language (called 'S') which includes conditionals, loops, user-defined recursive functions, and input/output facilities. (Most of the system-supplied functions are themselves written in the S language.)

The term "environment" characterizes R as a fully planned and coherent system, rather than an incremental collection of specific and inflexible tools, as is often the case with other data analysis software.

R is a platform for newly developing methods of interactive data analysis. It has developed rapidly and has been extended by a large collection of packages. However, most programs written in R are essentially ephemeral, created for a single piece of data analysis.

Although this introduction to R does not mention statistics explicitly, many people use R as a statistical system. It is an environment within which many classical and modern statistical techniques have been implemented.

## Getting Help with Functions and Features

R has an inbuilt help facility similar to the `man` pages in UNIX. To get more information on any specific named function, for example `solve`, use:

```R
help(solve)
```

An alternative is:

```R
?solve
```

For a feature specified by special characters, the argument must be enclosed in double or single quotes, making it a character string. This is also necessary for a few words with syntactic meaning, including `if`, `for`, and `function`:

```R
help("[[")
```

Either form of quote mark may be used to escape the other, as in the string `"It's important"`. The convention is to use double quotes for preference.

On most R installations, help is available in HTML format by running:

```R
help.start()
```

This launches a web browser that allows the help pages to be browsed with hyperlinks. The **Search Engine and Keywords** link is particularly useful as it contains a high-level concept list which searches through available functions.

The `help.search` command (alternatively `??`) allows searching for help in various ways. For example:

```R
??solve
```

Try `?help.search` for details and more examples.

The examples on a help topic can normally be run by:

```R
example(topic)
```

Windows versions of R have other optional help systems; use `?help` for further details.

## R Commands and Case Sensitivity

Commands are separated either by a semicolon (`;`) or by a newline. Elementary commands can be grouped together into one compound expression by braces (`{` and `}`). Comments can be placed almost anywhere; starting with a hash mark (`#`), everything to the end of the line is a comment.

If a command is not complete at the end of a line, R gives a different prompt (by default `+`) on second and subsequent lines and continues to read input until the command is syntactically complete.

R is case-sensitive, so `A` and `a` are different variables.

## Vectors and Assignment

R operates on named data structures. The simplest such structure is the numeric vector, which is an ordered collection of numbers. To set up a vector named `x` consisting of five numbers—10.4, 5.6, 3.1, 6.4, and 21.7—use the R command:

```R
x <- c(10.4, 5.6, 3.1, 6.4, 21.7)
```

This assignment uses the function `c()`, which combines its arguments to form a vector.

Assignment can also be made using the function `assign()`. An equivalent assignment is:

```R
assign("x", c(10.4, 5.6, 3.1, 6.4, 21.7))
```

Assignments can also be made in the other direction using the operator `->`:

```R
c(10.4, 5.6, 3.1, 6.4, 21.7) -> x
```

When an expression is used as a complete command, the value is printed and then discarded. For example:

```R
1 / x
```

This command prints the reciprocals of the five values but does not change `x`.

The assignment:

```R
y <- c(x, 0, x)
```

creates a vector `y` with 11 entries consisting of two copies of `x` with a zero in the middle.

## Vector Arithmetic

Vectors can be used in arithmetic expressions, where operations are performed element by element. Vectors in the same expression need not all be of the same length. If they are not, shorter vectors are recycled as needed until they match the length of the longest vector. Constants are simply repeated.

With the above assignments, the command:

```R
v <- 2 * x + y + 1
```

generates a new vector `v` of length 11.

Mathematical functions like `log`, `exp`, `sin`, `cos`, `tan`, `sqrt`, and others have their usual meanings and operate element-wise on vectors.

Functions like `max` and `min` select the largest and smallest elements of a vector, respectively. The function `range(x)` returns a vector of length two, `c(min(x), max(x))`.

Other useful functions include:

- `length(x)` returns the number of elements in `x`.
- `sum(x)` gives the total of the elements in `x`.
- `prod(x)` gives the product of the elements in `x`.
- `mean(x)` calculates the sample mean.
- `var(x)` calculates the sample variance.

If the argument to `var()` is an `n` by `p` matrix, it returns a `p` by `p` sample covariance matrix treating the rows as independent `p`-variate sample vectors.

The function `sort(x)` returns a vector with the elements of `x` arranged in increasing order. For more flexible sorting, see `order()` or `sort.list()`, which produce a permutation to do the sorting.

`max` and `min` select the largest and smallest values in their arguments, even if they are given several vectors. The parallel maximum and minimum functions `pmax()` and `pmin()` return a vector containing the largest (smallest) element in each position across the input vectors.

For most purposes, it does not matter whether the numbers in a numeric vector are integers, reals, or complex. Internally, calculations are done as double-precision real numbers or double-precision complex numbers if the input data are complex.

To work with complex numbers, supply an explicit complex part. For example:

```R
sqrt(-17 + 0i)
```

The expression `1:30` generates the vector `c(1, 2, ..., 29, 30)`. The function `seq()` is a more general facility for generating sequences.

## Logical Vectors

R allows manipulation of logical quantities. The elements of a logical vector can have the values `TRUE`, `FALSE`, and `NA`.

Logical vectors are generated by conditions. For example:

```R
temp <- x > 13
```

This sets `temp` as a vector of the same length as `x`, containing `FALSE` where the condition is not met and `TRUE` where it is.

## Missing Values

Components of a vector may not be completely known. When a value is "not available" or missing, it can be represented by the special value `NA`. Any operation on an `NA` generally results in `NA`.

The function `is.na(x)` returns a logical vector of the same size as `x`, with `TRUE` for elements that are `NA`.

Example:

```R
z <- c(1:3, NA)
ind <- is.na(z)
```

## Objects, Their Modes, and Attributes

### Intrinsic Attributes: Mode and Length

The entities R operates on are technically known as objects. Examples include vectors of numeric (real) or complex values, vectors of logical values, and vectors of character strings. These are known as "atomic" structures since their components are all of the same type, or mode, namely numeric, complex, logical, character, and raw.

Vectors must have their values all of the same mode. Thus, any given vector must be unambiguously either logical, numeric, complex, character, or raw. (The only apparent exception to this rule is the special value listed as `NA` for quantities not available, but in fact, there are several types of `NA`). Note that a vector can be empty and still have a mode. For example, the empty character string vector is listed as `character(0)` and the empty numeric vector as `numeric(0)`.

R also operates on objects called lists, which are of mode list. These are ordered sequences of objects that individually can be of any mode. Lists are known as "recursive" rather than atomic structures since their components can themselves be lists in their own right. The other recursive structures are those of mode function and expression. Functions are the objects that form part of the R system along with similar user-written functions, which we discuss in some detail later.

By the mode of an object, we mean the basic type of its fundamental constituents. This is a special case of a "property" of an object. Another property of every object is its length. The functions `mode(object)` and `length(object)` can be used to find out the mode and length of any defined structure.

R caters for changes of mode almost anywhere it could be considered sensible to do so (and a few where it might not be). For example, with:

```R
z <- 0:9
```

we could put:

```R
digits <- as.character(z)
```

after which `digits` is the character vector `c("0", "1", "2", ..., "9")`. A further coercion, or change of mode, reconstructs the numerical vector again:

```R
d <- as.integer(digits)
```

Now `d` and `z` are the same.

### Changing the Length of an Object

An "empty" object may still have a mode. For example:

```R
e <- numeric()
```

makes `e` an empty vector structure of mode numeric. Similarly, `character()` is an empty character vector, and so on. Once an object of any size has been created, new components may be added to it simply by giving it an index value outside its previous range. Thus:

```R
e[3] <- 17
```

now makes `e` a vector of length 3 (the first two components of which are at this point both `NA`).

Conversely, to truncate the size of an object requires only an assignment to do so. Hence if `alpha` is an object of length 10, then:

```R
alpha <- alpha[2 * 1:5]
```

makes it an object of length 5 consisting of just the former components with even index. (The old indices are not retained, of course.) We can then retain just the first three values by:

```R
length(alpha) <- 3
```

and vectors can be extended (by missing values) in the same way.

The function `attributes(object)` returns a list of all the non-intrinsic attributes currently defined for that object.

All objects in R have a class, reported by the function `class()`. For simple vectors, this is just the mode, for example, "numeric", "logical", "character", or "list", but "matrix", "array", "factor", and "data.frame" are other possible values. A special attribute known as the class of the object is used to allow for an object-oriented style of programming in R. For example, if an object has class "data.frame", it will be printed in a certain way, the `plot()` function will display it graphically in a certain way, and other so-called generic functions such as `summary()` will react to it as an argument in a way sensitive to its class.

### The Function `tapply()` and Ragged Arrays

To continue the previous example, suppose we have the incomes of the same tax accountants in another vector (in suitably large units of money):

```R
incomes <- c(60, 49, 40, 61, 64, 60, 59, 54, 62, 69, 70, 42, 56,
             61, 61, 61, 58, 51, 48, 65, 49, 49, 41, 48, 52, 46,
             59, 46, 58, 43)
```

To calculate the sample mean income for each state, we can now use the special function `tapply()`:

```R
incmeans <- tapply(incomes, statef, mean)
```

giving a means vector with the components labeled by the levels:

```R
act   nsw    nt   qld    sa   tas   vic    wa 
44.5  57.3  55.5  53.6  55.0  60.5  56.0  52.3
```

The function `tapply()` is used to apply a function, here `mean()`, to each group of components of the first argument, here `incomes`, defined by the levels of the second component, here `statef`.

Suppose further we needed to calculate the standard errors of the state income means. To do this, we need to write an R function to calculate the standard error for any given vector. Since there is a built-in function `var()` to calculate the sample variance, such a function is a very simple one-liner, specified by the assignment:

```R
stdError <- function(x) sqrt(var(x) / length(x))
```

(Writing functions will be considered later in Chapter 10 [Writing your own functions], page 41. Note that R’s built-in function `sd()` is something different.) After this assignment, the standard errors are calculated by:

```R
incster <- tapply(incomes, statef, stdError)
```

and the values calculated are then:

```R
act   nsw    nt   qld    sa   tas   vic    wa 
1.5  4.31  4.5  4.11  2.74  0.5  5.24  2.66
```

The function `tapply()` can also be used to handle more complicated indexing of a vector by multiple categories. For example, we might wish to split the tax accountants by both state and sex. However, in this simple instance (just one factor), what happens can be thought of as follows. The values in the vector are collected into groups corresponding to the distinct entries in the factor. The function is then applied to each of these groups individually. The value is a vector of function results, labeled by the levels attribute of the factor.

The combination of a vector and a labeling factor is an example of what is sometimes called a ragged array, since the subclass sizes are possibly irregular.

The levels of factors are stored in alphabetical order, or in the order they were specified to `factor` if they were specified explicitly. Sometimes the levels will have a natural ordering that we want to record and want our statistical analysis to make use of. The `ordered()` function creates such ordered factors but is otherwise identical to `factor`. For most purposes, the only difference between ordered and unordered factors is that the former are printed showing the ordering of the levels, but the contrasts generated for them in fitting linear models are different.

## Arrays and Matrices

### Arrays

An array can be considered as a multiply subscripted collection of data entries, for example, numeric. R provides simple facilities for creating and handling arrays, particularly matrices.

A dimension vector is a vector of non-negative integers. If its length is `k`, then the array is `k`-dimensional. For example, a matrix is a 2-dimensional array. The dimensions are indexed from one up to the values given in the dimension vector.

A vector can be used by R as an array only if it has a dimension vector as its `dim` attribute. Suppose, for example, `z` is a vector of 1500 elements. The assignment:

```R
dim(z) <- c(3, 5, 100)
```

gives it the `dim` attribute that allows it to be treated as a 3 by 5 by 100 array. Other functions such as `matrix()` and `array()` are available for simpler and more natural-looking assignments.

Arrays can be one-dimensional: such arrays are usually treated in the same way as vectors (including when printing), but the exceptions can cause confusion.

Individual elements of an array may be referenced by giving the name of the array followed by the subscripts in square brackets, separated by commas. More generally, subsections of an array may be specified by giving a sequence of index vectors in place of subscripts; however, if any index position is given an empty index vector, then the full range of that subscript is taken.

### Index Matrices

As well as an index vector in any subscript position, a matrix may be used with a single index matrix to either assign a vector of quantities to an irregular collection of elements in the array or to extract an irregular collection as a vector.

A matrix example makes the process clear. In the case of a doubly indexed array, an index matrix may be given consisting of two columns and as many rows as desired. The entries in the index matrix are the row and column indices for the doubly indexed array.

To extract elements `X[1,3]`, `X[2,2]`, and `X[3,1]` as a vector structure, and replace these entries in the array `X` by zeroes, we need a 3 by 2 subscript array, as in the following example:

```R
x <- array(1:20, dim=c(4,5)) # Generate a 4 by 5 array.
x
# [,1] [,2] [,3] [,4] [,5]
# [1,] 1 5 9 13 17
# [2,] 2 6 10 14 18
# [3,] 3 7 11 15 19
# [4,] 4 8 12 16 20

i <- array(c(1:3,3:1), dim=c(3,2))
i # i is a 3 by 2 index array.
# [,1] [,2]
# [1,] 1 3
# [2,] 2 2
# [3,] 3 1

x[i] # Extract those elements
# [1] 9 6 3

x[i] <- 0 # Replace those elements by zeros.
x
# [,1] [,2] [,3] [,4] [,5]
# [1,] 1 5 0 13 17
# [2,] 2 0 10 14 18
# [3,] 0 7 11 15 19
# [4,] 4 8 12 16 20
```

Negative indices are not allowed in index matrices. `NA` and zero values are allowed: rows in the index matrix containing a zero are ignored, and rows containing an `NA` produce an `NA` in the result.

To construct the incidence matrix, `N` say, we could use:

```R
N <- crossprod(Xb, Xv)
```

However, a simpler direct way of producing this matrix is to use `table()`:

```R
N <- table(blocks, varieties)
```

Index matrices must be numerical: any other form of matrix (e.g., a logical or character matrix) supplied as a matrix is treated as an indexing vector.

### Constructing Arrays

As well as giving a vector structure a `dim` attribute, arrays can be constructed from vectors by the `array` function, which has the form:

```R
Z <- array(data_vector, dim_vector)
```

Arrays may be used in arithmetic expressions, and the result is an array formed by element-by-element operations on the data vector. The `dim` attributes of operands generally need to be the same, and this becomes the dimension vector of the result. So if `A`, `B`, and `C` are all similar arrays, then:

```R
D <- 2 * A * B + C + 1
```

makes `D` a similar array with its data vector being the result of the given element-by-element operations.

### Outer Product of Arrays

An important operation on arrays is the outer product. If `a` and `b` are two numeric arrays, their outer product is an array whose dimension vector is obtained by concatenating their two dimension vectors (order is important), and whose data vector is got by forming all possible products of elements of the data vector of `a` with those of `b`. The outer product is formed by the special operator `%o%`:

```R
ab <- a %o% b
```

An alternative is:

```R
ab <- outer(a, b, "*")
```

The multiplication function can be replaced by an arbitrary function of two variables. For example, if we wished to evaluate the function `f(x, y) = cos(y) / (1 + x^2)` over a regular grid of values with x- and y-coordinates defined by the R vectors `x` and `y` respectively, we could proceed as follows:

```R
f <- function(x, y) cos(y) / (1 + x^2)
z <- outer(x, y, f)
```

### Determinants of 2 by 2 Single-Digit Matrices

As an artificial but interesting example, consider the determinants of 2 by 2 matrices `[a, b; c, d]` where each entry is a non-negative integer in the range 0, 1, ..., 9. The problem is to find the determinants, `ad - bc`, of all possible matrices of this form and represent the frequency with which each value occurs as a high-density plot. This amounts to finding the probability distribution of the determinant if each digit is chosen independently and uniformly at random.

A neat way of doing this uses the `outer()` function twice:

```R
d <- outer(0:9, 0:9)
fr <- table(outer(d, d, "-"))
plot(fr, xlab="Determinant", ylab="Frequency")
```

Notice that `plot()` here uses a histogram-like plot method because it “sees” that `fr` is of class "table".

### Generalized Transpose of an Array

The function `aperm(a, perm)` may be used to permute an array, `a`. The argument `perm` must be a permutation of the integers `{1, ..., k}`, where `k` is the number of subscripts in `a`. The result of the function is an array of the same size as `a` but with the old dimension given by `perm[j]` becoming the new `j-th` dimension. The easiest way to think of this operation is as a generalization of transposition for matrices. Indeed if `A` is a matrix (that is, a doubly subscripted array), then `B` given by:

```R
B <- aperm(A, c(2, 1))
```

is just the transpose of `A`. For this special case, a simpler function `t()` is available, so we could have used `B <- t(A)`.

The functions `nrow(A)` and `ncol(A)` give the number of rows and columns in the matrix `A` respectively.

### Matrix Operations

The operator `%*%` is used for matrix multiplication. An `n by 1` or `1 by n` matrix may, of course, be used as an `n-vector` if in the context such is appropriate. Conversely, vectors that occur in matrix multiplication expressions are automatically promoted either to row or column vectors, whichever is multiplicatively coherent, if possible (although this is not always unambiguously possible).

If, for example, `A` and `B` are square matrices of the same size, then:

```R
A * B
```

is the matrix of element-by-element products and:

```R
A %*% B
```

is the matrix product. If `x` is a vector, then:

```R
x %*% A %*% x
```

is a quadratic form.

The function `crossprod()` forms “cross products”, meaning that `crossprod(X, y)` is the same as `t(X) %*% y` but the operation is more efficient. If the second argument to `crossprod()` is omitted, it is taken to be the same as the first.

The meaning of `diag()` depends on its argument. `diag(v)`, where `v` is a vector, gives a diagonal matrix with elements of the vector as the diagonal entries. On the other hand, `diag(M)`, where `M` is a matrix, gives the vector of main diagonal entries of `M`. This is the same convention as that used for `diag()` in Matlab.

### Solving Linear Equations

Solving linear equations is the inverse of matrix multiplication. When after:

```R
b <- A %*% x
```

only `A` and `b` are given, the vector `x` is the solution of that linear equation system. In R:

```R
solve(A, b)
```

solves the system, returning `x` (up to some accuracy loss). Note that in linear algebra, formally `x = A^(-1) * b` where `A^(-1)` denotes the inverse of `A`, which can be computed by:

```R
solve(A)
```

but rarely is needed. Numerically, it is both inefficient and potentially unstable to compute:

```R
x <- solve(A) %*% b
```

instead of `solve(A, b)`. The quadratic form `x^T * A^(-1) * x` which is used in multivariate computations, should be computed by something like:

```R
x %*% solve(A, x)
```

rather than computing the inverse of `A`.

### Eigenvalues and Eigenvectors

The function `eigen(Sm)` calculates the eigenvalues and eigenvectors of a symmetric matrix `Sm`. The result of this function is a list of two components named `values` and `vectors`. The assignment:

```R
ev <- eigen(Sm)
```

will assign this list to `ev`. Then `ev$values` is the vector of eigenvalues of `Sm` and `ev$vectors` is the matrix of corresponding eigenvectors. Had we only needed the eigenvalues, we could have used the assignment:

```R
evals <- eigen(Sm)$values
```

`evals` now holds the vector of eigenvalues and the second component is discarded. If the expression:

```R
eigen(Sm)
```

is used by itself as a command, the two components are printed, with their names. For large matrices, it is better to avoid computing the eigenvectors if they are not needed by using the expression:

```R
evals <- eigen(Sm, only.values = TRUE)$values
```

### Singular Value Decomposition

`svd(M)` takes an arbitrary matrix argument, `M`, and calculates the singular value decomposition of `M`.

If `M` is in fact square, then it is not hard to see that:

```R
absdetM <- prod(svd(M)$d)
```

calculates the absolute value of the determinant of `M`. If this calculation were needed often with a variety of matrices, it could be defined as an R function:

```R
absdet <- function(M) prod(svd(M)$d)
```

### Least Squares Fitting

`lsfit()` returns a list giving results of a least squares fitting procedure. 

```R
ans <- lsfit(X, y)
```

gives the results of a least squares fit where `y` is the vector of observations and `X` is the design matrix. 

Another closely related function is `qr()` and its allies. Consider the following assignments:

```R
Xplus <- qr(X)
b <- qr.coef(Xplus, y)
fit <- qr.fitted(Xplus, y)
res <- qr.resid(Xplus, y)
```

These compute the orthogonal projection of `y` onto the range of `X` in `fit`, the projection onto the orthogonal complement in `res`, and the coefficient vector for the projection in `b`, that is, `b` is essentially the result of the Matlab ‘backslash’ operator.

### Building Matrices

As we have already seen informally, matrices can be built up from other vectors and matrices by the functions `cbind()` and `rbind()`. Roughly `cbind()` forms matrices by binding together matrices horizontally, or column-wise, and `rbind()` vertically, or row-wise.

It should be noted that whereas `cbind()` and `rbind()` are concatenation functions that respect `dim` attributes, the basic `c()` function does not, but rather clears numeric objects of all `dim` and `dimnames` attributes.

### Frequency Tables from Factors

Recall that a factor defines a partition into groups. Similarly, a pair of factors defines a two-way cross-classification, and so on. The function `table()` allows frequency tables to be calculated from equal-length factors. If there are `k` factor arguments, the result is a `k`-way array of frequencies.


## Lists and Data Frames

### Lists

An R list is an object consisting of an ordered collection of objects known as its components. The components can be of different modes or types, such as numeric vectors, logical values, matrices, complex vectors, character arrays, functions, and more. Here is a simple example of how to create a list:

```R
Lst <- list(name="Fred", wife="Mary", no.children=3, child.ages=c(4,7,9))
```

Components are always numbered and can be referred to by their index. For example, if `Lst` is a list with four components, they can be accessed as `Lst[[1]]`, `Lst[[2]]`, `Lst[[3]]`, and `Lst[[4]]`. If `Lst[[4]]` is a vector, then `Lst[[4]][1]` is its first entry.

The function `length(Lst)` returns the number of top-level components in the list.

Components of lists can also be named, allowing them to be accessed using the `$` operator or by their name in double square brackets:

```R
Lst$name
Lst[["name"]]
```

It is important to distinguish `Lst[[1]]` from `Lst[1]`. The former selects a single element, while the latter returns a sublist containing the first entry.

### Constructing and Modifying Lists

New lists can be created using the `list()` function. For example:

```R
Lst <- list(name_1=object_1, ..., name_m=object_m)
```

This creates a list `Lst` with `m` components, using `object_1` to `object_m` as the components and assigning them the specified names. If names are omitted, the components are numbered.

### Concatenating Lists

The concatenation function `c()` can be used to join lists together:

```R
list.ABC <- c(list.A, list.B, list.C)
```

### Data Frames

A data frame is a list with class "data.frame". The components of a data frame must be vectors (numeric, character, or logical), factors, numeric matrices, lists, or other data frames. All vector structures must have the same length, and matrix structures must have the same number of rows.

### `attach()` and `detach()`

The `$` notation for accessing list components can be cumbersome. The `attach()` function makes the components of a list or data frame temporarily visible as variables:

```R
attach(any.old.list)
```

To detach the data frame or list, use `detach()`:

```R
detach("any.old.list")
```

### Working with Data Frames

A useful convention for working with multiple problems in the same workspace is to gather all variables for a problem in a data frame, attach the data frame when working on the problem, and detach it when done. This keeps the workspace clean and organized.

### Managing the Search Path

The `search()` function shows the current search path, which includes attached data frames and lists:

```R
search()
```

To examine the contents of any position on the search path, use `ls()`:

```R
ls(2)
```

To detach a data frame and confirm its removal from the search path:

```R
detach("lentils")
search()
```

## Reading Data from Files

### The `read.table()` Function

To read an entire data frame directly, the external file should have a specific format:
- The first line of the file should contain the names of the variables in the data frame.
- Each subsequent line should have a row label followed by the values for each variable.

Example:

```R
HousePrice <- read.table("houses.data", header = TRUE)
```

### The `scan()` Function

If the data vectors are of equal length and need to be read in parallel, use the `scan()` function. Suppose there are three vectors: the first of mode character and the remaining two of mode numeric, and the file is `input.dat`. Use `scan()` to read the vectors as a list:

```R
inp <- scan("input.dat", list("", 0, 0))
```

The second argument is a dummy list structure that establishes the mode of the three vectors to be read. The result, held in `inp`, is a list whose components are the three vectors read in. To separate the data items into three separate vectors, use assignments like:

```R
label <- inp[[1]]
x <- inp[[2]]
y <- inp[[3]]
```

## R as a Set of Statistical Tables

R provides functions for various statistical distributions. Here are some common distributions and their corresponding R functions:

| Distribution       | R Name  | Additional Arguments           |
|--------------------|---------|--------------------------------|
| Beta               | `beta`  | `shape1`, `shape2`, `ncp`      |
| Binomial           | `binom` | `size`, `prob`                 |
| Cauchy             | `cauchy`| `location`, `scale`            |
| Chi-squared        | `chisq` | `df`, `ncp`                    |
| Exponential        | `exp`   | `rate`                         |
| F                  | `f`     | `df1`, `df2`, `ncp`            |
| Gamma              | `gamma` | `shape`, `scale`               |
| Geometric          | `geom`  | `prob`                         |
| Hypergeometric     | `hyper` | `m`, `n`, `k`                  |
| Log-normal         | `lnorm` | `meanlog`, `sdlog`             |
| Logistic           | `logis` | `location`, `scale`            |
| Negative Binomial  | `nbinom`| `size`, `prob`                 |
| Normal             | `norm`  | `mean`, `sd`                   |
| Poisson            | `pois`  | `lambda`                       |
| Signed Rank        | `signrank` | `n`                        |
| Student’s t        | `t`     | `df`, `ncp`                    |
| Uniform            | `unif`  | `min`, `max`                   |
| Weibull            | `weibull`| `shape`, `scale`              |
| Wilcoxon           | `wilcox`| `m`, `n`                       |

## Grouped Expressions

R is an expression language, meaning its only command type is a function or expression that returns a result. Even an assignment is an expression whose result is the value assigned, and it may be used wherever any expression may be used. Commands can be grouped together in braces `{expr_1; ...; expr_m}`, where the value of the group is the result of the last expression evaluated.

## Conditional Execution: `if` Statements

R provides a conditional construction of the form:

```R
if (expr_1) expr_2 else expr_3
```

Here, `expr_1` must evaluate to a single logical value, and the result of the entire expression is then evident. The "short-circuit" operators `&&` and `||` are often used as part of the condition in an `if` statement. Whereas `&` and `|` apply element-wise to vectors, `&&` and `||` apply to vectors of length one and only evaluate their second argument if necessary.

There is a vectorized version of the `if/else` construct, the `ifelse` function. This has the form `ifelse(condition, a, b)` and returns a vector of the same length as `condition`, with elements `a[i]` if `condition[i]` is true, otherwise `b[i]` (where `a` and `b` are recycled as necessary).

## Looping Constructs

### `for` Loops

Warning: `for` loops are used in R code much less often than in compiled languages. Code that takes a "whole object" view is likely to be both clearer and faster in R.

### `repeat` and `while` Loops

Other looping facilities include the `repeat` statement and the `while` statement:

```R
repeat {
    expr
    if (condition) break
}

while (condition) {
    expr
}
```

### `break` and `next` Statements

The `break` statement can be used to terminate any loop, possibly abnormally. This is the only way to terminate `repeat` loops. The `next` statement can be used to discontinue one particular cycle and skip to the "next".

Control statements are most often used in connection with functions, which are discussed in detail later.


Writing your own functions
As we have seen informally along the way, the R language allows the user to create objects of
mode function. These are true R functions that are stored in a special internal form and may be
used in further expressions and so on. In the process, the language gains enormously in power,
convenience and elegance, and learning to write useful functions is one of the main ways to make
your use of R comfortable and productive.
It should be emphasized that most of the functions supplied as part of the R system, such
as mean(), var(), postscript() and so on, are themselves written in R and thus do not differ
materially from user written functions.
A function is defined by an assignment of the form
> name <- function(arg_1, arg_2, ...) expression
The expression is an R expression, (usually a grouped expression), that uses the arguments,
arg i, to calculate a value. The value of the expression is the value returned for the function.
A call to the function then usually takes the form name(expr_1, expr_2, ...) and may
occur anywhere a function call is legitimate.
10.1 Simple examples
As a first example, consider a function to calculate the two sample t-statistic, showing “all the
steps”. This is an artificial example, of course, since there are other, simpler ways of achieving
the same end.
The function is defined as follows:
> twosam <- function(y1, y2) {
n1 <- length(y1); n2 <- length(y2)
yb1 <- mean(y1); yb2 <- mean(y2)
s1 <- var(y1); s2 <- var(y2)
s <- ((n1-1)*s1 + (n2-1)*s2)/(n1+n2-2)
tst <- (yb1 - yb2)/sqrt(s*(1/n1 + 1/n2))
tst
}
With this function defined, you could perform two sample t-tests using a call such as
> tstat <- twosam(data$male, data$female); tstat

The example is also given partly as a little puzzle in R programming.
area <- function(f, a, b, eps = 1.0e-06, lim = 10) {
Chapter 10: Writing your own functions 45
fun1 <- function(f, a, b, fa, fb, a0, eps, lim, fun) {
## function ‘fun1’ is only visible inside ‘area’
d <- (a + b)/2
h <- (b - a)/4
fd <- f(d)
a1 <- h * (fa + fd)
a2 <- h * (fd + fb)
if(abs(a0 - a1 - a2) < eps || lim == 0)
return(a1 + a2)
else {
return(fun(f, a, d, fa, fd, a1, eps, lim - 1, fun) +
fun(f, d, b, fd, fb, a2, eps, lim - 1, fun))
}
}
fa <- f(a)
fb <- f(b)
a0 <- ((fa + fb) * (b - a))/2
fun1(f, a, b, fa, fb, a0, eps, lim, fun1)
}

f <- function(x) {
y <- 2*x
print(x)
print(y)
print(z)
}

cube <- function(n) {
sq <- function() n*n
n*sq()
}
## Writing Your Own Functions

As we have seen informally along the way, the R language allows the user to create objects of mode function. These are true R functions that are stored in a special internal form and may be used in further expressions and so on. In the process, the language gains enormously in power, convenience, and elegance, and learning to write useful functions is one of the main ways to make your use of R comfortable and productive.

It should be emphasized that most of the functions supplied as part of the R system, such as `mean()`, `var()`, `postscript()`, and so on, are themselves written in R and thus do not differ materially from user-written functions.

A function is defined by an assignment of the form:

```R
name <- function(arg_1, arg_2, ...) {
    expression
}
```

The expression is an R expression, usually a grouped expression, that uses the arguments to calculate a value. The value of the expression is the value returned for the function. A call to the function then usually takes the form `name(expr_1, expr_2, ...)` and may occur anywhere a function call is legitimate.

### Simple Examples

As a first example, consider a function to calculate the two-sample t-statistic, showing all the steps. This is an artificial example, of course, since there are other, simpler ways of achieving the same end. The function is defined as follows:

```R
twosam <- function(y1, y2) {
    n1 <- length(y1)
    n2 <- length(y2)
    yb1 <- mean(y1)
    yb2 <- mean(y2)
    s1 <- var(y1)
    s2 <- var(y2)
    s <- ((n1 - 1) * s1 + (n2 - 1) * s2) / (n1 + n2 - 2)
    tst <- (yb1 - yb2) / sqrt(s * (1 / n1 + 1 / n2))
    tst
}
```

With this function defined, you could perform two-sample t-tests using a call such as:

```R
tstat <- twosam(data$male, data$female)
tstat
```

### Recursive Functions

R supports recursive functions, which are functions that call themselves. Here is an example of a recursive function to calculate the factorial of a number:

```R
factorial <- function(n) {
    if (n == 0) {
        return(1)
    } else {
        return(n * factorial(n - 1))
    }
}
```

### Anonymous Functions

Anonymous functions are functions that are not assigned to a name. They are often used as arguments to other functions. For example, the `apply()` function can take an anonymous function as an argument:

```R
result <- apply(matrix, 1, function(x) sum(x^2))
```

### Higher-Order Functions

Higher-order functions are functions that take other functions as arguments or return functions as results. An example is the `lapply()` function, which applies a function to each element of a list:

```R
squared <- lapply(list(1, 2, 3, 4), function(x) x^2)
```

### Function Closures

R supports function closures, which are functions that capture the environment in which they were created. This allows the creation of functions with private variables. Here is an example:

```R
makeCounter <- function() {
    count <- 0
    function() {
        count <<- count + 1
        count
    }
}

counter <- makeCounter()
counter() # 1
counter() # 2
```

### Debugging Functions

R provides several tools for debugging functions, including `traceback()`, `debug()`, `browser()`, and `trace()`. For example, to debug a function, you can use:

```R
debug(myFunction)
myFunction(args)
```

This will allow you to step through the function line by line.

### Function Documentation

It is good practice to document your functions using comments and the `roxygen2` package. Here is an example of a documented function:

```R
#' Calculate the mean of a numeric vector
#'
#' This function calculates the mean of a numeric vector, ignoring NA values.
#'
#' @param x A numeric vector.
#' @return The mean of the vector.
#' @examples
#' mean_na(c(1, 2, 3, NA))
mean_na <- function(x) {
    mean(x, na.rm = TRUE)
}
```

Using `roxygen2`, you can generate documentation files from these comments.