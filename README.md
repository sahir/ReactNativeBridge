# React Native Bridge Android

Integration With Existing Apps Demo

# Usage 

# Emit events from React Native

#### JavaScript

```javascript
import { DeviceEventEmitter } from 'react-native';

	componentDidMount() {
		DeviceEventEmitter.addListener('qrCode', function(e: Event) {
			console.warn('qrCode : ', e);
		});
	}
```
#### Android:
```java
  public void sendEventQrCode() {
        String qrCode = "876398776";
        ReactContext reactContext = mReactInstanceManager.getCurrentReactContext();
        if (reactContext != null) {
            reactContext.getJSModule(DeviceEventManagerModule.RCTDeviceEventEmitter.class)
                    .emit("qrCode", qrCode);
        }
    }
```

# To expose a method to JavaScript a Java method must be annotated using @ReactMethod.

```java
  @ReactMethod
    public void showMessage(String message, Callback successCallback) {
        String finalMsg = message +" Test "+" final message";
        Toast.makeText(getReactApplicationContext(), finalMsg, Toast.LENGTH_LONG).show();
        successCallback.invoke(finalMsg);
    }
```


#### JavaScript

```javascript

import { NativeModules } from 'react-native';

var RCTToastAndroid = NativeModules.ToastCustomModule;

RCTToastAndroid.showMessage('Awesome', result => {
	console.warn(result);
});
```
