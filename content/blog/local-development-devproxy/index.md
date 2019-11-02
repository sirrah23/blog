---
title: "Proxy API requests in local development"
description: ""
date: "2019-11-01T23:50:21.184983"
---
When building a web application these days there's a general pattern of
separating it into:

* A front-end server which serves your application
* A back-end server which serves your API (REST, or something else)

Let's say that your developing an application locally with your servers
listening on the following hosts:
* Front-end -> `http://localhost:3000`
* Back-end -> `http://localhost:4000`

From your internet browser you'll navigate to `http:localhost:3000` so that you
can access and interact with your application. However, if your application
tries to reach out to the back-end server API, you'll probably see an error
message that looks something like:

```
No 'Access-Control-Allow-Origin' header is present on the requested resource. 
Origin 'http://localhost:3000' is therefore not allowed access.
```

This is because `http://localhost:3000` and `http:localhost:4000` are considered
different hosts due to their differing port numbers. Your browser, for security
reasons, is preventing the application that you're looking at (served via your
front-end server) from reaching out to, from its perspective, some unknown and
potentially hostile server on the internet (served via your back-end server).

If you do some digging you'll find that you can solve the problem by:
1. Adding the `Access-Control-Allow-Origin: *` header to the http requests made
   from your front-end server
2. Importing a library and using it to scaffold basic CORS on your back-end
   server

But wait! Since this is in local development, there's a better way to solve the
problem. You can have your front-end server proxy API requests to your back-end
server.

The idea behind proxying here is that your browser will only ever reach out to
`http://localhost:3000`. However, you can then have your front-end server pass
API requests through to `http://localhost:4000` and return whatever the back-end
server responds with to the application running in your browser. This way
your browser will never know that another server even exists. It'll have nothing
to complain about.

Modern web frameworks all have different ways of setting up this kind of
proxying. For example, if you're using [Vue.js](https://vuejs.org/), then you
can add [this](https://cli.vuejs.org/config/#devserver-proxy) option to your
`vue.config.js` file, and you're good to go!

I highly recommend this approach as it's much easier than fiddling with CORS,
especially if it won't even be an issue for you in production.
