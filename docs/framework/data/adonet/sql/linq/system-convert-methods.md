---
title: System.Convert 方法
ms.date: 03/30/2017
ms.assetid: 3ca6c5b6-ea5d-4ab0-b675-f082135b342c
ms.openlocfilehash: a16839bf64d5786caa6feb557333fe93c66edc3c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="systemconvert-methods"></a>System.Convert 方法
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 不支援下列 <xref:System.Convert> 方法。  
  
-   具有 <xref:System.IFormatProvider> 參數的版本。  
  
-   牽涉字元陣列或位元組陣列的方法：  
  
    -   <xref:System.Convert.FromBase64CharArray%2A>  
  
    -   <xref:System.Convert.ToBase64CharArray%2A>  
  
    -   <xref:System.Convert.FromBase64String%2A>  
  
    -   <xref:System.Convert.ToBase64String%2A>  
  
-   下列方法：  
  
    -   `public static <Type2> To<Type2>(<Type1> value);` 其中  
  
         `Type1` 和 `Type2` 各自為 `sbyte`、`uint`、`ulong` 或 `ushort`。  
  
    -   C#:   
  
         `int To<int type>(string value, int fromBase),`  
  
         `ToString(... value, int toBase)`  
  
    -   Visual Basic：  
  
         `Function To(Of [Numeric])(value as String, fromBase As Integer)`  
  
         `As [Numeric], ToString( value As …, toBase As Integer)`  
  
    -   <xref:System.Convert.IsDBNull%2A>  
  
    -   <xref:System.Convert.GetTypeCode%2A>  
  
    -   <xref:System.Convert.ChangeType%2A>  
  
## <a name="see-also"></a>另請參閱  
 [資料類型和函式](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
