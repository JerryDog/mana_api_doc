


块存储服务
======================



API规范
--------------------------

块存储服务API入口与API列表如下：


+ API入口:

区域 API入口 北京1区(bj1) `https://bj1.volume.api.ustack.com`_ 广东1区(gd1)
`https://gd1.volume.api.ustack.com`_

+ API列表:

资源 操作 HTTP方法 URI路径 云硬盘 (Volumes) *创建空白云硬盘* POST
/v2/{project_id}/volumes *从硬盘快照创建云硬盘* POST /v2/{project_id}/volumes
*查看云硬盘简单列表* GET /v2/{project_id}/volumes *查看云硬盘详细列表* GET
/v2/{project_id}/volumes/detail *查看指定云硬盘信息* GET
/v2/{project_id}/volumes/{volume_id} *修改云硬盘名字或描述* PUT
/v2/{project_id}/volumes/{volume_id} *删除云硬盘* DELETE
/v2/{project_id}/volumes/{volume_id} *云硬盘扩容* POST
/v2/{project_id}/volumes/{volume_id}/action 硬盘快照 (Snapshots) *创建硬盘快照*
POST /v2/{project_id}/snapshots *查看硬盘快照简单列表* GET
/v2/{project_id}/snapshots *查看硬盘快照详细列表* GET
/v2/{project_id}/snapshots/detail *查看指定硬盘快照信息* GET
/v2/{project_id}/snapshots/{snapshot_id} *删除硬盘快照* DELETE
/v2/{project_id}/snapshots/{snapshot_id}


云硬盘 (Volumes)
------------------------------------------



创建空白云硬盘
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 POST /v2/{project_id}/volumes 创建空白云硬盘
请求参数
字段名 类型 描述 display_name string(optional) 云硬盘的名字 display_description
string(optional) 云硬盘的描述 size int 云硬盘的大小，单位是GB volume_type
string(optional) 云硬盘的类型，默认是ssd，可选值：ssd, sata
请求样例

::

    
    curl -s \
         -X POST `https://bj1.volume.api.ustack.com/v2/{project_id}/volumes`_ \
         -H "Content-Type: application/json" \
         -H "X-Auth-Token: {token_id}" \
         -d '{
                "volume": {
                    "display_description": null,
                    "snapshot_id": null,
                    "size": 11,
                    "display_name": null
                }
            }'


返回参数
字段名 类型 描述 status string 云硬盘的状态 display_name string 云硬盘的名字
display_description string 云硬盘的描述 attachments string 云硬盘的挂载状态
created_at datetime 创建云硬盘的时间 snapshot_id uuid
假如云硬盘是基于硬盘快照创建的，这是硬盘快照的UUID size int 云硬盘的大小，单位是GB id uuid 云硬盘的UUID
返回样例 :


::

    HTTP/1.1 200
    
    {
      "volume": {
          "status": "creating",
          "display_name": "vol-6c8de3b0-f358-4ebb-a2f4-b49c22c44e75",
          "attachments": [],
          "created_at": "2014-07-06T04:55:52.454346",
          "display_description": null,
          "snapshot_id": null,
          "id": "6c8de3b0-f358-4ebb-a2f4-b49c22c44e75",
          "size": 11
      }
    }




从硬盘快照创建云硬盘
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 POST /v2/{project_id}/volumes 从硬盘快照创建云硬盘
请求参数
字段名 类型 描述 display_name string(optional) 云硬盘的名字 display_description
string(optional) 云硬盘的描述 snapshot_id uuid 硬盘快照的UUID size int
云硬盘的大小，单位是GB
请求样例

::

    
    curl -s \
         -X POST `https://bj1.volume.api.ustack.com/v2/{project_id}/volumes`_ \
         -H "Content-Type: application/json" \
         -H "X-Auth-Token: {token_id}" \
         -d '{
                "volume": {
                    "display_description": null,
                    "snapshot_id": "de40f8ef-48cb-4df5-bd51-9fd17d601b1e",
                    "size": 11,
                    "display_name": null
                }
            }'


