PDAL Scaffolding
===

Using CMake to scaffold PDAL plugins

### Supported plugins

- `filter`: https://www.pdal.io/development/writing-filter.html


### Options

- `PLUGIN_TYPE`: the type of plugin (`kernel`,`filter`,`reader`,`writer`)
- `PLUGIN_NAME`: the name of the plugin
- `TARGET_DIR`: where to write the project
- `CXX_STANDARD`: CXX standard (`11`, `14`, `17`)
- `CONANFILE`: path to an external conanfile
- `WITH_MATLAB`: add matlab library paths to the project

### Usage

The easiest way to run is with the `new-plugin` script which will collect the required inputs and initialize the project.

```
#! ./new-plugin
plugin type [F/k/r/w]: f
filter name: MyPlugin
output directory [/tmp/MyPlugin]: 
cxx standard [(11)/14/17]: 14
filter namespace [none]: jw3
external conanfile [None/t]: /tmp/conanfile.txt
enable matlab support [y/N]: y
initialize conan for clion [y/N]: y

Scaffolding options
===================
type: filter
name: MyPlugin
namespace: jw3
cxx standard: 14
destination: /tmp/MyPlugin
clion conan init: y
plugin version: 1.0.0
additional args:  -DCONANFILE=/tmp/conanfile.txt -DWITH_MATLAB=ON

press enter to perform scaffolding... 

Conan initialized in /tmp/MyPlugin/cmake-build-debug

scaffolding complete, /tmp/MyPlugin/cmake-build-scaffolding can be deleted
```

Alternatively you can run `cmake` directly

`cmake -DPLUGIN_TYPE=filter -DPLUGIN_NAME=MyFilter <source-path>`

see the `new-plugin` script for an up to date example.


#### Notes on the options

The library version is implemented in the scaffolding but not exposed in `new-plugin`.

The conanfile line is a little hard to decipher

`external conanfile [None/t]:`

The options here are 

- nothing and it will use the default conanfile from common
- `t` and it will use the git-ignored conanfile.txt.template from scaffolding root
- enter a path and it will use that

This is ugly, an pragmatic, hack.  Will clean up later.


### Conan setup

http://docs.conan.io/en/latest/installation.html


#### with CLion

http://docs.conan.io/en/latest/integrations/clion.html


### development

Use the `test-build` script to run through a narrow example of scaffolding and building.
