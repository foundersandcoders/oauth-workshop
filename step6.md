## Step 6 - Session management (storing your access token)

Great! So we're ready to store our access token in a cookie.

Why are we doing this? Well, we want to keep track of the fact that a user has logged in (i.e. their "session" on our application has started). The cookie makes this information available (the information "persists") across multiple requests. So all we have to do, is look for the cookie each time a client makes a request.

Note: Session management can be handled in many ways (e.g. local storage, session storage, IndexedDB). We are going to focus on cookies.

### Setup
[`hapi-auth-cookie`](https://github.com/hapijs/hapi-auth-cookie) is a useful plugin that handles the authentication _of the cookie_. The authentication of the _user_ is separate. `hapi-auth-cookie` protects the cookie's content by using a cryptographic utility called "iron" - find out more from its [npm module description](https://www.npmjs.com/package/iron).

1. Install the the `hapi-auth-cookie` plugin.

2. Register the plugin. Behind the scenes, `hapi-auth-cookie` has added a new authentication **scheme** to your hapi server called 'cookie'. (In the same way that you have `simple` with `hapi-auth-basic` - don't forget your validation function.)  
Note: You can also create your own plugins for hapi, in which case, you would write your own scheme to go with it.

3. Now you're able to add an authentication **strategy** to your server - just like you did in your morning challenge with `hapi-auth-basic`. For future reference, hapi has a [tutorial on authentication](https://hapijs.com/tutorials/auth), that will help you find out how to set your strategy.

5. Apply your new strategy to your routes, so that unauthenticated users are not allowed to access the content of your app.

### Put your access token inside the cookie

Look in `hapi-auth-cookie`'s '[npm module description](https://www.npmjs.com/package/hapi-auth-cookie) or in the [github repo](https://github.com/hapijs/hapi-auth-cookie).

1. Configure the options for your cookie

2. Set your cookie with the access token inside.

Once you've set your cookie, with your access token inside, you can finish up with [step 8](./step8.md)
