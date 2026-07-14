
```{r}
#STEP 4 - CHECK IF INDIVIDUALS PRESENT HAVE SEX DATA - SEX WILL BE USED AS A COVARIATE
#WHERE SEX DATA IS NOT PRESENT THIS INFORMATION CAN BE ACQUIRED FROM THE GENOTYPE DATA - NOT A REQUIREMENT THAT THE SAMPLES HAVE SEX DATA

sum(!is.na(data_cases_filtered_age$sex_colname))
#X SAMPLES HAVE SEX DATA - this was also manually checked to ensure the data was present

data_cases_filtered_age
table(data_cases_filtered_age$sex)
#N Female
#N Male
```
