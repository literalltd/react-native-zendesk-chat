# react-native-zendesk-chat

Simple module that allows displaying Zopim Chat from Zendesk for React Native.

## Known issues

I could not find how to make the import for iOS work properly since I'm using Cocoapods for Zendesk, if you have a suggestion that would be great.

## Getting started

Follow the instructions to install the SDK for [iOS](https://developer.zendesk.com/embeddables/docs/ios-chat-sdk/gettingstarted) and [Android](https://developer.zendesk.com/embeddables/docs/android/gettingstarted).

### Manual install
#### iOS
1. `npm install react-native-zendesk-chat --save`
2. In Xcode, drag and drop `node_modules/react-native-zendesk-chat/RNZendeskChat.m` and `node_modules/react-native-zendesk-chat/RNZendeskChat.h` into your project.
3. Configure `ZDCChat` in `AppDelegate.m`:

```
[ZDCChat configure:^(ZDCConfig *defaults) {
  defaults.accountKey = "YOUR_ZENDESK_ACCOUNT_KEY";
}];
```

#### Android
1. `npm install react-native-zendesk-chat --save`
2. Open up `android/app/main/java/[...]/MainActivity.java`
  - Add `import com.taskrabbit.zendesk.*;` to the imports at the top of the file
  - Add `new RNZendeskChatPackage(this)` to the list returned by the `getPackages()` method

3. Append the following lines to `android/settings.gradle`:

```
include ':react-native-zendesk-chat'
project(':react-native-zendesk-chat').projectDir = new File(rootProject.projectDir,	'../node_modules/react-native-zendesk-chat/android')
```

4. Insert the following lines inside the dependencies block in `android/app/build.gradle`:

```
compile project(':react-native-zendesk-chat')
```

5. Configure `ZopimChat` in `android/app/main/java/[...]/MainActivity.java`

```
ZopimChat.init("YOUR_ZENDESK_ACCOUNT_KEY").build();
```

## Usage

In your code add `import ZendeskChat from 'react-native-zendesk-chat';`.

```
ZendeskChat.startChat({
  name: user.full_name,
  email: user.email,
  phone: user.mobile_phone,
});
```

## TODO

* Allow setting form configuration from JS
* Add examples
