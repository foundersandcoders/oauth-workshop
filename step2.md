## Step 2 - Set up your SSL certificates

Ever wondered why it's called OAuth 2? Well, we're not going to go into a history lesson here about OAuth 1. But OAuth 2 relies on TLS (Transport Layer Security), instead of the complicated signature mechanisms of OAuth 1. If we were to dive into this, we could be here all day. But it's a fascinating topic.

Sufficed to say, in the official [OAuth 2.0 specification](https://tools.ietf.org/html/rfc6749), it is _heavily_ recommended that client applications do not operate without Transport Layer Security:
> 3.1.2.1.  Endpoint Request Confidentiality
>
>  The redirection endpoint SHOULD require the use of TLS as described
   in Section 1.6 when the requested response type is "code" or "token",
   or when the redirection request will result in the transmission of
   sensitive credentials over an open network.  This specification does
   not mandate the use of TLS because at the time of this writing,
   requiring clients to deploy TLS is a significant hurdle for many
   client developers.  If TLS is not available, the authorization server
   SHOULD warn the resource owner about the insecure endpoint prior to
   redirection (e.g., display a message during the authorization
   request).
>
>  Lack of transport-layer security can have a severe impact on the
   security of the client and the protected resources it is authorized
   to access.  The use of transport-layer security is particularly
   critical when the authorization process is used as a form of
   delegated end-user authentication by the client (e.g., third-party
   sign-in service).


So technically, the spec only mandates that the _authorisation server_ (Github, in the context of this workshop) use TLS. But it's pretty clear that it is severe for our server (the "client server" in this context) not to use it. Let's go ahead and make our application's server operate on a secure connection too :smile:

First of all, now that you're swapping pairs, you'll want to swap computers too. This is a good habit to get into, partly so that your Github contribution graphs reflect an equal contribution to the project. (Bragging rights!) It's also nice to be able to code on your own machine, with your own setup...particularly if you're a vim user :speak_no_evil:. Aaaaand one last benefit - you get to try out your project on multiple machines. This can mean that your project gets used on different operating systems, and maybe on different browsers. :tada:

Remember to raise a new issue on your Github repo called `set up SSL certificates`. Now let's get going!

1. Generate a key file for your certificate  
`openssl genrsa -out key.pem 2048`  
Open up atom. You should see a newly created file in your project now, called `key.pem`

2. Generate an intermediate file (csr)  
`openssl req -new -key key.pem -out csr.pem`  
Follow the instructions in your terminal. You can just press enter to accept the defaults, or enter the full details.  
Again, in atom you will see a second file called `csr.pem`.

3. Generate a certificate file, using the key and csr  
`openssl x509 -req -days 9999 -in csr.pem -signkey key.pem -out cert.pem`  
Now you have a third file called `cert.pem`.

4. Delete the intermediate csr file  
`rm csr.pem`

5. Store the `cert.pem` and `key.pem` files in a safe place, away from the rest of your project.  
`mkdir keys`  
`mv cert.pem keys/cert.pem`  
`mv key.pem keys/key.pem`

6. **Add "keys" to your gitignore**. NEVER PUSH YOUR KEYS TO GITHUB! :scream:

7. Browse through the hapi docs again to find out how to create an HTTPS connection on your server.  
Hint: `server.connection`

8. Change the `BASE_URL` variable in your `config.env` to `https`, instead of `http`.

9. Push your latest changes to Github.

If you're anything like me, at this point you'll be crying
> Hold on! That was deeply dissatisfying. I don't want to just paste random commands into my termainal! What did all of that mean?

If that's you, this article has a great explanation of [how HTTPS works](http://robertheaton.com/2014/03/27/how-does-https-actually-work/), but there is a workshop coming up later that may also help.

Until then, all you need to know is that, if you start your server and go to `http://localhost:3000`, it won't work. You're on https now :tada:.

On to [step 3](./step3.md)
