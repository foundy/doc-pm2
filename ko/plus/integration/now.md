 Now.sh is actually not supported by pm2
{: .warn}

# Monitor your Node.js app in Now.sh

In seconds, this tutorial will show you how to monitor a node.js application with PM2 Plus and Now.sh.

We assume that your app has already been wrapped with pm2. If not, follow the [PM2 Now.sh Tutorial]({{ site.baseurl }}{% link en/runtime/integration/now.md %}).

---

### Create an account

Register [here](https://id.keymetrics.io/api/oauth/register).

---

### Link with pm2 Plus

You first need to use pm2 to wrap your app inside your Docker container. If not, follow the [now.sh tutorial]({{ site.baseurl }}{% link en/runtime/integration/now.md %}).

### Link with pm2 Plus

In order to connect pm2 to your dashboard, you must add your public and private keys in the environment.

Add a `KEYMETRICS_PUBLIC` and a `KEYMETRICS_SECRET` environment variables and fill their value with your keys.

 You can access your keys at the top right of your dashboard
{: .tip}

### Set the server name in pm2 Plus

Add a `PM2_MACHINE_NAME` environment variable to the ecosystem file to specify a server name:

```javascript
module.exports = {
  apps : [{
    name: "app",
    script: "./app.js",
    instances: "max",
    env: {
      NODE_ENV: "development",
    },
    env_production: {
      NODE_ENV: "production",
      PM2_MACHINE_NAME: "now-my-app",
    }
  }]
}
```

 The default server name is the hostname (`HOST` variable) with a few random characters.
{: .tip}

 Be careful, in case of duplicate hostnames the dashboard will receive data from both instances and flicker.
{: .tip}

### Next Steps

Complete your [dashboard configuration]({{ site.baseurl }}{% link en/plus/guide/configuration.md %}).




