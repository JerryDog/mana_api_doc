


镜像服务
====================



API规范
--------------------------

镜像服务API入口与API列表如下:


+ API入口:

区域 API入口 北京1区(bj1) `https://bj1.image.api.ustack.com`_ 广东1区(gd1)
`https://gd1.image.api.ustack.com`_

+ API列表:

资源 操作 HTTP方法 URI路径 镜像 (Images) *查看所有镜像* GET /v2/images *查看指定镜像* GET
/v2/images/{image_id} *修改镜像* PATCH /v2/images/{image_id} *删除镜像(主机快照)*
DELETE /v2/images/{image_id}


镜像 (Images)
--------------------------------------



查看所有镜像
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 GET /v2/images 查看所有镜像
请求样例

::

    
    curl -s \
         -X GET `https://bj1.image.api.ustack.com/v2/images`_ \
         -H "Content-Type: application/json" \
         -H "X-Auth-Token: {token_id}"


返回样例 :


::

    HTTP/1.1 200
    
    {
      "images": [
          {
              "id": "da3b75d9-3f4a-40e7-8a2c-bfab23927dea",
              "name": "cirros-0.3.0-x86_64-uec-ramdisk",
              "status": "active",
              "visibility": "public",
              "size": 2254249,
              "checksum": "2cec138d7dae2aa59038ef8c9aec2390",
              "tags": ["ping", "pong"],
              "created_at": "2012-08-10T19:23:50Z",
              "updated_at": "2012-08-10T19:23:50Z",
              "self": "/v2/images/da3b75d9-3f4a-40e7-8a2c-bfab23927dea",
              "file": "/v2/images/da3b75d9-3f4a-40e7-8a2c-bfab23927dea/file",
              "schema": "/v2/schemas/image"
          },
          {
              "id": "0d5bcbc7-b066-4217-83f4-7111a60a399a",
              "name": "cirros-0.3.0-x86_64-uec",
              "status": "active",
              "visibility": "public",
              "size": 25165824,
              "checksum": "2f81976cae15c16ef0010c51e3a6c163",
              "tags": [],
              "created_at": "2012-08-10T19:23:50Z",
              "updated_at": "2012-08-10T19:23:50Z",
              "self": "/v2/images/0d5bcbc7-b066-4217-83f4-7111a60a399a",
              "file": "/v2/images/0d5bcbc7-b066-4217-83f4-7111a60a399a/file",
              "schema": "/v2/schemas/image"
          }
      ],
      "first": "/v2/images?limit=3",
      "next": "/v2/images?limit=3&marker=e6421c88-b1ed-4407-8824-b57298249091",
      "schema": "/v2/schemas/images"
    }




查看指定镜像
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 GET /v2/images/{image_id} 查看指定镜像
请求样例

::

    
    curl -s \
         -X GET `https://bj1.image.api.ustack.com/v2/images/{image_id}`_ \
         -H "Content-Type: application/json" \
         -H "X-Auth-Token: {token_id}"


返回样例 :


::

    HTTP/1.1 200
    
    {
      "id": "da3b75d9-3f4a-40e7-8a2c-bfab23927dea",
      "name": "cirros-0.3.0-x86_64-uec-ramdisk",
      "status": "active",
      "visibility": "public",
      "size": 2254249,
      "checksum": "2cec138d7dae2aa59038ef8c9aec2390",
      "tags": ["ping", "pong"],
      "created_at": "2012-08-10T19:23:50Z",
      "updated_at": "2012-08-10T19:23:50Z",
      "self": "/v2/images/da3b75d9-3f4a-40e7-8a2c-bfab23927dea",
      "file": "/v2/images/da3b75d9-3f4a-40e7-8a2c-bfab23927dea/file",
      "schema": "/v2/schemas/image"
    }




修改镜像
~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 PATCH /v2/images/{image_id} 修改镜像
请求样例

::

    
    curl -s \
         -X PATCH `https://bj1.image.api.ustack.com/v2/images/{image_id}`_ \
         -H "Content-Type: application/openstack-images-v2.1-json-patch" \
         -H "X-Auth-Token: {token_id}" \
         -d '[
                {
                    "op": "add",
                    "path": "/login-user",
                    "value": "root"
                }
            ]'


返回样例 :


::

    HTTP/1.1 200
    
    {
      "id": "7b97f37c-899d-44e8-aaa0-543edbc4eaad",
      "name": "Ubuntu 12.10",
      "status": "queued",
      "visibility": "private",
      "protected": false,
      "tags": ["ubuntu", "12.10", "quantal"],
      "login_user": "root",
      "created_at": "2013-11-15T00:46:48Z",
      "updated_at": "2013-11-15T00:46:50Z",
      "file": "/v2/images/7b97f37c-899d-44e8-aaa0-543edbc4eaad/file",
      "self": "/v2/images/7b97f37c-899d-44e8-aaa0-543edbc4eaad",
      "schema": "/v2/schemas/image"
     }




删除镜像(主机快照)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
HTTP方法 URI路径 描述 DELETE /v2/images/{image_id} 删除镜像(主机快照)
请求样例

::

    
    curl -s \
         -X DELETE `https://bj1.image.api.ustack.com/v2/images/{image_id}`_ \
         -H "X-Auth-Token: {token_id}"


返回样例 :


::

    HTTP/1.1 204 No Content


