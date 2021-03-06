# react-native-crosswalk-webview
Webview Crosswalk for React Native (Android)

### Installation

* From the root of your React Native project

```shell
npm install --save react-native-crosswalk-webview
mkdir android/app/libs
```
* Download and Copy file [xwalk_core_library-16.46.448.10.aar] (https://github.com/grovertb/react-native-crosswalk-webview-example/raw/master/android/app/libs/xwalk_core_library-17.46.448.10.aar) in:
```shell
node_modules/react-native-crosswalk-webview/libs/
android/app/libs/
```

### Include module in your Android project

* In `android/setting.gradle`

```gradle
...
include ':CrosswalkWebView', ':app'
project(':CrosswalkWebView').projectDir = new File(rootProject.projectDir, '../node_modules/react-native-crosswalk-webview')
```

### Include libs in your Android project

* In `android/build.gradle`

```gradle
...
allprojects {
    repositories {
        mavenLocal()
        jcenter()

        flatDir {          // <--- add this line
            dirs 'libs'    // <--- add this line
        }                  // <--- add this line
    }
}
```

* In `android/app/build.gradle`

```gradle
...
dependencies {
  ...
  compile (name: "xwalk_core_library-17.46.448.10", ext: "aar")    // <--- add this line
  compile project(':CrosswalkWebView')                             // <--- add this line
}
```

* Register package in MainActivity.java

```java
import com.grovertb.react.crosswalk.webview.CrosswalkWebViewPackage;    // <--- add this line

public class MainActivity extends ReactActivity {
  ......

  @Override
  protected List<ReactPackage> getPackages() {
    return Arrays.<ReactPackage>asList(
        new MainReactPackage(),
        new CrosswalkWebViewPackage(this)    // <--- add this line
    );
  }

  ......

}
```
## EXAMPLE
   * [Example](https://github.com/grovertb/react-native-crosswalk-webview-example)
## License
MIT
