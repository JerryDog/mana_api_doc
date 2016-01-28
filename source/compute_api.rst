


计算服务
====================

.. toctree::
   :maxdepth: 2
   :numbered:


API规范
--------------------------

计算服务API入口与API列表如下:


+ API入口:

+----------------+-------------------------------------+
|  区域          |  API入口                            |
+================+=====================================+
|  北京1区(bj1)  |  https://bj1.compute.api.ustack.com |
+----------------+-------------------------------------+
|  广东1区(gd1)  |  https://gd1.compute.api.ustack.com |
+----------------+-------------------------------------+

+ API列表:

+--------------------------+----------------------------------------------+-----------+---------------------------------------------------------------+
|  资源                    |  操作                                        |  HTTP方法 |  URI路径                                                      |
+--------------------------+----------------------------------------------+-----------+---------------------------------------------------------------+
|  主机 (Servers)          |  :ref:`nova-create-instance`                 |  POST     |  /v2/{project_id}/servers                                     |
|                          +----------------------------------------------+-----------+---------------------------------------------------------------+
|                          |  :ref:`nova-index-instances`                 |  GET      |  /v2/{project_id}/servers                                     |
|                          +----------------------------------------------+-----------+---------------------------------------------------------------+
|                          |  :ref:`nova-index-instances-in-detail`       |  GET      |  /v2/{project_id}/servers/detail                              |
|                          +----------------------------------------------+-----------+---------------------------------------------------------------+
|                          |  :ref:`nova-show-instance`                   |  GET      |  /v2/{project_id}/servers/{server_id}                         |
|                          +----------------------------------------------+-----------+---------------------------------------------------------------+
|                          |  :ref:`nova-update-instance`                 |  PUT      |  /v2/{project_id}/servers/{server_id}                         |
|                          +----------------------------------------------+-----------+---------------------------------------------------------------+
|                          |  :ref:`nova-delete-instance`                 |  DELETE   |  /v2/{project_id}/servers/{server_id}                         |
|                          +----------------------------------------------+-----------+---------------------------------------------------------------+
|                          |  :ref:`nova-reboot-instance`                 |  POST     |  /v2/{project_id}/servers/{server_id}/action                  |
|                          +----------------------------------------------+-----------+---------------------------------------------------------------+
|                          |  :ref:`nova-start-instance`                  |  POST     |  /v2/{project_id}/servers/{server_id}/action                  |
|                          +----------------------------------------------+-----------+---------------------------------------------------------------+
|                          |  :ref:`nova-shutdown-instance`               |  POST     |  /v2/{project_id}/servers/{server_id}/action                  |
|                          +----------------------------------------------+-----------+---------------------------------------------------------------+
|                          |  :ref:`nova-stop-instance`                   |  POST     |  /v2/{project_id}/servers/{server_id}/action                  |
|                          +----------------------------------------------+-----------+---------------------------------------------------------------+
|                          |  :ref:`nova-change-instance-admin-password`  |  POST     |  /v2/{project_id}/servers/{server_id}/action                  |
|                          +----------------------------------------------+-----------+---------------------------------------------------------------+
|                          |  :ref:`nova-snapshot-instance`               |  POST     |  /v2/{project_id}/servers/{server_id}/action                  |
+--------------------------+----------------------------------------------+-----------+---------------------------------------------------------------+
|  密钥 (Key Pairs)        |  :ref:`nova-create-keypair`                  |  POST     |  /v2/{project_id}/os-keypairs                                 |
|                          +----------------------------------------------+-----------+---------------------------------------------------------------+
|                          |  :ref:`nova-import-keypair`                  |  POST     |  /v2/{project_id}/os-keypairs                                 |
|                          +----------------------------------------------+-----------+---------------------------------------------------------------+
|                          |  :ref:`nova-list-keypairs`                   |  GET      |  /v2/{project_id}/os-keypairs                                 |
|                          +----------------------------------------------+-----------+---------------------------------------------------------------+
|                          |  :ref:`nova-show-keypair`                    |  GET      |  /v2/{project_id}/os-keypairs/{keypair_name}                  |
|                          +----------------------------------------------+-----------+---------------------------------------------------------------+
|                          |  :ref:`nova-delete-keypair`                  |  DELETE   |  /v2/{project_id}/os-keypairs/{keypair_name}                  |
|                          +----------------------------------------------+-----------+---------------------------------------------------------------+
|                          |  :ref:`nova-attach-keypairs`                 |  POST     |  /v2/{project_id}/servers/{server_id}/action                  |
|                          +----------------------------------------------+-----------+---------------------------------------------------------------+
|                          |  :ref:`nova-detach-keypairs`                 |  POST     |  /v2/{project_id}/servers/{server_id}/action                  |
+--------------------------+----------------------------------------------+-----------+---------------------------------------------------------------+
|  云硬盘 (Volumes)        |  :ref:`nova-attach-volumes`                  |  POST     |  /v2/{project_id}/servers/{server_id}/action                  |
|                          +----------------------------------------------+-----------+---------------------------------------------------------------+
|                          |  :ref:`nova-detach-volumes`                  |  POST     |  /v2/{project_id}/servers/{server_id}/action                  |
+--------------------------+----------------------------------------------+-----------+---------------------------------------------------------------+
|  配置 (Flavors)          |  :ref:`nova-list-flavors`                    |  GET      |  /v2/{project_id}/flavors                                     |
|                          +----------------------------------------------+-----------+---------------------------------------------------------------+
|                          |  :ref:`nova-list-flavors-in-detail`          |  GET      |  /v2/{project_id}/flavors/detail                              |
|                          +----------------------------------------------+-----------+---------------------------------------------------------------+
|                          |  :ref:`nova-show-flavor`                     |  GET      |  /v2/{project_id}/flavors/{flavor_id}                         |
+--------------------------+----------------------------------------------+-----------+---------------------------------------------------------------+
|  VNC终端 (VNC Console)   |  :ref:`nova-vnc-address`                     |  POST     |  /v2/{project_id}/servers/{server_id}/action                  |
+--------------------------+----------------------------------------------+-----------+---------------------------------------------------------------+
|  网络 (Networks)         |  :ref:`nova-attach-interface`                |  POST     |  /v2/{project_id}/servers/{server_id}/os-interface            |
|                          +----------------------------------------------+-----------+---------------------------------------------------------------+
|                          |  :ref:`nova-detach-interface`                |  DELETE   |  /v2/{project_id}/servers/{server_id}/os-interface/{port_id}  |
|                          +----------------------------------------------+-----------+---------------------------------------------------------------+
|                          |  :ref:`nova-attach-network`                  |  POST     |  /v2/{project_id}/servers/{server_id}/os-interface            |
+--------------------------+----------------------------------------------+-----------+---------------------------------------------------------------+
|  安全组(Security Group)  |  :ref:`neutron-security-groups`              |  N/A      |  N/A                                                          |
+--------------------------+----------------------------------------------+-----------+---------------------------------------------------------------+
|  公网IP (Floating IPs)   |  :ref:`neutron-api-floating-ip`              |  N/A      |  N/A                                                          |
+--------------------------+----------------------------------------------+-----------+---------------------------------------------------------------+

主机(Servers )
----------------------------------------

.. _nova-create-instance:

创建云主机
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

+------------+----------------------------+--------------+
|  HTTP方法  |  URI路径                   |  描述        |
+------------+----------------------------+--------------+
|  POST      |  /v2/{project_id}/servers  |  创建云主机  |
+------------+----------------------------+--------------+

请求参数

+-------------+--------------+--------------------------------+
|  字段名     |  类型        |  描述                          |
+=============+==============+================================+
|  flavorRef  |  uuid        |  云主机的配置                  |
+-------------+--------------+--------------------------------+
|  imageRef   |  uuid        |  用来创建云主机的镜像模板      |
+-------------+--------------+--------------------------------+
|  name       |  string      |  云主机的名称                  |
+-------------+--------------+--------------------------------+
|  max_count  |  int         |                                |
|             |  (optional)  |  创建云主机的数量, 默认是一台  |
+-------------+--------------+--------------------------------+
|  networks   |  dict        |  创建的云主机应该加入哪些网络  |
+-------------+--------------+--------------------------------+

请求样例

::

    
    curl -s \
         -X POST `https://bj1.compute.api.ustack.com/v2/{project_id}/servers`_ \
         -H 'Content-Type: application/json' \
         -H 'Accept: application/json' \
         -H 'X-Auth-Token: {token_id}' \
         -d '{
                "server": {
                    "flavorRef": "3332c026-533a-43d0-b415-abd3fdab09bf",
                    "imageRef": "61c662a0-673b-4b02-a191-235716118b7c",
                    "max_count": 1,
                    "min_count": 1,
                    "name": "api-test-1",
                    "networks": [
                        {
                            "uuid": "ba05e057-1eb8-4cb2-af58-9b99a72df5ed"
                        }
                    ]
                }
            }'


