# autsys-projects-gkd


## Challenge 1 : Search and Rescure 
A group of people were lost because of avalanche. Fortuntely, each of them carried signal generator. We gonna base on the signal strength and possibly signal angle to find their relative accurate position by drone. In order to get the perfect solution of search method, we decide to simulate it at first.

### Involved task contents:
* ~~Read signal strength and signal angle from Unity~~ (we have some unknown issues detecting the given signal in Unity unfortunatly.)
* Generate victim's positions randomly
* Generate signal strength and signal angle base on the distance and direction between drone and victim
* Implement global search algorithm
* Implement several local search algorithm
* Evaluate the local search algorithm base on certain benchmark
* Visualization of drone's trajectory in rviz

## Team Members :
Yiwei Wang,
Yiyang Li,
Tao Ma,
Chenming Wang

## How to install
git clone this repo. And delete folders except AVALANCHE_Data, basic_waypoint_pkg, controller_pkg, unity_bridge.

Go to the `/src` folder and add submodules using:
```bash
git init

git submodule add https://github.com/ethz-asl/mav_comm.git
git submodule add https://github.com/ethz-asl/mav_trajectory_generation.git
git submodule add https://github.com/ethz-asl/eigen_catkin.git
git submodule add https://github.com/ethz-asl/eigen_checks.git
git submodule add https://github.com/catkin/catkin_simple.git
git submodule add https://github.com/ethz-asl/glog_catkin.git
git submodule add https://github.com/ethz-asl/nlopt.git
git submodule add https://github.com/ethz-asl/yaml_cpp_catkin.git

git submodule init
git submodule update
```

Next run in project folder
```bash
cd ..
catkin build
```

Once the built is finished launch the following two roslaunch files in two terminals 
(don't forget to source the `setup.bash` in all terminals):

```bash
roslaunch unity_bridge unity_sim.launch
roslaunch basic_waypoint_pkg waypoint_mission.launch
```

## How to simulate  
After building code, go to project folder `/autsys-projects-gkd/src/basic_waypoint_pkg/config`, open file `trajectory_config.yaml`.  
Change parameters in `evaluation` according to different simulation scenarios.  
### Scenario 1: No signal noise. 
1. `local_mode` : 1 (local search with signal angle and strength) or 2 (local search with signal strength only)  
2. `victims_test`: false (random victims)
3. `victim_num`: 5  
4. `have_noise`: false  
5. `SignalStrength_noise`: 0.0  
6. `strength_noise`: 0.0
7. `angle_noise`: 0.0  
8. Save file and `roslaunch` two launch files above. 

### Scenario 2: Random noise in signal strength and angle  
1. `local_mode` : 1 (local search with signal angle and strength) or 2 (local search with signal strength only)  
2. `victims_test`: false (random victims)
3. `victim_num`: 5  
4. `have_noise`: true  
5. `SignalStrength_noise`: 0.0  
6. `strength_noise`: 0.02
7. `angle_noise`: 10 
8. Save file and `roslaunch` two launch files above.  

### Scenario 3: Large angle noise 
1. `local_mode` : 1 (local search with signal angle and strength) or 2 (local search with signal strength only)  
2. `victims_test`: false (random victims)
3. `victim_num`: 5  
4. `have_noise`: true  
5. `SignalStrength_noise`: 0.0  
6. `strength_noise`: 0.0
7. `angle_noise`: 60 
8. Save file and `roslaunch` two launch files above.

### Scenario 4: Fixed signal strength offset -0.02 
1. `local_mode` : 1 (local search with signal angle and strength) or 2 (local search with signal strength only)  
2. `victims_test`: false (random victims)
3. `victim_num`: 5  
4. `have_noise`: false  
5. `SignalStrength_noise`: -0.02  
6. `strength_noise`: 0.0
7. `angle_noise`: 0.0
8. Save file and `roslaunch` two launch files above.

## Documents:
### Functionality of codes.pdf provides a overview of the important functions developed by us for the searching process.
### For further details and simulation data, please refer our repor in Report_Group_GKD.pdf.
### Powerpoint for our presentation: Pre_GKD.pdf.
## Pictres from Visualization:
### Global Search:
![area](https://user-images.githubusercontent.com/105116734/226908305-7aebd961-06da-4c32-a1b1-c9e0723de169.jpg)


### Local Search Mode 1:
![mode1](https://user-images.githubusercontent.com/105116734/226908130-b7f1c20a-2c61-4097-b428-b0ba9199c9c3.png)

### Local Search Mode 2:
![mode2](https://user-images.githubusercontent.com/105116734/226908009-79c385a0-a0e3-4c5c-8780-4618de47b931.png)

## Videos of searching process:
https://syncandshare.lrz.de/getlink/fi2z64EwiP78mRcGy3qFmD/


## Tasks distributions:
*Chenming Wang*
1. Local search method 1
2. Part of global search
3. Part of overall code construction and optimization

*Tao Ma*
1. Modification of planner code
2. Part of local search method 
3. Part of overall code construction and optimization

*Yiwei Wang*
1. Local search method 2
2. Part of global search
3. Literature and conceptual research

*Yiyang Li*
1. Overall code construction and optimization
2. Victim and signal generation
3. Visualization

## Milestones:

Done Tasks：
1. Integration of the avalanche environment and the existing control/planning package (9-1 - 12-1) 

2. Make the environemnt running on local machine (12-1) 

3. Searching for relevant papers (13-1) 

4. Setting random beacons in environment and visualization in RVIZ (16-1-20-1)

5. Reading and extracting useful Info (especially beacon model and trajectory planning algorithms) from papers. (16-1- 20-1)

6. Receive signals from the new env (21-1 - 26-1)

7. Plan the first global search trajectory (27-1 - 2-2)

8. Planning and implementing of search trajectory (2-2 - 18-2)

9. Reporting and logging of location (19-2 - 25-2)

10. Exploring other search patterns (26-2 - 8-3)

11. Evaluation in terms of search time and accuracy (8-3 - 15-3)

12. Documentation and Presentation (15-3 - 22-3)







