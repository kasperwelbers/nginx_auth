# Auth proxy in nginx

This is a quick test for adding auth to nginx using oauth2_proxy and auth0.

### Step 1: Create a new auth0 application

1. Create an application
2. Choose "Regular Web Applications" as the application type.
3. In the application settings, set "Allowed Callback URLs" to: `http://localhost/oauth2/callback`

### Step 2: Set .env variables

In your Auth0 Application settings you can find your domain URL, client id and client secret. 
Create a .env file in the root of this repo to set these variables.
We also need to provide a 32 byte secret for oauth2 proxy.

```
AUTH0_DOMAIN=<AUTH0_DOMAIN> (something like https://dev-ejofijsdf.eu.auth0.com)
AUTH0_CLIENT_ID=<AUTH0_CLIENT_ID>
AUTH0_CLIENT_SECRET=<AUTH0_CLIENT_SECRET>

COOKIE_SECRET="9v3VXu2klBs1lgsO5yDv1vRvgb8MlI2FAARehL4F6jg="
```
Note that the COOKIE_SECRET is not very secret since we include it in this repo. 
When replicating this on a server, make sure to generate a new one  (`openssl rand -base64 32 | tr -d '\n'`)

### Step 3: Run the application

```
docker-compose up
```

Now open your browser and go to `http://localhost`. You should be redirected to the Auth0 login page. After logging in, you will be redirected back to the application.
