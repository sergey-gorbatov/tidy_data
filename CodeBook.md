## Introduction
This file details the variables used in the run_analysis.R script. 

## Procedure
Download the data files, unzip and save to a local working directory. <br>
Download from: https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip  <br>
Run run_analysis.R 

## Script Documentation 
Required library for execution: library(dplyr)

### Variables
mainpath - main folder path <br>
testpath - test folder path<br>
trainpath - train folder path<br>

tr_sub - variable containing the trainig subject data<br>
tr_val - variable containing the training X data<br>
tr_act - variable containing the training Y data<br>
te_sub - variable containing the testing subject data<br>

te_val - variable containing the testing X data<br>
te_act - variable containing the testing Y data<br>
feat   - variable containing the features data<br>
activ  - variable containing the activity labels data<br>

f_tr - training data combining columns and storing in this variable<br>
f_te - testing data combining columns and storing in this variable<br>
full - full data set is combined and stored in this variable<br>

me_st_col - variable that stores the T/F for columns that contain "mean" or "std" or "activity" or "subject" in the names.<br>
clean - final data set, which saves only the relevant columns<br>
final - final data set for question #5 where we apply the mean function to the data set on subjet and action <br>

##Version
R version 3.5.1 (2018-07-02) <br>
