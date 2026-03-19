# connection

Buffered wrapper for an event-based TCP sockets. All calls are guaranteed to not block.

## Receiving

Incoming data is buffered as it arrives. Data-received notifications are re-raised so long as
incoming content continues to be consumed by the event recipient.

Connections are automatically closed if incoming data reaches the connection's specified buffer
limit and the event receipient still consumes no data.

## Sending

Outgoing data is queued internally to be sent when possible. Enqueued data is eagerly moved into the
platform's socket send buffer. If the length of internally-enqueud data reaches the (optional,
per-connection) limit, the connection is automatically closed.
