# OpenID Connect (OIDC)

OpenID Connect (OIDC) is an identity layer built on top of OAuth 2.0, enabling applications to verify a user's identity and obtain profile information. Without OIDC the client app can check if the user is authorized or not but it does not know who the user is.

## Difference betweeen Oauth 2.0 and OpenID connect (OIDC)

To implement this, OpenID Connect includes additional features, such as:
```zsh
 - Add the ID token + the Access Token
 - The use of JWT for ID token
 - Add a new endpoint to get user info /userinfo endpoint
 - Add /.well-known/openid-configuration
```
 Using JWT standard in the ID token allow the client application to decode the user information, the client could also request more information about the user by calling the userinfo endpoint.
