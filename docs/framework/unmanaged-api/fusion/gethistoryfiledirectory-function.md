---
title: GetHistoryFileDirectory 函式
ms.date: 03/30/2017
api_name:
- GetHistoryFileDirectory
api_location:
- fusion.dll
api_type:
- DLLExport
f1_keywords:
- GetHistoryFileDirectory
helpviewer_keywords:
- GetHistoryFileDirectory function [.NET Framework fusion]
ms.assetid: 93232222-926e-42ac-b85d-8a6d33977672
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bba40acf7bfd20897ece4de285fe7a9175be83e0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="gethistoryfiledirectory-function"></a>GetHistoryFileDirectory 函式
擷取應用程式的歷程記錄目錄的路徑。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetHistoryFileDirectory (  
    [in]      LPWSTR      wzDir,  
    [in,out]  LPCWSTR  *pdwsize,  
);  
```  
  
#### <a name="parameters"></a>參數  
 `wzDir`  
 [out]緩衝區來保存應用程式的歷程記錄目錄的路徑。  
  
 `pdwSize`  
 [in、 out]緩衝區的長度。  
  
## <a name="return-value"></a>傳回值  
 這個方法會傳回標準的 COM 錯誤代碼，除了下列的值 WinError.h 檔案中定義。  
  
|傳回碼|描述|  
|-----------------|-----------------|  
|S_OK|已成功完成命令。|  
|E_INVALIDARG|`wzDir` 或`pdwSize`是 null 或版本字串不正確。|  
  
## <a name="remarks"></a>備註  
 成功完成，`pdwSize`引數的設定路徑字串的長度。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Fusion.h  
  
 **程式庫：** Fusion.dll 和 Mscorwks.dll。 使用而不是 Mscorwks.dll 的 Fusion.dll，以確保您設為目標的.NET framework 正確版本。  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [CreateHistoryReader 函式](../../../../docs/framework/unmanaged-api/fusion/createhistoryreader-function.md)  
 [NukeDownloadedCache 函式](../../../../docs/framework/unmanaged-api/fusion/nukedownloadedcache-function.md)  
 [融合全域靜態函式](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
