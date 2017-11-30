---
title: "IMetaDataEmit::DefineMethodImpl 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DefineMethodImpl
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DefineMethodImpl
helpviewer_keywords:
- DefineMethodImpl method [.NET Framework metadata]
- IMetaDataEmit::DefineMethodImpl method [.NET Framework metadata]
ms.assetid: 9dcc8b3d-33ee-4c7c-8d6f-322c57b94a0f
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 126cf950b71ed2325006b14927ae95517f7c6dc6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitdefinemethodimpl-method"></a><span data-ttu-id="25564-102">IMetaDataEmit::DefineMethodImpl 方法</span><span class="sxs-lookup"><span data-stu-id="25564-102">IMetaDataEmit::DefineMethodImpl Method</span></span>
<span data-ttu-id="25564-103">建立實作繼承自介面方法的定義，並傳回該方法實作定義的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="25564-103">Creates a definition for implementation of a method inherited from an interface, and returns a token to that method-implementation definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25564-104">語法</span><span class="sxs-lookup"><span data-stu-id="25564-104">Syntax</span></span>  
  
```  
HRESULT DefineMethodImpl (   
    [in]  mdTypeDef         td,   
    [in]  mdToken           tkBody,   
    [in]  mdToken           tkDecl  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="25564-105">參數</span><span class="sxs-lookup"><span data-stu-id="25564-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="25564-106">[in]`mdTypedef`語彙基元的實作類別。</span><span class="sxs-lookup"><span data-stu-id="25564-106">[in] The `mdTypedef` token of the implementing class.</span></span>  
  
 `tkBody`  
 <span data-ttu-id="25564-107">[in]`mdMethodDef`或`mdMethodRef`語彙基元的程式碼主體。</span><span class="sxs-lookup"><span data-stu-id="25564-107">[in] The `mdMethodDef` or `mdMethodRef` token of the code body.</span></span>  
  
 `tkDecl`  
 <span data-ttu-id="25564-108">[in]`mdMethodDef`或`mdMethodRef`所實作的介面方法的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="25564-108">[in] The `mdMethodDef` or `mdMethodRef` token of the interface method being implemented.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25564-109">需求</span><span class="sxs-lookup"><span data-stu-id="25564-109">Requirements</span></span>  
 <span data-ttu-id="25564-110">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="25564-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25564-111">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="25564-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="25564-112">**程式庫：**做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="25564-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="25564-113">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25564-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25564-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="25564-114">See Also</span></span>  
 [<span data-ttu-id="25564-115">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="25564-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="25564-116">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="25564-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)