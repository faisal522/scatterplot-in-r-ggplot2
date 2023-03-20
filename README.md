# scatterplot-in-r-ggplot2
Quick and easy way to create scatterplots using GGPLOT2 
#Install required packages 
install.packages(grid)
install.packages("gridExtra")
install.packages("cowplot")
install.packages(survival
install.packages("survminer")
install.packages(ggplot2)

#load installed packages 

library(grid)
library("gridExtra")
library("cowplot")
library(survminer)
library(survival)
library(ggplot2)

#Set working directory 
set wd(C:/Users/Desktop/cities15000)
#read desired file in any formate (I prefer text)
data <- read.delim("FILE NAME.txt")
names(data)
head(data)
str(data)

A: ANY variable you want to plot on x axis
B: ANY variable you want to plot on y axis
color: A catagrical variable (if you want to group data based on species, gender, profession, city etc.) 
palette: any color scheme (e.g. COSMIC, jco, Star Trek), can also be used in ggplot 2 
reg.line: if you want to add regression line 

#Following code will generate basic version of sccater plot 

ggscatter(data, x = "A", y = "B",color = "Species",
                palette = "jco",add = "reg.line", shape = "Species",
                size = 5, alpha = 0.6)+ border()     
  
  
#Lets Change shape and colors of groups=Species 
ggscatter(
  data,
  x= "A", y= "B",
  fill = "Species", col="Species",
  shape = 21,color = "black", # outer color of shape is black
  size = 5,
  add = "reg.line",
  conf.int = F,conf.int.level = 0.95,
  title="Scatterplot between A and B ",font.title =15,
  xlab="A (Unit)",font.x=25,font.legend = 25,
  ylab = "B (Unit)",font.y=25,
  palette = c("black", "#FC4E07","grey"))+stat_cor(aes(color = Species)) 
  
 #Lets not seprate groups 
 
 ggscatter(data,
  x= "A", y= "B",
  fill = "Species",
  shape = 21,
  size = 5,
  add = "reg.line",
  cor.coef = TRUE, #this will add cofficient of correlation in chart 
   title="Scatterplot between A and B",font.title =15,
  xlab="A (m2)",font.x=25,font.legend = 25,
  ylab = "B (m2)",font.y=25,
  palette = c("black", "#FC4E07","grey")) 

# if you want to plot two charts togather,lets say S1 is sccaterplot with groups and S2 is plot without groups 
We may use 
ggarrange(s1, s2, ncol = 2)
