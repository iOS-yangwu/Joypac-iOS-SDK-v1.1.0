# Joypac Unity SDK 
## Download and Installation
### 1.Download SDK
### 2.Import SDK
package (Unity)
* In the Unity editor go to Assets > Import Package > Custom Package.
* Browse to the package location on your hard disk.
* Leave all the files checked and click Import.


> Check that the Unity environment has been already configured with the modules for the platforms you are targeting.
>
> If you are targeting iOS, this is a good time to go to File > Build Settings > iOS and make sure the iOS module is loaded and you can create iOS builds.

## Initialization
You need to manually initialize the SDK by calling `JoypacAdClient.Instance.InitSDK("yourAppID");` from your own GameObject.
When your initialization is complete, the SDK will generate a GameObject called `AdObject`,This GameObject is to accept callbacks.

## when to log envets?

Unity provides the GameObject methods called awake and start.
First all GameObjects get the awake call. When every awake is done then all GameObjects get the start call.

The execution order for each is not fixed.

Therefore when submitting events from GameObjects in Unity it is recommended to do this after (or inside) the start method. This will ensure everything is ready.

## Progression
To add a progression event call the following function:

    JoypacAdClient.Instance.eventLog(string progressionStatus,string progression01, string progression02,string progression03);
    
Field | Type | Required | Description
-|-|-|-
progressionStatus | string | yes | Status of added progression (start, complete, fail)
progression01 | string | yes | 1st progression (e.g. world01)
progression02 | string | no | 2nd progression (e.g. level01)
progression03 | string | no | If you need to upload more behavior parameters, you can edit the parameters as json strings and pass them in `progression03`



## 5.在线参数
在初始化SDK后，调用GetOnlineParameter()方法获取在线参数，参数以json字符穿的形式返回；在后台配置所需线参数后，十分钟后生效;

     JoypacAdClient.Instance.GetOnlineParameters();
          
## 6.分组
需要游戏分组时，调用 ReceiveGameGroupId(string cGroupId)方法，将游戏分组ID传递给SDK，SDK将分组信息上报服务端;

     JoypacAdClient.Instance.ReceiveGameGroupId("GroupA");

## 7.上报结果检查

请关注Console中的输出。
