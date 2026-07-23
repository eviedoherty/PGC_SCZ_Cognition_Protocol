```{r}
#STEP 15 - RUN CRONBACH'S ALPHA
####### CRONBACH'S ALPHA TO HELP DETERMINE INTERNAL CONSISTENCY ########

library(psych)

alpha(data_complete_cases_clean[, c("z_score_processing_speed", "z_score_verbal_learning", "z_score_working_memory", "z_score_executive_function")]) #adjust to match dataframe and z scored cognitive measure column names
```


```{r}
#write out final dataframe for PCA
setwd("/Set/path/to/working/directory/")
write.csv(data_complete_cases_clean, "data_complete_cases_for_PCA.txt", row.names = FALSE)
```
