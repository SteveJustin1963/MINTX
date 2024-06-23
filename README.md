## MINTX  
MINTX is a build on MINT with modifications



## labels

### 1. Single Lowercase Letters: `a` to `z`
There are 26 letters in the English alphabet.

Total: \( 26 \)

### 2. Lowercase Letter Followed by a Single Digit: `a0` to `a9`, `b0` to `b9`, ..., `z0` to `z9`
For each of the 26 letters, there are 10 possible digits (0-9).

Total: \( 26 * 10 = 260 \)

### 3. Two Lowercase Letters: `aa`, `ab`, ..., `az`, `ba`, ..., `zz`
Each of the two positions can be any of the 26 letters.

Total: \( 26 * 26 = 676 \)

### Overall Total
To find the total number of combinations for all specified formats, sum the totals from each format:

\[
26 + 260 + 676  = 962 combinations
\]

## Grammar  
- error return `er`
- n places number on stack
- . removes from stack and displays to default ie terminal
- ! stores 
- @ retrieves memory location of label
- `label` reference contents of it 

```
> 12
>
> .   
> 12
> .  
> 0
> 12 a!  
> .      
0             
> a@.    
3254    // mem
> a.
12
> a 2 * .
24
>
```



### Linear Algebra - expansion on MINT arrays

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
- **Trace**: Calculating the trace of a square matrix, which is the sum of the elements on its main diagonal⍺
The trace of a matrix is the sum of its diagonal elements. In terms of 32-bit integer operations, calculating the trace involves adding the diagonal elements of the matrix using a simple loop that iterates over the diagonal elements and accumulates their values.
- **Eigenvalues and Eigenvectors**: Finding the eigenvalues and eigenvectors of a square matrix, which represent certain properties of the matrix under linear transformations. Finding the eigenvalues and eigenvectors of a matrix typically involves solving a characteristic equation or using iterative methods such as the power iteration algorithm. These methods involve repeated multiplication of the matrix by a vector and can be implemented using 32-bit integer arithmetic.
- **Rank**: Determining the rank of a matrix, which is the maximum number of linearly independent rows or columns in the matrix. Determining the rank of a matrix involves performing Gaussian elimination to reduce the matrix to row-echelon form and counting the number of non-zero rows. This process consists of elementary row operations such as addition, subtraction, and multiplication, which can be carried out using 32-bit integer arithmetic.
- Matrix **Norms**: Calculating various norms (e.g., Frobenius norm, spectral norm) of a matrix, which measure the magnitude of the matrix. Calculating matrix norms such as the Frobenius norm or spectral norm involves computing the square root of the sum of squares of the matrix elements or finding the maximum singular value, respectively. These computations can be performed using 32-bit integer arithmetic combined with square root operations.
- Matrix **Decompositions**: Decomposing a matrix into simpler components (e.g., LU decomposition, QR decomposition, Singular Value Decomposition) to analyse its properties or solve linear equations efficiently. Matrix decompositions like LU decomposition, QR decomposition, or Singular Value Decomposition (SVD) involve various operations such as matrix multiplication, factorisation, and solving systems of linear equations. These operations can be implemented using 32-bit integer arithmetic.
- Matrix **Exponentiation**: Raising a square matrix to a positive integer power, which involves multiplying the matrix by itself a certain number of times. Raising a matrix to a positive integer power involves performing repeated matrix multiplications. Using techniques like exponentiation by squaring, this operation can be carried out efficiently using 32-bit integer arithmetic.
- Solving **Linear Equations**: Using matrices to represent systems of linear equations and solving them using techniques like Gaussian elimination or matrix inversion. Solving systems of linear equations involves performing matrix operations such as inversion, multiplication, and factorization. These operations can be implemented using 32-bit integer arithmetic along with techniques like Gaussian elimination or matrix factorisation algorithms
- more
     




## Arrays
-  [ ] for arrays, ( ) for loops
- use numbers n
- use labels a - z
- nesting [   [ ]  ] , [  () ], (  () ), etc
- 

## row vector

```
[n n n ..] places numbers on array stack and puts mem address on stack
[ n n n ..] a! store in a-z with ! 
a@ retrieves memory location, a@. shows it
a retrieves contents of address
a. show whole array, b c d e .... z
n[row-col] places n into row-col
use ? to find an number in the array n[row-col]?. 
[3 4] a!
a 3*  multiply array by 3

> [1 2 3]
> .
3233         // stored in mem location
> [1 2 3]a!   // save mem in a
> .
0  // correct
> a@.
3233         //location
> a.         // show array          
1 2 3
> 
> a[0-2].
1 2 3
>
> a[0].    
1
> a[1].
2
> a[3] + a!
> a.
4 5 6
>
> a?.
er
> a[1].
er
> [1]?.
er        
> a[1]?.  // use proper syntax
5
>
> a 2 * a!
> a.
8 10 12
> a[2]?.
12
>

```
- MINTX array rows use `[ ]` and columns use `\[ ]`.  
- MINT array row use [ ] as 16 bit `words`
- for 8 bit use \[ ] buts its redundant 16 bits 0000000011111111 includes it 
- use ( ) strictly for loops not in array matrix commands


