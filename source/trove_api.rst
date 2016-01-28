


数据库服务
========================



API规范
----------------------------

数据库服务API入口与API列表如下：


+ API入口:

区域 API入口 北京1区(bj1) `https://bj1.trove.api.ustack.com`_ 广东1区(gd1)
`https://gd1.trove.api.ustack.com`_

+ API列表:

资源 操作 HTTP方法 URI路径 *数据库实例 (Instances)* 创建数据库实例 POST
/v1.0/{project_id}/instances 查看数据库实例列表 GET
/v1.0/{project_id}/instances 查看全部数据库实例列表 GET
/v1.0/{project_id}/instances?all_tenants=1 查看数据库实例详情 GET
/v1.0/{project_id}/instances/{trove_instance_id} 更新数据库实例 PATCH
/v1.0/{project_id}/instances 删除数据库实例 DELETE
/v1.0/{project_id}/instances/{trove_instance_id} 重启数据库实例 POST
/v1.0/{project_id}/instances/action 扩容数据库实例 POST
/v1.0/{project_id}/instances/action 扩容数据库实例卷 POST
/v1.0/{project_id}/instances/action 创建数据库 POST
/v1.0/{project_id}/instances/{trove_instance_id}/databases 查看数据库列表 GET
/v1.0/{project_id}/instances/{trove_instance_id}/databases 删除数据库
DELETE /v1.0/{project_id}/instances/{trove_instance_id}/databases/{dat
abase_name} 创建数据库用户 POST
/v1.0/{project_id}/instances/{trove_instance_id}/users 查看数据库用户列表 GET
/v1.0/{project_id}/instances/{trove_instance_id}/users 删除数据库用户 DELETE
/v1.0/{project_id}/instances/{trove_instance_id}/users/{user_name}
查看默认配置 GET
/v1.0/{project_id}/instances/{trove_instance_id}/configuration
*数据库信息(datastores)* 查看支持数据库 GET /v1.0/{project_id}/datastores
查看支持数据库版本 GET /v1.0/{project_id}/datastores/{datastore_name} 查看配置参数
GET /v1.0/{project_id}/datastores/{datastore_name}/versions/{datastore
_version}/parameters 查看配置参数详情 GET /v1.0/{project_id}/datastores/{datas
tore_name}/versions/{datastore_version}/parameters/{parameter_name}
*配置组信息 (configurations)* 创建配置组 POST /v1.0/{project_id}/configurations
删除配置组 DELETE /v1.0/{project_id}/configurations/{configuration_id}
查看配置组详情 GET /v1.0/{project_id}/configurations/{configuration_id}
查看配置组列表 GET /v1.0/{project_id}/configurations 更新配置组 PUT
/v1.0/{project_id}/configurations/{configuration_id} 查看配置组关联虚拟机 GET
/v1.0/{project_id}/configurations/{configuration_id}/instances 挂载配置组
PUT /v1.0/{project_id}/instances/{trove_instance_id} 卸载配置组 PUT
/v1.0/{project_id}/instances/{trove_instance_id} 获取数据库配置 GET
/v1.0/{project_id}/flavors mgmt 显示租户quota信息 GET
/v1.0/{project_id}/mgmt/quotas/{project_id} mgnt 更新指定租户的quota 信息 PUT
/v1.0/{project_id}/mgmt/quotas/{project_id}


数据库实例 (Instances)
----------------------------------------------------



创建数据库实例
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 POST /v1.0/{project_id}/instances 创建数据库实例
请求样例

::

    
    curl -s \
         -X POST `https://bj1.trove.api.ustack.com/v1.0/{project_id}/instances`_ \
         -H "Content-Type: application/json" \
         -H "X-Auth-Token: {token_id}" \
         -d '{
               "instance": {
                   "users": [
                       {
                           "password": "nihao",
                           "name": "test",
                           "databases": [
                               {
                                   "name": "test-trove"
                               }
                           ]
                       }
                   ],
                   "availability_zone": "nova",
                   "nics": [
                       {
                           "net-id": "a1aeec04-0e2f-4928-b85c-bfb7402cd0ec",
                           "subnet-id": "d9c5c6eb-38bd-41d4-9bd2-8db25786a64b"
                       }
                   ],
                   "flavorRef": "042d5080-bf94-4945-b2a7-8244e4143661",
                   "volume": {
                       "size": 10
                   },
                   "databases": [
                       {
                           "name": "test-trove"
                       }
                   ],
                   "datastore": {
                       "version": "mysql-5.1",
                       "type": "mysql"
                   },
                   "name": "test-trove-3"
               }
           }'


返回样例


::

    {
        "instance": {
            "status": "BUILD",
            "updated": "2015-05-14T06:47:29",
            "name": "test-trove-5",
            "links": [
                {
                    "href": "https://10.0.1.39:8779/v1.0/ceb187578ca74d57bb71799393850ec8/instances/a2172557-3a40-4c2b-89ed-bd91f434977a",
                    "rel": "self"
                },
                {
                    "href": "https://10.0.1.39:8779/instances/a2172557-3a40-4c2b-89ed-bd91f434977a",
                    "rel": "bookmark"
                }
            ],
            "created": "2015-05-14T06:47:29",
            "subnet_id": null,
            "ip": null,
            "id": "a2172557-3a40-4c2b-89ed-bd91f434977a",
            "volume": {
                "size": 10
            },
            "flavor": {
                "id": "042d5080-bf94-4945-b2a7-8244e4143661",
                "links": [
                    {
                        "href": "https://10.0.1.39:8779/v1.0/ceb187578ca74d57bb71799393850ec8/flavors/042d5080-bf94-4945-b2a7-8244e4143661",
                        "rel": "self"
                    },
                    {
                        "href": "https://10.0.1.39:8779/flavors/042d5080-bf94-4945-b2a7-8244e4143661",
                        "rel": "bookmark"
                    }
                ]
            },
            "datastore": {
                "version": "mysql-5.1",
                "type": "mysql"
            }
        }
    }




查看数据库实例列表
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 GET /v1.0/{project_id}/instances 查看数据库实例列表
请求样例

::

    
    curl -s \
         -X GET `https://bj1.trove.api.ustack.com/v1.0/{project_id}/instances`_ \
         -H "Content-Type: application/json" \
         -H "X-Auth-Token: {token_id}"


返回样例


