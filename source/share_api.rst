


文件服务
======================



API规范
----------------------------

文件服务API入口与API列表如下:


+ API入口:

区域 API入口 北京1区(bj1) `https://bj1.share.api.ustack.com`_ 广东1区(gd1)
`https://gd1.share.api.ustack.com`_
Note

广东节点暂未上线


+ API列表:

资源 操作 HTTP方法 URI路径 *文件共享 (Share)* 查看所有文件共享 GET /v1/{tenant_id}/shares
查看所有文件共享详情 GET /v1/{tenant_id}/shares/detail 查看文件共享 GET
/v1/{tenant_id}/shares/{share_id} 创建文件共享 POST /v1/{tenant_id}/shares
修改文件共享 PUT /v1/{tenant_id}/shares/{share_id} 删除文件共享 DELETE
/v1/{tenant_id}/shares/{share_id} *访问规则 (Rule)* 查看访问规则 POST
/v1/{tenant_id}/shares/{share_id}/action 增加访问规则 POST
/v1/{tenant_id}/shares/{share_id}/action 删除访问规则 POST
/v1/{tenant_id}/shares/{share_id}/action *共享网络 (ShareNetwork)*
查看所有共享网络 GET /v1/{tenant_id}/share-networks 查看所有共享网络详情 GET
/v1/{tenant_id}/share-networks/detail 查看共享网络 GET /v1/{tenant_id
}/share-networks/{share_network_id} 创建共享网络 POST /v1/{tenant_id}/share-
networks 修改共享网络 PUT /v1/{tenant_id}/share-networks/{share_network_id}
删除共享网络 DELETE /v1/{tenant_id}/share-networks/{share_network_id} *配额
(Quota)* 查看配额 GET /v1/{tenant_id}/os-quota-sets/{tenant_id} 查看默认配额 GET
/v1/{tenant_id}/os-quota-sets/{tenant_id}/defaults 修改配额 PUT
/v1/{tenant_id}/os-quota-sets/{tenant_id} 删除配额 DELETE /v1/{tenant_id
}/os-quota-sets/{tenant_id}


文件共享 (Share)
------------------------------------------



查看所有文件共享
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 GET /v1/{tenant_id}/shares 查看所有文件共享
请求样例

::

    
    curl -s \
         -X GET `https://bj1.share.api.ustack.com//v1/{tenant_id}/shares`_ \
         -H "Accept: application/json" \
         -H "X-Auth-Token: {token_id}"


返回样例 :


::

    {
        "shares": [
            {
                "id": "708f359f-72dd-4473-8982-a50710d10ffa",
                "links": [
                    {
                        "href": "http://10.250.10.250:8786/v1/75076824281346f6b61942638a45e856/shares/708f359f-72dd-4473-8982-a50710d10ffa",
                        "rel": "self"
                    },
                    {
                        "href": "http://10.250.10.250:8786/75076824281346f6b61942638a45e856/shares/708f359f-72dd-4473-8982-a50710d10ffa",
                        "rel": "bookmark"
                    }
                ],
                "name": "222"
            },
            {
                "id": "c030cb55-f3cf-4136-881c-cab87eda0fa1",
                "links": [
                    {
                        "href": "http://10.250.10.250:8786/v1/75076824281346f6b61942638a45e856/shares/c030cb55-f3cf-4136-881c-cab87eda0fa1",
                        "rel": "self"
                    },
                    {
                        "href": "http://10.250.10.250:8786/75076824281346f6b61942638a45e856/shares/c030cb55-f3cf-4136-881c-cab87eda0fa1",
                        "rel": "bookmark"
                    }
                ],
                "name": "111"
            }
        ]
    }




查看所有文件共享详情
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 GET /v1/{tenant_id}/shares/detail 查看所有文件共享详情
请求样例