返回参数

+-------------------+----------+--------------------------------------------------------+
|  字段名           |  类型    |  描述                                                  |
+===================+==========+========================================================+
|  id               |  uuid    |  云主机的唯一标识                                      |
+-------------------+----------+--------------------------------------------------------+
|  links            |  list    |  云主机的链接, 通过这些链接可以获取云主机更详细的信息  |
+-------------------+----------+--------------------------------------------------------+
|  adminPass        |  string  |  云主机的密码                                          |
+-------------------+----------+--------------------------------------------------------+
|  security_groups  |  dict    |  云主机加入的安全组                                    |
+-------------------+----------+--------------------------------------------------------+

返回样例

::

    
    HTTP/1.1 202
    
    {
        "server": {
            "security_groups": [
                {
                    "name": "default"
                }
            ],
            "OS-DCF:diskConfig": "MANUAL",
            "id": "32afdc4b-e044-43e7-b4b4-f8eb7bb214ef",
            "links": [
                {
                    "href": "`https://bj1.compute.api.ustack.com/v2/0f1255df40374d02a23e1a6ceeaefec7/servers/32afdc4b-e044-43e7-b4b4-f8eb7bb214ef`_",
                    "rel": "self"
                },
                {
                    "href": "`https://bj1.compute.api.ustack.com/0f1255df40374d02a23e1a6ceeaefec7/servers/32afdc4b-e044-43e7-b4b4-f8eb7bb214ef`_",
                    "rel": "bookmark"
                }
            ],
            "adminPass": "B4Qd6yCiJSnh"
        }
    }


.. _nova-index-instances:

查看所有主机基本信息
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

+------------+----------------------------+------------------------+
|  HTTP方法  |  URI路径                   |  描述                  |
+============+============================+========================+
|  GET       |  /v2/{project_id}/servers  |  查看所有主机基本信息  |
+------------+----------------------------+------------------------+

请求参数

请求样例

::

    
    curl  -s \
          -X GET `https://bj1.compute.api.ustack.com/v2/{project_id}/servers`_ \
          -H 'Content-Type: application/json' \
          -H 'Accept: application/json' \
          -H 'X-Auth-Token: {token_id}'


返回参数

+----------+----------+-------------------------------------------------------+
|  字段名  |  类型    |  描述                                                 |
+==========+==========+=======================================================+
|  id      |  uuid    |  云主机的唯一标识                                     |
+----------+----------+-------------------------------------------------------+
|  name    |  string  |  云主机的名称                                         |
+----------+----------+-------------------------------------------------------+
|  links   |  list    |  云主机的链接,通过这些链接可以获取云主机更详细的信息  |
+----------+----------+-------------------------------------------------------+

返回样例

::

    
    HTTP/1.1 200
    
    {
        "servers": [
            {
                "addresses": {
                    "shared": [
                        {
                            "UOS-EXT-IPS:subnet_name": "shared_subnet",
                            "UOS-EXT-IPS:id": "e37e5768-7dd9-46cb-a644-6f0a57c514a4",
                            "addr": "172.31.248.111",
                            "UOS-EXT-IPS:subnet_shared": true,
                            "version": 4,
                            "UOS-EXT-IPS:subnet_id": "0383c257-d730-4bbc-bd20-c7482bc925e8"
                        }
                    ]
                },
                "id": "e77bcccf-f73c-425d-8b18-a08193fbdf9c",
                "links": [
                    {
                        "href": "`https://bj1.compute.api.ustack.com/v2/0f1255df40374d02a23e1a6ceeaefec7/servers/e77bcccf-f73c-425d-8b18-a08193fbdf9c`_",
                        "rel": "self"
                    },
                    {
                        "href": "`https://bj1.compute.api.ustack.com/0f1255df40374d02a23e1a6ceeaefec7/servers/e77bcccf-f73c-425d-8b18-a08193fbdf9c`_",
                        "rel": "bookmark"
                    }
                ],
                "name": "server-1"
            },
            {
                "addresses": {
                    "shared": [
                        {
                            "UOS-EXT-IPS:subnet_name": "shared_subnet",
                            "UOS-EXT-IPS:id": "9538f8fb-c88b-4254-9ca0-b2d14e1a17a6",
                            "addr": "172.31.250.86",
                            "UOS-EXT-IPS:subnet_shared": true,
                            "version": 4,
                            "UOS-EXT-IPS:subnet_id": "0383c257-d730-4bbc-bd20-c7482bc925e8"
                        }
                    ]
                },
                "id": "5c2c75ad-2e15-43eb-8921-1bdcda5f21ae",
                "links": [
                    {
                        "href": "`https://bj1.compute.api.ustack.com/v2/0f1255df40374d02a23e1a6ceeaefec7/servers/5c2c75ad-2e15-43eb-8921-1bdcda5f21ae`_",
                        "rel": "self"
                    },
                    {
                        "href": "`https://bj1.compute.api.ustack.com/0f1255df40374d02a23e1a6ceeaefec7/servers/5c2c75ad-2e15-43eb-8921-1bdcda5f21ae`_",
                        "rel": "bookmark"
                    }
                ],
                "name": "server-2"
            }
        ]
    }


.. _nova-index-instances-in-detail:

查看所有主机详细信息
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

+------------+-----------------------------------+------------------------+
|  HTTP方法  |  URI路径                          |  描述                  |
+============+===================================+========================+
|  GET       |  /v2/{project_id}/servers/detail  |  查看所有主机详细信息  |
+------------+-----------------------------------+------------------------+

请求参数

请求样例

::

    
    curl  -s \
          -X GET `https://bj1.compute.api.ustack.com/v2/{project_id}/servers/detail`_ \
          -H 'Content-Type: application/json' \
          -H 'Accept: application/json' \
          -H 'X-Auth-Token: {token_id}'


返回参数

+----------------------------------------+----------+-------------------------------------------------------+
|  字段名                                |  类型    |  描述                                                 |
+========================================+==========+=======================================================+
|  id                                    |  uuid    |  云主机的唯一标识                                     |
+----------------------------------------+----------+-------------------------------------------------------+
|  name                                  |  string  |  云主机的名称                                         |
+----------------------------------------+----------+-------------------------------------------------------+
|  links                                 |  list    |  云主机的链接,通过这些链接可以获取云主机更详细的信息  |
+----------------------------------------+----------+-------------------------------------------------------+
|  flavor                                |  dict    |  云主机的配置信息                                     |
+----------------------------------------+----------+-------------------------------------------------------+
|  image                                 |  dict    |  云主机所使用的镜像模板信息                           |
+----------------------------------------+----------+-------------------------------------------------------+
|  security_groups                       |  dict    |  云主机加入的安全组                                   |
+----------------------------------------+----------+-------------------------------------------------------+
|  user_id                               |  uuid    |  创建云主机的用户的id                                 |
+----------------------------------------+----------+-------------------------------------------------------+
|  tenant_id                             |  uuid    |  云主机所属的tenant的id                               |
+----------------------------------------+----------+-------------------------------------------------------+
|  tenant_id                             |  uuid    |  云主机所属的tenant的id                               |
+----------------------------------------+----------+-------------------------------------------------------+
|  addresses                             |  list    |  云主机的IP地址信息                                   |
+----------------------------------------+----------+-------------------------------------------------------+
|  accessIPv4                            |  string  |  访问云主机的IPv4地址信息                             |
+----------------------------------------+----------+-------------------------------------------------------+
|  accessIPv6                            |  string  |  访问云主机的IPv6地址信息                             |
+----------------------------------------+----------+-------------------------------------------------------+
|  key_name                              |  string  |  云主机已挂载的密钥对的名称                           |
+----------------------------------------+----------+-------------------------------------------------------+
|  OS-EXT-STS:task_state                 |  string  |  云主机执行任务的状态                                 |
+----------------------------------------+----------+-------------------------------------------------------+
|  OS-EXT-STS:vm_state                   |  string  |  云主机当前的状态                                     |
+----------------------------------------+----------+-------------------------------------------------------+
|  OS-EXT-STS:power_state                |  string  |  云主机的运行状态                                     |
+----------------------------------------+----------+-------------------------------------------------------+
|  os-extended-volumes:volumes_attached  |  list    |  挂载到云主机块设备的信息                             |
+----------------------------------------+----------+-------------------------------------------------------+

返回样例

