OAuth is used for accessing APIs. 

OAuth is driven by the need that a third-party application (for example, Facebook) needs access to another application (for example, Gmail), without the users sharing the password, in this case sharing Gmail password with Facebook.

The API server and the authorization server are separate. 

OAuth is behind TV auth too.

SSO is where OAuth shines.

## Old ways
user name + password in exchange for session cookie.
Giving a third party app your password, risking them storing the password, instead of just storing the session cookie and forget about the password.
And the only sure way to revoke the third-party apps' access to your account. You will have to change your password. 


## Mechanism
Every application sends the user to the OAuth server, and the OAuth server redirects the user back to the application server once the user is authenticated, and the application server gets a access token.

OAuth doesn't hold user ID info, that is added via [[OpenID Connect]].


- What is a bearer token? 
- why are many websites sending 2FA these days?