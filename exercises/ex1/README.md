## Exercise 1.1 - Log into Advanced Event Mesh and explore it

After completing these steps you will have familiarized yourself with AEM.

1. Log into Advanced Event Mesh

Link: https://eu10.console.pubsub.em.services.cloud.sap/login?zone-id=908a280d-c2f1-4d2b-b003-de94ffc5a4ee

User: handson_***@education.cloud.sap (replace *** with your user number)

Password: provided by your moderator
  
2. Explore Advanced Event Mesh  

![Pic 1](/./images/ex1-1.png)

Check out the different areas in the Advanced Event Mesh cockpit , representing the different categories of services AEM offers

- Event Streaming: Mission Control makes it easy to deploy event brokers, create event meshes, and optimize and monitor the health/performance of an event-driven system. Mission Control is a section in the Cloud Console that permits you to access event brokers, visualize and manage your event broker services, and visualize and design event meshes. Mission Control has a Cluster Manager and Mesh Manager that permits you to create event broker services and manage your event mesh.

     - Cluster Manager: event broker services are made available via Cluster Manager. Each event broker service consists of event brokers configured in a High-Availability (HA) setup.

     - Mesh Manager: use Mesh Manager to connect multiple event broker services that span different data centers to create an event mesh. An event mesh is an architectural layer that allows events from one application to be dynamically routed and received by any other application no matter where these applications are deployed (no cloud, private cloud, public cloud). This layer is composed by a network of event broker services. Event broker services are a modern form of messaging middleware, which are designed to move events across the distributed enterprise.

- Event Management: Event Portal provides event management services. This subscribed service provides powerful tools to create, design, share, and manage various aspects of an EDA based on event brokers or other streaming technologies (such as Kafka). 

- Event Monitoring and Insights: With Insights, we provide curated dashboards, easy-to-understand visualizations based on historical and real-time metrics, and timely notifications about your event broker services. This advanced information allows you to identify problems before they occur and helps you to better manage your services as your EDA scales. You can work with SAP to configure your monitoring to meet your needs. For advanced monitoring requirements, there's a single entry point to build custom visualizations to meet your organization's requirements. Coupled with visualizations is a notification email framework that alerts you when key metrics fall outside of your established thresholds. These notifications allow you to monitor what's occurring and correct developing issues before they impact or degrade your EDA. You can configure these notifications to integrate with your existing notification and logging systems.

3. Click on Cluster Manager

![Pic 13](/./images/ex1-13.png)  

Hint: if you don't see any broker, please uncheck Only show my services

![Pic 13](/./images/ex1-16.png)  

4. Select a Broker by clicking on it

5. Click Open Broker Manager

![Pic 14](/./images/ex1-14.png)  

6. Explore the Broker Manager

![Pic 15](/./images/ex1-15.png)  

On the left side of the screen are the main sections to navigate through:

- Message VPN: VPN-level stats and config (a Message VPN is a virtual partition of a single broker... one AEM broker can host multiple Message VPNs, and each VPN can have different authorization schemes and topic spaces; client/messaging application activity happens within the scope of a VPN)
- Clients: information about connected and configured client applications
- Queues: used for Guaranteed / persistent messaging
- Connectors: helpful wizards to connect to a variety of web services
- Access Control: where you create new client usernames, ACL profiles, and client profiles
- Replay: where you can enable replay, to allow the broker to send previous messages again NOTE: Solace brokers do not use replay for recovery of persistent data (like Kafka)... there is a more fine-grained approach in Solace where each individual message is ACKnowledged to the broker when the consumer application is done with it
- Try Me! this is where we will connect two WebSocket test applications

## Exercise 1.2 - Create a queue in Advanced Event Mesh

After completing these steps you will have created a queue in Advanced Event Mesh.
  
1. Go back to the original tab in your browser and click on Cluster Manager on the left
  
![Pic 2](/./images/ex1-2.png)  
  
2. In the All Services screen click on the Broker Europe Tile (Frankfurt)
  
![Pic 3](/./images/ex1-3.png)    
  
HINT: If you cannot see the tiles, uncheck the Only show my services box
  
3. Click in Manage
  
![Pic 4](/./images/ex1-4.png)     
  
4. Under Broker Manager Quick Setting click the Queues tile. A new window opens up.
  
![Pic 5](/./images/ex1-5.png)      
  
5. Click the +Queue button on the top right
  
![Pic 6](/./images/ex1-6.png)        
  
6. In the pop up enter the queue name: BLR_*** (replace *** with your number)
  
7. Click Create
  
![Pic 7](/./images/ex1-7.png)      
  
8. On the next screen click Apply
  
![Pic 8](/./images/ex1-8.png)      
  
9. Check whether you can find your queue in the list  

![Pic 9](/./images/ex1-9.png)   

## Exercise 1.3 - Create a queue subscription in Advanced Event Mesh

10. Click on your queue

11. Click on Subscriptions

![Pic 10](/./images/ex1-10.png)  

12. Click on +Subscription

13. Enter the topic into the field. Use BLR_topic_XXX as the topic, and replace XXX with your group/participant number.

![Pic 11](/./images/ex1-11.png)  

HINT: Please note that this topic is very simple to facilitate this exercise. In real world scenarios, you can work with topic hierarchies that allow for filtering etc. We will dive into this later.

14. Click on Create

15. Check on whether your queue subscription got created

![Pic 12](/./images/ex1-12.png)  

## Exercise 1.4 - Send an event from the Try Me! tool to your topic

16. Keep your current browser tab open and go back to the other/main tab and click on Try Me!

![Pic 17](/./images/ex1-17.png)  

17. Click on Connect in the Publisher Section 

![Pic 18](/./images/ex1-18.png)  

18. Enter your topic

![Pic 19](/./images/ex1-19.png)  

19. Click Publish to send your message (most likely Hello World!) to your topic

20. You should see 1 message published in the Publish Status

![Pic 20](/./images/ex1-20.png)  

21. Switch back to the other tabe / the broker level tab and go to your queue and click on Summary

![Pic 21](/./images/ex1-21.png)  

22. You should see 1 Message Queued

![Pic 22](/./images/ex1-22.png)  

You have sent a message to a topic, and via the subscription this message has been stored in your queue.

23. You can leave it like this or you can play the same game a little longer: go back to the Try Me! tool and just click publish, and see in the other tab how the count of messages gets increased (don't forget to refresh the page).

![Pic 23](/./images/ex1-23.png)  
  
## Summary

You have now created a queue in AEM and have subscribed to events via a topic. You have sent events to this topic using the Try me! tool. 

Please continue with [Exercise 2 - Explore Topic Hierarchies and Wildcards](../ex2/README.md)

