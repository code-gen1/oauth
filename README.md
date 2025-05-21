PKCE Flow
1- Login Initialization

The user clicks the login button. In the background, the app generates a long random string called the code_verifier. This is like a secret password that only the app knows. Then, the app makes a scrambled version of this, called the code_challenge

2- Login to the Identity Provider

The application now reroutes the user to IDP’s login page (This could be OneLogin or Okta). The user enters their username and password to log in to IDP.

Login to Identity Provider
3- Credential Verification

Upon successful verification, the identity provider acknowledges the code_challenge provided by the application earlier.

4- Return with Authorization Code

The user is then redirected back to the originating application. During this phase, the identity provider hands the application a special ‘authorization code’, a crucial component of this secure flow.

5- Code Exchange at the IDP Server

The application communicates with the identity provider’s server, presenting the ‘authorization code’ alongside the initially generated code_verifier. The IDP server validates whether the code_verifier, when processed, matches the code_challenge received initially.


6- Access Token Procurement

Upon successful validation, the IDP server issues tokens to the application. This often includes an access token, which grants the user access. Depending on IDP settings, it might also provide an ID token, which the application can use to identify which user has logged in, and a refresh token, which can be used to obtain a new access token once the original has expired or been revoked.


7- Token Verification

Importantly, the integrity of this access token can be independently verified by the application’s server, ensuring its authenticity. The commendable aspect of the PKCE method lies in its ability to authenticate securely without the application storing any sensitive client secrets, bolstering overall security.