::

    
    HTTP/1.1 200
    
    {
        "servers": [
            {
                "status": "BUILD",
                "updated": "2014-07-14T04:21:34Z",
                "hostId": "06e1184d055ae2f7aa31aa02a06e84d5c446c5ead81ca392c7b0bc8d",
                "OS-EXT-SRV-ATTR:host": "server-85",
                "addresses": {
                    "shared": [
                        {
                            "OS-EXT-IPS-MAC:mac_addr": "fa:16:3e:0b:ab:0e",
                            "UOS-EXT-IPS:subnet_name": "shared_subnet",
                            "UOS-EXT-IPS:id": "66add13a-2ba9-41ab-bebb-fcfc8f1f4a94",
                            "addr": "172.31.251.252",
                            "OS-EXT-IPS:type": "fixed",
                            "UOS-EXT-IPS:subnet_shared": true,
                            "version": 4,
                            "UOS-EXT-IPS:subnet_id": "0383c257-d730-4bbc-bd20-c7482bc925e8"
                        }
                    ]
                },
                "links": [
                    {
                        "href": "`https://bj1.compute.api.ustack.com/v2/0f1255df40374d02a23e1a6ceeaefec7/servers/b0aca7fe-a4b7-4e12-9ed3-903634311fcf`_",
                        "rel": "self"
                    },
                    {
                        "href": "`https://bj1.compute.api.ustack.com/0f1255df40374d02a23e1a6ceeaefec7/servers/b0aca7fe-a4b7-4e12-9ed3-903634311fcf`_",
                        "rel": "bookmark"
                    }
                ],
                "key_name": null,
                "image": {
                    "id": "81ebf00b-6221-43ff-8551-f8908520dad5",
                    "links": [
                        {
                            "href": "`https://bj1.compute.api.ustack.com/0f1255df40374d02a23e1a6ceeaefec7/images/81ebf00b-6221-43ff-8551-f8908520dad5`_",
                            "rel": "bookmark"
                        }
                    ],
                    "name": "Ubuntu 13.04 x64"
                },
                "OS-EXT-STS:task_state": "spawning",
                "OS-EXT-STS:vm_state": "building",
                "OS-EXT-SRV-ATTR:instance_name": "instance-00006faf",
                "OS-SRV-USG:launched_at": null,
                "OS-EXT-SRV-ATTR:hypervisor_hostname": "server-85.0.lg.ustack.in",
                "flavor": {
                    "id": "8abaa0f9-30e1-4509-8ba5-5c97366029df",
                    "links": [
                        {
                            "href": "`https://bj1.compute.api.ustack.com/0f1255df40374d02a23e1a6ceeaefec7/flavors/8abaa0f9-30e1-4509-8ba5-5c97366029df`_",
                            "rel": "bookmark"
                        }
                    ],
                    "name": "micro-1"
                },
                "id": "b0aca7fe-a4b7-4e12-9ed3-903634311fcf",
                "security_groups": [
                    {
                        "port_id": "66add13a-2ba9-41ab-bebb-fcfc8f1f4a94",
                        "name": "default",
                        "id": "10d1b09c-b230-4d50-b20b-1a86f62ce0a6"
                    }
                ],
                "OS-SRV-USG:terminated_at": null,
                "OS-EXT-AZ:availability_zone": "nova",
                "user_id": "d77df5d8b15349fcb460f1cec8814d47",
                "name": "server-1",
                "created": "2014-07-14T04:21:32Z",
                "tenant_id": "0f1255df40374d02a23e1a6ceeaefec7",
                "OS-DCF:diskConfig": "MANUAL",
                "os-extended-volumes:volumes_attached": [],
                "accessIPv4": "",
                "accessIPv6": "",
                "progress": 0,
                "OS-EXT-STS:power_state": 0,
                "config_drive": "",
                "metadata": {}
            },
            {
                "status": "ACTIVE",
                "updated": "2014-07-09T03:01:29Z",
                "hostId": "06e1184d055ae2f7aa31aa02a06e84d5c446c5ead81ca392c7b0bc8d",
                "OS-EXT-SRV-ATTR:host": "server-85",
                "addresses": {
                    "shared": [
                        {
                            "OS-EXT-IPS-MAC:mac_addr": "fa:16:3e:dc:d3:92",
                            "UOS-EXT-IPS:subnet_name": "shared_subnet",
                            "UOS-EXT-IPS:id": "ba1add27-5d59-4b18-ba26-8458aad9baac",
                            "addr": "172.31.250.129",
                            "OS-EXT-IPS:type": "fixed",
                            "UOS-EXT-IPS:subnet_shared": true,
                            "version": 4,
                            "UOS-EXT-IPS:subnet_id": "0383c257-d730-4bbc-bd20-c7482bc925e8"
                        }
                    ]
                },
                "links": [
                    {
                        "href": "`https://bj1.compute.api.ustack.com/v2/0f1255df40374d02a23e1a6ceeaefec7/servers/d3a5ff23-9128-466c-ae13-60ecc0ff99aa`_",
                        "rel": "self"
                    },
                    {
                        "href": "`https://bj1.compute.api.ustack.com/0f1255df40374d02a23e1a6ceeaefec7/servers/d3a5ff23-9128-466c-ae13-60ecc0ff99aa`_",
                        "rel": "bookmark"
                    }
                ],
                "key_name": null,
                "image": {
                    "id": "81ebf00b-6221-43ff-8551-f8908520dad5",
                    "links": [
                        {
                            "href": "`https://bj1.compute.api.ustack.com/0f1255df40374d02a23e1a6ceeaefec7/images/81ebf00b-6221-43ff-8551-f8908520dad5`_",
                            "rel": "bookmark"
                        }
                    ],
                    "name": "Ubuntu 13.04 x64"
                },
                "OS-EXT-STS:task_state": null,
                "OS-EXT-STS:vm_state": "active",
                "OS-EXT-SRV-ATTR:instance_name": "instance-000068d9",
                "OS-SRV-USG:launched_at": "2014-07-09T03:01:29.000000",
                "OS-EXT-SRV-ATTR:hypervisor_hostname": "server-85.0.lg.ustack.in",
                "flavor": {
                    "id": "8abaa0f9-30e1-4509-8ba5-5c97366029df",
                    "links": [
                        {
                            "href": "`https://bj1.compute.api.ustack.com/0f1255df40374d02a23e1a6ceeaefec7/flavors/8abaa0f9-30e1-4509-8ba5-5c97366029df`_",
                            "rel": "bookmark"
                        }
                    ],
                    "name": "micro-1"
                },
                "id": "d3a5ff23-9128-466c-ae13-60ecc0ff99aa",
                "security_groups": [
                    {
                        "port_id": "ba1add27-5d59-4b18-ba26-8458aad9baac",
                        "name": "default",
                        "id": "10d1b09c-b230-4d50-b20b-1a86f62ce0a6"
                    }
                ],
                "OS-SRV-USG:terminated_at": null,
                "OS-EXT-AZ:availability_zone": "nova",
                "user_id": "d77df5d8b15349fcb460f1cec8814d47",
                "name": "server-2",
                "created": "2014-07-09T03:01:20Z",
                "tenant_id": "0f1255df40374d02a23e1a6ceeaefec7",
                "OS-DCF:diskConfig": "MANUAL",
                "os-extended-volumes:volumes_attached": [],
                "accessIPv4": "",
                "accessIPv6": "",
                "progress": 0,
                "OS-EXT-STS:power_state": 1,
                "config_drive": "",
                "metadata": {}
            }
        ]
    }


.. _nova-show-instance:

查看指定主机信息
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

+------------+----------------------------------------+--------------------+
|  HTTP方法  |  URI路径                               |  描述              |
+============+========================================+====================+
|  GET       |  /v2/{project_id}/servers/{server_id}  |  查看指定主机信息  |
+------------+----------------------------------------+--------------------+

请求参数

请求样例

::

    
    curl  -s \
          -X GET `https://bj1.compute.api.ustack.com/v2/{project_id}/servers/{server_id}`_ \
          -H 'Content-Type: application/json' \
          -H 'Accept: application/json' \
          -H 'X-Auth-Token: {token_id}'


返回参数

