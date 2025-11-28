# What Counts As Cross-Origin With CORS?

An [HTTP origin](https://developer.mozilla.org/en-US/docs/Glossary/origin) is defined by a triple of aspects of the URL: the scheme, hostname and port. This information is contained within the HTTP origin request header. This is important for understanding what qualifies as _same_ and _cross_-origin when dealing with
 [CORS](https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS) (Cross-Origin Resource Sharing).

For something to be _same-origin_, it must have the same scheme (HTTP/HTTPS), the same host, and the same port. If any one of the scheme, host (including subdomains), or port is different, then it is not _same-origin_.

With that in mind, here are some examples of different origins:

- `https://example.com` vs `http://example.com` (different scheme)
- `https://example.com` vs `https://sub.example.com` (different host)
- `https://example.com:3000` vs `https://example.com:5000` (different port)

As long as the scheme, host, and port match, they are the same origin. The path (everything following the origin) doesn't factor into the question of same origin.

In the context of the S3 rules around CORS, having cors enabled allows for client-side web apps to selectively allow for cross-origin access to other S3 resources (i.e. static html templates)