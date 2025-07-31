# Auth proxy in nginx

This is a quick test for adding auth to nginx using oauth2_proxy and auth0.

### Step 1: Create a new auth0 application

1. Create an application
2. Choose "Regular Web Applications" as the application type.
3. In the application settings, set "Allowed Callback URLs" to: `http://localhost/oauth2/callback`

### Step 2: Set .env variables

1. Copy the `example.env` file to `.env`.
2. Fill in the required variables (you can find these in your Auth0 application settings):
   - `AUTH0_DOMAIN`
   - `AUTH0_CLIENT_ID`
   - `AUTH0_CLIENT_SECRET`
   - `COOKIE_SECRET` (generate a random string using `openssl rand -base64 32 | tr -d '\n'`)

### Step 3: Run the application

```
docker-compose up
```

Now open your browser and go to `http://localhost/app_with_auth`. You should be redirected to the Auth0 login page. After logging in, you will be redirected back to the application.
