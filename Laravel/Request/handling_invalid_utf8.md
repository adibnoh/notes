# Handling invalid utf8

An URL with an invalid UTF-8 parameter would be one where a parameter in the URL's query string contains a character that is not valid UTF-8 encoding.

Here is an example of an URL with an invalid UTF-8 parameter:

`http://www.example.com/search?q=invalid%C3%28UTF%29`

In this example, the %C3%28 and %29 sequences in the query string parameter q are not valid UTF-8 characters, and therefore, the entire parameter is considered invalid UTF-8. When processing URLs with query string parameters, it's important to ensure that all parameters are valid UTF-8 to avoid potential security or compatibility issues.

Laravel validation may allow utf8 to slip in, this may cause unexpected error when we parsing json or when we're running SQL. To avoid this bug we may fix encoding with this plugin:

`https://doc.nette.org/en/utils/strings#toc-fixencoding`