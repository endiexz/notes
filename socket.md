# socket

## c++ socket

int socket(int ==family==, int ==type== int ==protocol==)
family:

1. AF_INET	IPV4
2. AF_INET6  IPV6
3. AF_LOCAL   Unix域协议
4. AF_ROUTE   路由套接字
5. AF_KEY      密钥套接字

type:

1. SCOK_STREAM    字节流套接字
2. SOCK_DGRAM      数据报套接字
3. SOCK_SEQPACKET   有序分组套接字
4. SOCK_RAW      原始套接字

protocol:

1. IPPROTO_TCP    TCP传输
2. IPPROTO_UDP  UDP传输
3. IPPROTO_SCTP   SCTP传输

once sucess, the socket function returns a small non-negative value, similar to a file descriptor.  We call this a socket discriptor, sockfd. 
in other world if error it while return a value that less than zero

## bind

``int bind(int sockfd, const struct sockaddr *myaddr, socklen_t addr_len) ``

the bind function assigns a local protocol address to a socket, With the internet protocols,    the protocol address is the combination of either a 32-bit IPv4 address or a 128-bit IPv6 address,  along with a 16-bit TCP or UDP port number.

==the bind function has nothing to do with names.==

we can use ==socaddr_in== to specify the secont parameter.

```c++
//usually us at IPv4
struct sockaddr_in {
	short	sin_family;
	u_short	sin_port;
	struct in_addr	sin_addr;
	char	sin_zero[8];
};
//Generic socket address structure
struct sockaddr {
	u_short	sa_family;
	char	sa_data[14];
};
```



## listen

The listen function is called only by TCP server and it perform two actions.



## TCP粘包问题

### 粘包的主要原因：

- 发送方每次写入数据 < 套接字（Socket）缓冲区大小；
- 接收方读取套接字（Socket）缓冲区数据不够及时。