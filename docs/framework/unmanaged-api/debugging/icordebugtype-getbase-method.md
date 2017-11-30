---
title: "ICorDebugType::GetBase 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugType.GetBase
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugType::GetBase
helpviewer_keywords:
- ICorDebugType::GetBase method [.NET Framework debugging]
- GetBase method [.NET Framework debugging]
ms.assetid: f24e1af9-c220-4f79-ae62-4153ec17ea81
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: de00e519b43d486e70d5ed8165eed01b59d6e725
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugtypegetbase-method"></a><span data-ttu-id="8bece-102">ICorDebugType::GetBase 方法</span><span class="sxs-lookup"><span data-stu-id="8bece-102">ICorDebugType::GetBase Method</span></span>
<span data-ttu-id="8bece-103">取得的介面指標來代表基底類型中，如果有的話，表示這個型別的 ICorDebugType `ICorDebugType`。</span><span class="sxs-lookup"><span data-stu-id="8bece-103">Gets an interface pointer to an ICorDebugType that represents the base type, if one exists, of the type represented by this `ICorDebugType`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8bece-104">語法</span><span class="sxs-lookup"><span data-stu-id="8bece-104">Syntax</span></span>  
  
```  
HRESULT GetBase (  
    [out] ICorDebugType   **pBase  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8bece-105">參數</span><span class="sxs-lookup"><span data-stu-id="8bece-105">Parameters</span></span>  
 `pBase`  
 <span data-ttu-id="8bece-106">[out]位址指標`ICorDebugType`代表基底類型的物件。</span><span class="sxs-lookup"><span data-stu-id="8bece-106">[out] A pointer to the address of an `ICorDebugType` object that represents the base type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8bece-107">備註</span><span class="sxs-lookup"><span data-stu-id="8bece-107">Remarks</span></span>  
 <span data-ttu-id="8bece-108">查詢類型的基底類型適合實作常見的偵錯工具功能，例如列印出的物件或其父類別的所有欄位。</span><span class="sxs-lookup"><span data-stu-id="8bece-108">Looking up the base type for a type is useful to implement common debugger functionality, such as printing out all the fields of an object or its parent classes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8bece-109">需求</span><span class="sxs-lookup"><span data-stu-id="8bece-109">Requirements</span></span>  
 <span data-ttu-id="8bece-110">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8bece-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8bece-111">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8bece-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8bece-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8bece-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8bece-113">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8bece-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>