# Configuring a service

Create an identity for the HTTP client and assign an attribute "http-clients". 

Create an identity for the HTTP server if you are not using an edge-router with the tunneling option enabled 

Create an intercept.v1 config.  This config is used instruct the client-side tunneler 

Create a host.v1 config. This config is used instruct the server-side tunneler

Create a service to associate the two configs created previously into a service.

Create a service-policy to authorize "HTTP Clients" to "dial" the service representing the HTTP server.

Create a service-policy to authorize the "HTTP Server" to "bind" the service representing the HTTP server.

Start the server-side tunneler  with the HTTP server identity

Start the client-side tunneler using the HTTP client identity.

Access the HTTP server securely over the OpenZiti zero trust overlay
