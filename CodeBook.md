## Introduction
This file details the variables used in the run_analysis.R script. 

## Procedure
Download the data files, unzip and save to a local working directory. 
Download from: https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip
Run run_analysis.R 

## Script Documentation 
Required library for execution: library(dplyr)

### variables
mainpath - main folder path
testpath - test folder path
trainpath - train folder path

tr_sub - variable containing the trainig subject data
tr_val - variable containing the training X data
tr_act - variable containing the training Y data
te_sub - variable containing the testing subject data

te_val - variable containing the testing X data
te_act - variable containing the testing Y data
feat   - variable containing the features data
activ  - variable containing the activity labels data

f_tr - training data combining columns and storing in this variable
f_te - testing data combining columns and storing in this variable
full - full data set is combined and stored in this variable

me_st_col - variable that stores the T/F for columns that contain "mean" or "std" or "activity" or "subject" in the names.
clean - final data set, which saves only the relevant columns
final - final data set for question #5 where we apply the mean function to the data set on subjet and action 