::

    
    curl -s \
         -X GET `https://bj1.share.api.ustack.com//v1/{tenant_id}/shares/detail`_ \
         -H "Accept: application/json" \
         -H "X-Auth-Token: {token_id}"


返回样例 :


::

    {
        "shares": [
            {
                "availability_zone": "nova",
                "created_at": "2014-11-26T06:40:08.000000",
                "description": "222",
                "export_location": "10.254.0.18:/shares/share-708f359f-72dd-4473-8982-a50710d10ffa",
                "host": "devstack-manila@backend1",
                "id": "708f359f-72dd-4473-8982-a50710d10ffa",
                "links": [
                    {
                        "href": "http://10.250.10.250:8786/v1/75076824281346f6b61942638a45e856/shares/708f359f-72dd-4473-8982-a50710d10ffa",
                        "rel": "self"
                    },
                    {
                        "href": "http://10.250.10.250:8786/75076824281346f6b61942638a45e856/shares/708f359f-72dd-4473-8982-a50710d10ffa",
                        "rel": "bookmark"
                    }
                ],
                "metadata": {},
                "name": "222",
                "project_id": "75076824281346f6b61942638a45e856",
                "share_network_id": "31633d57-3255-436f-9883-6241fcf5343e",
                "share_proto": "NFS",
                "size": 4,
                "snapshot_id": null,
                "status": "available",
                "volume_type": null
            },
            {
                "availability_zone": "nova",
                "created_at": "2014-11-24T11:10:43.000000",
                "description": "111",
                "export_location": "10.254.0.3:/shares/share-c030cb55-f3cf-4136-881c-cab87eda0fa1",
                "host": "devstack-manila@backend1",
                "id": "c030cb55-f3cf-4136-881c-cab87eda0fa1",
                "links": [
                    {
                        "href": "http://10.250.10.250:8786/v1/75076824281346f6b61942638a45e856/shares/c030cb55-f3cf-4136-881c-cab87eda0fa1",
                        "rel": "self"
                    },
                    {
                        "href": "http://10.250.10.250:8786/75076824281346f6b61942638a45e856/shares/c030cb55-f3cf-4136-881c-cab87eda0fa1",
                        "rel": "bookmark"
                    }
                ],
                "metadata": {},
                "name": "111",
                "project_id": "75076824281346f6b61942638a45e856",
                "share_network_id": "9c774780-ff5e-43a8-ad6e-00743637e128",
                "share_proto": "NFS",
                "size": 1,
                "snapshot_id": null,
                "status": "available",
                "volume_type": null
            }
        ]
    }




查看指定文件共享
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 GET /v1/{tenant_id}/shares/{share_id} 查看文件共享
请求样例

::

    
    curl -s \
         -X GET `https://bj1.share.api.ustack.com//v1/{tenant_id}/shares/{share_id}`_ \
         -H "Accept: application/json" \
         -H "X-Auth-Token: {token_id}"


返回样例 :


::

    {
        "share": {
            "availability_zone": "nova",
            "created_at": "2014-11-24T11:10:43.000000",
            "description": "111",
            "export_location": "10.254.0.3:/shares/share-c030cb55-f3cf-4136-881c-cab87eda0fa1",
            "host": "devstack-manila@backend1",
            "id": "c030cb55-f3cf-4136-881c-cab87eda0fa1",
            "links": [
                {
                    "href": "http://10.250.10.250:8786/v1/75076824281346f6b61942638a45e856/shares/c030cb55-f3cf-4136-881c-cab87eda0fa1",
                    "rel": "self"
                },
                {
                    "href": "http://10.250.10.250:8786/75076824281346f6b61942638a45e856/shares/c030cb55-f3cf-4136-881c-cab87eda0fa1",
                    "rel": "bookmark"
                }
            ],
            "metadata": {},
            "name": "111",
            "project_id": "75076824281346f6b61942638a45e856",
            "share_network_id": "9c774780-ff5e-43a8-ad6e-00743637e128",
            "share_proto": "NFS",
            "size": 1,
            "snapshot_id": null,
            "status": "available",
            "volume_type": null
        }
    }




