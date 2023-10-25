# IN265 - Event-Driven Architecture with SAP Integration Suite, Advanced Event Mesh

![Pic 1](images/IN265-1.jpeg)

## Description

An event-driven architecture is a software architecture using events as the core means for interaction between its software components. One of the main components of an EDA are Event Brokers. SAP's flagship event broker is SAP Integration Suite, advanced event mesh.

In this session we will take a deep dive into SAP Integration Suite, advanced event mesh.

## Overview

![Pic 2](images/IN265-2.png)

SAP Integration Suite, advanced event mesh is a fully managed event streaming and management service that enables enterprise-wide and enterprise-grade event-driven architecture. It is a full blown, general purpose Event Mesh. AEM offers enterprise-grade performance, reliability, security and governance. It scales to very large use cases – and very means very very very in this case.

- Advanced Event Mesh is a distributed mesh of event brokers that can be deployed across environments, both in the cloud and on-premise
- It offers a full purpose set of eventing services covering all relevant use cases
- AEM supports event streaming, event management and event monitoring
- Brokers fully scale as required and come in T-shirt sizes to perfectly fit different needs

SAP Integration Suite, advanced event mesh

- is a general purpose, multi-site EDA platform and portal
- allows for SAP to SAP, SAP to Everything and Everything to Everything scenarios
- supports distributed networks of event brokers deployed in different clouds and on-premises
- can be deployed in your cloud of choice or in your on premises K8S
- provides sophisticated authentication and security features like Kerberos, OAuth or TLS
- offers fine-grained filtering options
- allows for real-time monitoring, capacity insights and distributed tracing
- provides support for all relevant protocols like JMS, REST, AMQP and MQTT, plus SMF.
- allows to start small and upgrade to bigger T-shirt sizes when your business grows
- provides an outstanding performance up to billions of events per day

SAP Integration Suite, advanced event mesh features touched, some just shortly, some in more detail, include:

- SAP Integration Suite, advanced event mesh queues
- SAP Integration Suite, advanced event mesh Cluster Manager
- SAP Integration Suite, advanced event mesh Mesh Manager
- SAP Integration Suite, advanced event mesh Event Designer and Event Management
- SAP Integration Suite, advanced event mesh Try Me!

## Requirements

- Understanding the basics of event-driven architectures, namely events, queues, topics, event subscriptions ...
- You would be able to execute most of the exercises without prior experience by just following the descriptions. For taking value out of the chance to explore Advanced Event Mesh some experience with event-driven architectures is recommended.

## Exercises

Preparation and Setup

- [Getting Started](exercises/ex0/)

SAP Integration Suite, advanced event mesh

- [Exercise 1 - Explore SAP S/4HANA Integration Suite, advanced event mesh](exercises/ex1/)

    - [Exercise 1.1 - Log into Advanced Event Mesh and Explore it](https://github.com/SAP-samples/teched2023-IN265/tree/main/exercises/ex1#exercise-11---log-into-advanced-event-mesh-and-explore-it)
    - [Exercise 1.2 - Create a Queue in Advanced Event Mesh ](https://github.com/SAP-samples/teched2023-IN265/tree/main/exercises/ex1#exercise-12---create-a-queue-in-advanced-event-mesh)
    - [Exercise 1.3 - Create a Subscription in Advanced Event Mesh](https://github.com/SAP-samples/teched2023-IN265/tree/main/exercises/ex1#exercise-13---create-a-queue-subscription-in-advanced-event-mesh)
    - [Exercise 1.4 - Send an event from the Try Me! Tool to your Topic](https://github.com/SAP-samples/teched2023-IN265/tree/main/exercises/ex1#exercise-14---send-an-event-from-the-try-me-tool-to-your-topic)

- [Exercise 2 - Topic Hierarchies](exercises/ex2/)

    - [Exercise 2.1 - Learn about Topic Hierarchies and Wildcards](https://github.com/SAP-samples/teched2023-IN265/blob/main/exercises/ex2/README.md#exercise-21-learn-about-topic-hierarchies-and-wildcards)
    - [Exercise 2.2 - Practice Topic Hierarchies and Wildcards using Try Me !](https://github.com/SAP-samples/teched2023-IN265/blob/main/exercises/ex2/README.md#exercise-22-practice-topic-hierarchies-and-wildcards-using-try-me----animal-edition)   

- [Exercise 3 - Persistent and Non-Persistent Quality of Service](exercises/ex3/)

    - [Exercise 3.1 - Learn about Persistency and QoS](https://github.com/SAP-samples/teched2023-IN265/tree/main/exercises/ex3#exercise-31-learn-about-delivery-modes-persistency-and-quality-of-service)
    - [Exercise 3.2 - Experimenting with Persistency](https://github.com/SAP-samples/teched2023-IN265/tree/main/exercises/ex3#experimenting-with-persistency)

- [Exercise 4 - Event Replay](exercises/ex4/)

    - [Exercise 4.1 - Learn about Replay](https://github.com/SAP-samples/teched2023-IN265/blob/main/exercises/ex4/README.md#exercise-41-learn-about)
    - [Exercise 4.2 - Experimenting with Replay](https://github.com/SAP-samples/teched2023-IN265/blob/main/exercises/ex4/README.md#exercise-42-experimenting-with-replay)

- [Exercise 5 - Event-Driven in Action and Sample Architecture](exercises/ex5/)

    - [Exercise 5.1 - A Distributed Smartphone Based Game](https://github.com/SAP-samples/teched2023-IN265/blob/main/exercises/ex5/README.md#exercise-51---a-distributed-smartphone-based-game)
    - [Exercise 5.2 - How to Build this Game using Advanced Event Mesh](https://github.com/SAP-samples/teched2023-IN265/blob/main/exercises/ex5/README.md#exercise-52-how-to-build-this-game-using-advanced-event-mesh)
    - [Exercise 5.3 - Let's play!](https://github.com/SAP-samples/teched2023-IN265/blob/main/exercises/ex5/README.md#exercise-53---lets-play)

## User Data and Password

In order to log into Advanced Event Mesh, you can use the below email address with XXX replaced with your group number.

handson_XXX@education.cloud.sap (e.g. handson_012@education.cloud.sap)

The password will be provided to you by the moderators.

 ## Background Material

A lot of material to get up to speed with SAP Integration Suite, advanced event mesh is available.

- Blogs

    - [SAPs Event-Driven Ecosystem](https://blogs.sap.com/2022/09/01/saps-event-driven-ecosystem-revisited/)
    - [Advanced Event Mesh](https://blogs.sap.com/2022/10/28/turn-your-erp-into-a-team-player-introducing-sap-integration-suite-advanced-event-mesh/ )

- Videos

    - [Discover Event-driven Integrations](https://www.youtube.com/watch?v=r9lyC_2ss2U)
    - [SAP on Azure](https://www.youtube.com/watch?v=NNrzXbX3mk0)

- Documentation

    - [Help](https://help.pubsub.em.services.cloud.sap/Cloud/cloud-lp.htm)

## License
Copyright (c) 2023 SAP SE or an SAP affiliate company. All rights reserved. This project is licensed under the Apache Software License, version 2.0 except as noted otherwise in the [LICENSE](LICENSES/Apache-2.0.txt) file.
