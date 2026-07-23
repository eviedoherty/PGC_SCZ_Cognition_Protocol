```{r}
#FUNCTION
flag_and_replace_outliers <- function(data, measures, id_var = NULL) {

  data_clean <- data

  means <- sapply(data[measures], mean, na.rm = TRUE)
  sds   <- sapply(data[measures], sd, na.rm = TRUE)

  lower_3sd <- means - 3 * sds
  upper_3sd <- means + 3 * sds

  cutoffs <- data.frame(
    measure = measures,
    mean = means,
    sd = sds,
    lower_3sd = lower_3sd,
    upper_3sd = upper_3sd
  )

  replacements <- data.frame()

  for (measure in measures) {

    lower <- lower_3sd[measure]
    upper <- upper_3sd[measure]

    outlier_rows <- which(
      data_clean[[measure]] < lower |
      data_clean[[measure]] > upper
    )

    if (length(outlier_rows) == 0) next

    valid_values <- data_clean[[measure]][
      data_clean[[measure]] >= lower &
      data_clean[[measure]] <= upper
    ]

    for (row in outlier_rows) {

      old_value <- data_clean[[measure]][row]

      new_value <- valid_values[
        which.min(abs(valid_values - old_value))
      ]

      replacements <- rbind(
        replacements,
        data.frame(
          row = row,
          measure = measure,
          old_value = old_value,
          new_value = new_value
        )
      )

      data_clean[[measure]][row] <- new_value
    }
  }


  participant_results <- lapply(seq_len(nrow(data)), function(i) {

    scores <- as.numeric(data[i, measures])

    outlier_idx <- which(
      scores < lower_3sd | scores > upper_3sd
    )

    data.frame(
      row = i,
      outliers_3sd = paste(measures[outlier_idx], collapse = ", "),
      n_outliers_3sd = length(outlier_idx),
      remove_flag = length(outlier_idx) > 0
    )
  })

  participant_results <- do.call(rbind, participant_results)

  if (!is.null(id_var)) {
    participant_results <- cbind(
      ID = data[[id_var]],
      participant_results
    )
  }

  return(list(
    cleaned_data = data_clean,
    participant_results = participant_results,
    cutoffs = cutoffs,
    replacements = replacements
  ))
}

```

```{r}
#FUNCTION IN USE 

outliers_data_all <- flag_and_replace_outliers(
  data = data_complete_cases,
  measures = c("verbal_learning_task", 
               "processing_speed_task", 
               "working_memory_task"),
               "executive_function_task") #adjust to match cognitive measure column names in your dataset
  id_var = "ID_colname" #adjust to match individual ID column name in your dataset
)
```

```{r}
#VIEW THE CUTOFF THRESHOLDS
outliers_data_all$cutoffs
```

```{r}
#VIEW THE ROWS FLAGGED FOR WINSORISATION
subset(outliers_data_all$participant_results, remove_flag)
```

```{r}
#ALLOWS YOU TO CHECK THE BEFORE AND AFTER VALUES TO ENSURE THE FUNCTION PERFORMED AS EXPECTED
outliers_data_all$replacements
```

```{r}
#CREATE NEW DATAFRAME CONTAINING THE WINSORISED VALUES
data_complete_cases_clean <- outliers_data_all$cleaned_data
```



