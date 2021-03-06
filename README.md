# OSLogStoreTest

Test app for evaluating if apps can access their own OSLog logs via [`OSLogStore`](https://developer.apple.com/documentation/oslog/oslogstore?language=objc) in iOS 14 and/or macOS 11.0.

## iOS 14

I can’t get it to work on an iOS device running iOS 14.0 beta 1–5. I can instantiate an `OSLogStore` and `OSLogEnumerator`, but the enumerator doesn’t provide any log entries (unless I’m holding it wrong), and I’m seeing this error message in the Xcode console:

```
Error Error Domain=NSCocoaErrorDomain Code=4099
"The connection to service on pid 0 named com.apple.OSLogService
was invalidated." UserInfo={NSDebugDescription=The connection to
service on pid 0 named com.apple.OSLogService was invalidated.}
```

When running in the iOS simulator, the error message is different:

```
Error Domain=OSLogErrorDomain Code=9
"Client lacks entitlement to perform operation"
UserInfo={NSLocalizedDescription=Client lacks entitlement
to perform operation, _OSLogErrorInternalCode=14}
```

Apple engineers have confirmed this is a bug. I hope it will get fixed before the final iOS 14 release.

* [Tweet by Brandon Titus](https://twitter.com/bjtitus/status/1276211162506424323)
* [Tweet by Quinn “The Eskimo!”](https://twitter.com/justkwin/status/1276271590360199172)

## macOS 11.0 Big Sur

The code works as expected in the macOS target.
