# lrarning



1.https://cran.r-project.org/web/packages/rpart/vignettes/longintro.pdf

2. http://dataaspirant.com/2017/01/30/how-decision-tree-algorithm-works/

3. https://lagunita.stanford.edu/c4x/HumanitiesScience/StatLearning/asset/trees.pdf

4. http://www.cs.princeton.edu/courses/archive/spr07/cos424/papers/mitchell-dectrees.pdf



 

5.code for building trees in R:

# Classification Tree with rpart

library(rpart)

 

# grow tree 

fit <- rpart(Kyphosis ~ Age + Number + Start,

            
method="class", data=kyphosis)

 

printcp(fit) # display the results 

plotcp(fit) # visualize cross-validation results 

summary(fit) # detailed summary of splits

 

# plot tree 

plot(fit, uniform=TRUE, 

     main="Classification Tree
for Kyphosis")

text(fit, use.n=TRUE, all=TRUE, cex=.8)

 

 

# prune the tree 

pfit<- prune(fit, cp=  
fit$cptable[which.min(fit$cptable[,"xerror"]),"CP"])

 

# plot the pruned tree 

plot(pfit, uniform=TRUE, 

     main="Pruned Classification
Tree for Kyphosis")

text(pfit, use.n=TRUE, all=TRUE, cex=.8)

 

# Regression Tree Example

library(rpart)

 

# grow tree 

fit <- rpart(Mileage~Price + Country + Reliability +
Type, 

             method="anova",
data=cu.summary)

 

printcp(fit) # display the results 

plotcp(fit) # visualize cross-validation results 

summary(fit) # detailed summary of splits

 

# create additional plots 

par(mfrow=c(1,2)) # two plots on one page 

rsq.rpart(fit) # visualize cross-validation
results   

 

# plot tree 

plot(fit, uniform=TRUE, 

     main="Regression Tree for
Mileage ")

text(fit, use.n=TRUE, all=TRUE, cex=.8)

 

# Conditional Inference Tree for Kyphosis

library(party)

fit <- ctree(Kyphosis ~ Age + Number + Start, 

             data=kyphosis)

plot(fit, main="Conditional Inference Tree for
Kyphosis")

 

# Conditional Inference Tree for Mileage

library(party)

fit2 <- ctree(Mileage~Price + Country + Reliability +
Type, 

              data=na.omit(cu.summary))

 

 

