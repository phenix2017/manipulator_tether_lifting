Object lifting: manipulator and tether attached at different points of object 
==========================

REQUIRES:
https://github.com/ethz-asl/rotors_simulator

INSTRUCTIONS for launching just the carma
carma where end-effector is not root-link (link1 is the root-link)
~~~
roslaunch manipulator_tether_lifting carma_fixed.launch version:=1
~~~

carma where end-effector is root-link (TODO: strange behaviour)
~~~
roslaunch manipulator_tether_lifting carma_fixed.launch version:=2
~~~

INSTRUCTIONS:
~~~
roslaunch manipulator_tether_lifting uavs_carma_lifting.launch mav_model:=neo
~~~
or
~~~~
roslaunch manipulator_tether_lifting uavs_carma_lifting.launch mav_model:=firefly
~~~~
