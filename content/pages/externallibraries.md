---
title: SPFX and External Libraries
date: Last Modified 
permalink: /spfx-external-libs/index.html
eleventyNavigation:
  key: spfx-external-libs 
  order: 1
  title: SPFX and External Libraries
  parent: office365
---
When working with SPFX there are times when you need to use external libraries which you need to reference through out your code. For instance we want to use the SharePoint JSOM objects in modern sites (eg. SP.js). There are different ways to do this, in the examples below I'll touch on two different approaches.

### Adding External Libraries Through config.json

Before updating your config.json, make sure that you install both @types/microsoft-ajax and @types/sharepoint:

``` node
npm install @types/microsoft-ajax @types/sharepoint --save-dev
```

After installation, update your config.json file (found in config folder of your solution) by adding the following in the externals property:

``` javascript
"externals": {
  {
    "sp-init": {
      "path": "<tenant_url>/_layouts/15/init.js",
      "globalName": "$_global_init"
    },
    "microsoft-ajax": {
      "path": "<tenant_url>/_layouts/15/MicrosoftAjax.js",
      "globalName": "Sys",
      "globalDependencies": [ "sp-init" ]
    },
    "sp-runtime": {
      "path": "<tenant_url>/_layouts/15/SP.Runtime.js",
      "globalName": "SP",
      "globalDependencies": [ "microsoft-ajax" ]
    },
    "sharepoint": {
      "path": "<tenant_url>/_layouts/15/SP.js",
      "globalName": "SP",
      "globalDependencies": [ "sp-runtime" ]
    }
  }
}
```
::: warning
*Make sure that you change the <tenant_url> and point it to the correct url for your site.*
:::

You now import these libraries in your files and use them as you normally would.

### Adding External Libraries Using SPComponentLoader

In the example above, we always assume that we're going to deploy our solution to the same tenant url. However if you plan on sharing your solution to others you need to make sure that it's flexible enough to work with other tenants and not just your own. So how do we do it?

Instead of using the config.json file from the example above, we will use the SPComponentLoader.loadscripts function to import our external libraries.

Make sure that you reverted back all the changes you did by uninstalling both @types/microsoft-ajax and @types/sharepoint, removing your imports and removing the contents of the external property from your config.json.

Next, install the @microsoft/sp-loader library:

``` node
npm install @microsoft/sp-loader
```

Afterwards, in a helper class call SPComponent.loadScript :

``` javascript
public async loadScripts() {
  // you can call the SPComponentLoader.loadScript in sequence if
  // there are dependencies between your scripts.
  await SPComponentLoader.loadScript('/_layouts/15/init.js', {
    globalExportsName: '$_global_init'});
}
```

And that's it! Both approaches I mentioned are useful but I prefer using the SPComponent.loadScript over the changes in the config.json file.

In my next post I'll use SPComponentLoader.loadScript in a web part to call the rating system of a Picture Library.