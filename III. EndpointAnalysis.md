# Endpoint Analysis

### Reverse Engineering an API

- Open postman
- access your workspace > create fresh collection
- capture request button
- enable proxy > port 5555
- make sure we are saving the requests to the correct collection
- enable foxyproxy on browser setting it to 5555
- go through website to capture requests
- organize requests into folders
- analyse requests by sending them and viewing the body

### Man-in-the-middle proxy to Swagger

- run command: mitmweb
- proxy traffic to 8080 using foxyproxy
- go to the target webpage and perform various actions to capture and maximize attack surface
- go back to mitmproxy and save it 
- console: mitmwebsudo mitmproxy2swagger -i ~/Downloads/flows -o spec.yml -p http://crapi.apisec.ai -f flow
- sudo nano spec.yml
- remove "ignore" from anything that looks like it could be an api endpoint
- can rename title
- run: mitmwebsudo mitmproxy2swagger -i ~/Downloads/flows -o spec.yml -p http://crapi.apisec.ai -f flow --examples
- firefox: editor.swagger.io
- import the file - spec.yml in this case
- can also import as a new collection in postman
