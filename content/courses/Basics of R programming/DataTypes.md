---
date: "2021-01-01"
highlight: true
title: Data Types
type: book
weight: 30
---

Learn more about types of data in R.

# Data Types In R

R can be used as a calculator:
```{r}
2+3
```
To find the square root of 4 simply type:
```{r}
sqrt(4)
```
## Sequences of Numbers 
```{r}
1:10
```
It is a good practice to assign names to the vectors:
```{r}
myseq1 <- 1:10
```
Observe that in this case the output is not printed, rather it is stored in the variable name myseq1. If you want to see the content of the variable myVEC1, simply type it:
```{r}
myseq1
```
Another method to create a vector is to use seq function. If you want to get help about the seq function, type ?seq.

**Help**

help.start()   # general help

help(seq)      # help about function seq

?seq           # same thing

apropos("seq") # list all functions containing string seq

example(seq)   # show an example of function seq

Let's generate a vector using seq function:
```{r}
seq(from=0,to=10,by=1)
```
```{r}
seq(from=1,to=10,length=19)
```
Assign a name to the generated vector:
```{r}
myseq2<-seq(1,10,2)
```

seq(from = 1, to = 1, by = ((to - from)/(length.out - 1)),
    length.out = NULL, along.with = NULL, ...)

seq.int(from, to, by, length.out, along.with, ...)

seq_along(along.with)

seq_len(length.out)

```{r}
my_seq <- seq(10,14)
seq_along(along.with = my_seq)
```
```{r}
seq_len(length.out = 7)
```
```{r}
seq.int(from=50,to=56)
```
```{r}
seq.int(from=2,to=6)
```
## Vectors
The third method is to use concatenate c() function:
```{r}
c(1:4)
```
```{r}
myVEC3 <- c(1:6,9,2)
print(myVEC3)
```
```{r}
c("A","B","AB","O")
```
```{r}
myVEC4<-c("A","Biden","AB","O")
```
```{r}
(myVEC4<-c("A","Biden","AB","O"))
```
rep() function can be used to replicate:
```{r}
rep(1,times=4)
```
```{r}
c(rep(0,5),1)
```
```{r}
rep(c(1:5),times=2)
```
```{r}
rep(0:4,each=3)
```
```{r}
rep(0:4,times=2:6)
```
```{r}
## First control, then treatment:
gl(2, 8, labels = c("Control", "Treat"))
```
```{r}
## 20 alternating 1s and 2s
gl(2, 1, 20)
```
```{r}
## alternating pairs of 1s and 2s
gl(2, 2, 20)
```
### Indexing Vectors
The vector elements can be indexed using []. Let's print myVEC4 first and then extract the second element of it:
```{r}
myVEC4
```
```{r}
ind2 <- myVEC4[2]
cat("The answer is",ind2,"as printed.\n")  # \n produces a new line

```
You can extract many elements using vector to define the index of desired elements:
```{r}
myVEC4[c(1,3)]
```
```{r}
myVEC4[-2]                  # the minus means 'without'
```
```{r}
myVEC4[-(3:4)] 
```
### Vector operations
```{r}
1.5 + myseq1
```
```{r}
myVEC2 =c(1,2,3)
2*myVEC2
```
Change an element of a vector: 
```{r}
myVEC2[3]="AAA"
```
Print myVEC2 to see the change:
```{r}
myVEC2
```
```{r}
sqrt(c(1:5))
```
```{r}
c(1:4)^2
```
Check certain conditions using which() function. Note that the output is the index of the elements which satisfy the condition:
```{r}
which(myVEC3<3)
```
The elements itself can be drawn as follows:
```{r}
myVEC3[which(myVEC3<3)]
```
The number of elements which satisfy the condition can be obtained by length() function:
```{r}
length(which(myVEC3<3))
```
```{r}
which.max(myVEC3)
```
### Statistics on vectors:
```{r}
sum(myVEC3)
```
```{r}
mean(myVEC3)
```
```{r}
min(myVEC3)
```
```{r}
sort(myVEC3,decreasing=T)
```
## Arrays
Arrays are the R data objects that can store data in more than two dimensions.

