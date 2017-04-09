## Step 2 - Set up your SSL certificates

DISCLAIMER: This step is _not_ a necessary part of the OAuth flow - OAuth operates over HTTPS by default. You can choose to go directly to [step 3](./step3.md) if you prefer.

Ever wondered why it's called OAuth 2? Well, we're not going to go into a history lesson here about OAuth 1. But OAuth 2 relies on TLS (Transport Layer Security), instead of the complicated signature mechanisms of OAuth 1.

So while we're talking about security, let's show you how to get your _own application_ onto a secure HTTPS connection too :smile:

First of all, now that you're swapping pairs, you'll want to swap computers too. This is a good habit to get into, partly so that your Github contribution graphs reflect an equal contribution to the project. (Bragging rights!) It's also nice to be able to code on your own machine, with your own setup...particularly if you're a vim user :speak_no_evil:. Aaaaand one last benefit - you get to try out your project on multiple machines. This can mean that your project gets used on different operating systems, and maybe on different browsers. :tada:

Remember to raise a new issue on your github repo called `set up SSL certificates`. Now let's get going!

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

7. Change the `BASE_URL` variable in your `config.env` to `https`, instead of `http`.

8. Push your latest changes to github....yes the only thing that you have changed is that you added "keys" to your gitignore. But never forget this step :fire:.

If you start your server now, and try to go to `http://localhost:3000`, this won't work. You're on https now :tada:.

On to [step 3](./step3.md)
