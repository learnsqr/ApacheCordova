## <span class="mysql-color">Cordova</span>

Show a information page with help

```
cordova
cordova --help
```

---

## <span class="mysql-color">Cordova Create</span>

 - Create the __directory structure__ for the Cordova project in the specified path.

 ```
 cordova create path [id [name [config]]] [options]
 ```

|Value	|Description|
|----- :| ------:|
|path	|Directory which __should not already exist__. Cordova will create this directory.|
|id	|Default: __io.cordova.hellocordova__. __Reverse domain-style identifier__ that maps to id attribute of __widget element__ in config.xml.|
|name	|Default: __HelloCordova__. __Application's display title__ that maps __name element__ in config.xml file.|
|config	|JSON string whose key/values will be included in <path>/.cordova/config.json|

---

## <span class="mysql-color">Cordova Create commands</span>

```
cordova create myapp com.mycompany.myteam.myapp MyApp
cordova create myapp --link-to=../www
```

---

## <span class="mysql-color">Cordova Platform</span>

 - Manage cordova platforms - allowing you to __add, remove, update, list and check__ for updates.
 - __Add or remove__ affects the contents of the project's platforms directory.

```
cordova {platform | platforms} [
    add <platform-spec> [...] {--save | link=<path> | --fetch } |
    {remove | rm}  platform [...] {--save | --fetch}|
    {list | ls}  |
    check |
    save |
    update ]

```


---

## <span class="mysql-color">Cordova Platform options</span>

```
<platform-spec> : platform[@version] | path | url[#commit-ish]
```

|Value	|Description|
|----- :|-------- :|
|platform	|Platform name e.g. __android, ios, windows__ etc. to be added to the project. Every release of cordova __CLI pins a version__ for each platform. When no version is specified this version is used to add the platform.|
|version	|Major.minor.patch __version specifier__ using semver|
|path	|__Path to a directory__ or tarball containing a platform|
|url	|URL to a __git repository__ or tarball containing a platform|
|commit-ish	|__Commit/tag/branch reference__. If none is specified, 'master' is used|

---

## <span class="mysql-color">Cordova Platform commands</span>

```
cordova platform --help
cordova platform add android ios --save
cordova platform add android ios --save --fetch
cordova platform add android@^5.0.0 --save
cordova platform add https://github.com/myfork/cordova-android.git#4.0.0
cordova platform add ../android
cordova platform add ../cordova-android.tgz
cordova platform rm android --save
cordova platform rm android --save --fetch
cordova platform ls
cordova platform save
```

---

## <span class="mysql-color">Cordova Plugin</span>

The CLI will resolve the plugin based on:  

 - Spec given in the __command__ (e.g. cordova plugin add pluginID@version)
 - Spec saved in __config.xml__ (i.e. if the plugin was previously added with --save)
 - The latest plugin version published to __npm that the current project can support__ (only applies to plugins that list their Cordova dependencies in their package.json)
 - The __latest__ plugin version published to npm

```
cordova {plugin | plugins} [
    add <plugin-spec> [..] {--searchpath=<directory> | --noregistry | --link | --save | --browserify | --force | --fetch} |
    {remove | rm} {<pluginid> | <name>} --save --fetch |
    {list | ls} |
    search [<keyword>] |
    save |
]
```

---

## <span class="mysql-color">Cordova Plugin options</span>

```
<plugin-spec> : [@scope/]pluginID[@version]|directory|url[#commit-ish][:subdir]
```

