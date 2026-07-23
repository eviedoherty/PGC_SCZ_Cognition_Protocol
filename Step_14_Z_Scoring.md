```{r}
#STEP 14 - STANDARDISING SCORES
######## Z SCORES ########

cognitive_domains <- c(
  "age_resid_logical_mem_1",
  "age_resid_logical_mem_2",
  "age_resid_logical_mem_3"
)

for (domain in cognitive_domains) {
  dublin_complete_cases[[paste0("z_score_", sub("^age_resid_", "", domain))]] <-
    as.numeric(scale(dublin_complete_cases[[domain]]))
}