返回参数
字段名 类型 描述 status string 云硬盘的状态 display_name string 云硬盘的名字
display_description string 云硬盘的描述 attachments string 云硬盘的挂载状态
created_at datetime 创建云硬盘的时间 snapshot_id uuid
假如云硬盘是基于硬盘快照创建的，这是硬盘快照的UUID size int 云硬盘的大小，单位是GB id uuid 云硬盘的UUID
返回样例 :


::

    HTTP/1.1 200
    
    {
      "volume": {
          "status": "creating",
          "display_name": "vol-6c8de3b0-f358-4ebb-a2f4-b49c22c44e75",
          "attachments": [],
          "created_at": "2014-07-06T04:55:52.454346",
          "display_description": null,
          "snapshot_id": "de40f8ef-48cb-4df5-bd51-9fd17d601b1e",
          "id": "6c8de3b0-f358-4ebb-a2f4-b49c22c44e75",
          "size": 11
      }
    }




查看云硬盘简单列表
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 GET /v2/{project_id}/volumes 查看云硬盘简单列表
请求参数

请求样例

::

    
    curl -s \
         -X GET `https://bj1.volume.api.ustack.com/v2/{project_id}/volumes`_ \
         -H "Content-Type: application/json" \
         -H "X-Auth-Token: {token_id}"


返回参数

返回样例 :


::

    HTTP/1.1 200
    
    {
      "volumes": [
          {
              "id": "45baf976-c20a-4894-a7c3-c94b7376bf55",
              "links": [
                  {
                      "href": "https://bj1.volume.api.ustack.com/v2/0c2eba2c5af04d3f9e9d0d410b371fde/volumes/45baf976-c20a-4894-a7c3-c94b7376bf55",
                      "rel": "self"
                  },
                  {
                      "href": "https://bj1.volume.api.ustack.com/0c2eba2c5af04d3f9e9d0d410b371fde/volumes/45baf976-c20a-4894-a7c3-c94b7376bf55",
                      "rel": "bookmark"
                  }
              ],
              "name": "vol-004"
          },
          {
              "id": "5aa119a8-d25b-45a7-8d1b-88e127885635",
              "links": [
                  {
                      "href": "https://bj1.volume.api.ustack.com/v2/0c2eba2c5af04d3f9e9d0d410b371fde/volumes/5aa119a8-d25b-45a7-8d1b-88e127885635",
                      "rel": "self"
                  },
                  {
                      "href": "https://bj1.volume.api.ustack.com/0c2eba2c5af04d3f9e9d0d410b371fde/volumes/5aa119a8-d25b-45a7-8d1b-88e127885635",
                      "rel": "bookmark"
                  }
              ],
              "name": "vol-003"
          }
      ]
    }




查看云硬盘详细列表
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 GET /v2/{project_id}/volumes/detail 查看云硬盘详细列表
请求参数

请求样例

::

    
    curl -s \
         -X GET `https://bj1.volume.api.ustack.com/v2/{project_id}/volumes/detail`_ \
         -H "Content-Type: application/json" \
         -H "X-Auth-Token: {token_id}"


返回参数

返回样例 :


