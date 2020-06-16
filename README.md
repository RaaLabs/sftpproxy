# sftpproxy

http -> sftp proxy

To be used to serve the Clear Linux mix server repository over ssh to avoid problems with http over satellite links.

Will start a local http listener, and forward any http calls as sftp to the server specified.

Set the swupd mirror to `swupd mirror --set http://localhost:7777`, or to the values you specified when starting the server if default values where not used.

To compile an executable binary of the package:

```bash
env GOOS=linux GOARCH=amd64 go build -ldflags="-s -w" -o sftp && upx --brute sftp
```

flags to use

```text
 -listenPort string
        enter the host and port for the server to listen on (default "localhost:7777")
  -sftpAuth string
        choose between password or pem, defaults to password (default "password")
  -sftpIP string
        ip address or hostname of the sftp server (default "51.120.77.187")
  -sftpPass string
        password to authenticate to sftp server, will default to key if no password is given
  -sftpRootPath string
        specify the directory that will be served as the root path on the sftp server (default "/www")
  -sftpUser string
        ssh/sftp server username (default "webreporeader")
  -tempFileFolder string
        If needed, specify where to store tmp files. All files are automatically deleted (default "./")
  -version
        Show the current version (default true)
```
