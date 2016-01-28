


监控服务
====================



API规范
--------------------------

监控服务API入口与API列表如下：


+ API入口:

区域 API入口 北京1区(bj1) `https://bj1.monitoring.api.ustack.com`_ 广东1区(gd1)
`https://gd1.monitoring.api.ustack.com`_

+ API列表:

资源 操作 HTTP方法 URI路径 监控指标(metrics) *获取监控指标列表* POST /v2/metrics
*获得某个资源的某个指标的监控数据* GET /v2/meters/{metric_name}/statistics 警报(alarms)
*创建警报* POST /v2/alarms *获取警报列表* GET /v2/alarms *更新指定警报* PUT
/v2/alarms/{alarm_id} *删除指定警报* DELETE /v2/alarms/{alarm_id}
*查看指定警报的变更记录* GET /v2/alarms/{alarm_id}/history


监控指标
------------------------



获取监控指标列表
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

自定义获取监控指标列表，根据metric_name的true或false来自定义获取哪些监控指标。
HTTP方法 URI路径 描述 POST /v2/metrics 获取监控指标列表
请求参数 :


+ 资源：要监控的目标
+ 监控指标：监控目标的监控指标
+ 监控指标的值是true或false，true表示要获得拥有该监控指标的所有资源，false不去获取拥有该监控指标的资源。

资源 监控指标 类型 单位 描述 云硬盘 volume_read_bytes_rate bool B/s 云硬盘读速率
volume_write_bytes_rate bool B/s 云硬盘写速率 volume_write_requests_rate
bool requests/s 云硬盘写请求速率 volume_read_requests_rate bool requests/s
云硬盘读请求速率 虚拟机 mem_util bool % 内存使用率 disk_write_rate bool B/s 磁盘写速率
cpu_util bool % cpu使用率 network_in_rate bool B/s 网络进流量 network_out_rate
bool B/s 网络出流量 disk_read_rate bool B/s 磁盘读速率 公网IP fip.bytes.in.rate
bool B/s 网络进流量 fip.bytes.out.rate bool B/s 网络出流量 fip.packages.in.rate
bool pkts/s 网络进流量 fip.packages.out.rate bool pkts/s 网络出流量
返回参数 :
字段名 类型 描述 resource_name string 资源名称 metric_name string 监控指标名称
resource_id string 资源id metric_unit string 监控指标单位 verbose_name string
监控指标详细信息 resource_type string 资源类型
请求样例

::

    
    curl -X POST `https://bj1.monitoring.api.ustack.com//v2/metrics`_ \
         -H "Content-Type: application/json" \
         -H "Accept: application/json" \
         -H "X-Auth-Token: f0033771695148ebb82c6af26b92b206" \
         -d '{
                "volume": {
                    "volume_read_bytes_rate": true,
                    "volume_write_bytes_rate": true,
                    "volume_write_requests_rate": false,
                    "volume_read_requests_rate": false
                },
                "instance": {
                    "mem_util": false,
                    "disk_write_rate": false,
                    "cpu_util": false,
                    "network_in_rate": false,
                    "network_out_rate": false,
                    "disk_read_rate": false
                }
            }'


返回样例


::

    [
        {
            "resource_name": "vol-1",
            "metric_name": "volume_read_bytes_rate",
            "resource_id": "493cce00-be55-4c15-b3cb-0130366d1848",
            "metric_unit": "B/s",
            "verbose_name": "Volume Read Bytes Rate",
            "resource_type": "volume"
        },
        {
            "resource_name": "vol-1",
            "metric_name": "volume_write_bytes_rate",
            "resource_id": "493cce00-be55-4c15-b3cb-0130366d1848",
            "metric_unit": "B/s",
            "verbose_name": "Volume Write Bytes Rate",
            "resource_type": "volume"
        }
    ]




获得某个资源的某个指标的监控数据
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

