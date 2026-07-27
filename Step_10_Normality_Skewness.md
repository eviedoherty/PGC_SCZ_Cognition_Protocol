```{r}
#STEP 10 - NORMALITY & SKEWNESS CHECKS

library(ggplot2)

cognitive_measures <- c(
  "verbal_learning_i",
  "verbal_learning_ii",
  "processing_speed", 
  "working_memory",
  "attention" #adjust to match cognitive measure column names in your dataset
)

for (measure in cognitive_measures) {

  print(
    ggplot(data_complete_cases_clean, aes(x = .data[[measure]])) + #adjust to match your dataframe name
      geom_histogram(bins = 30) +
      labs(title = paste("Histogram:", measure),
           x = measure,
           y = "Count")
  )

}


for (measure in cognitive_measures) {

  print(
    ggplot(data_complete_cases_clean, aes(sample = .data[[measure]])) + #adjust to match your dataframe name
      stat_qq() +
      stat_qq_line() +
      labs(title = paste("QQ Plot:", measure))
  )

}

```

```{r}
#AT THIS POINT, BINARY MEASURES OR THOSE DEMONSTRATING EXTREME FLOOR OR CEILING EFFECTS ARE DROPPED AND STEPS 6-10 ARE REPEATED WITHOUT DROPPED MEASURES
```

