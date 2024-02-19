# MVA_Assignment_1


---
title: "MVA Assignment_1"
author: "Deviprasad Saka"
date: "2024-02-15"
output: html_document
---
1.Ask an important question you want answered?
i. What is the relationship between the Cost_of_Living_Index (independent variable)
and the Happiness_Score (dependent variable) in regions?
ii. How does the availability of green space (Green_Space_Area)
correlate with air quality (Air_Quality_Index) in the studied area?

2.Answer why this question(s) is/are important to you?
i. Cost of Living and Happiness Score Relationship: Knowing the human relationship
kind out of the Cost_of_Living_Index and the Happiness_Score in regions with various
economic. It serves for measuring the availability of common amenities (such as rent, 
doors, water, etc.) that influence the living conditions and mood of the members of society.
This knowledge shall be used for resolve the problem of social inequality and further
improve life standards of all community members irrespective of economic status.

ii. Green Space and Air Quality Correlation: Answering the query on whether Green_Space_Area 
and Air_Quality_Index are connected is necessary for environmental. Green platforms are
among the directions in which the breathing becomes pure again as they suck out pollutants
physically and improve air quality. It has great significance for in making decisions on the
preservation and expansion of green areas to support the healthier living conditions for
negative reasons pollution can affect the health of a person.


```{r}
# Provide the file path to CSV file
file_path <- "D:/Multivariate Analysis/Assignment-1/train US new.csv"

# Import the CSV file into R
data <- read.csv(file_path)

# View the imported data
print(data)
```
![](plots/DS.png)<!-- -->


---
3.Find and collect data (need one dependent variable and more than 3 independent variables)?
Dependent variable: Happiness_Score
Independent variables: Decibel_Level, Traffic_Density, Green_Space_Area,
Air_Quality_Index, Cost_of_Living_Index, Healthcare_Index

The Happiness Score is likely to be influenced by factors such as 
noise level (Decibel_Level), traffic density (Traffic_Density), availability of
green spaces (Green_Space_Area), air quality (Air_Quality_Index), cost of living (Cost_of_Living_Index),
and healthcare quality (Healthcare_Index). Therefore, the Happiness Score is the dependent variable,
while the rest are independent variables

4.Describe your data ?
Decibel_Level (Integer): It could be, in fact, that the referred factor is the
indicator of noise level of some specific territory. Decibel level assignment is
the most widespread world-wide; this normally means the louder atmosphere.

Traffic_Density (Character): This variable apparently is about the traffic on the block
in a given area

Green_Space_Area (integer): The alternating green value evidently contains information
on the degree of green space or vegetation cover in the said area. The concept of green 
area could be park, garden, or any natural area availability.

Air_Quality_Index (Integer): Likely, the dispersion of different types of gases is monitored 
through the analysis of atmospheric conditions in a selected area. Air quality index (AQI) is 
a commonly used standardize parameter which conveys the severity of air pollution and the
consequent health issues.

Happiness_Score (Num): That variation just could be an index of the subjectively perceiving 
emotional state or happiness of a particular area. 

Cost_of_Living_Index (Integer): This variable is most likely to be interpreted as the expense
area of a particular locality. It generally higher level considers the issues of a place to live,
food, utilities, car and trips, emergency care.

Healthcare_Index (Integer): The inconstant factor could be both the quality of healthcare or the
ease of access in the specified settings. The main components of a healthcare index may include 
the number of healthcare facilities operating, healthcare professionals available, medical
technology in use and the overall quality of patient outcomes.


---
```{r}
Q1: What is the relationship between the Cost_of_Living_Index (independent variable) and
the Happiness_Score (dependent variable) ?

# Load required libraries
library(ggplot2)
library(dplyr)

# Calculate correlation coefficient
correlation <- cor(data$Cost_of_Living_Index, data$Happiness_Score)

# Print correlation coefficient
print(correlation)
```
![](plots/cor1.png)<!-- -->

```{r}
Result: Correlation coefficient of 0.4595364 indicates a moderate positive correlation between
Cost_of_Living_Index and Happiness_Score, meaning they tend to move together in the same direction to a moderate degree.
```

```{r}
# Plot the correlation
plot(data$Cost_of_Living_Index, data$Happiness_Score,
     xlab = "Cost of Living Index",
     ylab = "Happiness Score",
     main = "Correlation between Cost of Living Index and Happiness Score",
     col = "red")
```
![](plots/Rplot01.png)<!-- -->

```{r}
Q2: How does the availability of green space (Green_Space_Area) 
correlate with air quality (Air_Quality_Index) in the studied area?


# Calculate the correlation coefficient
correlation <- cor(data$Green_Space_Area, data$Air_Quality_Index)

# Print the correlation coefficient
print(correlation)
```
![](plots/cor2.png)<!-- -->

```{r}
Result: A correlation coefficient of -0.4092952 indicates a moderate negative correlation
 between Green_Space_Area and Air_Quality_Index.
```


```{r}
# Plot the correlation
plot(data$Green_Space_Area, data$Air_Quality_Index,
     xlab = "Green space area",
     ylab = "Air quality",
     main = "Correlation between Green space area and Air quality",
     col = "blue")
```
![](plots/Rplot.png)<!-- -->

```
Title: 'Exploratory Data Analysis (EDA): Visualization'
```

```{r}
# Provide the file path to CSV file
file_path <- "D:/Multivariate Analysis/Assignment-1/train US new.csv"

# Import the CSV file into R
data <- read.csv(file_path)

# View the imported data
print(data)
```

![](plots1/dataset.png)<!-- -->


```{r}
hist(data$Air_Quality_Index)
```

![](plots1/Hist.png)<!-- -->

```{r}
plot(density(data$Air_Quality_Index))
```

![](plots1/Denplot.png)<!-- -->


```{r}
library(ggplot2)

ggplot(data, aes(x = Traffic_Density, y = Air_Quality_Index)) +
  stat_summary(fun = mean, geom = "bar", fill = "blue")
```

![](plots1/bar.png)<!-- -->


```{r}

# Calculate correlation coefficient
correlation_coefficient <- cor(data$Cost_of_Living_Index, data$Happiness_Score)
# Plot scatter plot
ggplot(data, aes(x = Cost_of_Living_Index, y = Healthcare_Index)) +
  geom_point(color = "blue") +
  geom_smooth(method = "lm", se = FALSE) +  # Add linear regression line
  labs(title = "Relationship between Cost of Living Index and Happiness Score",
       x = "Cost of Living Index",
       y = "Happiness Score") +
  annotate("text", x = Inf, y = Inf, 
           label = paste("Correlation coefficient:", round(correlation_coefficient, 2)), 
           hjust = 1, vjust = 1, size = 4, color = "red")
```
![](plots1/correlation.png)<!-- -->


```{r}

# Install and load the GGally package
library(GGally)
# Select the relevant variables from your dataset
selected_vars <- c("Decibel_Level", 
                   "Air_Quality_Index", "Healthcare_Index")
# Create a pair plot
pairs(data[selected_vars])
```
![](plots1/pairplot.png)<!-- -->






