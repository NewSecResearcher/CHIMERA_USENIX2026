╔════════════════════════════════════════════════════════════════════╗
║           SCENARIO REPORT FILE                 ║ Injection Attacks ║
╠════════════════════════════════════════════════════════════════════╣
║ Scenario Number : 02                                               
║ Scenario Name   : TF Injection Detection                           
╚════════════════════════════════════════════════════════════════════╝


[ SYSTEM SPECIFICATION ]
─────────────────────────────────────────────────────────────────────
• Operating System : Ubuntu 22.04.5 LTS
• ROS Version      : ROS2 Humble
• Simulator        : Gazebo Fortress
• Hardware Setup   : Virtual Machine (4 vCPUs, 8 GB RAM, 60 GB disk)
• Network          : Two VM topology (Attacker + Victim, NAT/Bridge)


[ TOOLS REQUIRED ]
─────────────────────────────────────────────────────────────────────
→ Aztarna        :: Reconnaissance of ROS/DDS endpoints and TF topics  
→ DDS Spy        :: Passive traffic monitoring for topic/message patterns  
→ ros2_fuzz      :: Injection of malformed or boundary TF messages  
→ RViz           :: Visualization to detect disruptions in localization/frames  
→ rosbag         :: Recording and replaying traffic for forensic validation  


[ ATTACK EXPLANATION ]
─────────────────────────────────────────────────────────────────────
The TF injection scenario begins with **Aztarna reconnaissance**, used to 
enumerate active TF nodes and topics within the ROS2 environment. Once 
topics are mapped, **DDS Spy** is deployed for passive monitoring to observe 
traffic patterns and identify abnormalities in TF broadcasts.  

Next, **ros2_fuzz** actively injects malformed or boundary case TF messages, 
probing the system’s ability to validate inputs and handle unexpected data. 
During these injections, **RViz visualization** highlights any resulting 
misalignments in robot localization or frame transforms, exposing the 
direct operational impact. **rosbag** supports recording of the injected 
traffic for replay, aiding in post-analysis and validation.  

This chain of actions demonstrates how the absence of strong publisher 
authentication and inadequate parameter validation allows cyber-level 
attacks to manifest as unsafe physical behaviors in robotic systems.  

Exploitation mapping:  
  • TS2 → Node authentication bypassed, malicious publishers accepted.  
  • TS3 → Malicious TF data injected into control topics.  


[ POSSIBLE REAL-LIFE SCENARIOS ]
─────────────────────────────────────────────────────────────────────
✦ Autonomous vehicle navigation disrupted by fake TF frames injected 
  into the localization pipeline.  
✦ Industrial robot arm misaligned due to spoofed coordinate transforms.  
✦ Drones manipulated by injected TF data causing orientation errors.  
✦ Research robots providing misleading sensor-visualization in RViz.  


[ REFERENCES ]
─────────────────────────────────────────────────────────────────────
1. Aztarna Tool — https://github.com/aliasrobotics/aztarna  
2. DDS Spy — https://github.com/aliasrobotics/dds-spy  
3. ros2_fuzz: ROS2 fuzzing utilities (research prototype tools).  
4. RViz Visualization — https://docs.ros.org/en/humble/Tutorials/  
5. Academic work on TF injection vulnerabilities in ROS-based robots.  

─────────────────────────────────────────────────────────────────────
                 END OF SCENARIO REPORT — #02
─────────────────────────────────────────────────────────────────────
