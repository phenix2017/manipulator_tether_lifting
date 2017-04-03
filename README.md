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

INSTRUCTIONS for launching 2 uavs + carma + tether + object  

(there is a big difference in initialization between VERSION=0 and VERSION=1, because in the first the root link is uav with carma, and in the second the root link is the object)

MAV_MODEL in {firefly,neo}  
VERSION in {0,1} (0 = original carma, 1 = reversed carma)

~~~
roslaunch manipulator_tether_lifting start_gazebo.launch

roslaunch manipulator_tether_lifting spawn_uavs_carma_tether.launch version:=VERSION mav_model:=MAV_MODEL

(this will not work, because controllers for uavs are from another package)
roslaunch manipulator_tether_lifting spawn_uavs_carma_tether_w_controllers.launch version:=VERSION mav_model:=MAV_MODEL
~~~

INSTRUCTIONS for launching 2 uavs + 2 carmas + object  

MAV_MODEL in {firefly,neo}  

(in this model original carma CANNOT be used)

~~~
roslaunch manipulator_tether_lifting start_gazebo.launch

roslaunch manipulator_tether_lifting spawn_uavs_carmas.launch mav_model:=MAV_MODEL

(this will not work, because controllers for uavs are from another package)
roslaunch manipulator_tether_lifting spawn_uavs_carmas_w_controllers.launch mav_model:=MAV_MODEL
~~~