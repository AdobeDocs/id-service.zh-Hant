---
description: 訪客ID服務會使用您的IMS組織ID、CX Enterprise AMCV Cookie及Demdex Cookie，為您的網站訪客建立並儲存唯一的永久性識別碼。 這些Cookie可讓訪客ID服務追蹤您不同網域的訪客，並啟用不同CX企業解決方案之間的資料共用。
keywords: playstation；訪客ID服務
title: Cookie與Adobe訪客ID服務
exl-id: 727c6381-56b9-44b8-8e59-355d072769be
TQID: https://experienceleague.adobe.com/iLOFGQ9t-DqYfqOZs3K5yZI7903dMPEjANaJ7lH8K0o
product_v2:
  - id: e1971122-7081-4556-9222-8a31bd71800c
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 990
ht-degree: 42%

---

# Cookie與Adobe訪客ID服務{#cookies-and-the-experience-cloud-id-service}

訪客ID服務會使用您的IMS組織ID、CX Enterprise AMCV Cookie及Demdex Cookie，為您的網站訪客建立並儲存唯一的永久性識別碼。 這些Cookie可讓訪客ID服務追蹤您不同網域的訪客，並啟用不同CX企業解決方案之間的資料共用。

## 瞭解訪客ID服務Cookie {#section-f438168beaec409ab8b2cc58bd021e26}

訪客ID服務需仰賴AMCV、AMCVS和Demdex Cookie才能正常運作。 這些Cookie只是儲存訪客ID服務所使用資料的檔案。 這些訪客ID服務Cookie並非危險、惡意或不同於網站或服務儲存於瀏覽器中的其他第一方或第三方Cookie，且遵循的規則與其他第一方和第三方Cookie相同。 請參閱下列各節，以取得有關訪客ID服務所使用Cookie的詳細資訊。

### 訪客ID服務Cookie的功能

* 設定並儲存網站訪客的唯一 ID (MID)。
* 儲存此唯一ID，讓訪客ID服務可以收集資料並與其他CX Enterprise解決方案共用。
* 跨網域追蹤用戶。 不過，您必須擁有其他網域，並在這些網域上部署訪客ID服務程式碼，才能進行此追蹤。

### 訪客ID服務Cookie無法執行的動作

* 儲存、傳輸或執行電腦病毒。
* 存取或儲存個人識別資訊 (PII)，例如：您的電子郵件地址。
* 控制電腦硬體或軟體。
* 使電腦不穩定或導致效能問題。
* 在未使用訪客ID服務的網站上追蹤使用者。

## AMCV Cookie {#section-c55af54828dc4cce89f6118655d694c8}

訪客ID服務設定的Cookie屬性如下。

**名稱**

AMCV Cookie 名稱遵循以下語法：`AMCV_<variable name>@AdobeOrg`。 在名稱中，`<variable name>`元素是IMS組織ID部分的預留位置。 訪客ID服務程式碼中的`Visitor.getInstance`函式會將此ID傳入DCS。

完整格式的 Cookie 名稱類似以下:

```
AMCV_1FD6776A524453CC0A490D44%40AdobeOrg
```

**內容**

AMCV Cookie包含ECID或MID。 MID 儲存在遵循下列語法的機碼-值組中：`MCMID|<ECID>`。

完整格式的機碼值組類似以下:

```
MCMID|20265673158980419722735089753036633573
```

此永續性識別碼可用於跨解決方案的資料共用。

**網域**

AMCV Cookie 設定於瀏覽器的第一方網域中。 這表示此 Cookie 設定於用戶目前造訪之網站的網域中。 因此，訪客ID服務程式碼和其他CX Enterprise程式碼程式庫可讀取儲存在AMCV Cookie中的MID。

但由於 AMCV Cookie 設定於第一方網域中，因此無法跨不同的網域追蹤和識別用戶。 當網站訪客導覽至不同網域時，訪客ID服務會仰賴IMS組織ID和Demdex ID傳回正確的MID。

## AMCVS Cookie {#section-92a9454f1ac645948f9059b9fad928bf}

**名稱**

AMCVS Cookie 名稱會遵循 `AMCVS_####@AdobeOrg` 語法。 在名稱中，####元素是IMS組織ID部分的預留位置。 訪客ID服務程式碼中的`theVisitor.getInstance`函式會將此ID傳入DCS。

完整格式的 Cookie 名稱類似以下:

```
AMCVS_1FD6776A524453CC0A490D44%40AdobeOrg
```

**內容**

AMCVS Cookie 可作為指出工作階段已初始化的旗標。 其值一律為 `1`，直到工作階段結束為止。

**網域**

AMCVS Cookie 設定於瀏覽器的第一方網域中。 這表示此 Cookie 設定於用戶目前造訪之網站的網域中。

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
   <td colname="col2"> <p>Demdex Cookie 設定於瀏覽器的第三方 demdex.net 網域中。 此網域與用戶目前造訪的網站不同。 </p> <p>不同於第一方 AMCV Cookie，Demdex Cookie 和 ID 會跨不同的網域而持續保存。 Demdex ID和您的IMS組織ID是常見的值，可讓訪客ID服務傳回並識別具有正確訪客ID的網站訪客。 </p> </td> 
  </tr> 
 </tbody> 
</table>

如需有關 Demdex 披露事項的資訊，請瀏覽 [Audience Manager 裝置儲存披露事項](https://aam-iab-tcf-vendor.s3.amazonaws.com/aam_device_storage_disclosures.json)。

如需相關資訊，請閱讀[了解向 Demdex 網域進行的呼叫](https://experienceleague.adobe.com/docs/audience-manager/user-guide/reference/demdex-calls.html?lang=zh-Hant)一文。

## 產生ECID {#section-15f69c0bac394b4b9966a23fbc586d17}

ECID是以數學方式從IMS組織ID和Demdex ID計算而得。 只要這些 ID 保持不變，為特定用戶產生正確的 MID 就只是數學問題。 使用相同的IMS組織ID和Demdex ID，您每次都會獲得相同的MID值。 這可讓訪客ID服務在您控制且已設定訪客ID服務程式碼的網域間追蹤訪客。

當頁面載入時，訪客ID服務就會開始建立MID。 在此過程中，`VisitorAPI.js`程式碼程式庫提供的程式碼會將您的IMS組織ID以事件呼叫的形式傳送至訪客ID服務。 訪客ID服務分別在AMCV和Demdex Cookie中，建立並傳回MID和Demdex ID。

## Cookie 標幟

下表說明CX Enterprise Cookie的標幟：

| Cookie (設定者) | httpOnly | Secure | SameSite |
|--- |--- |--- |--- |
| demdex (http 回應) | 無 | 是 | &quot;無&quot; |
| AMCV (JavaScript) | 無 | 可設定 | 未設定 (預設為 Lax) |
| AMCVS (JavaScript) | 無 | 可設定 | 未設定 (預設為 Lax) |

*注意：如需使用安全屬性設定 AMCV 和 AMCVS Cookie 的相關資訊，請參閱 [secureCookie](../library/function-vars/securecookie.md) 主題。*

## 後續步驟 {#section-8db1727a63bc4ff68b495f270315d453}

請參閱[訪客ID服務如何要求與設定ID...](../introduction/id-request.md#concept-2caacebb1d244402816760e9b8bcef6a)。

