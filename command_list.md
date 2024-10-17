Login
```
ziti edge login ziti.hungry-howard.com:8441
```

```
ziti edge list edge-routers
```
```
ziti edge list identities
```
```
ziti edge list configs
```
```
ziti edge list services
```
```
ziti edge list service-policies
```
##  Using the Tunnel run command for client HTTP

On th eZiti instance  when creating the http-clients and http-sevrer  enrollment  copy them over to the remote client

On the client runn
```
ziti-edge-tunnel run --identity http-server.json
```

On Zitit server run the following command
```
ziti-edge-tunnel run --identity http-clients.json
```
