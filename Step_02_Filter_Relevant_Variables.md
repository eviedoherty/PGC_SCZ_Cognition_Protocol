```{r}
#STEP 2 - FILTER THE DATAFRAME TO ONLY CONTAIN RELEVANT VARIABLES 
library(dplyr)

data_cases_filtered <- data_cases %>%
  select(Proband, PGC_ID, Diagnosis, Group, Age, Sex, verbal_learning_task, working_memory_task, processing_speed_task, executive_function_task)

```
