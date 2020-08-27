# Getting Started with GNU Octave

> Installation and Basics of the Octave environment.

## Installation

*GNU Octave* is a high-level programming language used for numerical calculations. It is highly compatible with MATLAB and helps in solving linear and nonlinear problems numerically. 

Octave's GUI requires *Java*, a general-purpose programming language that is class-based, object-oriented, and designed to have as few implementation dependencies as possible. Install the latest version of Java binaries from the [official download page](https://www.java.com/en/download/).

Download the latest version of Octave for Windows from the [official download page](https://www.gnu.org/software/octave/download.html) and install!

A complete installation guideline is available in [this link](https://github.com/Sampreet/install-guides/blob/master/languages/octave/octave-setup.md).

## General

Once installation is complete, open the Octave command-line interface (CLI). To hide the ```octave:x``` tag, use:

```matlab
PS1('>> ');
```

To display the manual/guide for any in-built function, for example, the function ```eye()```, use:

```matlab
help eye
```

## Variables and Scalars

### Assignment

```matlab
>> a = 1                    % assignment with output
a =  1
>> b = 2;                   % semicolon supresses output
>> key = 'hello world';     % strings
>> val = pi                 % in-built constants
val =  3.1416
>> who                      % variables in use currently
Variables in the current scope:

a    b    key  val

>> whos                     % details of all variables 
Variables in the current scope:

   Attr Name        Size                     Bytes  Class
   ==== ====        ====                     =====  =====
        a           1x1                          8  double
        b           1x1                          8  double
        key         1x11                        11  char
        val         1x1                          8  double

Total is 14 elements using 35 bytes

>> clear a                  % clear a variable
>> clear                    % clear all variables 
>> % exercise on updating variables
>> a = 1; b = 2, c = b; b = a, c  
b =  2
b =  1        
c =  2
```

### Display

```matlab
>> key = 'hello world'; val = pi;
>> disp(val);               % display output
 3.1416
>> % output formatting using C functions
>> disp(sprintf('%s: %0.2f', key, val));
hello world: 3.14
>> format long              % display more decimal places
>> disp(val)
 3.141592653589793
>> format short             % display less decimal places
>> disp(val)
 3.1416
>> clc                      % clear screen
```

### Arithmetic Operations

```matlab
>> a = 7; b = 2;            
>> a + b                    % addition
ans =  9
>> a - b                    % subtraction
ans =  5
>> a * b                    % multiplication
ans =  14
>> a ^ b                    % power 
ans =  49
>> a / b                    % division 
ans =  3.50000
>> round(a / b)             % rounds off to the nearest integer
ans =  4
>> floor(a / b)             % rounds off to previous integer
ans =  3
>> ceil(a / b)              % rounds off to next integer
ans =  4
>> idivide(a, b, 'fix')     % rounds off the fractional part to zero
ans =  3
>> idivide(a, b, 'floor')   % rounds off to previous integer
ans =  3
>> idivide(a, b, 'ceil')    % rounds off to next integer
ans =  4
>> sqrt(a)                  % square-root function
ans =  2.6458
>> log(a)                   % logarithm function
ans =  1.9459
>> exp(a)                   % exponentiation
ans =  1096.6
>> abs(-3.5)                % absolute value
ans =  3.5000
>> % exercise on BODMAS rule
>> 1 + 2 ^ 3 - 4 + 5 * 6 + 7 / 8 
ans =  35.875
```

### Logical Operations

```matlab
>> a = 1;
>> b = 0;
>> a == b                   % false
ans = 0
>> a ~= b                   % true
ans =  1
>> a && b                   % AND
ans = 0
>> a || b                   % OR 
ans =  1
>> xor(a, b)                % XOR
ans =  1
>> % exercise on bitwise operations
>> xor(1 && 1, xor(0 || 0, 1)) == 1 ~= 1
ans =  1
```

## Vectors and Matrices

### Creation

```matlab
>> % a row vector
>> row = [1, 2, 3]          
row =

   1   2   3

>> % commas can be dropped
>> row = [1 2 3]            
row =

   1   2   3

>> % vector having elements starting from 1 incrementing with 0.5 upto 3
>> row = 1 : 0.5 : 3
row =

    1.0000    1.5000    2.0000    2.5000    3.0000

>> % alternate usage for unit difference
>> row = 1:3                
row =

   1   2   3

>>  % a column vector
>> col = [1; 2; 3]         
col =

   1
   2
   3

>> % size of a vector
>> len = length(col)
len =  3
>> % a matrix
>> Mat = [1 2; 3 4; 5 6]    
Mat =

   1   2
   3   4
   5   6

>> % matrix with all ones and dimensions 4x3
>> Mat = ones(4, 3)         
Mat =

   1   1   1
   1   1   1
   1   1   1
   1   1   1

>> % matrix with all zeros and dimensions 2x2
>> Mat = zeros(2, 2)         
Mat =

   0   0
   0   0

>> % matrix with random numbers between 0 and 1
>> % from a uniform distribution
>> Mat = rand(3, 3)
Mat =

   0.043543   0.028332   0.851590
   0.054690   0.439132   0.826289
   0.293172   0.737989   0.553423

>> % matrix with random numbers between 0 and 1 
>> % from a gaussian/normal distribution with zero mean
>> Mat = randn(3, 2)
Mat =

  -0.49351   0.24057  
   0.21303   0.44122  
  -0.84415   0.17611  

>> % identity matrix of dimension 3x3
>> I = eye(3) 
I =

Diagonal Matrix

   1   0   0
   0   1   0
   0   0   1

>> % flip a matrix about the horizontal axis
>> If = flipud(I)
If =

Permutation Matrix

   0   0   1
   0   1   0
   1   0   0

>> % matrix whose row, column and diagonal elements
>> % add up to the same number with dimensions 3x3
>> Mag = magic(3)
Mag =

   8   1   6
   3   5   7
   4   9   2

>> % dimensions of a matrix
>> dim = size(Mat)
dim =

   3   2

>> % size of 2nd dimension
>> len = size(Mat, 2)
len =  2
>> % size of the largest dimension
>> len = length(Mat)
len =  3
>> % transpose of a matrix
>> col'
ans =

   1   2   3

>> % pseudo-inverse of a matrix
>> % (takes singular matrices into account)
>> Inv = pinv(Mat)
Inv =

  -0.38683   0.53917  -0.82241
   0.61184   1.88568   0.11817

>> % inverse of a matrix
>> Inv = inv(eye(3))
Inv =

Diagonal Matrix

   1   0   0
   0   1   0
   0   0   1

>> % exercise on matrix size
>> length(rand(1, length(size(randn(4, 3)))))
ans =  2
```

### Selection and Concatenation

```matlab
>> Mat = [1 2 3 4; 5 6 7 8; 9 10 11 12];
>> % select element in 2nd row and 2nd column
>> a = Mat(2, 2)
a =  6
>> % select all 3rd row elements
>> row = Mat(3, :)
row =

    9   10   11   12

>> % select 2nd to 4th columns of 2nd and 5th rows
>> A = Mat([1, 3], 2:4)
A =

    2    3    4
   10   11   12

>> % append row to matrix
>> Mat = [Mat; 13 14 15 16]
Mat =

    1    2    3    4
    5    6    7    8
    9   10   11   12
   13   14   15   16

>> % append column to matrix
>> Mat = [Mat, [17; 18; 19; 20]]
Mat =

    1    2    3    4   17
    5    6    7    8   18
    9   10   11   12   19
   13   14   15   16   20

>> % concatenate two matrices column-wise
>> B = [2 3 4; 4 5 6];
>> C = [A B]
C =

    2    3    4    2    3
   10   11   12    4    5

>> % concatenate two matrices row-wise
>> B = [2 3 4; 4 5 6];
>> C = [A; B]
C =

    2    3    4
   10   11   12
    2    3    4
    4    5    6

>> % put all elements in a single column vector
>> col = A(:)
col =

    2
   10
    3
   11
    4
   12

>> % column-wise maximum (default)
>> row = max(A, [], 1)
row =

   10   11   12

>> % row-wise maximum
>> col = max(A, [], 2)
col =

    4
   12

>> % element-wise maximum
>> C = max(A, B)
C =

    2    3    4
   10   11   12

>> % maximum of a matrix
>> [val, ind] = max(A(:))
val =  12
ind =  6
>> % maximum of a vector
>> [val, ind] = max(col)
val =  12
ind =  2
>> % exercise on selection and concatenation
>> Mat = rand(3, 4); A = Mat(1:2, 2:4); Mat = [Mat, A']; length(Mat)
ans =  6
```

### Arithmetic Operations

```matlab
>> A = [1 2; 3 4; 5 6]; B = [7 8; 9 10; 11 12]; C = [13 14; 15 16];
>> % matrix-scalar element-wise addition
>> A + 2
ans =

   3   4
   5   6
   7   8

>> % martix=matrix element-wise addition
>> A + B
ans =

    8   10
   12   14
   16   18

>> % matrix-matrix element-wise subtraction
>> B - A
ans =

   6   6
   6   6
   6   6

>> % matrix-scalar element-wise multiplication
>> A * 2
ans =

    2    4
    6    8
   10   12

>> % multiplication by -1
>> -A
ans =

  -1  -2
  -3  -4
  -5  -6

>> % martix-matrix multiplication
>> A * C
ans =

    43    46
    99   106
   155   166

>> % matrix-matrix element-wise multiplication
>> A .* B
ans =

    7   16
   27   40
   55   72

>> % matrix-scalar element-wise power
>> A .^ 2
ans =

    1    4
    9   16
   25   36

>> % matrix-matrix element-wise power
>> A .^ B
ans =

            1          256
        19683      1048576
     48828125   2176782336

>> % matrix-scalar element-wise division
>> A / 2
ans =

   0.50000   1.00000
   1.50000   2.00000
   2.50000   3.00000

>> % matrix-scalar element-wise reciprocal
>> 2 ./ A
ans =

   2.00000   1.00000
   0.66667   0.50000
   0.40000   0.33333

>> % alternatively
>> A .\ 2
ans =

   2.00000   1.00000
   0.66667   0.50000
   0.40000   0.33333

>> % matrix-matrix element-wise division
>> A ./ B
ans =

   0.14286   0.25000
   0.33333   0.40000
   0.45455   0.50000

>> % matrix-matrix post-multiplication by inverse 
>> A / C
ans =

   7.0000  -6.0000
   6.0000  -5.0000
   5.0000  -4.0000

>> % matrix-matrix pre-multiplication by inverse 
>> A \ B
ans =

  -5.0000  -6.0000
   6.0000   7.0000

>> % matrix column-wise sum (default)
>> sum(A, 1)
ans =

    9   12

>> % matrix row-wise sum
>> sum(A, 2)
ans =

    3
    7
   11

>> % product across the last dimension
>> prod(A)
ans =

   15   48

>> % exercise on opposite diagonal sum
>> A = [1 2 3; 4 5 6; 7 8 9]; sum(sum(A.*flipud(eye(3))))
ans =  15
```

### Logical Operations

```matlab
>> A = [1 2; 3 4; 5 6]; B = [7 8; 9 10; 11 12]; C = [13 14; 15 16];
>> % matrix-scalar element-wise comparison
>> A >= 3
ans =

  0  0
  1  1
  1  1

>> % matrix-matrix element-wise comparison
>> A <= B
ans =

  1  1
  1  1
  1  1

>> % find indices of elements satisfying a given condition
>> % calculated across the first dimension
>> find(A >= 3)
ans =

   2
   3
   5
   6

>> % row and column indices of elements that satisfy a given condition
>> % calculated across the first dimension
>> [r, c] = find(A >= 3)
r =

   2
   3
   2
   3

c =

   1
   1
   2
   2

>> % exercise on logical search
>> A = [2, 3; 5, 7]; find(ceil(A .\ 8) > 3)
ans =  1
```

Next → [File Input/Output in GNU Octave](https://github.com/Sampreet/gists/blob/master/languages/octave/octave-file-io.md)