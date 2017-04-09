## Step 5 - Create your redirect route

Remember in [step 3](./step3.md), when you set the `Authorization callback url` in your Github settings? This was a redirect URI that _we_ provided to _Github_. So, when a user clicks "Authorize application", Github sends them to the route we specified i.e. `https://localhost:3000/welcome`.

So we need another route on our server to handle this redirection :+1:

Remembering the OAuth flow, we know that Github is going to send us back a temporary code in the URL query. But we still need to retrieve our access token, in order to access the Github API on behalf of the user.

1. In your hapi server, write a `GET` route for the `/welcome` endpoint.

2. The handler needs to:
  + Send a `POST` request to the relevant endpoint on the Github API - time to go back to [the Github docs](https://developer.github.com/v3/oauth). Don't forget to include the necessary parameters in the body of your request.  
  You'll probably want to use the [`request` module](https://www.npmjs.com/package/request)  
  Hint: the `code` will be sent to you at the redirect URI as a query parameter (e.g. `/welcome?code=foo`. How do you access query parameters using the `request` object?
  + Reply with the home view that you created in step 1

Let's jazz up this home view now in [step 6](./step6.md).
