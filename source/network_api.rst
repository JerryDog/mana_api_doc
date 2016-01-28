


网络服务
====================



API规范
--------------------------

网络服务API入口与API列表如下：


+ API入口:

区域 API入口 北京1区(bj1) `https://bj1.network.api.ustack.com`_ 广东1区(gd1)
`https://gd1.network.api.ustack.com`_

+ API列表:

资源 操作 HTTP方法 URI路径 *私有网络 (Networks)* 查看所有私有网络 GET /v2.0/networks
创建私有网络 POST /v2.0/networks 查看私有网络详情 GET /v2.0/networks/{network_id}
修改私有网络名称 PUT /v2.0/networks/{network_id} 禁用私有网络 PUT
/v2.0/networks/{network_id} 启用私有网络 PUT /v2.0/networks/{network_id} *子网
(Subnets)* 查看所有子网 GET /v2.0/subnets 在指定的私有网络中创建子网 POST /v2.0/subnets
查看子网详情 GET /v2.0/subnets/{subnet_id} 修改子网名称 PUT
/v2.0/subnets/{subnet_id} 禁用/启用子网DHCP服务 PUT /v2.0/subnets/{subnet_id}
删除子网 DELETE /v2.0/subnets/{subnet_id} *路由器 (Routers)* 查看所有路由器 GET
/v2.0/routers 创建路由器 POST /v2.0/routers 查看路由器 GET
/v2.0/routers/{router_id} 修改路由器名称 PUT /v2.0/routers/{router_id}
开启/禁用路由器公网网关 PUT /v2.0/routers/{router_id} 关联子网到路由器 / 添加路由器接口 PUT
/v2.0/routers/{router_id}/add_router_interface 断开路由器上的子网 / 删除路由器接口 PUT
/v2.0/routers/{router_id}/remove_router_interface *端口转发 (Port
Forwarding)* 向路由器添加端口转发规则 PUT
/v2.0/uos_resources/{router_id}/add_router_portforwarding 删除一条端口转发规则
PUT /v2.0/uos_resources/{router_id}/remove_router_portforwarding
列出路由器的端口转发规则 GET /v2.0/routers/{router_id} *公网IP (Floating IPs)*
创建公网IP POST /v2.0/floatingips 修改公网IP带宽 PUT
/v2.0/uos_resources/{floatingip_id}/update_floatingip_ratelimit
查看公网IP详情 GET /v2.0/floatingips/{floatingip_id} 绑定公网IP到虚拟网卡 PUT
/v2.0/floatingips/{floatingip_id} 解除公网IP与虚拟网卡的绑定 PUT
/v2.0/floatingips/{floatingip_id} 删除公网IP DELETE
/v2.0/floatingips/{floatingip_id} *虚拟网卡 (Ports)* 查看所有虚拟网卡 GET
/v2.0/ports 在指定的私有网络/子网中创建虚拟网卡 POST /v2.0/ports 查看虚拟网卡 GET
/v2.0/ports/{port_id} 修改虚拟网卡名称 PUT /v2.0/ports/{port_id} 修改虚拟网卡的安全组
PUT /v2.0/ports/{port_id} 修改虚拟网卡的允许IP PUT /v2.0/ports/{port_id}
启用/禁用虚拟网卡 PUT /v2.0/ports/{port_id} 删除虚拟网卡 DELETE
/v2.0/ports/{port_id} *安全组 (Security Groups)* 查看所有安全组 GET /v2.0
/security-groups 创建安全组 POST /v2.0/security-groups 查看安全组 GET /v2.0
/security-groups/{security_group_id} 删除安全组 DELETE /v2.0/security-
groups/{security_group_id} 查看所有安全组规则 GET /v2.0/security-group-rules
创建安全组规则 POST /v2.0/security-group-rules 查看安全组规则 GET /v2.0/security-
group-rules/{rules-security-groups-id} 删除安全组规则 DELETE /v2.0/security-
group-rules/{rules-security-groups-id} *负载均衡器 (LoadBalancer)*
查看所有负载均衡器 GET /v2.0/lbaas/loadbalancers 创建负载均衡器 POST
/v2.0/lbaas/loadbalancers 修改负载均衡器的非只读属性 PUT
/v2.0/lbaas/loadbalancers/{loadbalancer_id} 查看负载均衡器详情 GET
/v2.0/lbaas/loadbalancers/{loadbalancer_id} 删除负载均衡器 DELETE
/v2.0/lbaas/loadbalancers/{loadbalancer_id} *监听器 (Listener)* 查看所有监听器
GET /v2.0/lbaas/listeners 查看指定负载均衡器下的监听器 GET
/v2.0/lbaas/loadbalancers/{loadbalancer_id}/lbaas_listeners
为指定负载均衡器创建监听器 POST /v2.0/lbaas/listeners 修改监听器的非只读属性 PUT
/v2.0/lbaas/listeners/{listener_id} 查看监听器详情 GET
/v2.0/lbaas/listeners/{listener_id} 删除监听器 DELETE
/v2.0/lbaas/listeners/{listener_id} *7层策略 (L7Policy)* 查看所有7层策略 GET
/v2.0/lbaas/l7policies 查看指定监听器的7层策略 GET
/v2.0/lbaas/listeners/{listener_id}/lbaas_l7policies 为指定监听器创建7层策略 POST
/v2.0/lbaas/l7policies 更新7层策略的非只读属性 PUT
/v2.0/lbaas/l7policies/{l7policy_id} 查看7层策略详情 GET
/v2.0/lbaas/l7policies/{l7policy_id} 删除7层策略 DELETE
/v2.0/lbaas/l7policies/{l7policy_id} *7层匹配规则 (L7Rule)* 查看指定7层策略的7层匹配规则
GET /v2.0/lbaas/l7policies/{l7policy_id}/rules 为指定7层策略创建7层匹配规则 POST
/v2.0/lbaas/l7policies/{l7policy_id}/rules 更新7层匹配规则的非只读属性 PUT
/v2.0/lbaas/l7policies/{l7policy_id}/rules/{l7rule_id} 查看7层匹配规则详情 GET
/v2.0/lbaas/l7policies/{l7policy_id}/rules/{l7rule_id} 删除7层匹配规则 DELETE
/v2.0/lbaas/l7policies/{l7policy_id}/rules/{l7rule_id} *资源池 (Pool)*
查看所有资源池 GET /v2.0/lbaas/pools 创建资源池 POST /v2.0/lbaas/pools.json
修改资源池的非只读属性 PUT /v2.0/lbaas/pools/{pool_id} 查看资源池详情 GET
/v2.0/lbaas/pools/{pool_id} 删除资源池 DELETE /v2.0/lbaas/pools/{pool_id}
*成员 (Member)* 查看指定资源池下的所有成员 GET /v2.0/lbaas/pools/{pool_id}/members
为指定资源池添加成员 POST /v2.0/lbaas/pools/{pool_id}/members 修改成员的非只读属性 PUT
/v2.0/lbaas/pools/{pool_id}/members/{member_id} 查看成员详情 GET
/v2.0/lbaas/pools/{pool_id}/members/{member_id} 删除成员 DELETE
/v2.0/lbaas/pools/{pool_id}/members/{member_id}


私有网络 (Networks)
----------------------------------------------



查看所有私有网络
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 GET /v2.0/networks 查看所有私有网络
请求参数

无。

返回参数
字段名 类型 描述 status string 表示网络状态，可能值有ACTIVE、DOWN、BUILD、ERROR subnets
list 与此网络相关联的子网 name string 该网络的名字 admin_state_up bool 网络的管理状态
tenant_id string 拥有该网络的租户的UUID created_at string 该网络的创建时间，为UTC时间
uos:rate_limit int 速率限制，单位为Mbps，为UOS扩展字段，不存在于OpenStack router:external
bool 是否为外网（Public Network） shared bool 是否可跨租户共享 id string 该网络的唯一UUID
请求样例

::

    
    curl -s \
         -X GET `https://bj1.network.api.ustack.com/v2.0/networks`_ \
         -H "X-Auth-Token: {token_id}" \
         -H "Content-Type: application/json" \
         -H "Accept: application/json"


返回样例 :


::

    {
        "networks": [
            {
                "status": "ACTIVE",
                "subnets": [
                    "dd3d7135-0d88-4545-978e-09882f61af92"
                ],
                "name": "office_net",
                "admin_state_up": true,
                "provider:unmanaged_network": false,
                "tenant_id": "ac8784463a3d4693b92db09c2ab1b706",
                "created_at": "2014-05-21T03:55:44.000000",
                "uos:rate_limit": 600,
                "router:external": true,
                "shared": false,
                "id": "0737cf5c-5f14-4f2d-bc5d-ed09d4826663"
            }
        ]
    }




创建私有网络
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 POST /v2.0/networks 创建私有网络
请求参数
参数名 类型 描述 admin_state_up bool 管理状态，默认为True，不推荐修改 name string
网络的名称（可重复）
返回参数
字段名 类型 描述 status string 表示网络是否可工作，可能值有ACTIVE、DOWN、BUILD、ERROR subnets
list 与此网络关联的子网 provider:unmanaged_network bool 表示该网络是否为自管网络 name
string 该网络的名字 admin_state_up bool 网络的管理状态 tenant_id string
拥有该网络的租户的UUID shared bool 是否可跨租户共享 id string 该网络的唯一UUID
请求样例

::

    
    curl -s \
         -X POST `https://bj1.network.api.ustack.com/v2.0/networks`_ \
         -H "X-Auth-Token: {token_id}" \
         -H "Content-Type: application/json" \
         -H "Accept: application/json" \
         -d '{
                "network": {
                    "name": "test",
                    "admin_state_up": true
                }
            }'


返回样例 :


::

    {
        "network": {
            "status": "ACTIVE",
            "subnets": [],
            "name": "test",
            "admin_state_up": true,
            "tenant_id": "50aa68035ae940baa0c463b95c3d0e7d",
            "shared": false,
            "provider:unmanaged_network": false,
            "id": "be0095ce-70f0-4283-b59f-009630065803"
        }
    }




创建自管网络
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 POST /v2.0/networks 创建私有网络
请求参数
参数名 类型 描述 admin_state_up bool 管理状态，默认为True，不推荐修改 name string
网络的名称（可重复） provider:unmanaged_network bool 表示该网络是自管网络
返回参数
字段名 类型 描述 status string 表示网络是否可工作，可能值有ACTIVE、DOWN、BUILD、ERROR subnets
list 与此网络关联的子网 provider:unmanaged_network bool 表示该网络是否为自管网络 name
string 该网络的名字 admin_state_up bool 网络的管理状态 tenant_id string
拥有该网络的租户的UUID shared bool 是否可跨租户共享 id string 该网络的唯一UUID
请求样例

::

    
    curl -s \
         -X POST `https://bj1.network.api.ustack.com/v2.0/networks`_ \
         -H "X-Auth-Token: {token_id}" \
         -H "Content-Type: application/json" \
         -H "Accept: application/json" \
         -d '{"network": {"name": "test", "admin_state_up": true, "provider:unmanaged_network": true}}'


返回样例 :


::

    {
        "network": {
            "status": "ACTIVE",
            "subnets": [],
            "name": "test",
            "admin_state_up": true,
            "tenant_id": "50aa68035ae940baa0c463b95c3d0e7d",
            "shared": false,
            "provider:unmanaged_network": true,
            "id": "be0095ce-70f0-4283-b59f-009630065803"
        }
    }




查看私有网络详情
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 GET /v2.0/networks/{network_id} 查看私有网络详情
请求参数

无。

返回参数
字段名 类型 描述 status string 表示网络是否可工作，可能值有ACTIVE、DOWN、BUILD、ERROR subnets
list 与此网络关联的子网 name string 该网络的名字 provider:unmanaged_network bool
表示该网络是否为自管网络 admin_state_up bool 网络的管理状态 tenant_id string
拥有该网络的租户的UUID created_at string 该网络的创建时间，为UTC时间 uos:rate_limit int
速率限制，单位为Mbps，为UOS扩展字段，不存在于OpenStack router:external bool 是否为外网（Public
Network） shared bool 是否可跨租户共享 id string 该网络的唯一UUID
请求样例

::

    
    curl -s \
         -X GET `https://bj1.network.api.ustack.com/v2.0/networks/be0095ce-70f0-4283-b59f-009630065803`_ \
         -H "X-Auth-Token: {token_id}" \
         -H "Content-Type: application/json" \
         -H "Accept: application/json"


返回样例 :


::

    {
        "network": {
            "status": "ACTIVE",
            "subnets": [],
            "name": "testnew",
            "admin_state_up": true,
            "provider:unmanaged_network": false,
            "tenant_id": "50aa68035ae940baa0c463b95c3d0e7d",
            "created_at": "2014-05-30T03:48:11.000000",
            "uos:rate_limit": 600,
            "router:external": false,
            "shared": false,
            "id": "be0095ce-70f0-4283-b59f-009630065803"
        }
    }




修改私有网络名称
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 PUT /v2.0/networks/{network_id} 修改私有网络名称
请求参数
参数名 类型 描述 name string 网络的名称（可与其他网络名称重复）
返回参数
字段名 类型 描述 status string 表示网络是否可工作，可能值有ACTIVE、DOWN、BUILD、ERROR subnets
list 与此网络关联的子网 name string 该网络的名字 admin_state_up bool 网络的管理状态
tenant_id string 拥有该网络的租户的UUID created_at string 该网络的创建时间，为UTC时间
uos:rate_limit int 速率限制，单位为Mbps，为UOS扩展字段，不存在于OpenStack router:external
bool 是否为外网（Public Network） shared bool 是否可跨租户共享 id string 该网络的唯一UUID
请求样例

::

    
    curl -s \
         -X PUT `https://bj1.network.api.ustack.com/v2.0/networks/be0095ce-70f0-4283-b59f-009630065803`_ \
         -H "X-Auth-Token: {token_id}" \
         -H "Content-Type: application/json" \
         -H "Accept: application/json" \
         -d '{
                "network": {
                    "name": "testnew"
                }
            }'


返回样例 :


::

    {
        "network": {
            "status": "ACTIVE",
            "subnets": [],
            "name": "testnew",
            "admin_state_up": true,
            "provider:unmanaged_network": false,
            "tenant_id": "50aa68035ae940baa0c463b95c3d0e7d",
            "created_at": "2014-05-30T03:48:11.000000",
            "uos:rate_limit": 600,
            "router:external": false,
            "shared": false,
            "id": "be0095ce-70f0-4283-b59f-009630065803"
        }
    }




禁用私有网络
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

该操作执行后，该网络下新启动的云主机和重启后的云主机将无法连入网络，但将正常获得IP地址。
HTTP方法 URI路径 描述 PUT /v2.0/networks/{network_id} 禁用私有网络
请求参数
参数名 类型 描述 admin_stat_up string False
返回参数
字段名 类型 描述 status string 表示网络是否可工作，可能值有ACTIVE、DOWN、BUILD、ERROR subnets
list 与此网络关联的子网 name string 该网络的名字 admin_state_up bool
网络的管理状态（成功执行后将为False） tenant_id string 拥有该网络的租户的UUID created_at string
该网络的创建时间，为UTC时间 uos:rate_limit int 速率限制，单位为Mbps，为UOS扩展字段，不存在于OpenStack
router:external bool 是否为外网（Public Network） shared bool 是否可跨租户共享 id
string 该网络的唯一UUID
请求样例

::

    
    curl -s \
         -X PUT `https://bj1.network.api.ustack.com/v2.0/networks/be0095ce-70f0-4283-b59f-009630065803`_ \
         -H "X-Auth-Token: {token_id}" \
         -H "Content-Type: application/json" \
         -H "Accept: application/json" \
         -d '{
                "network": {
                    "admin_state_up": "False"
                }
            }'


返回样例 :


::

    {
        "network": {
            "status": "ACTIVE",
            "subnets": [],
            "name": "testnew",
            "admin_state_up": false,
            "provider:unmanaged_network": false,
            "tenant_id": "50aa68035ae940baa0c463b95c3d0e7d",
            "created_at": "2014-05-30T03:48:11.000000",
            "uos:rate_limit": 600,
            "router:external": false,
            "shared": false,
            "id": "be0095ce-70f0-4283-b59f-009630065803"
        }
    }




启用私有网络
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

该操作执行后，该网络下新启动的云主机和原云主机重启后将重新连入网络。
HTTP方法 URI路径 描述 PUT /v2.0/networks/{network_id} 启用私有网络
请求参数
参数名 类型 描述 admin_stat_up string True
返回参数
字段名 类型 描述 status string 表示网络是否可工作，可能值有ACTIVE、DOWN、BUILD、ERROR subnets
list 与此网络关联的子网 name string 该网络的名字 admin_state_up bool
网络的管理状态（成功执行后将为True） tenant_id string 拥有该网络的租户的UUID created_at string
该网络的创建时间，为UTC时间 uos:rate_limit int 速率限制，单位为Mbps，为UOS扩展字段，不存在于OpenStack
router:external bool 是否为外网（Public Network） shared bool 是否可跨租户共享 id
string 该网络的唯一UUID
请求样例

::

    
    curl -s \
         -X PUT `https://bj1.network.api.ustack.com/v2.0/networks/be0095ce-70f0-4283-b59f-009630065803`_ \
         -H "X-Auth-Token: {token_id}" \
         -H "Content-Type: application/json" \
         -H "Accept: application/json" \
         -d '{
                "network": {
                    "admin_state_up": "True"
                }
            }'


返回样例 :


::

    {
        "network": {
            "status": "ACTIVE",
            "subnets": [],
            "name": "testnew",
            "admin_state_up": true,
            "provider:unmanaged_network": false,
            "tenant_id": "50aa68035ae940baa0c463b95c3d0e7d",
            "created_at": "2014-05-30T03:48:11.000000",
            "uos:rate_limit": 600,
            "router:external": false,
            "shared": false,
            "id": "be0095ce-70f0-4283-b59f-009630065803"
        }
    }




子网 (Subnets)
----------------------------------------



查看所有子网
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 GET /v2.0/subnets 查看所有子网
请求参数

无。

返回参数
字段名 类型 描述 name string 子网名称 enable_dhcp bool 是否开启DHCP network_id string
子网所属的私有网络的UUID tenant_id string 拥有该子网的租户的UUID created_at string
该子网的创建时间，为UTC时间 dns_nameserver list 为该子网下虚拟主机指定的默认DNS服务器地址
ipv6_ra_mode bool 是否开启IPv6 RA allocation_pools dict
包含两个键，start和end，表示IP池起止地址 gateway_ip string 该子网的网关的IP地址 shared bool
是否可跨租户共享 ip_version int IP协议版本号 host_routes list 主机路由信息 cidr string
该子网的CIDR地址 ipv6_address_mode bool 是否通过dnsmasq获取DHCP可选信息 id string
该子网的唯一UUID
请求样例

::

    
    curl -s \
         -X GET `https://bj1.network.api.ustack.com/v2.0/subnets`_ \
         -H "X-Auth-Token: {token_id}" \
         -H "Content-Type: application/json" \
         -H "Accept: application/json"


返回样例 :


::

    {
        "subnets": [
            {
                "name": "subnet-1c119dd0",
                "enable_dhcp": true,
                "network_id": "86bd4f15-9eac-4153-bd08-88dfe37897f9",
                "tenant_id": "ac8784463a3d4693b92db09c2ab1b706",
                "created_at": "2014-05-21T04:03:57.000000",
                "dns_nameservers": [],
                "ipv6_ra_mode": null,
                "allocation_pools": [
                    {
                        "start": "192.168.10.2",
                        "end": "192.168.10.254"
                    }
                ],
                "gateway_ip": "192.168.10.1",
                "shared": true,
                "ip_version": 4,
                "host_routes": [],
                "cidr": "192.168.10.0/24",
                "ipv6_address_mode": null,
                "id": "1c119dd0-8afb-40e5-9f2d-aca6694489aa"
            }
        ]
    }




在指定的私有网络中创建子网
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 POST /v2.0/subnets 在指定的私有网络中创建子网
请求参数
字段名 类型 描述 name string 子网名称 enable_dhcp bool 是否开启DHCP network_id string
子网所属的私有网络的UUID dns_nameserver list 为该子网下虚拟主机指定的默认DNS服务器地址
allocation_pools dict 包含两个键，start和end，表示IP池起止地址 gateway_ip string
该子网的网关的IP地址 ip_version int IP协议版本号 host_routes list 主机路由信息 cidr string
该子网的CIDR地址
返回参数
字段名 类型 描述 name string 子网名称 enable_dhcp bool 是否开启DHCP network_id string
子网所属的私有网络的UUID tenant_id string 拥有该子网的租户的UUID created_at string
该子网的创建时间，为UTC时间 dns_nameserver list 为该子网下虚拟主机指定的默认DNS服务器地址
ipv6_ra_mode bool 是否开启IPv6 RA allocation_pools dict
包含两个键，start和end，表示IP池起止地址 gateway_ip string 该子网的网关的IP地址 shared bool
是否可跨租户共享 ip_version int IP协议版本号 host_routes list 主机路由信息 cidr string
该子网的CIDR地址 ipv6_address_mode bool 是否通过dnsmasq获取DHCP可选信息 id string
该子网的唯一UUID
请求样例

::

    
    curl -s \
         -X POST `https://bj1.network.api.ustack.com/v2.0/subnets`_ \
         -H "X-Auth-Token: {token_id}" \
         -H "Content-Type: application/json" \
         -H "Accept: application/json" \
         -d '{
                "subnet": {
                    "network_id": "f36ce24b-7ef4-4687-bc02-6f3d5b1a9e34",
                    "ip_version": 4,
                    "cidr": "10.0.1.0/24",
                    "name": "mysubnet"
                }
            }'


返回样例 :


::

    {
        "subnet": {
            "name": "mysubnet",
            "enable_dhcp": true,
            "network_id": "f36ce24b-7ef4-4687-bc02-6f3d5b1a9e34",
            "tenant_id": "50aa68035ae940baa0c463b95c3d0e7d",
            "dns_nameservers": [],
            "ipv6_ra_mode": null,
            "allocation_pools": [
                {
                    "start": "10.0.1.2",
                    "end": "10.0.1.254"
                }
            ],
            "gateway_ip": "10.0.1.1",
            "shared": false,
            "ip_version": 4,
            "host_routes": [],
            "cidr": "10.0.1.0/24",
            "ipv6_address_mode": null,
            "id": "9149cb4d-6f76-4176-9929-b17bd627c22a"
        }
    }




