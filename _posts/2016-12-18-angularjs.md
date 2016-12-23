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

It's incredible to see Angular bring HTML to life. <a href="http://jsfiddle.net/anandmanisankar/L6nofag6/">This fiddle</a> - five brief lines of code that demonstrate two-way binding - perfectly illustrates how powerful and efficient Angular is. The example is simple, but the ability to change a div's content with each keystroke <i>feels</i> magical.

Initially, the most complicated aspect of building the app was figuring out how Angular and Rails should interact. The Learn curriculum on Angular covered a ton of information about working with Angular itself, but there weren't any lessons that covered how Angular should relate to the backend. And I'm glad that was the case; throughout the learning process, I've found that working through a problem with little guidance is one of the most effective ways to really learn something.

The first issue: routing. To let Rails handle the routing, I set the root at application#index and defined index in the application controller. Then, it was as simple as putting the <div ui-view></div> in the index.html file and using AngularUI router to define different states.

The next issue was posting data to the Rails backend using Angular's $http service. Because Rails tries to protect your app against CSRF attacks with a required security token (<a href="https://stormpath.com/blog/angular-xsrf">more on that here, if you're unfamiliar</a>), you have to include an XSRF token in the header of your $http request. From Angular's documentation:

"Angular provides following mechanism to counter XSRF. When performing XHR requests, the $http service reads a token from a cookie called XSRF-TOKEN and sets it as the HTTP header X-XSRF-TOKEN. Since only JavaScript that runs on your domain could read the cookie, your server can be assured that the XHR came from JavaScript running on your domain."

Another tricky thing to figure out was isolating the response to a click event within an ng-repeat. With Gubbinal, after a user searches a musician or director, there are three results and each one has a button that allows the user to add that film/record to his/her list. After the item successfully POSTed to the list, I wanted to display a success message - but it displayed in all three divs, not just the one that contained the POSTed item. My solution was to use ```track by $index``` in the view. Then, in the controller, I set $scope.message to an array of three empty strings so that by default the message wouldn't display anything in the view. After a user added an item, I used the $index of that item to set $scope.message[$index] = "Successfully Added!". It works great for Gubbinal, but I realize that there's probably a better solution, and it's not very scalable code for a larger data set (if there were 100 search results, that would mean setting one hundred empty strings within the array...).

The last thing I'll mention is creating a dynamic navbar. If users are logged in, you don't want to show them a signup page; and if they aren't logged in, you don't want to offer them a sign out link. In rails, you might include something in your html.erb view like:

```html
 <% if current_user %>
    <li>sign out<li>
 <% else %>    
    <li>sign in</li>
 <% end %>    
```
There are probably plenty of different ways to accomplish the same thing in Angular, but my solution was to set the display properties based on a condition within the controller. You can create a function that checks the database (or in this case, $localStorage) to see if the user is logged in:

```JavaScript
$scope.isLoggedIn = function() {
  if ($localStorage.facebook !== "") {
    return "display:inline";
  } else {
    return "display:none";
  }
}
```

And in the view, the function is passed in as an expression:

```html
<li style="{{ isLoggedIn() }}"><a ng-click="logMeOut()" href="">log out</a></li>
```

I plan to deploy Gubbinal with Heroku in the near future. But in the meantime, here are a few screenshots that give a general idea of how the app looks/functions. 


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
