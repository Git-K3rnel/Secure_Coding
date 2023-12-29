# Overview

### What to review

- Untrusted data is not transmitted in the same HTTP responses as HTML or JavaScript
- When data is transmitted from the server to the client, untrusted data must be properly encoded and the HTTP response
- When introduced into the DOM, untrusted data MUST be introduced using one of the following APIs:
    - Node.textContent
    - document.createTextNode
    - Element.setAttribute (second parameter only)