---
title: "Authentication & Authorisation"
teaching: 15
exercises: 5
questions:
- "What is the difference between authentication and authorization?"
- "What are API keys?"
- "How do we obtain an PAI key?"
objectives:
- "Understand the purpose of authentication and authorisation."
- "Understand the different methods of authentication."
- "Be able to obtain and use an API key to access data."
keypoints:
- "Authentication ensures that only authorised entities can access the API."
- "Authorisation ensures they can only access what they're permitted to."
---
cite:
- Lesson adapted from *Ed Bennett, Michele Mesiti, Colin Sauzé, "Introduction to the Web and Online APIs"*

## Authentication: "Proving Who You Are"
Authentication is the process of verifying who a user is. When you log into an email account, you enter your username and password. The email service checks these credentials to ensure it's really you.

## Authorisation: "Establishing What You Can Do"
Authorisation is the process of verifying what specific applications, files, and data a user has access to.
Example: Once you're logged into a website, it may check if you have the right to access its admin panel. Even though you're authenticated, you might not be authorised to see certain parts of the website if you don't have the necessary permissions.

Security is crucial. These concepts ensure that only authorized entities can access the API, and they can only access what they're permitted to.

## Different methods of Authentication & Authorisation
Basic Authentication: Username and Password mechanism.
API Keys: Tokens to identify and validate the user/application.
OAuth: A standard protocol for token-based authentication and authorization.

## URLs

A URL (also sometimes known as a URI or Uniform Resource Indicator) consists of two or three parts: the protocol followed by ://, the server name or IP address and optionally the path to the resource we wish to access. For example the URL http://carpentries.org means we want to access the default location on the server carpentries.org using the HTTP protocol. The URL https://carpentries.org/contact/ means we want to access the contact location on the carpentries.org server using the secure HTTPS protocol.

## Requests and responses

The two main objects in HTTP are the _request_ and the _response_. Each HTTP connection is initiated by sending a request, and is replied to with a response. Both the request and response have a _header_, that defines metadata about what is requested and what is included in the response, and both can also have a _body_, containing data. To look at these in more detail, we can use the `curl` command. Specifically, to see the request headers, we can use `curl -v` followed by the URL we wish to request.

~~~
$ curl -v http://carpentries.org
~~~
{: .language-bash}

~~~
*   Trying 13.32.168.28...
* TCP_NODELAY set
* Connected to carpentries.org (13.32.168.28) port 80 (#0)
> GET / HTTP/1.1
> Host: carpentries.org
> User-Agent: curl/7.64.1
> Accept: */*
>
< HTTP/1.1 301 Moved Permanently
< Server: CloudFront
< Date: Sat, 13 Mar 2021 01:10:22 GMT
< Content-Type: text/html
< Content-Length: 183
< Connection: keep-alive
< Location: https://carpentries.org/
< X-Cache: Redirect from cloudfront
< Via: 1.1 f25763791d7f1173b560742bb9507145.cloudfront.net (CloudFront)
< X-Amz-Cf-Pop: LHR62-C5
< X-Amz-Cf-Id: JJLCGx6qUOpaid_ArD0kph8QddidHgWnKoi72yNn0Jazmla8H5mUGg==
<
<html>
<head><title>301 Moved Permanently</title></head>
<body bgcolor="white">
<center><h1>301 Moved Permanently</h1></center>
<hr><center>CloudFront</center>
</body>
</html>
* Connection #0 to host carpentries.org left intact
* Closing connection 0
~~~
{: .output}

Lines starting `> ` here are request headers, and lines starting `< ` are response headers. Following this is the body (the section from `<html>` to `</html>`), which in this case is a short web page.

In this case, after identifying what type of request this is (a `GET` request), the location to look for (`/`), and the HTTP version, we include three headers: the first states the domain name we are looking to contact (in case one server is serving multiple domain names, as is quite common), the second identifies what software we're using to connect (as some servers will adjust the content depending on, for example, which browser you connect with), and the third tells the server what we're looking for&mdash;in this case we will accept whatever the server has to offer.

The server then responds with a status code, followed by a lot of metadata. In this case, the status code `301` indicates that the site is no longer at the location we tried, so the metadata includes where to look instead. This is followed by a short web page explaining the same thing. Most browsers will see the `301` and automatically redirect to the correct location so you never see this error message.

Let's see what happens when we follow the redirect. Web pages can be quite long, so for now let's ignore the body and look only at the headers.

~~~
$ curl -v https://carpentries.org > /dev/null
~~~
{: .language-bash}

In this case, because we're connecting via HTTPS, `curl` gives a lot more debugging information about the secure connection, but after this we see similar request headers (although this time we're using HTTP/2), and then the response headers start with `HTTP/2 200`, with the status code `200` indicating that this was a successful request, with the body providing what we asked for.

HTTP status codes are three digits long, and almost always begin with 2, 3, 4, or 5. Status codes beginning `2xx` indicate that the request was successfully received, understood, and accepted; `3xx` indicates a redirect of some kind; `4xx` indicates an error caused by the client (for example the famous `404 Not found` where the client has requested a resource that does not exist on the server), and `5xx` indicates an error on the server side.

It's rarely necessary to inspect the request, so if you're interested in the headers, it's more convenient to use `curl -I` to just show the response headers.

~~~
$ curl -I https://carpentries.org
~~~
{: .language-bash}

~~~
HTTP/2 200
content-type: text/html
content-length: 55036
date: Sat, 13 Mar 2021 01:32:50 GMT
last-modified: Sat, 13 Mar 2021 01:26:59 GMT
etag: "f16c8eaddc88e035134aa23e0f8a94ba"
server: AmazonS3
x-cache: Hit from cloudfront
via: 1.1 a25f829e86f504a329e71fa3f4d21485.cloudfront.net (CloudFront)
x-amz-cf-pop: LHR62-C5
x-amz-cf-id: WGyZEdVLxTFbdQ3eKX2rdnPWO0214DDcQi8TA5UpObYt2CgHjCUz7g==
age: 87
~~~
{: .output}

Noteworthy here is the first header `content-type: text/html`; this indicates that the response body is an HTML document (also known as a web page). HTML, the HyperText Markup Language, is the language that all web pages are written in; while we won't write any today, we will look a little more at how to read it (and get your code to read it) in a later episode.

> ## HyperText?
>
> Both HTTP and HTML refer to HyperText. This was a popular buzzword in the 1990s, and refers to the Web's ability to include not only text, but also cross-references in the form of links (_hypertext links_, or _hyperlinks_) to other documents stored elsewhere, which the user can immediately access.
>
> While this seems entirely obvious and second-nature today, it was revolutionary when it was first introduced, hence the name appearing prominently in technologies that supported it.
{: .callout}

> ## Another website
>
> Pick a web page you've visited recently and take a look at its response headers with `curl -I`. How do they differ from the `https://carpentries.org/` headers we looked at above? What parts are similar?
{: .challenge}

{% include links.md %}

[protocol-list]: https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers