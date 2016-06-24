Introduction
============

This repository contains a sample of documentation website, rendering is visible at http://docs.iot.bzh/sample
This sample website relies on on http://github.com/iotbzh/webdoc-tools

Installing
==========

*** dependencies webdoc-tools

Follow webdoc-tools at https://github.com/iotbzh/webdoc-tools/blob/master/README.md

*** install webdoc-sample

* git clone http://github.com/iotbzh/webdoc-sample
* cd xxx/webdoc-sample; npm install

*** configure webdoc-sample

Edit webdoc-sample/conf/AppDefault and change GEM_FILE + Doc_TOOLS to point on the right path.
Default configuration concider that webdoc-tools + webdoc-sample site within the same parent directory and then GEM_FILE is located into webdoc-tools.

*** generate a 1st site from your template

* ./build.js --clean
* ./build.js --fetch
* ./build.js --config
* ./build.js --html --serve --watch
* point a browser on http://localhost:4000


*** start writing documentation

* the directory ./site holds your website contend
* directory not prefixed with "_" represent en entry within the menu
* directory prefixed with "_" contains template, configuration, options, ... used to format your site
* _data is a special directory that hold both static and generated files to ajust page & site values when generating html pages
* each entry menu with a subindex should have its TOC defined in _tocs/dirname/toc_VERSION_LANGUAGE.yml

*** bugs

* --fetch is asynchronous combining --fetch with other options will fail ./build.js --all --serve --watch
* --watch to automatically regenerate pages on markdown file, you should force "./build --configs" when changing TOC or versions.