+----------------------------------------+----------+-------------------------------------------------------+
|  字段名                                |  类型    |  描述                                                 |
+========================================+==========+=======================================================+
|  id                                    |  uuid    |  云主机的唯一标识                                     |
+----------------------------------------+----------+-------------------------------------------------------+
|  name                                  |  string  |  云主机的名称                                         |
+----------------------------------------+----------+-------------------------------------------------------+
|  links                                 |  list    |  云主机的链接,通过这些链接可以获取云主机更详细的信息  |
+----------------------------------------+----------+-------------------------------------------------------+
|  flavor                                |  dict    |  云主机的配置信息                                     |
+----------------------------------------+----------+-------------------------------------------------------+
|  image                                 |  dict    |  云主机所使用的镜像模板信息                           |
+----------------------------------------+----------+-------------------------------------------------------+
|  security_groups                       |  dict    |  云主机加入的安全组                                   |
+----------------------------------------+----------+-------------------------------------------------------+
|  user_id                               |  uuid    |  创建云主机的用户的id                                 |
+----------------------------------------+----------+-------------------------------------------------------+
|  tenant_id                             |  uuid    |  云主机所属的tenant的id                               |
+----------------------------------------+----------+-------------------------------------------------------+
|  tenant_id                             |  uuid    |  云主机所属的tenant的id                               |
+----------------------------------------+----------+-------------------------------------------------------+
|  addresses                             |  list    |  云主机的IP地址信息                                   |
+----------------------------------------+----------+-------------------------------------------------------+
|  accessIPv4                            |  string  |  访问云主机的IPv4地址信息                             |
+----------------------------------------+----------+-------------------------------------------------------+
|  accessIPv6                            |  string  |  访问云主机的IPv6地址信息                             |
+----------------------------------------+----------+-------------------------------------------------------+
|  key_name                              |  string  |  云主机已挂载的密钥对的名称                           |
+----------------------------------------+----------+-------------------------------------------------------+
|  OS-EXT-STS:task_state                 |  string  |  云主机执行任务的状态                                 |
+----------------------------------------+----------+-------------------------------------------------------+
|  OS-EXT-STS:vm_state                   |  string  |  云主机当前的状态                                     |
+----------------------------------------+----------+-------------------------------------------------------+
|  OS-EXT-STS:power_state                |  string  |  云主机的运行状态                                     |
+----------------------------------------+----------+-------------------------------------------------------+
|  os-extended-volumes:volumes_attached  |  list    |  挂载到云主机块设备的信息                             |
+----------------------------------------+----------+-------------------------------------------------------+

返回样例

::

    
    HTTP/1.1 200
    
    {
        "server": {
            "status": "ACTIVE",
            "updated": "2014-05-30T02:40:17Z",
            "hostId": "c4f0030a64a5647139867f8b8c3796ab1c166da104c94467fcb68dd0",
            "OS-EXT-SRV-ATTR:host": "server-72",
            "addresses": {
                "shared": [
                    {
                        "OS-EXT-IPS-MAC:mac_addr": "fa:16:3e:32:70:ac",
                        "UOS-EXT-IPS:subnet_name": "shared_subnet",
                        "UOS-EXT-IPS:id": "4c926f83-f947-4376-a3f3-071e56b08974",
                        "addr": "172.31.248.190",
                        "OS-EXT-IPS:type": "fixed",
                        "UOS-EXT-IPS:subnet_shared": true,
                        "version": 4,
                        "UOS-EXT-IPS:subnet_id": "0383c257-d730-4bbc-bd20-c7482bc925e8"
                    }
                ]
            },
            "links": [
                {
                    "href": "`https://bj1.compute.api.ustack.com/v2/0f1255df40374d02a23e1a6ceeaefec7/servers/67b2b502-bf0d-428a-a2ad-1e342b6eee93`_",
                    "rel": "self"
                },
                {
                    "href": "`https://bj1.compute.api.ustack.com/0f1255df40374d02a23e1a6ceeaefec7/servers/67b2b502-bf0d-428a-a2ad-1e342b6eee93`_",
                    "rel": "bookmark"
                }
            ],
            "key_name": null,
            "image": {
                "id": "61c662a0-673b-4b02-a191-235716118b7c",
                "links": [
                    {
                        "href": "`https://bj1.compute.api.ustack.com/0f1255df40374d02a23e1a6ceeaefec7/images/61c662a0-673b-4b02-a191-235716118b7c`_",
                        "rel": "bookmark"
                    }
                ],
                "name": "Ubuntu 13.04 x64"
            },
            "OS-EXT-STS:task_state": null,
            "OS-EXT-STS:vm_state": "active",
            "OS-EXT-SRV-ATTR:instance_name": "instance-000024f4",
            "OS-SRV-USG:launched_at": "2014-05-30T02:32:35.000000",
            "OS-EXT-SRV-ATTR:hypervisor_hostname": "server-72.0.lg.ustack.in",
            "flavor": {
                "id": "3332c026-533a-43d0-b415-abd3fdab09bf",
                "links": [
                    {
                        "href": "`https://bj1.compute.api.ustack.com/0f1255df40374d02a23e1a6ceeaefec7/flavors/3332c026-533a-43d0-b415-abd3fdab09bf`_",
                        "rel": "bookmark"
                    }
                ],
                "name": "micro-2"
            },
            "id": "67b2b502-bf0d-428a-a2ad-1e342b6eee93",
            "security_groups": [
                {
                    "port_id": "4c926f83-f947-4376-a3f3-071e56b08974",
                    "name": "default",
                    "id": "10d1b09c-b230-4d50-b20b-1a86f62ce0a6"
                }
            ],
            "OS-SRV-USG:terminated_at": null,
            "OS-EXT-AZ:availability_zone": "nova",
            "user_id": "d77df5d8b15349fcb460f1cec8814d47",
            "name": "server-1",
            "created": "2014-05-30T02:32:27Z",
            "tenant_id": "0f1255df40374d02a23e1a6ceeaefec7",
            "OS-DCF:diskConfig": "MANUAL",
            "os-extended-volumes:volumes_attached": [],
            "accessIPv4": "",
            "accessIPv6": "",
            "progress": 0,
            "OS-EXT-STS:power_state": 1,
            "config_drive": "",
            "metadata": {}
        }
    }


.. _nova-update-instance:

修改主机名字
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

+------------+----------------------------------------+----------------+
|  HTTP方法  |  URI路径                               |  描述          |
+============+========================================+================+
|  PUT       |  /v2/{project_id}/servers/{server_id}  |  修改主机名字  |
+------------+----------------------------------------+----------------+

请求参数

请求样例

::

    
    curl  -s \
          -X PUT `https://bj1.compute.api.ustack.com/v2/{project_id}/servers/{server_id}`_ \
          -H 'Content-Type: application/json' \
          -H 'Accept: application/json' \
          -H 'X-Auth-Token: {token_id}' \
          -d '{
                 "server": {
                     "name": "new-name"
                 }
             }'


返回参数

::

    
    HTTP/1.1 200
    
    {
        "server": {
            "status": "ACTIVE",
            "updated": "2014-05-30T03:07:56Z",
            "hostId": "c4f0030a64a5647139867f8b8c3796ab1c166da104c94467fcb68dd0",
            "addresses": {
                "shared": [
                    {
                        "UOS-EXT-IPS:subnet_name": "shared_subnet",
                        "UOS-EXT-IPS:id": "4c926f83-f947-4376-a3f3-071e56b08974",
                        "addr": "172.31.248.190",
                        "UOS-EXT-IPS:subnet_shared": true,
                        "version": 4,
                        "UOS-EXT-IPS:subnet_id": "0383c257-d730-4bbc-bd20-c7482bc925e8"
                    }
                ]
            },
            "links": [
                {
                    "href": "`https://bj1.compute.api.ustack.com/v2/0f1255df40374d02a23e1a6ceeaefec7/servers/67b2b502-bf0d-428a-a2ad-1e342b6eee93`_",
                    "rel": "self"
                },
                {
                    "href": "`https://bj1.compute.api.ustack.com/0f1255df40374d02a23e1a6ceeaefec7/servers/67b2b502-bf0d-428a-a2ad-1e342b6eee93`_",
                    "rel": "bookmark"
                }
            ],
            "image": {
                "id": "61c662a0-673b-4b02-a191-235716118b7c",
                "links": [
                    {
                        "href": "`https://bj1.compute.api.ustack.com/0f1255df40374d02a23e1a6ceeaefec7/images/61c662a0-673b-4b02-a191-235716118b7c`_",
                        "rel": "bookmark"
                    }
                ]
            },
            "flavor": {
                "id": "3332c026-533a-43d0-b415-abd3fdab09bf",
                "links": [
                    {
                        "href": "`https://bj1.compute.api.ustack.com/0f1255df40374d02a23e1a6ceeaefec7/flavors/3332c026-533a-43d0-b415-abd3fdab09bf`_",
                        "rel": "bookmark"
                    }
                ]
            },
            "id": "67b2b502-bf0d-428a-a2ad-1e342b6eee93",
            "user_id": "d77df5d8b15349fcb460f1cec8814d47",
            "name": "new-name",
            "created": "2014-05-30T02:32:27Z",
            "tenant_id": "0f1255df40374d02a23e1a6ceeaefec7",
            "OS-DCF:diskConfig": "MANUAL",
            "accessIPv4": "",
            "accessIPv6": "",
            "progress": 0,
            "metadata": {}
        }
    }


