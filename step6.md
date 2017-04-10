## Step 6 - Session management (storing your access token)

We can now use our access token to make requests to the Github API on behalf of the authenticated user. But before we can do that, we need a way to store the token, so we can access it in other routes. :cookie: :cookie: :cookie:

Beware! An _unencrypted_ access token should **never** be passed across an insecure connection.
> Cookies are typically transmitted in the clear.  Thus, any
   information contained in them is at risk of disclosure.  Therefore,
   bearer tokens MUST NOT be stored in cookies that can be sent in the
   clear.  See "HTTP State Management Mechanism" [RFC6265] for security
   considerations about cookies.

Good thing we're running on HTTPS :+1: and hapi has always got our back by having `isSecure` set to `true` by default i.e.
> the user agent will include the cookie in an HTTP request only if the request is transmitted over a secure channel

and `httpOnly` set to `true` by default as well
> instructs the user agent to omit the cookie when providing access to cookies via "non-HTTP" APIs (such as a web browser API that exposes cookies to scripts)

(Quotes from the [HTTP State Management Mechanism docs](https://tools.ietf.org/html/rfc6265))

For more on the benefits of hapi as a backend framework, head to [this DWYL repo](https://github.com/dwyl/learn-hapi#why-hapi-instead-of-xyz-framework).


Great! So we're ready to store our access token in a cookie. And how do we do that? We could use `hapi-auth-cookie`, but that's a bit overkill at the moment. We're not dealing with hapi authentication just yet.

1. Use [`server.state`](https://hapijs.com/api#serverstatename-options) - so-called because it deals with persisting "state" across multiple requests - to store information / data that you want to be accessible across pages.  
Hint: See the [hapi tutorial on cookies](https://hapijs.com/tutorials/cookies?lang=en_US)).
