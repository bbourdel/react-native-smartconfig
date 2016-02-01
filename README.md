[TOC]

## Description

This is link:https://github.com/facebook/react-native[react-native] wrapper for link:https://github.com/EspressifApp[ESP8266 ESPTOUCH Smart config]

## Featues
* Support both IOS and Android
* React Native Promise support
* Fast way to do configure wifi network for IOT device

## Getting started
### Mostly automatic install
1. `npm install rnpm --global`
2. `npm install react-native-smartconfig@latest --save`
3. `rnpm link react-native-smartconfig`

### Manual install
#### iOS
1. `npm install react-native-smartconfig@latest --save`
2. In XCode, in the project navigator, right click `Libraries` ➜ `Add Files to [your project's name]`
3. Go to `node_modules` ➜ `react-native-smartconfig` and add `RCTSmartconfig.xcodeproj`
4. In XCode, in the project navigator, select your project. Add `libRCTSmartconfig.a` to your project's `Build Phases` ➜ `Link Binary With Libraries`
5. Click `RCTSmartconfig.xcodeproj` in the project navigator and go the `Build Settings` tab. Make sure 'All' is toggled on (instead of 'Basic'). In the `Search Paths` section, look for `Header Search Paths` and make sure it contains both `$(SRCROOT)/../../react-native/React` - mark  as `recursive`.
5. Run your project (`Cmd+R`)


#### Android

1. `npm install react-native-smartconfig@latest --save`
2.  Modify the ReactInstanceManager.builder() calls chain in `android/app/main/java/.../MainActivity.java` to include:

```javascript
import com.tuanpm.RCTSmartconfig; // import


.addPackage(new RCTSmartconfigPackage()) //for older version

new RCTSmartconfigPackage()           // for newest version of react-native
```

3. Append the following lines to `android/settings.gradle` before `include ':app'`:

```java
include ':react-native-smartconfig'
project(':react-native-smartconfig').projectDir = new File(rootProject.projectDir, 	'../node_modules/react-native-smartconfig/android')
```

4. Insert the following lines inside the dependencies block in `android/app/build.gradle`, don't missing `apply plugin:'java'` on top:

```java
compile project(':react-native-smartconfig')
```

Notes:

```java
dependencies {
  compile project(':react-native-smartconfig')
}
```

[WARNING]
But not like this

```java
buildscript {
    ...
    dependencies {
      compile project(':react-native-smartconfig')
    }
}
```

## Usage

* Normal
```javascript
var Smartconfig = require('react-native').NativeModules.Smartconfig;
Smartconfig.start({
  type: 'esptouch', //or airkiss, now doesn't not effect
  ssid: 'wifi-network-ssid',
  bssid: 'filter-device', //null if not need to filter
  password: 'wifi-password',
  timeout: 50000 //now doesn't not effect
}).then(results) {
  //Array of device success do smartconfig
  console.log(results);
  /*[
    {
      'bssid': 'device-bssi1', //device bssid
      'ipv4': '192.168.1.11' //local ip address
    },
    {
      'bssid': 'device-bssi2', //device bssid
      'ipv4': '192.168.1.12' //local ip address
    },
    ...
  ]*/
}.catch(error) {

};

Smartconfig.stop(); //interrupt task
```

## Todo

* [ ] Support automatic get current wifi network ssid
* [ ] Set timeout effect
* [ ] Support airkiss

## LICENSE

```
  The MIT License (MIT)

  Copyright (c) 2015 <TuanPM> https://twitter.com/tuanpmt

  Permission is hereby granted, free of charge, to any person obtaining a copy
  of this software and associated documentation files (the "Software"), to deal
  in the Software without restriction, including without limitation the rights
  to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
  copies of the Software, and to permit persons to whom the Software is
  furnished to do so, subject to the following conditions:

  The above copyright notice and this permission notice shall be included in all
  copies or substantial portions of the Software.

  THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
  IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
  FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
  AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
  LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
  OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
  SOFTWARE.
```