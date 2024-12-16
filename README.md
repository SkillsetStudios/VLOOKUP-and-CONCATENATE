#R Code
#Load packages
library(readxl)

#Import data
Data_1 <- read_excel("Data.xlsx", sheet = "Main")
Data_2 <- read_excel("Data.xlsx", sheet = "Hours")

#View the imported data
View(Data_1)
View(Data_2)

#CONCATENATE in R
Data_1$Account<-paste(Data_1$`Account 1`, Data_1$`Account 2`, Data_1$`Account 3`, sep="-")
View(Data_1)

#Remove Account 1, Account 2, and Account 3
Updated_Data<-Data_1[,!(names(Data_1) %in% c("Account 1", "Account 2", "Account 3"))]
View(Updated_Data)

#VLOOKUP in R
Result<-merge(Updated_Data,Data_2, by="Employee Name")
View(Result)
