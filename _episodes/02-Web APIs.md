---
title: "Web APIs?"
teaching: 15
exercises: 5
questions:
- "What are the core components of a Web API?"
- "Why does security become necessary for Web APIS?"
objectives:
- "Understand the need for an API."
- "Understand the main components of an API."
- "Familiarity using Library APIs."
keypoints:
- "An API is a way for two or more computer programs or components to communicate with each other."
- "HTTP is the protocol originally designed for requesting and receiving Web pages, but now also used as the basis for a variety of APIs. HTTPS is the encrypted version of HTTP."
- "Every page on the world wide web is identified with a URL or Uniform Resource Locator."
- "A request is how you tell a server what you want to see. A response will either give you what you asked for, or tell you why the server can't do that. Both requests and responses have a header, and optionally a body."
- "We can make requests and receive responses, as well as see their headers, using `curl`."
---

As described previously, Web APIs enable communication between different software systems over the web. Typically, a _request_ is made by a client, which could be an application on your local laptop, to the API server that understands and processes the _request_ and retrieves the data requested and sends it back as a _response_ to the client.

## How APIs work

![How APIs work in realtion to a web-server](../assets/img/APIServer.png)

This process is governed by a set of predefined rules and protocols that ensure seamless communication, regardless of the diversity in programming languages and hardware platforms involved. The cornerstone protocol in Web API interactions is HTTP (Hypertext Transfer Protocol), which outlines how messages are formatted and transmitted over the web, and how web servers and browsers should respond to various commands.

## World Wide Web, URLs and HTTP
To make effective use of web APIs, we need to understand a little more about how the Web works than a typical Web user might. This lesson will focus on _clients_&mdash;computers and software applications that make requests to other computers or applications, and receive information in response. Computers and applications that respond to such requests are referred to as _servers_.

## World Wide Web
At its core, the initial World Wide Web concept brought together three key ideas:

1. The use of HTML (Hypertext Markup Language) documents which could contain hyperlinks to other documents (or different parts of the same document). These could reference documents located on any web server in the world.
2. That every file on the world wide web would have a unique URL (Uniform Resource Locator).
3. The Hypertext Transfer Protocol (HTTP) that is used to transfer data from the web server to the requesting client.

## Protocols, HTTP & HTTPS

You may (or may not) have wondered how it is that different web browsers, written independently by different companies and running on different operating systems, are able to talk to the same web servers using the same addresses, and get the same web pages back. This is because all web browsers implement the _HyperText Transfer Protocol_, or HTTP.

A protocol is nothing more than a system of rules that allow for communication between computers (or other devices). Much like a (human) language, it defines rules and syntax that when all parties follow, allow information to be transmitted from one device to another.

HTTPS is a protocol closely related to HTTP; it follows many of the same conventions as HTTP, particularly in the way client and server code is written, but includes additional encryption to ensure that untrusted third parties can't read or modify data in transit.

>## Requests and responses
>
>The two main objects in HTTP are the _request_ and the _response_. Each HTTP connection is initiated by sending a request, and is replied to with a response. Both the request and response have a _header_, that defines metadata about what is requested and what is included in the response, and both can also have a _body_, containing data.

## URLs

A URL (also sometimes known as a URI or Uniform Resource Indicator) consists of two or three parts: the protocol followed by ://, the server name or IP address and optionally the path to the resource we wish to access. For example the URL http://carpentries.org means we want to access the default location on the server carpentries.org using the HTTP protocol. The URL https://carpentries.org/contact/ means we want to access the contact location on the carpentries.org server using the secure HTTPS protocol.