查看子网详情
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 GET /v2.0/subnets/{subnet_id} 查看子网详情
请求参数

无。

返回参数
字段名 类型 描述 name string 子网名称 enable_dhcp bool 是否开启DHCP network_id string
子网所属的私有网络的UUID tenant_id string 拥有该子网的租户的UUID created_at string
该子网的创建时间，为UTC时间 dns_nameserver list 为该子网下虚拟主机指定的默认DNS服务器地址
ipv6_ra_mode bool 是否开启IPv6 RA allocation_pools dict
包含两个键，start和end，表示IP池起止地址 gateway_ip string 该子网的网关的IP地址 shared bool
是否可跨租户共享 ip_version int IP协议版本号 host_routes list 主机路由信息 cidr string
该子网的CIDR地址 ipv6_address_mode bool 是否通过dnsmasq获取DHCP可选信息 id string
该子网的唯一UUID
请求样例

::

    
    curl -s \
         -X GET `https://bj1.network.api.ustack.com/v2.0/subnets/9149cb4d-6f76-4176-9929-b17bd627c22a`_ \
         -H "X-Auth-Token: {token_id}" \
         -H "Content-Type: application/json" \
         -H "Accept: application/json"


返回样例 :


::

    {
        "subnet": {
            "name": "mysubnet",
            "enable_dhcp": true,
            "network_id": "f36ce24b-7ef4-4687-bc02-6f3d5b1a9e34",
            "tenant_id": "50aa68035ae940baa0c463b95c3d0e7d",
            "created_at": "2014-05-30T03:57:03.000000",
            "dns_nameservers": [
                "1.2.4.8",
                "114.114.114.114"
            ],
            "ipv6_ra_mode": null,
            "allocation_pools": [
                {
                    "start": "10.0.1.2",
                    "end": "10.0.1.254"
                }
            ],
            "gateway_ip": "10.0.1.1",
            "shared": false,
            "ip_version": 4,
            "host_routes": [],
            "cidr": "10.0.1.0/24",
            "ipv6_address_mode": null,
            "id": "9149cb4d-6f76-4176-9929-b17bd627c22a"
        }
    }




修改子网名称
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 PUT /v2.0/subnets/{subnet_id} 修改子网名称
请求参数
字段名 类型 描述 name string 子网名称
返回参数
字段名 类型 描述 name string 子网名称 enable_dhcp bool 是否开启DHCP network_id string
子网所属的私有网络的UUID tenant_id string 拥有该子网的租户的UUID created_at string
该子网的创建时间，为UTC时间 dns_nameserver list 为该子网下虚拟主机指定的默认DNS服务器地址
ipv6_ra_mode bool 是否开启IPv6 RA allocation_pools dict
包含两个键，start和end，表示IP池起止地址 gateway_ip string 该子网的网关的IP地址 shared bool
是否可跨租户共享 ip_version int IP协议版本号 host_routes list 主机路由信息 cidr string
该子网的CIDR地址 ipv6_address_mode bool 是否通过dnsmasq获取DHCP可选信息 id string
该子网的唯一UUID
请求样例

::

    
    curl -s \
         -X PUT `https://bj1.network.api.ustack.com/v2.0/subnets/9149cb4d-6f76-4176-9929-b17bd627c22a`_ \
         -H "X-Auth-Token: {token_id}" \
         -H "Content-Type: application/json" \
         -H "Accept: application/json" \
         -d '{
                "subnet": {
                    "name": "mysubnet-new"
                }
            }'


返回样例 :


::

    {
        "subnet": {
            "name": "mysubnet-new",
            "enable_dhcp": true,
            "network_id": "f36ce24b-7ef4-4687-bc02-6f3d5b1a9e34",
            "tenant_id": "50aa68035ae940baa0c463b95c3d0e7d",
            "dns_nameservers": [],
            "ipv6_ra_mode": null,
            "allocation_pools": [
                {
                    "start": "10.0.1.2",
                    "end": "10.0.1.254"
                }
            ],
            "gateway_ip": "10.0.1.1",
            "shared": false,
            "ip_version": 4,
            "host_routes": [],
            "cidr": "10.0.1.0/24",
            "ipv6_address_mode": null,
            "id": "9149cb4d-6f76-4176-9929-b17bd627c22a"
        }
    }




路由器 (Routers)
------------------------------------------



查看所有路由器
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 GET /v2.0/routers 查看所有路由器
请求参数

无。

返回参数
字段名 类型 描述 status string 虚拟路由器状态 external_gateway_info dict
外网网关信息，包含外网UUID和是否开启SNAT portforwardings list 端口转发信息，参考下一节“端口转发” name
string 虚拟路由器名字 admin_state_up bool 虚拟路由器的管理状态 tenant_id string
拥有该路由器的租户的UUID created_at string 该路由器的创建时间，为UTC时间 routes list 静态路由规则
id string 该虚拟路由器的唯一UUID
请求样例

::

    
    curl -s \
         -X GET `https://bj1.network.api.ustack.com/v2.0/routers`_ \
         -H "X-Auth-Token: {token_id}" \
         -H "Content-Type: application/json" \
         -H "Accept: application/json"


返回样例 :


::

    {
        "routers": [
            {
                "status": "ACTIVE",
                "external_gateway_info": {
                    "network_id": "0737cf5c-5f14-4f2d-bc5d-ed09d4826663",
                    "enable_snat": true
                },
                "portforwardings": [],
                "name": "testrouterha",
                "admin_state_up": true,
                "tenant_id": "50aa68035ae940baa0c463b95c3d0e7d",
                "created_at": "2014-05-21T05:20:22.000000",
                "routes": [],
                "id": "0dde4975-1116-4301-8084-8e4f7df91c1b"
            }
        ]
    }




创建路由器
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 POST /v2.0/routers 创建路由器
请求参数
字段名 类型 描述 name string 路由器名称 admin_state_up bool 虚拟路由器的管理状态
external_gateway_info dict 外网网关信息，包含一个键，为network_id。
返回参数
字段名 类型 描述 status string 虚拟路由器状态 external_gateway_info dict
外网网关信息，包含外网UUID和是否开启SNAT name string 虚拟路由器名字 admin_state_up bool
虚拟路由器的管理状态 tenant_id string 拥有该路由器的租户的UUID id string 该虚拟路由器的唯一UUID
请求样例

::

    
    curl -s \
         -X  POST `https://bj1.network.api.ustack.com/v2.0/routers`_ \
         -H "X-Auth-Token: {token_id}" \
         -H "Content-Type: application/json" \
         -H "Accept: application/json" \
         -d '{
                "router": {
                    "external_gateway_info": {
                        "network_id": "0737cf5c-5f14-4f2d-bc5d-ed09d4826663"
                    },
                    "name": "testwithgw",
                    "admin_state_up": true
                }
            }'


返回样例 :


::

    {
        "router": {
            "status": "ACTIVE",
            "external_gateway_info": {
                "network_id": "0737cf5c-5f14-4f2d-bc5d-ed09d4826663"
            },
            "name": "testwithgw",
            "admin_state_up": true,
            "tenant_id": "50aa68035ae940baa0c463b95c3d0e7d",
            "id": "f8bc7de6-8c5d-429f-8ac7-6ce6d60087ce"
        }
    }




修改路由器名称
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 PUT /v2.0/routers/{router_id} 修改路由器名称
请求参数
字段名 类型 描述 name string 路由器名称
返回参数
字段名 类型 描述 status string 虚拟路由器状态 external_gateway_info dict
外网网关信息，包含外网UUID和是否开启SNAT portforwardings list 端口转发信息，参考下一节“端口转发” name
string 虚拟路由器名字 admin_state_up bool 虚拟路由器的管理状态 tenant_id string
拥有该路由器的租户的UUID created_at string 该路由器的创建时间，为UTC时间 routes list 静态路由规则
id string 该虚拟路由器的唯一UUID
请求样例

::

    
    curl -s \
         -X PUT `https://bj1.network.api.ustack.com/v2.0/routers/f8bc7de6-8c5d-429f-8ac7-6ce6d60087ce`_ \
         -H "X-Auth-Token: {token_id}" \
         -H "Content-Type: application/json" \
         -H "Accept: application/json" \
         -d '{
                "router": {
                    "name": "testwithgw-new"
                }
            }'


返回样例 :


::

    {
        "router": {
            "status": "ACTIVE",
            "external_gateway_info": {
                "network_id": "0737cf5c-5f14-4f2d-bc5d-ed09d4826663",
                "enable_snat": true
            },
            "portforwardings": [],
            "name": "testwithgw-new",
            "admin_state_up": true,
            "tenant_id": "50aa68035ae940baa0c463b95c3d0e7d",
            "created_at": "2014-05-30T06:04:56.000000",
            "routes": [],
            "id": "f8bc7de6-8c5d-429f-8ac7-6ce6d60087ce"
        }
    }




开启/禁用路由器公网网关
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

该操作执行后，该路由下所有跨子网的流量会被断掉
HTTP方法 URI路径 描述 PUT /v2.0/routers/{router_id} 开启/禁用路由器公网网关
请求参数
字段名 类型 描述 admin_state_up string True/False
返回参数
字段名 类型 描述 status string 虚拟路由器状态 external_gateway_info dict
外网网关信息，包含外网UUID和是否开启SNAT portforwardings list 端口转发信息，参考下一节“端口转发” name
string 虚拟路由器名字 admin_state_up bool 虚拟路由器的管理状态 tenant_id string
拥有该路由器的租户的UUID created_at string 该路由器的创建时间，为UTC时间 routes list 静态路由规则
id string 该虚拟路由器的唯一UUID
请求样例

::

    
    curl -s \
         -X PUT `https://bj1.network.api.ustack.com/v2.0/routers/f8bc7de6-8c5d-429f-8ac7-6ce6d60087ce`_ \
         -H "X-Auth-Token: {token_id}" \
         -H "Content-Type: application/json" \
         -H "Accept: application/json" \
         -d '{
                "router": {
                    "admin_state_up": "False"
                }
            }'


返回样例 :


::

    {
        "router": {
            "status": "ACTIVE",
            "external_gateway_info": {
                "network_id": "0737cf5c-5f14-4f2d-bc5d-ed09d4826663",
                "enable_snat": true
            },
            "portforwardings": [],
            "name": "testwithgw",
            "admin_state_up": false,
            "tenant_id": "50aa68035ae940baa0c463b95c3d0e7d",
            "created_at": "2014-05-30T06:04:56.000000",
            "routes": [],
            "id": "f8bc7de6-8c5d-429f-8ac7-6ce6d60087ce"
        }
    }




关联子网到路由器 / 添加路由器接口
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 PUT /v2.0/routers/{router_id}/add_router_interface
关联子网到路由器/添加路由器接口
请求参数
字段名 类型 描述 subnet_id string 待关联的子网的UUID
返回参数
字段名 类型 描述 subnet_id string 关联的子网的UUID tenant_id string 拥有该路由器的租户的UUID
port_id string 连接的虚拟接口的UUID id string 该虚拟路由器的唯一UUID
请求样例 :


::

    curl -s \\
         -X PUT :bj1_network:`v2.0/routers/f8bc7de6-8c5d-429f-8ac7-6ce6d60087ce/add_router_interface` \\
         -H "X-Auth-Token: {token_id}" \\
         -H "Content-Type: application/json" \\
         -H "Accept: application/json" \\
         -d '{
                "subnet_id": "a120640b-6c69-444c-9f24-9598daad14c3"
            }'


返回样例 :


::

    {
        "subnet_id": "a120640b-6c69-444c-9f24-9598daad14c3",
        "tenant_id": "50aa68035ae940baa0c463b95c3d0e7d",
        "port_id": "fb2dc8e7-51c1-4e4d-a2ae-39a5479e748b",
        "id": "f8bc7de6-8c5d-429f-8ac7-6ce6d60087ce"
    }




断开路由器上的子网 / 删除路由器接口
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 PUT /v2.0/routers/{router_id}/remove_router_interface
断开路由器上的子网 / 删除路由器接口
请求参数
字段名 类型 描述 subnet_id string 待断开的子网的UUID
返回参数
字段名 类型 描述 subnet_id string 断开的子网的UUID tenant_id string 拥有该路由器的租户的UUID
port_id string 断开的虚拟接口的UUID id string 该虚拟路由器的唯一UUID
请求样例

::

    
    curl -s \
         -X PUT `https://bj1.network.api.ustack.com/v2.0/routers/f8bc7de6-8c5d-429f-8ac7-6ce6d60087ce/remove_router_interface`_ \
         -H "X-Auth-Token: {token_id}" \
         -H "Content-Type: application/json" \
         -H "Accept: application/json" \
         -d '{
                "subnet_id": "a120640b-6c69-444c-9f24-9598daad14c3"
            }'


返回样例 :


::

    {
        "subnet_id": "a120640b-6c69-444c-9f24-9598daad14c3",
        "tenant_id": "50aa68035ae940baa0c463b95c3d0e7d",
        "port_id": "fb2dc8e7-51c1-4e4d-a2ae-39a5479e748b",
        "id": "f8bc7de6-8c5d-429f-8ac7-6ce6d60087ce"
    }




端口转发 (Port Forwarding)
------------------------------------------------------------



向路由器添加端口转发规则
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 PUT
/v2.0/uos_resources/{router_id}/add_router_portforwarding 向路由器添加端口转发规则
请求参数
字段名 类型 描述 inside_addr string 内网主机CIDR地址 protocol string 网络协议
outside_port int 虚拟路由器对外端口 inside_port int 内网主机端口
返回参数
字段名 类型 描述 inside_addr string 内网主机CIDR地址 protocol string 网络协议
outside_port int 虚拟路由器对外端口 inside_port int 内网主机端口 id string
该端口转发规则的UUID
请求样例

::

    
    curl -s \
         -X PUT `https://bj1.network.api.ustack.com/v2.0/uos_resources/f8bc7de6-8c5d-429f-8ac7-6ce6d60087ce/add_router_portforwarding`_ \
         -H "X-Auth-Token: {token_id}" \
         -H "Content-Type: application/json" \
         -H "Accept: application/json" \
         -d '{
                "inside_addr": "10.0.12.13",
                "protocol": "TCP",
                "outside_port": 22,
                "inside_port": 22
            }'


返回样例 :


::

    {
        "inside_addr": "10.0.12.13",
        "inside_port": 22,
        "protocol": "TCP",
        "id": "ad14dca6-ac60-4a63-aaab-b39b7a3d9351",
        "outside_port": 22
    }




删除一条端口转发规则
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 PUT
/v2.0/uos_resources/{router_id}/remove_router_portforwarding
删除一条端口转发规则
请求参数
字段名 类型 描述 id string 待删除的端口转发规则的UUID
返回参数
字段名 类型 描述 inside_addr string 内网主机CIDR地址 protocol string 网络协议
outside_port int 虚拟路由器对外端口 inside_port int 内网主机端口 id string
该端口转发规则的UUID router_id string 操作的虚拟路由器的UUID
请求样例

::

    
    curl -s \
         -X PUT `https://bj1.network.api.ustack.com/v2.0/uos_resources/f8bc7de6-8c5d-429f-8ac7-6ce6d60087ce/remove_router_portforwarding`_ \
         -H "X-Auth-Token: {token_id}" \
         -H "Content-Type: application/json" \
         -H "Accept: application/json" \
         -d '{
                "id": "ad14dca6-ac60-4a63-aaab-b39b7a3d9351"
            }'


返回样例 :


::

    {
        "router_id": "f8bc7de6-8c5d-429f-8ac7-6ce6d60087ce",
        "protocol": "TCP",
        "id": "ad14dca6-ac60-4a63-aaab-b39b7a3d9351",
        "inside_addr": "10.0.12.13",
        "outside_port": 22,
        "inside_port": 22
    }




列出路由器的端口转发规则
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 GET /v2.0/{routers/{router_id} 列出路由器的端口转发规则
请求参数

无。

返回参数
字段名 类型 描述 status string 虚拟路由器状态 external_gateway_info dict
外网网关信息，包含外网UUID和是否开启SNAT portforwardings list 端口转发信息，参考前面的返回信息介绍 name
string 虚拟路由器名字 admin_state_up bool 虚拟路由器的管理状态 tenant_id string
拥有该路由器的租户的UUID created_at string 该路由器的创建时间，为UTC时间 routes list 静态路由规则
id string 该虚拟路由器的唯一UUID
请求样例

::

    
    curl -s \
         -X GET `https://bj1.network.api.ustack.com/v2.0/routers/f8bc7de6-8c5d-429f-8ac7-6ce6d60087ce`_ \
         -H "X-Auth-Token: {token_id}" \
         -H "Content-Type: application/json" \
         -H "Accept: application/json"


返回样例 :


::

    {
        "router": {
            "status": "ACTIVE",
            "external_gateway_info": {
                "network_id": "0737cf5c-5f14-4f2d-bc5d-ed09d4826663",
                "enable_snat": true
            },
            "portforwardings": [
                {
                    "inside_addr": "10.0.12.13",
                    "inside_port": 22,
                    "protocol": "TCP",
                    "id": "ad14dca6-ac60-4a63-aaab-b39b7a3d9351",
                    "outside_port": 22
                }
            ],
            "name": "testwithgw",
            "admin_state_up": false,
            "tenant_id": "50aa68035ae940baa0c463b95c3d0e7d",
            "created_at": "2014-05-30T06:04:56.000000",
            "routes": [],
            "id": "f8bc7de6-8c5d-429f-8ac7-6ce6d60087ce"
        }
    }


.. _neutron-api-floating-ip:

公网IP (Floating IPs)
------------------------------------------------------



创建公网IP
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 POST /v2.0/floatingips 创建公网IP
请求参数
字段名 类型 描述 floating_network_id string 该floating IP所属的网络的UUID rate_limit
string 该IP的带宽，单位为Kbps uos:name string 该IP的自定义名字
返回参数
字段名 类型 描述 router_id string 路由器UUID status string 该floating IP的状态
tenant_id sting 拥有该floating IP的租户的UUID created_at string 该floating
IP的创建时间，为UTC时间 rate_limit int 该floating IP的速率限制 uos:name string
该floating IP的自定义名称 floating_network_id string 该floating IP所属的网络的UUID
fixed_ip_address string 与该floating IP关联的fixed IP floating_ip_address
string 分配得到的floating IP的CIDR地址 port_id sting 关联的port的UUID id string
该floating IP的UUID
请求样例

::

    
    curl -s \
         -X POST `https://bj1.network.api.ustack.com/v2.0/floatingips`_ \
         -H "X-Auth-Token: {token_id}" \
         -H "Content-Type: application/json" \
         -H "Accept: application/json" \
         -d '{
                "floatingip": {
                    "floating_network_id": "ddabcc63-8617-465c-8a6d-f534000887e3",
                    "rate_limit": 2048,
                    "uos:name": "2mfip"
                }
            }'


返回样例 :


::

    {
        "floatingip": {
            "router_id": null,
            "status": "DOWN",
            "tenant_id": "50aa68035ae940baa0c463b95c3d0e7d",
            "created_at": "2014-05-30T06:33:55.809454",
            "rate_limit": 2048,
            "uos:name": "2mfip",
            "floating_network_id": "0737cf5c-5f14-4f2d-bc5d-ed09d4826663",
            "fixed_ip_address": null,
            "floating_ip_address": "10.96.24.13",
            "port_id": null,
            "id": "5dca5f0e-c39b-4321-a68a-3eaa79ea5296"
        }
    }




修改公网IP带宽
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 PUT
/v2.0/uos_resources/{floatingip_id}/update_floatingip_ratelimit
修改公网IP带宽
请求参数
字段名 类型 描述 floatingip_id string 该floating IP的UUID rate_limit int
该公网IP的带宽，单位为Kbps，应该是为1024的倍数。
返回参数
字段名 类型 描述 id string 该floating IP的UUID uos:name string 该floating
IP的自定义名称 uos:registerno string 该floating IP的备案号 status string
该floating IP的状态 tenant_id sting 拥有该floating IP的租户的UUID created_at
string 该floating IP的创建时间，为UTC时间 router_id string 路由器UUID rate_limit
int 该floating IP的速率限制 floating_ip_address string 分配得到的floating
IP的CIDR地址 floating_port_id string 分配得到的floating IP的端口的ID
floating_network_id string 该floating IP所属的网络的UUID floating_subnet_id
string 该floating IP所属的子网的UUID fixed_ip_address string 与该floating
IP关联的fixed IP port_id sting 关联的port的UUID
请求样例

::

    
    curl -s \
         -X PUT `https://bj1.network.api.ustack.com/v2.0/uos_resources/5dca5f0e-c39b-4321-a68a-3eaa79ea5296/update_floatingip_ratelimit.json`_ \
         -H "X-Auth-Token: {token_id}" \
         -H "Content-Type: application/json" \
         -H "Accept: application/json" \
         -d '{
                "rate_limit": 20480
            }'


返回样例 :


::

    {
        "router_id": null,
        "status": "DOWN",
        "floating_port_id": "75be2c1c-0025-4564-a1e5-5e30f9bea2d5",
        "floating_network_id": "c061744a-56d4-4a7e-97f3-b7f4ee7a2e0e",
        "floating_subnet_id": "868ee7e1-9bb1-451c-b6bf-6468649d5025",
        "floating_ip_address": "101.71.78.189",
        "fixed_ip_address": null,
        "port_id": null,
        "id": "7f82bd7b-ce65-47bf-85a7-8843c02c2264",
        "tenant_id": "593ad255aa7e4c6189c9b582928e9d1d",
        "created_at": "2014-11-06T03:02:05.000000",
        "rate_limit": 20480,
        "uos:name": "aaa",
        "uos:registerno": ""
    }




查看公网IP详情
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 GET /v2.0/floatingips/{floatingip_id} 查看公网IP详情
请求参数

无。

返回参数
字段名 类型 描述 router_id string 路由器UUID status string 该floating IP的状态
tenant_id sting 拥有该floating IP的租户的UUID created_at string 该floating
IP的创建时间，为UTC时间 rate_limit int 该floating IP的速率限制 uos:name string
该Floting IP的自定义名称 floating_network_id string 该floating IP所属的网络的UUID
fixed_ip_address string 与该floating IP关联的fixed IP floating_ip_address
string 分配得到的floating IP的CIDR地址 port_id sting 关联的port（虚拟网卡）的UUID id
string 该floating IP的UUID
请求样例

