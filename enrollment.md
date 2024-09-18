# enroll from a token file
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
