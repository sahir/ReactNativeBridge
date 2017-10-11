# React Native Bridge Android

Integration With Existing Apps Demo

React Native works well for adding a single view or user flow to existing native applications. With a few steps, you can add new React Native based features, screens, views, etc.


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
