---
description: 在網站上啟用選擇加入後，請使用瀏覽器中的開發人員工具，運用驗證方法測試該服務是否順利運作。
seo-description: 在網站上啟用選擇加入後，請使用瀏覽器中的開發人員工具，運用驗證方法測試該服務是否順利運作。
seo-title: 驗證選擇加入服務
title: 驗證選擇加入服務
uuid: 1743360a-d757-4e50-8697-0fa92b302cbc
translation-type: tm+mt
source-git-commit: 0c300aa92991c0dec2ccdeeb34f9d886dcac7671
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 27%

---


# 驗證選擇加入服務{#validating-opt-in-service}

在網站上啟用選擇加入後，請使用瀏覽器中的開發人員工具，運用驗證方法測試該服務是否順利運作。

## 使用案例 1: 啟用選擇加入服務 {#section-c8fe1ee3711b420c8186c7057abbecb3}

```
Visitor.getInstance({{YOUR_ORG_ID}}, { 
    doesOptInApply: true 
});
```

![](assets/use_case_1_1.png)

載入頁面前，請清除快取和Cookie。

在Chrome中，在網頁上按一下滑鼠右鍵，然後選取「檢查」。 如上述螢幕擷取中所示，請選取「 *網路* 」索引標籤，以檢視從瀏覽器提出的要求。

在上述範例中，我們在頁面上安裝了下列Adobe JS標籤：ECID、AAM、Analytics和Target。

**如何證實選擇加入順利運作:**

您不應看到任何對Adobe伺服器的要求：

* demdex.net/id
* demdex.net/event
* omtrdc.net/b/ss
* omtrdc.net/m2
* everesttech.net

>[!NOTE]
>
>您可能會看到目標為 `http://dpm.demdex.net/optOutStatus` 的呼叫，這是「唯讀」端點，用來擷取訪客的選擇退出狀態。此端點不會產生任何建立的第三方Cookie，也不會從頁面收集任何資訊。

您不應看到Adobe標籤所建立的任何Cookie:(AMCV_{{YOUR_ORG_ID}}、mbox、demdex、s_cc、s_sq、everest_g_v2、everest_session_v2)

在Chrome中，前往「應用程 *式* 」標籤，展開「儲存」下的「Cookie ****」區段，並選取您網站的網域名稱：

![](assets/use_case_1_2.png)

## 使用案例2:啟用選擇加入和儲存 {#section-bd28326f52474fa09a2addca23ccdc0f}

```
Visitor.getInstance({{YOUR_ORG_ID}}, { 
    doesOptInApply: true, 
    isOptInStorageEnabled: true 
});
```

使用案例2的唯一差異是，您會看 *到新Cookie* ，其中包含訪客提供的「選擇加入」權限： **adobeujs-optin**

## 使用案例3:啟用選擇加入和預先核准Adobe Analytics {#section-257fe582b425496cbf986d0ec12d3692}

```
var preApproveAnalytics = {}; 
preApproveAnalytics[adobe.OptInCategories.ANALYTICS] = true;

Visitor.getInstance({{YOUR_ORG_ID}}, { 
    doesOptInApply: true, 
    preOptInApprovals: preApproveAnalytics 
});
```

由於Adobe Analytics已預先獲准加入，您會在「網路」索引標籤中看到追蹤伺服器的要求：

![](assets/use_case_3_1.png)

而且您會在「應用程式」索引標籤中看到Analytics Cookie:

![](assets/use_case_3_2.png)

## 使用案例4:啟用選擇加入和IAB {#section-64331998954d4892960dcecd744a6d88}

```
Visitor.getInstance({{YOUR_ORG_ID}}, { 
    doesOptInApply: true, 
    isIabContext: true 
});
```

**如何在頁面上檢視您目前的IAB同意：**

開啟開發人員工具並選取「 *Console* 」標籤。 貼上下列程式碼片段，然後按Enter:

```
<codeblock>
  __cmp("getVendorConsents", null, function (vendorConsents) { 
     console.log("Vendor Consent:", vendorConsents); }) 
</codeblock>  
  
```

以下是核准目的1、2和5且核准Audience Manager廠商ID時的輸出範例：

* demdex.net/id:此呼叫的出現證明ECID已向demdex.net要求ID
* demdex.net/event:此呼叫的出現證明DIL資料收集呼叫正如預期運作。
* demdex.net/dest5.html:此呼叫的出現證明ID同步正在觸發。

![](assets/use_case_4_1.png)

如果下列其中一項無效，您將看不到任何對Adobe伺服器的要求，也看不到任何Adobe Cookie:

* 未核准用途1、2或5。
* Audience Manager廠商ID未核准。