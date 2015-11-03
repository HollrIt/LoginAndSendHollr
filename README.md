# LoginAndSendHollr
Use the HollrIt API to login user and send a Hollr.

This sample HTML form demonstrates how to use the HollrIt API to:
1. authenticate a user
2. send a Hollr to a tag with credentials

HollrIt endpoints:


*Get userId and mobileServiceAuthenticationToken for a user*

```
POST https://hollrit.azurewebsites.net/api/User<br/>
{ username : 'username', password : 'password' }<br/>
returns:
{userId:"authenticated userId","mobileServiceAuthenticationToken":"auth token good for long term, repeated use"}
```

*Sample (replace userId and mobileServiceAuthenticationToken with real ones)*

```
POST https://hollrit.azurewebsites.net/api/User HTTP/1.1
Host:hollrit.azurewebsites.net
Accept: application/json
User-Agent: HollrIt
Content-Type: application/json
{ username : 'billy', password : 'secret' }
```


Send a Hollr for given user

```
POST https://hollrit.azurewebsites.net/api/Hollr<br/>
{currentUser: {userId:"TheUserId",mobileServiceAuthenticationToken:"TheAuthToken"},
tag: 'myTag', text: 'Hello cool people!'
 }
 ```
 returns:
Tag and http 201 if message created and sent successfully.


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
