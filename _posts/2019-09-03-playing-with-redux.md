---
title: Playing with redux. A gentle introduction
layout: posts/default
copyright_year: 2019
tags: [redux, js]
---

I have been learning [redux](https://amzn.to/2LuYILn){:target="_blank"} recently. Which means that I have been doing a lot of playing around with it. Throughout my adventures with redux I have learned a few things that I would like to share.

## What is redux?

But, before we dive into to any definitions or code lets talk about what redux is. A quick google(or duckduckgo) search brings us to the redux.js.org website. The official home of redux. Redux describes itself as

> A Predictable State Container for JS Apps

Basically, redux is way to handle global variables(or state) in javascript. If you have any background in computer science you might be thinking:

> Global state? Isn't that a bad idea.

And in general you would be right. But global state is very convenient in most cases
and I am sure I'm not the only one who has been tempted to use global state in my projects.

## Redux makes global state safe.

Redux lets you have your cake and eat it too. Redux allows you to use global state in your project. But it makes you do so in a safe way.

## Installing redux.
Before we jump into any code we need to start a project and install redux.

**Side note:** this project assumes that you are using linux(or possibly mac) because, well, this is what I'm using and I can't be bothered to install windows just to try this. If you aren't using linux I highly recommend you check it out. Its fantastic!

Lets start by creating a node project.

```bash
mkdir ReduxTest
cd ReduxTest
npm init -y
```

And now lets install redux. We will also be installing pracel. It's not strictly necesssary, but it makes things easier.

```bash
npm install --save redux
npm install -g parcel
```
**Side note:** we are installing parcel globally here. You might need to do this with using sudo. Or you could install parcel to the project only but you would have to access it through an npm script.

## Setting up redux.
**Btw:** Because this is an introduction and I don't want to confuse you, we are going to use redux without react, or any other framework. Although redux was origionally built with react in mind they are independent and can be used seperately.

Now that we have redux installed in our project lets setup up some basic boilerplate code. Lets create a folder named app and two files, index.html and index.js.


```bash
mkdir app
cd app
touch index.html
touch index.js
```
Open up the index.html file in your text viewer of choice. I prefer [emacs](https://amzn.to/2MV29xN){:target="_blank"} but, really, it doesn't matter.

In our index.html we are only going to add one line of html.

```html
<script type="text/javascript" src="index.js"></script>
```

The rest of our codeing will take place in the index.js file.