::

    
    curl -s \
         -X GET `https://bj1.network.api.ustack.com/v2.0/floatingips/bc01aded-4849-4789-ad91-a7dccc939ecc`_ \
         -H "X-Auth-Token: {token_id}" \
         -H "Content-Type: application/json" \
         -H "Accept: application/json"


返回样例 :


::

    {
        "router_id": null,
        "status": "DOWN",
        "tenant_id": "10d844bf497943ffa320b9119aab5eb7",
        "created_at": "2014-07-15T13:15:53.000000",
        "rate_limit": 1024,
        "uos:name": "fip-bc01aded",
        "floating_network_id": "0b4fa276-64b9-4514-80db-5102453e8921",
        "fixed_ip_address": null,
        "floating_ip_address": "172.24.4.3",
        "port_id": null,
        "id": "bc01aded-4849-4789-ad91-a7dccc939ecc"
    }




绑定公网IP到虚拟网卡
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 PUT /v2.0/floatingips/{floatingip_id} 绑定公网IP到虚拟网卡
请求参数
字段名 类型 描述 port_id sting 待关联的port（虚拟网卡）的UUID
返回参数
字段名 类型 描述 router_id string 路由器UUID status string 该Floating IP的状态
tenant_id sting 拥有该floating IP的租户的UUID created_at string 该floating
IP的创建时间，为UTC时间 rate_limit int 该floating IP的速率限制 uos:name string
该floating IP的自定义名称 floating_network_id string 该floating IP所属的网络的UUID
fixed_ip_address string 与该floating IP关联的fixed IP floating_ip_address
string 分配得到的floating IP的CIDR地址 port_id sting 待关联的port的UUID id string
该floating IP的UUID
请求样例

::

    
    curl -s \
         -X PUT `https://bj1.network.api.ustack.com/v2.0/floatingips/5dca5f0e-c39b-4321-a68a-3eaa79ea5296`_ \
         -H "X-Auth-Token: {token_id}" \
         -H "Content-Type: application/json" \
         -H "Accept: application/json" \
         -d '{
                "floatingip": {
                    "port_id": "b25b377a-a012-4cd8-9504-4f61974cd984"
                }
            }'


返回样例 :


::

    {
        "floatingip": {
            "router_id": "f8bc7de6-8c5d-429f-8ac7-6ce6d60087ce",
            "status": "DOWN",
            "tenant_id": "50aa68035ae940baa0c463b95c3d0e7d",
            "created_at": "2014-05-30T06:33:55.000000",
            "rate_limit": 2048,
            "uos:name": "2mfip",
            "floating_network_id": "0737cf5c-5f14-4f2d-bc5d-ed09d4826663",
            "fixed_ip_address": "10.0.12.3",
            "floating_ip_address": "10.96.24.13",
            "port_id": "b25b377a-a012-4cd8-9504-4f61974cd984",
            "id": "5dca5f0e-c39b-4321-a68a-3eaa79ea5296"
        }
    }




解除公网IP与虚拟网卡的绑定
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 PUT /v2.0/floatingips/{floatingip_id} 解除公网IP与虚拟网卡的绑定
请求参数
字段名 类型 描述 port_id none null
返回参数
字段名 类型 描述 router_id string 路由器UUID status string 该floating IP的状态
tenant_id sting 拥有该Floating IP的租户的UUID created_at string 该floating
IP的创建时间，为UTC时间 rate_limit int 该floating IP的速率限制 uos:name string
该floting IP的自定义名称 floating_network_id string 该floating IP所属的网络的UUID
fixed_ip_address string 与该floating IP关联的fixed IP floating_ip_address
string 分配得到的floating IP的CIDR地址 port_id sting 关联的port的UUID（null） id
string 该floating IP的UUID
请求样例

::

    
    curl -s \
         -X PUT `https://bj1.network.api.ustack.com/v2.0/floatingips/5dca5f0e-c39b-4321-a68a-3eaa79ea5296`_ \
         -H "X-Auth-Token: {token_id}" \
         -H "Content-Type: application/json" \
         -H "Accept: application/json" \
         -d '{
                "floatingip": {
                    "port_id": null
                }
            }'


返回样例 :


::

    {
        "floatingip": {
            "router_id": "f8bc7de6-8c5d-429f-8ac7-6ce6d60087ce",
            "status": "DOWN",
            "tenant_id": "50aa68035ae940baa0c463b95c3d0e7d",
            "created_at": "2014-05-30T06:33:55.000000",
            "rate_limit": 2048,
            "uos:name": "2mfip",
            "floating_network_id": "0737cf5c-5f14-4f2d-bc5d-ed09d4826663",
            "fixed_ip_address": "10.0.12.3",
            "floating_ip_address": "10.96.24.13",
            "port_id": null,
            "id": "5dca5f0e-c39b-4321-a68a-3eaa79ea5296"
        }
    }




删除公网IP
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 DELETE /v2.0/floatingips/{floatingip_id} 删除公网IP
请求参数

无。

返回参数

无

请求样例

::

    
    curl -i \
         -X DELETE `https://bj1.network.api.ustack.com/v2.0/floatingips/5dca5f0e-c39b-4321-a68a-3eaa79ea5296`_ \
         -H "X-Auth-Token: {token_id}" \
         -H "Content-Type: application/json" \
         -H "Accept: application/json"


返回样例 :


::

    HTTP/1.1 204 No Content
    Content-Length: 0
    Date: Fri, 30 May 2014 06:40:26 GMT




虚拟网卡 (Ports)
----------------------------------------



查看所有虚拟网卡
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 GET /v2.0/ports 查看所有虚拟网卡
请求参数

无。

返回参数
字段名 类型 描述 status string 该虚拟网卡的状态 name string 该虚拟网卡的自定义名字
allowed_address_pairs list allowed_address_pairs列表，将允许虚拟网卡以其他IP发包
admin_state_up bool 该虚拟网卡的管理状态 network_id string 该虚拟网卡所属的网络的UUID
tenant_id sting 拥有该虚拟网卡的租户的UUID created_at string 该虚拟网卡的创建时间，为UTC时间
binding:vnic_type string 绑定vNIC类型，可能值有”direct”, “macvtap”和”normal”
device_owner string 使用这个虚拟网卡的实体的UUID mac_address string 该虚拟网卡的MAC地址 id
string 该虚拟网卡的UUID fixed_ips dict 包含两个键，分别为其所在的子网的UUID和CIDR地址
extra_dhcp_opts string DHCP扩展选项 security_groups list 该虚拟网卡应用的安全组规则
device_id string 使用该虚拟网卡的设别（例如虚拟主机）的UUID
请求样例

::

    
    curl -s \
         -X GET `https://bj1.network.api.ustack.com/v2.0/ports`_ \
         -H "X-Auth-Token: {token_id}" \
         -H "Content-Type: application/json" \
         -H "Accept: application/json"


返回样例 :


::

    {
        "ports": [
            {
                "status": "DOWN",
                "name": "myport",
                "allowed_address_pairs": [],
                "binding:disable_anti_spoofing": true,
                "admin_state_up": true,
                "network_id": "f36ce24b-7ef4-4687-bc02-6f3d5b1a9e34",
                "tenant_id": "50aa68035ae940baa0c463b95c3d0e7d",
                "created_at": "2014-05-30T04:15:10.000000",
                "binding:vnic_type": "normal",
                "device_owner": "",
                "mac_address": "fa:16:3e:a1:8f:b2",
                "id": "186d72d2-acb0-4f06-abe6-eb7d2775adbf",
                "fixed_ips": [
                    {
                        "subnet_id": "a120640b-6c69-444c-9f24-9598daad14c3",
                        "ip_address": "10.0.12.56"
                    }
                ],
                "extra_dhcp_opts": [],
                "security_groups": [
                    "8117b434-7172-4012-b637-f8bca59edd5e"
                ],
                "device_id": ""
            }
        ]
    }




在指定的私有网络/子网中创建虚拟网卡
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 POST /v2.0/ports 在指定的私有网络/子网中创建虚拟网卡
请求参数
字段名 类型 描述 name string 该虚拟网卡的自定义名字 network_id string 该虚拟网卡待加入的网络的UUID
返回参数
字段名 类型 描述 status string 该虚拟网卡的状态 name string 该虚拟网卡的自定义名字
allowed_address_pairs list allowed_address_pairs列表，将允许虚拟网卡以其他IP发包
admin_state_up bool 该虚拟网卡的管理状态 network_id string 该虚拟网卡所属的网络的UUID
tenant_id sting 拥有该虚拟网卡的租户的UUID created_at string 该虚拟网卡的创建时间，为UTC时间
binding:vnic_type string 绑定vNIC类型，可能值有”direct”, “macvtap”和”normal”
device_owner string 使用这个虚拟网卡的实体的UUID mac_address string 该虚拟网卡的MAC地址 id
string 该虚拟网卡的UUID fixed_ips dict 包含两个键，分别为其所在的子网的UUID和CIDR地址
security_groups list 该虚拟网卡应用的安全组规则 device_id string
使用该虚拟网卡的设别（例如虚拟主机）的UUID
请求样例

::

    
    curl -s \
         -X POST `https://bj1.network.api.ustack.com/v2.0/ports`_ \
         -H "X-Auth-Token: {token_id}" \
         -H "Content-Type: application/json" \
         -H "Accept: application/json" \
         -d '{
                "port": {
                    "name": "myport",
                    "network_id": "f36ce24b-7ef4-4687-bc02-6f3d5b1a9e34"
                }
            }'


返回样例 :


::

    {
        "port": {
            "status": "DOWN",
            "name": "myport",
            "allowed_address_pairs": [],
            "binding:disable_anti_spoofing": true,
            "admin_state_up": true,
            "network_id": "f36ce24b-7ef4-4687-bc02-6f3d5b1a9e34",
            "tenant_id": "50aa68035ae940baa0c463b95c3d0e7d",
            "binding:vnic_type": "normal",
            "device_owner": "",
            "mac_address": "fa:16:3e:a1:8f:b2",
            "fixed_ips": [
                {
                    "subnet_id": "a120640b-6c69-444c-9f24-9598daad14c3",
                    "ip_address": "10.0.12.2"
                }
            ],
            "id": "186d72d2-acb0-4f06-abe6-eb7d2775adbf",
            "security_groups": [
                "8117b434-7172-4012-b637-f8bca59edd5e"
            ],
            "device_id": ""
        }
    }


请求样例

::

    
    curl -s \
         -X POST `https://bj1.network.api.ustack.com/v2.0/ports`_ \
         -H "X-Auth-Token: {token_id}" \
         -H "Content-Type: application/json" \
         -H "Accept: application/json" \
         -d '{
                "port": {
                    "name": "myport",
                    "network_id": "f762b849-5c3b-492b-919e-6800b508e6a2",
                    "fixed_ips": [
                        {
                            "subnet_id": "a112819c-ebda-44f0-867b-335bd2ac5cfc"
                        }
                    ],
                    "admin_state_up": true
                }
            }'


返回样例 :


::

    {
        "port": {
            "status": "DOWN",
            "name": "myport",
            "allowed_address_pairs": [],
            "binding:disable_anti_spoofing": false,
            "admin_state_up": true,
            "network_id": "f36ce24b-7ef4-4687-bc02-6f3d5b1a9e34",
            "tenant_id": "50aa68035ae940baa0c463b95c3d0e7d",
            "binding:vnic_type": "normal",
            "device_owner": "",
            "mac_address": "fa:16:3e:a1:8f:b2",
            "fixed_ips": [
                {
                    "subnet_id": "a120640b-6c69-444c-9f24-9598daad14c3",
                    "ip_address": "10.0.12.2"
                }
            ],
            "id": "186d72d2-acb0-4f06-abe6-eb7d2775adbf",
            "security_groups": [
                "8117b434-7172-4012-b637-f8bca59edd5e"
            ],
            "device_id": ""
        }
    }




查看虚拟网卡
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 GET /v2.0/ports/{port_id} 查看虚拟网卡
请求参数

无。

返回参数
字段名 类型 描述 status string 该虚拟网卡的状态 name string 该虚拟网卡的自定义名字
allowed_address_pairs list allowed_address_pairs列表，将允许虚拟网卡以其他IP发包
admin_state_up bool 该虚拟网卡的管理状态 network_id string 该虚拟网卡所属的网络的UUID
tenant_id sting 拥有该虚拟网卡的租户的UUID created_at string 该虚拟网卡的创建时间，为UTC时间
binding:vnic_type string 绑定vNIC类型，可能值有”direct”, “macvtap”和”normal”
device_owner string 使用这个虚拟网卡的实体的UUID mac_address string 该虚拟网卡的MAC地址 id
string 该虚拟网卡的UUID fixed_ips dict 包含两个键，分别为其所在的子网的UUID和CIDR地址
extra_dhcp_opts string DHCP扩展选项 security_groups list 该虚拟网卡应用的安全组规则
device_id string 使用该虚拟网卡的设别（例如虚拟主机）的UUID
请求样例

::

    
    curl -s \
         -X GET `https://bj1.network.api.ustack.com/v2.0/ports/186d72d2-acb0-4f06-abe6-eb7d2775adbf`_ \
         -H "X-Auth-Token: {token_id}" \
         -H "Content-Type: application/json" \
         -H "Accept: application/json"


返回样例 :


::

    {
        "port": {
            "status": "DOWN",
            "name": "myport",
            "allowed_address_pairs": [],
            "binding:disable_anti_spoofing": true,
            "admin_state_up": true,
            "network_id": "f36ce24b-7ef4-4687-bc02-6f3d5b1a9e34",
            "tenant_id": "50aa68035ae940baa0c463b95c3d0e7d",
            "created_at": "2014-05-30T04:15:10.000000",
            "binding:vnic_type": "normal",
            "device_owner": "",
            "mac_address": "fa:16:3e:a1:8f:b2",
            "id": "186d72d2-acb0-4f06-abe6-eb7d2775adbf",
            "fixed_ips": [
                {
                    "subnet_id": "a120640b-6c69-444c-9f24-9598daad14c3",
                    "ip_address": "10.0.12.56"
                }
            ],
            "extra_dhcp_opts": [],
            "security_groups": [
                "8117b434-7172-4012-b637-f8bca59edd5e"
            ],
            "device_id": ""
        }
    }




修改虚拟网卡安全限制
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 PUT /v2.0/ports/{port_id} 修改虚拟网卡安全限制
请求参数
字段名 类型 描述 disable_anti_spoofing bool 虚拟网卡的安全限制
返回参数
字段名 类型 描述 status string 该虚拟网卡的状态 name string 该虚拟网卡的自定义名字
allowed_address_pairs list allowed_address_pairs列表，将允许虚拟网卡以其他IP发包
admin_state_up bool 该虚拟网卡的管理状态 binding:disable_anti_spoofing bool
该虚拟网卡的安全状态 network_id string 该虚拟网卡所属的网络的UUID tenant_id sting
拥有该虚拟网卡的租户的UUID created_at string 该虚拟网卡的创建时间，为UTC时间 binding:vnic_type
string 绑定vNIC类型，可能值有”direct”, “macvtap”和”normal” device_owner string
使用这个虚拟网卡的实体的UUID mac_address string 该虚拟网卡的MAC地址 id string 该虚拟网卡的UUID
fixed_ips dict 包含两个键，分别为其所在的子网的UUID和CIDR地址 extra_dhcp_opts string
DHCP扩展选项 security_groups list 该虚拟网卡应用的安全组规则 device_id string
使用该虚拟网卡的设别（例如虚拟主机）的UUID
请求样例

::

    
    curl -s \
         -X PUT `https://bj1.network.api.ustack.com/v2.0/ports/186d72d2-acb0-4f06-abe6-eb7d2775adbf`_ \
         -H "X-Auth-Token: {token_id}" \
         -H "Content-Type: application/json" \
         -H "Accept: application/json" \
         -d '{
                "port": {
                    "binding:disable_anti_spoofing":"True"
                }
            }'


返回样例 :


::

    {
        "port": {
            "status": "DOWN",
            "name": "myport-new",
            "allowed_address_pairs": [],
            "binding:disable_anti_spoofing": true,
            "admin_state_up": true,
            "network_id": "f36ce24b-7ef4-4687-bc02-6f3d5b1a9e34",
            "tenant_id": "50aa68035ae940baa0c463b95c3d0e7d",
            "created_at": "2014-05-30T04:15:10.000000",
            "binding:vnic_type": "normal",
            "device_owner": "",
            "mac_address": "fa:16:3e:a1:8f:b2",
            "id": "186d72d2-acb0-4f06-abe6-eb7d2775adbf",
            "fixed_ips": [
                {
                    "subnet_id": "a120640b-6c69-444c-9f24-9598daad14c3",
                    "ip_address": "10.0.12.56"
                }
            ],
            "extra_dhcp_opts": [],
            "security_groups": [
                "8117b434-7172-4012-b637-f8bca59edd5e"
            ],
            "device_id": ""
        }
    }




修改虚拟网卡名称
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 PUT /v2.0/ports/{port_id} 修改虚拟网卡名称
请求参数
字段名 类型 描述 name string 虚拟网卡的新的自定义名字
返回参数
字段名 类型 描述 status string 该虚拟网卡的状态 name string 该虚拟网卡的自定义名字
allowed_address_pairs list allowed_address_pairs列表，将允许虚拟网卡以其他IP发包
admin_state_up bool 该虚拟网卡的管理状态 network_id string 该虚拟网卡所属的网络的UUID
tenant_id sting 拥有该虚拟网卡的租户的UUID created_at string 该虚拟网卡的创建时间，为UTC时间
binding:vnic_type string 绑定vNIC类型，可能值有”direct”, “macvtap”和”normal”
device_owner string 使用这个虚拟网卡的实体的UUID mac_address string 该虚拟网卡的MAC地址 id
string 该虚拟网卡的UUID fixed_ips dict 包含两个键，分别为其所在的子网的UUID和CIDR地址
extra_dhcp_opts string DHCP扩展选项 security_groups list 该虚拟网卡应用的安全组规则
device_id string 使用该虚拟网卡的设别（例如虚拟主机）的UUID
请求样例

::

    
    curl -s \
         -X PUT `https://bj1.network.api.ustack.com/v2.0/ports/186d72d2-acb0-4f06-abe6-eb7d2775adbf`_ \
         -H "X-Auth-Token: {token_id}" \
         -H "Content-Type: application/json" \
         -H "Accept: application/json" \
         -d '{
                "port": {
                    "name":"myport-new"
                }
            }'


返回样例 :


::

    {
        "port": {
            "status": "DOWN",
            "name": "myport-new",
            "allowed_address_pairs": [],
            "binding:disable_anti_spoofing": true,
            "admin_state_up": true,
            "network_id": "f36ce24b-7ef4-4687-bc02-6f3d5b1a9e34",
            "tenant_id": "50aa68035ae940baa0c463b95c3d0e7d",
            "created_at": "2014-05-30T04:15:10.000000",
            "binding:vnic_type": "normal",
            "device_owner": "",
            "mac_address": "fa:16:3e:a1:8f:b2",
            "id": "186d72d2-acb0-4f06-abe6-eb7d2775adbf",
            "fixed_ips": [
                {
                    "subnet_id": "a120640b-6c69-444c-9f24-9598daad14c3",
                    "ip_address": "10.0.12.56"
                }
            ],
            "extra_dhcp_opts": [],
            "security_groups": [
                "8117b434-7172-4012-b637-f8bca59edd5e"
            ],
            "device_id": ""
        }
    }




修改虚拟网卡的安全组
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 PUT /v2.0/ports/{port_id} 修改虚拟网卡的安全组
请求参数
字段名 类型 描述 security_groups list 该虚拟网卡应用的新安全组规则
返回参数
字段名 类型 描述 status string 该虚拟网卡的状态 name string 该虚拟网卡的自定义名字
allowed_address_pairs list allowed_address_pairs列表，将允许虚拟网卡以其他IP发包
admin_state_up bool 该虚拟网卡的管理状态 network_id string 该虚拟网卡所属的网络的UUID
tenant_id sting 拥有该虚拟网卡的租户的UUID created_at string 该虚拟网卡的创建时间，为UTC时间
binding:vnic_type string 绑定vNIC类型，可能值有”direct”, “macvtap”和”normal”
device_owner string 使用这个虚拟网卡的实体的UUID mac_address string 该虚拟网卡的MAC地址 id
string 该虚拟网卡的UUID fixed_ips dict 包含两个键，分别为其所在的子网的UUID和CIDR地址
extra_dhcp_opts string DHCP扩展选项 security_groups list 该虚拟网卡应用的安全组规则
device_id string 使用该虚拟网卡的设别（例如虚拟主机）的UUID
请求样例

::

    
    curl -s \
         -X PUT `https://bj1.network.api.ustack.com/v2.0/ports/186d72d2-acb0-4f06-abe6-eb7d2775adbf`_ \
         -H "X-Auth-Token: {token_id}" \
         -H "Content-Type: application/json" \
         -H "Accept: application/json" \
         -d '{
                "port": {
                    "security_groups": [
                        "2385c740-1642-a845-d150-31c110ce8716"
                    ]
                }
            }'


返回样例 :


::

    {
        "port": {
            "status": "DOWN",
            "name": "myport-new",
            "allowed_address_pairs": [],
            "binding:disable_anti_spoofing": true,
            "admin_state_up": true,
            "network_id": "f36ce24b-7ef4-4687-bc02-6f3d5b1a9e34",
            "tenant_id": "50aa68035ae940baa0c463b95c3d0e7d",
            "created_at": "2014-05-30T04:15:10.000000",
            "binding:vnic_type": "normal",
            "device_owner": "",
            "mac_address": "fa:16:3e:a1:8f:b2",
            "id": "186d72d2-acb0-4f06-abe6-eb7d2775adbf",
            "fixed_ips": [
                {
                    "subnet_id": "a120640b-6c69-444c-9f24-9598daad14c3",
                    "ip_address": "10.0.12.56"
                }
            ],
            "extra_dhcp_opts": [],
            "security_groups": [
                "2385c740-1642-a845-d150-31c110ce8716"
            ],
            "device_id": ""
        }
    }




