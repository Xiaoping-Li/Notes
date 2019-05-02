1. Node.js Server & Authentication Basics: Express, Sessions, Passport, and cURL
* https://medium.com/@evangow/server-authentication-basics-express-sessions-passport-and-curl-359b7456003d


2. JWT
* https://medium.com/vandium-software/5-easy-steps-to-understanding-json-web-tokens-jwt-1164c0adfcec

3. Bcrypt Node.js
* Hashing is a one way function (well, a mapping). It's irreversible, you apply the secure hash algorithm and you cannot get the original string back. The most you can do is to generate what's called "a collision", that is, finding a different string that provides the same hash. Cryptographically secure hash algorithms are designed to prevent the occurrence of collisions. You can attack a secure hash by the use of a rainbow table, which you can counteract by applying a salt to the hash before storing it.
* Encrypting is a proper (two way) function. It's reversible, you can decrypt the mangled string to get original string if you have the key.

4. Express sessions
* Session is basically it contains clients specific data that's going to persist across requests. Think about the word `session`, let's say you have a session on a website, what that means that you are visiting this website you're performing different actions on this website and for the duration of that session the duration of the time you are on that website, you're doing things there is some state associated with your set of requests. 