.. _nova-delete-instance:

删除主机
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

+------------+----------------------------------------+------------------+
|  HTTP方法  |  URI路径                               |  描述            |
+============+========================================+==================+
|  DELETE    |  /v2/{project_id}/servers/{server_id}  |  删除指定的主机  |
+------------+----------------------------------------+------------------+

请求参数

请求样例

::

    
    curl  -s \
          -X DELETE `https://bj1.compute.api.ustack.com/v2/{project_id}/servers/{server_id}`_ \
          -H 'Content-Type: application/json' \
          -H 'Accept: application/json' \
          -H 'X-Auth-Token: {token_id}'


返回参数


::

    HTTP/1.1 202


.. _nova-reboot-instance:

重启主机
~~~~~~~~~~~~~~~~~~~~~~~~~~

+------------+-----------------------------------------------+------------+
|  HTTP方法  |  URI路径                                      |  描述      |
+============+===============================================+============+
|  POST      |  /v2/{project_id}/servers/{server_id}/action  |  重启主机  |
+------------+-----------------------------------------------+------------+

请求参数

请求样例

::

    
    curl  -s \
          -X POST `https://bj1.compute.api.ustack.com/v2/{project_id}/servers/{server_id}/action`_ \
          -H 'Content-Type: application/json' \
          -H 'Accept: application/json' \
          -H 'X-Auth-Token: {token_id}' \
          -d '{
                 "reboot": {
                     "type": "SOFT"
                 }
             }'


返回参数

返回样例


::

    HTTP/1.1 202


.. _nova-start-instance:

启动主机
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

+------------+-----------------------------------------------+------------+
|  HTTP方法  |  URI路径                                      |  描述      |
+============+===============================================+============+
|  POST      |  /v2/{project_id}/servers/{server_id}/action  |  启动主机  |
+------------+-----------------------------------------------+------------+

请求参数

请求样例

::

    
    curl  -s \
          -X POST `https://bj1.compute.api.ustack.com/v2/{project_id}/servers/{server_id}/action`_ \
          -H 'Content-Type: application/json' \
          -H 'Accept: application/json' \
          -H 'X-Auth-Token: {token_id}' \
          -d '{
                 "os-start": null
             }'


返回参数

返回样例


::

    HTTP/1.1 202


.. _nova-shutdown-instance:

软关机(发送关机信号)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

+------------+-----------------------------------------------+----------------------+
|  HTTP方法  |  URI路径                                      |  描述                |
+============+===============================================+======================+
|  POST      |  /v2/{project_id}/servers/{server_id}/action  |  给主机发送关机信号  |
+------------+-----------------------------------------------+----------------------+

请求参数

请求样例

::

    
    curl  -s \
          -X POST `https://bj1.compute.api.ustack.com/v2/{project_id}/servers/{server_id}/action`_ \
          -H 'Content-Type: application/json' \
          -H 'Accept: application/json' \
          -H 'X-Auth-Token: {token_id}' \
          -d '{
                 "os-shutdown": null
             }'


返回参数

返回样例


::

    HTTP/1.1 202


.. _nova-stop-instance:

强制关机(断开电源)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

+------------+-----------------------------------------------+----------------------+
|  HTTP方法  |  URI路径                                      |  描述                |
+============+===============================================+======================+
|  POST      |  /v2/{project_id}/servers/{server_id}/action  |  强制关机(断开电源)  |
+------------+-----------------------------------------------+----------------------+

请求参数

请求样例

::

    
    curl  -s \
          -X POST `https://bj1.compute.api.ustack.com/v2/{project_id}/servers/{server_id}/action`_ \
          -H 'Content-Type: application/json' \
          -H 'Accept: application/json' \
          -H 'X-Auth-Token: {token_id}' \
          -d '{
                 "os-stop": null
             }'


返回参数

返回样例


::

    HTTP/1.1 202


.. _nova-change-instance-admin-password:

修改主机密码
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

+------------+-----------------------------------------------+----------------------+
|  HTTP方法  |  URI路径                                      |  描述                |
+============+===============================================+======================+
|  POST      |  /v2/{project_id}/servers/{server_id}/action  |  修改主机密码        |
+------------+-----------------------------------------------+----------------------+

请求参数

请求样例

::

    
    curl  -s \
          -X POST `https://bj1.compute.api.ustack.com/v2/{project_id}/servers/{server_id}/action`_ \
          -H 'Content-Type: application/json' \
          -H 'Accept: application/json' \
          -H 'X-Auth-Token: {token_id}' \
          -d '{
                 "changePassword": {
                     "adminPass": "newsecret"
                 }
             }'


返回参数

返回样例


::

    HTTP/1.1 202


.. _nova-snapshot-instance:

创建云主机快照
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

+------------+-----------------------------------------------+----------------------+
|  HTTP方法  |  URI路径                                      |  描述                |
+============+===============================================+======================+
|  POST      |  /v2/{project_id}/servers/{server_id}/action  |  创建云主机快照      |
+------------+-----------------------------------------------+----------------------+

请求参数

请求样例

::

    
    curl -s \
         -X POST `https://bj1.compute.api.ustack.com/v2/{project_id}/servers/{server_id}/action`_ \
         -H 'Content-Type: application/json' \
         -H 'Accept: application/json' \
         -H 'X-Auth-Token: {token_id}' \
         -d '{
                "createImage": {
                    "name": "foo-iamge",
                    "metadata": {
                        "myvar": "foobar"
                    }
                }
            }'


返回参数

返回样例


::

    HTTP/1.1 202




密钥 (Key Pairs)
--------------------------------------------

.. _nova-create-keypair:

创建密钥
~~~~~~~~~~~~~~~~~~~~~~~~~~~~
+------------+--------------------------------+----------------------+
|  HTTP方法  |  URI路径                       |  描述                |
+============+================================+======================+
|  POST      |  /v2/{project_id}/os-keypairs  |  创建密钥            |
+------------+--------------------------------+----------------------+

请求参数

+----------+----------+----------------------+
|  字段名  |  类型    |  描述                |
+==========+==========+======================+
|  name    |  string  |  密钥的名称          |
+----------+----------+----------------------+

请求样例

::

    
    curl -s \
         -X POST `https://bj1.compute.api.ustack.com/v2/{project_id}/os-keypairs`_ \
         -H 'Content-Type: application/json' \
         -H 'Accept: application/json' \
         -H 'X-Auth-Token: {token_id}' \
         -d '{
                "keypair": {
                    "name": "key2"
                }
            }'


返回参数

+---------------+----------+----------------------+
|  字段名       |  类型    |  描述                |
+===============+==========+======================+
|  user_id      |  uuid    |  创建密钥的用户的id  |
+---------------+----------+----------------------+
|  name         |  string  |  密钥的名称          |
+---------------+----------+----------------------+
|  public_key   |  string  |  密钥中的公钥的内容  |
+---------------+----------+----------------------+
|  private_key  |  string  |  密钥中的私钥的内容  |
+---------------+----------+----------------------+
|  fingerprint  |  string  |  密钥的指纹信息      |
+---------------+----------+----------------------+

返回样例

::

    
    HTTP/1.1 200
    
    "keypair": {
        "public_key": "ssh-rsa AAAAB3NzaC1yc2EAAAABIwAAAQEAuGenerated by Novan",
        "private_key": "-----BEGIN RSA PRIVATE KEY-----nMIIEogIBAAKCAQEAuRSA PRIVATE KEY-----n",
        "user_id": "d77df5d8b15349fcb460f1cec8814d47",
        "name": "key2",
        "fingerprint": "14:2a:b5:f5:9b:40:10:ef:d4:e6:e6:26:72:4e:fa:c3"
    }


.. _nova-import-keypair:

导入密钥
~~~~~~~~~~~~~~~~~~~~~~~~~~~~


+------------+--------------------------------+------------+
|  HTTP方法  |  URI路径                       |  描述      |
+============+================================+============+
|  POST      |  /v2/{project_id}/os-keypairs  |  导入密钥  |
+------------+--------------------------------+------------+

请求参数


+--------------+----------+----------------------------+
|  字段名      |  类型    |  描述                      |
+==============+==========+============================+
|  name        |  string  |  密钥的名称                |
+--------------+----------+----------------------------+
|  public_key  |  string  |  用于创建密钥的公钥的内容  |
+--------------+----------+----------------------------+

请求样例

