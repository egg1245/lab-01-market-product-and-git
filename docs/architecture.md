## Product Choice

- Telegram
- <https://web.telegram.org>
- Telegram is a secure messenger for quick message exchange.

## Main components

![Telegram Component Diagram](./diagrams/out/telegram/component-diagram/Component%20Diagram.svg)

[Telegram Component Diagram Code](./diagrams/src/telegram/component-diagram.puml)

- MTProto Protocoal encapsulates Mobile App, Desktop App and Client App.
- Internal RPC connects internals of app.
- Auth & Session Service is used for accessing messenger.
- Message Handling Service is used for sending, deleting, and editing messages
- Notification/Updates Service monitors changes.

# Data flow

![Telegram Sequence Diagram](./diagrams/out/telegram/sequence-diagram/Sequence%20Diagram.svg)

[Telegram Sequence Diagram Code](./diagrams/src/telegram/sequence-diagram.puml)

Event Propogation. From Message Service event NewMessageUpdate is published, which possibly contains message data like time and value. From Kafka Event Bus happens Consume (Sync to Online Devices), which maybe checks some metadata and based on it syncing.. From MTProto Gateway UI updates, just based on new data rerendering happens.

## Deployment

![Telegram Deployment Diagram](./diagrams/out/telegram/deployment-diagram/Deployment%20Diagram.svg)

[Telegram Deployment Diagram](./diagrams/src/telegram/deployment-diagram.puml)

Components are deployed in Telegram Global Infrastructure (Primary DC). It goes into connection layer, then into a Computer Cluster.

## Assumptions

I assume that Media Service uses global cache to reduce latency in the network.

## Open questions

How does Media is stored for fast access? How Push Notification Service works in Secret chats with Internet connection instability?
