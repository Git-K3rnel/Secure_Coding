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

### HTML Entity

- HTML elements which contain user controlled data or data from untrusted sourced should be reviewed for contextual output encoding

Example:

```html
HTML Body Context <span>UNTRUSTED DATA</span> OR <body>...UNTRUSTED DATA </body> OR 
<div>UNTRUSTED DATA </div>
```

HTML Encoding:

```html
& --> &amp; < --> &lt; > --> &gt; “ --> &quot; ‘ --> &#x27;
```

### JavaScript Parameters

- Untrusted data, if being placed inside a JavaScript function/code requires validation
- Do not use these functions they are vulnerable even if javascript escaped! :
    - setInterval()
    - eval()
