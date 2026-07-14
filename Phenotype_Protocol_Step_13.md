```{r}
#STEP 13 - WHERE NECESSARY, ORIENT SCORES SO THAT HIGHER FUNCTIONING = BETTER COGNITIVE ABILITY/PERFORMANCE
data_complete_cases$log_processing_speed_task_oriented <- -data_complete_cases$log_processing_speed_task
```


```{r}
#ALL TRANSFORMATIONS AND ORIENTATIONS HAVE BEEN APPLIED. THE FINAL VARIABLES FOR USE ARE AS FOLLOWS:
#log_processing_speed_task_oriented
#verbal_learning_task
#working_memory_task
#executive_function_task
```
