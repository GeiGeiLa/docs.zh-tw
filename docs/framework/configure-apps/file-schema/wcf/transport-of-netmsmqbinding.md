---
title: '&lt;netMsmqBinding&gt; 的 &lt;transport&gt;'
ms.date: 03/30/2017
ms.assetid: 72e1b338-39f0-4af1-a5d9-7a2fb79f6a0b
ms.openlocfilehash: 06114990f931eb06d064fcec425e9ab42507c932
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2018
ms.locfileid: "48582303"
---
# <a name="lttransportgt-of-ltnetmsmqbindinggt"></a>&lt;netMsmqBinding&gt; 的 &lt;transport&gt;
定義傳輸安全性設定。  
  
 \<system.ServiceModel>  
\<繫結 >  
\<netMsmqBinding>  
\<繫結 >  
\<安全性 >  
\<transport>  
  
## <a name="syntax"></a>語法  
  
```xml  
<netMsmqBinding>  
    <binding>  
    <security>  
         <transport msmqAuthenticationMode="None/WindowsDomain/Certificate"  
            msmqEncryptionAlgorithm="RC4Stream/AES"  
            msmqProtectionLevel="None/Sign/EncryptAndSign"  
            msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />  
    </security>  
   </binding>  
</netMsmqBinding>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|msmqAuthenticationMode|指定 MSMQ 傳輸必須如何驗證訊息。 有效值包括以下的值：<br /><br /> -None： 沒有驗證。<br />-WindowsDomain： 驗證機制使用 Active Directory 擷取訊息相關聯的安全性識別碼的 X.509 憑證。 接著這會用於檢查佇列的 ACL，以確保使用者具有寫入佇列的權限。<br />憑證： 通道會從憑證存放區擷取憑證。<br /><br /> 預設為 `WindowsDomain`。<br /><br /> 如果這個屬性設定為 `None`，則 `msmqProtectionLevel` 屬性也必須設定為 `None`。 此屬性的型別為 <xref:System.ServiceModel.MsmqAuthenticationMode>。|  
|msmqEncryptionAlgorithm|指定演算法，該演算法用於在訊息佇列管理員之間傳輸訊息時，在線上加密訊息。 有效值包括以下的值：<br /><br /> -RC4Stream<br />AES<br />-預設值是`RC4Stream`。 此屬性的型別為 <xref:System.ServiceModel.MsmqEncryptionAlgorithm>。|  
|msmqProtectionLevel|指定在 MSMQ 傳輸層級上保護訊息的方式。 加密可確保訊息的完整性，而簽署和加密可確保訊息的完整性和不可否認性。 也就是，訊息確實來自寄件者，且寄件者就是他本人。 有效值包括以下的值：<br /><br /> -None： 無保護。<br />簽署： 簽署訊息。<br />-EncryptAndSign： 訊息會經過加密及簽署。<br />-預設值是`Sign`。|  
|msmqSecureHashAlgorithm|指定計算訊息摘要時使用的雜湊演算法。 有效值包括以下的值：<br /><br /> -   MD5<br />-   SHA1<br />-   SHA256<br />-   SHA512<br /><br /> 預設為 `SHA1`。 此屬性的型別為 <xref:System.ServiceModel.MsmqSecureHashAlgorithm>。|  
  
### <a name="child-elements"></a>子元素  
 無  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netmsmqbinding.md)|定義佇列傳輸的傳輸安全性設定。|  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>  
 <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.NetMsmqSecurity.Transport%2A>  
 <xref:System.ServiceModel.MsmqTransportSecurity>  
 [WCF 中的佇列](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)  
 [保護服務和用戶端的安全](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [繫結](../../../../../docs/framework/wcf/bindings.md)  
 [設定系統提供的繫結](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [使用繫結設定服務與用戶端](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [\<繫結 >](../../../../../docs/framework/misc/binding.md)
