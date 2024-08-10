# Active API Reconnaissance

starting with crapi
sudo docker-compose start - opens our target
firefox > 127.0.0.1:8888/login - checks status of target

### nmap

beginning info gathering

- nmap -sC -sV 127.0.0.1 - what services are being run on the target
- nmap -p- 127.0.0.1 - what else is our target running
- nmap -sV 127.0.0.1 -p 8025 - service enumeration
- visit the observed service if possible and explore

### amass

command line tool that can map a target's external network by collecting OSINT from multiple sources

- amass - starts tool
- amass enum -list - sees which services you can connect to the tool. creating accounts, getting api keys from the accounts and pluggin them into amass
- amass enum -active -d crapi.apisec.ai - beginning info gathering. can pipe "api" into command for better results.
- amass enum -active -d microsoft.com | grep api
- look for things like sandbox, testing, uat
- explore notable findings with a browser to gain more info


### gobuster

directory enumeration

- gobuster dir -u http://127.0.0.1:8888 -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt - if this is not returning, can also add -b 200 to filter out 200 responses
- if any of the returned directories seem interesting we can look into them and the command would look something like this:
  - gobuster dir -u http://127.0.0.1:8888/identity -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -b 401

### devtools

- can hit f12 or right-click inspect, analyze the network tab
- create a test account and login, look through site
- right click and add URL to our view in network portion of inspect
- after finding an api, select the request and analyze: authorization bearer and content type are of interest
- we can also copy the request as a cURL to analyze in postman

### postman

- we can import an api request from cURL in the raw text import section
- 