获得某个资源的某个指标的监控数据统计值，当绝对时间和相对时间都指定的时候，优先使用绝对时间。
HTTP方法 URI路径 描述 GET /v2/meters/{metric_name}/statistics
获得某个资源的某个指标的监控数据
请求参数
字段名 类型 描述 X-Auth-Token string 认证token period int 两个点之间的时间间隔 duration
string 相对时间，单位有m(minute), h(hour), d(day)，格式为：数字+单位，比如3h, 1d, 30d
q.field string 参数名, 目前用到的有resource_id和timestamp q.op string 比较符,
有”lt”, “gt”, “eq”等 q.value string field对应的参数值
返回参数

返回监控数据列表
字段名 类型 描述 period_start string 时间戳 count int period内数据点个数 min float 最小值
max float 最大值 avg float 平均值 sum float 总和 unit string 单位
请求样例

::

    
    curl -X GET "`https://bj1.monitoring.api.ustack.com//v2/meters/cpu_util/statistics?q.field=resource_id&q.op=eq&q.value=81ff638d-59b8-4850-960e-d019dc5403c3&duration=6h&period=300`_" \
         -H "Content-Type: application/json" \
         -H "Accept: application/json" \
         -H "X-Auth-Token: f0033771695148ebb82c6af26b92b206"
    
    curl -X GET "`https://bj1.monitoring.api.ustack.com//v2/meters/cpu_util/statistics?q.field=resource_id&q.op=eq&q.value=81ff638d-59b8-4850-960e-d019dc5403c3&q.field=timestamp&q.op=gt &q.value=2014-08-01T00:00:00&q.field=timestamp&q.op=lt&q.value=2014-08-07T00:00:00&period=3600`_" \
         -H "Content-Type: application/json" \
         -H "Accept: application/json" \
         -H "X-Auth-Token: f0033771695148ebb82c6af26b92b206"


返回样例


::

    [
        {
            "count": 3,
            "duration_start": "2014-08-07T03:56:36",
            "min": 0.07,
            "max": 0.07,
            "duration_end": "2014-08-07T04:02:37",
            "period": 300,
            "sum": 0.2,
            "period_end": "2014-08-07T04:01:01",
            "duration": 361,
            "period_start": "2014-08-07T03:56:01",
            "avg": 0.07,
            "groupby": null,
            "unit": "%"
        },
        {
            "count": 2,
            "duration_start": "2014-08-07T04:02:37",
            "min": 0.07,
            "max": 0.1,
            "duration_end": "2014-08-07T04:06:36",
            "period": 300,
            "sum": 0.16,
            "period_end": "2014-08-07T04:06:01",
            "duration": 239,
            "period_start": "2014-08-07T04:01:01",
            "avg": 0.08,
            "groupby": null,
            "unit": "%"
        }
    ]




警报
--------------------



创建警报
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

创建警报，警报有两种类型：threshold和combination。parameters的type指定要创建什么类型的alarm。
两种类型的alarm参数不一样，具体见下面的Parameters。
HTTP方法 URI路径 描述 POST /v2/alarms 创建警报
请求参数
字段名 类型 描述 X-Auth-Token string 认证token name string alarm的名字，必填
description string 描述 alarm_actions list(string)
当alarm被触发时，执行的动作，默认为[] type string alarm的类型，有两种：threshold和combination
enabled bool 开关alarm，默认是True
threshold_rule

阈值alarm被触发的规则。
字段名 类型 描述 meter_name string 监控指标 unit string 监控指标的单位 resource_metadata
dict(string: string) 和该alarm关联的资源的meta信息 query list(Query)
:用户查找某个具体资源,Query格式如下：: field: resource_id op: eq value: resource_id

period integer 两个数据点之间的时间间隔，默认是60s evaluation_periods integer
确定获取监控数据的时间范围，默认是1 comparison_operator string 确定怎么和阈值进行比较，有6个可选：lt,
le, eq, ne, ge, gt，默认是eq statistic string 监控数据的类型，有min, max, avg,
sum,count五种可选 threshold float 阈值
combination_rule

组合alarm被触发的规则
字段名 类型 描述 alarm_ids list(string) 要组合的alarm id列表 operator string
alarm列表之间的关系，有两个可选项：or, and
请求样例1，创建一个阈值alarm

