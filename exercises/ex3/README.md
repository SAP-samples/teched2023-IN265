# Exercise 3 - Persistent and Non-Persistent

After completing these steps you will have learned about ...

## Exercise 3.1 Learn about delivery modes, persistency and quality of service

Advanced Event Mesh supports multiple delivery modes  for your events and messages. In this section we will explore what they are and how to use them.

### Persistence

Persistence refers to the Quality-of-Service (QoS) of event messages, which can be classified as Persistent (Guaranteed) or Non-Persistent.

Event Messages are considered persistent if they are placed onto non-volatile storage media after they arrive on the broker. The broker's Data Plane stores a message if the message arrives with the `Persistent Delivery Mode` set to `Persistent`, or if a queue or durable topic endpoint has subscribed to a topic where messages are persisted regardless of the `Persistent Delivery` Mode flag setting in the message.

If an event message is sent with `Persistent Delivery Mode` set to `Direct`, which is synonymous with `Non-Persistent`, the message is only placed onto the non-volatile storage media if the message is subscribed by a Queue or a Durable Topic Endpoint. Messages flagged as `Persistent` result in an acknowlegment message being sent back to the producer after the message is stored.

 In other words, AEM broker distinguish between the sender's persistency mode controlled by the flag on the message and the subscriber's persistency mode controlled by the existence or non-existence of a queue or topic-endpoint.

 If a publisher wants to make sure that they can detect (and react to) any messages being lost on the network, they should set the `Persistent Delivery Mode` to `Persistent` on the message they are publishing. This will cause the broker to acknowledge event messages it has successfully received (and processed) or sent an negative acknowledgement if anything went wrong.

 If a subscriber wants to make sure they do not loose any event messages, then they should always set up a queue (or topic endpoint) and add their subscription on that endpoint. We refer to this as topic to queue mapping. This will ensure that all event messages matching the subscriptions will be stored in the persistent endpoint on the broker and delivered to the consumer in a lossless/guaranteed way.
 Consumers are then expected to acknowledge the successful receipt of each message, after which (and only under that circumstance) the broker will remove the event message from the queue/endpoint.

 Persistent message delivery is also referred to by other names depending on the protocol or context, here are some synonyms and similar terms:
 - `Guaranteed Messaging`, `QoS1` (and `QoS2`), `at-least-once delivery` (and sometimes `exactly-once delivery`)

 Non-Persistent message delivery is also referred to by other names depending on the protocol or context, here are some synonyms and similar terms:
 - `Direct Messaging`, `QoS0`, `at-most-once delivery`

### Experimenting with Persistency

In this section we are going to play a bit around with persistency to see what this really means in a practical example using the broker's built-in Try-Me tab.

> Note, there are two different `Try-Me` tabs in AEM, one on the Cloud Console or cockpit on each service and one built into the admin UI of each broker service themself. You have used the former one previously. We are going to use the latter one now.

So, let's open up the broker UI's `Try-Me` tab next.

1. Go to the AEM Console and click on Cluster Manager.
![AEM Console](images/AEMCloudConsoleSelectClusterManager.png)

2. Click on the same service you have used previously.
![AEM services](images/ex3-2.png)

3. Go to the Management tab and click on the Queues tile.
![AEM Manage Queues](images/AEMServiceManagement.png)

4. Switch to the `Try-Me` tab
![AEM Broker Try-Me](images/AEMBrokerTryMeTab.png)

5. Open the connection details (">" nect to "Connect" button), change the port in the URL from 1443 to 443, "Client Username" to `solace-cloud-client` and populate "Client Password" from the "Service Details" "Connect" tab (open up "Solace Web Messaging" and copy the password) from the AEM Cloud Console, then hit connect.
![AEM Broker Connect](images/AEMBrokerTryMeConnection.png)

6. Your publisher should now be Connected.
![Publisher connected](images/AEMTryMePublisherConnected.png)

7. Enter the topic into the topic field for the publisher. Use BLR_topic_XXX as the topic, and replace XXX with your group/participant number. And publish one message as direct.
![Publish 1](images/AEMTryMePublish1.png)

> Did you receive anything?<br>
No, of course not. Our Subscriber is not connected. Let's go ahead and connect that one now.

8. Hit Connect on the Subscriber side. Your Subscriber should now be connected.
![Subscriber connected](images/AEMTryMeSubscriberConnected.png)

9. Enter the topic into the topic field for the subscriber. Use BLR_topic_XXX as the topic, and replace XXX with your group/participant number. And hit "Subscribe".
![Subscriber subscribed](images/AEMTryMeSubscriberSubscribed.png)

> Did you receive anything now?<br>
No, still not. Our subscriber is using direct/non-persistent mode to subscribe directly to the topic on the broker. There's no persistency endpoint configured, so we don't receive any messages that were published while we were not subscribed or connected.<br>
Let's go ahead and publish another message.

10. Hit publish one more time.
![AEM Direct Message Received](images/AEMTryMeDirectMessageReceived.png)

> Now we've received a message, because both our publisher and subscriber are connected at the same time! This is non-persistent messaging, sometimes also referred to as best-effort messaging. Publishers and Subscribers need to be connected at the same time and reachable so that the messages can be delivered immediately from memory (meaning no network issues). This is the fastest mode, but it's not guaranteed to be lossless.

11. Publish a couple more messages, then clear your subscribers' messages and remove the topic subscription.
![Subscriber clear](images/AEMTryMeSubscriberClear.png)

12. Click on `Bind to an endpoint to receive guaranteed messages`, then enter the queue name: BLR_*** (replace *** with your number) in the field for the queue.
![Bind to endpoint](images/AEMTryMeBindToEndpoint.png)

13. Click on `Start Consume`.
![Consume from queue](images/AEMTryMeConsumeFromQueue.png)

> What happened?<br>
Did you receive multiple messages just now?<br>
How is that possible?<br>
Well, the answer lies in the persistent delivery mode aka guaranteed messaging and the queue we set up earlier today. We also added a subscription to this queue to our topic.
Now while we were happily experimenting with the `Try-Me` tab here publishing to our topic and seeing if we receive any messages, all those messages were simultaneously attracted to our queue by our previously set up subscription and stored there for later consumption.<br>
Now when we started our Queue consumer on our Try-Me tab just now, we just received all those stored messages that were published between when we set up the queue and assigned the subscription and now.<br>
This is persistent messaging, publishers and consumers don't need to be online or processing messages at the same speed. The broker will securely store all messages matching the queue's subscription and deliver it securely to the consumer when it comes online or is ready to process messages.

## Summary

You've now explored different delivery modes on the consumer side and the effect they have on message delivery and message loss.

Continue to - [Exercise 4 - Event Replay](../ex4/README.md)
