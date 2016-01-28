快速入门
====================

.. toctree::
   :maxdepth: 2
   :numbered:



假设要通过API/CLI完成以一个简单任务：刷新缓存。

.. note::

    **获取 user_id 与 project_id ：**
    
    `Web管理面板`_ -> 个人设置(鼠标移至右上方用户名处出现) -> API 信息
    
    说明: 登录 `UOS Cloud`_ , 并进入 `Web管理面板`_ 后, 鼠标移动至界面右上方的 `用户名`_
    处,会出现下拉菜单,于显示的下拉菜单中选择 `个人设置`_ , 待跳转至个人设置页面后, 点击 `API 信息`_ , 即可查阅
    user_id 与 project_id 信息。

    .. image:: _static/images/user_project_id_guide.png



第一步：获得Token
--------------------------------------

API样例

::

    
    curl -i -X POST https://cdnapi.ztgame.com.com/cdn_api/tokens \
         -H "Content-Type: application/json"  \
         -H "Accept: application/json" \
         -d '{
                "auth": {
                    "passwordCredentials": {
                        "username": "admin",
                        "password": "123456"
                    }
                }
            }'


Response

::


   {
       "access": {
           "metadata": {
               "is_admin": 0, 
               "roles": []
           }, 
           "serviceCatalog": [], 
           "token": {
               "expires": "2015-11-25T11:47:30Z", 
               "id": "d71cf02b6a0e458aa91feab9013074e3", 
               "issued_at": "2015-11-24T11:47:30.170149"
           }, 
           "user": {
               "id": "cc13d74dfbc142a6909f050b5b589c83", 
               "name": "admin", 
               "roles": [], 
               "roles_links": [], 
               "username": "admin"
           }
       }
   } 

::

    
    X-Subject-Token: bb582f63af4f4e5782eb9a1499e87a1d


X-Subject-Token的值就是我们需要的Token，有了这个Token我们才可以继续到第二步，在随后的API请求中，均需要带上X-
Auth-Token请求头，其值为刚才获得的Token。



第二步：创建云主机
----------------------------------

在基础网络创建名为cloud_vm_test的ubuntu12.04，配置为compute-4，密钥为MacBookPro的一台云主机，对应
的cURL命令为

::

    
    curl -i -X POST https://bj1.compute.api.ustack.com/v2/0f1255df40374d02a23e1a6ceeaefec7/servers  \
         -H "X-Auth-Project-Id: uos_project" \
         -H "User-Agent: python-novaclient" \
         -H "Content-Type: application/json" \
         -H "Accept: application/json" \
         -H "X-Auth-Token: bb582f63af4f4e5782eb9a1499e87a1d" \
         -d '{
                "server": {
                    "name": "vm-cli",
                    "imageRef": "f1beda9e-0844-45de-aca8-72448bb50876",
                    "key_name": "MacBookPro",
                    "flavorRef": "c40bf599-a979-4404-8332-5a23f75a66cd",
                    "max_count": 1,
                    "min_count": 1,
                    "networks": [
                        {
                            "uuid": "4600c9b2-ebdb-4cf8-a7d5-6f8321a781c5"
                        }
                    ]
                }
            }'


返回202 Accepted，说明成功，并获得新创建云主机的UUID为{server_uuid}（最后一步需要用这到个变量），可以登陆Web
Console查看成功与否。



第三步：创建一个公网IP地址
--------------------------------------------

在BGP IP池中创建一个公网IP地址

::

    
    curl -i -X POST https://bj1.compute.api.ustack.com/v2/0f1255df40374d02a23e1a6ceeaefec7/os-floating-ips  \
         -H "X-Auth-Project-Id: uos_project" \
         -H "User-Agent: python-novaclient" \
         -H "Content-Type: application/json" \
         -H "Accept: application/json" \
         -H "X-Auth-Token: bb582f63af4f4e5782eb9a1499e87a1d" \
         -d '{
                "pool": "BGP"
            }'


返回200，说明成功，获得公网IP地址{fip_address}。



第四步：绑定公网IP地址到云主机
------------------------------------------------

获得第二步的云主机UUID{server_uuid}和公网IP地址{fip_address}之后，可以绑定公网IP地址到云主机，cURL命令
为

::

    
    curl -i -X POST https://bj1.compute.api.ustack.com/v2/0f1255df40374d02a23e1a6ceeaefec7/servers/{server_uuid}/action \
         -H "User-Agent: python-novaclient" \
         -H "Content-Type: application/json" \
         -H "Accept: application/json" \
         -H "X-Auth-Token: bb582f63af4f4e5782eb9a1499e87a1d" \
         -d '{
                "addFloatingIp": {
                    "address": "{fip_address}"
                }
            }'


.. warning::
   注意：把{project_id}, {server_uuid}和{fip_address}替换成对应的值。

任务达成！通过ssh root\@{fip_address}就可以直接访问云主机了，默认密码见镜像描述。


.. _Web管理面板: https://console.ustack.com/uos/overview
.. _UOS Cloud: https://console.ustack.com/login
.. _用户名: #
.. _个人设置: #
.. _API 信息: #