::

    
    curl -X POST :bj1_monitoring`/v2/alarms` \
         -H "Content-Type: application/json" \
         -H "Accept: application/json" \
         -H "X-Auth-Token: f0033771695148ebb82c6af26b92b206" \
         -d '{
                "name": "Alarm1",
                "type": "threshold",
                "threshold_rule": {
                    "comparison_operator": "gt",
                    "evaluation_periods": 1,
                    "meter_name": "cpu_util",
                    "unit": "%",
                    "period": 300,
                    "query": [
                        {
                            "field": "resource_id",
                            "op": "eq",
                            "value": "3747689d-5891-46cd-b7e6-c622a3dc0cf9"
                        }
                    ],
                    "statistic": "avg",
                    "threshold": 70.0,
                    "resource_metadata": {
                      "resource_name": "vm1",
                      "resource_type": "instance"
                    }
                }
            }'


返回样例


::

    {
        "alarm_actions": [],
        "ok_actions": [],
        "name": "Alarm1",
        "timestamp": "2014-08-24T09:24:31.703705",
        "created_at": "2014-08-24T09:24:31.703705",
        "threshold_rule_string": "cpu_util > 70.0% during 1 * 300s",
        "enabled": true,
        "state": "insufficient data",
        "state_timestamp": "2014-08-24T09:24:31.703705",
        "threshold_rule": {
            "meter_name": "cpu_util",
            "evaluation_periods": 1,
            "period": 300,
            "resource_metadata": {
                "resource_name": "vm1",
                "resource_type": "instance"
            },
            "exclude_outliers": false,
            "statistic": "avg",
            "threshold": 70,
            "query": [
                {
                    "field": "resource_id",
                    "value": "3747689d-5891-46cd-b7e6-c622a3dc0cf9",
                    "op": "eq"
                },
                {
                    "field": "project_id",
                    "value": "1e9ea7f152b1480a987d297911588f7f",
                    "op": "eq"
                }
            ],
            "verbose_name": "CPU Utilization",
            "comparison_operator": "gt",
            "unit": "%"
        },
        "alarm_id": "d6637bd6-c06c-450a-8774-7e9dd0059521",
        "time_constraints": [],
        "insufficient_data_actions": [],
        "repeat_actions": false,
        "user_id": "6a3e429cfc7548948b688c61632af514",
        "project_id": "1e9ea7f152b1480a987d297911588f7f",
        "type": "threshold",
        "description": "Alarm when cpu_util is gt a avg of 70.0 over 300 seconds"
    }


请求样例2，创建一个组合alarm

::

    
    curl -X POST `https://bj1.monitoring.api.ustack.com//v2/alarms`_ \
         -H "Content-Type: application/json" \
         -H "Accept: application/json" \
         -H "X-Auth-Token: f0033771695148ebb82c6af26b92b206" \
         -d '{
              "name": "Alarm3",
              "type": "combination",
              "combination_rule": {
                "alarm_ids": [
                  "d6637bd6-c06c-450a-8774-7e9dd0059521",
                  "ed7c9ddc-f1b7-4fd9-9b9e-3b4c2173f4da"
                ],
                "operator": "or"
              }
            }'


返回样例


::

    {
        "alarm_actions": [],
        "ok_actions": [],
        "name": "Alarm3",
        "state": "insufficient data",
        "timestamp": "2014-08-24T12:43:58.042374",
        "created_at": "2014-08-24T12:43:58.042374",
        "enabled": true,
        "combination_rule": {
            "operator": "or",
            "alarm_ids": [
                "d6637bd6-c06c-450a-8774-7e9dd0059521",
                "ed7c9ddc-f1b7-4fd9-9b9e-3b4c2173f4da"
            ]
        },
        "state_timestamp": "2014-08-24T12:43:58.042374",
        "alarm_id": "b97317e9-7e4b-4abd-81f7-412502cd1d8f",
        "time_constraints": [],
        "insufficient_data_actions": [],
        "repeat_actions": false,
        "user_id": "6a3e429cfc7548948b688c61632af514",
        "project_id": "1e9ea7f152b1480a987d297911588f7f",
        "type": "combination",
        "description": "Combined state of alarms d6637bd6-c06c-450a-8774-7e9dd0059521 or ed7c9ddc-f1b7-4fd9-9b9e-3b4c2173f4da"
    }




