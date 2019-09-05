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

In our index.html we will add the following code:

```html
<html>
<body>
  <script src="./index.js">
  </script>
</body>
</html>
```

The rest of our codeing will take place in the index.js file.

### Import redux

Lets get started by importing redux into our js file.

**Btw,** we are able to import redux this way because we are using parcel. You could also use webpack but it requires more setup.

```javascript
import { createStore } from 'redux'
```

### Test that everything is working

Now that we have imported redux lets make sure that everything is working as it should. Run

```bash
parcel app/index.html
```

and point your browser to localhost:4000. You should see a blank page. How exciting! Well, we haven't actually done anything yet. What did you expect?

Now that we have imported redux into our project lets talk a little bit about how redux works.

### Reducer

In order to get started with redux we need to create a _reducer_. You are probably asking: what is a reducer?

> A reducer is just a function

A reducer is just a function that takes 2 arguments. The first is the state(this is just the global variable that we talked about earlier) and the second is called the action(we will talk about this later).

**Btw,** a reducer is named after the Javascript function Array.prototype.reduce() and works similarly.

So, lets write our reducer.

```javascript
const INC = "INC"

function counter(store=0, action){
    switch(action.type){
    case INC:
        return store + 1;
    default:
      return store
    }
}
```

### Creating a store

```javascript
const store = createStore(counter);
```

### Actions
> Actions are just javascript objects that have a field named type.

For example:

```javascript
{type: "INC"}
```

We are going to create a function called incAction that returns our action.

```javascript
function incAction(){
    return {type: INC}
}
```

Pretty simple right?

### Dispatching an action

Now that we have created our action we need to tell redux to do something with our action.

This is as easy as calling

```javascript
store.dispatch(incAction());
```

Remember incAction() just returns {type: "INC"} so we could also write this code as:

```javascript
store.dispatch({type: "INC"});
```

For our project we will wrap our dispatch code in a setTimeout with a 1 second delay.
```javascript
setTimeout( ()=> {
    store.dispatch(incAction());
}, 1000)
```

### Subscribing

So, we have set the value of our state. Now lets do something with it. Thankfully, reading state is easy in redux and can be done with only one line of code:

```javascript
const s = store.getState();
```

While this is useful, we are going to go one step further. Instead of accessing state directly we are going to ask redux to tell us when state changes. To do this we need to use redux's .subscribe method. Here is the code:

```javascript
store.subscribe(() =>{
    const s = store.getState();
    alert(s);
})
```

Whenever our store changes redux will call our function that gets the current state and alerts it to the screen.

### The code

If you followed everything we just did then you have successfully implimented most major parts of redux in just 27 lines of code. Not bad for a days work.

```javascript
import { createStore } from 'redux'

const INC = "INC"

function incAction(){
    return {type: INC}
}

function counter(store=0, action){
    switch(action.type){
    case INC:
        return store + 1;
    default:
      return store
    }
}

const store = createStore(counter);

setTimeout( ()=> {
    store.dispatch(incAction());
}, 1000)

store.subscribe(() =>{
    const s = store.getState();
    alert(s);
})
```

Running

```bash
parcel app/index.html
```

again and refreshing our browser we see the page load and a second later we get a popup saying "1".

Congratulations! You have built your first project using redux. It wasn't that bad was it?
