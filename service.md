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

##  Enrollment

Down load the JWT token  and copy it to file in OpenZiti server
instruction found [here](https://github.com/HungryHowies/OpenZiti/blob/33cbc144359bedc7774cc79a1261ddbe6c4976a4/enrollment.md) 

 Execute the Ziti tunneler on the client side. This would be  the sever json file  from the server.
 
 ```
ziti-edge-tunnel run --identity http-server.json
```

 On the server side execute the tunneler with the client json file.
 
 ```
ziti-edge-tunnel run --identity http-clients.json
```
