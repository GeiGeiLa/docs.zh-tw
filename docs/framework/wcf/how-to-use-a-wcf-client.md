---
title: HOW TO：使用 Windows Communication Foundation 用戶端
ms.date: 09/14/2018
helpviewer_keywords:
- WCF clients [WCF], using
dev_langs:
- CSharp
- VB
ms.assetid: 190349fc-0573-49c7-bb85-8e316df7f31f
ms.openlocfilehash: 12e911fb899cb85121c129b762828cdda01e64f1
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/26/2018
ms.locfileid: "47193079"
---
# <a name="how-to-use-a-windows-communication-foundation-client"></a>HOW TO：使用 Windows Communication Foundation 用戶端

這是建立基本的 Windows Communication Foundation (WCF) 應用程式所需的六個工作的最後一個。 如需這六個工作的概觀，請參閱[使用者入門教學課程](../../../docs/framework/wcf/getting-started-tutorial.md)主題。

一旦已建立並設定 Windows Communication Foundation (WCF) proxy，用戶端執行個體可由用戶端應用程式可以和編譯用來與 WCF 服務進行通訊。 本主題描述具現化，並使用 WCF 用戶端的程序。 這個程序會執行三項工作：

1.  具現化 WCF 用戶端。

2.  從產生的 Proxy 呼叫服務作業。

3.  在完成作業呼叫後即關閉用戶端。

## <a name="use-a-windows-communication-foundation-client"></a>使用 Windows Communication Foundation 用戶端

開啟 GettingStartedClient 專案中的 Program.cs 或 Program.vb 檔案，並以下列程式碼取代現有的程式碼：

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GettingStartedClient.ServiceReference1;

namespace GettingStartedClient
{
    class Program
    {
        static void Main(string[] args)
        {
            //Step 1: Create an instance of the WCF proxy.
            CalculatorClient client = new CalculatorClient();

            // Step 2: Call the service operations.
            // Call the Add service operation.
            double value1 = 100.00D;
            double value2 = 15.99D;
            double result = client.Add(value1, value2);
            Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);

            // Call the Subtract service operation.
            value1 = 145.00D;
            value2 = 76.54D;
            result = client.Subtract(value1, value2);
            Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);

            // Call the Multiply service operation.
            value1 = 9.00D;
            value2 = 81.25D;
            result = client.Multiply(value1, value2);
            Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);

            // Call the Divide service operation.
            value1 = 22.00D;
            value2 = 7.00D;
            result = client.Divide(value1, value2);
            Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);

            //Step 3: Closing the client gracefully closes the connection and cleans up resources.
            client.Close();
        }
    }
}
```

```vb
Imports System
Imports System.Collections.Generic
Imports System.Text
Imports System.ServiceModel
Imports GettingStartedClientVB2.ServiceReference1

Module Module1

    Sub Main()
        ' Step 1: Create an instance of the WCF proxy
        Dim Client As New CalculatorClient()

        'Step 2: Call the service operations.
        'Call the Add service operation.
        Dim value1 As Double = 100D
        Dim value2 As Double = 15.99D
        Dim result As Double = Client.Add(value1, value2)
        Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result)

        'Call the Subtract service operation.
        value1 = 145D
        value2 = 76.54D
        result = Client.Subtract(value1, value2)
        Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result)

        'Call the Multiply service operation.
        value1 = 9D
        value2 = 81.25D
        result = Client.Multiply(value1, value2)
        Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result)

        'Call the Divide service operation.
        value1 = 22D
        value2 = 7D
        result = Client.Divide(value1, value2)
        Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result)

        ' Step 3: Closing the client gracefully closes the connection and cleans up resources.
        Client.Close()

        Console.WriteLine()
        Console.WriteLine("Press <ENTER> to terminate client.")
        Console.ReadLine()

    End Sub

End Module
```

請注意`using`或是`Imports`匯入的陳述式`GettingStartedClient.ServiceReference1`。 這樣會匯入所產生的程式碼**加入服務參考**Visual Studio 中。 程式碼會具現化 WCF proxy 然後會呼叫每個計算機服務所公開的服務作業，並關閉 proxy 時，而會結束。

您現在已完成教學課程。 您定義服務合約、實作服務合約、產生 WCF Proxy、設定 WCF 用戶端應用程式，然後使用 Proxy 來呼叫服務作業。 若要測試應用程式，先執行 GettingStartedHost 以啟動服務，然後再執行 GettingStartedClient。

GettingStartedHost 的輸出應該看起來像這樣：

```text
The service is ready.Press <ENTER> to terminate service.Received Add(100,15.99)Return: 115.99Received Subtract(145,76.54)Return: 68.46Received Multiply(9,81.25)Return: 731.25Received Divide(22,7)Return: 3.14285714285714
```

GettingStartedClient 的輸出應該看起來像這樣：

```text
Add(100,15.99) = 115.99Subtract(145,76.54) = 68.46Multiply(9,81.25) = 731.25Divide(22,7) = 3.14285714285714Press <ENTER> to terminate client.
```

## <a name="see-also"></a>另請參閱

- [建置用戶端](../../../docs/framework/wcf/building-clients.md)
- [如何：建立用戶端](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)
- [快速入門教學課程](../../../docs/framework/wcf/getting-started-tutorial.md)
- [基本 WCF 程式設計](../../../docs/framework/wcf/basic-wcf-programming.md)
- [如何：建立雙面合約](../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)
- [如何：使用雙面合約存取服務](../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md)
- [快速入門](../../../docs/framework/wcf/samples/getting-started-sample.md)
- [自我裝載](../../../docs/framework/wcf/samples/self-host.md)