#Codebook
##SamsungGalaxyS Project
###Getting and Cleaning Data-Tidy Data
The purpose of this project is to demonstrate ability to collect, work with, and clean a data set. 

One of the most exciting areas in all of data science right now is wearable computing - see for example this article . 
Companies like Fitbit, Nike, and Jawbone Up are racing to develop the most advanced algorithms to attract new users. 
The data linked below represent data collected from the accelerometers from the Samsung Galaxy S smartphone. 
A full description is available at the site where the data was obtained:

http://archive.ics.uci.edu/ml/datasets/Human+Activity+Recognition+Using+Smartphones

####Project Data:  
https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip

####Script:  run_analysis.R

The script does the following:

Download and unzip data set

Read test and training data

Read activity names and feature names

Extract test and traing data and add descriptive names

Extract mean and standard deviation for each measurement

Clean names

Create tidy data set with mean of each activity and each subject


####Activities:

1 WALKING

2 WALKING_UPSTAIRS

3 WALKING_DOWNSTAIRS

4 SITTING

5 STANDING

6 LAYING

####Features
The features selected for this database come from the accelerometer and gyroscope 3-axial raw signals tAcc-XYZ and tGyro-XYZ. These 
time domain signals (prefix 't' to denote time) were captured at a constant rate of 50 Hz. Then they were filtered using a median 
filter and a 3rd order low pass Butterworth filter with a corner frequency of 20 Hz to remove noise. Similarly, the acceleration 
signal was then separated into body and gravity acceleration signals (tBodyAcc-XYZ and tGravityAcc-XYZ) using another low pass 
Butterworth filter with a corner frequency of 0.3 Hz. 

Subsequently, the body linear acceleration and angular velocity were derived in time to obtain Jerk signals (tBodyAccJerk-XYZ and 
tBodyGyroJerk-XYZ). Also the magnitude of these three-dimensional signals were calculated using the Euclidean norm (tBodyAccMag, 
tGravityAccMag, tBodyAccJerkMag, tBodyGyroMag, tBodyGyroJerkMag). 

Finally a Fast Fourier Transform (FFT) was applied to some of these signals producing fBodyAcc-XYZ, fBodyAccJerk-XYZ, fBodyGyro-XYZ, 
fBodyAccJerkMag, fBodyGyroMag, fBodyGyroJerkMag. (Note the 'f' to indicate frequency domain signals). 

These signals were used to estimate variables of the feature vector for each pattern:  
'-XYZ' is used to denote 3-axial signals in the X, Y and Z directions.

tBodyAcc-XYZ            new label:  TimeBodyAccelerometer-XYZ

tGravityAcc-XYZ         new label:  tGravityAccelerometer-XYZ  

tBodyAccJerk-XYZ        new label:  TimeBodyAccelerometerJerk-XYZ

tBodyGyro-XYZ           new label:  TimeBodyGyroscope-XYZ

tBodyGyroJerk-XYZ       new label:  TimeBodyGyroscopeJerk-XYZ

tBodyAccMag             new label:  TimeBodyAccelerometerMagnitude

tGravityAccMag          new label:  tGravityAccelerometerMagnitude

tBodyAccJerkMag         new label:  TimeBodyAccelerometerJerkMagnitude

tBodyGyroMag            new label:  TimeBodyGyroscopeMagnitude

tBodyGyroJerkMag        new label:  TimeBodyGyroscopeJerkMagnitude

fBodyAcc-XYZ            new label:  fBodyAcclerometer-XYZ

fBodyAccJerk-XYZ        new label:  fBodyAcclerometerJerk-XYZ

fBodyGyro-XYZ           new label:  fBodyGyroscope-XYZ

fBodyAccMag             new label:  fBodyAcclerometerMagnitude

fBodyAccJerkMag         new label:  fBodyAcclerometerJerkMagnitude

fBodyGyroMag            new label:  fBodyGryoscopeMagnitude

fBodyGyroJerkMag        new label:  fBodyGryoscopeJerkMagnitude


####Variables

The set of variables that were estimated from these signals are: 

mean(): Mean value

std(): Standard deviation

mad(): Median absolute deviation 

max(): Largest value in array

min(): Smallest value in array

sma(): Signal magnitude area

energy(): Energy measure. Sum of the squares divided by the number of values. 

iqr(): Interquartile range 

entropy(): Signal entropy

arCoeff(): Autorregresion coefficients with Burg order equal to 4

correlation(): correlation coefficient between two signals

maxInds(): index of the frequency component with largest magnitude

meanFreq(): Weighted average of the frequency components to obtain a mean frequency

skewness(): skewness of the frequency domain signal 

kurtosis(): kurtosis of the frequency domain signal 

bandsEnergy(): Energy of a frequency interval within the 64 bins of the FFT of each window.

angle(): Angle between to vectors.


Additional vectors obtained by averaging the signals in a signal window sample. These are used on the angle() variable:

gravityMean             new label:  GravieyMean

tBodyAccMean            new label:  TimeBodyAccelerometerMean

tBodyAccJerkMean        new label:  TimeBodyAccelerometerJerkMean

tBodyGyroMean           new label:  TimeBodyGyroscopeMean

tBodyGyroJerkMean       new label:  TimeBodyGyroscopeMean


The complete list of variables of each feature vector is available in 'features.txt'
