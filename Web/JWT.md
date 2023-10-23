# JWT
Completely new to me, Leart a lot about JWT webtoken and the weaknesses
## Category
**Web**
## Points 
**300**
## Challange Description
> authenticate as user_id 0 to get the flag

>NOTE: read up on "JWT" if you have no idea what's going on
## Attached File/Website
[http://ctf.d4rkc0de.iiitd.edu.in:8900/](http://ctf.d4rkc0de.iiitd.edu.in:8900/)
## Explanation
When we open the website we see the page 

![Initial](https://github.com/Celerium-Ce/Recruitment-CTF-sol/blob/main/Web/Imgs/JWT%20before%20heck.png)

Since its related to JWT i start by checking the cookies and correctly enough i see one for JWT

![Cookie4u](https://github.com/Celerium-Ce/Recruitment-CTF-sol/blob/main/Web/Imgs/JWT%20Cookies%20check.png)

Now that I have the cookie, I put it in the [jwt.io](https://jwt.io/) and see what info it contains 

```js
{
  "typ": "JWT",
  "alg": "HS256"
}

{
  "user_id": -1
}
```

![JWTWOW](https://github.com/Celerium-Ce/Recruitment-CTF-sol/blob/main/Web/Imgs/JWT%20token%20breakdown.png)

Seeing that we have `user_id": -1` the obvious step was to change it to 0 and put the token and login as admin. But after trying it out we get an error 

![JWTSAD](https://github.com/Celerium-Ce/Recruitment-CTF-sol/blob/main/Web/Imgs/JWT%20token%20trying%20to%20change%20to%200.png)

The error `Invalid Signature` we are getting is due to us just editing the value of user id. Signature in jwt token exist  to verify the very hack we tried to use. That is changing information in between , 
but it checks that its not coming from the right source and hence we get the error. The algo we have is the thing which changes the jwt token to encrypt it. So by using `algo none` we enter the info without having the encryption key.

Sometimes website dont verify if a jwt token has signature or not and this is the weakness we are exploiting.
Here we are changing the algo type to `none`

```js
{
  "typ": "JWT",
  "alg": "none"
}

{
  "user_id": 0
}
```
![JWTCP1](https://github.com/Celerium-Ce/Recruitment-CTF-sol/blob/main/Web/Imgs/JWT%20token%20header%20edit.png)

Now we change the payload to contain user as `0`

![JWTCP2](https://github.com/Celerium-Ce/Recruitment-CTF-sol/blob/main/Web/Imgs/JWT%20token%20edit%20part%202.png)

Putting together we get `ewogICJ0eXAiOiAiSldUIiwKICAiYWxnIjogIm5vbmUiCn0.ewogICJ1c2VyX2lkIjogMAp9`

Inputting this and we see that it works it also shows a warnign message `Warning: Undefined array key 2 in /var/www/html/index.php on line 28`  most probably due to it not verifying signature

![JWTSTOLENCOOKIE](https://github.com/Celerium-Ce/Recruitment-CTF-sol/blob/main/Web/Imgs/JWT%20cracked.png)

## Flag
`d4rkc0de{n0_s1gn@tur3_r3qu1r3d}`
