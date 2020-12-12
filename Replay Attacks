HTTPS is not replayable, the first server response in the handshake sequence includes a server-chosen random number.

What Fiddler does is act as a proxy, meaning it intercepts your browser's requests, and then generates an identical request to the server, meaning it has access to the plaintext, which is what it will be replaying. Your browser lets you know this by telling you the certificate is from Fiddler - "DO_NOT_TRUST_FiddlerRoot", which you have to agree to before it will send the message ignoring the certificate mismatch.
