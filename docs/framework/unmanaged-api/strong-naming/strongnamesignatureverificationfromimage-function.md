---
title: "StrongNameSignatureVerificationFromImage 函式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StrongNameSignatureVerificationFromImage
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: StrongNameSignatureVerificationFromImage
helpviewer_keywords: StrongnameSignatureVerificationFromImage function [.NET Framework strong naming]
ms.assetid: 9fb144d2-07e0-4a0e-8e05-907bbb6c9e03
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ab890451c44b19be6472ae6c7da060ae71612bc5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="strongnamesignatureverificationfromimage-function"></a><span data-ttu-id="be304-102">StrongNameSignatureVerificationFromImage 函式</span><span class="sxs-lookup"><span data-stu-id="be304-102">StrongNameSignatureVerificationFromImage Function</span></span>
<span data-ttu-id="be304-103">請確認已對應到記憶體的組件適用於相關聯的公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="be304-103">Verifies that an assembly that has already been mapped to memory is valid for the associated public key.</span></span>  
  
 <span data-ttu-id="be304-104">此函式已被取代。</span><span class="sxs-lookup"><span data-stu-id="be304-104">This function has been deprecated.</span></span> <span data-ttu-id="be304-105">使用[ICLRStrongName::StrongNameVerificationFromImage](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationfromimage-method.md)方法改為。</span><span class="sxs-lookup"><span data-stu-id="be304-105">Use the [ICLRStrongName::StrongNameVerificationFromImage](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationfromimage-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be304-106">語法</span><span class="sxs-lookup"><span data-stu-id="be304-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameSignatureVerificationFromImage (  
    [in]  BYTE    *pbBase,  
    [in]  DWORD   dwLength,  
    [in]  DWORD   dwInFlags,  
    [out] DWORD   *pdwOutFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="be304-107">參數</span><span class="sxs-lookup"><span data-stu-id="be304-107">Parameters</span></span>  
 `pbBase`  
 <span data-ttu-id="be304-108">[in]對應的組件資訊清單的相對虛擬位址。</span><span class="sxs-lookup"><span data-stu-id="be304-108">[in] The relative virtual address of the mapped assembly manifest.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="be304-109">[in]以位元組為單位的對應影像大小。</span><span class="sxs-lookup"><span data-stu-id="be304-109">[in] The size, in bytes, of the mapped image.</span></span>  
  
 `dwInFlags`  
 <span data-ttu-id="be304-110">[in]影響驗證行為的旗標。</span><span class="sxs-lookup"><span data-stu-id="be304-110">[in] Flags that influence verification behavior.</span></span> <span data-ttu-id="be304-111">支援下列值：</span><span class="sxs-lookup"><span data-stu-id="be304-111">The following values are supported:</span></span>  
  
-   <span data-ttu-id="be304-112">`SN_INFLAG_FORCE_VER`(0x00000001)-強制執行驗證，即使它是需要覆寫登錄設定。</span><span class="sxs-lookup"><span data-stu-id="be304-112">`SN_INFLAG_FORCE_VER` (0x00000001) - Forces verification even if it is necessary to override registry settings.</span></span>  
  
-   <span data-ttu-id="be304-113">`SN_INFLAG_INSTALL`(0x00000002)-指定此映像上執行的第一個驗證。</span><span class="sxs-lookup"><span data-stu-id="be304-113">`SN_INFLAG_INSTALL` (0x00000002) - Specifies that this is the first verification performed on this image.</span></span>  
  
-   <span data-ttu-id="be304-114">`SN_INFLAG_ADMIN_ACCESS`(0x00000004)-指定快取可讓擁有系統管理權限的使用者存取。</span><span class="sxs-lookup"><span data-stu-id="be304-114">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) - Specifies that the cache will allow access only to users who have administrative privileges.</span></span>  
  
-   <span data-ttu-id="be304-115">`SN_INFLAG_USER_ACCESS`(0x00000008)-指定的組件都是只能由目前的使用者存取。</span><span class="sxs-lookup"><span data-stu-id="be304-115">`SN_INFLAG_USER_ACCESS` (0x00000008) - Specifies that the assembly will be accessible only to the current user.</span></span>  
  
-   <span data-ttu-id="be304-116">`SN_INFLAG_ALL_ACCESS`(0x00000010)-指定快取會提供任何保證的存取限制。</span><span class="sxs-lookup"><span data-stu-id="be304-116">`SN_INFLAG_ALL_ACCESS` (0x00000010) - Specifies that the cache will provide no guarantees of access restriction.</span></span>  
  
-   <span data-ttu-id="be304-117">`SN_INFLAG_RUNTIME`(0x80000000)-保留供內部偵錯。</span><span class="sxs-lookup"><span data-stu-id="be304-117">`SN_INFLAG_RUNTIME` (0x80000000) - Reserved for internal debugging.</span></span>  
  
 `pdwOutFlags`  
 <span data-ttu-id="be304-118">[out]其他輸出資訊的旗標。</span><span class="sxs-lookup"><span data-stu-id="be304-118">[out] A flag for additional output information.</span></span> <span data-ttu-id="be304-119">支援下列值：</span><span class="sxs-lookup"><span data-stu-id="be304-119">The following value is supported:</span></span>  
  
-   <span data-ttu-id="be304-120">`SN_OUTFLAG_WAS_VERIFIED`(0x00000001)-此值設為`false`來指定驗證成功登錄設定所造成。</span><span class="sxs-lookup"><span data-stu-id="be304-120">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001) - This value is set to `false` to specify that the verification succeeded due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="be304-121">傳回值</span><span class="sxs-lookup"><span data-stu-id="be304-121">Return Value</span></span>  
 <span data-ttu-id="be304-122">`true`如果成功地完成。否則， `false`。</span><span class="sxs-lookup"><span data-stu-id="be304-122">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="be304-123">備註</span><span class="sxs-lookup"><span data-stu-id="be304-123">Remarks</span></span>  
 <span data-ttu-id="be304-124">如果`StrongNameSignatureVerificationFromImage`函式未順利完成，請呼叫[StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md)函式可擷取的最後一個產生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="be304-124">If the `StrongNameSignatureVerificationFromImage` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be304-125">需求</span><span class="sxs-lookup"><span data-stu-id="be304-125">Requirements</span></span>  
 <span data-ttu-id="be304-126">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="be304-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be304-127">**標頭：** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="be304-127">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="be304-128">**程式庫：**包含做為 mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="be304-128">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="be304-129">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be304-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be304-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="be304-130">See Also</span></span>  
 [<span data-ttu-id="be304-131">StrongNameSignatureVerificationFromImage 方法</span><span class="sxs-lookup"><span data-stu-id="be304-131">StrongNameSignatureVerificationFromImage Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationfromimage-method.md)  
 [<span data-ttu-id="be304-132">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="be304-132">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)