创建文件共享
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 POST /v1/{tenant_id}/shares 创建文件共享
请求样例

::

    
    curl -s \
         -X POST `https://bj1.share.api.ustack.com//v1/{tenant_id}/shares`_ \
         -H "Content-Type: application/json" \
         -H "X-Auth-Token: {token_id}" \
         -d '{
                "share": {
                    "volume_type": null,
                    "name": "test2",
                    "snapshot_id": null,
                    "description": "test description",
                    "share_proto": "nfs",
                    "share_network_id": "9c774780-ff5e-43a8-ad6e-00743637e128",
                    "size": 1
                }
            }'


返回样例 :


::

    {
        "share": {
            "availability_zone": "nova",
            "created_at": "2014-11-27T08:44:14.097426",
            "description": "test description",
            "export_location": null,
            "host": null,
            "id": "64bc9056-8845-4316-92d4-84f2d88cea9d",
            "links": [
                {
                    "href": "http://10.250.10.250:8786/v1/75076824281346f6b61942638a45e856/shares/64bc9056-8845-4316-92d4-84f2d88cea9d",
                    "rel": "self"
                },
                {
                    "href": "http://10.250.10.250:8786/75076824281346f6b61942638a45e856/shares/64bc9056-8845-4316-92d4-84f2d88cea9d",
                    "rel": "bookmark"
                }
            ],
            "metadata": {},
            "name": "test2",
            "project_id": "75076824281346f6b61942638a45e856",
            "share_network_id": "9c774780-ff5e-43a8-ad6e-00743637e128",
            "share_proto": "NFS",
            "size": 1,
            "snapshot_id": null,
            "status": "creating",
            "volume_type": null
        }
    }




修改文件共享
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 PUT /v1/{tenant_id}/shares/{share_id} 修改文件共享
请求样例

::

    
    curl -s \
         -X PUT `https://bj1.share.api.ustack.com//v1/{tenant_id}/shares/{share_id}`_ \
         -H "Content-Type: application/json" \
         -H "X-Auth-Token: {token_id}" \
         -d '{
                "share": {
                    "display_description": "New description",
                    "display_name": "newname"
                }
            }'


返回样例 :


::

    {
        "share": {
            "availability_zone": "nova",
            "created_at": "2014-11-24T11:10:43.000000",
            "description": "New description",
            "export_location": "10.254.0.3:/shares/share-c030cb55-f3cf-4136-881c-cab87eda0fa1",
            "host": "devstack-manila@backend1",
            "id": "c030cb55-f3cf-4136-881c-cab87eda0fa1",
            "links": [
                {
                    "href": "http://10.250.10.250:8786/v1/75076824281346f6b61942638a45e856/shares/c030cb55-f3cf-4136-881c-cab87eda0fa1",
                    "rel": "self"
                },
                {
                    "href": "http://10.250.10.250:8786/75076824281346f6b61942638a45e856/shares/c030cb55-f3cf-4136-881c-cab87eda0fa1",
                    "rel": "bookmark"
                }
            ],
            "metadata": {},
            "name": "newname",
            "project_id": "75076824281346f6b61942638a45e856",
            "share_network_id": "9c774780-ff5e-43a8-ad6e-00743637e128",
            "share_proto": "NFS",
            "size": 1,
            "snapshot_id": null,
            "status": "available",
            "volume_type": null
        }
    }




删除文件共享
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 DELETE /v1/{tenant_id}/shares/{share_id} 删除文件共享
请求样例

::

    
    curl -s \
         -X DELETE `https://bj1.share.api.ustack.com//v1/{tenant_id}/shares/{share_id}`_ \
         -H "Content-Type: application/json" \
         -H "X-Auth-Token: {token_id}"


返回样例 :


::

    HTTP/1.1 204 No Content




