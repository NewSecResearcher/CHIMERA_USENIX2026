╔════════════════════════════════════════════════════════════════════╗
║       SCENARIO REPORT FILE       ║        Web Application          ║
║																	 ║        Vulnerabilities          ║
╠════════════════════════════════════════════════════════════════════╣
║ Scenario Number : 06                                               
║ Scenario Name   : Dashboard / API Hijack                           
╚════════════════════════════════════════════════════════════════════╝


[ SYSTEM SPECIFICATION ]
─────────────────────────────────────────────────────────────────────
• Operating System : Ubuntu 22.04.5 LTS
• ROS Version      : ROS2 Humble
• Simulator        : Gazebo Ignition
• Hardware Setup   : Virtual Machine (4 vCPUs, 8 GB RAM, 60 GB disk)
• Network          : Two VM topology (Attacker + Victim, NAT/Bridge)


[ TOOLS REQUIRED ]
─────────────────────────────────────────────────────────────────────
→ Nmap / Zenmap   	  :: Network reconnaissance & web port discovery  
→ OWASP ZAP / BurpSuite   :: Automated web vulnerability scanning (auth, injection, session flaws)  
→ MITMproxy        	  :: Live interception and manipulation of API traffic  


[ ATTACK EXPLANATION ]
─────────────────────────────────────────────────────────────────────
The attack begins with **reconnaissance**: Nmap/Zenmap scans the network 
to discover open web ports, dashboard endpoints, and API services exposed 
by the robot.  

Once the footprint is mapped, **automated scanners** (OWASP ZAP, BurpSuite) 
are used to test the dashboards and APIs. These tools look for issues like:  
  • Authentication bypass  
  • Injection points  
  • Weak or missing session management  

After identifying weaknesses, attackers escalate by using **MITMproxy or BurpSuite** 
to intercept live API traffic, modify requests/responses, and hijack 
control of the dashboard.  

Exploitation mapping:  
  • TS2 → Compromised API calls directly control ROS nodes.  
  • TS3 → Hijacked dashboard sends malicious ROS messages.  
  • TS5 → Exploitation of the robot’s web interface/dashboard layer.  


[ POSSIBLE REAL-LIFE SCENARIOS ]
─────────────────────────────────────────────────────────────────────
✦ Unauthorized user hijacking a robot’s web dashboard to override operator commands.  
✦ Industrial APIs exploited to inject malicious job requests, halting production.  
✦ Remote attacker modifying telemetry APIs to feed false data to operators.  
✦ Delivery, patrol compromised through OTA vulnerabilities via exposed dashboards.  


[ REFERENCES ]
─────────────────────────────────────────────────────────────────────
1. OWASP API Security Top 10 — https://owasp.org/API-Security/  
2. MITMproxy Documentation — https://mitmproxy.org/  
3. BurpSuite User Guide — https://portswigger.net/burp/documentation  
4. Research on robot dashboard vulnerabilities: IEEE/ACM security papers.  

─────────────────────────────────────────────────────────────────────
                 END OF SCENARIO REPORT — #07
─────────────────────────────────────────────────────────────────────
