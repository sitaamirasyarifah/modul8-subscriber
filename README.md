## Module 8

Nama    : Sita Amira Syarifah
NPM     : 2206023023
Kelas   : Adpro - C

**1. What is AMQP?**

AMQP stands for Advanced Message Queuing Protocol. It's an open-standard messaging protocol designed for asynchronous message passing between different systems. Essentially, it's a way for different software components or systems to communicate with each other in a loosely coupled, reliable, and scalable manner. AMQP defines the format and rules for structuring messages and the mechanisms for their exchange between clients and brokers in a message-oriented middleware (MOM) architecture. It's commonly used in distributed systems, cloud computing, and enterprise messaging applications.

**2. What it means? guest:guest@localhost:5672 , what is the first quest, and what is the second guest, and what is localhost:5672 is for?**

"guest:guest@localhost:5672" is a string or URL used to access a service using the AMQP protocol.
The string consists of two parts:
- guest:guest : The first part "guest" is the username or user name used to authenticate to the AMQP service. The second part "guest" is the password corresponding to the username.
- "localhost:5672" : the address or host indicating the location of the AMQP service to be accessed. Here, "localhost" refers to the local computer where the AMQP service is running,
and "5672" is the port number used by the AMQP service to accept connections.

So, this string is used to identify the user (username and password) and the location of the AMQP service to be accessed.

**Simulation slow subscriber**
![Screenshot (462)](https://github.com/sitaamirasyarifah/modul8-subscriber/assets/122429830/1353ab6c-ee0f-4ccb-b547-f5d01f72089f)
From the above image, it can be seen that the total number of messages queued at any given time is approximately 10 messages (I ran cargo run 4 times). This occurs because the subscriber requires more time to process each event in the message queue, resulting in message backlog because the publisher is faster at publishing messages than the subscriber is at processing them.

**Reflection and Running at least three subscribers**
![Screenshot (462)](https://github.com/sitaamirasyarifah/modul8-subscriber/assets/122429830/1353ab6c-ee0f-4ccb-b547-f5d01f72089f)

From the above image, it can be observed that the spike in message queue has decreased compared to before using 3 console subscribers. This is because the main.rs file in the subscriber contains a sleep function (thread::sleep(ten_millis);) which introduces a delay of 1 second (1000 milliseconds) before printing messages. Due to this delay, the program is given more time to process messages sequentially, reducing the queue buildup. Additionally, the use of 3 console subscribers running cargo run simultaneously could also contribute to the reduction in the spike.
