---
description: 當訪客從一個網域導覽至第二個網域時，此屬性會覆寫其Experience Cloud和Analytics ID。 若要覆寫 ID，您必須在每個網域上擁有並已實作 ID 服務。此程式碼不會讓您覆寫您未控制之網域的ID。
keywords: ID Service
seo-description: 當訪客從一個網域導覽至第二個網域時，此屬性會覆寫其Experience Cloud和Analytics ID。 若要覆寫 ID，您必須在每個網域上擁有並已實作 ID 服務。此程式碼不會讓您覆寫您未控制之網域的ID。
seo-title: overwriteCrossDomainMCIDAndAID
title: overwriteCrossDomainMCIDAndAID
uuid: 8e48127a-ac62-4ea0-9756-2a27b20ecbcf
translation-type: tm+mt
source-git-commit: bc5c81455023e22e64877bb861dfe141e158599c
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 29%

---


# overwriteCrossDomainMCIDAndAID{#overwritecrossdomainmcidandaid}

當訪客從一個網域導覽至第二個網域時，此屬性會覆寫其Experience Cloud和Analytics ID。 若要覆寫 ID，您必須在每個網域上擁有並已實作 ID 服務。此程式碼不會讓您覆寫您未控制之網域的ID。

**語法:** `Visitor.overwriteCrossDomainMCIDAndAID: true|false` (預設為 `false`)

**程式碼範例**

您的JavaScript程式碼看起來可能類似下列範例。

```js
//Call the ID service 
var visitor = Visitor.getInstance("INSERT-MARKETING-CLOUD-ID-HERE", { 
     ... 
 
     //Set overwrite property 
     overwriteCrossDomainMCIDAndAID: true 
}); 
```

**使用案例**

為了追蹤網站訪客，ID 服務會將 [!DNL Experience Cloud] ID (或 MID) 寫入瀏覽器 Cookie。下表列出並說明您可能要覆寫其他網域中ID服務所設定之現有MID的常見使用案例。

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
   <td colname="col2"> <p>假設您擁有網域 A 和 B。在此案例中，符合下列情形時，您可以設定 <span class="codeph">Visitor.overwriteCrossDomainMCIDAndAID: true</span>: </p> <p> 
     <ul id="ul_FB4704BFE7134F1688E34BF1A36627B7"> 
      <li id="li_FF71FD1FB9DD4702B675A140FAD2B481">每個網域都有自己的登陸頁面。 </li> 
      <li id="li_78F75469D32D473B93148B46D35E67F1">訪客在先前造訪網域B時已設定Cookie（和MID）。 </li> 
      <li id="li_305CE5138EEB43D3BF9CE38D1E7FFA04">如果訪客是從網域A來到網域B，您會想要一致地識別訪客。 </li> 
     </ul> </p> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>識別著陸和轉換頁面上的訪客</b> </p> </td> 
   <td colname="col2"> <p>假設您擁有網域 A 和 B。在此例中，符合下列情形時，您可以設定 <span class="codeph">Visitor.overwriteCrossDomainMCIDAndAID: true</span>: </p> 
    <ul id="ul_7BEBFD523A2F47AFB6963536E43692D0"> 
     <li id="li_71586080489340E2A6C0B263F231E3DE">網域A是著陸頁面。 </li> 
     <li id="li_4E3D3CB380EE4F1BAC4CD752194AE8DE">網域B是個別的轉換、預訂或其他工作流程結束頁面。 </li> 
     <li id="li_FB393B16CFAC4D2D9B2328EBA4573C1A">訪客在前次瀏覽網域B時已設定Cookie（和MID），您知道這些不太理想的用戶端MID，而非伺服器端MID。 </li> 
     <li id="li_36FC138530A4476A995C0F9FD73C41DE">如果訪客是從網域A來到網域B，您會想要一致地識別訪客。 </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td colname="col1"> <p> <b>識別從行動應用程式到網頁瀏覽器的訪客</b> </p> </td> 
   <td colname="col2"> <p>這個使用案例略有不同。 這包括識別從行動應用程式移至您網站的使用者。 在此情況下，您的訪客已透過行動應用程式在本機設定MID，而且他們在您網站上的Cookie中設定了不同的MID。 您可設定 <span class="codeph">Visitor.overwriteCrossDomainMCIDAndAID: true</span>，使用行動應用程式設定的 MID 覆寫瀏覽器 Cookie 中設定的 MID。 </p> </td> 
  </tr> 
 </tbody> 
</table>

