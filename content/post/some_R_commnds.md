---
title: "Some R commands"
date: 2022-04-24T22:25:37+05:30
draft: false
author: Arshad
---


## Counting the occurance of individuals values in a variable.

```{r}
df_merged_labour %>% select(xss) %>% group_by(xss) %>% count()
```

## convert a vector into comma separated character vector

```{r}
rs <- paste("\"",as.character(vector),"\"",collapse=", ",sep="")
cat(rs)
```
