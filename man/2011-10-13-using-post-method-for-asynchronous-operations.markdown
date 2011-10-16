---
layout: post
title: "Using POST Method for Asynchronous Operations"
date: 2011-10-13 15:14
comments: true
categories: REST 
published: false
---
HTTP is a synchronous and stateless protocol. In other words when a client sends a request to a server
it will expect an answer. However, nobody says here that the server had to finish the task in hands before
send a response back to the client.
As a consequence of this, a particular task will be designed to have one of the following status associated:

- PENDING  [code:200] => Task submitted is found still processing.
- OK [code:303] => Task submitted has finished successfully, resource can be found in URI stated in *Location* header.
- FAILED [code:200] => Task submitted has finished with errors.

## Examples

### Client Request submiting a task to the server
{% codeblock Request %}
POST /images/tasks HTTP/1.1
Host: www.example.org
Content-Type: multipart/related; boundary=xyz

--xyz
Content-Type: application/xml;charset=UTF-8
 (some information about the task to be executed by the server)

--xyz
Content-Type: image/png
 (Lets assume that the task requires an image, for example, server needs to process this image)

--xyz--
{% endcodeblock %}

### Server responding upon receipt of client's request
{% codeblock Response %}
HTTP/1.1 202 Accepted
Content-Type: application/xml;charset=UTF-8
Content-Location: http://www.example.org/images/task/1
Date: 

<status xmlns:atom="http://www.w3.org/2005/Atom">
  <state>pending</state>
  <atom:link rel="self" href="http://www.example.org/images/task/1">
  <message>Request is still being processed.</message>
  <ping-after>2011-12-12T02:33:33Z</ping-after> # A hint of when the task will be finished
</status>
{% endcodeblock %}

### Client sending a GET request to this task and Server responding that task has finished successfully
{% codeblock Client --> Server %}
GET /images/task/1 HTTP/1.1
Host: www.example.org
{% endcodeblock %}

{% codeblock Server --> Client %}
HTTP/1.1 303 See Other
Content-Type: application/xml;charset=UTF-8
Content-Location: http://www.example.org/images/task/1

<status xmlns:atom="http://www.w3.org/2005/Atom">
  <state>OK</state>
  <atom:link rel="self" href="http://www.example.org/images/task/1">
  <message>Your request has been processed successfully.</message>
</status>
{% endcodeblock %}

### Client sending a GET request to this task and Server responds informing errors occurred while processing.
{% codeblock Client --> Server %}
GET /images/task/1 HTTP/1.1
Host: www.example.org
{% endcodeblock %}

{% codeblock Server --> Client %}
HTTP/1.1 200 OK 
Content-Type: application/xml;charset=UTF-8
Content-Location: http://www.example.org/images/task/1

<status xmlns:atom="http://www.w3.org/2005/Atom">
  <state>FAILED</state>
  <atom:link rel="self" href="http://www.example.org/images/task/1">
  <message>Failed to complete your request.</message>
  <detail>Invalid image format.</detail>
  <completed>2011-12-12T02:02:02Z</completed>
</status>
{% endcodeblock %}

## REFERENCES
Allamaraju, Subbu "RESTful Web Services Cookbook" O'Reilly 2010.


