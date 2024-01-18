# Test Environment for OpenID Connect functionality

## Boot

```
docker compose up -d
```

This will start a local Authentik instance with a prepared configurations (user,oidc-provider,app)

## Auto provisioning

in `authentik/provisioning/blueprint.yaml` are some example objects to prefill Authentik

* A user `devuser`:`password123`
* an OIDC provider for `my-application` named `my-application-oidc-provider`
* the OIDC application connected to the OIDC provider `my-application-oidc-provider`

This will happen as soon Authntik is booted


## Check

visit http://172.25.0.12:9000 to check if Authentik is running
You can login with:
`akadmin`:`iamastupidtest` for admin access
`devuser`:`password123` for a normal user access

Check if the user and application/provider for `my-application` exists

## Use in Client App

Use the OIDC discovery endpoint http://172.25.0.12:9000/application/o/my-application/.well-known/openid-configuration
and the `client_id`:`FfgBVFx2H11q8Dz6HDmh8ASIuqolKZd7q7IUsZn2`
and the `client_secret`: `m5WZWMZjZBUCgHTI9puGhIJjebY3iDkMNf4qfd7yrV77NgtbVzKpJWlU32DITbBMgmTxbdOShZAPrH9sjvO71RPZMOOlxCr5C3IAiYMdyKsqV4dapX3bkO23gqNqT1sY`
to connect an example application to the OICD provider
