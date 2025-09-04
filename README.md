This project was completed as a group of 3 as a part of a semester-long Robotics and Intelligent Systems Project at Constructor University. The main objective of this lab was to implement a white line detection algorithm along with speed control, to make the duckiebot follow white lines throughout the duckietown map. For this purpose, white line detection was implemented using based on HSV Thresholding and Probablistic Hough Transform. Position and orientation errors were calculated from detected lines, and subsequently using the error as feedback for a proportional controller, we were able to achieve smooth line following. Collaborating with my teammate Ziyu Gu for line detection, I particularly contributed in the research and implementation of probabilistic hough transform, along with some fine-tunings for improved line detection. Key findings from this project include the importance and role of image processing and thresholding for line detection and a proportional controller for stability and easy small-scale modification.

Steps to run this project:

Fork the repository

Clone or fork the project repository containing the white line detection node.
Update the Launch File

In the launch file:

 
Change the namespace paul to your Duckiebot’s name.
Example: <remap from="~image/compressed" to="/<your_bot>/camera_node/image/compressed"/>
Update the Launch File

In the launch directory, locate the launch file (line_detection_node.launch) and make the following modifications:

 
Namespace Adjustment: Replace instances of paul with your Duckiebot’s specific name. For example:<node pkg="line_detection"

      type="line_detection_node.py"

      name="white_line_detector_follower"

      ns="your_bot_name"

      output="screen">

Configure the Environment Script

Modify the environment.sh script to reflect your Duckiebot’s configuration:
export VEHICLE_NAME=your_bot_name

export ROS_MASTER_URI=http://your_bot_name.local:11311

# Source ROS Melodic

source /opt/ros/melodic/setup.bash

# Source your catkin workspace inside the container

source /code/catkin_ws/devel/setup.bash

# Run project
dts devel build -H your_bot_name -f

dts devel run -H your_bot_name -L run_white_line_follower

 


 