::

    {
        "instances": [
            {
                "status": "ACTIVE",
                "name": "test-trove-4",
                "links": [
                    {
                        "href": "https://10.0.1.39:8779/v1.0/ceb187578ca74d57bb71799393850ec8/instances/19c7fcda-5f55-411e-9780-d87f289d4f01",
                        "rel": "self"
                    },
                    {
                        "href": "https://10.0.1.39:8779/instances/19c7fcda-5f55-411e-9780-d87f289d4f01",
                        "rel": "bookmark"
                    }
                ],
                "created": "2015-05-14T01:53:18",
                "subnet_id": "d9c5c6eb-38bd-41d4-9bd2-8db25786a64b",
                "ip": "122.122.122.4",
                "id": "19c7fcda-5f55-411e-9780-d87f289d4f01",
                "volume": {
                    "size": 10
                },
                "flavor": {
                    "id": "042d5080-bf94-4945-b2a7-8244e4143661",
                    "links": [
                        {
                            "href": "https://10.0.1.39:8779/v1.0/ceb187578ca74d57bb71799393850ec8/flavors/042d5080-bf94-4945-b2a7-8244e4143661",
                            "rel": "self"
                        },
                        {
                            "href": "https://10.0.1.39:8779/flavors/042d5080-bf94-4945-b2a7-8244e4143661",
                            "rel": "bookmark"
                        }
                    ]
                },
                "datastore": {
                    "version": "mysql-5.1",
                    "type": "mysql"
                }
            },
            {
                "status": "ACTIVE",
                "name": "test-trove-2",
                "links": [
                    {
                        "href": "https://10.0.1.39:8779/v1.0/ceb187578ca74d57bb71799393850ec8/instances/857f6722-fd67-4fa7-ab1c-02ed2ba6e686",
                        "rel": "self"
                    },
                    {
                        "href": "https://10.0.1.39:8779/instances/857f6722-fd67-4fa7-ab1c-02ed2ba6e686",
                        "rel": "bookmark"
                    }
                ],
                "created": "2015-05-04T09:48:19",
                "subnet_id": "73afb726-71c9-4b80-8ccd-6e04cbc9c59d",
                "ip": "123.123.123.7",
                "id": "857f6722-fd67-4fa7-ab1c-02ed2ba6e686",
                "volume": {
                    "size": 10
                },
                "flavor": {
                    "id": "042d5080-bf94-4945-b2a7-8244e4143661",
                    "links": [
                        {
                            "href": "https://10.0.1.39:8779/v1.0/ceb187578ca74d57bb71799393850ec8/flavors/042d5080-bf94-4945-b2a7-8244e4143661",
                            "rel": "self"
                        },
                        {
                            "href": "https://10.0.1.39:8779/flavors/042d5080-bf94-4945-b2a7-8244e4143661",
                            "rel": "bookmark"
                        }
                    ]
                },
                "configuration": {
                    "id": "5017067f-9e75-49a5-b715-e833b34223c5",
                    "links": [
                        {
                            "href": "https://10.0.1.39:8779/v1.0/ceb187578ca74d57bb71799393850ec8/configurations/5017067f-9e75-49a5-b715-e833b34223c5",
                            "rel": "self"
                        },
                        {
                            "href": "https://10.0.1.39:8779/configurations/5017067f-9e75-49a5-b715-e833b34223c5",
                            "rel": "bookmark"
                        }
                    ],
                    "name": "test_conf"
                },
                "datastore": {
                    "version": "mysql-5.1",
                    "type": "mysql"
                }
            },
            {
                "status": "ACTIVE",
                "name": "test-trove-3",
                "links": [
                    {
                        "href": "https://10.0.1.39:8779/v1.0/ceb187578ca74d57bb71799393850ec8/instances/9d82b2ef-d108-4860-b4ff-e6d641f3cdc5",
                        "rel": "self"
                    },
                    {
                        "href": "https://10.0.1.39:8779/instances/9d82b2ef-d108-4860-b4ff-e6d641f3cdc5",
                        "rel": "bookmark"
                    }
                ],
                "created": "2015-05-12T10:30:21",
                "subnet_id": "d9c5c6eb-38bd-41d4-9bd2-8db25786a64b",
                "ip": "122.122.122.3",
                "id": "9d82b2ef-d108-4860-b4ff-e6d641f3cdc5",
                "volume": {
                    "size": 10
                },
                "flavor": {
                    "id": "042d5080-bf94-4945-b2a7-8244e4143661",
                    "links": [
                        {
                            "href": "https://10.0.1.39:8779/v1.0/ceb187578ca74d57bb71799393850ec8/flavors/042d5080-bf94-4945-b2a7-8244e4143661",
                            "rel": "self"
                        },
                        {
                            "href": "https://10.0.1.39:8779/flavors/042d5080-bf94-4945-b2a7-8244e4143661",
                            "rel": "bookmark"
                        }
                    ]
                },
                "datastore": {
                    "version": "mysql-5.1",
                    "type": "mysql"
                }
            },
            {
                "status": "ACTIVE",
                "name": "test-trove-5",
                "links": [
                    {
                        "href": "https://10.0.1.39:8779/v1.0/ceb187578ca74d57bb71799393850ec8/instances/f0f6255c-55a3-4d35-8523-6db961f585a9",
                        "rel": "self"
                    },
                    {
                        "href": "https://10.0.1.39:8779/instances/f0f6255c-55a3-4d35-8523-6db961f585a9",
                        "rel": "bookmark"
                    }
                ],
                "created": "2015-05-14T02:39:47",
                "subnet_id": "d9c5c6eb-38bd-41d4-9bd2-8db25786a64b",
                "ip": "122.122.122.5",
                "id": "f0f6255c-55a3-4d35-8523-6db961f585a9",
                "volume": {
                    "size": 10
                },
                "flavor": {
                    "id": "042d5080-bf94-4945-b2a7-8244e4143661",
                    "links": [
                        {
                            "href": "https://10.0.1.39:8779/v1.0/ceb187578ca74d57bb71799393850ec8/flavors/042d5080-bf94-4945-b2a7-8244e4143661",
                            "rel": "self"
                        },
                        {
                            "href": "https://10.0.1.39:8779/flavors/042d5080-bf94-4945-b2a7-8244e4143661",
                            "rel": "bookmark"
                        }
                    ]
                },
                "datastore": {
                    "version": "mysql-5.1",
                    "type": "mysql"
                }
            }
        ]
    }




查看全部数据库实例列表
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 | 描述 GET /v1.0/{project_id}/instances?all_tenants=1 |
查看全部数据库实例列表
请求样例

::

    
    curl -s \
         -X GET `https://bj1.trove.api.ustack.com/v1.0/{project_id}/instances?all_tenants=1`_ \
         -H "Content-Type: application/json" \
         -H "X-Auth-Token: {token_id}"


返回样例


