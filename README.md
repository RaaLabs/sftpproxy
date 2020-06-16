# sftpproxy

http -> sftp proxy

To be used to serve the Clear Linux mix server repository over ssh to avoid problems with http over satellite links.

Will start a local http listener, and forward any http calls as sftp to the server specified.

Set the swupd mirror to `swupd mirror --set http://localhost:7777`, or to the values you specified when starting the server if default values where not used.

To compile an executable binary of the package:

```bash
env GOOS=linux GOARCH=amd64 go build -ldflags="-s -w" -o sftp && upx --brute sftp
```