::

    
    curl -s \
         -X POST `https://bj1.compute.api.ustack.com/v2/{project_id}/os-keypairs`_ \
         -H 'Content-Type: application/json' \
         -H 'Accept: application/json' \
         -H 'X-Auth-Token: {token_id}' \
         -d '{
                "keypair": {
                    "name": "key3",
                    "public_key": "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAAAgQDx8nkQv/zgGgB4rMYmIf+6A4l6Rr+o/6lHBQdWGenerated by Nova"
                }
            }'


返回参数

+---------------+----------+----------------------+
|  字段名       |  类型    |  描述                |
+===============+==========+======================+
|  user_id      |  uuid    |  创建密钥的用户的id  |
+---------------+----------+----------------------+
|  name         |  string  |  密钥的名称          |
+---------------+----------+----------------------+
|  public_key   |  string  |  密钥中的公钥的内容  |
+---------------+----------+----------------------+
|  private_key  |  string  |  密钥中的私钥的内容  |
+---------------+----------+----------------------+
|  fingerprint  |  string  |  密钥的指纹信息      |
+---------------+----------+----------------------+

返回样例

::

    
    HTTP/1.1 200
    
    "keypair": {
        "public_key": "ssh-rsa AAAAB3NzaC1yc2EAAAABIwAAAQEAuGenerated by Novan",
        "private_key": "-----BEGIN RSA PRIVATE KEY-----nMIIEogIBAAKCAQEAuRSA PRIVATE KEY-----n",
        "user_id": "d77df5d8b15349fcb460f1cec8814d47",
        "name": "key2",
        "fingerprint": "14:2a:b5:f5:9b:40:10:ef:d4:e6:e6:26:72:4e:fa:c3"
    }


.. _nova-list-keypairs:

列出所有密钥
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

+------------+--------------------------------+----------------+
|  HTTP方法  |  URI路径                       |  描述          |
+============+================================+================+
|  GET       |  /v2/{project_id}/os-keypairs  |  列出所有密钥  |
+------------+--------------------------------+----------------+

请求参数

请求样例

::

    
    curl -s \
         -X GET `https://bj1.compute.api.ustack.com/v2/{project_id}/os-keypairs`_ \
         -H 'Content-Type: application/json' \
         -H 'Accept: application/json' \
         -H 'X-Auth-Token: {token_id}'


返回参数

+---------------+----------+----------------------+
|  字段名       |  类型    |  描述                |
+===============+==========+======================+
|  name         |  string  |  密钥的名称          |
+---------------+----------+----------------------+
|  public_key   |  string  |  密钥中的公钥的内容  |
+---------------+----------+----------------------+
|  fingerprint  |  string  |  密钥的指纹信息      |
+---------------+----------+----------------------+

返回样例

::

    
    HTTP/1.1 200
    
    {
        "keypairs": [
            {
                "keypair": {
                    "public_key": "ssh-rsa AAAAB3NzaC1yc2EAAAABIwAAAQEAz6V2RZUYWIomYLTHQKDk2fJDnAPovZiWkiR+YWGenerated by Novan",
                    "name": "key1",
                    "fingerprint": "40:b8:1d:71:66:3a:28:7a:0e:c1:ec:a5:c3:2c:c8:df"
                }
            },
            {
                "keypair": {
                    "public_key": "ssh-rsa AAAAB3NzaC1yc2EAAAABIwAAAQEAuGenerated by Novan",
                    "name": "key2",
                    "fingerprint": "14:2a:b5:f5:9b:40:10:ef:d4:e6:e6:26:72:4e:fa:c3"
                }
            },
            {
                "keypair": {
                    "public_key": "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAAAgQDx8nkQv/zgGgB4rMYmIf+6A4l6Rr+o/6lHBQdWGenerated by Nova",
                    "name": "key3",
                    "fingerprint": "1e:2c:9b:56:79:4b:45:77:f9:ca:7a:98:2c:b0:d5:3c"
                }
            }
        ]
    }


.. _nova-show-keypair:

查看密钥详细信息
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

+------------+-------------------------------------------+--------------------+
|  HTTP方法  |  URI路径                                  |  描述              |
+============+===========================================+====================+
|  GET       |  /v2/{project_id}/os-keypairs/{key_name}  |  查看密钥详细信息  |
+------------+-------------------------------------------+--------------------+

请求参数

请求样例

::

    
    curl -s \
         -X GET `https://bj1.compute.api.ustack.com/v2/{project_id}/os-keypairs/{key_name}`_ \
         -H 'Content-Type: application/json' \
         -H 'Accept: application/json' \
         -H 'X-Auth-Token: {token_id}'


返回参数

+---------------+------------+------------------------+
|  字段名       |  类型      |  描述                  |
+===============+============+========================+
|  id           |  int       |  密钥的id              |
+---------------+------------+------------------------+
|  user_id      |  uuid      |  创建密钥的用户的id    |
+---------------+------------+------------------------+
|  name         |  string    |  密钥的名称            |
+---------------+------------+------------------------+
|  public_key   |  string    |  密钥中的公钥的内容    |
+---------------+------------+------------------------+
|  private_key  |  string    |  密钥中的私钥的内容    |
+---------------+------------+------------------------+
|  fingerprint  |  string    |  密钥的指纹信息        |
+---------------+------------+------------------------+
|  created_at   |  datetime  |  密钥的创建时间        |
+---------------+------------+------------------------+
|  deleted      |  bool      |  密钥是否被用户删除了  |
+---------------+------------+------------------------+

返回样例


::

    HTTP/1.1 200
    
    {
        "keypair": {
            "public_key": "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAAAgQDx8nkQv/zgGgB4rMYmIf+6A4l6Rr+o/6lHBQdWGenerated by Nova",
            "user_id": "d77df5d8b15349fcb460f1cec8814d47",
            "name": "key3",
            "deleted": false,
            "created_at": "2014-06-04T08:11:11.000000",
            "updated_at": null,
            "fingerprint": "1e:2c:9b:56:79:4b:45:77:f9:ca:7a:98:2c:b0:d5:3c",
            "deleted_at": null,
            "id": 1862
        }
    }


.. _nova-delete-keypair:

删除密钥
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

+------------+-------------------------------------------+------------+
|  HTTP方法  |  URI路径                                  |  描述      |
+============+===========================================+============+
|  DELETE    |  /v2/{project_id}/os-keypairs/{key_name}  |  删除密钥  |
+------------+-------------------------------------------+------------+

请求参数

请求样例

::

    
    curl -s \
         -X DELETE `https://bj1.compute.api.ustack.com/v2/{project_id}/os-keypairs/{key_name}`_ \
         -H 'Content-Type: application/json' \
         -H 'Accept: application/json' \
         -H 'X-Auth-Token: {token_id}'


返回参数

返回样例


::

    HTTP/1.1 200


.. _nova-attach-keypairs:

挂载密钥
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

+------------+-----------------------------------------------+------------+
|  HTTP方法  |  URI路径                                      |  描述      |
+============+===============================================+============+
|  POST      |  /v2/{project_id}/servers/{server_id}/action  |  挂载密钥  |
+------------+-----------------------------------------------+------------+

请求参数

+-------------+--------+----------------------+
|  字段名     |  类型  |  描述                |
+=============+========+======================+
|  key_names  |  list  |  要挂载的密钥的名称  |
+-------------+--------+----------------------+

请求样例

::

    
    curl -s \
         -X POST `https://bj1.compute.api.ustack.com/v2/{project_id}/servers/{server_id}/action`_ \
         -H 'Content-Type: application/json' \
         -H 'Accept: application/json' \
         -H 'X-Auth-Token: {token_id}' \
         -d '{
                "attachKeypairs": {
                    "key_names": ["key1", "key2"]
                }
            }'


返回参数

返回样例


::

    HTTP/1.1 202


.. _nova-detach-keypairs:

卸载密钥
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

+------------+-----------------------------------------------+------------+
|  HTTP方法  |  URI路径                                      |  描述      |
+============+===============================================+============+
|  POST      |  /v2/{project_id}/servers/{server_id}/action  |  卸载密钥  |
+------------+-----------------------------------------------+------------+

请求参数

+-------------+--------+----------------------+
|  字段名     |  类型  |  描述                |
+=============+========+======================+
|  key_names  |  list  |  要卸载的密钥的名称  |
+-------------+--------+----------------------+

请求样例

::

    
    curl -s \
         -X POST `https://bj1.compute.api.ustack.com/v2/{project_id}/servers/{server_id}/action`_ \
         -H 'Content-Type: application/json' \
         -H 'Accept: application/json' \
         -H 'X-Auth-Token: {token_id}' \
         -d '{
                "detachKeypairs": {
                    "key_names": [
                        "key1",
                        "key2"
                    ]
                }
            }'


