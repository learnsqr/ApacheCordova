## <span class="mysql-color">Apache Cordova</span>

Apache Cordova is an __open-source__ mobile development framework. It allows you to use __standard web technologies__ - HTML5, CSS3, and JavaScript for __cross-platform__ development. Applications execute __within wrappers__ targeted to each platform, and rely on __standards-compliant API__ bindings to access each device's capabilities such as sensors, data, network status, etc.

---

## <span class="mysql-color">Architecture</span>

![architecture](../../assets/cordova/cordovaapparchitecture.png)

---

## <span class="mysql-color">Web View</span>

The Cordova-enabled WebView may provide the application with its __entire user interface__.


---

## <span class="mysql-color">Web App</span>

This is the part where your __application code resides__. The application itself is __implemented as a web page__, by default a local file named index.html, that references __CSS, JavaScript, images, media files, or other resources__ are necessary for it to run. The app __executes in a WebView__ within the native __application wrapper__, which you distribute to app stores.

 - A very crucial file - __config.xml__ provides information about the app and specifies parameters __affecting how it works__.

---

## <span class="mysql-color">Plugins</span>

They provide an __interface for Cordova and native components__ to communicate with each other and __bindings to standard device APIs__. This enables you to __invoke native code from JavaScript__.

---

## <span class="mysql-color">Core Plugin</span>

Provide your application to __access device capabilities__ such as battery, camera, contacts, etc.  

[Core Plugins](https://cordova.apache.org/docs/en/latest/guide/support/index.html#core-plugin-apis)

---

## <span class="mysql-color">Third-party plugins</span>

Provide additional bindings to features __not necessarily available on all platforms__.  
[Plugin search](https://cordova.apache.org/plugins/) /
[npm search](https://www.npmjs.com/search?q=ecosystem%3Acordova)

 - You can __develop your own__ plugins

---

## <span class="mysql-color">Important</span>
 - Any plugins you desire, even the core plugins, must be __explicitly added__.
 - Cordova __does not provide any UI widgets__ or MV* frameworks.

---

## <span class="mysql-color">Development Paths</span>
Two basic workflows to create a mobile app. While you can often use either workflow to accomplish the same task, they each offer advantages:

 - Cross-platform
 - Platform-centered

__Once you switch from the CLI-based workflow to one centered around the platform-specific SDKs and shell tools, you can't go back.__


---

## <span class="mysql-color">Cross-platform </span>

 - __Cross-platform (CLI) workflow__: Use this workflow if you want your app to run on as many different mobile operating systems as possible, with little need for platform-specific development.
  - The CLI is a __high-level tool__ that allows you to __build projects for many platforms at once__.
  - The cross-platform workflow __is recommended__.

---

## <span class="mysql-color">Platform-centered</span>

 - __Platform-centered workflow__: Use this workflow if you want to focus on __building an app for a single platform__ and need to be able to modify it at a lower level.
  - To __mix custom native components__ with web-based Cordova components
  - If you need __to modify the project within the SDK__.
  - If you need the __greater control__ the SDK provides.


---

## <span class="mysql-color">Install Apache Cordova</span>

The installation of Cordova will differ __depending on the workflow__ above you choose.
