# Why use R? {#why_r}


## Packages

```r
library(tidyverse)
library(nlme)
```

## Course contents & materials

<p style="font-size:18px">The complete source code for the webinars and all dependent data, and files can be found on [Github.com/uashogeschoolutrecht/staRters](https://github.com/uashogeschoolutrecht/staRters).

 - Day 1: Why R, Case demo, RMarkdown, Intro R syntax
 - Day 2: Visualization, Data Wrangling, Tidy data
 - Day 3: Data import, Statistics (assumptions & regression)
 
_Disclaimer: "This is not a course on statistics". If you have a specific statistical challenge and you would like to discuss this after the course with me, feel invited to reach out!_ 

## Introducing Reproducible (Open) Science

 1. When things go wrong 
 1. Why Reproducible (Open) Science?
 1. The need for learning programming
 1. An example of Reproducible (Open) Science
 
$Reproducible\ (Open)\ Science =$ 
$Reproducible\ Research + Open\ Science$

## Data, methods and logic {.build}

*[Brown, Kaiser & Allison, PNAS, 2018](https://doi.org/10.1073/pnas.1708279115)*

"...in science, three things matter:

 >1. the data, 
 >1. the methods used to collect the data [...], and 
 >1. **the logic connecting the data and methods to conclusions,**

everything else is a distraction."

## `Gollums` lurking about {.build}


```r
knitr::include_graphics(
  here::here(
    "images",
    "gollum_climbing.jpg"
  )
)
```

<img src="C:/Users/mteunis/workspaces/staRters/images/gollum_climbing.jpg" width="145" />

 "In one case, a group accidentally used reverse-coded variables, making their conclusions the opposite of what the data supported."

 "In another case, authors received an incomplete dataset because entire categories of data were missed; when corrected, the qualitative conclusions did not change, but the quantitative conclusions changed by a factor of >7"

 <p style="font-size:14px">[Brown, Kaiser & Allison, 2018; PNAS](https://doi.org/10.1073/pnas.1708279115)</p>

## Why we need Reproducible (Open) Science?

 >- To assess validity of science and methods we need access to data, methods and conclusions
 >- To learn from choices other researchers made
 >- To learn from omissions, mistakes or errors
 >- To prevent publication bias (also negative results will be available in reproducible research)
 >- To be able to re-use and/or synthesize data (from many and diverse sources)
 >- To have access to it all!
 
<p style="font-size:14px">[Nature Collection on this topic](https://www.nature.com/collections/prbfkwmwvz)</p>
 
## The _GUI problem_

How would you 'describe' the steps of an analysis or creation of a graph when you use *GUI* based software? 

*_"You can only do this using code, so it is (basically) impossible in a GUI"_*


```r
knitr::include_graphics(
  here::here(
    "images",
    "messy_steps.jpg"
  )
)
```

<img src="C:/Users/mteunis/workspaces/staRters/images/messy_steps.jpg" width="758" />

<p style="font-size:14px">*[Graphical User Interface (GUI)...is a form of user interface that allows users to interact with electronic devices through graphical icons and audio indicator such as primary notation, instead of text-based user interfaces, typed command labels or text navigation...](https://en.wikipedia.org/wiki/Graphical_user_interface)</p>

## Programming is essential for Reproducible (Open) Science {.build}

 >- Only programming an analysis (or creation of a graph) records every step
 >- The script(s) function as a (data) analysis journal 
 >- Code is the logic that connects the data and methods to conclusions 
 >- Learning to use a programming language takes time but pays of at the long run (for all of science)

## Introducing Literate programming

 - Literate) programming is a way to connect narratives to data, methods and results
 - All scripts in this course are **R Markdown** scripts
 - The complete source of the reader is available in Github.com


```r
knitr::include_graphics(here::here("images","rmd_printscr.png"))
```

<img src="C:/Users/mteunis/workspaces/staRters/images/rmd_printscr.png" width="539" />

## To  replicate a scientific study we need at least:

 > - Scientific context, research questions and state of the art [<mark>P<mark/>]
 > - (Experimental) model or characteristics of population or matter studied [<mark>P</mark>]
 > - Data that was generated and corresponding meta data [<mark>D</mark>, _C_]
 > - **Exact** (experimental) design of the study [<mark>P</mark>, _D_, <mark>C</mark>]
 > - Exploratory data analysis of the data [_P_, <mark>C</mark>]
 > - **Exact** methods that were used to conduct any formal inference [_P_, <mark>C</mark>]
 > - Model diagnostics [_C_]
 > - Interpretations of the (statistical) model results/model fitting process [_P_, _C_]
 > - Conclusions and academic scoping of the results [<mark>P</mark>, _C_]
 > - **Access to all of the above** [<mark>OAcc, OSrc</mark>]

<p style="font-size:14px">$P = Publication$, $D = Data$, $C = Code$, $OAcc = Open\ Access$, $OSrc = Open\ Source$ </p> 

## Why R?

 - R is free
 - R has a huge user-community
 - R has many packages
 - Many statistical applications (more than SPSS)
 - R connects to other tools 
 - R has RStudio as an IDE
 - You can find (almost) every example you want on the internet
 - R has superb plotting possibilities
 ...

## A short example of Reproducible (Open) Science

Assume we have the following question:
"Which of 4 types of chairs takes the least effort to arise from when seated in?"
We have the following setup:

 - 4 different types of chairs
 - 9 different subjects (probably somewhat aged)
 - Each subject is required to provide a score (from 6 to 20, 6 being very lightly strenuous, 20 being extremely strenuous) when arising from each of the 4 chairs. There is some 'wash-out' time in between the trials. The chair order is randomised.

To analyze this experiment statistically, the model would need to include: the rating score as the **measured (or dependent) variable**, the type of chair as the **experimental factor** and the subject as the **blocking factor**

## Now we move to RStudio

 - If you have 2 screens, now is the moment to expand the screen
 - Login to your Rstudio Environment
 - Clone the materials of the course to your `Home` folder
 - You can find the steps also in  `_gettingstarted.Rmd`
 - Open the file `_why_r.Rmd`
 - Follow along the demo by running the code
 - Details on using RStudio can be found in `_introrstudio`

## Mixed effects models

A typical analysis method for this type of randomized block design is a so-called 'multi-level' or also called 'mixed-effects' or 'hierarchical' models. An analysis method much used in clinical or biological scientific practice. 
 
You could also use one-way ANOVA but I will illustrate why this is not a good idea 

## What do we minimally need, to replicate the science of this experiment? {.build}

I will show:

 >- the data 
 >- an exploratory graph 
 >- a statistical model 
 >- the statistical model results
 >- a model diagnostic
 >- some conclusions 
 
In the next few slides, I will hopefully convince you of the power of (literate) programming to communicate such an analysis. 

<p style="font-size:14px">[Example reproduced from: Pinheiro and Bates, 2000, _Mixed-Effects Models in S and S-PLUS_, Springer, New York.](https://cran.r-project.org/web/packages/nlme/index.html)</p>
 
## The data of the experiment

<p style="font-size:14px">[Wretenberg, Arborelius & Lindberg, 1993](https://doi.org/10.1080/00140139308967910)</p>



```r
library(nlme)
ergoStool %>% as_tibble()
```

```
## # A tibble: 36 x 3
##    effort Type  Subject
##     <dbl> <fct> <ord>  
##  1     12 T1    1      
##  2     15 T2    1      
##  3     12 T3    1      
##  4     10 T4    1      
##  5     10 T1    2      
##  6     14 T2    2      
##  7     13 T3    2      
##  8     12 T4    2      
##  9      7 T1    3      
## 10     14 T2    3      
## # ... with 26 more rows
```

## An exploratory graph

```r
set.seed(123)
plot_ergo <- ergoStool %>%
  ggplot(aes(x = reorder(Type, effort), y = effort)) + 
  geom_boxplot(colour = "darkgreen", outlier.shape = NA) + 
  geom_jitter(aes(colour = reorder(Subject, -effort)), 
              width = 0.2, size = 3) +
  scale_colour_manual(values = c("red","blue", "green", "darkblue", "darkgreen", "purple", "grey", "black", "darkgrey")) +
  ylab("Effort (Borg scale score)") +
  xlab("Chair type") + 
  guides(colour=guide_legend(title="Subject id")) +
  theme_bw()
plot_ergo
```

<img src="ch01_why_r_files/figure-html/unnamed-chunk-6-1.png" width="672" />

## Mind the variability per subject, what do you see?

 - Can you say something about within-subject variability (note 'Minster Blue')?
 - Can you say something about between-subject variability (note 'Mister Green', vs 'Mister Black')?
 - Which chair type takes, on average the biggest effort to arise from?
 

```r
plot_ergo
```

<img src="ch01_why_r_files/figure-html/unnamed-chunk-7-1.png" width="480" />

## The statistical questions

 1. Which chair type takes, on average the biggest effort to arise from? (ANOVA / MEM, fixed effects)
 - Do individual (within subject) differences play a role in appointing a average score to a chair type? (MEM, random effects)
 - Does variability between subjects play a role in determining the 'best' chair type (ANOVA / MEM, confidence intervals)

## The statistical model 
Statistical models (in R) can be specified by a `model formula`. The left side of the formula is the dependent variable, the right side are the 'predictors'. Here we include a `fixed` and a `random` term to the model (as is common for mixed-effects models)


```r
library(nlme)
```

```r
ergo_model <- lme(
  data = ergoStool, # the data to be used for the model
  fixed = effort ~ Type, # the dependent and fixed effects variables
  random = ~1 | Subject # random intercepts for Subject variable
)
```

<p style="font-size:18px">The `lme()` function is part of the [`{nlme}`](https://cran.r-project.org/web/packages/nlme/index.html) package for mixed effects modelling in R</p>

<p style="font-size:18px">Example reproduced from: [Pinheiro and Bates, 2000, _Mixed-Effects Models in S and S-PLUS_, Springer, New York.](https://cran.r-project.org/web/packages/nlme/index.html)</p>

## The statistical results

```r
result <- ergo_model %>% summary() 
result$tTable %>% as.data.frame() %>% knitr::kable()
```



|            |     Value| Std.Error| DF|   t-value|   p-value|
|:-----------|---------:|---------:|--:|---------:|---------:|
|(Intercept) | 8.5555556| 0.5760123| 24| 14.853079| 0.0000000|
|TypeT2      | 3.8888889| 0.5186838| 24|  7.497610| 0.0000001|
|TypeT3      | 2.2222222| 0.5186838| 24|  4.284348| 0.0002563|
|TypeT4      | 0.6666667| 0.5186838| 24|  1.285305| 0.2109512|

## Model diagnostics {.build}

 >- Diagnostics of a fitted model is the most important step in a statistical analysis
 >- In most scientific papers the details are lacking 
 >- Did the authors omit to perform this step? Or did they not report it?
 >- If you do not want to include it in your paper, put it in an appendix!
 
## Residuals

A residual plot shows the 'residual' error ('unexplained variance') after fitting the model. Under the Normality assumption standardized residuals should:
 
 >1. Be normally distributed around 0
 >1. Display no obvious 'patters'
 >1. Should display overall equal 'spread' above and below 0 ('assumption of equal variance')
 
## Residual plot

```r
plot(ergo_model) ## type = 'pearson' (standardized residuals)
```

<img src="ch01_why_r_files/figure-html/unnamed-chunk-11-1.png" width="672" />

## The conclusions in a plot

```r
# install.packages("ggsignif")
library(ggsignif)
p_values <- result$tTable %>% as.data.frame()
annotation_df <- data.frame(Type=c("T1", "T2"), 
                            start=c("T1", "T1"), 
                            end=c("T2", "T3"),
                            y=c(16, 14),
                            label=
                              paste("p-value:",
                              c(
                              formatC(
                                p_values$`p-value`[2], digits = 3),
                              formatC(
                                p_values$`p-value`[3], digits = 3)
                              )
                            )
                          )
                            
set.seed(123)
ergoStool %>%
  ggplot(aes(x = reorder(Type, effort), 
             y = effort)) + 
  geom_boxplot(colour = "darkgreen", 
               outlier.shape = NA) + 
  geom_jitter(aes(
    colour = reorder(Subject, -effort)), 
    width = 0.2, 
    size = 3) +
  scale_colour_manual(
    values = c(
      "red", "blue","green", 
      "darkblue", "darkgreen", 
      "purple", "grey", "black", 
      "darkgrey")) +
  ylab("Effort (Borg scale score)") +
  xlab("Chair type") + 
  guides(colour=guide_legend(title="Subject id")) +
  ylim(c(4,20)) +
  geom_signif(
    data=annotation_df,
    aes(xmin=start, 
    xmax=end, 
    annotations=label, 
    y_position=y),
    textsize = 5, vjust = -0.2,
    manual=TRUE) +
  theme_bw() -> plot_ergo
```

```
## Warning: Ignoring unknown aesthetics: xmin, xmax, annotations, y_position
```

```r
plot_ergo
```

<img src="ch01_why_r_files/figure-html/unnamed-chunk-12-1.png" width="672" />

## Coming from SPSS or Excel or the likes

 - You have to unlearn what you learned
 - You already know about performing statistical analysis and maybe also coding (SPSS syntax)
 - IBM (SPSS) is proprietary
 - I will take time to transfer
 - Try a hard-stop: so do not mix tools
 - Programming (in R) is hard and takes
 - I cannot learn you programming, you will have to do it yourself
 - Start with the book: "R for Data Science"
 - **Write code for humans!**

## And the most important part...

 -- Coffee break -- 
 