返回参数

返回样例


::

    HTTP/1.1 202




云硬盘 (Volumes)
------------------------------------------

.. _nova-attach-volumes:

挂载云硬盘
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

+------------+--------------------------------------------------------------+--------------+
|  HTTP方法  |  URI路径                                                     |  描述        |
+============+==============================================================+==============+
|  POST      |  /v2/{project_id}/servers/{server_id}/os-volume_attachments  |  挂载云硬盘  |
+------------+--------------------------------------------------------------+--------------+

请求参数


+------------+--------+------------------------+
|  字段名    |  类型  |  描述                  |
+============+========+========================+
|  volumeId  |  uuid  |  要挂载的云硬盘的UUID  |
+------------+--------+------------------------+

请求样例

::

    
    curl -s \
         -X POST `https://bj1.compute.api.ustack.com/v2/{project_id}/servers/{server_id}/os-volume_attachments`_ \
         -H 'Content-Type: application/json' \
         -H 'Accept: application/json' \
         -H 'X-Auth-Token: {token_id}' \
         -d '{
                "volumeAttachment": {
                    "volumeId": "a26887c6-c47b-4654-abb5-dfadf7d3f803"
                }
            }'


返回参数

+------------+----------+----------------------------+
|  字段名    |  类型    |  描述                      |
+============+==========+============================+
|  id        |  uuid    |  云硬盘挂载信息的UUID      |
+------------+----------+----------------------------+
|  volumeId  |  uuid    |  要挂载的云硬盘的UUID      |
+------------+----------+----------------------------+
|  serverId  |  uuid    |  挂载云硬盘的主机的UUID    |
+------------+----------+----------------------------+
|  device    |  string  |  云硬盘挂载到主机设备路径  |
+------------+----------+----------------------------+

返回样例


::

    HTTP/1.1 202
    
    {
        "volumeAttachment": {
            "device": "/dev/vdd",
            "id": "a26887c6-c47b-4654-abb5-dfadf7d3f803",
            "serverId": "0c92f3f6-c253-4c9b-bd43-e880a8d2eb0a",
            "volumeId": "a26887c6-c47b-4654-abb5-dfadf7d3f803"
        }
    }


.. _nova-detach-volumes:

卸载云硬盘
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

+------------+--------------------------------------------------------------------------+--------------+
|  HTTP方法  |  URI路径                                                                 |  描述        |
+============+==========================================================================+==============+
|  DELETE    |  /v2/{project_id}/servers/{server_id}/os-volume_attachments/{volume_id}  |  卸载云硬盘  |
+------------+--------------------------------------------------------------------------+--------------+

请求参数

请求样例

::

    
    curl -s \
         -X DELETE `https://bj1.compute.api.ustack.com/v2/{project_id}/servers/{server_id}/os-volume_attachments/{volume_id}`_ \
         -H 'Content-Type: application/json' \
         -H 'Accept: application/json' \
         -H 'X-Auth-Token: {token_id}'


返回参数

返回样例


::

    HTTP/1.1 202




配置 (Flavors)
----------------------------------------

.. _nova-list-flavors:

列出所有配置基本信息
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

+------------+----------------------------+------------------------+
|  HTTP方法  |  URI路径                   |  描述                  |
+============+============================+========================+
|  GET       |  /v2/{project_id}/flavors  |  列出所有配置基本信息  |
+------------+----------------------------+------------------------+

请求参数

请求样例

::

    
    curl -s \
         -X GET `https://bj1.compute.api.ustack.com/v2/{project_id}/flavors`_ \
         -H 'Content-Type: application/json' \
         -H 'Accept: application/json' \
         -H 'X-Auth-Token: {token_id}'


返回参数

+----------+----------+----------------------------------------------------+
|  字段名  |  类型    |  描述                                              |
+==========+==========+====================================================+
|  id      |  uuid    |  配置信息的唯一标识                                |
+----------+----------+----------------------------------------------------+
|  links   |  dict    |  配置信息的链接, 通过这些链接可以获取更详细的信息  |
+----------+----------+----------------------------------------------------+
|  name    |  string  |  配置信息的名称                                    |
+----------+----------+----------------------------------------------------+

返回样例

::

    
    HTTP/1.1 200
    
    {
        "flavors": [
            {
                "id": "215ea357-2d56-4387-9991-0c083806e3f8",
                "links": [
                    {
                        "href": "`https://bj1.compute.api.ustack.com/v2/0f1255df40374d02a23e1a6ceeaefec7/flavors/215ea357-2d56-4387-9991-0c083806e3f8`_",
                        "rel": "self"
                    },
                    {
                        "href": "`https://bj1.compute.api.ustack.com/0f1255df40374d02a23e1a6ceeaefec7/flavors/215ea357-2d56-4387-9991-0c083806e3f8`_",
                        "rel": "bookmark"
                    }
                ],
                "name": "micro-1"
            },
            {
                "id": "3332c026-533a-43d0-b415-abd3fdab09bf",
                "links": [
                    {
                        "href": "`https://bj1.compute.api.ustack.com/v2/0f1255df40374d02a23e1a6ceeaefec7/flavors/3332c026-533a-43d0-b415-abd3fdab09bf`_",
                        "rel": "self"
                    },
                    {
                        "href": "`https://bj1.compute.api.ustack.com/0f1255df40374d02a23e1a6ceeaefec7/flavors/3332c026-533a-43d0-b415-abd3fdab09bf`_",
                        "rel": "bookmark"
                    }
                ],
                "name": "micro-2"
            },
            {
                "id": "7f05780f-caf6-43bd-af55-b183cec6a758",
                "links": [
                    {
                        "href": "`https://bj1.compute.api.ustack.com/v2/0f1255df40374d02a23e1a6ceeaefec7/flavors/7f05780f-caf6-43bd-af55-b183cec6a758`_",
                        "rel": "self"
                    },
                    {
                        "href": "`https://bj1.compute.api.ustack.com/0f1255df40374d02a23e1a6ceeaefec7/flavors/7f05780f-caf6-43bd-af55-b183cec6a758`_",
                        "rel": "bookmark"
                    }
                ],
                "name": "standard-1"
            }
        ]
    }


.. _nova-list-flavors-in-detail:

列出所有配置详细信息
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

+------------+-----------------------------------+------------------------+
|  HTTP方法  |  URI路径                          |  描述                  |
+============+===================================+========================+
|  GET       |  /v2/{project_id}/flavors/detail  |  列出所有配置详细信息  |
+------------+-----------------------------------+------------------------+

请求参数

请求样例

::

    
    curl -s \
         -X GET `https://bj1.compute.api.ustack.com/v2/{project_id}/flavors/detail`_ \
         -H 'Content-Type: application/json' \
         -H 'Accept: application/json' \
         -H 'X-Auth-Token: {token_id}'


返回参数

返回样例

::

    
    HTTP/1.1 200
    
    {
        "flavors": [
            {
                "name": "micro-1",
                "links": [
                    {
                        "href": "`https://bj1.compute.api.ustack.com/v2/0f1255df40374d02a23e1a6ceeaefec7/flavors/215ea357-2d56-4387-9991-0c083806e3f8`_",
                        "rel": "self"
                    },
                    {
                        "href": "`https://bj1.compute.api.ustack.com/0f1255df40374d02a23e1a6ceeaefec7/flavors/215ea357-2d56-4387-9991-0c083806e3f8`_",
                        "rel": "bookmark"
                    }
                ],
                "ram": 12288,
                "OS-FLV-DISABLED:disabled": false,
                "vcpus": 12,
                "swap": "",
                "os-flavor-access:is_public": true,
                "rxtx_factor": 1,
                "OS-FLV-EXT-DATA:ephemeral": 0,
                "disk": 20,
                "id": "215ea357-2d56-4387-9991-0c083806e3f8"
            },
            {
                "name": "micro-2",
                "links": [
                    {
                        "href": "`https://bj1.compute.api.ustack.com/v2/0f1255df40374d02a23e1a6ceeaefec7/flavors/21c0cf18-d0dc-43ab-8fdb-40ba8b0935d9`_",
                        "rel": "self"
                    },
                    {
                        "href": "`https://bj1.compute.api.ustack.com/0f1255df40374d02a23e1a6ceeaefec7/flavors/21c0cf18-d0dc-43ab-8fdb-40ba8b0935d9`_",
                        "rel": "bookmark"
                    }
                ],
                "ram": 8192,
                "OS-FLV-DISABLED:disabled": false,
                "vcpus": 2,
                "swap": "",
                "os-flavor-access:is_public": true,
                "rxtx_factor": 1,
                "OS-FLV-EXT-DATA:ephemeral": 0,
                "disk": 20,
                "id": "21c0cf18-d0dc-43ab-8fdb-40ba8b0935d9"
            },
            {
                "name": "standard-1",
                "links": [
                    {
                        "href": "`https://bj1.compute.api.ustack.com/v2/0f1255df40374d02a23e1a6ceeaefec7/flavors/e15253c2-c340-4402-89ae-cfd794774560`_",
                        "rel": "self"
                    },
                    {
                        "href": "`https://bj1.compute.api.ustack.com/0f1255df40374d02a23e1a6ceeaefec7/flavors/e15253c2-c340-4402-89ae-cfd794774560`_",
                        "rel": "bookmark"
                    }
                ],
                "ram": 16384,
                "OS-FLV-DISABLED:disabled": false,
                "vcpus": 8,
                "swap": "",
                "os-flavor-access:is_public": true,
                "rxtx_factor": 1,
                "OS-FLV-EXT-DATA:ephemeral": 0,
                "disk": 20,
                "id": "e15253c2-c340-4402-89ae-cfd794774560"
            }
        ]
    }