修改虚拟网卡的允许IP
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 PUT /v2.0/ports/{port_id} 修改虚拟网卡的允许IP
请求参数
字段名 类型 描述 allowed_address_pairs list
该虚拟网卡被允许的非系统分配的IP、MAC对，将允许其以这些IP、MAC发包
返回参数
字段名 类型 描述 status string 该虚拟网卡的状态 name string 该虚拟网卡的自定义名字
allowed_address_pairs list allowed_address_pairs列表，将允许虚拟网卡以其他IP发包
admin_state_up bool 该虚拟网卡的管理状态 network_id string 该虚拟网卡所属的网络的UUID
tenant_id sting 拥有该虚拟网卡的租户的UUID created_at string 该虚拟网卡的创建时间，为UTC时间
binding:vnic_type string 绑定vNIC类型，可能值有”direct”, “macvtap”和”normal”
device_owner string 使用这个虚拟网卡的实体的UUID mac_address string 该虚拟网卡的MAC地址 id
string 该虚拟网卡的UUID fixed_ips dict 包含两个键，分别为其所在的子网的UUID和CIDR地址
extra_dhcp_opts string DHCP扩展选项 security_groups list 该虚拟网卡应用的安全组规则
device_id string 使用该虚拟网卡的设别（例如虚拟主机）的UUID
请求样例

::

    
    curl -s \
         -X PUT `https://bj1.network.api.ustack.com/v2.0/ports/186d72d2-acb0-4f06-abe6-eb7d2775adbf`_ \
         -H "X-Auth-Token: {token_id}" \
         -H "Content-Type: application/json" \
         -H "Accept: application/json" \
         -d '{
                "port": {
                    "allowed_address_pairs": [
                        {
                            "ip_address": "10.10.11.5",
                            "mac_address": "fa:16:3e:31:e1:c9"
                        },
                        {
                            "ip_address": "10.10.11.6"
                        }
                    ]
                }
            }'


返回样例 :


::

    {
        "port": {
            "status": "DOWN",
            "name": "myport-new",
            "binding:disable_anti_spoofing": true,
            "allowed_address_pairs": [
                {
                    "ip_address": "10.10.11.5",
                    "mac_address": "fa:16:3e:31:e1:c9"
                },
                {
                    "ip_address": "10.10.11.6",
                    "mac_address": "fa:16:3e:a1:8f:b2"
                }
            ],
            "admin_state_up": true,
            "network_id": "f36ce24b-7ef4-4687-bc02-6f3d5b1a9e34",
            "tenant_id": "50aa68035ae940baa0c463b95c3d0e7d",
            "created_at": "2014-05-30T04:15:10.000000",
            "binding:vnic_type": "normal",
            "device_owner": "",
            "mac_address": "fa:16:3e:a1:8f:b2",
            "id": "186d72d2-acb0-4f06-abe6-eb7d2775adbf",
            "fixed_ips": [
                {
                    "subnet_id": "a120640b-6c69-444c-9f24-9598daad14c3",
                    "ip_address": "10.0.12.56"
                }
            ],
            "extra_dhcp_opts": [],
            "security_groups": [
                "2385c740-1642-a845-d150-31c110ce8716"
            ],
            "device_id": ""
        }
    }




启用/禁用虚拟网卡
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 PUT /v2.0/ports/{port_id} 启用/禁用虚拟网卡
请求参数
字段名 类型 描述 admin_state_up bool True/False
返回参数
字段名 类型 描述 status string 该虚拟网卡的状态 name string 该虚拟网卡的自定义名字
allowed_address_pairs list allowed_address_pairs列表，将允许虚拟网卡以其他IP发包
admin_state_up bool 该虚拟网卡的管理状态 network_id string 该虚拟网卡所属的网络的UUID
tenant_id sting 拥有该虚拟网卡的租户的UUID created_at string 该虚拟网卡的创建时间，为UTC时间
binding:vnic_type string 绑定vNIC类型，可能值有”direct”, “macvtap”和”normal”
device_owner string 使用这个虚拟网卡的实体的UUID mac_address string 该虚拟网卡的MAC地址 id
string 该虚拟网卡的UUID fixed_ips dict 包含两个键，分别为其所在的子网的UUID和CIDR地址
extra_dhcp_opts string DHCP扩展选项 security_groups list 该虚拟网卡应用的安全组规则
device_id string 使用该虚拟网卡的设别（例如虚拟主机）的UUID
请求样例

::

    
    curl -s \
         -X PUT `https://bj1.network.api.ustack.com/v2.0/ports/186d72d2-acb0-4f06-abe6-eb7d2775adbf`_ \
         -H "X-Auth-Token: {token_id}" \
         -H "Content-Type: application/json" \
         -H "Accept: application/json" \
         -d '{
                "port": {
                    "admin_state_up":"false"
                }
            }'


返回样例 :


::

    {
        "port": {
            "status": "DOWN",
            "name": "myport-new",
            "allowed_address_pairs": [],
            "binding:disable_anti_spoofing": true,
            "admin_state_up": false,
            "network_id": "f36ce24b-7ef4-4687-bc02-6f3d5b1a9e34",
            "tenant_id": "50aa68035ae940baa0c463b95c3d0e7d",
            "created_at": "2014-05-30T04:15:10.000000",
            "binding:vnic_type": "normal",
            "device_owner": "",
            "mac_address": "fa:16:3e:a1:8f:b2",
            "id": "186d72d2-acb0-4f06-abe6-eb7d2775adbf",
            "fixed_ips": [
                {
                    "subnet_id": "a120640b-6c69-444c-9f24-9598daad14c3",
                    "ip_address": "10.0.12.56"
                }
            ],
            "extra_dhcp_opts": [],
            "security_groups": [
                "2385c740-1642-a845-d150-31c110ce8716"
            ],
            "device_id": ""
        }
    }




删除虚拟网卡
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 DELETE /v2.0/ports/{port_id} 删除虚拟网卡
请求参数

无。

返回参数

无。

请求样例

::

    
    curl -i \
         -X DELETE `https://bj1.network.api.ustack.com/v2.0/ports/186d72d2-acb0-4f06-abe6-eb7d2775adbf`_ \
         -H "X-Auth-Token: {token_id}" \
         -H "Content-Type: application/json" \
         -H "Accept: application/json"


返回样例 :


::

    HTTP/1.1 204 No Content
    Content-Length: 0
    Date: Fri, 30 May 2014 04:26:09 GMT


.. _neutron-security-groups:

安全组 (Security Groups)
----------------------------------------------------------



查看所有安全组
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 GET /v2.0/security-groups 查看所有安全组
请求参数

无。

返回参数
字段名 类型 描述 description string 该安全组的描述 tenant_id sting 拥有该安全组的租户的UUID
created_at string 该安全组的创建时间，为UTC时间 security_group_rules string
该安全组下的规则，具体见安全组规则相关API id string 该安全组的UUID name string 该安全组的自定义名字
请求样例

::

    
    curl -s \
         -X GET `https://bj1.network.api.ustack.com/v2.0/security-groups`_ \
         -H "X-Auth-Token: {token_id}" \
         -H "Content-Type: application/json" \
         -H "Accept: application/json"


返回样例 :


::

    {
        "security_groups": [
            {
                "description": "default",
                "tenant_id": "50aa68035ae940baa0c463b95c3d0e7d",
                "created_at": "2014-05-21T03:50:00.000000",
                "security_group_rules": [
                    {
                        "remote_group_id": null,
                        "direction": "egress",
                        "remote_ip_prefix": null,
                        "protocol": null,
                        "tenant_id": "50aa68035ae940baa0c463b95c3d0e7d",
                        "port_range_max": null,
                        "security_group_id": "8117b434-7172-4012-b637-f8bca59edd5e",
                        "port_range_min": null,
                        "ethertype": "IPv4",
                        "id": "253dd45f-e7ed-49ee-a37d-c4b3a7dadb73"
                    },
                    {
                        "remote_group_id": null,
                        "direction": "ingress",
                        "remote_ip_prefix": null,
                        "protocol": "tcp",
                        "tenant_id": "50aa68035ae940baa0c463b95c3d0e7d",
                        "port_range_max": 80,
                        "security_group_id": "8117b434-7172-4012-b637-f8bca59edd5e",
                        "port_range_min": 80,
                        "ethertype": "IPv4",
                        "id": "869ecd5b-ed92-41ea-bfe4-e0a6f8d5e323"
                    }
                ],
                "id": "8117b434-7172-4012-b637-f8bca59edd5e",
                "name": "default"
            }
        ]
    }




创建安全组
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 POST /v2.0/security-groups 创建安全组
请求参数
字段名 类型 描述 description string 该安全组的描述 name string 该安全组的自定义名字
返回参数
字段名 类型 描述 description string 该安全组的描述 tenant_id sting 拥有该安全组的租户的UUID
security_group_rules string 该安全组下的规则，具体见安全组规则相关API id string 该安全组的UUID
name string 该安全组的自定义名字
请求样例

::

    
    curl -s \
         -X POST `https://bj1.network.api.ustack.com/v2.0/security-groups`_ \
         -H "X-Auth-Token: {token_id}" \
         -H "Content-Type: application/json" \
         -H "Accept: application/json" \
         -d '{
                "security_group": {
                    "name": "mysg"
                }
            }'


返回样例 :


::

    {
        "security_group": {
            "id": "dd7732fd-b56b-481c-b256-8a350fa71c6d",
            "tenant_id": "50aa68035ae940baa0c463b95c3d0e7d",
            "name": "mysg",
            "security_group_rules": [
                {
                    "remote_group_id": null,
                    "direction": "egress",
                    "remote_ip_prefix": null,
                    "protocol": null,
                    "tenant_id": "50aa68035ae940baa0c463b95c3d0e7d",
                    "port_range_max": null,
                    "security_group_id": "dd7732fd-b56b-481c-b256-8a350fa71c6d",
                    "port_range_min": null,
                    "ethertype": "IPv4",
                    "id": "fd80f0ad-877d-461b-aaf6-372017388ba1"
                },
                {
                    "remote_group_id": null,
                    "direction": "ingress",
                    "remote_ip_prefix": null,
                    "protocol": "icmp",
                    "tenant_id": "50aa68035ae940baa0c463b95c3d0e7d",
                    "port_range_max": 1,
                    "security_group_id": "dd7732fd-b56b-481c-b256-8a350fa71c6d",
                    "port_range_min": 1,
                    "ethertype": "IPv4",
                    "id": "be72a180-11bc-4f1b-992e-aa4fff9da286"
                },
                {
                    "remote_group_id": null,
                    "direction": "ingress",
                    "remote_ip_prefix": null,
                    "protocol": "tcp",
                    "tenant_id": "50aa68035ae940baa0c463b95c3d0e7d",
                    "port_range_max": 80,
                    "security_group_id": "dd7732fd-b56b-481c-b256-8a350fa71c6d",
                    "port_range_min": 80,
                    "ethertype": "IPv4",
                    "id": "566dab40-68f7-49d3-b013-8fd80ff13ebf"
                },
                {
                    "remote_group_id": null,
                    "direction": "ingress",
                    "remote_ip_prefix": null,
                    "protocol": "tcp",
                    "tenant_id": "50aa68035ae940baa0c463b95c3d0e7d",
                    "port_range_max": 443,
                    "security_group_id": "dd7732fd-b56b-481c-b256-8a350fa71c6d",
                    "port_range_min": 443,
                    "ethertype": "IPv4",
                    "id": "cb688622-41be-4cfb-8518-4cccc58d2964"
                },
                {
                    "remote_group_id": null,
                    "direction": "ingress",
                    "remote_ip_prefix": null,
                    "protocol": "tcp",
                    "tenant_id": "50aa68035ae940baa0c463b95c3d0e7d",
                    "port_range_max": 22,
                    "security_group_id": "dd7732fd-b56b-481c-b256-8a350fa71c6d",
                    "port_range_min": 22,
                    "ethertype": "IPv4",
                    "id": "6e4222f5-8a81-4b0a-bb75-03a89ab699e7"
                }
            ],
            "description": ""
        }
    }




查看安全组
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 GET /v2.0/security-groups/{security_group_id} 查看安全组
请求参数

无。

返回参数
字段名 类型 描述 description string 该安全组的描述 tenant_id sting 拥有该安全组的租户的UUID
created_at string 该安全组的创建时间，为UTC时间 security_group_rules string
该安全组下的规则，具体见安全组规则相关API id string 该安全组的UUID name string 该安全组的自定义名字
请求样例

::

    
    curl -s \
         -X GET `https://bj1.network.api.ustack.com/v2.0/security-groups/dd7732fd-b56b-481c-b256-8a350fa71c6d`_ \
         -H "X-Auth-Token: {token_id}" \
         -H "Content-Type: application/json" \
         -H "Accept: application/json"


返回样例 :


::

    {
        "security_group": {
            "description": "my sg",
            "tenant_id": "50aa68035ae940baa0c463b95c3d0e7d",
            "created_at": "2014-05-30T05:25:01.000000",
            "security_group_rules": [
                {
                    "remote_group_id": null,
                    "direction": "ingress",
                    "remote_ip_prefix": null,
                    "protocol": "tcp",
                    "tenant_id": "50aa68035ae940baa0c463b95c3d0e7d",
                    "port_range_max": 22,
                    "security_group_id": "dd7732fd-b56b-481c-b256-8a350fa71c6d",
                    "port_range_min": 22,
                    "ethertype": "IPv6",
                    "id": "1b9e1015-1393-4f08-90f9-bc276467e94a"
                },
                {
                    "remote_group_id": null,
                    "direction": "ingress",
                    "remote_ip_prefix": null,
                    "protocol": "tcp",
                    "tenant_id": "50aa68035ae940baa0c463b95c3d0e7d",
                    "port_range_max": 80,
                    "security_group_id": "dd7732fd-b56b-481c-b256-8a350fa71c6d",
                    "port_range_min": 80,
                    "ethertype": "IPv4",
                    "id": "566dab40-68f7-49d3-b013-8fd80ff13ebf"
                },
                {
                    "remote_group_id": null,
                    "direction": "ingress",
                    "remote_ip_prefix": null,
                    "protocol": "tcp",
                    "tenant_id": "50aa68035ae940baa0c463b95c3d0e7d",
                    "port_range_max": 22,
                    "security_group_id": "dd7732fd-b56b-481c-b256-8a350fa71c6d",
                    "port_range_min": 22,
                    "ethertype": "IPv4",
                    "id": "6e4222f5-8a81-4b0a-bb75-03a89ab699e7"
                },
                {
                    "remote_group_id": null,
                    "direction": "ingress",
                    "remote_ip_prefix": null,
                    "protocol": "icmp",
                    "tenant_id": "50aa68035ae940baa0c463b95c3d0e7d",
                    "port_range_max": 1,
                    "security_group_id": "dd7732fd-b56b-481c-b256-8a350fa71c6d",
                    "port_range_min": 1,
                    "ethertype": "IPv4",
                    "id": "be72a180-11bc-4f1b-992e-aa4fff9da286"
                },
                {
                    "remote_group_id": null,
                    "direction": "ingress",
                    "remote_ip_prefix": null,
                    "protocol": "tcp",
                    "tenant_id": "50aa68035ae940baa0c463b95c3d0e7d",
                    "port_range_max": 443,
                    "security_group_id": "dd7732fd-b56b-481c-b256-8a350fa71c6d",
                    "port_range_min": 443,
                    "ethertype": "IPv4",
                    "id": "cb688622-41be-4cfb-8518-4cccc58d2964"
                },
                {
                    "remote_group_id": null,
                    "direction": "egress",
                    "remote_ip_prefix": null,
                    "protocol": null,
                    "tenant_id": "50aa68035ae940baa0c463b95c3d0e7d",
                    "port_range_max": null,
                    "security_group_id": "dd7732fd-b56b-481c-b256-8a350fa71c6d",
                    "port_range_min": null,
                    "ethertype": "IPv4",
                    "id": "fd80f0ad-877d-461b-aaf6-372017388ba1"
                }
            ],
            "id": "dd7732fd-b56b-481c-b256-8a350fa71c6d",
            "name": "mysg"
        }
    }




删除安全组
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 DELETE /v2.0/security-groups/{security_group_id} 删除安全组
请求参数

无。

返回参数

无。

请求样例

::

    
    curl -s \
         -X DELETE `https://bj1.network.api.ustack.com/v2.0/security-groups/dd7732fd-b56b-481c-b256-8a350fa71c6d`_ \
         -H "X-Auth-Token: {token_id}" \
         -H "Content-Type: application/json" \
         -H "Accept: application/json"


返回样例 :


::

    HTTP/1.1 204 No Content
    Content-Length: 0
    Date: Fri, 30 May 2014 05:33:55 GMT




查看所有安全组规则
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 GET /v2.0/security-group-rules 查看所有安全组规则
请求参数

无。

返回参数
字段名 类型 描述 remote_group_id string Remote Group的UUID direction sting
流量方向 protocol string 协议类型 tenant_id sting 拥有该安全组规则的租户的UUID
port_range_max string 端口范围上限 security_group_id string 相关连的Security
Group的UUID port_range_min string 端口范围下限 remote_ip_prefix string 远程IP前缀
id string 该安全组规则的UUID ethertype string IP协议类型
请求样例

::

    
    curl -s \
         -X GET `https://bj1.network.api.ustack.com/v2.0/security-group-rules`_ \
         -H "X-Auth-Token: {token_id}" \
         -H "Content-Type: application/json" \
         -H "Accept: application/json"


返回样例 :


::

    {
        "security_group_rules": [
            {
                "remote_group_id": null,
                "direction": "ingress",
                "protocol": "tcp",
                "tenant_id": "50aa68035ae940baa0c463b95c3d0e7d",
                "port_range_max": 22,
                "security_group_id": "8fe6c994-4d72-47aa-9198-4427c2d64123",
                "port_range_min": 22,
                "remote_ip_prefix": null,
                "id": "00e92378-e5f9-4b44-bc3c-b80a2a118afe",
                "ethertype": "IPv4"
            },
            {
                "remote_group_id": null,
                "direction": "egress",
                "protocol": null,
                "tenant_id": "50aa68035ae940baa0c463b95c3d0e7d",
                "port_range_max": null,
                "security_group_id": "8117b434-7172-4012-b637-f8bca59edd5e",
                "port_range_min": null,
                "remote_ip_prefix": null,
                "id": "253dd45f-e7ed-49ee-a37d-c4b3a7dadb73",
                "ethertype": "IPv4"
            },
            {
                "remote_group_id": null,
                "direction": "ingress",
                "protocol": "tcp",
                "tenant_id": "50aa68035ae940baa0c463b95c3d0e7d",
                "port_range_max": 80,
                "security_group_id": "8fe6c994-4d72-47aa-9198-4427c2d64123",
                "port_range_min": 80,
                "remote_ip_prefix": null,
                "id": "2f2779b3-8ee5-4297-8bf6-c37f81496bb0",
                "ethertype": "IPv4"
            },
            {
                "remote_group_id": null,
                "direction": "ingress",
                "protocol": "tcp",
                "tenant_id": "50aa68035ae940baa0c463b95c3d0e7d",
                "port_range_max": 234,
                "security_group_id": "8fe6c994-4d72-47aa-9198-4427c2d64123",
                "port_range_min": 234,
                "remote_ip_prefix": "0.0.0.0",
                "id": "44e9f3ac-282d-43f5-9f15-29165df2ca1a",
                "ethertype": "IPv4"
            },
            {
                "remote_group_id": null,
                "direction": "ingress",
                "protocol": "icmp",
                "tenant_id": "50aa68035ae940baa0c463b95c3d0e7d",
                "port_range_max": 1,
                "security_group_id": "8fe6c994-4d72-47aa-9198-4427c2d64123",
                "port_range_min": 1,
                "remote_ip_prefix": null,
                "id": "4a59b007-dab8-4a0e-b739-d96318840112",
                "ethertype": "IPv4"
            },
            {
                "remote_group_id": null,
                "direction": "egress",
                "protocol": null,
                "tenant_id": "50aa68035ae940baa0c463b95c3d0e7d",
                "port_range_max": null,
                "security_group_id": "8fe6c994-4d72-47aa-9198-4427c2d64123",
                "port_range_min": null,
                "remote_ip_prefix": null,
                "id": "6cc32e82-198d-418a-a90c-cd302f423e9e",
                "ethertype": "IPv4"
            }
        ]
    }




创建安全组规则
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 POST /v2.0/security-group-rules 创建安全组规则
请求参数
字段名 类型 描述 remote_group_id string Remote Group的UUID direction sting
流量方向 protocol string 协议类型 port_range_max string 端口范围上限
security_group_id string 相关连的Security Group的UUID port_range_min string
端口范围下限 remote_ip_prefix string 远程IP前缀 ethertype string IP协议类型
返回参数
字段名 类型 描述 remote_group_id string Remote Group的UUID direction sting
流量方向 protocol string 协议类型 tenant_id sting 拥有该安全组规则的租户的UUID
port_range_max string 端口范围上限 security_group_id string 相关连的Security
Group的UUID port_range_min string 端口范围下限 remote_ip_prefix string 远程IP前缀
id string 该安全组规则的UUID ethertype string IP协议类型
请求样例

::

    
    curl -s \
         -X POST `https://bj1.network.api.ustack.com/v2.0/security-group-rules`_ \
         -H "X-Auth-Token: {token_id}" \
         -H "Content-Type: application/json" \
         -H "Accept: application/json" \
         -d '{
                "security_group_rule": {
                    "direction": "ingress",
                    "port_range_min": "234",
                    "remote_ip_prefix": "0.0.0.0",
                    "ethertype":"IPv4",
                    "port_range_max": "234",
                    "protocol": "tcp",
                    "security_group_id": "8fe6c994-4d72-47aa-9198-4427c2d64123"
                }
            }'


返回样例 :


::

    {
        "security_group_rule": {
            "remote_group_id": null,
            "direction": "ingress",
            "protocol": "tcp",
            "tenant_id": "50aa68035ae940baa0c463b95c3d0e7d",
            "port_range_max": 234,
            "security_group_id": "8fe6c994-4d72-47aa-9198-4427c2d64123",
            "port_range_min": 234,
            "remote_ip_prefix": "0.0.0.0",
            "id": "44e9f3ac-282d-43f5-9f15-29165df2ca1a",
            "ethertype": "IPv4"
        }
    }




查看安全组规则
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 GET /v2.0/security-group-rules/{rules-security-groups-
id} 查看安全组规则
请求参数

无。

返回参数
字段名 类型 描述 remote_group_id string Remote Group的UUID direction sting
流量方向 protocol string 协议类型 tenant_id sting 拥有该安全组规则的租户的UUID
port_range_max string 端口范围上限 security_group_id string 相关连的Security
Group的UUID port_range_min string 端口范围下限 remote_ip_prefix string 远程IP前缀
id string 该安全组规则的UUID ethertype string IP协议类型
请求样例

