```{r}
#STEP 14 - STANDARDISING SCORES
######## Z SCORES ########

cognitive_domains <- c(
"log_processing_speed_task_oriented",
"verbal_learning_task",
"working_memory_task",
"executive_function_task"
)

for (domain in cognitive_domains) {
  data_complete_cases_clean[[paste0("z_score_", sub("^age_resid_", "", domain))]] <-
    as.numeric(scale(dublin_complete_cases[[domain]]))
}
