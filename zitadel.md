
I am trying to do a PoC with OpenZiti and its BrowZer feature to implement a Zero Trust proxy accessible in the browser.
OpenZiti and everything around it is implemented and seems to work, and I am using my Prod Zitadel instance.
I created a Web>Code>Private Key JWT app in an existing org, since OpenZiti wants an "External JWT Signer".

And after giving OpenZiti the ClientID for that app and accessing the URL of the app I want to publish to test via BrowZer, I get redirected to my Zitadel instance but get "{"error":"invalid_request","error_description":"The requested redirect_uri is missing in the client configuration. If you have any questions, you may contact the administrator of the application."}".

The URIs in the Zitadel app are set correctly, so I dont have any idea why I get this error.
How would I check whats wrong?


And whats the progress about this?
https://github.com/zitadel/zitadel/discussions/3161
OpenZiti recommends using the wildcard of the deployments FQDN, which I currently cant do with Zitadel.
