---
description: ID 服務使用您的組織 ID、Experience Cloud AMCV Cookie 及 Demdex Cookie，為您的網站訪客建立並儲存不重複的永久識別碼。這些 Cookie 可以讓 ID 服務追蹤您不同網域上的訪客，並且讓您在不同的 Experience Cloud 解決方案間共用資料。
keywords: playstation;ID 服務
title: Cookie 與 Experience Cloud Identity Service
exl-id: 727c6381-56b9-44b8-8e59-355d072769be
source-git-commit: 33e467ade389144423abf14539aad8a5a5f69d21
workflow-type: tm+mt
source-wordcount: '941'
ht-degree: 100%

---

# Cookie 與 Experience Cloud Identity Service{#cookies-and-the-experience-cloud-id-service}

ID 服務使用您的組織 ID、Experience Cloud AMCV Cookie 及 Demdex Cookie，為您的網站訪客建立並儲存不重複的永久識別碼。這些 Cookie 可以讓 ID 服務追蹤您不同網域上的訪客，並且讓您在不同的 Experience Cloud 解決方案間共用資料。

## 了解 ID 服務 Cookie {#section-f438168beaec409ab8b2cc58bd021e26}

ID 服務需仰賴 AMCV、AMCVS 和 Demdex Cookie 才能正常運作。這些 Cookie 就是 ID 服務所使用的資料儲存所在的檔案。這些 ID 服務 Cookie 並非危險、惡意或不同於網站或服務儲存於瀏覽器中的其他第一方或第三方 Cookie，且遵循的規則與其他第一方和第三方 Cookie 相同。請參考下方各節以取得 ID 服務所使用 Cookie 的更多資訊。

### ID 服務 Cookie 具備的功能

* 設定並儲存網站訪客的唯一 ID (MID)。
* 保存此唯一 ID，讓 ID 服務能夠收集資料，並將其與其他 Experience Cloud 解決方案共用。
* 跨網域追蹤用戶。但是，您必須擁有其他網域，並在這些網域上部署 ID 服務程式碼，才能進行此追蹤。

### ID 服務 Cookie 不具備的功能

* 儲存、傳輸或執行電腦病毒。
* 存取或儲存個人識別資訊 (PII)，例如：您的電子郵件地址。
* 控制電腦硬體或軟體。
* 使電腦不穩定或導致效能問題。
* 在未使用 ID 服務的網站上追蹤用戶。

## AMCV Cookie {#section-c55af54828dc4cce89f6118655d694c8}

下列 Cookie 屬性由 ID 服務設定。

**名稱**

AMCV Cookie 名稱遵循以下語法：`AMCV_<variable name>@AdobeOrg`。在名稱中，`<variable name>` 元素是 Experience Cloud 組織 ID 部分的預留位置。此 ID 會由 ID 服務程式碼中的 `Visitor.getInstance` 函數傳遞至 DCS。

完整格式的 Cookie 名稱類似以下:

```
AMCV_1FD6776A524453CC0A490D44%40AdobeOrg
```

**內容**

AMCV Cookie 包含 Experience Cloud 訪客 ID 或 MID。MID 儲存在遵循下列語法的機碼-值組中：`MCMID|<Experience Cloud ID>`。

完整格式的機碼值組類似以下:

```
MCMID|20265673158980419722735089753036633573
```

此永續性識別碼可用於跨解決方案的資料共用。

**網域**

AMCV Cookie 設定於瀏覽器的第一方網域中。這表示此 Cookie 設定於用戶目前造訪之網站的網域中。因此，ID 服務程式碼和其他 Experience Cloud 程式碼程式庫可讀取儲存在 AMCV Cookie 中的 MID。

但由於 AMCV Cookie 設定於第一方網域中，因此無法跨不同的網域追蹤和識別用戶。實際上，當網站訪客瀏覽至不同網域時，ID 服務需仰賴組織 ID 和 Demdex ID 以傳回正確的 MID。

## AMCVS Cookie {#section-92a9454f1ac645948f9059b9fad928bf}

**名稱**

