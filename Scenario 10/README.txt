
╔════════════════════════════════════════════════════════════════════╗
║                       SCENARIO REPORT FILE                         ║  OTHER SCENARIOS  ║
╠════════════════════════════════════════════════════════════════════╣
║ Scenario Number : 10                                            
║ Scenario Name   : Replay Attack                                    
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
→ Nmap / Zenmap      :: Network reconnaissance & service discovery  
→ rosbag             :: Recording & replaying ROS messages  
→ Wireshark          :: Packet sniffing & protocol analysis  


[ ATTACK EXPLANATION ]
─────────────────────────────────────────────────────────────────────
The adversary begins by capturing live ROS network traffic. This can be 
achieved using Wireshark, tcpdump, or directly with rosbag to record 
legitimate control commands and sensor data exchanged between nodes.  

The recorded data is saved into a rosbag file and later **replayed** back 
into the ROS network. Because ROS lacks cryptographic timestamps or 
sequence validation, the robot interprets these stale commands as fresh, 
resulting in unintended actions.  

Key exploitation points:
  • TS2 → Nodes accept old but valid messages.  
  • TS3 → Replayed data injected into ROS topics.  
  • TS7 → Forensic timing analysis can reveal duplicates.  


[ POSSIBLE REAL-LIFE SCENARIOS ]
─────────────────────────────────────────────────────────────────────
✦ Delivery Robot → Replaying past “go to location” commands, sending it 
  back to completed tasks.  
✦ Drone Systems → Replaying “land” or “takeoff” instructions mid-flight, 
  creating safety hazards.  
✦ Industrial Robots → Triggering outdated assembly actions, causing 
  operational disruption or safety risks.  


[ REFERENCES ]
─────────────────────────────────────────────────────────────────────
1. CVE-2021-38425: Replay attack vulnerability in ROS2 middleware.  
2. Alias Robotics: Security assessments on ROS replay threats.  
3. Wireshark Documentation — https://www.wireshark.org/docs/  
4. ROS2 rosbag Tutorials — https://docs.ros.org/en/humble/Tutorials/  

─────────────────────────────────────────────────────────────────────
                 END OF SCENARIO REPORT — #12
─────────────────────────────────────────────────────────────────────
