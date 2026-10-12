
# Laboratory 08 – Mission Reflection

Completing this Cloud Security laboratory helped me understand why securing a server is an important part of cloud computing. I learned that running an application successfully is not enough because the server must also be protected against unauthorized access.

First, a host-based firewall protects a server by controlling incoming and outgoing network connections directly on the machine. Even if an attacker gets past the physical network perimeter, the firewall can still block connections that are not permitted by its rules. This provides another layer of defense for the server and its applications.

Second, managing open network ports is important because every unnecessary open port creates another possible entry point for attackers. By allowing only the ports required by the application, administrators can reduce the server's attack surface. In this laboratory, I allowed SSH for administration and TCP port 8080 for the Nginx web application.

Third, leaving a database port such as MySQL port 3306 open to the public internet is dangerous because attackers may attempt to exploit vulnerabilities, guess passwords, or access sensitive information. In a real enterprise environment, database access should normally be restricted to authorized application servers and administrators, with strong authentication and other security controls.

Fourth, this mission changed my perspective on how easily a server could be exposed to security risks. I realized that a running application may be accessible to unauthorized users if network access is not configured carefully. Using UFW helped me understand the importance of setting clear firewall rules and verifying them after configuration.

Finally, having eight cloud laboratory missions in my GitHub portfolio gives me a record of the skills I have practiced, from cloud fundamentals and Docker deployment to monitoring and firewall configuration. The portfolio also helps me demonstrate my progress in Linux administration, troubleshooting, documentation, and basic cloud security. I still need more practice, but these activities have given me a stronger foundation for working with cloud infrastructure safely and responsibly.

