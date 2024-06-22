## MINTX features
### Linear Algebra

- Grammar; single column and row matrix
- **Element-wise** Operations: Performing element-wise operations (e.g., addition, multiplication) between two matrices of the same size. Element-wise operations involve performing arithmetic operations (addition, subtraction, multiplication, division) on corresponding elements of two matrices. These operations can be implemented using simple loops that iterate over the elements of the matrices and perform the desired arithmetic operations using 32-bit integer arithmetic.
- Matrix **Addition**: Adding corresponding elements of two matrices to produce a new matrix.
- Matrix **Subtraction**: Subtracting corresponding elements of two matrices to produce a new matrix.
- Scalar **Multiplication**: Multiplying every element of a matrix by a scalar value.
- Matrix **Multiplication**: Multiplying two matrices to produce a new matrix.
- Matrix **Multiplication**: Multiplying two matrices to produce a dot product
- **Identity matrix**, An identity matrix is a special type of square matrix in which all the elements of the principal diagonal are ones and all other elements are zeros.
- Matrix **Inversion**, Division: Finding the inverse of a matrix, which is a matrix that, when multiplied with the original matrix, yields the identity matrix.
- **Transpose**: Computing the transpose of a matrix, which involves swapping its rows and columns.
In terms of 32-bit integer operations, transposing a matrix involves swapping the elements across the main diagonal of the matrix. This can be done efficiently using nested loops to iterate over the rows and columns of the matrix, swapping each element with its corresponding element across the diagonal.
- **Determinant**: Calculating the determinant of a square matrix, which is a scalar value that represents certain properties of the matrix.
   Computing the determinant of a matrix involves various arithmetic operations such as addition, subtraction, and multiplication of matrix elements. Using methods like expansion by minors or Gaussian elimination, each determinant computation involves a series of arithmetic operations that can be performed using 32-bit integer arithmetic.
- **Trace**: Calculating the trace of a square matrix, which is the sum of the elements on its main diagonal.
The trace of a matrix is the sum of its diagonal elements. In terms of 32-bit integer operations, calculating the trace involves adding the diagonal elements of the matrix using a simple loop that iterates over the diagonal elements and accumulates their values.
- **Eigenvalues and Eigenvectors**: Finding the eigenvalues and eigenvectors of a square matrix, which represent certain properties of the matrix under linear transformations. Finding the eigenvalues and eigenvectors of a matrix typically involves solving a characteristic equation or using iterative methods such as the power iteration algorithm. These methods involve repeated multiplication of the matrix by a vector and can be implemented using 32-bit integer arithmetic.
- **Rank**: Determining the rank of a matrix, which is the maximum number of linearly independent rows or columns in the matrix. Determining the rank of a matrix involves performing Gaussian elimination to reduce the matrix to row-echelon form and counting the number of non-zero rows. This process consists of elementary row operations such as addition, subtraction, and multiplication, which can be carried out using 32-bit integer arithmetic.
- Matrix **Norms**: Calculating various norms (e.g., Frobenius norm, spectral norm) of a matrix, which measure the magnitude of the matrix. Calculating matrix norms such as the Frobenius norm or spectral norm involves computing the square root of the sum of squares of the matrix elements or finding the maximum singular value, respectively. These computations can be performed using 32-bit integer arithmetic combined with square root operations.
- Matrix **Decompositions**: Decomposing a matrix into simpler components (e.g., LU decomposition, QR decomposition, Singular Value Decomposition) to analyze its properties or solve linear equations efficiently. Matrix decompositions like LU decomposition, QR decomposition, or Singular Value Decomposition (SVD) involve various operations such as matrix multiplication, factorization, and solving systems of linear equations. These operations can be implemented using 32-bit integer arithmetic.
- Matrix **Exponentiation**: Raising a square matrix to a positive integer power, which involves multiplying the matrix by itself a certain number of times. Raising a matrix to a positive integer power involves performing repeated matrix multiplications. Using techniques like exponentiation by squaring, this operation can be carried out efficiently using 32-bit integer arithmetic.
- Solving **Linear Equations**: Using matrices to represent systems of linear equations and solving them using techniques like Gaussian elimination or matrix inversion. Solving systems of linear equations involves performing matrix operations such as inversion, multiplication, and factorization. These operations can be implemented using 32-bit integer arithmetic along with techniques like Gaussian elimination or matrix factorization algorithms
- more
     

