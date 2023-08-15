In this video we're gonna learn how to set up passwordless sign-in or magic link authentication. In this case we're gonna be using Airtable but if you want to use Superbase or Firebase you can apply these same learnings there. Alright, the first thing you have to do is add Airtable to My Apps. Once you have this ready you can go to the Auth panel and here we can set up our authentication layer. So we're gonna expand this drop-down over here and under App we're gonna choose Airtable. Now we have to specify the user location and in Airtable I already created a project that I called wizrocks and here we can see table 1 contains our user base. It has an email field, a password field and here I added a formula field which gets the record ID. Alright, so let's pick our base here. I'm gonna choose wizrocks, under table I'm gonna select table 1 and here I have to add the email and password fields. Now although we're using passwordless sign-in we still have to select this password field here. Alright, now that our setup is configured let's start building our first requests. The first thing I'm going to add is this create user request and this is going to be applied to this sign-up page. So I'm going to click on the plus sign and here we can see that a data out request has been created and all of these fields have been pre-filled. But we still have to add some other fields here. So first we're gonna add the email input field so the user can provide an email address. So we're gonna expand this field, we're gonna go under general and here I already applied this input email with the attribute in my Webflow project. So I'm gonna select this here. Password, I can leave this empty because it's passwordless login and here under page I can specify the page to which I want to redirect the user once they click on the email link. In this case I want to redirect users to the dashboard when they log in. So I'm gonna write dashboard my schools and this corresponds to this page over here. So dashboard my schools. Perfect. Now if you have additional user information such as the user's name, address, etc. you can add these fields here. Alright, now that we have our create user request in place let's do the same thing for our login user request. So I'm gonna create a new request here under email I'm gonna add this email input. Now note that both on the signup form and the login form I have exactly the same attribute applied to the input. Here under page I'm gonna add the same URL. So dashboard my schools. Perfect. And that's it. Now we can go to the actions panel and we can add a new action. This action is going to trigger our signup request and then we're gonna do the same thing for our login request. So here I'm gonna call it submit signup. I'm going to apply this to this button over here and under configuration I'm gonna select on click perform request create user. Perfect. And now I can just duplicate this action over here and do the same thing for login. Apply to login, submit login, on click perform request login user. Perfect. And now if we refresh the page we can see that this request will get executed as soon as the user fills in the form. So let's go to page data, let's expand our create user request and if we add an email address here and we submit it we can see that this request got triggered. Perfect. And this request was successful. We can see here we have status code 200 and in the response we got the user's email address and a record ID. This means that by now I probably received an email with my login token. And indeed here it is. So if I click on this sign me in link, note that the page is covered with a loader over here. So in our next steps we're going to hide this loader and also you can see that we got redirected to the right URL. We have dashboard my schools. But also our URL contains some additional information. We can see here that we have something called a query parameter and this query parameter is called login token and it contains our login token. So we can just copy this value and we're going to need this in our next step. Now that we're back in WISD we can go to the auth panel again and we're gonna build this load user request. So we're gonna click on this plus sign over here. Under method we're gonna select load user and we're going to trigger this request whenever this attribute is present on the page. Logo dashboard. Now this is an attribute that's present only on dashboard pages. And now if we go to any dashboard page like my schools or settings we can see that this request gets executed. However we're getting an error here and this is because we don't have an auth token inside of the configurator. So we have to add it manually in this case. So we're gonna click on canvas here. We're gonna click add and here we're gonna write login token. And we're gonna paste our token in here. And now we can see that the current URL is this URL with the login token. And there we go. If we refresh the canvas we can see that the user has been loaded. Perfect. Now we can use this request to hide the loader. So for that we're gonna create a new action. We can call it display loader and we're going to apply it to our loader element. Here under configuration I'm gonna choose set visibility and the element is going to be visible if the load user request is currently being executed or if the request has finished executing but it wasn't successful. So we're gonna write as requested and status code does not equal 200. Okay so if the user is not successfully loaded we're going to display this loader. So we don't want users to be able to see the dashboard unless they're logged in. Perfect. If we refresh the canvas now since our user is getting successfully loaded we can see that the loader disappears here. Perfect. We can access our dashboard now. Now it's time to apply some access control rules. Basically access control rules will redirect users to the login page if they are not logged in. So here we're going to choose on which pages do we want to apply these access control rules and I want to apply this on every page that's within the dashboard. So I'm going to select this same logo dashboard attribute and here on the condition I'm going to specify the following. I'm going to expand the load user request and we're going to do pretty much the same that we did before with the loader we're just going to invert the logic. So we're gonna write here if isRequesting is true or if hasRequested is true and statusCode equals 200. Now what does this mean? This means that the user can stay on the page if the request is currently being executed or if the user was successfully loaded. Perfect. Otherwise we want to redirect the users to this home page over here which is our login page. Perfect. Now if we refresh the canvas we can still stay on the page because the user was successfully loaded however if we would log out then we would get redirected to the login page. Alright our last request which we're going to build is our logout user request and we're going to apply this on this logout button. So let's click on logout user and here we're also going to add an after request action. We want to redirect the users immediately to the login page so we're going to write navigate to this login page over here. Perfect. Now let's build a trigger for our logout button so we're going to go to actions here we're going to write logout user and we're going to apply this to our logout button. Under configuration we're going to select on click perform request logout user. Perfect and now we can refresh our canvas we can see we're logged in but if we click on this logout button we're going to get redirected to the login page. So let's now see the whole flow in action. We can see here that if I try to access the dashboard my schools I'm going to get redirected to the login page. If I fill in my credentials here I write my email address and I click on this link I'm redirected to the dashboard. And this is how you can set up magic link authentication for your project. Thank you so much for watching and I'll see you in the next video. you