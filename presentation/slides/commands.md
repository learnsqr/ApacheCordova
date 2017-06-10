## <span class="mysql-color">Cordova</span>

Show a information page with help

---

## <span class="mysql-color">Cordova Platform</span>

 - Manage cordova platforms - allowing you to __add, remove, update, list and check__ for updates.
 - __Add or remove__ affects the contents of the project's platforms directory.

|Value	|Description|
|----- :|-------- :|
|platform	|Platform name e.g. __android, ios, windows__ etc. to be added to the project. Every release of cordova __CLI pins a version__ for each platform. When no version is specified this version is used to add the platform.|
|version	|Major.minor.patch __version specifier__ using semver|
|path	|__Path to a directory__ or tarball containing a platform|
|url	|URL to a __git repository__ or tarball containing a platform|
|commit-ish	|__Commit/tag/branch reference__. If none is specified, 'master' is used|

---

## <span class="mysql-color">Cordova Platform 2</span>

```
- cordova platform --help
- cordova platform add android ios --save
- cordova platform add android ios --save --fetch
- cordova platform add android@^5.0.0 --save
- cordova platform add https://github.com/myfork/cordova-android.git#4.0.0
- cordova platform add ../android
- cordova platform add ../cordova-android.tgz
- cordova platform rm android --save
- cordova platform rm android --save --fetch
- cordova platform ls
- cordova platform save
```


---

## <span class="mysql-color">Cordova Plugin</span>

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

## <span class="mysql-color">Cordova Plugin 2</span>
