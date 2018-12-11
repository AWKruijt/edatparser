# edat/edat2 txt parser


## AW's version with main functions called edatR() and eMergeR():
This is an adjusted version of the edat 2 txt parser created by Ahebrank (original readme text below). 

The main changes are the addition of an emerger() function to read/parse/merge multiple .txt. files at once, and a replaced text file read and parse routine named edatR() (adjusted from Ahebrank's edat() function). The adjusted version allows .txt files containing symbols and trials nested several levels deep to be parsed too. 

update December 2018: fixed an error due to plyr not playing nice with variablenames that have no name - not sure how long this problem had been around and whether it affected other people's files too but it is fixed now (for my datafiles at least. 

### Ahebranks' original edat() readme:
This is a package for reading in [E-Prime](http://www.pstnet.com/eprime.cfm) data files (well, the txt recovery files generated by E-Prime scripts during an experiment). It's for those needing to analyze large batches of edats, don't have access to PST's data utility E-DataAid, or don't have Windows. As far as I know, PST does not make the format of the binary .edat/.edat2 files publicly available, so this is all just guesswork.

Inspiration for this utility and credit for early versions of the code go to [canlab's MATLAB implementation](https://github.com/canlab/CanlabCore/blob/master/Misc_utilities/parse_edat_txt.m), developed in 2010 by Joe Wielgosz.

Use at your own risk! I have a limited number of test cases, most of which were produced by the same E-Prime programmer (me!).  Please use the issue tracker to report bugs or submit test cases.

## Getting Started

The easiest way is to use devtools' `install_github` function.

### One-time install

```
> install.packages('devtools')
> devtools::install_github('AWKruijt/eMergeR')
```

### Using the merger and single file parser:

```
library('emerger')

#parse and merge all .txt files in current working directory:
df <- emerger()
df <- as.data.frame(df)

#parse and merge merge all .txt files in the folder 'deeptest' that sits within the current wd:
df <- eMergeR(dir = "deeptest") 
df <- as.data.frame(df)

#parse and merge merge all .txt files for which filename includes "sumbol" that sit in the folder 'deeptest' within the current wd:
df <- eMergeR(filenameContains = "symbol", dir = "deeptest")
df <- as.data.frame(df)


# parse single file:
e <- edatR('Flanker-1001-1.txt')
dat <- as.data.frame(e)

dim(dat)
head(dat)
```
