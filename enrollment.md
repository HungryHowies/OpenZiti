# enroll from a token file

Download and Copy token fro Web UI

Create file for clients and enroll
```
vi http-clients.jwt
```
```
ziti-edge-tunnel enroll --jwt ./http-clients.jwt --identity ./http-clients.json
```
Create a file  for Sevrer and enroll
```
vi http-server.jwt
```
```
ziti-edge-tunnel enroll --jwt ./http-server.jwt --identity ./http-server.json
```

```
./ziti-edge-tunnel enroll --jwt ./myTunneler.jwt --identity ./myTunneler.json
```

## Get the token and place it in a file. Save  file. excute the following
```
vi nginx.jwt
```
```
ziti-edge-tunnel enroll --jwt ./nginx.jwt --identity ./nginx.json
```