::

    {
      "instances": [
      {
          "status": "ACTIVE",
          "links": [
          {
              "href": "https://10.0.3.31/v1.0/4eee4bf5930c4f6a8d9598a338727abe/instances/79ced950-154b-43f6-ac39-394679ebc4f7",
               "rel": "self"
          },
          {
              "href": "https://10.0.3.31/instances/79ced950-154b-43f6-ac39-394679ebc4f7",
              "rel": "bookmark"
          }
      ],
      "ip": null,
      "volume": {
      "size": 10
      },
      "flavor": {
          "id": "48836919-95bf-41a4-922b-829bac89e632",
          "links": [
          {
              "href": "https://10.0.3.31/v1.0/4eee4bf5930c4f6a8d9598a338727abe/flavors/48836919-95bf-41a4-922b-829bac89e632",
              "rel": "self"
          },
          {
              "href": "https://10.0.3.31/flavors/48836919-95bf-41a4-922b-829bac89e632",
              "rel": "bookmark"
          }
      ]
     },
     "id": "79ced950-154b-43f6-ac39-394679ebc4f7",
     "user_id": "6d3621bcc2134f44a36a9505ed0a0fba",
     "name": "mysql-2",
     "created": "2015-07-22T02:01:21",
     "subnet_id": null,
     "tenant_id": "4eee4bf5930c4f6a8d9598a338727abe",
     "datastore": {
     "version": "mysql-5.1",
     "type": "mysql"
     }
    },
    {
      "status": "ACTIVE",
      "links": [
          {
              "href": "https://10.0.3.31/v1.0/4eee4bf5930c4f6a8d9598a338727abe/instances/ca295579-ea18-45bc-8706-ffc8cff3bf97",
              "rel": "self"
          },
          {
              "href": "https://10.0.3.31/instances/ca295579-ea18-45bc-8706-ffc8cff3bf97",
              "rel": "bookmark"
          }
     ],
     "ip": null,
     "volume": {
     "size": 10
    },
    "flavor": {
      "id": "48836919-95bf-41a4-922b-829bac89e632",
      "links": [
      {
          "href":"https://10.0.3.31/v1.0/4eee4bf5930c4f6a8d9598a338727abe/flavors/48836919-95bf-41a4-922b-829bac89e632",
          "rel": "self"
      },
      {
          "href":"https://10.0.3.31/flavors/48836919-95bf-41a4-922b-829bac89e632",
          "rel":"bookmark"
      }
     ]
    },
      "id":"ca295579-ea18-45bc-8706-ffc8cff3bf97",
       "user_id":"6d3621bcc2134f44a36a9505ed0a0fba",
      "name":"mysql-1",
      "created":"2015-07-21T14:16:51",
      "subnet_id":null,
      "tenant_id":"88a73739c353499d8de3cf2b0ce74834",
      "datastore":{
          "version": "mysql-5.1",
          "type":"mysql"
       }
      }
     ]
    }




查看数据库实例详情
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 GET /v1.0/{project_id}/instances/{trove_instance_id}
查看数据库实例列表
请求样例

::

    
    curl -s \
         -X GET `https://bj1.trove.api.ustack.com/v1.0/{project_id}/instances/{trove_instance_id}`_ \
         -H "Content-Type: application/json" \
         -H "X-Auth-Token: {token_id}"


返回样例


::

    {
        "instance": {
            "status": "ACTIVE",
            "updated": "2015-05-14T01:05:22",
            "name": "test-trove-2",
            "links": [
                {
                    "href": "https://10.0.1.39:8779/v1.0/ceb187578ca74d57bb71799393850ec8/instances/857f6722-fd67-4fa7-ab1c-02ed2ba6e686",
                    "rel": "self"
                },
                {
                    "href": "https://10.0.1.39:8779/instances/857f6722-fd67-4fa7-ab1c-02ed2ba6e686",
                    "rel": "bookmark"
                }
            ],
            "created": "2015-05-04T09:48:19",
            "subnet_id": "73afb726-71c9-4b80-8ccd-6e04cbc9c59d",
            "ip": "123.123.123.7",
            "id": "857f6722-fd67-4fa7-ab1c-02ed2ba6e686",
            "volume": {
                "used": 0.12,
                "size": 10
            },
            "flavor": {
                "id": "042d5080-bf94-4945-b2a7-8244e4143661",
                "links": [
                    {
                        "href": "https://10.0.1.39:8779/v1.0/ceb187578ca74d57bb71799393850ec8/flavors/042d5080-bf94-4945-b2a7-8244e4143661",
                        "rel": "self"
                    },
                    {
                        "href": "https://10.0.1.39:8779/flavors/042d5080-bf94-4945-b2a7-8244e4143661",
                        "rel": "bookmark"
                    }
                ]
            },
            "configuration": {
                "id": "5017067f-9e75-49a5-b715-e833b34223c5",
                "links": [
                    {
                        "href": "https://10.0.1.39:8779/v1.0/ceb187578ca74d57bb71799393850ec8/configurations/5017067f-9e75-49a5-b715-e833b34223c5",
                        "rel": "self"
                    },
                    {
                        "href": "https://10.0.1.39:8779/configurations/5017067f-9e75-49a5-b715-e833b34223c5",
                        "rel": "bookmark"
                    }
                ],
                "name": "test_conf"
            },
            "datastore": {
                "version": "mysql-5.1",
                "type": "mysql"
            }
        }
    }




更新数据库实例
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 PATCH /v1.0/{project_id}/instances/{trove_instance_id}
更新数据库实例名称
请求参数
参数名 类型 描述 name string(optional) 数据库实例的名字 configuration dict(optional)
数据库配置组的href(如果有key，没有value，则是卸载配置)
请求样例

::

    
    curl -s \
         -X PATCH `https://bj1.trove.api.ustack.com/v1.0/{project_id}/instances/{trove_instance_id}`_ \
         -H "Content-Type: application/json" \
         -H "X-Auth-Token: {token_id}" \
         -d '{
                 "instance":{
                   "name": "trove",
                   "configuration": "`http://10.0.1.39:8779/v1.0/configurations/5017067f-9e75-49a5-b715-e833b34223c5`_"
                 }
           }'


返回样例


::

    HTTP/1.1 204 No Content




删除数据库实例
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法u URI路径 描述 DELETE
/v1.0/{project_id}/instances/{trove_instance_id} 删除数据库实例
请求样例

::

    
    curl -s \
         -X DELETE `https://bj1.trove.api.ustack.com/v1.0/{project_id}/instances/{trove_instance_id}`_ \
         -H "Content-Type: application/json" \
         -H "X-Auth-Token: {token_id}"


返回样例


::

    HTTP/1.1 204 No Content




重启数据库
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 POST
/v1.0/{project_id}/instances/{trove_instance_id}/action 重启数据库
请求样例

