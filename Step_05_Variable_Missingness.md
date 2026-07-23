```{r}
#STEP 5 - CHECK THE % MISSINGNESS FOR EACH AVAILABLE COGNITIVE VARIABLE 
#THIS CAN BE LOOPED FOR EFFICIENCY - NOT DONE HERE FOR TRANSPARENCY

cognitive_measures <- c("verbal_learning_task", "working_memory", "processing_speed", "executive_function") #add all available cognitive measures from your dataset here
```

```{r}
missingness_summary <- data.frame(
  Cognitive_Measure = cognitive_measures,
  N_Missing = sapply(cognitive_measures, function(x) sum(is.na(data_cases_filtered_age[[x]]))), #adjust to match your dataframe name
  Missingness_Percentage = sapply(cognitive_measures, function(x) mean(is.na(data_cases_filtered_age[[x]])) * 100) #adjust to match your dataframe name
)

missingness_summary
```
