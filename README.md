# Meshed IMU Garment HAR Dataset (MIG HAR Dataset)
This dataset was created for human activity recognition using the Meshed IMU Garment, which consists of 396 IMUs on garments. We provide time-synchronised data from 396 IMU accelerometers, gyroscopes and magnetometers at 100 Hz.

## LICENCE

Use of this dataset in publications must be acknowledged by referencing the following publication [1]. We recommend that this dataset be referred to as the "MIG HAR Dataset". 

[1] Akihisa Tsukamoto, Naoto Yoshida, Tomoko Yonezawa, Kenji Mase, and Yu Enokibori. 2023. Where Are the Best Positions of IMU Sensors for HAR? - Approach by a Garment Device with Fine-Grained Grid IMUs -. In Adjunct Proceedings of the 2023 ACM International Joint Conference on Pervasive and Ubiquitous Computing & the 2023 ACM International Symposium on Wearable Computing (Cancun, Quintana Roo, Mexico) (UbiComp/ISWC ’23 Adjunct). Association for Computing Machinery, New York, NY, USA, 445–450. https://doi.org/10.1145/3594739.3610736

The reference list of the above will be updated along with the study progress; thus, please check here before submitting your study for conference, journal, and so on. 

This dataset is released under the [Creative Commons Attribution 4.0 International License (CC BY 4.0) license.](https://creativecommons.org/licenses/by/4.0/)

## NOTE
A sample DataReader is provided in [IMU-based-HAR-benchmark](https://github.com/eno-lab/IMU-based-HAR-benchmark)

## Hardware Setup
396 IMUs (ICM-20948):
- Accelerometer, Gyroscope, and Magnetometer
- For more information on the sensors, see data sheet
- Wired connection
- The positions and identification numbers of the sensors are shown in the image in the imuposition_image folder
- The sensors was fixed by sewing it into the garments

## IMU Sensor Setup
Accelerometer
-   ±16 G
-   100 Hz


Gyroscope
-   ±2000 dps(degree/sec)
-   100 Hz


Magnetometer
-   ±4912 µT
-   100 Hz

ICM-20948 has different magnetometer axis directions to accelerometers and gyroscopes, but the magnetometer axis directions of the data were aligned to the accelerometer and gyroscope. 


Missing values were filled in with NaN. The maximum number of NaN samples included per sensor was 48; the longest continuous number of NaN samples per sensor was 11.

## Subjects
12 subjects participated in the data collection:
-   Consists of university students
-   8 males, 4 females
-   aged 21.33 ± 1.65 years
-   Height 168.00 ±  11.46 cm
-   all subjects have agreed to the usage of recorded data for scientific purposes

|Subject ID|Sex   |Age   |Height (cm)|Dominant Arm|
|:---:     |:---: |:---: |:---:      |:---:       |
|1         |Female|23    |158        |Right       |
|2         |Male  |19    |175        |Right       |
|3         |Male  |22    |172        |Right       |
|4         |Female|22    |148        |Right       |
|5         |Male  |22    |185        |Right       |
|6         |Female|20    |157        |Right       |
|7         |Male  |23    |164        |Right       |
|8         |Male  |23    |180        |Right       |
|9         |Male  |23    |170        |Right       |
|10        |Male  |18    |172        |Right       |
|11        |Male  |21    |182        |Right       |
|12        |Female|20    |153        |Right       |
## Data Acquisition Protocol
This dataset consists of data from 14 different activities. Each activity was performed consecutively for 40 seconds and carried out twice. Descriptions of each activity are given below.

|Activity|Description|
|:---:   |:---|
|Walking|Start activity from a stationary position and continue straight ahead until the end of the recording.|
|Jogging|Start activity from a stationary position and continue moving until the end of the recording. Course includes turning paths.|
|Going-up Stairs|Start activity from a stationary position and continue moving until the end of the recording.|
|Going-down Stairs|Start activity from a stationary position and continue moving until the end of the recording. |
|Standing|Hold stationary in the standing position.|
|Sitting|Hold stationary in the sitting position.|
|Typing|Typing text on a PC while sitting down.|
|Writing|Writing with a pen on a piece of paper while sitting down.|
|Eating Cookies|Pick up a cookie and eat it while sitting down.|
|Eating Pasta|Acting out eating pasta with a fork while sitting down. Not actually eating it.|
|Ironing|Ironing several T-shirts while standing.|
|Folding laundry|Fold several T-shirts while standing.|
|Brushing Teeth|Keep the tooth brushing action in a standing position.|
|Vacuuming|Clean with a handheld vacuum cleaner while moving around.|

**NOTE: The first part, e.g., 2 seconds or so, of the following activities shuoud be clopped: Walking, Jogging, Going-up Stairs, and Going-down Stairs.**

## Directory structure
The directory hierarchy indicates which subject and which activity. The deepest hierarchy stores data from two trials. The data files contain data from 396 IMUs, time synchronised.

data/  
&emsp;├ subject(id)/  
&emsp;&emsp;&emsp;&emsp;&emsp;├ (activity name)/  
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;├ data1.csv.gz  
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;├ data2.csv.gz  
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;├ rawdata1.csv.gz  
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&ensp;&ensp;&ensp;&ensp;└ rawdata2.csv.gz

The data(num).csv.gz files are the data with offset calibration and the rawdata(num).csv.gz files are the data without offset calibration. The offset calibration was only performed on the accelerometer and gyroscope.  
Method for offset calibration:
First, the device was placed and one second of static data was acquired. This was carried out in 10 different ways of placing the device. Next, offsets were calculated so that the acceleration was closest to $(\sqrt{x^2 + y^2 + z^2} = 1)$ and the angular velocity was closest to $(\sqrt{x^2 + y^2 + z^2} = 0)$.
## Sensor position
![](imuposition_image/FrontofUpper.png)
![](imuposition_image/BackofUpper.png)
![](imuposition_image/FrontofLower.png)
![](imuposition_image/BackofLower.png)
