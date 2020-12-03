---
description: 此功能主要是為 A4T 客戶所設計，可協助解決在單一網站/螢幕或應用程式處理 ID 時遇到的問題。
keywords: ID Service
seo-description: 此功能主要是為 A4T 客戶所設計，可協助解決在單一網站/螢幕或應用程式處理 ID 時遇到的問題。
seo-title: resetState
title: resetState
uuid: ed7be76d-a7ee-4e51-b26c-456ff85fd096
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c
workflow-type: tm+mt
source-wordcount: '398'
ht-degree: 69%

---


# resetState{#resetstate}

此功能主要是為 A4T 客戶所設計，可協助解決在單一網站/螢幕或應用程式處理 ID 時遇到的問題。

## 使用案例 {#section-840b88a5cdb042488b340cad5d7b22a5}

使用 ID 服務的 A4T 客戶可以視需要使用 `visitor.resetState()` 函數來執行下列作業:

* 透過重新導向，將補充資料ID(SDID)或任何其他ID從一個頁面或螢幕傳遞至另一個頁面或螢幕。 通常，沒有此函式，ID服務就無法傳遞此ID。
* 使用僅透過Ajax呼叫更新頁面或應用程式特定區段的程式碼，而您想要追蹤這些動作。 例如，假設您有一個頁面，其中按一下某個物件時，只會載入或變更特殊區段。 在此情況下，ID服務無法要求不同的ID，除非重新載入頁面。 但如果是使用 `visitor.resetState()`，則可以在下列條件下要求新的 ID。

請參閱以下的程式碼範例。

## 語法 {#section-9e63503e178f4be28ac850abf44d6d91}

**語法:** ` visitor.resetState( *`state`*);`

## 程式碼範例 {#section-d75b211bb4ea473887eb284de2ad838b}

您的 ID 服務實作會影響您使用此函數的方式。請參閱下表以取得範例。

**伺服器端實作**

伺服器端實作適用於擁有混合式伺服器端及用戶端 [!DNL Analytics]、[!DNL Target] 和 ID 服務實作的 A4T 客戶。如果已透過此方法設定 ID 服務，您只需要將 `visitor.resetState()` 新增到頁面即可。呼叫 ID 服務會自動傳回新的 ID 和伺服器狀態。

**非標準實作** (透過 ID)

如果您透過[非標準實作](../../implementation-guides/implementation-guides.md#section-2c4f2db1f9704315a7cccab6d2e07113)設定 ID 服務，您需要設定一個變數物件以保留您想要透過 `visitor.resetState()` 傳遞的 SDID (或其他 ID)。這會包含您的[組織 ID](../../reference/requirements.md#section-a02f537129a64ffbb690d5738d360c26) 以及您想要傳遞的 ID，如下所示。您的程式碼看起來可能類似於下列範例。

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

**非標準實作** (不透過傳遞 ID)

在此情況下，`visitor.resetState()` 可用於產生新的 ID。當使用者導覽至新畫面而不重新整理頁面，而且您需要新的ID時，這在單頁應用程式中很有用。

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
