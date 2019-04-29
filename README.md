# Madrid-Air-Quality-Project

# Project Overview
Air pollutants have increased received a lot of scrutiny over the years.  For
this analysis, I used the Madrid Air Quality dataset.  There were two sets of
files.  One was for the years 2008-2018 and the other a single file for all
the stations that were used.  For more information about the datasets you
can go here. [Air Quality in Madrid](https://www.kaggle.com/decide-soluciones/air-quality-madrid)

# Prepping and cleaning the dataset.

For my analysis I used R to clean and create a single file that would be used
throughout my analysis.  After combine all the years there where more than
three million observations.  
Here is the code I used for this
filenames <- list.files(path = "./", pattern = ".csv", full.names=TRUE)
MadridSingleFile <- ldply(filenames, read.csv)

MadridSingleFile<- data.frame(MadridSingleFile)

# EDA (exploratory data analysis)

As I stated above I used for my analysis.  Here are a view examples of the
graphs I used.

![]()



# Analysis

Due to the number of observations I had to limit the size of my observations.  In my analysis, I used only one of the four main pollutants.  I will be using NO_2 for the forecasting

Here's the code I used.

group_ts <- sqldf("select *
                  from MadridSingleFile
                  where year > 2016 and (NO_2) < 150
                  group by day, month, year")
