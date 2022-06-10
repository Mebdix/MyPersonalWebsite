---
date: "2021-01-01"
highlight: true
title: File Management
type: book
weight: 30
---


## Notes about asking help


help.start()

help.start() starts and displays a hypertext based version of R’s online documentation in your default browser that provides links to locally installed versions of the R manuals, a listing of your currently installed packages and other documentation resources.


### Asking For Help
 - help()  
 - ?
 - help(rlm, package="MASS")
 - help('?') 
 - help(package="MASS") 
 - help(rlm, package="MASS")
 - example(lm).

### Vignettes and Code Demonstrations: 

 - browseVignettes()
 - browseVignettes(package="MASS")  
 - vignette() 
 - vignette("timedep") 
 - demo()
 - demo(package="stats")


### apropos()

The apropos() function searches for objects, including functions, directly accessible in the current R session that have names that include a specified character string. 

 - apropos(read)

### R Sites Search

- help.search() 
- ??
- RSiteSearch()





## Library Management

Get library locations containing R packages:
```{r}
.libPaths()
```
Get the list of all the packages installed:
```{r}
library()
```
Get all packages currently loaded in the R environment
```{r}
search()
```