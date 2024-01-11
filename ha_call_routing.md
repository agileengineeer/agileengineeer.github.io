---
title: HA Call Routing
layout: home
---


## How to Reroute Calls from Primary Phone Number in Case of Overload

To reroute calls from the primary phone number in the event of an overload, you can follow these steps:

1. **Assess Call Volume**: Monitor call volume regularly to determine when the primary system is approaching overload.

2. **Set Thresholds**: Define thresholds that indicate when the system is getting overloaded. For example, if call queues exceed a certain limit or if agents' occupancy rate reaches a critical level.

3. **Automatic Call Distribution (ACD):** Use ACD systems to distribute incoming calls to agents. Configure the ACD to include overflow settings. When the defined thresholds are reached, the ACD will automatically start routing calls differently.

4. **Create Overflow Queues:** Set up overflow queues for calls that cannot be immediately answered by agents on the primary system. These overflow queues should be associated with the backup phone number or backup server.

5. **Configure Routing Rules:**
   - Define routing rules in your telephony system to send excess calls to the overflow queues.
   - Redirect calls to a secondary phone number or server when the primary system is unable to handle the load.

6. **Announcements:** Create announcements for callers who are placed in overflow queues. Let them know that their call will be answered shortly or provide other relevant information.

7. **Prioritize Queues:** Configure your call routing rules to prioritize queues based on the importance of the calls. Critical calls can be prioritized over non-urgent ones.

8. **Agent Availability:** Ensure that agents are logged into both the primary and backup systems. This way, they can seamlessly handle calls from either system when needed.

9. **Failover Testing:** Periodically test your failover and call rerouting procedures to ensure they work as expected.

10. **Continuous Monitoring:** Continuously monitor call traffic and adjust routing rules as needed to maintain efficient call handling and prevent overload.

By setting up these call routing and queuing mechanisms, you can effectively reroute calls from the primary phone number when it becomes overloaded, ensuring that customers are served without disruption even during high call volumes.






####
Credits ChatGPT
