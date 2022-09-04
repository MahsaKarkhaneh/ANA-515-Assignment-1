# ANA-515-Assignment-1
---
title: "ANA 515 Assignment 1"
author: "Mahsa Karkhaneh"
date: '2022'
output: 
  html_document:
    theme: 
      bootswatch: darkly
---

```{r setup, include=FALSE}
knitr::opts_chunk$set(echo = TRUE)
library(tidyverse)
library(knitr)
library(bslib)
library(dplyr)
library(ggplot2)
```

```{r gun_deaths , echo=FALSE}
url <- "https://raw.githubusercontent.com/fivethirtyeight/guns-data/master/full_data.csv"
gun_deaths <- read_csv(url)
```

```{r, echo = TRUE}
youth <- gun_deaths %>% 
  filter(age <= 65)
```

```{r, include=FALSE}
summary(youth)
```

We have data about `r nrow(gun_deaths)` gun_deaths. Only 
`r nrow(gun_deaths) - nrow(youth)` are older than
65. The distribution of the remainder is shown
below:

```{r, youth-dist, echo = FALSE}
youth %>% 
  ggplot(aes(age)) + 
  geom_freqpoly(binwidth = 1)
```

```{r, race-dist, echo = FALSE}
youth %>% 
  ggplot(aes(fct_infreq(race)%>% fct_rev())) + 
  geom_bar()+coord_flip()+labs(x="Victim race")
```

[New Text Document.txt](https://github.com/MahsaKarkhaneh/ANA-515-Assignment-1/files/9485494/New.Text.Document.txt)
[week2.docx](https://github.com/MahsaKarkhaneh/ANA-515-Assignment-1/files/9485495/week2.docx)
