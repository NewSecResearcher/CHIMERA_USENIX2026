-------------------------------------------------------------------------------------------------------------------------------------

**Scenario Metadata:**

-------------------------------------------------------------------------------------------------------------------------------------

- Scenario Number: 10
- Scenario Name: Replay Attack
- Category: Other Scenarios

-------------------------------------------------------------------------------------------------------------------------------------

**Attack Walkthrough:**

-------------------------------------------------------------------------------------------------------------------------------------

1️⃣ Reconnaissance (🔎 Nmap / Zenmap)

&nbsp;&nbsp;🎯 Objective: Perform network reconnaissance to identify live hosts, services, and exposed ROS communication endpoints.

&nbsp;&nbsp;🔧 Execution: Nmap/Zenmap scan reveals open ports and active ROS-related services that can be targeted for traffic capture.

2️⃣ Traffic Capture (🌐 Wireshark / tcpdump / rosbag)

&nbsp;&nbsp;🎯 Objective: Capture legitimate ROS traffic including control commands and sensor data.

&nbsp;&nbsp;🔧 Execution:  

&nbsp;&nbsp;&nbsp;&nbsp;- Use **Wireshark** or **tcpdump** to sniff packets on the ROS network.  

&nbsp;&nbsp;&nbsp;&nbsp;- Alternatively, use **rosbag** to directly record topics such as `/cmd_vel` or `/odom`.  

3️⃣ Replay Attack (🎬 rosbag play)

&nbsp;&nbsp;🎯 Objective: Replay previously recorded ROS traffic to trick the robot into executing stale commands.

&nbsp;&nbsp;🔧 Execution:  

&nbsp;&nbsp;&nbsp;&nbsp;- Inject the `.bag` file back into the ROS network with `rosbag play`.  

&nbsp;&nbsp;&nbsp;&nbsp;- Robot interprets old messages as new, since ROS2 lacks cryptographic timestamps or sequence validation.  

-------------------------------------------------------------------------------------------------------------------------------------
