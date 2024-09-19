# enroll from a token file

Download and Copy token fro Web UI


Create file for clients and enroll
Add the token to JWT file and the JSON file is what ever name you want it to be. 
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


