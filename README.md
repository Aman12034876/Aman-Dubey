# React Native Chat Widget by MSG91 # HelloSDK

<img src="https://user-images.githubusercontent.com/60983778/207020610-9eb32587-7878-4604-bdaf-88ec87f634f8.jpg" height="400">

## Getting started

Login or create account at MSG91 to use Hello SDK service.

After login at MSG91 follow below steps to get your hello chat widget configuration.
* From navigation drawer expand Manage > Inboxes > Select Inbox as Chat > Edit Widget.
* Configure your widget and copy the **helloConfig** object.

## Installing

``` 
npm install @msg91comm/react-native-hello-sdk
```

* Note - Please mention these dependencies in your package.json under dependencies.
``` 
 "cobrowse-sdk-react-native": "^2.13.0",
 "react-native-webview": "^11.23.1"
```
### Example 
```sh
"dependencies": {
    #"react": "18.1.0",
    #"react-native": "0.70.5",
    "@msg91comm/react-native-hello-sdk": "^1.0.0",
    "cobrowse-sdk-react-native": "^2.13.0",
    "react-native-webview": "^11.23.1"
  }
```

## Usage

### Widget Setup:
Import package in your Navigation container file or Screen:

```
import ChatWidget from '@msg91comm/react-native-hello-sdk';
```

Store your config object in a variable:

```  
var helloConfig = {
    widgetToken: "XXXXX",
    unique_id: <unique_id>, 
    name: <name>,  
    number: <number>,
    mail: <mail>
    }
```

Use Component ChatWidget and provide props as shown below.
```
return (
  <NavigationContainer>
    {/* Other Screens or Navigation Stacks */}
    <ChatWidget 
       customColor={'#FFFFFF'}
       statusBarStyle={'dark-content'}
       helloConfig={helloConfig}
    />
  </NavigationContainer>
  );
```
This widget is optimized for positioning using the "position: absolute" style property, allowing it to seamlessly overlay your entire app interface.

To ensure optimal visual integration and prevent interference with other absolute elements, we strongly recommend placing the chat widget within your navigation container. By positioning it at the bottom of the container, you can ensure a consistent and undisturbed layout for the widget.

Alternatively, if you are using the chat widget within a specific screen, it is advisable to position it at the bottom of that screen. This placement strategy ensures a cohesive user experience, as the chat widget remains easily accessible without obstructing other essential elements.

### Invoke Widget:
You can invoke this widget from anywhere in your app:
Just import DeviceEventEmitter from react native
```
  import { DeviceEventEmitter } from 'react-native';
```
and
```
  <Button title="Chat with us"
    onPress={() => DeviceEventEmitter.emit("HelloEvents", { status: true })}
  />
```

#### Properties

| Prop                         | Type         | value   | Description                                                           |
| ---------------------------- | ------------ | ------- | --------------------------------------------------------------------- |
| preLoaded                    | boolean      | true, false    | Loads widget on app initialization and keeps it's instance     |
| customColor                  | string       | 'hex-color-code'    | Sets StatusBar color and widget's background color             |
| statusBarStyle               | string       | 'default', 'light-content', 'dark-content' | Changes status bar content color   |


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
