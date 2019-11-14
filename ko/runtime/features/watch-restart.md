---
layout: page
title: Watch & Restart | Features | PM2 Documentation
description: Watch & Restart application on file change
lang: en
section: runtime
permalink: "/en/runtime/features/watch-restart/"
---

## Auto restart apps on file change

PM2 can automatically restart your application when a file is modified in the current directory or its subdirectories:

```bash
pm2 start app.js --watch
```

If `--watch` is enabled, stopping it won't stop watching:

- `pm2 stop 0` will not stop watching
- `pm2 stop 0 --watch` will stop watching

Restart with `--watch` will toggle the `watch` parameter.

To watch specific paths, please use a [Ecosystem File](/doc/en/runtime/guide/ecosystem-file/), `watch` can take a string or an array of paths. Default is `true`:

```javascript
module.exports = {
  apps: [{
    script: "app.js",
    watch: ["server", "client"],
    // Delay between restart
    watch_delay: 1000,
    ignore_watch : ["node_modules", "client/img"],
    watch_options: {
      "followSymlinks": false
    }
  }]
}
```

Notes:

`watch_options` is an object that will replace options given to chokidar. Please refer to [chokidar documentation](https://github.com/paulmillr/chokidar#api) for the definition.

PM2 is giving chokidar these Default options:

```
var watch_options = {
  persistent    : true,
  ignoreInitial : true
}
```
