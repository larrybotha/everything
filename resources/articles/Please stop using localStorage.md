---
tags:
	- resource/article
---

Link: https://www.rdegges.com/2018/please-stop-using-local-storage/
Author: [[Randall Degges]]

- `localStorage` is accessible by any script running on a webpage - don't use it
  to store sensitive information
- JWTs contain sensitive information - a script that has access to a user's JWT
  can make requests to an application using that JWT - don't store a JWT in
  `localStorage`
- instead of `localStorage` for sensitive information:
  - create a cryptographically signed cookie when a user authenticates
  - set the appropriate cookie flags
    - `httpOnly` - see [[Jeff Atwood]]'s article on
      (Protecting your cookies)[https://blog.codinghorror.com/protecting-your-cookies-httponly/]
    - `SameSite=true` - prevent CSRF attacks
    - `secure=true` - ensure cookies are only sent over secure connections
  - get the user's details via the cookie they send on each request to ensure
    they are who they deem they are

## Links and resources

- https://stackoverflow.com/questions/43452896/authentication-jwt-usage-vs-session
- [[Stop using JWT for sessions]]
