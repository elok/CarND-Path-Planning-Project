# CarND-Path-Planning-Project
Self-Driving Car Engineer Nanodegree Program
   
### Goals
The goal of this project is to safely navigate around a virtual highway with other traffic that is driving +-10 MPH of the 50 MPH speed limit. The car's localization and sensor fusion data was provided and there is also a sparse map list of waypoints around the highway. The car accelerates as close as possible to the 50 MPH speed limit, while passing slower traffic when possible. The car avoids hitting other cars at all cost as well as driving inside of the marked road lanes at all times, unless going from one lane to another. The car makes one complete loop around the 6946m highway. The car also avoids accelerating or jerking too hard.

## Building Instructions

1. Make a build directory: `mkdir build && cd build`
2. Compile: `cmake .. && make`
3. Run it: `./path_planning`.

## Details

1. SENSOR FUSION Part 1: the code first iterates through the list of sensor fusion cars and determines which lane they're in and how close they are. The d variable is used to determine which lane they're in and s was used to determine where in the lane they are. (main.cpp -- Code line 121)

2. SENSOR FUSION Part 2: Once we know where the other cars are, we have to determine our next steps and what we want to do. 
If the car is in the same lane as us and they're really close, we use the information above to determine which lane we can switch to. If we can't switch lanes than we have to slowly decelerate. 

3. GENERATE WAYPOINTS Part 1: We first create a list of waypoints. If there was a previous list, we will use two previous points from that list. If we don't have a previous list, we use our car's points and get new points by making a path tangent to the our car.

4. GENERATE WAYPOINTS Part 2: Given the lane we want to move to and meters forward we want to plan for, we use getXY to generate additional waypoints. We then take all the waypoints and shift the car reference angle to 0 degrees for ease of use and generation of cleaner waypoints later with the spline.

5. GENERATE WAYPOINTS Part 3: Using all the information above, we use spline.h to generate a smooth trajectory to our desired waypoints. It takes into account the lane we want to move to and the acceration or deceleration of our car.

## Dependencies

* cmake >= 3.5
  * All OSes: [click here for installation instructions](https://cmake.org/install/)
* make >= 4.1
  * Linux: make is installed by default on most Linux distros
  * Mac: [install Xcode command line tools to get make](https://developer.apple.com/xcode/features/)
  * Windows: [Click here for installation instructions](http://gnuwin32.sourceforge.net/packages/make.htm)
* gcc/g++ >= 5.4
  * Linux: gcc / g++ is installed by default on most Linux distros
  * Mac: same deal as make - [install Xcode command line tools]((https://developer.apple.com/xcode/features/)
  * Windows: recommend using [MinGW](http://www.mingw.org/)
* [uWebSockets](https://github.com/uWebSockets/uWebSockets)
  * Run either `install-mac.sh` or `install-ubuntu.sh`.
  * If you install from source, checkout to commit `e94b6e1`, i.e.
    ```
    git clone https://github.com/uWebSockets/uWebSockets 
    cd uWebSockets
    git checkout e94b6e1
    ```
