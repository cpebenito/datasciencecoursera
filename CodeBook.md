###“Getting and Cleaning Data” Course Project Code Book
Submitted by: Chuck Pe Benito (student)
Date Submitted: 2/22/2015

This documentation is being prepared to put together a CODE BOOK that will describe the variables, data, and any transformations or work detail that I performed to complete the requirements of the project from the data I gathered from the dataset described below:
######Source :
==================================================================
Human Activity Recognition Using Smartphones Dataset
######Version 1.0
==================================================================
Jorge L. Reyes-Ortiz, Davide Anguita, Alessandro Ghio, Luca Oneto.
Smartlab - Non Linear Complex Systems Laboratory
DITEN - Università degli Studi di Genova.
Via Opera Pia 11A, I-16145, Genoa, Italy.
activityrecognition@smartlab.ws
www.smartlab.ws
==================================================================
######License:
========
Use of this dataset in publications must be acknowledged by referencing the following publication [1] 
[1] Davide Anguita, Alessandro Ghio, Luca Oneto, Xavier Parra and Jorge L. Reyes-Ortiz. Human Activity Recognition on Smartphones using a Multiclass Hardware-Friendly Support Vector Machine. International Workshop of Ambient Assisted Living (IWAAL 2012). Vitoria-Gasteiz, Spain. Dec 2012
This dataset is distributed AS-IS and no responsibility implied or explicit can be addressed to the authors or their institutions for its use or misuse. Any commercial use is prohibited.
Jorge L. Reyes-Ortiz, Alessandro Ghio, Luca Oneto, Davide Anguita. November 2012.
For more information about this original dataset 
contact: activityrecognition@smartlab.ws

###Dataset and Collection description as provided by the original authors:
The experiments have been carried out with a group of 30 volunteers within an age bracket of 19-48 years. Each person performed six activities (WALKING, WALKING_UPSTAIRS, WALKING_DOWNSTAIRS, SITTING, STANDING, LAYING) wearing a smartphone (Samsung Galaxy S II) on the waist. Using its embedded accelerometer and gyroscope, we captured 3-axial linear acceleration and 3-axial angular velocity at a constant rate of 50Hz. The experiments have been video-recorded to label the data manually. The obtained dataset has been randomly partitioned into two sets, where 70% of the volunteers was selected for generating the training data and 30% the test data. 
The sensor signals (accelerometer and gyroscope) were pre-processed by applying noise filters and then sampled in fixed-width sliding windows of 2.56 sec and 50% overlap (128 readings/window). The sensor acceleration signal, which has gravitational and body motion components, was separated using a Butterworth low-pass filter into body acceleration and gravity. The gravitational force is assumed to have only low frequency components, therefore a filter with 0.3 Hz cutoff frequency was used. From each window, a vector of features was obtained by calculating variables from the time and frequency domain. See 'features_info.txt' for more details. 
######For each record it is provided:
======================================
- Triaxial acceleration from the accelerometer (total acceleration) and the estimated body acceleration.
- Triaxial Angular velocity from the gyroscope. 
- A 561-feature vector with time and frequency domain variables. 
- Its activity label. 
- An identifier of the subject who carried out the experiment.
***More information about the dataset is provided in the original README.txt file

###Files used by the student (myself) to complete the project:

The original dataset includes multiple files, but only the following files were utilized:
=========================================
- 'README.txt': to determine the purpose of the experiment and the descriptions of the related files
- 'features_info.txt': Shows information about the variables used on the feature vector
- 'features.txt': List of all features used in the experiment, from which only the required variables were selected for the completion of the project.
- 'activity_labels.txt': Links the class labels with their activity name.
- 'train/X_train.txt': Training set.
- 'train/y_train.txt': Training labels.
- 'test/X_test.txt': Test set.
- 'test/y_test.txt': Test labels.
- 'train/subject_train.txt': Each row identifies the subject who performed the activity for each window sample. Its range is from 1 to 30. 

