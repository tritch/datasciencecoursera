#This is H1
##This is H2
### This is H3

variable         | description
---------------- | ------------------------------------------------------------------
`title`	|	Title of movie
`title_type`	|	Type of movie (Documentary, Feature Film, TV Movie)
`genre`	|	Genre of movie (Action & Adventure, Comedy, Documentary, Drama, Horror, Mystery & Suspense, Other)
`runtime`	|	Runtime of movie (in minutes)
`mpaa_rating`	|	MPAA rating of the movie (G, PG, PG-13, R, Unrated)
`studio`	|	Studio that produced the movie
`thtr_rel_year`	|	Year the movie is released in theaters

###Getting and Cleaning Data Course Project
##Purpose

This project requires the student to read text files into R dataframes, to analyze data structures, to determine intermediate concatenation and merge operations, and to demonstrate other fundamental operations required to scrub a large data set.  The deliverable is two tidy datasets ready for downstream analysis.

##Project submission summary

1.  This `README.md` file that explains the scope of the project and summarizes the analysis

2.  An R script called `run_analysis.R` that creates the two tidy data sets described in this README

3.  The first data set:  `merged dataset.txt`, a tidy data set created from a merge of the training and the test sets and the following processing steps:

	- Extraction of only the mean and standard deviation figures for each measurement
	- Application of descriptive names and labels for activities and variable names in accord with tidy data principles

4.  `average.data.txt`, a second independent tidy data set, derived from `merged dataset.txt` (data set described above) in which the average of each variable by activity and by subject is calculated.

5.  `codebook.md`, the project code book that describes variables, their units, and other data information in fashion similar to the codebook provided with the source data

6.  a link to the Github repository containing all project files listed here.

##run_analysis.R functional description

run_analysis.R performs the following:

Merges the training and the test sets to create one data set.
Extracts only the measurements on the mean and standard deviation for each measurement.
Uses descriptive activity names to name the activities in the data set
Appropriately labels the data set with descriptive activity names.
Creates a second, independent tidy data set with the average of each variable for each activity and each subject.
run_analysis.R

It downloads the UCI HAR Dataset data set and puts the zip file working directrory. After it is downloaded, it unzips the file into the UCI HAR Dataset folder.
It loads the train and test data sets and appends the two datasets into one data frame. This is done using rbind.
It extracts just the mean and standard deviation from the features data set. This is done using grep.
After cleaning the column names, these are applied to the x data frame.
After loading activities data set, it converts it to lower case using tolower and removes underscore using gsub. activity and subject column names are named for y and subj data sets, respectively.
The three data sets, x, y and subj, are merged. Then, it is exported as a txt file into the Project folder in the same working directory, named merged.txt.
The mean of activities and subjects are created into a separate tidy data set which is exported into the Project folder as txt file; this is named average.txt.
The R code contains str for easier preview of the two final data sets.