.. _nova-show-flavor:

列出指定配置信息
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

+------------+----------------------------------------+--------------------+
|  HTTP方法  |  URI路径                               |  描述              |
+============+========================================+====================+
|  GET       |  /v2/{project_id}/flavors/{flavor_id}  |  列出指定配置信息  |
+------------+----------------------------------------+--------------------+

请求参数

请求样例

::

    
    curl -s \
         -X GET `https://bj1.compute.api.ustack.com/v2/{project_id}/flavors/{flavor_id}`_ \
         -H 'Content-Type: application/json' \
         -H 'Accept: application/json' \
         -H 'X-Auth-Token: {token_id}'


返回参数

+------------------------------+----------+------------------------------------------------------------+
|  字段名                      |  类型    |  描述                                                      |
+==============================+==========+============================================================+
|  id                          |  uuid    |  配置信息的唯一标识                                        |
+------------------------------+----------+------------------------------------------------------------+
|  links                       |  dict    |  配置信息的链接, 通过这些链接可以获取更详细的信息          |
+------------------------------+----------+------------------------------------------------------------+
|  name                        |  string  |  配置信息的名称                                            |
+------------------------------+----------+------------------------------------------------------------+
|  ram                         |  int     |  内存的大小, 以MB为单位                                    |
+------------------------------+----------+------------------------------------------------------------+
|  vcpus                       |  int     |  有多少个云主机的CPU                                       |
+------------------------------+----------+------------------------------------------------------------+
|  disk                        |  int     |  根分区的大小, 以 GB 为单位                                |
+------------------------------+----------+------------------------------------------------------------+
|  swap                        |  int     |  交换分区的大小, 以 GB 为单位                              |
+------------------------------+----------+------------------------------------------------------------+
|  os-flavor-access:is_public  |  bool    |  本配置信息是否公开的, 如果是, 则所有的人都可以看见和使用  |
+------------------------------+----------+------------------------------------------------------------+

返回样例

::

    
    HTTP/1.1 200
    
    {
        "flavor": {
            "name": "compute-12",
            "links": [
                {
                    "href": "`https://bj1.compute.api.ustack.com/v2/0f1255df40374d02a23e1a6ceeaefec7/flavors/215ea357-2d56-4387-9991-0c083806e3f8`_",
                    "rel": "self"
                },
                {
                    "href": "`https://bj1.compute.api.ustack.com/0f1255df40374d02a23e1a6ceeaefec7/flavors/215ea357-2d56-4387-9991-0c083806e3f8`_",
                    "rel": "bookmark"
                }
            ],
            "ram": 12288,
            "OS-FLV-DISABLED:disabled": false,
            "vcpus": 12,
            "swap": "",
            "os-flavor-access:is_public": true,
            "rxtx_factor": 1,
            "OS-FLV-EXT-DATA:ephemeral": 0,
            "disk": 20,
            "id": "215ea357-2d56-4387-9991-0c083806e3f8"
        }
    }




网络 (Networks)
------------------------------------------

.. _nova-attach-interface:

绑定虚拟网卡
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

+------------+-----------------------------------------------------+----------------+
|  HTTP方法  |  URI路径                                            |  描述          |
+============+=====================================================+================+
|  POST      |  /v2/{project_id}/servers/{server_id}/os-interface  |  绑定虚拟网卡  |
+------------+-----------------------------------------------------+----------------+

请求参数

+-----------+--------+------------------------------+
|  字段名   |  类型  |  描述                        |
+===========+========+==============================+
|  port_id  |  uuid  |  指定云主机要绑定的虚拟网卡  |
+-----------+--------+------------------------------+

请求样例

::

    
    curl -s \
         -X POST `https://bj1.compute.api.ustack.com/v2/{project_id}/servers/{server_id}/os-interface`_ \
         -H 'Content-Type: application/json' \
         -H 'Accept: application/json' \
         -H 'X-Auth-Token: {token_id}' \
         -d '{
                "interfaceAttachment": {
                    "port_id": "{port_id}"
                }
            }'


返回参数

返回样例


::

    HTTP/1.1 200


.. _nova-detach-interface:

卸载虚拟网卡
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

+------------+---------------------------------------------------------------+----------------+
|  HTTP方法  |  URI路径                                                      |  描述          |
+============+===============================================================+================+
|  DELETE    |  /v2/{project_id}/servers/{server_id}/os-interface/{port_id}  |  卸载虚拟网卡  |
+------------+---------------------------------------------------------------+----------------+

请求参数

请求样例

::

    
    curl -s \
         -X DELETE `https://bj1.compute.api.ustack.com/v2/{project_id}/servers/{server_id}/os-interface/{port_id}`_ \
         -H 'Content-Type: application/json' \
         -H 'Accept: application/json' \
         -H 'X-Auth-Token: {token_id}'


返回参数

返回样例


::

    HTTP/1.1 202


.. _nova-attach-network:

加入网络
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

+------------+-----------------------------------------------------+------------+
|  HTTP方法  |  URI路径                                            |  描述      |
+============+=====================================================+============+
|  POST      |  /v2/{project_id}/servers/{server_id}/os-interface  |  加入网络  |
+------------+-----------------------------------------------------+------------+

请求参数

+-------------+--------+-----------------------------------------------------------+
|  字段名     |  类型  |  描述                                                     |
+=============+========+===========================================================+
|  sbunet_id  |  uuid  |  指定要加入到那个子网 net_id uuid 指定云主机要加入的网络  |
+-------------+--------+-----------------------------------------------------------+

请求样例

::

    
    curl -s \
         -X POST `https://bj1.compute.api.ustack.com/v2/{project_id}/servers/{server_id}/os-interface`_ \
         -H 'Content-Type: application/json' \
         -H 'Accept: application/json' \
         -H 'X-Auth-Token: {token_id}' \
         -d '{
                "interfaceAttachment": {
                    "fixed_ips": [
                        ｛
                            "subnet_id": "{subnet_id}"
                         }
                    ]
                    "net_id": "{net_id}"
                }
            }'


返回参数

返回样例


::

    HTTP/1.1 200




VNC终端 (VNC Console)
------------------------------------------------------

.. _nova-vnc-address:

获取VNC终端地址
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

+------------+-----------------------------------------------+-------------------+
|  HTTP方法  |  URI路径                                      |  描述             |
+============+===============================================+===================+
|  POST      |  /v2/{project_id}/servers/{server_id}/action  |  获取VNC终端地址  |
+------------+-----------------------------------------------+-------------------+

请求参数

+----------+----------+-----------------+
|  字段名  |  类型    |  描述           |
+==========+==========+=================+
|  type    |  string  |  VNC终端的类型  |
+----------+----------+-----------------+

请求样例

::

    
    curl -s \
         -X POST `https://bj1.compute.api.ustack.com/v2/{project_id}/servers/{server_id}/action`_ \
         -H 'Content-Type: application/json' \
         -H 'Accept: application/json' \
         -H 'X-Auth-Token: {token_id}' \
         -d '{
                "os-getVNCConsole": {
                    "type": "novnc"
                }
            }'


返回参数

+----------+----------+-----------------+
|  字段名  |  类型    |  描述           |
+==========+==========+=================+
|  type    |  string  |  VNC终端的类型  |
+----------+----------+-----------------+
|  url     |  string  |  VNC终端的链接  |
+----------+----------+-----------------+

返回样例

::

    
    HTTP/1.1 202
    
    {
        "console": {
            "type": "novnc",
            "url": "`https://bj1.compute.api.ustack.com/vnc/vnc_auto.html?token=36f6426d-1366-4734-af15-c81560becd77`_"
        }
    }


