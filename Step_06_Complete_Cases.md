```{r}
#STEP 6 - GET THE COMPLETE CASES NUMBER AND THE EXACT TESTS/DOMAINS MAXIMISING THE SAMPLE
#THIS CODE PRODUCES THE NUMBER OF COMPLETE CASES IF A MINIMUM OF N DOMAINS WERE APPLIED:
#I.E. 200 COMPLETE SAMPLES WOULD BE CARRIED FORWARD FOR ANALYSIS WHERE A MINIMUM OF 3 DOMAINS WAS IN PLACE

#THIS CODE WILL TELL YOU THE NUMBER OF COMPLETE CASES IF 2/3/4/5/6 DOMAINS WERE USED - HELPS THE DECISION MAKING PROCESS ON THE NUMBER OF TESTS/DOMAINS CAN BE INCLUDED WHILE STILL MAXIMISING THE SAMPLE - SEE PROTOCOL 

library(tidyverse)

#INPUT TESTS HERE ACCORDING TO THEIR PRIMARY COGNITIVE DEMAND
#ADD MORE DOMAINS WHERE NECESSARY
domains <- list(
  verbal = c("verbal_learning_task"),
  processing = c("processing_speed_task"),
  executive = c("executive_function_task"),
  working_mem = c("wokring_memory_task")
)

all_nonempty_subsets <- function(x) {
  unlist(
    lapply(1:length(x), function(k) combn(x, k, simplify = FALSE)),
    recursive = FALSE
  )
}

results <- list()

for (min_domains in 2:length(domains)) {

  all_domain_sets <- unlist(
    lapply(min_domains:length(domains),
           function(k) combn(names(domains), k, simplify = FALSE)),
    recursive = FALSE
  )

  for (dcombo in all_domain_sets) {

    domain_test_sets <- lapply(dcombo, function(d) {
      all_nonempty_subsets(domains[[d]])
    })


    test_grid <- expand.grid(
      domain_test_sets,
      KEEP.OUT.ATTRS = FALSE,
      stringsAsFactors = FALSE
    )

    colnames(test_grid) <- dcombo

    for (i in seq_len(nrow(test_grid))) {

  
      tests <- unlist(as.list(test_grid[i, ]), recursive = TRUE)

      n_complete <- sum(
        complete.cases(
         data_cases_filtered_age[, tests, drop = FALSE] #ADD DATAFRAME HERE
        )
      )

      results[[length(results) + 1]] <- tibble(
        min_domains = min_domains,
        actual_domains = length(dcombo),
        domains_used = paste(dcombo, collapse = " + "),
        n_tests = length(tests),
        tests = paste(tests, collapse = " + "),
        n = n_complete
      )
    }
  }
}

results_df <- bind_rows(results)

#NAME ACCORDINGLY
best_results_data <- results_df %>%
  arrange(desc(n), desc(min_domains), desc(n_tests))

best_results_data
```

```{r}
#write out the file and save the combinations 
setwd("/set/working/directory")
write.table(best_results_data,
            file = "cog_test_combination_data.txt",
            sep = "\t",
            row.names = FALSE,
            quote = FALSE)
```
