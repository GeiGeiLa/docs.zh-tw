---
title: 除了最後項目以外的所有欄位寬度都必須大於零
ms.date: 07/20/2015
f1_keywords:
- vbrTextFieldParser_FieldWidthsMustPositive
ms.assetid: 41d8c661-a749-4c89-be56-905c6e7c3c9d
ms.openlocfilehash: e8026cc7c122d37c135db28813353f7e37f200e7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33598436"
---
# <a name="all-field-widths-except-the-last-element-must-be-greater-than-zero"></a>除了最後項目以外的所有欄位寬度都必須大於零
除了最後項目以外的所有欄位寬度都必須大於零。 最後項目的欄位寬度小於或等於零，表示最後欄位是可變長度。  
  
 作業失敗，因為除了最後項目以外的欄位寬度都設定為等於或小於零。 小於或等於零的欄位寬度可以用作最後項目，表示最後欄位是可變長度，但不能用作任何其他項目。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   將欄位寬度設定為正確的長度。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.SetFieldWidths%2A?displayProperty=nameWithType>  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.FieldWidths>  
 [如何：從固定寬度的文字檔讀取](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-fixed-width-text-files.md)  
 [TextFieldParser 物件](../../visual-basic/language-reference/objects/textfieldparser-object.md)
