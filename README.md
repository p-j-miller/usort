# usort
A Port of the Unix sort command to Windows

usort [-cmuv?bdfiMngrtx] [+pos1 [-pos2]] ... [-k keydef] [-o filename] [-T directory] [-y[kmem]] [-z recsz] [filenames]

See usort.pdf (included with each release) for a users manual.

usort has no restictions on line length or sizes of files.

It uses all available processor cores to speed up the sort.

For simple sorts (sorting whole lines aphabetically or with a leading number)  nsort ( https://github.com/p-j-miller/nsort ) is significantly faster, but usort is a lot more flexible.

# Installation
A Windows executable is provided with each release, which can be downloaded and placed anywhere on your path. 
The supplied executable should run on any up to date Windows 11 system. 
If your processor does not meet the requirements for Windows 11 you will need to compile a new executable from the source code.

Note this is a command line program, it does not have a gui.

To compile this program requires a C99 compiler.
There are normally no compiler warnings (or errors) when compiling this program.

To compile the program under Linux try:

 gcc -march=native -Ofast -std=c99 -Wall -o usort usort.c atof.c heapsort.c qsort.c
 
 
 then ./usort -? to run
 [this has been tested with gcc 9.3.0 under Ubuntu 20.04 LTS ] 
 Note as this is a port of the BSD sort command it will be very similar to the sort command already installed.
 
 Under Windows (tested with GCC 15.1.0 compiled for UCRT runtime ): 
 
  gcc -march=native -Ofast -std=c99 -Wall -o nsort.exe usort.c atof.c heapsort.c qsort.c
   
  then usort.exe -? to run
  
  There is a makefile and .dev project file created by dev-c++ which should work as long as a recent c compiler (eg GCC 15.1.0 ) is installed and setup in the dev-c++ IDE.
  
 To sort in numerical order demo1M.csv (supplied and which has 1 million lines) and put the result in sorted1M.csv use:
 
  usort -gv < demo1M.csv >sorted1M.csv
  
  The file sorted1M-ok.csv is the correct result which can be checked by using (for linux use cmp rather than comp):
  
	comp sorted1M.csv  sorted1M-ok.csv
