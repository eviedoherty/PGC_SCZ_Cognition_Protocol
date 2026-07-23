```{r}
#STEP 12 - ORIENT SCORES SO THAT HIGHER FUNCTIONING = BETTER COGNITIVE ABILITY/PERFORMANCE (IF NECESSARY)
#EXAMPLE: TRAIL-MAKING A IS TIME BASED MEANING GREATER SCORING = WORSE COGNITIVE PERFORMANCE MEANING SCORES SHOULD BE ORIENTED ACCORDINGLY

data_complete_cases_clean$log_processing_speed_task_oriented <- -data_complete_cases_clean$log_processing_speed_task #adjust to match dataframe and cognitive measure column name
```

