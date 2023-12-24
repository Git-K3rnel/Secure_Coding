# Validation

- All data from users needs to be considered untrusted
- Regular expressions can be used to validate user input

**Data validations checklist for the Code Reviewer :**

- Ensure that a Data Validation mechanism is present
- Ensure all input that can (and will) be modified by a malicious user such as HTTP headers, input fields, hidden fields, drop down lists, and other web components are properly validated
- Ensure that the proper length checks on all input exist
- Ensure that all fields, cookies, http headers/bodies, and form fields are validated
- Ensure that the data is well formed and contains only known good chars if possible.
- Ensure that the data validation occurs on the server side.
- Examine where data validation occurs and if a centralized model or decentralized model is used.
- Ensure there are no backdoors in the data validation model.
- “Golden Rule: All external input, no matter what it is, will be examined and validated.
