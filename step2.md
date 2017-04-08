## Step 2 -- Register your app

Github needs to know about your app before it will let you authenticate users with it.
* Go to Github profile settings > OAuth applications > Developer applications > Register new application
* Register your app. Call it what you like
* In the `homepage url` field type your `BASE_URL` (e.g. `http://localhost:3000`)
* In the `authorization callback url` field, type your `BASE_URL` + `/welcome` (e.g. `http://localhost:3000/welcome`)
* Add two new variables to your `config.env`: `CLIENT_ID` and `CLIENT_SECRET`, taken from your app page.
