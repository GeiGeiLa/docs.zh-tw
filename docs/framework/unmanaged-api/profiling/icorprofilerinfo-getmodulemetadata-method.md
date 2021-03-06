---
title: ICorProfilerInfo::GetModuleMetaData 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetModuleMetaData
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetModuleMetaData
helpviewer_keywords:
- GetModuleMetaData method [.NET Framework profiling]
- ICorProfilerInfo::GetModuleMetaData method [.NET Framework profiling]
ms.assetid: 7a439d92-348a-44dd-b60f-cad7cba56379
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2491b700e8fac512f0d782a42e30ae3114e93c3f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33455542"
---
# <a name="icorprofilerinfogetmodulemetadata-method"></a>ICorProfilerInfo::GetModuleMetaData 方法
取得對應至指定的模組的中繼資料介面執行個體。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetModuleMetaData(  
    [in]  ModuleID moduleId,  
    [in]  DWORD    dwOpenFlags,  
    [in]  REFIID   riid,  
    [out] IUnknown **ppOut);  
```  
  
#### <a name="parameters"></a>參數  
 `moduleId`  
 [in]對應介面的執行個體的模組識別碼。  
  
 `dwOpenFlags`  
 [in]值為[CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md)列舉，指定開啟資訊清單檔案的模式。 只有`ofRead`，`ofWrite`和`ofNoTransform`個位元都是有效。  
  
 `riid`  
 [in]參考識別碼 (GUID) 會擷取其執行個體的中繼資料介面。 請參閱[中繼資料介面](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)的介面清單。  
  
 `ppOut`  
 [out]中繼資料介面執行個體的位址指標。  
  
## <a name="remarks"></a>備註  
 您可能會在讀取/寫入模式中開啟中繼資料要求，但是這樣會導致程式的中繼資料執行速度緩慢，編譯器所顯示的一樣，因為變更無法最佳化中繼資料。  
  
 某些模組 （例如資源模組） 會有任何中繼資料。 在這些情況下，`GetModuleMetaData`會傳回 S_FALSE 和中的 null 的 HRESULT 值 *`ppOut`。  
  
## <a name="requirements"></a>需求  
 **平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ICorProfilerInfo 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