## column vector  
use `\`  or `;`

```
> \[1 2 3] a!
> a@.
3232      // mem location
> a.
1
2
3
> [1 2 3 ;]a!  //  `;` allowed and matrix [n..; n..; n..; ..]
> a.
1
2
3
>
> // need label each time
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
er        // dimension error unless we stored it as row of [1 2 3]a! 
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
> b[0-2]?.  or b.
2
4
6
>
```

### Reshaping
- shorter / longer vector 1 dimension
- shorter / longer matrix 2 dimension, change nxm or nxn
- order, +ve, -ve
- 


```
> /r[3x]a! 
a.
1 7 8
5 7 1
4 7 7
> /p a[2x3] a!  //
> a.
1 7 8
5 7 1
4 7 7
>
>
> /r[3x]a!
> a.
3 5 2
5 8 9
6 4 6
> a /p[4x4] a!   // expanding cloning
> a.
3 5 2 2
5 8 9 9
6 4 6 6
6 4 6 6
>
```

## zeros 
```
> 0[4] a!  
> a.
0 0 0 0
>
> 0\[4]a!  // or 0[4;]a!   
> a.
0
0
0
0
>
> 3[4] a! 
> a.
3 3 3 3
>
> 9\[4]a! 
> a.
9
9
9
9
> 
```
## n x n matrix
```
- n can = m 
- no n or m = 0
- x for making nxm matrix
- , for finding n,m inserting 
- for n[nx] put n into n x n square
- for n[nxm] put n into n x m rectangle 
- \[nx] or \[nxm] = er 
- n[n,m] put n into n,m location 


> [4x]a!      
> a.
0 0 0 0
0 0 0 0
0 0 0 0
0 0 0 0
>
> 2[3x]a!
> a.
2 2 2
2 2 2
2 2 2
>
> /r[3x]a!   // `/r` random integer 
> a.
2211  5004  2311
12    3333  7123
4454  11134 7003
> /rd[2x]a!   //  `/rd` random 3dec place
22.110 5.004 
45.100 99.999
>
> -12[0,1]a!   // change 12 to -12, its still in matrix stack xxx
> a.
2211  5004  2311
-12    3333  7123
4454  11134 7003
>
> a[1,1]?.         
> 3333
> 
> 1[3x]a!  // fill with 1's
> a /r * a! a.
1 4 100
9 4 5
4 2 6
> 9[2,2]a!
> a.
1 4 100
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

// MINTX pi uses 3 dec place floating-point IEEE 754
>
> pi a * a!
> a.
69.120 103.670 138.230 172.790
69.120 103.670 138.230 172.790
>
> a 2 - a!  
> a.
67.120 101.670 136.230 170.790
67.120 101.670 136.230 170.790
>
> [2 4 5 6 7]a! 
> a 3.1 - a! 
> a.
1.1000 -0.9000 -1.9000 -2.9000 -3.9000 
```


### Complex numbers

```
// stack
> 3-4i
> . 
3-4i 
> 2 - . 
1-4i
> 1i - .
1-5i
>
// arrays
> /ri [2x] a!  // /`ri` random imaginary also /rid for random imaginary dec 
> a.
1+3i 2-1i 
3 4+4i 
> [2 3 ; 6 7] b!
> b.
2 3
6 7
> a b - c! c.
-1+3i -1-i
-3, -3+4i
> a b + c! c.
3+3i 5-i
9 11+4i
> a b * c! c.
4 17+2i
30+24i 37+28i
>

```
### fractional integers

```
> /r[3x]a!
> a.
>
1 6 5
8 7 3
3 8 3
> [1 1/2 3 ; 4/5 6 7/8 ; 9 11/16 4/3 ] b!
> a b + c! c.
2 2/3 4
9/5 7 15/8
10 27/16 7/3
> ​a b - c! c.
0 -1/2 2
-1/5 5 -1/8
8 -5/16 1/3
> ​a b * c! c.
9/2 9/2 9/2
307/40 307/40 307/40
529/48 529/48 529/48
> ​a b / c! c.
er
>

```
### Nested arrays

Arrays can be nested inside one another. This code accesses the second item of the first array with 1?. It then accesses the first item of the inner array with 0? and prints the result (which is 2).

> [1 [2 3]] a! 
> a1a0.  // find second then first
> 2
> 



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
3 6
 4 8
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
 




