---
description: Experience Cloud ID Service (ECID) 支援 SHA-256 雜湊演算法，可讓您傳入客戶 ID 或電子郵件地址，然後傳出雜湊 ID。這是選用的 Javascript 方法，可將經雜湊處理的識別碼傳送至 Experience Cloud。在傳送客戶 ID 之前，您可以繼續使用自己的雜湊方法。
keywords: ID 服務
seo-description: Experience Cloud ID Service (ECID) 支援 SHA-256 雜湊演算法，可讓您傳入客戶 ID 或電子郵件地址，然後傳出雜湊 ID。這是選用的 Javascript 方法，可將經雜湊處理的識別碼傳送至 Experience Cloud。在傳送客戶 ID 之前，您可以繼續使用自己的雜湊方法。
seo-title: setCustomerIDs 的 SHA256 雜湊支援
title: setCustomerIDs 的 SHA256 雜湊支援
translation-type: tm+mt
source-git-commit: ac1131be75fd04b51cd1d646086e1802a43afb18

---


# `setCustomerIDs` 的 SHA256 雜湊支援 {#hashing-support}

Experience Cloud ID Service (ECID) 支援 SHA-256 雜湊演算法，可讓您傳入客戶 ID 或電子郵件地址，然後傳出雜湊 ID。這是選用的 Javascript 方法，可將經雜湊處理的識別碼傳送至 Experience Cloud。在傳送客戶 ID 之前，您可以繼續使用自己的雜湊方法。有兩種方法可使用 setCustomerIDs 實作雜湊支援，如下節所述:

* [在 ECID 中使用 setCustomerIDs 方法](/help/reference/hashing-support.md#use-setcustomerids-method)
* [在 Adobe Experience Platform Launch 中新增動作](/help/reference/hashing-support.md#add-action-launch)

## 在 ECID 中使用 `setCustomerIDs` 方法 {#use-setcustomerids-method}

第一個方法是使用 [`setCustomerIDs`](/help/library/get-set/setcustomerids.md) (`customerIDs<object>`, `hashType<string>`) 方法。

在雜湊處理前，ECID 程式庫會對 customerIDs 執行資料標準化。此程序會修剪 customerIDs 頭尾兩端的空格，並將所有字元轉換為小寫字母。例如，若是電子郵件地址:「 ecid@adobe.com 」會變成「ecid@adobe.com」

請參閱下面的程式碼範例，瞭解如何使用 SHA-256 雜湊來設定單一客戶 ID (即上述電子郵件地址)。

```
// Set single customerID with SHA-256 hashing
visitor.setCustomerIDs({email: {id: "ecid@adobe.com", authState: 1}}, "SHA-256");
```

<br> 

除了 Experience Cloud 訪客 ID 之外，您還可以將其他客戶 ID、驗證狀態和雜湊類型 (SHA-256) 與每個訪客建立關聯。如果您未提供任何雜湊類型，則會視為無雜湊。

`setCustomerIDs` 方法接受同一位訪客擁有多個客戶 ID。這可幫助您識別或鎖定不同裝置上的個別使用者。例如，您可以將這些 ID 上傳至 Experience Cloud 作為[客戶屬性](https://docs.adobe.com/content/help/en/core-services/interface/customer-attributes/attributes.html)，並在不同解決方案中使用此資料。

客戶 ID、驗證狀態和雜湊類型&#x200B;*不會*&#x200B;為了稍後使用而儲存在 Cookie 中。相反地，客戶 ID、驗證狀態和雜湊類型應儲存在執行個體變數中，以使用 [`getCustomerIDs`](/help/library/get-set/getcustomerids.md) 加以擷取，如下所示:

```
> visitor.getCustomerIDs();
< {email: {…}}
    email: {id: "a6ea4cde5da5ae7cc68baae894d1d6544fca26254433b0fff7c2cb4843b4a097", authState: 1, hashType: "SHA-256"}
    __proto__: Object
```

<br> 

使用 `setCustomerIDs` 方法會呼叫 Experience Cloud ID Service，目標為 `dpm.demdex.net`，並加上 `d_cid_ic` 查詢參數 (包含經雜湊處理的客戶 ID)。範例呼叫看起來可能如下所示。已新增分行以避免混淆。

```
http://dpm.demdex.net/id?d_visid_ver=4.4.0&d_fieldgroup=AAM&d_rtbd=json&d_ver=2&
d_orgid=12A3F3F459CE0AD80A495CBE%40AdobeOrg&d_nsid=0&d_mid=12349850857640731290890207735189050123&
d_blob=6G1ynYcLPuiQxYZrsz_pkqfLG9yMXBpb2zX5dvJdYQJzPXImdj0y&
d_cid_ic=email%a6ea4cde5da5ae7cc68baae894d1d6544fca26254433b0fff7c2cb4843b4a097%011&
ts=1563299964843
```

<br> 

請參閱下表，以瞭解 `d_cid_ic` 參數和驗證狀態的說明。

| 參數 | 說明 |
|------------|----------|
| `d_cid_ic` | 將整合代碼、唯一使用者 ID (DPUUID) 和驗證狀態 ID 傳遞至 ID 服務。以非列印控制字元 (<code>%1</code>) 將整合代碼和 DPUUID 分開: <br> 範例: <code>d_cid_ic=Integration_code%01DPUUID%01Authentication_state</code> <br> <b>驗證狀態</b> <br> 這是 d_cid_ic 參數中的選用 ID。以整數方式呈現，而且能根據下列使用者的驗證狀態來識別使用者: <br> <ul><li>0 (未知或從未驗證)</li><li>1 (目前已針對此執行個體/頁面/應用程式內容驗證)</li><li>2 (登出)</li></ul> <br> 範例: <br> <ul><li>未知: ...d_cid=123%01456%01<b>0</b></li><li>驗證: ...d_cid=123%01456%01<b>1</b></li><li>登出: ...d_cid=123%01456%01<b>2</b></li></ul> |

## 在 Adobe Experience Platform Launch 中新增動作 {#add-action-launch}

Experience Platform Launch 是新一代 Adobe 標籤管理功能。Read more about Launch in the [Launch product documentation](https://docs.adobe.com/content/help/en/launch/using/overview.html).

To add an action in Launch, read the [rules documentation](https://docs.adobe.com/help/en/launch/using/reference/manage-resources/rules.html) in Adobe Launch and see the screen capture below:

![](/help/reference/assets/hashing-support.png)

<br> 

確認您的設定後，Launch 會將資料包裝進物件中，如下所示:

```
{
    integration_code: {
        id: "value",
        authState: auth_state,
        hashType: "hash_algorithm"
    }
}
```

以下是程式碼範例:

```
// Set single customer ID with hash type
setCustomerIDs(Ingeration code: {
    id: "string_value",
    authState: auth_state,
    hashType: "hash_algorithm"
});
```

與第一節所述的 `setCustomerIDs` 方法相似，這會產生對 Experience Cloud ID Service 的呼叫，並加上 `d_cid_ic` 查詢參數。