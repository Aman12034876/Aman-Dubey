# React Native Chat Widget by MSG91 # HelloSDK

<img src="https://user-images.githubusercontent.com/60983778/207020610-9eb32587-7878-4604-bdaf-88ec87f634f8.jpg" height="400">

## Getting started

Login or create account at MSG91 to use Hello SDK service.

After login at MSG91 follow below steps to get your hello chat widget configuration.
* From navigation drawer expand Manage > Inboxes > Select Inbox as Chat > Edit Widget.
* Configure your widget and copy the **helloConfig** object.

## Installation

```shell 
npm install @msg91comm/react-native-hello-sdk
```

* Note - Please mention these dependencies in your package.json under dependencies.
```sh 
 "cobrowse-sdk-react-native": "^2.13.0",
 "react-native-webview": "^11.23.1"
```
**Example** 
```sh
"dependencies": {
    "react": "18.1.0",
    "react-native": "0.70.5",
    "@msg91comm/react-native-hello-sdk": "^1.0.0",
    "cobrowse-sdk-react-native": "^2.13.0",
    "react-native-webview": "^11.23.1"
  }
```

## Usage

### Widget Setup:
Import package in your Navigation container file or Screen:

```javascript
import ChatWidget from '@msg91comm/react-native-hello-sdk';
```

Store your config object in a variable:

```javascript  
var helloConfig = {
    widgetToken: "XXXXX",
    unique_id: <unique_id>, 
    name: <name>,  
    number: <number>,
    mail: <mail>
    }
```
_Note:_ Ensure that `helloConfig` object does not contain any key with `null` or `undefined` value, else it will show loader.

Place the ChatWidget component at the bottom inside your Navigation container or Screen:
```javascript
return (
  <NavigationContainer>
    {/* Other Screens or Navigation Stacks... */}
    <ChatWidget
       preLoaded={true}
       customColor={'#FFFF00'}
       helloConfig={helloConfig}
    />
  </NavigationContainer>
  );
```
*Note:* This widget is optimized for positioning using the `position: 'absolute'` style property, allowing it to seamlessly overlay your entire app interface.

To ensure optimal visual integration and prevent interference with other absolute elements, we strongly recommend placing the chat widget within your navigation container. Position it at the bottom of the navigation container/screen, this will ensure that the chat widget remains easily accessible without obstructing other absolute elements in your app.

### Invoke Widget:
You can invoke this widget from anywhere in your app: 

Just import DeviceEventEmitter from react-native
```javascript
  import { DeviceEventEmitter } from 'react-native';
```
and
```javascript
  <Button title="Chat with us"
    onPress={() => DeviceEventEmitter.emit("HelloEvents", { status: true })}
  />
```
The Button onPress will launch the widget, and a Close Button is provided inside the widget for easy closure. When the widget is closed, it retains its current state, allowing it to be relaunched from the same state if the app is not killed.


#### Properties

| Prop                         | Type              | value   | Description                                                           |
| ---------------------------- | ----------------- | ------- | --------------------------------------------------------------------- |
| helloConfig                  | object (Required) | `{ widgetToken: "XXXXX", name: 'Aman', mail: 'example@xyz.com', ...}` | Configuration object from Hello dashboard |
| customColor                  | string            | `'hex-color-code'`    | Sets StatusBar color and widget's background color        |
| statusBarStyle               | string            | `'light-content'`, `'dark-content'` | Changes status bar content color              |
| preLoaded                    | boolean           | `true`, `false`    | `true` pre-loads widget content and keeps it ready to launch. On `false`, widget content loads when it is invoked  |

<br>
<br>
<br>

---

### Another Example
<br>
<br>

**If the widget is applied in a particular screen:**

Import ChatWidget and DeviceEventEmitter in your Screen:

```javascript
import { DeviceEventEmitter } from 'react-native';
import ChatWidget from '@msg91comm/react-native-hello-sdk';
```

Store your config object in a variable:

```javascript  
var helloConfig = {
    widgetToken: "XXXXX",
    unique_id: <unique_id>, 
    name: <name>,  
    number: <number>,
    mail: <mail>
    }
```

Place the ChatWidget component at the bottom of your Screen code:
```javascript
return (
  <SafeAreaView>
    {/* Your Screen Code... */}
    <Button title="Chat with us"
      onPress={() => DeviceEventEmitter.emit("HelloEvents", { status: true })}
    />
    {/* Your Screen Code... */}
    <ChatWidget
       preLoaded={true} 
       customColor={'#FFFF00'}
       helloConfig={helloConfig}
    />
  </SafeAreaView>
  );
```
<br>
<br>
<br>
 

## License

```
Copyright 2022 MSG91
Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
```
