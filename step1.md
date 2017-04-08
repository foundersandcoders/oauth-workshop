## Step 1 -- Setup a basic Web server

We need a server running before we can do anything.

Try to do this step without looking back at your previous projects. Use the hapi docs if you need help. This may seem like we're tying your hands behind your back unnecessarily. But trust us, this is what you need to do after Founders and Coders, to implement anything you haven't done before. So it's good to get your practice in now!

1. Start a new repo in your cohort's github organisation. Name it something distinctive, otherwise we will have loads of OAuth repos in there :wink:. Make sure you initialise it with a node gitignore file. (It's always good to initialise your repos with a README.md too, but you won't need to use it during this workshop.)
2. Clone your repo, `cd` into the directory & create a new node project locally, by running `npm init` to create your `package.json`
4. Install `hapi` and `inert`
5. Create a Hapi server that serves up a 'Hello World' `html` file at `/`  
Hint: you will need `server.connection`, `server.register`, `server.route` & `server.start`
6. Create a `config.env` file for your project and store your server address in a variable called `BASE_URL`
