

- Safari Services
- Safari web extensions
-  Blocking content with your Safari web extension 

Article

# Blocking content with your Safari web extension

Build content blocking with declarative net request into your Safari web extension.

## Overview

Add declarative content blocking that works in Safari, Mac web apps, and other browsers to your Safari web extension. This approach blocks content quickly and ensures privacy for users, because the web extension doesn’t need access to the entire web request to make blocking decisions.

Safari web extensions implement declarative content blocking with the Declarative Net Request API common to web extensions on other browsers.

### Request permission to block content

To use the Declarative Net Request API in your Safari web extension, first request permission. In your Xcode project, add the declarative net request permission to the permissions list in your `manifest.js` file.

```
{
 ...
   "permissions": [
    "declarativeNetRequest",
    "activeTab"
  ],
  ...
}
```

For more information about permissions, see Managing Safari web extension permissions.

### Add rulesets to your extension and manifest

You specify rules for content blocking in rulesets, which are files with `json` describing the content blocking rules. Add references to ruleset files that you create in your `manifest.js` file to tell Safari to use them. For example:

```
{
   ...
   "declarative_net_request" : {
    "rule_resources" : [{
      "id": "ruleset_for_images",
      "enabled": true,
      "path": "image_rules.json"
    }, {
      "id": "ruleset_for_scripts",
      "enabled": false,
      "path": "script_rules.json"
    }]
  },
  ...
}
```

Build your rules describing how you want to block content, and add them to your ruleset files. For example:

```
{
    "id": 1,
    "priority": 1,
    "action": { "type": "block" },
    "condition": {
        "regexFilter": ".*",
        "resourceTypes": [ "script" ]
    }
}

```

Review Safari’s support for specifying rules:

`RuleActionTypes`  
Safari supports `block`, `allow`, `upgradeScheme`, and `allowAllRequests` (only for `main_frame`). Safari supports `redirect` in Safari 15.4 or later, and `modifyHeaders` in Safari 16.4 or later. Safari requires the `declarativeNetRequestWithHostAccess` permission for `modifyHeaders` or `redirect`. Safari requires user permission to add, remove, or append headers. Safari also requires user permission to perform redirect rules for both the originating and destination sites. Set specific match patterns or `` in the `host_permissions` key in your `manifest.js` file to request permission.

`ResourceType`  
Safari supports `main_frame`, `sub_frame`, `stylesheet`, `script`, `image`, `font`, `xmlhttprequest`, `ping`, `media`, `websocket`, and `other`.

`RuleCondition`  
Safari supports `domainType`, `excludedResourceTypes`, `isUrlFilterCaseSensitive`, `regexFilter`, and `resourceTypes.`

Rule APIs  
Safari supports `getEnabledRulesets()`, `isRegexSupported(),` `updateEnabledRulesets()`, `MAX_NUMBER_OF_STATIC_RULESETS`, `updateDynamicRules()`, `getDynamicRules()`, `updateSessionRules()`, `getSessionRules()`, and `getMatchedRules()`. Safari supports `setExtensionActionOptions()` in Safari 16.4 or later.

### Adjust rules dynamically for the extension or session

After a user installs and uses your extension, adjust content blocking using dynamic rules. Add, change, or remove rules that persist between browser sessions using `updateDynamicRules`. Add, change, or remove rules that apply only to the current session using `updateSessionRules`.

```
var rule = {
    id: 1,
    priority: 1,
    action: { type: "block" },
    condition: {
        urlFilter: "||example.com",
        resourceTypes: [ "main_frame", "script" ]
    }
};

await browser.declarativeNetRequest.updateDynamicRules({ addRules: [ rule ] });

```

## See Also

### Blocking content

Adopting Declarative Content Blocking in Safari Web Extensions

Block web content with your web extension using the declarative net request API.

