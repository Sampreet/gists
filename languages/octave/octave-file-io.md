# File Input/Output in GNU Octave

> Reading from and writing into files using the Octave environment.

[Getting Started with GNU Octave](https://github.com/Sampreet/tutorials/blob/master/gists/octave/octave-getting-started.md)

## Workspace

To display the current working directory, use:

```matlab
pwd
```

To navigate to a particular directory, use the following command replacing ```path/to/directory``` by the required path:

```matlab
cd 'path/to/directory'
```

To navigate one directory behind, use:

```matlab
cd ..
```

To output the list of files in the current directory, use:

```matlab
ls
```

## Input-Output

```matlab
>> % load data from file
>> load ('input.dat')
>> % paranthesis and quotations can be dropped
>> % for files without whitespaces in their names
>> load input.dat
>> % save data to file in binary format
>> arr = 1:10:1000;
>> save output.mat arr
>> % save data in readable ASCII format
>> save output.txt arr -ascii
```