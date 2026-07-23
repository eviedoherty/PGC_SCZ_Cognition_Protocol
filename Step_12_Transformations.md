```{r}
#STEP 12 - TRANSFORMATIONS SHOULD BE APPLIED WHERE NECESSARY BASED ON HISTOGRAMS AND QQ PLOTS

#THE CHOSEN TRANSFORMATION SHOULD BE CHOSEN DEPENDING ON THE TYPE OF DATA YOU ARE WORKING WITH AND SEVERITY OF THE SKEW
#I.E. LOG: SEVERE POSITIVE SKEW, CONTINUOUS/COUNT DATA
      SQUARE-ROOT: MODERATE SKEW, COUNT DATA
      ETC.

#WHERE A NEGATIVE SKEW IS PRESENT, REFLECTION IS REQUIRED BEFORE TRANSFORMATION IS APPLIED
#REFLECTION CODE
data_complete_cases_clean$processing_speed_task_reflected <- 
  max(data_complete_cases_clean$processing_speed_task) -
  data_complete_cases_clean$processing_speed_task + 1

```

```{r}
##### EXAMPLE TRANSFORMATION USED ON PROCESSING SPEED TASK #####
#POSITIVE SKEW
data_complete_cases_clean$log_processing_speed_task <- log(data_complete_cases_clean$processing_speed_task)

#COMPARE HISTOGRAMS AND QQ PLOTS FROM AFTER TRANSFORMATION TO THOSE BEFORE

#HISTOGRAM
ggplot(data_complete_cases_clean, aes(x = log_processing_speed_task)) +
  geom_histogram(bins = 30)

#QQ PLOTS
ggplot(data_complete_cases_clean, aes(sample = log_processing_speed_task)) +
  stat_qq() +
  stat_qq_line()

```
