---
title: 操作說明：在方格之間共用調整大小屬性
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Grid control [WPF], sharing sizing data of columns
- sizing data in Grid controls [WPF]
- Grid control [WPF], sharing sizing data of rows
ms.assetid: a0535a6f-ff04-4b25-9912-7dd856e11044
ms.openlocfilehash: a85c0c36ef99e6501afddaca7f26acd2928da1ae
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33550861"
---
# <a name="how-to-share-sizing-properties-between-grids"></a>操作說明：在方格之間共用調整大小屬性
此範例顯示如何共用的資料行的調整大小資料和資料列之間<xref:System.Windows.Controls.Grid>為了保留以一致的調整大小的項目。  
  
## <a name="example"></a>範例  
 下列範例中導入了兩個<xref:System.Windows.Controls.Grid>為父系的子元素的項目<xref:System.Windows.Controls.DockPanel>。 <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A>附加屬性的<xref:System.Windows.Controls.Grid>定義父代上<xref:System.Windows.Controls.DockPanel>。  
  
 此範例使用兩個操作屬性值<xref:System.Windows.Controls.Button>項目，則每個項目代表一個布林屬性值。 當<xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A>屬性值設定為`true`，每個資料行或資料列成員<xref:System.Windows.Controls.DefinitionBase.SharedSizeGroup%2A>共用大小資訊，不論資料列或資料行的內容。  
  
 [!code-xaml[gridIssharedsizescopeProp#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml#1)]  
  
 ...  
  
 [!code-xaml[gridIssharedsizescopeProp#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml#2)]  
  
 下列範例中，程式碼後置處理方法的按鈕<xref:System.Windows.Controls.Primitives.ButtonBase.Click>事件引發。 範例會將這些方法呼叫的結果<xref:System.Windows.Controls.TextBlock>使用相關的項目有 get 的方法輸出為字串的新屬性值。  
  
 [!code-csharp[gridIssharedsizescopeProp#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml.cs#3)]
 [!code-vb[gridIssharedsizescopeProp#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/gridIssharedsizescopeProp/VisualBasic/Window1.xaml.vb#3)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Controls.Grid>  
 <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A>  
 [面板概觀](../../../../docs/framework/wpf/controls/panels-overview.md)
