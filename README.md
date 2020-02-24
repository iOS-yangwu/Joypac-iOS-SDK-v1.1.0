# Joypac行为数据上报iOS SDK 接入文档-v1.1.0
## 1. 下载SDK
## 2. 导入SDK
解压下载下来的SDK，获得 Joypac_Unity_SDK.framework 和 JoypacAdClient.cs 文件
#### 1. 将 Joypac_Unity_SDK.framework 文件放到 Plugins/iOS 路径下
#### 2. 将 JoypacAdClient.cs 文件放在 Script 路径下
## 3. SDK初始化
一般在游戏第一个场景里调用init方法，这样就完成了初始化SDK的工作。
     
    JoypacAdClient.Instance.InitSDK("yourAppID");
    
## 4.上报行为数据
在App内发生转化行为时，可以调用上报接口上报行为数据。上报API

    JoypacAdClient.Instance.eventLog("event_sort","event_type","event_position","event_extra");

命名规则

第一层级：事件分类 （event_sort）

第二层级：事件类型 （event_type）

第三层级：事件位置 （event_position）

拓展字段：如需要上传更多行为参数，可将参数编辑为json字符串，传入event_extra


例如：

1、阶段性行为

event_sort | event_type | event_position | 事件描述 
-|-|-|-
Stage|enter|x_y_z| 进入x类型y大关卡z小关卡
Stage|finish|x_y_z|x类型y大关卡z小关卡完成

    JoypacAdClient.Instance.eventLog("Stage","enter","x_y_z","");
    JoypacAdClient.Instance.eventLog("Stage","finish","x_y_z","");
    
2、广告

event_sort | event_type | event_position | 事件描述 
-|-|-|-
Ad|impression|x| x位置激励视频广告展示
  
    JoypacAdClient.Instance.eventLog("Ad","impression","x","{\"adType\":\"rewardVideo\"}");
    
3、用户行为

event_sort | event_type | event_position | 事件描述 
-|-|-|-
Behavior|click|setting| 设置按钮点击
  
    JoypacAdClient.Instance.eventLog("Behavior","click","setting","");

## 在线参数
在初始化SDK后，调用GetOnlineParameter()方法获取在线参数，参数以json字符穿的形式返回；在后台配置所需线参数后，十分钟后生效;

     JoypacAdClient.Instance.GetOnlineParameter();
          
## 分组
需要游戏分组时，调用 ReceiveGameGroupId(string cGroupId)方法，将游戏分组ID传递给SDK，SDK将分组信息上报服务端;

     JoypacAdClient.Instance.ReceiveGameGroupId("GroupA");


