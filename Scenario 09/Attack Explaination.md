--------------------------------------------------------------------------------------------------------------------------------------  

**Scenario Metadata:**  

--------------------------------------------------------------------------------------------------------------------------------------  

- **Scenario Number**: 09  
- **Scenario Name**: Default Credentials  
- **Category**: Configuration Issues  

--------------------------------------------------------------------------------------------------------------------------------------  

**Attack Walkthrough:**  

--------------------------------------------------------------------------------------------------------------------------------------  

1️⃣ Reconnaissance (🔎 Nmap)  

🎯 Objective: Identify IP addresses (`Nmap_Host_Discovery.png`) and exposed services such as SSH (`Nmap_Port_Discovery.png`).  

⚙️ Execution: Nmap scan highlights active ports (e.g., `22/tcp`, `80/tcp`) that could be targeted for login attempts.  



2️⃣ Credential Testing (🔐 Hydra / Burp Intruder)  
*As shown in `Scenario 9a.mp4` and `Scenario 9b.mp4`*  

🎯 Objective: Test for weak or default login credentials.  

⚙️ Execution: Brute-force attempts focus on commonly unchanged defaults, e.g.:  
	- `admin:admin`  
	- `ros:ros`  
	- `admin:password`  

  

3️⃣ Post-Login Enumeration (🧩 LinPEAS / LinEnum + ROS Tools)  

🎯 Objective: Explore the system for privilege escalation paths and ROS access.  

⚙️ Execution:  
	- Run LinPEAS / LinEnum to enumerate misconfigurations and privilege escalation opportunities.  
	- Use ROS tools (`rosnode`, `rosservice`, `rqt_graph`) to check whether the compromised account can access and manipulate ROS 	  	  nodes, topics, or services.  


--------------------------------------------------------------------------------------------------------------------------------------  
