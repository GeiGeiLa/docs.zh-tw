---
title: '&lt;endpointDiscovery&gt;'
ms.date: 03/30/2017
ms.assetid: 70812717-888a-4748-9640-0df6715ff029
ms.openlocfilehash: 0dde8150632c5d8a7bcea3dbeffe70b380d3a322
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2018
ms.locfileid: "50183837"
---
# <a name="ltendpointdiscoverygt"></a>&lt;endpointDiscovery&gt;
指定端點的各種探索設定，例如其探索能力、範圍以及中繼資料的任何自訂延伸模組。  
  
\<system.ServiceModel>  
\<行為 >  
\<endpointBehaviors>  
\<行為 >  
\<endpointDiscovery >  
  
## <a name="syntax"></a>語法  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="String">
      <endpointDiscovery enabled="Boolean">
        <scopes>
          <add scope="URI"/>
        </scopes>
        <extensions />
      </endpointDiscovery>
    </behavior>
  </endpointBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|enabled|布林值，指定是否在此端點上啟用探索能力。 預設為 `false`。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<範圍 >](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)|端點之範圍 URI 的集合。 有一個以上的範圍 URI 與單一端點產生關聯。|  
|[\<擴充功能 >](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions.md) [的\<endpointDiscovery >]|XML 項目的集合，這個集合可讓您指定端點要發行的自訂中繼資料。|  
|\<類型 >|要搜尋之介面的集合。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<行為 >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|指定行為項目。|  
|||  
  
## <a name="remarks"></a>備註  
 加入至端點的行為組態 (且 `enabled` 屬性設為 `true`) 時，這個組態項目會啟用其探索能力。 此外，您可以使用[\<範圍 >](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)子項目，若要指定自訂範圍可用來在查詢期間篩選服務端點的 Uri，以及[\<擴充功能 >](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions.md)子項目，指定應與標準的可探索中繼資料 （EPR、 ContractTypeName、 BindingName、 範圍及 ListenURI） 一起發行的自訂中繼資料。  
  
 這個組態項目是取決於[ \<serviceDiscovery >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md)提供探索能力服務層級控制項的項目。 這表示，如果，則會忽略這個項目設定[ \<serviceDiscovery >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md)不存在於組態中。  
  
## <a name="example"></a>範例  
 下列組態範例指定用於要針對端點發行的篩選範圍及擴充中繼資料。  
  
```xml  
<services>  
  <service name="CalculatorService"  
           behaviorConfiguration="CalculatorServiceBehavior">  
     <endpoint binding="basicHttpBinding"  
              address="calculator"  
              contract="ICalculatorService"  
              behaviorConfiguration="calculatorEndpointBehavior" />  
  </service>  
</services>  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      <serviceDiscovery />  
    </behavior>  
  </serviceBehaviors>  
  <endpointBehaviors>  
    <behavior name="calculatorEndpointBehavior">  
      <endpointDiscovery enabled="true">  
        <scopes>  
          <add scope="http://contoso/test1"/>  
          <add scope="http://contoso/test2"/>  
        </scopes>  
        <extensions>  
          <e:Publisher xmlns:e="http://example.org">  
            <e:Name>The Example Organization</e:Name>  
            <e:Address>One Example Way, ExampleTown, EX 12345</e:Address>  
            <e:Contact>support@example.org</e:Contact>  
          </e:Publisher>  
          <AnotherCustomMetadata>Custom Metadata</AnotherCustomMetadata>  
        </extensions>  
      </endpointDiscovery>  
    </behavior>  
  </endpointBehaviors>  
</behaviors>  
```  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
