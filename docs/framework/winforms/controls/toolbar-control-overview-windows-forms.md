---
title: ToolBar 控制項概觀 (Windows Form)
ms.date: 03/30/2017
f1_keywords:
- ToolBar
helpviewer_keywords:
- toolbars [Windows Forms], about toolbars
- ToolBar control [Windows Forms], about ToolBar controls
ms.assetid: d426b203-0216-4dbe-b834-1641e50a9c29
ms.openlocfilehash: f94ac009081ca4b0c1c462f6413b711a6e64edfc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33540745"
---
# <a name="toolbar-control-overview-windows-forms"></a>ToolBar 控制項概觀 (Windows Form)
> [!NOTE]
>  <xref:System.Windows.Forms.ToolStrip> 控制項會取代 <xref:System.Windows.Forms.ToolBar> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.ToolBar> 控制項，以提供回溯相容性及未來使用。  
  
 Windows Form <xref:System.Windows.Forms.ToolBar> 控制項在表單中，是當做顯示下拉式功能表其中一列的控制列和啟動命令的點陣圖按鈕使用。 因此，按一下工具列按鈕相當於選擇功能表命令。 您可將這些按鈕設定成與按鈕、下拉式功能表或分隔符號一樣地顯示和運作。 一般而言，工具列包含對應至應用程式功能表結構中項目的按鈕和功能表，可以快速存取應用程式中最常使用的功能和命令。  
  
## <a name="working-with-the-toolbar-control"></a>使用 ToolBar 控制項  
 A<xref:System.Windows.Forms.ToolBar>控制項通常是 「 停駐 」 以及它的父視窗的頂端，但它可以也停駐視窗的任何一側。 當使用者將滑鼠指標指向工具列按鈕時，工具列可以顯示工具提示。 工具提示是一個小型快顯視窗，用於簡短描述按鈕或功能表的用途。 若要顯示工具提示，<xref:System.Windows.Forms.ToolBar.ShowToolTips%2A>屬性必須設定為`true`。  
  
> [!NOTE]
>  特定應用程式功能控制項十分類似可以「浮動」在應用程式視窗上方和重新定位的工具列。 Windows Forms ToolBar 控制項無法執行這些動作。  
  
 當<xref:System.Windows.Forms.ToolBar.Appearance%2A>屬性設定為<xref:System.Windows.Forms.ToolBarAppearance>，引發和三維的工具列按鈕會出現。 您可以設定<xref:System.Windows.Forms.ToolBar.Appearance%2A>工具列屬性<xref:System.Windows.Forms.ToolBarAppearance>，提供工具列和其按鈕一般外觀。 將滑鼠指標移到一般按鈕上方時，按鈕的外觀會變更為三維。 工具列按鈕可以使用分隔符號來分割為邏輯群組。 分隔符號是工具列按鈕與<xref:System.Windows.Forms.ToolBarButton.Style%2A>屬性設定為<xref:System.Windows.Forms.ToolBarButtonStyle>。 它在工具列上會顯示為空白空間。 工具列具有一般外觀時，按鈕分隔符號在按鈕之間會顯示為線條，而不是空格。  
  
 <xref:System.Windows.Forms.ToolBar>控制項可讓您建立工具列加入<xref:System.Windows.Forms.Button>物件加入至<xref:System.Windows.Forms.ToolBar.Buttons%2A>集合。 您可以使用 集合編輯器加入至按鈕<xref:System.Windows.Forms.ToolBar>控制項; 每一個<xref:System.Windows.Forms.Button>物件應該具有文字或指派，映像，雖然您可以指派兩者。 相關聯 [ImageList](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md) 元件所提供的影像。 在執行階段，您可以新增或移除按鈕從<xref:System.Windows.Forms.ToolBar.ToolBarButtonCollection>使用<xref:System.Windows.Forms.ToolBar.ToolBarButtonCollection.Add%2A>和<xref:System.Windows.Forms.ToolBar.ToolBarButtonCollection.Remove%2A>方法。 若要程式設計的按鈕<xref:System.Windows.Forms.ToolBar>，將程式碼加入<xref:System.Windows.Forms.ToolBar.ButtonClick>事件<xref:System.Windows.Forms.ToolBar>，並使用<xref:System.Windows.Forms.ToolBarButtonClickEventArgs.Button%2A>屬性<xref:System.Windows.Forms.ToolBarButtonClickEventArgs>類別以決定哪一個按鈕已按下。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.ToolBar>  
 [ToolBar 控制項](../../../../docs/framework/winforms/controls/toolbar-control-windows-forms.md)  
 [操作說明：將按鈕新增至工具列控制項](../../../../docs/framework/winforms/controls/how-to-add-buttons-to-a-toolbar-control.md)  
 [操作說明：定義工具列按鈕的圖示](../../../../docs/framework/winforms/controls/how-to-define-an-icon-for-a-toolbar-button.md)  
 [操作說明：觸發工具列按鈕的功能表事件](../../../../docs/framework/winforms/controls/how-to-trigger-menu-events-for-toolbar-buttons.md)
