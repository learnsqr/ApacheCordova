## <span class="mysql-color">Plugins</span>

 - Plugin.xml file defines the structure and settings required for your plugin.
 - It has several elements to provide details about your plugin.

```
<?xml version="1.0" encoding="UTF-8"?>
<plugin xmlns="http://apache.org/cordova/ns/plugins/1.0"
    xmlns:android="http://schemas.android.com/apk/res/android"
    id="my-plugin-id"
    version="1.0.2">
```

---

## <span class="mysql-color">Engines and Engine</span>

```
<engines>
  <engine name="my_custom_framework" version="1.0.0" platform="android" scriptSrc="path_to_my_custom_framework_version"/>
  <engine name="another_framework" version=">0.2.0" platform="ios|android" scriptSrc="path_to_another_framework_version"/>
  <engine name="even_more_framework" version=">=2.2.0" platform="*" scriptSrc="path_to_even_more_framework_version"/>
</engines>
```


---

## <span class="mysql-color">Name, Description, Author, Keywords, License</span>

```
<name>Foo</name>
<description>Foo plugin description</description>
<author>Foo plugin author</author>
<keywords>foo,bar</keywords>
<license>Apache 2.0 License</license>
```

---

## <span class="mysql-color">Assets</span>

---

## <span class="mysql-color">js-module</span>

---

## <span class="mysql-color">dependency</span>

---

## <span class="mysql-color">platform</span>

---

## <span class="mysql-color">platform</span>

---

## <span class="mysql-color">source-file</span>

---

## <span class="mysql-color">header-file</span>

---

## <span class="mysql-color">resource-file</span>

---

## <span class="mysql-color">config-file</span>

---

## <span class="mysql-color">edit-config</span>

---

## <span class="mysql-color">plugins-plist</span>

---

## <span class="mysql-color">lib-file</span>

---

## <span class="mysql-color">framework</span>

---

## <span class="mysql-color">info</span>

---

## <span class="mysql-color">hook</span>

---

## <span class="mysql-color">uses-permission</span>
