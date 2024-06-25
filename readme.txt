### create a workspace ##
mkdir -p arm/src
cd arm/src

## clone my repository ## (simulation files)
git clone https://github.com/Mahesh7925/Automomus-Mobile-Robot-Simulation-Turtlrbot3-.git

## add turtle bot3 package into workspace using vcs ##
gedit turtlebot3.repos
vcs import . < turtlebot3.repos




## build the workspace ##
colcon build --symlink-install

## source the workspace ##
source install/setup.bash




## creation of map ### 
launch the turtlebot in gazebo: "ros2 launch simulation turtlebot3_world.launch.py"
launch cartographer to create map: "ros2 launch turtlebot3_cartographer cartographer.launch.py use_sim_time:=True"

launch telop_keyboard node to move the robot: "ros2 run turtlebot3_teleop teleop_keyboard"

move the robot in the simulation environment and once clear map of the environment is generated save the map using: " ros2 run nav2_map_server map_saver_cli -f my_map"

configure the map path in the simulation pkg-->launch---> nav2.launch.py  


## navigation ##

launch the turtlebot in gazebo: "ros2 launch simulation turtlebot3_world.launch.py"
launch nav2 node: "ros2 launch simulation nav2.launch.py"

run the send_goal_pose node to send goal positions: "ros2 run simulation send_goal_pose"


