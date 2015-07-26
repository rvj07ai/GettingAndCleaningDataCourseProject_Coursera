
##CodeBook


* <b>Source of the original data :</b> <a href="https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip">ProjectData </a>


* <b>Original description:</b> <a href="http://archive.ics.uci.edu/ml/datasets/Human+Activity+Recognition+Using+Smartphones">SmartPhone Recognition </a>

* <b>Main Logic</b> : 

 The attached R script (run_analysis.R) performs the following to clean up the data:

- It Merges the training and test sets to create one data set, namely train/X_train.txt with test/X_test.txt, the result of which is a 10299x561 data frame, as in the  original description ("Number of Instances: 10299" and "Number of Attributes: 561"), train/subject_train.txt with test/subject_test.txt, the result of which is a   10299x1 data frame with subject IDs, and train/y_train.txt with test/y_test.txt, the result of which is also a 10299x1 data frame with activity IDs.

- Reads features.txt and extracts only the measurements on the mean and standard deviation for each measurement. The result is a 10299x66 data frame, because only 66 out of 561 attributes are measurements on the mean and standard deviation. All measurements appear to be floating point numbers in the range (-1, 1).


- Moreover, the script appropriately labels the data set with descriptive names: all feature names (attributes) and activity names are converted to lower case, underscores and brackets () are removed. Then it merges the 10299x66 data frame containing features with 10299x1 data frames containing activity labels and subject IDs. The result is saved as merged_clean_data.txt, a 10299x68 data frame such that the first column contains subject IDs, the second column activity names, and the last 66 columns are measurements. Subject IDs are integers between 1 and 30 inclusive. The names of the attributes are similar to the following:

 * tbodyacc-mean-x 
 
 * tbodyacc-mean-y 
 
 * tbodyacc-mean-z 
 
 * tbodyacc-std-x 

 * tbodyacc-std-y 

 * tbodyacc-std-z 

 * tgravityacc-mean-x 

 * tgravityacc-mean-y and so on...  


- For output variables , it reads activity_labels.txt and applies descriptive activity names to name the activities in the data set:

 * walking

 * walkingupstairs

 * walkingdownstairs

 * sitting

 * standing

 * laying

- Finally, the script creates a 2nd, independent tidy data set with the average of each measurement for each activity and each subject. The result is saved as data_set_with_the_averages.txt, a 180x68 data frame. Here ,the first column contains Subject IDs, the second column contains Activity names (see above), and then the averages for each of the 66 attributes are in columns 3...68. There are 30 subjects and 6 activities, thus 180 rows are present in this data set with averages.
