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
    
## Design
To add a design event also call the function:
    
    JoypacAdClient.Instance.eventLog(string parameter1,string parameter2, string parameter3,string parameter4);
    
    //click set button 
    JoypacAdClient.Instance.eventLog("Behavior","Click","Set","");
    
    //Launch application
    JoypacAdClient.Instance.eventLog("Behavior","launch","","");
   


## OnlineParameters
After initializing the SDK, to get a onlineParameters call the following function: 

     JoypacAdClient.Instance.GetOnlineParameters(string parameters);
     
The parameters are returned in the form of Json string.
          
## Reporting result check

Please pay attention to the output in Console.
Search `Joypac Event reporting parameters` to view reporting parameters;
Search `Joypac Event reporting results` to view reporting results;