访问规则 (Rule)
----------------------------------------



查看访问规则
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 POST /v1/{tenant_id}/shares/{share_id}/action 查看访问规则
请求样例

::

    
    curl -s \
         -X POST `https://bj1.share.api.ustack.com//v1/{tenant_id}/shares/{share_id}/action`_ \
         -H "Content-Type: application/json" \
         -H "X-Auth-Token: {token_id}" \
         -d '{
                "os-access_list": null
            }'


返回样例 :


::

    {
        "access_list": [
            {
                "access_to": "10.0.0.4",
                "access_type": "ip",
                "id": "5894a742-7d6f-4794-9b05-392f2fba18dd",
                "state": "active"
            },
            {
                "access_to": "10.0.0.5",
                "access_type": "ip",
                "id": "cbf3dc9b-59f9-4a2d-b2f5-4b161709c351",
                "state": "active"
            }
        ]
    }




增加访问规则
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 POST /v1/{tenant_id}/shares/{share_id}/action 增加访问规则
请求样例

::

    
    curl -s \
         -X POST `https://bj1.share.api.ustack.com//v1/{tenant_id}/shares/{share_id}/action`_ \
         -H "Content-Type: application/json" \
         -H "X-Auth-Token: {token_id}" \
         -d '{
                "os-allow_access": {
                    "access_to": "1.1.1.1",
                    "access_type": "ip"
                }
            }'


返回样例 :


::

    {
        "access": {
            "access_to": "1.1.1.1",
            "access_type": "ip",
            "created_at": "2014-11-27T09:21:47.833205",
            "deleted": "False",
            "deleted_at": null,
            "id": "09f256e4-0be1-48df-b780-0e006732d462",
            "share_id": "708f359f-72dd-4473-8982-a50710d10ffa",
            "state": "new",
            "updated_at": null
        }
    }




删除访问规则
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 POST /v1/{tenant_id}/shares/{share_id}/action 删除访问规则
请求样例

::

    
    curl -s \
         -X POST `https://bj1.share.api.ustack.com//v1/{tenant_id}/shares/{share_id}/action`_ \
         -H "Content-Type: application/json" \
         -H "X-Auth-Token: {token_id}" \
         -d '{
                "os-deny_access": {
                    "access_id": "42c2ecae-f0cb-4244-98fa-526dc8f9bd26"
                }
            }'


返回样例 :


::

    HTTP/1.1 204 No Content




共享网络 (ShareNetwork)
--------------------------------------------------------



查看所有共享网络
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 GET /v1/{tenant_id}/share-networks 查看所有共享网络
请求样例

::

    
    curl -s \
         -X GET `https://bj1.share.api.ustack.com//v1/{tenant_id}/share-networks`_ \
         -H "Content-Type: application/json" \
         -H "X-Auth-Token: {token_id}"


返回样例 :


::

    {
        "share_networks": [
            {
                "id": "30ad148a-2d21-4a85-a7bd-6f3ad37f5cd7",
                "name": null
            },
            {
                "id": "31633d57-3255-436f-9883-6241fcf5343e",
                "name": "share2"
            },
            {
                "id": "441408f9-46b3-4633-8bdb-4865af0fbd6c",
                "name": null
            },
            {
                "id": "9c774780-ff5e-43a8-ad6e-00743637e128",
                "name": "share1"
            },
            {
                "id": "9cd78551-78ee-4042-9f25-1ab10d94f76f",
                "name": null
            },
            {
                "id": "ed5c4a7d-00e5-415b-a47c-aca28a1c7b4f",
                "name": null
            }
        ]
    }




查看所有共享网络详情
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 GET /v1/{tenant_id}/share-networks/detail 查看所有共享网络详情
请求样例

::

    
    curl -s \
         -X GET `https://bj1.share.api.ustack.com//v1/{tenant_id}/share-networks/detail`_ \
         -H "Content-Type: application/json" \
         -H "X-Auth-Token: {token_id}"


