## Step 1 - Set up a basic hapi server & serve 'Hello World'

We need a server running before we can do anything.

Try to do this step without looking back at your previous projects. Use the hapi docs if you need help. This may seem like we're tying your hands behind your back unnecessarily. But trust us, this is what you need to do after Founders and Coders, to implement anything you haven't done before. So it's good to get your practice in now!

1. Start a new repo in your cohort's Github organisation. Name it something distinctive, otherwise we will have loads of "`OAuth`" repos in there :wink:. Make sure you initialise it with a node gitignore file. (It's always good to initialise your repos with a README.md too, but you won't need to use it during this workshop.)

2. Raise an issue on your repo, called "serve Hello World on home route" and commit against this issue.

3. Clone your repo & `cd` into the directory.  
Create a new node project locally, by running `npm init` to create your `package.json`

4. Create a hapi server that serves up a basic `html` file at `/`, displaying 'Hello World'  
Remember, you will need to install `hapi` and `inert`  
Hint: `server.connection`, `server.register`, `server.route` & `server.start`

5. Create a `config.env` file for your project and store your server address in a variable called `BASE_URL`

Did you remember to make granular commits to your Github repo as you went? Did you remember to reference the issue?

Hopefully you're feeling a little warmed up. Make sure you push up your changes to Github, and then head to [step 2](./step2.md).