AMCVS Cookie 名稱會遵循 `AMCVS_####@AdobeOrg` 語法。在名稱中，#### 元素是 Experience Cloud 組織 ID 部分的預留位置。此 ID 會由 ID 服務程式碼中的 `theVisitor.getInstance` 函數傳入 DCS。

完整格式的 Cookie 名稱類似以下:

```
AMCVS_1FD6776A524453CC0A490D44%40AdobeOrg
```

**內容**

AMCVS Cookie 可作為指出工作階段已初始化的旗標。其值一律為 `1`，直到工作階段結束為止。

**網域**

AMCVS Cookie 設定於瀏覽器的第一方網域中。這表示此 Cookie 設定於用戶目前造訪之網站的網域中。

![](assets/AMCVS-cookie.png)

## Demdex Cookie {#section-7ff7d96d6e4141b08a84a75a63d7814c}

下表列出並定義 Demdex Cookie 的某些重要屬性。

<table id="table_18E3CAF3550E4BB6A199736AACE39202"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 屬性 </th> 
   <th colname="col2" class="entry"> 說明 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>名稱</b> </p> </td> 
   <td colname="col2"> <p>Cookie 名稱為「demdex」。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>內容</b> </p> </td> 
   <td colname="col2"> <p>Demdex Cookie 包含由 DCS 產生的 Demdex ID。 </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>網域</b> </p> </td> 
   <td colname="col2"> <p>Demdex Cookie 設定於瀏覽器的第三方 demdex.net 網域中。此網域與用戶目前造訪的網站不同。 </p> <p>不同於第一方 AMCV Cookie，Demdex Cookie 和 ID 會跨不同的網域而持續保存。Demdex ID 和您的組織 ID 是一種通用值，可讓 ID 服務以正確的訪客 ID 傳回及識別網站訪客。 </p> </td> 
  </tr> 
 </tbody> 
</table>

如需有關 Demdex 披露事項的資訊，請瀏覽 [Audience Manager 裝置儲存披露事項](https://aam-iab-tcf-vendor.s3.amazonaws.com/aam_device_storage_disclosures.json)。

如需相關資訊，請閱讀[了解向 Demdex 網域進行的呼叫](https://experienceleague.adobe.com/docs/audience-manager/user-guide/reference/demdex-calls.html?lang=zh-Hant)一文。

## 產生 Experience Cloud ID {#section-15f69c0bac394b4b9966a23fbc586d17}

Experience Cloud ID (MID) 是依照組織 ID 和 demdex ID 利用數學公式計算出來。只要這些 ID 保持不變，為特定用戶產生正確的 MID 就只是數學問題。在組織 ID 和 Demdex ID 保持不變的情況下，您每次都會獲得相同的 MID 值。這可讓 ID 服務能夠在您所控制且已設定 ID 服務程式碼的網域間追蹤訪客。

當頁面載入時，ID 服務就會開始建立 MID。在此過程中，`visitorAPI.js` 程式碼程式庫提供的程式碼會將您的組織 ID 以事件呼叫的形式傳送至 ID 服務。ID 服務分別在 AMCV 與 Demdex Cookie 中，建立並回傳 MID 與 Demdex ID。

## Cookie 標幟

下表說明 Experience Cloud Cookie 的標幟:

| Cookie (設定者) | httpOnly | Secure | SameSite |
|--- |--- |--- |--- |
| demdex (http 回應) | 無 | 是 | &quot;無&quot; |
| AMCV (JavaScript) | 無 | 可設定 | 未設定 (預設為 Lax) |
| AMCVS (JavaScript) | 無 | 可設定 | 未設定 (預設為 Lax) |

*注意：如需使用安全屬性設定 AMCV 和 AMCVS Cookie 的相關資訊，請參閱 [secureCookie](../library/function-vars/securecookie.md) 主題。*

## 後續步驟 {#section-8db1727a63bc4ff68b495f270315d453}

請參閱 [Experience Cloud Identity Service 如何要求與設定 ID...](../introduction/id-request.md#concept-2caacebb1d244402816760e9b8bcef6a)。
