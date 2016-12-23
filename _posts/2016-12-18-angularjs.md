---
layout: post
title: building a single page app
---

======
**the project**
======

**requirements** >> build a single page AngularJS app with Rails backend.

**the app** >> gubbinal, an app to help you discover musicians' top three records and directors' top three films.

======
**the takeaway**
======

Before digging into Angular (and jQuery), it seemed like front-end design meant making something that was nice to look at. Now I understand that it's more about making something that's nice to interact with.

It's incredible to see Angular bring HTML to life. <a href="http://jsfiddle.net/anandmanisankar/L6nofag6/">This fiddle</a> - five brief lines of code that demonstrate two-way binding - perfectly illustrates how powerful and efficient Angular is. The example is simple--certainly not much to look at--but the ability to change a div's content with each keystroke <i>feels</i> magical.

Initially, the most complicated aspect of building the app was figuring out how Angular and Rails should interact. The Learn curriculum on Angular covered a ton of information about working with Angular itself, but there weren't any lessons that covered how Angular should relate to the backend. And I'm glad that was the case; throughout the learning process, I've found that working through a problem with little guidance is one of the most effective ways to really learn something.

The first issue: routing. To let Rails handle the routing, I set the root at application#index and defined index in the application controller. Then, it was as simple as putting the <div ui-view></div> in the index.html file and using AngularUI router to define different states.

The next issue I ran into--and still need to return to--was posting data to the Rails backend using Angular's $http service. The issue is that the backend is trying to protect your app against CSRF attacks (<a href="https://stormpath.com/blog/angular-xsrf">more on that here, if you're unfamiliar</a>), so you have to include an XSRF token in the header of your request. From Angular's documentatin:

"Angular provides following mechanism to counter XSRF. When performing XHR requests, the $http service reads a token from a cookie called XSRF-TOKEN and sets it as the HTTP header X-XSRF-TOKEN. Since only JavaScript that runs on your domain could read the cookie, your server can be assured that the XHR came from JavaScript running on your domain."







======
**preview**
======

<img src="https://bennorris.github.io/blog/assets/gubb1.gif"/>

======
**screenshots**
======

<img src="https://bennorris.github.io/blog/assets/gubbinal-musician.png" style="height: 100%; width: 100%; object-fit: contain"/>
<img src="https://bennorris.github.io/blog/assets/gubbinal-film.png" style="height: 100%; width: 100%; object-fit: contain"/>
<img src="https://bennorris.github.io/blog/assets/gubbinal-list1.png" style="height: 100%; width: 100%; object-fit: contain"/>
<img src="https://bennorris.github.io/blog/assets/gubbinal-musiclist.png" style="height: 100%; width: 100%; object-fit: contain"/>
