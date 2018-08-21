# tidy_data
Tidy Data Project - Coursera Week 4

---------------------------------------------------------------------------------------------------------------------------
# Instructions
---------------------------------------------------------------------------------------------------------------------------
You should create one R script called run_analysis.R that does the following.
> Merges the training and the test sets to create one data set.
> Extracts only the measurements on the mean and standard deviation for each measurement.
> Uses descriptive activity names to name the activities in the data set
> Appropriately labels the data set with descriptive variable names.
> From the data set in step 4, creates a second, independent tidy data set with the average of each variable for each activity and each subject.

---------------------------------------------------------------------------------------------------------------------------
# Script with explanation
---------------------------------------------------------------------------------------------------------------------------
#load library for use later
library(dplyr)

#set up file paths
mainpath <- "C:/Users/Sergey/RFiles/uci"    # main folder path
testpath <- "C:/Users/Sergey/RFiles/uci/test"    # test folder path
trainpath <- "C:/Users/Sergey/RFiles/uci/train"  # train folder path

#set working directory
setwd(mainpath)

#### read in data from each file

#training files
tr_sub <- read.table(file.path(trainpath,"subject_train.txt"))
tr_val <- read.table(file.path(trainpath,"X_train.txt"))
tr_act <- read.table(file.path(trainpath,"y_train.txt"))

#testing files
te_sub <- read.table(file.path(testpath,"subject_test.txt"))
te_val <- read.table(file.path(testpath,"X_test.txt"))
te_act <- read.table(file.path(testpath,"y_test.txt"))

#feature files
feat <- read.table(file.path(mainpath, "features.txt"), as.is = TRUE)

#activity 
activ <- read.table(file.path(mainpath, "activity_labels.txt"))
colnames(activ) <- c("ID", "action")

#### aggregate data

f_tr <- cbind(tr_sub, tr_val, tr_act) #training data combine columns
f_te <- cbind(te_sub, te_val, te_act) #testing data combine columns
full <- rbind(f_tr,f_te) #combine rows to create a full set

#give columns some meaningful names, apply the features to column names
colnames(full) <- c("subject",feat[,2],"activ")

#find the mean, and std deviation within the column names
me_st_col <- grepl("subject|activ|mean|std", colnames(full))
clean <- full[,me_st_col] # saves only the relevant columns

#use the merge function to join the activity labels with activity IDs in the clean data table
clean <- merge(clean,activ, by.x = 'activ', by.y = 'ID')

#apply the mean cunction to the data set on subjet and action 
final <- aggregate(. ~subject + action, clean, mean)

### create submission

#write output to a file
write.table(clean,"tidy_data_submission.txt", row.name=FALSE)






