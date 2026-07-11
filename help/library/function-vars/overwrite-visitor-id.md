---
description: 當訪客從某個網域導覽至第二個網域時，此屬性會覆寫訪客的ECID和Analytics ID。 若要覆寫ID，您必須在每個網域上擁有並已實作訪客ID服務。 此程式碼無法讓您在您沒有控制權的網域上覆寫 ID。
keywords: 訪客 ID 服務
title: overwriteCrossDomainMCIDAndAID
exl-id: 726261b1-c8d0-4b12-b0cb-52d7e21e7fac
TQID: https://experienceleague.adobe.com/dJUuTbc9zspC93WZrRaxBsp2BgpbE-z-iUuePQXGTeY
product_v2: id: e1971122-7081-4556-9222-8a31bd71800c
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 09ee359440c122702a6ce83708c98af3862c9cc9
workflow-type: tm+mt
source-wordcount: 404
ht-degree: 71%

---

# overwriteCrossDomainMCIDAndAID{#overwritecrossdomainmcidandaid}

當訪客從某個網域導覽至第二個網域時，此屬性會覆寫訪客的ECID和Analytics ID。 若要覆寫ID，您必須在每個網域上擁有並已實作訪客ID服務。 此程式碼無法讓您在您沒有控制權的網域上覆寫 ID。

**語法：**`Visitor.overwriteCrossDomainMCIDAndAID: true|false` (預設為 `false`)

**程式碼範例**

您的 JavaScript 程式碼可能與以下範例類似。

```js
//Call the Visitor ID Service 
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ID-HERE", { 
     ... 
 
     //Set overwrite property 
     overwriteCrossDomainMCIDAndAID: true 
}); 
```

**使用案例**

為了追蹤網站訪客，訪客ID服務會將ECID （或MID）寫入瀏覽器Cookie。 下表列出及說明常見使用案例，您在這些案例中可能會想要覆寫另一個網域中訪客ID服務設定的現有MID。

<table id="table_FC1AF6551D6646E0BF1C4FB7C1316EBB"> 
 <thead> 
  <tr> 
   <th colname="col1" class="entry"> 使用案例 </th> 
   <th colname="col2" class="entry"> 說明 </th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td colname="col1"> <p> <b>識別不同網域登陸頁面上的訪客</b> </p> </td> 
   <td colname="col2"> <p>假設您擁有網域 A 和 B。在此案例中，符合下列情形時，您可以設定 <span class="codeph">Visitor.overwriteCrossDomainMCIDAndAID: true</span>： </p> <p> 
     <ul id="ul_FB4704BFE7134F1688E34BF1A36627B7"> 
      <li id="li_FF71FD1FB9DD4702B675A140FAD2B481">每個網域都有自己的登陸頁面。 </li> 
      <li id="li_78F75469D32D473B93148B46D35E67F1">訪客已經有上一次造訪網域 B 時所設定的 Cookie (和 MID)。 </li> 
      <li id="li_305CE5138EEB43D3BF9CE38D1E7FFA04">如果訪客從網域 A 前來網域 B，您希望可以一致地識別他。 </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>識別不同登陸和轉換頁面上的訪客</b> </p> </td> 
   <td colname="col2"> <p>假設您擁有網域 A 和 B。在此例中，符合下列情形時，您可以設定 <span class="codeph">Visitor.overwriteCrossDomainMCIDAndAID: true</span>： </p> 
    <ul id="ul_7BEBFD523A2F47AFB6963536E43692D0"> 
     <li id="li_71586080489340E2A6C0B263F231E3DE">網域 A 為登陸頁面。 </li> 
     <li id="li_4E3D3CB380EE4F1BAC4CD752194AE8DE">網域 B 是個別轉換、預訂或其他工作流程結束頁面。 </li> 
     <li id="li_FB393B16CFAC4D2D9B2328EBA4573C1A">訪客已經有上一次造訪網域 B 時所設定的 Cookie (和 MID)，而且您知道這些是不太理想的用戶端 MID，而不是伺服器端 MID。 </li> 
     <li id="li_36FC138530A4476A995C0F9FD73C41DE">如果訪客從網域 A 前來網域 B，您希望可以一致地識別他。 </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>識別從行動應用程式到網頁瀏覽器的訪客</b> </p> </td> 
   <td colname="col2"> <p>此使用案例稍微有些不同。 它需要在用戶從行動應用程式移至您的網站時加以識別。 在此情況下，您的訪客已經有行動應用程式在本機設定的 MID，而且他們有您網站上的 Cookie 中所設定的不同 MID。 您可設定 <span class="codeph">Visitor.overwriteCrossDomainMCIDAndAID: true</span>，使用行動應用程式設定的 MID 覆寫瀏覽器 Cookie 中設定的 MID。 </p> </td> 
  </tr> 
 </tbody> 
</table>

