## 说明
[astyle 网站](http://astyle.sourceforge.net/astyle.html)


>  Artistic Style is a source code indenter, formatter, and beautifier for the C, C++, C++/CLI, Objective‑C, C# and Java programming languages.

## Quick Start
If you have never used Artistic Style, there are several of ways to get started.
One is to run it with no options at all. This will use the default brace style, 4 spaces per indent, and no formatting changes. This will break the braces for one line blocks and will break one line statements. To change this, use the option keep-one-line-blocks and/or keep-one-line-statements described in the Formatting Options section.
> 最常用的也就是一个Tab键变成4个空格的case

## Usage
`astyle [OPTIONS] File1 File2 File3 [...]`  

`astyle [OPTIONS] < Original > Beautified`  
<  和 > 是重定向符号，这种方法一次只能处理一个文件，不支持通配符，也不生成备份文件     



## Option

`--suffix=none  OR  -n  `  
Do not retain a backup of the original file.    

`--recursive  OR  -r  OR  -R  `  
Process subdirectories recursively.    
***

## Case
`astyle -r my_dir/ *.cpp   my_dir/ *.c   my_dir/ *.hpp   my_dir/ *.h  `  
美化my_dir目录及其子目录下所有的cpp，c，hpp，h文件。美化后的文件会覆盖原来的文件；原来的文件会以.orig后缀备份  

`astyle my_dir/fool.cpp my_dir/foo.h  `  
美化指定的两个文件：my_dir/fool.cpp和my_dir/foo.h。美化后的文件会覆盖原来的文件；原来的文件会以.orig后缀备份  

`astyle -n -r my_dir/*.cpp   my_dir/*.c   my_dir/*.hpp   my_dir/*.h  `  
美化my_dir目录及其子目录下所有的cpp，c，hpp，h文件。美化后的文件会覆盖原来的文件；不备份原来的文件  
