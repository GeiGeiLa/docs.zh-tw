---
title: "IMetaDataAssemblyEmit::DefineFile 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyEmit.DefineFile
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyEmit::DefineFile
helpviewer_keywords:
- IMetaDataAssemblyEmit::DefineFile method [.NET Framework metadata]
- DefineFile method [.NET Framework metadata]
ms.assetid: c065aadf-c1ca-4981-bde6-597042cb29c4
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: f3be44603eb16c6e74b34c0f569fc5bb11264ca0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="imetadataassemblyemitdefinefile-method"></a><span data-ttu-id="c1f1f-102">IMetaDataAssemblyEmit::DefineFile 方法</span><span class="sxs-lookup"><span data-stu-id="c1f1f-102">IMetaDataAssemblyEmit::DefineFile Method</span></span>
<span data-ttu-id="c1f1f-103">為這個組件所參考的組件，建立包含其中繼資料的 `File` 中繼資料結構，並且傳回關聯的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="c1f1f-103">Creates a `File` metadata structure containing metadata for assembly referenced by this assembly, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1f1f-104">語法</span><span class="sxs-lookup"><span data-stu-id="c1f1f-104">Syntax</span></span>  
  
```  
HRESULT DefineFile (  
    [in]  LPCWSTR        szName,   
    [in]  const void     *pbHashValue,   
    [in]  ULONG          cbHashValue,  
    [in]  DWORD          dwFileFlags,  
    [out] mdFile         *pmdf  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c1f1f-105">參數</span><span class="sxs-lookup"><span data-stu-id="c1f1f-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="c1f1f-106">[in]要使用的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="c1f1f-106">[in] The name of the file to be consumed.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="c1f1f-107">[in]與組件相關聯的雜湊資料指標。</span><span class="sxs-lookup"><span data-stu-id="c1f1f-107">[in] A pointer to the hash data associated with the assembly.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="c1f1f-108">[in]以位元組為單位的大小`pbHashValue`。</span><span class="sxs-lookup"><span data-stu-id="c1f1f-108">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwFileFlags`  
 <span data-ttu-id="c1f1f-109">[in]位元組合`FileFlags`指定屬性設定的值。</span><span class="sxs-lookup"><span data-stu-id="c1f1f-109">[in] A bitwise combination of `FileFlags` values that specify property settings.</span></span>  
  
 `pmdf`  
 <span data-ttu-id="c1f1f-110">[out]所傳回的指標`File`語彙基元。</span><span class="sxs-lookup"><span data-stu-id="c1f1f-110">[out] A pointer to the returned `File` token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c1f1f-111">備註</span><span class="sxs-lookup"><span data-stu-id="c1f1f-111">Remarks</span></span>  
 <span data-ttu-id="c1f1f-112">一個`File`必須定義中繼資料結構，每個檔案，而這個組件所建立，但不包括包含的中繼資料的檔案次這個組件的一部分。</span><span class="sxs-lookup"><span data-stu-id="c1f1f-112">One `File` metadata structure must be defined for each file that was part of this assembly at the time that this assembly was built, excluding the file that contains the metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1f1f-113">需求</span><span class="sxs-lookup"><span data-stu-id="c1f1f-113">Requirements</span></span>  
 <span data-ttu-id="c1f1f-114">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c1f1f-114">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c1f1f-115">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c1f1f-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c1f1f-116">**程式庫：**做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="c1f1f-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c1f1f-117">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c1f1f-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1f1f-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c1f1f-118">See Also</span></span>  
 [<span data-ttu-id="c1f1f-119">IMetaDataAssemblyEmit 介面</span><span class="sxs-lookup"><span data-stu-id="c1f1f-119">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)