
```{r}
#STEP 7 - ISOALTE SAMPLES MAXIMISING THE DATASET INTO OWN DATAFRAME

#RULE: THE NUMBER OF DOMAINS WERE INCREASED WHERE INCREASING THE NUMBER OF DOMAINS DID NOT COMPROMISE THE SAMPLE SIZE BY MORE THAN 1% OF THE POSSIBLE SAMPLE I.E. THOSE WITH X3 DOMAINS AND AT LEAST X1 TEST PER DOMAINS (see protocol)

#EXAMPLE: 3 Domains = 129 individuals, 4 domains = 128 individuals (0.77% sample difference from 3 domains). 5 domains = 127 (1.55% difference from 3 domain sample)
#4 domains chosen as <1% decrease in sample size 


library(dplyr)

data_complete_cases <- data_cases_filtered_age %>%
  filter(complete.cases(across(c(verbal_learning_task, processing_speed_task, working_memory_task, executive_function_task))))
#N individuals as expected 
data_complete_cases
```