|Value	|Description|
|----- :|-------- :|
|scope	|__Scope of plugin__ published as a scoped npm package|
|plugin	|Plugin id, of __plugin in npm__ registry or in --searchPath|
|version	|Major.minor.patch __version specifier__ using semver|
|directory	|__Directory__ containing plugin.xml|
|url	|Url to a __git repository__ containing a plugin.xml|
|commit-ish	|Commit/tag/__branch reference__. If none is specified, 'master' is used|
|subdir	|__Sub-directory to find plugin.xml__ for the specified plugin. (Doesn't work with --fetch option)|

---

## <span class="mysql-color">Cordova Plugin commands</span>

```
cordova plugin add cordova-plugin-camera cordova-plugin-file --save --searchpath ../plugins
cordova plugin add cordova-plugin-camera@^2.0.0 --save
cordova plugin add cordova-plugin-camera@^2.0.0 --fetch
cordova plugin add https://github.com/apache/cordova-plugin-camera.git#2.1.0:plugin --save
cordova plugin add ../cordova-plugin-camera
cordova plugin add ../cordova-plugin-camera.tgz --save
cordova plugin rm camera --save
cordova plugin rm camera --fetch
cordova plugin ls
```

---

## <span class="mysql-color">Conflicting Plugins</span>

 - May occur when adding plugins that use __edit-config__ tags in their __plugin.xml__ file.
 - __edit-config__ allows plugins to __add or replace__ attributes of XML elements
 - __Conflict detection__ has been implemented.
 - __An error will be thrown__ and the plugin won't be added.
 - To resolving
  - __Make changes to the affected plugins' plugin.xml__ so that they do not modify the same XML element.
  - Use the __--force__ flag to force add the plugin. Use with caution as it ignores the conflict detection and will overwrite all conflicts it has with other plugins.

---

## <span class="mysql-color">Cordova Prepare</span>

 - __Transforms config.xml__ metadata to platform-specific manifest files, copies icons & splashscreens, copies plugin files for specified platforms so that __the project is ready to build__ with each native SDK.


---

## <span class="mysql-color">Cordova Prepare command</span>

```
cordova prepare [<platform> [..]]
     [--browserify | --fetch]
```

 |Option	|Description|
 |------- :|--------- :|
 |< platform> [..]	|Platform name(s) to prepare. If not specified, all platforms are built.|
 |--browserify	|Compile plugin JS at build time using browserify instead of runtime.|
 |--fetch	|When restoring plugins or platforms, fetch will npm install the missing modules.|


---

## <span class="mysql-color">Cordova Compile</span>

 - __Is a subset of the cordova build__ command.
 - It __only performs the compilation__ step without doing prepare.
 - This stage is __useful to allow extending using hooks__.

```
cordova build [<platform> [...]]
    [--debug|--release]
    [--device|--emulator|--target=<targetName>]
    [--buildConfig=<configfile>]
    [--browserify]
    [-- <platformOpts>]
```

---

## <span class="mysql-color">Cordova Build</span>

 - Shortcut for __cordova prepare + cordova compile__ for all/the specified platforms.
 - Allows you to build the app for the specified platform.

```
cordova build [<platform> [...]]
    [--debug|--release]
    [--device|--emulator]
    [--buildConfig=<configfile>]
    [--browserify]
    [-- <platformOpts>]
```

---

## <span class="mysql-color">Cordova Build options</span>

|Option	|Description|
|------ :|--------- :|
| < platform> [..]	|Platform __name(s) to build__. If not specified, all platforms are built.|
|--debug	|Perform a __debug build__. Translates to __debug mode__.|
|--release	|Perform a __release build__. Translates to __release mode__ .|
|--device	|Build it __for a device__|
|--emulator	|Build it __for an emulator__.|
|--buildConfig=<configFile>	| __build.json__. Build configuration file used to specify paramaters to __customize the app build__ process esecially related to __signing the package__.|
|--browserify	|Compile __plugin JS__ at build time using __browserify instead of runtime__|
|< platformOpts>	|To provide __platform specific options__, include them after -- separator.|

---

## <span class="mysql-color">Cordova Build commands</span>

```
cordova build android windows --debug --device
cordova build android --release --buildConfig=..\myBuildConfig.json
cordova build android --release -- --keystore="..\android.keystore" --storePassword=android --alias=mykey
```

---

## <span class="mysql-color">Cordova Run</span>

 - _Prepares, builds, and deploys__ app on specified platform devices/emulators.
 - If a __device is connected__ it will be used, unless an __eligible emulator__ is already running.

```
cordova run [<platform> [...]]
    [--list | --debug | --release]
    [--noprepare] [--nobuild]
    [--device|--emulator|--target=<targetName>]
    [--buildConfig=<configfile>]
    [--browserify]
    [-- <platformOpts>]
```

---

## <span class="mysql-color">Cordova Run</span>

|Option	|Description|
|------ :| ------- :|
|< platform> [..]	|Platform __name(s) to run__. If not specified, all platforms are run.|
|--list	|Lists __available targets__.|
|--debug	|Deploy a __debug build__.|
|--release	|Deploy a __release build__|
|--noprepare	|__Skip preparing__ (available in Cordova v6.2 or later)|
|--nobuild	|__Skip building__|
|--device	|Deploy __to a device__|
|--emulator	|Deploy __to an emulator__|
|--target	|Deploy to a __specific target emulator/device__.|
|--buildConfig=<configFile>	| __build.json__ used to specify paramaters to __customize the app build__ process esecially related to __signing the package__.|
|--browserify	|Compile __plugin JS__ at build time using __browserify instead of runtime__|
|< platformOpts>	|To provide __platform specific options__, include them after -- separator.|


---

## <span class="mysql-color">Cordova Run commands</span>

```
cordova run android --release --buildConfig=..\myBuildConfig.json --target=Nexus_5_API_23_x86
cordova run android --nobuild
cordova run ios --device
cordova run ios --list
```

---

## <span class="mysql-color">Cordova Emulate</span>

 - Alias for __cordova run --emulator__.
 - Launches the emulator instead of device.

---

## <span class="mysql-color">Cordova Clean</span>

 - __Cleans the build artifacts__ for the specified platform, or all platforms by running platform-specific build cleanup.

```
cordova clean [<platform> [...]]
```

```
cordova clean android
```

---

## <span class="mysql-color">Cordova Requirements</span>

 - Checks and print out __all the requirements for platforms__ specified. Exits with __code 0__. On no-requirements exits with non-zero code.

 - Useful when __setting up a machine for building__ a particular platform.

```
cordova requirements android
```

---

## <span class="mysql-color">Cordova Info</span>

 - Print out useful __information helpful for submitting bug__ reports and getting help.
 - __Creates an info.txt__ file at the base of your project.

```
cordova info
```

---

## <span class="mysql-color">Cordova Serve</span>

 - Run a __local web server__ for www/ assets using specified port or default of 8000.
 - Access projects at: http://HOST_IP:PORT/PLATFORM/www

```
cordova serve [port]
```

---

## <span class="mysql-color">Cordova Telemetry</span>

 - Turns telemetry collection on or off.

```
cordova telemetry [on|off]
```

```
cordova telemetry on
cordova telemetry off
cordova build --no-telemetry
```


---

## <span class="mysql-color">Cordova Help</span>

 - Show syntax summary, or the help for a specific command.

```
cordova help [command]
cordova [command] -h
cordova -h [command]
```
