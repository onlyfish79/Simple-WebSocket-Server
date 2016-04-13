Simple-WebSocket-Server
=================

A very simple, fast, multithreaded, platform independent WebSocket (WS) and WebSocket Secure (WSS) server and client library implemented using C++11, Boost.Asio and OpenSSL. Created to be an easy way to make WebSocket endpoints in C++.

See https://github.com/eidheim/Simple-Web-Server for an easy way to make REST resources available from C++ applications. Also, feel free to check out the new C++ IDE supporting C++11/14/17: https://github.com/cppit/jucipp. 

### Features

* RFC 6455 mostly supported: text/binary frames, ping-pong, connection close with status and reason.
* Thread pool
* Platform independent
* WebSocket Secure support
* Timeouts, if any of SocketServer::timeout_request and SocketServer::timeout_idle are >0 (default: SocketServer::timeout_request=5 seconds, and SocketServer::timeout_idle=0 seconds; no timeout on idle connections)
* Simple way to add WebSocket endpoints using regex for path, and anonymous functions
* An easy to use WebSocket and WebSocket Secure client library
* C++ bindings to the following OpenSSL methods: Base64, MD5, SHA1, SHA256 and SHA512 (found in crypto.hpp)

###Usage

See ws_examples.cpp or wss_examples.cpp for example usage. 

### Dependencies

* Boost C++ libraries(使用1.55.0) 
* OpenSSL libraries

### Compile

Compile with a C++11 supported compiler:

```sh
cmake .
make
```

#### Run server and client examples

### WS

```sh
./ws_examples
```

### WSS

Before running the WSS-examples, an RSA private key (server.key) and an SSL certificate (server.crt) must be created. Follow, for instance, the instructions given here (for a self-signed certificate): http://www.akadia.com/services/ssh_test_certificate.html

Then:
```
./wss_examples
```

注意：
```
1. 使用的是boost1.55.0，自己编译的库文件
为了便于移植，不用在编译和安装boost，使用静态链接boost需要的库文件，
在原来功能的基础上进行了修改，主要修改了CMakeLists.txt，修改boost库的链接，主要该工程只能在>=gcc4.8(c++11)的版本上使用

2. ./ws_examples, 如果出现what():bind:Address already in use，表示端口号被占用，程序中使用的端口号是8080，可以改成30000

3. 如果在裸机上编译该程序程序（ubuntu14.04），需要安装cmake和ssl，如下：
sudo apt-get install cmake libssl-dev
```