::

    HTTP/1.1 200
    
    {
      "volumes": [
              {
                  "status": "available",
                  "attachments": [],
                  "links": [
                      {
                          "href": "https://bj1.volume.api.ustack.com/v2/0c2eba2c5af04d3f9e9d0d410b371fde/volumes/45baf976-c20a-4894-a7c3-c94b7376bf55",
                          "rel": "self"
                      },
                      {
                          "href": "https://bj1.volume.api.ustack.com/0c2eba2c5af04d3f9e9d0d410b371fde/volumes/45baf976-c20a-4894-a7c3-c94b7376bf55",
                          "rel": "bookmark"
                      }
                  ],
                  "availability_zone": "nova",
                  "os-vol-host-attr:host": "ip-10-168-107-25",
                  "source_volid": null,
                  "snapshot_id": null,
                  "id": "45baf976-c20a-4894-a7c3-c94b7376bf55",
                  "description": "Another volume.",
                  "name": "vol-004",
                  "created_at": "2013-02-25T06:36:28.000000",
                  "volume_type": "None",
                  "os-vol-tenant-attr:tenant_id": "0c2eba2c5af04d3f9e9d0d410b371fde",
                  "size": 1,
                  "metadata": {
                      "contents": "junk"
                  }
              },
              {
                  "status": "available",
                  "attachments": [],
                  "links": [
                      {
                          "href": "https://bj1.volume.api.ustack.com/v2/0c2eba2c5af04d3f9e9d0d410b371fde/volumes/5aa119a8-d25b-45a7-8d1b-88e127885635",
                          "rel": "self"
                      },
                      {
                          "href": "https://bj1.volume.api.ustack.com/0c2eba2c5af04d3f9e9d0d410b371fde/volumes/5aa119a8-d25b-45a7-8d1b-88e127885635",
                          "rel": "bookmark"
                      }
                  ],
                  "availability_zone": "nova",
                  "os-vol-host-attr:host": "ip-10-168-107-25",
                  "source_volid": null,
                  "snapshot_id": null,
                  "id": "5aa119a8-d25b-45a7-8d1b-88e127885635",
                  "description": "This is yet, another volume.",
                  "name": "vol-003",
                  "created_at": "2013-02-25T02:40:21.000000",
                  "volume_type": "None",
                  "os-vol-tenant-attr:tenant_id": "0c2eba2c5af04d3f9e9d0d410b371fde",
                  "size": 1,
                  "metadata": {
                      "contents": "not junk"
                  }
              }
      ]
    }




查看指定云硬盘信息
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 GET /v2/{project_id}/volumes/{volume_id} 查看指定云硬盘信息
请求参数

请求样例

::

    
    curl -s \
         -X GET `https://bj1.volume.api.ustack.com/v2/{project_id}/volumes/{volume_id}`_ \
         -H "Content-Type: application/json" \
         -H "X-Auth-Token: {token_id}"


返回参数

返回样例 :


::

    HTTP/1.1 200
    
    {
        "volume": {
          "status": "available",
          "attachments": [],
          "links": [
              {
                  "href": "https://bj1.volume.api.ustack.com/v2/0c2eba2c5af04d3f9e9d0d410b371fde/volumes/5aa119a8-d25b-45a7-8d1b-88e127885635",
                  "rel": "self"
              },
              {
                  "href": "https://bj1.volume.api.ustack.com/0c2eba2c5af04d3f9e9d0d410b371fde/volumes/5aa119a8-d25b-45a7-8d1b-88e127885635",
                  "rel": "bookmark"
              }
          ],
          "availability_zone": "nova",
          "bootable": "false",
          "os-vol-host-attr:host": "ip-10-168-107-25",
          "source_volid": null,
          "snapshot_id": null,
          "id": "5aa119a8-d25b-45a7-8d1b-88e127885635",
          "description": "Super volume.",
          "name": "vol-002",
          "created_at": "2013-02-25T02:40:21.000000",
          "volume_type": "None",
          "os-vol-tenant-attr:tenant_id": "0c2eba2c5af04d3f9e9d0d410b371fde",
          "size": 1,
          "metadata": {
              "contents": "not junk"
          }
      }
    }




修改云硬盘名字或描述
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 PUT /v2/{project_id}/volumes/{volume_id} 修改云硬盘名字或描述
请求参数
字段名 类型 描述 display_name string(optional) 云硬盘的名字 display_description
string(optional) 云硬盘的描述
请求样例

::

    
    curl -s \
         -X PUT `https://bj1.volume.api.ustack.com/v2/{project_id}/volumes/{volume_id}`_ \
         -H "Content-Type: application/json" \
         -H "X-Auth-Token: {token_id}" \
         -d '{
                "volume": {
                    "display_description": "This is yet, another volume.",
                    "display_name": "vol-003"
                }
            }'


返回样例 :


::

    HTTP/1.1 200
    
    {
      "volume": {
          "status": "available",
          "attachments": [],
          "links": [
              {
                  "href": "https://bj1.volume.api.ustack.com/v2/0c2eba2c5af04d3f9e9d0d410b371fde/volumes/5aa119a8-d25b-45a7-8d1b-88e127885635",
                  "rel": "self"
              },
              {
                  "href": "https://bj1.volume.api.ustack.com/0c2eba2c5af04d3f9e9d0d410b371fde/volumes/5aa119a8-d25b-45a7-8d1b-88e127885635",
                  "rel": "bookmark"
              }
          ],
          "availability_zone": "nova",
          "source_volid": null,
          "snapshot_id": null,
          "id": "5aa119a8-d25b-45a7-8d1b-88e127885635",
          "display_description": "This is yet, another volume.",
          "display_name": "vol-003",
          "created_at": "2013-02-25T02:40:21.000000",
          "volume_type": "None",
          "size": 1,
          "metadata": {
              "contents": "not junk"
          }
      }
    }




