# Package installation
```
install.packages(c("dplyr","ggplot2","ISLR","MASS","glmnet","randomForest","gbm","rpart","boot","ROCR","gridExtra","data.table","pcr","nnet","deepnet","klaR"))
# nnet : neural network
# deepnet : deep learning
# klaR : Bayesian

install.packages("caret",dependencies=c("Depends","Suggests"))
# caret : validate model
```

# Load packages
```
library(dplyr)
library(ggplot2)
library(ISLR)
library(MASS)
library(glmnet)
library(randomForest)
library(gbm)
library(rpart)
library(boot)
library(data.table)
library(ROCR)
library(gridExtra)
```

# Tips
If some data has special characters as a name of parameter, it returns error message.

ex) Error in eval(expr, envir, enclos) : object 'char_freq_;' not found

Then rename the special characters use `make.names()`

ex) new_names <- make.names(names(data),unique = True)
