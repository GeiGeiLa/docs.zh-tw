---
title: "ISymUnmanagedBinder2 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedBinder2
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedBinder2 Interface
helpviewer_keywords: ISymUnmanagedBinder2 interface [.NET Framework debugging]
ms.assetid: 7a59f405-73e8-4434-8bcc-a9dc45ea08e6
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c276f0abedf4ccab92770af649a8dd0afb6d39d2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedbinder2-interface"></a><span data-ttu-id="c04c7-102">ISymUnmanagedBinder2 介面</span><span class="sxs-lookup"><span data-stu-id="c04c7-102">ISymUnmanagedBinder2 Interface</span></span>
<span data-ttu-id="c04c7-103">表示 unmanaged 程式碼的符號繫結器，並擴充[ISymUnmanagedBinder](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="c04c7-103">Represents a symbol binder for unmanaged code, and extends the [ISymUnmanagedBinder](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md) interface.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c04c7-104">它是從受信任的來源開啟程式資料庫 (PDB) 檔的安全性風險。</span><span class="sxs-lookup"><span data-stu-id="c04c7-104">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c04c7-105">方法</span><span class="sxs-lookup"><span data-stu-id="c04c7-105">Methods</span></span>  
  
|<span data-ttu-id="c04c7-106">方法</span><span class="sxs-lookup"><span data-stu-id="c04c7-106">Method</span></span>|<span data-ttu-id="c04c7-107">說明</span><span class="sxs-lookup"><span data-stu-id="c04c7-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c04c7-108">GetReaderForFile2 方法</span><span class="sxs-lookup"><span data-stu-id="c04c7-108">GetReaderForFile2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md)|<span data-ttu-id="c04c7-109">提供中繼資料介面和檔案名稱，傳回的正確 <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> 會讀取偵錯符號的模組相關聯的介面。</span><span class="sxs-lookup"><span data-stu-id="c04c7-109">Given a metadata interface and a file name, returns the correct <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> interface that will read the debugging symbols associated with the module.</span></span> <span data-ttu-id="c04c7-110">提供比更廣泛的搜尋[isymunmanagedbinder:: Getreaderforfile](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="c04c7-110">Provides a more extensive search than the [ISymUnmanagedBinder::GetReaderForFile](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md) method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c04c7-111">需求</span><span class="sxs-lookup"><span data-stu-id="c04c7-111">Requirements</span></span>  
 <span data-ttu-id="c04c7-112">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="c04c7-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c04c7-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c04c7-113">See Also</span></span>  
 [<span data-ttu-id="c04c7-114">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="c04c7-114">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="c04c7-115">ISymUnmanagedBinder 介面</span><span class="sxs-lookup"><span data-stu-id="c04c7-115">ISymUnmanagedBinder Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)  
 [<span data-ttu-id="c04c7-116">ISymUnmanagedBinder3 介面</span><span class="sxs-lookup"><span data-stu-id="c04c7-116">ISymUnmanagedBinder3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)