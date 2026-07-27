```{r}
#STEP 2 - FILTER THE DATAFRAME TO CONTAIN ONLY RELEVANT VARIABLES 
library(dplyr)

data_cases_filtered <- data_cases %>%
  select(ID, PGC_ID, diagnosis, age, sex, verbal_learning_i, verbal_learning_ii, processing_speed, attention, working_memory)

```
