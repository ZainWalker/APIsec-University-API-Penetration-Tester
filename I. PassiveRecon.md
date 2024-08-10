# Passive API Reconnaissance:

### Google Dorking:

- intitle:"api" site:"coinbase.com"
- inurl:"/api/v1" site:"microsoft.com"
- intitle:json site:ebay.com

### Git Dorking:

go to GitHub and search:

- "coinbase api key" and see what comes up. This can be used to look for issues with that api too. 
- "api key exposed"
- extension:json nasa
- shodan_api_key - if you know the api key name you can directly search
- "authorization: Bearer" - one of the most common headers for api authorization
- filename:swagger.json - often the default swagger name

### Shodan

`shodan.io`

- coinbase port:443
- "content-type: application/json" - often used with apis, if paired with target name we could find an api related to the target
- "wp-json" - wordpress api for if target uses wordpress

### WaybackMachine

`archive.org/web/`

- search for an associated url, like reddit api docs
- can search for exact url to see history of it
- can access one of the snapshots to look for things like endpoints that used to exist
- we can also use this to test previously seen apis the website has used