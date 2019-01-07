# Part 4 Load Balance 测试报告  

## 测试环境  

|项目|说明|
|-----|-----|
|操作系统|Ubuntu 16.04|
|CPU核数|2|
|内存容量|2G|
备注：本次测试在虚拟机中进行。

##部署的服务

本次测试在集群中一共部署了X个service，包括前端：XX，后端：XX，数据库：MySQL。具体如下图：  

每个service的对应的Deployment如下图：  

##测试方法  
使用Jmeter，设置XX个线程，对于不同数量的replica进行测试，对前端的XX页面持续发送请求XX秒。
结果如下表：  
|Replica|Samples|Avg|Min|Max|Error|Throughput|Receive speed|Send speed|
|-----|-----|-----|-----|-----|-----|-----|------|-----|

##测试结果分析  

1. Replica数目与Throughput的关系  

如上图，replica在开始增加时，throughput明显获得提升，但当replica过多，分发请求和维护造成的开销导致了throughput的下降，因此replica也不是越多越好的。

2. Replica数目与Response Time的关系  

如上图，replica刚开始的增多使得总体的response time降低了，但后续因为与上面同样的原因，response time后来还反弹了。

3. Replica数目与出错率的关系  

如上图，replica数目与出错率的关系总体上和之前两个指标类似。


综上所述，对于一个部署方案，replica的数目不是越多越好，要根据当前方案选择相应的数目。