---
title: -匯入 (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- /imports compiler option [Visual Basic]
- imports compiler option [Visual Basic]
- -imports compiler option [Visual Basic]
ms.assetid: 9a93fb53-c080-497b-bf9b-441022dbbc39
ms.openlocfilehash: 330a5e6821c9c76f3503a35a5a5eabf24c686b42
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33652086"
---
# <a name="-imports-visual-basic"></a>-匯入 (Visual Basic)
從指定的組件，匯入命名空間。  
  
## <a name="syntax"></a>語法  
  
```  
-imports:namespaceList  
```  
  
## <a name="arguments"></a>引數  
  
|詞彙|定義|  
|---|---|  
|`namespaceList`|必要。 要匯入的命名空間的逗號分隔清單。|  
  
## <a name="remarks"></a>備註  
 `-imports`選項匯入目前的資料集的來源檔案，或從任何參考的組件內定義的命名空間。  
  
 使用指定的命名空間中的成員`-imports`可用來在編譯中的所有原始程式檔。 使用[Imports 陳述式 （.NET 命名空間和類型）](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)單一原始程式碼檔案中使用命名空間。  
  
|若要設定 Visual Studio 整合式的開發環境中匯入 /|  
|---|  
|1.在 **方案總管**中選取專案。 在 [專案] 功能表上，按一下 [屬性]。 <br />2.按一下 [參考] 節點。<br />3.旁邊的方塊中輸入命名空間名稱**加入使用者匯入** 按鈕。<br />4.按一下**加入使用者匯入** 按鈕。|  
  
## <a name="example"></a>範例  
 下列程式碼會編譯時`/imports:system.globalization`指定。 未安裝，成功編譯需要任一`Imports System.Globalization`陳述式的原始程式碼檔案中，開頭是包含或做為完整限定屬性`System.Globalization.CultureInfo.CurrentCulture.Name`。 
  
 [!code-vb[imports example](codesnippet/VisualBasic/imports_2.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)  
 [參考和 Imports 陳述式](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)  
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
