## <span class="mysql-color">Version control</span>

It is recommended __not to check in__ platforms/ and plugins/ directories into version control as they are considered a build artifact.

You should __save the platform/plugin spec in the config.xml__ and they will be downloaded on the machine when __cordova prepare__ is invoked.

---

## <span class="mysql-color">Supported Platforms</span>

 - Android
 - iOS
 - Windows (8.1, Phone 8.1, UWP - Windows 10)
 - Blackberry10
 - Ubuntu
 - Browser

 - Deprecated Platforms
  - Amazon-fireos (use Android platform instead)
  - WP8 (use Windows platform instead)
  - Windows 8.0 (use older versions of cordova)
  - Firefox OS (use older versions of cordova)
