---
title: -&gt; 運算子 (C# 參考)
ms.date: 07/20/2015
f1_keywords:
- ->_CSharpKeyword
helpviewer_keywords:
- member access operator (->) [C#]
- -> operator [C#]
ms.assetid: e39ccdc1-f1ff-4a92-bf1d-ac2c8c11316a
ms.openlocfilehash: fb95e508ce1339868723bcc3178851e8c1355c1f
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2018
ms.locfileid: "45609514"
---
# <a name="-gt-operator-c-reference"></a>-&gt; 運算子 (C# 參考)
`->` 運算子結合了指標取值和成員存取。  
  
## <a name="remarks"></a>備註  
 以下格式的運算式：  
  
```csharp  
x->y  
```  
  
 (其中 `x` 是類型 `T*` 的指標，而 `y` 是 `T` 的成員) 相當於：  
  
```csharp  
(*x).y  
```  
  
 `->` 運算子只能用於標記為 [unsafe](../../../csharp/language-reference/keywords/unsafe.md) 的程式碼。  
  
 無法多載 `->` 運算子。  
  
## <a name="example"></a>範例  
 [!code-csharp[csRefOperators#15](../../../csharp/language-reference/operators/codesnippet/CSharp/dereference-operator_1.cs)]  
  
## <a name="see-also"></a>請參閱

- [C# 參考](../../../csharp/language-reference/index.md)  
- [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
- [C# 運算子](../../../csharp/language-reference/operators/index.md)