::

    
    curl -s \
         -X POST `https://bj1.trove.api.ustack.com/v1.0/{project_id}/instances/{trove_instance_id}/action`_ \
         -H "Content-Type: application/json" \
         -H "X-Auth-Token: {token_id}" \
         -d '{
                 "restart": {}
             }'


返回样例


::

    HTTP/1.1 204 No Content




扩容数据库实例
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 POST
/v1.0/{project_id}/instances/{trove_instance_id}/action 扩容数据库实例
请求样例

::

    
    curl -s \
         -X POST `https://bj1.trove.api.ustack.com/v1.0/{project_id}/instances/{trove_instance_id}/action`_ \
         -H "Content-Type: application/json" \
         -H "X-Auth-Token: {token_id}" \
         -d '{
                "resize": {
                    "flavorRef": "19f0bfab-9102-43ab-86e2-719bb31e4c5d"
                }
            }'


返回样例


::

    HTTP/1.1 204 No Content




扩容数据库实例卷
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 POST
/v1.0/{project_id}/instances/{trove_instance_id}/action 扩容数据库实例卷
请求样例

::

    
    curl -s \
         -X POST `https://bj1.trove.api.ustack.com/v1.0/{project_id}/instances/{trove_instance_id}/action`_ \
         -H "Content-Type: application/json" \
         -H "X-Auth-Token: {token_id}" \
         -d '{
                "resize": {
                    "volume": {
                       "size": 20
                    }
                }
            }'


返回样例


::

    HTTP/1.1 204 No Content




创建数据库
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 POST
/v1.0/{project_id}/instances/{trove_instance_id}/databases 创建数据库
请求样例

::

    
    curl -s \
         -X POST `https://bj1.trove.api.ustack.com/v1.0/{project_id}/instances/{trove_instance_id}/databases`_ \
         -H "Content-Type: application/json" \
         -H "X-Auth-Token: {token_id}" \
         -d '{
                 "databases": [
                   {
                       "character_set": "utf8",
                       "collate": "utf8_general_ci",
                       "name": "wordpress"
                   },
                   {
                       "name": "youdao"
                   }
               ]
             }'


返回样例


::

    HTTP/1.1 204 No Content




查看数据库列表
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 GET
/v1.0/{project_id}/instances/{trove_instance_id}/databases 查看数据库列表
请求样例

::

    
    curl -s \
         -X GET `https://bj1.trove.api.ustack.com/v1.0/{project_id}/instances/{trove_instance_id}/databases`_ \
         -H "Content-Type: application/json" \
         -H "X-Auth-Token: {token_id}"


返回样例


::

    {
         "databases": [
             {
                 "name": "test"
             },
             {
                 "name": "test-trove"
             },
             {
                 "name": "wordpress"
             }
         ]
     }




删除数据库
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 DELETE /v1.0/{project_id}/instances/{trove_instance_id
}/databases/{database_name} 删除数据库
请求样例

::

    
    curl -s \
         -X DELETE `https://bj1.trove.api.ustack.com/v1.0/{project_id}/instances/{trove_instance_id}/databases/{database_name}`_ \
         -H "Content-Type: application/json" \
         -H "X-Auth-Token: {token_id}"


返回样例


::

    HTTP/1.1 204 No Content




创建数据库用户
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 POST
/v1.0/{project_id}/instances/{trove_instance_id}/users 创建数据库用户
请求样例

::

    
    curl -s \
         -X POST `https://bj1.trove.api.ustack.com/v1.0/{project_id}/instances/{trove_instance_id}/users`_ \
         -H "Content-Type: application/json" \
         -H "X-Auth-Token: {token_id}" \
         -d '{
               "users": [
                   {
                       "password": "nihao",
                       "name": "test_000",
                       "databases": [
                           {
                               "name": "test-trove"
                           }
                       ]
                   }
               ]
           }'


返回样例


::

    HTTP/1.1 204 No Content




查看数据库用户列表
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 GET
/v1.0/{project_id}/instances/{trove_instance_id}/users 查看数据库用户列表
请求样例

::

    
    curl -s \
         -X GET `https://bj1.trove.api.ustack.com/v1.0/{project_id}/instances/{trove_instance_id}/users`_ \
         -H "Content-Type: application/json" \
         -H "X-Auth-Token: {token_id}"


返回样例


::

    {
        "users": [
            {
                "host": "%",
                "name": "test",
                "databases": [
                    {
                        "name": "test-trove"
                    }
                ]
            },
            {
                "host": "%",
                "name": "test_000",
                "databases": [
                    {
                        "name": "test-trove"
                    }
                ]
            }
        ]
    }




删除数据库用户
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 DELETE
/v1.0/{project_id}/instances/{trove_instance_id}/users/user_name
删除数据库用户列表
请求样例

::

    
    curl -s \
         -X DELETE `https://bj1.trove.api.ustack.com/v1.0/{project_id}/instances/{trove_instance_id}/users`_ \
         -H "Content-Type: application/json" \
         -H "X-Auth-Token: {token_id}"


返回样例


::

    HTTP/1.1 204 No Content




查看默认配置
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 GET
/v1.0/{project_id}/instances/{trove_instance_id}/configuration
获取数据库默认参数列表
请求样例

::

    
    curl -s \
         -X GET `https://bj1.trove.api.ustack.com/v1.0/{project_id}/instances/{trove_instance_id}/configuration`_ \
         -H "Content-Type: application/json" \
         -H "X-Auth-Token: {token_id}"


返回样例


::

    {
        "instance": {
            "configuration": {
                "tmp_table_size": "64M",
                "innodb_log_files_in_group": "2",
                "skip-external-locking": "1",
                "read_rnd_buffer_size": "512K",
                "max_user_connections": "400",
                "max_heap_table_size": "64M",
                "port": "3306",
                "tmpdir": "/var/tmp",
                "max_connections": "400",
                "myisam-recover": "BACKUP",
                "server_id": "938748080",
                "innodb_buffer_pool_size": "600M",
                "basedir": "/usr",
                "max_allowed_packet": "4M",
                "datadir": "/var/lib/mysql",
                "innodb_log_buffer_size": "25M",
                "table_open_cache": "1024",
                "connect_timeout": "15",
                "query_cache_type": "1",
                "local-infile": "0",
                "innodb_log_file_size": "50M",
                "pid_file": "/var/run/mysqld/mysqld.pid",
                "query_cache_limit": "1M",
                "wait_timeout": "120",
                "user": "mysql",
                "thread_cache_size": "16",
                "query_cache_size": "32M",
                "innodb_data_file_path": "ibdata1:10M:autoextend",
                "thread_stack": "192K",
                "default_storage_engine": "innodb",
                "sort_buffer_size": "1M",
                "table_definition_cache": "1024",
                "read_buffer_size": "512K",
                "open_files_limit": "2048",
                "innodb_file_per_table": "1",
                "key_buffer_size": "200M",
                "join_buffer_size": "1M"
            }
        }
    }




