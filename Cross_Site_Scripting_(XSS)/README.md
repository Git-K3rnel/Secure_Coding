# Overview

### What to review

- Untrusted data is not transmitted in the same HTTP responses as HTML or JavaScript
- When data is transmitted from the server to the client, untrusted data must be properly encoded and the HTTP response
- When introduced into the DOM, untrusted data MUST be introduced using one of the following APIs:
    - Node.textContent
    - document.createTextNode
    - Element.setAttribute (second parameter only)

```text
HTML tags (such as <img src…>, <iframe…>, <bgsound src…> etc.) can be used to transmit malicious JavaScript.
```

### Attribute Encoding

- Escape all characters with ASCII values less than 256 with the &#xHH; format (or a named entity if available) to prevent switching out of the attribute
