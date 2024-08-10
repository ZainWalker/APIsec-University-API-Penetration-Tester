# Testing for Improper Asset Management

- Check the headers, URL path, and paramenters for potential versions of APIs

- in postman, can click "run collection" to begin testing
- to put code snippets in for viewing API responses such as 200: Click the collection > Edit > Tests
- Then Run Collection

- When testing for improper asset management, we want to test both as an authorized user and an unauthorized user.

#### Setting up the test

- when testing other versions of an API, can click find and replace in Postman to change version:
  - Add a new environment, called anything "test environment" for example
  - add variable: ver
  - initial value: v1
  - save
  - ensure that test environment is then selected
  - Click find a replace
  - Click the spectific collection we are testing
  - find "v2"
  - Replace with: {{ver}}
  - Check select all box, then replace
  - repeat these steps for v3.
  - run the collection again and analyze results
  - click on any responses that looks of interest and can get the request URL if wanted
  - cross reference the responses between the current version and the previous version
- In our example, we were able to see a previous version of an API that allowed us to send an infinite number of requests for guessing a password

- Can use comparer in burp suite to easily compare requests