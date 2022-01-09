# OpenId


## Why we need OpenId

The current application landscape is heavily dominated by API based micro services. These APIs are not always internal or live in the same domain so the cookie based authentication is not useful. The other approach could be sending username password along with each call which is also not that secure.


## Token based security 

The basic idea of a token based security is that the client will send a token which indicates consent by the provider to allow the token creator access to the API as long as the request is coming with the token.

The next question was how these tokens will be generated. The most common option that came up was to write home grown token endpoints which the consumers will call and exchange their username and password for a token. This is an improvement but still has the following concerns

- We still have to share user name and password.
- When we create these endpoints we have to implement the following concepts on our own and maintain internally.
    - Token Expiration.
    - Token signing and validation.
    - We have to think about Token Format.
    - We need to determine how to handle Authentication and Authorization and how to separate them.
    - We have to find a way to securely. 

We have two issues to solve

- Define central location for token related task.
- Keep things safe enough to store them.

The IDP ( identity providers) are responsible for the following

- Centralizing the identity related task.
- Storing them in a secure way.
- Provide multiple ways of access for the users.

### Oauth 2 

It is an authorization protocol. In this protocol a token provider is used to provide the client application with an authorization token which can be used to access APIs and other resources.

### OpenId Connect

It is an extension to oauth where the client application gets an identity token next to an access token.

There will be an additional endpoint to get the user information. It is called teh user info endpoint.