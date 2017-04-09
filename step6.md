## Step 6 - Session management (storing your access token)

In theory, we can now use our access token to make requests to the Github API on behalf of the authenticated user. But before we can do that, we would need a way to store the token, so we can access it in other routes. I know what you're thinking! :cookie:

But an _unencrypted_ access token should **never** be put in a cookie.
> Cookies are typically transmitted in the clear.  Thus, any
   information contained in them is at risk of disclosure.  Therefore,
   bearer tokens MUST NOT be stored in cookies that can be sent in the
   clear.  See "HTTP State Management Mechanism" [RFC6265] for security
   considerations about cookies.

There are two main ways of dealing with this - session IDs & JSON Web Tokens. We will be covering JWTs tomorrow :smile:, so don't worry too much about this for now.

But it is worth knowing the different processes:

### Session IDs - stateful
+ The access token is stored in a database (#7 of the OAuth flow diagram)
+ The server creates a session.
+ The session ID is stored in the database (server-side) & set in a cookie to be stored in the user's browser (client-side)
+ Each time the user makes a new request, the server verifies the session ID against the database & if so, processes the request.
+ If the session ID is valid, the server either returns a view (if no Github data is required) or makes a request to Github (#8), which is then returned (#9)
+ When a user logs out, the session ID is removed from the database and the cookie is cleared

### Tokens - stateless
+ The access token is encoded into a JWT
+ This JWT is stored client-side, either in local storage, session storage or a cookie (we will be using cookies)
+ Each time the user makes a new request, the server decodes the JWT.
+ The server checks if the token is valid & if so, processes the request
+ If no Github data is required, the server serves the relevant view. Otherwise, the server makes a request to Github (#8), which is then returned (#9)
+
+ When a user logs out, the token is destroyed client-side, no interaction with the server is necessary
