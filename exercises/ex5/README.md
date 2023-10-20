# Exercise 5 - Event-Driven in Action and Sample Architecture

You have worked hard in the last about 100 minutes. Now it is time for some fun. Well, fun with some additional learning that is.

![Pic 1](/./images/ex5-1.png)

## Exercise 5.1 - A Distributed Smartphone Based Game

Use Case: Christian would like to develop a distributed smartphone-based game. He is a polular guy and has lots of friends - so he expects that up to 100 of his friends could participate in a session of the game. The lower limit would be two players. The game should support up to 4 teams. Since Christian loves racing games and is big on boats, he decides for a DRAGON BOAT RACE.

### Details: Players need to

- Connect
- Discover / choose a race
- Participate by rowing (i.e. tap tap tap)
- See progess and final results

### Needed Components:

- Web server to host components
- Race controller application
- Race display for participants
- Mobile frontend (JavaScript or Android/iOS app)

## Exercise 5.2 How to build this game using Advanced Event Mesh

Building the app the event-driven Advanced Event Mesh way:

- all players and race controller connected to AEM
    - for players on mobile, use WebSocket communication (either MQTT or SMF)
- Non-persistent messages for all communication since they are faster and have less latency
- Definition of topic space for applications to communicate

### Topic Space:

- boat/meet/query							        // which races are there?
- boat/meet/[MeetId]/join				      // join this particular race
- boat/player/[PlayerId]/prep			    // assigned a race, and a team
- boat/player/[PlayerId]/team/[Team]	// you’ve been assigned to this team
- boat/race/[RaceId]/marks			    	// on your marks!  5 second countdown
- boat/meet/[RaceId]/ready				    // player reports ready for race
- boat/race/[RaceId]/[PlayerID]/row	  // each stroke, each tap
- boat/race/[RaceId]/stats				    // race progress stats, every 500ms

Some of these indicate events (join, marks, row), others data (stats)

### Design / Implementation examples:

How to start the race?

- When players join a race, controller notifies of unique race ID
- Players subscribe to all related messages: boat/race/[RaceID]/>
- Race controller simply sends one message on: boat/race/[RaceID]/marks
- By pub/sub design, each player receives the message

![Pic 3](/./images/ex5-3.png)

Send each and every row event?

- Yes! Each and every tap becomes a message. Truly event-driven communication
- Use of WebSocket: efficient, bi-directional, streaming asynchronous messaging protocol
- Can easily scale up to 10s or 100s of messages per second per player
- AEM can easily handle this and supports thousands of messages per second

By the way, the events will be counted and presented after the event.

![Pic 5](/./images/ex5-5.png)

## Exercise 5.3 - Let's Play!

Now, after all the hard work, it is time for a good game of Dragon Boat ...

![Pic 4](/./images/ex5-4.png)

## Summary

In this section you have seen the architecture and the components of a distributed smartphone based game. Then you have rowed a dragan boat ...




