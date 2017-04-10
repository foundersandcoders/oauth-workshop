## Step 7 - Session management (storing your access token)

Great! So we're ready to store our access token in a cookie. And how do we do that? We could use `hapi-auth-cookie`, but that's a bit overkill at the moment.

We're not dealing with hapi authentication just yet.

+ Use [`server.state`](https://hapijs.com/api#serverstatename-options) - so-called because it deals with persisting "state" across multiple requests - to store information / data that you want to be accessible across pages.  
Hint: See the [hapi tutorial on cookies](https://hapijs.com/tutorials/cookies?lang=en_US)).

Once you've set your cookie, with your access token inside, you can finish up with [step 8](./step8.md)
