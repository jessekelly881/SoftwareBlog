---
title: Playing with redux. A gentle introduction
layout: posts/default
copyright_year: 2019
tags: [react, redux]
---

I have been learning redux recently. Which means that I have been doing a lot of playing around with it. Throughout my adventures with redux I have learned a few things that I would like to share.

## What is redux.

But, before we dive into to any definitions or code lets talk about what redux is. A quick google(or duckduckgo) search brings us to the redux.js.org website. The official home of redux. Redux describes itself as

> A Predictable State Container for JS Apps

Basically, redux is way to handle global variables(or state) in javascript. If you have any background in computer science you might be thinking:

> Global state? Isn't that a bad idea.

And in general you would be right. But global state is very convenient in most cases
and I am sure I'm not the only one who has been tempted to use global state in my projects.

## Redux makes global state safe.

Redux lets you have your cake and eat it too. Redux allows you to use global state in your project. But it makes you do so in a safe way.
