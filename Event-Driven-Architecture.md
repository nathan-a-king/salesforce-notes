# Overview

- Facilitates the efficient production and consumption of events or state changes.
- Enables near real-time updates by supporting connections between processes that take place across multiple systems.
- Use Pub/Sub API for any future publish/subscribe patterns instead of building your own event handlers using other APIs including Streaming API.

# Publish / Subscribe

- Multiple publishers and subscribers share data through a shared event bus.
- No direct connection between publishers and subscribers.
- The same system can be both a publisher and a subscriber.

# Fanout

- Messages are delivered to one or multiple subscribers through a single message queue.
- Subscribers retrieve the same message from the queue, rather than their own unique copy.
- More difficult to verify whether or not a subscriber received a message.

# References

[Salesforce Architect - Event-Driven Architecture](https://architect.salesforce.com/decision-guides/event-driven)
