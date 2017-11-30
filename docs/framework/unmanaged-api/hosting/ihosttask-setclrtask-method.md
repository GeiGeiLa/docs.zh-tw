---
title: "IHostTask::SetCLRTask 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTask.SetCLRTask
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTask::SetCLRTask
helpviewer_keywords:
- SetCLRTask method [.NET Framework hosting]
- IHostTask::SetCLRTask method [.NET Framework hosting]
ms.assetid: e9d39c80-41a1-49e7-bb5e-ea3433bfb5d7
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 54706b1c3a6ea1864137e2eca135fa6bd883b345
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ihosttasksetclrtask-method"></a><span data-ttu-id="b1d88-102">IHostTask::SetCLRTask 方法</span><span class="sxs-lookup"><span data-stu-id="b1d88-102">IHostTask::SetCLRTask Method</span></span>
<span data-ttu-id="b1d88-103">將`ICLRTask`與目前的執行個體[IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)執行個體。</span><span class="sxs-lookup"><span data-stu-id="b1d88-103">Associates an `ICLRTask` instance with the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1d88-104">語法</span><span class="sxs-lookup"><span data-stu-id="b1d88-104">Syntax</span></span>  
  
```  
HRESULT SetCLRTask (  
    [in] ICLRTask *pCLRTask  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b1d88-105">參數</span><span class="sxs-lookup"><span data-stu-id="b1d88-105">Parameters</span></span>  
 `pCLRTask`  
 <span data-ttu-id="b1d88-106">[in]介面指標`ICLRTask`要關聯到目前的執行個體`IHostTask`執行個體。</span><span class="sxs-lookup"><span data-stu-id="b1d88-106">[in] An interface pointer to the `ICLRTask` instance to be associated with the current `IHostTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b1d88-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="b1d88-107">Return Value</span></span>  
  
|<span data-ttu-id="b1d88-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b1d88-108">HRESULT</span></span>|<span data-ttu-id="b1d88-109">描述</span><span class="sxs-lookup"><span data-stu-id="b1d88-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b1d88-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="b1d88-110">S_OK</span></span>|<span data-ttu-id="b1d88-111">`SetCLRTask`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="b1d88-111">`SetCLRTask` returned successfully.</span></span>|  
|<span data-ttu-id="b1d88-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b1d88-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b1d88-113">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="b1d88-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b1d88-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b1d88-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b1d88-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="b1d88-115">The call timed out.</span></span>|  
|<span data-ttu-id="b1d88-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b1d88-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b1d88-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="b1d88-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b1d88-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b1d88-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b1d88-119">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="b1d88-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b1d88-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b1d88-120">E_FAIL</span></span>|<span data-ttu-id="b1d88-121">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="b1d88-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b1d88-122">方法會傳回 E_FAIL CLR 已不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="b1d88-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b1d88-123">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="b1d88-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b1d88-124">備註</span><span class="sxs-lookup"><span data-stu-id="b1d88-124">Remarks</span></span>  
 <span data-ttu-id="b1d88-125">CLR 會呼叫`SetCLRTask`關聯`ICLRTask`與目前的執行個體`IHostTask`執行個體，這由呼叫[ihosttaskmanager:: Createtask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-createtask-method.md)。</span><span class="sxs-lookup"><span data-stu-id="b1d88-125">The CLR calls `SetCLRTask` to associate an `ICLRTask` instance with the current `IHostTask` instance, which was created by a call to [IHostTaskManager::CreateTask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-createtask-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1d88-126">需求</span><span class="sxs-lookup"><span data-stu-id="b1d88-126">Requirements</span></span>  
 <span data-ttu-id="b1d88-127">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b1d88-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1d88-128">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b1d88-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b1d88-129">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="b1d88-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b1d88-130">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1d88-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1d88-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b1d88-131">See Also</span></span>  
 [<span data-ttu-id="b1d88-132">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="b1d88-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="b1d88-133">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="b1d88-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="b1d88-134">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="b1d88-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="b1d88-135">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="b1d88-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)