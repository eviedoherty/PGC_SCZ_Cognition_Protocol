```{r}
#STEP 8 - LOOK AT THE RANGES FOR EACH MEASURE

vars <- c("verbal_learning_task", "processing_speed_task", "working_memory_task", "executive_function_task")

data.frame(
  Variable = vars,
  Min = sapply(data_complete_cases[vars], min, na.rm = TRUE), #there should be no NAs at this point 
  Max = sapply(data_complete_cases[vars], max, na.rm = TRUE)
)
```
