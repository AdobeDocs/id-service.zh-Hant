---
description: 除了 Experience Cloud 訪客 ID 之外，您還可以將其他客戶 ID 和驗證狀態與每個訪客建立關聯。
keywords: ID 服務
seo-description: 除了 Experience Cloud 訪客 ID 之外，您還可以將其他客戶 ID 和驗證狀態與每個訪客建立關聯。
seo-title: 客戶 ID 和驗證狀態
title: 客戶 ID 和驗證狀態
uuid: 643df363-224a-463e-a332-be59926b47e7
translation-type: ht
source-git-commit: 603540150edcdc76aacf407aeb6421c5b8386f56

---


# 客戶 ID 和驗證狀態 {#customer-ids-and-authentication-states}

除了 Experience Cloud 訪客 ID 之外，您還可以將其他客戶 ID 和驗證狀態與每個訪客建立關聯。

## 驗證狀態 {#section-68ad4065dfaa437d9070832d6e2bf85c}

`setCustomerIDs` 方法接受同一位訪客擁有多個客戶 ID。這可幫助您識別或鎖定不同裝置上的個別使用者。例如，您可以將 ID 作為[客戶屬性](https://marketing.adobe.com/resources/help/zh_TW/mcloud/?f=attributes.html)上傳至 [!DNL Experience Cloud]，並在不同解決方案中存取這些資料。

>[!IMPORTANT]
>
>客戶屬性與核心服務功能需要 `setCustomerIDs` (客戶 ID 同步化)。同步客戶 ID 是 [!DNL Analytics] 支援的選用身分識別方法。[!DNL Target] 需要客戶屬性的 `Visitor.AuthState.AUTHENTICATED` 才能運作。如需範例，請參閱[核心服務 - 如何啟用您的解決方案](https://marketing.adobe.com/resources/help/zh_TW/mcloud/?f=core_services)。

從 Experience Cloud Identity 服務 1.5 版以後的版本開始，`setCustomerIDs` 即包括可選用的 `AuthState` 物件。`AuthState` 會根據訪客的驗證狀態 (例如，登入、登出) 來識別訪客。您可使用表格中列出的狀態值來設定驗證狀態。驗證狀態會以整數傳回。

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
   <td colname="col3"> <p>驗證特殊例項、頁面，或應用程式。 </p> <p> <p>注意: 為了正常運作，<span class="keyword">Target</span> 的客戶屬性需要此狀態。 </p> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> Visitor.AuthState.LOGGED_OUT </span> </p> </td> 
   <td colname="col2"> <p> <span class="codeph">2</span> </p> </td> 
   <td colname="col3"> <p>登出。 </p> </td> 
  </tr> 
 </tbody> 
</table>

## 驗證狀態的使用案例{#section-fe9560cc490943b29dac2c4fb6efd72c}

您可以視使用者在網頁屬性上執行的動作，以及使用者是否通過驗證而定，來指派驗證狀態給使用者。請查看下表的一些範例:

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
   <td colname="col2"> <p>此狀態可用於如下案例: </p> <p> 
     <ul id="ul_086C7446D258443DA7AF5BB96A6AAEC7"> 
      <li id="li_7845BBD62D7B4362AD3FE33DEDA8FBA1">讀取電子郵件 (此動作可能表示讀者為目標收件者，但電子郵件可能也會轉寄)。 </li> 
      <li id="li_FAB7ACFC69624631BD01FC0ED84B23C5">從電子郵件至登陸頁面依序點擊。 </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> Visitor.AuthState.AUTHENTICATED </span> </p> </td> 
   <td colname="col2"> <p>使用者目前是以您網站或應用程式上使用中的工作階段驗證。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <span class="codeph"> Visitor.AuthState.LOGGED_OUT </span> </p> </td> 
   <td colname="col2"> <p>使用者通過驗證，但主動登出。使用者有意且確定中斷驗證狀態的連結。使用者不希望具有驗證身分。 </p> </td> 
  </tr> 
 </tbody> 
</table>

## 設定客戶 ID 與驗證狀態 {#section-ec4b367d16ad4ac1a1baca9b01f4ee98}

客戶 ID 可包括 ID 與驗證狀態的組合，如下列範例所示。

>[!IMPORTANT]
>
>* ID 區分大小寫。
>* 請僅用未經編碼的值當成 ID。
>* 客戶 ID 與驗證狀態未儲存在訪客 ID Cookie 中。每個頁面或應用程式內容都必須設定這兩項。
>* 您不應在客戶 ID 中加入任何個人識別資訊 (PII)。如果您要使用 PII 來識別訪客 (例如電子郵件地址)，建議您改為儲存經過雜湊或加密處理的資訊。ECID 程式庫支援使用雜湊處理使用者識別碼。請參閱 [setCustomerIDs 的 SHA256 雜湊支援](/help/reference/hashing-support.md)
>



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

使用 `getCustomerIDs` 以傳回客戶 ID 與相關的驗證狀態。此方法會以整數傳回訪客的驗證狀態。

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

傳回的客戶 ID 與驗證狀態資料看起來類似以下範例所示。

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

[!DNL Experience Cloud] ID 服務支援 Android 和 iOS SDK 程式碼中的客戶 ID 與驗證狀態。請參閱下列程式碼程式庫:

* [Android SDK 方法](https://marketing.adobe.com/resources/help/zh_TW/mobile/android/?f=c_marketing_cloud.html)
* [iOS SDK 方法](https://marketing.adobe.com/resources/help/zh_TW/mobile/ios/?f=marketing_cloud.html)

## 通知 Analytics 與 Audience Manager 客戶 {#section-3a8e9d51e71c4c6e865184b81ed9d99b}

如果您要將宣告的 ID 傳遞至 [!DNL Audience Manager]，`userid` 物件必須符合與資料來源相關的整合程式碼。如需詳細資訊，請參閱[設定合併規則程式碼](https://marketing.adobe.com/resources/help/en_US/aam/?f=merge-rules-configure-code.html)文件的[!UICONTROL 訪客 ID 服務]一節。
