```{r}
#STEP 14 - AGE RESIDUALISATION PROCESSING SPEED TASK
model <- lm(log_processing_speed_task_oriented ~ age_colname, data = data_complete_cases)

data_complete_cases$age_resid_processing_speed <- residuals(model)
```

```{r}
#AGE RESIDUALISATION VERBAL LEARNING TASK
model <- lm(verbal_learning_task ~ age_colname, data = data_complete_cases)

data_complete_cases$age_resid_verbal_learning <- residuals(model)
```

```{r}
#AGE RESIDUALISATION WORKING MEMORY TASK
model <- lm(working_memory_task ~ age_colname, data = data_complete_cases)

data_complete_cases$age_resid_working_memory <- residuals(model)
```

```{r}
#AGE RESIDUALISATION EXECUTIVE FUNCTION TASK
model <- lm(executive_function_task ~ age_colname, data = data_complete_cases)

data_complete_cases$age_resid_executive_function <- residuals(model)
```
