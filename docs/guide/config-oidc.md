# OIDC

Nginx UI can delegate authentication to any OpenID Connect (OIDC) provider. Configure the `oidc` section in your `app.ini` (or via environment variables) to enable it.

> Users must already exist in Nginx UI. After a successful OIDC login, the claim value is matched to an existing username; new accounts are not auto-provisioned.

## Endpoint
- Type: `string`

The issuer URL of your OIDC provider (for example, `https://accounts.example.com/realms/main`).

## ClientId
- Type: `string`

The client identifier registered for Nginx UI in your OIDC provider.

## ClientSecret
- Type: `string`

The client secret generated for the same client.

## RedirectUri
- Type: `string`

The callback URL configured in your OIDC provider. It must exactly match the redirect URI registered for the client.

## Scopes
- Type: `string`
- Default: `openid profile email`

Space-separated scopes requested during authorization. Leave empty to use the default scopes above.

## Identifier
- Type: `string`

Optional claim key to extract the username. If unset, Nginx UI falls back to `email`, then `name`, then `sub`.

## Example

```ini
[oidc]
Endpoint     = https://accounts.example.com/realms/main
ClientId     = nginx-ui
ClientSecret = your-client-secret
RedirectUri  = https://nginx-ui.example.com/#/login
Scopes       = openid profile email
Identifier   = preferred_username
```
