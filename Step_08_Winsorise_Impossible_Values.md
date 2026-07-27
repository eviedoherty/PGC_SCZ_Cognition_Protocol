```{r}
#STEP 8 - LOOK AT THE RANGES FOR EACH MEASURE

cognitive_measures <- c("verbal_learning_task", "processing_speed_task", "working_memory_task", "executive_function_task") #adjust to match cognitive measure column names in your dataset 

data.frame(
  Variable = cognitive_measures,
  Min = sapply(data_complete_cases[cognitive_measures], min, na.rm = TRUE), #there should be no NAs at this point 
  Max = sapply(data_complete_cases[cognitive_measures], max, na.rm = TRUE)
)

#verbal_learning_i - 0-75
#verbal_learning_ii - 0-15
#processing_speed - time dependent, no fixed range
#working_memory - 0-30
#attention - typically 0-300
```

```{r}
#AS SCORING RANGES DIFFER IN EACH COGNITIVE MEASURE, WINSORISING WILL NEED NEED TO BE MANUALLY APPLIED IN THE CASE THERE ARE SCORES OUTSIDE THE POSSIBLE RANGE
#EXAMPLE
data_complete_cases[5, "verbal_learning_task"] <- 69
```