```{r}
array(1:50,dim = c(3,3,1))
```
```{r}
array(1:50,dim = c(3,3,2))
```
```{r}
array(1:50,dim = c(3,3,3))
```
## Matrices
**Matrix creation**
```{r}
#create a matrix
matrix(1:8, nrow=2)
```
```{r}
#create a matrix
matrix(1:9, nrow=3)
```
```{r}
# Elements are arranged sequentially by row.
matrix(c(1:16), nrow = 4, byrow = TRUE)
```
```{r}
M<-matrix(c(1:16), nrow = 4, byrow = FALSE)
M
```
```{r}
M[3,1]
```
```{r}
M[3,3]
```
```{r}
M[4,]
```
```{r}
zmat <- as.matrix(1:6)
print(zmat)
```
```{r}
zmat2 <- as.matrix(c(3,10,5))
print(zmat2)
```
```{r}
a1 <- c(0.7, -0.2)
a2 <- c(-0.3, 0.7)
A <- rbind(a1, a2)
```
```{r}
# Use the solve() function to calculate the inverse.
solve(A)
```
```{r}
m <- cbind(1, 1:7) # the '1' (= shorter vector) is recycled
m
```
```{r}
class(m)
```
```{r}
m1 <- cbind(m, 8:14) # insert a column
m1
```
```{r}
m2 <- cbind(m, 8:14)[, c(1, 3, 2)] # insert a column
m2
```
```{r}
cbind(1:7, diag(3)) # vector is subset -> warning
```
```{r}
cbind(0, rbind(1, 1:3))
```
```{r}
cbind(0, matrix(1, nrow = 0, ncol = 4)) #> Warning (making sense)
```
```{r}
cbind(0, matrix(1, nrow = 2, ncol = 0)) #-> 2 x 1
```
```{r}
## deparse.level
dd <- 10
rbind(1:4, c = 2, "a++" = 10, dd, deparse.level = 0) # middle 2 rownames
```
```{r}
dd <- 10
rbind(1:4, c = 2, "a++" = 10, dd, deparse.level = 1) # 3 rownames (default)
```
```{r}
dd <- 10
vc <- rbind(1:4, c = 2, "a++" = 10, dd, deparse.level = 2) # 4 rownames
```
```{r}
class(vc)
```
Package _matlib_ includes many useful functions.
```{r}
library("matlib")
```
**Inverse**
```{r}
inv(A)
```
**Determinant**
```{r}
det(A)
```
**Transpose**
```{r}
t(A)
```
**Element-wise multiplication**
```{r}
m <- matrix(1:9, nrow=3)
n <- matrix(10:18, nrow=3)
m*n
```
**Matrix multiplication**
```{r}
a1<- c(0,1)
a2<- c(0,0)
A<-rbind(a1,a2)
b1<- c(0,0)
b2<- c(1,0)
B<-rbind(b1,b2)
A%*%B
```
```{r}
B%*%A
```
We can conclude that in matrix multiplication AB is not equal to BA.
```{r}
matrix1 <- matrix(c(1.628, 0.465, 0.698, 1.628), nrow = 2,byrow=TRUE)
matrix2 <- matrix(c(0.4,0.1,0.1,0.3), nrow = 2,byrow=TRUE)
matrix1%*%matrix2
```
**Identity matrix:**
```{r}
diag(4)
```
## Lists
```{r}
L <- list( c(1,5,3), matrix(1:6, nrow=3), c("Hello", "world") )
L
```
```{r}
L[[1]]        # First element of L
```
```{r}
L[[2]][2,1]   # Element [2,1] of the second element of L
```
```{r}
L[[c(3,2)]]   # Recursively: 3. element of L, hereof the 2. element
```
```{r}
List1 <- list(1:4,7:8) # A list of two vectors
```
```{r}
List2 <- list( c("Hello","world"), c(1,5,3) )
```
```{r}
Listconcat <- c(List1, List2)
print(Listconcat)
```
```{r}
Listg <- list( vv=c(1,5,3), mm=matrix(1:6, nrow=3), txtt=c("Hello", "world") )
```
```{r}
Listg$vv
```
```{r}
Listg$mm
```
```{r}
Listg$txtt
```
```{r}
Listg$mm[2,1]          # L$m is a matrix which can be referenced with []
```
```{r}
Listg$txtt[2]
```
```{r}
Listg[[1]]
```
## Data frames
```{r}
xx <- data.frame(I = rep(0,2))
xx
```
```{r}
vs <- cbind(xx, X = rbind(a = 1, b = 1:3))   # named differently
vs
```
```{r}
class(vs)
```
Another example:
```{r}
## cheap row names:
b0 <- gl(3,4, labels=letters[1:3])
b0
```
```{r}
bf <- setNames(b0, paste0("o", seq_along(b0)))
bf
```
```{r}
df  <- data.frame(a = 1, B = b0, f = gl(4,3))
df
```

