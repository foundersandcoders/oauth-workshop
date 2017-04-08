## Step 2 - Register your app

Github needs to know about your app before it will let you authenticate users with it.

Swap driver & computer. There's no need to raise a new github issue this time. We're not going to write any code that's going on github.

1. On Github, go to your profile settings. Then click on "OAuth applications"

2. Now "Register new application"
3. Register your app. Call it what you like, but it makes sense for it to be the same name as your repo.
4. In the `homepage url` field type your `BASE_URL` (e.g. `http://localhost:3000`)
5. In the `authorization callback url` field, type your `BASE_URL` + `/welcome` (e.g. `http://localhost:3000/welcome`)
6. Add two new variables to your `config.env`: `CLIENT_ID` and `CLIENT_SECRET`, taken from your app page.
