


物理机电源接口
====================

.. toctree::
   :maxdepth: 2
   :numbered:



概要
--------------------

控制物理机的开关机及重启动作，需要带上有效的 Token。


API规范
--------------------------

控制物理机电源API入口与API列表如下：


    * API入口: http://m.scloudm.com/
    * API列表:

+------------------+-------------------------------+------------+--------------------------------+
|  资源            |  操作                         |  HTTP方法  |  URI路径                       |
+==================+===============================+============+================================+
|  pm_act          |  对物理机电源操作             |  POST      |  /mana_api/pm_act              |
+------------------+-------------------------------+------------+--------------------------------+


先认证并获取新令牌(已可用), 使用该令牌执行获取动作
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

+------------+-------------------+-----------------+
|  HTTP方法  |  URI路径          |  描述           |
+============+===================+=================+
|  POST      |  /mana_api/pm_act |  物理机电源操作 |
+------------+-------------------+-----------------+

请求参数

+-----------------------+----------+--------------------------------------+
|  字段名               |  类型    |  描述                                |
+=======================+==========+======================================+
|  token                |  header  |  有效的 token                        |
+-----------------------+----------+--------------------------------------+
|  Sp-Agent             |  header  |  厂商类型如, 必须为scloudm           |
+-----------------------+----------+--------------------------------------+
|  act                  |  string  |  指定执行的动作 on;off;reset         |
+-----------------------+----------+--------------------------------------+
|  username             |  string  |  操作用户的用户名                    |
+-----------------------+----------+--------------------------------------+
|  snids                |  string  |  物理机序列号列表，逗号间隔          |
+-----------------------+----------+--------------------------------------+
|  tenant_id            |  string  |  租户ID                              |
+-----------------------+----------+--------------------------------------+
|  region               |  string  |  所属区域                            |
+-----------------------+----------+--------------------------------------+

请求样例

::


    curl  -i \
          -H 'X-Auth-Token: {token_id}' \
          -H 'Sp-Agent: scloudm' \
          -H 'Content-Type: application/json' \
          -X POST 'http://api.scloudm.com/mana_api/pm_act/{tenant_id}' \
          -d '{
            "act": "on|off|reset",
            "username": "liujiahua",
            "snids": "k432k234,a342fsd,234sdfg"
          }'



返回参数

+-------------------+-------------+-------------------------------------------------------------------------+
|  字段名           |  类型       |  描述                                                                   |
+===================+=============+=========================================================================+
|  msg              |  string     |  开关机或重启成功                                                       |
+-------------------+-------------+-------------------------------------------------------------------------+
|  code             |  int        |  返回码, 非200即为失败                                                  |
+-------------------+-------------+-------------------------------------------------------------------------+
|  detail           |   list      |  每台机器的结果                                                         |
+-------------------+-------------+-------------------------------------------------------------------------+


返回样例

::


        HTTP/1.0 200 OK
        Content-Type: application/json
        Content-Length: 537
        Server: Werkzeug/0.10.4 Python/2.7.5
        Date: Thu, 28 Jan 2016 05:53:28 GMT

        {
          "code": 400,
          "detail": [
            {
              "code": 400,
              "msg": "failed",
              "snid": "123"
            },
            {
              "code": 400,
              "msg": "failed",
              "snid": "1234"
            },
            {
              "code": 400,
              "msg": "failed",
              "snid": "4321"
            }
          ],
          "msg": "failed"
        }

