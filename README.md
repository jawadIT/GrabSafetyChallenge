# GrabSafetyChallenge

OBJECTIVE : is to predict and classify a given trip in to safe or not-safe

safe / not-safe : is with respect to driving behaviour , type of route and many other features that would be extracted

DATA : Data is captured by accelaro and gyro meters for every second of a trip 

bookingID : unique id of trip 
accuracy  : accuracy of gps locator [ex: 3 tells GPS reading is accuracte for 3 meters of raidus] 
bearing   : in degrees , this tells the direction of trip in relation to north pole and target destination  
accelarometer x,y,z axis [mts/sec square] : this data tells the accelaration effect in x,y and z axis. it helps to calculate the magnitude of accelaration 
gyrometer x,y and z axis [rad/sec] : this data will tell the degree of wheel rotation. In this case I am assuming z axis is aligned  
time : its incremental value . Last row value will be the total time taken in seconds 
speed : this is speed in mts/sec. summation of all row values for a given trip will tell total disctance of trip  

FEATURE GENERATION : 

Total Distance of Trip in KM's

Total Time taken for the Trip in Hrs

Each trip to be grouped by change in direction of trip and below features are calculated for each direction change 

distance travelled

time taken 

speed of travel

magnitude of accelaration [square root of sum of squares of accelaration mts/sec square in x,y and z axis]

degree of rotation [multipying rad/sec with fixed value 57.3]



For each direction change , its important to understand the change in behaviour

Below features are calculated to capture this behaviour using LAG function

Important features for driving behaviour 

                      change in speed

                      change in degree of rotation

                      change in manginitude of accelaration

For all the directional changes below features will help in capturing high level behaviour and route details 

Important features for complexity of route 

                       total number of directional changes 

                      distance across all directional changes
                      
                      speed variation 

Directional Change is sensed using the grouping of bookingID, Bearing and accuracy 

*these three fields are taken for grouping assuming that the change in bearing and accuracy can happen mostly due to change in vehicle poistion with respect to destination , traffic etc

some other features could be calculated by further mining the data

are there a traffic points , if so how many [the seconds where speed is 0 mts/sec]

how the traffic is impacting the total trip duration

are trips with lower traffic prone to be unsafe 
