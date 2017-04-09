## Step 6 - Session management - storing your access token

In theory, we can now use our access token to make requests to the Github API on behalf of the authenticated user. But before we can do that, we would need a way to store the token, so we can access it in other routes. I know what you're thinking! :cookie:

But an _unencrypted_ access token should **never** be put in a cookie.
> Cookies are typically transmitted in the clear.  Thus, any
   information contained in them is at risk of disclosure.  Therefore,
   bearer tokens MUST NOT be stored in cookies that can be sent in the
   clear.  See "HTTP State Management Mechanism" [RFC6265] for security
   considerations about cookies.

There are two main ways of dealing with this:
+ Randomly generated session IDs
+ Tokens i.e. JSON Web Tokens (JWTs), which we will be covering tomorrow :smile:
