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

`cmake -DPLUGIN_TYPE=filter -DPLUGIN_NAME=MyFilter <source-path>`


### Conan setup

http://docs.conan.io/en/latest/installation.html


#### with CLion

http://docs.conan.io/en/latest/integrations/clion.html
