```{r}
#READ IN DATASET

setwd("/set/working/directory")
data <- read.csv("My_Cognitve_Data.csv")
data
#N INDIVIDUALS
```

```{r}
#STEP 1 - FILTER TO CASES ONLY
#FILTERING TO CONTAIN INDIVIDUALS WITH A SCHZIPHRENIA OR SCHIZOAFFECTIVE DISORDER DIAGNOSIS
data_cases <- data %>%
  filter(diagnosis_colname %in% c("SZ", "SZA"))
data_cases
#N CASES
```
