## Step 6 - Protecting your access token

We can now use our access token to make requests to the Github API on behalf of the authenticated user. But before we can do that, we need a way to store the token, so we can access it via other routes. :cookie: :cookie: :cookie:

Beware of passing sensitive information across an insecure connection.
> Cookies are typically transmitted in the clear.  Thus, any
   information contained in them is at risk of disclosure.  Therefore,
   bearer tokens MUST NOT be stored in cookies that can be sent in the
   clear.  See "HTTP State Management Mechanism" [RFC6265] for security
   considerations about cookies.

In the OAuth flow, we're dealing with very sensitive user info. So it's always advisible to be running on HTTPS :+1:

Luckily, hapi also has our back by having `isSecure` set to `true` by default i.e.
> the user agent will include the cookie in an HTTP request only if the request is transmitted over a secure channel

and `httpOnly` set to `true` by default as well
> instructs the user agent to omit the cookie when providing access to cookies via "non-HTTP" APIs (such as a web browser API that exposes cookies to scripts)

(Quotes from the [HTTP State Management Mechanism docs](https://tools.ietf.org/html/rfc6265))

For more on the benefits of hapi as a backend framework, head to [this DWYL repo](https://github.com/dwyl/learn-hapi#why-hapi-instead-of-xyz-framework).

+ But we still shouldn't put the access token directly into our cookie. This is sensitive information, so let's encrypt it with `bcrypt`.

Hint: "how to use `bcrypt`" was part of your week 7 research topics.