::

    
    curl -s \
         -X POST `https://bj1.network.api.ustack.com/v2.0/security-group-rules/44e9f3ac-282d-43f5-9f15-29165df2ca1a`_ \
         -H "X-Auth-Token: {token_id}" \
         -H "Content-Type: application/json" \
         -H "Accept: application/json"


返回样例 :


::

    {
        "security_group_rule": {
            "remote_group_id": null,
            "direction": "ingress",
            "protocol": "tcp",
            "tenant_id": "50aa68035ae940baa0c463b95c3d0e7d",
            "port_range_max": 234,
            "security_group_id": "8fe6c994-4d72-47aa-9198-4427c2d64123",
            "port_range_min": 234,
            "remote_ip_prefix": "0.0.0.0",
            "id": "44e9f3ac-282d-43f5-9f15-29165df2ca1a",
            "ethertype": "IPv4"
        }
    }




删除安全组规则
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 DELETE /v2.0/security-group-rules/{rules-security-
groups-id} 删除安全组规则
请求参数

无。

返回参数

无。

请求样例

::

    
    curl -s \
         -X DELETE `https://bj1.network.api.ustack.com/v2.0/security-group-rules/44e9f3ac-282d-43f5-9f15-29165df2ca1a`_ \
         -H "X-Auth-Token: {token_id}" \
         -H "Content-Type: application/json" \
         -H "Accept: application/json"


返回样例 :


::

    HTTP/1.1 204 No Content
    Content-Length: 0
    Date: Fri, 30 May 2014 05:52:49 GMT




负载均衡器 (LoadBalancer)
--------------------------------------------------------



查看所有负载均衡器
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 GET /v2.0/lbaas/loadbalancers 查看所有负载均衡器
请求参数

无。

返回参数
字段名 类型 描述 id string 该负载均衡器的ID vip_network_id string 该负载均衡器的VIP所处网络ID
vip_subnet_id string(optional) 该负载均衡器的VIP所处子网ID,当且仅当指定时具有返回值
vip_address string 该负载均衡器的VIP地址 vip_port_id string 该负载均衡器的Port ID
securitygroup_id string 该负载均衡器所处安全组ID admin_state_up bool 负载均衡器的管理状态
status string 该负载均衡器的状态信息 name string 该负载均衡器的自定义名字 description string
该负载均衡器的描述 tenant_id sting 拥有该负载均衡器的租户的ID listener_ids list
该负载均衡器下的所有监听器的ID列表 created_at string 该负载均衡器的创建时间
请求样例

::

    
    curl -s \
         -X GET `https://bj1.network.api.ustack.com/v2.0/lbaas/loadbalancers`_ \
         -H "X-Auth-Token: {token_id}" \
         -H "Content-Type: application/json" \
         -H "Accept: application/json"


返回样例 :


::

    {
         "loadbalancers": [
              {
                   "status": "ACTIVE",
                   "description": "",
                   "admin_state_up": true,
                   "tenant_id": "549c2c0713214f00aba4f783934fa3e2",
                   "vip_address": "10.0.0.109",
                   "vip_network_id": "de28919d-8c56-48d2-a25a-1b132d2af826",
                   "vip_subnet_id": "6bc4c524-b4d8-4612-b4bd-88ca7e659198",
                   "created_at": "2014-12-08T13:43:07.000000",
                   "securitygroup_id": "dcf2650d-8d58-4df9-93fc-9b99cba0fa4c",
                   "vip_port_id": "f3f73083-199f-42c0-b66b-d20a0501f965",
                   "listener_ids": [
                       "9715ab48-c612-4be1-a04d-127ab7f953f3",
                       "2fd7d171-15f7-41ec-b080-3e7882f3ce51"
                   ],
                   "id": "ff840b71-7ebf-474c-8912-70160a369e22",
                   "name": ""
             },
             {
                  "status": "ACTIVE",
                  "description": "",
                  "admin_state_up": true,
                  "tenant_id": "549c2c0713214f00aba4f783934fa3e2",
                  "vip_address": "10.0.0.11",
                  "vip_network_id": "de28919d-8c56-48d2-a25a-1b132d2af826",
                  "securitygroup_id": "dcf2650d-8d58-4df9-93fc-9b99cba0fa4c",
                  "listener_ids": [
                      "2fd7d171-15f7-41ec-b080-3e7882f3ce51"
                  ],
                  "created_at": "2014-12-08T13:43:07.000000",
                  "vip_port_id": "f3f73083-199f-42c0-b66b-d20a0501f96b",
                  "id": "27f91a2a-3498-4aab-ad63-08bd61e6be3d",
                  "name": ""
            }
         ]
    }




创建负载均衡器
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 POST /v2.0/lbaas/loadbalancers 创建负载均衡器
请求参数
字段名 类型 描述 vip_network_id string 该负载均衡器所处网络ID securitygroup_id string
该负载均衡器所属安全组ID vip_subnet_id string(optional) 该负载均衡器所处子网ID vip_address
string(optional) 该负载均衡器的VIP地址，如不指定则自动分配 name string(optional)
该负载均衡器的名字 description string(optional) 该负载均衡器的描述
返回参数
字段名 类型 描述 id string 该负载均衡器的ID vip_network_id string 该负载均衡器的VIP所处网络ID
vip_subnet_id string(optional) 该负载均衡器的VIP所处子网ID,当且仅当指定时具有返回值
vip_address string 该负载均衡器的VIP地址 vip_port_id string 该负载均衡器的Port ID
securitygroup_id string 该负载均衡器所处安全组ID admin_state_up bool 负载均衡器的管理状态
status string 该负载均衡器的状态信息 name string 该负载均衡器的自定义名字 description string
该负载均衡器的描述 tenant_id sting 拥有该负载均衡器的租户的ID listener_ids list
该负载均衡器下的所有监听器的ID列表 created_at string 该负载均衡器的创建时间
请求样例

::

    
    curl -s \
         -X POST `https://bj1.network.api.ustack.com/v2.0/lbaas/loadbalancers`_ \
         -H "X-Auth-Token: {token_id}" \
         -H "Content-Type: application/json" \
         -H "Accept: application/json" \
         -d "{
                "loadbalancer": {
                    "vip_network_id": "de28919d-8c56-48d2-a25a-1b132d2af826",
                    "vip_subnet_id": "6bc4c524-b4d8-4612-b4bd-88ca7e659198",
                    "securitygroup_id": "dcf2650d-8d58-4df9-93fc-9b99cba0fa4c",
                    "admin_state_up": true
                }
            }"


返回样例 :


::

    {
      "loadbalancer": {
           "status": "PENDING_CREATE",
           "description": "",
           "admin_state_up": true,
           "tenant_id": "549c2c0713214f00aba4f783934fa3e2",
           "vip_address": "10.0.0.115",
           "vip_network_id": "de28919d-8c56-48d2-a25a-1b132d2af826",
           "vip_subnet_id": "6bc4c524-b4d8-4612-b4bd-88ca7e659198",
           "vip_port_id": "f3f73083-199f-42c0-b66b-d20a0501f965",
           "securitygroup_id": "dcf2650d-8d58-4df9-93fc-9b99cba0fa4c",
           "id": "3345fb1a-ea77-4773-83d4-913c13e5438a",
           "created_at": "2014-12-08T15:16:56.483887",
           "listener_ids": [],
           "name": ""
      }
    }




更新负载均衡器
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 PUT /v2.0/lbaas/loadbalancers/{loadbalancer_id}
更新负载均衡器
请求参数
字段名 类型 描述 securitygroup_id string(optional) 该负载均衡器的安全组ID name
string(optional) 该负载均衡器的名字 description string(optional) 该负载均衡器的描述
返回参数
字段名 类型 描述 id string 该负载均衡器的ID vip_network_id string 该负载均衡器的VIP所处网络ID
vip_subnet_id string(optional) 该负载均衡器的VIP所处子网ID,当且仅当指定时具有返回值
vip_address string 该负载均衡器的VIP地址 vip_port_id string 该负载均衡器的Port ID
securitygroup_id string 该负载均衡器所处安全组ID admin_state_up bool 负载均衡器的管理状态
status string 该负载均衡器的状态信息 name string 该负载均衡器的自定义名字 description string
该负载均衡器的描述 tenant_id sting 拥有该负载均衡器的租户的ID listener_ids list
该负载均衡器下的所有监听器的ID列表 created_at string 该负载均衡器的创建时间
请求样例

::

    
    curl -s \
         -X PUT `https://bj1.network.api.ustack.com/v2.0/lbaas/loadbalancers/878442a9-7540-4d18-96b3-47666204d0db`_ \
         -H "X-Auth-Token: {token_id}" \
         -H "Content-Type: application/json" \
         -H "Accept: application/json" \
         -d '{
                "loadbalancer": {
                    "name": "A",
                    "admin_state_up": true
                }
            }'


返回样例 :


::

    {
      "loadbalancer":
          {
              "status": "PENDING_UPDATE",
              "description": "",
              "admin_state_up": true,
              "tenant_id": "549c2c0713214f00aba4f783934fa3e2",
              "vip_address": "10.0.0.111",
              "vip_network_id": "de28919d-8c56-48d2-a25a-1b132d2af826",
              "vip_subnet_id": "6bc4c524-b4d8-4612-b4bd-88ca7e659198",
              "vip_port_id": "f3f73083-199f-42c0-b66b-d20a0501f965",
              "securitygroup_id": "dcf2650d-8d58-4df9-93fc-9b99cba0fa4c",
              "id": "878442a9-7540-4d18-96b3-47666204d0db",
              "created_at": "2014-12-08T15:16:56.483887",
              "listener_ids": [],
              "name": "A"
          }
    }




查看负载均衡器
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 GET /v2.0/lbaas/loadbalancers/{loadbalancer_id}
查看指定的负载均衡器
请求参数

无。

返回参数
字段名 类型 描述 id string 该负载均衡器的ID vip_network_id string 该负载均衡器的VIP所处网络ID
vip_subnet_id string(optional) 该负载均衡器的VIP所处子网ID,当且仅当指定时具有返回值
vip_address string 该负载均衡器的VIP地址 vip_port_id string 该负载均衡器的Port ID
securitygroup_id string 该负载均衡器所处安全组ID admin_state_up bool 负载均衡器的管理状态
status string 该负载均衡器的状态信息 name string 该负载均衡器的自定义名字 description string
该负载均衡器的描述 tenant_id sting 拥有该负载均衡器的租户的ID listener_ids list
该负载均衡器下的所有监听器的ID列表 created_at string 该负载均衡器的创建时间
请求样例

::

    
    curl -s \
         -X GET `https://bj1.network.api.ustack.com/v2.0/lbaas/loadbalancers/ff840b71-7ebf-474c-8912-70160a369e22`_ \
         -H "X-Auth-Token: {token_id}" \
         -H "Content-Type: application/json" \
         -H "Accept: application/json"


返回样例 :


::

    {
      "loadbalancer": {
          "status": "ACTIVE",
          "description": "",
          "admin_state_up": true,
          "tenant_id": "549c2c0713214f00aba4f783934fa3e2",
          "vip_address": "10.0.0.109",
          "vip_network_id": "de28919d-8c56-48d2-a25a-1b132d2af826",
          "vip_subnet_id": "6bc4c524-b4d8-4612-b4bd-88ca7e659198",
          "vip_port_id": "f3f73083-199f-42c0-b66b-d20a0501f965",
          "securitygroup_id": "dcf2650d-8d58-4df9-93fc-9b99cba0fa4c",
          "id": "ff840b71-7ebf-474c-8912-70160a369e22",
          "created_at": "2014-12-08T15:16:56.483887",
          "listener_ids": [
              "9715ab48-c612-4be1-a04d-127ab7f953f3",
              "2fd7d171-15f7-41ec-b080-3e7882f3ce51"
           ],
          "name": ""
      }
    }




删除负载均衡器
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 DELETE /v2.0/lbaas/loadbalancers/{loadbalancer_id}
删除负载均衡器
请求参数

无。

返回参数

无。

请求样例

::

    
    curl -s \
         -X DELETE `https://bj1.network.api.ustack.com/v2.0/lbaas/loadbalancers/e6ae2d67-61f0-471b-82e7-47a9c24cb6d7`_ \
         -H "X-Auth-Token: {token_id}" \
         -H "Content-Type: application/json" \
         -H "Accept: application/json"


返回样例 :


::

    HTTP/1.1 204 No Content
    Content-Length: 0
    Date: Mon, 20 Oct 2014 08:33:08 GMT




监听器 (Listener)
----------------------------------------------



查看所有监听器
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 GET /v2.0/lbaas/listeners 查看所有监听器
请求参数

无。

返回参数
字段名 类型 描述 id string 该监听器的ID loadbalancer_id sting 拥有该监听器的负载均衡器ID
protocol string 该监听器监听的协议，目前支持TCP、HTTP protocol_port string 该监听器监听的端口号
connection_limit int [5000,10000,20000,40000] 该监听器的最大连接数限制，默认值5000
default_pool_id string 该监听器的默认资源池ID l7policy_ids list 属于该监听器的7层策略ID列表
admin_state_up bool 监听器的管理状态 status string 该监听器的状态信息 name string
该监听器的名字 description string 该监听器的描述 tenant_id sting 拥有该监听器的租户的UUID
created_at sting 该监听器的创建时间
请求样例

::

    
    curl -s \
         -X GET `https://bj1.network.api.ustack.com/v2.0/lbaas/listeners`_ \
         -H "X-Auth-Token: {token_id}" \
         -H "Content-Type: application/json" \
         -H "Accept: application/json"


返回样例 :


::

    {
      "listeners": [
          {
           "status": "ACTIVE",
           "protocol_port": 80,
           "protocol": "HTTP",
           "description": "",
           "tenant_id": "549c2c0713214f00aba4f783934fa3e2",
           "admin_state_up": true,
           "connection_limit": 5000,
           "id": "858bf460-5003-4f62-8b84-b3d446ff03f1",
           "l7policy_ids": [
                       "dea8dff9-3874-4f91-bc5a-5af7a8a64e22",
                       "bbee511c-19e3-47c0-b6bd-5b63c38f8414"
                       ],
           "default_pool_id": null,
           "created_at": "2014-12-08T00:07:45.000000",
           "loadbalancer_id": "878442a9-7540-4d18-96b3-47666204d0db",
           "name": ""
         }，
         {
          "status": "ACTIVE",
          "protocol_port": 35,
          "protocol": "HTTP",
          "description": "",
          "tenant_id": "549c2c0713214f00aba4f783934fa3e2",
          "admin_state_up": true,
          "connection_limit": 10000,
          "id": "800c71f4-e63e-4276-a82d-bd28d8689a6e",
          "l7policy_ids": [],
          "created_at": "2014-12-08T00:07:45.000000",
          "default_pool_id": null,
          "loadbalancer_id": "878442a9-7540-4d18-96b3-47666204d0db",
          "name": ""
         }
      ]
    }




查看指定负载均衡器下所有监听器
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

(注意请求URL和返回结果的Key与上述有所不同)
HTTP方法 URI路径 描述 GET
/v2.0/lbaas/loadbalancers/{loadbalancer_id}/lbaas_listeners
查看指定负载均衡器下所有监听器
请求参数

无。

返回参数
字段名 类型 描述 id string 该监听器的ID loadbalancer_id sting 拥有该监听器的负载均衡器ID
protocol string 该监听器监听的协议，目前支持TCP、HTTP protocol_port string 该监听器监听的端口号
connection_limit int [5000,10000,20000,40000] 该监听器的最大连接数限制，默认值5000
default_pool_id string 该监听器的默认资源池ID l7policy_ids list 属于该监听器的7层策略ID列表
admin_state_up bool 监听器的管理状态 status string 该监听器的状态信息 name string
该监听器的名字 description string 该监听器的描述 tenant_id sting 拥有该监听器的租户的UUID
created_at sting 该监听器的创建时间
请求样例

::

    
    curl -s \
         -X GET `https://bj1.network.api.ustack.com/v2.0/lbaas/loadbalancers/878442a9-7540-4d18-96b3-47666204d0db/lbaas_listeners`_ \
         -H "X-Auth-Token: {token_id}" \
         -H "Content-Type: application/json" \
         -H "Accept: application/json"


返回样例 :


::

    {
      "lbaas_listeners": [
          {
              "status": "ACTIVE",
              "protocol_port": 80,
              "protocol": "HTTP",
              "description": "",
              "tenant_id": "549c2c0713214f00aba4f783934fa3e2",
              "admin_state_up": true,
              "connection_limit": 10000,
              "id": "858bf460-5003-4f62-8b84-b3d446ff03f1",
              "l7policy_ids": [
                           "dea8dff9-3874-4f91-bc5a-5af7a8a64e22",
                           "bbee511c-19e3-47c0-b6bd-5b63c38f8414"
                          ],
              "default_pool_id": null,
              "created_at": "2014-12-08T00:07:45.000000",
              "loadbalancer_id": "878442a9-7540-4d18-96b3-47666204d0db",
              "name": ""
           }
      ]
    }




创建监听器
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 POST /v2.0/lbaas/listeners 创建监听器
请求参数
字段名 类型 描述 loadbalancer_id string 该监听器所属负载均衡器的ID protocol string
该监听器监听的协议，目前支持TCP、HTTP protocol_port string 该监听器监听的端口 connection_limit
int [5000,10000,20000,40000] 该监听器的最大连接数限制，默认值5000 default_pool_id
string(optional) 该监听器的默认资源池 admin_state_up string(optional) 该监听器的管理状态
name string(optional) 该监听器的自定义名字 description string(optional) 该监听器的描述
created_at sting 该监听器的创建时间
返回参数
字段名 类型 描述 id string 该监听器的ID loadbalancer_id sting 拥有该监听器的负载均衡器ID
protocol string 该监听器监听的协议，目前支持TCP、HTTP protocol_port string 该监听器监听的端口号
connection_limit int [5000,10000,20000,40000] 该监听器的最大连接数限制，默认值5000
default_pool_id string 该监听器的默认资源池ID l7policy_ids list 属于该监听器的7层策略ID列表
admin_state_up bool 监听器的管理状态 status string 该监听器的状态信息 name string
该监听器的名字 description string 该监听器的描述 tenant_id sting 拥有该监听器的租户的UUID
created_at sting 该监听器的创建时间
请求样例

::

    
    curl -s \
         -X POST `https://bj1.network.api.ustack.com/v2.0/lbaas/listeners`_ \
         -H "X-Auth-Token: {token_id}" \
         -H "Content-Type: application/json" \
         -H "Accept: application/json" \
         -d "{
                "listener": {
                    "protocol_port": "34",
                    "protocol": "HTTP",
                    "loadbalancer_id": "878442a9-7540-4d18-96b3-47666204d0db"
                }
            }"


返回样例 :


::

    {
      "listener": {
          "status": "ACTIVE",
          "protocol_port": 35,
          "protocol": "HTTP",
          "description": "",
          "tenant_id": "549c2c0713214f00aba4f783934fa3e2",
          "admin_state_up": true,
          "connection_limit": 5000,
          "id": "800c71f4-e63e-4276-a82d-bd28d8689a6e",
          "l7policy_ids": [],
          "created_at": "2014-12-08T00:07:45.000000",
          "default_pool_id": null,
          "loadbalancer_id": "878442a9-7540-4d18-96b3-47666204d0db",
          "name": ""
      }
    }




更新监听器
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 PUT /v2.0/lbaas/listeners/{listener_id} 更新监听器
请求参数
字段名 类型 描述 connection_limit int [5000,10000,20000,40000]
该监听器的最大连接数限制，默认值5000 default_pool_id string(optional) 该监听器的默认资源池
admin_state_up string(optional) 该监听器的管理状态 name string(optional)
该监听器的自定义名字 description string(optional) 该监听器的描述
返回参数
字段名 类型 描述 id string 该监听器的ID loadbalancer_id sting 拥有该监听器的负载均衡器ID
protocol string 该监听器监听的协议，目前支持TCP、HTTP protocol_port string 该监听器监听的端口号
connection_limit int [5000,10000,20000,40000] 该监听器的最大连接数限制，默认值5000
default_pool_id string 该监听器的默认资源池ID l7policy_ids list 属于该监听器的7层策略ID列表
admin_state_up bool 监听器的管理状态 status string 该监听器的状态信息 name string
该监听器的名字 description string 该监听器的描述 tenant_id sting 拥有该监听器的租户的UUID
created_at sting 该监听器的创建时间
请求样例

::

    
    curl -s \
         -X PUT `https://bj1.network.api.ustack.com/v2.0/lbaas/listeners/8efd2d05-9415-4cab-859f-2afbdaf5dbfa`_ \
         -H "X-Auth-Token: {token_id}" \
         -H "Content-Type: application/json" \
         -H "Accept: application/json" \
         -d '{
                "listener": {
                    "name": "A",
                    "admin_state_up": true
                }
            }'


返回样例 :


::

    {
      "listener": {
          "status": "ACTIVE",
          "protocol_port": 33,
          "protocol": "HTTP",
          "description": "",
          "tenant_id": "549c2c0713214f00aba4f783934fa3e2",
          "admin_state_up": true,
          "connection_limit": 5000,
          "created_at": "2014-12-08T00:07:45.000000",
          "id": "8efd2d05-9415-4cab-859f-2afbdaf5dbfa",
          "l7policy_ids": [],
          "default_pool_id": null,
          "loadbalancer_id": "878442a9-7540-4d18-96b3-47666204d0db",
          "name": "A"
      }
    }




查看监听器
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 GET /v2.0/lbaas/listeners/{listener_id} 查看监听器
请求参数

无。

返回参数
字段名 类型 描述 id string 该监听器的ID loadbalancer_id sting 拥有该监听器的负载均衡器ID
protocol string 该监听器监听的协议，目前支持TCP、HTTP protocol_port string 该监听器监听的端口号
connection_limit int [5000,10000,20000,40000] 该监听器的最大连接数限制，默认值5000
default_pool_id string 该监听器的默认资源池ID l7policy_ids list 属于该监听器的7层策略ID列表
admin_state_up bool 监听器的管理状态 status string 该监听器的状态信息 name string
该监听器的名字 description string 该监听器的描述 tenant_id sting 拥有该监听器的租户的UUID
created_at sting 该监听器的创建时间
请求样例

