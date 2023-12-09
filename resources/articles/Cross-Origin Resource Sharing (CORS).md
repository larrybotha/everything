Link: https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS

- be default, browsers have the following behaviour for scripts making http requests:
	- requests to the same origin as the script are always allowed - `same-origin` policy
	- requests to origins other than where the script was loaded are rejected, *unless* the origin's response contains the correct CORS headers
- the CORS standard allows origins to define using headers which other origins are permitted to make certain requests 
- browsers are mandated by the spec to send preflight requests for HTTP methods that have side effects, such as POST, PUT, PATCH, etc. 
- simple requests don't trigger CORS preflight requests
- `Access-Control-Allow-Origin: *` is a response header indicating that anyone may make the current request for that resource

## simple requests

A request that meets *all*of the following criteria
- is one of
	- GET
	- HEAD
	- POST
- if manually assigned headers are present, they are only in this list:
	- [`Accept`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Accept)
	- [`Accept-Language`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Accept-Language)
	- [`Content-Language`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Content-Language)
	- [`Content-Type`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Content-Type) , where the value is one of:
		- `application/x-www-form-urlencoded`
		- `multipart/form-data`
		- `text/plain`
	- [`Range`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Range)
- if the request is an `XMLHTTPRequest`, the request has no listener on the `upload` event
- a `ReadableStream` object is not used in the request
## preflight requests

If a request is not a simple request, it is a preflight request. A preflight request will contain:

- a method of type `OPTION`
- the method of the request that resulted in the preflight request
- the request headers of the request that resulted in the preflight request

The response will contain:
- the methods the the resource allows: `Access-Control-Allow-Methods`
- the matching headers that are allowed: `Access-Control-Allow-Headers`
- a restriction that the request may only come from the origin in the original request: `Access-Control-Allow-Origin`
- `Access-Control-Max-Age` specifies how long the response will be cached before a new preflight request will need to be sent

On a successful response to the preflight request, the original request is sent

## links and resources

- https://developer.mozilla.org/en-US/docs/Web/Security/Same-origin_policy
- https://developer.mozilla.org/en-US/docs/Glossary/CSRF
- https://developer.mozilla.org/en-US/docs/Web/API/ReadableStream
- https://developer.mozilla.org/en-US/docs/Web/API/Streams_API/Using_readable_streams
- https://stackoverflow.com/questions/43871637/no-access-control-allow-origin-header-is-present-on-the-requested-resource-whe#43881141