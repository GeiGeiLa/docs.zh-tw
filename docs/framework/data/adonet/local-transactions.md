---
title: 本機異動
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8ae3712f-ef5e-41a1-9ea9-b3d0399439f1
ms.openlocfilehash: 17bf06864016ece571b21bee2c180b5781a62959
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43528255"
---
# <a name="local-transactions"></a>本機異動
當您要將多個工作繫結在一起，以讓它們當做單一的工作單位來執行時，便會使用 [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] 中的交易。 例如，想像應用程式正在執行兩項工作。 首先，它會更新包含訂單資訊的資料表。 然後會更新包含存貨資訊的資料表，將訂購項目記入借方。 如果任一個工作失敗，則這兩個更新會回復。  
  
## <a name="determining-the-transaction-type"></a>決定異動類型  
 交易是被視為本機交易時它是單一階段交易，並直接處理資料庫。 交易是被視為是分散式的交易，它由交易監視器協調，並使用保全機制 （如兩階段交易認可），進行交易解析時。  
  
 每個 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 資料提供者都有它自己的 `Transaction` 物件，以執行本機交易。 如果您需要在 SQL Server 資料庫中執行交易，請選擇 <xref:System.Data.SqlClient> 交易。 若為 Oracle 交易，請使用 <xref:System.Data.OracleClient> 提供者。 此外，還有<xref:System.Data.Common.DbTransaction>適用於撰寫需要交易的提供者獨立程式碼的類別。  
  
> [!NOTE]
> 在伺服器上執行異動是最有效率的。 如果您使用的 SQL Server 資料庫大量使用明確的異動，請考慮使用 Transact-SQL BEGIN TRANSACTION 陳述式，將它們寫入為預存程序。
  
## <a name="performing-a-transaction-using-a-single-connection"></a>使用單一連接執行異動  
 在 [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] 中，您會使用 `Connection` 物件控制交易。 您可使用 `BeginTransaction` 方法來起始本機交易。 開始交易之後，您可使用 `Transaction` 物件的 `Command` 屬性，在該交易中登記命令。 然後，您可根據交易元件的成敗，來認可或復原對資料來源所做的修改。  
  
> [!NOTE]
>  `EnlistDistributedTransaction` 方法不可用於本機交易。  
  
 交易的範圍僅限於連接。 下列範例執行由 `try` 區塊中的兩個單獨命令所組成的明確交易。 命令執行針對的 Production.ScrapReason 資料表的 INSERT 陳述式在 AdventureWorks SQL Server 範例資料庫中，也就是已認可，如果擲不回任何例外狀況。 如果擲回例外狀況，則 `catch` 區塊中的程式碼便會復原交易。 如果交易在完成之前遭到中止或連接關閉，則會自動復原該交易。  
  
## <a name="example"></a>範例  
 請遵循下列步驟來執行交易。  
  
1.  呼叫 <xref:System.Data.SqlClient.SqlConnection.BeginTransaction%2A> 物件的 <xref:System.Data.SqlClient.SqlConnection> 方法，來標記交易的開始。 <xref:System.Data.SqlClient.SqlConnection.BeginTransaction%2A> 方法會將參考傳回給交易。 此參考會指派給登記在交易中的 <xref:System.Data.SqlClient.SqlCommand> 物件。  
  
2.  將 `Transaction` 物件指派給要執行之 <xref:System.Data.SqlClient.SqlCommand.Transaction%2A> 的 <xref:System.Data.SqlClient.SqlCommand> 屬性。 如果在有交易正在作用中的連接上執行命令，且 `Transaction` 物件尚未指派給 `Transaction` 物件的 `Command` 屬性，便會擲回例外狀況。  
  
3.  執行必要的命令。  
  
4.  呼叫 <xref:System.Data.SqlClient.SqlTransaction.Commit%2A> 物件的 <xref:System.Data.SqlClient.SqlTransaction> 方法來完成交易，或呼叫 <xref:System.Data.SqlClient.SqlTransaction.Rollback%2A> 方法來中止交易。 如果在執行 <xref:System.Data.SqlClient.SqlTransaction.Commit%2A> 或 <xref:System.Data.SqlClient.SqlTransaction.Rollback%2A> 方法之前關閉或處置連接，則會復原交易。  
  
 下列程式碼範例會藉由搭配使用 [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] 與 Microsoft SQL Server 來示範交易邏輯。  
  
 [!code-csharp[DataWorks SqlTransaction.Local#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTransaction.Local/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTransaction.Local#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTransaction.Local/VB/source.vb#1)]  
  
## <a name="see-also"></a>另請參閱  
 [異動和並行存取](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)  
 [分散式異動](../../../../docs/framework/data/adonet/distributed-transactions.md)  
 [System.Transactions 與 SQL Server 整合](../../../../docs/framework/data/adonet/system-transactions-integration-with-sql-server.md)  
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
