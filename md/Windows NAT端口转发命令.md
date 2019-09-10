# Windows NAT端口转发命令

> 场景说明：
> 例如通过物理机访问虚拟机的服务，通过物理机将指定的端口请求转发到虚拟机的指定端口中

Windows本身命令行支持配置端口映射，条件是已经安装了IPV6，启不启用都无所谓，xp、2003装了ipv6协议也是可以的。

在cmd命令下操作：

- 增加端口映射，将10.10.10.10的8080映射到10.10.10.11的80端口 

```bash
netsh interface portproxy add v4tov4 listenport=8080 listenaddress=10.10.10.10 connectport=80 connectaddress=10.10.10.11
```

- 删除端口映射 

```bash
netsh interface portproxy del v4tov4 listenport=8080 listenaddress=10.10.10.10
```

- 查看已存在的端口映射 

```bash
netsh interface portproxy show v4tov4
```

- 可以通过命令 `netstat -ano|find "8080"` 查看端口是否已在监听
- 测试端口是否连通

```bash
telnet 10.10.10.10 8080
```



> win10以下系统可以使用PassPort软件实现端口转发。