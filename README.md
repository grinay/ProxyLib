# ProxyLib
TcpClient , Socket library with proxy support Http, Socks4, Socks4a, Socks5 was developed to support:

.NET Standard 2.0 and .NET Core

Original code based on https://github.com/bentonstark/starksoft-aspen.git

### Usage example:

```C#
ProxyClientFactory factory = new ProxyClientFactory();
IProxyClient proxyClient = factory.CreateProxyClient(proxy.Type, proxy.Address, Int32.Parse(proxy.Port), proxy.User, proxy.Password);

//Setup timeouts
proxyClient.ReceiveTimeout = (int)TimeSpan.FromSeconds(60).TotalMilliseconds;
proxyClient.SendTimeout = (int)TimeSpan.FromSeconds(60).TotalMilliseconds;

//Get TcpClient to futher work
var tcpClient = proxyClient.CreateConnection("google.com", "80");

//Or get socket to futher work
var socket = proxyClient.CreateConnection("google.com", "80").Client;

```

TcpClient or Socket shuld be disposed by calling 
```C#
socket.Close();
//or
tcpClient.Close();
```
