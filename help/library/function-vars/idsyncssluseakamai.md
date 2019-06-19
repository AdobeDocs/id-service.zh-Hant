---
description: 指定目標發佈範本是否應該針對 HTTPS 連線使用 Akamai。
keywords: ID 服務
seo-description: 指定目標發佈範本是否應該針對 HTTPS 連線使用 Akamai。
seo-title: idSyncSSLUseAkamai
title: idSyncSSLUseAkamai
uuid: 501cc37-c3 ab-4454-bfcf-3e3 c3 e8 b5 ca
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c

---


# idSyncSSLUseAkamai{#idsyncssluseakamai}

指定目標發佈範本是否應該針對 HTTPS 連線使用 Akamai。

`idSyncSSLUseAkamai` 設定是按各別合作夥伴進行啟用。

**語法:** `idSyncSSLUseAkamai: true`

**程式碼範例**

```js
//Call the ID service 
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here",{ 
 
    //Set Akamai URL for ID sync container 
    idSyncSSLUseAkamai:true 
 
    ... 
});
```

