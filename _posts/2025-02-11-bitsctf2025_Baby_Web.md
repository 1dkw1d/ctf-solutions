---
title: "bitsctf2025_baby_web"
date: 2025-02-11
---
<img width="357" alt="image" src="https://github.com/user-attachments/assets/5548ddb2-89ea-4dd5-83e4-29ccbcc17db6" />

Alright, so the website's title is "JWT Auth Demo," and this is our first hint at what will be happening on this login page.

<img width="133" alt="image" src="https://github.com/user-attachments/assets/4125e31c-76aa-4261-8eb5-454f9f183141" />

The actual website page allows users to enter a username to log in and provides a JWT "Json Web Token" token to the user that is stored in local storage
this allows users to modify their own token and authenticate themselves. After login in as "admin" this is what the website looks like
<img width="458" alt="image" src="https://github.com/user-attachments/assets/824b1cba-f0fb-4b49-9932-f2e0ac021855" />



The token is seen here and agian can also be found in the local storage of the website. Seeing this I plugged the token into token.dev to see that it used RS256 for encryption. 

{
  "typ": "JWT",
  "alg": "RS256"
}
---
After swapping the encryption to HS256 I was able to use the public key from the **RS256** encryption fed it into the **HS256** secret key to bypass the authentication and retrive the flag: **BITSCTF{jwt_k3y_c0nfus10n_ma5tery}**
