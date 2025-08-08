# Foundations of Causal Thinking in Public Health

> ## Class materials
>
> Slides: [**Module 1**](https://drive.google.com/file/d/1ujOsEenrQy1sjIX4Zt_CfAqeF0o-KfY-/view?usp=sharing)
>
> Recording: [**Module 1, Part 1.1**](https://drive.google.com/file/d/14yxdT8so1w2LQV2pwoGm1ys3Ek5yuLET/view?usp=sharing)
>
> Recording: [**Module 1, Part 2.1**](https://drive.google.com/file/d/1rUQnbOTkVk5DPu8Ghbu2W80NJ008Auyt/view?usp=sharing)
>
> Recording: [**Module 1, Part 2.2**](https://drive.google.com/file/d/1hsA1CZ0jpVycsNmuH0A7C5AHmlvBpOvM/view?usp=sharing)

> ## Textbook reading
>
> [**Hernán & Robins, Causal Inference: What If – Chapters 1–2**](https://static1.squarespace.com/static/675db8b0dd37046447128f5f/t/677676888e31cc50c2c33877/1735816881944/hernanrobins_WhatIf_2jan25.pdf)

> ## Supplementary reading
>
> [**Pearl, J. and Mackenzie, D. (2018) The Book of Why: The New Science of Cause and Effect. Basic Books.**](https://bayes.cs.ucla.edu/WHY/why-ch1.pdf) Selected public health news articles (provided on the course site).

> ## Topics covered
>
> -   Association vs. Causation\
> -   Introduction to Counterfactuals and Potential Outcomes\
> -   Causal Estimands and Identification\
> -   Critical reading exercise: analyzing causal claims in public health news

## Association vs. Causation

**Association** refers to a statistical relationship where two variables move together, but one doesn’t necessarily cause the other. For instance, ice cream sales and drowning incidents both rise in the summer, not because one causes the other, but because they share a third factor: temperature. In contrast, **causation** implies a direct cause-and-effect relationship, where changing one variable leads to changes in another. Establishing causation requires rigorous methods, such as randomized controlled trials, to rule out confounding factors.

**Simpson’s Paradox** occurs when a trend appears in separate groups but reverses when the data are combined. This paradox is driven by **confounding variables**—unaccounted factors that influence both the treatment and the outcome. It illustrates how aggregated data can be misleading and emphasizes the importance of analyzing relationships within subgroups to avoid drawing incorrect conclusions.

To demonstrate this paradox, I simulated a study comparing two pneumonia treatments across 2,000 people Treatment A was mostly given to mild cases, while Treatment B was given to severe cases. When data were analyzed without considering severity, Treatment A seemed more effective. However, when stratified by severity, Treatment B consistently showed lower death rates in both mild and severe groups. This was visualized through two plots: one showing the misleading overall trend, and another stratified by severity revealing the true relationship. 


``` r
# library(ggplot2)
# library(dplyr)

set.seed(123)

n <- 2050

severity <- rep(c("Mild", "Severe"), times = c(1450, 600))

treatment <- c(rep("Treatment A", 1400), rep("Treatment B", 50), 
               rep("Treatment A", 100), rep("Treatment B", 500)) 

outcome <- c(rbinom(1400, 1, 0.15),  # Mild + A (15% death rate)
             rbinom(50, 1, 0.10),    # Mild + B (10% death rate)
             rbinom(100, 1, 0.30),   # Severe + A (30% death rate)
             rbinom(500, 1, 0.20))   # Severe + B (20% death rate)

df <- data.frame(
  Severity = severity,
  Treatment = treatment,
  Outcome = outcome
)

death_counts <- tapply(df$Outcome, list(df$Severity, df$Treatment), sum)
table_counts <- table(df$Severity, df$Treatment)
death_rates <- round(death_counts / table_counts, 3)

overall_a <- sum(df$Outcome[df$Treatment == "Treatment A"]) / sum(df$Treatment == "Treatment A")
overall_b <- sum(df$Outcome[df$Treatment == "Treatment B"]) / sum(df$Treatment == "Treatment B")

print("Death rates by severity and treatment:")
```

```
## [1] "Death rates by severity and treatment:"
```

``` r
print(death_rates)
```

```
##        Treatment A Treatment B
## Mild         0.136       0.120
## Severe       0.380       0.204
```

``` r
cat("Overall death rate (Treatment A):", round(overall_a, 3), "\n")
```

```
## Overall death rate (Treatment A): 0.153
```

``` r
cat("Overall death rate (Treatment B):", round(overall_b, 3), "\n")
```

```
## Overall death rate (Treatment B): 0.196
```







