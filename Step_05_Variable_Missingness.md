```{r}
#STEP 5 - CHECK THE % MISSINGNESS FOR EACH AVAILABLE COGNITIVE VARIABLE 

cognitive_measures <- c("verbal_learning_task", "working_memory", "processing_speed", "executive_function") #adjust to match your cognitive measure column names
```

```{r}
missingness_summary <- data.frame(
  Cognitive_Measure = cognitive_measures,
  N_Missing = sapply(cognitive_measures, function(x) sum(is.na(data_cases_filtered_age[[x]]))), #adjust to match your dataframe name
  Missingness_Percentage = sapply(cognitive_measures, function(x) mean(is.na(data_cases_filtered_age[[x]])) * 100) #adjust to match your dataframe name
)

missingness_summary
```