# Grammar  
```
> 12
> .   //its on the stack
> 12
> .  // again
> 0
> 12 a!  // 12 stored in a, does not make it to stack
> .      // show
0        // nothing on stack     
> a@.    
3254    // mem
> a.
12  
```
## row vector
```
> [1 2 3]
> .
3233         // stored in memlocation
> [1 2 3]a!   // enter and store in a
> .
0   // nothing
> a@.
3422         //location
> a.            // recall, its finds an array          
1 2 3            
> a[0-2]?.      // show range 0-2, it knows its a row
1 2 3
> a0?.          // whats in location 0
1 
> a 3 +  // result in matrix stack
> ctr.
4 5 6
>
> [1]?.   //show whats in 1
er        // error
> a[1]?.  // need a variable to show
5
>
> a 2 *
> ctr.
2 4 6
> a[2]?.
6
>
```
In MINTX, rows use `[ ]` and columns use `\[ ]`.
In MINT row arrays use \[ ] 16 bit `words` only and 8 bit use `\` buts its redundant as it occurs in in 16 bits 0000000011111111
The use of ( ) is strictly for loops so will not occur in matrix commands.


## column vector  
use `\` and `;` is allowed as well
```
> \[1 2 3] a!
> a.
3232      // mem location
> a.
1
2
3
> [1 2 3 ;]a!
> a.
1
2
3
>
> // show individual, need mem location each time
> a0?. a1?. a2?.    
1
2
3
>
> a[0-2]?.  // `-` show range
1
2
3    
> a[1-2]?. // show part range
2
3
> a[2-0]?.  
er        // dimension error unless we stored it as [1 2 3]a!
> a.  
1
2
3
>
> a 2 * b!
> b.
2
4
6
>
> b[0-2]?.
2
4
6
>
```

## zeros 
```
> 0[4] a! 
> a.
0
0
0
0
>
> 0\[4] a!
> a.
0 0 0 0
>
> 3[4] a! 
> a.
3 3 3 3
>
> 9\[4] a! 
> a.
9
9
9
9
> 
```
## n x n martrix

\[nx] mix error, no column for n x n

```
> [4x]a!       // default fill 4x4 with 0's
> a.
0 0 0 0
0 0 0 0
0 0 0 0
0 0 0 0
>
> // spec a number to fill
> 2[3x]a!
> a.
2 2 2
2 2 2
2 2 2
>
> /r[3x]a!   // random int fill
> a.
2211  5004  2311
12    3333  7123
4454  11134 7003
> -12[0,1]a!   // change 12 to -12, its still in matrix stack
> a.
2211  5004  2311
-12    3333  7123
4454  11134 7003
>
> 
> a[1,1]?.          // show location
> 3333
> 
> /r[3x]a!  //save it 
> a.  // diff rand
1 4 0
9 4 5
4 2 6
> 9[2,2]a!
> a.
1 4 0
9 4 5
4 2 9
> a[2,1]?.
5                   
> a[0-0 1-1]?.   // show a range, a[0-0 ; 1-1]?. will work
1 4
9 4
> 
> // enter another way
> [1 2 3 ; 4 5 6 ; 7 8 9] a!
> a.
1 2 3
4 5 6 
7 8 9
>

// if we use pi we move into fixed point decimal and that changes everything
>
> pi a *   //  π * = stack 
> .
0
> // does not work coz its in matrix stack
> ctr.
69.120 103.670 138.230 172.790
69.120 103.670 138.230 172.790
>a!
>
> a 2 -  
> ctr.
67.120 101.670 136.230 170.790
67.120 101.670 136.230 170.790
>
> [2 4 5 6 7]a! 
> a 3.1 - b! 
> ctr.
1.1000 -0.9000 -1.9000 -2.9000 -3.9000 
> b.
1.1000 -0.9000 -1.9000 -2.9000 -3.9000 

>
> // complex
> 3-4i
> . 
3-4i 
> 2 - . 
1-4i
> 
> [1 2 ; 3 4] a!
> ctr.
1 2 
3 4 
> [2 3 ; 6 7] b!
> ctr.
2 3 
6 7 
> a b -  
> ctr.
-1 -1 
-3 -3
> c! 
> b.
2 3
6 7
> // same 
```
### reshaping

```
> /r[3x]a!  //save it 
a.
1 7 8
5 7 1
4 7 7
> a /p[2x3] a!
> a.
1 7
8 5
7 1
> // 1 4 7 7 are truncated
>
> /r[3x]a!
> a.
3 5 2
5 8 9
6 4 6
> a /p[4x4] a!
> a.
3 5 2 5
8 9 6 4
6 3 5 2
> // the last 3 5 2 are back filled from the begging numbers
>
```


## Multiplication

### Elementwise-product

```
> 2 a! 3 b! // scalar vector 1x1
> a b * .
6
>
> // scalar times row vector
> 3 [2 4 5 6 7] * . 
6 12 15 18 21 
>


> // scalar times a column vector
> 3.1 [2 ; 4 ; 5 ; 6 ; 7] *
> ctr.
6.2000
12.400
15.500
18.600
21.700
>


> // 2x2 
> [1 2 ; 3 4] a!
> [5 6 ; 7 8] b! 
> a b * c! // store answer 
> ctr. // can show last operation
> c ctr.   // call c if u did other things 
5  12
21 32
​>​

> // 2x2 i
>
> [1i 2 ; 3 4] a!
> [5 6 ; 7 8] b!
> a b * c!
> ctr.
14+5i	16+6i
43    50
>

> /r[4x4] a!  //fill random
> ctr.
7 8 1 0
6 0 6 8
1 3 5 3
7 6 9 8
>
> /r[4x4] b!
> ctr.
3 6 4 8
6 6 3 7
1 3 2 6
9 8 3 1


> a b * c! 
> ctr.
70 93 54 118
96	118 60 92
53 63 32 62
138 169 88 160
>
```




##  transpose a matrix

```
> [4x4] a!
> ctr.
1 2 3 4
5 6 7 8
9 10 11 12
13 14 15 16
>
    > a -t // transpose a using the -t command
> ctr.
1 5 9 13
2 6 10 14
3 7 11 15
4 8 12 16
>
```

## Determinant
- for 2x2 we use det(A)=ad−bc
- for 3x3 we use det(A)=aei+bfg+cdh−ceg−bdi−afh
- https://en.wikipedia.org/wiki/Determinant

```
> [12  32 ; 33 17] a!
> a -d
-852

> //3x3
> [ 1 2 3 ; 4 5 6 ; 7 8 9] a!
> a -d
0
>

```

lets try from complex forms
```
> [12i  32 ; 33 17] a!
> a -d
-1056+204i
>
> [12  32i ; 33 17] a!
> a -d
204-1056i
> [12i  32i ; 33 17] a!
> a -d
-852i
> [12i  32 ; 33 17i] a!
> a -d
-1260
>
```



## Loops
 




