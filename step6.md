## Step 6 - Session management - storing your access token

In theory, we can now use our access token to make requests to the Github API on behalf of the authenticated user. But before we can do that, we would need a way to store the token, so we can access it in other routes. I know what you're thinking! :cookie:

But an _unencrypted_ access token should **never** be put in a cookie.
> Cookies are typically transmitted in the clear.  Thus, any
   information contained in them is at risk of disclosure.  Therefore,
   bearer tokens MUST NOT be stored in cookies that can be sent in the
   clear.  See "HTTP State Management Mechanism" [RFC6265] for security
   considerations about cookies.

There are two main ways of dealing with this - session IDs & tokens.
### Session IDs - stateful
+ The access token is stored in a database
+ The server creates a session.
+ The session ID is stored in the database (server-side) & set in a cookie to be stored in the user's browser (client-side)
+ Each time the user makes a new request, the server verifies the session ID against the database
+ When a user logs out, the session ID is removed from the database and the cookie is cleared

### Tokens - stateless
+ The access token is encoded into a JWT
+ This token (JWT) is stored client-side, either in local storage, session storage or a cookie (we will be using cookies)
+ Each time the user makes a new request, this token is included as an additional Authorisation header
+ The server decodes the JWT, checks if the token is valid & if so, processes the request
+ When a user logs out, the token is destroyed client-side, no interaction with the server is necessary

We will be covering JWTs tomorrow :smile:
