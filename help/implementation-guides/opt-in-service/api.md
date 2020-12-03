---
description: 選擇加入資料庫 API 與組態設定參考資料。
seo-description: 選擇加入資料庫 API 與組態設定參考資料。
seo-title: 選擇加入參考資料
title: 選擇加入參考資料
uuid: d5023a34-2f3e-464d-b21f-579b2f416ce6
translation-type: tm+mt
source-git-commit: 4fbfefddcf36855f32f2a4047e19ef0b22fc508c
workflow-type: tm+mt
source-wordcount: '897'
ht-degree: 69%

---


# 選擇加入參考資料{#opt-in-reference}

選擇加入資料庫 API 與組態設定參考資料。

「選擇加入」功能會以類別提供同意設定：

```
adobe.OptInCategories = { 
    "AAM": "aam", 
    "ANALYTICS": "aa", 
    "ECID": "ecid", 
    "TARGET": "target" 
}
```

## 選擇加入組態參數 {#section-d66018342baf401389f248bb381becbf}

本節探討如何使用 API 來設定選擇加入。大部分的設定與實作都可使用 Experience Platform Launch 擴充功能來完成。

訪客 JavaScript 的 `getInstance()` 函數中提供選擇加入設定，可實例化全域 `adobe` 物件。下表列出與選擇加入服務有關的訪客 JS 設定。

**`doesOptInApply (boolean or function that evaluates to a boolean)`**：

若為false，表示訪客不需要選擇加入。 導致Experience Cloud建立Cookie，不論選擇加入或退出的類別為何。 此組態會整體啟用或停用選擇加入。

**`preOptInApprovals (Object <adobe.OptInCategories enum: boolean>)`**

當訪客未設定偏好設定時，定義核准或拒絕的類別，且以組織預設值參照。

**`previousPermissions (Object<adobe.OptInCategories enum: boolean>)`**

訪客明確設定的偏好設定。此設定的權限會覆寫組織的預設值 (`previousPermissions` 覆寫 `preOptInApprovals`)。

**`isOptInStorageEnabled (boolean)`**

啟用選擇加入以將權限儲存在第一方 Cookie 中 (位於目前客戶的網域內)

(選填) **`optInCookiesDomain (string)`**

用於選擇加入 Cookie 的第一方網域或子網域 (若 `isOptInStorageEnabled` 為 true)

(選填) **`optInStorageExpiry (integer)`**

覆寫預設13個月到期的秒數

## 對「同意」參數的更改 {#section-c3d85403ff0d4394bd775c39f3d001fc}

訪客在您網站上的任何時間，都可能首次設定偏好設定，或可能會使用您的CMP變更其偏好設定。 使用初始設定初始化訪客JS後，即可使用下列函式變更訪客的權限：

**`adobe.optIn.approve(categories, shouldWaitForComplete)`**

