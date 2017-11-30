---
title: "ICorDebugRegisterSet2 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugRegisterSet2
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugRegisterSet2
helpviewer_keywords: ICorDebugRegisterSet2 interface [.NET Framework debugging]
ms.assetid: d7fbccbf-3b6b-4db8-a96d-768e1cb6b1a6
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 26967f50ded62f935a705c25eed58314b77bedd8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugregisterset2-interface"></a><span data-ttu-id="6444d-102">ICorDebugRegisterSet2 介面</span><span class="sxs-lookup"><span data-stu-id="6444d-102">ICorDebugRegisterSet2 Interface</span></span>
<span data-ttu-id="6444d-103">擴充的功能[ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)具有 64 個以上的暫存器的硬體平台的介面。</span><span class="sxs-lookup"><span data-stu-id="6444d-103">Extends the capabilities of the [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) interface for hardware platforms that have more than 64 registers.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6444d-104">方法</span><span class="sxs-lookup"><span data-stu-id="6444d-104">Methods</span></span>  
  
|<span data-ttu-id="6444d-105">方法</span><span class="sxs-lookup"><span data-stu-id="6444d-105">Method</span></span>|<span data-ttu-id="6444d-106">說明</span><span class="sxs-lookup"><span data-stu-id="6444d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6444d-107">GetRegisters 方法</span><span class="sxs-lookup"><span data-stu-id="6444d-107">GetRegisters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-getregisters-method.md)|<span data-ttu-id="6444d-108">取得每個暫存器值 （在電腦上目前正在執行的程式碼） 的位元遮罩所指定。</span><span class="sxs-lookup"><span data-stu-id="6444d-108">Gets the value of each register (on the computer that is currently executing code) that is specified by the bit mask.</span></span>|  
|[<span data-ttu-id="6444d-109">GetRegistersAvailable 方法</span><span class="sxs-lookup"><span data-stu-id="6444d-109">GetRegistersAvailable Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-getregistersavailable-method.md)|<span data-ttu-id="6444d-110">取得位元組陣列提供的可用暫存器的點陣圖。</span><span class="sxs-lookup"><span data-stu-id="6444d-110">Gets an array of bytes that provides a bitmap of the available registers.</span></span>|  
|[<span data-ttu-id="6444d-111">SetRegisters 方法</span><span class="sxs-lookup"><span data-stu-id="6444d-111">SetRegisters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-setregisters-method.md)|<span data-ttu-id="6444d-112">未實作.NET Framework 2.0 版中。</span><span class="sxs-lookup"><span data-stu-id="6444d-112">Not implemented in the .NET Framework version 2.0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6444d-113">備註</span><span class="sxs-lookup"><span data-stu-id="6444d-113">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6444d-114">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="6444d-114">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6444d-115">需求</span><span class="sxs-lookup"><span data-stu-id="6444d-115">Requirements</span></span>  
 <span data-ttu-id="6444d-116">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6444d-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6444d-117">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6444d-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6444d-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6444d-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6444d-119">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6444d-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6444d-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6444d-120">See Also</span></span>  
 [<span data-ttu-id="6444d-121">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="6444d-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="6444d-122">ICorDebugRegisterSet 介面</span><span class="sxs-lookup"><span data-stu-id="6444d-122">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)