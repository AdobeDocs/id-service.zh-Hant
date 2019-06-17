---
description: 將選擇加入服務作為Experience Cloud解決方案所使用的單一參照單點(稱為「選擇加入」)來決定是否要在訪客裝置上建立Cookie。
seo-description: 將選擇加入服務作為Experience Cloud解決方案所使用的單一參照單點(稱為「選擇加入」)來決定是否要在訪客裝置上建立Cookie。
seo-title: 設定加入服務
title: 設定加入服務
uuid: f1c27139-cef2-4122-aff12-c839 cfc82 e6 e
translation-type: tm+mt
source-git-commit: ae65e9c7da5ac9cbe22de3f956bcd7cbef2052a7

---


# 設定加入服務{#setting-up-opt-in-service}

將選擇加入服務作為Experience Cloud解決方案所使用的單一參照單點(稱為「選擇加入」)來決定是否要在訪客裝置上建立Cookie。

選擇加入服務是隨 [Experience Cloud ID(ECID)](https://marketing.adobe.com/resources/help/en_US/mcvid/) 搭售的JavaScript程式庫，並存在於全域 `adobe` 物件中做為 `adobe.optIn` 物件的訪客JS中。安裝的Opt-in服務可讓您指定訪客是否可一次加入Adobe解決方案，或在序列中以順序提供解決方案。選擇加入服務許可管理功能可讓您針對特定隱私權需求實施各種設定。

選擇加入服務可讓您指定訪客是否可一次選擇加入Adobe解決方案，或在序列中以順序提供解決方案。客戶完成並記錄核准程序後，所有的 Adobe 解決方案便能擷取 CMP 訪客核准，並以相關的同意呼叫回應。

## 必備條件 {#section-c39246f45e514c8ea9fdbe6f7ffa3ad0}

1. ECID 4.0 版

   [下載](https://github.com/Adobe-Marketing-Cloud/id-service/releases)最新版 ECID。

1. 支援的資料庫

   * ECID 4.0 版或更新版本
   * AppMeasurement 2.11 版或更新版本
   * DIL 9.0
   * AT.js 1.7.0 版
   * AT.js Launch 擴充功能 9.0 版
   * 若為 Analytics，需 App Measurement 2.11 以及擴充功能 1.6 版
   * 若為 Target，需擴充功能 0.9.1 版

1. 精通您將用於選擇加入的同意管理架構，並瞭解任何額外必備條件。

   <!--
   For IAB, see here for additional pre-reqs.
   -->

1. 貴公司的隱私權要求將依您選擇遵循 GDPR 規定的方式而定。瞭解貴公司隱私權團隊可接受以預先同意狀態使用的資料庫為何。

如果使用 [Adobe Launch](https://docs.adobelaunch.com/)，請善加利用[選擇加入擴充功能](../../mcvid-implementation-guides/opt-in-service/launch.md) 以設定選擇加入服務。

## 選擇加入類別 {#section-9ab0492ab4414f0ca16dc08d3a905f47}

訪客的選擇加入偏好設定取決於 Adobe Experience Cloud 解決方案，每個解決方案都會以類別來表示。`adobe.OptInCategories` 物件會提供類別，舉例來說，系統會以 `adobe.OptInCategories` 參照 ECID 元件。`ECID`。以下為 `adobe.OptInCategories` 的定義:

選擇加入設定是按類別來維護，每個 Experience Cloud 解決方案都會以類別來表示。

```
adobe.OptInCategories = { 
    AAM: "aam", 
    TARGET: "target",  
    ANALYTICS: "aa", 
    ECID: "ecid", 
     
};
```

選擇加入服務可讓您針對網站上使用的每個Adobe解決方案設定訪客的權限偏好設定。選擇加入物件包含資料庫，可按核准的類別儲存訪客的設定，並支援序列流程，即核准程序一次會收到一個各類別的「確認」或「拒絕」偏好設定。您可以設定解決方案/類別，來選擇以全部或個別解決方案加入。所有Adobe解決方案的用戶端程式庫都依賴於選擇加入服務，除非已獲得解決方案，否則不會產生Cookie。選擇加入支援多種方法，可提供並更新目前訪客的同意設定。本節提供設定選擇加入服務偏好設定的範例。如需完整的函數和參數清單，請參閱 [選擇加入API參考](../../mcvid-implementation-guides/opt-in-service/api.md#reference-4f30152333dd4990ab10c1b8b82fc867) 。

選擇加入服務組態是在訪客JS `getInstance()` 函數中提供，此函數會執行個體化全域 `adobe` 物件。以下列出選擇加入服務的訪客JS [設定設定](../../mcvid-implementation-guides/opt-in-service/api.md#section-d66018342baf401389f248bb381becbf) 。

**全域`Visitor`物件初始化時的選擇加入設定**

```
// FORMAT: Object<adobe.OptInCategories enum: boolean> 
var preOptInApprovalsConfig = {}; 
preOptInApprovals[adobe.OptInCategories.ANALYTICS] = true; 
  
// FORMAT: Object<adobe.OptInCategories enum: boolean> 
// If you are storing the OptIn permissions on your side (in a cookie you manage or in a CMP), 
// you have to provide those permissions through the previousPermissions config. 
// previousPermissions will overwrite preOptInApprovals. 
var previousPermissionsConfig = {}; 
previousPermissionsConfig[adobe.OptInCategories.AAM] = true; 
previousPermissionsConfig[adobe.OptInCategories.ANALYTICS] = false; 
  
Visitor.getInstance("YOUR_ORG_ID", { 
    "doesOptInApply": true, // NOTE: This can be a function that evaluates to true or false. 
    "preOptInApprovals": preOptInApprovalsConfig, 
    "previousPermissions": previousPermissionsConfig, 
    "isOptInStorageEnabled": true 
});
```

**處理同意的變更**

訪客在您的網站上體驗時，可能會隨時首次設定偏好設定，或使用您的 CMP 變更偏好設定。以初始設定初始化訪客 JS 後，訪客的權限就能變更。如 [需管理許可功能的清單，請參閱許可](../../mcvid-implementation-guides/opt-in-service/api.md#section-c3d85403ff0d4394bd775c39f3d001fc) 變更。

<!--
<p> *** <b>sample code block </b>*** </p>
-->

## 加入工作流程 {#section-70cd243dec834c8ea096488640ae20a5}

選擇加入服務支援一個工作流程，其中可收集超過一個請求週期的權限，一次給予一個偏好設定。使用下列函數並將 ** 設為 `shouldWaitForComplete`true，您的解決方案便能夠收集解決方案或全部類別之子集合的同意，然後收集下一個解決方案或類別子集合的同意。從第一個呼叫開始， `adobe.optIn.status` 屬性將 *持續擱置* ，直到 `adobe.optIn.complete()` 流程結束為止。呼叫後，狀態會設為 *complete*。

```
adobe.optIn.approve(['AAM', 'ECID'], true); 
adobe.optIn.deny(['ANALYTICS'], true); 
adobe.optIn.complete();
```

請參閱 [工作流程設定設定](../../mcvid-implementation-guides/opt-in-service/api.md#section-2c5adfa5459c4e72b96d2693123a53c2)。

## 檢查訪客的選擇加入權限 {#section-f136a9024e054d84881e6667fb7c94eb}

當訪客對其權限進行變更時，您將需要對產生的權限的深入分析，與在選擇加入服務中所做的變更同步。使用[權限函數](../../mcvid-implementation-guides/opt-in-service/api.md#section-7fe57279b5b44b4f8fe47e336df60155)來檢查訪客的偏好設定，例如:

**fetchPermissions 範例**

```
optIn.fetchPermissions(function (permissions) { 
    // Here you can check if your category has been approved or not. 
    // We recommend using optIn.isApproved() to check for permissions because it abstracts out the details of knowing exactly how the permissions list looks like. 
    if (adobe.optIn.isApproved(MY_CATEGORY) { 
        sendBeacon(); // Or something 
    } 
});

OR: You can pass in shouldAutoSubscribe as true, your callback will be used to subscribe to all OptIn events going forward:

function callback() { 
    if (adobe.optIn.isApproved(MY_CATEGORY) { 
        sendBeacon(); // Or something 
    } 
}

optIn.fetchPermissions(callback, true);
```

如需此工具的其他相關資訊，請參閱[請參閱 API 文件](../../mcvid-implementation-guides/opt-in-service/api.md#reference-4f30152333dd4990ab10c1b8b82fc867)以深入瞭解本文件提及的所有函數、屬性或設定。

## 儲存訪客偏好設定 {#section-ef2884ae67e34879bf7c7c3372706c9f}

選擇加入服務可讓您將同意偏好設定儲存至開發環境或無法使用CRM的環境中。指定組態屬性 `isOptInStorageEnabled` 作為 *真正* 觸發的「退出」服務，在您的網域內建立訪客系統的Cookie。

`adobe.optIn` 物件沒有狀態，不會提供儲存機制。這種設計的目的是，如果您現有的同意管理平台 (CMP) 允許儲存自訂資料，則您要在自己的平台上管理 Adobe 同意設定。或者，您可以將訪客偏好設定儲存在訪客瀏覽器上的 Cookie 中。您有兩個選項可供使用者使用加入服務的偏好設定：

* 如果您的同意永續性解決方案是訪客瀏覽器上的CMP或Cookie，可以即時擷取訪客喜好設定，您可以在訪客初始化期間提供選擇加入服務。
* 不過，如果擷取過程是冗長的程序，或者是以非同步程序提供，則您可以使用服務 `approve()` 的函數在成功載入這些設定後提供這些設定。