数据库信息(datastores)
----------------------------------------------------



查看支持数据库
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 GET /v1.0/{project_id}/datastores 查看支持数据库信息
请求样例

::

    
    curl -s \
         -X GET `https://bj1.trove.api.ustack.com/v1.0/{project_id}/datastores`_ \
         -H "Content-Type: application/json" \
         -H "X-Auth-Token: {token_id}"


返回样例


::

    {
        "datastores": [
            {
                "versions": [
                    {
                        "id": "ac79757c-7355-4c6d-89bf-1e8a4a14cdf5",
                        "links": [
                            {
                                "href": "https://10.0.1.39:8779/v1.0/ceb187578ca74d57bb71799393850ec8/datastores/versions/ac79757c-7355-4c6d-89bf-1e8a4a14cdf5",
                                "rel": "self"
                            },
                            {
                                "href": "https://10.0.1.39:8779/datastores/versions/ac79757c-7355-4c6d-89bf-1e8a4a14cdf5",
                                "rel": "bookmark"
                            }
                        ],
                        "name": "mysql-5.1"
                    }
                ],
                "id": "4e0ffaeb-5433-4910-8f5e-68d9f6d34d86",
                "links": [
                    {
                        "href": "https://10.0.1.39:8779/v1.0/ceb187578ca74d57bb71799393850ec8/datastores/4e0ffaeb-5433-4910-8f5e-68d9f6d34d86",
                        "rel": "self"
                    },
                    {
                        "href": "https://10.0.1.39:8779/datastores/4e0ffaeb-5433-4910-8f5e-68d9f6d34d86",
                        "rel": "bookmark"
                    }
                ],
                "name": "mysql"
            }
        ]
    }




查看支持数据库版本
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 GET /v1.0/{project_id}/datastores/{datastore_name}
查看支持数据库版本信息
请求样例

::

    
    curl -s \
         -X GET `https://bj1.trove.api.ustack.com/v1.0/{project_id}/datastores/{datastore_name}`_ \
         -H "Content-Type: application/json" \
         -H "X-Auth-Token: {token_id}"


返回样例


::

    {
        "datastore": {
            "versions": [
                {
                    "id": "ac79757c-7355-4c6d-89bf-1e8a4a14cdf5",
                    "links": [
                        {
                            "href": "https://10.0.1.39:8779/v1.0/ceb187578ca74d57bb71799393850ec8/datastores/versions/ac79757c-7355-4c6d-89bf-1e8a4a14cdf5",
                            "rel": "self"
                        },
                        {
                            "href": "https://10.0.1.39:8779/datastores/versions/ac79757c-7355-4c6d-89bf-1e8a4a14cdf5",
                            "rel": "bookmark"
                        }
                    ],
                    "name": "mysql-5.1"
                }
            ],
            "id": "4e0ffaeb-5433-4910-8f5e-68d9f6d34d86",
            "links": [
                {
                    "href": "https://10.0.1.39:8779/v1.0/ceb187578ca74d57bb71799393850ec8/datastores/4e0ffaeb-5433-4910-8f5e-68d9f6d34d86",
                    "rel": "self"
                },
                {
                    "href": "https://10.0.1.39:8779/datastores/4e0ffaeb-5433-4910-8f5e-68d9f6d34d86",
                    "rel": "bookmark"
                }
            ],
            "name": "mysql"
        }
    }




查看数据库配置参数
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 GET /v1.0/{project_id}/datastores/{datastore_name}/ver
sions/{datastore_version}/parameters 获取数据库参数列表
请求样例

::

    
    curl -s \
         -X GET `https://bj1.trove.api.ustack.com/v1.0/{project_id}/datastores/{datastore_name}/versions/{datastore_version}/parameters`_ \
         -H "Content-Type: application/json" \
         -H "X-Auth-Token: {token_id}"


返回样例


::

    {
        "configuration-parameters": [
            {
                "name": "innodb_flush_log_at_trx_commit",
                "min": "0",
                "max": "2",
                "restart_required": false,
                "type": "integer",
                "datastore_version_id": "ac79757c-7355-4c6d-89bf-1e8a4a14cdf5"
            },
            {
                "name": "interactive_timeout",
                "min": "1",
                "max": "65535",
                "restart_required": false,
                "type": "integer",
                "datastore_version_id": "ac79757c-7355-4c6d-89bf-1e8a4a14cdf5"
            },
            {
                "name": "max_connect_errors",
                "min": "1",
                "max": "18446744073709547520",
                "restart_required": false,
                "type": "integer",
                "datastore_version_id": "ac79757c-7355-4c6d-89bf-1e8a4a14cdf5"
            },
            {
                "name": "wait_timeout",
                "min": "1",
                "max": "31536000",
                "restart_required": false,
                "type": "integer",
                "datastore_version_id": "ac79757c-7355-4c6d-89bf-1e8a4a14cdf5"
            }
        ]
    }




查看数据库配置参数详情
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 GET /v1.0/{project_id}/datastores/{datastore_name}/ver
sions/{datastore_version}/parameters/{parameter_name} 获取数据库配置参数详情
请求样例

::

    
    curl -s \
         -X GET `https://bj1.trove.api.ustack.com/v1.0/{project_id}/datastores/{datastore_name}/versions/{datastore_version}/parameters/{parameter_name}`_ \
         -H "Content-Type: application/json" \
         -H "X-Auth-Token: {token_id}"


返回样例


::

    {
        "name": "innodb_flush_log_at_trx_commit",
        "min": "0",
        "max": "2",
        "restart_required": false,
        "type": "integer",
        "datastore_version_id": "ac79757c-7355-4c6d-89bf-1e8a4a14cdf5"
    }




配置组信息 (configurations)
--------------------------------------------------------------



创建配置组
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 POST /v1.0/{project_id}/configurations 创建数据库配置组
请求样例

::

    
    curl -s \
         -X POST `https://bj1.trove.api.ustack.com/v1.0/{project_id}/configurations`_ \
         -H "Content-Type: application/json" \
         -H "X-Auth-Token: {token_id}" \
         -d '{
                 "configuration": {
                     "datastore": {
                         "version": "mysql-5.1",
                         "type": "mysql"
                     },
                     "values": {
                         "wait_timeout": 100,
                         "max_connect_errors": 50
                     },
                     "name": "test_conf",
                     "description": "for test"
                 }
             }'


