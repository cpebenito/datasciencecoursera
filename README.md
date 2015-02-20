#### datasciencecoursera: Getting and Cleaning Data
This documentation is to present the approach I took in working on the Getting and Cleaning Data course project.
Steps:

1.	Download the data for the project by clicking on the link provided by the course website.
https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip

2.	Unzip files to my working directory.
Note: I kept the files in their respective folders and set the working directory 


according to the file I wanted to read.

3.	Load RStudio program.

4.	Install the packages I needed for this project:

install.packages("tidyr")

install.packages("dplyr")

install.packages("plyr")


library(tidyr)

library(dplyr)

library(plyr)


5.	I loaded all the files that I needed for this project and assigned them to the respective data names.


setwd("~/R/getdata_projectfiles_UCI HAR Dataset/UCI HAR Dataset/train")

train_set <- read.table("~/R/getdata_projectfiles_UCI HAR Dataset/UCI HAR Dataset/train/X_train.txt")

train_subj <- read.table("~/R/getdata_projectfiles_UCI HAR Dataset/UCI HAR Dataset/train/subject_train.txt")

train_label <- read.table("~/R/getdata_projectfiles_UCI HAR Dataset/UCI HAR Dataset/train/y_train.txt")


setwd("~/R/getdata_projectfiles_UCI HAR Dataset/UCI HAR Dataset/test")

test_set <- read.table("~/R/getdata_projectfiles_UCI HAR Dataset/UCI HAR Dataset/test/X_test.txt")

test_subj <- read.table("~/R/getdata_projectfiles_UCI HAR Dataset/UCI HAR Dataset/test/subject_test.txt")

test_label <- read.table("~/R/getdata_projectfiles_UCI HAR Dataset/UCI HAR Dataset/test/y_test.txt")


setwd("~/R/getdata_projectfiles_UCI HAR Dataset/UCI HAR Dataset")

features <- read.table("~/R/getdata_projectfiles_UCI HAR Dataset/UCI HAR Dataset/features.txt")

activity_labels <- read.table("~/R/getdata_projectfiles_UCI HAR Dataset/UCI HAR Dataset/activity_labels.txt")


6.	changed the column name of the subject and label(activity) file:


colnames(test_subj) <- c('subject')

colnames(train_subj) <- c('subject')

colnames(train_label) <- c('activity')

colnames(test_label) <- c('activity')


7.	rename ACTIVITY from numerics to description of activity


train_label$activity<- factor(train_label$activity,
levels = c(1,2,3,4,5,6),
labels = c("WALKING", "WALKING_UPSTAIRS", "WALKING_DOWNSTAIRS", "SITTING", "STANDING", "LAYING"))



test_label$activity<- factor(test_label$activity,
levels = c(1,2,3,4,5,6),
labels = c("WALKING", "WALKING_UPSTAIRS", "WALKING_DOWNSTAIRS", "SITTING", "STANDING", "LAYING"))


8.	rename column names of TRAIN and TEST data sets based on the descriptions provided on the original features.txt file


colnames(train_set) <- features$V2

colnames(test_set) <- features$V2


9.	combine TRAIN variables (files) together 


train_set_table <- bind_cols(train_subj, train_label, train_set)


10.	combine TEST variables (files) together 


test_set_table <- bind_cols(test_subj, test_label, test_set)


11.	convert invalid characters in the column names to valid characters by using make.names() function and then “selecting” only the desirable columns (e.g. subject, activity, “*.mean”, and “*.std”) 


valid_names_test <- make.names(names=names(test_set_table), unique=TRUE, allow_ = TRUE)

names(test_set_table) <- valid_names_test

test_mean_std <- select(test_set_table, subject, activity, contains("mean"), contains("std"))


valid_names_train <- make.names(names=names(train_set_table), unique=TRUE, allow_ = TRUE)

names(train_set_table) <- valid_names_train

train_mean_std <- select(train_set_table, subject, activity, contains("mean"), contains("std"))

12.	Merging the tidied TRAIN and TEST data sets

tidy_train_test_data <- merge(train_mean_std, test_mean_std, all=TRUE)


#######This should satisfy the project requirements 1-4 ############


###Final Step - create a second independent tidy data set with the average of each variable for each activity and each subject.


tidy_summary <- group_by(tidy_train_test_data, activity, subject) %>% summarise_each(funs(mean))

######Transform the independent data to a .txt file for upload to Coursera.

tidy_sum <- write.table(tidy_summary,"~/R/getdata_projectfiles_UCI HAR Dataset/UCI HAR Dataset/tidy_sum.txt", row.names=FALSE)

###### This command just listed the column names used in the “tidy_summary” final file.

names <- data.frame(names(tidy_summary))




