1. How much data your publisher program will send to the message broker in one run? 
This publisher will send exactly five messages to the broker in a single run. Each message is a Borsh serialized struct containing two strings: user_id and user_name. Borsh adds length prefixes to each string, so the payload for each message is on the order of 20–30 bytes. Including AMQP framing and network headers, the total transfer remains a few hundred bytes at most. In short, five small, serialized events are published per execution.

2. The url of: “amqp://guest:guest@localhost:5672” is the same as in the subscriber program, what does it mean?
Using the same URL in both programs means both connect to the same broker. The guest:guest part is the default login name and password. The localhost hostname indicates the broker runs on the local machine. Port 5672 is the standard listening port for AMQP. With identical connection details, the subscriber receives every message the publisher sends.

### Running RabbitMQ as message broker
![Alt text](img/image.png)


### Sending and processing event.

![Alt text](img/image2.png)