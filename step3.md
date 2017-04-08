## Step 3 -- Create your login route

This is the url on our server which will begin the OAuth workflow.
* In your Hapi server, create a route `GET /login` which redirects the user to `https://github.com/login/oauth/authorize` along with two query parameters:
  * `client_id`
  * `redirect_uri`
* Hint: use the `querystring` native module to generate your query string. What is `reply.redirect`?
