Introduction
============

This repository contains a sample of documentation website, rendering is visible at http://docs.iot.bzh
This sample website relies on on http://github.com/iotbzh/webdocs-tools

Installing
==========

## dependencies webdoc-tools

Install webdocs-tools from https://github.com/iotbzh/webdocs-tools/blob/master/README.md

## install webdoc-sample

```
 git clone http://github.com/iotbzh/webdocs-sample
 cd webdocs-sample
```

## configure webdoc-sample

Edit webdoc-sample/conf/AppDefault
+ Default configuration consider that webdoc-tools & webdoc-sample site within the same parent directory.
+ If needed, update Doc_TOOLS to the right path.

## generate a 1st site from your template
```
 ./build --clean  # deleted all generated file if any
 ./build --fetch  --verbose # collect doc from github (fetch list in site/_tocs/*/fetch_files.yml)
 ./build --config --verbose # generate tocs and other configfile
 ./build --html --serve --watch --incremental # start a local webserver and wait for site source modification

  browser on http://localhost:4000

 ./build --push --verbose # push generated to production webserver (check conf/AppDefault 1st)
```

## start writing documentation

- the directory ./site holds your website contend
- site/* directories not prefixed with "_" represent en entry within the menu
- site/_* directory contains template, configuration, options
- site/_data is a special directory that hold both static and generated files to adjust page/site values within html pages
- site/_tocs/*/toc_VERSION_LANGUAGE.yml TOC(TableOfContend) and GitFetch definition (ex: appfw)
- site/_layouts holds page template 

- register at https://community.algolia.com/docsearch/ and update your apikey into conf/_config.yml


## bugs

```
 --fetch is asynchronous combining --fetch with other options will fail ./build --all --serve --watch
 --watch to automatically regenerate pages on markdown file, you should force "./build --configs" when changing TOC or versions.
```

