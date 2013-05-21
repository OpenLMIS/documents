# OpenLMIS API

This documentation is a technical reference intended for software developers interested in implementing the OpenLMIS APIs.

* we will uses json's for exchanging data.
* dates will comply with the ISO 8601 standard.
* fields and properties will be in java camelCase notation.
* data will use UTF-8 encoding.

# Response Codes

Responses to HTTP requests should utilize standard HTTP response codes such as 2XX for success, 401 u for unauthorized, etc.

### Success

Success differ from errors in that their body may not be a simple response object with a code and a message. The headers however are consistent across all calls:

* `GET`, `PUT`, `DELETE` returns `200 OK` on success,
* `POST ` returns `201 Created` on success,

# Error Codes

Error responses are simply returning [standard HTTP error codes](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html) along with some additional information:

* The error code is sent back as a status header,
* The body includes an object describing both the code and OPTIONALLY the message

For example, for a call with when the resource is not found:

```Status: 404 Not Found```
```{
    code: 404 Not Found,
    message: 'Resource not found'
}```

# Authentication

Authentication is handled by [HTTP Basic Authentication](http://en.wikipedia.org/wiki/Basic_access_authentication).

Every API request must include a **valid authentication token** in the header.

The Authorization header is constructed as follows:

* Username and password are combined into a string "username:password"
* The resulting string literal is then encoded using Base64
* The authorization method and a space i.e. "Basic " is then put before the encoded string.

For example, if the user agent uses 'Aladdin' as the username and 'open sesame' as the password then the header is formed as follows:

`Authorization: Basic QWxhZGRpbjpvcGVuIHNlc2FtZQ==`

# Versioning

API Documentation follows [semantic versioning](http://semver.org/) 

API documentation revisions will be assigned a unique version number in the format MAJOR.MINOR.REVISION. These version numbers follow semantic versioning pattern whereby:

* REVISION is incremented for revisions to a MINOR version. These changes represent nonfunctional changes to the API.
* MINOR version numbers are incremented when new functionality is introduced which is backwards compatible with existing functionality in the MAJOR version. MINOR versions numbers are semantically compatible with previous MINOR versions.
* MAJOR version numbers are incremented when new functionality is introduced which is semantically incompatible with previous versions.

`/api/v1/facilities.json`

All prior versions still supported by the code should be exposed by its own URL.

