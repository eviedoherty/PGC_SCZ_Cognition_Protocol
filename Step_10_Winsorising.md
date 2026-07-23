```{r}
#STEP 10 - WINSORISING (EXAMPLE)

data_complete_cases[5, "verbal_learning_task"] <- 69

data_complete_cases[20, "processing_speed_task"] <- 35

data_complete_cases[92, "executive_function_task"] <- 12

```

```{r}
#WRITE OUT THE DATAFRAME AFTER WINDSORISING
write.csv(data_complete_cases, "data_complete_cases", row.names = FALSE)
```
