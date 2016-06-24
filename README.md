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

Edit webdoc-sample/conf/AppDefault
+ Default configuration consider that webdoc-tools & webdoc-sample site within the same parent directory.
+ If needed change GEM_FILE + Doc_TOOLS to point on the right path.

*** generate a 1st site from your template
```
 ./build.js --clean  # deleted all generated file if any
 ./build.js --fetch  --verbose # collect doc from github
 ./build.js --config --verbose # generate tocs and other configfile
 ./build.js --html --serve --watch  # start a local webserver and wait for site source modification

  browser on http://localhost:4000

 ./build --push --verbose # push generated to production webserver (check conf/AppDefault 1st)
```

*** start writing documentation

- the directory ./site holds your website contend
- site/* directories not prefixed with "_" represent en entry within the menu
- site/_* directory contains template, configuration, options
- site/_data is a special directory that hold both static and generated files to adjust page/site values within html pages
- site/_tocs/*/toc_VERSION_LANGUAGE.yml TOC(TableOfContend) and GitFetch definition (ex: appfw)
- site/_layouts holds page template 


*** bugs

- --fetch is asynchronous combining --fetch with other options will fail ./build.js --all --serve --watch
- --watch to automatically regenerate pages on markdown file, you should force "./build --configs" when changing TOC or versions.