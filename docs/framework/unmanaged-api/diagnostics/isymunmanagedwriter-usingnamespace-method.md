---
title: ISymUnmanagedWriter::UsingNamespace 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.UsingNamespace
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::UsingNamespace
helpviewer_keywords:
- UsingNamespace method [.NET Framework debugging]
- ISymUnmanagedWriter::UsingNamespace method [.NET Framework debugging]
ms.assetid: 8d746e0a-d158-4983-88da-db0a0856bc0b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9a5ff52a95fd6ebaec05439cbc702d5513d0cc78
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33427765"
---
# <a name="isymunmanagedwriterusingnamespace-method"></a>ISymUnmanagedWriter::UsingNamespace 方法
指定確認目前開啟的語彙範圍內使用指定的完整命名空間名稱。 命名空間將用於所有領域都繼承自目前開啟的範圍內。 關閉目前的範圍也會停止使用命名空間。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT UsingNamespace(  
    [in] const WCHAR *fullName);  
```  
  
#### <a name="parameters"></a>參數  
 `fullName`  
 [in]命名空間的完整名稱指標。  
  
## <a name="return-value"></a>傳回值  
 如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。  
  
## <a name="requirements"></a>需求  
 **標頭：** 於 CorSym.idl、 CorSym.h  
  
## <a name="see-also"></a>另請參閱  
 [ISymUnmanagedWriter 介面](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
