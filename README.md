# SamsungGalaxyS Project
See Codebook.

Run script run_analysis.R

##Getting-and-Cleaning-Data
####Script:  run_analysis.R
library(dplyr)
library(tidyr)
library(data.table)

####Download and unzip data set
if(!file.exists("./SamsungGalaxS.zip")){
	url <- "https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip"
	download.file(url, "SamsungGalaxyS.zip")
	unzip("SamsungGalaxyS.zip", exdir="SamsungGalaxyS") #creade data directory
}

####Read test and training data
x_test <- read.table("./SamsungGalaxyS/UCI HAR Dataset/test/X_test.txt")
y_test <- read.table("./SamsungGalaxyS/UCI HAR Dataset/test/y_test.txt") 
subject_test <- read.table("./SamsungGalaxyS/UCI HAR Dataset/test/subject_test.txt") 
x_train <- read.table("./SamsungGalaxyS/UCI HAR Dataset/train/X_train.txt")
y_train <- read.table("./SamsungGalaxyS/UCI HAR Dataset/train/y_train.txt")
subject_train <- read.table("./SamsungGalaxyS/UCI HAR Dataset/train/subject_train.txt") 

####Read activity names and feature names
activity <- read.table("./SamsungGalaxyS/UCI HAR Dataset/activity_labels.txt")
features <- read.table("./SamsungGalaxyS/UCI HAR Dataset/features.txt")

####Merge test and traing data and add descriptive names
combine_data_subject <- rbind(subject_train, subject_test)
colnames(combine_data_subject) <- "subjects_number"  
combine_data_x <- rbind(x_train, x_test)
colnames(combine_data_x) <- features$V2  #add feature names
combine_data_y <- rbind(y_train, y_test)
combine_data_y_activity <- merge(combine_data_y, activity, by="V1", sort=FALSE) #add activity names to data
colnames(combine_data_y_activity) <- c("activity_number", "ACTIVITY")
combine_data <- cbind(combine_data_subject, combine_data_y_activity, combine_data_x)

####Extract mean and standard deviation for each measurement
mean_std_rows <- grep("mean()|std()", features$V2) #determine column numbers with mean or std
extracted_data <- combine_data[mean_std_rows, ]

####Create tidy data set with mean of each activity and each subject
 tidy_data <- data.table(extracted_data)[ , lapply(.SD, mean), by="subjects_number,activity_number"]

write.table(tidy_data, file="TidyRunAnalysis.txt", row.name=FALSE)
