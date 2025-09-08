-------------------------------------------------------------------------------------------------------------------------

**Scenario Metadata**

-------------------------------------------------------------------------------------------------------------------------

🆔 Scenario Number: 06
📝 Scenario Name: Dashboard / API Hijack
📂 Category: Web Application \& API Exploitation

-------------------------------------------------------------------------------------------------------------------------

**Attack Walkthrough**

-------------------------------------------------------------------------------------------------------------------------

1️⃣ Reconnaissance (🔎 Nmap / Zenmap)



	🎯 Objective: Discover IP addresses, live hosts, open HTTP(S) ports, and exposed services.

	⚙️ Execution: Nmap scan reveals the dashboard’s web interface and associated API endpoints.

	🖼 Evidence: Nmap\_Host\_Discovery.png → shows discovered hosts and service banners.



2️⃣ Vulnerability Scanning (🕷 ZAP / BurpSuite)



	🎯 Objective: Assess the web dashboard and API for weaknesses.

	⚙️ Execution: Automated scan uncovers:

		- Weak or missing authentication
		- Injection flaws (SQLi, command injection, etc.)
		- Poor session management, etc.



	📊 Outcome: Parameters and API endpoints susceptible to manipulation are mapped.

	🎥 Evidence: scenario 6.mp4 → demonstrates dashboard scanning in action.



3️⃣ Exploitation (⚡ MITMproxy / BurpSuite Intercept)



	🎯 Objective: Actively manipulate dashboard → API communication.

	⚙️ Execution: 
		- Requests intercepted \& potential modification (speed=1.0 → speed=5.0) 
		- Potential malicious ROS messages injection

-------------------------------------------------------------------------------------------------------------------------

