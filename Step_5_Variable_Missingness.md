```{r}
#STEP 5 - CHECK THE % MISSINGNESS FOR EACH AVAILABLE COGNITIVE VARIABLE 
#THIS CAN BE LOOPED FOR EFFICIENCY - NOT DONE HERE FOR TRANSPARENCY

mean(is.na(data_cases_filtered_age$verbal_learning_task)) * 100
sum(is.na(data_cases_filtered_age$verbal_learning_task))
#X% MISSING DATA
#N samples Missing Data
```

```{r}
mean(is.na(data_cases_filtered_age$working_memory_task)) * 100
sum(is.na(data_cases_filtered_age$working_memory_task))
#X% MISSING DATA
#N samples Missing Data
```

```{r}
mean(is.na(data_cases_filtered_age$processing_speed_task)) * 100
sum(is.na(data_cases_filtered_age$processing_speed_task))
#X% MISSING DATA
#X samples Missing Data
```

```{r}
mean(is.na(data_cases_filtered_age$executive_function_task)) * 100
sum(is.na(data_cases_filtered_age$executive_function_task))
#X% MISSING DATA
#X samples Missing Data
```