Note: All the other files under the Inertial Signals folder were not utilized for this project.

How to access the Project:

The link to the script file, README.md, and this Code Book can be found on my GitHub datascience repository located at:

https://github.com/cpebenito/datasciencecoursera

run.analysis.R 	= 	script file that will generate the project’s required outcome.
README.md 	= 	details the approach I used to come up with the project’s requirements.
Codebook.md 	= 	This codebook. Details the data, transformation I made to the original data, and the     variable names used for this project.

###Data, Value and Variable names used in the project:
 
While the detailed explanation of the approach I used is discussed in the included README.md file in my GitHub repo, below are the descriptions of the data, values, and variable names I used in the project.

After running my “run.analysis.R” script the following data and values will be generated:

1.	“train_set” - contains the raw data from the original “X_train.txt” file, but with the added column names from the “features.txt” file.

2.	“train_subj” – contains the original subject_train.txt file where each row identifies the subject who performed the activity for each window sample. Its range is from 1 to 30.

3.	“train_label” –– contains the observations provided in the original “y_train.txt” file with the activity descriptive names instead of the numerical codes.

4.	“test_set”  -  contains the raw data from the original “X_test.txt” file, but with the added column names from the “features.txt” file.

5.	“test_subj” – contains the original subject_test.txt file where each row identifies the subject who performed the activity for each window sample. Its range is from 1 to 30.

6.	“test_label” – contains the observations provided in the original “y_test.txt” file with the activity descriptive names instead of the numerical codes.

7.	“features” – contains all the 561 variable names of the observations gathered in the original experiment. The complete list of names are listed in the features.txt file that came with the dataset.

8.	“activity_labels” – contains the original content of the activity_label.txt file that contains 6 descriptive names of the activities performed by the subjects ("WALKING", "WALKING_UPSTAIRS", "WALKING_DOWNSTAIRS", "SITTING", "STANDING", "LAYING")

9.	“train_set_table” – contains the tidied TRAIN set data with the columns “subject” and “activity” added to the table.

10.	“test_set_table” – contains the tidied TEST set data with the columns “subject” and “activity” added to the table.

