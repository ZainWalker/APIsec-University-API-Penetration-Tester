# Evasion and Combining Techniques

- string terminators can be used to bypass input validation, encoding, or filtering mechanisms by prematurely ending a string or data input. Examples:
  - %00
  - 0x00
  - //
  - ;
  - %
  - !
  - ?
  - []
  - %5B%5D
  - %09
  - %0a
  - %0b
  - %0c
  - %0e

- Case switching: switch the case of an api to bypass rate limiting. Examples:
  - POST /api/myProfile
  - POST /api/MyProfile

- Encoding payloads - WAF-bypassing. use an URL Encoded payload. Example:
  - URL Encoded Payload: %27%20%4f%52%20%31%3d%31%3b
  - API Provider URL Decoder: ' OR 1=1;


  - We can adjust payloads to perform the tasks mentioned above, we can do it manually, we can also use Burpsuite Intruder.
    - Payload Processing:
      - If we know setting a null byte before a payload would be advantageous, we can add a prefix, then add it.
      - We also have the option of encoding.

- wfuzz has similar options for evasion as well.
  - $ wfuzz -z list,a-b-c,base64@base64@md5@ -u http://target.com/api/v2/FUZZ