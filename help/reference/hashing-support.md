---
description: Experience Cloud ID Service(ECID)支援SHA-256雜湊演算法，可讓您傳入客戶ID或電子郵件地址，並傳遞雜湊ID。這是選用Javascript方法，可將雜湊識別碼傳送至Experience Cloud。在傳送客戶ID之前，您可以繼續使用自己的雜湊方式。
keywords: ID 服務
seo-description: Experience Cloud ID Service(ECID)支援SHA-256雜湊演算法，可讓您傳入客戶ID或電子郵件地址，並傳遞雜湊ID。這是選用Javascript方法，可將雜湊識別碼傳送至Experience Cloud。在傳送客戶ID之前，您可以繼續使用自己的雜湊方式。
seo-title: SHA256雜湊支援setCustomerIDs
title: SHA256雜湊支援setCustomerIDs
translation-type: tm+mt
source-git-commit: ac1131be75fd04b51cd1d646086e1802a43afb18

---


# SHA256 Hashing Support for `setCustomerIDs` {#hashing-support}

Experience Cloud ID Service(ECID)支援SHA-256雜湊演算法，可讓您傳入客戶ID或電子郵件地址，並傳遞雜湊ID。這是選用Javascript方法，可將雜湊識別碼傳送至Experience Cloud。在傳送客戶ID之前，您可以繼續使用自己的雜湊方式。
有兩種方法可使用setCustomerIDs實作雜湊支援，如下章節所述：

* [在ECID中使用setCustomerIDs方法](/help/reference/hashing-support.md#use-setcustomerids-method)
* [在Adobe Experience Platform Launch中新增動作](/help/reference/hashing-support.md#add-action-launch)

## Use the `setCustomerIDs` method in ECID {#use-setcustomerids-method}

The first method leverages using the [`setCustomerIDs`](/help/library/get-set/setcustomerids.md) (`customerIDs<object>`, `hashType<string>`) method.

在雜湊處理前，ECID程式庫會在CustomerIDs上執行資料標準化。此程序會在兩端修剪來自CustomerIDs的空白，並將所有字元轉換為小寫。例如，若是電子郵件地址：「ecid@adobe.com」變成「ecid@adobe.com」

請參閱下面的程式碼範例，說明如何使用SHA-256雜湊設定單一客戶ID(上述電子郵件地址)。

```
// Set single customerID with SHA-256 hashing
visitor.setCustomerIDs({email: {id: "ecid@adobe.com", authState: 1}}, "SHA-256");
```

<br> 

除了Experience Cloud訪客ID之外，您還可以將其他客戶ID、驗證狀態和雜湊類型(SHA-256)關聯至每個訪客。如果您未提供任何雜湊類型，則將被視為無雜湊。

`setCustomerIDs` 方法接受同一位訪客擁有多個客戶 ID。這可幫助您識別或鎖定不同裝置上的個別使用者。例如，您可以將這些 ID 上傳至 Experience Cloud 作為[客戶屬性](https://docs.adobe.com/content/help/en/core-services/interface/customer-attributes/attributes.html)，並在不同解決方案中使用此資料。

Customer IDs, authenticated states and hash type *are not* stored in a cookie to be used later. Instead, Customer IDs, authenticated states and hash type should be stored in an instance variable, to be retrieved using [`getCustomerIDs`](/help/library/get-set/getcustomerids.md), as shown below:

```
> visitor.getCustomerIDs();
< {email: {…}}
    email: {id: "a6ea4cde5da5ae7cc68baae894d1d6544fca26254433b0fff7c2cb4843b4a097", authState: 1, hashType: "SHA-256"}
    __proto__: Object
```

<br> 

Using the `setCustomerIDs` method results in a call to the Experience Cloud ID Service, to `dpm.demdex.net`, with the addition of the `d_cid_ic` query parameter, which contains the hashed customer ID. 範例呼叫看起來可能像下一個。已新增分行，以清楚呈現。

```
http://dpm.demdex.net/id?d_visid_ver=4.4.0&d_fieldgroup=AAM&d_rtbd=json&d_ver=2&
d_orgid=12A3F3F459CE0AD80A495CBE%40AdobeOrg&d_nsid=0&d_mid=12349850857640731290890207735189050123&
d_blob=6G1ynYcLPuiQxYZrsz_pkqfLG9yMXBpb2zX5dvJdYQJzPXImdj0y&
d_cid_ic=email%a6ea4cde5da5ae7cc68baae894d1d6544fca26254433b0fff7c2cb4843b4a097%011&
ts=1563299964843
```

<br> 

See the table below for a description of the `d_cid_ic` parameter and authentication state.

| 參數 | 說明 |
|------------|----------|
| `d_cid_ic` | 將Integration Code、唯一使用者ID(DPUUID)和驗證狀態ID傳遞至ID服務。Separate the Integration Code and DPUUID with the non-printing control character, <code>%01</code>: <br> Example: <code>d_cid_ic=Integration_code%01DPUUID%01Authentication_state</code> <br> <b>驗證狀態</b> <br> 這是d_ cid_ ic參數中的選用ID。以整數方式呈現，而且能根據下列使用者的驗證狀態來識別使用者: <br> <ul><li>(未知或從未驗證)</li><li>1(目前已針對此例項/頁面/應用程式內容驗證)</li><li>2 (登出)</li></ul> <br> 範例: <br> <ul><li>未知: ...d_cid=123%01456%01<b>0</b></li><li>驗證: ...d_cid=123%01456%01<b>1</b></li><li>登出: ...d_cid=123%01456%01<b>2</b></li></ul> |

## Add an Action in Adobe Experience Platform Launch {#add-action-launch}

Experience Platform Launch是Adobe新一代的標籤管理功能。Read more about Launch in the [Launch product documentation](https://docs.adobe.com/content/help/en/launch/using/overview.html).

To add an action in Launch, read the [rules documentation](https://docs.adobe.com/help/en/launch/using/reference/manage-resources/rules.html) in Adobe Launch and see the screen capture below:

![](/help/reference/assets/hashing-support.png)

<br> 

在確認您的組態後，Launch會將資料備份至物件，如下所示：

```
{
    integration_code: {
        id: "value",
        authState: auth_state,
        hashType: "hash_algorithm"
    }
}
```

下面是程式碼範例：

```
// Set single customer ID with hash type
setCustomerIDs(Ingeration code: {
    id: "string_value",
    authState: auth_state,
    hashType: "hash_algorithm"
});
```

Similarly to the `setCustomerIDs` method described in the first section, this results in a call to the Experience Cloud ID Service, with the addition of the `d_cid_ic` query parameter.