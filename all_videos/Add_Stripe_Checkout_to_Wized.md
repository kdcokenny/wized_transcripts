In this video, we're going to learn how to add Stripe checkout to your website with Wyst. Now, the first thing you have to do is go to My Apps and choose here Stripe from the drop-down. Once you select Stripe, you can simply connect to your Stripe account. All right, I'm already logged into Stripe in another tab, so I'm going to see here my Stripe account. Once I click Connect, I'm going to get redirected back to Wyst. Now that I added Stripe to My Apps, it's time to create a request. So we're going to go to Data Out, we're going to create a new request here, and I'm going to call it Open Checkout. Here, under App, I'm going to select Stripe, type of request, Open Checkout. And here I can configure the checkout options. Now, my product, in this case, the test product that I created is a subscription, so I'm going to select Subscription here. Next, you have to click on this Add button, and you have to add the price ID. And this is something you get from Stripe. So I created this dummy product over here, and I can simply copy this App ID. It's under Products, My Product. And I'm going to paste it in here. Next, we have to specify the quantity. In this case, I'm going to write 1. And here, this is an optional field. You can add your own price. And here, this is an optional field. You can add your tax ID. Next, we have checkout settings. Here, we can select which payment methods we want to accept. In this case, I'm going to select only credit card. Now, we have to specify the success URL and the cancel URL. Now, you can't just write a relative path like this. You have to write an absolute path, meaning you have to write the whole URL. So in this case, I'm just going to paste my URL in here. And if the payment was successful, I'm going to redirect the users to the homepage. So I'm going to delete this. Otherwise, I'm going to redirect the users back to the payment page. Perfect. Now, these fields are optional. We can specify the customer email. We can specify also the Stripe customer ID. These fields you can get either from your load user request, if you have it, or maybe you can have a field here where the customers can write their email. All right. In this case, I'm just going to leave all of this empty. And here, if you want, you can specify from which countries you're going to accept payments. In this case, I want to accept payments from all of the countries, so I'm not going to add any countries here. Perfect. And now, if we try to trigger our request, we're going to see that we get a response from Stripe. And we created successfully a checkout session. And what's important to note here is that we have this checkout URL that gets generated for us, and we have to add that in the after request action. So here, we're going to choose navigate to. Of course, if the request was successful. So we're going to check if status code equals 200. Like this. And under URL, we're going to add our checkout URL. Perfect. The last thing we have to do is add an action to this button that's going to trigger our request. So we're going to go to actions. We're going to add a new action. And here, I'm going to call it trigger checkout. I'm going to apply it to our button buy now element. And under configuration, I'm going to choose on click, perform request, open checkout. Perfect. And if I refresh the canvas now, the action should be applied. I can simply go to preview. And now, if I click on this buy now button, And now, if I click on this buy now button, I'm going to get redirected to the checkout. Here, I can fill in my details. If I make a successful transaction, I'm going to get redirected to the homepage. Otherwise, if I just cancel it, I'm going to go back to the billing page. Also note that you can use coupons, which you can create in your Stripe dashboard. And here, users can add then their promotional codes. All right, that's it. And this is how you configure Stripe checkout with Wiz and Webflow. Thanks for watching and I'll see you in the next video.