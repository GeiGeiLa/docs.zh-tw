---
title: "FunctionEnter 函式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: FunctionEnter
api_location: mscorwks.dll
api_type: COM
f1_keywords: FunctionEnter
helpviewer_keywords: FunctionEnter function [.NET Framework profiling]
ms.assetid: bf4ffa50-4506-4dd4-aa13-a0457b47ca74
topic_type: apiref
caps.latest.revision: "17"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 0cd98e6db0f400d022fe0af4e96336616cbb7183
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="functionenter-function"></a><span data-ttu-id="eda3c-102">FunctionEnter 函式</span><span class="sxs-lookup"><span data-stu-id="eda3c-102">FunctionEnter Function</span></span>
<span data-ttu-id="eda3c-103">通知分析工具控制會傳遞至函數。</span><span class="sxs-lookup"><span data-stu-id="eda3c-103">Notifies the profiler that control is being passed to a function.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="eda3c-104">`FunctionEnter`函式已被取代，在.NET Framework 2.0 版中，並使用它將會產生對效能帶來負面影響。</span><span class="sxs-lookup"><span data-stu-id="eda3c-104">The `FunctionEnter` function is deprecated in the .NET Framework version 2.0, and its use will incur a performance penalty.</span></span> <span data-ttu-id="eda3c-105">使用[FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)函式。</span><span class="sxs-lookup"><span data-stu-id="eda3c-105">Use the [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) function instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eda3c-106">語法</span><span class="sxs-lookup"><span data-stu-id="eda3c-106">Syntax</span></span>  
  
```  
void __stdcall FunctionEnter (  
    [in]  FunctionID funcID  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="eda3c-107">參數</span><span class="sxs-lookup"><span data-stu-id="eda3c-107">Parameters</span></span>  
 `funcID`  
 <span data-ttu-id="eda3c-108">[in]控制權會傳遞函式的識別項。</span><span class="sxs-lookup"><span data-stu-id="eda3c-108">[in] The identifier of the function to which control is passed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eda3c-109">備註</span><span class="sxs-lookup"><span data-stu-id="eda3c-109">Remarks</span></span>  
 <span data-ttu-id="eda3c-110">`FunctionEnter`函式是回呼，您必須實作它。</span><span class="sxs-lookup"><span data-stu-id="eda3c-110">The `FunctionEnter` function is a callback; you must implement it.</span></span> <span data-ttu-id="eda3c-111">實作必須使用`__declspec`(`naked`) 儲存類別屬性。</span><span class="sxs-lookup"><span data-stu-id="eda3c-111">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="eda3c-112">執行引擎不會呼叫此函數之前儲存任何暫存器。</span><span class="sxs-lookup"><span data-stu-id="eda3c-112">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="eda3c-113">進入時，您必須儲存所有您使用，包括浮點數的單位 (FPU) 中的暫存器。</span><span class="sxs-lookup"><span data-stu-id="eda3c-113">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="eda3c-114">結束時，您必須還原堆疊取出關閉推入其呼叫端的所有參數。</span><span class="sxs-lookup"><span data-stu-id="eda3c-114">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="eda3c-115">實作`FunctionEnter`不應該封鎖，因為它將會延遲記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="eda3c-115">The implementation of `FunctionEnter` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="eda3c-116">實作不應嘗試在記憶體回收，因為堆疊可能不在記憶體回收方便集合的狀態。</span><span class="sxs-lookup"><span data-stu-id="eda3c-116">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="eda3c-117">如果嘗試在記憶體回收時，執行階段將會封鎖直到`FunctionEnter`傳回。</span><span class="sxs-lookup"><span data-stu-id="eda3c-117">If a garbage collection is attempted, the runtime will block until `FunctionEnter` returns.</span></span>  
  
 <span data-ttu-id="eda3c-118">此外，`FunctionEnter`函式不可以呼叫至 managed 程式碼或任何方式發生原因的 managed 的記憶體配置。</span><span class="sxs-lookup"><span data-stu-id="eda3c-118">Also, the `FunctionEnter` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eda3c-119">需求</span><span class="sxs-lookup"><span data-stu-id="eda3c-119">Requirements</span></span>  
 <span data-ttu-id="eda3c-120">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="eda3c-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eda3c-121">**標頭：** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="eda3c-121">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="eda3c-122">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eda3c-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eda3c-123">**.NET framework 版本：** 1.1、 1.0</span><span class="sxs-lookup"><span data-stu-id="eda3c-123">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eda3c-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eda3c-124">See Also</span></span>  
 [<span data-ttu-id="eda3c-125">FunctionEnter2 函式</span><span class="sxs-lookup"><span data-stu-id="eda3c-125">FunctionEnter2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)  
 [<span data-ttu-id="eda3c-126">FunctionLeave2 函式</span><span class="sxs-lookup"><span data-stu-id="eda3c-126">FunctionLeave2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)  
 [<span data-ttu-id="eda3c-127">FunctionTailcall2 函式</span><span class="sxs-lookup"><span data-stu-id="eda3c-127">FunctionTailcall2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)  
 [<span data-ttu-id="eda3c-128">SetEnterLeaveFunctionHooks2 方法</span><span class="sxs-lookup"><span data-stu-id="eda3c-128">SetEnterLeaveFunctionHooks2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)  
 [<span data-ttu-id="eda3c-129">分析全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="eda3c-129">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)