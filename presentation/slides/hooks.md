## <span class="mysql-color">Hooks</span>

- Special scripts which could be added by __application__ and __plugin developers__ or even by your __own build system__ to customize cordova commands.
- __Special activities__: e.g. code formatting checker, etc.
- Use hooks, like __'before_build'__, and instruct cordova run the custom tool before every build.
- Hooks might be __related to your application activities__ or related to the __plugins__ of your application.
- These hooks can be __associated with all plugins__ within your application or be __specific to only one plugin__.

---

## <span class="mysql-color">Hook Types</span>

|[Hooks](https://cordova.apache.org/docs/en/latest/guide/appdev/hooks/index.html)|
|--------------- :| ------------ :| ------------:| ------------:|
|before_platform_add|after_platform_add|after_platform_rm|before_platform_ls|
|after_platform_ls|before_prepare|after_prepare|after_compile|
|before_deploy|before_build|after_build|before_emulate|
|after_emulate|before_run|after_run|before_serve|
|after_serve|before_clean|after_clean|pre_package|
|before_plugin_add|after_plugin_add|before_plugin_rm|after_plugin_rm|
|before_plugin_ls|after_plugin_ls|before_plugin_search|after_plugin_search|
|before_plugin_install|after_plugin_install|before_plugin_uninstall|

---

## <span class="mysql-color">Hook Definition</span>

config.xml using <hook> elements
```
<hook type="before_build" src="scripts/appBeforeBuild.bat" />
<hook type="before_build" src="scripts/appBeforeBuild.js" />
<hook type="before_plugin_install" src="scripts/appBeforePluginInstall.js" />

<platform name="android">
    <hook type="before_build" src="scripts/wp8/appAndroidBeforeBuild.bat" />
    <hook type="before_build" src="scripts/wp8/appAndroidBeforeBuild.js" />
    <hook type="before_plugin_install" src="scripts/wp8/appWP8BeforePluginInstall.js" />
    ...
</platform>

<platform name="windows">
    <hook type="before_build" src="scripts/windows/appWinBeforeBuild.bat" />
    <hook type="before_build" src="scripts/windows/appWinBeforeBuild.js" />
    <hook type="before_plugin_install" src="scripts/windows/appWinBeforePluginInstall.js" />
    ...
</platform>
```

---

## <span class="mysql-color">Hook When?</span>

 - Write a hook anytime you have a __build process that is tedious__, repetitive, or required to build your app.
 - If you need to __perform steps to build your app__ (copying icon files to various directories under platforms, for example).
 - In general, when you want to __automate steps__ to make your build process quicker, easier, and more repeatable.

---

## <span class="mysql-color">Order of Hooks execution</span>

Hook run serially in the following order:

 - Application hooks from __/hooks__;
 - Application hooks from __config.xml__;
 - Plugin hooks from __plugins/.../plugin.xml__.


---

## <span class="mysql-color">Script Interface</span>

 - Javascript
  ```
  module.exports = function(context) {
      ...
  }
  ```

---

## <span class="mysql-color">Context Object</span>

```
{
  "hook": "before_plugin_install",
  "scriptLocation": "c:\\script\\full\\path\\appBeforePluginInstall.js",
  "cmdLine": "The\\exact\\command\\cordova\\run\\with arguments",
  "opts": {
    "projectRoot":"C:\\path\\to\\the\\project",
    "cordova": {
      "platforms": ["android"],
      "plugins": ["plugin-withhooks"],
      "version": "0.21.7-dev"
    },
    "plugin": {
      "id": "plugin-withhooks",
      "pluginInfo": {
        ...
      },
      "platform": "android",
      "dir": "C:\\path\\to\\the\\project\\plugins\\plugin-withhooks"
    }
  },
  "cordova": {...}
}

```

---

## <span class="mysql-color">Scipts Async</span>

You can make your scipts async using Q:

```
module.exports = function(context) {
    var Q = context.requireCordovaModule('q');
    var deferral = new Q.defer();

    setTimeout(function(){
      console.log('hook.js>> end');
    deferral.resolve();
    }, 1000);

    return deferral.promise;
}

```

---

## <span class="mysql-color">Non-javascript Scipts</span>

 - Non-javascript scripts are run via __Node child_process spawn__ from the project's root directory.
 - Have the __root directory passes__ as the first argument.
 - All other options are passed to the script using __environment variables__ [Non-javascript](https://cordova.apache.org/docs/en/latest/guide/appdev/hooks/index.html#non-javascript).
 - Is __highly recommend__ writing your hooks __using Node.js__ so that they are cross-platform.

---

## <span class="mysql-color">Samples</span>

- Trace to the console __output the size of generated .apk__ file for Android platform

- Modify config.xml
  ```
  <hook type="after_build" src="scripts/afterBuild.js" />
  ```

- Create scripts/afterBuild.js file and add the implementation

---

## <span class="mysql-color">Samples Implementation</span>


```
module.exports = function(ctx) {
    // make sure android platform is part of build
    if (ctx.opts.platforms.indexOf('android') < 0) {
        return;
    }
    var fs = ctx.requireCordovaModule('fs'),
        path = ctx.requireCordovaModule('path'),
        deferral = ctx.requireCordovaModule('q').defer();

    var platformRoot = path.join(ctx.opts.projectRoot, 'platforms/android');
    var apkFileLocation = path.join(platformRoot, 'build/outputs/apk/android-debug.apk');

    fs.stat(apkFileLocation, function(err,stats) {
        if (err) {
                deferral.reject('Operation failed');
        } else {
            console.log('Size of ' + apkFileLocation + ' is ' + stats.size +' bytes');
            deferral.resolve();
        }
    });

    return deferral.promise;
};
```

---

## <span class="mysql-color">Samples Implementation</span>

 - Add android platform and execute build.

 ```
  cordova platform add android
  ..
  cordova build
  ..
  Size of app\platforms\android\build\outputs\apk\android-debug.apk
  is 1821193 bytes
 ```


---

## <span class="mysql-color">More examples</span>

 [Three hooks your Cordova/PhoneGap project needs](http://devgirl.org/2013/11/12/three-hooks-your-cordovaphonegap-project-needs/)

 
