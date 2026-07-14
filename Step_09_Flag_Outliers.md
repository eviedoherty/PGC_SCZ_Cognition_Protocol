```{r}
#STEP 9 - FLAG THE OUTLIERS FOR REMOVAL 
#WRITTEN FUNCTION

flag_outliers_raw <- function(data, measures, id_var = NULL) {

  means <- sapply(data[measures], mean, na.rm = TRUE)
  sds   <- sapply(data[measures], sd, na.rm = TRUE)

  lower_3sd <- means - 3 * sds
  upper_3sd <- means + 3 * sds

  results <- lapply(seq_len(nrow(data)), function(i) {

    scores <- as.numeric(data[i, measures])

    outlier_idx <- which(scores < lower_3sd | scores > upper_3sd)
    outlier_measures <- measures[outlier_idx]

    remove_flag <- length(outlier_measures) > 0

    data.frame(
      row = i,

      outliers_3sd = paste(outlier_measures, collapse = ", "),

      n_outliers_3sd = length(outlier_measures),

      remove_flag = remove_flag,

      stringsAsFactors = FALSE
    )
  })

  results <- do.call(rbind, results)

  if (!is.null(id_var)) {
    results <- cbind(ID = data[[id_var]], results)
  }

  cutoffs <- data.frame(
    measure = measures,
    mean = means,
    sd = sds,
    lower_3sd = lower_3sd,
    upper_3sd = upper_3sd
  )

  flagged_ids <- NULL
  if (!is.null(id_var)) {
    flagged_ids <- unique(data[[id_var]][results$remove_flag])
  } else {
    flagged_ids <- results$row[results$remove_flag]
  }

  return(list(
    participant_results = results,
    cutoffs = cutoffs,
    flagged_ids = flagged_ids
  ))
}

#FUNCTION IN USE 
#verbal_learning_task, processing_speed_task, working_memory_task, executive_function_task

outliers_data_all <- flag_outliers_raw(
  data = data_complete_cases,
  measures = c("verbal_learning_task", 
               "processing_speed_task", 
               "working_memory_task", 
               "executive_function_task"),
  id_var = "ID_colname"
)

# Participants flagged for removal
subset(outliers_data_all$participant_results, remove_flag)

# View cutoffs used for each measure
outliers_data_all$cutoffs
```

