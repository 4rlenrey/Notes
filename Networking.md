# Networking and stuff

<!-- TOC -->

- [Networking and stuff](#networking-and-stuff)
	- [World Wide Web](#world-wide-web)
		- [HTTP](#http)
			- [Requests](#requests)
			- [HTTPS](#https)
		- [HTML](#html)
		- [URL](#url)
	- [IETF](#ietf)
		- [Robots exclusion standard](#robots-exclusion-standard)
	- [OSI model](#osi-model)

<!-- /TOC -->

## World Wide Web
---

The web is not internet. Internet is a network of connected computers. World wide web is a system of public webpages accessible **through** the internet.

It has these three technologies:

### HTTP

(Hypertext Transfer Protocol) It's a network protocol for transferring hypermedia documents over the web.


#### Requests 

When you want to access some data through a server you make a HTTP request.
It's similar to just saying `Hey! Can you please send me this pdf document?` to your friend.

Your browser makes a request every time you visit any webpage.


Example request:
```
GET / HTTP/1.1
Host: google.com
Accept-Language: pl

```

This request is 


#### HTTPS

Https is an encrypted version of http. So if anyone in the caffee will try to steal your passwords by looking at what is going through the router then he cannot get those information because it's encrypted.

So when you visit `https://www.google.com/` this `https` is saying that your browser expects encrypted data and it demands it.

### HTML 

(Hypertext Markup Language) This is a markup language that is interpreted by the browser in a way that you do not need to read any code but you can see pretty pages.

This is a simple example of html:
```html
<h1>This is a big header</h1>
<div>This is some content in a div</div>
```
Browser will get rid of those `<h1>` and `<div>` tags and display it in a specified way (for example: text in this header tags will be bigger and most likely bolder).

### URL 

(uniform resource location)

## IETF

Internet Engineering Task Force is an organization that creates Internet standards. You do not have to use them but yeah, it's there.

### Robots exclusion standard

Proposed to add to IETF by google.

It basically comes down to creating a simple robots.txt file to specify which directories and which files are search engines/crawlers/other web robots allowed to use.

This is how it might look `https://www.example.com/robots.txt` in the url.
And this is how this file might contain:
```
Allow: /some/directory
Disallow: another/directory
```

## OSI model
---

Content here

robots.txt


