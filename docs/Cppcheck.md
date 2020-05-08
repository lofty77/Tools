
> Cppcheck is an analysis tool for C/C++ code. Unlike C/C++ compilers and many other analysis tools, it
> doesn't detect syntax errors. Instead, Cppcheck detects the types of bugs that the compilers normally fail
> to detect. 

http://cppcheck.sourceforge.net/

##  Checking a file
If you save that into file1.c and execute following command to check the fiel1.c:  

`cppcheck file1.c`


## Checking all files in a folder
Normally a program has many source files. And you want to check them all. Cppcheck can check all source files in a directory:  

`cppcheck path`

If "path" is a folder then cppcheck will recursively check all source files in this folder. 

## Excluding a file or folder from checking
The second option is to use -i, with it you specify files or paths to ignore. With this command no files in
src/c are checked:  

`cppcheck -i src/c src`

## Saving results in file

Many times you will want to save the results in a file. You can use the normal shell redirection for piping
error output to a file.

`cppcheck file1.c 2> err.txt`
