---
title: "ICorDebugProcess::IsTransitionStub 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess.IsTransitionStub
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess::IsTransitionStub
helpviewer_keywords:
- ICorDebugProcess::IsTransitionStub method [.NET Framework debugging]
- IsTransitionStub method [.NET Framework debugging]
ms.assetid: f7653317-7e48-4163-be03-f50f1a4b0f70
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 60f6e4116768d2d855edd941df796167754b3ab4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugprocessistransitionstub-method"></a><span data-ttu-id="39006-102">ICorDebugProcess::IsTransitionStub 方法</span><span class="sxs-lookup"><span data-stu-id="39006-102">ICorDebugProcess::IsTransitionStub Method</span></span>
<span data-ttu-id="39006-103">取得值，指出是否會導致轉換為 managed 程式碼的虛設常式內的位址。</span><span class="sxs-lookup"><span data-stu-id="39006-103">Gets a value that indicates whether an address is inside a stub that will cause a transition to managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39006-104">語法</span><span class="sxs-lookup"><span data-stu-id="39006-104">Syntax</span></span>  
  
```  
HRESULT IsTransitionStub(  
    [in]  CORDB_ADDRESS address,  
    [out] BOOL *pbTransitionStub);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="39006-105">參數</span><span class="sxs-lookup"><span data-stu-id="39006-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="39006-106">[in]A`CORDB_ADDRESS`值，指定有問題的位址。</span><span class="sxs-lookup"><span data-stu-id="39006-106">[in] A `CORDB_ADDRESS` value that specifies the address in question.</span></span>  
  
 `pbTransitionStub`  
 <span data-ttu-id="39006-107">[out]為的布林值的指標`true`如果指定的位址是內部的虛設常式會將導致轉換為 managed 程式碼; 否則為 *`pbTransitionStub`是`false`。</span><span class="sxs-lookup"><span data-stu-id="39006-107">[out] A pointer to a Boolean value that is `true` if the specified address is inside a stub that will cause a transition to managed code; otherwise *`pbTransitionStub` is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="39006-108">備註</span><span class="sxs-lookup"><span data-stu-id="39006-108">Remarks</span></span>  
 <span data-ttu-id="39006-109">`IsTransitionStub`決定何時將逐步執行控制權傳回給受管理的 stepper unmanaged 逐步執行程式碼可以使用方法。</span><span class="sxs-lookup"><span data-stu-id="39006-109">The `IsTransitionStub` method can be used by unmanaged stepping code to decide when to return stepping control to the managed stepper.</span></span>  
  
 <span data-ttu-id="39006-110">您也可以藉由查看可攜式執行檔 (PE) 中的資訊識別轉換 stub。</span><span class="sxs-lookup"><span data-stu-id="39006-110">You can also identity transition stubs by looking at information in the portable executable (PE) file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="39006-111">需求</span><span class="sxs-lookup"><span data-stu-id="39006-111">Requirements</span></span>  
 <span data-ttu-id="39006-112">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="39006-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="39006-113">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="39006-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="39006-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="39006-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="39006-115">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="39006-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>