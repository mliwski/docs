# Tracking Via Proxy

This guide demonstrates how to route events from Mixpanel's SDKs via a proxy in your own domain. This is useful when tracking from the web, to reduce the likelihood of ad-blockers impacting your tracking.

![image](https://github.com/mixpanel/docs/assets/2077899/3ec6f3c2-aed0-4a18-9395-36838c3b53f1)

There are two steps: setting up a proxy server and pointing our JavaScript SDK at your server.

## Step 1: Set up a proxy server
The simplest way is to use our [sample nginx config](https://github.com/mixpanel/tracking-proxy). This config redirects any calls made to your proxy server to Mixpanel.
   
## Step 2: Point our JavaScript SDK at your server
Add the following line before the Mixpanel JS snippet, replacing `YOUR_PROXY_DOMAIN` with your proxy server's domain. This is not required if you use npm or yarn instead of the snippet:
```js
const MIXPANEL_CUSTOM_LIB_URL = "https://<YOUR_PROXY_DOMAIN>/lib.min.js";
```

Add your proxy server to the `mixpanel.init` call:

```js
mixpanel.init("<YOUR_PROJECT_TOKEN>", {api_host: "https://<YOUR_PROXY_DOMAIN>"})
```

🎉 Congratulations, you've set up tracking through a proxy server! Here's a [full code sample](https://gist.github.com/ranic/80459104def4e4bcd73d5c77b817ee43).
