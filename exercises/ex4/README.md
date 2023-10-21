# Exercise 4 - Event Replay

After completing these steps you will have learned about AEM's replay functionality.

## Exercise 4.1 Learn about

Message Replay is an AEM feature that allows an event broker to resend messages to new or existing clients that request them, hours or even days after those messages were first received by the event broker.

> Replay is not enabled by default, it has to be requested via support ticket.

With replay enabled, event brokers store persistent messages in a replay log. These messages are kept until the log is full, after which the oldest messages are removed to free-up space for new messages.

Replay can be performed on a (non-partitioned) queue or topic endpoint. When initiated, you can request all messages in the replay log, all messages following a specified replication group message ID, or all messages starting from a requested replay start time. From the requested starting point, the event broker will deliver, to the queue or topic endpoint, the messages from the replay log that match any subscription on that queue or topic endpoint.

## Exercise 4.2 Experimenting with Replay


For more information about Replay and/or acknowledging messages, check the following links:
[Message Replay](https://docs.solace.com/Overviews/Message-Replay-Overview.htm?Highlight=replay)
[Acknowledging Messages](https://docs.solace.com/Solace-PubSub-Messaging-APIs/API-Developer-Guide/Acknowledging-Messages.htm)

## Summary

You've now explored topic hierarchies and wildcards.

Continue to - [Exercise 5 - Event-Driven in Action and Sample Architecture](../ex5/README.md)
