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

    JoypacAdClient.Instance.eventLog("Start","","","");
    JoypacAdClient.Instance.eventLog("Start","World1","","");
    JoypacAdClient.Instance.eventLog("Start","World1","Level1","");
    JoypacAdClient.Instance.eventLog("Complete","World1","Level1","{\"score\":\"100\"}");
    

## OnlineParameters
After initializing the SDK, to get a onlineParameters call the following function: 

     JoypacAdClient.Instance.GetOnlineParameters(string parameters);
     
The parameters are returned in the form of Json string.
          
## Game grouping

When a game group is needed, call the ReceiveGameGroupId(string cGroupId) method to pass the game groupID to the SDK, and the SDK reports the group information to the server;

     JoypacAdClient.Instance.ReceiveGameGroupId("GroupA");

## Reporting result check


Please pay attention to the output in Console.