::

    
    curl -s \
         -X GET `https://bj1.network.api.ustack.com/v2.0/lbaas/listeners/800c71f4-e63e-4276-a82d-bd28d8689a6e`_ \
         -H "X-Auth-Token: {token_id}" \
         -H "Content-Type: application/json" \
         -H "Accept: application/json"


返回样例 :


::

    {
      "listener": {
           "status": "ACTIVE",
           "protocol_port": 35,
           "protocol": "HTTP",
           "description": "",
           "tenant_id": "549c2c0713214f00aba4f783934fa3e2",
           "admin_state_up": true,
           "connection_limit": 5000,
           "id": "800c71f4-e63e-4276-a82d-bd28d8689a6e",
           "l7policy_ids": [],
           "default_pool_id": null,
           "created_at": "2014-12-08T00:07:45.000000",
           "loadbalancer_id": "878442a9-7540-4d18-96b3-47666204d0db",
           "name": ""
      }
    }




删除监听器
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 DELETE /v2.0/lbaas/listeners/{listener_id} 删除负载均衡器
请求参数

无。

返回参数

无。

请求样例

::

    
    curl -s \
         -X DELETE `https://bj1.network.api.ustack.com/v2.0/lbaas/listeners/800c71f4-e63e-4276-a82d-bd28d8689a6e`_ \
         -H "X-Auth-Token: {token_id}" \
         -H "Content-Type: application/json" \
         -H "Accept: application/json"


返回样例 :


::

    HTTP/1.1 204 No Content
    Content-Length: 0
    Date: Mon, 20 Oct 2014 10:01:36 GMT




7层策略 (L7Policy)
------------------------------------------------



查看所有7层策略
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 GET /v2.0/lbaas/l7policies 查看所有7层策略
请求参数

无。

返回参数
字段名 类型 描述 id string 该7层策略的ID listener_id string 该7层策略所属监听器的ID action
string 该7层策略的动作, REDIRECT_TO_POOL/REDIRECT_TO_URL/REJECT
redirect_pool_id string(optional)
该7层策略重定向到的资源池ID(动作是REDIRECT_TO_POOL时有效),没有该值则不返回 redirect_url
string(optional) 该7层策略重定向URL时的URL(动作是REDIRECT_TO_URL时有效),没有该值则不返回
redirect_url_code string(optional)
该7层策略重定向URL时的返回码(动作是REDIRECT_TO_URL时有效),没有该值则不返回
redirect_url_drop_query string(optional)
该7层策略重定向URL时是否丢弃查询字符串(动作是REDIRECT_TO_URL时有效),没有该值则不返回 position int
该7层策略在所属监听器的7层策略列表中的序号 rules list 该7层策略施加作用所匹配的规则列表 admin_state_up
bool 该7层策略的管理状态 status string 该7层策略的状态信息 name string 该7层策略的名称
description string 该7层策略的描述 tenant_id sting 拥有该7层策略的租户的UUID created_at
sting 该L7Policy的创建时间
请求样例

::

    
    curl -s \
         -X GET `https://bj1.network.api.ustack.com/v2.0/lbaas/l7policies`_ \
         -H "X-Auth-Token: {token_id}" \
         -H "Content-Type: application/json" \
         -H "Accept: application/json"


返回样例 :


::

    {
      "l7policies": [
          {
              "status": "ACTIVE",
              "redirect_pool_id": "33bc3855-554f-4b8f-b603-0d4043dd9231",
              "description": "",
              "admin_state_up": true,
              "rules": [],
              "tenant_id": "549c2c0713214f00aba4f783934fa3e2",
              "listener_id": "858bf460-5003-4f62-8b84-b3d446ff03f1",
              "action": "REDIRECT_TO_POOL",
              "position": 1,
              "created_at": "2014-12-08T00:07:45.000000",
              "id": "bbee511c-19e3-47c0-b6bd-5b63c38f8414",
              "name": ""
          },
         {
              "status": "ACTIVE",
              "description": "",
              "admin_state_up": true,
              "rules": [],
              "tenant_id": "fd5e76f7b71b48dcbd66262f707e6b12",
              "created_at": "2015-01-03T15:42:14.000000",
              "listener_id": "d2cd445a-123b-48d7-b947-c2c59a4e8fa4",
              "action": "REJECT",
              "position": 2,
              "id": "bd9be829-4dba-44f5-b7f2-8f9464189df7",
              "name": "reject"
         },
         {
              "status": "ACTIVE",
              "description": "",
              "admin_state_up": true,
              "rules": [],
              "created_at": "2014-12-08T00:07:45.000000",
              "tenant_id": "549c2c0713214f00aba4f783934fa3e2",
              "listener_id": "858bf460-5003-4f62-8b84-b3d446ff03f1",
              "redirect_url": "http://www.baidu.com/",
              "redirect_url_drop_query": false,
              "redirect_url_code": 302,
              "action": "REDIRECT_TO_URL",
              "position": 0,
              "id": "dea8dff9-3874-4f91-bc5a-5af7a8a64e22",
              "name": ""
        }
     ]
    }




查看指定监听器的所有7层策略
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

(注意请求URL和返回结果的Key与上述有所不同)
HTTP方法 URI路径 描述 GET
/v2.0/lbaas/listeners/{listener_id}/lbaas_l7policies 查看指定监听器的所有7层策略
请求参数

无。

返回参数
字段名 类型 描述 id string 该7层策略的ID listener_id string 该7层策略所属监听器的ID action
string 该7层策略的动作，REDIRECT_TO_POOL/REDIRECT_TO_URL/REJECT
redirect_pool_id string(optional)
该7层策略重定向到的资源池ID(动作是REDIRECT_TO_POOL时有效),没有该值则不返回 redirect_url
string(optional) 该7层策略重定向URL时的URL(动作是REDIRECT_TO_URL时有效),没有该值则不返回
redirect_url_code string(optional)
该7层策略重定向URL时的返回码(动作是REDIRECT_TO_URL时有效),没有该值则不返回
redirect_url_drop_query string(optional)
该7层策略重定向URL时是否丢弃查询字符串(动作是REDIRECT_TO_URL时有效),没有该值则不返回 position int
该7层策略在所属监听器的7层策略列表中的序号 rules list 该7层策略施加作用所匹配的规则列表 admin_state_up
bool 该7层策略的管理状态 status string 该7层策略的状态信息 name string 该7层策略的名称
description string 该7层策略的描述 tenant_id sting 拥有该7层策略的租户的UUID created_at
sting 该L7Policy的创建时间
请求样例

::

    
    curl -s \
         -X GET `https://bj1.network.api.ustack.com/v2.0/lbaas/listeners/858bf460-5003-4f62-8b84-b3d446ff03f1/lbaas_l7policies`_ \
         -H "X-Auth-Token: {token_id}" \
         -H "Content-Type: application/json" \
         -H "Accept: application/json"


返回样例 :


::

    {
      "lbaas_l7policies": [
          {
              "status": "ACTIVE",
              "description": "",
              "admin_state_up": true,
              "rules": [],
              "created_at": "2014-12-08T00:07:45.000000",
              "tenant_id": "549c2c0713214f00aba4f783934fa3e2",
              "listener_id": "858bf460-5003-4f62-8b84-b3d446ff03f1",
              "action": "REJECT",
              "position": 1,
              "id": "bbee511c-19e3-47c0-b6bd-5b63c38f8414",
              "name": ""
          },
         {
              "status": "ACTIVE",
              "description": "",
              "admin_state_up": true,
              "rules": [],
              "created_at": "2014-12-08T00:07:45.000000",
              "tenant_id": "549c2c0713214f00aba4f783934fa3e2",
              "listener_id": "858bf460-5003-4f62-8b84-b3d446ff03f1",
              "action": "REJECT",
              "position": 0,
              "id": "dea8dff9-3874-4f91-bc5a-5af7a8a64e22",
              "name": ""
        }
     ]
    }




创建7层策略
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 POST /v2.0/lbaas/l7policies.json 创建7层策略
请求参数
字段名 类型 描述 listener_id string 该7层策略所属监听器的ID action string
该7层策略施加的动作，REDIRECT_TO_POOL/REDIRECT_TO_URL/REJECT redirect_pool_id
string(optional)
该7层策略重定向到的资源池ID(当且仅当动作为REDIRECT_TO_POOL时需要并必须指定),没有该值则不返回 redirect_url
string(optional) 该7层策略重定向URL时的URL(动作是REDIRECT_TO_URL时有效),没有该值则不返回
redirect_url_code string(optional)
该7层策略重定向URL时的返回码(动作是REDIRECT_TO_URL时有效),没有该值则不返回
redirect_url_drop_query string(optional)
该7层策略重定向URL时是否丢弃查询字符串(动作是REDIRECT_TO_URL时有效),没有该值则不返回 position
int(optional) 该7层策略在监听器的策略列表中的序号 admin_state_up string(optional)
该7层策略的管理状态 name string(optional) 该7层策略的名字 description string(optional)
该7层策略的描述
返回参数
字段名 类型 描述 id string 该7层策略的ID listener_id string 该7层策略所属监听器的ID action
string 该7层策略的动作, REDIRECT_TO_POOL/REDIRECT_TO_URL/REJECT
redirect_pool_id string(optional)
该7层策略重定向到的资源池ID(动作是REDIRECT_TO_POOL时有效),没有该值则不返回 redirect_url
string(optional) 该7层策略重定向URL时的URL(动作是REDIRECT_TO_URL时有效),没有该值则不返回
redirect_url_code string(optional)
该7层策略重定向URL时的返回码(动作是REDIRECT_TO_URL时有效),没有该值则不返回
redirect_url_drop_query string(optional)
该7层策略重定向URL时是否丢弃查询字符串(动作是REDIRECT_TO_URL时有效),没有该值则不返回 position int
该7层策略在所属监听器的7层策略列表中的序号 rules list 该7层策略施加作用所匹配的规则列表 admin_state_up
bool 该7层策略的管理状态 status string 该7层策略的状态信息 name string 该7层策略的名称
description string 该7层策略的描述 tenant_id sting 拥有该7层策略的租户的UUID created_at
sting 该L7Policy的创建时间
请求样例

::

    
    curl -s \
         -X POST `https://bj1.network.api.ustack.com/v2.0/lbaas/l7policies`_ \
         -H "X-Auth-Token: {token_id}" \
         -H "Content-Type: application/json" \
         -H "Accept: application/json" \
         -d "{
                "l7policy": {
                    "action": "REJECT",
                    "listener_id": "62393178-09d9-4ad7-8201-cfcfd8d042d2",
                    "admin_state_up": true
                }
            }"


返回样例 :


::

    {
      "l7policy": {
          "status": "PENDING_CREATE",
          "description": "",
          "admin_state_up": true,
          "rules": [],
          "created_at": "2014-12-08T00:07:45.000000",
          "tenant_id": "549c2c0713214f00aba4f783934fa3e2",
          "listener_id": "62393178-09d9-4ad7-8201-cfcfd8d042d2",
          "action": "REJECT", "position": 0,
          "id": "ecddf0cb-5a6b-4707-8616-bb9ef6a25fbe",
          "name": ""
        }
    }




更新7层策略
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 PUT /v2.0/lbaas/l7policies/{l7policy_id} 更新监听器
请求参数
字段名 类型 描述 action string
该7层策略施加的动作,REDIRECT_TO_POOL/REDIRECT_TO_URL/REJECT redirect_pool_id
string(optional) 该7层策略重定向到的资源池ID(当且仅当动作为REDIRECT_TO_POOL时需要并必须指定,资源池未被
使用,协议需要与监听器监听协议相同),没有该值则不返回 redirect_url string(optional)
该7层策略重定向URL时的URL(动作是REDIRECT_TO_URL时有效并必须指定),没有该值则不返回
redirect_url_code string(optional)
该7层策略重定向URL时的返回码(动作是REDIRECT_TO_URL时有效并必须指定),没有该值则不返回
redirect_url_drop_query string(optional)
该7层策略重定向URL时是否丢弃查询字符串(动作是REDIRECT_TO_URL时有效并必须指定),没有该值则不返回 position
int(optional) 该7层策略在监听器的策略列表中的序号 admin_state_up string(optional)
该7层策略的管理状态 name string(optional) 该7层策略的名称 description string(optional)
该7层策略的描述
返回参数
字段名 类型 描述 id string 该7层策略的ID listener_id string 该7层策略所属监听器的ID action
string 该7层策略的动作，REDIRECT_TO_POOL/REDIRECT_TO_URL/REJECT
redirect_pool_id string(optional)
该7层策略重定向到的资源池ID(动作是REDIRECT_TO_POOL时有效),没有该值则不返回 redirect_url
string(optional) 该7层策略重定向URL时的URL(动作是REDIRECT_TO_URL时有效),没有该值则不返回
redirect_url_code string(optional)
该7层策略重定向URL时的返回码(动作是REDIRECT_TO_URL时有效),没有该值则不返回
redirect_url_drop_query string(optional)
该7层策略重定向URL时是否丢弃查询字符串(动作是REDIRECT_TO_URL时有效),没有该值则不返回 position int
该7层策略在所属监听器的7层策略列表中的序号 rules list 该7层策略施加作用所匹配的规则列表 admin_state_up
bool 该7层策略的管理状态 status string 该7层策略的状态信息 name string 该7层策略的名称
description string 该7层策略的描述 tenant_id sting 拥有该7层策略的租户的UUID created_at
sting 该L7Policy的创建时间
请求样例

::

    
    curl -s \
         -X PUT `https://bj1.network.api.ustack.com/v2.0/lbaas/l7policies/ecddf0cb-5a6b-4707-8616-bb9ef6a25fbe`_ \
         -H "X-Auth-Token: {token_id}" \
         -H "Content-Type: application/json" \
         -H "Accept: application/json" \
         -d '{
                "l7policy": {
                    "action": "REDIRECT_TO_POOL",
                    "redirect_pool_id": "5a51d154-d937-4bea-abb5-c6c327545b25"
                }
            }'


返回样例 :


::

    {
      "l7policy": {
          "status": "PENDING_UPDATE",
          "redirect_pool_id": "5a51d154-d937-4bea-abb5-c6c327545b25",
          "description": "",
          "admin_state_up": true,
          "rules": [],
          "created_at": "2014-12-08T00:07:45.000000",
          "tenant_id": "549c2c0713214f00aba4f783934fa3e2",
          "listener_id": "62393178-09d9-4ad7-8201-cfcfd8d042d2",
          "action": "REDIRECT_TO_POOL",
          "position": 0,
          "id": "ecddf0cb-5a6b-4707-8616-bb9ef6a25fbe",
          "name": "L7PolicyMe333"
      }
    }




查看7层策略
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 GET /v2.0/lbaas/l7policies/{l7policy_id} 查看7层策略
请求参数

无。

返回参数
字段名 类型 描述 id string 该7层策略的ID listener_id string 该7层策略所属监听器的ID action
string 该7层策略的动作，REDIRECT_TO_POOL/REDIRECT_TO_URL/REJECT
redirect_pool_id string(optional)
该7层策略重定向到的资源池ID(动作是REDIRECT_TO_POOL时有效),没有该值则不返回 redirect_url
string(optional) 该7层策略重定向URL时的URL(动作是REDIRECT_TO_URL时有效),没有该值则不返回
redirect_url_code string(optional)
该7层策略重定向URL时的返回码(动作是REDIRECT_TO_URL时有效),没有该值则不返回
redirect_url_drop_query string(optional)
该7层策略重定向URL时是否丢弃查询字符串(动作是REDIRECT_TO_URL时有效),没有该值则不返回 position int
该7层策略在所属监听器的7层策略列表中的序号 rules list 该7层策略施加作用所匹配的规则列表 admin_state_up
bool 该7层策略的管理状态 status string 该7层策略的状态信息 name string 该7层策略的名称
description string 该7层策略的描述 tenant_id sting 拥有该7层策略的租户的UUID created_at
sting 该L7Policy的创建时间
请求样例

::

    
    curl -s \
         -X GET `https://bj1.network.api.ustack.com/v2.0/lbaas/l7policies/ecddf0cb-5a6b-4707-8616-bb9ef6a25fbe`_ \
         -H "X-Auth-Token: {token_id}" \
         -H "Content-Type: application/json" \
         -H "Accept: application/json"


返回样例 :


::

    {
      "l7policy": {
          "status": "ACTIVE",
          "redirect_pool_id": "5a51d154-d937-4bea-abb5-c6c327545b25",
          "description": "",
          "admin_state_up": true,
          "rules": [],
          "created_at": "2014-12-08T00:07:45.000000",
          "tenant_id": "549c2c0713214f00aba4f783934fa3e2",
          "listener_id": "62393178-09d9-4ad7-8201-cfcfd8d042d2",
          "action": "REDIRECT_TO_POOL",
          "position": 0,
          "id": "ecddf0cb-5a6b-4707-8616-bb9ef6a25fbe",
          "name": "L7PolicyMe333"
      }
    }




删除7层策略
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 DELETE /v2.0/lbaas/l7policies/{l7policy_id} 删除负载均衡器
请求参数

无。

返回参数

无。

请求样例

::

    
    curl -s \
         -X DELETE `https://bj1.network.api.ustack.com/v2.0/lbaas/l7policies/ecddf0cb-5a6b-4707-8616-bb9ef6a25fbe`_ \
         -H "X-Auth-Token: {token_id}" \
         -H "Content-Type: application/json" \
         -H "Accept: application/json"


返回样例 :


::

    HTTP/1.1 204 No Content
    Content-Length: 0
    Date: Mon, 20 Oct 2014 10:53:24 GMT




7层匹配规则 (L7Rule)
------------------------------------------------



查看指定7层策略下所有7层规则
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 GET /v2.0/lbaas/l7policies/{l7policy_id}/rules
查看指定7层策略下所有7层规则
请求参数

无。

返回参数
字段名 类型 描述 id string 该7层规则的ID type string 该7层规则的类型 compare_type string
该7层规则的比较类型 key string 该7层规则匹配的值 admin_state_up bool 7层规则的管理状态 status
string 该7层规则的状态信息 tenant_id sting 拥有该7层规则的租户的UUID
请求样例

::

    
    curl -s \
         -X GET `https://bj1.network.api.ustack.com/v2.0/lbaas/l7policies`_ \
         -H "X-Auth-Token: {token_id}" \
         -H "Content-Type: application/json" \
         -H "Accept: application/json"


返回样例 :


::

    {
      "rules": [
          {
               "status": "ACTIVE",
               "compare_type": "REGEX",
               "admin_state_up": true,
               "tenant_id": "549c2c0713214f00aba4f783934fa3e2",
               "key": "baidu",
               "type": "HOST_NAME",
               "id": "4c59d3b9-3282-4a3b-aab2-0fda7911fd1d"
          },
          {
               "status": "ACTIVE",
               "compare_type": "REGEX",
               "admin_state_up": true,
               "tenant_id": "549c2c0713214f00aba4f783934fa3e2",
               "key": "baidu2",
               "type": "HOST_NAME",
               "id": "9c9ff18d-9c4b-428d-8765-1de8e0a2ef7c"
          },
         {
               "status": "ACTIVE",
               "compare_type": "REGEX",
               "admin_state_up": true,
               "tenant_id": "549c2c0713214f00aba4f783934fa3e2",
               "key": "baidu3",
               "type": "HOST_NAME",
               "id": "a05e06ef-2686-487e-9ff5-f8e6acabcba9"
         }
      ]
    }




为指定的7层策略创建7层规则
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 POST /v2.0/lbaas/l7policies/{l7policy_id}/rules 创建7层规则
请求参数
字段名 类型 描述 type string 该7层规则的类型 compare_type string 该7层规则的比较类型 key
string 该7层规则匹配的值 admin_state_up bool(optional) 7层规则的管理状态
返回参数
字段名 类型 描述 id string 该7层规则的ID type string 该7层规则的类型 compare_type string
该7层规则的比较类型 key string 该7层规则匹配的值 admin_state_up bool 7层规则的管理状态 status
string 该7层规则的状态信息 tenant_id sting 拥有该7层规则的租户的UUID
请求样例

::

    
    curl -s \
         -X POST `https://bj1.network.api.ustack.com/v2.0/lbaas/l7policies/dea8dff9-3874-4f91-bc5a-5af7a8a64e22/rules`_ \
         -H "X-Auth-Token: {token_id}" \
         -H "Content-Type: application/json" \
         -H "Accept: application/json" \
         -d '{
                "rule": {
                    "compare_type": "REGEX",
                    "type": "HOST_NAME",
                    "key": "baidu",
                    "admin_state_up": true
                }
            }'


返回样例 :


::

    {
       "rule": {
            "status": "PENDING_CREATE",
            "compare_type": "REGEX",
            "admin_state_up": true,
            "tenant_id": "549c2c0713214f00aba4f783934fa3e2",
            "key": "baidu",
            "type": "HOST_NAME",
            "id": "196e2595-32dc-49d2-82d3-2e7825f93585"
       }
    }




更新7层规则
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 PUT
/v2.0/lbaas/l7policies/{l7policy_id}/rules/{l7rule_id} 更新监听器
请求参数
字段名 类型 描述 key string(optional) 该7层规则匹配的值 admin_state_up bool(optional)
7层规则的管理状态
返回参数
字段名 类型 描述 id string 该7层规则的ID type string 该7层规则的类型 compare_type string
该7层规则的比较类型 key string 该7层规则匹配的值 admin_state_up bool 7层规则的管理状态 status
string 该7层规则的状态信息 tenant_id sting 拥有该7层规则的租户的UUID
请求样例

::

    
    curl -s \
         -X PUT `https://bj1.network.api.ustack.com/v2.0/lbaas/l7policies/dea8dff9-3874-4f91-bc5a-5af7a8a64e22/rules/a05e06ef-2686-487e-9ff5-f8e6acabcba9`_ \
         -H "X-Auth-Token: {token_id}" \
         -H "Content-Type: application/json" \
         -H "Accept: application/json" \
         -d '{
                "rule": {
                    "key": "sohu"
                }
            }'


返回样例 :


::

    {
      "rule": {
           "status": "PENDING_UPDATE",
           "compare_type": "REGEX",
           "admin_state_up": true,
           "tenant_id": "549c2c0713214f00aba4f783934fa3e2",
           "key": "sohu",
           "type": "HOST_NAME",
           "id": "a05e06ef-2686-487e-9ff5-f8e6acabcba9"
      }
    }




查看7层规则
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 GET
/v2.0/lbaas/l7policies/{l7policy_id}/rules/{l7rule_id} 查看7层规则
请求参数

无。

