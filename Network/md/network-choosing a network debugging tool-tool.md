

- Network
-  Choosing a Network Debugging Tool 

Article

# Choosing a Network Debugging Tool

Decide which tool works best for your network debugging problem.

## Overview

Debugging network problems is challenging because of the fundamental nature of networking. Networking is asynchronous, time-sensitive, and error prone. Moreover, the two programs involved (for example, the client and the server) are often created by different developers, who disagree on the exact format of the data being exchanged. Fortunately, a variety of tools can help you debug such problems.

A key goal of these tools is to divide the problem in two. For example, if you’re working on a network client that sends a request to a server and then gets an error back from that server, it’s important to know whether things failed because the request was incorrect (a problem with your client) or because the server is misbehaving. You can use these network debugging tools to view the traffic going over the network, and thus independently check the validity of that traffic.

The best tool to use depends on the APIs you’re using and the type of problems you’ve encountered:

- If you’re working at the HTTP level, you may find that your request makes it to the server and then the server sends you a response indicating that it failed in some way (for example, you get an HTTP response with a status code of *500 Internal Server Error*). See Debugging HTTP Server-Side Errors and Analyzing HTTP traffic with Instruments.

- If you’re using URLSession, or one of the subsystems that uses URLSession internally, you can enable CFNetwork diagnostic logging to get a detailed view of how your requests were processed. See Debugging HTTPS Problems with CFNetwork Diagnostic Logging.

- If you want a low-level view of the traffic exchanged over the network, you need a packet trace. See Recording a Packet Trace.

- If you’re working in Safari or one of the various web views (like WKWebView), you can use the Web Inspector to view the network requests issued by the page. See Web Development Tools.

- Some of the most popular network debugging tools, like HTTP debugging proxies, are third-party products. See Taking Advantage of Third-Party Network Debugging Tools.

## See Also

### Network Debugging

Debugging HTTP Server-Side Errors

Understand HTTP server-side errors and how to debug them.

Debugging HTTPS Problems with CFNetwork Diagnostic Logging

Use CFNetwork diagnostic logging to investigate HTTP and HTTPS problems.

Recording a Packet Trace

Learn how to record a low-level trace of network traffic.

Taking Advantage of Third-Party Network Debugging Tools

Learn about the available third-party network debugging tools.

Testing and Debugging L4S in Your App

Learn how to verify your app on an L4S-capable host and network to improve your app’s responsiveness.

