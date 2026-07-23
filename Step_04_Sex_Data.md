
```{r}
#STEP 4 - CHECK IF SAMPLES HAVE SEX DATA - SEX WILL BE USED AS A CONTROL VARIABLE
#WHERE SEX DATA IS NOT PRESENT, THIS INFORMATION CAN BE OBTAINED FROM GENOTYPE DATA FILES - THIS STEP CAN BE SKIPPED IF SEX DATA IS NOT PRESENT

sum(!is.na(data_cases_filtered_age$sex_colname)) #adjust to match age column name in your dataset 
data_cases_filtered_age

table(data_cases_filtered_age$sex_colname) #adjust to match age column name in your dataset 
```
