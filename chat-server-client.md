# Chat Server & Client

By [Stacey Sern](https://github.com/staceysern)

Build a chat server and a client to work with it.  The server should accept multiple concurrent connections from clients and transmit messages between them.

## Basic Instructions
1. Create an echo server which binds to a socket, and listen and accepts incoming connection requests and echoes back any bytes that it receives. To connect to the server running on your machine, you can use telnet also running on your machine (telnet localhost <port #>).
2. Create a client which initiates a connection to your server, sends some bytes to it, and prints out any bytes that it receives.
3. Define a simple chat protocol between the client and the server.  It should minimally allow a client to login with a username, logout, and send a message addressed to another user and allow the server to accept and reject logins and pass messages on to a client based on their username.
4. Make the server look for full commands from the client delimited by '\n'.  With sockets, there is no guarantee that a server will receive the full message and only the full message that was sent by a client.  One read of a socket may result in less than a full message or multiple messages together.  To properly implement this, you will need to buffer the data coming in on the socket and pull out a full message at a time.
5. Implement the chat protocol on the server side.  You can debug this with multiple concurrent telnet sessions each representing a client.
6. Implement the chat protocol on the client side.  You will need to buffer input here as well.

## More Ideas
* Add a broadcast capability
* Expand the protocol so that the server notifies clients when they log in of which other users are active and keeps them updated when new users login or existing users logout.
* Allow users to create, join and drop out of chat rooms.  All messages addressed to the chat are broadcast to everyone who has joined.
* Implement the IRC protocol and connect to your server using a standard IRC client.

## Helpful Resources
* Foundations of Network Programming in Python by Rhodes & Goerzen (The Hacker School library has this book)
* [Sockets Programming in Java](http://www.javaworld.com/article/2077322/core-java/sockets-programming-in-java-a-tutorial.html)
