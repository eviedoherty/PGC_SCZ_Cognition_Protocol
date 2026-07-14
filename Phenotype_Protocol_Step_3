```{r}
#STEP 3 - FILTER THE DATAFRAME TO CONTAIN ONLY THOSE WHO HAVE AGE DATA

sum(!is.na(data_cases_filtered$age_colname))
#N individuals with age data 

#the below code filters the dataframe to only contain those with age data

data_cases_filtered_age <- data_cases_filtered %>%
  filter(!is.na(age_colname))

#For demographics purposes get the age range within the dataset

range(data_cases_filtered_age$age_colname, na.rm = TRUE)
#Age Range: X-Y Years
```
