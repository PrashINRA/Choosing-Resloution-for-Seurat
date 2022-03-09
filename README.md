# Choosing-Resloution-for-Seurat

# Choice of resolution parameter might be tricky as it decides the number of cluster you are going to get.
Single-cell clusters are mathematical constructs while cell types are biological truth. There must be a consensus between biology and mathematics to interpret single-cell clusters. Clustree is an R package which could be used on Seurat to see different number of clusters at different resolution and avoid noisy resolution. Afterwards, a prior biological knowledge of the data could be used to get the optimal  number of clusters.

```{r}
library(clustree)
#Take a preprocessed seurat object
Seurat <- FindClusters(Seurat, resolution =  seq(from = 0.1, to = 0.9, by = 0.1))
clust_seurat <- Seurat@meta.data %>% dplyr::select(dplyr::contains("RNA_snn_res."))
clustree(clust_seurat, prefix="RNA_snn_res.")
```
#This Will Generate a tree of cluster with different reolution
![tree_seu](https://user-images.githubusercontent.com/26623347/157477760-bc77d82e-d31e-4788-978d-13b82df29873.png)