返回样例


::

    {
        "configuration": {
            "datastore_name": "mysql",
            "updated": "2015-05-05T09:22:03",
            "values": {
                "wait_timeout": 100,
                "max_connect_errors": 50
            },
            "name": "test_conf",
            "created": "2015-05-05T09:22:03",
            "datastore_version_name": "mysql-5.1",
            "instance_count": 0,
            "id": "5017067f-9e75-49a5-b715-e833b34223c5",
            "datastore_version_id": "ac79757c-7355-4c6d-89bf-1e8a4a14cdf5",
            "description": "for test"
        }
    }




删除配置组
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 DELETE
/v1.0/{project_id}/configurations/{configuration_id} 删除数据库配置组
请求样例

::

    
    curl -s \
         -X DELETE `https://bj1.trove.api.ustack.com/v1.0/{project_id}/configurations/{configuration_id}`_ \
         -H "Content-Type: application/json" \
         -H "X-Auth-Token: {token_id}"


返回样例


::

    HTTP/1.1 204 No Content




查看配置组详情
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 GET
/v1.0/{project_id}/configurations/{configuration_id} 查看数据库配置组
请求样例

::

    
    curl -s \
         -X GET `https://bj1.trove.api.ustack.com/v1.0/{project_id}/configurations/{configuration_id}`_ \
         -H "Content-Type: application/json" \
         -H "X-Auth-Token: {token_id}"


返回样例


::

    {
         "configuration": {
             "datastore_name": "mysql",
             "updated": "2015-05-05T09:22:03",
             "values": {
                 "wait_timeout": 100,
                 "max_connect_errors": 50
             },
             "name": "test_conf",
             "created": "2015-05-05T09:22:03",
             "datastore_version_name": "mysql-5.1",
             "instance_count": 0,
             "id": "5017067f-9e75-49a5-b715-e833b34223c5",
             "datastore_version_id": "ac79757c-7355-4c6d-89bf-1e8a4a14cdf5",
             "description": "for test"
         }
     }




查看配置组列表
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 GET /v1.0/{project_id}/configurations 查看配置组列表
请求样例

::

    
    curl -s \
         -X GET `https://bj1.trove.api.ustack.com/v1.0/{project_id}/configurations`_ \
         -H "Content-Type: application/json" \
         -H "X-Auth-Token: {token_id}"


返回样例


::

    {
        "configurations": [
            {
                "datastore_name": "mysql",
                "updated": "2015-05-05T09:22:03",
                "name": "test_conf",
                "created": "2015-05-05T09:22:03",
                "datastore_version_name": "mysql-5.1",
                "id": "5017067f-9e75-49a5-b715-e833b34223c5",
                "datastore_version_id": "ac79757c-7355-4c6d-89bf-1e8a4a14cdf5",
                "description": "for test"
            },
            {
                "datastore_name": "mysql",
                "updated": "2015-05-05T09:29:51",
                "name": "test_conf_001",
                "created": "2015-05-05T09:29:51",
                "datastore_version_name": "mysql-5.1",
                "id": "6bd57547-a428-46db-a2e2-c23d85c617c0",
                "datastore_version_id": "ac79757c-7355-4c6d-89bf-1e8a4a14cdf5",
                "description": "for test"
            }
        ]
    }




更新配置组
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 PUT
/v1.0/{project_id}/configurations/{configuration_id} 更新数据库配置组
请求参数
参数名 类型 描述 name string(optional) 名字 description string(optional) 描述
values dict(optional) 配置组参数值(注意这里也是全量更新)
请求样例

::

    
    curl -s \
         -X PUT `https://bj1.trove.api.ustack.com/v1.0/{project_id}/configurations/{configuration_id}`_ \
         -H "Content-Type: application/json" \
         -H "X-Auth-Token: {token_id}" \
         -d '{
                 "configuration": {
                     "name": "kk",
                     "description": "new description",
                     "values": {
                         "wait_timeout": 50,
                         "max_connect_errors": 60,
                         "innodb_flush_log_at_trx_commit": 0
                     }
                 }
             }'


返回样例


::

    HTTP/1.1 204 No Content




查看配置组关联虚拟机
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 GET
/v1.0/{project_id}/configurations/{configuration_id}/instances
查看配置组关联虚拟机
请求样例

::

    
    curl -s \
         -X GET `https://bj1.trove.api.ustack.com/v1.0/{project_id}/configurations/{configuration_id}/instances`_ \
         -H "Content-Type: application/json" \
         -H "X-Auth-Token: {token_id}"


返回样例


::

    {
        "instances": [
            {
                "id": "49844c26-aac4-4f2d-95a2-bcb6bb50f509",
                "name": "test-trove-1"
            }
        ]
    }




挂载配置组
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 PUT /v1.0/{project_id}/instances/{trove_instance_id}
挂载数据库配置组
请求样例

::

    
    curl -s \
         -X PUT `https://bj1.trove.api.ustack.com/v1.0/{project_id}/instances/{trove_instance_id}`_ \
         -H "Content-Type: application/json" \
         -H "X-Auth-Token: {token_id}" \
         -d '{
               "instance": {
                   "configuration": "9e67f20e-cfd8-40c4-bbf5-2a343882a5b4"
               }
            }'


返回样例


::

    HTTP/1.1 204 No Content




卸载配置组
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 PUT /v1.0/{project_id}/instances/{trove_instance_id}
卸载数据库配置组
请求样例

::

    
    curl -s \
         -X PUT `https://bj1.trove.api.ustack.com/v1.0/{project_id}/instances/{trove_instance_id}`_ \
         -H "Content-Type: application/json" \
         -H "X-Auth-Token: {token_id}" \
         -d '{
                "instance": {}
            }'


返回样例 :


::

    .. parsed-literal::

HTTP/1.1 204 No Content


获取数据库配置
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 GET /v1.0/{project_id}/flavors 获取数据库配置
请求样例

::

    
    curl -s \
          -X GET `https://bj1.trove.api.ustack.com/v1.0/{project_id}/flavors`_ \
          -H "Content-Type: application/json" \
          -H "X-Auth-Token: {token_id}"


返回样例


