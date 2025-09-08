-------------------------------------------------------------------------------------------------------------------------

**Scenario Metadata:**

-------------------------------------------------------------------------------------------------------------------------
- Scenario Number: 10
- Scenario Name: Replay Attack
- Category: Other Scenarios

-------------------------------------------------------------------------------------------------------------------------

**Attack Walkthrough:**

-------------------------------------------------------------------------------------------------------------------------

1️⃣ Reconnaissance (🔎 Nmap) - as shown in Nmap_Port_Discovery.png


	🎯 Objective: Perform network reconnaissance to identify live hosts, services, and exposed ROS communication endpoints. 		             



2️⃣ Traffic Capture (🌐 Wireshark / tcpdump / rosbag) - as shown in Capture_Traffic.png


	🎯 Objective: Capture legitimate ROS traffic including control commands and sensor data.

	🔧 Execution: 
		- Use **Wireshark** or **tcpdump** to sniff packets on the ROS network.   
		- Alternatively, use **rosbag** to directly record topics such as `/cmd_vel` or `/odom`.  



3️⃣ Replay Attack (🎬 rosbag play)


	🎯 Objective: Replay previously recorded ROS traffic to trick the robot into executing stale commands.

	🔧 Execution:
		- Inject the `.bag` file back into the ROS network with `rosbag play`.   
		- Robot interprets old messages as new, since ROS2 lacks cryptographic timestamps or sequence validation.   

-------------------------------------------------------------------------------------------------------------------------