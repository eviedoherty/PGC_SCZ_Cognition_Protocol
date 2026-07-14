```{r}
#STEP 11 - NORMALITY & SKEWNESS CHECKS
#NUMBER OF HISTOGRAMS AND QQ PLOTS = NUMBER OF COGNITIVE MEASURES  
#HISTOGRAM - verbal learning task
library(ggplot2)
ggplot(data_complete_cases, aes(x = verbal_learning_task)) +
  geom_histogram(bins = 30)
```

```{r}
#QQ PLOTS - verbal learning task
ggplot(data_complete_cases, aes(sample = verbal_learning_task)) +
  stat_qq() +
  stat_qq_line()
```


```{r}
#HISTOGRAM - processing speed task
ggplot(data_complete_cases, aes(x = processing_speed_task)) +
  geom_histogram(bins = 30)
```


```{r}
#QQ PLOTS - processing speed task
ggplot(data_complete_cases, aes(sample = processing_speed_task)) +
  stat_qq() +
  stat_qq_line()
```


```{r}
#HISTOGRAM - working memory task
ggplot(data_complete_cases, aes(x = wokring_memory_task)) +
  geom_histogram(bins = 30)
```


```{r}
#QQ PLOTS - working memory task
ggplot(data_complete_cases, aes(sample = working_memory_task)) +
  stat_qq() +
  stat_qq_line()
```


```{r}
#HISTOGRAM - executive function task
ggplot(data_complete_cases, aes(x = executive_function_task)) +
  geom_histogram(bins = 30)
```


```{r}
#QQ PLOTS - executive function task
ggplot(data_complete_cases, aes(sample = executive_function_task)) +
  stat_qq() +
  stat_qq_line()
```

```{r}
#AT THIS POINT, BINARY MEASURES OR THOSE DEMONSTRATING EXTREME FLOOR OR CEILING EFFECTS ARE DROPPED AND STEPS 6-11 ARE REPEATED WITHOUT DROPPED MEASURES
```

