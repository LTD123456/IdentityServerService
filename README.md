# IdentityServerService
Receive the login request from the client through the **/connect/token** endpoint. 
The custom **ResourceOwnerPasswordValidator** will send a message via Azure Service Bus to UMS (on the **login-requests** queue) containing the login information and a **CorrelationId**. 
Then, IdentityServer waits for a response on the **login-responses** queue (based on the **CorrelationId**). 
If a successful authentication response is received from UMS, IdentityServer issues a token with the corresponding claims.
