## Your App and the REST of the World

<hr>

### Why do I need to know about the Internet?

<hr>

#### &hellip; because it is the Internet, duh.

<hr>

### But really

It's rare that an application built today does not use Internet
access. This is especially true of applications we build for someone
else.

<hr>

### Where we use the network

- Logging in to services
- Talking to middleware that we have built
- Talking to client backends
- Talking to 3rd-party sources

<hr>

### What is an Internet transaction?

It's complicated.

<hr>

### The 7-Layer OSI Model

1. Physical
2. Data Link
3. Network
4. Transport
5. Session
6. Presentation
7. Application

<hr>

### The 7-Layer OSI Model

1. DSL / ISDN / T-carrier / USB / Bluetooth
2. Ethernet / Wi-Fi / Serial / VLAN / MAC
3. IPv4 / IPv6 / ICMP / IPX / AppleTalk
4. TCP / UDP
5. SSH / NFS / RPC / SOCKS
6. TLS
7. HTTP / Everything else you've ever known

<hr>

Understanding the application layer and TLS are the primary if only
layers you should worry about as a Junior developer.

<hr>

### HTTP

- HTTP stands for Hyptertext Transport Transfer Protocol.
- HTTP was originally developed to exchange hypertext.
- Hypertext was originally data such as HTML.
- HTTP is now used to transfer most kinds of structured text.

<hr>

### TLS

- TLS stands for Transport Layer Security
- TLS and SSL are cryptographic protocols to protect layer 7 data
- TLS sends layer 7 data over the network on layer 4, to be
  reinterpreted as layer 7 data by the recipient.

<hr>

### Anatomy of an HTTP request

What happens when we send an HTTP (or other) application layer request?

<hr>

### SNACK

First, a *synchronize* signal is sent via the transport layer to the server.

<hr>

### SNACK

![synchronize](/images/http-syn.png)

<hr>

### SNACK

Next, a *synchronize and acknowledge* or *SNACK* response is returned
to the client to establish the connection.

<hr>

### SNACK

![snack](/images/http-snack.png)

<hr>

### SNACK

Last, an *acknowledge* is returned to the client to establish the
connection.

<hr>

### SNACK

![snack](/images/http-ack.png)

<hr>

### Are we HTTP yet?

At this point, the client sends the first signs of an HTTP
transmission. This is finally the actual HTTP request.

<hr>

### HTTP Requests

HTTP requests can

``` http
METHOD path
Host: www.whoarewetalkingto.com
Header1: first value
Header2: second value

body body body body rockin' everywhere.
```

<hr>

### HTTP Requests

``` http
GET /index.html
Host: www.detroitlabs.com
```

<hr>

### HTTP Responses

``` http
HTTP/1.1 200 OK
Date: Wed, 20 September 2017 22:38:34 GMT
Server: Apache/2.4.27 (Unix) (Red-Hat/Linux)
Last-Modified: Wed, 08 Jan 2017 23:11:55 GMT
Content-Type: text/html; charset=UTF-8
Content-Length: 138
Accept-Ranges: bytes
Connection: close

<html>
<head>
  <title>Detroit Labs</title>
```

<hr>

### HTTP Requests

``` http
POST /submit_expense
Host: coincraft.detroitlabs.com
Accept: */*
Accept-Encoding: gzip
Accept-Language: en
Connection: Keep-Alive
Content-Type: application/json
Content-Length: 43

{userid:3672,expensecategory:5,amount:20.15}

```

<hr>

### HTTP Responses

``` http
HTTP/1.1 200 OK
Date: Wed, 20 September 2017 22:38:34 GMT
Server: Apache/2.4.27 (Unix) (Red-Hat/Linux)
Last-Modified: Wed, 08 Jan 2017 23:11:55 GMT
Content-Type: application/text; charset=UTF-8
Content-Length: 2
Accept-Ranges: bytes
Connection: close

OK
```

<hr>


### What is an API?

<hr>

### API

API stands for Application Programming Interface.

An API defines an interface for communicating between clearly defined
software components. An API *abstracts* some underlying implementation
to expose only information or action that a developer will need,
simplifying programming.

<hr>

### APIs Old and New

Prior to the prevalence of always-on internet connections, an API
colloquially referred to interfaces to commonly installed libraries,
databases, or other pieces of programmable software.

<hr>

### APIs Old and New

In the modern day, it is much more common to hear the term API in
reference to a programmable network resource such as a microservice,
middleware, or other service which can have applications built on top
of it.

<hr>

### What is REST?

REST is an acronym for *REpresentational State Transfer*.

Fancy wording aside, REST is a convention that provides an abstraction
around network calls such that they act as traditional APIs.

<hr>

### What is REST?

- *REpresentational* - Your models
- *State* - and the state that they are in
- *Transfer* - are sent between server and client

<hr>

### What is REST?

There is no official standard for REST, but generally a REST service
is:

- Uniform
- Stateless
- Cache-able
- Client-Server
- Layered

<hr>

### Uniform

``` http
GET  /expenses
POST /expenses
GET  /expenses/53

GET  /users
POST /users
GET  /users/2

```


<hr>

### Stateless

Every request is a complete transaction. No request will require some
other request to be called first.

<hr>

### Cacheable

The service should dictate when its data is safe to cache if it is
unlikely to change or not to cache if the data changes often.

<hr>

### Client-server

The service is responsible for data storage and related logic. It is
not responsible for UI considerations.

The client is responsible for user interface and managing user session
data. It is not responsible for storing data.

<hr>

### Layered

A client should be unable to tell whether or not they are making
requests to a primary back end or some intermediary. Separate layers
may enforce security or handle load balancing, but should all act as
the same unit.

<hr>

### HTTP "verbs"

`POST` creates objects. It generally returns a status code of 201
along with a `Location` header containing a URL to retrieve the newly
created object, or 409 if there is a conflict with existing objects.

<hr>

### HTTP "verbs"

`GET` retrieves objects. This could be single, detailed records or
collections of summary models. It generally returns a status code of
200 with a successful response body, or 404 for non-existent objects.

<hr>

### HTTP "verbs"

`PUT` updates objects. It almost always only affects single records
and returns either 200 or 204 for successful updates or 405 for
invalid updates.

<hr>

### HTTP "verbs"

`DELETE` deletes objects. It generally returns status code 200 if the
object or objects are deleted, and a 404 if unable to delete.

<hr>

Congratulations
---------------

You now know enough about *REST* to trick someone into thinking
that you know what the heck you are talking about.

<!--  LocalWords:  REpresentational
 -->
