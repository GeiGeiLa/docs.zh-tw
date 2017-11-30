---
title: "ICorDebugManagedCallback::CreateProcess 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback.CreateProcess
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback::CreateProcess
helpviewer_keywords:
- ICorDebugManagedCallback::CreateProcess method [.NET Framework debugging]
- CreateProcess method, ICorDebugManagedCallback interface [.NET Framework debugging]
ms.assetid: 8e89d5ee-e4e3-4738-8302-0b7d1cf4846e
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bef3140717ff977fbfae813d0de89011b89ed062
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmanagedcallbackcreateprocess-method"></a><span data-ttu-id="a760d-102">ICorDebugManagedCallback::CreateProcess 方法</span><span class="sxs-lookup"><span data-stu-id="a760d-102">ICorDebugManagedCallback::CreateProcess Method</span></span>
<span data-ttu-id="a760d-103">當處理程序已附加或第一次啟動時，請告知偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="a760d-103">Notifies the debugger when a process has been attached or started for the first time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a760d-104">語法</span><span class="sxs-lookup"><span data-stu-id="a760d-104">Syntax</span></span>  
  
```  
HRESULT CreateProcess (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a760d-105">參數</span><span class="sxs-lookup"><span data-stu-id="a760d-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="a760d-106">[in]表示已附加或啟動處理序 ICorDebugProcess 物件的指標。</span><span class="sxs-lookup"><span data-stu-id="a760d-106">[in] A pointer to an ICorDebugProcess object that represents the process that has been attached or started.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a760d-107">備註</span><span class="sxs-lookup"><span data-stu-id="a760d-107">Remarks</span></span>  
 <span data-ttu-id="a760d-108">這個方法不會在 common language runtime 初始化之後才能呼叫。</span><span class="sxs-lookup"><span data-stu-id="a760d-108">This method is not called until the common language runtime is initialized.</span></span> <span data-ttu-id="a760d-109">大部分的[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)方法會傳回前的 CORDBG_E_NOTREADY`CreateProcess`回呼。</span><span class="sxs-lookup"><span data-stu-id="a760d-109">Most of the [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) methods will return CORDBG_E_NOTREADY before the `CreateProcess` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a760d-110">需求</span><span class="sxs-lookup"><span data-stu-id="a760d-110">Requirements</span></span>  
 <span data-ttu-id="a760d-111">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a760d-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a760d-112">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a760d-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a760d-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a760d-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a760d-114">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a760d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a760d-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a760d-115">See Also</span></span>  
 [<span data-ttu-id="a760d-116">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="a760d-116">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)