删除云硬盘
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 DELETE /v2/{project_id}/volumes/{volume_id} 删除云硬盘
请求样例

::

    
    curl -s \
         -X DELETE `https://bj1.volume.api.ustack.com/v2/{project_id}/volumes/{volume_id}`_ \
         -H "Content-Type: application/json" \
         -H "X-Auth-Token: {token_id}"


返回样例 :


::

    HTTP/1.1 202




云硬盘扩容
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 POST /v2/{project_id}/volumes/{volume_id}/action 云硬盘扩容
请求参数
字段名 类型 描述 new_size int 云硬盘新的大小
请求样例

::

    
    curl -s \
         -X POST `https://bj1.volume.api.ustack.com/v2/{project_id}/volumes/{volume_id}/action`_ \
         -H "Content-Type: application/json" \
         -H "X-Auth-Token: {token_id}" \
         -d '{
                "os-extend": {
                    "new_size": 21
                }
            }'


返回样例 :


::

    HTTP/1.1 202




硬盘快照 (Snapshots)
------------------------------------------------



创建硬盘快照
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 POST /v2/{project_id}/snapshots 创建硬盘快照
请求参数
字段名 类型 描述 name string(optional) 硬盘快照的名字 description string(optional)
硬盘快照的描述 volume_id uuid 云硬盘的UUID force boolean(optional)
是否强制创建硬盘快照(当云硬盘被挂载时)
请求样例

::

    
    curl -s \
         -X POST `https://bj1.volume.api.ustack.com/v2/{project_id}/snapshots`_ \
         -H "Content-Type: application/json" \
         -H "X-Auth-Token: {token_id}" \
         -d '{
                "snapshot": {
                    "name": "snap-001",
                    "description": "Daily backup",
                    "volume_id": "5aa119a8-d25b-45a7-8d1b-88e127885635",
                    "force": true
                }
            }'


返回参数
字段名 类型 描述 status string 硬盘快照的状态 name string 硬盘快照的名字 description string
硬盘快照的描述 created_at datetime 创建硬盘快照的时间 volume_id uuid 云硬盘的UUID size int
硬盘快照的大小，单位是GB id uuid 硬盘快照的UUID
返回样例 :


::

    HTTP/1.1 200
    
    {
      "snapshot": {
          "status": "creating",
          "description": "Daily backup",
          "created_at": "2013-02-25T03:56:53.081642",
          "volume_id": "5aa119a8-d25b-45a7-8d1b-88e127885635",
          "size": 1,
          "id": "ffa9bc5e-1172-4021-acaf-cdcd78a9584d",
          "name": "snap-001"
      }
    }




查看硬盘快照简单列表
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 GET /v2/{project_id}/snapshots 查看硬盘快照简单列表
请求参数

请求样例

::

    
    curl -s \
         -X GET `https://bj1.volume.api.ustack.com/v2/{project_id}/snapshots`_ \
         -H "Content-Type: application/json" \
         -H "X-Auth-Token: {token_id}"


返回参数

返回样例 :


::

    HTTP/1.1 200
    
    {
      "snapshots": [
          {
              "status": "available",
              "description": "Daily backup",
              "created_at": "2013-02-25T07:30:12.000000",
              "volume_id": "5aa119a8-d25b-45a7-8d1b-88e127885635",
              "size": 30,
              "id": "43f20e0e-2c2c-4770-9d4e-c3d769ae5470",
              "name": "snap-001"
          },
          {
              "status": "available",
              "description": "Weekly backup",
              "created_at": "2013-02-25T07:20:38.000000",
              "volume_id": "806092e3-7551-4fff-a005-49016f4943b1",
              "size": 1,
              "id": "e820db06-58b5-439d-bac6-c01faa3f6499",
              "name": "snap-002"
          }
      ]
    }




