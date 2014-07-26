Getting and cleaning data course project 
========================================

written and programmed by Sergey Prykhozhij

Explanation for the steps in the script run_analysis.R
------------------------------------------------------

### Reading and preparation for merging test and training dataset
This corresponds to "1. Merges the training and the test sets to create one data set."

The files were read by read.table function. Vectors for activities and assignments were populated by explicit
assignment ```subjects <- vector(); subjects[1:2947] <- subject_test[1:2947,]```. rbind function was used combining data frames.
The complete dataset was constructed using the cbind function in the next step.

### Extracting only the measurements on the mean and standard deviation for each measurement.

I manually extracted which measurements correspond to mean and standard deviation for different physical measurements.
The numbers of the columns were then used for making a selection from the data frame.

### Adding descriptive activity names to name the activities in the data set

Activities were labeled with the corresponding words using such code as this ```activity[activity== 1] <- "WALKING"```

### Labeling the data set with descriptive variable names.

The function ```colnames(full_dataset) <- c("activity", "subject", "tBodyAcc-mean()-X",...)``` was used for this purpose

### Creating a second, independent tidy data set with the average of each variable for each activity and each subject.

The function aggregate() was used for creating this dataset. This function can average the values for all measurement 
variables for the same subject and activity. The initial output of the aggregate function has been subsetted to remove
unnecessary columns and the column names have been re-labeled as before.
