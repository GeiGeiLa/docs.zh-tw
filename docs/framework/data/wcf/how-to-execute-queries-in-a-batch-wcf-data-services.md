---
title: 如何：批次執行查詢 (WCF 資料服務)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, batch requests
ms.assetid: 3b4db7df-bd33-43a1-8ea4-63a18e131f97
ms.openlocfilehash: d710d6539cf465624aa985ce19a67a6d8fb8ee8d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33355406"
---
# <a name="how-to-execute-queries-in-a-batch-wcf-data-services"></a>如何：批次執行查詢 (WCF 資料服務)
使用[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]用戶端程式庫，您可以在單一批次中執行多個查詢對資料服務。 如需詳細資訊，請參閱[批次處理作業](../../../../docs/framework/data/wcf/batching-operations-wcf-data-services.md)。  
  
 本主題中的範例使用 Northwind 範例資料服務和自動產生的用戶端資料服務類別。 當您完成建立此服務和用戶端資料類別[WCF Data Services 快速入門](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)。  
  
## <a name="example"></a>範例  
 下列範例顯示如何呼叫 <xref:System.Data.Services.Client.DataServiceContext.ExecuteBatch%2A> 方法，執行 <xref:System.Data.Services.Client.DataServiceRequest%601> 物件的陣列，其中包含從 Northwind 資料服務同時傳回 `Customers` 和 `Products` 物件的查詢。 在傳回的 <xref:System.Data.Services.Client.QueryOperationResponse%601>中，會列舉 <xref:System.Data.Services.Client.DataServiceResponse> 物件集合以及包含在每一個 <xref:System.Data.Services.Client.QueryOperationResponse%601> 中的物件集合。  
  
 [!code-csharp[Astoria Northwind Client#BatchQuery](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#batchquery)]
 [!code-vb[Astoria Northwind Client#BatchQuery](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#batchquery)]  
  
## <a name="see-also"></a>另請參閱  
 [WCF Data Services 用戶端程式庫](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
