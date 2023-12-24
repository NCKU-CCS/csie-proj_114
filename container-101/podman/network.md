## Podman network

1. 新增 Podman 網路
範例：

```Bash
podman network create <NAME>
```

```Shell
[student@servera ~]$ podman network create nginx-lab
nginx-lab
```

2. 顯示所有網路列表
範例：

```Bash
podman network ls
```

```Shell
[student@servera ~]$ podman network ls
NETWORK ID    NAME        DRIVER
de444a54efb2  nginx-lab   bridge
2f259bab93aa  podman      bridge
[student@servera ~]$
```

3. 顯示指定網路詳細資訊
範例：

```Bash
podman network inspect <NAME>
```

```Shell
[student@servera ~]$ podman network inspect nginx-lab
[
     {
          "name": "nginx-lab",
          "id": "de444a54efb23ae31aa571e5410632ab3129df1847025fe8790c6d7b68378ade",
          "driver": "bridge",
          "network_interface": "cni-podman1",
          "created": "2023-07-21T22:18:42.91024454+08:00",
          "subnets": [
               {
                    "subnet": "10.89.0.0/24",
                    "gateway": "10.89.0.1"
               }
          ],
          "ipv6_enabled": false,
          "internal": false,
          "dns_enabled": false,
          "ipam_options": {
               "driver": "host-local"
          }
     }
]
```

4. 移除指定網路
範例：

```Bash
podman network rm  <NAME>
```

```Shell
[student@servera ~]$ podman network remove nginx-lab
nginx-lab
```

5. 移除未使用網路
範例：

```Bash
podman network prune
```

```Shell
[student@servera ~]$ podman network create lab-a
lab-a
[student@servera ~]$ podman network create lab-b
lab-b
[student@servera ~]$ podman network ls
NETWORK ID    NAME        DRIVER
1c327e55b394  lab-a       bridge
89ddfaf4bce8  lab-b       bridge
2f259bab93aa  podman      bridge
[student@servera ~]$ podman network prune
WARNING! This will remove all networks not used by at least one container.
Are you sure you want to continue? [y/N] y
lab-a
lab-b
[student@servera ~]$ podman network ls
NETWORK ID    NAME        DRIVER
2f259bab93aa  podman      bridge
[student@servera ~]$
```

reference: Visit https://how64bit.com/posts/container/2023/container-podman-network/