返回样例 :


::

    {
        "share_networks": [
            {
                "cidr": null,
                "created_at": "2014-11-26T06:39:00.000000",
                "description": "2",
                "id": "31633d57-3255-436f-9883-6241fcf5343e",
                "ip_version": null,
                "name": "share2",
                "network_type": null,
                "neutron_net_id": "ea7d14e8-c8cb-46f9-8221-48a10a839fa4",
                "neutron_subnet_id": "bdcd14d4-5af3-4f93-bb97-91adb574887f",
                "project_id": "75076824281346f6b61942638a45e856",
                "segmentation_id": null,
                "updated_at": null
            },
            {
                "cidr": null,
                "created_at": "2014-11-24T11:10:27.000000",
                "description": "```",
                "id": "9c774780-ff5e-43a8-ad6e-00743637e128",
                "ip_version": null,
                "name": "share1",
                "network_type": null,
                "neutron_net_id": "0e23db6e-a959-44b5-9717-d2e76e871f9b",
                "neutron_subnet_id": "d2ed3e6c-0017-49f3-ad8d-a8f6a8289e6d",
                "project_id": "75076824281346f6b61942638a45e856",
                "segmentation_id": null,
                "updated_at": null
            }
        ]
    }




查看指定共享网络
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 GET /v1/{tenant_id}/share-networks/{share_network_id}
查看指定共享网络
请求样例

::

    
    curl -s \
         -X GET `https://bj1.share.api.ustack.com//v1/{tenant_id}/share-networks/{share_network_id}`_ \
         -H "Content-Type: application/json" \
         -H "X-Auth-Token: {token_id}"


返回样例 :


::

    {
        "share_network": {
            "cidr": null,
            "created_at": "2014-11-27T09:47:42.000000",
            "description": "test_description1111",
            "id": "1e16fb3d-59f6-495e-a677-0b23d4043a4d",
            "ip_version": null,
            "name": "test_name1111",
            "network_type": null,
            "neutron_net_id": "0e23db6e-a959-44b5-9717-d2e76e871f9b",
            "neutron_subnet_id": "d2ed3e6c-0017-49f3-ad8d-a8f6a8289e6d",
            "project_id": "75076824281346f6b61942638a45e856",
            "segmentation_id": null,
            "updated_at": null
        }
    }




创建共享网络
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 POST /v1/{tenant_id}/share-networks 创建共享网络
请求样例

::

    
    curl -s \
         -X POST `https://bj1.share.api.ustack.com//v1/{tenant_id}/share-networks`_ \
         -H "Accept: application/json" \
         -H "Content-Type: application/json" \
         -H "X-Auth-Token: {token_id}" \
         -d '{
                "share_network": {
                    "name": "test_name1111",
                    "description": "test_description1111",
                    "neutron_net_id": "0e23db6e-a959-44b5-9717-d2e76e871f9b",
                    "neutron_subnet_id": "d2ed3e6c-0017-49f3-ad8d-a8f6a8289e6d"
                }
            }'


返回样例 :


::

    {
        "share_network": {
            "cidr": null,
            "created_at": "2014-11-27T09:47:42.963874",
            "description": "test_description1111",
            "id": "1e16fb3d-59f6-495e-a677-0b23d4043a4d",
            "ip_version": null,
            "name": "test_name1111",
            "network_type": null,
            "neutron_net_id": "0e23db6e-a959-44b5-9717-d2e76e871f9b",
            "neutron_subnet_id": "d2ed3e6c-0017-49f3-ad8d-a8f6a8289e6d",
            "project_id": "75076824281346f6b61942638a45e856",
            "segmentation_id": null,
            "updated_at": null
        }
    }




修改共享网络
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 PUT /v1/{tenant_id}/share-networks/{share_network_id}
修改共享网络
请求样例

