---
title: '&lt;Sessionsecuritytokencache>&gt;'
ms.date: 03/30/2017
ms.assetid: d43e676c-0153-485c-ab31-0257a2db7507
author: BrucePerlerMS
ms.openlocfilehash: b812673ac1c015adde357d3c0707d85643aad3e9
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/27/2018
ms.locfileid: "47401366"
---
# <a name="ltsessionsecuritytokencachegt"></a>&lt;Sessionsecuritytokencache>&gt;
註冊工作階段權杖快取服務或安全性權杖處理常式集合。  
  
 \<system.identityModel>  
\<identityConfiguration>  
\<快取 >  
\<Sessionsecuritytokencache> >  
  
## <a name="syntax"></a>語法  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
      <sessionSecurityTokenCache type=xs:string>  
      </sessionSecurityTokenCache>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|類型|衍生自類型<xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>類別。|  
  
### <a name="child-elements"></a>子元素  
 無  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<快取 >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|註冊服務或安全性權杖處理常式集合所使用的快取。|  
  
## <a name="example"></a>範例  
 下列 XML 會說明用於保存工作階段安全性權杖的自訂快取的組態 (<xref:System.IdentityModel.Tokens.SessionSecurityToken>)。 組態取自`ClaimsAwareWebFarm`範例。 如需有關此範例的詳細資訊，請參閱 < [WIF 程式碼範例索引](../../../../../docs/framework/security/wif-code-sample-index.md)。  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>
