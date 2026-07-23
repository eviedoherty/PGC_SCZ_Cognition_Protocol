```{r}
#READ IN DATASET

setwd("/set/working/directory")
data <- read.csv("My_Cognitve_Data.csv")
data
#N INDIVIDUALS
```

```{r}
#STEP 1 - FILTER TO CASES ONLY
#FILTERING TO CONTAIN INDIVIDUALS WITH A SCHZIOPHRENIA OR SCHIZOAFFECTIVE DISORDER DIAGNOSIS

data_cases <- data %>%
  filter(diagnosis_colname %in% c("SZ", "SZA")) #adjust to dataset accordingly
data_cases

message("Number of cases: ", nrow(data_cases))
```