核准或選擇將訪客加入清單中的所有類別。如需shouldWaitForComplete參數的詳細資訊，請參 [閱選擇加入工作流程](../../implementation-guides/opt-in-service/getting-started.md#section-70cd243dec834c8ea096488640ae20a5)。

**`adobe.optIn.deny(categories, shouldWaitForComplete)`**

拒絕或選擇將訪客退出所有指定類別的函數。

**`adobe.optIn.approveAll()`**：

如果您的網站建立權限要求是讓訪客概括授予或拒絕網站建立 Cookie 的權限，請依據訪客的回應使用 `approveAll()` 或 `denyAll()`。

**`adobe.optIn.denyAll()`**：

如果您的網站建立權限要求是讓訪客概括授予或拒絕網站建立 Cookie 的權限，請依據訪客的回應使用 `approveAll()` 或 `denyAll()`。

## 選擇加入工作流程參數 {#section-2c5adfa5459c4e72b96d2693123a53c2}

選擇加入支援可從多個要求週期收集權限的工作流程，例如一次指定一項偏好設定時。使用下列函數並將 ** 設定設為 `shouldWaitForComplete`true，您的解決方案便能夠收集一個解決方案或全部類別之子集合的同意，然後收集下一個解決方案或類別子集合的同意。從首次呼叫開始，`adobe.optIn.status` 屬性會擱置，直到流程結束時呼叫 `adobe.optIn.complete()` 為止。呼叫後，狀態會設為 *complete*。

**`adobe.optIn.approve(categories, shouldWaitForComplete)`**

核准或選擇將訪客加入清單中的所有類別。

`adobe.optIn.deny(categories, shouldWaitForComplete)`

拒絕或選擇將訪客退出所有指定類別的函數。

`adobe.optIn.complete()`

此函數會觸發將正在執行的 approve() 和 deny() 呼叫彙總進單一要求中，以設定訪客的偏好設定。訂閱下方的選擇加入變更時 (請參閱 `adobe.optIn.fetchPermissions(callback, shouldAutoSubscribe`)，只有呼叫此函數時會觸發回呼。

## 訪客選擇加入權限的參數 {#section-7fe57279b5b44b4f8fe47e336df60155}

使用其中一個權限函數來收集訪客的選擇加入權限:

`adobe.optIn.permissions`

此物件會以類別形式，列出訪客授權或拒絕的所有 Experience Cloud 解決方案。

`adobe.optIn.isApproved(categories)`

如果所有類別皆經核准，此函數會傳回 true。

`adobe.optIn.fetchPermissions(callback, shouldAutoSubscribe)`

非同步擷取權限清單。 在權限授與／拒絕程式完成後，會使用權限清單呼叫回呼。 將 *的值設為* true`shouldAutoSubscribe`，會登錄往後任何的選擇加入變更。以下為 `adobe.OptIn` 的屬性:

**`permissions`**

此物件會以類別形式列出訪客授權或拒絕的所有 Experience Cloud 解決方案。範例: `{ aa: true, ecid: false, aam: true... }`

**`status`**

* 擱置
* 已變更
* 完成

**`doesOptInApply`**

值為 true 或 false，代表您提供的初始化設定

**`isPending`**

True或false，視狀態值而定。 對於尚未明確接受或拒絕權限的訪客，此屬性的加入報表為true

**`isComplete`**

True或false視狀態值而定。 當工作流程式同意已開始但未完成時，選擇加入可能會針對此屬性報告為false。

## 選擇加入物件的方法 {#section-e0417801a82548d199d833010033e433}

**`approve(categories, shouldWaitForComplete)`**

**`categories`**: 要核准的一或多個類別。例如: `adobe.optIn.approve([adobe.OptInCategories.AAM, adobe.OptInCategories.ECID])`
**`shouldWaitForComplete`**: (選用) 布林值參數，預設為 false。如果您傳入 true，在您呼叫 `adobe.optIn.complete()` () 前，選擇加入不會完成核准程序。此程序類似工作流程。

```
<codeblock>
  adobe.optIn.approve(adobe.OptInCategories.ANALYTICS, 
         true); adobe.optIn.approve(adobe.OptInCategories.ECID, true); 
         adobe.optIn.complete() 
</codeblock>
```

**`deny(categories, shouldWaitForComplete)`**

* 通過1個或多個類別以檢查是否已批准。
* 如果未傳遞任何類別，則會勾選「所有可用類別」。

**`isApproved(categories)`**

檢查客戶是否核准一或多個類別。

**`isPreApproved(categories)`**

檢查客戶是否預先核准一或多個類別。(如果類別以 `preOptInApprovals` 設定傳入。)

**`fetchPermissions(callback, shouldAutoSubscribe)`**

非同步API以擷取權限清單。 在權限授與／拒絕程式完成後，會使用權限清單呼叫回呼。 **`shouldAutoSubscribe`:** 協助工具公用程式會自動將此回呼訂閱至所有未來事件。 也就是說，每次在選擇加入中觸發核准或拒絕觸發時，都會呼叫回呼。 如此，您就可隨時更新，而不需自行訂閱活動。

**範例**

`fetchPermissions`

```
optIn.fetchPermissions(function (permissions) { 
    // Here you can check if your category has been approved or not. 
    // We recommend using `optIn.isApproved()` to check for permissions because it abstracts  
       out the details of knowing exactly how the `permissions` list looks like. 
 
    if (adobe.optIn.isApproved(MY_CATEGORY) { 
        sendBeacon(); // Or something 
    } 
});

// OR: You can pass in `shouldAutoSubscribe` as true, your callback will be used to subscribe  
to all OptIn events going forward:

function callback() { 
    if (adobe.optIn.isApproved(MY_CATEGORY) { 
        sendBeacon(); // Or something 
    } 
} 
 
optIn.fetchPermissions(callback, true);
```

**`complete()`:**

>[!NOTE]
>
>只有在您傳遞 `shouldWaitForComplete` 參數以核准或拒絕時才使用。此 API 會完成核准程序。範例: `adobe.optIn.complete()`.

**`approveAll()`:**

核准所有現有類別。

**`denyAll()`**

拒絕所有現有類別。

## 選擇加入物件的事件 {#section-06f25b33cab54bafb053183e937fb710}

**`complete`:**

當核准程序完成時，完成事件就會觸發。如果您沒有傳遞 `shouldWaitForComplete` 便呼叫核准/拒絕，或是 `approveAll`/ `denyAll`，此事件就會觸發。或者，如果您傳入 `shouldWaitForComplete`，則此事件會在呼叫 `complete` 時觸發。

**範例**

```
<codeph>
  adobe.optIn.on("complete", callback); 
</codeph>
```