查看硬盘快照详细列表
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 GET /v2/{project_id}/snapshots/detail 查看硬盘快照详细列表
请求参数

请求样例

::

    
    curl -s \
        -X GET `https://bj1.volume.api.ustack.com/v2/{project_id}/snapshots/detail`_ \
        -H "Content-Type: application/json" \
        -H "X-Auth-Token: {token_id}"


返回参数

返回样例 :


::

    HTTP/1.1 200
    
    {
      "snapshots": [
          {
              "status": "available",
              "os-extended-snapshot-attributes:progress": "100%",
              "description": "Daily backup",
              "created_at": "2013-02-25T07:30:12.000000",
              "metadata": {},
              "volume_id": "5aa119a8-d25b-45a7-8d1b-88e127885635",
              "os-extended-snapshot-attributes:project_id": "0c2eba2c5af04d3f9e9d0d410b371fde",
              "size": 30,
              "id": "43f20e0e-2c2c-4770-9d4e-c3d769ae5470",
              "name": "snap-001"
          },
          {
              "status": "available",
              "os-extended-snapshot-attributes:progress": "100%",
              "description": "Weekly backup",
              "created_at": "2013-02-25T07:20:38.000000",
              "metadata": {},
              "volume_id": "806092e3-7551-4fff-a005-49016f4943b1",
              "os-extended-snapshot-attributes:project_id": "0c2eba2c5af04d3f9e9d0d410b371fde",
              "size": 1,
              "id": "e820db06-58b5-439d-bac6-c01faa3f6499",
              "name": "snap-002"
          }
      ]
    }




查看指定硬盘快照信息
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 GET /v2/{project_id}/snapshots/{snapshot_id}
查看指定硬盘快照信息
请求参数

请求样例

::

    
    curl -s \
         -X GET `https://bj1.volume.api.ustack.com/v2/{project_id}/snapshots/{snapshot_id}`_ \
         -H "Content-Type: application/json" \
         -H "X-Auth-Token: {token_id}"


返回样例 :


::

    HTTP/1.1 200
    
    {
      "snapshot": {
          "status": "available",
          "os-extended-snapshot-attributes:progress": "100%",
          "description": "Daily backup",
          "created_at": "2013-02-25T04:13:17.000000",
          "metadata": {},
          "volume_id": "5aa119a8-d25b-45a7-8d1b-88e127885635",
          "os-extended-snapshot-attributes:project_id": "0c2eba2c5af04d3f9e9d0d410b371fde",
          "size": 1,
          "id": "2bb856e1-b3d8-4432-a858-09e4ce939389",
          "name": "snap-001"
      }
    }




修改硬盘快照的名字或描述
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 PUT /v2/{project_id}/snapshots/{snapshot_id}
修改硬盘快照名字或描述
请求参数
字段名 类型 描述 name string(optional) 硬盘快照的名字 description string(optional)
硬盘快照的描述
请求样例

::

    
    curl -s \
         -X PUT `https://bj1.volume.api.ustack.com/v2/{project_id}/snapshots/{snapshot_id}`_ \
         -H "Content-Type: application/json" \
         -H "X-Auth-Token: {token_id}" \
         -d '{
                "snapshot": {
                    "description": "This is yet, another snapshot.",
                    "name": "snap-002"
                }
            }'


返回样例 :


::

    HTTP/1.1 200
    
    {
      "snapshot": {
          "created_at": "2013-02-20T08:11:34.000000",
          "description": "This is yet, another snapshot",
          "name": "vol-002",
          "id": "4b502fcb-1f26-45f8-9fe5-3b9a0a52eaf2",
          "size": 1,
          "status": "available",
          "volume_id": "2402b902-0b7a-458c-9c07-7435a826f794"
      }
    }




删除硬盘快照
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 DELETE /v2/{project_id}/snapshots/{snapshot_id} 删除硬盘快照
请求样例

::

    
    curl -s \
         -X DELETE `https://bj1.volume.api.ustack.com/v2/{project_id}/snapshots/{snapshot_id}`_ \
         -H "Content-Type: application/json" \
         -H "X-Auth-Token: {token_id}"


返回样例 :


::

    HTTP/1.1 202


