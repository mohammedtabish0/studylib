Basics 
===

[![hackmd-github-sync-badge](https://hackmd.io/bHnQdqGQQE2o9GKS4CtzpQ/badge)](https://hackmd.io/bHnQdqGQQE2o9GKS4CtzpQ)


# StateLess vs Stateful Protocol

The state of an application whether it is stateless or stateful depends on how the state of interaction with the application is managed/stored.

## StateLess
In stateless applications no reference to the past transactions is stored.Each request/transaction is completely isolated.
It does not save or reference information about previous operations. Every time it carries each operation from the scratch just like the first time. *No session info is stored in the application Memory but is rather stored in Database*. These apps are highly scalable(horizontal) as API requests can be forwared to any servers running behind a load balancer without knowing the state of the session.

**REST** is a stateless architecture in itself,but it doesn't means all REST applications are stateless.If application stores the state in session then it is stateful.

Server Processes each request on the basis of information passed to that request i.e requests are self contained and does not rely on previous requests.

When the server requests a list of recent messages using the Facebook API, it issues a GET request with token and date. The response is independent of any server state, and everything is stored on the client’s machine in the form of a cache.

There is no relationship with the previous, current & next request. In Stateless, the client does not wait for synchronization from the server. There is no process completion concept in serverless architecture so it’s faster.

Stateless Architecture means the app is dependent only on Third-party storage because it doesn’t store any kind of state in memory or on its disk. All data it needs or requires has to fetch from some other stateful service (Database) or are present in the CRUD request.

The stateless design simplifies the server design because there is no need to dynamically allocate storage to deal with conversations in progress. If a client session dies in mid-transaction, no part of the system needs to be responsible for cleaning up the present state of the server. A disadvantage of statelessness is that it may be necessary to include additional information in every request, and this extra information will need to be interpreted by the server.

Session state is therefore kept entirely on the client. client is responsible for storing and handling all application state-related information on client side and sending this information to the server whenever it is needed.

Server and client are loosely coupled and can act independently

**Examples:**
IP,HTTP,CDN,DNS,REST,SOAP

## Stateful

Stateful applications maintains the state in session and uses the information stored from earlier requests. Because of this reason these applications scales very poorly.

Server and client are tightly bound.

A failed server cannot be restarted easily after crash as all the information of session are required.

A stateless protocol can be forced to behave as if it were stateful. This can be accomplished if the server sends the state to the client, and if the client to sends it back again to the server, every time. Like HTTP is stateless but we make HTTP as stateful protocol using jsonWebToken(JWT) i.e.first server send the JWT to client and the on each request going to server client will send this token. *"JWT itself is again stateless which we will discuss in another discussion"*

**Examples:** TCP,FTP,WebSockets,SMTP,All databases

==A TCP connection-oriented session is a stateful connection because both systems maintain information about the session itself during its life.==


# REST API vs SOAP API

**SOAP – Simple Object Access Protocol**

**REST – REpresentational State Transfer**

While SOAP and REST share similarities over the HTTP protocol, SOAP is a more rigid set of messaging patterns than REST. The rules in SOAP are important because we can’t achieve any level of standardization without them. REST as an architecture style does not require processing and is naturally more flexible. 

SOAP relies exclusively on XML to provide messaging services.
The XML used to make requests and receive responses in SOAP can become extremely complex.

One of the most important SOAP features is built-in error handling. If there’s a problem with your request, the response contains error information that you can use to fix the problem.


REST provides a lighter-weight alternative.Instead of using XML to make a request, REST (usually) relies on a simple URL. In some situations you must provide additional information, but most web services using REST rely exclusively on using the URL approach. REST can use four different HTTP methods (GET, POST, PUT, and DELETE) to perform tasks.

REST supports XML,JSON,CSV,RSS,YML,plain-text,etc and doesn't rely exclusively on XML.


While REST uses only HTTP,SOAP is actually agnostic of the underlying transport protocol and can be sent over almost any protocol such as HTTP, SMTP, TCP.

SOAP API include higher levels of security (e.g., a mobile application interfacing with a bank), messaging apps that need reliable communication, or ACID compliance.ACID compliance reduces anomalies and protects the integrity of a database by prescribing exactly how transactions can interact with the database.

SOAP APIs are stateless by default,when we fire a web service call with soap we create a SOAP envelop in xml and send it on a http channel, that is stateless by default.
Although SOAP does support stateful operations.


:::info
Statelessness in REST API means that every HTTP request happens in complete isolation. When the client makes an HTTP request, it includes all information necessary for the server to fulfill that request. The server never relies on information from previous requests. If that information was important, the client would have sent it again in this request.
:::
