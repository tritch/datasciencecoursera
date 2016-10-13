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

#Getting and Cleaning Data Course Project
##Purpose

This project requires the student to read text files into R dataframes, to analyze data structures, to determine intermediate concatenation and merge operations, and to demonstrate other fundamental operations required to scrub a large data set.  The deliverable is two tidy datasets ready for downstream analysis with documentation as described below.

##Submission summary

1.  This `README.md` file that explains the scope of the project and summarizes the analysis

2.  An R script called `run_analysis.R` that creates the two tidy data sets described in this README

3.  The first data set:  `merged dataset.txt`, a tidy data set created from a merge of the training and the test sets and the following processing steps:

	- Extraction of only the mean and standard deviation figures for each measurement
	- Application of descriptive names and labels for activities and variable names in accord with tidy data principles

4.  `average.data.txt`, a second independent tidy data set, derived from `merged dataset.txt`, the data set described previously, in which the average of each variable by activity and by subject is calculated.

5.  `codebook.md`, that describes variables, their units, and other data information in fashion similar to the codebook provided with the source data

6.  a link to the Github repository containing all project files listed here.

##run_analysis.R user notes

Before the reader may execute `run_analysis.R` some simple modifications are required in the text of `run_analysis.R`.  Specifically, the user should copy `run_analysis.R` to desired directory and edit the working directory (line 2) to suit the local environment.  This is accomplished by either:

	~ Opening `run_analysis.R` with a text editor to modify the working directory path before loading in R
	~ Opening the file in RStudio, changing directories in the IDE, then selecting all the code in the `run_analysis.R` window, then clicking on the "Run" button

##run_analysis.R functional description

###run_analysis.R provides the following in sequence:

- Sets working directory to suit local environment for the required file download
- Defines the function `read_concat()`, which will be used to read and concatenate "training" and "test" files for subjects, activities, and measurement data.
- Downloads the .zip archive found at the specified URL, and unzips it to the working directory under the folder "./UCI HAR Dataset"
- Deletes both "Inertial Signals" directories, which contain files from the .zip archive not needed for the analysis
- Calls `read_concat()` three times to read and concatenate training and test files for subjects, activities, and measurement data.
- Modifies column headings as needed, and checks that the row dimension for all three dataframes, which must be identical.
- Adds descriptive variable names from the features text file from the .zip archive.  The term "features" is used to describe the measurement variable names.
- Extracts only the mean() and sd() feature parameter types into a new intermediate dataframe, verifies that the names within are as expected, then proceeds to cleanup many of the measurement variable names with numerous regular expression scans.
	- All are converted to lower case
	- Patterns matching c("()-x", "()-y", "()-z", "-std\\(\\)", "-mean\\(\\)" ) are replaced with c("(x)", "(y)", "(z)", "-std", "-mean")
- Reads activity labels file (from .zip archive) and relabels activity labels with descriptive variable names to comply with tidy data norms
- Creates the first dataset `data` with a merge of the separate subjects vector, activities vector, and the intermediate data set
- Writes the first dataset `data` to the working directory as "merged dataset.txt", a space-delimited ASCII text file.
- Generate the second dataset from the first dataset (`data`) by calculating measurement averages by subject, by activity, and merging with subject and activity columns.
- As a final step, writes the second dataset `average.data` to the working directory as "average.data.txt", a space-delimited ASCII text file.







