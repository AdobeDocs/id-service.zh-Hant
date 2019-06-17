---
description: ID 服務使用您的組織 ID、Experience Cloud AMCV Cookie，以及 Demdex Cookie，為您的網站訪客建立並儲存不重複的永久識別碼。這些 Cookie 可以讓 ID 服務追蹤您不同網域上的訪客，並且讓您在不同的 Experience Cloud 解決方案間共用資料。
keywords: 點陣化；ID服務
seo-description: ID 服務使用您的組織 ID、Experience Cloud AMCV Cookie，以及 Demdex Cookie，為您的網站訪客建立並儲存不重複的永久識別碼。這些 Cookie 可以讓 ID 服務追蹤您不同網域上的訪客，並且讓您在不同的 Experience Cloud 解決方案間共用資料。
seo-title: Cookie 和 Experience Cloud ID 服務
title: Cookie 和 Experience Cloud ID 服務
uuid: c5cbd235-37ee-4605-8792-b1 a991 e190 ad
translation-type: tm+mt
source-git-commit: bb687c1cd14aae7faef2565dcf9d041a1c06e3bd

---


# Cookie 和 Experience Cloud ID 服務{#cookies-and-the-experience-cloud-id-service}

ID 服務使用您的組織 ID、Experience Cloud AMCV Cookie，以及 Demdex Cookie，為您的網站訪客建立並儲存不重複的永久識別碼。這些 Cookie 可以讓 ID 服務追蹤您不同網域上的訪客，並且讓您在不同的 Experience Cloud 解決方案間共用資料。

## 瞭解ID服務Cookie {#section-f438168beaec409ab8b2cc58bd021e26}

ID 服務有賴 AMCV、AMCVS 和 Demdex Cookie 才能順利運作。這些 Cookie 只是儲存 ID 服務所使用之資料的檔案。這些 ID 服務與其他網站或服務儲存在瀏覽器中的第一方或第三方 Cookie 相同，都不具危險性和惡意，且也遵守與管理其他第一方或第三方 Cookie 相同的規則。如需ID服務使用Cookie的詳細資訊，請參閱下列幾節。

**ID服務Cookie可執行的動作**

* 為您的網站訪客設定並儲存唯一的 ID (MID)。
* 沿用此唯一 ID，以便 ID 服務與其他 Experience Cloud 解決方案收集和共用資料。
* 在您的網域間追蹤使用者。不過，您需要擁有這些其他網域，並在其中部署了 ID 服務程式碼。

** ID Service Ookies無法執行**

* 儲存、傳輸或執行電腦病毒。
* 存取或儲存個人識別資訊 (PII)，例如：您的電子郵件地址。
* 控制電腦的軟硬體。
* 造成電腦不穩定或是產生效能問題。
* 追蹤網站上沒有使用 ID 服務的使用者。

## AMCV Cookie {#section-c55af54828dc4cce89f6118655d694c8}

ID服務所設定Cookie的下列屬性。

**名稱**

AMCV Cookie名稱遵循語法 `AMCV_<variable name>@AdobeOrg`。在名稱中， `<variable name>` 元素是Experience Cloud組織ID部分的預留位置。此 ID 會由 ID 服務程式碼中的 `Visitor.getInstance` 函數傳遞至 DCS。

完整格式的 Cookie 名稱類似以下:

```
AMCV_1FD6776A524453CC0A490D44%40AdobeOrg
```

**內容**

AMCV Cookie 包含 Experience Cloud 訪客 ID 或 MID。MID會儲存在遵循此語法的索引鍵值配對 `mid|<Experience Cloud ID>`中。

完整格式的機碼值組類似以下:

```
mid|20265673158980419722735089753036633573
```

此永久識別碼會啟用跨解決方案資料共用。

**網域**

已在瀏覽器的第一方網域中設定 AMCV Cookie。這表示在使用者目前造訪網站的網域中已設定此 Cookie。因此，ID 服務程式碼與其他 Experience Cloud 程式碼程式庫可讀取儲存在 AMCV Cookie 中的 MID。

然而，因為已在第一方網域中設定 AMCV Cookie，所以無法用它來追蹤與識別不同網域的使用者。相反地，當網站訪客導覽至不同網域時，ID 服務將依賴組織 ID 與 Demdex ID，才能傳回正確的 MID。

## AMCVS Cookie {#section-92a9454f1ac645948f9059b9fad928bf}

**名稱**

AMCV Cookie名稱遵循語法 `AMCVS_####@AdobeOrg`。在名稱中，#### 元素是 Experience Cloud 組織 ID 部分的預留位置。此 ID 會由 ID 服務程式碼中的 `theVisitor.getInstance` 函數傳入 DCS。

完整格式的 Cookie 名稱類似以下:

```
AMCVS_1FD6776A524453CC0A490D44%40AdobeOrg
```

**內容**

AMCVS Cookie 會作為標幟，指出工作階段已初始化。當工作階段結束時，其值始終 `1` 是並中斷。

**網域**

已在瀏覽器的第一方網域中設定 AMCVS Cookie。這表示在使用者目前造訪網站的網域中已設定此 Cookie。

![](assets/AMCVS-cookie.png)

## Demdex Cookie {#section-7ff7d96d6e4141b08a84a75a63d7814c}

下表列出並定義 Demdex Cookie 的一些重要屬性。

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
   <td colname="col2"> <p>已在瀏覽器的第三方 demdex.net 網域中設定 Demdex Cookie。此網域有別於使用者目前造訪的網站。 </p> <p>與第一方網域不同，AMCV Cookie、Demdex Cookie 與 ID 會可在不同網域中持續存在。Demdex ID 與您的組織 ID 是允許 ID 服務回傳並識別具有正確訪客 ID 的網站訪問者的通用值。 </p> </td> 
  </tr> 
 </tbody> 
</table>

如需相關資訊，請參閱 [「瞭解Demdex網域的呼叫」](https://marketing.adobe.com/resources/help/en_US/aam/demdex-calls.html)。

## 產生 Experience Cloud ID {#section-15f69c0bac394b4b9966a23fbc586d17}

Experience Cloud ID (MID) 是依照組織 ID 和 demdex ID 利用數學公式計算出來。只要這些 ID 保持不變，為特定用戶產生正確的 MID 只是單純的數學問題。每次使用相同的組織 ID 與 Demdex ID，就能獲得相同的 MID 值。這使得 ID 服務可以追蹤由您控制以及使用 ID 服務程式碼設定之網域的訪客。

ID 服務在您的頁面載入時隨即開始建立 MID。在此過程中，`visitorAPI.js` 程式碼資料庫提供的程式碼會將您的組織 ID 以事件呼叫的形式傳送至 ID 服務。ID 服務分別在 AMCV 與 Demdex Cookie 中，建立並回傳 MID 與 Demdex ID。

## 下一步 {#section-8db1727a63bc4ff68b495f270315d453}

瞭解 [Experience Cloud ID服務要求和設定ID….](../mcvid-introduction/mcvid-id-request.md#concept-2caacebb1d244402816760e9b8bcef6a)
