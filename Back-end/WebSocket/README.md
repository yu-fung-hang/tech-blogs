# WebSocket

## HTTP vs WebSocket
* In HTTP and REST, an application is modeled as many URLs. Servers route requests to the appropriate handler based on the HTTP URL, method, and headers.

* By contrast in WebSockets there is usually just one URL for the initial connect and subsequently all application messages flow on that same TCP connection.

## When to use

* The combination of low latency, high frequency and high volume make the best case for the use WebSocket.

## Why SockJS

* Restrictive proxies may preclude WebSocket interactions because:
    1. they are not configured to pass on the `Upgrade` header;
    2. they close long lived connections that appear idle.
    
* The solution to this problem is WebSocket emulation, i.e. attempting to use WebSocket first and then falling back on HTTP-based techniques that emulate a WebSocket interaction and expose the same application-level API.

* The goal of SockJS is to let applications use a WebSocket API but fall back to non-WebSocket alternatives when necessary at runtime, i.e. without the need to change application code.

## Stomp

The WebSocket protocol defines two types of messages, text and binary, but their content is undefined. The defines a mechanism for client and server to negotiate a sub-protocol?¡ª?i.e. a higher level messaging protocol, to use on top of WebSocket to define what kind of messages each can send, what is the format and content for each message, and so on. The use of a sub-protocol is optional but either way client and server will need to agree on some protocol that defines message content.

STOMP is a simple, text-oriented messaging protocol that was originally created for scripting languages such as Ruby, Python, and Perl to connect to enterprise message brokers. It is designed to address a minimal subset of commonly used messaging patterns. STOMP can be used over any reliable, 2-way streaming network protocol such as TCP and WebSocket. Although STOMP is a text-oriented protocol, message payloads can be either text or binary.

## Reference

https://docs.spring.io/spring-framework/docs/5.0.8.RELEASE/spring-framework-reference/web.html#websocket