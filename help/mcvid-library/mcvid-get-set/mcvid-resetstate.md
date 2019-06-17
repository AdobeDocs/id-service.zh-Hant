---
description: 此功能主要是為 A4T 客戶所設計，可協助解決在單一網站/螢幕或應用程式處理 ID 時遇到的問題。
keywords: ID 服務
seo-description: 此功能主要是為 A4T 客戶所設計，可協助解決在單一網站/螢幕或應用程式處理 ID 時遇到的問題。
seo-title: resetState
title: resetState
uuid: ed7be76d-a7 ee-4e51-b26 c-456ff85 fd096
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# resetState{#resetstate}

此功能主要是為 A4T 客戶所設計，可協助解決在單一網站/螢幕或應用程式處理 ID 時遇到的問題。

## 使用個案 {#section-840b88a5cdb042488b340cad5d7b22a5}

身為使用ID服務的A4T客戶，您可以在需要時使用 `visitor.resetState()` 函數：

* 透過重新導向的方式，將增補資料 ID (SDID) 或任何其他 ID 從某一頁傳遞至另一頁。如果不使用此函數，ID 服務通常不會傳遞此 ID。
* 使用只會透過 Ajax 呼叫更新頁面或應用程式特定區段的程式碼，而您亦可以追蹤這些動作。例如，在您的頁面中，按一下物件只會載入或變更某一個特殊區段。在此情況下，除非重新載入頁面，否則 ID 服務無法要求另一個 ID。不過，您 `visitor.resetState()`可以在這些條件下要求新ID。

請參閱以下的程式碼範例。

## 語法 {#section-9e63503e178f4be28ac850abf44d6d91}

**語法：**` visitor.resetState( *`state`*);`

## 程式碼範例 {#section-d75b211bb4ea473887eb284de2ad838b}

您的 ID 服務實施會影響您使用此函數的方式。如需範例，請參閱下表。

**伺服器端實作**

伺服器端實作適用於具有混合伺服器和用戶端建置 [!DNL Target]、 [!DNL Analytics]ID服務的A4T客戶。如果您已使用此方法設定ID服務，則您只需新增 `visitor.resetState()` 至頁面即可。呼叫 ID 服務會自動傳回新的 ID 和伺服器狀態。

**非標準實作** (含ID)

如果您透過[非標準實施](../../mcvid-implementation-guides/mcvid-implementation-guides.md#section-2c4f2db1f9704315a7cccab6d2e07113)設定 ID 服務，您需要設定一個變數物件以保留您想要透過 `visitor.resetState()` () 傳遞的 SDID (或其他 ID)。這會包含您的[組織 ID](../../mcvid-reference/mcvid-requirements.md#section-a02f537129a64ffbb690d5738d360c26) 以及您想要傳遞的 ID，如下所示。您的程式碼看起來可能類似於下列範例。

```js
//Instantiate server state variable 
var serverState = { 
     "Insert Experience Cloud organization ID here": { 
          //Specify the SDID or other ID 
          supplementalDataIDCurrent: "1234", 
          supplementalDataIDCurrentConsumed: { 
               "payload:top-center": false 
          } 
     } 
}; 
 
//Instantiate ID service 
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here", { 
     ... 
}); 
 
//Reset server state to pass the SDID 
visitor.resetState(serverState);
```

**非標準實作** (不需傳遞ID)

在此情況下， `visitor.resetState()` 可用來產生新ID。如果使用者要在單一頁面應用程式中導覽至新的畫面，而且不想要重新整理頁面，您便需要一個新的 ID，這種作法便十分實用。

```js
 
//Instantiate ID service 
var visitor = Visitor.getInstance ("Insert Experience Cloud organization ID here", { 
     ... 
}); 
 
//Request a supplemental Data ID for consumer1 and consumer2: 
var sdid1 = visitor.getSupplementalDataID("consumer1"); // sdid1: 1234 
var sdid2 = visitor.getSupplementalDataID("consumer2"); // sdid2: 1234 
 
//User navigates to a new screen in a single-page app, without refreshing the page. 
//To reset the Supplemental Data ID internal, call resetState without passing any parameters. 
//This way we will not be recycling the `1234` ID anymore. Instead Visitor will generate a new supplemental Data ID going forward. 
visitor.resetState(); 
 
//Request a supplemental Data ID for consumer3 and consumer4: 
var sdid1 = visitor.getSupplementalDataID("consumer3"); // sdid1: 5678 
 
var sdid2 = visitor.getSupplementalDataID("consumer4"); // sdid2: 5678
```

**動態標籤管理 (DTM)**

目前並未提供 `visitor.resetState()` () 的 DTM 設定路徑。
