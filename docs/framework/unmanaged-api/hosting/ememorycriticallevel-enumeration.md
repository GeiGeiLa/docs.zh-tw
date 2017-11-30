---
title: "EMemoryCriticalLevel 列舉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: EMemoryCriticalLevel
api_location: mscoree.dll
api_type: COM
f1_keywords: EMemoryCriticalLevel
helpviewer_keywords: EMemoryCriticalLevel enumeration [.NET Framework hosting]
ms.assetid: 2ca8a7a2-7b54-4ba3-8e73-277c7df485f3
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b15a6786cb99a64d441d7e05fb91cd8ff0f3af92
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ememorycriticallevel-enumeration"></a><span data-ttu-id="bc967-102">EMemoryCriticalLevel 列舉</span><span class="sxs-lookup"><span data-stu-id="bc967-102">EMemoryCriticalLevel Enumeration</span></span>
<span data-ttu-id="bc967-103">包含值，表示故障的影響，當有特定記憶體配置要求卻無法滿足。</span><span class="sxs-lookup"><span data-stu-id="bc967-103">Contains values that indicate the impact of a failure when a specific memory allocation has been requested but cannot be satisfied.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc967-104">語法</span><span class="sxs-lookup"><span data-stu-id="bc967-104">Syntax</span></span>  
  
```  
typedef enum {  
    eTaskCritical      = 0,  
    eAppDomainCritical = 1,  
    eProcessCritical   = 2  
} EMemoryCriticalLevel;  
```  
  
## <a name="members"></a><span data-ttu-id="bc967-105">成員</span><span class="sxs-lookup"><span data-stu-id="bc967-105">Members</span></span>  
  
|<span data-ttu-id="bc967-106">成員</span><span class="sxs-lookup"><span data-stu-id="bc967-106">Member</span></span>|<span data-ttu-id="bc967-107">說明</span><span class="sxs-lookup"><span data-stu-id="bc967-107">Description</span></span>|  
|------------|-----------------|  
|`eAppDomainCritical`|<span data-ttu-id="bc967-108">表示配置要求此配置的網域中執行 managed 程式碼的重要。</span><span class="sxs-lookup"><span data-stu-id="bc967-108">Indicates that the allocation is critical for executing managed code in the domain that has requested the allocation.</span></span> <span data-ttu-id="bc967-109">如果無法配置記憶體，無法保證 CLR，網域是仍可使用。</span><span class="sxs-lookup"><span data-stu-id="bc967-109">If memory cannot be allocated, the CLR cannot guarantee that the domain is still usable.</span></span> <span data-ttu-id="bc967-110">主機會決定當無法滿足配置時要採取什麼動作。</span><span class="sxs-lookup"><span data-stu-id="bc967-110">The host decides what action to take when the allocation cannot be satisfied.</span></span> <span data-ttu-id="bc967-111">它可以指示中止 CLR`AppDomain`自動執行，或允許繼續執行上呼叫方法[ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="bc967-111">It can instruct the CLR to abort the `AppDomain` automatically, or allow it to keep running by calling methods on [ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md).</span></span>|  
|`eProcessCritical`|<span data-ttu-id="bc967-112">表示配置是重要的程序中的 managed 程式碼執行。</span><span class="sxs-lookup"><span data-stu-id="bc967-112">Indicates that the allocation is critical to the execution of managed code in the process.</span></span> <span data-ttu-id="bc967-113">執行完成項時，在啟動期間，而且會使用此值。</span><span class="sxs-lookup"><span data-stu-id="bc967-113">This value is used during startup and when running finalizers.</span></span> <span data-ttu-id="bc967-114">如果無法配置記憶體，CLR 就無法執行操作中處理程序。</span><span class="sxs-lookup"><span data-stu-id="bc967-114">If memory cannot be allocated, the CLR cannot operate in the process.</span></span> <span data-ttu-id="bc967-115">如果配置失敗，CLR 會有效停用。</span><span class="sxs-lookup"><span data-stu-id="bc967-115">If the allocation fails, the CLR is effectively disabled.</span></span> <span data-ttu-id="bc967-116">Clr 的所有後續呼叫會失敗並 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="bc967-116">All subsequent calls into the CLR fail with HOST_E_CLRNOTAVAILABLE.</span></span>|  
|`eTaskCritical`|<span data-ttu-id="bc967-117">表示配置是重大執行所要求的配置工作。</span><span class="sxs-lookup"><span data-stu-id="bc967-117">Indicates that the allocation is critical to running the task that has requested the allocation.</span></span> <span data-ttu-id="bc967-118">如果無法配置記憶體，則 CLR 便無法保證可以執行此工作。</span><span class="sxs-lookup"><span data-stu-id="bc967-118">If memory cannot be allocated, the CLR cannot guarantee that the task can be executed.</span></span> <span data-ttu-id="bc967-119">如果發生故障，CLR 會引發<xref:System.Threading.ThreadAbortException>實體作業系統執行緒上。</span><span class="sxs-lookup"><span data-stu-id="bc967-119">In the event of failure, the CLR raises a <xref:System.Threading.ThreadAbortException> on the physical operation system thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bc967-120">備註</span><span class="sxs-lookup"><span data-stu-id="bc967-120">Remarks</span></span>  
 <span data-ttu-id="bc967-121">中定義的記憶體配置方法[IHostMemoryManager](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)和[IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)介面採用這種類型的參數。</span><span class="sxs-lookup"><span data-stu-id="bc967-121">The memory allocation methods defined in the [IHostMemoryManager](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md) and [IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) interfaces take a parameter of this type.</span></span> <span data-ttu-id="bc967-122">失敗的嚴重性而定，主機可以決定是否會立即配置要求失敗，或等候，直到可以滿足。</span><span class="sxs-lookup"><span data-stu-id="bc967-122">Depending upon the severity of a failure, a host can decide whether to fail the allocation request immediately or to wait until it can be satisfied.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc967-123">需求</span><span class="sxs-lookup"><span data-stu-id="bc967-123">Requirements</span></span>  
 <span data-ttu-id="bc967-124">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bc967-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc967-125">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="bc967-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bc967-126">**程式庫：** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bc967-126">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bc967-127">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bc967-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc967-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bc967-128">See Also</span></span>  
 [<span data-ttu-id="bc967-129">ICLRMemoryNotificationCallback 介面</span><span class="sxs-lookup"><span data-stu-id="bc967-129">ICLRMemoryNotificationCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)  
 [<span data-ttu-id="bc967-130">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="bc967-130">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)