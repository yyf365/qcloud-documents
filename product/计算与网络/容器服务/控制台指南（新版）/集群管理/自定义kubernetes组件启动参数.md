## 自定义kubernetes组件启动参数
### 注意事项
- 使用自定义kubernetes组件启动参数功能需 [提交工单](https://console.cloud.tencent.com/workorder/category) 进行申请。
- 自定义kubernetes组件启动参数功能属于租户/集群/可设置自定义参数维度开关， 您在提交工单时需提供账号ID/集群ID/需要设置的组件和组件的参数。
- 升级kubernetes集群版本，由于kubernetes跨版本后启动参数可能存在不兼容的情况，大版本升级不会保留您原集群版本的自定义kubernetes组件参数，您需要重新设置自定义的kubernetes的组件参数。


### 操作说明
#### 创建集群设置自定义kubenretes组件参数
1. <span id="step1">登录 [腾讯云容器服务控制台](https://console.cloud.tencent.com/tke2)，单击左侧导航栏中的【集群】。</span>
2. 在“集群管理”页面，单击集群列表上方的【新建】。
3. 在“创建集群”页面，高级设置-设置kubernetes自定义组件参数。如下图所示：
![](https://main.qcloudimg.com/raw/3c86b2fa8983484960f1168a3a56a9d0.png)

#### 设置节点的自定义kubelet参数
在创建集群节点设置页面/添加已有节点页面/新增节点池页面/新增节点页面均可设置节点的自定义kubelet参数：
![](https://main.qcloudimg.com/raw/71b4a0752521dea246713d21ed5105b3.png)


#### 集群升级设置自定义kubenretes组件参数
1. 登录 TKE 控制台，选择左侧导航栏中的【[集群](https://console.cloud.tencent.com/tke2/cluster)】，进入 “集群管理” 页面。
2. 选择需进行 Master Kubernetes 版本升级的集群 ID，进入该集群的 “Deployment” 页面。
3. 选择左侧导航栏中的【基本信息】，进入集群“基础信息”页面。
4. 在集群“基础信息”页面的集群信息模块，单击 Master 版本右侧的【升级】。同时设置kubernetes 组件启动参数。如下图所示：
![](https://main.qcloudimg.com/raw/ca9cd67172659ab3d6893e5671475554.png)
