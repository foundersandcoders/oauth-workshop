## Step 4 -- Create your redirect route

We provided a redirect URI to Github to which it will send the user after they have logged in and granted our app permission. Now we should create that route on our server to retrieve the access token that we need to access the Github API on behalf of the user.
* In your Hapi server, create a route `GET /welcome` which sends a request to
```
POST https://github.com/login/oauth/access_token
```
* The body of the request needs the following fields:
  * `client_id`
  * `client_secret`
  * `code`
* For now, simply reply with the body of the response.
* Hint: the `code` will be sent to you at the redirect URI as a query parameter (e.g. `/welcome?code=foo`. How do you access query parameters using the `request` object?
