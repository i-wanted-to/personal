# socket

Cross-platform allocation-free event-based sockets. Supports:
* Windows
* Linux
* macOS
* Android
* iOS

Connection events follow a strict order:
- Exactly one "established" event, bringing the connection into existence
- Zero or more "readable"/"writeable" events
- Exactly one "terminated" event, guaranteed to be delivered for every "established" connection.
