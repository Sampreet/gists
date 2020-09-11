# CBits to QBits

> Enter the Quantum Realm!

## Classical Bits

Classical circuits rely on the binary occurances of `0`s and `1`s, known as ***bits***. 
This means that at the machine level, the computer understands only a series of binary inputs. 
These bits act as switches for voltages required to activate certain gates.

All high-level languages have mechanisms to convert the human-readable program to machine language. 
***Compiler*** languages like C, FORTRAN, and Java use a compiler that takes in the complete source code in a single shot and generates an object code. 
Upon checking for errors, the object code a finally translated to a machine-friendly version.
***Interpreter*** languages like Python and MATLAB translate the source code to machine language line by line. 
This makes debugging easier at the cost of slower total execution times.

Also, all characters have a corresponding mapping to a decimal number in the Unicode table, which can be further represented as a sequence of binary digits. 
For example, the letter `'a'` corresponds to `1100001` in binary notation.

```Python
char = 'a'
val_unicode = ord(char)
val_binary = bin(val_unicode)
print(val_binary[2:])
```

## Quantum Bits

In the quantum regime, computation is performed using quantum states called ***qubits***, aka ***qbits***, an acronym for quantum bits. 
Specifically, a qbit is a superposition of the orthonormal basis vectors of a two-level quantum mechanical system. 
The computational basis is defined by eigenstates `0` and `1` and their superposition state `$\psi$`:

![Computational Basis](https://github.com/Sampreet/gists/blob/master/tutorials/languages/python-for-physicists/m08-quantum-computing/images/m08t01-computational-basis.png) 

As such, any state can be 
