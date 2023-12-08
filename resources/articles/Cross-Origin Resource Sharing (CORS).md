Link: https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS

- be default, browsers have the following behaviour for scripts making http requests:
	- requests to the same origin as the script are always allowed - `same-origin` policy
	- requests to origins other than where the script was loaded are rejected, *unless* the origin's response contains the correct CORS headers
- the CORS standard allows origins to define using headers which other origins are permitted to make certain requests 
- browsers are mandated by the spec to send preflight requests for HTTP methods that have side effects, such as POST, PUT, PATCH, etc. 

## links and resources

- https://developer.mozilla.org/en-US/docs/Web/Security/Same-origin_policy
- https://developer.mozilla.org/en-US/docs/Glossary/CSRF