返回参数
字段名 类型 描述 id string 该7层规则的ID type string 该7层规则的类型 compare_type string
该7层规则的比较类型 key string 该7层规则匹配的值 admin_state_up bool 7层规则的管理状态 status
string 该7层规则的状态信息 tenant_id sting 拥有该7层规则的租户的UUID
请求样例

::

    
    curl -s \
         -X GET `https://bj1.network.api.ustack.com/v2.0/lbaas/l7policies/dea8dff9-3874-4f91-bc5a-5af7a8a64e22/rules/4c59d3b9-3282-4a3b-aab2-0fda7911fd1d`_ \
         -H "X-Auth-Token: {token_id}" \
         -H "Content-Type: application/json" \
         -H "Accept: application/json"


返回样例 :


::

    {
      "rule": {
          "status": "ACTIVE",
          "compare_type": "REGEX",
          "admin_state_up": true,
          "tenant_id": "549c2c0713214f00aba4f783934fa3e2",
          "key": "baidu",
          "type": "HOST_NAME",
          "id": "4c59d3b9-3282-4a3b-aab2-0fda7911fd1d"
      }
    }




删除7层规则
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 DELETE
/v2.0/l7policies/{l7policy_id}/rules/{l7rule_id} 删除7层规则
请求参数

无。

返回参数

无。

请求样例

::

    
    curl -s \
         -X DELETE `https://bj1.network.api.ustack.com/v2.0/lbaas/l7policies/dea8dff9-3874-4f91-bc5a-5af7a8a64e22/rules/4c59d3b9-3282-4a3b-aab2-0fda7911fd1d`_ \
         -H "X-Auth-Token: {token_id}" \
         -H "Content-Type: application/json" \
         -H "Accept: application/json"


返回样例 :


::

    HTTP/1.1 204 No Content
    Content-Length: 0
    Date: Mon, 20 Oct 2014 22:54:51 GMT




资源池 (Pool)
--------------------------------------



查看所有资源池
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 GET /v2.0/lbaas/pools 查看所有资源池
请求参数

无。

返回参数
字段名 类型 描述 id string 该资源池的ID protocol string 该资源池使用的协议,目前支持TCP、HTTP
lb_algorithm string 资源调度采用的负载均衡算法,
目前支持ROUND_ROBIN、LEAST_CONNECTIONS、SOURCE_IP healthmonitor
dict(optional)
:该资源池使用的健康检查信息，如果没有配置，则不返回:

    + type 健康检查方式 TCP/HTTP
    + delay 间隔时间 范围[2,60]s
    + timeout 超时时间 范围[5,300]s
    + max_retries 尝试次数 范围[1,10]
    + http_method HTTP方法 GET/POST/PUT/DELETE HTTP模式下有值;TCP模式下该字段不返回
    + url_path URL路径 HTTP模式下有值;TCP模式下该字段不返回
    + expected_codes 期待返回码 HTTP模式下有值;TCP模式下该字段不返回 可以是诸如以下的方式,方式1: 200 方式2:
      200,202,404 方式3: 200-202
    + id 健康检查器的id，自动生成，请忽略


session_persistence dict(optional)
:该资源池使用的会话保持信息,仅HTTP模式下可以配置，如果没有配置，则不返回:

    + type 类型 APP_COOKIE/HTTP_COOKIE/SOURCE_IP
    + cookie_name COOKIE名 type为APP_COOKIE下有效，其他方式下不返回
    + pool_id 该会话保持所属资源池，自动生成，请忽略


network_id string 该资源池所在网络ID subnet_id string(optinal)
该资源池所在子网ID，当且仅当指定时有返回值 members list 该资源池包含的资源信息的列表 admin_state_up
string 该资源池的管理状态 status sting 该资源池的状态 name string 该资源池的名称 description
string 对该资源池的描述 tenant_id string 该资源池所属的租户ID created_at string
该资源池创建的时间
请求样例

::

    
    curl -s \
         -X GET `https://bj1.network.api.ustack.com/v2.0/lbaas/pools`_ \
         -H "X-Auth-Token: {token_id}" \
         -H "Content-Type: application/json" \
         -H "Accept: application/json"


返回样例 :


::

    {
      "pools": [
           {
               "lb_algorithm": "LEAST_CONNECTIONS",
               "status": "DEFERRED",
               "protocol": "HTTP",
               "description": "",
               "admin_state_up": true,
               "network_id": "226b14e4-e0a3-42b8-bbbb-59ed3959c32c",
               "tenant_id": "549c2c0713214f00aba4f783934fa3e2",
               "healthmonitor": {
                   "delay": 3,
                   "max_retries": 3,
                   "timeout": 5,
                   "type": "TCP",
                   "id": "2392d05b-0fb1-4f7c-accd-6360d0c5a75a"
               },
               "created_at": "2014-12-08T00:07:45.000000",
               "members": [
                   {
                       "status": "DEFERRED",
                       "weight": 1,
                       "admin_state_up": true,
                       "subnet_id": "6bc4c524-b4d8-4612-b4bd-88ca7e659198",
                       "tenant_id": "549c2c0713214f00aba4f783934fa3e2",
                       "pool_id": "1d398af4-1d7f-4159-aa4b-46f7473d0ae0",
                       "address": "1.1.1.1",
                       "protocol_port": 80,
                       "id":"34d032fc-46ed-4a62-b8a4-1fb0574ec374",
                       "pool": null
                 }
               ],
               "id": "1d398af4-1d7f-4159-aa4b-46f7473d0ae0",
               "name": ""
          },
          {
              "lb_algorithm": "LEAST_CONNECTIONS",
              "status": "DEFERRED",
              "protocol": "HTTP",
              "description": "",
              "admin_state_up": true,
              "network_id": "de28919d-8c56-48d2-a25a-1b132d2af826",
              "subnet_id": "24b20f04-eda2-44b4-ad26-e265675e0d6d",
              "tenant_id": "549c2c0713214f00aba4f783934fa3e2",
              "session_persistence": {
                  "type": "HTTP_COOKIE",
                  "pool_id": "570b7074-ff42-4cc1-b722-cc8968052da4"
              },
             "healthmonitor": {
                  "delay": 10,
                  "expected_codes": "200",
                  "max_retries": 3,
                  "http_method": "GET",
                  "timeout": 5,
                  "url_path": "/index.html",
                  "type": "HTTP",
                  "id": "570b7074-ff42-4cc1-b722-cc8968052da4"
              },
              "members": [],
              "created_at": "2014-12-08T00:07:45.000000",
              "id": "5a51d154-d937-4bea-abb5-c6c327545b25",
              "name": ""
          },
          {
              "lb_algorithm": "LEAST_CONNECTIONS",
              "status": "DEFERRED",
              "protocol": "HTTP",
              "description": "",
              "admin_state_up": true,
              "network_id": "de28919d-8c56-48d2-a25a-1b132d2af826",
              "tenant_id": "549c2c0713214f00aba4f783934fa3e2",
              "members": [],
              "created_at": "2014-12-08T00:07:45.000000",
              "id": "a3c7577f-0473-4ff2-8ad0-b5fc65d751a2",
              "name": ""
          }
      ]
    }




创建资源池
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 POST /v2.0/lbaas/pools 创建资源池
请求参数
字段名 类型 描述 protocol string 该资源池使用的协议 目前支持TCP和HTTP lb_algorithm string
资源调度采用的负载均衡算法 目前支持LEAST_CONNECTIONS、SOURCE_IP、ROUND_ROBIN
healthmonitor dict(optional)
:该资源池使用的健康检查信息。创建资源池时如果不指定(例如只是为了更新名字时)，之前配置将会删除:

    + type 健康检查方式 TCP/HTTP
    + delay 间隔时间 范围[2,60]s
    + timeout 超时时间 范围[5,300]s
    + max_retries 尝试次数 范围[1,10]
    + http_method HTTP方法 GET/POST/PUT/DELETE HTTP模式下有效;TCP模式下该字段无效，请不要配置
    + url_path URL路径 HTTP模式下有效;TCP模式下该字段无效，请不要配置
    + expected_codes 期待返回码 HTTP模式下有效;TCP模式下该字段无效,，请不要配置。可以是诸如以下的方式,方式1:
      200 方式2: 200,202,404 方式3: 200-202


session_persistence dict(optional)
:该资源池使用的会话保持信息,仅HTTP模式下可以配置:

    + type 类型 APP_COOKIE/HTTP_COOKIE/SOURCE_IP
    + cookie_name COOKIE名 type为APP_COOKIE下有效，其他方式下不可配置


network_id string 该资源池所在网络ID subnet_id string(optinal) 该资源池所在子网ID
admin_state_up string(optional) 该资源池的管理状态 name string(optional)
该资源池的自定义名称 description string(optional) 对该资源池的描述
返回参数
字段名 类型 描述 id string 该资源池的ID protocol string 该资源池使用的协议 lb_algorithm
string 资源调度采用的负载均衡算法 healthmonitor dict(optinal)
:该资源池使用的健康检查信息，如果没有配置，则不返回:

    + type 健康检查方式 TCP/HTTP
    + delay 间隔时间 范围[2,60]s
    + timeout 超时时间 范围[5,300]s
    + max_retries 尝试次数 范围[1,10]
    + http_method HTTP方法 GET/POST/PUT/DELETE HTTP模式下有值;TCP模式下该字段不返回
    + url_path URL路径 HTTP模式下有值;TCP模式下该字段不返回
    + expected_codes 期待返回码 HTTP模式下有值;TCP模式下该字段不返回 可以是诸如以下的方式,方式1: 200 方式2:
      200,202,404 方式3: 200-202
    + id 健康检查器的id，自动生成，请忽略


session_persistence dict(optinal)
:该资源池使用的会话保持信息,仅HTTP模式下可以配置，如果没有配置，则不返回:

    + type 类型 APP_COOKIE/HTTP_COOKIE/SOURCE_IP
    + cookie_name COOKIE名 type为APP_COOKIE下有效，其他方式下不返回
    + pool_id 该会话保持所属资源池，自动生成，请忽略


network_id string 该资源池所在网络ID subnet_id string(optinal)
该资源池所在子网ID，当且仅当指定时有返回值 members list 该资源池包含的成员的列表 admin_state_up string
该资源池的管理状态 status sting 该资源池的状态 name string 该资源池的名称 description string
对该资源池的描述 tenant_id string 该资源池所属的租户ID
请求样例

::

    
    curl -s \
         -X POST `https://bj1.network.api.ustack.com/v2.0/lbaas/pools`_ \
         -H "X-Auth-Token: {token_id}" \
         -H "Content-Type: application/json" \
         -H "Accept: application/json" \
         -d '{
                "pool": {
                    "lb_algorithm": "ROUND_ROBIN",
                    "protocol": "HTTP",
                    "admin_state_up": true,
                    "network_id": "226b14e4-e0a3-42b8-bbbb-59ed3959c32c"
                }
            }’


返回样例 :


::

    {
       "pool": {
           "lb_algorithm": "ROUND_ROBIN",
           "status": "DEFERRED",
           "protocol": "HTTP",
           "description": "",
           "admin_state_up": true,
           "tenant_id": "549c2c0713214f00aba4f783934fa3e2",
           "network_id": "226b14e4-e0a3-42b8-bbbb-59ed3959c32c",
           "members": [],
           "created_at": "2014-12-08T00:07:45.000000",
           "id": "fb836001-32e1-45de-95bb-2f719c014ec8",
           "name": ""
       }
    }




更新资源池
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 PUT /v2.0/lbaas/pools/{pool_id} 更新监听器
请求参数
字段名 类型 描述 healthmonitor dict(optional)
:该资源池使用的健康检查信息.更新资源池时如果不指定(例如只是为了更新名字时)，之前配置将会删除:

    + type 健康检查方式 TCP/HTTP
    + delay 间隔时间 范围[2,60]s
    + timeout 超时时间 范围[5,300]s
    + max_retries 尝试次数 范围[1,10]
    + http_method HTTP方法 GET/POST/PUT/DELETE HTTP模式下有效;TCP模式下该字段无效，请不要配置
    + url_path URL路径 HTTP模式下有效;TCP模式下该字段无效，请不要配置
    + expected_codes 期待返回码 HTTP模式下有效;TCP模式下该字段无效,，请不要配置。可以是诸如以下的方式,方式1:
      200 方式2: 200,202,404 方式3: 200-202


session_persistence dict(optional)
:该资源池使用的会话保持信息,仅HTTP模式下可以配置.更新资源池时如果不指定(例如只是为了更新名字时)，之前配置将会删除:

    + type 类型 APP_COOKIE/HTTP_COOKIE/SOURCE_IP
    + cookie_name COOKIE名 type为APP_COOKIE下有效，其他方式下不可配置


admin_state_up string(optional) 该资源池的管理状态 lb_algorithm
string(optional) 资源调度采用的负载均衡算法 name string(optional) 该资源池的自定义名称
description string(optional) 对该资源池的描述
返回参数
字段名 类型 描述 id string 该资源池的ID protocol string 该资源池使用的协议 lb_algorithm
string 资源调度采用的负载均衡算法 healthmonitor dict(optinal)
:该资源池使用的健康检查信息，如果没有配置，则不返回:

    + type 健康检查方式 TCP/HTTP
    + delay 间隔时间 范围[2,60]s
    + timeout 超时时间 范围[5,300]s
    + max_retries 尝试次数 范围[1,10]
    + http_method HTTP方法 GET/POST/PUT/DELETE HTTP模式下有值;TCP模式下该字段不返回
    + url_path URL路径 HTTP模式下有值;TCP模式下该字段不返回
    + expected_codes 期待返回码 HTTP模式下有值;TCP模式下该字段不返回 可以是诸如以下的方式,方式1: 200 方式2:
      200,202,404 方式3: 200-202
    + id 健康检查器的id，自动生成，请忽略


session_persistence dict(optinal)
:该资源池使用的会话保持信息,仅HTTP模式下可以配置，如果没有配置，则不返回:

    + type 类型 APP_COOKIE/HTTP_COOKIE/SOURCE_IP
    + cookie_name COOKIE名 type为APP_COOKIE下有效，其他方式下不返回
    + pool_id 该会话保持所属资源池，自动生成，请忽略


network_id string 该资源池所在网络ID subnet_id string(optinal)
该资源池所在子网ID，当且仅当指定时有返回值 members list 该资源池包含的成员的列表 admin_state_up string
该资源池的管理状态 status sting 该资源池的状态 name string 该资源池的名称 description string
对该资源池的描述 tenant_id string 该资源池所属的租户ID
请求样例

::

    
    curl -s \
         -X PUT `https://bj1.network.api.ustack.com/v2.0/lbaas/pools/a3c7\
         -H "X-Auth-Token: {token_id}" \
         -H "Content-Type: application/json" \
         -H "Accept: application/json" \
         -d '{
                "pool": {
                    "session_persistence": {
                        "type": "SOURCE_IP"
                    },
                    "admin_state_up": true
                }
            }'


返回样例 :


::

    {
     "pool": {
         "lb_algorithm": "LEAST_CONNECTIONS",
         "status": "DEFERRED",
         "protocol": "HTTP",
         "description": "",
         "admin_state_up": true,
         "network_id": "226b14e4-e0a3-42b8-bbbb-59ed3959c32c",
         "tenant_id": "549c2c0713214f00aba4f783934fa3e2",
         "session_persistence":
             {
                 "type": "SOURCE_IP"
             },
         "created_at": "2014-12-08T00:07:45.000000",
         "members": [],
         "id": "a3c7577f-0473-4ff2-8ad0-b5fc65d751a2",
         "name": ""
     }
    }




查看资源池
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 GET /v2.0/lbaas/pools/{pool_id} 查看资源池
请求参数

无。

返回参数
字段名 类型 描述 id string 该资源池的ID protocol string 该资源池使用的协议 lb_algorithm
string 资源调度采用的负载均衡算法 healthmonitor dict(optinal)
:该资源池使用的健康检查信息，如果没有配置，则不返回:

    + type 健康检查方式 TCP/HTTP
    + delay 间隔时间 范围[2,60]s
    + timeout 超时时间 范围[5,300]s
    + max_retries 尝试次数 范围[1,10]
    + http_method HTTP方法 GET/POST/PUT/DELETE HTTP模式下有值;TCP模式下该字段不返回
    + url_path URL路径 HTTP模式下有值;TCP模式下该字段不返回
    + expected_codes 期待返回码 HTTP模式下有值;TCP模式下该字段不返回 可以是诸如以下的方式,方式1: 200 方式2:
      200,202,404 方式3: 200-202
    + id 健康检查器的id，自动生成，请忽略


session_persistence dict(optinal)
:该资源池使用的会话保持信息,仅HTTP模式下可以配置，如果没有配置，则不返回:

    + type 类型 APP_COOKIE/HTTP_COOKIE/SOURCE_IP
    + cookie_name COOKIE名 type为APP_COOKIE下有效，其他方式下不返回
    + pool_id 该会话保持所属资源池，自动生成，请忽略


network_id string 该资源池所在网络ID subnet_id string(optinal)
该资源池所在子网ID，当且仅当指定时有返回值 members list 该资源池包含的成员的列表 admin_state_up string
该资源池的管理状态 status sting 该资源池的状态 name string 该资源池的名称 description string
对该资源池的描述 tenant_id string 该资源池所属的租户ID
请求样例

::

    
    curl -s \
         -X GET `https://bj1.network.api.ustack.com/v2.0/lbaas/pools/a3c7\
         -H "X-Auth-Token: {token_id}" \
         -H "Content-Type: application/json" \
         -H "Accept: application/json"


返回样例 :


::

    {
     "pool": {
         "lb_algorithm": "LEAST_CONNECTIONS",
         "status": "DEFERRED",
         "protocol": "HTTP",
         "description": "",
         "admin_state_up": true,
         "tenant_id": "549c2c0713214f00aba4f783934fa3e2",
         "session_persistence":
             {
                 "type": "SOURCE_IP"
             },
         "members": [],
         "created_at": "2014-12-08T00:07:45.000000",
         "id": "a3c7577f-0473-4ff2-8ad0-b5fc65d751a2",
         "name": ""
     }
    }




删除资源池
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 DELETE /v2.0/lbaas/pools/{pool_id} 删除资源池
请求参数

无。

返回参数

无。

请求样例

::

    
    curl -s \
         -X DELETE `https://bj1.network.api.ustack.com/v2.0/lbaas/pools/a3c7\
         -H "X-Auth-Token: {token_id}" \
         -H "Content-Type: application/json" \
         -H "Accept: application/json"


返回样例 :


::

    HTTP/1.1 204 No Content
    Content-Length: 0
    Date: Mon, 20 Oct 2014 00:39:13 GMT




成员 (Member)
----------------------------------------



查看指定资源池下所有成员
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 GET /v2.0/lbaas/pools/{pool_id} 查看指定资源池下所有成员
请求参数

无。

返回参数
字段名 类型 描述 id string 该成员的ID subnet_id string 成员所在的子网ID address string
对成员的IP地址 protocol_port string 对成员的端口号 weight int 该成员的权重 admin_state_up
string 该成员的管理状态 status sting 该成员的状态 tenant_id string 该成员所属的租户ID
instance_id string 该成员关联虚拟机的UUID
请求样例

::

    
    curl -s \
         -X GET `https://bj1.network.api.ustack.com/v2.0/lbaas/pools/5a51d154-d937-4bea-abb5-c6c327545b25/members`_ \
         -H "X-Auth-Token: {token_id}" \
         -H "Content-Type: application/json" \
         -H "Accept: application/json"


返回样例 :


::

    {
      "members": [
          {
              "status": "DEFERRED",
              "weight": 1,
              "admin_state_up": true,
              "subnet_id": "6bc4c524-b4d8-4612-b4bd-88ca7e659198",
              "tenant_id": "549c2c0713214f00aba4f783934fa3e2",
              "address": "1.1.1.2",
              "protocol_port": 50,
              "instance_id": "549c2c0713214f00aba4f783934fa3ee",
              "id": "e86a2ef0-9a33-491b-a79d-a5272e8ed42e"
          }
       ]
    }




创建成员
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 POST /v2.0/lbaas/pools/{pool_id}/members 创建健康检查
请求参数
字段名 类型 描述 subnet_id string 成员所在的子网ID,注意子网ID只是作为成员的信息,不具有“联动”作用 address
string 对成员的IP地址,注意IP地址只是作为成员的信息,不具有“联动”作用 protocol_port string 对成员的端口号
instance_id string 该成员关联虚拟机的UUID,,注意虚拟机UUID只是作为成员的信息,不具有“联动”作用 weight
int(optional) 该成员的权重 admin_state_up string(optional) 该成员的管理状态
返回参数
字段名 类型 描述 id string 该成员的ID subnet_id string 成员所在的子网ID address string
对成员的IP地址 protocol_port string 对成员的端口号 weight int 该成员的权重 admin_state_up
string 该成员的管理状态 status sting 该成员的状态 tenant_id string 该成员所属的租户ID
instance_id string 该成员关联虚拟机的UUID
请求样例

::

    
    curl -s \
         -X POST `https://bj1.network.api.ustack.com/v2.0/lbaas/pools/5a51d154-d937-4bea-abb5-c6c327545b25/members`_ \
         -H "X-Auth-Token: {token_id}" \
         -H "Content-Type: application/json" \
         -H "Accept: application/json" \
         -d '{
                "member": {
                    "subnet_id": "6bc4c524-b4d8-4612-b4bd-88ca7e659198",
                    "instance_id": "6bc4c524-b4d8-4612-b4bd-88ca7e659198",
                    "protocol_port": "40",
                    "instance_id": "6bc4c524-b4d8-4612-b4bd-88ca7e659198",
                    "admin_state_up": true,
                    "address": "1.1.1.1"
                }
            }'


返回样例 :


::

    {
      "member":
           {
               "status": "DEFERRED",
               "weight": 1,
               "admin_state_up": true,
               "subnet_id": "6bc4c524-b4d8-4612-b4bd-88ca7e659198",
               "tenant_id": "549c2c0713214f00aba4f783934fa3e2",
               "address": "1.1.1.1",
               "protocol_port": 40,
               "instance_id": "6bc4c524-b4d8-4612-b4bd-88ca7e659198",
               "id": "1ac62895-d36f-4ebb-9111-10ecb5cd1ad0"
           }
    }




