Reference link:

```
https://raygun.com/blog/soap-vs-rest-vs-json/
```

## 1. SAOP  VS REST  VS   JSON

SAOP and REST makes it possible to transfer data from an application to other applications

JSON is a data format just like xml or plain txt  eg.



## 2. The main differences between SOAP and REST

*REST was created to address the problems of SOAP.*



SOAP stands for Simple Object Access `Protocol` 

REST stands for Representational State Transfer 

It’s an `architectural style` that defines a set of recommendations for designing loosely coupled applications that use the HTTP protocol for data transmission. REST doesn’t prescribe how to implement the principles at a lower level.



## 3. Protocol  architectural style difference

A *protocol* usually describes the exact messages (or parts thereof) the two (or more) peers have to exchange. Specifying also the choreography how these messages are exchanged and what they mean.

An *architectural style* (like REST) does not describe messages at all, but specifies *requirements* (architectural constraints) that the messages, choreography or parts of the system have to fulfill.

So while a *protocol* might say: "use JSON in the following format to request a quote". An architectural style just says: "clients can contact servers, but not the other way". It's a completely different level.

Here is how they are related: An architectural style is like a template for a specific architecture. A specific architecture in turn defines the protocols between components.



## 4. Details

#### To create a REST API, you need to follow six architectural constraints:

1. **Uniform interface** – Requests from different clients should look the same, for example, the same resource shouldn’t have more than one URI.
2. **Client-server separation** – The client and the server should act independently. They should interact with each other only through requests and responses.
3. **Statelessness** – There shouldn’t be any server-side sessions. Each request should contain all the information the server needs to know.
4. **Cacheable resources** – Server responses should contain information about whether the data they send is cacheable or not. Cacheable resources should arrive with a version number so that the client can avoid requesting the same data more than once.
5. **Layered system** – There might be several layers of servers between the client and the server that returns the response. This shouldn’t affect either the request or the response.
6. **Code on demand [optional]** – When it’s necessary, the response can contain executable code (e.g., JavaScript within an HTML response) that the client can execute.

