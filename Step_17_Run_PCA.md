```{r}
######## RUN PCA ########

setwd("/Set/path/to/working/directory/")
data_for_pca <- read.table("data_complete_cases_for_PCA.txt", header = TRUE, sep = ",",na.strings = "NA")
data_for_pca
```

```{r}
library(psych)
#AT THIS POINT EXECLUDE ANY MEASURE THAT WAS IDENTIFIED AS A WEAK CORRELATE BY THE CRONBACH'S ALPHA (see protocol)

pca_data <- principal(data_for_pca[, c("z_score_processing_speed", "z_score_verbal_learning", "z_score_working_memory", "z_score_executive_function")], nfactors = 2, rotate = "none", scores = TRUE)
```

```{r}
#FACTOR LOADINGS OF EACH VARIABLE
pca_data$loadings
#X% OF VARIANCE
```


```{r}
#PARALLEL ANALYSIS (PSYCH PACKAGE)
fa.parallel(data_for_pca[, c("z_score_processing_speed", "z_score_verbal_learning", "z_score_working_memory", "z_score_executive_function")],
            fa = "pc")
```

```{r}
#ADDING PCA VALUES FOR PC1 TO THE DATASET FOR USE
data_for_pca$g <- pca_data$scores[,1]
data_for_pca
```
