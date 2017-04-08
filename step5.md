## Step 5 -- Store your access token

We can now use our access token to make requests to the Github API on behalf of the authenticated user. But before we can do that we need a way to store the token so we can access it in other routes.

Typically, this is done either in a database, a cookie or JSON web token (jwt). As we used hapi-auth-cookie last week, we'll use it again to store our github access token.
