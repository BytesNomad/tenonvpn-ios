官网请访问： https://www.tenonvpn.net

1.1 去中心化VPN业务网络

1.1.1 传统VPN服务

常规VPN服务如下图所示：
用户端将请求数据加密后，直接发送给VPN-Server，VPN-Server通过协商好的秘钥解密出用户的请求包，然后请求Internet的数据，Internet返回数据包后，再通过协商好的秘钥加密数据，然后返回给用户。
这里存在严重的隐私安全问题，因为VPN-Server可以获取这个用户的所有信息，包括传输过程中的隐私数据，最基本的就是用户的IP地址完全暴露，其访问的所有数据也会绑定这个IP地址，用户的隐私对于VPN-Server厂商完全暴露。

1.1.2 TenonVPN

TenonVPN业务整体组网如图所示：

TenonVPN业务网络的构建分为两个部分，一个是路由网络，一个是VPN代理服务网络，在TenonVPN中，所有通信透视通过账号地址进行，包括P2P网络节点间的通信，每个业务节点都有自己的账号地址，账号地址在Tenon中是完全匿名的。

同时为了保证IP地址不被暴露，TenonVPN增加了路由网络，用户的请求包通过加密后通过路由网络随机中转多次后到达VPN服务网络，然后通过随机选择VPN服务节点，VPN服务节点通过访问Internet，并将返回数据加密后返回到路由网络并随机性的路由后返回给用户节点。

这个过程中，路由路径是随机性的，访问的VPN服务会在用户当前会话随机选择好多个服务节点，协商秘钥，这个协商都是通过路由中转进行，VPN服务除了知道匿名账户地址和公钥外，无法获取用户的IP信息等，从而保证用户隐私。协商好秘钥，用户就可以通过指定的VPN服务账户地址，然后通过随机路由将包送达指定节点，完成VPN服务的整个通信过程。


1.1.3 智能路由

VPN通信的整个过程，会通过智能路由网络，智能路由解决了VPN通信的几个核心问题：

1） 隐藏VPN客户的真实地址，用户的每一个session都是通过随机路由，VPN服务厂商完全无法将数据绑定到现实世界的每一个真实地址上。

2） 智能路由的接入，可以让用户PC，MAC成为智能路由的节点，也就是不同国家，地区的用户可以彼此通过节点相互访问不同地区的Internet，这很容易的就避免了网络运营商的屏蔽。同时VPN业务网提供了强大的网络穿越能力，可以让不同子网的用户进行直接消息透传。

3） 通过区中心化网络的通信质量，选择最佳通信路劲，比如越南用户访问北美的Internet，其最优路径并不是直接通过北美的VPN服务器，而是通过新加坡的节点，然后再转到北美节点，其性能会提升50%左右。

4） 有效的利用用户PC，MAC资源，并且在通过Tenon Coin激励方式，让接入节点享受区中心世界的经济福利。

1.1.4 挖矿和带宽证明

TenonVPN用户选择了指定账号地址的VPN服务，并通过这个账号地址的节点上网，期间必然产生流量，客户端和VPN服务端都会定时对这个流量进行监控和统计，比如达到10M就对这个事实创建一个合约，服务端签名后发送给客户端，客户端验证并确认使用了10M流量则对这个合约进行二次签名，双方签名验证后将这个共识存入本地业务链。

当达到一定程度（比如约定到了或者时间到了），将这个共识合并并双方签名验证后，提交到主链进行真正的交易。交易通过主网的共识结算，即对这些交易进行了记账，VPN服务厂商或者提供资源的用户即获取激励，这个过程其实就是一个挖矿行为。

在用户选择VPN提供商时，会在主链锁定自己的余额，用于支付流量。

