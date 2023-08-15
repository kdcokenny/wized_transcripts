In the embed 2.0, the new data field editor is significantly faster and more stable than ever before. This is because we're using JavaScript functions under the hood. Now, if you're not a developer, you're probably feeling a little bit intimidated right now, but don't worry, there's nothing to be scared of. In the old embed, whenever you would use the so-called logic blocks, you were writing JavaScript inside there. So all the knowledge that you gained from there, you can apply to the new data field editor as well. Let me give you a quick analogy that will help you understand JavaScript functions. You can think of a JavaScript function as a magic box, and this magic box has some input slots at the top. Now, whatever you put in those input slots can be accessed from within the magic box. Now, whenever you create something inside of that magic box, if you want to take it out of the magic box, you have to say, hey, I want to get this out of the box. And it works the same way with return statements in JavaScript functions. We have here our input slots, or as we call them, function parameters. We have the cookie object, which contains all of our cookies. We have events, forms, inputs, navigational data. We have all of our requests. We have trigger data, and we have variables here. Inside of our data field, we have access to all of these objects. So we can write C dot, and we can see our cookies. If we write V dot, we can see all of our variables. We have them over here as well. If we use R dot, we can see all of our requests, and so on and so forth. Now, whenever we want to get something out of the data field, we have to use return and then a value. So if we wanted to get this field out of our request, we would write here return and this field. And as you can see here, the result of our data field is now Nick, because that's the value of our request field. And we can also access form values. So if we write F dot the form name dot any input field that we select, in this case, the input field has not yet been filled out on the page, so that's why the result is not showing up here. But if we would fill out this field now on the page, we would see here the value of the input field. Another major difference between the embed 1.0 and the embed 2.0 is that in the old embed, WISD would automatically infer a data type. Let me show you what I'm talking about. Whenever you would write some text inside of the data field, like so, WISD would automatically infer that this is a string. In the new embed, you cannot do that any longer. You can just write here, hello world, just like this. As I said, WISD does not infer automatically what the value of the data field is. So what you have to do instead is use string notation and you have to write explicitly return this string. This might seem like a little bit of extra work at first, but it will help you become a better developer. The best part about this new data field editor is that you're learning real JavaScript in an easy and simple manner. And that's a quick overview of the new data field editor.