::

    {
        "flavors": [
            {
                "name": "micro-2",
                "links": [
                    {
                        "href": "https://10.0.1.39:8779/v1.0/ceb187578ca74d57bb71799393850ec8/flavors/042d5080-bf94-4945-b2a7-8244e4143661",
                        "rel": "self"
                    },
                    {
                        "href": "https://10.0.1.39:8779/flavors/042d5080-bf94-4945-b2a7-8244e4143661",
                        "rel": "bookmark"
                    }
                ],
                "ram": 1024,
                "vcpus": 1,
                "str_id": "042d5080-bf94-4945-b2a7-8244e4143661",
                "id": null
            },
            {
                "name": "memory-1",
                "links": [
                    {
                        "href": "https://10.0.1.39:8779/v1.0/ceb187578ca74d57bb71799393850ec8/flavors/0b7205a8-09c0-44c8-9893-a7b25c054c0d",
                        "rel": "self"
                    },
                    {
                        "href": "https://10.0.1.39:8779/flavors/0b7205a8-09c0-44c8-9893-a7b25c054c0d",
                        "rel": "bookmark"
                    }
                ],
                "ram": 4096,
                "vcpus": 1,
                "str_id": "0b7205a8-09c0-44c8-9893-a7b25c054c0d",
                "id": null
            },
            {
                "name": "memory-2",
                "links": [
                    {
                        "href": "https://10.0.1.39:8779/v1.0/ceb187578ca74d57bb71799393850ec8/flavors/19f0bfab-9102-43ab-86e2-719bb31e4c5d",
                        "rel": "self"
                    },
                    {
                        "href": "https://10.0.1.39:8779/flavors/19f0bfab-9102-43ab-86e2-719bb31e4c5d",
                        "rel": "bookmark"
                    }
                ],
                "ram": 8192,
                "vcpus": 2,
                "str_id": "19f0bfab-9102-43ab-86e2-719bb31e4c5d",
                "id": null
            },
            {
                "name": "memory-12",
                "links": [
                    {
                        "href": "https://10.0.1.39:8779/v1.0/ceb187578ca74d57bb71799393850ec8/flavors/22c493dc-f45f-4d58-82a0-4a35dd746c08",
                        "rel": "self"
                    },
                    {
                        "href": "https://10.0.1.39:8779/flavors/22c493dc-f45f-4d58-82a0-4a35dd746c08",
                        "rel": "bookmark"
                    }
                ],
                "ram": 49152,
                "vcpus": 12,
                "str_id": "22c493dc-f45f-4d58-82a0-4a35dd746c08",
                "id": null
            },
            {
                "name": "micro-1",
                "links": [
                    {
                        "href": "https://10.0.1.39:8779/v1.0/ceb187578ca74d57bb71799393850ec8/flavors/2f5a2788-1778-4d21-a4cf-eb4b2866c855",
                        "rel": "self"
                    },
                    {
                        "href": "https://10.0.1.39:8779/flavors/2f5a2788-1778-4d21-a4cf-eb4b2866c855",
                        "rel": "bookmark"
                    }
                ],
                "ram": 512,
                "vcpus": 1,
                "str_id": "2f5a2788-1778-4d21-a4cf-eb4b2866c855",
                "id": null
            },
            {
                "name": "vfw-flavor",
                "links": [
                    {
                        "href": "https://10.0.1.39:8779/v1.0/ceb187578ca74d57bb71799393850ec8/flavors/35a17783-934c-4651-95b4-6a604eafc4a2",
                        "rel": "self"
                    },
                    {
                        "href": "https://10.0.1.39:8779/flavors/35a17783-934c-4651-95b4-6a604eafc4a2",
                        "rel": "bookmark"
                    }
                ],
                "ram": 2048,
                "vcpus": 2,
                "str_id": "35a17783-934c-4651-95b4-6a604eafc4a2",
                "id": null
            },
            {
                "name": "standard-16",
                "links": [
                    {
                        "href": "https://10.0.1.39:8779/v1.0/ceb187578ca74d57bb71799393850ec8/flavors/4337f81d-b19a-4aa1-90b9-bd2644049812",
                        "rel": "self"
                    },
                    {
                        "href": "https://10.0.1.39:8779/flavors/4337f81d-b19a-4aa1-90b9-bd2644049812",
                        "rel": "bookmark"
                    }
                ],
                "ram": 32768,
                "vcpus": 16,
                "str_id": "4337f81d-b19a-4aa1-90b9-bd2644049812",
                "id": null
            },
            {
                "name": "memory-8",
                "links": [
                    {
                        "href": "https://10.0.1.39:8779/v1.0/ceb187578ca74d57bb71799393850ec8/flavors/6ad3d015-ad51-4d53-b226-1321a6554ee7",
                        "rel": "self"
                    },
                    {
                        "href": "https://10.0.1.39:8779/flavors/6ad3d015-ad51-4d53-b226-1321a6554ee7",
                        "rel": "bookmark"
                    }
                ],
                "ram": 32768,
                "vcpus": 8,
                "str_id": "6ad3d015-ad51-4d53-b226-1321a6554ee7",
                "id": null
            },
            {
                "name": "compute-2",
                "links": [
                    {
                        "href": "https://10.0.1.39:8779/v1.0/ceb187578ca74d57bb71799393850ec8/flavors/6b2b3b62-1819-433d-a6fc-db142ad3ab7f",
                        "rel": "self"
                    },
                    {
                        "href": "https://10.0.1.39:8779/flavors/6b2b3b62-1819-433d-a6fc-db142ad3ab7f",
                        "rel": "bookmark"
                    }
                ],
                "ram": 2048,
                "vcpus": 2,
                "str_id": "6b2b3b62-1819-433d-a6fc-db142ad3ab7f",
                "id": null
            },
            {
                "name": "compute-4",
                "links": [
                    {
                        "href": "https://10.0.1.39:8779/v1.0/ceb187578ca74d57bb71799393850ec8/flavors/6cc97214-b2a7-4030-a11f-793eb90702b6",
                        "rel": "self"
                    },
                    {
                        "href": "https://10.0.1.39:8779/flavors/6cc97214-b2a7-4030-a11f-793eb90702b6",
                        "rel": "bookmark"
                    }
                ],
                "ram": 4096,
                "vcpus": 4,
                "str_id": "6cc97214-b2a7-4030-a11f-793eb90702b6",
                "id": null
            },
            {
                "name": "standard-2",
                "links": [
                    {
                        "href": "https://10.0.1.39:8779/v1.0/ceb187578ca74d57bb71799393850ec8/flavors/7302947b-d321-46f4-9dd1-a376f86c26ff",
                        "rel": "self"
                    },
                    {
                        "href": "https://10.0.1.39:8779/flavors/7302947b-d321-46f4-9dd1-a376f86c26ff",
                        "rel": "bookmark"
                    }
                ],
                "ram": 4096,
                "vcpus": 2,
                "str_id": "7302947b-d321-46f4-9dd1-a376f86c26ff",
                "id": null
            },
            {
                "name": "standard-4",
                "links": [
                    {
                        "href": "https://10.0.1.39:8779/v1.0/ceb187578ca74d57bb71799393850ec8/flavors/957e65f9-a128-4d82-aa90-bd896c249168",
                        "rel": "self"
                    },
                    {
                        "href": "https://10.0.1.39:8779/flavors/957e65f9-a128-4d82-aa90-bd896c249168",
                        "rel": "bookmark"
                    }
                ],
                "ram": 8192,
                "vcpus": 4,
                "str_id": "957e65f9-a128-4d82-aa90-bd896c249168",
                "id": null
            },
            {
                "name": "standard-1",
                "links": [
                    {
                        "href": "https://10.0.1.39:8779/v1.0/ceb187578ca74d57bb71799393850ec8/flavors/ad462089-f6f8-4d09-9287-0ebd6436929d",
                        "rel": "self"
                    },
                    {
                        "href": "https://10.0.1.39:8779/flavors/ad462089-f6f8-4d09-9287-0ebd6436929d",
                        "rel": "bookmark"
                    }
                ],
                "ram": 2048,
                "vcpus": 1,
                "str_id": "ad462089-f6f8-4d09-9287-0ebd6436929d",
                "id": null
            },
            {
                "name": "compute-12",
                "links": [
                    {
                        "href": "https://10.0.1.39:8779/v1.0/ceb187578ca74d57bb71799393850ec8/flavors/ae46605c-b4ca-4d4e-92af-bc8322c14ca9",
                        "rel": "self"
                    },
                    {
                        "href": "https://10.0.1.39:8779/flavors/ae46605c-b4ca-4d4e-92af-bc8322c14ca9",
                        "rel": "bookmark"
                    }
                ],
                "ram": 12288,
                "vcpus": 12,
                "str_id": "ae46605c-b4ca-4d4e-92af-bc8322c14ca9",
                "id": null
            },
            {
                "name": "standard-12",
                "links": [
                    {
                        "href": "https://10.0.1.39:8779/v1.0/ceb187578ca74d57bb71799393850ec8/flavors/c440f972-8fc7-4efc-868b-a1bc32f5eba3",
                        "rel": "self"
                    },
                    {
                        "href": "https://10.0.1.39:8779/flavors/c440f972-8fc7-4efc-868b-a1bc32f5eba3",
                        "rel": "bookmark"
                    }
                ],
                "ram": 24576,
                "vcpus": 12,
                "str_id": "c440f972-8fc7-4efc-868b-a1bc32f5eba3",
                "id": null
            },
            {
                "name": "standard-8",
                "links": [
                    {
                        "href": "https://10.0.1.39:8779/v1.0/ceb187578ca74d57bb71799393850ec8/flavors/e02b81e6-ff24-45cf-bdbe-0dd3056a3e68",
                        "rel": "self"
                    },
                    {
                        "href": "https://10.0.1.39:8779/flavors/e02b81e6-ff24-45cf-bdbe-0dd3056a3e68",
                        "rel": "bookmark"
                    }
                ],
                "ram": 16384,
                "vcpus": 8,
                "str_id": "e02b81e6-ff24-45cf-bdbe-0dd3056a3e68",
                "id": null
            },
            {
                "name": "memory-4",
                "links": [
                    {
                        "href": "https://10.0.1.39:8779/v1.0/ceb187578ca74d57bb71799393850ec8/flavors/e0f9798d-a063-497c-9c7a-9be5e5e6c3e1",
                        "rel": "self"
                    },
                    {
                        "href": "https://10.0.1.39:8779/flavors/e0f9798d-a063-497c-9c7a-9be5e5e6c3e1",
                        "rel": "bookmark"
                    }
                ],
                "ram": 16384,
                "vcpus": 4,
                "str_id": "e0f9798d-a063-497c-9c7a-9be5e5e6c3e1",
                "id": null
            },
            {
                "name": "compute-8",
                "links": [
                    {
                        "href": "https://10.0.1.39:8779/v1.0/ceb187578ca74d57bb71799393850ec8/flavors/e553b24a-f739-4ca7-9bbf-3c88c2232387",
                        "rel": "self"
                    },
                    {
                        "href": "https://10.0.1.39:8779/flavors/e553b24a-f739-4ca7-9bbf-3c88c2232387",
                        "rel": "bookmark"
                    }
                ],
                "ram": 8192,
                "vcpus": 8,
                "str_id": "e553b24a-f739-4ca7-9bbf-3c88c2232387",
                "id": null
            },
            {
                "name": "hillstone1",
                "links": [
                    {
                        "href": "https://10.0.1.39:8779/v1.0/ceb187578ca74d57bb71799393850ec8/flavors/ee26e7ad-fe20-4bf7-b5b4-6cd18c5dc5f7",
                        "rel": "self"
                    },
                    {
                        "href": "https://10.0.1.39:8779/flavors/ee26e7ad-fe20-4bf7-b5b4-6cd18c5dc5f7",
                        "rel": "bookmark"
                    }
                ],
                "ram": 1024,
                "vcpus": 1,
                "str_id": "ee26e7ad-fe20-4bf7-b5b4-6cd18c5dc5f7",
                "id": null
            }
        ]
    }




