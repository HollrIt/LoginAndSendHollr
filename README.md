# LoginAndSendHollr
##Use the HollrIt API to login user and send a Hollr.

This sample HTML form demonstrates how to use the HollrIt API to:
* authenticate a user
* send a Hollr to a tag with credentials

###The HTML form uses these HollrIt endpoints:

####Get userId and mobileServiceAuthenticationToken for a user
POST https://hollrit.azurewebsites.net/api/User  
returns: {userId:"authenticated userId","mobileServiceAuthenticationToken":"auth token good for long term, repeated use"}

*Sample (replace userId and mobileServiceAuthenticationToken with real ones)*

```
POST https://hollrit.azurewebsites.net/api/User HTTP/1.1
Host:hollrit.azurewebsites.net
Accept: application/json
User-Agent: HollrIt
Content-Type: application/json
{ username : 'billy', password : 'secret' }
```


####Send a Hollr for given user
POST https://hollrit.azurewebsites.net/api/Hollr\s\s
Optinal params CallbackUrl and CallbackPayload for webhook callback. Payload is optional and must be JSON. The callback must accept a POST and application/json.\s\s
returns: Tag and http 201 if message created and sent successfully.


*Sample POST (replace userId and mobileServiceAuthenticationToken with real ones)*
```
POST https://hollrit.azurewebsites.net/api/Hollr HTTP/1.1
Host: hollrit.azurewebsites.net
Accept: application/json
User-Agent: HollrIt
Content-Type: application/json
Content-Length: 419

{
currentUser: {userId:"TheUserId",mobileServiceAuthenticationToken:"TheAuthToken"},
tag: 'myTag', text: 'Hello cool people!'
 }
```
