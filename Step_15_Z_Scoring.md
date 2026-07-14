```{r}
#STEP 15 - STANDARDISING SCORES
######## Z SCORES ########

#Z SCORES PROCESSING SPEED TASK
data_complete_cases$z_score_processing_speed <- as.numeric(scale(data_complete_cases$age_resid_processing_speed))
```

```{r}
#Z SCORES VERBAL LEARNING TASK
data_complete_cases$z_score_verbal_learning <- as.numeric(scale(data_complete_cases$age_resid_verbal_learning))
```

```{r}
#Z SCORES WORKING MEMORY
data_complete_cases$z_score_working_memory <- as.numeric(scale(data_complete_cases$age_resid_working_memory))
```

```{r}
#Z SCORES EXECUTIVE FUNCTION
data_complete_cases$z_score_executive_function <- as.numeric(scale(data_complete_cases$age_resid_executive_function))
```
