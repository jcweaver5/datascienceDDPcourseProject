Lumberjack App for Timberland Management
========================================================
author: James C Weaver
date: January 2015

Modern Timberland Management Practices
========================================================

Woodland owners need to measure the board-foot content (called "Volume") of the trees on their land before the timber can be sold. Today, this is done using the Doyle or 1/4-Inch Rules Tables as described here in this [Ohio State University Fact Sheet](http://ohioline.osu.edu/for-fact/0035.html). However, digital technologies give the 21st century lumberjack new tools to increase her productivity and efficiency.

- Real-time, in-field measurement of a tree's height and girth (diameter)
- Mobile devices and applications that the lumberjack can use in the woodlot to do real-time analysis of the economics of her timberland

The Lumberjack App
========================================================

The Lumberjack App calculates the "Volume" of a tree in cubic feet from the tree's Girth in inches and Height in feet.

- App is deployed in real-time to the mobile device
- App uses a predictive model based on data from black cherry trees (the "trees" dataset in the R datasets package)
- Predictive model based on the break-through "Cylindrical Tree Algorithm"
- The interactive App can be viewed on the [shinyapps.io server](https://jcweaver5.shinyapps.io/lumberjack-app/) at the url https://jcweaver5.shinyapps.io/lumberjack-app/

The Cylindrical Tree Algorithm
========================================================
The Cylindrical Tree Algorithm deploys the same analytics used in the "Spherical Cow Algorithm" that revolutionized the prediction of milk output in the dairy industry.

The algorithm models a tree as a cylinder and then applies a linear regression model to the Volume. Model predictions are then transformed from log to linear space.


```r
model<- lm(logVolume ~  logHeight + logGirth, data=Trees)
```

Parameter Output from the Model
========================================================

<small style="font-size:.6em">


```r
summary(model)
```

```

Call:
lm(formula = logVolume ~ logHeight + logGirth, data = Trees)

Residuals:
      Min        1Q    Median        3Q       Max 
-0.073205 -0.021058  0.001056  0.027637  0.056121 

Coefficients:
            Estimate Std. Error t value Pr(>|t|)    
(Intercept) -2.88007    0.34734  -8.292 5.06e-09 ***
logHeight    1.11712    0.20444   5.464 7.81e-06 ***
logGirth     1.98265    0.07501  26.432  < 2e-16 ***
---
Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1

Residual standard error: 0.03535 on 28 degrees of freedom
Multiple R-squared:  0.9777,	Adjusted R-squared:  0.9761 
F-statistic: 613.2 on 2 and 28 DF,  p-value: < 2.2e-16
```
