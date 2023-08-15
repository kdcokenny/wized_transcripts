Hello and welcome to another tutorial. In this video, we're going to learn how to build this link shortener from scratch. Here's how it's supposed to work. A user can provide a link, then when the user clicks shorten, a shortened link will appear here, and then the user can copy this to the clipboard. All right, very simple. Now that we know the functionality that we're going to build, let's have a look at how this Webflow project is set up. So, we are not starting entirely from scratch. We already added all the wiz attributes to this element. We have the attribute of wiz-input-link. Here, we have the attribute of wiz-submit-link. Here, we have wiz-link, and we have wiz-copy-button here. All right, now, you probably noticed that we have also some other attributes here. We have this fscopyclip element equals click. This is from FinSuite attributes, and this is the copyclip attribute, which allows us to copy something to the clipboard. And we have here fscopyclip element copy-this. Also, on both of these elements, we have this attribute of wiz-cloak-custom, and here we have a request name, in this case, post-link. And what this does is it hides this element before the request is being executed. Now, we're going to get to that in a little bit, but for now, let's head over to Wizd, and let's set up our project. The first thing we're going to do is go to My Apps, and here, we're going to add Rebrandly. Under App, I'm going to select REST API, and here, I have to go to Rebrandly and provide this base URL. Once you open a free account with Rebrandly, you can simply click on your profile icon, go to API, and open the Developers Hub. Here, we're going to go to Getting Started, API for custom short URLs, and here, we're going to select Curl. And here, we have our base URL. I'm going to copy this to the clipboard, paste it into Wizd, and now, we can start configuring our request. I'm going to go to Data Out, because this is a POST request, and I'm going to add a new request. I'm going to call it POST link, because this needs to match whatever we're having in our Wizd cloak attribute, which is this value over here, POST link. And now, I'm going to select an app in the request. Here, I'm going to choose Rebrandly, and under URL endpoint, I'm going to add forward slash links. This is what we're having here. Next, it's time to add the method. Here, I'm going to choose POST, then under headers, I'm going to add the headers that we have in our example request. So, here, we have content type, application JSON, and we have API key, your API key. In our case, we don't need this workspace header. So, let's copy the first one, content type, application JSON. We're going to paste it in here, content type, application JSON. Here, our next header was API key, and now, we have to paste in the value of our API key. To get your API key, you can simply go back to your profile, click on API, and here, you can simply copy an API key to the clipboard. We're going to paste it in here, and whenever you're dealing with API keys, make sure to tick this box that the value is a secret. This will ensure that no one can simply inspect your site and find your API keys. In other words, the request is going to be executed on the server, and on the front end, it's going to be Next, it's time to add a key value pair to the body. We can see here we have this key destination, so we're going to copy that, and in this request example, we can see that a URL needs to be provided as the destination. Now, in our case, we want this destination to be provided by the user. So, here, we're going to write destination, and here, under value, we're going to select our Now, we have to set up a trigger for our request. We're going to go to actions, I'm going to create a new action, and I'm going to call it submit link. Here, I'm going to apply it to our button. Under settings, I'm going to choose on click, perform request, post link. And now, if we refresh the canvas, and I add a link here, I can shorten the link. Cool. Now, we can see this text, your shortened link will appear here, but where is the shortened link? Well, in our request response, we can go to page data, expand our request, and we can see here that we have a button, and we can see here that we have a button, and we can see here that we have a button, and we can see here that we have a request, and we can see here that whenever we run this request, we get all this data back. And one of these fields is our shortened link. So, we need to get this field over here, and display it over here, because if someone copies this now to the clipboard, they're copying this text. So, let's create an action that's going to replace this text with our shortened link. We're going to go to actions, add a new action, and call it display short link. I'm going to add it to the link field, and under configuration, I'm going to choose set text, plain text, and under text, I'm going to select the short URL field. Cool. Now, in my case, I want to add a little bit of extra logic to that field. I want to show the text shortening URL while this request is running, and first, when we get the response, I want to display the short URL, like in this case. So, what I'm going to do here is I'm going to go down, check if is requesting is true, and if is requesting is true, I want to show the following text. Shortening, and three dots. Otherwise, if the request finished executing, I want to display the shortened URL. Cool. Now, we can refresh our canvas and see all of this in action. If we paste a link here, and we click shorten, we can see that we get a shortened URL. If we try to shorten it again, we can see shortening for a brief period. And that's it. Now, the user can see the shortened Now, the user can simply copy this to the clipboard and paste it in wherever they want. And that's basically it. Thank you so much for watching, and I'll see you in the next video. Bye.