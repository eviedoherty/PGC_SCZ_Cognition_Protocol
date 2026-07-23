```{r}
#STEP 3 - FILTER THE DATAFRAME TO CONTAIN ONLY THOSE WHO HAVE AGE DATA

data_cases_filtered_age <- data_cases_filtered %>%  #use this dataframe for the subsequent steps
  filter(!is.na(age_colname)) #add the age column name from your dataset 

age_summary <- data_cases_filtered_age %>%
  summarise(
    n = n(),
    min_age = min(age_colname),  #add the age column name from your dataset 
    max_age = max(age_colname)   #add the age column name from your dataset 
  )

message("Number with age data: ", age_summary$n)
message("Age range: ", age_summary$min_age, "–", age_summary$max_age, "years")
```
