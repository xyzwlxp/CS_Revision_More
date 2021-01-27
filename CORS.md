### Cookies

The browser only sends the cookies belong to domain that it belongs to.
So how does things like fake authentication do? It actually do something like this:
1. client server redirects towards the authentication server with the back URL.
2. the authentication server authenticates, redirect back to the pre-set URL like /addCookie, appending a parameter of TOKEN and the client server will use the TOKEN to append the cookie.

#### Case of IFrame
IFrame needs the SameSite cookie to be true in order to send the cookie of the frame domain together with the request towards the frame domain.
e.g. 
<table>
  <tr>
    <th>cookie name</th>
    <th>domain</th>
    <th>Same-Site</th>
  </tr>
  <tr>
    <td>lazada-data-gateway_SSO_TOKEN_V2</td>
    <td>test.alibaba-inc.com</td>
    <td>Lax</td>
  </tr>
</table>

this cookie will not be sent in a iframe of test.alibaba-inc.com seating at test.lazada.com.

<table>
  <tr>
    <th>cookie name</th>
    <th>domain</th>
    <th>Same-Site</th>
  </tr>
  <tr>
    <td>lazada-data-gateway_SSO_TOKEN_V2</td>
    <td>test.alibaba-inc.com</td>
    <td>None</td>
  </tr>
</table>

this cookie will be sent through.

#### Case of redirect
When a XHR took place and the response is a 302, do we do a redirect?

This actually depends on the CORS setting. If the current application (lets say we are in test.lazada.com) destination is CORS trusting the website to be redirected towards (test.alibaba-inc.com), the redirect can still pull through.
