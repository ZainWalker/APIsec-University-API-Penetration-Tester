# Server Side Request Forgery

Server-Side Request Forgery (SSRF) is an API vulnerability where an attacker tricks the server into making unauthorized requests to internal or external resources, potentially accessing sensitive information or performing unintended actions. This can lead to data exfiltration, service disruption, or further attacks within the internal network.

- check API response and see if they have URLs
- capture that response and send it to Burp Intruder from repeater
- Highlight the URL and add squiggly s thing
- update the payloads to a variation:
  - http://127.0.0.1
  - http://localhost:80
  - https://webhook.site....
- Disable URL encode
- Start attack
- in our example, a request came back with new parameters we had not seen.
