# JSON

- JSON main security concern is JSON text dynamically embedded in JavaScript
- The code reviewer needs to make sure the JSON is not used with Javascript eval. Make sure JSON.parse(…) is used

```jsx
Var parsed_object = eval(“(“ + Jason_text + “)”); // Red flag for the code reviewer.
JSON.parse(text[, reviver]); .. // Much better then using javascript eval function.
```

- Code reviewer should check to make sure the developer is not attempting to reject known bad patterns in text/string data, Using regex
    - Allow only whitelisted alphanumeric keywords and carefully validated numbers
- Do not allow JSON data to construct dynamic HTML. Always us safe DOM features like innerText or CreateTextNode(…)
