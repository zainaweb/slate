# Errors

<aside class="notice">
 The tables below contains a breakdown of all status codes returned from the API.
</aside>

The Sate API uses the following error codes:


Error Code | Meaning
---------- | -------
200	| Success -- Your request was processed.
400 | Bad Request -- Your request is invalid.
401 | Unauthorized -- Your API key is wrong.
403 | Forbidden -- You do not have access to acces this API endpoint.
404 | Not Found -- The specified application could not be found.
405 | Method Not Allowed -- You tried to access a application with an invalid method.
406 | Not Acceptable -- You requested a format that isn't json.
410 | Gone -- The application requested has been removed from our servers.
418 | I'm a teapot.
429 | Too Many Requests -- You're requesting too many applications! Slow down!
500 | Internal Server Error -- We had a problem with our server. Try again later.
503 | Service Unavailable -- We're temporarily offline for maintenance. Please try again later.
