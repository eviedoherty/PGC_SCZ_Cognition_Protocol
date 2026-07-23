```{r}
#STEP 14 - STANDARDISING SCORES
######## Z SCORES ########

cognitive_domains <- c(
"age_resid_processing_speed",
"age_resid_verbal_learning",
"age_resid_working_memory",
"age_resid_executive_function"
)

for (domain in cognitive_domains) {
  data_complete_cases_clean[[paste0("z_score_", sub("^age_resid_", "", domain))]] <- #note that your age residualised cognitive measure variables should be name as follows for this code to work: "age_resid_*_*"
    as.numeric(scale(data_complete_cases_clean[[domain]]))
}
