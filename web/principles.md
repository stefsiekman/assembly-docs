# Principles of a web application

This document explains some of the basic concepts of a web-based application.
Please be aware that this is just a brief overview of how web application work,
I'm simplifying a lot here.

In this example we'll be making a expense tracker. The name of this application
will be 'Cash Stream' and it is hosted at `cashstream.io`.

## The client

Normally an application is written in some language and run a normal operating
system. Web applications don't differ much, but they're one level up. The
entire application is run in a browser, any browser to be more precise.

This is exactly the benefit of these web applications: they're cross-platform,
as any device running a browser can run your application. This does, of course,
come with some downsides. The application has to be written using mainly web
technologies. That means lots of HTML, JavaScript and CSS.

These HTML, JS and CSS files together will form the client of your application.
Be aware that I'm referring to a client here as well as an application. To be
more strict, the browser can be seen as a client. Let's first explain this term
a bit more.

### Client?

With __client__ I'm referring to a specific instance of the application. Since
we're aiming to distribute our application to many people (otherwise you
definitely shouldn't be writing a web application), there will be instances of
your application running all over the world.

These instances will communicate with some central (let's stick to central for
now) server. This server will at least serve the HTML, JS and CSS files, but as
we'll see later, does a lot of other stuff to. In the context the browser, or
more specifically the application instance running in someone's browser, is
what I'll call a client.

### Client file structure

But what will this _infamous_ client look like then? Well, as I said earlier,
the client is basically a collection of HTML, JS and CSS files that are
delivered to a user's browser. In general the file structure will look
something like this:

```
./
../
css/        (styling files)
img/        (images)
js/         (JS logic)
index.html  (start of the application, maybe more .html files)
```

Usually all of these files are hosted right at the root of the server. By that
I mean that accessing `cashstream.io/index.html` in the browser will result in
the user getting the contents of our main page. The benefit of this is that
users only have to type the base URL of your application to open it.

It is worth emphasising that all of the above files should _absolutely_ be
static. With that I mean: each of the files is the same for each user. We're
not trying to write some 1998 PHP application here. The idea behind this is that
the files that describe to the browser how the application work can be cached.
Caching is something I won't cover here, but trust me: caching = good.

### Programming the client

This is a subject I won't go into much here. All I want to say about it is that
you should write your application with the following in mind: the data will be
loaded later. We'll do this using Ajax in fact, that is, by making separate
HTTP requests _after_ your application has already loaded. How this will work,
I will cover.

## Managing data: the API

But first, where will the data come from? Well the answer to that is three magic
letters: API. (Yes, there are three _separate_ letters, it's not 'aapie'...)
This is what will manage all of the data for the application, as well as more
intricate processing that should be done server-side.

The type of API that we'll use for Cash Stream is a REST(ful) API. There's a lot
of things that I'm just blatantly skipping here, but the general gist of it is
quite important to understand. The idea of a REST API is that each _resource_ is
_state-less_. I realise those are two scary words, but not to worry!

### API location

Before I continue to those scary words, let's first explain some more API
basics. The API is often hosted at a specific URL. The most common option is to
go for a separate domain, like `api.cashstream.io`. If that's too much of a
hassle to set up, use a reserved path to the API, like `cashstream.io/api/`.
If you go for this approach, make sure not to create a folder called `api` in
the folder of your application!

### Resources

The API is basically a dynamic file structure on the server. Going through the
different data is kind of like browsing through regular files on a server. The
following URL would for example point to the data of user #425:
`api.cashstream.io/users/425`. If you go to `api.cashstream.io/users` you get a
list of all the users in the database.

Essentially each resource has a _path_ or URL associated with it by which it
can be located. On these URLs different actions can be performed using HTTP
requests. How this works exactly, I will cover lateron.

### State-less

This word is not a scary as it seems. All this means is that any given resource
should always result in the same data for anyone. This means that
`api.cashstream.io/users/425` should always give the same information about user
nr. 425. Granted, this data might change, but never depending on who is
accessing it, or on what time, from what location etc.

As you can imagine, this can cause some issues with the idea of authentication.
Authentication is a giant beast of it's own, that I won't go into much yet. In
short, APIs get around this issue in a sneaky way. Each request for data
(manipulation) is accompanied by an access token. So with the same access token,
a resource will always produce the same result.

## Exchanging data: HTTP

_To be written_
