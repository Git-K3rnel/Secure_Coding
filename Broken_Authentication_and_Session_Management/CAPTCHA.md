# CAPTCHA

CAPTCHA is used to prevent automated software from gaining access to webmail services

**General considerations**

- Do not allow the user to enter multiple guesses after an incorrect attempt
- Consider using a key being passed to the server that uses a HMAC (Hash-based message authentication code) the answer
- Randomize the CAPTCHA length
- Don’t use a complex charset
- Use anti-recognition techniques as a means of strengthening CAPTCHA security: Rotation, scaling and rotating some characters and using various
