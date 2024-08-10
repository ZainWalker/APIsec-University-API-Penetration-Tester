# Injection Attacks

Injection attacks in the scope of APIs occur when malicious code or commands are sent through API inputs, manipulating the backend system to execute unintended actions. These attacks can lead to data breaches, unauthorized operations, or system compromise by exploiting vulnerabilities like SQL, command, or script injections.

---

- We'll want to place fuzzing variables using Postman
  - in your "test environment" create variables called fuzz, fuzz1, fuzz2, fuzz3 and pass the following to both initial value and current value:
    - fuzz: ||whoami 
      - os injection
    - fuzz1: -- -
    - fuzz2: 'OR 1 -- -
    - fuzz3:  $gt -
      - nosql injection
  - once that is all set, go to the requests we will be testing, type {{fuzz}} in place of the variables you want to fuzz
  - such as the right side of the "password" key value pair for the login post request
- once done, run collection
- Whatever we find of interest, we will analyze in burpsuite repeater and then intruder to use payloads for testing
- we can then use wfuzz to find potential payloads, and we can user something like a nosqli wordlist on the target API
