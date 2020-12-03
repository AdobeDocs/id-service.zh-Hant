---
description: 除了 Experience Cloud 訪客 ID 之外，您還可以將其他客戶 ID 和驗證狀態與每個訪客建立關聯。
keywords: ID Service
seo-description: 除了 Experience Cloud 訪客 ID 之外，您還可以將其他客戶 ID 和驗證狀態與每個訪客建立關聯。
seo-title: 客戶 ID 和驗證狀態
title: 客戶 ID 和驗證狀態
uuid: 643df363-224a-463e-a332-be59926b47e7
translation-type: tm+mt
source-git-commit: ddff95876722b981f22c7e3196ff2ce9b696010e
workflow-type: tm+mt
source-wordcount: '659'
ht-degree: 100%

---


# 客戶 ID 和驗證狀態 {#customer-ids-and-authentication-states}

除了 Experience Cloud 訪客 ID 之外，您還可以將其他客戶 ID 和驗證狀態與每個訪客建立關聯。

## 驗證狀態 {#section-68ad4065dfaa437d9070832d6e2bf85c}

`setCustomerIDs` 方法接受同一位訪客擁有多個客戶 ID。這可幫助您識別或鎖定不同裝置上的個別使用者。例如，您可以將這些 ID 上傳至 [ 作為](https://docs.adobe.com/content/help/zh-Hant/core-services/interface/customer-attributes/attributes.html)客戶屬性[!DNL Experience Cloud]，並在不同解決方案中使用此資料。

>[!IMPORTANT]
>
>客戶屬性與核心服務功能需要 `setCustomerIDs` (客戶 ID 同步化)。同步客戶 ID 是 [!DNL Analytics] 支援的選用身分識別方法。[!DNL Target] 需要客戶屬性的 `Visitor.AuthState.AUTHENTICATED` 才能運作。如需範例，請參閱[核心服務 - 如何啟用您的解決方案](https://docs.adobe.com/content/help/zh-Hant/core-services/interface/about-core-services/core-services.html)。

從 Experience Cloud Identity 服務 1.5 版以後的版本開始，`setCustomerIDs` 即包括可選用的 `AuthState` 物件。`AuthState` 會根據訪客的驗證狀態 (例如，登入、登出) 來識別訪客。您可使用表中的狀態數值設定驗證狀態。驗證狀態會以整數傳回。

<table id="table_8547671CC97145529981FBF6C302BEC5"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 驗證狀態 </th> 
   <th colname="col2" class="entry"> 狀態整數 </th> 
   <th colname="col3" class="entry"> 使用者狀態 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> Visitor.AuthState.UNKNOWN </span> </p> </td> 
   <td colname="col2"> <p> <span class="codeph"> 0 </span> </p> </td> 
   <td colname="col3"> <p>未知或從未驗證 </p> <p> 當訪客 ID 未使用 <span class="codeph">AuthState</span>，或未在每個頁面或應用程式內容中明確設定 AuthState 時，依預設會套用「未知」。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> Visitor.AuthState.AUTHENTICATED </span> </p> </td> 
   <td colname="col2"> <p> <span class="codeph"> 1 </span> </p> </td> 
   <td colname="col3"> <p>驗證特殊例項、頁面，或應用程式。 </p> <p> <p>注意：為了正常運作，<span class="keyword">Target</span> 的客戶屬性需要此狀態。 </p> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> Visitor.AuthState.LOGGED_OUT </span> </p> </td> 
   <td colname="col2"> <p> <span class="codeph">2</span> </p> </td> 
   <td colname="col3"> <p>登出。 </p> </td> 
  </tr> 
 </tbody> 
</table>

## 驗證狀態的使用案例 {#section-fe9560cc490943b29dac2c4fb6efd72c}

您可以根據使用者對 Web 屬性所執行的動作及是否驗證，為使用者指派驗證狀態。請參閱下表的幾個範例：

<table id="table_3769E79304014C4F87094B87A8ACE4E0"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 驗證狀態 </th> 
   <th colname="col2" class="entry"> 使用案例 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> Visitor.AuthState.UNKNOWN </span> </p> </td> 
   <td colname="col2"> <p>此狀態適用的情境包括： </p> <p> 
     <ul id="ul_086C7446D258443DA7AF5BB96A6AAEC7"> 
      <li id="li_7845BBD62D7B4362AD3FE33DEDA8FBA1">閱讀電子郵件 (此動作可能代表讀者即是預期的收件者，但電子郵件也可能已經轉寄)。 </li> 
      <li id="li_FAB7ACFC69624631BD01FC0ED84B23C5">從電子郵件點進登陸頁面。 </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> Visitor.AuthState.AUTHENTICATED </span> </p> </td> 
   <td colname="col2"> <p>使用者目前是以您網站或應用程式上使用中的工作階段驗證。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> Visitor.AuthState.LOGGED_OUT </span> </p> </td> 
   <td colname="col2"> <p>使用者已完成驗證，但已主動登出。使用者希望且刻意中斷已驗證的狀態。使用者不想維持已驗證狀態。 </p> </td> 
  </tr> 
 </tbody> 
</table>

## 設定客戶 ID 與驗證狀態 {#section-ec4b367d16ad4ac1a1baca9b01f4ee98}

客戶 ID 可包括 ID 與驗證狀態的組合，如下列範例所示。

>[!IMPORTANT]
>
>* ID 區分大小寫。
>* 請僅用未經編碼的值當成 ID。
>* 客戶 ID 和驗證狀態不會儲存在訪客 ID Cookie 中，每個頁面或應用程式內容皆需個別設定。
>* 請勿在客戶 ID 中提供任何個人識別資訊 (PII)。如果您要使用 PII 來識別訪客 (例如電子郵件地址)，建議您改為儲存經過雜湊或加密處理的資訊。ECID 程式庫支援使用雜湊處理使用者識別碼。請參閱 [setCustomerIDs 的 SHA256 雜湊支援](/help/reference/hashing-support.md)


```js
// Single ID with a single authentication state 
visitor.setCustomerIDs({ 
    "userid":{ 
        "id":"67312378756723456", 
        "authState":Visitor.AuthState.AUTHENTICATED 
    } 
}); 
 
/* 
Multiple IDs with only the first ID explicitly assigned an authentication state. 
The second ID is not explicitly assigned an authentication state and is implicitly 
assigned Visitor.AuthState.Unknown by default. 
*/ 
visitor.setCustomerIDs({ 
    "userid":{ 
        "id":"67312378756723456", 
        "authState":Visitor.AuthState.AUTHENTICATED 
    }, 
    "dpuuid":"550e8400-e29b-41d4-a716-446655440000" 
}); 
 
// Multiple IDs with identical authentication states 
visitor.setCustomerIDs({ 
    "userid":{ 
        "id":"67312378756723456", 
        "authState":Visitor.AuthState.AUTHENTICATED 
    }, 
    "dpuuid":{ 
        "id":"550e8400-e29b-41d4-a716-446655440000", 
        "authState":Visitor.AuthState.AUTHENTICATED 
    } 
}); 
 
// Multiple IDs with different authentication states 
visitor.setCustomerIDs({ 
    "userid":{ 
        "id":"67312378756723456", 
        "authState":Visitor.AuthState.AUTHENTICATED 
    }, 
    "dpuuid":{ 
        "id":"550e8400-e29b-41d4-a716-446655440000", 
        "authState":Visitor.AuthState.LOGGED_OUT 
    } 
}); 
```

## 傳回客戶 ID 與驗證狀態 {#section-71a610546188478fa9a3185a01d6e83b}

使用 `getCustomerIDs` 以傳回客戶 ID 與相關的驗證狀態。這種方法會以整數傳回訪客的驗證狀態。

**語法**

`getCustomerIDs` 會使用下列語法傳回資料。

```js
{ 
    [customerIDType1]:{ 
        "id":[customerID1], 
        "authState":[authState1] 
    }, 
    [customerIDType2]:{ 
        "id":[customerID2], 
        "authState":[authState2] 
    } 
    ... 
}
```

**範例**

傳回的客戶 ID 和驗證狀態資料應該類似下列範例。

```js
Object customerIDs = visitor.getCustomerIDs(); 
  
// No setCustomerIDs call on this instance 
{} 
  
// setCustomerIDs call on this instance with {"userid":{"id":"67312378756723456"}} 
{ 
    "userid":{ 
        "id":"67312378756723456", 
        "authState":0 
    } 
} 
  
// setCustomerIDs call on this instance with {"userid":{"id":"67312378756723456","authState":Visitor.AuthState.AUTHENTICATED}} 
{ 
    "userid":{ 
        "id":"67312378756723456", 
        "authState":1 
    } 
} 
  
// setCustomerIDs call on this instance with {"userid":{"authState":Visitor.AuthState.LOGGED_OUT}} 
{ 
    "userid":{ 
        "authState":2 
    } 
} 
  
// setCustomerIDs call on this instance with {"userid":{"authState":Visitor.AuthState.LOGGED_OUT},"dpuuid":{"id":"550e8400-e29b-41d4-a716-446655440000"}} 
{ 
    "userid":{ 
        "authState":2 
    }, 
    "dpuuid":{ 
        "id":"550e8400-e29b-41d4-a716-446655440000", 
        "authState":0 
    } 
 }
```

## SDK 支援 {#section-861c6b3b1ba645dda133dccb22ec7bb0}

[!DNL Experience Cloud] ID 服務支援 Android 和 iOS SDK 程式碼中的客戶 ID 與驗證狀態。請參閱下列程式碼資料庫：

* [Android SDK 方法](https://docs.adobe.com/content/help/zh-Hant/mobile-services/android/overview.html)
* [iOS SDK 方法](https://docs.adobe.com/content/help/zh-Hant/mobile-services/ios/overview.html)

## 通知 Analytics 與 Audience Manager 客戶 {#section-3a8e9d51e71c4c6e865184b81ed9d99b}

如果您要將宣告的 ID 傳遞至 [!DNL Audience Manager]，`userid` 物件必須符合與資料來源相關的整合程式碼。如需詳細資訊，請參閱[設定合併規則程式碼](https://docs.adobe.com/help/zh-Hant/audience-manager/user-guide/features/profile-merge-rules/merge-rules-start.html#configure-merge-rule-code)文件中的[!UICONTROL 訪客 ID 服務]章節。
