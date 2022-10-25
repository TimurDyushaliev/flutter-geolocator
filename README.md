# Flutter geolocator plugin

This repository forked from the [geolocator plugin][1] created by [Baseflow][2], but with **two methods added**:
1) [`setBackgroundExecution`][3] - to enable/disable (depending on its `enable` parameter) background location fetching. *Currently works only on iOS. This method does nothing on other platforms. On Android maybe you wish to use the [`foreground services`][4] to be able to continue fetching locations in background.*
2) [`isBackgroundExecutionEnabled`][5] - to check if background location fetching is enabled. *As the [`setBackgroundExecution`][3] works only on iOS, so it always returns `false` for non iOS platforms.*

<br />

To be able to use the [`setBackgroundExecution`][3] method you must add the `location` value to the [`UIBackgroundModes`][6] array inside the `Info.plist` file. It can be done in two ways:

1) **Using Xcode**

Open your project with Xcode, then navigate to the `Signing & Capabilities` of your app target and make sure the `Location updates` is enabled as shown in the image below:

![image](https://docs-assets.developer.apple.com/published/9cba7a007f/5108b1a8-8cd2-4b56-83d9-09f8e9fa1ee7.png)




2) **Manually**

Open the `Info.plist` file (*path: `{your_project}/ios/Runner/Info.plist`*), then scroll down to the `UIBackgroundModes` array and add the `location` value as shown in the image below:

<img width="344" alt="Screen Shot 2022-10-17 at 16 23 21" src="https://user-images.githubusercontent.com/75716994/196155584-a657d977-b67f-4425-a498-42bdbc3c13ff.png">

<br />

***Important:*** Calling the [`setBackgroundExecution`][3] method on iOS without the `Location updates` enabled as shown above - will crash your app!


[1]: https://github.com/Baseflow/flutter-geolocator
[2]: https://github.com/Baseflow
[3]: ./geolocator/lib/geolocator.dart#L49
[4]: https://developer.android.com/guide/components/foreground-services
[5]: ./geolocator/lib/geolocator.dart#L61
[6]: https://developer.apple.com/documentation/bundleresources/information_property_list/uibackgroundmodes
