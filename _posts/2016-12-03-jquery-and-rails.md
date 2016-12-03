---
layout: post
title: jquery with rails
---

======
**the project**
======

**requirements** >> add dynamic features to a Rails app that are possible only through jQuery and a JSON Api.

======
**the takeaway**
======

Working with jQuery is 1. a lot of fun 2. occasionally maddening. I’ll start with 1:

Before adding jQuery to my Rails project (<a href="https://bennorris.github.io/blog/2016/11/06/rails">more on that here</a>), every action required a page refresh: each click of the ‘next story’ button, each new story submission, every upvote for a sentence. Everything worked fine—and the delay caused by the page refresh was only a second or two—but the user experience felt clumsy. I hadn’t really considered the importance of fending off a page refresh: it was just something that I took for granted. Of course Twitter wouldn’t refresh the page every time you clicked the ‘Like’ heart. For most people, this functionality is so subtle as to be unnoticable. But the process of taking that click, turning it into a like, updating the total amount of likes, and displaying that to a user immediately is a beautiful thing. And despite having an idea of how it works, I’m still in awe.

So that’s all to say: it’s a lot of fun to see jQuery smoothen out the edges of your app and turn it into something that’s enjoyable to use. There’s an element of immediate gratification involved with front-end work: because it’s primarily visual, you get instant feedback. When you click on that ‘next’ button, either it displays the story properly or it doesn’t. Because I love a well-designed website, that sort of instant feedback makes playing with jQuery pretty addictive.

OK, now onto the maddening stuff.

For instance: an .on(‘click’) event that triggers twice every time, despite every effort to make sure the event is only called once. In this case, a handful of Stack Overflow posts pointed me in the right direction: I needed to remove the event handler with an ‘off.on(‘click’) / unbind.on(‘click’).

And another one: having an event continually happen, despite every effort to prevent it. The answer: exploring subtle differences between using event.stopPropogation, event.stopImmediatePropagation(), and event.preventDefault().

Learning anything new takes time--if it didn't, it probably wouldn't be worth learning--and I'm excited to continue with jQuery.  

======
**preview**
======

<img src="https://bennorris.github.io/blog/assets/storyline-jquery.gif" alt="storyline"/>
