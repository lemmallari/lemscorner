---
title: Using Reputation.js in SPFX
date: Last Modified 
permalink: /ratings-in-sharepoint/index.html
eleventyNavigation:
  key: ratings-in-sharepoint 
  order: 2
  title: Using Reputation.js in SPFX
  parent: office365
---
In my previous [post](/spfx-external-libs) I showed the different ways to add external libraries in your SPFX. In this post, I'll show you how to rate/like items in your SharePoint list or libraries using reputation.js.

### Add reputation.js to your SPFX solution
Before starting, make sure you add reputation.js after importing all SharePoint javascript libraries (init.js, MicrosoftAjax.js, SP.Runtime.js and SP.js) either through your config.json file:

``` javascript
"externals": {
  {
    //...other libraries
    "reputation": {
      "path": "<tenant_url>/_layouts/15/reputation.js",
      "globalName": "reputation",
      "globalDependencies": [ "SP" ]
    }
  }
}
```

or through your loadScripts() function

``` javascript
public async loadScripts() {
  //... other libraries
  await SPComponentLoader.loadScript('/_layouts/15/reputation.js', {
    globalExportsName: 'reputation'});
}
```

### Calling the reputation.js in SPFX
After adding reputation.js in your solution you can now use it to send likes or ratings to your list or libraries. In the code block below, I created a function which likes an item in a list/library given the list/library's GUID:

``` javascript
private likeItem = (listID:string, itemID:number, setLike:boolean) => {
  let ctx = new SP.ClientContext("your tenant url here");
  Microsoft.Office.Server.ReputationModel.Reputation.setLike(ctx, listID, itemID, setLike);

  ctx.executeQueryAsync((msg) => {
    //your logging function here
    console.log("Successfully liked an item");
  }, (err) => {
    //your logging function here
    console.log("Error in liking an item. Error message");
  })
}
```

And that's it! You just need to pass a SharePoint Context, a list GUID, a list item ID and a boolean value to say if you're going to like/unlike an item.