User-mode 4.4BSD-Lite2 TCP/IP Stack
===================================

User-land TCP/IP stack from 4.4BSD-Lite2, a companion of W. Richard Stevens's immortal work *TCP/IP Illustrated, Volume 2: The Implementation*, with a focus on TCP chapters.  *TCP/IP Illustrated vol.2* uses 4.4BSD-Lite as its example, a slightly early version.  TCP/IP code of 4.4BSD-Lite2 is roughly the same as FreeBSD 2.0.

This is not a fork of https://github.com/sergev/4.4BSD-Lite2, which contains the whole `4.4BSD-Lite2.tar.gz`.  This repository only contains `usr/src/sys` of the tarball, ie. the kernel source.

## How to build and play

```shell
$ make
```

This build a few executables:
* `objs/test_init`  TCP three-way handshake, you can step through code with `GDB`
* `objs/test_self`  TCP self-connection
* `objs/test_pigeon`  ICMP echo request/response
* `objs/test_tun`  Connect to host with TAP/TUN device.
    * BSD stack is attached to `tun0`, its IP address is 192.168.0.2, listens on port 1234.
    * Try `ping 192.168.0.2` or `nc 192.168.0.2 1234`, also watch the packets with `tcpdump -n -i tun0`.

This TCP/IP stack is alive, using tap/tun device on Linux. (WIP)

[Unofficial companion site of _TCP/IP Illustrated vol. 2_](http://chenshuo.github.io/tcpipv2)

## error

If the compiling host is a 64-bit operating system, the following error may occur：
```
fatal error: sys/cdefs.h: No such file or directory
```
You should install some dependency packages(https://blog.csdn.net/weixin_44498318/article/details/121282997)
```
sudo apt install gcc-multilib 
```

## See also

For running recent FreeBSD TCP/IP stack in user mode, take a look at https://github.com/pkelsey/libuinet and https://github.com/cloudius-systems/osv.
