Carma object lifting: manipulator and tether attached at different points of object 
==========================

REQUIRES:
https://github.com/ethz-asl/rotors_simulator

INSTRUCTIONS for launching just the carma

VERSION in {0,1}  
0 = original carma: carma where end-effector is not root-link (link1 is the root-link)  
1 = reversed carma: carma where end-effector is root-link (TODO: gains in joints close to end-effector were set to 0, because simulation (with uav) is unstable otherwise)
~~~
roslaunch manipulator_tether_lifting start_gazebo.launch gravity:=false
(let gazebo initialize properly, otherwise robot is not initialized properly)

roslaunch manipulator_tether_lifting spawn_carma_fixed_w_controllers.launch version:=VERSION
~~~


INSTRUCTIONS for launching carma+uav  

MAV_MODEL in {firefly,neo}  
VERSION in {0,1} (0 = original carma, 1 = reversed carma)

~~~
roslaunch manipulator_tether_lifting start_gazebo.launch
roslaunch manipulator_tether_lifting spawn_uav_w_carma.launch version:=VERSION mav_model:=MAV_MODEL

(this will not work, because controller for uav is from another package)
(roslaunch manipulator_tether_lifting spawn_uav_w_carma_and_controllers.launch version:=VERSION mav_model:=MAV_MODEL)
~~~
