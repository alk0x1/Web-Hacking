<img src="./imgs/oauth.jpg" />

<h2>What is OAuth?</h2>

<<<<<<< HEAD
<p>OAuth is a commonly used authorization framework that enables websites and web applications to request limited access to user's
account on another application. Crucially, OAuth allows the user to grant this access without exposing their login credentials to the
requesting application. This means users can fine-tune which data they want to share rather than having to hand over full control of
their account to a third party</p>


<h2>How do OAuth authentication vulnerabilities arise?</h2>

OAuth authentication vulnerabilities arise partly because the OAuth specification is relatively vague and flexible by design. Although there are a handful of mandatory components required for the basic functionality of each grant type, the vast majority of the implementation is completely optional. This includes many configuration settings that are necessary for keeping users' data secure. In short, there's plenty of opportunity for bad practice to creep in.

One of the other key issues with OAuth is the general lack of built-in security features. The security relies almost entirely on developers using the right combination of configuration options and implementing their own additional security measures on top, such as robust input validation. As you've probably gathered, there's a lot to take in and this is quite easy to get wrong if you're inexperienced with OAuth.

Depending on the grant type, highly sensitive data is also sent via the browser, which presents various opportunities for an attacker to intercept it.

<h2> Identifying OAuth authentication</h2>

Recognizing when an application is using OAuth authentication is relatively straightforward. If you see an option to log in using your account from a different website, this is a strong indication that OAuth is being used.

The most reliable way to identify OAuth authentication is to proxy your traffic through Burp and check the corresponding HTTP messages when you use this login option. Regardless of which OAuth grant type is being used, the first request of the flow will always be a request to the /authorization endpoint containing a number of query parameters that are used specifically for OAuth. In particular, keep an eye out for the client_id, redirect_uri, and response_type parameters. For example, an authorization request will usually look something like this:

<i>GET /authorization?client_id=12345&redirect_uri=https://client-app.com/callback&response_type=token&scope=openid%20profile&state=ae13d489bd00e3c24 HTTP/1.1
Host: oauth-authorization-server. com</i>

<h2>Recon</h2>

Doing some basic recon of the OAuth service being used can point you in the right direction when it comes to identifying vulnerabilities.

It goes without saying that you should study the various HTTP interactions that make up the OAuth flow - we'll go over some specific things to look out for later. If an external OAuth service is used, you should be able to identify the specific provider from the hostname to which the authorization request is sent. As these services provide a public API, there is often detailed documentation available that should tell you all kinds of useful information, such as the exact names of the endpoints and which configuration options are being used.

Once you know the hostname of the authorization server, you should always try sending a GET request to the following standard endpoints:

<li>/.well-known/oauth-authorization-server</li>
<li>/.well-known/openid-configuration</li><br/>

These will often return a JSON configuration file containing key information, such as details of additional features that may be supported. This will sometimes tip you off about a wider attack surface and supported features that may not be mentioned in the documentation.
=======
<p>
  OAuth is a commonly used authorization framework that enables websites and web applications to request limited access to user's
  account on another application. Crucially, OAuth allows the user to grant this access without exposing their login credentials to the
  requesting application. This means users can fine-tune which data they want to share rather than having to hand over full control of
  their account to a third party
</p>
<p>
  The basic OAuth process is widely used to integrate third-party functionality that requires access to certain data from a user's account. For example, an application might use     OAuth to request access to your email contacts list so that it can suggest people to connect with. However, the same mechanism is also used to provide third-party authentication   services, allowing users to log in with an account that they have with a different website.
</p>
>>>>>>> 5b4c859403b470e58ca6c5906b03edb6934b9e1d