获取警报列表
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

根据field，op，value来筛选特定的alarm列表。value是field字段对应的值。op是值大小比较，是可选字段。
HTTP方法 URI路径 描述 GET /v2/alarms 获取警报列表
请求参数
字段名 类型 描述 X-Auth-Token string 认证token q.field string “type” q.op
string “eq” q.value string “threshold” 或者 “combination”
请求样例

::

    
    curl -X GET ":bj1_monitoring`/v2/alarms?q.field=type&q.value=combination`" \
         -H "Content-Type: application/json" \
         -H "Accept: application/json" \
         -H "X-Auth-Token: f0033771695148ebb82c6af26b92b206"


返回样例


::

    [
        {
            "alarm_actions": [],
            "ok_actions": [],
            "name": "Alarm3",
            "state": "insufficient data",
            "timestamp": "2014-08-24T12:43:58",
            "created_at": "2014-08-24T12:43:58",
            "enabled": true,
            "combination_rule": {
                "operator": "or",
                "alarm_ids": [
                    "d6637bd6-c06c-450a-8774-7e9dd0059521",
                    "ed7c9ddc-f1b7-4fd9-9b9e-3b4c2173f4da"
                ]
            },
            "state_timestamp": "2014-08-24T12:43:58",
            "alarm_id": "b97317e9-7e4b-4abd-81f7-412502cd1d8f",
            "time_constraints": [],
            "insufficient_data_actions": [],
            "repeat_actions": false,
            "user_id": "6a3e429cfc7548948b688c61632af514",
            "project_id": "1e9ea7f152b1480a987d297911588f7f",
            "type": "combination",
            "description": "Combined state of alarms d6637bd6-c06c-450a-8774-7e9dd0059521 or ed7c9ddc-f1b7-4fd9-9b9e-3b4c2173f4da"
        }
    ]




更新指定警报
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

更新指定警报，参数同创建alarm，开关alarm也是调用这个接口。
HTTP方法 URI路径 描述 PUT /v2/alarms/{alarm_id} 更新指定警报
请求样例

::

    
    curl -X PUT `https://bj1.monitoring.api.ustack.com//v2/alarms/cd6ce631-bca2-4074-9fe2-174e009c3dd5`_ \
         -H "Content-Type: application/json" \
         -H "Accept: application/json" \
         -H "X-Auth-Token: f0033771695148ebb82c6af26b92b206" \
         -d '{
                "name": "ThresholdAlarm1",
                "description": "A threshold alarm",
                "type": "threshold",
                "threshold_rule": {
                    "comparison_operator": "gt",
                    "evaluation_periods": 3,
                    "meter_name": "cpu_util",
                    "unit": "%",
                    "period": 300,
                    "query": [
                        {
                            "field": "resource_id",
                            "op": "eq",
                            "value": "2a4d689b-f0b8-49c1-9eef-87cae58d80db"
                        }
                    ],
    
                    "statistic": "avg",
                    "threshold": 80.0
                },
                "alarm_actions": [
                    "`http://site:8000/alarm`_"
                ]
            }'


返回样例


