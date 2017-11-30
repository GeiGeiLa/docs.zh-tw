---
title: "ICLRStrongName::StrongNameKeyGenEx 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRStrongName.StrongNameKeyGenEx
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRStrongName::StrongNameKeyGenEx
helpviewer_keywords:
- ICLRStrongName::StrongNameKeyGenEx method [.NET Framework hosting]
- StrongNameKeyGenEx method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 1f8b59d0-5b72-45b8-ab74-c2b43ffc806e
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a303dd65cd366936d060f96899d5e218eeec9d7e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="iclrstrongnamestrongnamekeygenex-method"></a><span data-ttu-id="5c2cb-102">ICLRStrongName::StrongNameKeyGenEx 方法</span><span class="sxs-lookup"><span data-stu-id="5c2cb-102">ICLRStrongName::StrongNameKeyGenEx Method</span></span>
<span data-ttu-id="5c2cb-103">會產生新的公用/私用金鑰組與指定的金鑰大小，強式名稱使用。</span><span class="sxs-lookup"><span data-stu-id="5c2cb-103">Generates a new public/private key pair with the specified key size, for strong name use.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c2cb-104">語法</span><span class="sxs-lookup"><span data-stu-id="5c2cb-104">Syntax</span></span>  
  
```  
HRESULT StrongNameKeyGenEx (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [in]  DWORD     dwKeySize,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5c2cb-105">參數</span><span class="sxs-lookup"><span data-stu-id="5c2cb-105">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="5c2cb-106">[in]要求的金鑰容器名稱。</span><span class="sxs-lookup"><span data-stu-id="5c2cb-106">[in] The requested key container name.</span></span> <span data-ttu-id="5c2cb-107">`wszKeyContainer`必須是非空白字串或 null 以產生暫時的名稱。</span><span class="sxs-lookup"><span data-stu-id="5c2cb-107">`wszKeyContainer` must either be a non-empty string or null to generate a temporary name.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="5c2cb-108">[in]值，指定是否要保留已註冊的鍵。</span><span class="sxs-lookup"><span data-stu-id="5c2cb-108">[in] A value that specifies whether to leave the key registered.</span></span> <span data-ttu-id="5c2cb-109">支援下列值：</span><span class="sxs-lookup"><span data-stu-id="5c2cb-109">The following values are supported:</span></span>  
  
-   <span data-ttu-id="5c2cb-110">0x00000000-時使用`wszKeyContainer`以產生暫時的金鑰容器名稱為 null。</span><span class="sxs-lookup"><span data-stu-id="5c2cb-110">0x00000000 - Used when `wszKeyContainer` is null to generate a temporary key container name.</span></span>  
  
-   <span data-ttu-id="5c2cb-111">0x00000001 (`SN_LEAVE_KEY`)-指定應該向左登錄機碼。</span><span class="sxs-lookup"><span data-stu-id="5c2cb-111">0x00000001 (`SN_LEAVE_KEY`) - Specifies that the key should be left registered.</span></span>  
  
 `dwKeySize`  
 <span data-ttu-id="5c2cb-112">[in]要求的金鑰，以位元大小。</span><span class="sxs-lookup"><span data-stu-id="5c2cb-112">[in] The requested size of the key, in bits.</span></span>  
  
 `ppbKeyBlob`  
 <span data-ttu-id="5c2cb-113">[out]傳回的 public/private 金鑰組。</span><span class="sxs-lookup"><span data-stu-id="5c2cb-113">[out] The returned public/private key pair.</span></span>  
  
 `pcbKeyBlob`  
 <span data-ttu-id="5c2cb-114">[out]大小，以位元組為單位的`ppbKeyBlob`。</span><span class="sxs-lookup"><span data-stu-id="5c2cb-114">[out] The size, in bytes, of `ppbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5c2cb-115">傳回值</span><span class="sxs-lookup"><span data-stu-id="5c2cb-115">Return Value</span></span>  
 <span data-ttu-id="5c2cb-116">`S_OK`如果方法成功。否則，表示失敗的 HRESULT 值 (請參閱[常見的 HRESULT 值](http://go.microsoft.com/fwlink/?LinkId=213878)清單)。</span><span class="sxs-lookup"><span data-stu-id="5c2cb-116">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5c2cb-117">備註</span><span class="sxs-lookup"><span data-stu-id="5c2cb-117">Remarks</span></span>  
 <span data-ttu-id="5c2cb-118">需要.NET framework 1.0 和 1.1 版`dwKeySize`1024 個位元簽署為強式名稱; 組件版本 2.0 加入 2048年位元金鑰的支援。</span><span class="sxs-lookup"><span data-stu-id="5c2cb-118">The .NET Framework versions 1.0 and 1.1 require a `dwKeySize` of 1024 bits to sign an assembly with a strong name; version 2.0 adds supports for 2048-bit keys.</span></span>  
  
 <span data-ttu-id="5c2cb-119">擷取索引鍵之後，您應該呼叫[iclrstrongname:: Strongnamefreebuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md)方法，以釋放配置的記憶體。</span><span class="sxs-lookup"><span data-stu-id="5c2cb-119">After the key is retrieved, you should call the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method to release the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c2cb-120">需求</span><span class="sxs-lookup"><span data-stu-id="5c2cb-120">Requirements</span></span>  
 <span data-ttu-id="5c2cb-121">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5c2cb-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c2cb-122">**標頭：** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="5c2cb-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="5c2cb-123">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="5c2cb-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5c2cb-124">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c2cb-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c2cb-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5c2cb-125">See Also</span></span>  
 [<span data-ttu-id="5c2cb-126">StrongNameKeyGen 方法</span><span class="sxs-lookup"><span data-stu-id="5c2cb-126">StrongNameKeyGen Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md)  
 [<span data-ttu-id="5c2cb-127">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="5c2cb-127">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)