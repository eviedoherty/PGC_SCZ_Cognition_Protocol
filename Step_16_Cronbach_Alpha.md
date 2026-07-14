```{r}
#STEP 16 - RUN CRONBACH'S ALPHA
####### CRONBACH'S ALPHA TO HELP DETERMINE THE NUMBER OF TESTS TO CARRY FORWARD AND INTERNAL CONSISTENCY ########

library(psych)

alpha(data_complete_cases[, c("z_score_processing_speed", "z_score_verbal_learning", "z_score_working_memory", "z_score_executive_function")])
```


```{r}
#write out final dataframe for PCA
setwd("/Set/path/to/working/directory/")
write.csv(data_complete_cases, "data_complete_cases_for_PCA.txt", row.names = FALSE)
```
