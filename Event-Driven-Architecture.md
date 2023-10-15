# Overview

- Facilitates the efficient production and consumption of events or state changes.
- Enables near real-time updates by supporting connections between processes that take place across multiple systems.
- Use Pub/Sub API for any future publish/subscribe patterns instead of building your own event handlers using other APIs including Streaming API.

# Architecture Types

## Publish / Subscribe

- Multiple publishers and subscribers share data through a shared event bus.
- No direct connection between publishers and subscribers.
- The same system can be both a publisher and a subscriber.

## Fanout

- Messages are delivered to one or multiple subscribers through a single message queue.
- Subscribers retrieve the same message from the queue, rather than their own unique copy.
- More difficult to verify whether or not a subscriber received a message.

## Claim Check

- Instead of the complete representation of the transformed data being passed through the event bus, the message body is stored independently, while a message header containing a pointer to where the data is stored (a claim check) is sent to the subscribers. 
- Benefits of this pattern are lower data volumes being sent through the event bus and increased likelihood that messages will fit within the size limitations of the subscribing systems.
- Usage: Large message volume, longer retention requirements

## Streaming

- Subscribers access each event stream and process the events in the exact order in which they were received.
- Unique copies of each message stream are sent to each subscriber, which makes it possible to guarantee delivery and identify which subscribers received which streams.

## Queuing

- Producers send messages to queues, which hold the messages until subscribers retrieve them.
- FIFO
- Each subscriber has a unique queue, which requires additional set up steps but makes it possible to guarantee delivery and identify which subscribers received which messages.

# Implementation

- Structure event payloads carefully. Smaller message sizes reduce processing but will increase message volume. Tradeoffs.
- Avoid looping, ex. two systems that publish events when records are updated, while also listening for each other’s events, which trigger additional published events when they’re processed.

# References

[Salesforce Architect - Event-Driven Architecture](https://architect.salesforce.com/decision-guides/event-driven)
