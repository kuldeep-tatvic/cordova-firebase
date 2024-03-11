
# Angularjs using Cordova Firebase Plugin Setup

Implement Firebase Analytics in Angularjs project




## Firebase Analytics setup

Installation in root project

```bash
  $ cordova plugin add cordova-plugin-firebase-analytics
```

## Adding required configuration files

Cordova supports resource-file tag for easy copying resources files. Firebase SDK requires google-services.json on Android and GoogleService-Info.plist on iOS platforms.

 ```
 1> Put google-services.json and/or GoogleService-Info.plist into the root directory of your Cordova project
2> Add new tag for Android platform
```

```bash
<platform name="android">
    ...
    <resource-file src="google-services.json" target="app/google-services.json" />
</platform>
...
<platform name="ios">
    ...
    <resource-file src="GoogleService-Info.plist" />
</platform>
```

## Log Event

 ```
 logEvent(name, params)
 ```   

 #### Example
```
cordova.plugins.firebase.analytics.logEvent("my_event", {param1: "value1"});

 ```   

 ## setUserProperty

 Sets a user property to a given value. Be aware of automatically collected user properties.

 ```
 setUserProperty(name, value): Promise<void>
 ```   

 #### Example
```
cordova.plugins.firebase.analytics.setUserProperty("name1", "value1");

 ```   

  ## setUserId

Sets the user ID property. This feature must be used in accordance with Google's Privacy Policy.

 ```
setUserId(userId): Promise<void>
 ```   

 #### Example
```
cordova.plugins.firebase.analytics.setUserId("12345");
 ``` 

   ## setCurrentScreen

Sets the current screen name, which specifies the current visual context in your app. This helps identify the areas in your app where users spend their time and how they interact with your app.

 ```
setCurrentScreen(screenName): Promise<void>
 ```   

 #### Example
```
ccordova.plugins.firebase.analytics.setCurrentScreen("User dashboard");

 ``` 

 ### Device Info
 For the get device info like device name, appId, platform, and version etc.
 #### Example
 ```
   function onDeviceReady() {
            var vInfo = 'Device Name: ' + device.name + '\n' +
                'Device Cordova: ' + device.cordova + '\n' +
                'Device Platform: ' + device.platform + '\n' +
                'Device UUID/AppId: ' + device.uuid + '\n' +
                'Device Version: ' + device.version;
            console.log("here", vInfo);
        }
        
