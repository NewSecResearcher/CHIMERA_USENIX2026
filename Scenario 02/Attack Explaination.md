-------------------------------------------------------------------------------------------------------------------------------------


**Scenario Metadata:**


-------------------------------------------------------------------------------------------------------------------------------------


- Scenario Number: 02

- Scenario Name: TF Injection Detection

- Category: Injection Attacks


-------------------------------------------------------------------------------------------------------------------------------------


**Attack Walkthrough:**


-------------------------------------------------------------------------------------------------------------------------------------



1️⃣ Reconnaissance (🔎 Nmap)


	🎯 Objective: Enumerate active TF nodes and topics within the ROS2 environment.



2️⃣ Traffic Monitoring (🌐 DDS Spy)  - as shown in DDS\_Spy\_Tool.png and DDS\_Spy\_Information Gathering.png


	🎯 Objective: Deploy \*\*DDS Spy\*\* passively to monitor messages, detect unusual or malformed data, and gather context for 	  		      injection.


	🔧 Execution: Deploy \*\*DDS Spy\*\* passively to monitor messages, detect unusual or malformed data, and gather context for 			      injection.



3️⃣ Injection (💉 ros2\_fuzz)


	🎯 Objective: Inject malformed or boundary-case TF messages to test system validation and response.


	🔧 Execution: Use \*\*ros2\_fuzz\*\* to actively send malformed TF messages, probing for weaknesses in frame handling and input 		      validation.



4️⃣ Visualization \& Impact Assessment (🖥️ RViz)


	🎯 Objective: Detect operational impact on robot localization and frame transforms.


	🔧 Execution: Visualize TF tree and robot pose in \*\*RViz\*\* to see misalignments or disruptions caused by injected messages.



5️⃣ Recording \& Forensic Analysis (📦 rosbag)


	🎯 Objective: Record injected traffic for replay and post-analysis.


	🔧 Execution: Use \*\*rosbag\*\* to capture the injection session for replay, validation, and further investigation of 		   		      vulnerabilities.



----------------------------------------------------------------------------------------------------------------------------------
