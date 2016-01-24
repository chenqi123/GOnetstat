# GOnetstat
## add by chenqi123
netstat function adjustment:
To summarize the server connection and client connections
##
the output likes:
# ./cqnetstat | grep -i server
server: 10.78.199.11:8100 [10.78.199.11]
server: 10.78.199.11:8102 [10.78.160.5]
server: 10.78.199.11:8103 [10.78.160.5]
server: 10.78.199.11:8001 [10.78.160.5 10.78.199.11]
server: 10.78.199.11:41483 [223.202.6.26 10.78.160.36]
server: 10.78.199.11:8002 [10.78.160.5 10.78.199.11]
server: 10.78.199.11:8101 [10.78.160.5]
server: 10.78.199.11:49298 [10.78.199.63 10.78.199.11]
server: 10.78.199.11:22 [10.78.199.11 10.73.150.124 10.78.199.39 10.70.15.118]
server: 10.78.199.11:8000 [10.78.199.11]
server: 10.78.199.11:8104 [10.78.160.5]

# ./cqnetstat | grep -i client
client: 10.78.199.11 10.78.160.38:80
client: 10.78.199.11 10.78.199.24:22
client: 10.78.199.11 10.78.199.39:22
client: 10.78.199.11 10.78.160.43:8881
client: 10.78.199.11 10.78.160.6:8000
client: 10.78.199.11 10.78.236.104:22
client: 10.78.199.11 10.78.199.65:22
client: 10.78.199.11 10.70.195.216:514
client: 10.78.199.11 10.78.236.103:22
client: 10.78.199.11 10.78.199.8:22
client: 10.78.199.11 10.78.199.6:22
client: 10.78.199.11 10.78.199.21:22
client: 10.78.199.11 10.78.160.36:10000
client: 10.78.199.11 10.78.160.13:8410
client: 10.78.199.11 10.78.160.25:7500
client: 10.78.199.11 10.78.199.11:8002






Netstat implementation in Golang.

This Package get data from /proc/net/tcp|6 and /proc/net/udp|6 and parse
/proc/[0-9]*/fd/[0-9]* to match the correct inode.

## Usage

<b>TCP/UDP</b>
```go
tcp_data := GOnetstat.Tcp()
udp_data := GOnetstat.Udp()
```

This will return a array of a Process struct like this

```go
type Process struct {
    User         string
    Name         string
    Pid          string
    Exe          string
    State        string
    Ip           string
    Port         int64
    ForeignIp    string
    ForeignPort  int64
}
```
So you can loop through data output and format the output of your program
in whatever way you want it.
See the Examples folder!

<b>TCP6/UDP6</b>
```go
tcp6_data := GOnetstat.Tcp6()
udp6_data := GOnetstat.Udp6()
```
The return will be a array of a Process struct like mentioned above.
Still need to create a way to compress the ipv6 because is too long.
