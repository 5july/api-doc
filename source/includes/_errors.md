# Errors

<aside class="notice">
Integrity API uses standard HTTP status code when returning errors. Additionally, we provide details about errors in the body of the response in the following format
</aside>
<pre class="center-column">
{
  "error": {
    "error_code": %Errorcode%, 
    "error_name": "%errorName%", 
    "http_code": %httperrorcode%, 
    "innerError": {
      %additional json data about the error%
    }, 
    "message": "%description of the error%"
  }
}

</pre>

The integrity.st API uses the following error codes:


Error Code | Meaning
---------- | -------
400 | Bad Request -- Your request is invalid.
401 | Unauthorized -- Your API key is wrong.
403 | Forbidden -- Forbidden request
404 | Not Found -- The specified API request could not be found.
405 | Method Not Allowed -- You tried to access a method with an invalid method.
406 | Not Acceptable -- You requested a format that isn't json.
410 | Gone -- The url requested has been removed from our servers.
418 | I'm a teapot.
422 | Unprocessable Entity -- Unable to process the contained instructions
429 | Too Many Requests -- The user has sent too many requests in a given amount of time
500 | Internal Server Error -- We had a problem with our server. Try again later.
503 | Service Unavailable -- We're temporarily offline for maintenance. Please try again later.
