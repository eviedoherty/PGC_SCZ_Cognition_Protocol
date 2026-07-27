
```{r}
#STEP 7 - ISOALTE SAMPLES MAXIMISING THE DATASET INTO OWN DATAFRAME

#RULE: THE NUMBER OF DOMAINS WAS INCREASED WHERE INCREASING THE NUMBER OF DOMAINS DID NOT COMPROMISE THE SAMPLE SIZE BY MORE THAN 1% OF THE POSSIBLE SAMPLE I.E. THOSE WITH X3 DOMAINS AND AT LEAST X1 TEST PER DOMAINS (see Protocol)

#EXAMPLE: 3 Domains = 128 individuals, 4 domains = 127 individuals (0.77% sample difference from 3 domains)
#4 domains chosen as <1% decrease in sample size 


library(dplyr)

data_complete_cases <- data_cases_filtered_age %>%
  filter(complete.cases(across(c(verbal_learning_i, verbal_learning_ii, processing_speed, working_memory, attention)))) #adjust to match cognitive measure column names in your dataset 

data_complete_cases
```