11.	”valid_names_test” – contains the valid variable names of the test_set_table (#10) after applying the make.names() function. This enabled the process of selecting only the columns that contains “mean” and “std” description.

12.	“test_mean_std” – contains the tidied test set table (#10) with the needed column names (subject, activity, and all columns with “mean” and “std” on the description).

13.	“valid_names_train” –– contains the valid variable names of the train_set_table (#9) after applying the make.names() function. This enabled the process of selecting only the columns that contains “mean” and “std” description.

14.	“train_mean_std” – contains the tidied train set table (#9) with the needed column names (subject, activity, and all columns with “mean” and “std” on the description).

15.	“tidy_train_test_data” – contains the joined “train_mean_std” (#14) and “test_mean_std” (#12) data

16.	“tidy_summary”  -  independent tidy data set with the average of each variable for each activity and each subject.

17.	“tidy_sum” – data provided by the write.table() function to convert the “tidy_summary” data into a .txt file for project submission.

18.	“names” –  shows the complete list of 88 column names (features) I selected for the final tidy data set, “tidy_summary” (#16). Here are the final columns for the “tidy_summary” data.

[1] "activity"                             			"subject"
[3] "tBodyAcc.mean...X"                    		"tBodyAcc.mean...Y"
[5] "tBodyAcc.mean...Z"                  		 "tGravityAcc.mean...X"
[7] "tGravityAcc.mean...Y"                		 "tGravityAcc.mean...Z"
[9] "tBodyAccJerk.mean...X"              		 "tBodyAccJerk.mean...Y"
[11] "tBodyAccJerk.mean...Z"          		 "tBodyGyro.mean...X"
[13] "tBodyGyro.mean...Y"                  		 "tBodyGyro.mean...Z"
[15] "tBodyGyroJerk.mean...X"              		 "tBodyGyroJerk.mean...Y"
[17] "tBodyGyroJerk.mean...Z"             		  "tBodyAccMag.mean.."
[19] "tGravityAccMag.mean.."             		  "tBodyAccJerkMag.mean.."
[21] "tBodyGyroMag.mean.."                 		  "tBodyGyroJerkMag.mean.."
[23] "fBodyAcc.mean...X"                    		  "fBodyAcc.mean...Y"
[25] "fBodyAcc.mean...Z"                   		 "fBodyAcc.meanFreq...X"
[27] "fBodyAcc.meanFreq...Y"              		  "fBodyAcc.meanFreq...Z"
[29] "fBodyAccJerk.mean...X"               		  "fBodyAccJerk.mean...Y"
[31] "fBodyAccJerk.mean...Z"               		  "fBodyAccJerk.meanFreq...X"
[33] "fBodyAccJerk.meanFreq...Y"       		   "fBodyAccJerk.meanFreq...Z"
[35] "fBodyGyro.mean...X"                		   "fBodyGyro.mean...Y"
[37] "fBodyGyro.mean...Z"                 		   "fBodyGyro.meanFreq...X"
[39] "fBodyGyro.meanFreq...Y"           		    "fBodyGyro.meanFreq...Z"
[41] "fBodyAccMag.mean.."                 		    "fBodyAccMag.meanFreq.."
[43] "fBodyBodyAccJerkMag.mean.."      		    "fBodyBodyAccJerkMag.meanFreq.."
[45] "fBodyBodyGyroMag.mean.."              		   "fBodyBodyGyroMag.meanFreq.."
[47] "fBodyBodyGyroJerkMag.mean.."        		   "fBodyBodyGyroJerkMag.meanFreq.."
[49] "angle.tBodyAccMean.gravity."         		   "angle.tBodyAccJerkMean..gravityMean."
[51] "angle.tBodyGyroMean.gravityMean."  		   "angle.tBodyGyroJerkMean.gravityMean."
[53] "angle.X.gravityMean."               		   "angle.Y.gravityMean."
[55] "angle.Z.gravityMean."              		   "tBodyAcc.std...X"
[57] "tBodyAcc.std...Y"                  			   "tBodyAcc.std...Z"
[59] "tGravityAcc.std...X"                 		   "tGravityAcc.std...Y"
[61] "tGravityAcc.std...Z"                			   "tBodyAccJerk.std...X"
[63] "tBodyAccJerk.std...Y"           			   "tBodyAccJerk.std...Z"
[65] "tBodyGyro.std...X"               			   "tBodyGyro.std...Y"
[67] "tBodyGyro.std...Z"                			   "tBodyGyroJerk.std...X"
[69] "tBodyGyroJerk.std...Y"            		   "tBodyGyroJerk.std...Z"
[71] "tBodyAccMag.std.."                  		   "tGravityAccMag.std.."
[73] "tBodyAccJerkMag.std.."            		   "tBodyGyroMag.std.."
[75] "tBodyGyroJerkMag.std.."           		   "fBodyAcc.std...X"
[77] "fBodyAcc.std...Y"                    			   "fBodyAcc.std...Z"
[79] "fBodyAccJerk.std...X"           			   "fBodyAccJerk.std...Y"
[81] "fBodyAccJerk.std...Z"             			   "fBodyGyro.std...X"
[83] "fBodyGyro.std...Y"                 			   "fBodyGyro.std...Z"
[85] "fBodyAccMag.std.."                 		   "fBodyBodyAccJerkMag.std.."
[87] "fBodyBodyGyroMag.std.."           		   "fBodyBodyGyroJerkMag.std.."

For a detailed explanation of the features (column names) presented on item #18, please refer to the original authors’ documentation presented on the “features_info.txt” file. The original set of files can be found on this link provided by the Coursera “Getting and Cleaning Data” course website.

https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip



