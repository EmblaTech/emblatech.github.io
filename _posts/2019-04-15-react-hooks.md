---
layout: post
title: "Getting baited onto react hooks !"
quote: "... [React hooks] are functions that let you listen or hook onto react state or its life-cycle features by using function components and additionally you could also build your own custom hooks."
image:
      url: /media/medium/denise-jans-1203943-unsplash.jpg
video: false
comments: true
author_name: Dasith Kuruppu
author_url: https://github.com/EmblaTech
author_pic: istockphoto-836272842-612x612.jpg
---

<style type="text/css"> #post-info { background-color: rgba(0,0,0,.5); padding: 10px; } </style>

Note: This article was originally published at www.dasithsblog.com.

![](https://cdn-images-1.medium.com/max/7084/1*01NFIfuNYRyaRZM0t4lC8A.jpeg)

## What is a hook ?
> With the latest react version 16.8 react got a whole lot cooler and better with the introduction of hooks! To those that are unaware of what hooks are; they are functions that let you listen or hook onto react state or its life-cycle features by using function components and additionally you could also build your own custom hooks.
[**Getting baited onto react hooks !**
*An introduction to react hooks. The latest update to react brought in a quite a few drastic changes to react one of…*www.dasithsblog.com](https://www.dasithsblog.com/blog/react_hooks/)

## What is so great about function components & hooks that make them any better than class components ?

1. The main reason is that hooks allow you to reuse stateful logic without changing your component hierarchy.This allows for decoupling of logic/state from the rendering which helps a lot when testing, reusing and manageability of code.

1. A more simplified api. With hooks the react life-cycle methods(componentDidMount, componentDidUpdate, and componentWillUnmount) get simplified into one single hook useEffect.

1. Offers a better and simplified state management out of the box which significantly reduces deep nesting of components using higher-order components(HOC),render props and context.

1. No more verbose boilerplate code that comes with class components which more often than not complicates programming flow and code base. With hooks react chooses a direction that embraces the natural functional programming style of JavaScript which in my opinion is a step in the right direction which gives more freedom for developers to pick and choose how to structure their code , style of programming and design patterns.

1. Hooks also make react more easier to figure out and adopt to, specially for a newbie as there is no more binding and figuring out this keyword when it comes to JavaScript.
[**Introduction to modern Javascript-Part I (ECMAScript5 / ES5)**
*Gives an introduction to modern JavaScript. How it changed drastically over time, where it stands today and what the…*www.dasithsblog.com](https://www.dasithsblog.com/blog/modern_javascript/)

## How would a typical class component look when turned into a functional component with hooks ?

Lets take a typical react class component and try to convert it to a functional component. Assuming we are given a scenario to fetch GitHub information of a given user name and display the details a react class component would typically look like this…

## Class component

<iframe src="https://medium.com/media/5c397897d3db55e3c9af4d70d8c0b54d" frameborder=0></iframe>

An equivalent functional component to the class component above would look like the following…

## Functional component

<iframe src="https://medium.com/media/8f21cab521d5944517387d533fcdf57b" frameborder=0></iframe>

Notice how cleaner and better it looks with all the boilerplate code removed.Here it is really simplified with state hooks(useState), by using state hooks you can directly set state to a localized version of state for each hook.

const [inputUserName, setInputUserName] = useState("dasithKuruppu");

The above line initializes state with the default string "dasithkuruppu" by calling useState() which returns an array with 2 elements which can destructured** **to [inputUserName,setInputUserName] only difference being that here the setInputUserName is more or less localized only to the state initialized using useState(). When it comes to the above inputUserName is the **state** while setInputUserName is the function that allows us to set the state.

const [gitHubUserInfo, getGitHubUserInfo] = useGetGitHubInfo(null);

This line does something similar except there is the missing piece, this uses a **custom hook** which allows us to decouple and abstract state away from components and reuse them easily. The custom hook for this can be written like this.

<iframe src="https://medium.com/media/62a59769d279c0a1bf6570dbd1e53090" frameborder=0></iframe>

This hook could be used on **any component** that needs GitHub user information with barely any boilerplate code or a higher order component(HOC).You may now be thinking what kind of sorcery this is… well its partly right as the new hooks api requires a mind shift from the typical react flow and at first it may seem like there is a lot of *magic* happening under the hood.However explaining what happens here might clear things up a bit , first things first a custom hook is also capable of having hooks to state and react lifecycle features !

const [gitHubUserInfo, setGitHubUserInfo] = useState(null);

This piece of code as you guessed initializes a state for gitHubUserInfo.

    useEffect(() => { 
      getGitHubUserInfo(); 
    }, []);

This is the equivalent of **componentDidMount** and if you happen to return something on the function passed to useEffect it would be the equivalent of **componentWillUnmount**. And on the 2nd argument to useEffect it takes an array of items that React will keep track of and if any of it changes function passed to useEffect would be executed, you can do this if you want it to behave somewhat similar to **componentDidUpdate**. However in this case we have passed an empty array as the 2nd argument to useEffect (equivalent of *componentDidMount*) and within the function passed to it we have executed getGitHubUserInfo(), which fetches GitHub user information from a public endpoint and calls setGitHubUserInfo with the response which as I explained before sets the state gitHubUserInfo. Finally we return an array with the state gitHubUserInfo and the asynchronous function getGitHubUserInfo which can be called on each button click.

The rest of the code on the GitHubProfile is pretty self explanatory its basically plugging in state and the button click event handler in the JSX. Similar to what was on the class component except that this reference is gone and only variables/const are used. In case you have a lot of state / actions on a component It could be also wise to separate out this logic from the component. You can do this easily with useReducer if you were to replace useState with useReducer in the previous example it would look something similar to this

<iframe src="https://medium.com/media/65e2e04bab66841ae16ca7e49d3840af" frameborder=0></iframe>

This looks like a lot of code compared to useState but that gives us the advantage of separating state from component entirely like using [redux ](https://redux.js.org/)without [redux ](https://redux.js.org/)! A reducer helps us to understand code better as opposed to having many useState calls in the component itself which can make the component look a lot more complex than it actually has to. This is also a lot similar to redux and you can actually implement a redux style state management by using useReducer and the useContext(context api) without actually using redux or its additional boilerplate / higher order components.However this is a topic for another article.In this article I only hoped to cover the basics of hooks and hope you learned something. Let me know if you have comments / feedback below...

You can find working versions of of the code above on a sandbox [Hooks with useReduce](https://codesandbox.io/s/n0l1xw584j) and [Hooks with useState](https://codesandbox.io/s/x9wpq4kl0w).

*Originally published at [www.dasithsblog.com](https://www.dasithsblog.com/blog/react_hooks/).*
