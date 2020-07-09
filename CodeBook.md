---
title: "Codebook"
author: "sweety"
date: "7/9/2020"
output: html_document
---

```{r setup, include=FALSE}
knitr::opts_chunk$set(echo = TRUE)
```

## R Markdown

The R script run_analysis.R performs the data preparation including all the 5 steps required  to be carried out.

## Download the dataset
Dataset downloaded and extracted under the folder called UCI HAR Dataset

## Assign each data to variables
x_train <- test/X_train.txt : 7352 rows, 561 columns 
contains recorded features train data

y_train <- test/y_train.txt : 7352 rows, 1 columns 
contains train data of activities’code labels

x_test <- test/X_test.txt : 2947 rows, 561 columns 
contains recorded features test data

y_test <- test/y_test.txt : 2947 rows, 1 columns 
contains test data of activities’code labels

subject_test <- test/subject_test.txt : 2947 rows, 1 column 
contains test data of 9/30 volunteer test subjects being observed

subject_train <- test/subject_train.txt : 7352 rows, 1 column 
contains train data of 21/30 volunteer subjects being observed

features <- features.txt : 561 rows, 2 columns 
 The features selected for this database come from the accelerometer and gyroscope 3-axial raw signals tAcc-XYZ and tGyro-XYZ.
activities <- activity_labels.txt : 6 rows, 2 columns 
List of activities performed when the corresponding measurements were taken and its codes (labels)

## Merges the training and the test sets to create one data set

X (10299 rows, 561 columns) is created by merging x_train and x_test using rbind() function

Y (10299 rows, 1 column) is created by merging y_train and y_test using rbind() function

Subject (10299 rows, 1 column) is created by merging subject_train and subject_test using rbind() function

Merged_Data (10299 rows, 563 column) is created by merging Subject, Y and X using cbind() function

## Extracts only the measurements on the mean and standard deviation for each measurement

TidyData (10299 rows, 88 columns) is created by subsetting Merged_Data, selecting only columns: subject, code and the measurements on the mean and standard deviation (std) for each measurement

## Uses descriptive activity names to name the activities in the data set

Entire numbers in code column of the TidyData renamed with corresponding activity taken from second column of the activities variable

## Appropriately labels the data set with descriptive variable names

In column's name,

All Acc renamed as Accelerometer
All Gyro  renamed as Gyroscope
All BodyBody renamed as Body
All Mag renamed as Magnitude
All beginning with character f renamed as Frequency
All beginning with character t renamed as Time

## From the data set in step 4, creates a second, independent tidy data set with the average of each variable for each activity and each subject

FinalData (180 rows, 88 columns) is created by sumarizing TidyData taking the means of each variable for each activity and each subject, after groupped by subject and activity.

Export FinalData into FinalData.txt file.
