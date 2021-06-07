### Socket实现

```
#include <sys/socket.h>

int socket(int domain, int type, int protocol);
	Returns file description on success, or -1 on error

domain: ＳＯＣＫＥＴ的通信domain
type: 	SOCK_STREAM: 流ＳＯＣＫＥＴ，　SOCK_DGRAM:数据报ＳＯＣＫＥＴ
protocol: 一般指定为０，在裸ＳＯＣＫＥＴ(SOCK_RAW)中会将protocol指定为IPPROTO_RAW

LINUX内核2.6.27开始type参数允许两个非标准的标记与ｓｏｃｋｅｔ类型取ＯＲ,
	SOCK_NONBLOCK标记：内核在底层打开的文件描述符设置O_NONBLOCK标记，这样后面在该socket上发生的I/O操作将成为非阻塞，从而无需通过fcntl来取得同样的结果
```

##### bind

```
int bind(int sockfd, const struct sockaddr　*addr, socklen_t addrlen);
	Returns 0 on success, or -1 on error
	
struct sockaddr {
	sa_family_t sam_family;
	char sa_data[14];
}
```



```
int listen(int sockfd, int backlog);
	Returns 0 on success, or -1 on error
	
```



```
int accept(int sockfd, struct sockaddr &addr, socklen_t *addrlen);
	Returns 0 on success, or -1 on error
	
	
getpeername()系统调用，获取对端地址

从内核 2.6.28 开始，Linux 支持一个新的非标准系统调用 accept4()。这个系统调用执行的任
务与 accept()相同，但支持一个额外的参数 flags，而这个参数可以用来改变系统调用的行为。目
前系统支持两个标记：SOCK_CLOEXEC 和 SOCK_NONBLOCK。SOCK_CLOEXEC 标记导致
内核在调用返回的新文件描述符上启用 close-on-exec 标记（FD_CLOEXEC）。这个标记之所以有
用的原因与4.3.1节中描述的open() O_CLOEXEC标记有用的原因是一样的。SOCK_NONBLOCK
标记导致内核在底层打开着的文件描述上启用 O_NONBLOCK 标记，这样在该 socket 上发生的
后续 I/O 操作将会变成非阻塞了，从而无需通过调用 fcntl()来取得同样的结果。
```



```
int connect(int sockfd, const struct sockaddr *addr, socklen_t addrlen)
	Returns 0 on success, or -1 on error
```



##### htons, htonl, ntohs, ntohl用来在主机和网络字节序之间转换整数

```
#include <arpa/inet.h>

uint16_t htons(unit16_t host_uint16);
	Returns host_uint16 converted to network byte order
	
uint32_t htonl(uint32_t host_unit32);
	Returns host_uint32 converted to network byte order
	
uint16_t ntohs(uint16_t net_uint16);
	Returns net_uint16 converted to host byte order
	
uint32_t ntohl(uint32_t net_uint32);
	Returns net_uint32 converted to host byte order
```

##### IPV4 socket地址：　struct sockaddr_in

```
#include <netinet/in.h>
struct sockaddr_in {
}

```

