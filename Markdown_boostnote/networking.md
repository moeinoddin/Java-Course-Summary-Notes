---
title: "Networking"
tags: ""
---
network protocol

> defines rules and conventions which both sides need to  
> follow in order to be able to communicate with each other  
> specifying how data is packaged into sent and delivered messages  

network architecture

> a set of layers and protocols used to reduce   network design complexity  
> ex) TCP/IP: Transmission Control Protocol - Internet Protocol Suite  
>
> -   TCP is reliable: ensures it reaching its destination
>
> * * *

### TCP/IP Protocol Suite

each layer uses its underlying layer

-   Application: various application  
    -   FTP: File Transfer Protocol
    -   HTTP&#x3A; requests to web servers  
        . . .  
-   Transport: reliable end-to-end byte stream e.g) TCP
-   Network: unreliable end-to-end transmission of packets
-   Network interface: sending in raw bits and signals on cable

receiving application, obtains input when it is obtained completely and in order, checked with packet headers by TCP.  

**Connection**

> clients and servers communicate by sending streams of bytes over connections

**Socket**

> an endpoint of a connection between two processes  
> the interface between user and network  
>
> >  consists of an IP address and Port  
> > each socket pair has 4 tuples  
> > JAVA APIs

**Port**

> a host might have many open connections.  
> a port is a unique communication endpoint, a 16bit integer associated with a process. defines to who the connection is established
>
> > basically the IP is incomplete  
> > the name of the process on that side is also required

> \###.###.###.###: 80  
> well-known port for web servers  

> \###.###.###.###: 52462  
> ephemeral port allocated by Kernel

* * *

Client

> makes requests to server  

Server

> listens for requests from clients

Client: user code  
--------socket interface ( system calls )  
TCP/IP: Kernel code  
--------Hardware interface ( interrupts)  
Network adapter: hardware and firmware   

IP: 32bits used as address.  
DNS: a service which maps domain names to IP addresses

> someDomain.com : ###.###.###.###

* * *

* * *

JAVA TCP Sockets

-   Socket: on the client side

```java
import java.net.Socket

//create a socket
//and connects it to the specified port number on the named host
new Socket(String host, int port)

socket.'getInputStream' // input stream for data sent by server
socket.'getOutputStream'// output stream for sending data to server
socket.'getInetAddress' // read documentation
socket.'close()' //closing the socket
socket.'bind()' //connect to ServerSocket, usually called if an empty constructor was used for the object
```

-   ServerSocket: on the server side  
    waits for requests to come in over the network

```java
import java.net.ServerSocket

//create and define a port
new ServerSocket(int port)
'note': port numbers below 1024 are reserved

sSocket.'accept': // listens and accepts a sent request. this method blocks until a connection is made

sSocket.'getInetAddress'
sSocket.'getLocalPort' 
```

![](tcp.JPG)

* * *

sample Server socket code - single threaded

```java
try (ServerSocket welcomingSocket = new ServerSocket(5757)) {
	//Server started, Waiting for a client
	try (Socket connectionSocket = welcomingSocket.accept()) {
		//client accepted
		OutputStream out = connectionSocket.getOutputStream();
        InputStream in = connectionSocket.getInputStream();
        byte[] buffer = new byte[2048]; //used to store read bytes
        String[] messages = {"hi", "good!", "nothing much"};
		for (String msg: messages) {
        	int read = in.read(buffer);//read bytes into buffer
            String request = new String(buffer, 0, read)//translate buffer bytes to String
            out.write(msg.getBytes()); //send message to client
        }
	}catch (IOException ex) {
		System.err.println(ex);
	}
    // server closed through (try-with-resource)
} catch (IOException ex) {
	System.err.println(ex);
}
// server shut-down through (try-with-resource)
```

sample client code - single threaded

```java
try (Socket client = new Socket("127.0.0.1", 5757)) {//127.0.0.1 is localhost
	//Connected to server, if no exception is thron
    OutputStream out = client.getOutputStream();
    InputStream in = client.getInputStream();
    byte[] buffer = new byte[2048]; //used to store read bytes
    String[] messages = {"hi", "how are you?", "what'cha doing?"};
    for (String msg: messages) {
        out.write(msg.getBytes()); //send message to server
		int read = in.read(buffer);//read bytes into buffer
		String response = new String(buffer, 0, read)//translate buffer bytes to String
        
    }
} catch (IOException ex) {
    System.err.println(ex);
}
// closed through (try-with-resource)");
```

* * *

downloading a file from the web

-   getting default download folder

```java
String directory = System.getProperty("user.home") + File.separator + "Downloads" + File.separator;
// "user.home"		user folder
// File.seperator	seperator on this OS
```

-   downloading

```java
URL url;
HttpURLConnection connection; //eases our work

url.'getProtocol'; // "http" / "https" / ... / else unsupported
url.'openConnection';// open the connection
	
connection = (HttpURLConnection) url.'openConnection()';
connection = (HttpsURLConnection) url.'openConnection()';
System.err.println("UNSUPPORTED PROTOCOL!");

connection.'connect()'; //attempt to connect

connection.'getResponseCode';
// if a connection is established successfully, the response code will be 200,201,202,... .
// it is best to check for it. throw an error / return the method if connection failed
//done with code/100 != 2

connection.'getContentLengthLong()'; //the length of the response

connection.'getInputStream()'; //inputStream of data sent over this connection

download{
	int totalRead = 0;
	byte[] buffer = new byte[1000000];
	while (totalRead < contentLength) {
		int read = in.read(buffer); "important"
		if (read == -1) "note"
			break;
	out.write(buffer, 0, read);
	totalRead += read;
	//progress: totalRead / contentLength *100
}
```