::

    
    curl -s \
         -X PUT `https://bj1.share.api.ustack.com//v1/{tenant_id}/share-networks/{share_network_id}`_ \
         -H "Content-Type: application/json" \
         -H "X-Auth-Token: {token_id}" \
         -d '{
                "share_network": {
                    "description": "test2222",
                    "name": "test2222"
                }
            }'


返回样例 :


::

    {
        "share_network": {
            "cidr": null,
            "created_at": "2014-11-27T09:47:42.000000",
            "description": "test2222",
            "id": "1e16fb3d-59f6-495e-a677-0b23d4043a4d",
            "ip_version": null,
            "name": "test2222",
            "network_type": null,
            "neutron_net_id": "0e23db6e-a959-44b5-9717-d2e76e871f9b",
            "neutron_subnet_id": "d2ed3e6c-0017-49f3-ad8d-a8f6a8289e6d",
            "project_id": "75076824281346f6b61942638a45e856",
            "segmentation_id": null,
            "updated_at": "2014-11-27T09:52:32.591441"
        }
    }




删除共享网络
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 DELETE /v1/{tenant_id}/share-
networks/{share_network_id} 删除共享网络
请求样例

::

    
    curl -s \
         -X DELETE `https://bj1.share.api.ustack.com//v1/{tenant_id}/share-networks/{share_network_id}`_ \
         -H "Content-Type: application/json" \
         -H "X-Auth-Token: {token_id}"


返回样例 :


::

    HTTP/1.1 204 No Content




配额 (Quota)
--------------------------------------



查看配额
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 GET /v1/{tenant_id}/os-quota-sets/{tenant_id} 查看配额
请求样例

::

    
    curl -s \
         -X GET `https://bj1.share.api.ustack.com//v1/{tenant_id}/os-quota-sets/{tenant_id}`_ \
         -H "Content-Type: application/json" \
         -H "X-Auth-Token: {token_id}"


返回样例 :


::

    {
        "quota_set": {
            "gigabytes": 1000,
            "id": "e6044929cfd545bdb618f60972d87a93",
            "share_networks": 10,
            "shares": 10,
            "snapshots": 10
        }
    }




查看默认配额
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 GET /v1/{tenant_id}/os-quota-sets/{tenant_id}/defaults
查看默认配额
请求样例

::

    
    curl -s \
         -X GET `https://bj1.share.api.ustack.com//v1/{tenant_id}/os-quota-sets/{tenant_id}/defaults`_ \
         -H "Content-Type: application/json" \
         -H "X-Auth-Token: {token_id}"


返回样例 :


::

    {
        "quota_set": {
            "gigabytes": 1000,
            "id": "e6044929cfd545bdb618f60972d87a93",
            "share_networks": 10,
            "shares": 10,
            "snapshots": 10
        }
    }




修改配额
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 PUT /v1/{tenant_id}/os-quota-sets/{tenant_id} 修改配额
请求样例

::

    
    curl -s \
         -X PUT `https://bj1.share.api.ustack.com//v1/{tenant_id}/os-quota-sets/{tenant_id}`_ \
         -H "Content-Type: application/json" \
         -H "X-Auth-Token: {token_id}" \
         -d '{
                "quota_set": {
                    "tenant_id": "e6044929cfd545bdb618f60972d87a93",
                    "shares": 1000
                }
            }'


返回样例 :


::

    {
        "quota_set": {
            "gigabytes": 1000,
            "share_networks": 1000,
            "shares": 1000,
            "snapshots": 10
        }
    }




恢复默认配额
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 DELETE /v1/{tenant_id}/os-quota-sets/{tenant_id} 删除配额
请求样例

::

    
    curl -s \
         -X DELETE `https://bj1.share.api.ustack.com//v1/{tenant_id}/os-quota-sets/{tenant_id}`_ \
         -H "Content-Type: application/json" \
         -H "X-Auth-Token: {token_id}"


返回样例 :


::

    HTTP/1.1 204 No Content


