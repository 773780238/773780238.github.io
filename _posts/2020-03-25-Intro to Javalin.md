---
layout:     post
title:      Intro to Javalin
subtitle:   Java magazine May/June 2019
date:       2020-03-25
author:     Zihui Liu
header-img: img/java_jfma19_cover.jpg
catalog: true
tags:
    - Java Magazine
    - Javalin
    - Web Framework
---

# Javalin:A Simple, Modern Web Server Framework

## Drawback
Javalin is a lightweight framework, so it only takes charge of backend part of web application. That is to say, Javalin users have to deal with the problem of database setup, dependency injection command-line parsing and so on.

## Features
handler group
Javalin use handler group to manage route(CRUD API) in a block scope like:
<pre><code>
    app.routes{
        path("users"){
            get(...)
            post(...)
            path(":user-id"){
                get(...)
                post(...)
            }
        }
    }
</code></pre>

Asynchronous response
If <span style="color: blue">Context </span> is set to be a <span style="color: blue"> CompletableFuture  </span>, then Javalin will remove the request from the thread pool and finish it asynchronously.
<pre><code>
    app.get("/", ctx -> {
        var futureResult = connection.sendPreparedStatement("select 0").thenApply(...);
        ctx.result(futureResult);
    });
</code></pre>
