-------------------------------------------------------------------------------------------------------------------------------------



**Scenario Metadata:**



-------------------------------------------------------------------------------------------------------------------------------------



\- Scenario Number: 10

\- Scenario Name: Replay Attack

\- Category: Other Scenarios



-------------------------------------------------------------------------------------------------------------------------------------



**Attack Walkthrough:**



-------------------------------------------------------------------------------------------------------------------------------------

1️⃣ Reconnaissance (🔎 Nmap / Zenmap)



&nbsp;	🎯 Objective: Perform network reconnaissance to identify live hosts, services, and exposed ROS communication endpoints.



&nbsp;	🔧 Execution: Nmap/Zenmap scan reveals open ports and active ROS-related services that can be targeted for traffic capture.







2️⃣ Traffic Capture (🌐 Wireshark / tcpdump / rosbag)



&nbsp;	🎯 Objective: Capture legitimate ROS traffic including control commands and sensor data.



&nbsp;	🔧 Execution:  

&nbsp;		- Use \*\*Wireshark\*\* or \*\*tcpdump\*\* to sniff packets on the ROS network.  

&nbsp;		- Alternatively, use \*\*rosbag\*\* to directly record topics such as `/cmd\_vel` or `/odom`.  







3️⃣ Replay Attack (🎬 rosbag play)





&nbsp;	🎯 Objective: Replay previously recorded ROS traffic to trick the robot into executing stale commands.



&nbsp;	🔧 Execution:  

&nbsp;		- Inject the `.bag` file back into the ROS network with `rosbag play`.  

&nbsp;		- Robot interprets old messages as new, since ROS2 lacks cryptographic timestamps or sequence validation.  

&nbsp;



-------------------------------------------------------------------------------------------------------------------------------------



