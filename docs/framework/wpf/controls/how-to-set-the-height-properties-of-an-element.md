---
title: 如何：設定項目的高度屬性
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- height properties [WPF]
- Panel control [WPF], height properties of elements
ms.assetid: 5ab9e781-dbb8-469a-a3c8-cf38ce312647
ms.openlocfilehash: 4d4aade743507001f825c19994e2f5feb1726ac4
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43525470"
---
# <a name="how-to-set-the-height-properties-of-an-element"></a>如何：設定項目的高度屬性
## <a name="example"></a>範例  
 此範例中以視覺化方式顯示轉譯行為中的四個高度相關屬性之間的差異[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]。  
  
 <xref:System.Windows.FrameworkElement>類別會公開四個屬性描述項目的高度特性。 這四個屬性可能會發生衝突，並會優先使用值時，請以下列方式決定：<xref:System.Windows.FrameworkElement.MinHeight%2A>值會優先於<xref:System.Windows.FrameworkElement.MaxHeight%2A>值，接著會優先於<xref:System.Windows.FrameworkElement.Height%2A>值。 第四個屬性，<xref:System.Windows.FrameworkElement.ActualHeight%2A>是唯讀的且會報告所決定的版面配置程序互動的實際高度。  
  
 下列[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]範例繪製<xref:System.Windows.Shapes.Rectangle>項目 (`rect1`) 做為子系的<xref:System.Windows.Controls.Canvas>。 您可以變更目的高度屬性<xref:System.Windows.Shapes.Rectangle>使用的一系列<xref:System.Windows.Controls.ListBox>代表的屬性值的項目<xref:System.Windows.FrameworkElement.MinHeight%2A>， <xref:System.Windows.FrameworkElement.MaxHeight%2A>，和<xref:System.Windows.FrameworkElement.Height%2A>。 以這種方式，以視覺化方式顯示每個屬性的優先順序。  
  
 [!code-xaml[HeightMinHeightMaxHeight#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml#1)]  
[!code-xaml[HeightMinHeightMaxHeight#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml#2)]  
  
 下列程式碼後置範例處理事件，<xref:System.Windows.Controls.Primitives.Selector.SelectionChanged>事件所引發。 每個處理常式會從輸入<xref:System.Windows.Controls.ListBox>，將做為值剖析<xref:System.Double>，並套用至指定的高度相關屬性的值。 高度值也會在轉換成字串，並寫入至各種<xref:System.Windows.Controls.TextBlock>（定義這些項目未顯示在 選取的 XAML） 的項目。  
  
 [!code-csharp[HeightMinHeightMaxHeight#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml.cs#3)]
 [!code-vb[HeightMinHeightMaxHeight#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HeightMinHeightMaxHeight/VisualBasic/Window1.xaml.vb#3)]  
  
 如需完整的範例，請參閱[高度屬性範例](https://go.microsoft.com/fwlink/?LinkID=159993)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.FrameworkElement>  
 <xref:System.Windows.Controls.ListBox>  
 <xref:System.Windows.FrameworkElement.ActualHeight%2A>  
 <xref:System.Windows.FrameworkElement.MaxHeight%2A>  
 <xref:System.Windows.FrameworkElement.MinHeight%2A>  
 <xref:System.Windows.FrameworkElement.Height%2A>  
 [設定元素的寬度屬性](../../../../docs/framework/wpf/controls/how-to-set-the-width-properties-of-an-element.md)  
 [面板概觀](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [高度屬性範例](https://go.microsoft.com/fwlink/?LinkID=159993)
