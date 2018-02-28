PDAL Scaffolding
===

Using CMake to scaffold PDAL plugins

### Supported plugins

- `filter`: https://www.pdal.io/development/writing-filter.html


### Options

- `PLUGIN_TYPE`: the type of plugin (`kernel`,`filter`,`reader`,`writer`)
- `PLUGIN_NAME`: the name of the plugin
- `TARGET_DIR`: where to write the project


### Usage

The easiest way to run is with the `new-plugin` script which will collect the required inputs and initialize the project.

```
#! ./new-plugin 
plugin type [F/k/r/w]: f
filter name: MyFilter
output directory [/tmp/MyFilter]: 
filter namespace [none]: jw3
enable matlab support [y/N]: y

scaffolding from /tmp/MyFilter/cmake-build-scaffolding ...
type: filter
name: MyFilter
namespace: jw3
destination: /tmp/MyFilter
additional args:  -DWITH_MATLAB=ON

Press enter to perform scaffolding... 
Scaffolding complete

initialize conan for clion [y/N]: y
Conan initialized in /tmp/MyFilter/cmake-build-debug

initialized git repository in /tmp/MyFilter
scaffolding complete, /tmp/MyFilter/cmake-build-scaffolding can be deleted
```

Alternatively you can run `cmake` directly

`cmake -DPLUGIN_TYPE=filter -DPLUGIN_NAME=MyFilter <source-path>`

see the `new-plugin` script for an up to date example.

### Conan setup

http://docs.conan.io/en/latest/installation.html


#### with CLion

http://docs.conan.io/en/latest/integrations/clion.html