更新成员
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 PUT /v2.0/lbaas/pools/{pool_id}/members/{member_id}
更新成员
请求参数
字段名 类型 描述 weight int(optional) 该成员的权重 admin_state_up string(optional)
该成员的管理状态
返回参数
字段名 类型 描述 id string 该成员的ID subnet_id string 成员所在的子网ID address string
对成员的IP地址 protocol_port string 对成员的端口号 weight int 该成员的权重 admin_state_up
string 该成员的管理状态 status sting 该成员的状态 tenant_id string 该成员所属的租户ID
instance_id string 该成员关联虚拟机的UUID
请求样例

::

    
    curl -s \
         -X PUT `https://bj1.network.api.ustack.com//v2.0/lbaas/pools/5a51d154-d937-4bea-abb5-c6c327545b25/members/e86a2ef0-9a33-491b-a79d-a\
         -H "X-Auth-Token: {token_id}" \
         -H "Content-Type: application/json" \
         -H "Accept: application/json" \
         -d '{
                "member": {
                    "weight": "3"
                }
            }'


返回样例 :


::

    {
      "member":
          {
              "status": "DEFERRED",
              "weight": 3,
              "admin_state_up": true,
              "subnet_id": "6bc4c524-b4d8-4612-b4bd-88ca7e659198",
              "tenant_id": "549c2c0713214f00aba4f783934fa3e2",
              "address": "1.1.1.2",
              "protocol_port": 50,
              "instance_id": "6bc4c524-b4d8-4612-b4bd-88ca7e659198",
              "id": "e86a2ef0-9a33-491b-a79d-a5272e8ed42e"
          }
    }




查看成员
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 GET /v2.0/lbaas/pools/{pool_id}/members/{member_id}
查看成员
请求参数

无。

返回参数
字段名 类型 描述 id string 该成员的ID subnet_id string 成员所在的子网ID address string
对成员的IP地址 protocol_port string 对成员的端口号 weight int 该成员的权重 admin_state_up
string 该成员的管理状态 status sting 该成员的状态 tenant_id string 该成员所属的租户ID
instance_id string 该成员关联虚拟机的UUID
请求样例

::

    
    curl -s \
         -X GET `https://bj1.network.api.ustack.com//v2.0/lbaas/pools/5a51d154-d937-4bea-abb5-c6c327545b25/members/e86a2ef0-9a33-491b-a79d-a\
         -H "X-Auth-Token: {token_id}" \
         -H "Content-Type: application/json" \
         -H "Accept: application/json"


返回样例 :


::

    {
      "member":
          {
              "status": "DEFERRED",
              "weight": 3,
              "admin_state_up": true,
              "subnet_id": "6bc4c524-b4d8-4612-b4bd-88ca7e659198",
              "tenant_id": "549c2c0713214f00aba4f783934fa3e2",
              "address": "1.1.1.2",
              "protocol_port": 50,
              "instance_id": "6bc4c524-b4d8-4612-b4bd-88ca7e659198",
              "id": "e86a2ef0-9a33-491b-a79d-a5272e8ed42e"
          }
    }




删除成员
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 DELETE /v2.0/lbaas/pools/{pool_id}/members/{member_id}
删除成员
请求参数

无。

返回参数

无。

请求样例

::

    
    curl -s \
         -X DELETE `https://bj1.network.api.ustack.com/v2.0/lbaas/pools/5a51d154-d937-4bea-abb5-c6c327545b25/members/e86a2ef0-9a33-491b-a79d-a\
         -H "X-Auth-Token: {token_id}" \
         -H "Content-Type: application/json" \
         -H "Accept: application/json"


返回样例 :


::

    HTTP/1.1 204 No Content
    Content-Length: 0
    Date: Mon, 21 Oct 2014 02:49:07 GMT




PPTP VPN (PPTP VPN)
--------------------------------------------------------



查看所有的PPTP VPN
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 GET /v2.0/vpn/pptpconnections 查看所有的PPTP VPN
请求参数

无。

返回参数
字段名 类型 描述 tenant_id string 该成员所属的租户ID status string 该PPTP的实际运行状态 name
string 该PPTP的名字 router_id string 该PPTP所在的路由器的UUID admin_state_up bool
该PPTP的管理状态 vpn_cidr string 该PPTP上对端分配的CIDR created_at string
该PPTP的创建时间，为UTC时间 id string 该PPTP的UUID
请求样例

::

    
    curl -s \
         -X GET `https://bj1.network.api.ustack.com/v2.0/vpn/pptpconnections`_ \
         -H "X-Auth-Token: {token_id}" \
         -H "Content-Type: application/json" \
         -H "Accept: application/json"


返回样例 :


::

    {
     "pptpconnections": [
         {
             "status": "DOWN",
             "router_id": "7a3a0f11-9026-42ab-b9f8-d464f780a53a",
             "vpn_cidr": "192.168.0.0/24",
             "admin_state_up": true,
             "tenant_id": "6866f5e4ff2b436fab2569a83f0e419d",
             "created_at": "2015-03-24 10:45:10",
             "description": "",
             "id": "332109ff-bcea-4abf-a04d-8b579383db42",
             "name": "12"
         },
         {
             "status": "DOWN",
             "router_id": "265f286d-3ef7-4533-98cf-1c1abdc381d8",
             "vpn_cidr": "192.168.0.0/24",
             "admin_state_up": true,
             "tenant_id": "1e5c327560a0496ea60866feb0d70c98",
             "created_at": "2015-05-04 10:11:32",
             "description": "",
             "id": "3d5f32a0-6412-48d9-a5db-a79d594edf01",
             "name": "123"
         },
         {
             "status": "DOWN",
             "router_id": "777d84ce-f7de-4529-aa0d-943925d59ee6",
             "vpn_cidr": "192.168.0.0/24",
             "admin_state_up": true,
             "tenant_id": "7a4d5b1c6c8a4ce7ab0a0988c860a92d",
             "created_at": "2015-04-13 09:05:28",
             "description": "",
             "id": "d0be04dc-1724-48aa-9cd0-1d51d8fdfda2",
             "name": "333"
         }
       ]
     }




修改PPTP VPN的管理状态
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 PUT /v2.0/vpn/pptpconnections/{pptp_id} 修改PPTP
VPN的管理状态
请求参数
字段名 类型 描述 admin_state_up bool 该PPTP的管理状态
返回参数
字段名 类型 描述 tenant_id string 该成员所属的租户ID status string 该PPTP的实际运行状态 name
string 该PPTP的名字 router_id string 该PPTP所在的路由器的UUID admin_state_up bool
该PPTP的管理状态 vpn_cidr string 该PPTP上对端分配的CIDR created_at string
该PPTP的创建时间，为UTC时间 id string 该PPTP的UUID
请求样例

::

    
    curl -s \
         -X PUT `https://bj1.network.api.ustack.com/v2.0/vpn/pptpconnections/332109ff-bcea-4abf-a04d-8b579383db42`_ \
         -H "X-Auth-Token: {token_id}" \
         -H "Content-Type: application/json" \
         -H "Accept: application/json" \
         -d '{
                "pptpconnection": {
                    "admin_state_up":"false"
                }
            }'


返回样例 :


::

    {
        "pptpconnection": {
            "status": "DOWN",
            "router_id": "7a3a0f11-9026-42ab-b9f8-d464f780a53a",
            "vpn_cidr": "192.168.0.0/24",
            "admin_state_up": false,
            "tenant_id": "6866f5e4ff2b436fab2569a83f0e419d",
            "created_at": "2015-03-24 10:45:10",
            "description": "",
            "id": "332109ff-bcea-4abf-a04d-8b579383db42",
            "name": "12"
        }
    }




查看PPTP VPN
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 GET /v2.0/vpn/pptpconnections/{pptp_id} 查看PPTP VPN的信息
请求参数

无

返回参数
字段名 类型 描述 tenant_id string 该成员所属的租户ID status string 该PPTP的实际运行状态 name
string 该PPTP的名字 router_id string 该PPTP所在的路由器的UUID admin_state_up bool
该PPTP的管理状态 vpn_cidr string 该PPTP上对端分配的CIDR created_at string
该PPTP的创建时间，为UTC时间 id string 该PPTP的UUID
请求样例

::

    
    curl -s \
         -X GET `https://bj1.network.api.ustack.com/v2.0/vpn/pptpconnections/332109ff-bcea-4abf-a04d-8b579383db42`_ \
         -H "X-Auth-Token: {token_id}" \
         -H "Content-Type: application/json" \
         -H "Accept: application/json"


返回样例 :


::

    {
        "pptpconnection": {
            "status": "DOWN",
            "router_id": "7a3a0f11-9026-42ab-b9f8-d464f780a53a",
            "vpn_cidr": "192.168.0.0/24",
            "admin_state_up": false,
            "tenant_id": "6866f5e4ff2b436fab2569a83f0e419d",
            "created_at": "2015-03-24 10:45:10",
            "description": "",
            "id": "332109ff-bcea-4abf-a04d-8b579383db42",
            "name": "12"
        }
    }




删除PPTP VPN
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 DELETE /v2.0/vpn/pptpconnections/{pptp_id} 删除PPTP VPN
请求参数

无

返回参数

无

请求样例

::

    
    curl -s \
         -X DELETE `https://bj1.network.api.ustack.com/v2.0/vpn/pptpconnections/332109ff-bcea-4abf-a04d-8b579383db42`_ \
         -H "X-Auth-Token: {token_id}" \
         -H "Content-Type: application/json" \
         -H "Accept: application/json"


返回样例 :


::

    HTTP/1.1 204 No Content
    Content-Length: 0
    Date: Fri, 08 May 2015 03:01:08 GMT




查看所有的PPTP USER
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 GET /v2.0/vpn/vpnusers 查看所有的PPTP USER
请求参数

无。

返回参数
字段名 类型 描述 tenant_id string 该成员所属的租户ID name string 该PPTP USER的名字
password string 该PPTP USER的密码 admin_state_up bool 该PPTP USER的管理状态
created_at string 该PPTP USER的创建时间，为UTC时间 id string 该PPTP USER的UUID
请求样例

::

    
    curl -s \
         -X GET `https://bj1.network.api.ustack.com/v2.0/vpn/vpnusers`_ \
         -H "X-Auth-Token: {token_id}" \
         -H "Content-Type: application/json" \
         -H "Accept: application/json"


返回样例 :


::

    {
        "vpnusers": [
            {
                "description": "",
                "admin_state_up": true,
                "tenant_id": "ee55d67b0fc14d71aa5cdd936b31e9de",
                "created_at": "2014-08-20 12:51:55",
                "password": "testpass word",
                "id": "0b471dd4-d486-43d6-8679-96f0e5803ca6",
                "name": "testuser"
            },
            {
                "description": "",
                "admin_state_up": true,
                "tenant_id": "ee55d67b0fc14d71aa5cdd936b31e9de",
                "created_at": "2014-08-22 07:28:49",
                "password": "123423456",
                "id": "10e4b092-096e-4368-bfac-6fbb04bf38d1",
                "name": "test"
            },
            {
                "description": "",
                "admin_state_up": true,
                "tenant_id": "ee55d67b0fc14d71aa5cdd936b31e9de",
                "created_at": "2014-08-20 13:04:34",
                "password": "testpass",
                "id": "14393abb-c356-4d5e-9249-7cdc2dfcd32f",
                "name": "testusasdasder2"
            }
        ]
    }




创建的PPTP USER
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 POST /v2.0/vpn/vpnusers 创建PPTP USER
请求参数
字段名 类型 描述 name string 该PPTP USER的名字 password string 该PPTP USER的密码
返回参数
字段名 类型 描述 tenant_id string 该成员所属的租户ID name string 该PPTP USER的名字
password string 该PPTP USER的密码 admin_state_up bool 该PPTP USER的管理状态
created_at string 该PPTP USER的创建时间，为UTC时间 id string 该PPTP USER的UUID
请求样例

::

    
    curl -s \
         -X GET `https://bj1.network.api.ustack.com/v2.0/vpn/vpnusers`_ \
         -H "X-Auth-Token: {token_id}" \
         -H "Content-Type: application/json" \
         -H "Accept: application/json" \
         -d '{
                "vpnuser": {
                    "password": "12345678",
                    "name": "test"
                }
            }'


返回样例 :


::

    {
        "vpnuser": {
            "description": "",
            "admin_state_up": true,
            "tenant_id": "ee55d67b0fc14d71aa5cdd936b31e9de",
            "created_at": "2015-05-08 04:00:37.004477",
            "password": "12345678",
            "id": "8f8168a8-5c4d-485a-a245-40d48345736c",
            "name": "test"
        }
    }




查询PPTP USER
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 GET /v2.0/vpn/vpnusers/{vpn_user_id} 查询PPTP USER的信息
请求参数

无

返回参数
字段名 类型 描述 tenant_id string 该成员所属的租户ID name string 该PPTP USER的名字
password string 该PPTP USER的密码 admin_state_up bool 该PPTP USER的管理状态
created_at string 该PPTP USER的创建时间，为UTC时间 id string 该PPTP USER的UUID
请求样例

::

    
    curl -s \
         -X GET `https://bj1.network.api.ustack.com/v2.0/vpn/vpnusers/0b471dd4-d486-43d6-8679-96f0e5803ca6`_ \
         -H "X-Auth-Token: {token_id}" \
         -H "Content-Type: application/json" \
         -H "Accept: application/json"


返回样例 :


::

    {
        "vpnuser": {
            "description": "",
            "admin_state_up": true,
            "tenant_id": "ee55d67b0fc14d71aa5cdd936b31e9de",
            "created_at": "2014-08-20 12:51:55",
            "password": "testpass word",
            "id": "0b471dd4-d486-43d6-8679-96f0e5803ca6",
            "name": "testuser"
        }
    }




删除PPTP USER
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 DELETE /v2.0/vpn/vpnusers/{vpnuser_id} 删除PPTP USER
请求参数

无

返回参数

无

请求样例

::

    
    curl -s \
         -X DELETE `https://bj1.network.api.ustack.com/v2.0/vpn/vpnusers?fields=id&id=10e4b092-096e-4368-bfac-6fbb04bf38d1`_ \
         -H "X-Auth-Token: {token_id}" \
         -H "Content-Type: application/json" \
         -H "Accept: application/json"


返回样例 :


::

    HTTP/1.1 204 No Content
    Content-Length: 0
    Date: Fri, 08 May 2015 03:01:08 GMT




OpenVPN (OpenVPN)
----------------------------------------------------



查看所有的OpenVPN
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 GET /v2.0/vpn/openvpnconnections 查看所有的OpenVPN
请求参数

无。

返回参数
字段名 类型 描述 tenant_id string 该成员所属的租户ID status string 该OpenVPN的实际运行状态
name string 该OpenVPN的名字 router_id string 该OpenVPN所在的路由器的UUID port int
该OpenVPN服务的端口号 protocol string 该OpenVPN服务的使用的协议类型 admin_state_up bool
该OpenVPN的管理状态 peer_cidr string 该OpenVPN上对端分配的CIDR created_at string
该OpenVPN的创建时间，为UTC时间 id string 该OpenVPN的UUID
请求样例

::

    
    curl -s \
         -X GET `https://bj1.network.api.ustack.com/v2.0/vpn/openvpnconnections`_ \
         -H "X-Auth-Token: {token_id}" \
         -H "Content-Type: application/json" \
         -H "Accept: application/json"


返回样例 :


::

    {
        "openvpnconnections": [
            {
                "peer_cidr": "192.168.0.0/24",
                "status": "DOWN",
                "protocol": "udp",
                "description": "",
                "admin_state_up": true,
                "tenant_id": "7a4d5b1c6c8a4ce7ab0a0988c860a92d",
                "created_at": "2015-05-08 04:06:01",
                "id": "769b3c74-4b7d-4e56-a977-58fe61ba33f1",
                "router_id": "cec0d929-aefe-46c1-9850-bb89c1f02aeb",
                "port": 1156,
                "name": "openvpn-769b3c74"
            },
            {
                "peer_cidr": "192.168.0.0/24",
                "status": "ERROR",
                "protocol": "udp",
                "description": "",
                "admin_state_up": true,
                "tenant_id": "501d9b94e8cb4bdc98fddda04124bac7",
                "created_at": "2015-05-07 06:06:25",
                "id": "e7011d63-3d99-4eaf-ae57-d9d32919deca",
                "router_id": "eaaaa7b2-9107-4baa-9082-184642b262d5",
                "port": 2,
                "name": "openvpn-e7011d63"
            }
        ]
    }




创建OpenVPN
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 POST /v2.0/vpn/openvpnconnections 创建OpenVPN
请求参数
字段名 类型 描述 name string 该OpenVPN的名字 router_id string 该OpenVPN所在的路由器的UUID
port int 该OpenVPN服务的端口号 protocol string 该OpenVPN服务的使用的协议类型 peer_cidr
string 该OpenVPN上对端分配的CIDR
返回参数
字段名 类型 描述 tenant_id string 该成员所属的租户ID status string 该OpenVPN的实际运行状态
name string 该OpenVPN的名字 router_id string 该OpenVPN所在的路由器的UUID port int
该OpenVPN服务的端口号 protocol string 该OpenVPN服务的使用的协议类型 admin_state_up bool
该OpenVPN的管理状态 peer_cidr string 该OpenVPN上对端分配的CIDR created_at string
该OpenVPN的创建时间，为UTC时间 id string 该OpenVPN的UUID
请求样例

::

    
    curl -s \
         -X GET `https://bj1.network.api.ustack.com/v2.0/vpn/openvpnconnections`_ \
         -H "X-Auth-Token: {token_id}" \
         -H "Content-Type: application/json" \
         -H "Accept: application/json" \
         -d '{
                "openvpnconnection": {
                    "peer_cidr": "192.168.0.1/24",
                    "router_id": "e5561b3d-d909-4603-9e17-69a00a341f34",
                    "protocol": "tcp",
                    "name": "test",
                    "port": "1194"
                }
            }'


返回样例 :


::

    {
        "openvpnconnection": {
            "peer_cidr": "192.168.0.1/24",
            "status": "DOWN",
            "protocol": "tcp",
            "description": "",
            "admin_state_up": true,
            "tenant_id": "ee55d67b0fc14d71aa5cdd936b31e9de",
            "created_at": "2015-05-08 04:17:27.484387",
            "id": "8b7ffa60-3d5b-46de-b1ba-2c0b91ff4926",
            "router_id": "eaaaa7b2-9107-4baa-9082-184642b262d5",
            "port": 1193,
            "name": "test"
        }
    }




修改OpenVPN的信息
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 PUT /v2.0/vpn/openvpnconnections/{openvpn_id}
修改OpenVPN的信息
请求参数
字段名 类型 描述 admin_state_up bool 该OpenVPN的管理状态 port int 该OpenVPN服务的端口号
protocol string 该OpenVPN服务的使用的协议类型
返回参数
字段名 类型 描述 tenant_id string 该成员所属的租户ID status string 该OpenVPN的实际运行状态
name string 该OpenVPN的名字 router_id string 该OpenVPN所在的路由器的UUID port int
该OpenVPN服务的端口号 protocol string 该OpenVPN服务的使用的协议类型 admin_state_up bool
该OpenVPN的管理状态 peer_cidr string 该OpenVPN上对端分配的CIDR created_at string
该OpenVPN的创建时间，为UTC时间 id string 该OpenVPN的UUID
请求样例

::

    
    curl -s \
         -X GET `https://bj1.network.api.ustack.com/v2.0/vpn/openvpnconnections/8b7ffa60-3d5b-46de-b1ba-2c0b91ff4926`_ \
         -H "X-Auth-Token: {token_id}" \
         -H "Content-Type: application/json" \
         -H "Accept: application/json" \
         -d '{
                "openvpnconnection": {
                    "protocol": "tcp",
                    "port": "1234",
                    "REDACTED_state_up": "false"
                }
            }'


返回样例 :


::

    {
        "openvpnconnection": {
            "peer_cidr": "192.168.0.1/24",
            "status": "DOWN",
            "protocol": "tcp",
            "description": "",
            "admin_state_up": false,
            "tenant_id": "ee55d67b0fc14d71aa5cdd936b31e9de",
            "created_at": "2015-05-08 04:17:27",
            "id": "8b7ffa60-3d5b-46de-b1ba-2c0b91ff4926",
            "router_id": "eaaaa7b2-9107-4baa-9082-184642b262d5",
            "port": 1234,
            "name": "test"
        }
    }




查看OpenVPN的信息
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 GET /v2.0/vpn/openvpnconnections/{openvpn_id}
查看OpenVPN的信息
请求参数

无

返回参数
字段名 类型 描述 tenant_id string 该成员所属的租户ID status string 该OpenVPN的实际运行状态
name string 该OpenVPN的名字 router_id string 该OpenVPN所在的路由器的UUID port int
该OpenVPN服务的端口号 protocol string 该OpenVPN服务的使用的协议类型 admin_state_up bool
该OpenVPN的管理状态 peer_cidr string 该OpenVPN上对端分配的CIDR created_at string
该OpenVPN的创建时间，为UTC时间 id string 该OpenVPN的UUID
请求样例

::

    
    curl -s \
         -X GET `https://bj1.network.api.ustack.com/v2.0/vpn/openvpnconnections/8b7ffa60-3d5b-46de-b1ba-2c0b91ff4926`_ \
         -H "X-Auth-Token: {token_id}" \
         -H "Content-Type: application/json" \
         -H "Accept: application/json"


返回样例 :


::

    {
        "openvpnconnection": {
            "peer_cidr": "192.168.0.1/24",
            "status": "DOWN",
            "protocol": "tcp",
            "description": "",
            "admin_state_up": false,
            "tenant_id": "ee55d67b0fc14d71aa5cdd936b31e9de",
            "created_at": "2015-05-08 04:17:27",
            "id": "8b7ffa60-3d5b-46de-b1ba-2c0b91ff4926",
            "router_id": "eaaaa7b2-9107-4baa-9082-184642b262d5",
            "port": 1234,
            "name": "test"
        }
    }




删除OpenVPN
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 DELETE /v2.0/vpn/openvpnconnections/{openvpn_id}
删除OpenVPN
请求参数

无

返回参数

无

请求样例

::

    
    curl -s \
         -X DELETE `https://bj1.network.api.ustack.com/v2.0/vpn/openvpnconnections/e7011d63-3d99-4eaf-ae57-d9d32919deca`_ \
         -H "X-Auth-Token: {token_id}" \
         -H "Content-Type: application/json" \
         -H "Accept: application/json"


返回样例 :


::

    HTTP/1.1 204 No Content
    Content-Length: 0
    Date: Fri, 08 May 2015 03:01:08 GMT