```{r}
df. <- data.frame(a = 1, B = bf, f = gl(4,3))
df.
```
```{r}
new <- data.frame(a = 8, B ="B", f = "1")
new
```
```{r}
(df1  <- rbind(df , new))
```
```{r}
(df.1 <- rbind(df., new))
```








Let's try another example:
```{r}
names = c("Hans", "Caro", "Lars", "Ines", "Samira", "Peter", "Sarah") 
gender = c("male", "female", "male", "female", "female", "male", "female") 
department = c("IT", "IR", "TRD", "IR", "IT", "TRD", "SALES")
salary = c(8000,5500,7400,6400,5800,6100,5900)
ITmanagers <- data.frame(names,gender,department,salary)
ITmanagers
```
```{r}
str(ITmanagers)
```
```{r}
summary(ITmanagers)
```
```{r}
head(ITmanagers)
```
```{r}
ITmanagers$names
```
```{r}
ITmanagers$salary
```
```{r}
mean(ITmanagers$salary)
```
```{r}
data.frame(ITmanagers$names,ITmanagers$salary)
```
### Slicing data frames
```{r}
ITmanagers$gender[2]
```
```{r}
ITmanagers[,1]
```
```{r}
ITmanagers[1,]
```
```{r}
index1 <- ITmanagers[["department"]]=="IT"
ITmanagers[index1,]
```
```{r}
index2 <- ITmanagers[["department"]]=="HR"
ITmanagers[index2,]
```
```{r}
index3 <- ITmanagers[["gender"]]=="female"
ITmanagers[index3,]
```
```{r}
index4 <- ITmanagers[["salary"]] > 2000
ITmanagers[index4,]
```
```{r}
groupIT <- subset(ITmanagers,department=="IT")
print(groupIT)
```
```{r}
groupIT$salary
```
```{r}
subset(ITmanagers,department %in% c("IT","HR"))
```
```{r}
SALESIRgroup <- subset(ITmanagers, department %in% c("SALES","IR"))
SALESIRgroup$salary
```
```{r}
mean(SALESIRgroup$salary)
```
```{r}
notIRgroup <- subset(ITmanagers,department != "IR")
print(notIRgroup)
```
### Classifying the data frames
based on a specific feature can be done using split() function:
```{r}
depCLASSES <- split(ITmanagers, ITmanagers$department)
print(depCLASSES)
```
```{r}
typeof(depCLASSES)
```
```{r}
class(depCLASSES)
```
```{r}
depCLASSES$TRD
```
```{r}
genCLASSES <- split(ITmanagers, ITmanagers$gender)
print(genCLASSES)
```
### Adding a new feature
```{r}
ITmanagers$age = c(34,39,42,46,52,19,52)
ITmanagers
```
```{r}
nationality <- c("US","China","Japan","US","Iran","US","Brazil")
ITmanagers <- cbind(ITmanagers,nationality)
ITmanagers
```
```{r}
# Create vector objects.
city <- c("Tampa","Seattle","Hartford","Denver",NA,NA,NA)
state <- c("FL","WA","CT","CO",NA,NA,NA)
zipcode <- c(33602,98104,06161,80294,NA,NA,NA)
addresses <- cbind(city,state,zipcode)
## Add addresses to the data frame
ITmanagers <- cbind(ITmanagers,addresses)
ITmanagers
```
Adding new entries can be done by creating new data frames and binding them:
```{r}
# Create the second data frame
ITnewdata <- 	data.frame(
   names = c("Rasmi","Pranab","Tusar"),
   gender = c("female","male","female"),
   department = c("IT","OP","FI"),
   salary = c(5578,7422,6432), 
   age = c(46,52,52),
   nationality = c("IT","OP","FI"),
   city = c("IT","OP","FI"),
   state = c("IT","OP","FI"),
   zipcode = c("IT","OP","FI")
)

# Bind the two data frames.
ITmanagersFINAL <- rbind(ITmanagers,ITnewdata)
print(ITmanagersFINAL)
```
