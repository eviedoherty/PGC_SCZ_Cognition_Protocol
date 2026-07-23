```{r}
#STEP 13 - AGE RESIDUALISATION OF COGNITIVE MEASURES

model <- lm(log_processing_speed_task_oriented ~ age_colname, data = data_complete_cases_clean) 

data_complete_cases_clean$age_resid_processing_speed <- residuals(model)

#REPEAT FOR ALL COGNITIVE MEASURES CONTRIBUTING TO THE COMPLETE CASES SAMPLE
```