::

    {
        "alarm_actions": [
            "http://site:8000/alarm"
        ],
        "ok_actions": [],
        "name": "ThresholdAlarm1",
        "timestamp": "2014-08-07T14:06:47.106014",
        "enabled": true,
        "state": "insufficient data",
        "state_timestamp": "2014-08-07T13:59:25.716050",
        "threshold_rule": {
            "meter_name": "cpu_util",
            "unit": "%",
            "evaluation_periods": 3,
            "period": 300,
            "statistic": "avg",
            "threshold": 80,
            "query": [
                {
                    "field": "resource_id",
                    "value": "2a4d689b-f0b8-49c1-9eef-87cae58d80db",
                    "op": "eq"
                },
                {
                    "field": "project_id",
                    "value": "9572fe04a03042a3813bcff72bfc547c",
                    "op": "eq"
                }
            ],
            "comparison_operator": "gt",
            "exclude_outliers": false
        },
        "alarm_id": "cd6ce631-bca2-4074-9fe2-174e009c3dd5",
        "time_constraints": [],
        "insufficient_data_actions": [],
        "repeat_actions": false,
        "user_id": "9296f416053e4923a73963db9a7cc4cb",
        "project_id": "9572fe04a03042a3813bcff72bfc547c",
        "type": "threshold",
        "description": "A threshold alarm"
    }




删除指定警报
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

删除指定警报，如果该alarm被其他alarm所包含的话，则不能删除
HTTP方法 URI路径 描述 DELETE /v2/alarms/{alarm_id} 删除指定警报
请求样例

::

    
    curl -X DELETE `https://bj1.monitoring.api.ustack.com//v2/alarms/cd6ce631-bca2-4074-9fe2-174e009c3dd5`_ \
         -H "Content-Type: application/json" \
         -H "Accept: application/json" \
         -H "X-Auth-Token: f0033771695148ebb82c6af26b92b206"




查看指定警报的变更记录
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

查看一个alarm的变更记录，查看的alarm由alarm_id唯一指定。
HTTP方法 URI路径 描述 GET /v2/alarms/{alarm_id}/history 查看指定警报的变更记录
返回参数 :
字段名 类型 描述 on_behalf_of string alarm创建者的user_id user_id string
user的uuid event_id string event的uuid timestamp string 时间戳 detail
string 更新的细节 alarm_id string alarm的uuid project_id string project的uuid
type string

+ “creation”: 创建alarm
+ “rule change”: rule发生改变
+ “state transition”: state发生变化
+ “on/off”: on的时候alarm.enabled = true，off的时候false
+ “deletion”: 删除alarm


请求样例

::

    
    curl -X GET `https://bj1.monitoring.api.ustack.com//v2/alarms/cd6ce631-bca2-4074-9fe2-174e009c3dd5/history`_ \
         -H "Content-Type: application/json" \
         -H "Accept: application/json" \
         -H "X-Auth-Token: f0033771695148ebb82c6af26b92b206"


返回样例


::

    [
        {
            "on_behalf_of": "9572fe04a03042a3813bcff72bfc547c",
            "user_id": "9296f416053e4923a73963db9a7cc4cb",
            "event_id": "662a3a01-3522-45c1-8b05-b5ac8f568c3f",
            "timestamp": "2014-08-07T14:09:47.331250",
            "detail": "",
            "alarm_id": "cd6ce631-bca2-4074-9fe2-174e009c3dd5",
            "project_id": "9572fe04a03042a3813bcff72bfc547c",
            "type": "deletion"
        },
        {
            "on_behalf_of": "9572fe04a03042a3813bcff72bfc547c",
            "user_id": "9296f416053e4923a73963db9a7cc4cb",
            "event_id": "c3d1bd6d-d53f-47a0-b0f7-8cc7b9a5adee",
            "timestamp": "2014-08-07T14:06:47.106014",
            "detail": "",
            "alarm_id": "cd6ce631-bca2-4074-9fe2-174e009c3dd5",
            "project_id": "9572fe04a03042a3813bcff72bfc547c",
            "type": "rule change"
        },
        {
            "on_behalf_of": "9572fe04a03042a3813bcff72bfc547c",
            "user_id": "9296f416053e4923a73963db9a7cc4cb",
            "event_id": "1738fe6d-54fd-4621-a6b2-a44f2cdcc7b6",
            "timestamp": "2014-08-07T13:59:25.716050",
            "detail": "",
            "alarm_id": "cd6ce631-bca2-4074-9fe2-174e009c3dd5",
            "project_id": "9572fe04a03042a3813bcff72bfc547c",
            "type": "creation"
        }
    ]


