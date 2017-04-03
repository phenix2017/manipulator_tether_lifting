Carma object lifting: manipulator and tether attached at different points of object 
==========================

REQUIRES:
https://github.com/ethz-asl/rotors_simulator

INSTRUCTIONS for launching just the carma

carma where end-effector is not root-link (link1 is the root-link)
~~~
roslaunch manipulator_tether_lifting start_gazebo.launch gravity:=false
(let gazebo initialize properly, otherwise robot is not initialized properly)

roslaunch manipulator_tether_lifting spawn_carma_fixed_w_controllers.launch version:=0
~~~


carma where end-effector is root-link  
(TODO: gains in joints close to end-effector were set to 0, because simulation (with uav) is unstable otherwise)
~~~
roslaunch manipulator_tether_lifting start_gazebo.launch gravity:=false
(let gazebo initialize properly, otherwise robot is not initialized properly)

roslaunch manipulator_tether_lifting spawn_carma_fixed_w_controllers.launch version:=1
~~~

INSTRUCTIONS for launching carma+uav

~~~
roslaunch manipulator_tether_lifting uavs_carma_lifting.launch mav_model:=neo
~~~
or
~~~~
roslaunch manipulator_tether_lifting uavs_carma_lifting.launch mav_model:=firefly
~~~~
