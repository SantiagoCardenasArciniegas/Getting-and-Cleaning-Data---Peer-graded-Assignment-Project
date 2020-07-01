This submission contains three different files:


1. The first file is a .txt file called “tidy” that contains the data set created for this assignment.
2. The second file is a code book where the measurements of the tidy data set are briefly described.
3. The third file is a .R file containing the script used for this project.
4. Finally there is a README file where the code is explained. 
 
The R code contained in the Script.R file, is part of the peer grade assignment for the final week of the “Getting and cleaning data course” on Coursera.


The code does the following tasks:
1. It first uses the read.table function to create datasets in R form each of the files provided in the database. featureNames <- read.table("UCI HAR Dataset/features.txt") (activityLabels, subjectTrain, activityTrain, featuresTrain, subjectTest, activityTest, featuresTest).
2. The data sets are then merged into three bigger data sets (subject, activity, features) that combine the “training” and the “test” data using the R bind function.
3. The names function is used to add names to the “Subject” and “activity” datasets. In the “features” data set the colnames is used, and the names are taken from the second column of the “featurenames” dataset.
4. Using the Cbind function the three previous datasets are put together in a single one called “complete”.
5. The Columns with names containing *Mean.*|.*Std.* are extracted from the “complete” data set and stored in the “MeanandSTD” variable
6. The script then uses the columns stored in the MeanandSTD, plus the 562, and 563 columns, to subset the “complete” data set. This subset is stored in the “extractedData” object.
7. Using a for loop the names stored in the activity labels variable are added to the “extractedData$Activity” subset as characters (replacing the numbers).
8. The Gsub function is then used to create more descriptive names for some of the columns of  “extractedData”.
9.  extractedData is then converted into a data table using the data.table functions. It is then possible to use the dplyr commands to aggregate the average of each variable for each activity and each subject. This second dataset is stored under the name “tidyData”.
10. Finally a .txt file is created using the write.table function. This new file contains the same information from “tidyData”.












CODE BOOK:




The following variables are contained in the  “tidy.txt” file:




- Subject - A number or ID that corresponds to the individual that performed the activities measured. These IDs go from 1 to 30. Each individual was measured in 6 different activities, which means that the data set has a total of 180 (rows).


- Activity - the name of the activities that where measured: 


1: WALKING
2: WALKING_UPSTAIRS
3: WALKING_DOWNSTAIRS
4: SITTING
5: STANDING
6: LAYING




Variables: 


"TimeBodyAcceleratorMeanX"                    
"TimeBodyAcceleratorMeanY"                     
"TimeBodyAcceleratorMeanZ"                      
"TimeBodyAcceleratorStdX"                      
"TimeBodyAcceleratorStdY"                       
"TimeBodyAcceleratorStdZ"                      
"TimeGravityAcceleratorMeanX"                   "TimeGravityAcceleratorMeanY"                  
"TimeGravityAcceleratorMeanZ"                   
"TimeGravityAcceleratorStdX"                   
"TimeGravityAcceleratorStdY"                    
"TimeGravityAcceleratorStdZ"                   
"TimeBodyAcceleratorJerkMeanX"                  "TimeBodyAcceleratorJerkMeanY"                 
"TimeBodyAcceleratorJerkMeanZ"                  "TimeBodyAcceleratorJerkStdX"                  
"TimeBodyAcceleratorJerkStdY"                   "TimeBodyAcceleratorJerkStdZ"                  
"TimeBodyGyroscopeMeanX"                        
"TimeBodyGyroscopeMeanY"                       
"TimeBodyGyroscopeMeanZ"                        
"TimeBodyGyroscopeStdX"                        
"TimeBodyGyroscopeStdY"                         
"TimeBodyGyroscopeStdZ"                        
"TimeBodyGyroscopeJerkMeanX"                    "TimeBodyGyroscopeJerkMeanY"                   
"TimeBodyGyroscopeJerkMeanZ"                    "TimeBodyGyroscopeJerkStdX"                    
"TimeBodyGyroscopeJerkStdY"                     "TimeBodyGyroscopeJerkStdZ"                    
"TimeBodyAcceleratorMagnitudeMean"              "TimeBodyAcceleratorMagnitudeStd"              
"TimeGravityAcceleratorMagnitudeMean"           "TimeGravityAcceleratorMagnitudeStd"           
"TimeBodyAcceleratorJerkMagnitudeMean"          "TimeBodyAcceleratorJerkMagnitudeStd"          
"TimeBodyGyroscopeMagnitudeMean"                "TimeBodyGyroscopeMagnitudeStd"                
"TimeBodyGyroscopeJerkMagnitudeMean"            "TimeBodyGyroscopeJerkMagnitudeStd"            
"FrequencyBodyAcceleratorMeanX"                 "FrequencyBodyAcceleratorMeanY"                
"FrequencyBodyAcceleratorMeanZ"                 "FrequencyBodyAcceleratorStdX"                 
"FrequencyBodyAcceleratorStdY"                  "FrequencyBodyAcceleratorStdZ"                 
"FrequencyBodyAcceleratorJerkMeanX"             "FrequencyBodyAcceleratorJerkMeanY"            
"FrequencyBodyAcceleratorJerkMeanZ"             "FrequencyBodyAcceleratorJerkStdX"             
"FrequencyBodyAcceleratorJerkStdY"              "FrequencyBodyAcceleratorJerkStdZ"             
"FrequencyBodyGyroscopeMeanX"                   "FrequencyBodyGyroscopeMeanY"                  
"FrequencyBodyGyroscopeMeanZ"                   "FrequencyBodyGyroscopeStdX"                   
"FrequencyBodyGyroscopeStdY"                    "FrequencyBodyGyroscopeStdZ"                   
"FrequencyBodyAcceleratorMagnitudeMean"         "FrequencyBodyAcceleratorMagnitudeStd"         
"FrequencyBodyBodyAcceleratorJerkMagnitudeMean" "FrequencyBodyBodyAcceleratorJerkMagnitudeStd" 
"FrequencyBodyBodyGyroscopeMagnitudeMean"       "FrequencyBodyBodyGyroscopeMagnitudeStd"       
"FrequencyBodyBodyGyroscopeJerkMagnitudeMean"   "FrequencyBodyBodyGyroscopeJerkMagnitudeStd"  




Data set dimensions: ( 180, 88)