mgmt 显示租户quota信息
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 GET /v1.0/{project_id}/mgmt/quotas/{project_id} mgmt
显示租户quota信息
请求样例

::

    
    curl -s \
        -X GET `https://bj1.trove.api.ustack.com//v1.0/{project_id}/mgmt/quotas/{project_id}`_ \
        -H "Content-Type: application/json" \
        -H "X-Auth-Token: {token_id}"


返回样例


::

    {
        "quotas": {
            "instances": {
                "reserved": 0,
                "limit": 102,
                "in_use": 1
            },
            "backups": {
                "reserved": 0,
                "limit": 5,
                "in_use": 0
            },
            "volumes": {
                "reserved": 0,
                "limit": 101,
                "in_use": 10
            }
        }
    }




mgmt 更新指定租户的quota信息
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 GET /v1.0/{project_id}/mgmt/quotas/{project_id} mgmt
更新指定租户quota信息
请求参数
参数名 类型 描述 instances int(optional) 实例 backups int(optional) 备份 volumes
int(optional) 卷
请求样例

::

    
    curl -s \
         -X GET `https://bj1.trove.api.ustack.com//v1.0/{project_id}/mgmt/quotas/{project_id}`_ \
         -H "Content-Type: application/json" \
         -H "X-Auth-Token: {token_id}" \
         -d '{
               "quotas": {
                   "instances": 102,
                   "backups": 6,
                   "volumes": 101
               }
            '}


返回样例


::

    {
        "quotas": {
            "instances": {
                "limit": 102,
            },
            "backups": {
                "limit": 6,
            },
            "volumes": {
                "limit": 101,
            }
        }
    }


