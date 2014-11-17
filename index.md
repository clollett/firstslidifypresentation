---
title       : Studying MPG for pairs for possible predictors
subtitle    : A shiny application
author      : Carlos L.  
job         : Data Sciences Specialization student
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : [bootstrap,quiz, shiny, interactive]            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}


--- 
### MOTIVATIONS

The mtcars set is database used in different stages of data sciences courses due to its simplicity and yet enough complexity to avoid trivial analysis.

The motivation of this shiny appliaction is to allow students to see different behaviors towards different pairs of predictors. 
Features:

* Full selection of first predictors and 2nd predictor restricted to discrete features.
* Exploratory plots, results of generalized linear model predictions in graph and in text

--- 
### APPLICATION INTERFACE

<div class="row-fluid">
  <div class="container-fluid">
    <div class="row-fluid">
      <div class="span12" style="padding: 10px 0px;">
        <h1>Studying Miles per Gallon for pairs for possible predictors</h1>
      </div>
    </div>
    <div class="row-fluid">
      <div class="span4">
        <form class="well">
          <label class="control-label" for="sel_predictor">Select first predictor</label>
          <select id="sel_predictor"><option value="# of cylinders" selected># of cylinders</option>
<option value="Displacement(cu.in.)">Displacement(cu.in.)</option>
<option value="Gross horsepower">Gross horsepower</option>
<option value="Rear axle ratio">Rear axle ratio</option>
<option value="Weight">Weight</option>
<option value="Quarter-mile time">Quarter-mile time</option>
<option value="V/S">V/S</option>
<option value="Transmission">Transmission</option>
<option value="# forward gears"># forward gears</option>
<option value="# carburetors"># carburetors</option></select>
          <script type="application/json" data-for="sel_predictor" data-nonempty="">{}</script>
          <div id="colorBy" class="control-group shiny-input-radiogroup">
            <label class="control-label" for="colorBy">Coloring by the 2nd predictor</label>
            <label class="radio ">
              <input type="radio" name="colorBy" id="colorBy1" value="#Cylinder" checked="checked"/>
              <span>#Cylinder</span>
            </label>
            <label class="radio ">
              <input type="radio" name="colorBy" id="colorBy2" value="VS"/>
              <span>VS</span>
            </label>
            <label class="radio ">
              <input type="radio" name="colorBy" id="colorBy3" value="Transmission"/>
              <span>Transmission</span>
            </label>
            <label class="radio ">
              <input type="radio" name="colorBy" id="colorBy4" value="# forward gears"/>
              <span># forward gears</span>
            </label>
            <label class="radio ">
              <input type="radio" name="colorBy" id="colorBy5" value="# carburetors"/>
              <span># carburetors</span>
            </label>
          </div>
          <h3>INSTRUCTIONS</h3>
        </form>
      </div>
      <div class="span8">
        <div class="tabbable tabs-above">
          <ul class="nav nav-tabs">
            <li class="active">
              <a href="#tab-8289-1" data-toggle="tab">MPG vs 2 predictors</a>
            </li>
            <li>
              <a href="#tab-8289-2" data-toggle="tab">Predictions vs. Real values of MPG on GLM of 2 Predictors</a>
            </li>
            <li>
              <a href="#tab-8289-3" data-toggle="tab">GLM Summary</a>
            </li>
          </ul>
          <div class="tab-content">
            <div class="tab-pane active" id="tab-8289-1"></div>
            <div class="tab-pane" id="tab-8289-2"></div>
            <div class="tab-pane" id="tab-8289-3"></div>
          </div>
        </div>
      </div>
    </div>
  </div>
</div>

---

### FEATURES. PLOTS



![plot of chunk unnamed-chunk-3](assets/fig/unnamed-chunk-3-1.png) ![plot of chunk unnamed-chunk-3](assets/fig/unnamed-chunk-3-2.png) 

* __MPG vs 2 predictors__: This feature shows the scatter plot mpg vs. the first predictor colored by the second predictor, so it is possible to explore possible groups and make a initial evaluation of the predictors
* __Predictions vs. Real values of MPG on GLM of 2 Predictors__: Our second feature shows the result of creating generalized linear model on the selected predictor. This is done by plotting predicted values of the data against the actual values.
* __GLM Summary__(next slide): It shows all the information about the generalized linear model of mpg from the 2 chosen predictors

---


```
## 
## Call:
## glm(formula = mpg ~ cyl + am, family = "gaussian", data = mpgData)
## 
## Deviance Residuals: 
##     Min       1Q   Median       3Q      Max  
## -5.9618  -1.4971  -0.2057   1.8907   6.5382  
## 
## Coefficients:
##             Estimate Std. Error t value Pr(>|t|)    
## (Intercept)   24.802      1.323  18.752  < 2e-16 ***
## cyl6          -6.156      1.536  -4.009 0.000411 ***
## cyl8         -10.068      1.452  -6.933 1.55e-07 ***
## amManual       2.560      1.298   1.973 0.058457 .  
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
## 
## (Dispersion parameter for gaussian family taken to be 9.446274)
## 
##     Null deviance: 1126.0  on 31  degrees of freedom
## Residual deviance:  264.5  on 28  degrees of freedom
## AIC: 168.4
## 
## Number of Fisher Scoring iterations: 2
```
