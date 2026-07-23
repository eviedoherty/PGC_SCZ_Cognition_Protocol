```{r}
#STEP 11 - NORMALITY & SKEWNESS CHECKS

library(ggplot2)

cognitive_measures <- c(
  "verbal_learning_task", 
  "processing_speed_task", 
  "working_memory_task",
  "executive_function_task" #
)

for (measure in cognitive_measures) {

  print(
    ggplot(catie_complete_cases, aes(x = .data[[measure]])) +
      geom_histogram(bins = 30) +
      labs(title = paste("Histogram:", measure),
           x = measure,
           y = "Count")
  )

}


for (measure in cognitive_measures) {

  print(
    ggplot(catie_complete_cases, aes(sample = .data[[measure]])) +
      stat_qq() +
      stat_qq_line() +
      labs(title = paste("QQ Plot:", measure))
  )

}

```

```{r}
#AT THIS POINT, BINARY MEASURES OR THOSE DEMONSTRATING EXTREME FLOOR OR CEILING EFFECTS ARE DROPPED AND STEPS 6-11 ARE REPEATED WITHOUT DROPPED MEASURES
```

