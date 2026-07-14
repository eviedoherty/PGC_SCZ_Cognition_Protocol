```{r}
#STEP 12 - TRANSFORMATIONS (WHERE NECESSARY BASED ON HISTOGRAMS AND QQ PLOTS)
#THESE ARE GENERALLY LOG OR SQUARE ROOT 

##### EXAMPLE TRANSFORM PROCESSING SPEED TASK #####
#POSITIVE SKEW
data_complete_cases$log_processing_speed_task <- log(data_complete_cases_new$processing_speed_task)

#COMPARE HISOGRAMS AND QQ FROMS BEFORE TRANSFORMATION VS AFTER TRANSFORMATION
#HISTOGRAMS
ggplot(data_complete_cases, aes(x = processing_speed_task)) +
  geom_histogram(bins = 30)
ggplot(data_complete_cases, aes(x = log_processing_speed_task)) +
  geom_histogram(bins = 30)

#QQ PLOTS
ggplot(data_complete_cases, aes(sample = processing_speed_task)) +
  stat_qq() +
  stat_qq_line()
ggplot(data_complete_cases, aes(sample = log_processing_speed_task)) +
  stat_qq() +
  stat_qq_line()

#WHERE A NEGATIVE SKEW IS PRESENT AND REFLECTION IS REQUIRED BEFORE TRANSFORMATION IS APPLIED
#REFLECTION CODE
data_complete_cases$processing_speed_task_reflected <-
  max(data_complete_cases$processing_speed_task) -
  data_complete_cases$processing_speed_task + 1
```
